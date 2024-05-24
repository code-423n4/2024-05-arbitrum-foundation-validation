## Summary
The `perform` function is use as a form or method of upgrade from an old to a new rollUp. During a call to the [perform](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/rollup/BOLDUpgradeAction.sol#L464) function, the developers cached the `Owner` (as in config.owner) address to `address(this)` in order to perform the necessary deployments and return the ownerShip back, per natspec :
```solidity
// initialize the rollup with this contract as owner to set batch poster and validators
        // it will transfer the ownership back to the actual owner later
        address actualOwner = config.owner;
        config.owner = address(this);
``` 

The issue here is that, the caching is unnecessary as the [config](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/rollup/BOLDUpgradeAction.sol#L469) which is of a memory returned value of a [createConfig](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/rollup/BOLDUpgradeAction.sol#L367) function has the [config.Owner](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/rollup/BOLDUpgradeAction.sol#L393) set as `address(this)` also, this means that the caching is unnecessary as it will work just as expected without the catching

## Tool Used

Manual review

## Recommendation

Remove the caching and pass the returned `config` as its because the `address(this)` has already been set as the owner (as in config.owner).