## [L-01] Duplicate usage of modifiers when new stakers stake on an assertion.
The [`RollupUserLogic._newStake() function`](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/rollup/RollupUserLogic.sol#L137-L142) and [`RollupUserLogic.stakeOnNewAssertion() function`](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/rollup/RollupUserLogic.sol#L163-L167) uses the `onlyValidator` & `whenNotPaused` modifiers. The `newStake() function` is an internal function that is only called from the [`RollupUserLogic.newStakeOnNewAssertion() function`](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/rollup/RollupUserLogic.sol#L331-L342), and this function also calls the `stakeOnNewAssertion() function`, this means that the two modifiers are used twice.

Execution trace: `newStakeOnNewAssertion() => _newStake() => stakeOnNewAssertion()`

**Fix:**
Since the `newStake() function` is an internal function that is only called from the [`RollupUserLogic.newStakeOnNewAssertion() function`](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/rollup/RollupUserLogic.sol#L331-L342), and the `newStakeOnNewAssertion() function` also implementes the exact same two modifiers, the recommendation would be to remove those two modifiers from the `newStake() function`. 
- In the end, the execution of the [`RollupUserLogic.newStakeOnNewAssertion() function`](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/rollup/RollupUserLogic.sol#L331-L342) will be protected by the logic of those modifiers thanks to the [`RollupUserLogic.stakeOnNewAssertion() function`](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/rollup/RollupUserLogic.sol#L163-L167)

```
- function _newStake(uint256 depositAmount, address withdrawalAddress) internal onlyValidator whenNotPaused {
+ function _newStake(uint256 depositAmount, address withdrawalAddress) internal {
    // Verify that sender is not already a staker
    require(!isStaked(msg.sender), "ALREADY_STAKED");
    // amount will be checked when creating an assertion
    createNewStake(msg.sender, depositAmount, withdrawalAddress);
}
```
