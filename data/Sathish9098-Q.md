## QA REPORT

##

## [L-]  Risk of Confirming Assertion Prematurely if ``totalTimeUnrivaled`` Equals ``confirmationThresholdBlock``

The current check if (totalTimeUnrivaled < confirmationThresholdBlock) only reverts when totalTimeUnrivaled is strictly less than confirmationThresholdBlock. This means that if totalTimeUnrivaled is exactly equal to confirmationThresholdBlock, the condition is not met, and the code proceeds without reverting.

However, in the context of confirming assertions, this can be problematic. If the totalTimeUnrivaled is exactly equal to confirmationThresholdBlock, it implies that the confirmationThresholdBlock has not been fully passed yet. To ensure that the assertion is confirmed only after the required confirmation blocks have fully passed, the check should also include the case where totalTimeUnrivaled is equal to confirmationThresholdBlock.


```solidity
FILE:2024-05-arbitrum-foundation/src/challengeV2/libraries/EdgeChallengeManagerLib.sol

if (totalTimeUnrivaled < confirmationThresholdBlock) {
            revert InsufficientConfirmationBlocks(totalTimeUnrivaled, confirmationThresholdBlock);
        }

```
https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/challengeV2/libraries/EdgeChallengeManagerLib.sol#L741-L743

### Recommended Mitigation

```diff
- if (totalTimeUnrivaled < confirmationThresholdBlock) {
+ if (totalTimeUnrivaled <= confirmationThresholdBlock) {
            revert InsufficientConfirmationBlocks(totalTimeUnrivaled, confirmationThresholdBlock);
        }
```

##

## [L-] ``if (whitelistEnabled and not assertionChain.isValidator(msg.sender)) {``  check only allow other addresses creating edge if validatorWhitelistDisabled is set to true breaks the permission less concept as docs

if validatorWhitelistDisabled is true, the requirement to be on the validator list (isValidator[msg.sender]) is bypassed, allowing any address to act as a validator. However, if validatorWhitelistDisabled is false, then the address must be explicitly listed as a validator in isValidator to pass the check. This breaks the permission less concept as per docs.

```solidity
FILE:  

if (whitelistEnabled && !assertionChain.isValidator(msg.sender)) {
            revert NotValidator(msg.sender);
        }

```  
https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/challengeV2/EdgeChallengeManager.sol#L376-L378

##

## [L-] ``onlyOwner`` can block any validator from creating new assertions and new edges once ``isValidator`` is set to false without reason

The function setValidator allows the owner to set the validation status of multiple addresses. If a validator's status is suddenly set to false, it can impact the functions that rely on the isValidator status. Not possible to create new assertions and edges even they staked enough.

```solidity
FILE: 2024-05-arbitrum-foundation/src/rollup/RollupAdminLogic.sol

function setValidator(address[] calldata _validator, bool[] calldata _val) external override {
        require(_validator.length > 0, "EMPTY_ARRAY");
        require(_validator.length == _val.length, "WRONG_LENGTH");

        for (uint256 i = 0; i < _validator.length; i++) {
            isValidator[_validator[i]] = _val[i];
        }
        emit OwnerFunctionCalled(6);
    }

```
https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/rollup/RollupAdminLogic.sol#L180-L188

##

## [L-] ``newStakeOnNewAssertion`` function will revert when normal user called when ``validatorWhitelistDisabled`` is false  

The ``newStakeOnNewAssertion()`` function is declared as a public function, meaning that anyone can call this function to stake and create a new assertion. However, the ``stakeOnNewAssertion()`` function is only called by validators or when ``validatorWhitelistDisabled`` is set to true. This means that when normal users call this function, it reverts. 

```solidity
FILE: 2024-05-arbitrum-foundation/src/rollup/RollupUserLogic.sol

 function newStakeOnNewAssertion(
        uint256 tokenAmount,
        AssertionInputs calldata assertion,
        bytes32 expectedAssertionHash,
        address withdrawalAddress
    ) public {
        require(withdrawalAddress != address(0), "EMPTY_WITHDRAWAL_ADDRESS");
        _newStake(tokenAmount, withdrawalAddress);
        stakeOnNewAssertion(assertion, expectedAssertionHash);
        /// @dev This is an external call, safe because it's at the end of the function
        receiveTokens(tokenAmount);
    } 

```
https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/rollup/RollupUserLogic.sol#L331-L342

### Recommended Mitigation
Add onlyValidator Modifier to newStakeOnNewAssertion() function

```diff
 function newStakeOnNewAssertion(
        uint256 tokenAmount,
        AssertionInputs calldata assertion,
        bytes32 expectedAssertionHash,
        address withdrawalAddress
-    ) public {
+    ) public { onlyValidator
        require(withdrawalAddress != address(0), "EMPTY_WITHDRAWAL_ADDRESS");
        _newStake(tokenAmount, withdrawalAddress);
        stakeOnNewAssertion(assertion, expectedAssertionHash);
        /// @dev This is an external call, safe because it's at the end of the function
        receiveTokens(tokenAmount);
    } 

```

##

## [L-] ``mandatoryBisectionHeight()`` not return expected results

### Expected Result
The documentation states: ``Returns the highest power of 2 in the differing lower bits of start and end.`` This means the function should identify the highest power of 2 in the bits where start and end differ.

### Actual Result
 The function does not return the highest power of 2 in the differing lower bits; rather, it uses the most significant differing bit to create a mask and apply it to (end - 1). 

```solidity
FILE: 2024-05-arbitrum-foundation/src/challengeV2/libraries
/EdgeChallengeManagerLib.sol 

 function mandatoryBisectionHeight(uint256 start, uint256 end) internal pure returns (uint256) {
        if (end - start < 2) {
            revert HeightDiffLtTwo(start, end);
        }
        if (end - start == 2) {
            return start + 1;
        }

        uint256 diff = (end - 1) ^ start;
        uint256 mostSignificantSharedBit = UintUtilsLib.mostSignificantBit(diff);
        uint256 mask = type(uint256).max << mostSignificantSharedBit;
        return ((end - 1) & mask);
    }

```
https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/challengeV2/libraries/EdgeChallengeManagerLib.sol#L574-L588

##

## [L-1] ``expectedAssertionHash == bytes32(0) || getAssertionStorage(expectedAssertionHash).status == AssertionStatus.NoAssertion`` condition check is still vulnerable to reorg issues

Tts associated check for expectedAssertionHash aim to protect against certain issues that may arise from blockchain reorganizations (reorgs). However, despite these precautions, there can still be vulnerabilities.

- During a reorg, transactions can be reordered or included in different blocks. If a transaction that creates an assertion with a specific ``expectedAssertionHash`` is reprocessed after a reorg, the check might fail to recognize that the assertion was already processed, leading to inconsistent states or duplicate processing.

- Simultaneous transactions across competing chains can create race conditions, where multiple transactions with the same expectedAssertionHash are processed in different forks.

```solidity
FILE: 2024-05-arbitrum-foundation/src/rollup/RollupUserLogic.sol

// Early revert on duplicated assertion if expectedAssertionHash is set
        require(
            expectedAssertionHash == bytes32(0)
                || getAssertionStorage(expectedAssertionHash).status == AssertionStatus.NoAssertion,
            "EXPECTED_ASSERTION_SEEN"
        );


```
https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/rollup/RollupUserLogic.sol#L169-L173

##

## [L-2] Misleading comment in setOutbox() function

The current comment indicates that the function is adding a contract authorized to put messages into the rollup's inbox, but the function itself is setting an outbox contract and registering it with the bridge, rather than directly dealing with the inbox.

```solidity
FILE: 2024-05-arbitrum-foundation/src/rollup/RollupAdminLogic.sol

/**
     * @notice Add a contract authorized to put messages into this rollup's inbox
     * @param _outbox Outbox contract to add
     */
    function setOutbox(IOutbox _outbox) external override {
        outbox = _outbox;
        bridge.setOutbox(address(_outbox), true);
        emit OwnerFunctionCalled(0);
    }

```
https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/rollup/RollupAdminLogic.sol#L113-L121

### Recommended Mitigation
Here's a revised version of the comment to more accurately reflect the function's purpose.

```solidity
/**
 * @notice Set the outbox contract for the rollup and authorize it on the bridge
 * @param _outbox The outbox contract to be set and authorized
 */
function setOutbox(IOutbox _outbox) external override {
    outbox = _outbox;
    bridge.setOutbox(address(_outbox), true);
    emit OwnerFunctionCalled(0);
}

```

##

## [L-3] ``args.level`` value exceeds 255 then ``createLayerZeroEdge()`` function reverts 

args.level is uint8 type this can be accept the values up to 0-255. But if we add the 255 then this function reverts.

```solidity
FILE: 2024-05-arbitrum-foundation/src/challengeV2/EdgeChallengeManager.sol 

381: EdgeType eType = ChallengeEdgeLib.levelToType(args.level, NUM_BIGSTEP_LEVEL); 

```
https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/challengeV2/EdgeChallengeManager.sol#L381

### Recommendation

Clearly document the input ranges 

```diff

+ // args.level values should be 0-254 
EdgeType eType = ChallengeEdgeLib.levelToType(args.level, NUM_BIGSTEP_LEVEL);

```

##

## [L-] ``if (address(st) != address(0) && sa != 0) {``  current implementation allows all erc20 tokens which breaks the docs   

```
it is assumed to be WETH or a token that is not fee-on-transfer, rebasing, have a transfer hook or otherwise have non-standard ERC20 logics.

```

This are all the tokens allowed while staking but current implementation allow all ERC20 tokens without checks.

```solidity
FILE: Breadcrumbs2024-05-arbitrum-foundation/src/challengeV2
/EdgeChallengeManager.sol

 IERC20 st = stakeToken;
        uint256 sa = stakeAmounts[args.level];
        // when a zero layer edge is created it must include stake amount. Each time a zero layer
        // edge is created it forces the honest participants to do some work, so we want to disincentive
        // their creation. The amount should also be enough to pay for the gas costs incurred by the honest
        // participant. This can be arranged out of bound by the excess stake receiver.
        // The contract initializer can disable staking by setting zeros for token or amount, to change
        // this a new challenge manager needs to be deployed and its address updated in the assertion chain
        if (address(st) != address(0) && sa != 0) {

```
https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/challengeV2/EdgeChallengeManager.sol#L421-L429

##

## [L-] ``if (ard.assertionHash != args.claimId) {`` Potentially Redundant Check Between assertionHash and claimId in ``layerZeroTypeSpecificChecks() `` function

There is no possibility that values are different. ``args.claimId`` value only assigned to ``ard.assertionHash`` when creating ``ard`` variable .


```solidity
FILE: Breadcrumbs2024-05-arbitrum-foundation/src/challengeV2
/EdgeChallengeManager.sol

 ard = AssertionReferenceData(
                args.claimId,
                claimStateData.prevAssertionHash,
                assertionChain.isPending(args.claimId),
                assertionChain.getSecondChildCreationBlock(claimStateData.prevAssertionHash) > 0,
                predecessorStateData.assertionState,
                claimStateData.assertionState
            );

```
https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/challengeV2/EdgeChallengeManager.sol#L409

```solidity
FILE: 2024-05-arbitrum-foundation/src/challengeV2/libraries
/EdgeChallengeManagerLib.sol


if (ard.assertionHash != args.claimId) {
                revert AssertionHashMismatch(ard.assertionHash, args.claimId);
            }

```
https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/challengeV2/libraries/EdgeChallengeManagerLib.sol#L232-L234

##

## [L-] Incorrect Comment Describing Execution State Check in layerZeroTypeSpecificChecks() Function

```solidity
FILE:2024-05-arbitrum-foundation/src/challengeV2/libraries
/EdgeChallengeManagerLib.sol

// check the start and end execution states exist, the block hash entry should be non zero
            if (ard.startState.machineStatus == MachineStatus.RUNNING) {
                revert EmptyStartMachineStatus();
            }
            if (ard.endState.machineStatus == MachineStatus.RUNNING) {
                revert EmptyEndMachineStatus();
            }

```

This comment suggests that the check is verifying the existence of the start and end execution states and implies something about block hash entries, which is not what the code does.

### Recommended Mitigation

Add appropriate comments

```solidity
// Check that the start and end execution states are not running
// The machine status should not be 'RUNNING' for either the start or end state
            if (ard.startState.machineStatus == MachineStatus.RUNNING) {
                revert EmptyStartMachineStatus();
            }
            if (ard.endState.machineStatus == MachineStatus.RUNNING) {
                revert EmptyEndMachineStatus();
            }


```

##

## [L-] Incorrect Zero Value Check for ``bytes32`` Type in ``layerZeroTypeSpecificChecks()`` Function

Using if (ard.assertionHash == 0) to check if a bytes32 value is zero can lead to incorrect behavior or revert errors because 0 is implicitly treated as a uint256, not a bytes32. Comparing a bytes32 directly to a uint256 will likely result unintended behavior if the compiler allows it.

```solidity
FILE: 2024-05-arbitrum-foundation/src/challengeV2/libraries
/EdgeChallengeManagerLib.sol

229: if (ard.assertionHash == 0) { 

```
https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/challengeV2/libraries/EdgeChallengeManagerLib.sol#L229

### Recommended Mitigation

```solidity

229: if (ard.assertionHash == bytes32(0)) { 

```

##

## [L-] ``mandatoryBisectionHeight(ce.startHeight, ce.endHeight)`` function will revert in some cases instead of returning ``middleHeight`` value

The function reverts if end - start < 2. This means that for very close values of start and end (where the difference is less than 2), the function will not compute a bisection height but will instead revert with an error.

```solidity
FILE: 2024-05-arbitrum-foundation/src/challengeV2/libraries
/EdgeChallengeManagerLib.sol

 /// @notice Given a start and an endpoint determine the bisection height
    /// @dev    Returns the highest power of 2 in the differing lower bits of start and end
    function mandatoryBisectionHeight(uint256 start, uint256 end) internal pure returns (uint256) {
        if (end - start < 2) {
            revert HeightDiffLtTwo(start, end);
        }
        if (end - start == 2) {
            return start + 1;
        }

        uint256 diff = (end - 1) ^ start;
        uint256 mostSignificantSharedBit = UintUtilsLib.mostSignificantBit(diff);
        uint256 mask = type(uint256).max << mostSignificantSharedBit;
        return ((end - 1) & mask);
    }

```
https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/challengeV2/libraries/EdgeChallengeManagerLib.sol#L574-L588


##

## [L-] if (totalTimeUnrivaled < confirmationThresholdBlock) { Mismatched comparisons(uitn256 type with uint64)

The mismatched comparison between totalTimeUnrivaled (which is uint256) and confirmationThresholdBlock (which is uint64).

```solidity
FILE:2024-05-arbitrum-foundation/src/challengeV2/libraries
/EdgeChallengeManagerLib.sol

if (totalTimeUnrivaled < confirmationThresholdBlock) {
            revert InsufficientConfirmationBlocks(totalTimeUnrivaled, confirmationThresholdBlock);
        }

```
https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/challengeV2/libraries/EdgeChallengeManagerLib.sol#L741-L743

## [L-] 








