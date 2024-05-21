### **[ Low - 1 ]** 
-----
This has been flagged as NC by [4naly3er](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/4naly3er-report.md#nc-1-missing-checks-for-address0-when-assigning-values-to-address-state-variables) on the first instance, but I wanted to still report it as found a more severe impact(Low) for the lack of validation.

Essentially, since `EdgeChallengeManager` is allowed to be initialized with an `empty stakeToken`, that allow the possibility for users to create an `EdgeStakingPool` that can't do anything, so gas wasted creating such pool, which seems to warrant `Low severity`. Granted someone could argue that user should not try todo such action if the stakeToken is empty in ECM, but if the stakeAmounts are valid, that might be confusing and create some doubts about the validity of such operation. Finally, even if the ECM is updated afterward with a valid stakeToken, that pool would still remain unusable. Since `AssertionStakingPool` enforce in the Rollup contract that stakeToken can't be empty, that validation would not cause any negative impact.

```diff
abstract contract AbsBoldStakingPool is IAbsBoldStakingPool {
    using SafeERC20 for IERC20;

    /// @inheritdoc IAbsBoldStakingPool
    address public immutable stakeToken;
    /// @inheritdoc IAbsBoldStakingPool
    mapping(address => uint256) public depositBalance;

    constructor(address _stakeToken) {
+       if (_stakeToken == address(0)) {
+	    revert EmptyStakeToken();
+	}
+		
        stakeToken = _stakeToken;
    }
```


### PoC
Add the following test `testDeployEmptyStakeToken` in `EdgeChallengeManager.t.sol` and run the test. This demostrate that it's possible to create an EdgeStakingPool based on a ECM that has an empty stakeToken and such pool `can't be used`.

```diff
index 12ba7f0..74011f1 100644
--- a/test/challengeV2/EdgeChallengeManager.t.sol
+++ b/test/challengeV2/EdgeChallengeManager.t.sol
@@ -12,6 +12,7 @@ import "@openzeppelin/contracts/proxy/transparent/TransparentUpgradeableProxy.so
 import "@openzeppelin/contracts/proxy/transparent/ProxyAdmin.sol";
 import "../ERC20Mock.sol";
 import "./StateTools.sol";
+import "../../src/assertionStakingPool/EdgeStakingPoolCreator.sol";

 contract MockOneStepProofEntry is IOneStepProofEntry {
     function getStartMachineHash(bytes32 globalStateHash, bytes32 wasmModuleRoot) external pure returns (bytes32) {
@@ -121,6 +122,40 @@ contract EdgeChallengeManagerTest is Test {
         return (assertionChain, challengeManager, genesisAssertionHash);
     }

+    function testDeployEmptyStakeToken() public {
+        bytes32 edgeId = hex"00010001000100010001000100010001";
+
+        // 1) Deploy EdgeChallengeManager with a address(0) token
+        MockAssertionChain assertionChain = new MockAssertionChain();
+        assertionChain.setValidatorWhitelistDisabled(true);
+        EdgeChallengeManager challengeManagerTemplate = new EdgeChallengeManager();
+        EdgeChallengeManager challengeManager = EdgeChallengeManager(
+            address(new TransparentUpgradeableProxy(address(challengeManagerTemplate), address(new ProxyAdmin()), ""))
+        );
+        uint256[] memory stakeAmounts = miniStakeAmounts();
+
+        challengeManager.initialize(
+            assertionChain,
+            challengePeriodBlock,
+            new MockOneStepProofEntry(),
+            2 ** 5,
+            2 ** 5,
+            2 ** 5,
+            IERC20(address(0)), // <--------------- No staking token
+            excessStakeReceiver,
+            NUM_BIGSTEP_LEVEL,
+            stakeAmounts
+        );
+
+        // 2) Create the EdgeStakingPool
+        EdgeStakingPoolCreator stakingPoolCreator = new EdgeStakingPoolCreator();
+        IEdgeStakingPool stakingPool = stakingPoolCreator.createPool(address(challengeManager), edgeId);
+
+        // 3) Try to deposit into the pool
+        vm.expectRevert("Address: call to non-contract");
+        stakingPool.depositIntoPool(1);
+    }
+
     function testDeployInit() public {
```
https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/assertionStakingPool/AbsBoldStakingPool.sol#L24-L26

### **[ Low - 2 ]** 
This is related to `TOB-ARBCH-31` from the TrailOfBits audit. The fact that `EdgeChallengeManager.sol` is upgradeble, if an Admin would be to upgrade the contract and by mistakes update `stakeToken` and/or `stakeAmounts`, that would result in `catastrophic consequences`, which is why I still want to report this as `Low` by `explaining further` what would go wrong in such case.

## Impacts (stakeAmounts)
An upgrade implying a change in the staking requirement would be problematic (using WETH as stakeToken):

1. `No stake` required --> `100 WETH` stake required: A user which have created a level edge zero before the upgrade might be able to be refunded 100 WETH after the upgrade even if he didn't stake any at the edge creation (see **POC**).
2. `50 WETH` stake required --> `100 WETH` stake required: This is very similar to impact 1. A user which have created a level edge zero before the upgrade might be able to be refunded 100 WETH (instead of his 50 WETH staked), so the difference betweem the new stake requirement `-` the old stake requirement. This `impact is the most realistic` to be happening more often in production.
3. `100 WETH` stake required --> `50 WETH` stake required: A user which have created a level edge zero before the upgrade `will not` be able to get refunded his 100 WETH even if he did stake such amount at the edge creation since now the contract will refund only the new value, which is 50 WETH, so `half` of his original value.
4. `100 WETH` stake required --> `no stake` required: A user which have created a level edge zero before the upgrade `will not` be able to get refunded his 100 WETH even if he did stake such amount at the edge creation since now the contract will **skip** the transfer, so he will get `nothing`.

```solidity
    function refundStake(bytes32 edgeId) public {
        ChallengeEdge storage edge = store.get(edgeId);
        // setting refunded also do checks that the edge cannot be refunded twice
        edge.setRefunded();

        IERC20 st = stakeToken;
        uint256 sa = stakeAmounts[edge.level];
        // no need to refund with the token or amount where zero'd out
        if (address(st) != address(0) && sa != 0) {                                // <------------------------- THIS condition will SKIP the transfer, as identified in the TrailOfBits audit too
            st.safeTransfer(edge.staker, sa);
        }

        emit EdgeRefunded(edgeId, store.edges[edgeId].mutualId(), address(st), sa);
    }
```
## Impacts (stakeToken)
5. `address(0)` --> `WETH`: Same as Impact #1.
6. `WETH` --> `address(0)`: Same as Impact #4.
7. `WETH` --> `WBTC`: This will be ok for direct users, but for pool's user that will be `catastrophic` as switching to a new token would break the staking pool logic (both, assertion and edge) and users partipating in such pool would `lost their entire stake`. The reason is since the `stakeToken` is stored at pool creation (eg: WETH), when `EdgeChallengeManager` get upgraded to a new stakeToken (eg: WBTC), those tokens will still be transfered to the pool's contract when refunding/withdrawing occurs, but they will be `stuck there forever`, as the `safeTransfer` from `withdrawFromPool` will fail, as it will try to transfer the initial token (WETH) while the contract will now own new one (WBTC).
```
    function withdrawFromPool(uint256 amount) public {
        if (amount == 0) {
            revert ZeroAmount();
        }
        uint256 balance = depositBalance[msg.sender];
        if (amount > balance) {
            revert AmountExceedsBalance(msg.sender, amount, balance);
        }

        depositBalance[msg.sender] = balance - amount;
        IERC20(stakeToken).safeTransfer(msg.sender, amount); // <--- THIS will fail as the contract will not own any WETH, but WBTC
        
        emit StakeWithdrawn(msg.sender, amount);
    }
``` 

Be aware that all the mentionned impacts are also affecting `EdgeStakingPool` contract users, which ultimatelly could represent Alice or Bob in the following PoC. There is a twist thought, in case of `Impact #2`, the additional token transfered to EdgeStakingPool would be [stuck in it forever](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/assertionStakingPool/EdgeStakingPool.sol#L19-L21). The reason being that `depositIntoPool` and `withdrawFromPool` will be limited to the amount having being accounted only, so the developer assumption here would be broken.

```
///         Tokens sent directly to this contract will be lost.
///         It is assumed that the challenge manager will not return more tokens than the amount deposited by the pool.
///         Any tokens exceeding the deposited amount to the pool will be stuck in the pool forever.
```

## Proof of Concept
This is showcasing `Impact 1`. We have 3 actors in play: Admin, Alice and Bob.
1) Admin deploy ECM contract `without staking required` to create level zero edge.
2) Alice decide to create a challenge calling `ECM::createLayerZeroEdge`, no token are transfered as it's `stake free`.
3) Afterward (but before Alice challenge is completed), Admin decides to upgrade the contract changing the staking requirement, now `requiring 100 WETH` to create a level zero edge.
4) Bob decide to create a level zero edge for different claim/assertion (so not an Alice's rival edge).
5) Once Alice's challenge period is completed, she is able to confirm his claim, and afterward call `ECM::refundStake`. Even if she haven't staked any token, the ECM will send her back the 100 WETH, and since the contract only own 100 WETH (staked by Bob in the previous step), so effectivelly stealing the Bob's stake. (**user funds loss**)
6) Once Bob has his claim confirmed later on (assuming he wins his claim/assertion too), calling `ECM::refundStake` will be an odd surprise as the call will revert, as the contract will lack funds. (**protocol insolvency**)


## Recommended Mitigation Steps
If an upgrade is required for the `stakeToken and/or stakeAmounts`, normal upgrade `can't` be used, and only a complete upgrade which would also upgrade the proxy (so not re-use the storage) and officialize it with `RollupAdminLogic::setChallengeManager` afterward. That should be `documented very clearly and explicitly` as the current setup as the potential to break things down the road.
https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/challengeV2/EdgeChallengeManager.sol#L429





### **[ Low - 3 ]** 
-----
In `RollupAdminLogic.sol` seems like `_disableInitializers` should be added in the constructor to prevent the contract to be uninitialized as otherwise this open the door for an attacker to take it over.

```diff
contract RollupAdminLogic is RollupCore, IRollupAdmin, DoubleLogicUUPSUpgradeable {
    using AssertionStateLib for AssertionState;

+    constructor() {
+       _disableInitializers();
+    }

    ...
}
```
https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/rollup/RollupAdminLogic.sol#L15


### **[ Low - 4 ]** 
-----
In `EdgeStakingPoolCreator::createPool` you should add the `contract address` in the event as otherwise it can be lost easily. Granted that `getPool` is actually used for that too, but that would be more consistent with `AssertionStakingPoolCreator.sol`. If this was totally intentional, then please ignore.

```diff
    /// @notice Event emitted when a new staking pool is created
-   event NewEdgeStakingPoolCreated(address indexed challengeManager, bytes32 indexed edgeId);
+   event NewEdgeStakingPoolCreated(address indexed challengeManager, bytes32 indexed edgeId, address edgePool);


contract EdgeStakingPoolCreator is IEdgeStakingPoolCreator {
    /// @inheritdoc IEdgeStakingPoolCreator
    function createPool(
        address challengeManager,
        bytes32 edgeId
    ) external returns (IEdgeStakingPool) {
        EdgeStakingPool pool = new EdgeStakingPool{salt: 0}(challengeManager, edgeId);
-       emit NewEdgeStakingPoolCreated(challengeManager, edgeId);
+       emit NewEdgeStakingPoolCreated(challengeManager, edgeId, address(pool)); 
        return pool;
    }
```
https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/assertionStakingPool/EdgeStakingPoolCreator.sol#L20



### **[ NC - 1 ]** 
-----
The first condition in `SequencerInbox::postUpgradeInit` is redundant as already checked in [_setBufferConfig](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/bridge/SequencerInbox.sol#L848).

```diff
    function postUpgradeInit(BufferConfig memory bufferConfig_)
        external
        onlyDelegated
        onlyProxyOwner
    {
-       if (!isDelayBufferable) revert NotDelayBufferable();

        // Assuming we would not upgrade from a version that does not have the buffer initialized
        // If that is the case, postUpgradeInit do not need to be called
        if (buffer.bufferBlocks != 0) {
            revert AlreadyInit();
        }

        _setBufferConfig(bufferConfig_);
    }
```
https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/bridge/SequencerInbox.sol#L166


### **[ NC - 2 ]** 
-----
I think it would be easier to understand the code if you would do the following instead, which should be equivalent. At least `testRevertReduceDepositActive` and  `testRevertWithdrawActiveStake` are still happy with this change.
```diff
    /**
     * @notice Verify that the given staker is not active
     * @param stakerAddress Address to check
     */
    function requireInactiveStaker(address stakerAddress) internal view {
        require(isStaked(stakerAddress), "NOT_STAKED");
        // A staker is inactive if
        // a) their last staked assertion is the latest confirmed assertion
        // b) their last staked assertion have a child
        bytes32 lastestAssertion = latestStakedAssertion(stakerAddress);
        bool isLatestConfirmed = lastestAssertion == latestConfirmed();
-       bool haveChild = getAssertionStorage(lastestAssertion).firstChildBlock > 0;
+       bool isConfirmed = getAssertionStorage(lastestAssertion).status == AssertionStatus.Confirmed;
-       require(isLatestConfirmed || haveChild, "STAKE_ACTIVE");
+       require(isLatestConfirmed || isConfirmed, "STAKE_ACTIVE");

    }
```
https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/rollup/RollupCore.sol#L565-L574


### **[ NC - 3 ]** 
-----
Typo in a comment, "to keep" duplicated.
```diff
        // Fetch a storage reference to prevAssertion since we copied our other one into memory
-       // and we don't have enough stack available to keep to keep the previous storage reference around
+       // and we don't have enough stack available to keep the previous storage reference around

        prevAssertion.childCreated();
```
https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/rollup/RollupCore.sol#L500


### **[[ NC - Out-Of-Scope ]]** 
-----
Even if out-of-scope, I've fixed the following TODO in `Rollup.t.sol::SetUp` which I still want to submit.

```diff
index 3d7d9e6..755aeea 100644
--- a/test/Rollup.t.sol
+++ b/test/Rollup.t.sol
@@ -200,12 +200,9 @@ contract RollupTest is Test {
         });

         address rollupAddr = rollupCreator.createRollup(param);
-        // TODO: fix this
-        // bytes32 rollupSalt = keccak256(abi.encode(config, address(0), new address[](0), false, MAX_DATA_SIZE));
-        // address expectedRollupAddress = Create2Upgradeable.computeAddress(
-        //     rollupSalt, keccak256(type(RollupProxy).creationCode), address(rollupCreator)
-        // );
-        // assertEq(expectedRollupAddress, rollupAddr, "Unexpected rollup address");
+        bytes32 rollupSalt = keccak256(abi.encode(param));
+        address expectedRollupAddress = Create2Upgradeable.computeAddress(rollupSalt, keccak256(type(RollupProxy).creationCode), address(rollupCreator));
+        assertEq(expectedRollupAddress, rollupAddr, "Unexpected rollup address");

         userRollup = RollupUserLogic(address(rollupAddr));
         adminRollup = RollupAdminLogic(address(rollupAddr));
```
https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/test/Rollup.t.sol#L203-L208