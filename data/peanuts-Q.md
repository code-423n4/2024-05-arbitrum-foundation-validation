### [L-01] The stakes are unchangeable in EdgeChallengeManager

Whenever a player wants to create a layer zero edge, he has to deposit a mini-bond that is pre-set by the protocol, when the protocol initializes:

```
  /// @inheritdoc IEdgeChallengeManager
    function initialize(
        IAssertionChain _assertionChain,
        uint64 _challengePeriodBlocks,
        IOneStepProofEntry _oneStepProofEntry,
        uint256 layerZeroBlockEdgeHeight,
        uint256 layerZeroBigStepEdgeHeight,
        uint256 layerZeroSmallStepEdgeHeight,
        IERC20 _stakeToken,
        address _excessStakeReceiver,
        uint8 _numBigStepLevel,
>       uint256[] calldata _stakeAmounts
```

This stakeAmount cannot be changed. This may be a cause for concern if the stake token, which is WETH, grows in value. Since the stake amount cannot be changed, it may get economically expensive. Consider allowing the DAO to change this amount.  

https://github.com/OffchainLabs/bold/blob/0420b9ddb88f71f5e86ca1b3bc256c09346b8315/contracts/src/challengeV2/EdgeChallengeManager.sol#L363C9-L363C22

### [L-02] Excess stake is locked in the contract when creating assertions

When creating assertions in RollupUserLogic, the comments state that excess stake will be stuck.

```
 if (!getAssertionStorage(newAssertionHash).isFirstChild) {
            // We assume assertion.beforeStateData is valid here as it will be validated in createNewAssertion
            // only 1 of the children can be confirmed and get their stake refunded
            // so we send the other children's stake to the loserStakeEscrow
>           // NOTE: if the losing staker have staked more than requiredStake, the excess stake will be stuck
            IERC20(stakeToken).safeTransfer(loserStakeEscrow, assertion.beforeStateData.configData.requiredStake);
        }
```

Enforce the scenario such that the stake will not be stuck, by probably requiring a strict equal sign when checking the staking amount and depositing into the lowerEscrow contract.

https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/rollup/RollupUserLogic.sol#L209 

### [L-03] If updateTimerCacheByChildren is not called every time a edge is bisected, then the timer will not accrue.

It seems that to accrue the time for all instances of a challenge, the updateTimerCacheByChildren has to be called.

```
    /// @inheritdoc IEdgeChallengeManager
    function updateTimerCacheByChildren(bytes32 edgeId) public {
        (bool updated, uint256 newValue) = store.updateTimerCacheByChildren(edgeId);
        if (updated) emit TimerCacheUpdated(edgeId, newValue);
    }
```
```
    function updateTimerCacheByChildren(EdgeStore storage store, bytes32 edgeId) internal returns (bool, uint256) {
        return updateTimerCache(store, edgeId, timeUnrivaledTotal(store, edgeId));
    }
```
```
    function timeUnrivaledTotal(EdgeStore storage store, bytes32 edgeId) internal view returns (uint256) {
        uint256 totalTimeUnrivaled = timeUnrivaled(store, edgeId);
        if (store.edges[edgeId].lowerChildId != bytes32(0)) {
            uint256 lowerTimer = store.edges[store.edges[edgeId].lowerChildId].totalTimeUnrivaledCache;
            uint256 upperTimer = store.edges[store.edges[edgeId].upperChildId].totalTimeUnrivaledCache;
            totalTimeUnrivaled += lowerTimer < upperTimer ? lowerTimer : upperTimer;
        }
        return totalTimeUnrivaled;
    }
```

If the assertion creator forgets to call the function, then the time elapsed when waiting for the next bisection will not be added together.

Add the time when the edge is bisected.

https://github.com/OffchainLabs/bold/blob/0420b9ddb88f71f5e86ca1b3bc256c09346b8315/contracts/src/challengeV2/EdgeChallengeManager.sol#L497