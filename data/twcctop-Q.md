## L1  param  `prevAssertionHash`  is not necessary for the `confirmAssertion` function.


https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/265c57800145734362a4bb1b46465ff35b47beac/src/rollup/RollupUserLogic.sol#L113

in function `confirmAssertion`, param `prevAssertionHash` is supplied by user, actullay we have limit `prevAssertionHash`  must
equal to `latestConfirmed()`, so we can remove this param and get hash just from `latestConfirmed()`.


```solidity
    function confirmAssertion(
    bytes32 assertionHash,
@>    bytes32 prevAssertionHash,
    AssertionState calldata confirmState,
    bytes32 winningEdgeId,
    ConfigData calldata prevConfig,
    bytes32 inboxAcc
) external onlyValidator whenNotPaused {

 ...


@>  require(prevAssertionHash == latestConfirmed(), "PREV_NOT_LATEST_CONFIRMED");

```


## L2   function `stakeOnNewAssertion`  should be internal because it can only be called by `newStakeOnNewAssertion`.

https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/265c57800145734362a4bb1b46465ff35b47beac/src/rollup/RollupUserLogic.sol#L163

we have function `stakeOnNewAssertion`, it's used to create a new assertion.
in this function, we have check to make sure it's staked. 

```solidity

    function stakeOnNewAssertion(AssertionInputs calldata assertion, bytes32 expectedAssertionHash)
        public
        onlyValidator
        whenNotPaused
    {

...

 @>  require(isStaked(msg.sender), "NOT_STAKED");



```

The issue is,  we can not stake directly, we need to call `newStakeOnNewAssertion` to stake first, 
And function `stakeOnNewAssertion`  is only called in `newStakeOnNewAssertion`, so we can should make function `stakeOnNewAssertion` internal.

```solidity
    function newStakeOnNewAssertion(
        uint256 tokenAmount,
        AssertionInputs calldata assertion,
        bytes32 expectedAssertionHash,
        address withdrawalAddress
    ) public {
        require(withdrawalAddress != address(0), "EMPTY_WITHDRAWAL_ADDRESS");
        _newStake(tokenAmount, withdrawalAddress);
@>        stakeOnNewAssertion(assertion, expectedAssertionHash);
        /// @dev This is an external call, safe because it's at the end of the function
        receiveTokens(tokenAmount);
    }



```