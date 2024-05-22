## Function visibility for receiveTokens should be internal
https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/rollup/RollupUserLogic.sol#L366C2-L368C6
```
function receiveTokens(uint256 tokenAmount) private {
    IERC20(stakeToken).safeTransferFrom(msg.sender, address(this), tokenAmount);
}
```
Problem: The function receiveTokens is marked as private but should be internal to allow calls within the contract inheritance hierarchy.
### Impact: Limited extensibility and flexibility.

## mitigation 
```
function receiveTokens(uint256 tokenAmount) internal {
    IERC20(stakeToken).safeTransferFrom(msg.sender, address(this), tokenAmount);
}
```
