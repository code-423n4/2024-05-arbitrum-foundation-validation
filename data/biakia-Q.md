# Lines of code
https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/rollup/RollupUserLogic.sol#L82-L131

# Vulnerability details
In contract `RollupUserLogic`, the function `confirmAssertion` will check whether the deadline has passed:
```solidity
require(block.number >= assertion.createdAtBlock + prevConfig.confirmPeriodBlocks, "BEFORE_DEADLINE");
```
When the `block.number` is equal to `assertion.createdAtBlock + prevConfig.confirmPeriodBlocks`, this require statement will pass because it uses `>=` instead of `>`. This causes `prevConfig.confirmPeriodBlocks` to be one block less than expected.

# Recommended Mitigation Steps
Consider following fix:
```solidity
require(block.number > assertion.createdAtBlock + prevConfig.confirmPeriodBlocks, "BEFORE_DEADLINE");
```
