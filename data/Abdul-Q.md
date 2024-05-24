## [N-1] Inconsistency between Modifier Name and Logic

##### Instance 

https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/bridge/SequencerInbox.sol#L108C1-L113C6

##### Detail

The issue lies in the naming of the modifier “onlyRollupOwnerOrBatchPosterManager”. The name suggests that the modifier should allow access to either the rollupOwner or the BatchPosterManager. However, the logic within the modifier checks if the rollupOwner is the BatchPosterManager, which is a specific condition rather than a general one.

Therefore, the modifier name does not accurately reflect the logic used within it. A more appropriate name, based on the logic, could be “isRollupOwner_A_BatchPosterManager” or something similar that indicates the rollupOwner and BatchPosterManager are the same entity. This would make the code more readable and less prone to misunderstandings.


## [N-2] Unnecessary imports

##### Instances

-