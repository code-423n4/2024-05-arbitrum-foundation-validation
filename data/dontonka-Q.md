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


### **[ Low - 3 ]** 
-----
Similar to `TOB-ARBCH-32` from ToB audit. In `RollupUserLogic::addToDeposit` there is no validation for tokenAmount, thus `tokenAmount == 0` is possible, which allow user to waste gas for nothing. The same pattern apply for `RollupUserLogic::reduceDeposit`.

```diff
    function addToDeposit(address stakerAddress, uint256 tokenAmount) external onlyValidator whenNotPaused {
        _addToDeposit(stakerAddress, tokenAmount);
        /// @dev This is an external call, safe because it's at the end of the function
        receiveTokens(tokenAmount);
    }
```

Add the following test in `Rollup.t.sol` and it will pass.

```solidity
    function testSuccessAddToDepositZeroAmount() public {
        testSuccessConfirmEdgeByTime();
        vm.prank(validator1);
        userRollup.addToDeposit(validator1, 0);
    }
```
https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/rollup/RollupUserLogic.sol#L349-L353


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