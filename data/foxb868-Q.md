## **Low - 01:** [src\bridge\SequencerInbox.sol:390-406](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/bridge/SequencerInbox.sol#L390-L406)

The function `addSequencerL2BatchFromBlobs` calls the internal function `addSequencerL2BatchFromBlobsImpl` with the following parameters: [src\bridge\SequencerInbox.sol:L400-L406](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/bridge/SequencerInbox.sol#L400-L406)

```solidity
addSequencerL2BatchFromBlobsImpl(
    sequenceNumber,
    afterDelayedMessagesRead,
    prevMessageCount,
    newMessageCount
);
```
The `prevMessageCount` and `newMessageCount` parameters are passed directly from the function arguments, without any validation or checks. If the caller provides invalid values for these parameters, it could lead to unexpected behavior or vulnerabilities in the `addSequencerL2BatchFromBlobsImpl` function.

Consider adding input validation checks for `prevMessageCount` and `newMessageCount` before calling `addSequencerL2BatchFromBlobsImpl`. For example, check that `newMessageCount` is greater than `prevMessageCount`, or that the difference between them is within a reasonable range.

```solidity
function addSequencerL2BatchFromBlobs(
    uint256 sequenceNumber,
    uint256 afterDelayedMessagesRead,
    IGasRefunder gasRefunder,
    uint256 prevMessageCount,
    uint256 newMessageCount
) external refundsGas(gasRefunder, reader4844) {
    if (!isBatchPoster[msg.sender]) revert NotBatchPoster();
    if (isDelayProofRequired(afterDelayedMessagesRead)) revert DelayProofRequired();

    // Input validation
    if (newMessageCount <= prevMessageCount) revert InvalidMessageCounts();

    addSequencerL2BatchFromBlobsImpl(
        sequenceNumber,
        afterDelayedMessagesRead,
        prevMessageCount,
        newMessageCount
    );
}
```

## **Low - 02:** [src\bridge\SequencerInbox.sol:409-427](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/bridge/SequencerInbox.sol#L409-L427)
The code perform the following tasks:

Checking if the caller is a batch poster (`isBatchPoster[msg.sender]`).
Checking if the contract is configured to be delay `bufferable (isDelayBufferable)`.
Calling the `delayProofImpl` function with the provided `afterDelayedMessagesRead` and `delayProof` parameters.
Calling the `addSequencerL2BatchFromBlobsImpl` function with the provided `sequenceNumber`, `afterDelayedMessagesRead`, `prevMessageCount`, and `newMessageCount` parameters.

One potential area of improvement could be the use of modifiers or separate functions to enforce the access control and contract state checks. This could help separate concerns and make the code more readable and maintainable.

For example, create a modifier like `onlyBatchPoster` and `whenDelayBufferable` to encapsulate the access control and state checks, respectively. This would allow you to apply these checks consistently across multiple functions, reducing code duplication and improving maintainability.

```solidity
modifier onlyBatchPoster() {
    if (!isBatchPoster[msg.sender]) revert NotBatchPoster();
    _;
}

modifier whenDelayBufferable() {
    if (!isDelayBufferable) revert NotDelayBufferable();
    _;
}

function addSequencerL2BatchFromBlobsDelayProof(
    uint256 sequenceNumber,
    uint256 afterDelayedMessagesRead,
    IGasRefunder gasRefunder,
    uint256 prevMessageCount,
    uint256 newMessageCount,
    DelayProof calldata delayProof
)
    external
    refundsGas(gasRefunder, reader4844)
    onlyBatchPoster
    whenDelayBufferable
{
    delayProofImpl(afterDelayedMessagesRead, delayProof);
    addSequencerL2BatchFromBlobsImpl(
        sequenceNumber,
        afterDelayedMessagesRead,
        prevMessageCount,
        newMessageCount
    );
}
```
## **Low - 03:** [src\bridge\SequencerInbox.sol:430-453
](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/bridge/SequencerInbox.sol#L430-L453)

The function `addSequencerL2BatchFromOriginDelayProof` checks if the caller is the transaction origin (`msg.sender != tx.origin`) and reverts if it's not. This check is intended to prevent contracts from calling this function, as it should only be called directly by an external account (EOA).

However, this check alone is not sufficient to prevent contracts from calling this function indirectly through other functions or libraries. If a contract calls another function that eventually calls `addSequencerL2BatchFromOriginDelayProof`, the `tx.origin` will still be the original EOA, and the check will pass.

Consider adding an additional check to ensure that the caller is not a contract. This can be done by checking if the caller's code size is zero, as EOAs have a code size of zero, while contracts have a non-zero code size.

```solidity
function addSequencerL2BatchFromOriginDelayProof(
    uint256 sequenceNumber,
    bytes calldata data,
    uint256 afterDelayedMessagesRead,
    IGasRefunder gasRefunder,
    uint256 prevMessageCount,
    uint256 newMessageCount,
    DelayProof calldata delayProof
) external refundsGas(gasRefunder, IReader4844(address(0))) {
    // solhint-disable-next-line avoid-tx-origin
    if (msg.sender != tx.origin || msg.sender.code.length != 0) revert NotOrigin();
    if (!isBatchPoster[msg.sender]) revert NotBatchPoster();
    if (!isDelayBufferable) revert NotDelayBufferable();

    delayProofImpl(afterDelayedMessagesRead, delayProof);
    addSequencerL2BatchFromCalldataImpl(
        sequenceNumber,
        data,
        afterDelayedMessagesRead,
        prevMessageCount,
        newMessageCount,
        true
    );
}
```
By adding the check `msg.sender.code.length != 0`, that we ensure the caller is not a contract, providing an additional layer of security against potential indirect calls from contracts.

## **Low - 04:** [src\bridge\SequencerInbox.sol:455-510](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/bridge/SequencerInbox.sol#L455-L496)

This function `addSequencerL2BatchFromBlobsImpl` is responsible for multiple tasks, including forming the data hash, adding the sequencer L2 batch, emitting an event, and submitting a batch spending report.

- The function uses a `revert` statement to handle the `BadSequencerNumber` error case. While this is a valid approach, it might be better to use a custom error with more descriptive error messages. This would provide better debugging information and make it easier to understand the cause of the revert.

- The line `if (sequenceNumber != ~uint256(0))` could be optimized by using the constant `type(uint256).max` instead of the bitwise NOT operator (`~`). While the difference in gas cost is minimal, using the constant would make the code more readable and easier to understand.

- The conditional check `if (hostChainIsArbitrum) revert DataBlobsNotSupported();` could be moved to the beginning of the function or extracted into a separate function. This would make the control flow more explicit and easier to understand, especially if the condition needs to be checked in multiple places.

The code checks if the `hostChainIsArbitrum` flag is true and reverts with the `DataBlobsNotSupported` error if it is. This check is performed after executing several operations, including forming the data hash, adding the sequencer L2 batch, and emitting an event.

It would be more efficient and logical to perform this check at the beginning of the function, before executing any other operations. This way, if the host chain is Arbitrum and data blobs are not supported, the function can revert immediately without wasting gas on unnecessary computations.

By moving this check to the beginning of the function, you can save gas in the case where data blobs are not supported, and the code flow becomes more intuitive and easier to reason about.

```solidity
function addSequencerL2BatchFromBlobsImpl(
    uint256 sequenceNumber,
    uint256 afterDelayedMessagesRead,
    uint256 prevMessageCount,
    uint256 newMessageCount
) internal {
    // Check if data blobs are supported on the host chain
    if (hostChainIsArbitrum) revert DataBlobsNotSupported();

    // Rest of the function...
}
```

## **Low - 05:** src\bridge\SequencerInbox.sol:582-626

`addSequencerL2BatchDelayProof` function is responsible for multiple tasks, including access control, state updates, and calling other functions.

- The conditional check `afterDelayedMessagesRead > totalDelayedMessagesRead` is repeated in both the `addSequencerL2BatchDelayProof` and `delayProofImpl` functions. This could be extracted into a separate function or a modifier to avoid code duplication and improve maintainability.

- The addSequencerL2BatchFromCalldataImpl function call at the end of addSequencerL2BatchDelayProof could potentially lead to a reentrancy vulnerability if the called function makes external calls to untrusted contracts. It's recommended to follow the "Checks-Effects-Interactions" pattern to mitigate this risk.

In the `delayProofImpl` function, the condition `afterDelayedMessagesRead > totalDelayedMessagesRead` is checked to determine whether the buffer needs to be updated. However, if `afterDelayedMessagesRead` is equal to `totalDelayedMessagesRead`, the buffer will not be updated, even though new delayed messages might have been added.

This could lead to a situation where the buffer is not updated correctly, potentially causing issues with the force inclusion mechanism or other functionalities that rely on the buffer state.

```solidity
if (afterDelayedMessagesRead >= totalDelayedMessagesRead) {
    // ...
}
```
This way, the buffer will be updated whenever there are new delayed messages, ensuring that the buffer state remains consistent with the actual number of delayed messages.

## **Low - 06:** [src\bridge\SequencerInbox.sol:628-636](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/bridge/SequencerInbox.sol#L628-L635)
```solidity
    function isDelayProofRequired(uint256 afterDelayedMessagesRead) internal view returns (bool) {
        // if no new delayed messages are read, no buffer updates can be applied, so no proof required
        // if the buffer is synced, the buffer cannot be depleted, so no proof is required
        return
            isDelayBufferable &&
            afterDelayedMessagesRead > totalDelayedMessagesRead &&
            !buffer.isSynced();
    }
```
While the comments explain the logic behind the return statement, they could be more concise and clear. For example:
```solidity
// If no new delayed messages were read or the buffer is synced, no proof is required
return isDelayBufferable && afterDelayedMessagesRead > totalDelayedMessagesRead && !buffer.isSynced();
```

Instead of using a single return statement with multiple conditions, consider using early returns for each condition. This can improve readability and make the control flow more explicit.
```solidity
if (!isDelayBufferable) return false;
if (afterDelayedMessagesRead <= totalDelayedMessagesRead) return false;
if (buffer.isSynced()) return false;
return true;
```

If the `isDelayBufferable` and `buffer.isSynced()` conditions involve complex logic, consider extracting them into separate functions with descriptive names. This would improve code modularity and make the main function more readable.

## **Low - 07:** [src\bridge\SequencerInbox.sol:688-718](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/bridge/SequencerInbox.sol#L688-L718)

The function checks if the first byte of the data input is a valid header flag using the `isValidCallDataFlag` function. If the flag is invalid, it reverts with the `InvalidHeaderFlag` error. H**owever, there is a special case where the function does not revert, even if the first byte is an invalid header flag.**

**This special case occurs when the following conditions are met:**

The first byte of `data` is the `DAS_MESSAGE_HEADER_FLAG` (or any other flag that satisfies the condition `data[0] & DAS_MESSAGE_HEADER_FLAG != 0)`.
The length of `data` is greater than or equal to 33 bytes.

In this case, the function assumes that the first byte is a valid DAS message header flag, and it proceeds to check if the next 32 bytes (bytes 1 to 32) represent a valid DAS keyset hash. If the keyset hash is not valid, it reverts with the `NoSuchKeyset` error.

However, if the first byte is an invalid header flag and the length of data is greater than or equal to 33 bytes, the function will not revert, and it will proceed to process the data as a DAS message, even though the first byte is not a valid DAS message header flag.

This behavior could potentially lead to unintended consequences or security vulnerabilities if the function is called with malformed or malicious input data.

**To mitigate this:**
Consider adding an additional check to ensure that the first byte is a valid header flag, even in the case where the length of data is greater than or equal to 33 bytes. This would ensure that the function consistently validates the input data and reverts with the appropriate error message if the input is invalid.

## **Low - 08:** [src\bridge\SequencerInbox.sol:725-748](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/bridge/SequencerInbox.sol#L725-L748)

- The function `formBlobDataHash` is responsible for multiple tasks: retrieving data hashes, packing the header, calculating the blob cost, and returning the final data hash. Separating these concerns into smaller, more focused functions could improve code organization and maintainability.
- The constant `GAS_PER_BLOB` is used without any explanation of its meaning or value. It would be better to define a constant with a descriptive name and document its purpose and value.
- Instead of nesting the main logic inside an `if` statement, use an early return to handle the case where `dataHashes` is empty. This can improve code readability and make the happy path more apparent.
- The code uses low-level byte manipulation functions like `abi.encodePacked` and `bytes.concat`. While these are efficient, they can be error-prone and harder to maintain. Consider using a well-tested library like `solidity-bytes-utils` or `BytesLib` for byte manipulation operations, which can improve code readability and maintainability.


## **Low - 09:** [src\bridge\SequencerInbox.sol:755-789](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/bridge/SequencerInbox.sol#L755-L789)

  - **Use a more descriptive variable name for dataHash**

Consider using a constant for the `address(0x6c)` value: The `address(0x6c)` value is used to call the `ArbGasInfo` contract. It might be better to define this address as a constant at the top of the file or in a separate file for constants. This would make the code more readable and easier to maintain if the address needs to be changed in the future.

The `abi.encodePacked` call used to encode the spending report message is quite long and complex. It might be better to move this logic into a separate function to improve code readability and maintainability.

## **Low - 10:** [src\bridge\SequencerInbox.sol:791-823](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/bridge/SequencerInbox.sol#L791-L822)

```solidity
    function addSequencerL2BatchImpl(
        bytes32 dataHash,
        uint256 afterDelayedMessagesRead,
        uint256 calldataLengthPosted,
        uint256 prevMessageCount,
        uint256 newMessageCount
    )
        internal
        returns (
            uint256 seqMessageIndex,
            bytes32 beforeAcc,
            bytes32 delayedAcc,
            bytes32 acc
        )
    {
        if (afterDelayedMessagesRead < totalDelayedMessagesRead) revert DelayedBackwards();
        if (afterDelayedMessagesRead > bridge.delayedMessageCount()) revert DelayedTooFar();


        (seqMessageIndex, beforeAcc, delayedAcc, acc) = bridge.enqueueSequencerMessage(
            dataHash,
            afterDelayedMessagesRead,
            prevMessageCount,
            newMessageCount
        );


        totalDelayedMessagesRead = afterDelayedMessagesRead;


        if (calldataLengthPosted > 0 && !isUsingFeeToken) {
            // only report batch poster spendings if chain is using ETH as native currency
            submitBatchSpendingReport(dataHash, seqMessageIndex, block.basefee, 0);
        }
    }
```
- The variable names `beforeAcc`, `delayedAcc`, and `acc` are not very descriptive, making it harder to understand their purpose and meaning. Consider using more descriptive names that convey the intent of these variables.

- The function uses the literal value `0` in the `submitBatchSpendingReport` call. It's generally better to use named constants or `enums` to make the code more self-documenting and easier to maintain.

- Instead of relying on the `submitBatchSpendingReport` function, consider emitting events to log important state changes or actions. Events can be more efficient and provide better transparency and auditability.

- While the function checks for some error conditions, it could benefit from more comprehensive input validation and error handling. For example, check if the `dataHash` is valid or if the `calldataLengthPosted` is within an expected range.

## **Low - 01:** [src\bridge\SequencerInbox.sol:833-840](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/bridge/SequencerInbox.sol#L833-L840)
```solidity
    function forceInclusionDeadline(uint64 blockNumber) external view returns (uint64) {
        uint64 _delayBlocks = delayBlocks;
        if (isDelayBufferable) {
            uint64 _buffer = buffer.calcPendingBuffer(blockNumber);
            _delayBlocks = delayBufferableBlocks(_buffer);
        }
        return blockNumber + _delayBlocks;
    }
```

The calculation `blockNumber + _delayBlocks` could potentially be optimized by using a safer math library or by performing overflow checks. This would help prevent potential integer overflow issues.

- Depending on the frequency of calls to this function, it might be worth caching the result of `buffer.calcPendingBuffer(blockNumber)` to improve performance, especially if the calculation is computationally expensive.

If the `delayBlocks` value is constant or rarely changes, it could be worth caching the value to avoid redundant calculations.

```solidity
function forceInclusionDeadline(uint64 blockNumber) external view returns (uint64) {
    // Input validation
    if (blockNumber == 0) {
        revert InvalidBlockNumber();
    }

    uint64 _delayBlocks = delayBlocks;
    if (isDelayBufferable) {
        uint64 _buffer = buffer.calcPendingBuffer(blockNumber);
        _delayBlocks = delayBufferableBlocks(_buffer);

        // Additional validation for delayBufferableBlocks
        if (_delayBlocks == 0) {
            revert InvalidDelayBlocks();
        }
    }

    // Overflow check
    uint64 deadline = blockNumber + _delayBlocks;
    if (deadline < blockNumber) {
        revert DeadlineOverflow();
    }

    return deadline;
}
```

## **Low - 11:** src\bridge\SequencerInbox.sol:847-865
```solidity
    function _setBufferConfig(BufferConfig memory bufferConfig_) internal {
        if (!isDelayBufferable) revert NotDelayBufferable();
        if (!DelayBuffer.isValidBufferConfig(bufferConfig_)) revert BadBufferConfig();

        if (buffer.bufferBlocks == 0 || buffer.bufferBlocks > bufferConfig_.max) {
            buffer.bufferBlocks = bufferConfig_.max;
        }
        if (buffer.bufferBlocks < bufferConfig_.threshold) {
            buffer.bufferBlocks = bufferConfig_.threshold;
        }
        buffer.max = bufferConfig_.max;
        buffer.threshold = bufferConfig_.threshold;
        buffer.replenishRateInBasis = bufferConfig_.replenishRateInBasis;

        // if all delayed messages are read, the buffer is considered synced
        if (bridge.delayedMessageCount() == totalDelayedMessagesRead) {
            buffer.update(uint64(block.number));
        }
    }
```
Instead of checking the `isDelayBufferable` condition within the function, consider using a modifier to enforce this access control. Modifiers can help reduce code duplication and improve code organization.

The function uses the literal value `0` for checking if `buffer.bufferBlocks` is zero. It would be better to use a constant or an enumeration to make the code more self-documenting and easier to maintain.

The variable name `bufferConfig_` is not very descriptive. Consider using a more meaningful name that better represents the purpose of the variable.

## **Low - 12:** [src\bridge\SequencerInbox.sol:903-919](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/bridge/SequencerInbox.sol#L903-L919)
```solidity
    function setValidKeyset(bytes calldata keysetBytes) external onlyRollupOwner {
        uint256 ksWord = uint256(keccak256(bytes.concat(hex"fe", keccak256(keysetBytes))));
        bytes32 ksHash = bytes32(ksWord ^ (1 << 255));
        if (keysetBytes.length >= 64 * 1024) revert KeysetTooLarge();


        if (dasKeySetInfo[ksHash].isValidKeyset) revert AlreadyValidDASKeyset(ksHash);
        uint256 creationBlock = block.number;
        if (hostChainIsArbitrum) {
            creationBlock = ArbSys(address(100)).arbBlockNumber();
        }
        dasKeySetInfo[ksHash] = DasKeySetInfo({
            isValidKeyset: true,
            creationBlock: uint64(creationBlock)
        });
        emit SetValidKeyset(ksHash, keysetBytes);
        emit OwnerFunctionCalled(2);
    }
```
 Instead of using a struct to store the `DasKeySetInfo`, use a mapping with the `ksHash` as the key. This would simplify the code and potentially improve performance, as accessing values in a mapping is generally more efficient than accessing struct fields.

Before calculating the `ksWord` and `ksHash`, check if `keysetBytes.lengt`h is zero and revert if it is. This would prevent unnecessary computation and potential issues with hashing an empty byte array.

Use events for logging instead of `emit OwnerFunctionCalled`. The `emit OwnerFunctionCalled(2)` statement seems to be used for logging purposes. Instead of using a generic event, create a dedicated event for this function and include relevant information, such as the `ksHash` or `keysetBytes`. This would make the logs more informative and easier to analyze.

## **Low - 13:** [src\rollup\RollupCore.sol:82-118](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/rollup/RollupCore.sol#L82-L118)

The code seems to be declaring and initializing various state variables and mappings for the RollupCore contract.

However, there is one potential issue that could be worth considering: [src\rollup\RollupCore.sol:112](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/rollup/RollupCore.sol#L112)
```solidity
bool internal immutable _hostChainIsArbitrum = ArbitrumChecker.runningOnArbitrum();
```
The `_hostChainIsArbitrum` variable is initialized using the `ArbitrumChecker.runningOnArbitrum()` function. While the code itself does not provide the implementation of this function, it is likely a utility function that checks if the current execution environment is an Arbitrum chain.

The potential issue here is that the `runningOnArbitrum()` function might rely on certain conditions or checks that may not be accurate or reliable during contract deployment or initialization. If the conditions or checks used by this function are not valid or consistent during the contract deployment phase, the `_hostChainIsArbitrum` variable could be initialized with an incorrect value.

## **Low - 14:** [src\rollup\RollupCore.sol:236-267](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/rollup/RollupCore.sol#L236-L267)
```solidity
        AssertionNode storage assertion = getAssertionStorage(assertionHash);
        // Check that assertion is pending, this also checks that assertion exists
        require(assertion.status == AssertionStatus.Pending, "NOT_PENDING");


        // Authenticate data against assertionHash pre-image
        require(
            assertionHash
                == RollupLib.assertionHash({
                    parentAssertionHash: parentAssertionHash,
                    afterState: confirmState,
                    inboxAcc: inboxAcc
                }),
            "CONFIRM_DATA"
        );


        bytes32 blockHash = confirmState.globalState.getBlockHash();
        bytes32 sendRoot = confirmState.globalState.getSendRoot();


        // trusted external call to outbox
        outbox.updateSendRoot(sendRoot, blockHash);


        _latestConfirmed = assertionHash;
        assertion.status = AssertionStatus.Confirmed;

```
The check for the assertion status (`assertion.status == AssertionStatus.Pending`) is repeated in multiple places within the contract. Consider using a modifier or a helper function to encapsulate this check and avoid code duplication.

The error messages used in the `require` statements could be more descriptive and informative. For example, instead of `"NOT_PENDING"`, use a more descriptive message like `"Assertion is not in a pending state"`.

The function reads the a`ssertion` storage variable twice, once to check the status and again to update the status. Consider caching the storage value in memory to avoid redundant storage reads, which can improve gas efficiency.

While the function emits an `AssertionConfirmed` event, it could also emit events for other state changes, such as when the assertion status is updated from `Pending` to `Confirmed`. This can improve transparency and make it easier to track and audit state changes.

## **Low - 15:** [src\rollup\RollupCore.sol:317-324](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/rollup/RollupCore.sol#L317-L324)
```solidity
    function withdrawStaker(address stakerAddress) internal {
        Staker storage staker = _stakerMap[stakerAddress];
        address withdrawalAddress = staker.withdrawalAddress;
        uint256 initialStaked = staker.amountStaked;
        increaseWithdrawableFunds(withdrawalAddress, initialStaked);
        deleteStaker(stakerAddress);
        emit UserStakeUpdated(stakerAddress, withdrawalAddress, initialStaked, 0);
    }
```
Instead of relying solely on the `UserStakeUpdated` event for logging, consider adding additional events or logging mechanisms to improve visibility and auditability of the `withdrawStaker` function's execution. This can aid in debugging and monitoring the contract's behavior.

The `_stakerMap` mapping is accessed multiple times within the function. If this mapping is frequently accessed throughout the contract, consider caching the `Staker` struct in memory to reduce the number of storage reads and potentially improve gas efficiency.

## **Low - 16:** [src\rollup\RollupCore.sol:331-337](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/rollup/RollupCore.sol#L331-L337)
```solidity
    function withdrawFunds(address account) internal returns (uint256) {
        uint256 amount = _withdrawableFunds[account];
        _withdrawableFunds[account] = 0;
        totalWithdrawableFunds -= amount;
        emit UserWithdrawableFundsUpdated(account, amount, 0);
        return amount;
    }
```
The code is performing arithmetic operations on `uint256` values without an overflow/underflow checks. Use OpenZeppelin's `SafeMath` library to prevent potential integer overflows or underflows, which can lead to security vulnerabilities.

Consider using a mapping instead of an array for `_withdrawableFunds`. If the number of accounts is expected to be large, using a mapping (`mapping(address => uint256)`) instead of an array for `_withdrawableFunds` could improve gas efficiency and performance when accessing or updating the withdrawable funds for a specific account.

Emit events with indexed parameters: The `UserWithdrawableFundsUpdated` event could benefit from having the `account` parameter marked as `indexed`. This would allow for more efficient off-chain filtering and querying of events related to a specific account.

## **Low - 17:** [src\rollup\RollupCore.sol:343-349](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/rollup/RollupCore.sol#L343-L349)
```solidity
    function increaseWithdrawableFunds(address account, uint256 amount) internal {
        uint256 initialWithdrawable = _withdrawableFunds[account];
        uint256 finalWithdrawable = initialWithdrawable + amount;
        _withdrawableFunds[account] = finalWithdrawable;
        totalWithdrawableFunds += amount;
        emit UserWithdrawableFundsUpdated(account, initialWithdrawable, finalWithdrawable);
    }
```
The arithmetic operations in this function (`+`) are safe from overflows and underflows since the `amount` is added to the existing `_withdrawableFunds[account]` value. However, to save gas, you could use the `unchecked` block for these operations, as recommended by the Solidity documentation.
```solidity
function increaseWithdrawableFunds(address account, uint256 amount) internal {
    uint256 initialWithdrawable = _withdrawableFunds[account];
    unchecked {  <@
        uint256 finalWithdrawable = initialWithdrawable + amount;
        _withdrawableFunds[account] = finalWithdrawable;
        totalWithdrawableFunds += amount;
    }
    emit UserWithdrawableFundsUpdated(account, initialWithdrawable, finalWithdrawable);
}
```
This can save gas by skipping the overflow/underflow checks, which are unnecessary in this case.

The `UserWithdrawableFundsUpdated` event could benefit from having the `account` parameter indexed. This would allow for more efficient off-chain filtering and querying of events related to a specific account.
```solidity
event UserWithdrawableFundsUpdated(address indexed account, uint256 initialWithdrawable, uint256 finalWithdrawable);
```

## **Low - 18:** [src\rollup\RollupCore.sol:520-530](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/rollup/RollupCore.sol#L520-L530)
```solidity
    function genesisAssertionHash() external pure returns (bytes32) {
        GlobalState memory emptyGlobalState;
        AssertionState memory emptyAssertionState = AssertionState(emptyGlobalState, MachineStatus.FINISHED, bytes32(0));
        bytes32 parentAssertionHash = bytes32(0);
        bytes32 inboxAcc = bytes32(0);
        return RollupLib.assertionHash({
            parentAssertionHash: parentAssertionHash,
            afterState: emptyAssertionState,
            inboxAcc: inboxAcc
        });
    }
```
The `GlobalState` and `AssertionState` structs are allocated in memory using the memory keyword. If these structs are not modified within the function, it might be more efficient to create them as pure constants or immutable variables in the contract's storage. _This could potentially improve gas efficiency._

Consider using a constant for the initial value, Instead of using `bytes32(0)` multiple times, you could define a constant `ZERO_BYTES32` and use it throughout the contract for better readability and maintainability.