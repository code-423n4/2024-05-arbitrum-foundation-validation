## L-01 - [function multiUpdateTimeCacheByChildren](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/challengeV2/EdgeChallengeManager.sol#L491-L496)
```solidity
    function multiUpdateTimeCacheByChildren(bytes32[] calldata edgeIds) public {
        for (uint256 i = 0; i < edgeIds.length; i++) {
            (bool updated, uint256 newValue) = store.updateTimerCacheByChildren(edgeIds[i]);
            if (updated) emit TimerCacheUpdated(edgeIds[i], newValue);
        }
    }
```

**Use a more descriptive variable name for `sa`:** The variable name `sa` is not very descriptive, making it harder to understand what it represents. Consider using a more meaningful name like `stakeAmount` or `edgeStakeAmount`.

```solidity
uint256 stakeAmount = stakeAmounts[edge.level];
```
This improves code readability and maintainability.

**Consider using a modifier or a separate function for input validation:** The code currently checks if the `stakeToken` address and `stakeAmount` are non-zero before transferring the stake. This logic could be extracted into a modifier or a separate function to improve code organization and reusability.

```solidity
modifier validStake(uint256 level) {
    IERC20 st = stakeToken;
    uint256 sa = stakeAmounts[level];
    require(address(st) != address(0) && sa != 0, "Invalid stake");
    _;
}

function refundStake(bytes32 edgeId) public validStake(edge.level) {
    // ...
}
```
This separation of concerns improves code maintainability and makes it easier to reason about the code's behavior.

**Consider using a more gas-efficient way to check for non-zero addresses:** Instead of checking `address(st) != address(0)`, you can use the more gas-efficient `st.code.length > 0` to check if the address is a contract address.

```solidity
if (st.code.length > 0 && sa != 0) {
    st.safeTransfer(edge.staker, sa);
}
```
This optimization can lead to gas savings, especially in scenarios where the function is called frequently.

**Consider using a more descriptive event name:** The event name `EdgeRefunded` could be more descriptive to better convey the purpose of the event. For example, `StakeRefunded` or `EdgeChallengeStakeRefunded` might be more appropriate.

```solidity
emit StakeRefunded(edgeId, store.edges[edgeId].mutualId(), address(st), sa);
```
This improves code readability and makes it easier to understand the purpose of the event.

**Consider adding input validation for `edgeId`:** The function currently assumes that `edgeId` is a valid identifier for an existing edge in the `store`. Adding input validation to ensure the edge exists and can be refunded would improve the code's robustness and security.

```solidity
function refundStake(bytes32 edgeId) public {
    require(store.exists(edgeId), "Edge does not exist");
    ChallengeEdge storage edge = store.get(edgeId);
    require(!edge.isRefunded(), "Edge already refunded");
    // ...
}
```
This input validation helps prevent potential errors and vulnerabilities caused by invalid or malicious input.

## L-02 [function setAnyTrustFastConfirmer](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/rollup/RollupAdminLogic.sol#L317-L320)

Any external account or contract can call this function and set the `anyTrustFastConfirmer` address.

If an unauthorized party sets an incorrect or malicious address, it could disrupt the fast confirmation process or potentially enable attacks on the Rollup protocol.

**Consider:** adding the `onlyOwner` modifier, only the contract owner (or an authorized admin role) can update this critical address, mitigating the risk of unauthorized modifications.

**Input Validation:**

If the `_anyTrustFastConfirmer` parameter is not validated, it is possible to set the address to `address(0)` (the zero address), which is often considered an invalid address in Solidity contracts.
Assigning the zero address to `anyTrustFastConfirmer` could lead to unexpected behavior or errors when interacting with this address, potentially breaking the fast confirmation process.

Validating the input address ensures that a valid, non-zero address is assigned, enhancing the contract's robustness and preventing accidental or malicious assignment of an invalid address.

**Event Parameter:**

The current implementation emits a `hardcoded value (31)` in the event, which may not provide meaningful information for off-chain monitoring or debugging purposes.
By including the new `_anyTrustFastConfirmer` address as a parameter in the event, it provides valuable information about the specific address that was set, enhancing transparency and auditability.
This additional information can be useful for tracking changes to the `anyTrustFastConfirmer` address, enabling better monitoring and debugging capabilities.

## L-03: [Assertion.sol](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/rollup/Assertion.sol)

**Use of Solidity's built-in `block.number` type:** Instead of casting `block.number` to `uint64`, use the built-in `uint` type, which is an alias for `uint256`. This would eliminate the need for explicit casting and improve code readability.

```solidity
assertion.createdAtBlock = block.number;
self.firstChildBlock = block.number;
self.secondChildBlock = block.number;
```

**Consider using a mapping for child blocks:** Instead of using separate variables for `firstChildBlock` and `secondChildBlock`, use a mapping to store child block numbers.

This would make the code more extensible and easier to maintain if you need to support more than two children in the future.

```solidity
mapping(uint => uint) public childBlocks;

function childCreated(AssertionNode storage self) internal {
    uint childCount = self.childBlocks.length;
    self.childBlocks[childCount] = block.number;
}
```

**Use a more descriptive error message:** The error message [`"ASSERTION_NOT_EXIST"`](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/rollup/Assertion.sol#L94) could be more descriptive and informative. Consider providing a more detailed error message that explains the context and the reason for the error.

```solidity
function requireExists(AssertionNode memory self) internal pure {
    require(self.status != AssertionStatus.NoAssertion, "The assertion does not exist or has been removed.");
}
```

**Implement input validation:** 
```solidity
    function createAssertion(
        bool _isFirstChild,
        bytes32 _configHash
    ) internal view returns (AssertionNode memory) {
        AssertionNode memory assertion;
        assertion.createdAtBlock = uint64(block.number);
        assertion.isFirstChild = _isFirstChild;
        assertion.configHash = _configHash;
        assertion.status = AssertionStatus.Pending;
        return assertion;
    }
```
The [createAssertion](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/rollup/Assertion.sol#L70-L80) function does not validate the input parameters `_isFirstChild` and `_configHash`.

Consider adding input validation to ensure that the function behaves correctly and prevents potential security vulnerabilities.

```solidity
function createAssertion(
    bool _isFirstChild,
    bytes32 _configHash
) internal view returns (AssertionNode memory) {
    require(_configHash != bytes32(0), "Invalid config hash");

    // ... (rest of the function)
}
```

**Use events for better transparency and auditability:** Consider emitting events when important state changes occur, such as when an assertion is created or updated. Events can provide better transparency and auditability for off-chain monitoring and analysis.

```solidity
event AssertionCreated(uint assertionId, bool isFirstChild, bytes32 configHash);

function createAssertion(
    bool _isFirstChild,
    bytes32 _configHash
) internal view returns (AssertionNode memory) {
    // ... (create assertion)

    emit AssertionCreated(assertionId, _isFirstChild, _configHash);
    return assertion;
}
```

## L-04 [function calcBuffer](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/bridge/DelayBuffer.sol#L33-L63)

```solidity
    function calcBuffer(
        uint256 start,
        uint256 end,
        uint256 buffer,
        uint256 sequenced,
        uint256 threshold,
        uint256 max,
        uint256 replenishRateInBasis
    ) internal pure returns (uint256) {
        uint256 elapsed = end > start ? end - start : 0;
        uint256 delay = sequenced > start ? sequenced - start : 0;
        // replenishment rounds down and will not overflow since all inputs including
        // replenishRateInBasis are cast from uint64 in calcPendingBuffer
        buffer += (elapsed * replenishRateInBasis) / BASIS;


        uint256 unexpectedDelay = delay > threshold ? delay - threshold : 0;
        if (unexpectedDelay > elapsed) {
            unexpectedDelay = elapsed;
        }


        // decrease the buffer
        if (buffer > unexpectedDelay) {
            buffer -= unexpectedDelay;
            if (buffer > threshold) {
                // saturating above at the max
                return buffer > max ? max : buffer;
            }
        }
        // saturating below at the threshold
        return threshold;
    }
```

**Consider Refactoring for Readability:** The nested `if` statements and the ternary operator used for calculating `unexpectedDelay` could be refactored to improve readability. For example, the ternary operator could be replaced with an `if-else` statement, and the nested `if` statements could be split into separate functions or methods.

**Benefit:** Improved readability can make the code easier to understand and maintain, especially for complex logic.

This applies to the nested `if` statements and the ternary operator used for calculating `unexpectedDelay` within the `calcBuffer` function.

**Validate Input Parameters:** While the function is marked as `pure`, it might be a good practice to validate the input parameters to ensure they are within expected ranges. This could help catch potential issues early and prevent unexpected behavior.

**Benefit:** Input validation can help catch errors early and improve the overall robustness and reliability of the code.

This applies to the input parameters of the `calcBuffer` function, such as start, end, buffer, sequenced, threshold, max, and `replenishRateInBasis`.

**Consider Using SafeMath:** Although the code includes a comment stating that overflow is not possible, it might be a good practice to use `SafeMath` or similar libraries to ensure that arithmetic operations are safe and do not overflow or underflow.

**Benefit:** Using SafeMath or similar libraries can help prevent potential arithmetic errors and improve the overall security and reliability of the code.

This suggestion applies to the arithmetic operations performed within the `calcBuffer` function, specifically the addition and subtraction operations involving the buffer variable.

**Separating Buffer Calculation Logic:**

Separating the buffer calculation logic into a separate function would improve modularity and reusability. It would also make the code easier to understand and maintain, as the logic would be clearly defined in a single location.

**Example:**

```solidity
function calculateBuffer(uint256 start, uint256 end, ... /* other parameters */) public view returns (uint256) {
    // Buffer calculation logic here
}

function update(BufferData storage self, uint64 blockNumber) internal {
    self.bufferBlocks = calculateBuffer(
        self.prevBlockNumber,
        blockNumber,
        ... /* other parameters */
    );
    // ... other code
}
```

**Impact of Using Type Safety:**

Using `uint256` for all buffer-related variables would prevent overflow vulnerabilities. This is important because buffer values can become large, and overflowing could lead to unexpected results or errors.

**Impact of Using a Constant for Threshold:**

Defining a constant for the threshold value would improve readability and maintainability. It would also make it would be helpful to verify the current state.

## L-05 [function _validatorIsAfk()](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/rollup/RollupUserLogic.sol#L51-L60)

```solidity
    function _validatorIsAfk() internal view returns (bool) {
        AssertionNode memory latestConfirmedAssertion = getAssertionStorage(latestConfirmed());
        if (latestConfirmedAssertion.createdAtBlock == 0) return false;
        // We consider the validator is gone if the last known assertion is older than VALIDATOR_AFK_BLOCKS
        // Which is either the latest confirmed assertion or the first child of the latest confirmed assertion
        if (latestConfirmedAssertion.firstChildBlock > 0) {
            return latestConfirmedAssertion.firstChildBlock + VALIDATOR_AFK_BLOCKS < block.number;
        }
        return latestConfirmedAssertion.createdAtBlock + VALIDATOR_AFK_BLOCKS < block.number;
    }
```
**Early Return:** Instead of using an `if` statement to check for the base case (`latestConfirmedAssertion.createdAtBlock == 0`) and then continuing with the rest of the logic, you could return early in the base case. This can slightly improve readability and performance by avoiding unnecessary computations.

```solidity
if (latestConfirmedAssertion.createdAtBlock == 0) return false;
// Rest of the logic
```
**Benefit:** Improved code readability and potentially slightly better performance.

**Consistent Formatting:** While the code formatting is generally consistent, _there is a slight inconsistency in the spacing around the `+` operator in the last two lines._ It would be better to have consistent spacing throughout the code.

**Benefit:** Improved code readability and maintainability.

**Optimization:** Depending on the frequency of calls to this function and the size of the `AssertionNode` struct, it might be worth considering caching the `latestConfirmedAssertion` value to avoid redundant computations. However, this optimization should be carefully evaluated against the potential trade-offs, such as increased code complexity and memory usage.

**Benefit:** Improved performance, especially if the function is called frequently.

## L-06 [function confirmAssertion](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/rollup/RollupUserLogic.sol#L82-L131)

```solidity
    function confirmAssertion(
        bytes32 assertionHash,
        bytes32 prevAssertionHash,
        AssertionState calldata confirmState,
        bytes32 winningEdgeId,
        ConfigData calldata prevConfig,
        bytes32 inboxAcc
    ) external onlyValidator whenNotPaused {
        /*
        * To confirm an assertion, the following must be true:
        * 1. The assertion must be pending
        * 2. The assertion's deadline must have passed
        * 3. The assertion's prev must be latest confirmed
        * 4. The assertion's prev's child confirm deadline must have passed
        * 5. If the assertion's prev has more than 1 child, the assertion must be the winner of the challenge
        *
        * Note that we do not need to ever reject invalid assertion because they can never confirm
        *      and the stake on them is swept to the loserStakeEscrow as soon as the leaf is created
        */


        // The assertion's must exists and be pending and will be validated in RollupCore.confirmAssertionInternal
        AssertionNode storage assertion = getAssertionStorage(assertionHash);


        // prevAssertionHash is user supplied, but will be validated in RollupCore.confirmAssertionInternal
        AssertionNode storage prevAssertion = getAssertionStorage(prevAssertionHash);
        RollupLib.validateConfigHash(prevConfig, prevAssertion.configHash);


        // Check that deadline has passed
        require(block.number >= assertion.createdAtBlock + prevConfig.confirmPeriodBlocks, "BEFORE_DEADLINE");


        // Check that prev is latest confirmed
        require(prevAssertionHash == latestConfirmed(), "PREV_NOT_LATEST_CONFIRMED");


        if (prevAssertion.secondChildBlock > 0) {
            // if the prev has more than 1 child, check if this assertion is the challenge winner
            ChallengeEdge memory winningEdge = IEdgeChallengeManager(prevConfig.challengeManager).getEdge(winningEdgeId);
            require(winningEdge.claimId == assertionHash, "NOT_WINNER");
            require(winningEdge.status == EdgeStatus.Confirmed, "EDGE_NOT_CONFIRMED");
            require(winningEdge.confirmedAtBlock != 0, "ZERO_CONFIRMED_AT_BLOCK");
            // an additional number of blocks is added to ensure that the result of the challenge is widely
            // observable before it causes an assertion to be confirmed. After a winning edge is found, it will
            // always be challengeGracePeriodBlocks before an assertion can be confirmed
            require(
                block.number >= winningEdge.confirmedAtBlock + challengeGracePeriodBlocks,
                "CHALLENGE_GRACE_PERIOD_NOT_PASSED"
            );
        }


        confirmAssertionInternal(assertionHash, prevAssertionHash, confirmState, inboxAcc);
    }
```
**Use Modifiers for Repetitive Checks:** The function checks for several conditions, such as `block.number` being greater than certain values. _These checks could be extracted into modifiers to improve code readability and reusability._

**Improve Error Messages:** Some error messages, like `"BEFORE_DEADLINE"`, are not very descriptive. _More informative error messages would make it easier to debug issues._

**Avoid Unnecessary Storage Reads:** The function reads from storage multiple times for the same variables (`assertion` and `prevAssertion`). _It would be more gas-efficient to cache these values in memory to avoid redundant storage reads._

**Use Events for Better Observability:** The function does not emit any events, which can make it harder to track and monitor important state changes. _Adding events for critical operations, like assertion confirmation, would improve the observability and auditability of the contract._

## L-07: [function _newStake](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/rollup/RollupUserLogic.sol#L137-L142)

```solidity
    function _newStake(uint256 depositAmount, address withdrawalAddress) internal onlyValidator whenNotPaused {
        // Verify that sender is not already a staker
        require(!isStaked(msg.sender), "ALREADY_STAKED");
        // amount will be checked when creating an assertion
        createNewStake(msg.sender, depositAmount, withdrawalAddress);
    }
```
**Consider using a modifier for the `isStaked` check:** Instead of checking `isStaked` inside the function, you could create a modifier `onlyNotStaked` and apply it to the function. This would separate the concern of checking the staking status from the main functionality of creating a new stake.

**Benefit:** _Better separation of concerns and code organization._

Use a more specific error message: The error message `"ALREADY_STAKED"` could be more specific by including the address of the staker. For example, `"ALREADY_STAKED: {msg.sender}"`.

**Benefit:** Better error handling and debugging.

**Consider adding input validation:** While the depositAmount is checked when creating an assertion, it might be a good practice to validate the input parameters within the _newStake function as well. This could include checking if depositAmount is greater than zero and if withdrawalAddress is a valid address.

**Benefit:** Improved input validation and security.

## L-08: [function stakeOnNewAssertion](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/rollup/RollupUserLogic.sol#L163-L217)

```solidity
    function stakeOnNewAssertion(AssertionInputs calldata assertion, bytes32 expectedAssertionHash)
        public
        onlyValidator
        whenNotPaused
    {
        // Early revert on duplicated assertion if expectedAssertionHash is set
        require(
            expectedAssertionHash == bytes32(0)
                || getAssertionStorage(expectedAssertionHash).status == AssertionStatus.NoAssertion,
            "EXPECTED_ASSERTION_SEEN"
        );


        require(isStaked(msg.sender), "NOT_STAKED");


        // requiredStake is user supplied, will be verified against configHash later
        // the prev's requiredStake is used to make sure all children have the same stake
        // the staker may have more than enough stake, and the entire stake will be locked
        // we cannot do a refund here because the staker may be staker on an unconfirmed ancestor that requires more stake
        // excess stake can be removed by calling reduceDeposit when the staker is inactive
        require(amountStaked(msg.sender) >= assertion.beforeStateData.configData.requiredStake, "INSUFFICIENT_STAKE");


        bytes32 prevAssertion = RollupLib.assertionHash(
            assertion.beforeStateData.prevPrevAssertionHash,
            assertion.beforeState,
            assertion.beforeStateData.sequencerBatchAcc
        );
        getAssertionStorage(prevAssertion).requireExists();


        // Staker can create new assertion only if
        // a) its last staked assertion is the prev; or
        // b) its last staked assertion have a child
        bytes32 lastAssertion = latestStakedAssertion(msg.sender);
        require(
            lastAssertion == prevAssertion || getAssertionStorage(lastAssertion).firstChildBlock > 0,
            "STAKED_ON_ANOTHER_BRANCH"
        );


        (bytes32 newAssertionHash, bool overflowAssertion) =
            createNewAssertion(assertion, prevAssertion, expectedAssertionHash);
        _stakerMap[msg.sender].latestStakedAssertion = newAssertionHash;


        if (!overflowAssertion) {
            uint256 timeSincePrev = block.number - getAssertionStorage(prevAssertion).createdAtBlock;
            // Verify that assertion meets the minimum Delta time requirement
            require(timeSincePrev >= minimumAssertionPeriod, "TIME_DELTA");
        }


        if (!getAssertionStorage(newAssertionHash).isFirstChild) {
            // We assume assertion.beforeStateData is valid here as it will be validated in createNewAssertion
            // only 1 of the children can be confirmed and get their stake refunded
            // so we send the other children's stake to the loserStakeEscrow
            // NOTE: if the losing staker have staked more than requiredStake, the excess stake will be stuck
            IERC20(stakeToken).safeTransfer(loserStakeEscrow, assertion.beforeStateData.configData.requiredStake);
        }
    }
```

**Improve Error Handling:** Instead of using `require` statements with error messages, consider using custom errors and reverting with more descriptive error messages. This can save gas and provide better debugging information.

**Optimize Gas Usage:** Some operations in the function, such as the `getAssertionStorage` and `latestStakedAssertion` calls, may be gas-intensive, especially if they involve storage reads or writes. _Consider caching frequently accessed data or optimizing these operations to reduce gas costs._

**Use Events for Logging:** The function does not emit any events, which can make it difficult to track and monitor important state changes. _Consider emitting events for significant actions, such as creating a new assertion or transferring stakes, to improve transparency and auditability._

## L-09: [function fastConfirmAssertion](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/rollup/RollupUserLogic.sol#L252-L261)

```solidity
    ) public whenNotPaused {
        require(msg.sender == anyTrustFastConfirmer, "NOT_FAST_CONFIRMER");
        // this skip deadline, prev, challenge validations
        confirmAssertionInternal(assertionHash, parentAssertionHash, confirmState, inboxAcc);
    }
```
Instead of checking the `msg.sender` against `anyTrustFastConfirmer` within the function, consider using an access control modifier to enforce this restriction at the function level. This would make the code more concise and easier to maintain.

**Error Handling:** The error message `"NOT_FAST_CONFIRMER"` could be more descriptive and provide more context about the specific error condition. For example, `"CALLER_NOT_AUTHORIZED_FOR_FAST_CONFIRMATION"` would be more informative.

## L-10: [function fastConfirmAssertion](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/rollup/RollupUserLogic.sol#L252C5-L261)

```solidity
    function fastConfirmAssertion(
        bytes32 assertionHash,
        bytes32 parentAssertionHash,
        AssertionState calldata confirmState,
        bytes32 inboxAcc
    ) public whenNotPaused {
        require(msg.sender == anyTrustFastConfirmer, "NOT_FAST_CONFIRMER");
        // this skip deadline, prev, challenge validations
        confirmAssertionInternal(assertionHash, parentAssertionHash, confirmState, inboxAcc);
    }
```
**Validate Input Parameters:** The function does not validate the input parameters `tokenAmount` and `assertion`. It would be a good practice to add input validation checks to ensure that the provided values are within expected ranges and meet any other necessary constraints.

**Benefits:** Improved input validation, better error handling, and increased robustness against potential vulnerabilities.

**Use Modifiers or Guards:** Instead of checking the `withdrawalAddress` condition at the beginning of the function, consider using a modifier or a guard clause to enforce this condition. This can improve code readability and make the function's intent more explicit.

**Benefits:** Improved code readability, better separation of concerns, and easier maintenance.

**Avoid Unnecessary Comments:** The comment `/// @dev This is an external call, safe because it's at the end of the function` is unnecessary and can be removed. The code should be self-explanatory, and if a comment is needed, it should provide more meaningful information.

**Benefits:** Improved code readability and maintainability by reducing noise and clutter.

## L-11: [function withdrawStakerFunds](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/rollup/RollupUserLogic.sol#L358-L364)

```solidity
    function withdrawStakerFunds() external override whenNotPaused returns (uint256) {
        uint256 amount = withdrawFunds(msg.sender);
        require(amount > 0, "NO_FUNDS_TO_WITHDRAW");
        // This is safe because it occurs after all checks and effects
        IERC20(stakeToken).safeTransfer(msg.sender, amount);
        return amount;
    }
```
**Error Handling:** The `require` statement is used to check if the user has funds to withdraw. However, it might be better to use a more descriptive error message, such as `"NO_FUNDS_TO_WITHDRAW_FOR_USER"`, to provide more context in case of an error.

**Code Organization:** The code could benefit from better organization and separation of concerns. For example, the `withdrawFunds` function could be extracted into a separate function or utility library, making the `withdrawStakerFunds` function more concise and easier to maintain.

## L-12: [function assertionHash](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/rollup/RollupLib.sol#L23-L34)

```solidity
    function assertionHash(
        bytes32 parentAssertionHash,
        AssertionState memory afterState,
        bytes32 inboxAcc
    ) internal pure returns (bytes32) {
        // we can no longer have `hasSibling` in the assertion hash as it would allow identical assertions
        return assertionHash(
            parentAssertionHash,
            afterState.hash(),
            inboxAcc
        );
    }
```
The `hash()` call on `afterState` could be a computationally expensive operation, If this function is called frequently or in performance-critical paths, consider caching the result or exploring alternative approaches to improve efficiency.

## L-13: [function configHash](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/rollup/RollupLib.sol#L54-L71)

```solidity
    function configHash(
        bytes32 wasmModuleRoot,
        uint256 requiredStake,
        address challengeManager,
        uint64 confirmPeriodBlocks,
        uint64 nextInboxPosition
    ) internal pure returns (bytes32) {
        return
            keccak256(
                abi.encodePacked(
                    wasmModuleRoot,
                    requiredStake,
                    challengeManager,
                    confirmPeriodBlocks,
                    nextInboxPosition
                )
            );
    }
```
The `confirmPeriodBlocks` and `nextInboxPosition` parameters are of type `uint64`, which suggests they might have a limited range of valid values. If these values are indeed constants, it might be better to define them as constants at the contract level and pass them as constants to the function.

**Benefit:** Improved code maintainability and potential gas savings (if the values are indeed constants).

The order of the function arguments could be improved to follow a more logical or conventional order. For example, the `challengeManager` argument could be placed before the `requiredStake` argument, as the challenge manager is likely a more fundamental configuration parameter than the required stake.

**Benefit:** Improved code readability and maintainability.

L-14 - [function initialize](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/challengeV2/EdgeChallengeManager.sol#L305-L364)

Some of the variables, such as `LAYERZERO_BLOCKEDGE_HEIGHT`, `LAYERZERO_BIGSTEPEDGE_HEIGHT`, and `LAYERZERO_SMALLSTEPEDGE_HEIGHT`, are assigned values during initialization and never changed afterwards. If this is the case, it would be better to declare them as `constant` variables to save gas costs and improve code readability.

Move the constant values `LAYERZERO_BLOCKEDGE_HEIGHT`, `LAYERZERO_BIGSTEPEDGE_HEIGHT`, `LAYERZERO_SMALLSTEPEDGE_HEIGHT`, `NUM_BIGSTEP_LEVEL, and ZERO_BIGSTEP_LEVEL` to a dedicated constants section for clarity and code organization.
