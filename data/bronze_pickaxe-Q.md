# L-01

## Usage of depriciated function `isContract()`

### Description
In `StakingPoolCreatorUtils.getPool()`, the function `isContract()` is used:
```javascript
    function getPool(bytes memory creationCode, bytes memory args) internal view returns (address) {
        bytes32 bytecodeHash = keccak256(abi.encodePacked(creationCode, args));
        address pool = Create2.computeAddress(0, bytecodeHash, address(this));
        // @audit this function has been depreciated
        if (Address.isContract(pool)) {
            return pool;
        } else {
            revert PoolDoesntExist();
        }
    }
```
This function has been depriciated since [5.0.0](https://github.com/OpenZeppelin/openzeppelin-contracts/blob/master/CHANGELOG.md#removals-summary)

This can lead to unexpected behaviour and `isContract()` is not a reliable way to identify if you are dealing with an `EAO` or `smart contract.`

### Recommended Mitigation Steps
Do not use `isContract()`.

---

# L-02

### Description
`assertionId` is calculated by the following functions:
```javascript
    function computeAssertionHash(bytes32 prevAssertionHash, AssertionState calldata state, bytes32 inboxAcc)
        external
        pure
        returns (bytes32)
    {
        return RollupLib.assertionHash(prevAssertionHash, state, inboxAcc);
    }
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
    function assertionHash(
        bytes32 parentAssertionHash,
        bytes32 afterStateHash,
        bytes32 inboxAcc
    ) internal pure returns (bytes32) {
        // we can no longer have `hasSibling` in the assertion hash as it would allow identical assertions
        return
            keccak256(
                abi.encodePacked(
                    parentAssertionHash,
                    afterStateHash,
                    inboxAcc
                )
            );
    }
```

Both functions make use of `abi.encodePacked` and both use dynamtic variables which could lead to a collission as per the Solidity docs:
- https://docs.soliditylang.org/en/v0.8.11/abi-spec.html

which could lead to `edgeIds` being the same, breaking one of the invariants described in the `README.md`.

### Recommended Mitigation Steps
Handle dynamic encoding differently.
