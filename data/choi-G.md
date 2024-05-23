## Issue
The current implementation of hashing functions in `RollupLib.sol` might be optimized for gas usage. Efficient hashing is crucial and optimizing it can lead to significant gas savings.

## Impact
Optimized hashing functions can save gas during important operations, especially in high-volume environments like rollups. This can result in reduced transaction costs and improved performance.

## Proof of Concept
The following links leads to sections of the code in `RollupLib.sol` where hashing operations are implemented. These codes should be reviewed and optimized for gas efficiency.

- [RollupLib.sol, line 10-20](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/rollup/RollupLib.sol#L10-L20)
- [RollupLib.sol, line 30-40](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/rollup/RollupLib.sol#L30-L40)

Here is an example of a hashing function from the code:
```solidity
function hashAssertionNode(
    bytes32[2] memory globalState,
    bytes32[2] memory prevHash,
    uint64 deadlineTicks,
    uint256 assertionId
) internal pure returns (bytes32) {
    return keccak256(abi.encodePacked(
        globalState[0],
        globalState[1],
        prevHash[0],
        prevHash[1],
        deadlineTicks,
        assertionId
    ));
}
```

## Tools Used
Manual code review

## Mitigation Steps
- Inline assembly can be used to directly interact with the EVM for hashing. This can be more gas-efficient. Optimized code example:
```solidity
function optimizedHashAssertionNode(
    bytes32[2] memory globalState,
    bytes32[2] memory prevHash,
    uint64 deadlineTicks,
    uint256 assertionId
) internal pure returns (bytes32 result) {
    assembly {
        let ptr := mload(0x40)
        mstore(ptr, mload(globalState))
        mstore(add(ptr, 0x20), mload(add(globalState, 0x20)))
        mstore(add(ptr, 0x40), mload(prevHash))
        mstore(add(ptr, 0x60), mload(add(prevHash, 0x20)))
        mstore(add(ptr, 0x80), deadlineTicks)
        mstore(add(ptr, 0xa0), assertionId)
        result := keccak256(ptr, 0xc0)
    }
}
```
- Instead of encoding data using `abi.encodePacked`, consider packing the data in a more gas-efficient way. An example code:
```solidity
function moreEfficientHash(
    bytes32 globalState1,
    bytes32 globalState2,
    bytes32 prevHash1,
    bytes32 prevHash2,
    uint64 deadlineTicks,
    uint256 assertionId
) internal pure returns (bytes32) {
    return keccak256(abi.encode(
        globalState1,
        globalState2,
        prevHash1,
        prevHash2,
        deadlineTicks,
        assertionId
    ));
}
```