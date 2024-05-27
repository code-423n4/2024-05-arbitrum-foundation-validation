### Incorrect total time unrivaled returned by EdgeChallengeManager

The `timeUnrivaled` function of the `EdgeChallengeManager` contract returns the value of `EdgeChallengeManagerLib::timeUnrivaled`, instead of `timeUnrivaledTotal`. The latter accounts for the inherited timer on top of the edge’s timer.

On top of this there're no public getters for the `timeUnrivaledTotal` value, which is the one that actually matters to confirm a challenge.

Either add a public getter for `timeUnrivaledTotal`, or modify the code so that `EdgeChallengeManager::timeUnrivaled` returns the total time.