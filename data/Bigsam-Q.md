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

By implementing this change, the `updateRollupAddress` function will adhere to the expectations set by the `IBridge` interface and provide valuable information to external entities about rollup address updates.
