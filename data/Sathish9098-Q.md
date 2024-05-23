## QA REPORT

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






