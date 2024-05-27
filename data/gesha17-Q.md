# [L-01] updateRollupAddress() does not emit an event.

## Summary:
updateRollupAddress() in SequencerInbox.sol is a critical update function that should emit an event.

[(link)](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/bridge/SequencerInbox.sol#L208)
```js
    /// @notice Allows the rollup owner to sync the rollup address
    function updateRollupAddress() external {
        if (msg.sender != IOwnable(rollup).owner())
            revert NotOwner(msg.sender, IOwnable(rollup).owner());
        IOwnable newRollup = bridge.rollup();
        if (rollup == newRollup) revert RollupNotChanged();
        rollup = newRollup;
    }
```

The rollup address is central to the functionality of the protocol. The update function should emit an event for offchain monitoring parties.

## Mitigation Steps:
Emit an event from function.

# [L-02] Duplicate checks in EdgeChallangeManagerLib

## Summary:
The layerZeroTypeSpecificChecks() function checks the start and end state machine status:

[(link)](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/challengeV2/libraries/EdgeChallengeManagerLib.sol#L255)
```js
    if (ard.startState.machineStatus == MachineStatus.RUNNING) {
        revert EmptyStartMachineStatus();
    }
    if (ard.endState.machineStatus == MachineStatus.RUNNING) {
        revert EmptyEndMachineStatus();
    }

    // Create machine hashes out of the proven state
    bytes32 startStateHash = oneStepProofEntry.getMachineHash(ard.startState.toExecutionState());
    bytes32 endStateHash = oneStepProofEntry.getMachineHash(ard.endState.toExecutionState());

```

This is not necessary since the getMachineHash function in the OneStepProofEntry contract will do that check anyway.

[(link)](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/osp/OneStepProofEntry.sol#L75)
```js
    function getMachineHash(ExecutionState calldata execState) external pure override returns (bytes32) {
        if (execState.machineStatus == MachineStatus.FINISHED) {
            return keccak256(abi.encodePacked("Machine finished:", execState.globalState.hash()));
        } else if (execState.machineStatus == MachineStatus.ERRORED) {
            return keccak256(abi.encodePacked("Machine errored:", execState.globalState.hash()));
        } else {
            revert("BAD_MACHINE_STATUS");
        }
    }
```

This is technical debt that is being carried forward and can confuse developers.

## Mitigation Steps:
Only check for this in one place.