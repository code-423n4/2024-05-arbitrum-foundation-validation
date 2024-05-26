## QA-01: Missing Event Emission in `updateRollupAddress`

**Summary:**

This report identifies an inconsistency in the `updateRollupAddress` function within the `sequencerinbox.sol` contract. While the `IBridge` interface it imports declares a `RollupUpdated` event, the `updateRollupAddress` function itself doesn't emit this event after successfully updating the rollup address.

**Proof of Concept:**
**Github link**
https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/bridge/SequencerInbox.sol#L207-L214
https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/bridge/SequencerInbox.sol#L40
https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/bridge/IBridge.sol#L57
https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/bridge/IBridge.sol#L125

1. **Interface Declaration:**
   - The `IBridge` interface declares the `RollupUpdated` event:

   ```solidity
   event RollupUpdated(address rollup);
   ```

2. **Function Implementation:**
   - The `sequencerinbox.sol` contract imports the `IBridge` interface.
   - However, the `updateRollupAddress` function within `sequencerinbox.sol` doesn't emit the `RollupUpdated` event after updating the `rollup` variable:

   ```solidity
   function updateRollupAddress() external {
       // ... function logic for updating rollup ...
       rollup = newRollup;
   }
   ```

**Impact:**

- The absence of the `RollupUpdated` event emission means external observers or applications that might be interested in rollup address changes won't be notified. This could lead to:
    - Difficulty in tracking rollup updates for monitoring or integration purposes.
    
**Recommended Mitigation Steps:**

- Emit the `RollupUpdated` event at the end of the `updateRollupAddress` function, after successfully updating the `rollup` variable:

   ```solidity
   function updateRollupAddress() external {
       // ... function logic for updating rollup ...
       rollup = newRollup;
       emit RollupUpdated(rollup);
   }
   ```

## QA-02: Incomplete Power of Two Check in `isPowerOfTwo`

**Summary:**

There is a minor correction needed in the `isPowerOfTwo` function. While the original implementation aimed to check if a given `uint256` value is a power of 2, it incorrectly classified 1 as a power of 2.

**Proof of Concept:**
**Github code**
https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/challengeV2/libraries/EdgeChallengeManagerLib.sol#L327-L338

The provided code snippet for the `isPowerOfTwo` function:

```solidity
function isPowerOfTwo(uint256 x) internal pure returns (bool) {
  // zero is not a power of 2
  if (x == 0) {
    return false;
  }

  // if x is a power of 2, then this will be 0111111
  uint256 y = x - 1;

  // if x is a power of 2 then y will share no bits with x
  return ((x & y) == 0);
}
```

The initial check only excluded `0`. However, 1 is also not considered a power of 2.

**Impact:**

- The incorrect classification of 1 as a power of 2 could lead to unexpected behavior in the code that relies on this function.
- For example, if the function is used to validate an input that should be a strict power of 2 (e.g., an array length), allowing 1 could cause issues with memory allocation or indexing.

**Recommended Mitigation Steps:**

- Update the initial check to exclude both 0 and 1:

```solidity
function isPowerOfTwo(uint256 x) internal pure returns (bool) {
  // Zero and one are not powers of 2
  if (x <= 1) {
    return false;
  }

  // Same logic as before to check if x is a power of 2
  uint256 y = x - 1;
  return ((x & y) == 0);
}
```

