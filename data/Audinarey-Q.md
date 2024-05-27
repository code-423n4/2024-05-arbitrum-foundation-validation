## [L-01] The time an edge is unrivaled should never exceed max challenge Period
In the challenge time of an assertion should never exceed max 14 days inclusive of the grace period. The `totalTimeUnrivaledCache` which is the an inherited sum of the time time during which an edge is unrivalled over different bisection stages and should under normal circumstances not be more than 14 days total. However, the `EdgeChallengeManagerLib::updateTimerCache(...)` function is used to update [the `totalTimeUnrivaledCache`](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/challengeV2/libraries/EdgeChallengeManagerLib.sol#L507-L512) and makes room for a scenario where the value to be updated could be as high as `type(uint64).max` . 

```solidity
File: EdgeChallengeManagerLib.sol
502:     function updateTimerCache(EdgeStore storage store, bytes32 edgeId, uint256 newValue)
503:         internal
504:         returns (bool, uint256)
505:     {
506:         uint256 currentAccuTimer = store.edges[edgeId].totalTimeUnrivaledCache;
507:  @>     newValue = newValue > type(uint64).max ? type(uint64).max : newValue;
508:         // only update when increased
509:         if (newValue > currentAccuTimer) {
510:             store.edges[edgeId].totalTimeUnrivaledCache = uint64(newValue);
511:             return (true, newValue);
512:         }
513:         return (false, currentAccuTimer);
514:     }

```

This should not be the case if the 14 days period always hold even if blocks are mined and confirmed every second

## Recommended Mitigation steps

If for any reason the `newValue` gets up to or even exceeds the `type(uint64).max` consider reverting instead of cap the value as this should be a pointer to a fault in the challenge manager


## [L-02] `EdgeChallengeManager::confirmEdgeByOneStepProof(...)` arbitrarily estimates `totalTimeUnrivaledCache`

To confirm an edge by executing a one step proof, `EdgeChallengeManagerLib::confirmEdgeByOneStepProof(...)` is called. However it sets [the edge’s `totalTimeUnrivaledCache`](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/challengeV2/libraries/EdgeChallengeManagerLib.sol#L829-L830) to `type(uint64).max` . This is wrong as the total challenge period is not suppose to exceed 14 days during which `type(uint64).max` blocks cannot be mined or confirmed.

```solidity
File: EdgeChallengeManagerLib.sol
766:     function confirmEdgeByOneStepProof(
767:         EdgeStore storage store,
768:         bytes32 edgeId,
769:         IOneStepProofEntry oneStepProofEntry,
770:         OneStepData calldata oneStepData,
771:         ExecutionContext memory execCtx,
772:         bytes32[] calldata beforeHistoryInclusionProof,
773:         bytes32[] calldata afterHistoryInclusionProof,
774:         uint8 numBigStepLevel,
775:         uint256 bigStepHeight,
776:         uint256 smallStepHeight
777:     ) internal {
778:         if (!store.edges[edgeId].exists()) {
779:             revert EdgeNotExists(edgeId);
780:         }
...
829:         // we also check the edge is pending in setConfirmed()
830:         store.edges[edgeId].setConfirmed();
831:         // @audit QA this cannot be true since the max challenge time is 14 days, so we can assume that the edge was challenged once by thehaasertion and this still falls within 14days (in blocks I think)
832:  @>     store.edges[edgeId].totalTimeUnrivaledCache = type(uint64).max;
833:     }

```

## Recommended Mitigation Steps

Consider updating `totalTimeUnrivaledCache` with the previous store value instead of over writing it.

## [N-01] Consider removing empty `else` block when adding a new edge to a store

When a new edge is added to a store we store a magic string `UNRIVALED` in the `firstRivals` mapping which is a depending on whether or not there is a rival edge. However in this context and edge can either be rivalled or unrivalled but the developer attempts to handle 3 states leaving empty `else` block as seen on L188 below.

```solidity
File: EdgeChallengeManagerLib.sol
182:         if (firstRival == 0) {
183:             store.firstRivals[mutualId] = UNRIVALED;
184:         } else if (firstRival == UNRIVALED) {
185:             store.firstRivals[mutualId] = eId;
186:         } else {
187:             // after we've stored the first rival we dont need to keep a record of any
188:             // other rival edges - they will all have a zero time unrivaled
191:         }
```

Modify the `EdgeChallengeManagerLib::add(...)` function as shown below

```solidity
File: EdgeChallengeManagerLib.sol

182:         if (firstRival == 0) {
183:             store.firstRivals[mutualId] = UNRIVALED;

184:   -     } else if (firstRival == UNRIVALED) {

184:   +     } else (firstRival == UNRIVALED) {

185:             store.firstRivals[mutualId] = eId;
186:   -     } else {
187:   -         // after we've stored the first rival we dont need to keep a record of any
188:   -         // other rival edges - they will all have a zero time unrivaled
191:   -     }
```
