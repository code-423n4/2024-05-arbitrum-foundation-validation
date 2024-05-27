# [L-01] TransparentUpgradeableProxy clashing selector calls may not be delegated
## Impact
The protocol uses v4.7.0 of OZ TransparentUpgradeableProxy. However there is a known issue associated with this contract in versions - >=3.2.0 <4.8.3

A function in the implementation contract may be inaccessible if its selector clashes with one of the proxy's own selectors. Specifically, if the clashing function has a different signature with incompatible ABI encoding, the proxy could revert while attempting to decode the arguments from calldata.

The probability of an accidental clash is negligible, but one could be caused deliberately.

More:
* https://github.com/OpenZeppelin/openzeppelin-contracts/security/advisories/GHSA-mx2q-35m2-x2rh
* https://github.com/OpenZeppelin/openzeppelin-contracts/pull/4154
## Proof of Concept
The contracts that uses this version of the OZ library are:
* `BOLDUpgreadeAction.sol`
* `BridgeCreator.sol`
* `RollupCreator.sol`
## Tools Used
Manual review
## Recommended Mitigation Steps
Upgrade to OZ contract version >= 4.8.3

# [L-02] Missing parameter validation
## Impact
The only lack of validation in `EdgeChallengeManager.sol` `initialize` function is for the `stakeToken`
## Proof of Concept
https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/challengeV2/EdgeChallengeManager.sol#L330
## Tools Used
Manual review
## Recommended Mitigation Steps
Ensure that the input is valid token address: `address(_stakeToken) != address(0)`

# [L-03] Uninitialized state variable
## Impact
In `SequencerInbox.sol` contract `__LEGACY_MAX_TIME_VARIATION` state variable is neither initialized  nor used
## Proof of Concept
https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/bridge/SequencerInbox.sol#L99
## Tools Used
Manual review
## Recommended Mitigation Steps
It is recommended to initialize all internal variables or remove them if they will not be used in future

# [L-04] Floating pragma is used among the contracts
## Impact
Contracts should be deployed with the same compiler version and flags that they have been tested with thoroughly. Locking the pragma helps to ensure that contracts do not accidentally get deployed using, for example, an outdated compiler version that might introduce bugs that affect the contract system negatively.
## Tools Used
Manual review
## Recommended Mitigation Steps
Lock the pragma version and also consider known bugs (https://github.com/ethereum/solidity/releases) for the compiler version that is chosen.

# [L-05] Different pragma versions used 
## Impact
Contracts have different solidity compiler ranges referenced `>=0.6.9 <0.9.0`,  `^0.8.0`, `^0.8.4`, `^0.8.17`
## Proof of Concept
https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/bridge/DelayBuffer.sol
https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/bridge/ISequencerInbox.sol
https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/challengeV2/libraries/ArrayUtilsLib.sol
https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/challengeV2/libraries/ChallengeEdgeLib.sol
https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/libraries/Error.sol
## Tools Used
Manual review
## Recommended Mitigation Steps
Use the same pragma version and also consider known bugs (https://github.com/ethereum/solidity/releases) for the compiler version that is chosen.

# [G-01] Unnecessary check for Edge existance
## Impact
When the `confirmEdgeByOneStepProof` function is called from `EdgeChallengeManager.sol`, the existence of the edgeId is checked twice, leading to redundant checks that could be optimized for better performance and gas savings.
## Proof of Concept
The first check is performed in `store.getPrevAssertionHash` function:
https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/challengeV2/EdgeChallengeManager.sol#L546
```solidity
    bytes32 prevAssertionHash = store.getPrevAssertionHash(edgeId);
```
The second check is performed when we call `store.confirmEdgeByOneStepProof`:
https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/challengeV2/libraries/EdgeChallengeManagerLib.sol#L778

```solidity
    if (!store.edges[edgeId].exists()) {
        revert EdgeNotExists(edgeId);
    }
```
## Tools Used
Manual review
## Recommended Mitigation Steps
The second check can be removed for additional gas saving.

# [I-01] Unused imported interface
## Impact
The imported interface `IRollupLogic` in `IAssertionStakingPoolCreator.sol` is not used
## Proof of Concept
https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/assertionStakingPool/interfaces/IAssertionStakingPoolCreator.sol#L7
## Tools Used
Manual review
## Recommended Mitigation Steps
Consider removing the unused imports

# [I-02] Unused imported Errors
## Impact
The following imported errors are not used in `SequencerInbox.sol` - `BadPostUpgradeInit`, `ForceIncludeTimeTooSoon`
## Proof of Concept
https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/bridge/SequencerInbox.sol
## Tools Used
Manual review
## Recommended Mitigation Steps
Remove the unused imports