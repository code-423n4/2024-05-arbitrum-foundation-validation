### Prevent re-setting a state variable with the same value
Not only is wasteful in terms of gas, but this is especially problematic when an event is emitted and the old and new values set are the same, as listeners might not expect this kind of scenario.

```solidity
Path: ./src/bridge/SequencerInbox.sol

852:            buffer.bufferBlocks = bufferConfig_.max;	// @audit-issue

855:            buffer.bufferBlocks = bufferConfig_.threshold;	// @audit-issue

857:        buffer.max = bufferConfig_.max;	// @audit-issue

858:        buffer.threshold = bufferConfig_.threshold;	// @audit-issue

859:        buffer.replenishRateInBasis = bufferConfig_.replenishRateInBasis;	// @audit-issue

878:        delayBlocks = uint64(maxTimeVariation_.delayBlocks);	// @audit-issue

879:        futureBlocks = uint64(maxTimeVariation_.futureBlocks);	// @audit-issue

880:        delaySeconds = uint64(maxTimeVariation_.delaySeconds);	// @audit-issue

881:        futureSeconds = uint64(maxTimeVariation_.futureSeconds);	// @audit-issue

898:        isBatchPoster[addr] = isBatchPoster_;	// @audit-issue

937:        isSequencer[addr] = isSequencer_;	// @audit-issue

943:        batchPosterManager = newBatchPosterManager;	// @audit-issue
```
[852](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/bridge/SequencerInbox.sol#L852-L852), [855](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/bridge/SequencerInbox.sol#L855-L855), [857](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/bridge/SequencerInbox.sol#L857-L857), [858](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/bridge/SequencerInbox.sol#L858-L858), [859](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/bridge/SequencerInbox.sol#L859-L859), [878](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/bridge/SequencerInbox.sol#L878-L878), [879](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/bridge/SequencerInbox.sol#L879-L879), [880](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/bridge/SequencerInbox.sol#L880-L880), [881](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/bridge/SequencerInbox.sol#L881-L881), [898](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/bridge/SequencerInbox.sol#L898-L898), [937](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/bridge/SequencerInbox.sol#L937-L937), [943](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/bridge/SequencerInbox.sol#L943-L943), 


```solidity
Path: ./src/rollup/BOLDUpgradeAction.sol

108:        preImages[h] = abi.encode(executionState, inboxMaxCount);	// @audit-issue
```
[108](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/BOLDUpgradeAction.sol#L108-L108), 


```solidity
Path: ./src/rollup/BridgeCreator.sol

54:        ethBasedTemplates = _newTemplates;	// @audit-issue

59:        erc20BasedTemplates = _newTemplates;	// @audit-issue
```
[54](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/BridgeCreator.sol#L54-L54), [59](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/BridgeCreator.sol#L59-L59), 


```solidity
Path: ./src/rollup/RollupCore.sol

228:        _assertions[assertionHash] = initialAssertion;	// @audit-issue

229:        _latestConfirmed = assertionHash;	// @audit-issue

277:        _stakerMap[stakerAddress] = Staker(depositAmount, _latestConfirmed, stakerIndex, true, withdrawalAddress);	// @audit-issue
```
[228](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/RollupCore.sol#L228-L228), [229](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/RollupCore.sol#L229-L229), [277](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/RollupCore.sol#L277-L277), 


```solidity
Path: ./src/rollup/RollupCreator.sol

73:        bridgeCreator = _bridgeCreator;	// @audit-issue

74:        osp = _osp;	// @audit-issue

75:        challengeManagerTemplate = _challengeManagerLogic;	// @audit-issue

76:        rollupAdminLogic = _rollupAdminLogic;	// @audit-issue

77:        rollupUserLogic = _rollupUserLogic;	// @audit-issue

78:        upgradeExecutorLogic = _upgradeExecutorLogic;	// @audit-issue

79:        validatorWalletCreator = _validatorWalletCreator;	// @audit-issue

80:        l2FactoriesDeployer = _l2FactoriesDeployer;	// @audit-issue
```
[73](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/RollupCreator.sol#L73-L73), [74](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/RollupCreator.sol#L74-L74), [75](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/RollupCreator.sol#L75-L75), [76](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/RollupCreator.sol#L76-L76), [77](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/RollupCreator.sol#L77-L77), [78](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/RollupCreator.sol#L78-L78), [79](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/RollupCreator.sol#L79-L79), [80](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/RollupCreator.sol#L80-L80), 


```solidity
Path: ./src/rollup/RollupAdminLogic.sol

118:        outbox = _outbox;	// @audit-issue

185:            isValidator[_validator[i]] = _val[i];	// @audit-issue

205:        minimumAssertionPeriod = newPeriod;	// @audit-issue

224:        baseStake = newBaseStake;	// @audit-issue

282:        wasmModuleRoot = newWasmModuleRoot;	// @audit-issue

300:        inbox = newInbox;	// @audit-issue

309:        validatorWhitelistDisabled = _validatorWhitelistDisabled;	// @audit-issue

318:        anyTrustFastConfirmer = _anyTrustFastConfirmer;	// @audit-issue

327:        challengeManager = IEdgeChallengeManager(_challengeManager);	// @audit-issue
```
[118](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/RollupAdminLogic.sol#L118-L118), [185](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/RollupAdminLogic.sol#L185-L185), [205](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/RollupAdminLogic.sol#L205-L205), [224](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/RollupAdminLogic.sol#L224-L224), [282](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/RollupAdminLogic.sol#L282-L282), [300](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/RollupAdminLogic.sol#L300-L300), [309](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/RollupAdminLogic.sol#L309-L309), [318](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/RollupAdminLogic.sol#L318-L318), [327](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/RollupAdminLogic.sol#L327-L327), 


#### Recommendation

Implement checks in your Solidity contracts to avoid re-setting state variables to their existing values. Prior to updating a state variable, compare the new value with the current value and proceed with the assignment only if they differ. Additionally, ensure that events related to state variable updates are emitted only when actual changes occur. This approach not only saves gas but also prevents confusion and unnecessary triggers in event listeners. Regularly reviewing and optimizing your contract for such redundancies can significantly enhance efficiency and clarity in contract operations.

### Unnecessary Assert
Unnecessary `assert` statements in Solidity contracts can have several detrimental impacts on code readability, gas efficiency, and overall contract functionality. `assert` statements are typically used to check for conditions that should never occur under normal circumstances. While they can be valuable for catching unexpected errors and halting contract execution, their misuse can lead to unnecessary complexity and increased gas costs.


```solidity
Path: ./src/bridge/SequencerInbox.sol

651:        assert(header.length == HEADER_LENGTH);	// @audit-issue
```
[651](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/bridge/SequencerInbox.sol#L651-L651), 


```solidity
Path: ./src/challengeV2/libraries/MerkleTreeLib.sol

340:            assert(size <= postSize);	// @audit-issue
```
[340](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/challengeV2/libraries/MerkleTreeLib.sol#L340-L340), 


#### Recommendation

Use 'assert' statements in Solidity judiciously, reserving them for conditions that indicate critical and unforeseen errors. Avoid overuse to maintain code clarity and prevent unnecessary gas consumption due to these costly checks.

### Cache Local Variable Array Length In For Loop
If not cached, the solidity compiler will always read the length of the array during each iteration. If it is a memory array, this is an extra mload operation (3 additional gas for each iteration except for the first).

```solidity
Path: ./src/rollup/BOLDUpgradeAction.sol

528:            for (uint256 i = 0; i < validators.length; i++) {	// @audit-issue
```
[528](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/BOLDUpgradeAction.sol#L528-L528), 


```solidity
Path: ./src/rollup/RollupCreator.sol

225:        for (uint256 i = 0; i < deployParams.batchPosters.length; i++) {	// @audit-issue

235:            for (uint256 i = 0; i < deployParams.validators.length; i++) {	// @audit-issue
```
[225](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/RollupCreator.sol#L225-L225), [235](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/RollupCreator.sol#L235-L235), 


```solidity
Path: ./src/rollup/RollupAdminLogic.sol

184:        for (uint256 i = 0; i < _validator.length; i++) {	// @audit-issue

230:        for (uint256 i = 0; i < staker.length; i++) {	// @audit-issue
```
[184](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/RollupAdminLogic.sol#L184-L184), [230](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/RollupAdminLogic.sol#L230-L230), 


```solidity
Path: ./src/challengeV2/EdgeChallengeManager.sol

492:        for (uint256 i = 0; i < edgeIds.length; i++) {	// @audit-issue
```
[492](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/challengeV2/EdgeChallengeManager.sol#L492-L492), 


```solidity
Path: ./src/challengeV2/libraries/ArrayUtilsLib.sol

15:        for (uint256 i = 0; i < arr.length; i++) {	// @audit-issue

47:        for (uint256 i = 0; i < arr1.length; i++) {	// @audit-issue

50:        for (uint256 i = 0; i < arr2.length; i++) {	// @audit-issue
```
[15](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/challengeV2/libraries/ArrayUtilsLib.sol#L15-L15), [47](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/challengeV2/libraries/ArrayUtilsLib.sol#L47-L47), [50](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/challengeV2/libraries/ArrayUtilsLib.sol#L50-L50), 


```solidity
Path: ./src/challengeV2/libraries/MerkleTreeLib.sol

115:        for (uint256 i = 0; i < me.length; i++) {	// @audit-issue

188:        for (uint256 i = 0; i < me.length; i++) {	// @audit-issue

294:        for (uint256 i = 0; i < me.length; i++) {	// @audit-issue
```
[115](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/challengeV2/libraries/MerkleTreeLib.sol#L115-L115), [188](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/challengeV2/libraries/MerkleTreeLib.sol#L188-L188), [294](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/challengeV2/libraries/MerkleTreeLib.sol#L294-L294), 


#### Recommendation

To optimize gas consumption, cache the length of memory arrays before for loop iterations in Solidity. This reduces redundant mload operations, saving 3 gas per iteration after the first and improving overall contract efficiency.

### State Variable Access Within a Loop
State variable reads and writes are more expensive than local variable reads and writes. Therefore, it is recommended to replace state variable reads and writes within loops with a local variable. Gas savings should be multiplied by the average loop length.

```solidity
Path: ./src/rollup/RollupAdminLogic.sol

185:            isValidator[_validator[i]] = _val[i];	// @audit-issue: `isValidator` used in loop.
```
[185](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/RollupAdminLogic.sol#L185-L185), 


```solidity
Path: ./src/challengeV2/EdgeChallengeManager.sol

493:            (bool updated, uint256 newValue) = store.updateTimerCacheByChildren(edgeIds[i]);	// @audit-issue: `store` used in loop.
```
[493](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/challengeV2/EdgeChallengeManager.sol#L493-L493), 


#### Recommendation

Optimize gas usage in Solidity by replacing state variable reads and writes within loops with local variable operations. This reduces gas costs significantly, especially when multiplied by the average loop length.

### Unnecessary Assignment
The identified issue involves an unnecessary step of assigning a condition's result to a boolean variable before using it in an if-statement. This extra variable assignment is not required as the condition can be directly evaluated within the if-statement itself, making the code more concise and efficient.

```solidity
Path: ./src/rollup/BridgeCreator.sol

107:        bool isDelayBufferable = bufferConfig.threshold != 0;	// @audit-issue: This assignment is not needed. Binary operation can be used in condition directly.
108:
109:        // create ETH-based bridge if address zero is provided for native token, otherwise create ERC20-based bridge
110:        BridgeContracts memory frame = _createBridge(
111:            adminProxy,
112:            nativeToken == address(0) ? ethBasedTemplates : erc20BasedTemplates,
113:            isDelayBufferable
```
[107](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/BridgeCreator.sol#L107-L113), 


```solidity
Path: ./src/rollup/RollupCore.sol

571:        bool isLatestConfirmed = lastestAssertion == latestConfirmed();	// @audit-issue: This assignment is not needed. Binary operation can be used in condition directly.
572:        bool haveChild = getAssertionStorage(lastestAssertion).firstChildBlock > 0;
573:        require(isLatestConfirmed || haveChild, "STAKE_ACTIVE");

572:        bool haveChild = getAssertionStorage(lastestAssertion).firstChildBlock > 0;	// @audit-issue: This assignment is not needed. Binary operation can be used in condition directly.
573:        require(isLatestConfirmed || haveChild, "STAKE_ACTIVE");
```
[571](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/RollupCore.sol#L571-L573), [572](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/RollupCore.sol#L572-L573), 


```solidity
Path: ./src/challengeV2/EdgeChallengeManager.sol

521:        bool isBlockLevel = ChallengeEdgeLib.levelToType(topEdge.level, NUM_BIGSTEP_LEVEL) == EdgeType.Block;	// @audit-issue: This assignment is not needed. Binary operation can be used in condition directly.
522:        if (isBlockLevel && assertionChain.isFirstChild(topEdge.claimId)) {
```
[521](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/challengeV2/EdgeChallengeManager.sol#L521-L522), 


#### Recommendation

Review your Solidity code for instances where boolean variables are unnecessarily assigned from conditions only to be used in immediate if-statements. Simplify these constructs by directly placing the conditional expression within the if-statement, eliminating the intermediary boolean variable. This practice not only streamlines your code, making it more concise, but also potentially reduces gas costs by minimizing the operations performed. Refactoring in this manner can enhance the readability and efficiency of your smart contracts. Always ensure that such optimizations maintain the original logic and intent of the code.

### Unnecessary casting as variable is already of the same type
In Solidity, explicitly casting a variable to a type that it already represents is redundant and can lead to confusion and clutter in the code. This unnecessary casting doesn't typically consume additional gas since Solidity's optimizer often removes such redundant conversions during compilation. However, it does affect code readability and may obscure the actual intent of the code, making it harder for developers to understand and maintain. Ensuring that casting is used only when necessary helps maintain clean, clear, and efficient code.

```solidity
Path: ./src/rollup/BOLDUpgradeAction.sol

475:                    address(IMPL_CHALLENGE_MANAGER),	// @audit-issue: Variable `IMPL_CHALLENGE_MANAGER` is converted to `address` from type `address`.
```
[475](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/BOLDUpgradeAction.sol#L475-L475), 


```solidity
Path: ./src/rollup/RollupCreator.sol

204:        proxyAdmin.transferOwnership(address(upgradeExecutor));	// @audit-issue: Variable `upgradeExecutor` is converted to `address` from type `address`.

241:        IRollupAdmin(address(rollup)).setOwner(address(upgradeExecutor));	// @audit-issue: Variable `upgradeExecutor` is converted to `address` from type `address`.

261:            address(upgradeExecutor),	// @audit-issue: Variable `upgradeExecutor` is converted to `address` from type `address`.
```
[204](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/RollupCreator.sol#L204-L204), [241](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/RollupCreator.sol#L241-L241), [261](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/RollupCreator.sol#L261-L261), 


```solidity
Path: ./src/rollup/RollupAdminLogic.sol

139:        bridge.setDelayedInbox(address(_inbox), _enabled);	// @audit-issue: Variable `_inbox` is converted to `address` from type `address`.
```
[139](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/RollupAdminLogic.sol#L139-L139), 


```solidity
Path: ./src/assertionStakingPool/EdgeStakingPool.sol

46:        IERC20(stakeToken).safeIncreaseAllowance(address(challengeManager), requiredStake);	// @audit-issue: Variable `challengeManager` is converted to `address` from type `address`.
```
[46](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/assertionStakingPool/EdgeStakingPool.sol#L46-L46), 


#### Recommendation

Review your Solidity code for instances of unnecessary casting where variables are cast to their own type. Remove these redundant casts to enhance code clarity and maintainability. When writing new code, ensure that casting is only applied when changing a variable's type is genuinely needed. This practice helps in keeping the codebase straightforward and understandable, reducing potential confusion and errors associated with misinterpreting the variable types.

### Shortcircuit rules can be be used to optimize some gas usage
Some conditions may be reordered to save an SLOAD (2100 gas), as we avoid reading state variables when the first part of the condition fails (with `&&`), or succeeds (with `||`).

```solidity
Path: ./src/bridge/SequencerInbox.sol

711:            if (data[0] & DAS_MESSAGE_HEADER_FLAG != 0 && data.length >= 33) {	// @audit-issue: Control with `DAS_MESSAGE_HEADER_FLAG` can be done after all non state variable/function call controls.
```
[711](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/bridge/SequencerInbox.sol#L711-L711), 


#### Recommendation

Review your Solidity contracts for conditional statements that use `&&` and `||` operators. Prioritize conditions that are less gas-intensive or have a higher likelihood of determining the outcome of the entire expression. For instance, if a condition involves an `SLOAD` operation and another is a simple variable comparison, evaluate the simpler condition first:
Before optimization:
```solidity
if (contractStateVariable > value && isEligible(msg.sender)) {
    // Execution logic
}

After optimization:
```solidity
if (isEligible(msg.sender) && contractStateVariable > value) {
    // Execution logic
}

This rearrangement ensures that if `isEligible(msg.sender)` returns false, the contract avoids the gas cost associated with reading `contractStateVariable` from storage. Apply this principle across your contract's logic where applicable, especially in functions called frequently or in gas-sensitive contexts. Testing remains crucial; ensure that the reordering of conditions does not alter the intended logic or outcomes of your contract.

### Same cast is done multiple times
It's cheaper to do it once, and store the result to a variable.

```solidity
Path: ./src/bridge/SequencerInbox.sol

225:            bounds.minTimestamp = uint64(block.timestamp) - delaySeconds_;	// @audit-issue: Same casting also done in line(s): `[227]`.

229:            bounds.minBlockNumber = uint64(block.number) - delayBlocks_;	// @audit-issue: Same casting also done in line(s): `[231]`.
```
[225](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/bridge/SequencerInbox.sol#L225-L225), [229](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/bridge/SequencerInbox.sol#L229-L229), 


```solidity
Path: ./src/rollup/BOLDUpgradeAction.sol

362:        DoubleLogicUUPSUpgradeable(address(OLD_ROLLUP)).upgradeSecondaryTo(IMPL_PATCHED_OLD_ROLLUP_USER);	// @audit-issue: Same casting also done in line(s): `[357, 342]`.

538:        IRollupAdmin(address(rollup)).setOwner(actualOwner);	// @audit-issue: Same casting also done in line(s): `[532, 517, 535]`.
```
[362](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/BOLDUpgradeAction.sol#L362-L362), [538](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/BOLDUpgradeAction.sol#L538-L538), 


```solidity
Path: ./src/rollup/Assertion.sol

89:            self.secondChildBlock = uint64(block.number);	// @audit-issue: Same casting also done in line(s): `[87]`.
```
[89](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/Assertion.sol#L89-L89), 


```solidity
Path: ./src/rollup/BridgeCreator.sol

120:            IERC20Bridge(address(frame.bridge)).initialize(IOwnable(rollup), nativeToken);	// @audit-issue: Same casting also done in line(s): `[118]`.
```
[120](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/BridgeCreator.sol#L120-L120), 


```solidity
Path: ./src/rollup/RollupCore.sol

512:            address(challengeManager),	// @audit-issue: Same casting also done in line(s): `[493]`.
```
[512](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/RollupCore.sol#L512-L512), 


```solidity
Path: ./src/rollup/RollupCreator.sol

258:            address(proxyAdmin),	// @audit-issue: Same casting also done in line(s): `[198, 191]`.

192:            address(rollup),	// @audit-issue: Same casting also done in line(s): `[198, 264, 238, 241, 252]`.

241:        IRollupAdmin(address(rollup)).setOwner(address(upgradeExecutor));	// @audit-issue: Same casting also done in line(s): `[204, 261]`.

245:                address(bridgeContracts.inbox),	// @audit-issue: Same casting also done in line(s): `[254]`.

282:        upgradeExecutor.initialize(address(upgradeExecutor), executors);	// @audit-issue: Same casting also done in line(s): `[284]`.
```
[258](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/RollupCreator.sol#L258-L258), [192](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/RollupCreator.sol#L192-L192), [241](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/RollupCreator.sol#L241-L241), [245](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/RollupCreator.sol#L245-L245), [282](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/RollupCreator.sol#L282-L282), 


```solidity
Path: ./src/rollup/RollupAdminLogic.sol

35:        if (!bridge.allowedDelayedInboxes(address(connectedContracts.rollupEventInbox))) {	// @audit-issue: Same casting also done in line(s): `[36]`.

81:                challengeManager: address(challengeManager),	// @audit-issue: Same casting also done in line(s): `[98]`.
```
[35](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/RollupAdminLogic.sol#L35-L35), [81](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/RollupAdminLogic.sol#L81-L81), 


```solidity
Path: ./src/challengeV2/EdgeChallengeManager.sol

584:        emit EdgeRefunded(edgeId, store.edges[edgeId].mutualId(), address(st), sa);	// @audit-issue: Same casting also done in line(s): `[580]`.
```
[584](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/challengeV2/EdgeChallengeManager.sol#L584-L584), 


#### Recommendation

Identify instances in your Solidity contracts where the same value is cast to another type multiple times. Refactor these operations by performing the cast once and storing the result in a local variable. Use this variable for all subsequent operations requiring the cast value.

### Conditions Can Be Optimized
The way conditional statements are written can significantly impact the contract's gas efficiency, readability, and overall maintainability. Complex or poorly structured conditions can lead to increased execution costs and potential security vulnerabilities. There is often an opportunity to simplify and streamline these statements. By optimizing conditional logic, developers can create smarter contracts that are not only more cost-effective in terms of gas usage but also more secure and easier to understand and maintain. This optimization plays a crucial role in enhancing the performance and reliability of smart contracts on the Ethereum blockchain.

`require(bool_var)` is better than `require(bool_var == True)`.


```solidity
Path: ./src/challengeV2/libraries/ChallengeEdgeLib.sol

271:        if (edge.refunded == true) {	// @audit-issue
```
[271](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/challengeV2/libraries/ChallengeEdgeLib.sol#L271-L271), 


#### Recommendation

Optimize conditional statements in Solidity for better gas efficiency, readability, and maintainability. Simplify logic where possible and consider the cost implications of each condition to create more effective and secure smart contracts.

### It is a waste of GAS to emit variable literals
Emitting variable literals (true, false, address(0), 1 etc...) in events is inefficient, as it consumes extra gas without providing added value. These literals are fixed values that can be accessed or hardcoded elsewhere in the smart contract or application, making their inclusion in events redundant and an unnecessary drain on resources during transaction execution.

```solidity
Path: ./src/bridge/SequencerInbox.sol

890:        emit OwnerFunctionCalled(0);	// @audit-issue

899:        emit OwnerFunctionCalled(1);	// @audit-issue

918:        emit OwnerFunctionCalled(2);	// @audit-issue

929:        emit OwnerFunctionCalled(3);	// @audit-issue

938:        emit OwnerFunctionCalled(4); // Owner in this context can also be batch poster manager	// @audit-issue

944:        emit OwnerFunctionCalled(5);	// @audit-issue

949:        emit OwnerFunctionCalled(6);	// @audit-issue
```
[890](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/bridge/SequencerInbox.sol#L890-L890), [899](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/bridge/SequencerInbox.sol#L899-L899), [918](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/bridge/SequencerInbox.sol#L918-L918), [929](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/bridge/SequencerInbox.sol#L929-L929), [938](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/bridge/SequencerInbox.sol#L938-L938), [944](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/bridge/SequencerInbox.sol#L944-L944), [949](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/bridge/SequencerInbox.sol#L949-L949), 


```solidity
Path: ./src/rollup/RollupCore.sol

278:        emit UserStakeUpdated(stakerAddress, withdrawalAddress, 0, depositAmount);	// @audit-issue

323:        emit UserStakeUpdated(stakerAddress, withdrawalAddress, initialStaked, 0);	// @audit-issue

335:        emit UserWithdrawableFundsUpdated(account, amount, 0);	// @audit-issue
```
[278](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/RollupCore.sol#L278-L278), [323](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/RollupCore.sol#L323-L323), [335](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/RollupCore.sol#L335-L335), 


```solidity
Path: ./src/rollup/RollupAdminLogic.sol

120:        emit OwnerFunctionCalled(0);	// @audit-issue

130:        emit OwnerFunctionCalled(1);	// @audit-issue

140:        emit OwnerFunctionCalled(2);	// @audit-issue

152:        emit OwnerFunctionCalled(3);	// @audit-issue

160:        emit OwnerFunctionCalled(4);	// @audit-issue

187:        emit OwnerFunctionCalled(6);	// @audit-issue

197:        emit OwnerFunctionCalled(7);	// @audit-issue

206:        emit OwnerFunctionCalled(8);	// @audit-issue

216:        emit OwnerFunctionCalled(9);	// @audit-issue

225:        emit OwnerFunctionCalled(12);	// @audit-issue

234:        emit OwnerFunctionCalled(22);	// @audit-issue

255:        emit OwnerFunctionCalled(23);	// @audit-issue

266:        emit OwnerFunctionCalled(24);	// @audit-issue

274:        emit OwnerFunctionCalled(25);	// @audit-issue

283:        emit OwnerFunctionCalled(26);	// @audit-issue

292:        emit OwnerFunctionCalled(27);	// @audit-issue

301:        emit OwnerFunctionCalled(28);	// @audit-issue

310:        emit OwnerFunctionCalled(30);	// @audit-issue

319:        emit OwnerFunctionCalled(31);	// @audit-issue

328:        emit OwnerFunctionCalled(32);	// @audit-issue
```
[120](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/RollupAdminLogic.sol#L120-L120), [130](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/RollupAdminLogic.sol#L130-L130), [140](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/RollupAdminLogic.sol#L140-L140), [152](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/RollupAdminLogic.sol#L152-L152), [160](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/RollupAdminLogic.sol#L160-L160), [187](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/RollupAdminLogic.sol#L187-L187), [197](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/RollupAdminLogic.sol#L197-L197), [206](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/RollupAdminLogic.sol#L206-L206), [216](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/RollupAdminLogic.sol#L216-L216), [225](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/RollupAdminLogic.sol#L225-L225), [234](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/RollupAdminLogic.sol#L234-L234), [255](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/RollupAdminLogic.sol#L255-L255), [266](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/RollupAdminLogic.sol#L266-L266), [274](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/RollupAdminLogic.sol#L274-L274), [283](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/RollupAdminLogic.sol#L283-L283), [292](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/RollupAdminLogic.sol#L292-L292), [301](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/RollupAdminLogic.sol#L301-L301), [310](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/RollupAdminLogic.sol#L310-L310), [319](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/RollupAdminLogic.sol#L319-L319), [328](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/RollupAdminLogic.sol#L328-L328), 


#### Recommendation

Refrain from including fixed variable literals as parameters in your Solidity contract events. Evaluate your event emissions and remove literals that do not provide dynamic information about contract state or actions. For instance, instead of emitting an event with a `true` literal to indicate success, consider naming the event in a way that inherently indicates success or failure, such as `ActionSuccessful()`:
```solidity
// Before optimization
event ActionTaken(bool success);

// After optimization
event ActionSuccessful();
event ActionFailed();
```


### `event` Declared But Not Emitted
An event within the contract is declared but not utilized in any of the contract's functions or operations. Having unused event declarations can consume unnecessary space and may lead to misunderstandings for developers or users expecting this event as part of the contract's functionality.


```solidity
Path: ./src/rollup/BOLDUpgradeAction.sol

56:    event NodeCreated(	// @audit-issue
```
[56](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/BOLDUpgradeAction.sol#L56-L56), 


```solidity
Path: ./src/rollup/IRollupCore.sol

40:    event RollupChallengeStarted(	// @audit-issue
```
[40](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/IRollupCore.sol#L40-L40), 


#### Recommendation


Consider removing the unused event declaration to optimize the contract and enhance clarity. If there is an intent for this event to be part of certain operations, ensure it is emitted appropriately. Otherwise, for the sake of clean and efficient code, it is advisable to remove any unused declarations.


### Revert String Size Optimization
Shortening the revert strings to fit within 32 bytes will decrease deployment time and decrease runtime Gas when the revert condition is met.

Revert strings that are longer than 32 bytes require at least one additional `mstore`, along with additional overhead to calculate memory offset, etc.



```solidity
Path: ./src/rollup/BOLDUpgradeAction.sol

453:        require(	// @audit-issue: String length is `49`
454:            PROXY_ADMIN_SEQUENCER_INBOX.getProxyImplementation(sequencerInbox) == IMPL_SEQUENCER_INBOX,
455:            "DelayBuffer: new seq inbox implementation not set"
456:        );

457:        require(	// @audit-issue: String length is `38`
458:            ISequencerInbox(SEQ_INBOX).isDelayBufferable() == IS_DELAY_BUFFERABLE,
459:            "DelayBuffer: isDelayBufferable not set"
460:        );
```
[453](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/BOLDUpgradeAction.sol#L453-L456), [457](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/BOLDUpgradeAction.sol#L457-L460), 


```solidity
Path: ./src/rollup/RollupUserLogic.sol

124:            require(	// @audit-issue: String length is `33`
125:                block.number >= winningEdge.confirmedAtBlock + challengeGracePeriodBlocks,
126:                "CHALLENGE_GRACE_PERIOD_NOT_PASSED"
127:            );
```
[124](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/RollupUserLogic.sol#L124-L127), 


```solidity
Path: ./src/challengeV2/libraries/ArrayUtilsLib.sol

33:        require(endIndex <= arr.length, "End not less or equal than length");	// @audit-issue: String length is `33`
```
[33](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/challengeV2/libraries/ArrayUtilsLib.sol#L33-L33), 


```solidity
Path: ./src/challengeV2/libraries/MerkleTreeLib.sol

170:        require(level < me.length, "Level greater than highest level of current expansion");	// @audit-issue: String length is `53`

195:                require(me[i] == 0, "Append above least significant bit");	// @audit-issue: String length is `34`

322:        require(treeSize(preExpansion) == preSize, "Pre size does not match expansion");	// @audit-issue: String length is `33`

345:        require(root(exp) == postRoot, "Post expansion root not equal post");	// @audit-issue: String length is `34`
```
[170](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/challengeV2/libraries/MerkleTreeLib.sol#L170-L170), [195](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/challengeV2/libraries/MerkleTreeLib.sol#L195-L195), [322](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/challengeV2/libraries/MerkleTreeLib.sol#L322-L322), [345](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/challengeV2/libraries/MerkleTreeLib.sol#L345-L345), 


#### Recommendation


To optimize Gas usage in your Solidity contract, it is recommended to keep revert strings as short as possible and to ensure that they fit within 32 bytes. It is possible to use abbreviations or simplified error messages to keep the string length short. Doing so can reduce the amount of Gas used during deployment and runtime when the revert condition is met.


### Custom Errors in Solidity for Gas Efficiency
Starting from Solidity version 0.8.4, the language introduced a feature known as "custom errors". These custom errors provide a way for developers to define more descriptive and semantically meaningful error conditions without relying on string messages. Prior to this version, developers often used the `require` statement with string error messages to handle specific conditions or validations. However, every unique string used as a revert reason consumes gas, making transactions more expensive.

Custom errors, on the other hand, are identified by their name and the types of their parameters only, and they do not have the overhead of string storage. This means that, when using custom errors instead of `require` statements with string messages, the gas consumption can be significantly reduced, leading to more gas-efficient contracts.

```solidity
Path: ./src/bridge/SequencerInbox.sol

651:        assert(header.length == HEADER_LENGTH);	// @audit-issue
```
[651](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/bridge/SequencerInbox.sol#L651-L651), 


```solidity
Path: ./src/rollup/RollupLib.sol

77:        require(	// @audit-issue
78:            _configHash
79:                == configHash(
80:                    configData.wasmModuleRoot,
81:                    configData.requiredStake,
82:                    configData.challengeManager,
83:                    configData.confirmPeriodBlocks,
84:                    configData.nextInboxPosition
85:                ),
86:            "CONFIG_HASH_MISMATCH"
87:        );
```
[77](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/RollupLib.sol#L77-L87), 


```solidity
Path: ./src/rollup/BOLDUpgradeAction.sol

107:        require(h == stateHash(executionState, inboxMaxCount), "Invalid hash");	// @audit-issue

114:        require(inboxMaxCount != 0, "Hash not yet set");	// @audit-issue

378:        require(	// @audit-issue
379:            PREIMAGE_LOOKUP.stateHash(genesisAssertionState.toExecutionState(), inboxMaxCount)
380:                == latestConfirmedStateHash,
381:            "Invalid latest execution hash"
382:        );

453:        require(	// @audit-issue
454:            PROXY_ADMIN_SEQUENCER_INBOX.getProxyImplementation(sequencerInbox) == IMPL_SEQUENCER_INBOX,
455:            "DelayBuffer: new seq inbox implementation not set"
456:        );

457:        require(	// @audit-issue
458:            ISequencerInbox(SEQ_INBOX).isDelayBufferable() == IS_DELAY_BUFFERABLE,
459:            "DelayBuffer: isDelayBufferable not set"
460:        );

517:        require(address(rollup) == expectedRollupAddress, "UNEXPCTED_ROLLUP_ADDR");	// @audit-issue

529:                require(ROLLUP_READER.isValidator(validators[i]), "UNEXPECTED_NEW_VALIDATOR");
```
[107](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/BOLDUpgradeAction.sol#L107-L107), [114](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/BOLDUpgradeAction.sol#L114-L114), [378](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/BOLDUpgradeAction.sol#L378-L382), [453](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/BOLDUpgradeAction.sol#L453-L456), [457](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/BOLDUpgradeAction.sol#L457-L460), [517](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/BOLDUpgradeAction.sol#L517-L517), [526](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/BOLDUpgradeAction.sol#L529-L529), 


```solidity
Path: ./src/rollup/Assertion.sol

94:        require(self.status != AssertionStatus.NoAssertion, "ASSERTION_NOT_EXIST");	// @audit-issue
```
[94](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/Assertion.sol#L94-L94), 


```solidity
Path: ./src/rollup/RollupCore.sol

127:        require(assertionHash != bytes32(0), "ASSERTION_ID_CANNOT_BE_ZERO");	// @audit-issue

148:            require(blockNum > 0, "NO_ASSERTION");

244:        require(assertion.status == AssertionStatus.Pending, "NOT_PENDING");	// @audit-issue

247:        require(	// @audit-issue
248:            assertionHash
249:                == RollupLib.assertionHash({
250:                    parentAssertionHash: parentAssertionHash,
251:                    afterState: confirmState,
252:                    inboxAcc: inboxAcc
253:                }),
254:            "CONFIRM_DATA"
255:        );

304:        require(target <= current, "TOO_LITTLE_STAKE");	// @audit-issue

357:        require(staker.isStaked, "NOT_STAKED");	// @audit-issue

378:        require(	// @audit-issue
379:            assertion.afterState.machineStatus == MachineStatus.FINISHED
380:                || assertion.afterState.machineStatus == MachineStatus.ERRORED,
381:            "BAD_AFTER_STATUS"
382:        );

385:        require(	// @audit-issue
386:            RollupLib.assertionHash(
387:                assertion.beforeStateData.prevPrevAssertionHash,
388:                assertion.beforeState,
389:                assertion.beforeStateData.sequencerBatchAcc
390:            ) == prevAssertionHash,
391:            "INVALID_BEFORE_STATE"
392:        );

399:        require(assertion.beforeState.machineStatus == MachineStatus.FINISHED, "BAD_PREV_STATUS");	// @audit-issue

424:            require(afterGS.comparePositions(beforeGS) >= 0, "INBOX_BACKWARDS");

427:            require(afterStateCmpMaxInbox <= 0, "INBOX_TOO_FAR");

433:                require(afterGS.comparePositions(beforeGS) > 0, "OVERFLOW_STANDSTILL");

438:            require(afterGS.comparePositionsAgainstStartOfBatch(currentInboxPosition) <= 0, "INBOX_PAST_END");

445:            require(
446:                assertion.beforeStateData.configData.nextInboxPosition <= currentInboxPosition, "INBOX_NOT_POPULATED"
447:            );

466:            require(afterInboxPosition != 0, "EMPTY_INBOX_COUNT");

477:        require(	// @audit-issue
478:            newAssertionHash == expectedAssertionHash || expectedAssertionHash == bytes32(0),
479:            "UNEXPECTED_ASSERTION_HASH"
480:        );

485:        require(getAssertionStorage(newAssertionHash).status == AssertionStatus.NoAssertion, "ASSERTION_SEEN");	// @audit-issue

546:        require(assertionHash == RollupLib.assertionHash(prevAssertionHash, state, inboxAcc), "INVALID_ASSERTION_HASH");	// @audit-issue

566:        require(isStaked(stakerAddress), "NOT_STAKED");	// @audit-issue

573:        require(isLatestConfirmed || haveChild, "STAKE_ACTIVE");	// @audit-issue
```
[127](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/RollupCore.sol#L127-L127), [146](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/RollupCore.sol#L148-L148), [244](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/RollupCore.sol#L244-L244), [247](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/RollupCore.sol#L247-L255), [304](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/RollupCore.sol#L304-L304), [357](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/RollupCore.sol#L357-L357), [378](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/RollupCore.sol#L378-L382), [385](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/RollupCore.sol#L385-L392), [399](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/RollupCore.sol#L399-L399), [405](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/RollupCore.sol#L424-L424), [405](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/RollupCore.sol#L427-L427), [405](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/RollupCore.sol#L433-L433), [405](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/RollupCore.sol#L438-L438), [405](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/RollupCore.sol#L445-L447), [405](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/RollupCore.sol#L466-L466), [477](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/RollupCore.sol#L477-L480), [485](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/RollupCore.sol#L485-L485), [546](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/RollupCore.sol#L546-L546), [566](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/RollupCore.sol#L566-L566), [573](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/RollupCore.sol#L573-L573), 


```solidity
Path: ./src/rollup/RollupUserLogic.sol

21:        require(isValidator[msg.sender] || validatorWhitelistDisabled, "NOT_VALIDATOR");	// @audit-issue

28:        require(_stakeToken != address(0), "NEED_STAKE_TOKEN");	// @audit-issue

63:        require(!validatorWhitelistDisabled, "WHITELIST_DISABLED");	// @audit-issue

64:        require(_chainIdChanged(), "CHAIN_ID_NOT_CHANGED");	// @audit-issue

72:        require(!validatorWhitelistDisabled, "WHITELIST_DISABLED");	// @audit-issue

73:        require(_validatorIsAfk(), "VALIDATOR_NOT_AFK");	// @audit-issue

110:        require(block.number >= assertion.createdAtBlock + prevConfig.confirmPeriodBlocks, "BEFORE_DEADLINE");	// @audit-issue

113:        require(prevAssertionHash == latestConfirmed(), "PREV_NOT_LATEST_CONFIRMED");	// @audit-issue

118:            require(winningEdge.claimId == assertionHash, "NOT_WINNER");

119:            require(winningEdge.status == EdgeStatus.Confirmed, "EDGE_NOT_CONFIRMED");

120:            require(winningEdge.confirmedAtBlock != 0, "ZERO_CONFIRMED_AT_BLOCK");

124:            require(
125:                block.number >= winningEdge.confirmedAtBlock + challengeGracePeriodBlocks,
126:                "CHALLENGE_GRACE_PERIOD_NOT_PASSED"
127:            );

139:        require(!isStaked(msg.sender), "ALREADY_STAKED");	// @audit-issue

169:        require(	// @audit-issue
170:            expectedAssertionHash == bytes32(0)
171:                || getAssertionStorage(expectedAssertionHash).status == AssertionStatus.NoAssertion,
172:            "EXPECTED_ASSERTION_SEEN"
173:        );

175:        require(isStaked(msg.sender), "NOT_STAKED");	// @audit-issue

182:        require(amountStaked(msg.sender) >= assertion.beforeStateData.configData.requiredStake, "INSUFFICIENT_STAKE");	// @audit-issue

195:        require(	// @audit-issue
196:            lastAssertion == prevAssertion || getAssertionStorage(lastAssertion).firstChildBlock > 0,
197:            "STAKED_ON_ANOTHER_BRANCH"
198:        );

207:            require(timeSincePrev >= minimumAssertionPeriod, "TIME_DELTA");

233:        require(isStaked(stakerAddress), "NOT_STAKED");	// @audit-issue

258:        require(msg.sender == anyTrustFastConfirmer, "NOT_FAST_CONFIRMER");	// @audit-issue

278:        require(expectedAssertionHash != bytes32(0), "EXPECTED_ASSERTION_HASH");	// @audit-issue

337:        require(withdrawalAddress != address(0), "EMPTY_WITHDRAWAL_ADDRESS");	// @audit-issue

360:        require(amount > 0, "NO_FUNDS_TO_WITHDRAW");	// @audit-issue
```
[21](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/RollupUserLogic.sol#L21-L21), [28](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/RollupUserLogic.sol#L28-L28), [63](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/RollupUserLogic.sol#L63-L63), [64](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/RollupUserLogic.sol#L64-L64), [72](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/RollupUserLogic.sol#L72-L72), [73](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/RollupUserLogic.sol#L73-L73), [110](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/RollupUserLogic.sol#L110-L110), [113](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/RollupUserLogic.sol#L113-L113), [115](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/RollupUserLogic.sol#L118-L118), [115](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/RollupUserLogic.sol#L119-L119), [115](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/RollupUserLogic.sol#L120-L120), [115](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/RollupUserLogic.sol#L124-L127), [139](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/RollupUserLogic.sol#L139-L139), [169](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/RollupUserLogic.sol#L169-L173), [175](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/RollupUserLogic.sol#L175-L175), [182](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/RollupUserLogic.sol#L182-L182), [195](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/RollupUserLogic.sol#L195-L198), [204](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/RollupUserLogic.sol#L207-L207), [233](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/RollupUserLogic.sol#L233-L233), [258](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/RollupUserLogic.sol#L258-L258), [278](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/RollupUserLogic.sol#L278-L278), [337](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/RollupUserLogic.sol#L337-L337), [360](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/RollupUserLogic.sol#L360-L360), 


```solidity
Path: ./src/rollup/RollupCreator.sol

152:            require(
153:                deployParams.maxDataSize == ethSequencerInbox.maxDataSize(),
154:                "SI_MAX_DATA_SIZE_MISMATCH"
155:            );

156:            require(
157:                deployParams.maxDataSize == ethDelayBufferableSequencerInbox.maxDataSize(),
158:                "SI_MAX_DATA_SIZE_MISMATCH"
159:            );

160:            require(deployParams.maxDataSize == ethInbox.maxDataSize(), "I_MAX_DATA_SIZE_MISMATCH");

170:            require(
171:                deployParams.maxDataSize == erc20SequencerInbox.maxDataSize(),
172:                "SI_MAX_DATA_SIZE_MISMATCH"
173:            );

174:            require(
175:                deployParams.maxDataSize == erc20DelayBufferableSequencerInbox.maxDataSize(),
176:                "SI_MAX_DATA_SIZE_MISMATCH"
177:            );

178:            require(
179:                deployParams.maxDataSize == erc20Inbox.maxDataSize(),
180:                "I_MAX_DATA_SIZE_MISMATCH"
181:            );

305:            require(sent, "Refund failed");
```
[142](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/RollupCreator.sol#L152-L155), [142](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/RollupCreator.sol#L156-L159), [142](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/RollupCreator.sol#L160-L160), [142](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/RollupCreator.sol#L170-L173), [142](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/RollupCreator.sol#L174-L177), [142](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/RollupCreator.sol#L178-L181), [292](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/RollupCreator.sol#L305-L305), 


```solidity
Path: ./src/rollup/RollupAdminLogic.sol

57:        require(config.loserStakeEscrow != address(0), "INVALID_ESCROW_0");	// @audit-issue

128:        require(_outbox != address(outbox), "CUR_OUTBOX");	// @audit-issue

181:        require(_validator.length > 0, "EMPTY_ARRAY");	// @audit-issue

182:        require(_validator.length == _val.length, "WRONG_LENGTH");	// @audit-issue

214:        require(newConfirmPeriod > 0, "INVALID_CONFIRM_PERIOD");	// @audit-issue

229:        require(staker.length > 0, "EMPTY_ARRAY");	// @audit-issue

272:        require(newLoserStakerEscrow != address(0), "INVALID_ESCROW_0");	// @audit-issue
```
[57](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/RollupAdminLogic.sol#L57-L57), [128](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/RollupAdminLogic.sol#L128-L128), [181](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/RollupAdminLogic.sol#L181-L181), [182](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/RollupAdminLogic.sol#L182-L182), [214](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/RollupAdminLogic.sol#L214-L214), [229](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/RollupAdminLogic.sol#L229-L229), [272](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/RollupAdminLogic.sol#L272-L272), 


```solidity
Path: ./src/challengeV2/libraries/ArrayUtilsLib.sol

32:        require(startIndex < endIndex, "Start not less than end");	// @audit-issue

33:        require(endIndex <= arr.length, "End not less or equal than length");	// @audit-issue
```
[32](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/challengeV2/libraries/ArrayUtilsLib.sol#L32-L32), [33](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/challengeV2/libraries/ArrayUtilsLib.sol#L33-L33), 


```solidity
Path: ./src/challengeV2/libraries/MerkleTreeLib.sol

111:        require(me.length > 0, "Empty merkle expansion");	// @audit-issue

112:        require(me.length <= MAX_LEVEL, "Merkle expansion too large");	// @audit-issue

158:        require(level < MAX_LEVEL, "Level too high");	// @audit-issue

159:        require(subtreeRoot != 0, "Cannot append empty subtree");	// @audit-issue

160:        require(me.length <= MAX_LEVEL, "Merkle expansion too large");	// @audit-issue

170:        require(level < me.length, "Level greater than highest level of current expansion");	// @audit-issue

183:        require(next.length <= MAX_LEVEL, "Append creates oversize tree");	// @audit-issue

195:                require(me[i] == 0, "Append above least significant bit");

228:        require(next[next.length - 1] != 0, "Last entry zero");	// @audit-issue

265:        require(startSize < endSize, "Start not less than end");	// @audit-issue

287:        revert("Both y and z cannot be zero");	// @audit-issue

320:        require(preSize > 0, "Pre-size cannot be 0");	// @audit-issue

321:        require(root(preExpansion) == preRoot, "Pre expansion root mismatch");	// @audit-issue

322:        require(treeSize(preExpansion) == preSize, "Pre size does not match expansion");	// @audit-issue

323:        require(preSize < postSize, "Pre size not less than post size");	// @audit-issue

335:            require(proofIndex < proof.length, "Index out of range");

340:            assert(size <= postSize);

345:        require(root(exp) == postRoot, "Post expansion root not equal post");	// @audit-issue

349:        require(proofIndex == proof.length, "Incomplete proof usage");	// @audit-issue

364:        require(rootHash == calculatedRoot, "Invalid inclusion proof");	// @audit-issue
```
[111](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/challengeV2/libraries/MerkleTreeLib.sol#L111-L111), [112](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/challengeV2/libraries/MerkleTreeLib.sol#L112-L112), [158](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/challengeV2/libraries/MerkleTreeLib.sol#L158-L158), [159](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/challengeV2/libraries/MerkleTreeLib.sol#L159-L159), [160](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/challengeV2/libraries/MerkleTreeLib.sol#L160-L160), [170](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/challengeV2/libraries/MerkleTreeLib.sol#L170-L170), [183](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/challengeV2/libraries/MerkleTreeLib.sol#L183-L183), [188](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/challengeV2/libraries/MerkleTreeLib.sol#L195-L195), [228](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/challengeV2/libraries/MerkleTreeLib.sol#L228-L228), [265](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/challengeV2/libraries/MerkleTreeLib.sol#L265-L265), [287](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/challengeV2/libraries/MerkleTreeLib.sol#L287-L287), [320](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/challengeV2/libraries/MerkleTreeLib.sol#L320-L320), [321](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/challengeV2/libraries/MerkleTreeLib.sol#L321-L321), [322](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/challengeV2/libraries/MerkleTreeLib.sol#L322-L322), [323](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/challengeV2/libraries/MerkleTreeLib.sol#L323-L323), [332](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/challengeV2/libraries/MerkleTreeLib.sol#L335-L335), [332](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/challengeV2/libraries/MerkleTreeLib.sol#L340-L340), [345](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/challengeV2/libraries/MerkleTreeLib.sol#L345-L345), [349](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/challengeV2/libraries/MerkleTreeLib.sol#L349-L349), [364](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/challengeV2/libraries/MerkleTreeLib.sol#L364-L364), 


```solidity
Path: ./src/challengeV2/libraries/UintUtilsLib.sol

15:        require(x > 0, "Zero has no significant bits");	// @audit-issue

30:        require(x != 0, "Zero has no significant bits");	// @audit-issue
```
[15](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/challengeV2/libraries/UintUtilsLib.sol#L15-L15), [30](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/challengeV2/libraries/UintUtilsLib.sol#L30-L30), 


#### Recommendation


It is recommended to use custom errors instead of revert strings to reduce gas costs, especially during contract deployment. Custom errors can be defined using the error keyword and can include dynamic information.

### Avoid repeating computations
In Solidity development, repeating the same computations within a contract can lead to unnecessary gas consumption and reduce the contract's efficiency. This is particularly relevant in functions that are called frequently or involve complex calculations. Repeating computations not only wastes computational resources but also increases the cost of executing transactions. By identifying and eliminating redundant calculations, developers can optimize contract performance, reduce gas costs, and improve overall execution speed.

```solidity
Path: ./src/bridge/SequencerInbox.sol

301:            _totalDelayedMessagesRead - 1,	// @audit-issue: Same binary operation statement in line(s) between: ['322:322']
```
[301](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/bridge/SequencerInbox.sol#L301-L301), 


```solidity
Path: ./src/rollup/BridgeCreator.sol

112:            nativeToken == address(0) ? ethBasedTemplates : erc20BasedTemplates,	// @audit-issue: Same binary operation statement in line(s) between: ['117:117']
```
[112](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/BridgeCreator.sol#L112-L112), 


```solidity
Path: ./src/rollup/RollupCreator.sol

225:        for (uint256 i = 0; i < deployParams.batchPosters.length; i++) {	// @audit-issue: Same binary operation statement in line(s) between: ['235:235']
```
[225](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/RollupCreator.sol#L225-L225), 


```solidity
Path: ./src/challengeV2/EdgeChallengeManager.sol

360:        if (_numBigStepLevel + 2 != _stakeAmounts.length) {	// @audit-issue: Same binary operation statement in line(s) between: ['361:361']
```
[360](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/challengeV2/EdgeChallengeManager.sol#L360-L360), 


```solidity
Path: ./src/challengeV2/libraries/EdgeChallengeManagerLib.sol

248:            if (args.proof.length == 0) {	// @audit-issue: Same binary operation statement in line(s) between: ['294:294']

577:        if (end - start < 2) {	// @audit-issue: Same binary operation statement in line(s) between: ['580:580']

584:        uint256 diff = (end - 1) ^ start;	// @audit-issue: Same binary operation statement in line(s) between: ['587:587']
```
[248](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/challengeV2/libraries/EdgeChallengeManagerLib.sol#L248-L248), [577](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/challengeV2/libraries/EdgeChallengeManagerLib.sol#L577-L577), [584](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/challengeV2/libraries/EdgeChallengeManagerLib.sol#L584-L584), 


```solidity
Path: ./src/challengeV2/libraries/MerkleTreeLib.sol

118:                if (val != 0) {	// @audit-issue: Same binary operation statement in line(s) between: ['129:129']

195:                require(me[i] == 0, "Append above least significant bit");	// @audit-issue: Same binary operation statement in line(s) between: ['203:203']

223:            next[next.length - 1] = accumHash;	// @audit-issue: Same binary operation statement in line(s) between: ['228:228']
```
[118](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/challengeV2/libraries/MerkleTreeLib.sol#L118-L118), [195](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/challengeV2/libraries/MerkleTreeLib.sol#L195-L195), [223](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/challengeV2/libraries/MerkleTreeLib.sol#L223-L223), 


#### Recommendation

Review your Solidity contracts to identify any computations that are performed multiple times with the same inputs. Cache the results of these computations in local variables and reuse them within the function or across function calls if the state remains unchanged.

### Unused State Variables
There are state variables which are declared but not used in any function. This might increase the contract's gas usage unnecessarily.

```solidity
Path: ./src/bridge/SequencerInbox.sol

99:    ISequencerInbox.MaxTimeVariation private __LEGACY_MAX_TIME_VARIATION;	// @audit-issue
```
[99](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/bridge/SequencerInbox.sol#L99-L99), 


#### Recommendation

To optimize your contract's gas usage, remove any state variables that are declared but not used in any function. Unnecessary state variables can increase gas costs and should be eliminated during code review.

### Unused `error` definition
Note that there may be cases where an error superficially appears to be used, but this is only because there are multiple definitions of the error in different files. In such cases, the error definition should be moved into a separate file. The instances below are the unused definitions.


```solidity
Path: ./src/libraries/Error.sol

14:error BadPostUpgradeInit();	// @audit-issue

24:error NotRollup(address sender, address rollup);	// @audit-issue

36:error NotContract(address addr);	// @audit-issue

41:error MerkleProofTooLong(uint256 actualLength, uint256 maxProofLength);	// @audit-issue

47:error NotRollupOrOwner(address sender, address rollup, address owner);	// @audit-issue

53:error NotDelayedInbox(address sender);	// @audit-issue

57:error NotSequencerInbox(address sender);	// @audit-issue

61:error NotOutbox(address sender);	// @audit-issue

65:error InvalidOutboxSet(address outbox);	// @audit-issue

69:error InvalidTokenSet(address token);	// @audit-issue

73:error CallTargetNotAllowed(address target);	// @audit-issue

76:error CallNotAllowed();	// @audit-issue

81:error AlreadyPaused();	// @audit-issue

84:error AlreadyUnpaused();	// @audit-issue

87:error Paused();	// @audit-issue

90:error InsufficientValue(uint256 expected, uint256 actual);	// @audit-issue

93:error InsufficientSubmissionCost(uint256 expected, uint256 actual);	// @audit-issue

96:error NotAllowedOrigin(address origin);	// @audit-issue

100:error RetryableData(	// @audit-issue

114:error L1Forked();	// @audit-issue

120:error GasLimitTooLarge();	// @audit-issue

126:error ProofTooLong(uint256 proofLength);	// @audit-issue

131:error PathNotMinimal(uint256 index, uint256 maxIndex);	// @audit-issue

135:error UnknownRoot(bytes32 root);	// @audit-issue

139:error AlreadySpent(uint256 index);	// @audit-issue

142:error BridgeCallFailed();	// @audit-issue

156:error ForceIncludeTimeTooSoon();	// @audit-issue

168:error BadSequencerMessageNumber(uint256 stored, uint256 received);	// @audit-issue
```
[14](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/libraries/Error.sol#L14-L14), [24](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/libraries/Error.sol#L24-L24), [36](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/libraries/Error.sol#L36-L36), [41](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/libraries/Error.sol#L41-L41), [47](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/libraries/Error.sol#L47-L47), [53](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/libraries/Error.sol#L53-L53), [57](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/libraries/Error.sol#L57-L57), [61](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/libraries/Error.sol#L61-L61), [65](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/libraries/Error.sol#L65-L65), [69](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/libraries/Error.sol#L69-L69), [73](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/libraries/Error.sol#L73-L73), [76](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/libraries/Error.sol#L76-L76), [81](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/libraries/Error.sol#L81-L81), [84](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/libraries/Error.sol#L84-L84), [87](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/libraries/Error.sol#L87-L87), [90](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/libraries/Error.sol#L90-L90), [93](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/libraries/Error.sol#L93-L93), [96](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/libraries/Error.sol#L96-L96), [100](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/libraries/Error.sol#L100-L100), [114](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/libraries/Error.sol#L114-L114), [120](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/libraries/Error.sol#L120-L120), [126](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/libraries/Error.sol#L126-L126), [131](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/libraries/Error.sol#L131-L131), [135](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/libraries/Error.sol#L135-L135), [139](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/libraries/Error.sol#L139-L139), [142](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/libraries/Error.sol#L142-L142), [156](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/libraries/Error.sol#L156-L156), [168](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/libraries/Error.sol#L168-L168), 


```solidity
Path: ./src/challengeV2/libraries/ChallengeErrors.sol

40:error EdgeTypeNotBlock(uint8 level);	// @audit-issue

56:error EdgeClaimMismatch(bytes32 edgeId, bytes32 claimingEdgeId);	// @audit-issue

60:error EdgeNotAncestor(	// @audit-issue
```
[40](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/challengeV2/libraries/ChallengeErrors.sol#L40-L40), [56](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/challengeV2/libraries/ChallengeErrors.sol#L56-L56), [60](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/challengeV2/libraries/ChallengeErrors.sol#L60-L60), 


#### Recommendation

Unused `error` definitions should be removed from the contract, and if needed, consolidated into a separate file to avoid duplication.

### Using Prefix Operators Costs Less Gas Than Postfix Operators in Loops
Conditions can be optimized issues in Solidity refer to situations where smart contract developers write conditional statements that can be simplified or optimized for better gas efficiency, readability, and maintainability. Optimizing conditions can lead to more cost-effective and secure smart contracts.

```solidity
Path: ./src/rollup/BOLDUpgradeAction.sol

350:        for (uint64 i = 0; i < stakerCount; i++) {	// @audit-issue

528:            for (uint256 i = 0; i < validators.length; i++) {	// @audit-issue
```
[350](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/BOLDUpgradeAction.sol#L350-L350), [528](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/BOLDUpgradeAction.sol#L528-L528), 


```solidity
Path: ./src/rollup/RollupCreator.sol

225:        for (uint256 i = 0; i < deployParams.batchPosters.length; i++) {	// @audit-issue

235:            for (uint256 i = 0; i < deployParams.validators.length; i++) {	// @audit-issue
```
[225](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/RollupCreator.sol#L225-L225), [235](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/RollupCreator.sol#L235-L235), 


```solidity
Path: ./src/rollup/RollupAdminLogic.sol

184:        for (uint256 i = 0; i < _validator.length; i++) {	// @audit-issue

230:        for (uint256 i = 0; i < staker.length; i++) {	// @audit-issue
```
[184](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/RollupAdminLogic.sol#L184-L184), [230](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/RollupAdminLogic.sol#L230-L230), 


```solidity
Path: ./src/challengeV2/EdgeChallengeManager.sol

492:        for (uint256 i = 0; i < edgeIds.length; i++) {	// @audit-issue
```
[492](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/challengeV2/EdgeChallengeManager.sol#L492-L492), 


```solidity
Path: ./src/challengeV2/libraries/ArrayUtilsLib.sol

15:        for (uint256 i = 0; i < arr.length; i++) {	// @audit-issue

36:        for (uint256 i = startIndex; i < endIndex; i++) {	// @audit-issue

47:        for (uint256 i = 0; i < arr1.length; i++) {	// @audit-issue

50:        for (uint256 i = 0; i < arr2.length; i++) {	// @audit-issue
```
[15](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/challengeV2/libraries/ArrayUtilsLib.sol#L15-L15), [36](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/challengeV2/libraries/ArrayUtilsLib.sol#L36-L36), [47](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/challengeV2/libraries/ArrayUtilsLib.sol#L47-L47), [50](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/challengeV2/libraries/ArrayUtilsLib.sol#L50-L50), 


```solidity
Path: ./src/challengeV2/libraries/MerkleTreeLib.sol

115:        for (uint256 i = 0; i < me.length; i++) {	// @audit-issue

188:        for (uint256 i = 0; i < me.length; i++) {	// @audit-issue

294:        for (uint256 i = 0; i < me.length; i++) {	// @audit-issue

341:            proofIndex++;	// @audit-issue
```
[115](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/challengeV2/libraries/MerkleTreeLib.sol#L115-L115), [188](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/challengeV2/libraries/MerkleTreeLib.sol#L188-L188), [294](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/challengeV2/libraries/MerkleTreeLib.sol#L294-L294), [341](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/challengeV2/libraries/MerkleTreeLib.sol#L341-L341), 


#### Recommendation

To improve gas efficiency in your Solidity code, prefer using prefix operators (e.g., `++i` or `--i`) instead of postfix operators (e.g., `i++` or `i--`) within loops. Prefix operators typically result in lower gas costs and can contribute to more efficient contract execution.

### Do not calculate constants
Due to how constant variables are implemented (replacements at compile-time), an expression assigned to a constant variable is recomputed each time that the variable is used, which wastes some gas.

```solidity
Path: ./src/bridge/SequencerInbox.sol

76:    bytes1 public constant DATA_BLOB_HEADER_FLAG = DATA_AUTHENTICATED_FLAG | 0x10;	// @audit-issue

91:    uint256 internal constant GAS_PER_BLOB = 1 << 17;	// @audit-issue
```
[76](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/bridge/SequencerInbox.sol#L76-L76), [91](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/bridge/SequencerInbox.sol#L91-L91), 


#### Recommendation

Precompute and assign literal values to constant variables in your Solidity contracts. Avoid defining constants with expressions or calculations. By providing direct values, you ensure that the compiler replaces these constants efficiently in the bytecode, maximizing gas savings and contract performance. Review your contracts to identify any constants defined with expressions and refactor them to use precomputed literal values instead.

### Multiple accesses of a mapping/array should use a local variable cache
The instances below point to the second+ access of a value inside a mapping/array, within a function. Caching a mapping's value in a local `storage` or `calldata` variable when the value is accessed [multiple times](https://gist.github.com/IllIllI000/ec23a57daa30a8f8ca8b9681c8ccefb0), saves **~42 gas per access** due to not having to recalculate the key's keccak256 hash (Gkeccak256 - **30 gas**) and that calculation's associated stack operations. Caching an array's struct avoids recalculating the array offsets into memory/calldata

```solidity
Path: ./src/bridge/SequencerInbox.sol

310:            buffer.update(l1BlockAndTime[0]);	// @audit-issue: Same index access of variable `l1BlockAndTime` is used also on line(s): ['314', '299'].

705:            if (!isValidCallDataFlag(data[0])) revert InvalidHeaderFlag(data[0]);	// @audit-issue: Same index access of variable `data` is used also on line(s): ['705', '711'].
```
[310](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/bridge/SequencerInbox.sol#L310-L310), [705](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/bridge/SequencerInbox.sol#L705-L705), 


```solidity
Path: ./src/rollup/RollupAdminLogic.sol

232:            reduceStakeTo(staker[i], 0);	// @audit-issue: Same index access of variable `staker` is used also on line(s): ['231'].
```
[232](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/RollupAdminLogic.sol#L232-L232), 


```solidity
Path: ./src/challengeV2/EdgeChallengeManager.sol

494:            if (updated) emit TimerCacheUpdated(edgeIds[i], newValue);	// @audit-issue: Same index access of variable `edgeIds` is used also on line(s): ['493'].
```
[494](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/challengeV2/EdgeChallengeManager.sol#L494-L494), 


#### Recommendation

When a mapping or array value is accessed multiple times within a function, cache it in a local `storage` or `calldata` variable. This approach minimizes the gas cost by reducing the number of hash computations for mappings and offset calculations for arrays. Carefully review your functions to identify opportunities for such optimizations, especially in functions with frequent or repeated accesses to the same mapping or array element, to enhance gas efficiency in your contracts.

### State Variables That Are Used Multiple Times In a Function Should Be Cached In Stack Variables
When performing multiple operations on a state variable in a function, it is recommended to cache it first. Either multiple reads or multiple writes to a state variable can save gas by caching it on the stack. Caching of a state variable replaces each Gwarmaccess (100 gas) with a much cheaper stack read. Other less obvious fixes/optimizations include having local memory caches of state variable structs, or having local caches of state variable contracts/addresses. Saves 100 gas per instance.


```solidity
Path: ./src/bridge/SequencerInbox.sol

212:        if (rollup == newRollup) revert RollupNotChanged();	// @audit-issue: State variable `rollup` is used also on line(s): ['210', '209'].

295:        if (_totalDelayedMessagesRead <= totalDelayedMessagesRead) revert DelayedBackwards();	// @audit-issue: State variable `totalDelayedMessagesRead` is used also on line(s): ['349'].

612:                bytes32 delayedAcc = bridge.delayedInboxAccs(totalDelayedMessagesRead);	// @audit-issue: State variable `totalDelayedMessagesRead` is used also on line(s): ['609'].

844:        return _buffer < delayBlocks ? _buffer : delayBlocks;	// @audit-issue: State variable `delayBlocks` is used also on line(s): ['844'].

851:        if (buffer.bufferBlocks == 0 || buffer.bufferBlocks > bufferConfig_.max) {	// @audit-issue: State variable `buffer` is used also on line(s): ['851', '854'].
```
[212](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/bridge/SequencerInbox.sol#L212-L212), [295](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/bridge/SequencerInbox.sol#L295-L295), [612](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/bridge/SequencerInbox.sol#L612-L612), [844](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/bridge/SequencerInbox.sol#L844-L844), [851](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/bridge/SequencerInbox.sol#L851-L851), 


```solidity
Path: ./src/rollup/RollupCore.sol

510:            wasmModuleRoot,	// @audit-issue: State variable `wasmModuleRoot` is used also on line(s): ['491'].

492:                requiredStake: baseStake,	// @audit-issue: State variable `baseStake` is used also on line(s): ['511'].

512:            address(challengeManager),	// @audit-issue: State variable `challengeManager` is used also on line(s): ['493'].

513:            confirmPeriodBlocks	// @audit-issue: State variable `confirmPeriodBlocks` is used also on line(s): ['494'].
```
[510](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/RollupCore.sol#L510-L510), [492](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/RollupCore.sol#L492-L492), [512](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/RollupCore.sol#L512-L512), [513](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/RollupCore.sol#L513-L513), 


```solidity
Path: ./src/rollup/RollupCreator.sol

262:            address(validatorWalletCreator)	// @audit-issue: State variable `validatorWalletCreator` is used also on line(s): ['220'].
```
[262](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/RollupCreator.sol#L262-L262), 


```solidity
Path: ./src/rollup/RollupAdminLogic.sol

79:                wasmModuleRoot: wasmModuleRoot,	// @audit-issue: State variable `wasmModuleRoot` is used also on line(s): ['96'].

97:            baseStake,	// @audit-issue: State variable `baseStake` is used also on line(s): ['80'].

98:            address(challengeManager),	// @audit-issue: State variable `challengeManager` is used also on line(s): ['81'].

99:            confirmPeriodBlocks	// @audit-issue: State variable `confirmPeriodBlocks` is used also on line(s): ['82'].
```
[79](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/RollupAdminLogic.sol#L79-L79), [97](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/RollupAdminLogic.sol#L97-L97), [98](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/RollupAdminLogic.sol#L98-L98), [99](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/RollupAdminLogic.sol#L99-L99), 


```solidity
Path: ./src/challengeV2/EdgeChallengeManager.sol

418:            args, ard, oneStepProofEntry, expectedEndHeight, NUM_BIGSTEP_LEVEL, whitelistEnabled	// @audit-issue: State variable `NUM_BIGSTEP_LEVEL` is used also on line(s): ['381'].

514:            revert EdgeNotLayerZero(topEdge.id(), topEdge.staker, topEdge.claimId);	// @audit-issue: State variable `topEdge` is used also on line(s): ['524', '522'].
```
[418](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/challengeV2/EdgeChallengeManager.sol#L418-L418), [514](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/challengeV2/EdgeChallengeManager.sol#L514-L514), 


```solidity
Path: ./src/challengeV2/libraries/EdgeChallengeManagerLib.sol

289:            if (args.level != nextEdgeLevel(claimEdge.level, numBigStepLevel)) {	// @audit-issue: State variable `claimEdge` is used also on line(s): ['290'].

450:            bytes32 lowerLevelId = store.firstRivals[edge.originId];	// @audit-issue: State variable `edge` is used also on line(s): ['455'].
```
[289](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/challengeV2/libraries/EdgeChallengeManagerLib.sol#L289-L289), [450](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/challengeV2/libraries/EdgeChallengeManagerLib.sol#L450-L450), 


#### Recommendation

Cache state variables in stack or local memory variables within functions when they are used multiple times. This approach replaces costlier Gwarmaccess operations with cheaper stack reads, saving approximately 100 gas per instance and optimizing overall contract performance.

### Missing Constant Modifier For State Variables
State variables that are never re-assigned after their initial assignment should typically be declared with the `constant` modifier. This ensures that these variables remain unmodified and communicates their unchanging nature. Using the `constant` modifier also offers potential gas savings, as accessing these variables does not require any storage operations.

```solidity
Path: ./src/bridge/SequencerInbox.sol

99:    ISequencerInbox.MaxTimeVariation private __LEGACY_MAX_TIME_VARIATION;	// @audit-issue
```
[99](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/bridge/SequencerInbox.sol#L99-L99), 


```solidity
Path: ./src/challengeV2/EdgeChallengeManager.sol

266:    EdgeStore internal store;	// @audit-issue
```
[266](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/challengeV2/EdgeChallengeManager.sol#L266-L266), 


#### Recommendation

Declare state variables that are not reassigned after initialization with the 'constant' modifier in Solidity. This clarifies their unchanging nature, improves code readability, and saves gas by avoiding storage operations when accessing these variables.

### Increments can be `unchecked` in for-loops
Newer versions of the Solidity compiler will check for integer overflows and underflows automatically. This provides safety but increases gas costs.
When an unsigned integer is guaranteed to never overflow, the unchecked feature of Solidity can be used to save gas costs.A common case for this is for-loops using a strictly-less-than comparision in their conditional statement.

```solidity
Path: ./src/rollup/BOLDUpgradeAction.sol

350:        for (uint64 i = 0; i < stakerCount; i++) {	// @audit-issue

528:            for (uint256 i = 0; i < validators.length; i++) {	// @audit-issue
```
[350](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/BOLDUpgradeAction.sol#L350-L350), [528](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/BOLDUpgradeAction.sol#L528-L528), 


```solidity
Path: ./src/rollup/RollupCreator.sol

225:        for (uint256 i = 0; i < deployParams.batchPosters.length; i++) {	// @audit-issue

235:            for (uint256 i = 0; i < deployParams.validators.length; i++) {	// @audit-issue
```
[225](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/RollupCreator.sol#L225-L225), [235](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/RollupCreator.sol#L235-L235), 


```solidity
Path: ./src/rollup/RollupAdminLogic.sol

184:        for (uint256 i = 0; i < _validator.length; i++) {	// @audit-issue

230:        for (uint256 i = 0; i < staker.length; i++) {	// @audit-issue
```
[184](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/RollupAdminLogic.sol#L184-L184), [230](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/RollupAdminLogic.sol#L230-L230), 


```solidity
Path: ./src/challengeV2/EdgeChallengeManager.sol

492:        for (uint256 i = 0; i < edgeIds.length; i++) {	// @audit-issue
```
[492](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/challengeV2/EdgeChallengeManager.sol#L492-L492), 


```solidity
Path: ./src/challengeV2/libraries/ArrayUtilsLib.sol

15:        for (uint256 i = 0; i < arr.length; i++) {	// @audit-issue

36:        for (uint256 i = startIndex; i < endIndex; i++) {	// @audit-issue

47:        for (uint256 i = 0; i < arr1.length; i++) {	// @audit-issue

50:        for (uint256 i = 0; i < arr2.length; i++) {	// @audit-issue
```
[15](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/challengeV2/libraries/ArrayUtilsLib.sol#L15-L15), [36](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/challengeV2/libraries/ArrayUtilsLib.sol#L36-L36), [47](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/challengeV2/libraries/ArrayUtilsLib.sol#L47-L47), [50](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/challengeV2/libraries/ArrayUtilsLib.sol#L50-L50), 


```solidity
Path: ./src/challengeV2/libraries/MerkleTreeLib.sol

115:        for (uint256 i = 0; i < me.length; i++) {	// @audit-issue

188:        for (uint256 i = 0; i < me.length; i++) {	// @audit-issue

294:        for (uint256 i = 0; i < me.length; i++) {	// @audit-issue
```
[115](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/challengeV2/libraries/MerkleTreeLib.sol#L115-L115), [188](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/challengeV2/libraries/MerkleTreeLib.sol#L188-L188), [294](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/challengeV2/libraries/MerkleTreeLib.sol#L294-L294), 


#### Recommendation

Use unchecked math to block overflow / underflow check to save Gas.

### Divisions can be unchecked to save gas
The expression type(int).min/(-1) is the only case where division causes an overflow. Therefore, uncheck can be used to save gas in scenarios where it is certain that such an overflow will not occur.

```solidity
Path: ./src/bridge/SequencerInbox.sol

746:            block.basefee > 0 ? blobCost / block.basefee : 0	// @audit-issue

771:            extraGas += l1Fees / block.basefee;	// @audit-issue
```
[746](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/bridge/SequencerInbox.sol#L746-L746), [771](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/bridge/SequencerInbox.sol#L771-L771), 


```solidity
Path: ./src/bridge/DelayBuffer.sol

46:        buffer += (elapsed * replenishRateInBasis) / BASIS;	// @audit-issue
```
[46](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/bridge/DelayBuffer.sol#L46-L46), 


#### Recommendation

Utilize 'unchecked' blocks in Solidity for divisions where overflow is impossible, such as when 'type(int).min/(-1)' is not a concern. This can save gas by bypassing overflow checks in these specific cases.

### Add `unchecked {}` for subtractions where the operands cannot underflow because of a previous `require()` or `if`-statement
Unchecked keyword can be added to such scenerios: 
`require(a <= b); x = b - a` => `require(a <= b); unchecked { x = b - a }`

```solidity
Path: ./src/bridge/SequencerInbox.sol

322:            bridge.delayedInboxAccs(_totalDelayedMessagesRead - 1) !=	// @audit-issue
```
[322](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/bridge/SequencerInbox.sol#L322-L322), 


```solidity
Path: ./src/bridge/DelayBuffer.sol

55:            buffer -= unexpectedDelay;	// @audit-issue
```
[55](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/bridge/DelayBuffer.sol#L55-L55), 


```solidity
Path: ./src/rollup/RollupCore.sol

305:        uint256 amountWithdrawn = current - target;	// @audit-issue
```
[305](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/RollupCore.sol#L305-L305), 


```solidity
Path: ./src/challengeV2/libraries/ArrayUtilsLib.sol

35:        bytes32[] memory newArr = new bytes32[](endIndex - startIndex);	// @audit-issue
```
[35](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/challengeV2/libraries/ArrayUtilsLib.sol#L35-L35), 


```solidity
Path: ./src/challengeV2/libraries/EdgeChallengeManagerLib.sol

565:                return firstRivalCreatedAtBlock - edgeCreatedAtBlock;	// @audit-issue
```
[565](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/challengeV2/libraries/EdgeChallengeManagerLib.sol#L565-L565), 


```solidity
Path: ./src/assertionStakingPool/AbsBoldStakingPool.sol

50:        depositBalance[msg.sender] = balance - amount;	// @audit-issue
```
[50](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/assertionStakingPool/AbsBoldStakingPool.sol#L50-L50), 


#### Recommendation

In scenarios where subtraction cannot result in underflow due to prior `require()` or `if`-statements, wrap these operations in an `unchecked` block to save gas. This optimization should only be applied when the safety of the operation is assured. Carefully analyze each case to confirm that underflow is impossible before implementing `unchecked` blocks, as incorrect usage can lead to vulnerabilities in the contract.

### Stack variable is only used once
If the variable is only accessed once, it's cheaper to use the assigned value directly that one time, and save the 3 gas the extra stack assignment would spend

```solidity
Path: ./src/bridge/SequencerInbox.sol

218:        (	// @audit-issue: futureBlocks_ used only on line: 231
219:            uint64 delayBlocks_,
220:            uint64 futureBlocks_,
221:            uint64 delaySeconds_,
222:            uint64 futureSeconds_
223:        ) = maxTimeVariationInternal();

218:        (	// @audit-issue: futureSeconds_ used only on line: 227
219:            uint64 delayBlocks_,
220:            uint64 futureBlocks_,
221:            uint64 delaySeconds_,
222:            uint64 futureSeconds_
223:        ) = maxTimeVariationInternal();

254:        (	// @audit-issue: delayBlocks_ used only on line: 262
255:            uint64 delayBlocks_,
256:            uint64 futureBlocks_,
257:            uint64 delaySeconds_,
258:            uint64 futureSeconds_
259:        ) = maxTimeVariationInternal();

254:        (	// @audit-issue: futureBlocks_ used only on line: 263
255:            uint64 delayBlocks_,
256:            uint64 futureBlocks_,
257:            uint64 delaySeconds_,
258:            uint64 futureSeconds_
259:        ) = maxTimeVariationInternal();

254:        (	// @audit-issue: delaySeconds_ used only on line: 264
255:            uint64 delayBlocks_,
256:            uint64 futureBlocks_,
257:            uint64 delaySeconds_,
258:            uint64 futureSeconds_
259:        ) = maxTimeVariationInternal();

254:        (	// @audit-issue: futureSeconds_ used only on line: 265
255:            uint64 delayBlocks_,
256:            uint64 futureBlocks_,
257:            uint64 delaySeconds_,
258:            uint64 futureSeconds_
259:        ) = maxTimeVariationInternal();

296:        bytes32 messageHash = Messages.messageHash(	// @audit-issue: messageHash used only on line: 323
297:            kind,
298:            sender,
299:            l1BlockAndTime[0],
300:            l1BlockAndTime[1],
301:            _totalDelayedMessagesRead - 1,
302:            baseFeeL1,
303:            messageDataHash
304:        );

326:        (bytes32 dataHash, IBridge.TimeBounds memory timeBounds) = formEmptyDataHash(	// @audit-issue: dataHash used only on line: 338
327:            _totalDelayedMessagesRead
328:        );

326:        (bytes32 dataHash, IBridge.TimeBounds memory timeBounds) = formEmptyDataHash(	// @audit-issue: timeBounds used only on line: 350
327:            _totalDelayedMessagesRead
328:        );

329:        uint256 __totalDelayedMessagesRead = _totalDelayedMessagesRead;	// @audit-issue: __totalDelayedMessagesRead used only on line: 339

331:        uint256 newSeqMsgCount = prevSeqMsgCount; // force inclusion should not modify sequencer message count	// @audit-issue: newSeqMsgCount used only on line: 342

332:        (	// @audit-issue: seqMessageIndex used only on line: 345
333:            uint256 seqMessageIndex,
334:            bytes32 beforeAcc,
335:            bytes32 delayedAcc,
336:            bytes32 afterAcc
337:        ) = addSequencerL2BatchImpl(
338:                dataHash,
339:                __totalDelayedMessagesRead,
340:                0,
341:                prevSeqMsgCount,
342:                newSeqMsgCount
343:            );

332:        (	// @audit-issue: beforeAcc used only on line: 346
333:            uint256 seqMessageIndex,
334:            bytes32 beforeAcc,
335:            bytes32 delayedAcc,
336:            bytes32 afterAcc
337:        ) = addSequencerL2BatchImpl(
338:                dataHash,
339:                __totalDelayedMessagesRead,
340:                0,
341:                prevSeqMsgCount,
342:                newSeqMsgCount
343:            );

332:        (	// @audit-issue: delayedAcc used only on line: 348
333:            uint256 seqMessageIndex,
334:            bytes32 beforeAcc,
335:            bytes32 delayedAcc,
336:            bytes32 afterAcc
337:        ) = addSequencerL2BatchImpl(
338:                dataHash,
339:                __totalDelayedMessagesRead,
340:                0,
341:                prevSeqMsgCount,
342:                newSeqMsgCount
343:            );

332:        (	// @audit-issue: afterAcc used only on line: 347
333:            uint256 seqMessageIndex,
334:            bytes32 beforeAcc,
335:            bytes32 delayedAcc,
336:            bytes32 afterAcc
337:        ) = addSequencerL2BatchImpl(
338:                dataHash,
339:                __totalDelayedMessagesRead,
340:                0,
341:                prevSeqMsgCount,
342:                newSeqMsgCount
343:            );

461:        (	// @audit-issue: timeBounds used only on line: 494
462:            bytes32 dataHash,
463:            IBridge.TimeBounds memory timeBounds,
464:            uint256 blobGas
465:        ) = formBlobDataHash(afterDelayedMessagesRead);

461:        (	// @audit-issue: blobGas used only on line: 508
462:            bytes32 dataHash,
463:            IBridge.TimeBounds memory timeBounds,
464:            uint256 blobGas
465:        ) = formBlobDataHash(afterDelayedMessagesRead);

470:        (	// @audit-issue: beforeAcc used only on line: 490
471:            uint256 seqMessageIndex,
472:            bytes32 beforeAcc,
473:            bytes32 delayedAcc,
474:            bytes32 afterAcc
475:        ) = addSequencerL2BatchImpl(
476:                dataHash,
477:                afterDelayedMessagesRead,
478:                0,
479:                prevMessageCount,
480:                newMessageCount
481:            );

470:        (	// @audit-issue: delayedAcc used only on line: 492
471:            uint256 seqMessageIndex,
472:            bytes32 beforeAcc,
473:            bytes32 delayedAcc,
474:            bytes32 afterAcc
475:        ) = addSequencerL2BatchImpl(
476:                dataHash,
477:                afterDelayedMessagesRead,
478:                0,
479:                prevMessageCount,
480:                newMessageCount
481:            );

470:        (	// @audit-issue: afterAcc used only on line: 491
471:            uint256 seqMessageIndex,
472:            bytes32 beforeAcc,
473:            bytes32 delayedAcc,
474:            bytes32 afterAcc
475:        ) = addSequencerL2BatchImpl(
476:                dataHash,
477:                afterDelayedMessagesRead,
478:                0,
479:                prevMessageCount,
480:                newMessageCount
481:            );

520:        (bytes32 dataHash, IBridge.TimeBounds memory timeBounds) = formCallDataHash(	// @audit-issue: dataHash used only on line: 530
521:            data,
522:            afterDelayedMessagesRead
523:        );

520:        (bytes32 dataHash, IBridge.TimeBounds memory timeBounds) = formCallDataHash(	// @audit-issue: timeBounds used only on line: 548
521:            data,
522:            afterDelayedMessagesRead
523:        );

524:        (	// @audit-issue: beforeAcc used only on line: 544
525:            uint256 seqMessageIndex,
526:            bytes32 beforeAcc,
527:            bytes32 delayedAcc,
528:            bytes32 afterAcc
529:        ) = addSequencerL2BatchImpl(
530:                dataHash,
531:                afterDelayedMessagesRead,
532:                isFromOrigin ? data.length : 0,
533:                prevMessageCount,
534:                newMessageCount
535:            );

524:        (	// @audit-issue: delayedAcc used only on line: 546
525:            uint256 seqMessageIndex,
526:            bytes32 beforeAcc,
527:            bytes32 delayedAcc,
528:            bytes32 afterAcc
529:        ) = addSequencerL2BatchImpl(
530:                dataHash,
531:                afterDelayedMessagesRead,
532:                isFromOrigin ? data.length : 0,
533:                prevMessageCount,
534:                newMessageCount
535:            );

524:        (	// @audit-issue: afterAcc used only on line: 545
525:            uint256 seqMessageIndex,
526:            bytes32 beforeAcc,
527:            bytes32 delayedAcc,
528:            bytes32 afterAcc
529:        ) = addSequencerL2BatchImpl(
530:                dataHash,
531:                afterDelayedMessagesRead,
532:                isFromOrigin ? data.length : 0,
533:                prevMessageCount,
534:                newMessageCount
535:            );

612:                bytes32 delayedAcc = bridge.delayedInboxAccs(totalDelayedMessagesRead);	// @audit-issue: delayedAcc used only on line: 616

664:        (bytes memory header, IBridge.TimeBounds memory timeBounds) = packHeader(	// @audit-issue: header used only on line: 667
665:            afterDelayedMessagesRead
666:        );

664:        (bytes memory header, IBridge.TimeBounds memory timeBounds) = packHeader(	// @audit-issue: timeBounds used only on line: 667
665:            afterDelayedMessagesRead
666:        );

696:        (bytes memory header, IBridge.TimeBounds memory timeBounds) = packHeader(	// @audit-issue: header used only on line: 717
697:            afterDelayedMessagesRead
698:        );

696:        (bytes memory header, IBridge.TimeBounds memory timeBounds) = packHeader(	// @audit-issue: timeBounds used only on line: 717
697:            afterDelayedMessagesRead
698:        );

738:        (bytes memory header, IBridge.TimeBounds memory timeBounds) = packHeader(	// @audit-issue: header used only on line: 744
739:            afterDelayedMessagesRead
740:        );

738:        (bytes memory header, IBridge.TimeBounds memory timeBounds) = packHeader(	// @audit-issue: timeBounds used only on line: 745
739:            afterDelayedMessagesRead
740:        );

742:        uint256 blobCost = reader4844.getBlobBaseFee() * GAS_PER_BLOB * dataHashes.length;	// @audit-issue: blobCost used only on line: 746

770:            uint256 l1Fees = ArbGasInfo(address(0x6c)).getCurrentTxL1GasFees();	// @audit-issue: l1Fees used only on line: 771

783:        uint256 msgNum = bridge.submitBatchSpendingReport(	// @audit-issue: msgNum used only on line: 788
784:            batchPoster,
785:            keccak256(spendingReportMsg)
786:        );

836:            uint64 _buffer = buffer.calcPendingBuffer(blockNumber);	// @audit-issue: _buffer used only on line: 837

904:        uint256 ksWord = uint256(keccak256(bytes.concat(hex"fe", keccak256(keysetBytes))));	// @audit-issue: ksWord used only on line: 905
```
[218](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/bridge/SequencerInbox.sol#L218-L223), [218](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/bridge/SequencerInbox.sol#L218-L223), [254](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/bridge/SequencerInbox.sol#L254-L259), [254](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/bridge/SequencerInbox.sol#L254-L259), [254](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/bridge/SequencerInbox.sol#L254-L259), [254](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/bridge/SequencerInbox.sol#L254-L259), [296](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/bridge/SequencerInbox.sol#L296-L304), [326](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/bridge/SequencerInbox.sol#L326-L328), [326](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/bridge/SequencerInbox.sol#L326-L328), [329](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/bridge/SequencerInbox.sol#L329-L329), [331](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/bridge/SequencerInbox.sol#L331-L331), [332](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/bridge/SequencerInbox.sol#L332-L343), [332](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/bridge/SequencerInbox.sol#L332-L343), [332](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/bridge/SequencerInbox.sol#L332-L343), [332](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/bridge/SequencerInbox.sol#L332-L343), [461](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/bridge/SequencerInbox.sol#L461-L465), [461](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/bridge/SequencerInbox.sol#L461-L465), [470](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/bridge/SequencerInbox.sol#L470-L481), [470](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/bridge/SequencerInbox.sol#L470-L481), [470](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/bridge/SequencerInbox.sol#L470-L481), [520](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/bridge/SequencerInbox.sol#L520-L523), [520](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/bridge/SequencerInbox.sol#L520-L523), [524](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/bridge/SequencerInbox.sol#L524-L535), [524](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/bridge/SequencerInbox.sol#L524-L535), [524](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/bridge/SequencerInbox.sol#L524-L535), [612](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/bridge/SequencerInbox.sol#L612-L612), [664](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/bridge/SequencerInbox.sol#L664-L666), [664](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/bridge/SequencerInbox.sol#L664-L666), [696](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/bridge/SequencerInbox.sol#L696-L698), [696](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/bridge/SequencerInbox.sol#L696-L698), [738](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/bridge/SequencerInbox.sol#L738-L740), [738](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/bridge/SequencerInbox.sol#L738-L740), [742](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/bridge/SequencerInbox.sol#L742-L742), [770](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/bridge/SequencerInbox.sol#L770-L770), [783](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/bridge/SequencerInbox.sol#L783-L786), [836](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/bridge/SequencerInbox.sol#L836-L836), [904](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/bridge/SequencerInbox.sol#L904-L904), 


```solidity
Path: ./src/rollup/BOLDUpgradeAction.sol

385:        ISequencerInbox.MaxTimeVariation memory maxTimeVariation;	// @audit-issue: maxTimeVariation used only on line: 398

386:        BufferConfig memory bufferConfig;	// @audit-issue: bufferConfig used only on line: 407

415:        TransparentUpgradeableProxy bridge = TransparentUpgradeableProxy(payable(BRIDGE));	// @audit-issue: bridge used only on line: 416

421:        TransparentUpgradeableProxy inbox = TransparentUpgradeableProxy(payable(INBOX));	// @audit-issue: inbox used only on line: 422

424:        TransparentUpgradeableProxy rollupEventInbox = TransparentUpgradeableProxy(payable(REI));	// @audit-issue: rollupEventInbox used only on line: 425

428:        TransparentUpgradeableProxy outbox = TransparentUpgradeableProxy(payable(OUTBOX));	// @audit-issue: outbox used only on line: 429

484:        ContractDependencies memory connectedContracts = ContractDependencies({	// @audit-issue: connectedContracts used only on line: 524
485:            bridge: IBridge(BRIDGE),
486:            sequencerInbox: ISequencerInbox(SEQ_INBOX),
487:            inbox: IInboxBase(INBOX),
488:            outbox: IOutbox(OUTBOX),
489:            rollupEventInbox: IRollupEventInbox(REI),
490:            challengeManager: challengeManager,
491:            rollupAdminLogic: IMPL_NEW_ROLLUP_ADMIN,
492:            rollupUserLogic: IRollupUser(IMPL_NEW_ROLLUP_USER),
493:            validatorWalletCreator: ROLLUP_READER.validatorWalletCreator()
494:        });

521:        address actualOwner = config.owner;	// @audit-issue: actualOwner used only on line: 538
```
[385](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/BOLDUpgradeAction.sol#L385-L385), [386](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/BOLDUpgradeAction.sol#L386-L386), [415](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/BOLDUpgradeAction.sol#L415-L415), [421](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/BOLDUpgradeAction.sol#L421-L421), [424](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/BOLDUpgradeAction.sol#L424-L424), [428](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/BOLDUpgradeAction.sol#L428-L428), [484](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/BOLDUpgradeAction.sol#L484-L494), [521](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/BOLDUpgradeAction.sol#L521-L521), 


```solidity
Path: ./src/rollup/BridgeCreator.sol

107:        bool isDelayBufferable = bufferConfig.threshold != 0;	// @audit-issue: isDelayBufferable used only on line: 113
```
[107](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/BridgeCreator.sol#L107-L107), 


```solidity
Path: ./src/rollup/RollupCore.sol

275:        uint64 stakerIndex = uint64(_stakerList.length);	// @audit-issue: stakerIndex used only on line: 277

488:        AssertionNode memory newAssertion = AssertionNodeLib.createAssertion(	// @audit-issue: newAssertion used only on line: 502
489:            prevAssertion.firstChildBlock == 0, // assumes block 0 is impossible
490:            RollupLib.configHash({
491:                wasmModuleRoot: wasmModuleRoot,
492:                requiredStake: baseStake,
493:                challengeManager: address(challengeManager),
494:                confirmPeriodBlocks: confirmPeriodBlocks,
495:                nextInboxPosition: uint64(nextInboxPosition)
496:            })
497:        );

521:        GlobalState memory emptyGlobalState;	// @audit-issue: emptyGlobalState used only on line: 522

522:        AssertionState memory emptyAssertionState = AssertionState(emptyGlobalState, MachineStatus.FINISHED, bytes32(0));	// @audit-issue: emptyAssertionState used only on line: 527

523:        bytes32 parentAssertionHash = bytes32(0);	// @audit-issue: parentAssertionHash used only on line: 526

524:        bytes32 inboxAcc = bytes32(0);	// @audit-issue: inboxAcc used only on line: 528

571:        bool isLatestConfirmed = lastestAssertion == latestConfirmed();	// @audit-issue: isLatestConfirmed used only on line: 573

572:        bool haveChild = getAssertionStorage(lastestAssertion).firstChildBlock > 0;	// @audit-issue: haveChild used only on line: 573
```
[275](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/RollupCore.sol#L275-L275), [488](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/RollupCore.sol#L488-L497), [521](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/RollupCore.sol#L521-L521), [522](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/RollupCore.sol#L522-L522), [523](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/RollupCore.sol#L523-L523), [524](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/RollupCore.sol#L524-L524), [571](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/RollupCore.sol#L571-L571), [572](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/RollupCore.sol#L572-L572), 


```solidity
Path: ./src/rollup/RollupUserLogic.sol

103:        AssertionNode storage assertion = getAssertionStorage(assertionHash);	// @audit-issue: assertion used only on line: 110

200:        (bytes32 newAssertionHash, bool overflowAssertion) =	// @audit-issue: overflowAssertion used only on line: 204
201:            createNewAssertion(assertion, prevAssertion, expectedAssertionHash);

205:            uint256 timeSincePrev = block.number - getAssertionStorage(prevAssertion).createdAtBlock;	// @audit-issue: timeSincePrev used only on line: 207

279:        AssertionStatus status = getAssertionStorage(expectedAssertionHash).status;	// @audit-issue: status used only on line: 288

290:            (bytes32 newAssertionHash,) = createNewAssertion(assertion, prevAssertion, expectedAssertionHash);	// @audit-issue: newAssertionHash used only on line: 291
```
[103](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/RollupUserLogic.sol#L103-L103), [200](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/RollupUserLogic.sol#L200-L201), [205](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/RollupUserLogic.sol#L205-L205), [279](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/RollupUserLogic.sol#L279-L279), [290](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/RollupUserLogic.sol#L290-L290), 


```solidity
Path: ./src/rollup/RollupCreator.sol

144:            (	// @audit-issue: ethSequencerInbox used only on line: 153
145:                ,
146:                ISequencerInbox ethSequencerInbox,
147:                ISequencerInbox ethDelayBufferableSequencerInbox,
148:                IInboxBase ethInbox,
149:                ,
150:
151:            ) = bridgeCreator.ethBasedTemplates();

144:            (	// @audit-issue: ethDelayBufferableSequencerInbox used only on line: 157
145:                ,
146:                ISequencerInbox ethSequencerInbox,
147:                ISequencerInbox ethDelayBufferableSequencerInbox,
148:                IInboxBase ethInbox,
149:                ,
150:
151:            ) = bridgeCreator.ethBasedTemplates();

144:            (	// @audit-issue: ethInbox used only on line: 160
145:                ,
146:                ISequencerInbox ethSequencerInbox,
147:                ISequencerInbox ethDelayBufferableSequencerInbox,
148:                IInboxBase ethInbox,
149:                ,
150:
151:            ) = bridgeCreator.ethBasedTemplates();

162:            (	// @audit-issue: erc20SequencerInbox used only on line: 171
163:                ,
164:                ISequencerInbox erc20SequencerInbox,
165:                ISequencerInbox erc20DelayBufferableSequencerInbox,
166:                IInboxBase erc20Inbox,
167:                ,
168:
169:            ) = bridgeCreator.erc20BasedTemplates();

162:            (	// @audit-issue: erc20DelayBufferableSequencerInbox used only on line: 175
163:                ,
164:                ISequencerInbox erc20SequencerInbox,
165:                ISequencerInbox erc20DelayBufferableSequencerInbox,
166:                IInboxBase erc20Inbox,
167:                ,
168:
169:            ) = bridgeCreator.erc20BasedTemplates();

162:            (	// @audit-issue: erc20Inbox used only on line: 179
163:                ,
164:                ISequencerInbox erc20SequencerInbox,
165:                ISequencerInbox erc20DelayBufferableSequencerInbox,
166:                IInboxBase erc20Inbox,
167:                ,
168:
169:            ) = bridgeCreator.erc20BasedTemplates();

294:            uint256 cost = l2FactoriesDeployer.getDeploymentTotalCost(	// @audit-issue: cost used only on line: 300
295:                IInboxBase(_inbox),
296:                _maxFeePerGas
297:            );

304:            (bool sent, ) = msg.sender.call{value: address(this).balance}("");	// @audit-issue: sent used only on line: 305

308:            uint256 totalFee = l2FactoriesDeployer.getDeploymentTotalCost(	// @audit-issue: totalFee used only on line: 312
309:                IInboxBase(_inbox),
310:                _maxFeePerGas
311:            );
```
[144](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/RollupCreator.sol#L144-L151), [144](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/RollupCreator.sol#L144-L151), [144](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/RollupCreator.sol#L144-L151), [162](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/RollupCreator.sol#L162-L169), [162](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/RollupCreator.sol#L162-L169), [162](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/RollupCreator.sol#L162-L169), [294](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/RollupCreator.sol#L294-L297), [304](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/RollupCreator.sol#L304-L304), [308](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/RollupCreator.sol#L308-L311), 


```solidity
Path: ./src/rollup/RollupAdminLogic.sol

76:        AssertionNode memory initialAssertion = AssertionNodeLib.createAssertion(	// @audit-issue: initialAssertion used only on line: 86
77:            true,
78:            RollupLib.configHash({
79:                wasmModuleRoot: wasmModuleRoot,
80:                requiredStake: baseStake,
81:                challengeManager: address(challengeManager),
82:                confirmPeriodBlocks: confirmPeriodBlocks,
83:                nextInboxPosition: uint64(currentInboxCount)
84:            })
85:        );
```
[76](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/RollupAdminLogic.sol#L76-L85), 


```solidity
Path: ./src/challengeV2/EdgeChallengeManager.sol

382:        uint256 expectedEndHeight = getLayerZeroEndHeight(eType);	// @audit-issue: expectedEndHeight used only on line: 418

433:            address receiver = edgeAdded.hasRival ? excessStakeReceiver : address(this);	// @audit-issue: receiver used only on line: 434

500:        (bool updated, uint256 newValue) = store.updateTimerCacheByChildren(edgeId);	// @audit-issue: updated used only on line: 501

500:        (bool updated, uint256 newValue) = store.updateTimerCacheByChildren(edgeId);	// @audit-issue: newValue used only on line: 501

506:        (bool updated, uint256 newValue) = store.updateTimerCacheByClaim(edgeId, claimingEdgeId, NUM_BIGSTEP_LEVEL);	// @audit-issue: updated used only on line: 507

506:        (bool updated, uint256 newValue) = store.updateTimerCacheByClaim(edgeId, claimingEdgeId, NUM_BIGSTEP_LEVEL);	// @audit-issue: newValue used only on line: 507

521:        bool isBlockLevel = ChallengeEdgeLib.levelToType(topEdge.level, NUM_BIGSTEP_LEVEL) == EdgeType.Block;	// @audit-issue: isBlockLevel used only on line: 522

533:        uint256 totalTimeUnrivaled = store.confirmEdgeByTime(edgeId, assertionBlocks, challengePeriodBlocks);	// @audit-issue: totalTimeUnrivaled used only on line: 535

546:        bytes32 prevAssertionHash = store.getPrevAssertionHash(edgeId);	// @audit-issue: prevAssertionHash used only on line: 548

550:        ExecutionContext memory execCtx = ExecutionContext({	// @audit-issue: execCtx used only on line: 560
551:            maxInboxMessagesRead: prevConfig.nextInboxPosition,
552:            bridge: assertionChain.bridge(),
553:            initialWasmModuleRoot: prevConfig.wasmModuleRoot
554:        });
```
[382](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/challengeV2/EdgeChallengeManager.sol#L382-L382), [433](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/challengeV2/EdgeChallengeManager.sol#L433-L433), [500](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/challengeV2/EdgeChallengeManager.sol#L500-L500), [500](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/challengeV2/EdgeChallengeManager.sol#L500-L500), [506](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/challengeV2/EdgeChallengeManager.sol#L506-L506), [506](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/challengeV2/EdgeChallengeManager.sol#L506-L506), [521](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/challengeV2/EdgeChallengeManager.sol#L521-L521), [533](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/challengeV2/EdgeChallengeManager.sol#L533-L533), [546](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/challengeV2/EdgeChallengeManager.sol#L546-L546), [550](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/challengeV2/EdgeChallengeManager.sol#L550-L554), 


```solidity
Path: ./src/challengeV2/libraries/EdgeChallengeManagerLib.sol

251:            (bytes32[] memory inclusionProof,,) =	// @audit-issue: inclusionProof used only on line: 266
252:                abi.decode(args.proof, (bytes32[], AssertionStateData, AssertionStateData));

263:            bytes32 startStateHash = oneStepProofEntry.getMachineHash(ard.startState.toExecutionState());	// @audit-issue: startStateHash used only on line: 266

264:            bytes32 endStateHash = oneStepProofEntry.getMachineHash(ard.endState.toExecutionState());	// @audit-issue: endStateHash used only on line: 266

297:            (	// @audit-issue: claimStartInclusionProof used only on line: 309
298:                bytes32 startState,
299:                bytes32 endState,
300:                bytes32[] memory claimStartInclusionProof,
301:                bytes32[] memory claimEndInclusionProof,
302:                bytes32[] memory edgeInclusionProof
303:            ) = abi.decode(args.proof, (bytes32, bytes32, bytes32[], bytes32[], bytes32[]));

297:            (	// @audit-issue: claimEndInclusionProof used only on line: 319
298:                bytes32 startState,
299:                bytes32 endState,
300:                bytes32[] memory claimStartInclusionProof,
301:                bytes32[] memory claimEndInclusionProof,
302:                bytes32[] memory edgeInclusionProof
303:            ) = abi.decode(args.proof, (bytes32, bytes32, bytes32[], bytes32[], bytes32[]));

297:            (	// @audit-issue: edgeInclusionProof used only on line: 322
298:                bytes32 startState,
299:                bytes32 endState,
300:                bytes32[] memory claimStartInclusionProof,
301:                bytes32[] memory claimEndInclusionProof,
302:                bytes32[] memory edgeInclusionProof
303:            ) = abi.decode(args.proof, (bytes32, bytes32, bytes32[], bytes32[], bytes32[]));

334:        uint256 y = x - 1;	// @audit-issue: y used only on line: 337

381:        (bytes32[] memory preExpansion, bytes32[] memory preProof) =	// @audit-issue: preExpansion used only on line: 384
382:            abi.decode(args.prefixProof, (bytes32[], bytes32[]));

381:        (bytes32[] memory preExpansion, bytes32[] memory preProof) =	// @audit-issue: preProof used only on line: 384
382:            abi.decode(args.prefixProof, (bytes32[], bytes32[]));

421:        (ProofData memory proofData, bytes32 originId) =	// @audit-issue: proofData used only on line: 424
422:            layerZeroTypeSpecificChecks(store, args, ard, oneStepProofEntry, numBigStepLevel);

421:        (ProofData memory proofData, bytes32 originId) =	// @audit-issue: originId used only on line: 426
422:            layerZeroTypeSpecificChecks(store, args, ard, oneStepProofEntry, numBigStepLevel);

424:        (bytes32 startHistoryRoot) = layerZeroCommonChecks(proofData, args, expectedEndHeight);	// @audit-issue: startHistoryRoot used only on line: 426

469:        bytes32 mutualId = store.edges[edgeId].mutualId();	// @audit-issue: mutualId used only on line: 470

542:        bytes32 mutualId = store.edges[edgeId].mutualId();	// @audit-issue: mutualId used only on line: 543

584:        uint256 diff = (end - 1) ^ start;	// @audit-issue: diff used only on line: 585

585:        uint256 mostSignificantSharedBit = UintUtilsLib.mostSignificantBit(diff);	// @audit-issue: mostSignificantSharedBit used only on line: 586

586:        uint256 mask = type(uint256).max << mostSignificantSharedBit;	// @audit-issue: mask used only on line: 587

623:            (bytes32[] memory preExpansion, bytes32[] memory proof) = abi.decode(prefixProof, (bytes32[], bytes32[]));	// @audit-issue: preExpansion used only on line: 625

623:            (bytes32[] memory preExpansion, bytes32[] memory proof) = abi.decode(prefixProof, (bytes32[], bytes32[]));	// @audit-issue: proof used only on line: 625

646:            ChallengeEdge memory upperChild = ChallengeEdgeLib.newChildEdge(	// @audit-issue: upperChild used only on line: 651
647:                ce.originId, bisectionHistoryRoot, middleHeight, ce.endHistoryRoot, ce.endHeight, ce.level
648:            );

817:        bytes32 afterHash =	// @audit-issue: afterHash used only on line: 822
818:            oneStepProofEntry.proveOneStep(execCtx, machineStep, oneStepData.beforeHash, oneStepData.proof);
```
[251](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/challengeV2/libraries/EdgeChallengeManagerLib.sol#L251-L252), [263](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/challengeV2/libraries/EdgeChallengeManagerLib.sol#L263-L263), [264](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/challengeV2/libraries/EdgeChallengeManagerLib.sol#L264-L264), [297](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/challengeV2/libraries/EdgeChallengeManagerLib.sol#L297-L303), [297](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/challengeV2/libraries/EdgeChallengeManagerLib.sol#L297-L303), [297](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/challengeV2/libraries/EdgeChallengeManagerLib.sol#L297-L303), [334](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/challengeV2/libraries/EdgeChallengeManagerLib.sol#L334-L334), [381](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/challengeV2/libraries/EdgeChallengeManagerLib.sol#L381-L382), [381](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/challengeV2/libraries/EdgeChallengeManagerLib.sol#L381-L382), [421](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/challengeV2/libraries/EdgeChallengeManagerLib.sol#L421-L422), [421](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/challengeV2/libraries/EdgeChallengeManagerLib.sol#L421-L422), [424](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/challengeV2/libraries/EdgeChallengeManagerLib.sol#L424-L424), [469](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/challengeV2/libraries/EdgeChallengeManagerLib.sol#L469-L469), [542](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/challengeV2/libraries/EdgeChallengeManagerLib.sol#L542-L542), [584](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/challengeV2/libraries/EdgeChallengeManagerLib.sol#L584-L584), [585](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/challengeV2/libraries/EdgeChallengeManagerLib.sol#L585-L585), [586](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/challengeV2/libraries/EdgeChallengeManagerLib.sol#L586-L586), [623](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/challengeV2/libraries/EdgeChallengeManagerLib.sol#L623-L623), [623](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/challengeV2/libraries/EdgeChallengeManagerLib.sol#L623-L623), [646](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/challengeV2/libraries/EdgeChallengeManagerLib.sol#L646-L648), [817](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/challengeV2/libraries/EdgeChallengeManagerLib.sol#L817-L818), 


```solidity
Path: ./src/challengeV2/libraries/MerkleTreeLib.sol

174:        uint256 postSize = meSize + 2 ** level;	// @audit-issue: postSize used only on line: 178

268:        uint256 msb = UintUtilsLib.mostSignificantBit(startSize ^ endSize);	// @audit-issue: msb used only on line: 269

363:        bytes32 calculatedRoot = MerkleLib.calculateRoot(proof, index, keccak256(abi.encodePacked(leaf)));	// @audit-issue: calculatedRoot used only on line: 364
```
[174](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/challengeV2/libraries/MerkleTreeLib.sol#L174-L174), [268](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/challengeV2/libraries/MerkleTreeLib.sol#L268-L268), [363](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/challengeV2/libraries/MerkleTreeLib.sol#L363-L363), 


```solidity
Path: ./src/challengeV2/libraries/UintUtilsLib.sol

18:        uint256 isolated = ((x - 1) & x) ^ x;	// @audit-issue: isolated used only on line: 21
```
[18](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/challengeV2/libraries/UintUtilsLib.sol#L18-L18), 


```solidity
Path: ./src/assertionStakingPool/EdgeStakingPool.sol

45:        uint256 requiredStake = EdgeChallengeManager(challengeManager).stakeAmounts(args.level);	// @audit-issue: requiredStake used only on line: 46
```
[45](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/assertionStakingPool/EdgeStakingPool.sol#L45-L45), 


```solidity
Path: ./src/assertionStakingPool/StakingPoolCreatorUtils.sol

14:        bytes32 bytecodeHash = keccak256(abi.encodePacked(creationCode, args));	// @audit-issue: bytecodeHash used only on line: 15
```
[14](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/assertionStakingPool/StakingPoolCreatorUtils.sol#L14-L14), 


```solidity
Path: ./src/assertionStakingPool/EdgeStakingPoolCreator.sol

19:        EdgeStakingPool pool = new EdgeStakingPool{salt: 0}(challengeManager, edgeId);	// @audit-issue: pool used only on line: 21
```
[19](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/assertionStakingPool/EdgeStakingPoolCreator.sol#L19-L19), 


#### Recommendation

Eliminate single-use stack variables in Solidity to optimize gas consumption. Directly use the assigned value in the place of the variable. This approach saves the 3 gas typically used for the extra stack assignment, streamlining the function's execution and enhancing overall gas efficiency.

### Avoid Using State Variables Directly in `emit` for Gas Efficiency
In Solidity, emitting events is a common way to log contract activity and changes, especially for off-chain monitoring and interfacing. However, using state variables directly in `emit` statements can lead to increased gas costs. Each access to a state variable incurs gas due to storage reading operations. When these variables are used directly in `emit` statements, especially within functions that perform multiple operations, the cumulative gas cost can become significant. Instead, caching state variables in memory and using these local copies in `emit` statements can optimize gas usage.


```solidity
Path: ./src/bridge/SequencerInbox.sol

344:        emit SequencerBatchDelivered(
345:            seqMessageIndex,
346:            beforeAcc,
347:            afterAcc,
348:            delayedAcc,
349:            totalDelayedMessagesRead,	// @audit-issue: `totalDelayedMessagesRead` is a state variable and used on line(s): ['295']
350:            timeBounds,
351:            IBridge.BatchDataLocation.NoData
352:        );
```
[349](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/bridge/SequencerInbox.sol#L344-L352), 


```solidity
Path: ./src/rollup/RollupCore.sol

504:        emit AssertionCreated(
505:            newAssertionHash,
506:            prevAssertionHash,
507:            assertion,
508:            sequencerBatchAcc,
509:            nextInboxPosition,
510:            wasmModuleRoot,	// @audit-issue: `wasmModuleRoot` is a state variable and used on line(s): ['491']
511:            baseStake,
512:            address(challengeManager),
513:            confirmPeriodBlocks
514:        );

504:        emit AssertionCreated(
505:            newAssertionHash,
506:            prevAssertionHash,
507:            assertion,
508:            sequencerBatchAcc,
509:            nextInboxPosition,
510:            wasmModuleRoot,
511:            baseStake,	// @audit-issue: `baseStake` is a state variable and used on line(s): ['492']
512:            address(challengeManager),
513:            confirmPeriodBlocks
514:        );

504:        emit AssertionCreated(
505:            newAssertionHash,
506:            prevAssertionHash,
507:            assertion,
508:            sequencerBatchAcc,
509:            nextInboxPosition,
510:            wasmModuleRoot,
511:            baseStake,
512:            address(challengeManager),	// @audit-issue: `challengeManager` is a state variable and used on line(s): ['493']
513:            confirmPeriodBlocks
514:        );

504:        emit AssertionCreated(
505:            newAssertionHash,
506:            prevAssertionHash,
507:            assertion,
508:            sequencerBatchAcc,
509:            nextInboxPosition,
510:            wasmModuleRoot,
511:            baseStake,
512:            address(challengeManager),
513:            confirmPeriodBlocks	// @audit-issue: `confirmPeriodBlocks` is a state variable and used on line(s): ['494']
514:        );
```
[510](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/RollupCore.sol#L504-L514), [511](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/RollupCore.sol#L504-L514), [512](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/RollupCore.sol#L504-L514), [513](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/RollupCore.sol#L504-L514), 


```solidity
Path: ./src/rollup/RollupCreator.sol

251:        emit RollupCreated(
252:            address(rollup),
253:            deployParams.nativeToken,
254:            address(bridgeContracts.inbox),
255:            address(bridgeContracts.outbox),
256:            address(bridgeContracts.rollupEventInbox),
257:            address(challengeManager),
258:            address(proxyAdmin),
259:            address(bridgeContracts.sequencerInbox),
260:            address(bridgeContracts.bridge),
261:            address(upgradeExecutor),
262:            address(validatorWalletCreator)	// @audit-issue: `validatorWalletCreator` is a state variable and used on line(s): ['220']
263:        );
```
[262](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/RollupCreator.sol#L251-L263), 


```solidity
Path: ./src/rollup/RollupAdminLogic.sol

90:        emit AssertionCreated(
91:            genesisHash,
92:            parentAssertionHash,
93:            assertionInputs,
94:            inboxAcc,
95:            currentInboxCount,
96:            wasmModuleRoot,	// @audit-issue: `wasmModuleRoot` is a state variable and used on line(s): ['79']
97:            baseStake,
98:            address(challengeManager),
99:            confirmPeriodBlocks
100:        );

90:        emit AssertionCreated(
91:            genesisHash,
92:            parentAssertionHash,
93:            assertionInputs,
94:            inboxAcc,
95:            currentInboxCount,
96:            wasmModuleRoot,
97:            baseStake,	// @audit-issue: `baseStake` is a state variable and used on line(s): ['80']
98:            address(challengeManager),
99:            confirmPeriodBlocks
100:        );

90:        emit AssertionCreated(
91:            genesisHash,
92:            parentAssertionHash,
93:            assertionInputs,
94:            inboxAcc,
95:            currentInboxCount,
96:            wasmModuleRoot,
97:            baseStake,
98:            address(challengeManager),	// @audit-issue: `challengeManager` is a state variable and used on line(s): ['81']
99:            confirmPeriodBlocks
100:        );

90:        emit AssertionCreated(
91:            genesisHash,
92:            parentAssertionHash,
93:            assertionInputs,
94:            inboxAcc,
95:            currentInboxCount,
96:            wasmModuleRoot,
97:            baseStake,
98:            address(challengeManager),
99:            confirmPeriodBlocks	// @audit-issue: `confirmPeriodBlocks` is a state variable and used on line(s): ['82']
100:        );
```
[96](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/RollupAdminLogic.sol#L90-L100), [97](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/RollupAdminLogic.sol#L90-L100), [98](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/RollupAdminLogic.sol#L90-L100), [99](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/RollupAdminLogic.sol#L90-L100), 


```solidity
Path: ./src/challengeV2/EdgeChallengeManager.sol

535:        emit EdgeConfirmedByTime(edgeId, store.edges[edgeId].mutualId(), totalTimeUnrivaled);	// @audit-issue: `store` is a state variable and used on line(s): ['533', '512']

568:        emit EdgeConfirmedByOneStepProof(edgeId, store.edges[edgeId].mutualId());	// @audit-issue: `store` is a state variable and used on line(s): ['556', '546']

584:        emit EdgeRefunded(edgeId, store.edges[edgeId].mutualId(), address(st), sa);	// @audit-issue: `store` is a state variable and used on line(s): ['573']
```
[535](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/challengeV2/EdgeChallengeManager.sol#L535-L535), [568](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/challengeV2/EdgeChallengeManager.sol#L568-L568), [584](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/challengeV2/EdgeChallengeManager.sol#L584-L584), 


#### Recommendation


To optimize gas efficiency, cache state variables in memory when they are used multiple times within a function, including in `emit` statements.

### Storage Layout Optimization
Storage Layout Optimization in Solidity involves arranging state variables to minimize gas costs. Since storage is expensive, combining variables into as few slots as possible and deleting unneeded variables can significantly reduce the gas needed for contract operations.

```solidity
Path: ./src/challengeV2/EdgeChallengeManager.sol

266:    EdgeStore internal store;	// @audit-issue: ['Current storage layout is like this: ', "However it can be optimized by 1 storage by storing variables like in order: \n\t`['store', 'stakeAmounts', 'LAYERZERO_BLOCKEDGE_HEIGHT', 'LAYERZERO_BIGSTEPEDGE_HEIGHT', 'LAYERZERO_SMALLSTEPEDGE_HEIGHT', 'excessStakeReceiver', 'stakeToken', 'assertionChain', 'oneStepProofEntry', 'challengePeriodBlocks', 'NUM_BIGSTEP_LEVEL']`"]
267:
268:    /// @notice When creating a zero layer block edge a stake must be supplied. However since we know that only
269:    ///         one edge in a group of rivals can ever be confirmed, we only need to keep one stake in this contract
270:    ///         to later refund for that edge. Other stakes can immediately be sent to an excess stake receiver.
271:    ///         This excess stake receiver can then choose to refund the gas of participants who aided in the confirmation
272:    ///         of the winning edge
273:    address public excessStakeReceiver;
274:
275:    /// @notice The token to supply stake in
276:    IERC20 public stakeToken;
277:
278:    /// @notice The amount of stake token to be supplied when creating a zero layer block edge at a given level
279:    uint256[] public stakeAmounts;
280:
281:    /// @notice The number of blocks accumulated on an edge before it can be confirmed by time
282:    uint64 public challengePeriodBlocks;
283:
284:    /// @notice The assertion chain about which challenges are created
285:    IAssertionChain public assertionChain;
286:
287:    /// @inheritdoc IEdgeChallengeManager
288:    IOneStepProofEntry public override oneStepProofEntry;
289:
290:    /// @notice The end height of layer zero Block edges
291:    uint256 public LAYERZERO_BLOCKEDGE_HEIGHT;
292:    /// @notice The end height of layer zero BigStep edges
293:    uint256 public LAYERZERO_BIGSTEPEDGE_HEIGHT;
294:    /// @notice The end height of layer zero SmallStep edges
295:    uint256 public LAYERZERO_SMALLSTEPEDGE_HEIGHT;
296:    /// @notice The number of big step levels configured for this challenge manager
297:    ///         There is 1 block level, 1 small step level and N big step levels
298:    uint8 public NUM_BIGSTEP_LEVEL;
```
[266](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/challengeV2/EdgeChallengeManager.sol#L266-L298), 


#### Recommendation

To optimize storage and reduce gas costs, rearrange the storage variables in a way that makes the most of each 32-byte storage slot.

### Don't emit events inside a loop
Emitting an event has an overhead of 375 gas, which will be incurred on every iteration of the loop. It is cheaper to emit only once after the loop has finished.

```solidity
Path: ./src/challengeV2/EdgeChallengeManager.sol

494:            if (updated) emit TimerCacheUpdated(edgeIds[i], newValue);	// @audit-issue
```
[494](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/challengeV2/EdgeChallengeManager.sol#L494-L494), 


#### Recommendation

To optimize gas usage, avoid emitting events inside loops in Solidity. Instead, emit a single event after the loop completes, thereby saving the 375 gas overhead incurred on each iteration.

### `Internal` functions only called once can be inlined to save gas
If an internal function is only used once, there is no need to modularize it, unless the function calling it would otherwise be too long and complex. Not inlining costs 20 to 40 gas because of two extra JUMP instructions and additional stack operations needed for function calls.

```solidity
Path: ./src/bridge/SequencerInbox.sol

216:    function getTimeBounds() internal view virtual returns (IBridge.TimeBounds memory) {	// @audit-issue

659:    function formEmptyDataHash(uint256 afterDelayedMessagesRead)	// @audit-issue

675:    function isValidCallDataFlag(bytes1 headerByte) internal pure returns (bool) {	// @audit-issue

688:    function formCallDataHash(bytes calldata data, uint256 afterDelayedMessagesRead)	// @audit-issue

725:    function formBlobDataHash(uint256 afterDelayedMessagesRead)	// @audit-issue
```
[216](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/bridge/SequencerInbox.sol#L216-L216), [659](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/bridge/SequencerInbox.sol#L659-L659), [675](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/bridge/SequencerInbox.sol#L675-L675), [688](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/bridge/SequencerInbox.sol#L688-L688), [725](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/bridge/SequencerInbox.sol#L725-L725), 


```solidity
Path: ./src/bridge/DelayBuffer.sol

33:    function calcBuffer(	// @audit-issue

82:    function calcPendingBuffer(BufferData storage self, uint64 blockNumber)	// @audit-issue

104:    function isSynced(BufferData storage self) internal view returns (bool) {	// @audit-issue

115:    function isValidBufferConfig(BufferConfig memory config) internal pure returns (bool) {	// @audit-issue
```
[33](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/bridge/DelayBuffer.sol#L33-L33), [82](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/bridge/DelayBuffer.sol#L82-L82), [104](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/bridge/DelayBuffer.sol#L104-L104), [115](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/bridge/DelayBuffer.sol#L115-L115), 


```solidity
Path: ./src/rollup/BridgeCreator.sol

63:    function _createBridge(	// @audit-issue
```
[63](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/BridgeCreator.sol#L63-L63), 


```solidity
Path: ./src/rollup/RollupCore.sol

225:    function initializeCore(AssertionNode memory initialAssertion, bytes32 assertionHash) internal {	// @audit-issue

274:    function createNewStake(address stakerAddress, uint256 depositAmount, address withdrawalAddress) internal {	// @audit-issue

286:    function increaseStakeBy(address stakerAddress, uint256 amountAdded) internal {	// @audit-issue

317:    function withdrawStaker(address stakerAddress) internal {	// @audit-issue

331:    function withdrawFunds(address account) internal returns (uint256) {	// @audit-issue
```
[225](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/RollupCore.sol#L225-L225), [274](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/RollupCore.sol#L274-L274), [286](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/RollupCore.sol#L286-L286), [317](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/RollupCore.sol#L317-L317), [331](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/RollupCore.sol#L331-L331), 


```solidity
Path: ./src/rollup/RollupUserLogic.sol

33:    function _chainIdChanged() internal view returns (bool) {	// @audit-issue

51:    function _validatorIsAfk() internal view returns (bool) {	// @audit-issue

137:    function _newStake(uint256 depositAmount, address withdrawalAddress) internal onlyValidator whenNotPaused {	// @audit-issue

232:    function _addToDeposit(address stakerAddress, uint256 depositAmount) internal onlyValidator whenNotPaused {	// @audit-issue
```
[33](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/RollupUserLogic.sol#L33-L33), [51](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/RollupUserLogic.sol#L51-L51), [137](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/RollupUserLogic.sol#L137-L137), [232](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/RollupUserLogic.sol#L232-L232), 


```solidity
Path: ./src/rollup/RollupCreator.sol

85:    function createChallengeManager(address rollupAddr, address proxyAdminAddr, Config memory config)	// @audit-issue

267:    function _deployUpgradeExecutor(address rollupOwner, ProxyAdmin proxyAdmin)	// @audit-issue

287:    function _deployFactories(	// @audit-issue
```
[85](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/RollupCreator.sol#L85-L85), [267](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/RollupCreator.sol#L267-L267), [287](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/RollupCreator.sol#L287-L287), 


```solidity
Path: ./src/challengeV2/libraries/ArrayUtilsLib.sol

27:    function slice(bytes32[] memory arr, uint256 startIndex, uint256 endIndex)	// @audit-issue
```
[27](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/challengeV2/libraries/ArrayUtilsLib.sol#L27-L27), 


```solidity
Path: ./src/challengeV2/libraries/EdgeChallengeManagerLib.sol

483:    function hasLengthOneRival(EdgeStore storage store, bytes32 edgeId) internal view returns (bool) {	// @audit-issue

576:    function mandatoryBisectionHeight(uint256 start, uint256 end) internal pure returns (uint256) {	// @audit-issue
```
[483](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/challengeV2/libraries/EdgeChallengeManagerLib.sol#L483-L483), [576](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/challengeV2/libraries/EdgeChallengeManagerLib.sol#L576-L576), 


```solidity
Path: ./src/challengeV2/libraries/MerkleTreeLib.sol

238:    function appendLeaf(bytes32[] memory me, bytes32 leaf) internal pure returns (bytes32[] memory) {	// @audit-issue

251:    function maximumAppendBetween(uint256 startSize, uint256 endSize) internal pure returns (uint256) {	// @audit-issue
```
[238](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/challengeV2/libraries/MerkleTreeLib.sol#L238-L238), [251](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/challengeV2/libraries/MerkleTreeLib.sol#L251-L251), 


```solidity
Path: ./src/challengeV2/libraries/ChallengeEdgeLib.sol

93:    function newLayerZeroEdge(	// @audit-issue

258:    function isLayerZero(ChallengeEdge storage edge) internal view returns (bool) {	// @audit-issue
```
[93](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/challengeV2/libraries/ChallengeEdgeLib.sol#L93-L93), [258](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/challengeV2/libraries/ChallengeEdgeLib.sol#L258-L258), 


```solidity
Path: ./src/challengeV2/libraries/UintUtilsLib.sol

14:    function leastSignificantBit(uint256 x) internal pure returns (uint256 msb) {	// @audit-issue
```
[14](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/challengeV2/libraries/UintUtilsLib.sol#L14-L14), 


#### Recommendation

Inline 'internal' functions in Solidity that are called only once to save gas. This avoids the additional gas cost of 20 to 40 units associated with extra JUMP instructions and stack operations required for separate function calls, unless the calling function becomes too complex.

### `Private` functions only called once can be inlined to save gas
If a private function is only used once, there is no need to modularize it, unless the function calling it would otherwise be too long and complex. Not inlining costs 20 to 40 gas because of two extra JUMP instructions and additional stack operations needed for function calls.

```solidity
Path: ./src/rollup/BOLDUpgradeAction.sol

341:    function cleanupOldRollup() private {	// @audit-issue

367:    function createConfig() private view returns (Config memory) {	// @audit-issue

411:    function upgradeSurroundingContracts(address newRollupAddress) private {	// @audit-issue

433:    function upgradeSequencerInbox() private {	// @audit-issue
```
[341](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/BOLDUpgradeAction.sol#L341-L341), [367](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/BOLDUpgradeAction.sol#L367-L367), [411](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/BOLDUpgradeAction.sol#L411-L411), [433](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/BOLDUpgradeAction.sol#L433-L433), 


```solidity
Path: ./src/rollup/RollupCore.sol

355:    function deleteStaker(address stakerAddress) private {	// @audit-issue
```
[355](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/RollupCore.sol#L355-L355), 


```solidity
Path: ./src/challengeV2/libraries/EdgeChallengeManagerLib.sol

213:    function layerZeroTypeSpecificChecks(	// @audit-issue

344:    function layerZeroCommonChecks(ProofData memory proofData, CreateEdgeArgs calldata args, uint256 expectedEndHeight)	// @audit-issue

391:    function toLayerZeroEdge(bytes32 originId, bytes32 startHistoryRoot, CreateEdgeArgs calldata args)	// @audit-issue

689:    function checkClaimIdLink(EdgeStore storage store, bytes32 edgeId, bytes32 claimingEdgeId, uint8 numBigStepLevel)	// @audit-issue
```
[213](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/challengeV2/libraries/EdgeChallengeManagerLib.sol#L213-L213), [344](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/challengeV2/libraries/EdgeChallengeManagerLib.sol#L344-L344), [391](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/challengeV2/libraries/EdgeChallengeManagerLib.sol#L391-L391), [689](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/challengeV2/libraries/EdgeChallengeManagerLib.sol#L689-L689), 


#### Recommendation

Inline 'private' functions in Solidity that are called only once to save gas. This avoids the additional gas cost of 20 to 40 units associated with extra JUMP instructions and stack operations required for separate function calls, unless the calling function becomes too complex.

### Optimizing Arithmetic with Shift Operators for Division and Multiplication by Powers of Two
In computational operations, especially within contexts where efficiency matters, certain arithmetic operations can be optimized. One such optimization is leveraging shift operators for division and multiplication by powers of two. This stems from the binary nature of numbers in computing, where shifting bits to the left (using `<<`) effectively multiplies a number by 2 for each position shifted, and shifting bits to the right (using `>>`) divides the number by 2 for each position shifted.

In Solidity, and many other programming languages, using shift operators can be more gas-efficient than traditional arithmetic operations for these specific cases. For instance, instead of performing `value * 4`, one can use `value << 2`, and instead of `value / 4`, one can use `value >> 2`. These optimizations can result in reduced gas costs and faster execution times.


```solidity
Path: ./src/bridge/SequencerInbox.sol

906:        if (keysetBytes.length >= 64 * 1024) revert KeysetTooLarge();	// @audit-issue
```
[906](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/bridge/SequencerInbox.sol#L906-L906), 


#### Recommendation

When performing division or multiplication by powers of two in Solidity, consider using shift operators (`<<` for multiplication and `>>` for division) for improved gas efficiency. This optimization takes advantage of the binary nature of computing and can lead to reduced gas costs and faster execution times.

### Experimental Features Enabled
Experimental features in Solidity refer to functionalities or language features that are not stable or finalized and are still in the testing and development phase. Enabling experimental features in a smart contract can introduce risks and potential vulnerabilities, as these features may not behave as expected or may change in future compiler versions. This issue highlights situations where experimental features have been enabled in Solidity code.


```solidity
Path: ./src/bridge/ISequencerInbox.sol

7:pragma experimental ABIEncoderV2;	// @audit-issue
```
[7](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/bridge/ISequencerInbox.sol#L7-L7), 


#### Recommendation

Avoid using experimental features in Solidity for production smart contracts. If experimental features are necessary for development, ensure thorough testing and be prepared for potential changes in future compiler versions. Prioritize stability and security in contract design.

### Multiple Pragma Definition
In Solidity, pragma statements are used to specify the compiler version and settings for a smart contract. This issue occurs when multiple pragma statements are defined within the same contract or file. Each pragma statement should be unique within a contract or file, as it sets the compiler version and potentially other compiler-specific configurations.


```solidity
Path: ./src/bridge/SequencerInbox.sol

5:pragma solidity ^0.8.0;	// @audit-issue
```
[5](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/bridge/SequencerInbox.sol#L5-L5), 


```solidity
Path: ./src/bridge/DelayBufferTypes.sol

7:pragma solidity >=0.6.9 <0.9.0;	// @audit-issue
```
[7](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/bridge/DelayBufferTypes.sol#L7-L7), 


```solidity
Path: ./src/bridge/DelayBuffer.sol

5:pragma solidity ^0.8.0;	// @audit-issue
```
[5](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/bridge/DelayBuffer.sol#L5-L5), 


```solidity
Path: ./src/bridge/ISequencerInbox.sol

6:pragma solidity >=0.6.9 <0.9.0;	// @audit-issue
```
[6](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/bridge/ISequencerInbox.sol#L6-L6), 


```solidity
Path: ./src/rollup/IRollupLogic.sol

5:pragma solidity ^0.8.0;	// @audit-issue
```
[5](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/IRollupLogic.sol#L5-L5), 


```solidity
Path: ./src/rollup/RollupLib.sol

5:pragma solidity ^0.8.0;	// @audit-issue
```
[5](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/RollupLib.sol#L5-L5), 


```solidity
Path: ./src/rollup/BOLDUpgradeAction.sol

5:pragma solidity ^0.8.0;	// @audit-issue
```
[5](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/BOLDUpgradeAction.sol#L5-L5), 


```solidity
Path: ./src/rollup/Assertion.sol

5:pragma solidity ^0.8.0;	// @audit-issue
```
[5](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/Assertion.sol#L5-L5), 


```solidity
Path: ./src/rollup/AssertionState.sol

5:pragma solidity ^0.8.0;	// @audit-issue
```
[5](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/AssertionState.sol#L5-L5), 


```solidity
Path: ./src/rollup/BridgeCreator.sol

5:pragma solidity ^0.8.0;	// @audit-issue
```
[5](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/BridgeCreator.sol#L5-L5), 


```solidity
Path: ./src/rollup/RollupCore.sol

5:pragma solidity ^0.8.0;	// @audit-issue
```
[5](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/RollupCore.sol#L5-L5), 


```solidity
Path: ./src/rollup/IRollupCore.sol

5:pragma solidity ^0.8.0;	// @audit-issue
```
[5](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/IRollupCore.sol#L5-L5), 


```solidity
Path: ./src/rollup/RollupUserLogic.sol

5:pragma solidity ^0.8.0;	// @audit-issue
```
[5](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/RollupUserLogic.sol#L5-L5), 


```solidity
Path: ./src/rollup/RollupCreator.sol

5:pragma solidity ^0.8.0;	// @audit-issue
```
[5](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/RollupCreator.sol#L5-L5), 


```solidity
Path: ./src/rollup/RollupAdminLogic.sol

5:pragma solidity ^0.8.0;	// @audit-issue
```
[5](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/RollupAdminLogic.sol#L5-L5), 


```solidity
Path: ./src/rollup/IRollupAdmin.sol

5:pragma solidity ^0.8.0;	// @audit-issue
```
[5](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/IRollupAdmin.sol#L5-L5), 


```solidity
Path: ./src/rollup/Config.sol

5:pragma solidity ^0.8.0;	// @audit-issue
```
[5](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/Config.sol#L5-L5), 


```solidity
Path: ./src/rollup/RollupProxy.sol

5:pragma solidity ^0.8.0;	// @audit-issue
```
[5](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/RollupProxy.sol#L5-L5), 


```solidity
Path: ./src/libraries/Error.sol

5:pragma solidity ^0.8.4;	// @audit-issue
```
[5](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/libraries/Error.sol#L5-L5), 


```solidity
Path: ./src/challengeV2/IAssertionChain.sol

5:pragma solidity ^0.8.17;	// @audit-issue
```
[5](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/challengeV2/IAssertionChain.sol#L5-L5), 


```solidity
Path: ./src/challengeV2/EdgeChallengeManager.sol

5:pragma solidity ^0.8.17;	// @audit-issue
```
[5](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/challengeV2/EdgeChallengeManager.sol#L5-L5), 


```solidity
Path: ./src/challengeV2/libraries/ArrayUtilsLib.sol

5:pragma solidity ^0.8.17;	// @audit-issue
```
[5](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/challengeV2/libraries/ArrayUtilsLib.sol#L5-L5), 


```solidity
Path: ./src/challengeV2/libraries/EdgeChallengeManagerLib.sol

5:pragma solidity ^0.8.17;	// @audit-issue
```
[5](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/challengeV2/libraries/EdgeChallengeManagerLib.sol#L5-L5), 


```solidity
Path: ./src/challengeV2/libraries/MerkleTreeLib.sol

5:pragma solidity ^0.8.17;	// @audit-issue
```
[5](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/challengeV2/libraries/MerkleTreeLib.sol#L5-L5), 


```solidity
Path: ./src/challengeV2/libraries/ChallengeEdgeLib.sol

5:pragma solidity ^0.8.17;	// @audit-issue
```
[5](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/challengeV2/libraries/ChallengeEdgeLib.sol#L5-L5), 


```solidity
Path: ./src/challengeV2/libraries/UintUtilsLib.sol

5:pragma solidity ^0.8.17;	// @audit-issue
```
[5](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/challengeV2/libraries/UintUtilsLib.sol#L5-L5), 


```solidity
Path: ./src/challengeV2/libraries/ChallengeErrors.sol

5:pragma solidity ^0.8.17;	// @audit-issue
```
[5](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/challengeV2/libraries/ChallengeErrors.sol#L5-L5), 


```solidity
Path: ./src/challengeV2/libraries/Enums.sol

5:pragma solidity ^0.8.17;	// @audit-issue
```
[5](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/challengeV2/libraries/Enums.sol#L5-L5), 


```solidity
Path: ./src/assertionStakingPool/AssertionStakingPoolCreator.sol

6:pragma solidity ^0.8.0;	// @audit-issue
```
[6](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/assertionStakingPool/AssertionStakingPoolCreator.sol#L6-L6), 


```solidity
Path: ./src/assertionStakingPool/EdgeStakingPool.sol

5:pragma solidity ^0.8.0;	// @audit-issue
```
[5](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/assertionStakingPool/EdgeStakingPool.sol#L5-L5), 


```solidity
Path: ./src/assertionStakingPool/StakingPoolCreatorUtils.sol

6:pragma solidity ^0.8.0;	// @audit-issue
```
[6](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/assertionStakingPool/StakingPoolCreatorUtils.sol#L6-L6), 


```solidity
Path: ./src/assertionStakingPool/EdgeStakingPoolCreator.sol

6:pragma solidity ^0.8.0;	// @audit-issue
```
[6](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/assertionStakingPool/EdgeStakingPoolCreator.sol#L6-L6), 


```solidity
Path: ./src/assertionStakingPool/AssertionStakingPool.sol

6:pragma solidity ^0.8.0;	// @audit-issue
```
[6](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/assertionStakingPool/AssertionStakingPool.sol#L6-L6), 


```solidity
Path: ./src/assertionStakingPool/AbsBoldStakingPool.sol

5:pragma solidity ^0.8.0;	// @audit-issue
```
[5](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/assertionStakingPool/AbsBoldStakingPool.sol#L5-L5), 


```solidity
Path: ./src/assertionStakingPool/interfaces/IAssertionStakingPool.sol

5:pragma solidity ^0.8.0;	// @audit-issue
```
[5](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/assertionStakingPool/interfaces/IAssertionStakingPool.sol#L5-L5), 


```solidity
Path: ./src/assertionStakingPool/interfaces/IEdgeStakingPool.sol

5:pragma solidity ^0.8.0;	// @audit-issue
```
[5](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/assertionStakingPool/interfaces/IEdgeStakingPool.sol#L5-L5), 


```solidity
Path: ./src/assertionStakingPool/interfaces/IEdgeStakingPoolCreator.sol

5:pragma solidity ^0.8.0;	// @audit-issue
```
[5](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/assertionStakingPool/interfaces/IEdgeStakingPoolCreator.sol#L5-L5), 


```solidity
Path: ./src/assertionStakingPool/interfaces/IAbsBoldStakingPool.sol

5:pragma solidity ^0.8.0;	// @audit-issue
```
[5](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/assertionStakingPool/interfaces/IAbsBoldStakingPool.sol#L5-L5), 


```solidity
Path: ./src/assertionStakingPool/interfaces/IAssertionStakingPoolCreator.sol

5:pragma solidity ^0.8.0;	// @audit-issue
```
[5](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/assertionStakingPool/interfaces/IAssertionStakingPoolCreator.sol#L5-L5), 


#### Recommendation

Ensure each Solidity contract or file contains a single, unique pragma statement to clearly specify the intended compiler version and settings. Avoid multiple pragma definitions to prevent confusion and potential compilation issues.

### Use `private` Rather than `public` for Constants 
In Solidity, constants represent immutable values that cannot be changed after they are set at compile-time. By default, constants have internal visibility, meaning they can be accessed within the contract they are declared in and in derived contracts. If a constant is explicitly declared as `public`, Solidity automatically generates a getter function for it. While this might seem harmless, it actually incurs a gas overhead, especially when the contract is deployed, as the EVM needs to generate bytecode for that getter. Conversely, declaring constants as `private` ensures that no additional getter is generated, optimizing gas usage.

```solidity
Path: ./src/bridge/SequencerInbox.sol

70:    uint256 public constant HEADER_LENGTH = 40;	// @audit-issue

73:    bytes1 public constant DATA_AUTHENTICATED_FLAG = 0x40;	// @audit-issue

76:    bytes1 public constant DATA_BLOB_HEADER_FLAG = DATA_AUTHENTICATED_FLAG | 0x10;	// @audit-issue

79:    bytes1 public constant DAS_MESSAGE_HEADER_FLAG = 0x80;	// @audit-issue

82:    bytes1 public constant TREE_DAS_MESSAGE_HEADER_FLAG = 0x08;	// @audit-issue

85:    bytes1 public constant BROTLI_MESSAGE_HEADER_FLAG = 0x00;	// @audit-issue

88:    bytes1 public constant ZERO_HEAVY_MESSAGE_HEADER_FLAG = 0x20;	// @audit-issue
```
[70](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/bridge/SequencerInbox.sol#L70-L70), [73](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/bridge/SequencerInbox.sol#L73-L73), [76](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/bridge/SequencerInbox.sol#L76-L76), [79](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/bridge/SequencerInbox.sol#L79-L79), [82](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/bridge/SequencerInbox.sol#L82-L82), [85](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/bridge/SequencerInbox.sol#L85-L85), [88](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/bridge/SequencerInbox.sol#L88-L88), 


```solidity
Path: ./src/bridge/DelayBuffer.sol

17:    uint256 public constant BASIS = 10000;	// @audit-issue
```
[17](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/bridge/DelayBuffer.sol#L17-L17), 


```solidity
Path: ./src/rollup/RollupUserLogic.sol

49:    uint256 public constant VALIDATOR_AFK_BLOCKS = 201600;	// @audit-issue
```
[49](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/RollupUserLogic.sol#L49-L49), 


```solidity
Path: ./src/challengeV2/libraries/EdgeChallengeManagerLib.sol

135:    bytes32 public constant UNRIVALED = keccak256(abi.encodePacked("UNRIVALED"));	// @audit-issue
```
[135](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/challengeV2/libraries/EdgeChallengeManagerLib.sol#L135-L135), 


```solidity
Path: ./src/challengeV2/libraries/MerkleTreeLib.sol

104:    uint256 public constant MAX_LEVEL = 64;	// @audit-issue
```
[104](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/challengeV2/libraries/MerkleTreeLib.sol#L104-L104), 


#### Recommendation

To optimize gas usage in your Solidity contracts, declare constants with `private` visibility rather than `public` when possible. Using `private` prevents the automatic generation of a getter function, reducing gas overhead, especially during contract deployment.

### Use `Array.unsafeAccess()` to avoid repeated array length checks
When using storage arrays, solidity adds an internal lookup of the array's length (a Gcoldsload **2100 gas**) to ensure you don't read past the array's end. You can avoid this lookup by using [`Array.unsafeAccess()`](https://github.com/OpenZeppelin/openzeppelin-contracts/blob/94697be8a3f0dfcd95dfb13ffbd39b5973f5c65d/contracts/utils/Arrays.sol#L57) in cases where the length has already been checked, as is the case with the instances below

```solidity
Path: ./src/rollup/RollupCore.sol

359:        _stakerList[stakerIndex] = _stakerList[_stakerList.length - 1];	// ('@audit-issue: Length of `_stakerList` already checked. ',)

360:        _stakerMap[_stakerList[stakerIndex]].index = stakerIndex;	// ('@audit-issue: Length of `_stakerList` already checked. ',)
```
[359](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/RollupCore.sol#L359-L359), [360](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/RollupCore.sol#L360-L360), 


#### Recommendation

Leverage `Array.unsafeAccess()` from OpenZeppelin's `Arrays` library for storage array accesses where the index is already known to be within bounds. Ensure that you have thoroughly checked the array length prior to using this method to avoid any risk of out-of-bounds errors. This approach is particularly beneficial in performance-critical sections of your code, such as loops over storage arrays where the length check is redundant. Incorporating `Array.unsafeAccess()` judiciously can lead to significant gas savings, making your contract more efficient. Always balance the use of such optimizations with the need for code safety and clarity.

### Consider pre-calculating the address of `address(this)` to save gas
Use `foundry`'s [`script.sol`](https://book.getfoundry.sh/reference/forge-std/compute-create-address) or `solady`'s [`LibRlp.sol`](https://github.com/Vectorized/solady/blob/main/src/utils/LibRLP.sol) to save the value in a constant, which will avoid having to spend gas to push the value on the stack every time it's used.

```solidity
Path: ./src/rollup/BOLDUpgradeAction.sol

393:            owner: address(this), // upgrade executor is the owner	// @audit-issue

522:        config.owner = address(this);	// @audit-issue
```
[393](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/BOLDUpgradeAction.sol#L393-L393), [522](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/BOLDUpgradeAction.sol#L522-L522), 


```solidity
Path: ./src/rollup/RollupUserLogic.sol

367:        IERC20(stakeToken).safeTransferFrom(msg.sender, address(this), tokenAmount);	// @audit-issue
```
[367](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/RollupUserLogic.sol#L367-L367), 


```solidity
Path: ./src/rollup/RollupCreator.sol

208:        deployParams.config.owner = address(this);	// @audit-issue

304:            (bool sent, ) = msg.sender.call{value: address(this).balance}("");	// @audit-issue
```
[208](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/RollupCreator.sol#L208-L208), [304](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/RollupCreator.sol#L304-L304), 


```solidity
Path: ./src/challengeV2/EdgeChallengeManager.sol

433:            address receiver = edgeAdded.hasRival ? excessStakeReceiver : address(this);	// @audit-issue
```
[433](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/challengeV2/EdgeChallengeManager.sol#L433-L433), 


```solidity
Path: ./src/assertionStakingPool/StakingPoolCreatorUtils.sol

15:        address pool = Create2.computeAddress(0, bytecodeHash, address(this));	// @audit-issue
```
[15](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/assertionStakingPool/StakingPoolCreatorUtils.sol#L15-L15), 


```solidity
Path: ./src/assertionStakingPool/AssertionStakingPool.sol

45:        IRollupUser(rollup).newStakeOnNewAssertion(requiredStake, assertionInputs, assertionHash, address(this));	// @audit-issue
```
[45](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/assertionStakingPool/AssertionStakingPool.sol#L45-L45), 


```solidity
Path: ./src/assertionStakingPool/AbsBoldStakingPool.sol

35:        IERC20(stakeToken).safeTransferFrom(msg.sender, address(this), amount);	// @audit-issue
```
[35](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/assertionStakingPool/AbsBoldStakingPool.sol#L35-L35), 


#### Recommendation

To enhance gas efficiency, cache the contract's address by storing `address(this)` in a state variable at the point of contract deployment or initialization. Use this cached address throughout the contract instead of repeatedly calling `address(this)`. This practice reduces the gas cost associated with multiple computations of the contract's address, leading to more efficient contract execution, especially in scenarios with frequent usage of the contract's address.

### Counting down in for statements is more gas efficient
Looping downwards in Solidity is more gas efficient due to how the EVM compares variables. In a 'for' loop that counts down, the end condition is usually to compare with zero, which is cheaper than comparing with another number. As such, restructure your loops to count downwards where possible.

```solidity
Path: ./src/rollup/BOLDUpgradeAction.sol

350:        for (uint64 i = 0; i < stakerCount; i++) {	// @audit-issue

528:            for (uint256 i = 0; i < validators.length; i++) {	// @audit-issue
```
[350](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/BOLDUpgradeAction.sol#L350-L350), [528](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/BOLDUpgradeAction.sol#L528-L528), 


```solidity
Path: ./src/rollup/RollupCreator.sol

225:        for (uint256 i = 0; i < deployParams.batchPosters.length; i++) {	// @audit-issue

235:            for (uint256 i = 0; i < deployParams.validators.length; i++) {	// @audit-issue
```
[225](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/RollupCreator.sol#L225-L225), [235](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/RollupCreator.sol#L235-L235), 


```solidity
Path: ./src/rollup/RollupAdminLogic.sol

184:        for (uint256 i = 0; i < _validator.length; i++) {	// @audit-issue

230:        for (uint256 i = 0; i < staker.length; i++) {	// @audit-issue
```
[184](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/RollupAdminLogic.sol#L184-L184), [230](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/RollupAdminLogic.sol#L230-L230), 


```solidity
Path: ./src/challengeV2/EdgeChallengeManager.sol

492:        for (uint256 i = 0; i < edgeIds.length; i++) {	// @audit-issue
```
[492](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/challengeV2/EdgeChallengeManager.sol#L492-L492), 


```solidity
Path: ./src/challengeV2/libraries/ArrayUtilsLib.sol

15:        for (uint256 i = 0; i < arr.length; i++) {	// @audit-issue

36:        for (uint256 i = startIndex; i < endIndex; i++) {	// @audit-issue

47:        for (uint256 i = 0; i < arr1.length; i++) {	// @audit-issue

50:        for (uint256 i = 0; i < arr2.length; i++) {	// @audit-issue
```
[15](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/challengeV2/libraries/ArrayUtilsLib.sol#L15-L15), [36](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/challengeV2/libraries/ArrayUtilsLib.sol#L36-L36), [47](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/challengeV2/libraries/ArrayUtilsLib.sol#L47-L47), [50](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/challengeV2/libraries/ArrayUtilsLib.sol#L50-L50), 


```solidity
Path: ./src/challengeV2/libraries/MerkleTreeLib.sol

115:        for (uint256 i = 0; i < me.length; i++) {	// @audit-issue

188:        for (uint256 i = 0; i < me.length; i++) {	// @audit-issue

294:        for (uint256 i = 0; i < me.length; i++) {	// @audit-issue
```
[115](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/challengeV2/libraries/MerkleTreeLib.sol#L115-L115), [188](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/challengeV2/libraries/MerkleTreeLib.sol#L188-L188), [294](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/challengeV2/libraries/MerkleTreeLib.sol#L294-L294), 


#### Recommendation

Where feasible, refactor `for` loops in your Solidity contracts to count downwards. Adjust the loop initialization, condition, and iteration statements to decrement the loop variable and terminate the loop when it reaches zero. This approach can lead to gas savings, making your contract more efficient in terms of execution costs. Ensure that this refactoring aligns with the logic and requirements of your contract, and thoroughly test to confirm that the revised loop behavior matches the intended functionality.

### Use solady library where possible to save gas
The following OpenZeppelin imports have a Solady equivalent, as such they can be used to save GAS as Solady modules have been specifically designed to be as GAS efficient as possible

```solidity
Path: ./src/rollup/BridgeCreator.sol

18:import "@openzeppelin/contracts/access/Ownable.sol";	// @audit-issue
```
[18](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/BridgeCreator.sol#L18-L18), 


```solidity
Path: ./src/rollup/RollupCore.sol

7:import "@openzeppelin/contracts-upgradeable/security/PausableUpgradeable.sol";	// @audit-issue
```
[7](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/RollupCore.sol#L7-L7), 


```solidity
Path: ./src/rollup/RollupUserLogic.sol

7:import "@openzeppelin/contracts/token/ERC20/IERC20.sol";	// @audit-issue
```
[7](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/RollupUserLogic.sol#L7-L7), 


```solidity
Path: ./src/rollup/RollupCreator.sol

12:import "@openzeppelin/contracts/proxy/transparent/TransparentUpgradeableProxy.sol";	// @audit-issue

13:import "@openzeppelin/contracts/access/Ownable.sol";	// @audit-issue

15:import {SafeERC20, IERC20} from "@openzeppelin/contracts/token/ERC20/utils/SafeERC20.sol";	// @audit-issue
```
[12](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/RollupCreator.sol#L12-L12), [13](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/RollupCreator.sol#L13-L13), [15](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/RollupCreator.sol#L15-L15), 


```solidity
Path: ./src/challengeV2/EdgeChallengeManager.sol

15:import "@openzeppelin/contracts/token/ERC20/utils/SafeERC20.sol";	// @audit-issue
```
[15](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/challengeV2/EdgeChallengeManager.sol#L15-L15), 


```solidity
Path: ./src/assertionStakingPool/EdgeStakingPool.sol

11:import "@openzeppelin/contracts/token/ERC20/IERC20.sol";	// @audit-issue

12:import "@openzeppelin/contracts/token/ERC20/utils/SafeERC20.sol";	// @audit-issue
```
[11](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/assertionStakingPool/EdgeStakingPool.sol#L11-L11), [12](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/assertionStakingPool/EdgeStakingPool.sol#L12-L12), 


```solidity
Path: ./src/assertionStakingPool/StakingPoolCreatorUtils.sol

9:import "@openzeppelin/contracts/utils/Address.sol";	// @audit-issue
```
[9](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/assertionStakingPool/StakingPoolCreatorUtils.sol#L9-L9), 


```solidity
Path: ./src/assertionStakingPool/AssertionStakingPool.sol

8:import "@openzeppelin/contracts/token/ERC20/IERC20.sol";	// @audit-issue
```
[8](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/assertionStakingPool/AssertionStakingPool.sol#L8-L8), 


```solidity
Path: ./src/assertionStakingPool/AbsBoldStakingPool.sol

7:import {IERC20} from "@openzeppelin/contracts/token/ERC20/IERC20.sol";	// @audit-issue

8:import {SafeERC20} from "@openzeppelin/contracts/token/ERC20/utils/SafeERC20.sol";	// @audit-issue
```
[7](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/assertionStakingPool/AbsBoldStakingPool.sol#L7-L7), [8](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/assertionStakingPool/AbsBoldStakingPool.sol#L8-L8), 


#### Recommendation

Evaluate and, where appropriate, integrate Solady modules in your Solidity contracts as alternatives to similar OpenZeppelin imports. Focus on areas where gas efficiency can be significantly improved. Ensure that any replacement with Solady's modules does not compromise the security or functionality of your contracts. Conduct thorough testing and code reviews when making such substitutions to confirm compatibility and maintain the integrity of your application. Stay informed about updates and community feedback on both libraries to make informed decisions about their use in your projects.

### Consider using solady's 'FixedPointMathLib'
Using Solady's "FixedPointMathLib" for multiplication or division operations in Solidity can lead to significant gas savings. This library is designed to optimize fixed-point arithmetic operations, which are common in financial calculations involving tokens or currencies. By implementing more efficient algorithms and assembly optimizations, "FixedPointMathLib" minimizes the computational resources required for these operations. For contracts that frequently perform such calculations, integrating this library can reduce transaction costs, thereby enhancing overall performance and cost-effectiveness. However, developers must ensure compatibility with their existing codebase and thoroughly test for accuracy and expected behavior to avoid any unintended consequences.

```solidity
Path: ./src/bridge/SequencerInbox.sol

742:        uint256 blobCost = reader4844.getBlobBaseFee() * GAS_PER_BLOB * dataHashes.length;	// @audit-issue

746:            block.basefee > 0 ? blobCost / block.basefee : 0	// @audit-issue

771:            extraGas += l1Fees / block.basefee;	// @audit-issue

906:        if (keysetBytes.length >= 64 * 1024) revert KeysetTooLarge();	// @audit-issue
```
[742](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/bridge/SequencerInbox.sol#L742-L742), [746](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/bridge/SequencerInbox.sol#L746-L746), [771](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/bridge/SequencerInbox.sol#L771-L771), [906](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/bridge/SequencerInbox.sol#L906-L906), 


```solidity
Path: ./src/bridge/DelayBuffer.sol

46:        buffer += (elapsed * replenishRateInBasis) / BASIS;	// @audit-issue
```
[46](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/bridge/DelayBuffer.sol#L46-L46), 


```solidity
Path: ./src/challengeV2/libraries/EdgeChallengeManagerLib.sol

805:                machineStep += stepSize * store.edges[cursor].startHeight;	// @audit-issue

807:                stepSize *= bigStepHeight;	// @audit-issue
```
[805](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/challengeV2/libraries/EdgeChallengeManagerLib.sol#L805-L805), [807](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/challengeV2/libraries/EdgeChallengeManagerLib.sol#L807-L807), 


#### Recommendation

Consider integrating Solady's 'FixedPointMathLib' into your Solidity contracts for optimized fixed-point arithmetic operations. This library can provide substantial gas savings and enhance the performance of your contract. Before integration, evaluate how 'FixedPointMathLib' aligns with your contract’s requirements. Ensure thorough testing for accuracy and compatibility with your existing contract logic. Carefully document any changes and keep track of how these optimizations affect your contract's operations to maintain transparency and reliability in your application. Adopting 'FixedPointMathLib' should be a considered decision, balancing the benefits of gas efficiency with the need for maintaining code clarity and functionality.

### Reduce Gas Usage by Moving to Solidity 0.8.19 or Later
This issue highlights the opportunity to reduce gas consumption in a smart contract by upgrading the Solidity compiler version to 0.8.19 or a later release. Gas usage is a critical consideration in Ethereum smart contracts, as it directly affects transaction costs and contract execution efficiency. Newer compiler versions often come with optimizations and improvements that can lead to reduced gas costs for certain operations and contract structures.


```solidity
Path: ./src/bridge/SequencerInbox.sol

5:pragma solidity ^0.8.0;	// @audit-issue
```
[5](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/bridge/SequencerInbox.sol#L5-L5), 


```solidity
Path: ./src/bridge/DelayBufferTypes.sol

7:pragma solidity >=0.6.9 <0.9.0;	// @audit-issue
```
[7](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/bridge/DelayBufferTypes.sol#L7-L7), 


```solidity
Path: ./src/bridge/DelayBuffer.sol

5:pragma solidity ^0.8.0;	// @audit-issue
```
[5](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/bridge/DelayBuffer.sol#L5-L5), 


```solidity
Path: ./src/bridge/ISequencerInbox.sol

6:pragma solidity >=0.6.9 <0.9.0;	// @audit-issue
```
[6](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/bridge/ISequencerInbox.sol#L6-L6), 


```solidity
Path: ./src/rollup/IRollupLogic.sol

5:pragma solidity ^0.8.0;	// @audit-issue
```
[5](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/IRollupLogic.sol#L5-L5), 


```solidity
Path: ./src/rollup/RollupLib.sol

5:pragma solidity ^0.8.0;	// @audit-issue
```
[5](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/RollupLib.sol#L5-L5), 


```solidity
Path: ./src/rollup/BOLDUpgradeAction.sol

5:pragma solidity ^0.8.0;	// @audit-issue
```
[5](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/BOLDUpgradeAction.sol#L5-L5), 


```solidity
Path: ./src/rollup/Assertion.sol

5:pragma solidity ^0.8.0;	// @audit-issue
```
[5](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/Assertion.sol#L5-L5), 


```solidity
Path: ./src/rollup/AssertionState.sol

5:pragma solidity ^0.8.0;	// @audit-issue
```
[5](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/AssertionState.sol#L5-L5), 


```solidity
Path: ./src/rollup/BridgeCreator.sol

5:pragma solidity ^0.8.0;	// @audit-issue
```
[5](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/BridgeCreator.sol#L5-L5), 


```solidity
Path: ./src/rollup/RollupCore.sol

5:pragma solidity ^0.8.0;	// @audit-issue
```
[5](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/RollupCore.sol#L5-L5), 


```solidity
Path: ./src/rollup/IRollupCore.sol

5:pragma solidity ^0.8.0;	// @audit-issue
```
[5](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/IRollupCore.sol#L5-L5), 


```solidity
Path: ./src/rollup/RollupUserLogic.sol

5:pragma solidity ^0.8.0;	// @audit-issue
```
[5](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/RollupUserLogic.sol#L5-L5), 


```solidity
Path: ./src/rollup/RollupCreator.sol

5:pragma solidity ^0.8.0;	// @audit-issue
```
[5](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/RollupCreator.sol#L5-L5), 


```solidity
Path: ./src/rollup/RollupAdminLogic.sol

5:pragma solidity ^0.8.0;	// @audit-issue
```
[5](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/RollupAdminLogic.sol#L5-L5), 


```solidity
Path: ./src/rollup/IRollupAdmin.sol

5:pragma solidity ^0.8.0;	// @audit-issue
```
[5](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/IRollupAdmin.sol#L5-L5), 


```solidity
Path: ./src/rollup/Config.sol

5:pragma solidity ^0.8.0;	// @audit-issue
```
[5](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/Config.sol#L5-L5), 


```solidity
Path: ./src/rollup/RollupProxy.sol

5:pragma solidity ^0.8.0;	// @audit-issue
```
[5](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/RollupProxy.sol#L5-L5), 


```solidity
Path: ./src/libraries/Error.sol

5:pragma solidity ^0.8.4;	// @audit-issue
```
[5](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/libraries/Error.sol#L5-L5), 


```solidity
Path: ./src/challengeV2/IAssertionChain.sol

5:pragma solidity ^0.8.17;	// @audit-issue
```
[5](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/challengeV2/IAssertionChain.sol#L5-L5), 


```solidity
Path: ./src/challengeV2/EdgeChallengeManager.sol

5:pragma solidity ^0.8.17;	// @audit-issue
```
[5](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/challengeV2/EdgeChallengeManager.sol#L5-L5), 


```solidity
Path: ./src/challengeV2/libraries/ArrayUtilsLib.sol

5:pragma solidity ^0.8.17;	// @audit-issue
```
[5](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/challengeV2/libraries/ArrayUtilsLib.sol#L5-L5), 


```solidity
Path: ./src/challengeV2/libraries/EdgeChallengeManagerLib.sol

5:pragma solidity ^0.8.17;	// @audit-issue
```
[5](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/challengeV2/libraries/EdgeChallengeManagerLib.sol#L5-L5), 


```solidity
Path: ./src/challengeV2/libraries/MerkleTreeLib.sol

5:pragma solidity ^0.8.17;	// @audit-issue
```
[5](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/challengeV2/libraries/MerkleTreeLib.sol#L5-L5), 


```solidity
Path: ./src/challengeV2/libraries/ChallengeEdgeLib.sol

5:pragma solidity ^0.8.17;	// @audit-issue
```
[5](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/challengeV2/libraries/ChallengeEdgeLib.sol#L5-L5), 


```solidity
Path: ./src/challengeV2/libraries/UintUtilsLib.sol

5:pragma solidity ^0.8.17;	// @audit-issue
```
[5](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/challengeV2/libraries/UintUtilsLib.sol#L5-L5), 


```solidity
Path: ./src/challengeV2/libraries/ChallengeErrors.sol

5:pragma solidity ^0.8.17;	// @audit-issue
```
[5](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/challengeV2/libraries/ChallengeErrors.sol#L5-L5), 


```solidity
Path: ./src/challengeV2/libraries/Enums.sol

5:pragma solidity ^0.8.17;	// @audit-issue
```
[5](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/challengeV2/libraries/Enums.sol#L5-L5), 


```solidity
Path: ./src/assertionStakingPool/AssertionStakingPoolCreator.sol

6:pragma solidity ^0.8.0;	// @audit-issue
```
[6](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/assertionStakingPool/AssertionStakingPoolCreator.sol#L6-L6), 


```solidity
Path: ./src/assertionStakingPool/EdgeStakingPool.sol

5:pragma solidity ^0.8.0;	// @audit-issue
```
[5](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/assertionStakingPool/EdgeStakingPool.sol#L5-L5), 


```solidity
Path: ./src/assertionStakingPool/StakingPoolCreatorUtils.sol

6:pragma solidity ^0.8.0;	// @audit-issue
```
[6](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/assertionStakingPool/StakingPoolCreatorUtils.sol#L6-L6), 


```solidity
Path: ./src/assertionStakingPool/EdgeStakingPoolCreator.sol

6:pragma solidity ^0.8.0;	// @audit-issue
```
[6](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/assertionStakingPool/EdgeStakingPoolCreator.sol#L6-L6), 


```solidity
Path: ./src/assertionStakingPool/AssertionStakingPool.sol

6:pragma solidity ^0.8.0;	// @audit-issue
```
[6](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/assertionStakingPool/AssertionStakingPool.sol#L6-L6), 


```solidity
Path: ./src/assertionStakingPool/AbsBoldStakingPool.sol

5:pragma solidity ^0.8.0;	// @audit-issue
```
[5](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/assertionStakingPool/AbsBoldStakingPool.sol#L5-L5), 


```solidity
Path: ./src/assertionStakingPool/interfaces/IAssertionStakingPool.sol

5:pragma solidity ^0.8.0;	// @audit-issue
```
[5](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/assertionStakingPool/interfaces/IAssertionStakingPool.sol#L5-L5), 


```solidity
Path: ./src/assertionStakingPool/interfaces/IEdgeStakingPool.sol

5:pragma solidity ^0.8.0;	// @audit-issue
```
[5](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/assertionStakingPool/interfaces/IEdgeStakingPool.sol#L5-L5), 


```solidity
Path: ./src/assertionStakingPool/interfaces/IEdgeStakingPoolCreator.sol

5:pragma solidity ^0.8.0;	// @audit-issue
```
[5](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/assertionStakingPool/interfaces/IEdgeStakingPoolCreator.sol#L5-L5), 


```solidity
Path: ./src/assertionStakingPool/interfaces/IAbsBoldStakingPool.sol

5:pragma solidity ^0.8.0;	// @audit-issue
```
[5](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/assertionStakingPool/interfaces/IAbsBoldStakingPool.sol#L5-L5), 


```solidity
Path: ./src/assertionStakingPool/interfaces/IAssertionStakingPoolCreator.sol

5:pragma solidity ^0.8.0;	// @audit-issue
```
[5](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/assertionStakingPool/interfaces/IAssertionStakingPoolCreator.sol#L5-L5), 


#### Recommendation

Consider upgrading to Solidity version 0.8.19 or later to leverage compiler optimizations for reduced gas consumption. Newer versions often include improvements that enhance transaction cost-efficiency and overall contract execution.

### Constant Keccak Variables Are Treated As Expressions, Not Constants
In Solidity, state variables or local variables declared with the `constant` keyword are expected to represent constant values that are determined at compile time. These constants typically do not incur any gas costs when accessed since their values are hard-coded into the contract bytecode.

However, this expected behavior deviates when using the `keccak256()` function. When a variable is initialized with a `keccak256()` hash computation, even if declared as `constant`, it isn't truly treated as a constant in the resulting bytecode. Instead, every time this "constant" is referenced, the EVM recalculates the hash. This behavior contrasts with other true constants, which are embedded directly into the bytecode and accessed without additional computations.


```solidity
Path: ./src/challengeV2/libraries/EdgeChallengeManagerLib.sol

135:    bytes32 public constant UNRIVALED = keccak256(abi.encodePacked("UNRIVALED"));	// @audit-issue
```
[135](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/challengeV2/libraries/EdgeChallengeManagerLib.sol#L135-L135), 


#### Recommendation

Avoid using 'keccak256()' to initialize 'constant' variables in Solidity. Instead, precompute the hash value outside of the contract and assign this precomputed value to the constant. This ensures the variable is a true constant, eliminating redundant hash computations and saving gas.

### Use bitmap to save gas
Bitmaps in Solidity are essentially a way of representing a set of boolean values within an integer type variable such as `uint256`. Each bit in the integer represents a true or false value (1 or 0), thus allowing efficient storage of multiple boolean values.

Bitmaps can save gas in the Ethereum network because they condense a lot of information into a small amount of storage. In Ethereum, storage is one of the most significant costs in terms of gas usage. By reducing the amount of storage space needed, you can potentially save on gas fees.

Here's a quick comparison:

If you were to represent 256 different boolean values in the traditional way, you would have to declare 256 different `bool` variables. Given that each `bool` occupies a storage slot and each storage slot costs 20,000 gas to initialize, you would end up paying a considerable amount of gas.

On the other hand, if you were to use a bitmap, you could store these 256 boolean values within a single `uint256` variable. In other words, you'd only pay for a single storage slot, resulting in significant gas savings.

However, it's important to note that while bitmaps can provide gas efficiencies, they do add complexity to the code, making it harder to read and maintain. Also, using bitmaps is efficient only when dealing with a large number of boolean variables that are frequently changed or accessed together. 

In contrast, the straightforward counterpart to bitmaps would be using arrays or mappings to store boolean values, with each `bool` value occupying its own storage slot. This approach is simpler and more readable but could potentially be more expensive in terms of gas usage.

```solidity
Path: ./src/bridge/SequencerInbox.sol

190:                actualIsUsingFeeToken = true;	// @audit-issue

927:        dasKeySetInfo[ksHash].isValidKeyset = false;	// @audit-issue
```
[190](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/bridge/SequencerInbox.sol#L190-L190), [927](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/bridge/SequencerInbox.sol#L927-L927), 


```solidity
Path: ./src/rollup/BOLDUpgradeAction.sol

530:                _vals[i] = true;	// @audit-issue
```
[530](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/BOLDUpgradeAction.sol#L530-L530), 


```solidity
Path: ./src/rollup/RollupCore.sol

431:                overflowAssertion = true;	// @audit-issue
```
[431](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/RollupCore.sol#L431-L431), 


```solidity
Path: ./src/rollup/RollupUserLogic.sol

65:        validatorWhitelistDisabled = true;	// @audit-issue

74:        validatorWhitelistDisabled = true;	// @audit-issue
```
[65](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/RollupUserLogic.sol#L65-L65), [74](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/RollupUserLogic.sol#L74-L74), 


```solidity
Path: ./src/rollup/RollupCreator.sol

236:                _vals[i] = true;	// @audit-issue
```
[236](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/RollupCreator.sol#L236-L236), 


```solidity
Path: ./src/challengeV2/libraries/EdgeChallengeManagerLib.sol

435:            store.hasMadeLayerZeroRival[msg.sender][mutualId] = true;	// @audit-issue
```
[435](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/challengeV2/libraries/EdgeChallengeManagerLib.sol#L435-L435), 


```solidity
Path: ./src/challengeV2/libraries/ChallengeEdgeLib.sol

275:        edge.refunded = true;	// @audit-issue
```
[275](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/challengeV2/libraries/ChallengeEdgeLib.sol#L275-L275), 


#### Recommendation

Consider using bitmaps in your Solidity contracts when you need to store and manipulate a large set of boolean values. This approach is particularly advantageous in terms of gas efficiency for scenarios involving frequent changes or accesses to these values. However, balance this efficiency with code readability and maintainability. Ensure that the use of bitmaps is well-documented, and consider the complexity it introduces into the code. Employ bitmaps judiciously, especially when their use results in significant gas savings, and the logic they represent is a core aspect of the contract's functionality.

### Using `bool`s for storage incurs overhead
[Booleans are more expensive than uint256](https://github.com/OpenZeppelin/openzeppelin-contracts/blob/58f635312aa21f947cae5f8578638a85aa2519f5/contracts/security/ReentrancyGuard.sol#L23-L27) or any type that takes up a full word because each write operation emits an extra SLOAD to first read the slot's contents, replace the bits taken up by the boolean, and then write back. This is the compiler's defense against contract upgrades and pointer aliasing, and it cannot be disabled.
Use `uint256(0)` and `uint256(1)` for true/false to avoid a Gwarmaccess (**[100 gas](https://gist.github.com/IllIllI000/1b70014db712f8572a72378321250058)**) for the extra SLOAD.


```solidity
Path: ./src/bridge/SequencerInbox.sol

95:    mapping(address => bool) public isBatchPoster;	// @audit-issue

115:    mapping(address => bool) public isSequencer;	// @audit-issue

131:    bool internal immutable hostChainIsArbitrum = ArbitrumChecker.runningOnArbitrum();	// @audit-issue

133:    bool public immutable isUsingFeeToken;	// @audit-issue

135:    bool public immutable isDelayBufferable;	// @audit-issue

187:        bool actualIsUsingFeeToken = false;	// @audit-issue
```
[95](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/bridge/SequencerInbox.sol#L95-L95), [115](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/bridge/SequencerInbox.sol#L115-L115), [131](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/bridge/SequencerInbox.sol#L131-L131), [133](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/bridge/SequencerInbox.sol#L133-L133), [135](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/bridge/SequencerInbox.sol#L135-L135), [187](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/bridge/SequencerInbox.sol#L187-L187), 


```solidity
Path: ./src/rollup/BOLDUpgradeAction.sol

46:    bool isStaked; // 2. must be staked	// @audit-issue

204:    bool public immutable DISABLE_VALIDATOR_WHITELIST;	// @audit-issue

207:    bool public immutable IS_DELAY_BUFFERABLE;	// @audit-issue
```
[46](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/BOLDUpgradeAction.sol#L46-L46), [204](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/BOLDUpgradeAction.sol#L204-L204), [207](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/BOLDUpgradeAction.sol#L207-L207), 


```solidity
Path: ./src/rollup/Assertion.sol

26:    bool isFirstChild;	// @audit-issue
```
[26](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/Assertion.sol#L26-L26), 


```solidity
Path: ./src/rollup/RollupCore.sol

96:    mapping(address => bool) public isValidator;	// @audit-issue

108:    bool public validatorWhitelistDisabled;	// @audit-issue

112:    bool internal immutable _hostChainIsArbitrum = ArbitrumChecker.runningOnArbitrum();	// @audit-issue
```
[96](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/RollupCore.sol#L96-L96), [108](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/RollupCore.sol#L108-L108), [112](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/RollupCore.sol#L112-L112), 


```solidity
Path: ./src/challengeV2/EdgeChallengeManager.sol

226:        bool hasRival,	// @audit-issue

227:        bool isLayerZero	// @audit-issue

236:        bytes32 indexed edgeId, bytes32 indexed lowerChildId, bytes32 indexed upperChildId, bool lowerChildAlreadyExists	// @audit-issue
```
[226](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/challengeV2/EdgeChallengeManager.sol#L226-L226), [227](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/challengeV2/EdgeChallengeManager.sol#L227-L227), [236](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/challengeV2/EdgeChallengeManager.sol#L236-L236), 


```solidity
Path: ./src/challengeV2/libraries/EdgeChallengeManagerLib.sol

86:    mapping(address => mapping(bytes32 => bool)) hasMadeLayerZeroRival;	// @audit-issue

105:    bool hasRival;	// @audit-issue

106:    bool isLayerZero;	// @audit-issue

117:    bool isPending;	// @audit-issue

119:    bool hasSibling;	// @audit-issue
```
[86](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/challengeV2/libraries/EdgeChallengeManagerLib.sol#L86-L86), [105](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/challengeV2/libraries/EdgeChallengeManagerLib.sol#L105-L105), [106](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/challengeV2/libraries/EdgeChallengeManagerLib.sol#L106-L106), [117](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/challengeV2/libraries/EdgeChallengeManagerLib.sol#L117-L117), [119](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/challengeV2/libraries/EdgeChallengeManagerLib.sol#L119-L119), 


```solidity
Path: ./src/challengeV2/libraries/ChallengeEdgeLib.sol

62:    bool refunded;	// @audit-issue
```
[62](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/challengeV2/libraries/ChallengeEdgeLib.sol#L62-L62), 


#### Recommendation

To minimize gas overhead in your Solidity contracts, consider using `uint256(1)` and `uint256(2)` to represent `true` and `false`, respectively, instead of `bool` types for storage. This approach avoids additional `SLOAD` and `SSTORE` operations, resulting in more gas-efficient code.

### Usage of `uints`/`ints` smaller than 32 bytes (256 bits) incurs overhead
When using elements that are smaller than 32 bytes, your contract’s gas usage may be higher. This is because the EVM operates on 32 bytes at a time. Therefore, if the element is smaller than that, the EVM must use more operations in order to reduce the size of the element from 32 bytes to the desired size.
https://docs.soliditylang.org/en/v0.8.11/internals/layout_in_storage.html Each operation involving a `uint8` costs an extra [22-28](https://gist.github.com/IllIllI000/9388d20c70f9a4632eb3ca7836f54977) gas (depending on whether the other operand is also a variable of type `uint8`) as compared to ones involving `uint256`, due to the compiler having to clear the higher bits of the memory word before operating on the `uint8`, as well as the associated stack operations of doing so. Use a larger size then downcast where needed


```solidity
Path: ./src/bridge/SequencerInbox.sol

119:    uint64 internal delayBlocks;	// @audit-issue

120:    uint64 internal futureBlocks;	// @audit-issue

121:    uint64 internal delaySeconds;	// @audit-issue

122:    uint64 internal futureSeconds;	// @audit-issue

219:            uint64 delayBlocks_,	// @audit-issue

255:            uint64 delayBlocks_,	// @audit-issue

273:            uint64,	// @audit-issue

274:            uint64,	// @audit-issue

275:            uint64,	// @audit-issue

276:            uint64	// @audit-issue

289:        uint8 kind,	// @audit-issue

833:    function forceInclusionDeadline(uint64 blockNumber) external view returns (uint64) {	// @audit-issue

834:        uint64 _delayBlocks = delayBlocks;	// @audit-issue

836:            uint64 _buffer = buffer.calcPendingBuffer(blockNumber);	// @audit-issue

843:    function delayBufferableBlocks(uint64 _buffer) internal view returns (uint64) {	// @audit-issue
```
[119](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/bridge/SequencerInbox.sol#L119-L119), [120](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/bridge/SequencerInbox.sol#L120-L120), [121](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/bridge/SequencerInbox.sol#L121-L121), [122](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/bridge/SequencerInbox.sol#L122-L122), [219](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/bridge/SequencerInbox.sol#L219-L219), [255](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/bridge/SequencerInbox.sol#L255-L255), [273](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/bridge/SequencerInbox.sol#L273-L273), [274](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/bridge/SequencerInbox.sol#L274-L274), [275](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/bridge/SequencerInbox.sol#L275-L275), [276](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/bridge/SequencerInbox.sol#L276-L276), [289](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/bridge/SequencerInbox.sol#L289-L289), [833](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/bridge/SequencerInbox.sol#L833-L833), [834](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/bridge/SequencerInbox.sol#L834-L834), [836](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/bridge/SequencerInbox.sol#L836-L836), [843](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/bridge/SequencerInbox.sol#L843-L843), 


```solidity
Path: ./src/bridge/DelayBuffer.sol

68:    function update(BufferData storage self, uint64 blockNumber) internal {	// @audit-issue

82:    function calcPendingBuffer(BufferData storage self, uint64 blockNumber)	// @audit-issue

85:        returns (uint64)	// @audit-issue
```
[68](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/bridge/DelayBuffer.sol#L68-L68), [82](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/bridge/DelayBuffer.sol#L82-L82), [85](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/bridge/DelayBuffer.sol#L85-L85), 


```solidity
Path: ./src/bridge/ISequencerInbox.sol

124:    function dasKeySetInfo(bytes32) external view returns (bool, uint64);	// @audit-issue

141:        uint8 kind,	// @audit-issue

163:    function forceInclusionDeadline(uint64 blockNumber)	// @audit-issue

166:        returns (uint64 blockNumberDeadline);	// @audit-issue
```
[124](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/bridge/ISequencerInbox.sol#L124-L124), [141](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/bridge/ISequencerInbox.sol#L141-L141), [163](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/bridge/ISequencerInbox.sol#L163-L163), [166](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/bridge/ISequencerInbox.sol#L166-L166), 


```solidity
Path: ./src/rollup/RollupLib.sol

58:        uint64 confirmPeriodBlocks,	// @audit-issue

59:        uint64 nextInboxPosition	// @audit-issue
```
[58](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/RollupLib.sol#L58-L58), [59](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/RollupLib.sol#L59-L59), 


```solidity
Path: ./src/rollup/BOLDUpgradeAction.sol

188:    uint8 public immutable NUM_BIGSTEP_LEVEL;	// @audit-issue

198:    uint64 public immutable CONFIRM_PERIOD_BLOCKS;	// @audit-issue

199:    uint64 public immutable CHALLENGE_PERIOD_BLOCKS;	// @audit-issue

205:    uint64 public immutable CHALLENGE_GRACE_PERIOD_BLOCKS;	// @audit-issue

209:    uint64 public immutable MAX;	// @audit-issue

210:    uint64 public immutable THRESHOLD;	// @audit-issue

211:    uint64 public immutable REPLENISH_RATE_IN_BASIS;	// @audit-issue

68:    function latestConfirmed() external view returns (uint64);	// @audit-issue

69:    function getNode(uint64 nodeNum) external view returns (Node memory);	// @audit-issue

70:    function getStakerAddress(uint64 stakerNum) external view returns (address);	// @audit-issue

71:    function stakerCount() external view returns (uint64);	// @audit-issue

134:    function latestConfirmed() external view returns (uint64) {	// @audit-issue

138:    function getNode(uint64 nodeNum) external view returns (Node memory) {	// @audit-issue

142:    function getStakerAddress(uint64 stakerNum) external view returns (address) {	// @audit-issue

146:    function stakerCount() external view returns (uint64) {	// @audit-issue

344:        uint64 stakerCount = ROLLUP_READER.stakerCount();	// @audit-issue

350:        for (uint64 i = 0; i < stakerCount; i++) {	// @audit-issue

21:    uint64 prevNum;	// @audit-issue

23:    uint64 deadlineBlock;	// @audit-issue

25:    uint64 noChildConfirmedBeforeBlock;	// @audit-issue

27:    uint64 stakerCount;	// @audit-issue

29:    uint64 childStakerCount;	// @audit-issue

31:    uint64 firstChildBlock;	// @audit-issue

33:    uint64 latestChildNumber;	// @audit-issue

35:    uint64 createdAtBlock;	// @audit-issue

42:    uint64 index;	// @audit-issue

43:    uint64 latestStakedNode;	// @audit-issue

45:    uint64 currentChallenge; // 1. cannot have current challenge	// @audit-issue
```
[188](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/BOLDUpgradeAction.sol#L188-L188), [198](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/BOLDUpgradeAction.sol#L198-L198), [199](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/BOLDUpgradeAction.sol#L199-L199), [205](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/BOLDUpgradeAction.sol#L205-L205), [209](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/BOLDUpgradeAction.sol#L209-L209), [210](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/BOLDUpgradeAction.sol#L210-L210), [211](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/BOLDUpgradeAction.sol#L211-L211), [68](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/BOLDUpgradeAction.sol#L68-L68), [69](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/BOLDUpgradeAction.sol#L69-L69), [70](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/BOLDUpgradeAction.sol#L70-L70), [71](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/BOLDUpgradeAction.sol#L71-L71), [134](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/BOLDUpgradeAction.sol#L134-L134), [138](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/BOLDUpgradeAction.sol#L138-L138), [142](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/BOLDUpgradeAction.sol#L142-L142), [146](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/BOLDUpgradeAction.sol#L146-L146), [344](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/BOLDUpgradeAction.sol#L344-L344), [350](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/BOLDUpgradeAction.sol#L350-L350), [21](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/BOLDUpgradeAction.sol#L21-L21), [23](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/BOLDUpgradeAction.sol#L23-L23), [25](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/BOLDUpgradeAction.sol#L25-L25), [27](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/BOLDUpgradeAction.sol#L27-L27), [29](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/BOLDUpgradeAction.sol#L29-L29), [31](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/BOLDUpgradeAction.sol#L31-L31), [33](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/BOLDUpgradeAction.sol#L33-L33), [35](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/BOLDUpgradeAction.sol#L35-L35), [42](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/BOLDUpgradeAction.sol#L42-L42), [43](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/BOLDUpgradeAction.sol#L43-L43), [45](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/BOLDUpgradeAction.sol#L45-L45), 


```solidity
Path: ./src/rollup/RollupCore.sol

31:    uint64 public confirmPeriodBlocks;	// @audit-issue

82:    uint64 public challengeGracePeriodBlocks;	// @audit-issue

162:    function getStakerAddress(uint64 stakerNum) external view override returns (address) {	// @audit-issue

217:    function stakerCount() public view override returns (uint64) {	// @audit-issue

275:        uint64 stakerIndex = uint64(_stakerList.length);	// @audit-issue

358:        uint64 stakerIndex = staker.index;	// @audit-issue

532:    function getFirstChildCreationBlock(bytes32 assertionHash) external view returns (uint64) {	// @audit-issue

536:    function getSecondChildCreationBlock(bytes32 assertionHash) external view returns (uint64) {	// @audit-issue
```
[31](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/RollupCore.sol#L31-L31), [82](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/RollupCore.sol#L82-L82), [162](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/RollupCore.sol#L162-L162), [217](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/RollupCore.sol#L217-L217), [275](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/RollupCore.sol#L275-L275), [358](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/RollupCore.sol#L358-L358), [532](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/RollupCore.sol#L532-L532), [536](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/RollupCore.sol#L536-L536), 


```solidity
Path: ./src/rollup/IRollupCore.sol

48:    function confirmPeriodBlocks() external view returns (uint64);	// @audit-issue

93:    function getStakerAddress(uint64 stakerNum) external view returns (address);	// @audit-issue

133:    function stakerCount() external view returns (uint64);	// @audit-issue
```
[48](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/IRollupCore.sol#L48-L48), [93](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/IRollupCore.sol#L93-L93), [133](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/IRollupCore.sol#L133-L133), 


```solidity
Path: ./src/rollup/RollupAdminLogic.sol

213:    function setConfirmPeriodBlocks(uint64 newConfirmPeriod) external override {	// @audit-issue
```
[213](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/RollupAdminLogic.sol#L213-L213), 


```solidity
Path: ./src/rollup/IRollupAdmin.sol

72:    function setConfirmPeriodBlocks(uint64 newConfirmPeriod) external;	// @audit-issue
```
[72](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/IRollupAdmin.sol#L72-L72), 


```solidity
Path: ./src/challengeV2/IAssertionChain.sol

22:    function getFirstChildCreationBlock(bytes32 assertionHash) external view returns (uint64);	// @audit-issue

23:    function getSecondChildCreationBlock(bytes32 assertionHash) external view returns (uint64);	// @audit-issue
```
[22](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/challengeV2/IAssertionChain.sol#L22-L22), [23](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/challengeV2/IAssertionChain.sol#L23-L23), 


```solidity
Path: ./src/challengeV2/EdgeChallengeManager.sol

282:    uint64 public challengePeriodBlocks;	// @audit-issue

298:    uint8 public NUM_BIGSTEP_LEVEL;	// @audit-issue

36:        uint64 _challengePeriodBlocks,	// @audit-issue

43:        uint8 _numBigStepLevel,	// @audit-issue

47:    function challengePeriodBlocks() external view returns (uint64);	// @audit-issue

133:        uint8 level,	// @audit-issue

149:        uint8 level,	// @audit-issue

307:        uint64 _challengePeriodBlocks,	// @audit-issue

314:        uint8 _numBigStepLevel,	// @audit-issue

517:        uint64 assertionBlocks = 0;	// @audit-issue

605:        uint8 level,	// @audit-issue

617:        uint8 level,	// @audit-issue
```
[282](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/challengeV2/EdgeChallengeManager.sol#L282-L282), [298](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/challengeV2/EdgeChallengeManager.sol#L298-L298), [36](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/challengeV2/EdgeChallengeManager.sol#L36-L36), [43](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/challengeV2/EdgeChallengeManager.sol#L43-L43), [47](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/challengeV2/EdgeChallengeManager.sol#L47-L47), [133](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/challengeV2/EdgeChallengeManager.sol#L133-L133), [149](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/challengeV2/EdgeChallengeManager.sol#L149-L149), [307](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/challengeV2/EdgeChallengeManager.sol#L307-L307), [314](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/challengeV2/EdgeChallengeManager.sol#L314-L314), [517](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/challengeV2/EdgeChallengeManager.sol#L517-L517), [605](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/challengeV2/EdgeChallengeManager.sol#L605-L605), [617](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/challengeV2/EdgeChallengeManager.sol#L617-L617), 


```solidity
Path: ./src/challengeV2/libraries/EdgeChallengeManagerLib.sol

218:        uint8 numBigStepLevel	// @audit-issue

417:        uint8 numBigStepLevel,	// @audit-issue

524:        uint8 numBigStepLevel	// @audit-issue

674:    function nextEdgeLevel(uint8 level, uint8 numBigStepLevel) internal pure returns (uint8) {	// @audit-issue

675:        uint8 nextLevel = level + 1;	// @audit-issue

689:    function checkClaimIdLink(EdgeStore storage store, bytes32 edgeId, bytes32 claimingEdgeId, uint8 numBigStepLevel)	// @audit-issue

726:        uint64 claimedAssertionUnrivaledBlocks,	// @audit-issue

727:        uint64 confirmationThresholdBlock	// @audit-issue

774:        uint8 numBigStepLevel,	// @audit-issue

35:    uint8 level;	// @audit-issue

104:    uint8 level;	// @audit-issue
```
[218](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/challengeV2/libraries/EdgeChallengeManagerLib.sol#L218-L218), [417](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/challengeV2/libraries/EdgeChallengeManagerLib.sol#L417-L417), [524](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/challengeV2/libraries/EdgeChallengeManagerLib.sol#L524-L524), [674](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/challengeV2/libraries/EdgeChallengeManagerLib.sol#L674-L674), [675](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/challengeV2/libraries/EdgeChallengeManagerLib.sol#L675-L675), [689](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/challengeV2/libraries/EdgeChallengeManagerLib.sol#L689-L689), [726](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/challengeV2/libraries/EdgeChallengeManagerLib.sol#L726-L726), [727](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/challengeV2/libraries/EdgeChallengeManagerLib.sol#L727-L727), [774](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/challengeV2/libraries/EdgeChallengeManagerLib.sol#L774-L774), [35](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/challengeV2/libraries/EdgeChallengeManagerLib.sol#L35-L35), [104](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/challengeV2/libraries/EdgeChallengeManagerLib.sol#L104-L104), 


```solidity
Path: ./src/challengeV2/libraries/ChallengeEdgeLib.sol

101:        uint8 level	// @audit-issue

139:        uint8 level	// @audit-issue

167:        uint8 level,	// @audit-issue

190:        uint8 level,	// @audit-issue

279:    function levelToType(uint8 level, uint8 numBigStepLevels) internal pure returns (EdgeType eType) {	// @audit-issue

48:    uint64 createdAtBlock;	// @audit-issue

51:    uint64 confirmedAtBlock;	// @audit-issue

59:    uint8 level;	// @audit-issue

64:    uint64 totalTimeUnrivaledCache;	// @audit-issue
```
[101](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/challengeV2/libraries/ChallengeEdgeLib.sol#L101-L101), [139](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/challengeV2/libraries/ChallengeEdgeLib.sol#L139-L139), [167](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/challengeV2/libraries/ChallengeEdgeLib.sol#L167-L167), [190](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/challengeV2/libraries/ChallengeEdgeLib.sol#L190-L190), [279](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/challengeV2/libraries/ChallengeEdgeLib.sol#L279-L279), [48](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/challengeV2/libraries/ChallengeEdgeLib.sol#L48-L48), [51](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/challengeV2/libraries/ChallengeEdgeLib.sol#L51-L51), [59](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/challengeV2/libraries/ChallengeEdgeLib.sol#L59-L59), [64](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/challengeV2/libraries/ChallengeEdgeLib.sol#L64-L64), 


```solidity
Path: ./src/bridge/DelayBufferTypes.sol

14:    uint64 threshold;	// @audit-issue

15:    uint64 max;	// @audit-issue

16:    uint64 replenishRateInBasis;	// @audit-issue

27:    uint64 bufferBlocks;	// @audit-issue

28:    uint64 max;	// @audit-issue

29:    uint64 threshold;	// @audit-issue

30:    uint64 prevBlockNumber;	// @audit-issue

31:    uint64 replenishRateInBasis;	// @audit-issue

32:    uint64 prevSequencedBlockNumber;	// @audit-issue
```
[14](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/bridge/DelayBufferTypes.sol#L14-L14), [15](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/bridge/DelayBufferTypes.sol#L15-L15), [16](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/bridge/DelayBufferTypes.sol#L16-L16), [27](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/bridge/DelayBufferTypes.sol#L27-L27), [28](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/bridge/DelayBufferTypes.sol#L28-L28), [29](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/bridge/DelayBufferTypes.sol#L29-L29), [30](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/bridge/DelayBufferTypes.sol#L30-L30), [31](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/bridge/DelayBufferTypes.sol#L31-L31), [32](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/bridge/DelayBufferTypes.sol#L32-L32), 


```solidity
Path: ./src/rollup/Assertion.sol

20:    uint64 firstChildBlock;	// @audit-issue

22:    uint64 secondChildBlock;	// @audit-issue

24:    uint64 createdAtBlock;	// @audit-issue

59:    uint64 confirmPeriodBlocks;	// @audit-issue

60:    uint64 nextInboxPosition;	// @audit-issue
```
[20](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/Assertion.sol#L20-L20), [22](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/Assertion.sol#L22-L22), [24](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/Assertion.sol#L24-L24), [59](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/Assertion.sol#L59-L59), [60](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/Assertion.sol#L60-L60), 


```solidity
Path: ./src/rollup/Config.sol

18:    uint64 confirmPeriodBlocks;	// @audit-issue

36:    uint8 numBigStepLevel;	// @audit-issue

37:    uint64 challengeGracePeriodBlocks;	// @audit-issue
```
[18](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/Config.sol#L18-L18), [36](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/Config.sol#L36-L36), [37](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/Config.sol#L37-L37), 


#### Recommendation

Minimize gas overhead by using 'uint256' or 'int256' instead of smaller integer types in Solidity contracts. The EVM operates more efficiently with 32-byte sizes. Downcast to smaller types only when necessary, as operations with smaller types like 'uint8' incur extra gas due to additional EVM operations for size adjustment.

### Use more recent OpenZeppelin version for gas boost
OpenZeppelin version 4.9.0+ provides many small gas optimizations, see [here](https://github.com/OpenZeppelin/openzeppelin-contracts/releases/tag/v4.9.0) for more info. Your project is using version: 4.7.3
```solidity
/// @audit Global finding.
```
[1](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/bridge/SequencerInbox.sol#L1), 


#### Recommendation

Consider using OpenZeppelin version 4.9.0+.

### Refactor modifiers to call a local function
Modifiers code is copied in all instances where it's used, increasing bytecode size. If deployment gas costs are a concern for this contract, refactoring modifiers into functions can reduce bytecode size significantly at the cost of one JUMP.

```solidity
Path: ./src/bridge/SequencerInbox.sol

103:    modifier onlyRollupOwner() {	// @audit-issue

108:    modifier onlyRollupOwnerOrBatchPosterManager() {	// @audit-issue
```
[103](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/bridge/SequencerInbox.sol#L103-L103), [108](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/bridge/SequencerInbox.sol#L108-L108), 


```solidity
Path: ./src/rollup/RollupUserLogic.sol

20:    modifier onlyValidator() {	// @audit-issue
```
[20](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/RollupUserLogic.sol#L20-L20), 


#### Recommendation

Evaluate your contract's use of modifiers, particularly those applied across multiple functions, to identify candidates for refactoring into functions. Convert these modifiers into external or public functions that perform the same checks or actions. Then, replace the modifier usage in function declarations with calls to these functions at the start of your functions

### Avoid Unnecessary Public Variables
Public state variables in Solidity automatically generate getter functions, increasing contract size and potentially leading to higher deployment and interaction costs. To optimize gas usage and contract efficiency, minimize the use of public variables unless external access is necessary. Instead, use internal or private visibility combined with explicit getter functions when required. This practice not only reduces contract size but also provides better control over data access and manipulation, enhancing security and readability. Prioritize lean, efficient contracts to ensure cost-effectiveness and better performance on the blockchain.

```solidity
Path: ./src/bridge/SequencerInbox.sol

65:    uint256 public totalDelayedMessagesRead;	// @audit-issue

67:    IBridge public bridge;	// @audit-issue

70:    uint256 public constant HEADER_LENGTH = 40;	// @audit-issue

73:    bytes1 public constant DATA_AUTHENTICATED_FLAG = 0x40;	// @audit-issue

76:    bytes1 public constant DATA_BLOB_HEADER_FLAG = DATA_AUTHENTICATED_FLAG | 0x10;	// @audit-issue

79:    bytes1 public constant DAS_MESSAGE_HEADER_FLAG = 0x80;	// @audit-issue

82:    bytes1 public constant TREE_DAS_MESSAGE_HEADER_FLAG = 0x08;	// @audit-issue

85:    bytes1 public constant BROTLI_MESSAGE_HEADER_FLAG = 0x00;	// @audit-issue

88:    bytes1 public constant ZERO_HEAVY_MESSAGE_HEADER_FLAG = 0x20;	// @audit-issue

93:    IOwnable public rollup;	// @audit-issue

95:    mapping(address => bool) public isBatchPoster;	// @audit-issue

101:    mapping(bytes32 => DasKeySetInfo) public dasKeySetInfo;	// @audit-issue

115:    mapping(address => bool) public isSequencer;	// @audit-issue

116:    IReader4844 public immutable reader4844;	// @audit-issue

125:    address public batchPosterManager;	// @audit-issue

128:    uint256 public immutable maxDataSize;	// @audit-issue

133:    bool public immutable isUsingFeeToken;	// @audit-issue

135:    bool public immutable isDelayBufferable;	// @audit-issue

138:    BufferData public buffer;	// @audit-issue
```
[65](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/bridge/SequencerInbox.sol#L65-L65), [67](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/bridge/SequencerInbox.sol#L67-L67), [70](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/bridge/SequencerInbox.sol#L70-L70), [73](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/bridge/SequencerInbox.sol#L73-L73), [76](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/bridge/SequencerInbox.sol#L76-L76), [79](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/bridge/SequencerInbox.sol#L79-L79), [82](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/bridge/SequencerInbox.sol#L82-L82), [85](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/bridge/SequencerInbox.sol#L85-L85), [88](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/bridge/SequencerInbox.sol#L88-L88), [93](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/bridge/SequencerInbox.sol#L93-L93), [95](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/bridge/SequencerInbox.sol#L95-L95), [101](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/bridge/SequencerInbox.sol#L101-L101), [115](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/bridge/SequencerInbox.sol#L115-L115), [116](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/bridge/SequencerInbox.sol#L116-L116), [125](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/bridge/SequencerInbox.sol#L125-L125), [128](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/bridge/SequencerInbox.sol#L128-L128), [133](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/bridge/SequencerInbox.sol#L133-L133), [135](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/bridge/SequencerInbox.sol#L135-L135), [138](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/bridge/SequencerInbox.sol#L138-L138), 


```solidity
Path: ./src/bridge/DelayBuffer.sol

17:    uint256 public constant BASIS = 10000;	// @audit-issue
```
[17](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/bridge/DelayBuffer.sol#L17-L17), 


```solidity
Path: ./src/rollup/BOLDUpgradeAction.sol

124:    IOldRollup public immutable rollup;	// @audit-issue

185:    uint256 public immutable BLOCK_LEAF_SIZE;	// @audit-issue

186:    uint256 public immutable BIGSTEP_LEAF_SIZE;	// @audit-issue

187:    uint256 public immutable SMALLSTEP_LEAF_SIZE;	// @audit-issue

188:    uint8 public immutable NUM_BIGSTEP_LEVEL;	// @audit-issue

190:    address public immutable L1_TIMELOCK;	// @audit-issue

191:    IOldRollup public immutable OLD_ROLLUP;	// @audit-issue

192:    address public immutable BRIDGE;	// @audit-issue

193:    address public immutable SEQ_INBOX;	// @audit-issue

194:    address public immutable REI;	// @audit-issue

195:    address public immutable OUTBOX;	// @audit-issue

196:    address public immutable INBOX;	// @audit-issue

198:    uint64 public immutable CONFIRM_PERIOD_BLOCKS;	// @audit-issue

199:    uint64 public immutable CHALLENGE_PERIOD_BLOCKS;	// @audit-issue

200:    address public immutable STAKE_TOKEN;	// @audit-issue

201:    uint256 public immutable STAKE_AMOUNT;	// @audit-issue

202:    uint256 public immutable CHAIN_ID;	// @audit-issue

203:    address public immutable ANY_TRUST_FAST_CONFIRMER;	// @audit-issue

204:    bool public immutable DISABLE_VALIDATOR_WHITELIST;	// @audit-issue

205:    uint64 public immutable CHALLENGE_GRACE_PERIOD_BLOCKS;	// @audit-issue

206:    address public immutable MINI_STAKE_AMOUNTS_STORAGE;	// @audit-issue

207:    bool public immutable IS_DELAY_BUFFERABLE;	// @audit-issue

209:    uint64 public immutable MAX;	// @audit-issue

210:    uint64 public immutable THRESHOLD;	// @audit-issue

211:    uint64 public immutable REPLENISH_RATE_IN_BASIS;	// @audit-issue

213:    IOneStepProofEntry public immutable OSP;	// @audit-issue

215:    ProxyAdmin public immutable PROXY_ADMIN_OUTBOX;	// @audit-issue

216:    ProxyAdmin public immutable PROXY_ADMIN_BRIDGE;	// @audit-issue

217:    ProxyAdmin public immutable PROXY_ADMIN_REI;	// @audit-issue

218:    ProxyAdmin public immutable PROXY_ADMIN_SEQUENCER_INBOX;	// @audit-issue

219:    ProxyAdmin public immutable PROXY_ADMIN_INBOX;	// @audit-issue

220:    StateHashPreImageLookup public immutable PREIMAGE_LOOKUP;	// @audit-issue

221:    RollupReader public immutable ROLLUP_READER;	// @audit-issue

224:    address public immutable IMPL_BRIDGE;	// @audit-issue

225:    address public immutable IMPL_SEQUENCER_INBOX;	// @audit-issue

226:    address public immutable IMPL_INBOX;	// @audit-issue

227:    address public immutable IMPL_REI;	// @audit-issue

228:    address public immutable IMPL_OUTBOX;	// @audit-issue

230:    address public immutable IMPL_PATCHED_OLD_ROLLUP_USER;	// @audit-issue

231:    address public immutable IMPL_NEW_ROLLUP_USER;	// @audit-issue

232:    address public immutable IMPL_NEW_ROLLUP_ADMIN;	// @audit-issue

233:    address public immutable IMPL_CHALLENGE_MANAGER;	// @audit-issue
```
[124](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/BOLDUpgradeAction.sol#L124-L124), [185](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/BOLDUpgradeAction.sol#L185-L185), [186](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/BOLDUpgradeAction.sol#L186-L186), [187](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/BOLDUpgradeAction.sol#L187-L187), [188](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/BOLDUpgradeAction.sol#L188-L188), [190](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/BOLDUpgradeAction.sol#L190-L190), [191](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/BOLDUpgradeAction.sol#L191-L191), [192](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/BOLDUpgradeAction.sol#L192-L192), [193](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/BOLDUpgradeAction.sol#L193-L193), [194](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/BOLDUpgradeAction.sol#L194-L194), [195](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/BOLDUpgradeAction.sol#L195-L195), [196](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/BOLDUpgradeAction.sol#L196-L196), [198](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/BOLDUpgradeAction.sol#L198-L198), [199](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/BOLDUpgradeAction.sol#L199-L199), [200](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/BOLDUpgradeAction.sol#L200-L200), [201](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/BOLDUpgradeAction.sol#L201-L201), [202](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/BOLDUpgradeAction.sol#L202-L202), [203](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/BOLDUpgradeAction.sol#L203-L203), [204](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/BOLDUpgradeAction.sol#L204-L204), [205](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/BOLDUpgradeAction.sol#L205-L205), [206](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/BOLDUpgradeAction.sol#L206-L206), [207](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/BOLDUpgradeAction.sol#L207-L207), [209](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/BOLDUpgradeAction.sol#L209-L209), [210](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/BOLDUpgradeAction.sol#L210-L210), [211](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/BOLDUpgradeAction.sol#L211-L211), [213](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/BOLDUpgradeAction.sol#L213-L213), [215](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/BOLDUpgradeAction.sol#L215-L215), [216](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/BOLDUpgradeAction.sol#L216-L216), [217](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/BOLDUpgradeAction.sol#L217-L217), [218](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/BOLDUpgradeAction.sol#L218-L218), [219](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/BOLDUpgradeAction.sol#L219-L219), [220](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/BOLDUpgradeAction.sol#L220-L220), [221](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/BOLDUpgradeAction.sol#L221-L221), [224](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/BOLDUpgradeAction.sol#L224-L224), [225](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/BOLDUpgradeAction.sol#L225-L225), [226](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/BOLDUpgradeAction.sol#L226-L226), [227](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/BOLDUpgradeAction.sol#L227-L227), [228](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/BOLDUpgradeAction.sol#L228-L228), [230](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/BOLDUpgradeAction.sol#L230-L230), [231](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/BOLDUpgradeAction.sol#L231-L231), [232](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/BOLDUpgradeAction.sol#L232-L232), [233](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/BOLDUpgradeAction.sol#L233-L233), 


```solidity
Path: ./src/rollup/BridgeCreator.sol

22:    BridgeTemplates public ethBasedTemplates;	// @audit-issue

23:    BridgeTemplates public erc20BasedTemplates;	// @audit-issue
```
[22](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/BridgeCreator.sol#L22-L22), [23](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/BridgeCreator.sol#L23-L23), 


```solidity
Path: ./src/rollup/RollupCore.sol

27:    uint256 public chainId;	// @audit-issue

31:    uint64 public confirmPeriodBlocks;	// @audit-issue

74:    uint256 public baseStake;	// @audit-issue

76:    bytes32 public wasmModuleRoot;	// @audit-issue

78:    IEdgeChallengeManager public challengeManager;	// @audit-issue

82:    uint64 public challengeGracePeriodBlocks;	// @audit-issue

84:    IInboxBase public inbox;	// @audit-issue

85:    IBridge public bridge;	// @audit-issue

86:    IOutbox public outbox;	// @audit-issue

87:    IRollupEventInbox public rollupEventInbox;	// @audit-issue

89:    address public validatorWalletCreator;	// @audit-issue

92:    address public loserStakeEscrow;	// @audit-issue

93:    address public stakeToken;	// @audit-issue

94:    uint256 public minimumAssertionPeriod;	// @audit-issue

96:    mapping(address => bool) public isValidator;	// @audit-issue

102:    mapping(address => Staker) public _stakerMap;	// @audit-issue

105:    uint256 public totalWithdrawableFunds;	// @audit-issue

106:    uint256 public rollupDeploymentBlock;	// @audit-issue

108:    bool public validatorWhitelistDisabled;	// @audit-issue

109:    address public anyTrustFastConfirmer;	// @audit-issue
```
[27](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/RollupCore.sol#L27-L27), [31](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/RollupCore.sol#L31-L31), [74](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/RollupCore.sol#L74-L74), [76](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/RollupCore.sol#L76-L76), [78](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/RollupCore.sol#L78-L78), [82](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/RollupCore.sol#L82-L82), [84](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/RollupCore.sol#L84-L84), [85](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/RollupCore.sol#L85-L85), [86](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/RollupCore.sol#L86-L86), [87](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/RollupCore.sol#L87-L87), [89](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/RollupCore.sol#L89-L89), [92](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/RollupCore.sol#L92-L92), [93](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/RollupCore.sol#L93-L93), [94](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/RollupCore.sol#L94-L94), [96](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/RollupCore.sol#L96-L96), [102](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/RollupCore.sol#L102-L102), [105](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/RollupCore.sol#L105-L105), [106](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/RollupCore.sol#L106-L106), [108](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/RollupCore.sol#L108-L108), [109](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/RollupCore.sol#L109-L109), 


```solidity
Path: ./src/rollup/RollupUserLogic.sol

27:    function initialize(address _stakeToken) external view override onlyProxy {	// @audit-issue

31:    uint256 internal immutable deployTimeChainId = block.chainid;	// @audit-issue

74:        validatorWhitelistDisabled = true;	// @audit-issue

76:	// @audit-issue

78:     * @notice Confirm a unresolved assertion	// @audit-issue

82:    function confirmAssertion(	// @audit-issue

84:        bytes32 prevAssertionHash,	// @audit-issue

85:        AssertionState calldata confirmState,	// @audit-issue

86:        bytes32 winningEdgeId,	// @audit-issue

87:        ConfigData calldata prevConfig,	// @audit-issue

89:    ) external onlyValidator whenNotPaused {	// @audit-issue

92:        * 1. The assertion must be pending	// @audit-issue

93:        * 2. The assertion's deadline must have passed	// @audit-issue

94:        * 3. The assertion's prev must be latest confirmed	// @audit-issue

96:        * 5. If the assertion's prev has more than 1 child, the assertion must be the winner of the challenge	// @audit-issue

102:        // The assertion's must exists and be pending and will be validated in RollupCore.confirmAssertionInternal	// @audit-issue

105:        // prevAssertionHash is user supplied, but will be validated in RollupCore.confirmAssertionInternal	// @audit-issue

106:        AssertionNode storage prevAssertion = getAssertionStorage(prevAssertionHash);	// @audit-issue

108:	// @audit-issue

109:        // Check that deadline has passed	// @audit-issue

49:    uint256 public constant VALIDATOR_AFK_BLOCKS = 201600;	// @audit-issue
```
[27](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/RollupUserLogic.sol#L27-L27), [31](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/RollupUserLogic.sol#L31-L31), [74](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/RollupUserLogic.sol#L74-L74), [76](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/RollupUserLogic.sol#L76-L76), [78](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/RollupUserLogic.sol#L78-L78), [82](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/RollupUserLogic.sol#L82-L82), [84](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/RollupUserLogic.sol#L84-L84), [85](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/RollupUserLogic.sol#L85-L85), [86](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/RollupUserLogic.sol#L86-L86), [87](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/RollupUserLogic.sol#L87-L87), [89](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/RollupUserLogic.sol#L89-L89), [92](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/RollupUserLogic.sol#L92-L92), [93](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/RollupUserLogic.sol#L93-L93), [94](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/RollupUserLogic.sol#L94-L94), [96](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/RollupUserLogic.sol#L96-L96), [102](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/RollupUserLogic.sol#L102-L102), [105](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/RollupUserLogic.sol#L105-L105), [106](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/RollupUserLogic.sol#L106-L106), [108](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/RollupUserLogic.sol#L108-L108), [109](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/RollupUserLogic.sol#L109-L109), [49](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/RollupUserLogic.sol#L49-L49), 


```solidity
Path: ./src/rollup/RollupCreator.sol

47:    BridgeCreator public bridgeCreator;	// @audit-issue

48:    IOneStepProofEntry public osp;	// @audit-issue

49:    IEdgeChallengeManager public challengeManagerTemplate;	// @audit-issue

50:    IRollupAdmin public rollupAdminLogic;	// @audit-issue

51:    IRollupUser public rollupUserLogic;	// @audit-issue

52:    IUpgradeExecutor public upgradeExecutorLogic;	// @audit-issue

54:    address public validatorWalletCreator;	// @audit-issue

56:    DeployHelper public l2FactoriesDeployer;	// @audit-issue
```
[47](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/RollupCreator.sol#L47-L47), [48](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/RollupCreator.sol#L48-L48), [49](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/RollupCreator.sol#L49-L49), [50](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/RollupCreator.sol#L50-L50), [51](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/RollupCreator.sol#L51-L51), [52](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/RollupCreator.sol#L52-L52), [54](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/RollupCreator.sol#L54-L54), [56](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/RollupCreator.sol#L56-L56), 


```solidity
Path: ./src/rollup/RollupAdminLogic.sol

27:        connectedContracts.bridge.setSequencerInbox(address(connectedContracts.sequencerInbox));	// @audit-issue

31:        connectedContracts.bridge.setOutbox(address(connectedContracts.outbox), true);	// @audit-issue

74:            currentInboxCount += 1;	// @audit-issue

76:        AssertionNode memory initialAssertion = AssertionNodeLib.createAssertion(	// @audit-issue

78:            RollupLib.configHash({	// @audit-issue

82:                confirmPeriodBlocks: confirmPeriodBlocks,	// @audit-issue

84:            })	// @audit-issue

85:        );	// @audit-issue

86:        initializeCore(initialAssertion, genesisHash);	// @audit-issue

87:	// @audit-issue

89:        assertionInputs.afterState = config.genesisAssertionState;	// @audit-issue

92:            parentAssertionHash,	// @audit-issue

93:            assertionInputs,	// @audit-issue

94:            inboxAcc,	// @audit-issue

96:            wasmModuleRoot,	// @audit-issue

102:            _assertionCreatedAtArbSysBlock[genesisHash] = ArbSys(address(100)).arbBlockNumber();	// @audit-issue

105:        emit RollupInitialized(config.wasmModuleRoot, config.chainId);	// @audit-issue

106:    }	// @audit-issue

108:    /**	// @audit-issue

109:     * Functions are only to reach this logic contract if the caller is the owner	// @audit-issue
```
[27](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/RollupAdminLogic.sol#L27-L27), [31](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/RollupAdminLogic.sol#L31-L31), [74](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/RollupAdminLogic.sol#L74-L74), [76](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/RollupAdminLogic.sol#L76-L76), [78](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/RollupAdminLogic.sol#L78-L78), [82](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/RollupAdminLogic.sol#L82-L82), [84](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/RollupAdminLogic.sol#L84-L84), [85](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/RollupAdminLogic.sol#L85-L85), [86](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/RollupAdminLogic.sol#L86-L86), [87](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/RollupAdminLogic.sol#L87-L87), [89](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/RollupAdminLogic.sol#L89-L89), [92](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/RollupAdminLogic.sol#L92-L92), [93](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/RollupAdminLogic.sol#L93-L93), [94](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/RollupAdminLogic.sol#L94-L94), [96](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/RollupAdminLogic.sol#L96-L96), [102](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/RollupAdminLogic.sol#L102-L102), [105](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/RollupAdminLogic.sol#L105-L105), [106](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/RollupAdminLogic.sol#L106-L106), [108](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/RollupAdminLogic.sol#L108-L108), [109](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/RollupAdminLogic.sol#L109-L109), 


```solidity
Path: ./src/challengeV2/EdgeChallengeManager.sol

273:    address public excessStakeReceiver;	// @audit-issue

276:    IERC20 public stakeToken;	// @audit-issue

279:    uint256[] public stakeAmounts;	// @audit-issue

282:    uint64 public challengePeriodBlocks;	// @audit-issue

285:    IAssertionChain public assertionChain;	// @audit-issue

288:    IOneStepProofEntry public override oneStepProofEntry;	// @audit-issue

291:    uint256 public LAYERZERO_BLOCKEDGE_HEIGHT;	// @audit-issue

293:    uint256 public LAYERZERO_BIGSTEPEDGE_HEIGHT;	// @audit-issue

295:    uint256 public LAYERZERO_SMALLSTEPEDGE_HEIGHT;	// @audit-issue

298:    uint8 public NUM_BIGSTEP_LEVEL;	// @audit-issue
```
[273](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/challengeV2/EdgeChallengeManager.sol#L273-L273), [276](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/challengeV2/EdgeChallengeManager.sol#L276-L276), [279](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/challengeV2/EdgeChallengeManager.sol#L279-L279), [282](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/challengeV2/EdgeChallengeManager.sol#L282-L282), [285](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/challengeV2/EdgeChallengeManager.sol#L285-L285), [288](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/challengeV2/EdgeChallengeManager.sol#L288-L288), [291](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/challengeV2/EdgeChallengeManager.sol#L291-L291), [293](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/challengeV2/EdgeChallengeManager.sol#L293-L293), [295](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/challengeV2/EdgeChallengeManager.sol#L295-L295), [298](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/challengeV2/EdgeChallengeManager.sol#L298-L298), 


```solidity
Path: ./src/challengeV2/libraries/EdgeChallengeManagerLib.sol

135:    bytes32 public constant UNRIVALED = keccak256(abi.encodePacked("UNRIVALED"));	// @audit-issue
```
[135](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/challengeV2/libraries/EdgeChallengeManagerLib.sol#L135-L135), 


```solidity
Path: ./src/challengeV2/libraries/MerkleTreeLib.sol

104:    uint256 public constant MAX_LEVEL = 64;	// @audit-issue
```
[104](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/challengeV2/libraries/MerkleTreeLib.sol#L104-L104), 


```solidity
Path: ./src/assertionStakingPool/EdgeStakingPool.sol

20:///         It is assumed that the challenge manager will not return more tokens than the amount deposited by the pool.	// @audit-issue

22:///	// @audit-issue

29:    address public immutable challengeManager;	// @audit-issue

31:    bytes32 public immutable edgeId;	// @audit-issue
```
[20](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/assertionStakingPool/EdgeStakingPool.sol#L20-L20), [22](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/assertionStakingPool/EdgeStakingPool.sol#L22-L22), [29](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/assertionStakingPool/EdgeStakingPool.sol#L29-L29), [31](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/assertionStakingPool/EdgeStakingPool.sol#L31-L31), 


```solidity
Path: ./src/assertionStakingPool/AssertionStakingPool.sol

20:///         Any tokens exceeding the deposited amount to the pool will be stuck in the pool forever.	// @audit-issue

22:    using SafeERC20 for IERC20;	// @audit-issue

25:    address public immutable rollup;	// @audit-issue

27:    bytes32 public immutable assertionHash;	// @audit-issue
```
[20](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/assertionStakingPool/AssertionStakingPool.sol#L20-L20), [22](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/assertionStakingPool/AssertionStakingPool.sol#L22-L22), [25](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/assertionStakingPool/AssertionStakingPool.sol#L25-L25), [27](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/assertionStakingPool/AssertionStakingPool.sol#L27-L27), 


```solidity
Path: ./src/assertionStakingPool/AbsBoldStakingPool.sol

20:    address public immutable stakeToken;	// @audit-issue

22:    mapping(address => uint256) public depositBalance;	// @audit-issue
```
[20](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/assertionStakingPool/AbsBoldStakingPool.sol#L20-L20), [22](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/assertionStakingPool/AbsBoldStakingPool.sol#L22-L22), 


#### Recommendation

Avoid creating explicit getter functions for 'public' state variables in Solidity. The compiler automatically generates getters for such variables, making additional functions redundant. This practice helps reduce contract size, lowers deployment costs, and simplifies maintenance and understanding of the contract.

### Use `do while` loops intead of for loops
A `do while` loop will cost less gas since the condition is not being checked for the first iteration.
```solidity
uint256 i = 1;
do {                   
    param2 += i;
    i++;
}
while (i < 50);
``` 
is better than
```solidity
for(uint256 i = 1; i< 50; i++){
    param1 += i;
}
```


```solidity
Path: ./src/rollup/BOLDUpgradeAction.sol

350:        for (uint64 i = 0; i < stakerCount; i++) {	// @audit-issue

528:            for (uint256 i = 0; i < validators.length; i++) {	// @audit-issue
```
[350](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/BOLDUpgradeAction.sol#L350-L350), [528](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/BOLDUpgradeAction.sol#L528-L528), 


```solidity
Path: ./src/rollup/RollupCreator.sol

225:        for (uint256 i = 0; i < deployParams.batchPosters.length; i++) {	// @audit-issue

235:            for (uint256 i = 0; i < deployParams.validators.length; i++) {	// @audit-issue
```
[225](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/RollupCreator.sol#L225-L225), [235](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/RollupCreator.sol#L235-L235), 


```solidity
Path: ./src/rollup/RollupAdminLogic.sol

184:        for (uint256 i = 0; i < _validator.length; i++) {	// @audit-issue

230:        for (uint256 i = 0; i < staker.length; i++) {	// @audit-issue
```
[184](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/RollupAdminLogic.sol#L184-L184), [230](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/RollupAdminLogic.sol#L230-L230), 


```solidity
Path: ./src/challengeV2/EdgeChallengeManager.sol

492:        for (uint256 i = 0; i < edgeIds.length; i++) {	// @audit-issue
```
[492](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/challengeV2/EdgeChallengeManager.sol#L492-L492), 


```solidity
Path: ./src/challengeV2/libraries/ArrayUtilsLib.sol

15:        for (uint256 i = 0; i < arr.length; i++) {	// @audit-issue

36:        for (uint256 i = startIndex; i < endIndex; i++) {	// @audit-issue

47:        for (uint256 i = 0; i < arr1.length; i++) {	// @audit-issue

50:        for (uint256 i = 0; i < arr2.length; i++) {	// @audit-issue
```
[15](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/challengeV2/libraries/ArrayUtilsLib.sol#L15-L15), [36](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/challengeV2/libraries/ArrayUtilsLib.sol#L36-L36), [47](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/challengeV2/libraries/ArrayUtilsLib.sol#L47-L47), [50](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/challengeV2/libraries/ArrayUtilsLib.sol#L50-L50), 


```solidity
Path: ./src/challengeV2/libraries/MerkleTreeLib.sol

115:        for (uint256 i = 0; i < me.length; i++) {	// @audit-issue

188:        for (uint256 i = 0; i < me.length; i++) {	// @audit-issue

294:        for (uint256 i = 0; i < me.length; i++) {	// @audit-issue
```
[115](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/challengeV2/libraries/MerkleTreeLib.sol#L115-L115), [188](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/challengeV2/libraries/MerkleTreeLib.sol#L188-L188), [294](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/challengeV2/libraries/MerkleTreeLib.sol#L294-L294), 


#### Recommendation

Where appropriate, consider using a `do while` loop instead of a `for` loop in your Solidity contracts. This is especially beneficial when the first iteration of the loop does not require a condition check. Refactor your loop logic to fit the `do while` structure for more gas-efficient execution. However, ensure that the loop's logic and termination conditions are correctly implemented to avoid infinite loops or other logical errors. Always balance gas efficiency with code readability and the specific requirements of your contract's logic.

### Using XOR (^) and AND (&) bitwise equivalents for gas optimizations
Given 4 variables a, b, c and d represented as such:
```
0 0 0 0 0 1 1 0 <- a
0 1 1 0 0 1 1 0 <- b
0 0 0 0 0 0 0 0 <- c
1 1 1 1 1 1 1 1 <- d
```
To have a == b means that every 0 and 1 match on both variables. Meaning that a XOR (operator ^) would evaluate to 0 ((a ^ b) == 0), as it excludes by definition any equalities.Now, if a != b, this means that there’s at least somewhere a 1 and a 0 not matching between a and b, making (a ^ b) != 0.Both formulas are logically equivalent and using the XOR bitwise operator costs actually the same amount of gas.However, it is much cheaper to use the bitwise OR operator (|) than comparing the truthy or falsy values.These are logically equivalent too, as the OR bitwise operator (|) would result in a 1 somewhere if any value is not 0 between the XOR (^) statements, meaning if any XOR (^) statement verifies that its arguments are different.


```solidity
Path: ./src/bridge/SequencerInbox.sol

150:            if (reader4844_ == IReader4844(address(0))) revert InitParamZero("Reader4844");	// @audit-issue

183:        if (bridge_ == IBridge(address(0))) revert HadZeroInit();	// @audit-issue

212:        if (rollup == newRollup) revert RollupNotChanged();	// @audit-issue

507:        if (msg.sender == tx.origin && !isUsingFeeToken) {	// @audit-issue

651:        assert(header.length == HEADER_LENGTH);	// @audit-issue

677:            headerByte == BROTLI_MESSAGE_HEADER_FLAG ||	// @audit-issue

678:            headerByte == DAS_MESSAGE_HEADER_FLAG ||	// @audit-issue

679:            (headerByte == (DAS_MESSAGE_HEADER_FLAG | TREE_DAS_MESSAGE_HEADER_FLAG)) ||	// @audit-issue

680:            headerByte == ZERO_HEAVY_MESSAGE_HEADER_FLAG;	// @audit-issue

736:        if (dataHashes.length == 0) revert MissingDataHashes();	// @audit-issue

851:        if (buffer.bufferBlocks == 0 || buffer.bufferBlocks > bufferConfig_.max) {	// @audit-issue

862:        if (bridge.delayedMessageCount() == totalDelayedMessagesRead) {	// @audit-issue

959:        if (ksInfo.creationBlock == 0) revert NoSuchKeyset(ksHash);	// @audit-issue
```
[150](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/bridge/SequencerInbox.sol#L150-L150), [183](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/bridge/SequencerInbox.sol#L183-L183), [212](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/bridge/SequencerInbox.sol#L212-L212), [507](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/bridge/SequencerInbox.sol#L507-L507), [651](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/bridge/SequencerInbox.sol#L651-L651), [677](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/bridge/SequencerInbox.sol#L677-L677), [678](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/bridge/SequencerInbox.sol#L678-L678), [679](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/bridge/SequencerInbox.sol#L679-L679), [680](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/bridge/SequencerInbox.sol#L680-L680), [736](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/bridge/SequencerInbox.sol#L736-L736), [851](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/bridge/SequencerInbox.sol#L851-L851), [862](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/bridge/SequencerInbox.sol#L862-L862), [959](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/bridge/SequencerInbox.sol#L959-L959), 


```solidity
Path: ./src/rollup/RollupLib.sol

78:            _configHash	// @audit-issue
```
[78](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/RollupLib.sol#L78-L78), 


```solidity
Path: ./src/rollup/BOLDUpgradeAction.sol

107:        require(h == stateHash(executionState, inboxMaxCount), "Invalid hash");	// @audit-issue

353:            if (staker.isStaked && staker.currentChallenge == 0) {	// @audit-issue

379:            PREIMAGE_LOOKUP.stateHash(genesisAssertionState.toExecutionState(), inboxMaxCount)	// @audit-issue

454:            PROXY_ADMIN_SEQUENCER_INBOX.getProxyImplementation(sequencerInbox) == IMPL_SEQUENCER_INBOX,	// @audit-issue

458:            ISequencerInbox(SEQ_INBOX).isDelayBufferable() == IS_DELAY_BUFFERABLE,	// @audit-issue

517:        require(address(rollup) == expectedRollupAddress, "UNEXPCTED_ROLLUP_ADDR");	// @audit-issue
```
[107](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/BOLDUpgradeAction.sol#L107-L107), [353](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/BOLDUpgradeAction.sol#L353-L353), [379](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/BOLDUpgradeAction.sol#L379-L379), [454](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/BOLDUpgradeAction.sol#L454-L454), [458](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/BOLDUpgradeAction.sol#L458-L458), [517](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/BOLDUpgradeAction.sol#L517-L517), 


```solidity
Path: ./src/rollup/Assertion.sol

86:        if (self.firstChildBlock == 0) {	// @audit-issue

88:        } else if (self.secondChildBlock == 0) {	// @audit-issue
```
[86](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/Assertion.sol#L86-L86), [88](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/Assertion.sol#L88-L88), 


```solidity
Path: ./src/rollup/BridgeCreator.sol

112:            nativeToken == address(0) ? ethBasedTemplates : erc20BasedTemplates,	// @audit-issue

117:        if (nativeToken == address(0)) {	// @audit-issue
```
[112](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/BridgeCreator.sol#L112-L112), [117](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/BridgeCreator.sol#L117-L117), 


```solidity
Path: ./src/rollup/RollupCore.sol

244:        require(assertion.status == AssertionStatus.Pending, "NOT_PENDING");	// @audit-issue

248:            assertionHash	// @audit-issue

379:            assertion.afterState.machineStatus == MachineStatus.FINISHED	// @audit-issue

380:                || assertion.afterState.machineStatus == MachineStatus.ERRORED,	// @audit-issue

386:            RollupLib.assertionHash(	// @audit-issue

399:        require(assertion.beforeState.machineStatus == MachineStatus.FINISHED, "BAD_PREV_STATUS");	// @audit-issue

451:            if (afterInboxPosition == currentInboxPosition) {	// @audit-issue

478:            newAssertionHash == expectedAssertionHash || expectedAssertionHash == bytes32(0),	// @audit-issue

485:        require(getAssertionStorage(newAssertionHash).status == AssertionStatus.NoAssertion, "ASSERTION_SEEN");	// @audit-issue

489:            prevAssertion.firstChildBlock == 0, // assumes block 0 is impossible	// @audit-issue

546:        require(assertionHash == RollupLib.assertionHash(prevAssertionHash, state, inboxAcc), "INVALID_ASSERTION_HASH");	// @audit-issue

558:        return getAssertionStorage(assertionHash).status == AssertionStatus.Pending;	// @audit-issue

571:        bool isLatestConfirmed = lastestAssertion == latestConfirmed();	// @audit-issue
```
[244](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/RollupCore.sol#L244-L244), [248](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/RollupCore.sol#L248-L248), [379](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/RollupCore.sol#L379-L379), [380](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/RollupCore.sol#L380-L380), [386](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/RollupCore.sol#L386-L386), [399](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/RollupCore.sol#L399-L399), [451](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/RollupCore.sol#L451-L451), [478](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/RollupCore.sol#L478-L478), [485](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/RollupCore.sol#L485-L485), [489](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/RollupCore.sol#L489-L489), [546](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/RollupCore.sol#L546-L546), [558](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/RollupCore.sol#L558-L558), [571](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/RollupCore.sol#L571-L571), 


```solidity
Path: ./src/rollup/RollupUserLogic.sol

53:        if (latestConfirmedAssertion.createdAtBlock == 0) return false;	// @audit-issue

113:        require(prevAssertionHash == latestConfirmed(), "PREV_NOT_LATEST_CONFIRMED");	// @audit-issue

118:            require(winningEdge.claimId == assertionHash, "NOT_WINNER");	// @audit-issue

119:            require(winningEdge.status == EdgeStatus.Confirmed, "EDGE_NOT_CONFIRMED");	// @audit-issue

170:            expectedAssertionHash == bytes32(0)	// @audit-issue

171:                || getAssertionStorage(expectedAssertionHash).status == AssertionStatus.NoAssertion,	// @audit-issue

196:            lastAssertion == prevAssertion || getAssertionStorage(lastAssertion).firstChildBlock > 0,	// @audit-issue

258:        require(msg.sender == anyTrustFastConfirmer, "NOT_FAST_CONFIRMER");	// @audit-issue

288:        if (status == AssertionStatus.NoAssertion) {	// @audit-issue
```
[53](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/RollupUserLogic.sol#L53-L53), [113](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/RollupUserLogic.sol#L113-L113), [118](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/RollupUserLogic.sol#L118-L118), [119](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/RollupUserLogic.sol#L119-L119), [170](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/RollupUserLogic.sol#L170-L170), [171](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/RollupUserLogic.sol#L171-L171), [196](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/RollupUserLogic.sol#L196-L196), [258](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/RollupUserLogic.sol#L258-L258), [288](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/RollupUserLogic.sol#L288-L288), 


```solidity
Path: ./src/rollup/RollupCreator.sol

153:                deployParams.maxDataSize == ethSequencerInbox.maxDataSize(),	// @audit-issue

157:                deployParams.maxDataSize == ethDelayBufferableSequencerInbox.maxDataSize(),	// @audit-issue

160:            require(deployParams.maxDataSize == ethInbox.maxDataSize(), "I_MAX_DATA_SIZE_MISMATCH");	// @audit-issue

171:                deployParams.maxDataSize == erc20SequencerInbox.maxDataSize(),	// @audit-issue

175:                deployParams.maxDataSize == erc20DelayBufferableSequencerInbox.maxDataSize(),	// @audit-issue

179:                deployParams.maxDataSize == erc20Inbox.maxDataSize(),	// @audit-issue

292:        if (_nativeToken == address(0)) {	// @audit-issue
```
[153](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/RollupCreator.sol#L153-L153), [157](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/RollupCreator.sol#L157-L157), [160](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/RollupCreator.sol#L160-L160), [171](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/RollupCreator.sol#L171-L171), [175](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/RollupCreator.sol#L175-L175), [179](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/RollupCreator.sol#L179-L179), [292](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/RollupCreator.sol#L292-L292), 


```solidity
Path: ./src/rollup/RollupAdminLogic.sol

40:        if (connectedContracts.sequencerInbox.totalDelayedMessagesRead() == 0) {	// @audit-issue

73:        if (currentInboxCount == config.genesisInboxCount) {	// @audit-issue

182:        require(_validator.length == _val.length, "WRONG_LENGTH");	// @audit-issue
```
[40](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/RollupAdminLogic.sol#L40-L40), [73](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/RollupAdminLogic.sol#L73-L73), [182](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/RollupAdminLogic.sol#L182-L182), 


```solidity
Path: ./src/rollup/RollupProxy.sol

16:            _getAdmin() == address(0) &&	// @audit-issue

17:            _getImplementation() == address(0) &&	// @audit-issue

18:            _getSecondaryImplementation() == address(0)	// @audit-issue
```
[16](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/RollupProxy.sol#L16-L16), [17](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/RollupProxy.sol#L17-L17), [18](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/RollupProxy.sol#L18-L18), 


```solidity
Path: ./src/challengeV2/EdgeChallengeManager.sol

317:        if (address(_assertionChain) == address(0)) {	// @audit-issue

321:        if (address(_oneStepProofEntry) == address(0)) {	// @audit-issue

325:        if (_challengePeriodBlocks == 0) {	// @audit-issue

331:        if (_excessStakeReceiver == address(0)) {	// @audit-issue

350:        if (_numBigStepLevel == 0) {	// @audit-issue

385:        if (eType == EdgeType.Block) {	// @audit-issue

387:            if (args.proof.length == 0) {	// @audit-issue

458:        bool lowerChildAlreadyExists = lowerChildAdded.edgeId == 0;	// @audit-issue

521:        bool isBlockLevel = ChallengeEdgeLib.levelToType(topEdge.level, NUM_BIGSTEP_LEVEL) == EdgeType.Block;	// @audit-issue

592:        if (eType == EdgeType.Block) {	// @audit-issue

594:        } else if (eType == EdgeType.BigStep) {	// @audit-issue

596:        } else if (eType == EdgeType.SmallStep) {	// @audit-issue
```
[317](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/challengeV2/EdgeChallengeManager.sol#L317-L317), [321](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/challengeV2/EdgeChallengeManager.sol#L321-L321), [325](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/challengeV2/EdgeChallengeManager.sol#L325-L325), [331](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/challengeV2/EdgeChallengeManager.sol#L331-L331), [350](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/challengeV2/EdgeChallengeManager.sol#L350-L350), [385](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/challengeV2/EdgeChallengeManager.sol#L385-L385), [387](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/challengeV2/EdgeChallengeManager.sol#L387-L387), [458](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/challengeV2/EdgeChallengeManager.sol#L458-L458), [521](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/challengeV2/EdgeChallengeManager.sol#L521-L521), [592](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/challengeV2/EdgeChallengeManager.sol#L592-L592), [594](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/challengeV2/EdgeChallengeManager.sol#L594-L594), [596](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/challengeV2/EdgeChallengeManager.sol#L596-L596), 


```solidity
Path: ./src/challengeV2/libraries/EdgeChallengeManagerLib.sol

182:        if (firstRival == 0) {	// @audit-issue

184:        } else if (firstRival == UNRIVALED) {	// @audit-issue

220:        if (ChallengeEdgeLib.levelToType(args.level, numBigStepLevel) == EdgeType.Block) {	// @audit-issue

229:            if (ard.assertionHash == 0) {	// @audit-issue

248:            if (args.proof.length == 0) {	// @audit-issue

255:            if (ard.startState.machineStatus == MachineStatus.RUNNING) {	// @audit-issue

258:            if (ard.endState.machineStatus == MachineStatus.RUNNING) {	// @audit-issue

294:            if (args.proof.length == 0) {	// @audit-issue

329:        if (x == 0) {	// @audit-issue

337:        return ((x & y) == 0);	// @audit-issue

378:        if (args.prefixProof.length == 0) {	// @audit-issue

472:        if (firstRival == 0) {	// @audit-issue

485:        return (hasRival(store, edgeId) && store.edges[edgeId].length() == 1);	// @audit-issue

545:        if (firstRival == 0) {	// @audit-issue

551:        if (firstRival == UNRIVALED) {	// @audit-issue

580:        if (end - start == 2) {	// @audit-issue
```
[182](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/challengeV2/libraries/EdgeChallengeManagerLib.sol#L182-L182), [184](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/challengeV2/libraries/EdgeChallengeManagerLib.sol#L184-L184), [220](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/challengeV2/libraries/EdgeChallengeManagerLib.sol#L220-L220), [229](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/challengeV2/libraries/EdgeChallengeManagerLib.sol#L229-L229), [248](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/challengeV2/libraries/EdgeChallengeManagerLib.sol#L248-L248), [255](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/challengeV2/libraries/EdgeChallengeManagerLib.sol#L255-L255), [258](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/challengeV2/libraries/EdgeChallengeManagerLib.sol#L258-L258), [294](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/challengeV2/libraries/EdgeChallengeManagerLib.sol#L294-L294), [329](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/challengeV2/libraries/EdgeChallengeManagerLib.sol#L329-L329), [337](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/challengeV2/libraries/EdgeChallengeManagerLib.sol#L337-L337), [378](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/challengeV2/libraries/EdgeChallengeManagerLib.sol#L378-L378), [472](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/challengeV2/libraries/EdgeChallengeManagerLib.sol#L472-L472), [485](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/challengeV2/libraries/EdgeChallengeManagerLib.sol#L485-L485), [545](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/challengeV2/libraries/EdgeChallengeManagerLib.sol#L545-L545), [551](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/challengeV2/libraries/EdgeChallengeManagerLib.sol#L551-L551), [580](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/challengeV2/libraries/EdgeChallengeManagerLib.sol#L580-L580), 


```solidity
Path: ./src/challengeV2/libraries/MerkleTreeLib.sol

117:            if (accum == 0) {	// @audit-issue

162:        if (me.length == 0) {	// @audit-issue

195:                require(me[i] == 0, "Append above least significant bit");	// @audit-issue

198:                if (accumHash == 0) {	// @audit-issue

203:                    if (me[i] == 0) {	// @audit-issue

321:        require(root(preExpansion) == preRoot, "Pre expansion root mismatch");	// @audit-issue

322:        require(treeSize(preExpansion) == preSize, "Pre size does not match expansion");	// @audit-issue

345:        require(root(exp) == postRoot, "Post expansion root not equal post");	// @audit-issue

349:        require(proofIndex == proof.length, "Incomplete proof usage");	// @audit-issue

364:        require(rootHash == calculatedRoot, "Invalid inclusion proof");	// @audit-issue
```
[117](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/challengeV2/libraries/MerkleTreeLib.sol#L117-L117), [162](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/challengeV2/libraries/MerkleTreeLib.sol#L162-L162), [195](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/challengeV2/libraries/MerkleTreeLib.sol#L195-L195), [198](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/challengeV2/libraries/MerkleTreeLib.sol#L198-L198), [203](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/challengeV2/libraries/MerkleTreeLib.sol#L203-L203), [321](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/challengeV2/libraries/MerkleTreeLib.sol#L321-L321), [322](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/challengeV2/libraries/MerkleTreeLib.sol#L322-L322), [345](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/challengeV2/libraries/MerkleTreeLib.sol#L345-L345), [349](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/challengeV2/libraries/MerkleTreeLib.sol#L349-L349), [364](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/challengeV2/libraries/MerkleTreeLib.sol#L364-L364), 


```solidity
Path: ./src/challengeV2/libraries/ChallengeEdgeLib.sol

76:        if (originId == 0) {	// @audit-issue

82:        if (startHistoryRoot == 0) {	// @audit-issue

85:        if (endHistoryRoot == 0) {	// @audit-issue

103:        if (staker == address(0)) {	// @audit-issue

106:        if (claimId == 0) {	// @audit-issue

231:        if (len == 0) {	// @audit-issue

271:        if (edge.refunded == true) {	// @audit-issue

280:        if (level == 0) {	// @audit-issue

284:        } else if (level == numBigStepLevels + 1) {	// @audit-issue
```
[76](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/challengeV2/libraries/ChallengeEdgeLib.sol#L76-L76), [82](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/challengeV2/libraries/ChallengeEdgeLib.sol#L82-L82), [85](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/challengeV2/libraries/ChallengeEdgeLib.sol#L85-L85), [103](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/challengeV2/libraries/ChallengeEdgeLib.sol#L103-L103), [106](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/challengeV2/libraries/ChallengeEdgeLib.sol#L106-L106), [231](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/challengeV2/libraries/ChallengeEdgeLib.sol#L231-L231), [271](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/challengeV2/libraries/ChallengeEdgeLib.sol#L271-L271), [280](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/challengeV2/libraries/ChallengeEdgeLib.sol#L280-L280), [284](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/challengeV2/libraries/ChallengeEdgeLib.sol#L284-L284), 


```solidity
Path: ./src/assertionStakingPool/AbsBoldStakingPool.sol

30:        if (amount == 0) {	// @audit-issue

42:        if (amount == 0) {	// @audit-issue
```
[30](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/assertionStakingPool/AbsBoldStakingPool.sol#L30-L30), [42](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/assertionStakingPool/AbsBoldStakingPool.sol#L42-L42), 


#### Recommendation

Review your Solidity contracts to identify any computations that are performed multiple times with the same inputs. Cache the results of these computations in local variables and reuse them within the function or across function calls if the state remains unchanged.

### Consider using `bytes32` rather than a `string`
Using the bytes types for fixed-length strings is more efficient than having the EVM have to incur the overhead of string processing. Consider whether the value needs to be a string. A good reason to keep it as a string would be if the variable is defined in an interface that this project does not own.


```solidity
Path: ./src/rollup/Config.sol

25:    string chainConfig;	// @audit-issue
```
[25](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/Config.sol#L25-L25), 


```solidity
Path: ./src/libraries/Error.sol

192:error InitParamZero(string name);	// @audit-issue
```
[192](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/libraries/Error.sol#L192-L192), 


#### Recommendation

For fixed-length strings, prefer using 'bytes32' over 'string' to leverage EVM efficiency and reduce overhead. Evaluate the necessity of using a string, especially if the variable isn't part of an externally defined interface.

### The result of a function call should be cached rather than re-calling the function
The function calls in solidity are expensive. If the same result of the same function calls are to be used several times, the result should be cached to reduce the gas consumption of repeated calls.        

```solidity
Path: ./src/bridge/SequencerInbox.sol

150:            if (reader4844_ == IReader4844(address(0))) revert InitParamZero("Reader4844");	// @audit-issue: Function call `IReader4844` is called multiple times at lines [148].

183:        if (bridge_ == IBridge(address(0))) revert HadZeroInit();	// @audit-issue: Function call `IBridge` is called multiple times at lines [182].

209:        if (msg.sender != IOwnable(rollup).owner())	// @audit-issue: Function call `owner` is called multiple times at lines [210].

209:        if (msg.sender != IOwnable(rollup).owner())	// @audit-issue: Function call `IOwnable` is called multiple times at lines [210].

871:            maxTimeVariation_.delayBlocks > type(uint64).max ||	// @audit-issue: Function call is called multiple times at line(s) [873, 874, 872].
```
[150](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/bridge/SequencerInbox.sol#L150-L150), [183](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/bridge/SequencerInbox.sol#L183-L183), [209](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/bridge/SequencerInbox.sol#L209-L209), [209](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/bridge/SequencerInbox.sol#L209-L209), [871](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/bridge/SequencerInbox.sol#L871-L871), 


```solidity
Path: ./src/rollup/BOLDUpgradeAction.sol

342:        IOldRollupAdmin(address(OLD_ROLLUP)).pause();	// @audit-issue: Function call `IOldRollupAdmin` is called multiple times at lines [357].

458:            ISequencerInbox(SEQ_INBOX).isDelayBufferable() == IS_DELAY_BUFFERABLE,	// @audit-issue: Function call `ISequencerInbox` is called multiple times at lines [461].

538:        IRollupAdmin(address(rollup)).setOwner(actualOwner);	// @audit-issue: Function call `IRollupAdmin` is called multiple times at lines [535, 532].
```
[342](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/BOLDUpgradeAction.sol#L342-L342), [458](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/BOLDUpgradeAction.sol#L458-L458), [538](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/BOLDUpgradeAction.sol#L538-L538), 


```solidity
Path: ./src/rollup/BridgeCreator.sol

120:            IERC20Bridge(address(frame.bridge)).initialize(IOwnable(rollup), nativeToken);	// @audit-issue: Function call `IOwnable` is called multiple times at lines [118].
```
[120](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/BridgeCreator.sol#L120-L120), 


```solidity
Path: ./src/rollup/RollupCore.sol

372:            assertion.beforeStateData.configData, getAssertionStorage(prevAssertionHash).configHash	// @audit-issue: Function call `getAssertionStorage` is called multiple times at lines [401].

433:                require(afterGS.comparePositions(beforeGS) > 0, "OVERFLOW_STANDSTILL");	// @audit-issue: Function call `comparePositions` is called multiple times at lines [424].
```
[372](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/RollupCore.sol#L372-L372), [433](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/RollupCore.sol#L433-L433), 


```solidity
Path: ./src/rollup/RollupUserLogic.sol

205:            uint256 timeSincePrev = block.number - getAssertionStorage(prevAssertion).createdAtBlock;	// @audit-issue: Function call `getAssertionStorage` is called multiple times at lines [189].
```
[205](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/RollupUserLogic.sol#L205-L205), 


```solidity
Path: ./src/rollup/RollupCreator.sol

238:            IRollupAdmin(address(rollup)).setValidator(deployParams.validators, _vals);	// @audit-issue: Function call `IRollupAdmin` is called multiple times at lines [241].

294:            uint256 cost = l2FactoriesDeployer.getDeploymentTotalCost(	// @audit-issue: Function call `getDeploymentTotalCost` is called multiple times at lines [308].

295:                IInboxBase(_inbox),	// @audit-issue: Function call `IInboxBase` is called multiple times at lines [309].
```
[238](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/RollupCreator.sol#L238-L238), [294](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/RollupCreator.sol#L294-L294), [295](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/RollupCreator.sol#L295-L295), 


```solidity
Path: ./src/challengeV2/libraries/EdgeChallengeManagerLib.sol

295:                revert EmptyEdgeSpecificProof();	// @audit-issue: Function call `EmptyEdgeSpecificProof` is called multiple times at lines [249].

507:        newValue = newValue > type(uint64).max ? type(uint64).max : newValue;	// @audit-issue: Function call is called multiple times at line(s) [507].

699:            revert OriginIdMutualIdMismatch(store.edges[edgeId].mutualId(), store.edges[claimingEdgeId].originId);	// @audit-issue: Function call `mutualId` is called multiple times at lines [698].

702:        if (nextEdgeLevel(store.edges[edgeId].level, numBigStepLevel) != store.edges[claimingEdgeId].level) {	// @audit-issue: Function call `nextEdgeLevel` is called multiple times at lines [706].

788:        if (store.edges[edgeId].length() != 1) {	// @audit-issue: Function call `length` is called multiple times at lines [789].
```
[295](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/challengeV2/libraries/EdgeChallengeManagerLib.sol#L295-L295), [507](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/challengeV2/libraries/EdgeChallengeManagerLib.sol#L507-L507), [699](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/challengeV2/libraries/EdgeChallengeManagerLib.sol#L699-L699), [702](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/challengeV2/libraries/EdgeChallengeManagerLib.sol#L702-L702), [788](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/challengeV2/libraries/EdgeChallengeManagerLib.sol#L788-L788), 


```solidity
Path: ./src/challengeV2/libraries/MerkleTreeLib.sol

126:                        accum = keccak256(abi.encodePacked(accum, bytes32(0)));	// @audit-issue: Function call `keccak256` is called multiple times at lines [135].

126:                        accum = keccak256(abi.encodePacked(accum, bytes32(0)));	// @audit-issue: Function call `encodePacked` is called multiple times at lines [135].
```
[126](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/challengeV2/libraries/MerkleTreeLib.sol#L126-L126), [126](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/challengeV2/libraries/MerkleTreeLib.sol#L126-L126), 


```solidity
Path: ./src/challengeV2/libraries/ChallengeEdgeLib.sol

272:            revert EdgeAlreadyRefunded(ChallengeEdgeLib.id(edge));	// @audit-issue: Function call `id` is called multiple times at lines [269, 266].
```
[272](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/challengeV2/libraries/ChallengeEdgeLib.sol#L272-L272), 


```solidity
Path: ./src/assertionStakingPool/EdgeStakingPool.sol

47:        bytes32 newEdgeId = EdgeChallengeManager(challengeManager).createLayerZeroEdge(args);	// @audit-issue: Function call `EdgeChallengeManager` is called multiple times at lines [45].
```
[47](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/assertionStakingPool/EdgeStakingPool.sol#L47-L47), 


#### Recommendation

Cache the result of function calls in Solidity instead of making repeated calls to the same function. This practice significantly reduces gas consumption by minimizing costly function call operations.

### Avoid updating storage when the value hasn't changed
Manipulating storage in solidity is gas-intensive. It can be optimized by avoiding unnecessary storage updates when the new value equals the existing value. If the old value is equal to the new value, not re-storing the value will avoid a Gsreset (2900 gas), potentially at the expense of a Gcoldsload (2100 gas) or a Gwarmaccess (100 gas).

```solidity
Path: ./src/bridge/SequencerInbox.sol

852:            buffer.bufferBlocks = bufferConfig_.max;	// @audit-issue

855:            buffer.bufferBlocks = bufferConfig_.threshold;	// @audit-issue

857:        buffer.max = bufferConfig_.max;	// @audit-issue

858:        buffer.threshold = bufferConfig_.threshold;	// @audit-issue

859:        buffer.replenishRateInBasis = bufferConfig_.replenishRateInBasis;	// @audit-issue

878:        delayBlocks = uint64(maxTimeVariation_.delayBlocks);	// @audit-issue

879:        futureBlocks = uint64(maxTimeVariation_.futureBlocks);	// @audit-issue

880:        delaySeconds = uint64(maxTimeVariation_.delaySeconds);	// @audit-issue

881:        futureSeconds = uint64(maxTimeVariation_.futureSeconds);	// @audit-issue

898:        isBatchPoster[addr] = isBatchPoster_;	// @audit-issue

937:        isSequencer[addr] = isSequencer_;	// @audit-issue

943:        batchPosterManager = newBatchPosterManager;	// @audit-issue
```
[852](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/bridge/SequencerInbox.sol#L852-L852), [855](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/bridge/SequencerInbox.sol#L855-L855), [857](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/bridge/SequencerInbox.sol#L857-L857), [858](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/bridge/SequencerInbox.sol#L858-L858), [859](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/bridge/SequencerInbox.sol#L859-L859), [878](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/bridge/SequencerInbox.sol#L878-L878), [879](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/bridge/SequencerInbox.sol#L879-L879), [880](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/bridge/SequencerInbox.sol#L880-L880), [881](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/bridge/SequencerInbox.sol#L881-L881), [898](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/bridge/SequencerInbox.sol#L898-L898), [937](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/bridge/SequencerInbox.sol#L937-L937), [943](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/bridge/SequencerInbox.sol#L943-L943), 


```solidity
Path: ./src/rollup/BOLDUpgradeAction.sol

108:        preImages[h] = abi.encode(executionState, inboxMaxCount);	// @audit-issue
```
[108](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/BOLDUpgradeAction.sol#L108-L108), 


```solidity
Path: ./src/rollup/BridgeCreator.sol

54:        ethBasedTemplates = _newTemplates;	// @audit-issue

59:        erc20BasedTemplates = _newTemplates;	// @audit-issue
```
[54](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/BridgeCreator.sol#L54-L54), [59](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/BridgeCreator.sol#L59-L59), 


```solidity
Path: ./src/rollup/RollupCore.sol

228:        _assertions[assertionHash] = initialAssertion;	// @audit-issue

229:        _latestConfirmed = assertionHash;	// @audit-issue

277:        _stakerMap[stakerAddress] = Staker(depositAmount, _latestConfirmed, stakerIndex, true, withdrawalAddress);	// @audit-issue
```
[228](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/RollupCore.sol#L228-L228), [229](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/RollupCore.sol#L229-L229), [277](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/RollupCore.sol#L277-L277), 


```solidity
Path: ./src/rollup/RollupCreator.sol

73:        bridgeCreator = _bridgeCreator;	// @audit-issue

74:        osp = _osp;	// @audit-issue

75:        challengeManagerTemplate = _challengeManagerLogic;	// @audit-issue

76:        rollupAdminLogic = _rollupAdminLogic;	// @audit-issue

77:        rollupUserLogic = _rollupUserLogic;	// @audit-issue

78:        upgradeExecutorLogic = _upgradeExecutorLogic;	// @audit-issue

79:        validatorWalletCreator = _validatorWalletCreator;	// @audit-issue

80:        l2FactoriesDeployer = _l2FactoriesDeployer;	// @audit-issue
```
[73](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/RollupCreator.sol#L73-L73), [74](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/RollupCreator.sol#L74-L74), [75](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/RollupCreator.sol#L75-L75), [76](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/RollupCreator.sol#L76-L76), [77](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/RollupCreator.sol#L77-L77), [78](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/RollupCreator.sol#L78-L78), [79](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/RollupCreator.sol#L79-L79), [80](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/RollupCreator.sol#L80-L80), 


```solidity
Path: ./src/rollup/RollupAdminLogic.sol

118:        outbox = _outbox;	// @audit-issue

185:            isValidator[_validator[i]] = _val[i];	// @audit-issue

205:        minimumAssertionPeriod = newPeriod;	// @audit-issue

224:        baseStake = newBaseStake;	// @audit-issue

282:        wasmModuleRoot = newWasmModuleRoot;	// @audit-issue

300:        inbox = newInbox;	// @audit-issue

309:        validatorWhitelistDisabled = _validatorWhitelistDisabled;	// @audit-issue

318:        anyTrustFastConfirmer = _anyTrustFastConfirmer;	// @audit-issue

327:        challengeManager = IEdgeChallengeManager(_challengeManager);	// @audit-issue
```
[118](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/RollupAdminLogic.sol#L118-L118), [185](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/RollupAdminLogic.sol#L185-L185), [205](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/RollupAdminLogic.sol#L205-L205), [224](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/RollupAdminLogic.sol#L224-L224), [282](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/RollupAdminLogic.sol#L282-L282), [300](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/RollupAdminLogic.sol#L300-L300), [309](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/RollupAdminLogic.sol#L309-L309), [318](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/RollupAdminLogic.sol#L318-L318), [327](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/RollupAdminLogic.sol#L327-L327), 


#### Recommendation

Optimize gas usage by avoiding storage updates in Solidity when the new value is the same as the existing one. This prevents unnecessary gas expenditure from storage resets, balancing the cost against cold or warm storage access as needed.

### Avoid zero transfers calls
In Solidity, unnecessary operations can waste gas. For example, a transfer function without a zero amount check uses gas even if called with a zero amount, since the contract state remains unchanged. Implementing a zero amount check avoids these unnecessary function calls, saving gas and improving efficiency.

```solidity
Path: ./src/rollup/RollupUserLogic.sol

367:        IERC20(stakeToken).safeTransferFrom(msg.sender, address(this), tokenAmount);	// @audit-issue
```
[367](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/RollupUserLogic.sol#L367-L367), 


#### Recommendation

Include a condition in your transfer functions to check for and prevent zero-value transfers. Implement a `require(amount > 0, "Transfer amount must be greater than zero");` statement at the beginning of the function. This preemptive check ensures that the function only proceeds with non-zero transfer amounts, avoiding wasteful operations and saving gas. Apply this optimization across all functions involving token transfers or similar operations to improve your contract's gas efficiency and operational effectiveness.

### Empty Blocks Should Be Removed Or Emit Something
The code should be refactored such that empty blocks no longer exist, or the block should do something useful, such as emitting an event or reverting. Empty blocks can introduce confusion and potential errors when the code is modified in the future.


```solidity
Path: ./src/bridge/SequencerInbox.sol

192:        } catch {}	// @audit-issue
```
[192](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/bridge/SequencerInbox.sol#L192-L192), 


```solidity
Path: ./src/rollup/RollupAdminLogic.sol

166:    function _authorizeUpgrade(address newImplementation) internal override {}	// @audit-issue

171:    function _authorizeSecondaryUpgrade(address newImplementation) internal override {}	// @audit-issue
```
[166](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/RollupAdminLogic.sol#L166-L166), [171](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/RollupAdminLogic.sol#L171-L171), 


```solidity
Path: ./src/challengeV2/libraries/EdgeChallengeManagerLib.sol

186:        } else {	// @audit-issue
187:            // after we've stored the first rival we dont need to keep a record of any
188:            // other rival edges - they will all have a zero time unrivaled
189:        }
```
[186](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/challengeV2/libraries/EdgeChallengeManagerLib.sol#L186-L189), 


#### Recommendation

Remove empty blocks in Solidity code to avoid confusion and potential errors. If a block is necessary, ensure it performs a useful action, like emitting an event or reverting, to justify its presence and clarify its purpose.

### Overridden function has no body
In Solidity, when a function is overridden from a base contract, it's expected to have its own implementation or body. However, there are cases where an overridden function is left with an empty body, either intentionally or due to oversight. An empty body in an overridden function can be misleading and might indicate an incomplete implementation. If the function is intentionally left empty (for instance, in cases of interface adherence or specific design patterns), this should be clearly documented. Otherwise, it should be provided with a proper implementation to ensure the contract's functionality aligns with its intended design and behavior.

```solidity
Path: ./src/rollup/RollupAdminLogic.sol

166:    function _authorizeUpgrade(address newImplementation) internal override {}	// @audit-issue

171:    function _authorizeSecondaryUpgrade(address newImplementation) internal override {}	// @audit-issue
```
[166](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/RollupAdminLogic.sol#L166-L166), [171](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/RollupAdminLogic.sol#L171-L171), 


#### Recommendation

Review all overridden functions in your Solidity contracts to ensure they have appropriate implementations. If an overridden function is intentionally left empty, include clear comments explaining the rationale. This approach prevents confusion and ensures that the contract's design and purpose are accurately conveyed. For functions that require an implementation, provide a meaningful body that aligns with the contract's intended functionality and the expectations set by the base contract or interface.

### Functions guaranteed to `revert` when called by normal users can be marked `payable`
If a function modifier such as `onlyOwner` is used, the function will revert if a normal user tries to pay the function. Marking the function as `payable` will lower the gas cost for legitimate callers because the compiler will not include checks for whether a payment was provided.

```solidity
Path: ./src/bridge/SequencerInbox.sol

161:    function postUpgradeInit(BufferConfig memory bufferConfig_)	// @audit-issue

177:    function initialize(	// @audit-issue

885:    function setMaxTimeVariation(ISequencerInbox.MaxTimeVariation memory maxTimeVariation_)	// @audit-issue

894:    function setIsBatchPoster(address addr, bool isBatchPoster_)	// @audit-issue

903:    function setValidKeyset(bytes calldata keysetBytes) external onlyRollupOwner {	// @audit-issue

922:    function invalidateKeysetHash(bytes32 ksHash) external onlyRollupOwner {	// @audit-issue

933:    function setIsSequencer(address addr, bool isSequencer_)	// @audit-issue

942:    function setBatchPosterManager(address newBatchPosterManager) external onlyRollupOwner {	// @audit-issue

947:    function setBufferConfig(BufferConfig memory bufferConfig_) external onlyRollupOwner {	// @audit-issue
```
[161](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/bridge/SequencerInbox.sol#L161-L161), [177](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/bridge/SequencerInbox.sol#L177-L177), [885](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/bridge/SequencerInbox.sol#L885-L885), [894](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/bridge/SequencerInbox.sol#L894-L894), [903](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/bridge/SequencerInbox.sol#L903-L903), [922](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/bridge/SequencerInbox.sol#L922-L922), [933](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/bridge/SequencerInbox.sol#L933-L933), [942](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/bridge/SequencerInbox.sol#L942-L942), [947](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/bridge/SequencerInbox.sol#L947-L947), 


```solidity
Path: ./src/rollup/BridgeCreator.sol

53:    function updateTemplates(BridgeTemplates calldata _newTemplates) external onlyOwner {	// @audit-issue

58:    function updateERC20Templates(BridgeTemplates calldata _newTemplates) external onlyOwner {	// @audit-issue
```
[53](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/BridgeCreator.sol#L53-L53), [58](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/BridgeCreator.sol#L58-L58), 


```solidity
Path: ./src/rollup/RollupUserLogic.sol

27:    function initialize(address _stakeToken) external view override onlyProxy {	// @audit-issue

82:    function confirmAssertion(	// @audit-issue

137:    function _newStake(uint256 depositAmount, address withdrawalAddress) internal onlyValidator whenNotPaused {	// @audit-issue

163:    function stakeOnNewAssertion(AssertionInputs calldata assertion, bytes32 expectedAssertionHash)	// @audit-issue

222:    function returnOldDeposit() external override onlyValidator whenNotPaused {	// @audit-issue

232:    function _addToDeposit(address stakerAddress, uint256 depositAmount) internal onlyValidator whenNotPaused {	// @audit-issue

241:    function reduceDeposit(uint256 target) external onlyValidator whenNotPaused {	// @audit-issue

349:    function addToDeposit(address stakerAddress, uint256 tokenAmount) external onlyValidator whenNotPaused {	// @audit-issue
```
[27](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/RollupUserLogic.sol#L27-L27), [82](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/RollupUserLogic.sol#L82-L82), [137](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/RollupUserLogic.sol#L137-L137), [163](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/RollupUserLogic.sol#L163-L163), [222](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/RollupUserLogic.sol#L222-L222), [232](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/RollupUserLogic.sol#L232-L232), [241](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/RollupUserLogic.sol#L241-L241), [349](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/RollupUserLogic.sol#L349-L349), 


```solidity
Path: ./src/rollup/RollupCreator.sol

63:    function setTemplates(	// @audit-issue
```
[63](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/RollupCreator.sol#L63-L63), 


```solidity
Path: ./src/rollup/RollupAdminLogic.sol

18:    function initialize(Config calldata config, ContractDependencies calldata connectedContracts)	// @audit-issue
```
[18](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/RollupAdminLogic.sol#L18-L18), 


#### Recommendation

Mark functions with access restrictions like 'onlyOwner' as 'payable' in Solidity. This reduces gas costs for legitimate callers by removing the compiler's checks for incoming payments, as the function will revert for unauthorized users anyway.

### `abi.encode()` is less efficient than `abi.encodePacked()`
When working with Solidity, it is important to pay attention to gas efficiency in order to optimize smart contracts. In this blog post, we will compare the gas costs of `abi.encode()` and `abi.encodepacked()` and explore why the latter is more efficient.Source: [reference](https://github.com/ConnorBlockchain/Solidity-Encode-Gas-Comparison)


```solidity
Path: ./src/rollup/BOLDUpgradeAction.sol

108:        preImages[h] = abi.encode(executionState, inboxMaxCount);	// @audit-issue

498:        bytes32 rollupSalt = keccak256(abi.encode(config));	// @audit-issue
```
[108](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/BOLDUpgradeAction.sol#L108-L108), [498](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/BOLDUpgradeAction.sol#L498-L498), 


```solidity
Path: ./src/rollup/AssertionState.sol

23:        return keccak256(abi.encode(state));	// @audit-issue
```
[23](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/AssertionState.sol#L23-L23), 


```solidity
Path: ./src/rollup/RollupCreator.sol

188:        RollupProxy rollup = new RollupProxy{salt: keccak256(abi.encode(deployParams))}();	// @audit-issue
```
[188](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/RollupCreator.sol#L188-L188), 


```solidity
Path: ./src/assertionStakingPool/AssertionStakingPoolCreator.sol

32:                abi.encode(_rollup, _assertionHash)	// @audit-issue
```
[32](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/assertionStakingPool/AssertionStakingPoolCreator.sol#L32-L32), 


```solidity
Path: ./src/assertionStakingPool/EdgeStakingPoolCreator.sol

32:                abi.encode(challengeManager, edgeId)	// @audit-issue
```
[32](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/assertionStakingPool/EdgeStakingPoolCreator.sol#L32-L32), 


#### Recommendation

Optimize gas usage by preferring 'abi.encodePacked()' over 'abi.encode()' where appropriate, as 'abi.encodePacked()' is generally more gas-efficient. However, ensure its suitability based on the data type and structure requirements, as 'abi.encodePacked()' can lead to ambiguity in certain cases.

### Multiple mappings can be replaced with a single struct mapping
Saves a storage slot for the mapping. Depending on the circumstances and sizes of types, can avoid a Gsset (20000 gas) per mapping combined. Reads and subsequent writes can also be cheaper when a function requires both values and they both fit in the same storage slot. Finally, if both fields are accessed in the same function, can save ~42 gas per access due to [not having to recalculate the key's keccak256 hash](https://gist.github.com/IllIllI000/ec23a57daa30a8f8ca8b9681c8ccefb0) (Gkeccak256 - 30 gas) and that calculation's associated stack operations.

```solidity
Path: ./src/bridge/SequencerInbox.sol

115:    mapping(address => bool) public isSequencer;	// @audit-issue: Can be combined with: 
	 isBatchPoster in SequencerInbox at line: 95
```
[115](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/bridge/SequencerInbox.sol#L115-L115), 


#### Recommendation

Refactor your Solidity contracts to replace multiple related mappings with a single mapping that uses a struct. This struct should contain all the fields that were previously in separate mappings. This consolidation optimizes storage usage by reducing the number of storage slots and hash computations required, leading to significant gas savings. Ensure that the fields within the struct are logically related and frequently accessed or modified together. This strategy is most effective when the size of struct fields allows them to fit within a single storage slot, maximizing the benefits of the EVM's storage packing capabilities.

### Assigning state variables directly with named struct constructors wastes gas
Using named arguments for struct means that the compiler needs to organize the fields in memory before doing the assignment, which wastes gas. Set each field directly in storage (use dot-notation), or use the unnamed version of the constructor.

```solidity
Path: ./src/bridge/SequencerInbox.sol

913:        dasKeySetInfo[ksHash] = DasKeySetInfo({	// @audit-issue
914:            isValidKeyset: true,
915:            creationBlock: uint64(creationBlock)
916:        });
```
[913](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/bridge/SequencerInbox.sol#L913-L916), 


#### Recommendation

Avoid using named arguments in struct constructors for state variable assignments in Solidity. Opt for direct field assignments using dot-notation or use unnamed struct constructors. This approach reduces unnecessary memory operations, thereby saving gas. Carefully assess struct assignments in your contract and refactor them to adopt this more gas-efficient method, especially in contracts with high-frequency struct manipulations.

### `x += y` costs more gas than `x = x + y` for stack variables
Not inlining costs 20 to 40 gas because of two extra JUMP instructions and additional stack operations needed for function calls.

```solidity
Path: ./src/bridge/SequencerInbox.sol

771:            extraGas += l1Fees / block.basefee;	// @audit-issue
```
[771](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/bridge/SequencerInbox.sol#L771-L771), 


```solidity
Path: ./src/bridge/DelayBuffer.sol

46:        buffer += (elapsed * replenishRateInBasis) / BASIS;	// @audit-issue

55:            buffer -= unexpectedDelay;	// @audit-issue
```
[46](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/bridge/DelayBuffer.sol#L46-L46), [55](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/bridge/DelayBuffer.sol#L55-L55), 


```solidity
Path: ./src/rollup/RollupAdminLogic.sol

74:            currentInboxCount += 1;	// @audit-issue
```
[74](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/RollupAdminLogic.sol#L74-L74), 


```solidity
Path: ./src/challengeV2/libraries/EdgeChallengeManagerLib.sol

493:            totalTimeUnrivaled += lowerTimer < upperTimer ? lowerTimer : upperTimer;	// @audit-issue

529:        totalTimeUnrivaled += store.edges[claimingEdgeId].totalTimeUnrivaledCache;	// @audit-issue

739:        totalTimeUnrivaled += claimedAssertionUnrivaledBlocks;	// @audit-issue

805:                machineStep += stepSize * store.edges[cursor].startHeight;	// @audit-issue

807:                stepSize *= bigStepHeight;	// @audit-issue
```
[493](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/challengeV2/libraries/EdgeChallengeManagerLib.sol#L493-L493), [529](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/challengeV2/libraries/EdgeChallengeManagerLib.sol#L529-L529), [739](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/challengeV2/libraries/EdgeChallengeManagerLib.sol#L739-L739), [805](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/challengeV2/libraries/EdgeChallengeManagerLib.sol#L805-L805), [807](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/challengeV2/libraries/EdgeChallengeManagerLib.sol#L807-L807), 


```solidity
Path: ./src/challengeV2/libraries/MerkleTreeLib.sol

296:                sum += 2 ** i;	// @audit-issue

339:            size += numLeaves;	// @audit-issue
```
[296](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/challengeV2/libraries/MerkleTreeLib.sol#L296-L296), [339](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/challengeV2/libraries/MerkleTreeLib.sol#L339-L339), 


#### Recommendation

Prefer using 'x = x + y' over 'x += y' for state variable assignments in Solidity to save gas. The latter incurs extra costs due to additional JUMP instructions and stack operations associated with non-inlined function calls.

### Use calldata instead of memory for function arguments that do not get mutated
Mark data types as `calldata` instead of `memory` where possible. This makes it so that the data is not automatically loaded into memory. If the data passed into the function does not need to be changed (like updating values in an array), it can be passed in as `calldata`. The one exception to this is if the argument must later be passed into another function that takes an argument that specifies `memory` storage.

```solidity
Path: ./src/bridge/SequencerInbox.sol

161:    function postUpgradeInit(BufferConfig memory bufferConfig_)	// @audit-issue

177:    function initialize(
178:        IBridge bridge_,
179:        ISequencerInbox.MaxTimeVariation calldata maxTimeVariation_,
180:        BufferConfig memory bufferConfig_	// @audit-issue
181:    ) external onlyDelegated {

605:    function delayProofImpl(uint256 afterDelayedMessagesRead, DelayProof memory delayProof)	// @audit-issue

847:    function _setBufferConfig(BufferConfig memory bufferConfig_) internal {	// @audit-issue

867:    function _setMaxTimeVariation(ISequencerInbox.MaxTimeVariation memory maxTimeVariation_)	// @audit-issue

885:    function setMaxTimeVariation(ISequencerInbox.MaxTimeVariation memory maxTimeVariation_)	// @audit-issue

947:    function setBufferConfig(BufferConfig memory bufferConfig_) external onlyRollupOwner {	// @audit-issue
```
[161](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/bridge/SequencerInbox.sol#L161-L161), [180](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/bridge/SequencerInbox.sol#L177-L181), [605](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/bridge/SequencerInbox.sol#L605-L605), [847](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/bridge/SequencerInbox.sol#L847-L847), [867](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/bridge/SequencerInbox.sol#L867-L867), [885](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/bridge/SequencerInbox.sol#L885-L885), [947](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/bridge/SequencerInbox.sol#L947-L947), 


```solidity
Path: ./src/bridge/DelayBuffer.sol

115:    function isValidBufferConfig(BufferConfig memory config) internal pure returns (bool) {	// @audit-issue
```
[115](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/bridge/DelayBuffer.sol#L115-L115), 


```solidity
Path: ./src/rollup/RollupLib.sol

23:    function assertionHash(
24:        bytes32 parentAssertionHash,
25:        AssertionState memory afterState,	// @audit-issue
26:        bytes32 inboxAcc
27:    ) internal pure returns (bytes32) {
```
[25](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/RollupLib.sol#L23-L27), 


```solidity
Path: ./src/rollup/BOLDUpgradeAction.sol

169:    constructor(uint256[] memory __array) {	// @audit-issue

287:    constructor(
288:        Contracts memory contracts,	// @audit-issue
289:        ProxyAdmins memory proxyAdmins,
290:        Implementations memory implementations,
291:        Settings memory settings
292:    ) {

287:    constructor(
288:        Contracts memory contracts,
289:        ProxyAdmins memory proxyAdmins,	// @audit-issue
290:        Implementations memory implementations,
291:        Settings memory settings
292:    ) {

287:    constructor(
288:        Contracts memory contracts,
289:        ProxyAdmins memory proxyAdmins,
290:        Implementations memory implementations,	// @audit-issue
291:        Settings memory settings
292:    ) {

287:    constructor(
288:        Contracts memory contracts,
289:        ProxyAdmins memory proxyAdmins,
290:        Implementations memory implementations,
291:        Settings memory settings	// @audit-issue
292:    ) {

464:    function perform(address[] memory validators) external {	// @audit-issue
```
[169](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/BOLDUpgradeAction.sol#L169-L169), [288](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/BOLDUpgradeAction.sol#L287-L292), [289](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/BOLDUpgradeAction.sol#L287-L292), [290](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/BOLDUpgradeAction.sol#L287-L292), [291](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/BOLDUpgradeAction.sol#L287-L292), [464](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/BOLDUpgradeAction.sol#L464-L464), 


```solidity
Path: ./src/rollup/Assertion.sol

93:    function requireExists(AssertionNode memory self) internal pure {	// @audit-issue
```
[93](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/Assertion.sol#L93-L93), 


```solidity
Path: ./src/rollup/AssertionState.sol

18:    function toExecutionState(AssertionState memory state) internal pure returns (ExecutionState memory) {	// @audit-issue

22:    function hash(AssertionState memory state) internal pure returns (bytes32) {	// @audit-issue
```
[18](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/AssertionState.sol#L18-L18), [22](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/AssertionState.sol#L22-L22), 


```solidity
Path: ./src/rollup/BridgeCreator.sol

45:    constructor(
46:        BridgeTemplates memory _ethBasedTemplates,	// @audit-issue
47:        BridgeTemplates memory _erc20BasedTemplates
48:    ) Ownable() {

45:    constructor(
46:        BridgeTemplates memory _ethBasedTemplates,
47:        BridgeTemplates memory _erc20BasedTemplates	// @audit-issue
48:    ) Ownable() {

63:    function _createBridge(
64:        address adminProxy,
65:        BridgeTemplates memory templates,	// @audit-issue
66:        bool isDelayBufferable
67:    ) internal returns (BridgeContracts memory) {
```
[46](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/BridgeCreator.sol#L45-L48), [47](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/BridgeCreator.sol#L45-L48), [65](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/BridgeCreator.sol#L63-L67), 


```solidity
Path: ./src/rollup/RollupCore.sol

225:    function initializeCore(AssertionNode memory initialAssertion, bytes32 assertionHash) internal {	// @audit-issue
```
[225](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/RollupCore.sol#L225-L225), 


```solidity
Path: ./src/rollup/RollupCreator.sol

85:    function createChallengeManager(address rollupAddr, address proxyAdminAddr, Config memory config)	// @audit-issue

137:    function createRollup(RollupDeploymentParams memory deployParams)	// @audit-issue
```
[85](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/RollupCreator.sol#L85-L85), [137](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/RollupCreator.sol#L137-L137), 


```solidity
Path: ./src/rollup/RollupProxy.sol

12:    function initializeProxy(Config memory config, ContractDependencies memory connectedContracts)	// @audit-issue
```
[12](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/RollupProxy.sol#L12-L12), 


```solidity
Path: ./src/challengeV2/libraries/ArrayUtilsLib.sol

13:    function append(bytes32[] memory arr, bytes32 newItem) internal pure returns (bytes32[] memory) {	// @audit-issue

27:    function slice(bytes32[] memory arr, uint256 startIndex, uint256 endIndex)	// @audit-issue

45:    function concat(bytes32[] memory arr1, bytes32[] memory arr2) internal pure returns (bytes32[] memory) {	// @audit-issue
```
[13](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/challengeV2/libraries/ArrayUtilsLib.sol#L13-L13), [27](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/challengeV2/libraries/ArrayUtilsLib.sol#L27-L27), [45](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/challengeV2/libraries/ArrayUtilsLib.sol#L45-L45), 


```solidity
Path: ./src/challengeV2/libraries/EdgeChallengeManagerLib.sol

160:    function add(EdgeStore storage store, ChallengeEdge memory edge) internal returns (EdgeAddedData memory) {	// @audit-issue

213:    function layerZeroTypeSpecificChecks(
214:        EdgeStore storage store,
215:        CreateEdgeArgs calldata args,
216:        AssertionReferenceData memory ard,	// @audit-issue
217:        IOneStepProofEntry oneStepProofEntry,
218:        uint8 numBigStepLevel
219:    ) private view returns (ProofData memory, bytes32) {

344:    function layerZeroCommonChecks(ProofData memory proofData, CreateEdgeArgs calldata args, uint256 expectedEndHeight)	// @audit-issue

411:    function createLayerZeroEdge(
412:        EdgeStore storage store,
413:        CreateEdgeArgs calldata args,
414:        AssertionReferenceData memory ard,	// @audit-issue
415:        IOneStepProofEntry oneStepProofEntry,
416:        uint256 expectedEndHeight,
417:        uint8 numBigStepLevel,
418:        bool whitelistEnabled
419:    ) internal returns (EdgeAddedData memory) {

604:    function bisectEdge(EdgeStore storage store, bytes32 edgeId, bytes32 bisectionHistoryRoot, bytes memory prefixProof)	// @audit-issue

766:    function confirmEdgeByOneStepProof(
767:        EdgeStore storage store,
768:        bytes32 edgeId,
769:        IOneStepProofEntry oneStepProofEntry,
770:        OneStepData calldata oneStepData,
771:        ExecutionContext memory execCtx,	// @audit-issue
772:        bytes32[] calldata beforeHistoryInclusionProof,
773:        bytes32[] calldata afterHistoryInclusionProof,
774:        uint8 numBigStepLevel,
775:        uint256 bigStepHeight,
776:        uint256 smallStepHeight
777:    ) internal {
```
[160](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/challengeV2/libraries/EdgeChallengeManagerLib.sol#L160-L160), [216](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/challengeV2/libraries/EdgeChallengeManagerLib.sol#L213-L219), [344](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/challengeV2/libraries/EdgeChallengeManagerLib.sol#L344-L344), [414](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/challengeV2/libraries/EdgeChallengeManagerLib.sol#L411-L419), [604](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/challengeV2/libraries/EdgeChallengeManagerLib.sol#L604-L604), [771](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/challengeV2/libraries/EdgeChallengeManagerLib.sol#L766-L777), 


```solidity
Path: ./src/challengeV2/libraries/MerkleTreeLib.sol

110:    function root(bytes32[] memory me) internal pure returns (bytes32) {	// @audit-issue

151:    function appendCompleteSubTree(bytes32[] memory me, uint256 level, bytes32 subtreeRoot)	// @audit-issue

238:    function appendLeaf(bytes32[] memory me, bytes32 leaf) internal pure returns (bytes32[] memory) {	// @audit-issue

292:    function treeSize(bytes32[] memory me) internal pure returns (uint256) {	// @audit-issue

312:    function verifyPrefixProof(
313:        bytes32 preRoot,
314:        uint256 preSize,
315:        bytes32 postRoot,
316:        uint256 postSize,
317:        bytes32[] memory preExpansion,	// @audit-issue
318:        bytes32[] memory proof
319:    ) internal pure {

312:    function verifyPrefixProof(
313:        bytes32 preRoot,
314:        uint256 preSize,
315:        bytes32 postRoot,
316:        uint256 postSize,
317:        bytes32[] memory preExpansion,
318:        bytes32[] memory proof	// @audit-issue
319:    ) internal pure {

359:    function verifyInclusionProof(bytes32 rootHash, bytes32 leaf, uint256 index, bytes32[] memory proof)	// @audit-issue
```
[110](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/challengeV2/libraries/MerkleTreeLib.sol#L110-L110), [151](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/challengeV2/libraries/MerkleTreeLib.sol#L151-L151), [238](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/challengeV2/libraries/MerkleTreeLib.sol#L238-L238), [292](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/challengeV2/libraries/MerkleTreeLib.sol#L292-L292), [317](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/challengeV2/libraries/MerkleTreeLib.sol#L312-L319), [318](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/challengeV2/libraries/MerkleTreeLib.sol#L312-L319), [359](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/challengeV2/libraries/MerkleTreeLib.sol#L359-L359), 


```solidity
Path: ./src/challengeV2/libraries/ChallengeEdgeLib.sol

184:    function mutualIdMem(ChallengeEdge memory ce) internal pure returns (bytes32) {	// @audit-issue

208:    function idMem(ChallengeEdge memory edge) internal pure returns (bytes32) {	// @audit-issue
```
[184](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/challengeV2/libraries/ChallengeEdgeLib.sol#L184-L184), [208](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/challengeV2/libraries/ChallengeEdgeLib.sol#L208-L208), 


```solidity
Path: ./src/assertionStakingPool/StakingPoolCreatorUtils.sol

13:    function getPool(bytes memory creationCode, bytes memory args) internal view returns (address) {	// @audit-issue
```
[13](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/assertionStakingPool/StakingPoolCreatorUtils.sol#L13-L13), 


#### Recommendation

To optimize gas usage in your Solidity functions, mark data types as `calldata` instead of `memory` wherever applicable. This prevents unnecessary data loading into memory. Use `calldata` for function arguments that do not require changes within the function, except when passing them into another function that explicitly requires `memory` storage.

### Nesting `if` statements that uses `&&` saves gas
In Solidity, the way conditional checks are structured can impact the gas consumption of a transaction. When conditions are combined using `&&` within an `if` statement, Solidity short-circuits the evaluation, meaning that if the first condition is `false`, the subsequent conditions won't be evaluated. This behavior can lead to gas savings compared to using separate nested `if` statements because not all conditions might need to be checked every time. By efficiently structuring these conditional checks, contracts can optimize the gas required for execution, leading to reduced costs for users.


```solidity
Path: ./src/bridge/SequencerInbox.sol

109:        if (msg.sender != rollup.owner() && msg.sender != batchPosterManager) {	// @audit-issue

484:        if (seqMessageIndex != sequenceNumber && sequenceNumber != ~uint256(0)) {	// @audit-issue

507:        if (msg.sender == tx.origin && !isUsingFeeToken) {	// @audit-issue

538:        if (seqMessageIndex != sequenceNumber && sequenceNumber != ~uint256(0)) {	// @audit-issue

568:        if (!isBatchPoster[msg.sender] && msg.sender != address(rollup)) revert NotBatchPoster();	// @audit-issue

591:        if (!isBatchPoster[msg.sender] && msg.sender != address(rollup)) revert NotBatchPoster();	// @audit-issue

711:            if (data[0] & DAS_MESSAGE_HEADER_FLAG != 0 && data.length >= 33) {	// @audit-issue

818:        if (calldataLengthPosted > 0 && !isUsingFeeToken) {	// @audit-issue
```
[109](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/bridge/SequencerInbox.sol#L109-L109), [484](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/bridge/SequencerInbox.sol#L484-L484), [507](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/bridge/SequencerInbox.sol#L507-L507), [538](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/bridge/SequencerInbox.sol#L538-L538), [568](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/bridge/SequencerInbox.sol#L568-L568), [591](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/bridge/SequencerInbox.sol#L591-L591), [711](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/bridge/SequencerInbox.sol#L711-L711), [818](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/bridge/SequencerInbox.sol#L818-L818), 


```solidity
Path: ./src/rollup/BOLDUpgradeAction.sol

353:            if (staker.isStaked && staker.currentChallenge == 0) {	// @audit-issue
```
[353](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/BOLDUpgradeAction.sol#L353-L353), 


```solidity
Path: ./src/rollup/RollupCore.sol

429:            if (assertion.afterState.machineStatus != MachineStatus.ERRORED && afterStateCmpMaxInbox < 0) {	// @audit-issue
```
[429](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/RollupCore.sol#L429-L429), 


```solidity
Path: ./src/rollup/RollupProxy.sol

16:            _getAdmin() == address(0) &&	// @audit-issue
17:            _getImplementation() == address(0) &&
18:            _getSecondaryImplementation() == address(0)
```
[16](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/RollupProxy.sol#L16-L18), 


```solidity
Path: ./src/challengeV2/EdgeChallengeManager.sol

376:        if (whitelistEnabled && !assertionChain.isValidator(msg.sender)) {	// @audit-issue

429:        if (address(st) != address(0) && sa != 0) {	// @audit-issue

522:        if (isBlockLevel && assertionChain.isFirstChild(topEdge.claimId)) {	// @audit-issue

580:        if (address(st) != address(0) && sa != 0) {	// @audit-issue
```
[376](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/challengeV2/EdgeChallengeManager.sol#L376-L376), [429](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/challengeV2/EdgeChallengeManager.sol#L429-L429), [522](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/challengeV2/EdgeChallengeManager.sol#L522-L522), [580](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/challengeV2/EdgeChallengeManager.sol#L580-L580), 


#### Recommendation


When multiple conditions need to be checked successively, try to combine them in a single `if` statement using `&&` instead of nesting separate `if` statements. This will leverage short-circuit evaluation for potential gas savings.


### Use `!= 0` Instead of `> 0` for Unsigned Integer Comparison
In Solidity, unsigned integers (e.g., `uint256`, `uint8`, etc.) represent non-negative whole numbers, ranging from 0 to a maximum value determined by their bit size. When performing comparisons on these numbers, especially to check if they are non-zero, developers have options. A common practice is to compare against zero using the `>` operator, as in `value > 0`. However, given the nature of unsigned integers, a more straightforward and slightly gas-efficient comparison is to use the `!=` operator, as in `value != 0`.

The primary rationale is that the `!=` comparison directly checks for non-equality, whereas the `>` comparison checks if one value is strictly greater than another. For unsigned integers, where negative values don't exist, the `!= 0` check is both semantically clearer and potentially more efficient at the EVM bytecode level.


```solidity
Path: ./src/bridge/SequencerInbox.sol

702:        if (data.length > 0) {	// @audit-issue

746:            block.basefee > 0 ? blobCost / block.basefee : 0	// @audit-issue

818:        if (calldataLengthPosted > 0 && !isUsingFeeToken) {	// @audit-issue
```
[702](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/bridge/SequencerInbox.sol#L702-L702), [746](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/bridge/SequencerInbox.sol#L746-L746), [818](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/bridge/SequencerInbox.sol#L818-L818), 


```solidity
Path: ./src/rollup/RollupCore.sol

148:            require(blockNum > 0, "NO_ASSERTION");	// @audit-issue

433:                require(afterGS.comparePositions(beforeGS) > 0, "OVERFLOW_STANDSTILL");	// @audit-issue

572:        bool haveChild = getAssertionStorage(lastestAssertion).firstChildBlock > 0;	// @audit-issue
```
[148](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/RollupCore.sol#L148-L148), [433](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/RollupCore.sol#L433-L433), [572](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/RollupCore.sol#L572-L572), 


```solidity
Path: ./src/rollup/RollupUserLogic.sol

56:        if (latestConfirmedAssertion.firstChildBlock > 0) {	// @audit-issue

115:        if (prevAssertion.secondChildBlock > 0) {	// @audit-issue

196:            lastAssertion == prevAssertion || getAssertionStorage(lastAssertion).firstChildBlock > 0,	// @audit-issue

360:        require(amount > 0, "NO_FUNDS_TO_WITHDRAW");	// @audit-issue
```
[56](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/RollupUserLogic.sol#L56-L56), [115](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/RollupUserLogic.sol#L115-L115), [196](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/RollupUserLogic.sol#L196-L196), [360](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/RollupUserLogic.sol#L360-L360), 


```solidity
Path: ./src/rollup/RollupAdminLogic.sol

181:        require(_validator.length > 0, "EMPTY_ARRAY");	// @audit-issue

214:        require(newConfirmPeriod > 0, "INVALID_CONFIRM_PERIOD");	// @audit-issue

229:        require(staker.length > 0, "EMPTY_ARRAY");	// @audit-issue
```
[181](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/RollupAdminLogic.sol#L181-L181), [214](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/RollupAdminLogic.sol#L214-L214), [229](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/RollupAdminLogic.sol#L229-L229), 


```solidity
Path: ./src/challengeV2/EdgeChallengeManager.sol

412:                assertionChain.getSecondChildCreationBlock(claimStateData.prevAssertionHash) > 0,	// @audit-issue
```
[412](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/challengeV2/EdgeChallengeManager.sol#L412-L412), 


```solidity
Path: ./src/challengeV2/libraries/EdgeChallengeManagerLib.sol

445:        while (edge.level > 0) {	// @audit-issue
```
[445](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/challengeV2/libraries/EdgeChallengeManagerLib.sol#L445-L445), 


```solidity
Path: ./src/challengeV2/libraries/MerkleTreeLib.sol

111:        require(me.length > 0, "Empty merkle expansion");	// @audit-issue

320:        require(preSize > 0, "Pre-size cannot be 0");	// @audit-issue
```
[111](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/challengeV2/libraries/MerkleTreeLib.sol#L111-L111), [320](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/challengeV2/libraries/MerkleTreeLib.sol#L320-L320), 


```solidity
Path: ./src/challengeV2/libraries/UintUtilsLib.sol

15:        require(x > 0, "Zero has no significant bits");	// @audit-issue
```
[15](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/challengeV2/libraries/UintUtilsLib.sol#L15-L15), 


#### Recommendation

Use '!= 0' instead of '> 0' for comparing unsigned integers in Solidity. This is semantically clearer and slightly more gas-efficient, as it directly checks for non-zero values without considering unnecessary relational comparisons.

### Operator `>=`/`<=` costs less gas than operator `>`/`<`
The compiler uses opcodes `GT` and `ISZERO` for code that uses `>`, but only requires `LT` for `>=`. A similar behaviour applies for `>`, which uses opcodes `LT` and `ISZERO`, but only requires `GT` for `<=`.


```solidity
Path: ./src/bridge/SequencerInbox.sol

318:        if (_totalDelayedMessagesRead > 1) {	// @audit-issue
```
[318](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/bridge/SequencerInbox.sol#L318-L318), 


```solidity
Path: ./src/rollup/BOLDUpgradeAction.sol

347:        if (stakerCount > 50) {	// @audit-issue
```
[347](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/BOLDUpgradeAction.sol#L347-L347), 


```solidity
Path: ./src/challengeV2/EdgeChallengeManager.sol

355:        if (_numBigStepLevel > 253) {	// @audit-issue
```
[355](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/challengeV2/EdgeChallengeManager.sol#L355-L355), 


```solidity
Path: ./src/challengeV2/libraries/EdgeChallengeManagerLib.sol

577:        if (end - start < 2) {	// @audit-issue

800:            while (store.edges[cursor].level > 1) {	// @audit-issue
```
[577](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/challengeV2/libraries/EdgeChallengeManagerLib.sol#L577-L577), [800](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/challengeV2/libraries/EdgeChallengeManagerLib.sol#L800-L800), 


#### Recommendation

Opt for '>=', '<=' operators over '>' and '<' in Solidity where logically appropriate, as they consume less gas. This is because '>=' and '<=' require only one opcode ('LT' or 'GT'), compared to the two opcodes ('GT'/'LT' and 'ISZERO') needed for '>' and '<'.

### Constructor Can Be Marked As Payable
`payable` functions cost less gas to execute, since the compiler does not have to add extra checks to ensure that a payment wasn't provided.

A `constructor` can safely be marked as `payable`, since only the deployer would be able to pass funds, and the project itself would not pass any funds.



```solidity
Path: ./src/bridge/SequencerInbox.sol

140:    constructor(	// @audit-issue
```
[140](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/bridge/SequencerInbox.sol#L140-L140), 


```solidity
Path: ./src/rollup/BOLDUpgradeAction.sol

126:    constructor(IOldRollup _rollup) {	// @audit-issue

169:    constructor(uint256[] memory __array) {	// @audit-issue

287:    constructor(	// @audit-issue
```
[126](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/BOLDUpgradeAction.sol#L126-L126), [169](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/BOLDUpgradeAction.sol#L169-L169), [287](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/BOLDUpgradeAction.sol#L287-L287), 


```solidity
Path: ./src/rollup/BridgeCreator.sol

45:    constructor(	// @audit-issue
```
[45](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/BridgeCreator.sol#L45-L45), 


```solidity
Path: ./src/rollup/RollupCreator.sol

58:    constructor() Ownable() {}	// @audit-issue
```
[58](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/RollupCreator.sol#L58-L58), 


```solidity
Path: ./src/challengeV2/EdgeChallengeManager.sol

300:    constructor() {	// @audit-issue
```
[300](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/challengeV2/EdgeChallengeManager.sol#L300-L300), 


```solidity
Path: ./src/assertionStakingPool/EdgeStakingPool.sol

35:    constructor(	// @audit-issue
```
[35](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/assertionStakingPool/EdgeStakingPool.sol#L35-L35), 


```solidity
Path: ./src/assertionStakingPool/AssertionStakingPool.sol

31:    constructor(	// @audit-issue
```
[31](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/assertionStakingPool/AssertionStakingPool.sol#L31-L31), 


```solidity
Path: ./src/assertionStakingPool/AbsBoldStakingPool.sol

24:    constructor(address _stakeToken) {	// @audit-issue
```
[24](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/assertionStakingPool/AbsBoldStakingPool.sol#L24-L24), 


#### Recommendation

Mark constructors as 'payable' in Solidity contracts to reduce gas costs, as this eliminates the need for the compiler to add checks against incoming payments. This is safe because only the deployer can send funds during contract creation, and typically no funds are sent at this stage.

### Initializers Can Be Marked As Payable
`payable` functions cost less gas to execute, since the compiler does not have to add extra checks to ensure that a payment wasn't provided.

A `initializer` can safely be marked as `payable`, since only the deployer would be able to pass funds, and the project itself would not pass any funds.



```solidity
Path: ./src/bridge/SequencerInbox.sol

177:    function initialize(	// @audit-issue
```
[177](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/bridge/SequencerInbox.sol#L177-L177), 


```solidity
Path: ./src/rollup/RollupUserLogic.sol

27:    function initialize(address _stakeToken) external view override onlyProxy {	// @audit-issue
```
[27](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/RollupUserLogic.sol#L27-L27), 


```solidity
Path: ./src/rollup/RollupAdminLogic.sol

18:    function initialize(Config calldata config, ContractDependencies calldata connectedContracts)	// @audit-issue
```
[18](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/RollupAdminLogic.sol#L18-L18), 


```solidity
Path: ./src/challengeV2/EdgeChallengeManager.sol

305:    function initialize(	// @audit-issue
```
[305](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/challengeV2/EdgeChallengeManager.sol#L305-L305), 


#### Recommendation

Mark initializers as 'payable' in Solidity contracts to reduce gas costs, as this eliminates the need for the compiler to add checks against incoming payments. This is safe because only the deployer can send funds during contract creation, and typically no funds are sent at this stage.

### Use `selfbalance()` instead of `address(this).balance`
In Solidity, contracts often need to query their own Ether balance. While `address(this).balance` has been a widely used approach to retrieve the current contract's balance, it is not the most gas-efficient method, especially with the introduction of the `SELFBALANCE` opcode in more recent EVM versions.

The `SELFBALANCE` opcode provides a more gas-efficient way to obtain the balance of the current contract. In Solidity, this can be invoked using the `selfbalance()` function. Compared to the `BALANCE` opcode used by `address(this).balance`, `SELFBALANCE` offers significant gas savings:

- `BALANCE`: The static gas cost is 0. If the accessed address is warm, the dynamic gas cost is 100. If the address is cold, the dynamic cost is 2,600.
  
- `SELFBALANCE`: Semantically equivalent to the `BALANCE` opcode when called on the contract's own address, but with a dramatically reduced minimum gas cost of 5.

Switching to `selfbalance()` can lead to significant gas savings, especially in operations or functions that frequently check the contract's balance.


```solidity
Path: ./src/rollup/RollupCreator.sol

304:            (bool sent, ) = msg.sender.call{value: address(this).balance}("");	// @audit-issue
```
[304](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/RollupCreator.sol#L304-L304), 


#### Recommendation

To optimize gas usage when querying a contract's own Ether balance in Solidity, it's recommended to use the `selfbalance()` function, which utilizes the more gas-efficient `SELFBALANCE` opcode. This can result in significant gas savings compared to `address(this).balance`.

### Optimize names to save gas
`public`/`external` function names and `public` member variable names can be optimized to save gas. Below are the interfaces/abstract contracts that can be optimized so that the most frequently-called functions use the least amount of gas possible during method lookup. Method IDs that have two leading zero bytes can save 128 gas each during deployment, and renaming functions to have lower method IDs will save 22 gas per call, [per sorted position shifted](https://medium.com/joyso/solidity-how-does-function-name-affect-gas-consumption-in-smart-contract-47d270d8ac92).


```solidity
Path: ./src/bridge/SequencerInbox.sol

64:contract SequencerInbox is DelegateCallAware, GasRefundEnabled, ISequencerInbox {	// @audit-issue
```
[64](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/bridge/SequencerInbox.sol#L64-L64), 


```solidity
Path: ./src/bridge/DelayBuffer.sol

16:library DelayBuffer {	// @audit-issue
```
[16](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/bridge/DelayBuffer.sol#L16-L16), 


```solidity
Path: ./src/bridge/ISequencerInbox.sol

15:interface ISequencerInbox is IDelayedMessageProvider {	// @audit-issue
```
[15](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/bridge/ISequencerInbox.sol#L15-L15), 


```solidity
Path: ./src/rollup/IRollupLogic.sol

12:interface IRollupUser is IRollupCore, IOwnable {	// @audit-issue
```
[12](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/IRollupLogic.sol#L12-L12), 


```solidity
Path: ./src/rollup/BOLDUpgradeAction.sol

49:interface IOldRollup {	// @audit-issue

77:interface IOldRollupAdmin {	// @audit-issue

83:interface ISeqInboxPostUpgradeInit {	// @audit-issue

94:contract StateHashPreImageLookup {	// @audit-issue

123:contract RollupReader is IOldRollup {	// @audit-issue

166:contract ConstantArrayStorage {	// @audit-issue

182:contract BOLDUpgradeAction {	// @audit-issue
```
[49](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/BOLDUpgradeAction.sol#L49-L49), [77](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/BOLDUpgradeAction.sol#L77-L77), [83](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/BOLDUpgradeAction.sol#L83-L83), [94](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/BOLDUpgradeAction.sol#L94-L94), [123](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/BOLDUpgradeAction.sol#L123-L123), [166](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/BOLDUpgradeAction.sol#L166-L166), [182](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/BOLDUpgradeAction.sol#L182-L182), 


```solidity
Path: ./src/rollup/BridgeCreator.sol

21:contract BridgeCreator is Ownable {	// @audit-issue
```
[21](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/BridgeCreator.sol#L21-L21), 


```solidity
Path: ./src/rollup/RollupCore.sol

22:abstract contract RollupCore is IRollupCore, PausableUpgradeable {	// @audit-issue
```
[22](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/RollupCore.sol#L22-L22), 


```solidity
Path: ./src/rollup/IRollupCore.sol

15:interface IRollupCore is IAssertionChain {	// @audit-issue
```
[15](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/IRollupCore.sol#L15-L15), 


```solidity
Path: ./src/rollup/RollupUserLogic.sol

15:contract RollupUserLogic is RollupCore, UUPSNotUpgradeable, IRollupUser {	// @audit-issue
```
[15](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/RollupUserLogic.sol#L15-L15), 


```solidity
Path: ./src/rollup/RollupCreator.sol

17:contract RollupCreator is Ownable {	// @audit-issue
```
[17](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/RollupCreator.sol#L17-L17), 


```solidity
Path: ./src/rollup/RollupAdminLogic.sol

15:contract RollupAdminLogic is RollupCore, IRollupAdmin, DoubleLogicUUPSUpgradeable {	// @audit-issue
```
[15](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/RollupAdminLogic.sol#L15-L15), 


```solidity
Path: ./src/rollup/IRollupAdmin.sol

13:interface IRollupAdmin {	// @audit-issue
```
[13](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/IRollupAdmin.sol#L13-L13), 


```solidity
Path: ./src/rollup/RollupProxy.sol

11:contract RollupProxy is AdminFallbackProxy {	// @audit-issue
```
[11](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/RollupProxy.sol#L11-L11), 


```solidity
Path: ./src/challengeV2/IAssertionChain.sol

13:interface IAssertionChain {	// @audit-issue
```
[13](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/challengeV2/IAssertionChain.sol#L13-L13), 


```solidity
Path: ./src/challengeV2/EdgeChallengeManager.sol

18:interface IEdgeChallengeManager {	// @audit-issue

206:contract EdgeChallengeManager is IEdgeChallengeManager, Initializable {	// @audit-issue
```
[18](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/challengeV2/EdgeChallengeManager.sol#L18-L18), [206](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/challengeV2/EdgeChallengeManager.sol#L206-L206), 


```solidity
Path: ./src/challengeV2/libraries/EdgeChallengeManagerLib.sol

129:library EdgeChallengeManagerLib {	// @audit-issue
```
[129](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/challengeV2/libraries/EdgeChallengeManagerLib.sol#L129-L129), 


```solidity
Path: ./src/challengeV2/libraries/MerkleTreeLib.sol

102:library MerkleTreeLib {	// @audit-issue
```
[102](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/challengeV2/libraries/MerkleTreeLib.sol#L102-L102), 


```solidity
Path: ./src/assertionStakingPool/AssertionStakingPoolCreator.sol

13:contract AssertionStakingPoolCreator is IAssertionStakingPoolCreator {	// @audit-issue
```
[13](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/assertionStakingPool/AssertionStakingPoolCreator.sol#L13-L13), 


```solidity
Path: ./src/assertionStakingPool/EdgeStakingPool.sol

25:contract EdgeStakingPool is AbsBoldStakingPool, IEdgeStakingPool {	// @audit-issue
```
[25](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/assertionStakingPool/EdgeStakingPool.sol#L25-L25), 


```solidity
Path: ./src/assertionStakingPool/EdgeStakingPoolCreator.sol

13:contract EdgeStakingPoolCreator is IEdgeStakingPoolCreator {	// @audit-issue
```
[13](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/assertionStakingPool/EdgeStakingPoolCreator.sol#L13-L13), 


```solidity
Path: ./src/assertionStakingPool/AssertionStakingPool.sol

21:contract AssertionStakingPool is AbsBoldStakingPool, IAssertionStakingPool {	// @audit-issue
```
[21](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/assertionStakingPool/AssertionStakingPool.sol#L21-L21), 


```solidity
Path: ./src/assertionStakingPool/AbsBoldStakingPool.sol

16:abstract contract AbsBoldStakingPool is IAbsBoldStakingPool {	// @audit-issue
```
[16](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/assertionStakingPool/AbsBoldStakingPool.sol#L16-L16), 


```solidity
Path: ./src/assertionStakingPool/interfaces/IAssertionStakingPool.sol

10:interface IAssertionStakingPool is IAbsBoldStakingPool {	// @audit-issue
```
[10](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/assertionStakingPool/interfaces/IAssertionStakingPool.sol#L10-L10), 


```solidity
Path: ./src/assertionStakingPool/interfaces/IEdgeStakingPool.sol

10:interface IEdgeStakingPool is IAbsBoldStakingPool {	// @audit-issue
```
[10](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/assertionStakingPool/interfaces/IEdgeStakingPool.sol#L10-L10), 


```solidity
Path: ./src/assertionStakingPool/interfaces/IEdgeStakingPoolCreator.sol

9:interface IEdgeStakingPoolCreator {	// @audit-issue
```
[9](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/assertionStakingPool/interfaces/IEdgeStakingPoolCreator.sol#L9-L9), 


```solidity
Path: ./src/assertionStakingPool/interfaces/IAbsBoldStakingPool.sol

7:interface IAbsBoldStakingPool {	// @audit-issue
```
[7](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/assertionStakingPool/interfaces/IAbsBoldStakingPool.sol#L7-L7), 


```solidity
Path: ./src/assertionStakingPool/interfaces/IAssertionStakingPoolCreator.sol

10:interface IAssertionStakingPoolCreator {	// @audit-issue
```
[10](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/assertionStakingPool/interfaces/IAssertionStakingPoolCreator.sol#L10-L10), 


#### Recommendation

Optimize gas usage by renaming 'public'/'external' functions and 'public' member variables in Solidity. Aim for shorter and more efficient names, especially for frequently called functions. This can save gas during deployment and reduce gas costs per call due to lower method ID sorting positions.

### Use `uint256(1)`/`uint256(2)` instead of `true`/`false` to save gas for changes
Avoids a Gsset (**20000 gas**) when changing from `false` to `true`, after having been `true` in the past. Since most of the bools aren't changed twice in one transaction, I've counted the amount of gas as half of the full amount, for each variable. Note that public state variables can be re-written to be `private` and use `uint256`, but have public getters returning `bool`s.

```solidity
Path: ./src/bridge/SequencerInbox.sol

95:    mapping(address => bool) public isBatchPoster;	// @audit-issue

115:    mapping(address => bool) public isSequencer;	// @audit-issue

131:    bool internal immutable hostChainIsArbitrum = ArbitrumChecker.runningOnArbitrum();	// @audit-issue

133:    bool public immutable isUsingFeeToken;	// @audit-issue

135:    bool public immutable isDelayBufferable;	// @audit-issue

187:        bool actualIsUsingFeeToken = false;	// @audit-issue
```
[95](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/bridge/SequencerInbox.sol#L95-L95), [115](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/bridge/SequencerInbox.sol#L115-L115), [131](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/bridge/SequencerInbox.sol#L131-L131), [133](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/bridge/SequencerInbox.sol#L133-L133), [135](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/bridge/SequencerInbox.sol#L135-L135), [187](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/bridge/SequencerInbox.sol#L187-L187), 


```solidity
Path: ./src/rollup/BOLDUpgradeAction.sol

46:    bool isStaked; // 2. must be staked	// @audit-issue

204:    bool public immutable DISABLE_VALIDATOR_WHITELIST;	// @audit-issue

207:    bool public immutable IS_DELAY_BUFFERABLE;	// @audit-issue
```
[46](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/BOLDUpgradeAction.sol#L46-L46), [204](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/BOLDUpgradeAction.sol#L204-L204), [207](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/BOLDUpgradeAction.sol#L207-L207), 


```solidity
Path: ./src/rollup/Assertion.sol

26:    bool isFirstChild;	// @audit-issue
```
[26](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/Assertion.sol#L26-L26), 


```solidity
Path: ./src/rollup/RollupCore.sol

96:    mapping(address => bool) public isValidator;	// @audit-issue

108:    bool public validatorWhitelistDisabled;	// @audit-issue

112:    bool internal immutable _hostChainIsArbitrum = ArbitrumChecker.runningOnArbitrum();	// @audit-issue
```
[96](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/RollupCore.sol#L96-L96), [108](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/RollupCore.sol#L108-L108), [112](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/RollupCore.sol#L112-L112), 


```solidity
Path: ./src/challengeV2/EdgeChallengeManager.sol

226:        bool hasRival,	// @audit-issue

227:        bool isLayerZero	// @audit-issue

236:        bytes32 indexed edgeId, bytes32 indexed lowerChildId, bytes32 indexed upperChildId, bool lowerChildAlreadyExists	// @audit-issue
```
[226](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/challengeV2/EdgeChallengeManager.sol#L226-L226), [227](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/challengeV2/EdgeChallengeManager.sol#L227-L227), [236](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/challengeV2/EdgeChallengeManager.sol#L236-L236), 


```solidity
Path: ./src/challengeV2/libraries/EdgeChallengeManagerLib.sol

86:    mapping(address => mapping(bytes32 => bool)) hasMadeLayerZeroRival;	// @audit-issue

105:    bool hasRival;	// @audit-issue

106:    bool isLayerZero;	// @audit-issue

117:    bool isPending;	// @audit-issue

119:    bool hasSibling;	// @audit-issue
```
[86](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/challengeV2/libraries/EdgeChallengeManagerLib.sol#L86-L86), [105](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/challengeV2/libraries/EdgeChallengeManagerLib.sol#L105-L105), [106](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/challengeV2/libraries/EdgeChallengeManagerLib.sol#L106-L106), [117](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/challengeV2/libraries/EdgeChallengeManagerLib.sol#L117-L117), [119](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/challengeV2/libraries/EdgeChallengeManagerLib.sol#L119-L119), 


```solidity
Path: ./src/challengeV2/libraries/ChallengeEdgeLib.sol

62:    bool refunded;	// @audit-issue
```
[62](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/challengeV2/libraries/ChallengeEdgeLib.sol#L62-L62), 


#### Recommendation

To minimize gas overhead in your Solidity contracts, consider using `uint256(1)` and `uint256(2)` to represent `true` and `false`, respectively, instead of `bool` types for storage. This approach avoids additional `SLOAD` and `SSTORE` operations, resulting in more gas-efficient code.

### Consider activating `via-ir` for deploying
The IR-based code generator was developed to make code generation more performant by enabling optimization passes that can be applied across functions.

It is possible to activate the IR-based code generator through the command line by using the flag `--via-ir`or by including the option `{"viaIR": true}`.

Keep in mind that compiling with this option may take longer. However, you can simply test it before deploying your code. If you find that it provides better performance, you can add the `--via-ir` flag to your deploy command.
```solidity
/// @audit Global finding.
```
[1](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/bridge/SequencerInbox.sol#L1), 


#### Recommendation

Consider activating `via-ir`.

### Optimize Deployment Size by Fine-tuning IPFS Hash
The Solidity compiler appends 53 bytes of metadata to the smart contract code, incurring an extra cost of 10,600 gas. This additional expense arises from 200 gas per bytecode, plus calldata cost, which amounts to 16 gas for non-zero bytes and 4 gas for zero bytes. This results in a maximum of 848 extra gas in calldata cost.

Reducing this cost is crucial for the following reasons:

The metadata's 53-byte addition leads to a deployment cost increase of 10,600 gas. It can also result in an additional calldata cost of up to 848 gas. Ways to Minimize Gas Consumption:

Employ the `--no-cbor-metadata` compiler option to exclude metadata. Be cautious as this might impact contract verification. Search for code comments that yield an IPFS hash with more zeros, thereby reducing calldata costs.

```solidity
/// @audit Global finding.
```
[1](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/bridge/SequencerInbox.sol#L1), 


#### Recommendation

To optimize deployment size and reduce associated costs, consider the following strategies:
1. **Exclude Metadata with Compiler Option**: Use the `solc` compiler’s `--metadata-hash none` or `--no-cbor-metadata` option to prevent the inclusion of metadata in the compiled bytecode. This action reduces the bytecode size, thus lowering deployment gas costs. However, exercise caution with this approach, as it might affect the ability to verify the contract on platforms like Etherscan.

2. **Optimize IPFS Hash for More Zeros**: If excluding metadata is not desirable, another approach involves optimizing code comments or elements that influence the metadata hash generation to achieve an IPFS hash with a higher proportion of zeros. Since calldata costs are lower for zero bytes, a metadata hash with more zeros can reduce the calldata costs associated with contract interactions.

Example for excluding metadata:
```bash
solc --metadata-hash none YourContract.sol
```


### Low level `call` can be optimized with assembly
`returnData` is copied to memory even if the variable is not utilized: the proper way to handle this is through a low level assembly call.
```solidity
// before
(bool success,) = payable(receiver).call{gas: gas, value: value}("");

//after
bool success;
assembly {
    success := call(gas, receiver, value, 0, 0, 0, 0)
}
```


```solidity
Path: ./src/rollup/RollupCreator.sol

304:            (bool sent, ) = msg.sender.call{value: address(this).balance}("");	// @audit-issue
```
[304](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/RollupCreator.sol#L304-L304), 


#### Recommendation

Optimize low-level 'call' operations in Solidity using assembly, especially when 'returnData' is not needed. This avoids unnecessary copying to memory and can lead to gas savings. For example, replace '(bool success,) = payable(receiver).call{gas: gas, value: value}("");' with an assembly block: 'assembly { success := call(gas, receiver, value, 0, 0, 0, 0) }'. This ensures a more efficient execution.

### Assembly: Use scratch space for building calldata
If an external call's calldata can fit into two or fewer words, use the scratch space to build the calldata, rather than allowing Solidity to do a memory expansion.

```solidity
Path: ./src/bridge/SequencerInbox.sol

104:        if (msg.sender != rollup.owner()) revert NotOwner(msg.sender, rollup.owner());	// @audit-issue

109:        if (msg.sender != rollup.owner() && msg.sender != batchPosterManager) {	// @audit-issue

188:        try IERC20Bridge(address(bridge_)).nativeToken() returns (address feeToken) {	// @audit-issue

198:        rollup = bridge_.rollup();	// @audit-issue

209:        if (msg.sender != IOwnable(rollup).owner())	// @audit-issue

210:            revert NotOwner(msg.sender, IOwnable(rollup).owner());	// @audit-issue

211:        IOwnable newRollup = bridge.rollup();	// @audit-issue

310:            buffer.update(l1BlockAndTime[0]);	// @audit-issue

319:            prevDelayedAcc = bridge.delayedInboxAccs(_totalDelayedMessagesRead - 2);	// @audit-issue

322:            bridge.delayedInboxAccs(_totalDelayedMessagesRead - 1) !=	// @audit-issue

323:            Messages.accumulateInboxMessage(prevDelayedAcc, messageHash)	// @audit-issue

330:        uint256 prevSeqMsgCount = bridge.sequencerReportedSubMessageCount();	// @audit-issue

610:            if (buffer.isUpdatable()) {	// @audit-issue

612:                bytes32 delayedAcc = bridge.delayedInboxAccs(totalDelayedMessagesRead);	// @audit-issue

623:                buffer.update(delayProof.delayedMessage.blockNumber);	// @audit-issue

634:            !buffer.isSynced();	// @audit-issue

717:        return (keccak256(bytes.concat(header, data)), timeBounds);	// @audit-issue

735:        bytes32[] memory dataHashes = reader4844.getDataHashes();	// @audit-issue

742:        uint256 blobCost = reader4844.getBlobBaseFee() * GAS_PER_BLOB * dataHashes.length;	// @audit-issue

770:            uint256 l1Fees = ArbGasInfo(address(0x6c)).getCurrentTxL1GasFees();	// @audit-issue

783:        uint256 msgNum = bridge.submitBatchSpendingReport(	// @audit-issue

807:        if (afterDelayedMessagesRead > bridge.delayedMessageCount()) revert DelayedTooFar();	// @audit-issue

825:        return bridge.sequencerInboxAccs(index);	// @audit-issue

829:        return bridge.sequencerMessageCount();	// @audit-issue

836:            uint64 _buffer = buffer.calcPendingBuffer(blockNumber);	// @audit-issue

849:        if (!DelayBuffer.isValidBufferConfig(bufferConfig_)) revert BadBufferConfig();	// @audit-issue

862:        if (bridge.delayedMessageCount() == totalDelayedMessagesRead) {	// @audit-issue

863:            buffer.update(uint64(block.number));	// @audit-issue

904:        uint256 ksWord = uint256(keccak256(bytes.concat(hex"fe", keccak256(keysetBytes))));	// @audit-issue

911:            creationBlock = ArbSys(address(100)).arbBlockNumber();	// @audit-issue
```
[104](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/bridge/SequencerInbox.sol#L104-L104), [109](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/bridge/SequencerInbox.sol#L109-L109), [188](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/bridge/SequencerInbox.sol#L188-L188), [198](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/bridge/SequencerInbox.sol#L198-L198), [209](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/bridge/SequencerInbox.sol#L209-L209), [210](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/bridge/SequencerInbox.sol#L210-L210), [211](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/bridge/SequencerInbox.sol#L211-L211), [310](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/bridge/SequencerInbox.sol#L310-L310), [319](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/bridge/SequencerInbox.sol#L319-L319), [322](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/bridge/SequencerInbox.sol#L322-L322), [323](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/bridge/SequencerInbox.sol#L323-L323), [330](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/bridge/SequencerInbox.sol#L330-L330), [610](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/bridge/SequencerInbox.sol#L610-L610), [612](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/bridge/SequencerInbox.sol#L612-L612), [623](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/bridge/SequencerInbox.sol#L623-L623), [634](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/bridge/SequencerInbox.sol#L634-L634), [717](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/bridge/SequencerInbox.sol#L717-L717), [735](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/bridge/SequencerInbox.sol#L735-L735), [742](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/bridge/SequencerInbox.sol#L742-L742), [770](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/bridge/SequencerInbox.sol#L770-L770), [783](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/bridge/SequencerInbox.sol#L783-L783), [807](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/bridge/SequencerInbox.sol#L807-L807), [825](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/bridge/SequencerInbox.sol#L825-L825), [829](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/bridge/SequencerInbox.sol#L829-L829), [836](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/bridge/SequencerInbox.sol#L836-L836), [849](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/bridge/SequencerInbox.sol#L849-L849), [862](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/bridge/SequencerInbox.sol#L862-L862), [863](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/bridge/SequencerInbox.sol#L863-L863), [904](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/bridge/SequencerInbox.sol#L904-L904), [911](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/bridge/SequencerInbox.sol#L911-L911), 


```solidity
Path: ./src/rollup/RollupLib.sol

31:            afterState.hash(),	// @audit-issue
```
[31](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/RollupLib.sol#L31-L31), 


```solidity
Path: ./src/rollup/BOLDUpgradeAction.sol

103:            keccak256(abi.encodePacked(executionState.globalState.hash(), inboxMaxCount, executionState.machineStatus));	// @audit-issue

131:        return rollup.wasmModuleRoot();	// @audit-issue

135:        return rollup.latestConfirmed();	// @audit-issue

139:        return rollup.getNode(nodeNum);	// @audit-issue

143:        return rollup.getStakerAddress(stakerNum);	// @audit-issue

147:        return rollup.stakerCount();	// @audit-issue

151:        return rollup.getStaker(staker);	// @audit-issue

155:        return rollup.isValidator(validator);	// @audit-issue

159:        return rollup.validatorWalletCreator();	// @audit-issue

342:        IOldRollupAdmin(address(OLD_ROLLUP)).pause();	// @audit-issue

344:        uint64 stakerCount = ROLLUP_READER.stakerCount();	// @audit-issue

351:            address stakerAddr = ROLLUP_READER.getStakerAddress(i);	// @audit-issue

352:            OldStaker memory staker = ROLLUP_READER.getStaker(stakerAddr);	// @audit-issue

357:                IOldRollupAdmin(address(OLD_ROLLUP)).forceRefundStaker(stakersToRefund);	// @audit-issue

362:        DoubleLogicUUPSUpgradeable(address(OLD_ROLLUP)).upgradeSecondaryTo(IMPL_PATCHED_OLD_ROLLUP_USER);	// @audit-issue

369:        bytes32 latestConfirmedStateHash = ROLLUP_READER.getNode(ROLLUP_READER.latestConfirmed()).stateHash;	// @audit-issue

370:        (ExecutionState memory genesisExecState, uint256 inboxMaxCount) = PREIMAGE_LOOKUP.get(latestConfirmedStateHash);	// @audit-issue

379:            PREIMAGE_LOOKUP.stateHash(genesisAssertionState.toExecutionState(), inboxMaxCount)	// @audit-issue

392:            wasmModuleRoot: ROLLUP_READER.wasmModuleRoot(),	// @audit-issue

397:            miniStakeValues: ConstantArrayStorage(MINI_STAKE_AMOUNTS_STORAGE).array(),	// @audit-issue

416:        PROXY_ADMIN_BRIDGE.upgrade(bridge, IMPL_BRIDGE);	// @audit-issue

417:        IBridge(BRIDGE).updateRollupAddress(IOwnable(newRollupAddress));	// @audit-issue

422:        PROXY_ADMIN_INBOX.upgrade(inbox, IMPL_INBOX);	// @audit-issue

425:        PROXY_ADMIN_REI.upgrade(rollupEventInbox, IMPL_REI);	// @audit-issue

426:        IRollupEventInbox(REI).updateRollupAddress();	// @audit-issue

429:        PROXY_ADMIN_OUTBOX.upgrade(outbox, IMPL_OUTBOX);	// @audit-issue

430:        IOutbox(OUTBOX).updateRollupAddress();	// @audit-issue

449:            PROXY_ADMIN_SEQUENCER_INBOX.upgrade(sequencerInbox, IMPL_SEQUENCER_INBOX);	// @audit-issue

454:            PROXY_ADMIN_SEQUENCER_INBOX.getProxyImplementation(sequencerInbox) == IMPL_SEQUENCER_INBOX,	// @audit-issue

458:            ISequencerInbox(SEQ_INBOX).isDelayBufferable() == IS_DELAY_BUFFERABLE,	// @audit-issue

461:        ISequencerInbox(SEQ_INBOX).updateRollupAddress();	// @audit-issue

493:            validatorWalletCreator: ROLLUP_READER.validatorWalletCreator()	// @audit-issue

500:            Create2Upgradeable.computeAddress(rollupSalt, keccak256(type(RollupProxy).creationCode));	// @audit-issue

524:        rollup.initializeProxy(config, connectedContracts);	// @audit-issue

529:                require(ROLLUP_READER.isValidator(validators[i]), "UNEXPECTED_NEW_VALIDATOR");	// @audit-issue

532:            IRollupAdmin(address(rollup)).setValidator(validators, _vals);	// @audit-issue

535:            IRollupAdmin(address(rollup)).setValidatorWhitelistDisabled(DISABLE_VALIDATOR_WHITELIST);	// @audit-issue

538:        IRollupAdmin(address(rollup)).setOwner(actualOwner);	// @audit-issue
```
[103](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/BOLDUpgradeAction.sol#L103-L103), [131](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/BOLDUpgradeAction.sol#L131-L131), [135](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/BOLDUpgradeAction.sol#L135-L135), [139](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/BOLDUpgradeAction.sol#L139-L139), [143](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/BOLDUpgradeAction.sol#L143-L143), [147](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/BOLDUpgradeAction.sol#L147-L147), [151](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/BOLDUpgradeAction.sol#L151-L151), [155](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/BOLDUpgradeAction.sol#L155-L155), [159](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/BOLDUpgradeAction.sol#L159-L159), [342](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/BOLDUpgradeAction.sol#L342-L342), [344](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/BOLDUpgradeAction.sol#L344-L344), [351](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/BOLDUpgradeAction.sol#L351-L351), [352](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/BOLDUpgradeAction.sol#L352-L352), [357](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/BOLDUpgradeAction.sol#L357-L357), [362](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/BOLDUpgradeAction.sol#L362-L362), [369](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/BOLDUpgradeAction.sol#L369-L369), [370](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/BOLDUpgradeAction.sol#L370-L370), [379](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/BOLDUpgradeAction.sol#L379-L379), [392](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/BOLDUpgradeAction.sol#L392-L392), [397](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/BOLDUpgradeAction.sol#L397-L397), [416](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/BOLDUpgradeAction.sol#L416-L416), [417](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/BOLDUpgradeAction.sol#L417-L417), [422](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/BOLDUpgradeAction.sol#L422-L422), [425](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/BOLDUpgradeAction.sol#L425-L425), [426](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/BOLDUpgradeAction.sol#L426-L426), [429](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/BOLDUpgradeAction.sol#L429-L429), [430](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/BOLDUpgradeAction.sol#L430-L430), [449](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/BOLDUpgradeAction.sol#L449-L449), [454](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/BOLDUpgradeAction.sol#L454-L454), [458](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/BOLDUpgradeAction.sol#L458-L458), [461](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/BOLDUpgradeAction.sol#L461-L461), [493](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/BOLDUpgradeAction.sol#L493-L493), [500](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/BOLDUpgradeAction.sol#L500-L500), [524](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/BOLDUpgradeAction.sol#L524-L524), [529](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/BOLDUpgradeAction.sol#L529-L529), [532](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/BOLDUpgradeAction.sol#L532-L532), [535](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/BOLDUpgradeAction.sol#L535-L535), [538](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/BOLDUpgradeAction.sol#L538-L538), 


```solidity
Path: ./src/rollup/BridgeCreator.sol

118:            IEthBridge(address(frame.bridge)).initialize(IOwnable(rollup));	// @audit-issue

120:            IERC20Bridge(address(frame.bridge)).initialize(IOwnable(rollup), nativeToken);	// @audit-issue

123:        frame.inbox.initialize(frame.bridge, frame.sequencerInbox);	// @audit-issue

124:        frame.rollupEventInbox.initialize(frame.bridge);	// @audit-issue

125:        frame.outbox.initialize(frame.bridge);	// @audit-issue
```
[118](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/BridgeCreator.sol#L118-L118), [120](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/BridgeCreator.sol#L120-L120), [123](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/BridgeCreator.sol#L123-L123), [124](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/BridgeCreator.sol#L124-L124), [125](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/BridgeCreator.sol#L125-L125), 


```solidity
Path: ./src/rollup/RollupCore.sol

117:        return ISequencerInbox(bridge.sequencerInbox());	// @audit-issue

152:            assertion.requireExists();	// @audit-issue

257:        bytes32 blockHash = confirmState.globalState.getBlockHash();	// @audit-issue

258:        bytes32 sendRoot = confirmState.globalState.getSendRoot();	// @audit-issue

261:        outbox.updateSendRoot(sendRoot, blockHash);	// @audit-issue

276:        _stakerList.push(stakerAddress);	// @audit-issue

361:        _stakerList.pop();	// @audit-issue

371:        RollupLib.validateConfigHash(	// @audit-issue

424:            require(afterGS.comparePositions(beforeGS) >= 0, "INBOX_BACKWARDS");	// @audit-issue

426:                afterGS.comparePositionsAgainstStartOfBatch(assertion.beforeStateData.configData.nextInboxPosition);	// @audit-issue

433:                require(afterGS.comparePositions(beforeGS) > 0, "OVERFLOW_STANDSTILL");	// @audit-issue

436:            uint256 currentInboxPosition = bridge.sequencerMessageCount();	// @audit-issue

438:            require(afterGS.comparePositionsAgainstStartOfBatch(currentInboxPosition) <= 0, "INBOX_PAST_END");	// @audit-issue

450:            uint256 afterInboxPosition = afterGS.getInboxPosition();	// @audit-issue

471:            sequencerBatchAcc = bridge.sequencerInboxAccs(afterInboxPosition - 1);	// @audit-issue

488:        AssertionNode memory newAssertion = AssertionNodeLib.createAssertion(	// @audit-issue

501:        prevAssertion.childCreated();	// @audit-issue

516:            _assertionCreatedAtArbSysBlock[newAssertionHash] = ArbSys(address(100)).arbBlockNumber();	// @audit-issue

550:        RollupLib.validateConfigHash(configData, getAssertionStorage(assertionHash).configHash);	// @audit-issue
```
[117](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/RollupCore.sol#L117-L117), [152](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/RollupCore.sol#L152-L152), [257](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/RollupCore.sol#L257-L257), [258](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/RollupCore.sol#L258-L258), [261](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/RollupCore.sol#L261-L261), [276](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/RollupCore.sol#L276-L276), [361](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/RollupCore.sol#L361-L361), [371](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/RollupCore.sol#L371-L371), [424](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/RollupCore.sol#L424-L424), [426](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/RollupCore.sol#L426-L426), [433](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/RollupCore.sol#L433-L433), [436](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/RollupCore.sol#L436-L436), [438](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/RollupCore.sol#L438-L438), [450](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/RollupCore.sol#L450-L450), [471](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/RollupCore.sol#L471-L471), [488](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/RollupCore.sol#L488-L488), [501](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/RollupCore.sol#L501-L501), [516](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/RollupCore.sol#L516-L516), [550](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/RollupCore.sol#L550-L550), 


```solidity
Path: ./src/rollup/RollupUserLogic.sol

107:        RollupLib.validateConfigHash(prevConfig, prevAssertion.configHash);	// @audit-issue

117:            ChallengeEdge memory winningEdge = IEdgeChallengeManager(prevConfig.challengeManager).getEdge(winningEdgeId);	// @audit-issue

189:        getAssertionStorage(prevAssertion).requireExists();	// @audit-issue

215:            IERC20(stakeToken).safeTransfer(loserStakeEscrow, assertion.beforeStateData.configData.requiredStake);	// @audit-issue

286:        getAssertionStorage(prevAssertion).requireExists();	// @audit-issue

295:                IERC20(stakeToken).safeTransfer(loserStakeEscrow, assertion.beforeStateData.configData.requiredStake);	// @audit-issue

304:            bridge.sequencerInboxAccs(assertion.afterState.globalState.getInboxPosition() - 1)	// @audit-issue

362:        IERC20(stakeToken).safeTransfer(msg.sender, amount);	// @audit-issue
```
[107](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/RollupUserLogic.sol#L107-L107), [117](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/RollupUserLogic.sol#L117-L117), [189](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/RollupUserLogic.sol#L189-L189), [215](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/RollupUserLogic.sol#L215-L215), [286](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/RollupUserLogic.sol#L286-L286), [295](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/RollupUserLogic.sol#L295-L295), [304](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/RollupUserLogic.sol#L304-L304), [362](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/RollupUserLogic.sol#L362-L362), 


```solidity
Path: ./src/rollup/RollupCreator.sol

151:            ) = bridgeCreator.ethBasedTemplates();	// @audit-issue

153:                deployParams.maxDataSize == ethSequencerInbox.maxDataSize(),	// @audit-issue

157:                deployParams.maxDataSize == ethDelayBufferableSequencerInbox.maxDataSize(),	// @audit-issue

160:            require(deployParams.maxDataSize == ethInbox.maxDataSize(), "I_MAX_DATA_SIZE_MISMATCH");	// @audit-issue

169:            ) = bridgeCreator.erc20BasedTemplates();	// @audit-issue

171:                deployParams.maxDataSize == erc20SequencerInbox.maxDataSize(),	// @audit-issue

175:                deployParams.maxDataSize == erc20DelayBufferableSequencerInbox.maxDataSize(),	// @audit-issue

179:                deployParams.maxDataSize == erc20Inbox.maxDataSize(),	// @audit-issue

204:        proxyAdmin.transferOwnership(address(upgradeExecutor));	// @audit-issue

209:        rollup.initializeProxy(	// @audit-issue

226:            bridgeContracts.sequencerInbox.setIsBatchPoster(deployParams.batchPosters[i], true);	// @audit-issue

229:            bridgeContracts.sequencerInbox.setBatchPosterManager(deployParams.batchPosterManager);	// @audit-issue

238:            IRollupAdmin(address(rollup)).setValidator(deployParams.validators, _vals);	// @audit-issue

241:        IRollupAdmin(address(rollup)).setOwner(address(upgradeExecutor));	// @audit-issue

282:        upgradeExecutor.initialize(address(upgradeExecutor), executors);	// @audit-issue

294:            uint256 cost = l2FactoriesDeployer.getDeploymentTotalCost(	// @audit-issue

308:            uint256 totalFee = l2FactoriesDeployer.getDeploymentTotalCost(	// @audit-issue
```
[151](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/RollupCreator.sol#L151-L151), [153](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/RollupCreator.sol#L153-L153), [157](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/RollupCreator.sol#L157-L157), [160](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/RollupCreator.sol#L160-L160), [169](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/RollupCreator.sol#L169-L169), [171](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/RollupCreator.sol#L171-L171), [175](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/RollupCreator.sol#L175-L175), [179](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/RollupCreator.sol#L179-L179), [204](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/RollupCreator.sol#L204-L204), [209](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/RollupCreator.sol#L209-L209), [226](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/RollupCreator.sol#L226-L226), [229](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/RollupCreator.sol#L229-L229), [238](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/RollupCreator.sol#L238-L238), [241](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/RollupCreator.sol#L241-L241), [282](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/RollupCreator.sol#L282-L282), [294](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/RollupCreator.sol#L294-L294), [308](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/RollupCreator.sol#L308-L308), 


```solidity
Path: ./src/rollup/RollupAdminLogic.sol

26:        connectedContracts.bridge.setDelayedInbox(address(connectedContracts.inbox), true);	// @audit-issue

27:        connectedContracts.bridge.setSequencerInbox(address(connectedContracts.sequencerInbox));	// @audit-issue

31:        connectedContracts.bridge.setOutbox(address(connectedContracts.outbox), true);	// @audit-issue

35:        if (!bridge.allowedDelayedInboxes(address(connectedContracts.rollupEventInbox))) {	// @audit-issue

36:            connectedContracts.bridge.setDelayedInbox(address(connectedContracts.rollupEventInbox), true);	// @audit-issue

37:            connectedContracts.rollupEventInbox.rollupInitialized(config.chainId, config.chainConfig);	// @audit-issue

40:        if (connectedContracts.sequencerInbox.totalDelayedMessagesRead() == 0) {	// @audit-issue

67:            afterStateHash: config.genesisAssertionState.hash(),	// @audit-issue

71:        uint256 currentInboxCount = bridge.sequencerMessageCount();	// @audit-issue

76:        AssertionNode memory initialAssertion = AssertionNodeLib.createAssertion(	// @audit-issue

102:            _assertionCreatedAtArbSysBlock[genesisHash] = ArbSys(address(100)).arbBlockNumber();	// @audit-issue

119:        bridge.setOutbox(address(_outbox), true);	// @audit-issue

129:        bridge.setOutbox(_outbox, false);	// @audit-issue

139:        bridge.setDelayedInbox(address(_inbox), _enabled);	// @audit-issue

291:        bridge.setSequencerInbox(_sequencerInbox);	// @audit-issue
```
[26](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/RollupAdminLogic.sol#L26-L26), [27](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/RollupAdminLogic.sol#L27-L27), [31](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/RollupAdminLogic.sol#L31-L31), [35](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/RollupAdminLogic.sol#L35-L35), [36](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/RollupAdminLogic.sol#L36-L36), [37](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/RollupAdminLogic.sol#L37-L37), [40](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/RollupAdminLogic.sol#L40-L40), [67](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/RollupAdminLogic.sol#L67-L67), [71](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/RollupAdminLogic.sol#L71-L71), [76](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/RollupAdminLogic.sol#L76-L76), [102](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/RollupAdminLogic.sol#L102-L102), [119](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/RollupAdminLogic.sol#L119-L119), [129](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/RollupAdminLogic.sol#L129-L129), [139](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/RollupAdminLogic.sol#L139-L139), [291](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/RollupAdminLogic.sol#L291-L291), 


```solidity
Path: ./src/challengeV2/EdgeChallengeManager.sol

336:        if (!EdgeChallengeManagerLib.isPowerOfTwo(layerZeroBlockEdgeHeight)) {	// @audit-issue

340:        if (!EdgeChallengeManagerLib.isPowerOfTwo(layerZeroBigStepEdgeHeight)) {	// @audit-issue

344:        if (!EdgeChallengeManagerLib.isPowerOfTwo(layerZeroSmallStepEdgeHeight)) {	// @audit-issue

374:        bool whitelistEnabled = !assertionChain.validatorWhitelistDisabled();	// @audit-issue

376:        if (whitelistEnabled && !assertionChain.isValidator(msg.sender)) {	// @audit-issue

381:        EdgeType eType = ChallengeEdgeLib.levelToType(args.level, NUM_BIGSTEP_LEVEL);	// @audit-issue

411:                assertionChain.isPending(args.claimId),	// @audit-issue

412:                assertionChain.getSecondChildCreationBlock(claimStateData.prevAssertionHash) > 0,	// @audit-issue

493:            (bool updated, uint256 newValue) = store.updateTimerCacheByChildren(edgeIds[i]);	// @audit-issue

500:        (bool updated, uint256 newValue) = store.updateTimerCacheByChildren(edgeId);	// @audit-issue

512:        ChallengeEdge storage topEdge = store.get(edgeId);	// @audit-issue

513:        if (!topEdge.isLayerZero()) {	// @audit-issue

514:            revert EdgeNotLayerZero(topEdge.id(), topEdge.staker, topEdge.claimId);	// @audit-issue

521:        bool isBlockLevel = ChallengeEdgeLib.levelToType(topEdge.level, NUM_BIGSTEP_LEVEL) == EdgeType.Block;	// @audit-issue

522:        if (isBlockLevel && assertionChain.isFirstChild(topEdge.claimId)) {	// @audit-issue

529:            assertionBlocks = assertionChain.getSecondChildCreationBlock(claimStateData.prevAssertionHash)	// @audit-issue

530:                - assertionChain.getFirstChildCreationBlock(claimStateData.prevAssertionHash);	// @audit-issue

535:        emit EdgeConfirmedByTime(edgeId, store.edges[edgeId].mutualId(), totalTimeUnrivaled);	// @audit-issue

546:        bytes32 prevAssertionHash = store.getPrevAssertionHash(edgeId);	// @audit-issue

548:        assertionChain.validateConfig(prevAssertionHash, prevConfig);	// @audit-issue

552:            bridge: assertionChain.bridge(),	// @audit-issue

568:        emit EdgeConfirmedByOneStepProof(edgeId, store.edges[edgeId].mutualId());	// @audit-issue

573:        ChallengeEdge storage edge = store.get(edgeId);	// @audit-issue

575:        edge.setRefunded();	// @audit-issue

581:            st.safeTransfer(edge.staker, sa);	// @audit-issue

584:        emit EdgeRefunded(edgeId, store.edges[edgeId].mutualId(), address(st), sa);	// @audit-issue

628:        return store.edges[edgeId].exists();	// @audit-issue

633:        return store.get(edgeId);	// @audit-issue

638:        return store.get(edgeId).length();	// @audit-issue

643:        return store.hasRival(edgeId);	// @audit-issue

653:        return store.hasLengthOneRival(edgeId);	// @audit-issue

658:        return store.timeUnrivaled(edgeId);	// @audit-issue

663:        return store.getPrevAssertionHash(edgeId);	// @audit-issue
```
[336](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/challengeV2/EdgeChallengeManager.sol#L336-L336), [340](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/challengeV2/EdgeChallengeManager.sol#L340-L340), [344](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/challengeV2/EdgeChallengeManager.sol#L344-L344), [374](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/challengeV2/EdgeChallengeManager.sol#L374-L374), [376](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/challengeV2/EdgeChallengeManager.sol#L376-L376), [381](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/challengeV2/EdgeChallengeManager.sol#L381-L381), [411](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/challengeV2/EdgeChallengeManager.sol#L411-L411), [412](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/challengeV2/EdgeChallengeManager.sol#L412-L412), [493](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/challengeV2/EdgeChallengeManager.sol#L493-L493), [500](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/challengeV2/EdgeChallengeManager.sol#L500-L500), [512](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/challengeV2/EdgeChallengeManager.sol#L512-L512), [513](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/challengeV2/EdgeChallengeManager.sol#L513-L513), [514](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/challengeV2/EdgeChallengeManager.sol#L514-L514), [521](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/challengeV2/EdgeChallengeManager.sol#L521-L521), [522](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/challengeV2/EdgeChallengeManager.sol#L522-L522), [529](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/challengeV2/EdgeChallengeManager.sol#L529-L529), [530](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/challengeV2/EdgeChallengeManager.sol#L530-L530), [535](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/challengeV2/EdgeChallengeManager.sol#L535-L535), [546](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/challengeV2/EdgeChallengeManager.sol#L546-L546), [548](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/challengeV2/EdgeChallengeManager.sol#L548-L548), [552](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/challengeV2/EdgeChallengeManager.sol#L552-L552), [568](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/challengeV2/EdgeChallengeManager.sol#L568-L568), [573](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/challengeV2/EdgeChallengeManager.sol#L573-L573), [575](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/challengeV2/EdgeChallengeManager.sol#L575-L575), [581](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/challengeV2/EdgeChallengeManager.sol#L581-L581), [584](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/challengeV2/EdgeChallengeManager.sol#L584-L584), [628](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/challengeV2/EdgeChallengeManager.sol#L628-L628), [633](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/challengeV2/EdgeChallengeManager.sol#L633-L633), [638](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/challengeV2/EdgeChallengeManager.sol#L638-L638), [643](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/challengeV2/EdgeChallengeManager.sol#L643-L643), [653](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/challengeV2/EdgeChallengeManager.sol#L653-L653), [658](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/challengeV2/EdgeChallengeManager.sol#L658-L658), [663](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/challengeV2/EdgeChallengeManager.sol#L663-L663), 


```solidity
Path: ./src/challengeV2/libraries/EdgeChallengeManagerLib.sol

142:        if (!store.edges[edgeId].exists()) {	// @audit-issue

161:        bytes32 eId = edge.idMem();	// @audit-issue

163:        if (store.edges[eId].exists()) {	// @audit-issue

196:            store.edges[eId].length(),	// @audit-issue

220:        if (ChallengeEdgeLib.levelToType(args.level, numBigStepLevel) == EdgeType.Block) {	// @audit-issue

263:            bytes32 startStateHash = oneStepProofEntry.getMachineHash(ard.startState.toExecutionState());	// @audit-issue

264:            bytes32 endStateHash = oneStepProofEntry.getMachineHash(ard.endState.toExecutionState());	// @audit-issue

280:            bytes32 originId = claimEdge.mutualId();	// @audit-issue

351:        bytes32 startHistoryRoot = MerkleTreeLib.root(MerkleTreeLib.appendLeaf(new bytes32[](0), proofData.startState));	// @audit-issue

431:            bytes32 mutualId = ce.mutualIdMem();	// @audit-issue

464:        if (!store.edges[edgeId].exists()) {	// @audit-issue

469:        bytes32 mutualId = store.edges[edgeId].mutualId();	// @audit-issue

485:        return (hasRival(store, edgeId) && store.edges[edgeId].length() == 1);	// @audit-issue

538:        if (!store.edges[edgeId].exists()) {	// @audit-issue

542:        bytes32 mutualId = store.edges[edgeId].mutualId();	// @audit-issue

555:            if (!store.edges[firstRival].exists()) {	// @audit-issue

585:        uint256 mostSignificantSharedBit = UintUtilsLib.mostSignificantBit(diff);	// @audit-issue

636:            lowerChildId = lowerChild.idMem();	// @audit-issue

639:            if (!store.edges[lowerChildId].exists()) {	// @audit-issue

654:        store.edges[edgeId].setChildren(lowerChildId, upperChildAdded.edgeId);	// @audit-issue

663:        bytes32 mutualId = store.edges[edgeId].mutualId();	// @audit-issue

678:        ChallengeEdgeLib.levelToType(nextLevel, numBigStepLevel);	// @audit-issue

698:        if (store.edges[edgeId].mutualId() != store.edges[claimingEdgeId].originId) {	// @audit-issue

699:            revert OriginIdMutualIdMismatch(store.edges[edgeId].mutualId(), store.edges[claimingEdgeId].originId);	// @audit-issue

729:        if (!store.edges[edgeId].exists()) {	// @audit-issue

746:        store.edges[edgeId].setConfirmed();	// @audit-issue

778:        if (!store.edges[edgeId].exists()) {	// @audit-issue

783:        if (ChallengeEdgeLib.levelToType(store.edges[edgeId].level, numBigStepLevel) != EdgeType.SmallStep) {	// @audit-issue

788:        if (store.edges[edgeId].length() != 1) {	// @audit-issue

789:            revert EdgeNotLengthOne(store.edges[edgeId].length());	// @audit-issue

829:        store.edges[edgeId].setConfirmed();	// @audit-issue
```
[142](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/challengeV2/libraries/EdgeChallengeManagerLib.sol#L142-L142), [161](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/challengeV2/libraries/EdgeChallengeManagerLib.sol#L161-L161), [163](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/challengeV2/libraries/EdgeChallengeManagerLib.sol#L163-L163), [196](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/challengeV2/libraries/EdgeChallengeManagerLib.sol#L196-L196), [220](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/challengeV2/libraries/EdgeChallengeManagerLib.sol#L220-L220), [263](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/challengeV2/libraries/EdgeChallengeManagerLib.sol#L263-L263), [264](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/challengeV2/libraries/EdgeChallengeManagerLib.sol#L264-L264), [280](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/challengeV2/libraries/EdgeChallengeManagerLib.sol#L280-L280), [351](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/challengeV2/libraries/EdgeChallengeManagerLib.sol#L351-L351), [431](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/challengeV2/libraries/EdgeChallengeManagerLib.sol#L431-L431), [464](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/challengeV2/libraries/EdgeChallengeManagerLib.sol#L464-L464), [469](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/challengeV2/libraries/EdgeChallengeManagerLib.sol#L469-L469), [485](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/challengeV2/libraries/EdgeChallengeManagerLib.sol#L485-L485), [538](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/challengeV2/libraries/EdgeChallengeManagerLib.sol#L538-L538), [542](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/challengeV2/libraries/EdgeChallengeManagerLib.sol#L542-L542), [555](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/challengeV2/libraries/EdgeChallengeManagerLib.sol#L555-L555), [585](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/challengeV2/libraries/EdgeChallengeManagerLib.sol#L585-L585), [636](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/challengeV2/libraries/EdgeChallengeManagerLib.sol#L636-L636), [639](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/challengeV2/libraries/EdgeChallengeManagerLib.sol#L639-L639), [654](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/challengeV2/libraries/EdgeChallengeManagerLib.sol#L654-L654), [663](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/challengeV2/libraries/EdgeChallengeManagerLib.sol#L663-L663), [678](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/challengeV2/libraries/EdgeChallengeManagerLib.sol#L678-L678), [698](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/challengeV2/libraries/EdgeChallengeManagerLib.sol#L698-L698), [699](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/challengeV2/libraries/EdgeChallengeManagerLib.sol#L699-L699), [729](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/challengeV2/libraries/EdgeChallengeManagerLib.sol#L729-L729), [746](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/challengeV2/libraries/EdgeChallengeManagerLib.sol#L746-L746), [778](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/challengeV2/libraries/EdgeChallengeManagerLib.sol#L778-L778), [783](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/challengeV2/libraries/EdgeChallengeManagerLib.sol#L783-L783), [788](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/challengeV2/libraries/EdgeChallengeManagerLib.sol#L788-L788), [789](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/challengeV2/libraries/EdgeChallengeManagerLib.sol#L789-L789), [829](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/challengeV2/libraries/EdgeChallengeManagerLib.sol#L829-L829), 


```solidity
Path: ./src/challengeV2/libraries/MerkleTreeLib.sol

178:        bytes32[] memory next = UintUtilsLib.mostSignificantBit(postSize) > UintUtilsLib.mostSignificantBit(meSize)	// @audit-issue

268:        uint256 msb = UintUtilsLib.mostSignificantBit(startSize ^ endSize);	// @audit-issue

276:            return UintUtilsLib.leastSignificantBit(y);	// @audit-issue

283:            return UintUtilsLib.mostSignificantBit(z);	// @audit-issue
```
[178](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/challengeV2/libraries/MerkleTreeLib.sol#L178-L178), [268](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/challengeV2/libraries/MerkleTreeLib.sol#L268-L268), [276](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/challengeV2/libraries/MerkleTreeLib.sol#L276-L276), [283](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/challengeV2/libraries/MerkleTreeLib.sol#L283-L283), 


```solidity
Path: ./src/challengeV2/libraries/ChallengeEdgeLib.sol

232:            revert EdgeNotExists(ChallengeEdgeLib.id(edge));	// @audit-issue

241:            revert ChildrenAlreadySet(ChallengeEdgeLib.id(edge), edge.lowerChildId, edge.upperChildId);	// @audit-issue

251:            revert EdgeNotPending(ChallengeEdgeLib.id(edge), edge.status);	// @audit-issue

266:            revert EdgeNotConfirmed(ChallengeEdgeLib.id(edge), edge.status);	// @audit-issue

269:            revert EdgeNotLayerZero(ChallengeEdgeLib.id(edge), edge.staker, edge.claimId);	// @audit-issue

272:            revert EdgeAlreadyRefunded(ChallengeEdgeLib.id(edge));	// @audit-issue
```
[232](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/challengeV2/libraries/ChallengeEdgeLib.sol#L232-L232), [241](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/challengeV2/libraries/ChallengeEdgeLib.sol#L241-L241), [251](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/challengeV2/libraries/ChallengeEdgeLib.sol#L251-L251), [266](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/challengeV2/libraries/ChallengeEdgeLib.sol#L266-L266), [269](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/challengeV2/libraries/ChallengeEdgeLib.sol#L269-L269), [272](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/challengeV2/libraries/ChallengeEdgeLib.sol#L272-L272), 


```solidity
Path: ./src/assertionStakingPool/AssertionStakingPoolCreator.sol

30:            StakingPoolCreatorUtils.getPool(	// @audit-issue
```
[30](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/assertionStakingPool/AssertionStakingPoolCreator.sol#L30-L30), 


```solidity
Path: ./src/assertionStakingPool/EdgeStakingPool.sol

45:        uint256 requiredStake = EdgeChallengeManager(challengeManager).stakeAmounts(args.level);	// @audit-issue

46:        IERC20(stakeToken).safeIncreaseAllowance(address(challengeManager), requiredStake);	// @audit-issue

47:        bytes32 newEdgeId = EdgeChallengeManager(challengeManager).createLayerZeroEdge(args);	// @audit-issue
```
[45](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/assertionStakingPool/EdgeStakingPool.sol#L45-L45), [46](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/assertionStakingPool/EdgeStakingPool.sol#L46-L46), [47](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/assertionStakingPool/EdgeStakingPool.sol#L47-L47), 


```solidity
Path: ./src/assertionStakingPool/StakingPoolCreatorUtils.sol

16:        if (Address.isContract(pool)) {	// @audit-issue
```
[16](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/assertionStakingPool/StakingPoolCreatorUtils.sol#L16-L16), 


```solidity
Path: ./src/assertionStakingPool/EdgeStakingPoolCreator.sol

30:            StakingPoolCreatorUtils.getPool(	// @audit-issue
```
[30](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/assertionStakingPool/EdgeStakingPoolCreator.sol#L30-L30), 


```solidity
Path: ./src/assertionStakingPool/AssertionStakingPool.sol

43:        IERC20(stakeToken).safeIncreaseAllowance(rollup, requiredStake);	// @audit-issue

51:        IRollupUser(rollup).returnOldDeposit();	// @audit-issue

56:        IRollupUser(rollup).withdrawStakerFunds();	// @audit-issue
```
[43](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/assertionStakingPool/AssertionStakingPool.sol#L43-L43), [51](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/assertionStakingPool/AssertionStakingPool.sol#L51-L51), [56](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/assertionStakingPool/AssertionStakingPool.sol#L56-L56), 


```solidity
Path: ./src/assertionStakingPool/AbsBoldStakingPool.sol

51:        IERC20(stakeToken).safeTransfer(msg.sender, amount);	// @audit-issue
```
[51](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/assertionStakingPool/AbsBoldStakingPool.sol#L51-L51), 


#### Recommendation

Review your smart contracts to identify and remove `block.number` and `block.timestamp` from the parameters of emitted events. Instead of manually adding these fields, rely on the Ethereum blockchain's inherent inclusion of this information within the block context. Simplify your event definitions to include only the essential data specific to the event's purpose, excluding universally available block metadata.

### Use assembly to check for `address(0)`
In Solidity, it's a common practice to check whether an Ethereum address variable is set to the zero address (`address(0)`) to handle various scenarios, such as token transfers or contract interactions. Typically, this check is performed using a conditional statement like `if (addressVariable == address(0))`.

However, using this approach in high-frequency or gas-sensitive operations can lead to unnecessary gas costs. A more gas-efficient alternative is to use inline assembly to perform the zero address check, which can significantly reduce gas consumption, especially in loops or complex contract logic.

By utilizing inline assembly for this specific check, you can optimize gas usage and make your Solidity code more efficient.

```solidity
Path: ./src/bridge/SequencerInbox.sol

148:            if (reader4844_ != IReader4844(address(0))) revert DataBlobsNotSupported();	// @audit-issue

150:            if (reader4844_ == IReader4844(address(0))) revert InitParamZero("Reader4844");	// @audit-issue

182:        if (bridge != IBridge(address(0))) revert AlreadyInit();	// @audit-issue

183:        if (bridge_ == IBridge(address(0))) revert HadZeroInit();	// @audit-issue

189:            if (feeToken != address(0)) {	// @audit-issue
```
[148](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/bridge/SequencerInbox.sol#L148-L148), [150](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/bridge/SequencerInbox.sol#L150-L150), [182](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/bridge/SequencerInbox.sol#L182-L182), [183](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/bridge/SequencerInbox.sol#L183-L183), [189](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/bridge/SequencerInbox.sol#L189-L189), 


```solidity
Path: ./src/rollup/BridgeCreator.sol

112:            nativeToken == address(0) ? ethBasedTemplates : erc20BasedTemplates,	// @audit-issue

117:        if (nativeToken == address(0)) {	// @audit-issue
```
[112](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/BridgeCreator.sol#L112-L112), [117](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/BridgeCreator.sol#L117-L117), 


```solidity
Path: ./src/rollup/RollupUserLogic.sol

28:        require(_stakeToken != address(0), "NEED_STAKE_TOKEN");	// @audit-issue

337:        require(withdrawalAddress != address(0), "EMPTY_WITHDRAWAL_ADDRESS");	// @audit-issue
```
[28](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/RollupUserLogic.sol#L28-L28), [337](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/RollupUserLogic.sol#L337-L337), 


```solidity
Path: ./src/rollup/RollupCreator.sol

228:        if (deployParams.batchPosterManager != address(0)) {	// @audit-issue

292:        if (_nativeToken == address(0)) {	// @audit-issue
```
[228](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/RollupCreator.sol#L228-L228), [292](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/RollupCreator.sol#L292-L292), 


```solidity
Path: ./src/rollup/RollupAdminLogic.sol

41:            connectedContracts.sequencerInbox.addSequencerL2Batch(0, "", 1, IGasRefunder(address(0)), 0, 1);	// @audit-issue

57:        require(config.loserStakeEscrow != address(0), "INVALID_ESCROW_0");	// @audit-issue

272:        require(newLoserStakerEscrow != address(0), "INVALID_ESCROW_0");	// @audit-issue
```
[41](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/RollupAdminLogic.sol#L41-L41), [57](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/RollupAdminLogic.sol#L57-L57), [272](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/RollupAdminLogic.sol#L272-L272), 


```solidity
Path: ./src/rollup/RollupProxy.sol

16:            _getAdmin() == address(0) &&	// @audit-issue

17:            _getImplementation() == address(0) &&	// @audit-issue

18:            _getSecondaryImplementation() == address(0)	// @audit-issue
```
[16](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/RollupProxy.sol#L16-L16), [17](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/RollupProxy.sol#L17-L17), [18](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/RollupProxy.sol#L18-L18), 


```solidity
Path: ./src/challengeV2/EdgeChallengeManager.sol

317:        if (address(_assertionChain) == address(0)) {	// @audit-issue

321:        if (address(_oneStepProofEntry) == address(0)) {	// @audit-issue

331:        if (_excessStakeReceiver == address(0)) {	// @audit-issue

429:        if (address(st) != address(0) && sa != 0) {	// @audit-issue

580:        if (address(st) != address(0) && sa != 0) {	// @audit-issue
```
[317](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/challengeV2/EdgeChallengeManager.sol#L317-L317), [321](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/challengeV2/EdgeChallengeManager.sol#L321-L321), [331](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/challengeV2/EdgeChallengeManager.sol#L331-L331), [429](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/challengeV2/EdgeChallengeManager.sol#L429-L429), [580](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/challengeV2/EdgeChallengeManager.sol#L580-L580), 


```solidity
Path: ./src/challengeV2/libraries/ChallengeEdgeLib.sol

103:        if (staker == address(0)) {	// @audit-issue

153:            staker: address(0),	// @audit-issue

259:        return edge.claimId != 0 && edge.staker != address(0);	// @audit-issue
```
[103](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/challengeV2/libraries/ChallengeEdgeLib.sol#L103-L103), [153](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/challengeV2/libraries/ChallengeEdgeLib.sol#L153-L153), [259](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/challengeV2/libraries/ChallengeEdgeLib.sol#L259-L259), 


#### Recommendation

To optimize gas usage in your Solidity code, consider using inline assembly for checking `address(0)`. This approach can significantly reduce gas costs, especially in high-frequency or gas-sensitive operations, leading to more efficient contract execution.

### Use assembly to check for `0`
Using assembly to check for zero can save gas by allowing more direct access to the evm and reducing some of the overhead associated with high-level operations in solidity.

```solidity
Path: ./src/bridge/SequencerInbox.sol

170:        if (buffer.bufferBlocks != 0) {	// @audit-issue

702:        if (data.length > 0) {	// @audit-issue

711:            if (data[0] & DAS_MESSAGE_HEADER_FLAG != 0 && data.length >= 33) {	// @audit-issue

736:        if (dataHashes.length == 0) revert MissingDataHashes();	// @audit-issue

746:            block.basefee > 0 ? blobCost / block.basefee : 0	// @audit-issue

818:        if (calldataLengthPosted > 0 && !isUsingFeeToken) {	// @audit-issue

851:        if (buffer.bufferBlocks == 0 || buffer.bufferBlocks > bufferConfig_.max) {	// @audit-issue

959:        if (ksInfo.creationBlock == 0) revert NoSuchKeyset(ksHash);	// @audit-issue
```
[170](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/bridge/SequencerInbox.sol#L170-L170), [702](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/bridge/SequencerInbox.sol#L702-L702), [711](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/bridge/SequencerInbox.sol#L711-L711), [736](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/bridge/SequencerInbox.sol#L736-L736), [746](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/bridge/SequencerInbox.sol#L746-L746), [818](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/bridge/SequencerInbox.sol#L818-L818), [851](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/bridge/SequencerInbox.sol#L851-L851), [959](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/bridge/SequencerInbox.sol#L959-L959), 


```solidity
Path: ./src/bridge/DelayBuffer.sol

117:            config.threshold != 0 &&	// @audit-issue

118:            config.max != 0 &&	// @audit-issue
```
[117](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/bridge/DelayBuffer.sol#L117-L117), [118](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/bridge/DelayBuffer.sol#L118-L118), 


```solidity
Path: ./src/rollup/BOLDUpgradeAction.sol

114:        require(inboxMaxCount != 0, "Hash not yet set");	// @audit-issue

353:            if (staker.isStaked && staker.currentChallenge == 0) {	// @audit-issue

526:        if (validators.length != 0) {	// @audit-issue
```
[114](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/BOLDUpgradeAction.sol#L114-L114), [353](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/BOLDUpgradeAction.sol#L353-L353), [526](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/BOLDUpgradeAction.sol#L526-L526), 


```solidity
Path: ./src/rollup/Assertion.sol

86:        if (self.firstChildBlock == 0) {	// @audit-issue

88:        } else if (self.secondChildBlock == 0) {	// @audit-issue
```
[86](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/Assertion.sol#L86-L86), [88](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/Assertion.sol#L88-L88), 


```solidity
Path: ./src/rollup/BridgeCreator.sol

107:        bool isDelayBufferable = bufferConfig.threshold != 0;	// @audit-issue
```
[107](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/BridgeCreator.sol#L107-L107), 


```solidity
Path: ./src/rollup/RollupCore.sol

148:            require(blockNum > 0, "NO_ASSERTION");	// @audit-issue

424:            require(afterGS.comparePositions(beforeGS) >= 0, "INBOX_BACKWARDS");	// @audit-issue

427:            require(afterStateCmpMaxInbox <= 0, "INBOX_TOO_FAR");	// @audit-issue

429:            if (assertion.afterState.machineStatus != MachineStatus.ERRORED && afterStateCmpMaxInbox < 0) {	// @audit-issue

433:                require(afterGS.comparePositions(beforeGS) > 0, "OVERFLOW_STANDSTILL");	// @audit-issue

438:            require(afterGS.comparePositionsAgainstStartOfBatch(currentInboxPosition) <= 0, "INBOX_PAST_END");	// @audit-issue

466:            require(afterInboxPosition != 0, "EMPTY_INBOX_COUNT");	// @audit-issue

489:            prevAssertion.firstChildBlock == 0, // assumes block 0 is impossible	// @audit-issue

572:        bool haveChild = getAssertionStorage(lastestAssertion).firstChildBlock > 0;	// @audit-issue
```
[148](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/RollupCore.sol#L148-L148), [424](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/RollupCore.sol#L424-L424), [427](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/RollupCore.sol#L427-L427), [429](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/RollupCore.sol#L429-L429), [433](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/RollupCore.sol#L433-L433), [438](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/RollupCore.sol#L438-L438), [466](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/RollupCore.sol#L466-L466), [489](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/RollupCore.sol#L489-L489), [572](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/RollupCore.sol#L572-L572), 


```solidity
Path: ./src/rollup/RollupUserLogic.sol

53:        if (latestConfirmedAssertion.createdAtBlock == 0) return false;	// @audit-issue

56:        if (latestConfirmedAssertion.firstChildBlock > 0) {	// @audit-issue

115:        if (prevAssertion.secondChildBlock > 0) {	// @audit-issue

120:            require(winningEdge.confirmedAtBlock != 0, "ZERO_CONFIRMED_AT_BLOCK");	// @audit-issue

196:            lastAssertion == prevAssertion || getAssertionStorage(lastAssertion).firstChildBlock > 0,	// @audit-issue

360:        require(amount > 0, "NO_FUNDS_TO_WITHDRAW");	// @audit-issue
```
[53](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/RollupUserLogic.sol#L53-L53), [56](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/RollupUserLogic.sol#L56-L56), [115](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/RollupUserLogic.sol#L115-L115), [120](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/RollupUserLogic.sol#L120-L120), [196](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/RollupUserLogic.sol#L196-L196), [360](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/RollupUserLogic.sol#L360-L360), 


```solidity
Path: ./src/rollup/RollupCreator.sol

233:        if (deployParams.validators.length != 0) {	// @audit-issue
```
[233](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/RollupCreator.sol#L233-L233), 


```solidity
Path: ./src/rollup/RollupAdminLogic.sol

40:        if (connectedContracts.sequencerInbox.totalDelayedMessagesRead() == 0) {	// @audit-issue

181:        require(_validator.length > 0, "EMPTY_ARRAY");	// @audit-issue

214:        require(newConfirmPeriod > 0, "INVALID_CONFIRM_PERIOD");	// @audit-issue

229:        require(staker.length > 0, "EMPTY_ARRAY");	// @audit-issue
```
[40](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/RollupAdminLogic.sol#L40-L40), [181](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/RollupAdminLogic.sol#L181-L181), [214](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/RollupAdminLogic.sol#L214-L214), [229](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/RollupAdminLogic.sol#L229-L229), 


```solidity
Path: ./src/challengeV2/EdgeChallengeManager.sol

325:        if (_challengePeriodBlocks == 0) {	// @audit-issue

350:        if (_numBigStepLevel == 0) {	// @audit-issue

387:            if (args.proof.length == 0) {	// @audit-issue

412:                assertionChain.getSecondChildCreationBlock(claimStateData.prevAssertionHash) > 0,	// @audit-issue

429:        if (address(st) != address(0) && sa != 0) {	// @audit-issue

458:        bool lowerChildAlreadyExists = lowerChildAdded.edgeId == 0;	// @audit-issue

580:        if (address(st) != address(0) && sa != 0) {	// @audit-issue
```
[325](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/challengeV2/EdgeChallengeManager.sol#L325-L325), [350](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/challengeV2/EdgeChallengeManager.sol#L350-L350), [387](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/challengeV2/EdgeChallengeManager.sol#L387-L387), [412](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/challengeV2/EdgeChallengeManager.sol#L412-L412), [429](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/challengeV2/EdgeChallengeManager.sol#L429-L429), [458](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/challengeV2/EdgeChallengeManager.sol#L458-L458), [580](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/challengeV2/EdgeChallengeManager.sol#L580-L580), 


```solidity
Path: ./src/challengeV2/libraries/EdgeChallengeManagerLib.sol

182:        if (firstRival == 0) {	// @audit-issue

198:            firstRival != 0,	// @audit-issue

199:            edge.claimId != 0	// @audit-issue

229:            if (ard.assertionHash == 0) {	// @audit-issue

248:            if (args.proof.length == 0) {	// @audit-issue

294:            if (args.proof.length == 0) {	// @audit-issue

329:        if (x == 0) {	// @audit-issue

337:        return ((x & y) == 0);	// @audit-issue

378:        if (args.prefixProof.length == 0) {	// @audit-issue

445:        while (edge.level > 0) {	// @audit-issue

472:        if (firstRival == 0) {	// @audit-issue

545:        if (firstRival == 0) {	// @audit-issue
```
[182](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/challengeV2/libraries/EdgeChallengeManagerLib.sol#L182-L182), [198](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/challengeV2/libraries/EdgeChallengeManagerLib.sol#L198-L198), [199](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/challengeV2/libraries/EdgeChallengeManagerLib.sol#L199-L199), [229](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/challengeV2/libraries/EdgeChallengeManagerLib.sol#L229-L229), [248](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/challengeV2/libraries/EdgeChallengeManagerLib.sol#L248-L248), [294](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/challengeV2/libraries/EdgeChallengeManagerLib.sol#L294-L294), [329](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/challengeV2/libraries/EdgeChallengeManagerLib.sol#L329-L329), [337](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/challengeV2/libraries/EdgeChallengeManagerLib.sol#L337-L337), [378](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/challengeV2/libraries/EdgeChallengeManagerLib.sol#L378-L378), [445](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/challengeV2/libraries/EdgeChallengeManagerLib.sol#L445-L445), [472](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/challengeV2/libraries/EdgeChallengeManagerLib.sol#L472-L472), [545](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/challengeV2/libraries/EdgeChallengeManagerLib.sol#L545-L545), 


```solidity
Path: ./src/challengeV2/libraries/MerkleTreeLib.sol

111:        require(me.length > 0, "Empty merkle expansion");	// @audit-issue

117:            if (accum == 0) {	// @audit-issue

118:                if (val != 0) {	// @audit-issue

129:            } else if (val != 0) {	// @audit-issue

159:        require(subtreeRoot != 0, "Cannot append empty subtree");	// @audit-issue

162:        if (me.length == 0) {	// @audit-issue

195:                require(me[i] == 0, "Append above least significant bit");	// @audit-issue

198:                if (accumHash == 0) {	// @audit-issue

203:                    if (me[i] == 0) {	// @audit-issue

222:        if (accumHash != 0) {	// @audit-issue

228:        require(next[next.length - 1] != 0, "Last entry zero");	// @audit-issue

275:        if (y != 0) {	// @audit-issue

282:        if (z != 0) {	// @audit-issue

295:            if (me[i] != 0) {	// @audit-issue

320:        require(preSize > 0, "Pre-size cannot be 0");	// @audit-issue
```
[111](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/challengeV2/libraries/MerkleTreeLib.sol#L111-L111), [117](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/challengeV2/libraries/MerkleTreeLib.sol#L117-L117), [118](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/challengeV2/libraries/MerkleTreeLib.sol#L118-L118), [129](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/challengeV2/libraries/MerkleTreeLib.sol#L129-L129), [159](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/challengeV2/libraries/MerkleTreeLib.sol#L159-L159), [162](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/challengeV2/libraries/MerkleTreeLib.sol#L162-L162), [195](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/challengeV2/libraries/MerkleTreeLib.sol#L195-L195), [198](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/challengeV2/libraries/MerkleTreeLib.sol#L198-L198), [203](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/challengeV2/libraries/MerkleTreeLib.sol#L203-L203), [222](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/challengeV2/libraries/MerkleTreeLib.sol#L222-L222), [228](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/challengeV2/libraries/MerkleTreeLib.sol#L228-L228), [275](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/challengeV2/libraries/MerkleTreeLib.sol#L275-L275), [282](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/challengeV2/libraries/MerkleTreeLib.sol#L282-L282), [295](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/challengeV2/libraries/MerkleTreeLib.sol#L295-L295), [320](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/challengeV2/libraries/MerkleTreeLib.sol#L320-L320), 


```solidity
Path: ./src/challengeV2/libraries/ChallengeEdgeLib.sol

76:        if (originId == 0) {	// @audit-issue

82:        if (startHistoryRoot == 0) {	// @audit-issue

85:        if (endHistoryRoot == 0) {	// @audit-issue

106:        if (claimId == 0) {	// @audit-issue

224:        return edge.createdAtBlock != 0;	// @audit-issue

231:        if (len == 0) {	// @audit-issue

240:        if (edge.lowerChildId != 0 || edge.upperChildId != 0) {	// @audit-issue

259:        return edge.claimId != 0 && edge.staker != address(0);	// @audit-issue

280:        if (level == 0) {	// @audit-issue
```
[76](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/challengeV2/libraries/ChallengeEdgeLib.sol#L76-L76), [82](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/challengeV2/libraries/ChallengeEdgeLib.sol#L82-L82), [85](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/challengeV2/libraries/ChallengeEdgeLib.sol#L85-L85), [106](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/challengeV2/libraries/ChallengeEdgeLib.sol#L106-L106), [224](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/challengeV2/libraries/ChallengeEdgeLib.sol#L224-L224), [231](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/challengeV2/libraries/ChallengeEdgeLib.sol#L231-L231), [240](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/challengeV2/libraries/ChallengeEdgeLib.sol#L240-L240), [259](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/challengeV2/libraries/ChallengeEdgeLib.sol#L259-L259), [280](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/challengeV2/libraries/ChallengeEdgeLib.sol#L280-L280), 


```solidity
Path: ./src/challengeV2/libraries/UintUtilsLib.sol

15:        require(x > 0, "Zero has no significant bits");	// @audit-issue

30:        require(x != 0, "Zero has no significant bits");	// @audit-issue
```
[15](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/challengeV2/libraries/UintUtilsLib.sol#L15-L15), [30](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/challengeV2/libraries/UintUtilsLib.sol#L30-L30), 


```solidity
Path: ./src/assertionStakingPool/AbsBoldStakingPool.sol

30:        if (amount == 0) {	// @audit-issue

42:        if (amount == 0) {	// @audit-issue
```
[30](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/assertionStakingPool/AbsBoldStakingPool.sol#L30-L30), [42](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/assertionStakingPool/AbsBoldStakingPool.sol#L42-L42), 


#### Recommendation

To optimize gas usage in your Solidity code, consider using inline assembly for checking `0`. This approach can significantly reduce gas costs, especially in high-frequency or gas-sensitive operations, leading to more efficient contract execution.

### Use assembly to write `address` storage values
Using assembly `{ sstore(state.slot, addr)}` instead of `state = addr` can save gas.


```solidity
Path: ./src/bridge/SequencerInbox.sol

152:        reader4844 = reader4844_;	// @audit-issue

197:        bridge = bridge_;	// @audit-issue

943:        batchPosterManager = newBatchPosterManager;	// @audit-issue
```
[152](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/bridge/SequencerInbox.sol#L152-L152), [197](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/bridge/SequencerInbox.sol#L197-L197), [943](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/bridge/SequencerInbox.sol#L943-L943), 


```solidity
Path: ./src/rollup/BOLDUpgradeAction.sol

127:        rollup = _rollup;	// @audit-issue

310:        IMPL_BRIDGE = implementations.bridge;	// @audit-issue

311:        IMPL_SEQUENCER_INBOX = implementations.seqInbox;	// @audit-issue

312:        IMPL_INBOX = implementations.inbox;	// @audit-issue

313:        IMPL_REI = implementations.rei;	// @audit-issue

314:        IMPL_OUTBOX = implementations.outbox;	// @audit-issue

315:        IMPL_PATCHED_OLD_ROLLUP_USER = implementations.oldRollupUser;	// @audit-issue

316:        IMPL_NEW_ROLLUP_USER = implementations.newRollupUser;	// @audit-issue

317:        IMPL_NEW_ROLLUP_ADMIN = implementations.newRollupAdmin;	// @audit-issue

318:        IMPL_CHALLENGE_MANAGER = implementations.challengeManager;	// @audit-issue
```
[127](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/BOLDUpgradeAction.sol#L127-L127), [310](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/BOLDUpgradeAction.sol#L310-L310), [311](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/BOLDUpgradeAction.sol#L311-L311), [312](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/BOLDUpgradeAction.sol#L312-L312), [313](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/BOLDUpgradeAction.sol#L313-L313), [314](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/BOLDUpgradeAction.sol#L314-L314), [315](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/BOLDUpgradeAction.sol#L315-L315), [316](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/BOLDUpgradeAction.sol#L316-L316), [317](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/BOLDUpgradeAction.sol#L317-L317), [318](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/BOLDUpgradeAction.sol#L318-L318), 


```solidity
Path: ./src/rollup/RollupCreator.sol

73:        bridgeCreator = _bridgeCreator;	// @audit-issue

74:        osp = _osp;	// @audit-issue

75:        challengeManagerTemplate = _challengeManagerLogic;	// @audit-issue

76:        rollupAdminLogic = _rollupAdminLogic;	// @audit-issue

77:        rollupUserLogic = _rollupUserLogic;	// @audit-issue

78:        upgradeExecutorLogic = _upgradeExecutorLogic;	// @audit-issue

79:        validatorWalletCreator = _validatorWalletCreator;	// @audit-issue

80:        l2FactoriesDeployer = _l2FactoriesDeployer;	// @audit-issue
```
[73](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/RollupCreator.sol#L73-L73), [74](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/RollupCreator.sol#L74-L74), [75](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/RollupCreator.sol#L75-L75), [76](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/RollupCreator.sol#L76-L76), [77](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/RollupCreator.sol#L77-L77), [78](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/RollupCreator.sol#L78-L78), [79](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/RollupCreator.sol#L79-L79), [80](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/RollupCreator.sol#L80-L80), 


```solidity
Path: ./src/rollup/RollupAdminLogic.sol

118:        outbox = _outbox;	// @audit-issue

273:        loserStakeEscrow = newLoserStakerEscrow;	// @audit-issue

300:        inbox = newInbox;	// @audit-issue

318:        anyTrustFastConfirmer = _anyTrustFastConfirmer;	// @audit-issue

327:        challengeManager = IEdgeChallengeManager(_challengeManager);	// @audit-issue
```
[118](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/RollupAdminLogic.sol#L118-L118), [273](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/RollupAdminLogic.sol#L273-L273), [300](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/RollupAdminLogic.sol#L300-L300), [318](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/RollupAdminLogic.sol#L318-L318), [327](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/RollupAdminLogic.sol#L327-L327), 


```solidity
Path: ./src/challengeV2/EdgeChallengeManager.sol

320:        assertionChain = _assertionChain;	// @audit-issue

324:        oneStepProofEntry = _oneStepProofEntry;	// @audit-issue

330:        stakeToken = _stakeToken;	// @audit-issue

334:        excessStakeReceiver = _excessStakeReceiver;	// @audit-issue
```
[320](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/challengeV2/EdgeChallengeManager.sol#L320-L320), [324](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/challengeV2/EdgeChallengeManager.sol#L324-L324), [330](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/challengeV2/EdgeChallengeManager.sol#L330-L330), [334](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/challengeV2/EdgeChallengeManager.sol#L334-L334), 


```solidity
Path: ./src/assertionStakingPool/EdgeStakingPool.sol

39:        challengeManager = _challengeManager;	// @audit-issue
```
[39](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/assertionStakingPool/EdgeStakingPool.sol#L39-L39), 


```solidity
Path: ./src/assertionStakingPool/AssertionStakingPool.sol

35:        rollup = _rollup;	// @audit-issue
```
[35](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/assertionStakingPool/AssertionStakingPool.sol#L35-L35), 


```solidity
Path: ./src/assertionStakingPool/AbsBoldStakingPool.sol

25:        stakeToken = _stakeToken;	// @audit-issue
```
[25](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/assertionStakingPool/AbsBoldStakingPool.sol#L25-L25), 


#### Recommendation

To reduce gas costs in your Solidity code, consider using assembly with `{ sstore(state.slot, addr) }` for writing `address` storage values instead of `state = addr`. This approach can result in significant gas savings.

### Use assembly to emit an `event`
To efficiently emit events, it's possible to utilize assembly by making use of scratch space and the free memory pointer. This approach has the advantage of potentially avoiding the costs associated with memory expansion.

However, it's important to note that in order to safely optimize this process, it is preferable to cache and restore the free memory pointer.

A good example of such practice can be seen in [Solady's](https://github.com/Vectorized/solady/blob/main/src/tokens/ERC1155.sol#L167) codebase.


```solidity
Path: ./src/bridge/SequencerInbox.sol

344:        emit SequencerBatchDelivered(	// @audit-issue

488:        emit SequencerBatchDelivered(	// @audit-issue

542:        emit SequencerBatchDelivered(	// @audit-issue

555:            emit SequencerBatchData(seqMessageIndex, data);	// @audit-issue

788:        emit InboxMessageDelivered(msgNum, spendingReportMsg);	// @audit-issue

890:        emit OwnerFunctionCalled(0);	// @audit-issue

899:        emit OwnerFunctionCalled(1);	// @audit-issue

917:        emit SetValidKeyset(ksHash, keysetBytes);	// @audit-issue

918:        emit OwnerFunctionCalled(2);	// @audit-issue

928:        emit InvalidateKeyset(ksHash);	// @audit-issue

929:        emit OwnerFunctionCalled(3);	// @audit-issue

938:        emit OwnerFunctionCalled(4); // Owner in this context can also be batch poster manager	// @audit-issue

944:        emit OwnerFunctionCalled(5);	// @audit-issue

949:        emit OwnerFunctionCalled(6);	// @audit-issue
```
[344](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/bridge/SequencerInbox.sol#L344-L344), [488](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/bridge/SequencerInbox.sol#L488-L488), [542](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/bridge/SequencerInbox.sol#L542-L542), [555](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/bridge/SequencerInbox.sol#L555-L555), [788](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/bridge/SequencerInbox.sol#L788-L788), [890](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/bridge/SequencerInbox.sol#L890-L890), [899](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/bridge/SequencerInbox.sol#L899-L899), [917](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/bridge/SequencerInbox.sol#L917-L917), [918](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/bridge/SequencerInbox.sol#L918-L918), [928](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/bridge/SequencerInbox.sol#L928-L928), [929](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/bridge/SequencerInbox.sol#L929-L929), [938](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/bridge/SequencerInbox.sol#L938-L938), [944](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/bridge/SequencerInbox.sol#L944-L944), [949](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/bridge/SequencerInbox.sol#L949-L949), 


```solidity
Path: ./src/rollup/BOLDUpgradeAction.sol

109:        emit HashSet(h, executionState, inboxMaxCount);	// @audit-issue

540:        emit RollupMigrated(expectedRollupAddress, address(challengeManager));	// @audit-issue
```
[109](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/BOLDUpgradeAction.sol#L109-L109), [540](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/BOLDUpgradeAction.sol#L540-L540), 


```solidity
Path: ./src/rollup/BridgeCreator.sol

55:        emit TemplatesUpdated();	// @audit-issue

60:        emit ERC20TemplatesUpdated();	// @audit-issue
```
[55](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/BridgeCreator.sol#L55-L55), [60](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/BridgeCreator.sol#L60-L60), 


```solidity
Path: ./src/rollup/RollupCore.sol

266:        emit AssertionConfirmed(assertionHash, blockHash, sendRoot);	// @audit-issue

278:        emit UserStakeUpdated(stakerAddress, withdrawalAddress, 0, depositAmount);	// @audit-issue

291:        emit UserStakeUpdated(stakerAddress, staker.withdrawalAddress, initialStaked, finalStaked);	// @audit-issue

308:        emit UserStakeUpdated(stakerAddress, withdrawalAddress, current, target);	// @audit-issue

323:        emit UserStakeUpdated(stakerAddress, withdrawalAddress, initialStaked, 0);	// @audit-issue

335:        emit UserWithdrawableFundsUpdated(account, amount, 0);	// @audit-issue

348:        emit UserWithdrawableFundsUpdated(account, initialWithdrawable, finalWithdrawable);	// @audit-issue

504:        emit AssertionCreated(	// @audit-issue
```
[266](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/RollupCore.sol#L266-L266), [278](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/RollupCore.sol#L278-L278), [291](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/RollupCore.sol#L291-L291), [308](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/RollupCore.sol#L308-L308), [323](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/RollupCore.sol#L323-L323), [335](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/RollupCore.sol#L335-L335), [348](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/RollupCore.sol#L348-L348), [504](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/RollupCore.sol#L504-L504), 


```solidity
Path: ./src/rollup/RollupCreator.sol

81:        emit TemplatesUpdated();	// @audit-issue

251:        emit RollupCreated(	// @audit-issue
```
[81](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/RollupCreator.sol#L81-L81), [251](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/RollupCreator.sol#L251-L251), 


```solidity
Path: ./src/rollup/RollupAdminLogic.sol

90:        emit AssertionCreated(	// @audit-issue

105:        emit RollupInitialized(config.wasmModuleRoot, config.chainId);	// @audit-issue

120:        emit OwnerFunctionCalled(0);	// @audit-issue

130:        emit OwnerFunctionCalled(1);	// @audit-issue

140:        emit OwnerFunctionCalled(2);	// @audit-issue

152:        emit OwnerFunctionCalled(3);	// @audit-issue

160:        emit OwnerFunctionCalled(4);	// @audit-issue

187:        emit OwnerFunctionCalled(6);	// @audit-issue

197:        emit OwnerFunctionCalled(7);	// @audit-issue

206:        emit OwnerFunctionCalled(8);	// @audit-issue

216:        emit OwnerFunctionCalled(9);	// @audit-issue

225:        emit OwnerFunctionCalled(12);	// @audit-issue

234:        emit OwnerFunctionCalled(22);	// @audit-issue

255:        emit OwnerFunctionCalled(23);	// @audit-issue

266:        emit OwnerFunctionCalled(24);	// @audit-issue

274:        emit OwnerFunctionCalled(25);	// @audit-issue

283:        emit OwnerFunctionCalled(26);	// @audit-issue

292:        emit OwnerFunctionCalled(27);	// @audit-issue

301:        emit OwnerFunctionCalled(28);	// @audit-issue

310:        emit OwnerFunctionCalled(30);	// @audit-issue

319:        emit OwnerFunctionCalled(31);	// @audit-issue

328:        emit OwnerFunctionCalled(32);	// @audit-issue
```
[90](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/RollupAdminLogic.sol#L90-L90), [105](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/RollupAdminLogic.sol#L105-L105), [120](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/RollupAdminLogic.sol#L120-L120), [130](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/RollupAdminLogic.sol#L130-L130), [140](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/RollupAdminLogic.sol#L140-L140), [152](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/RollupAdminLogic.sol#L152-L152), [160](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/RollupAdminLogic.sol#L160-L160), [187](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/RollupAdminLogic.sol#L187-L187), [197](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/RollupAdminLogic.sol#L197-L197), [206](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/RollupAdminLogic.sol#L206-L206), [216](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/RollupAdminLogic.sol#L216-L216), [225](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/RollupAdminLogic.sol#L225-L225), [234](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/RollupAdminLogic.sol#L234-L234), [255](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/RollupAdminLogic.sol#L255-L255), [266](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/RollupAdminLogic.sol#L266-L266), [274](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/RollupAdminLogic.sol#L274-L274), [283](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/RollupAdminLogic.sol#L283-L283), [292](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/RollupAdminLogic.sol#L292-L292), [301](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/RollupAdminLogic.sol#L301-L301), [310](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/RollupAdminLogic.sol#L310-L310), [319](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/RollupAdminLogic.sol#L319-L319), [328](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/RollupAdminLogic.sol#L328-L328), 


```solidity
Path: ./src/challengeV2/EdgeChallengeManager.sol

437:        emit EdgeAdded(	// @audit-issue

462:            emit EdgeAdded(	// @audit-issue

474:        emit EdgeAdded(	// @audit-issue

485:        emit EdgeBisected(edgeId, lowerChildId, upperChildAdded.edgeId, lowerChildAlreadyExists);	// @audit-issue

494:            if (updated) emit TimerCacheUpdated(edgeIds[i], newValue);	// @audit-issue

501:        if (updated) emit TimerCacheUpdated(edgeId, newValue);	// @audit-issue

507:        if (updated) emit TimerCacheUpdated(edgeId, newValue);	// @audit-issue

535:        emit EdgeConfirmedByTime(edgeId, store.edges[edgeId].mutualId(), totalTimeUnrivaled);	// @audit-issue

568:        emit EdgeConfirmedByOneStepProof(edgeId, store.edges[edgeId].mutualId());	// @audit-issue

584:        emit EdgeRefunded(edgeId, store.edges[edgeId].mutualId(), address(st), sa);	// @audit-issue
```
[437](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/challengeV2/EdgeChallengeManager.sol#L437-L437), [462](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/challengeV2/EdgeChallengeManager.sol#L462-L462), [474](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/challengeV2/EdgeChallengeManager.sol#L474-L474), [485](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/challengeV2/EdgeChallengeManager.sol#L485-L485), [494](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/challengeV2/EdgeChallengeManager.sol#L494-L494), [501](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/challengeV2/EdgeChallengeManager.sol#L501-L501), [507](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/challengeV2/EdgeChallengeManager.sol#L507-L507), [535](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/challengeV2/EdgeChallengeManager.sol#L535-L535), [568](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/challengeV2/EdgeChallengeManager.sol#L568-L568), [584](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/challengeV2/EdgeChallengeManager.sol#L584-L584), 


```solidity
Path: ./src/assertionStakingPool/AssertionStakingPoolCreator.sol

20:        emit NewAssertionPoolCreated(_rollup, _assertionHash, address(assertionPool));	// @audit-issue
```
[20](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/assertionStakingPool/AssertionStakingPoolCreator.sol#L20-L20), 


```solidity
Path: ./src/assertionStakingPool/EdgeStakingPoolCreator.sol

20:        emit NewEdgeStakingPoolCreated(challengeManager, edgeId);	// @audit-issue
```
[20](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/assertionStakingPool/EdgeStakingPoolCreator.sol#L20-L20), 


```solidity
Path: ./src/assertionStakingPool/AbsBoldStakingPool.sol

37:        emit StakeDeposited(msg.sender, amount);	// @audit-issue

53:        emit StakeWithdrawn(msg.sender, amount);	// @audit-issue
```
[37](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/assertionStakingPool/AbsBoldStakingPool.sol#L37-L37), [53](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/assertionStakingPool/AbsBoldStakingPool.sol#L53-L53), 


#### Recommendation

To optimize event emission in your Solidity code, consider using assembly with scratch space and the free memory pointer. This approach can help reduce gas costs by avoiding memory expansion expenses. However, it's crucial to ensure safe optimization by caching and restoring the free memory pointer, as demonstrated in examples like Solady's codebase.

### Use assembly to validate `msg.sender`
We can use assembly to efficiently validate `msg.sender` with the least amount of opcodes necessary. For more details check the following report [Here](https://code4rena.com/reports/2023-05-juicebox#g-06-use-assembly-to-validate-msgsender)


```solidity
Path: ./src/bridge/SequencerInbox.sol

104:        if (msg.sender != rollup.owner()) revert NotOwner(msg.sender, rollup.owner());	// @audit-issue

109:        if (msg.sender != rollup.owner() && msg.sender != batchPosterManager) {	// @audit-issue

209:        if (msg.sender != IOwnable(rollup).owner())	// @audit-issue

375:        if (msg.sender != tx.origin) revert NotOrigin();	// @audit-issue

440:        if (msg.sender != tx.origin) revert NotOrigin();	// @audit-issue

507:        if (msg.sender == tx.origin && !isUsingFeeToken) {	// @audit-issue

568:        if (!isBatchPoster[msg.sender] && msg.sender != address(rollup)) revert NotBatchPoster();	// @audit-issue

591:        if (!isBatchPoster[msg.sender] && msg.sender != address(rollup)) revert NotBatchPoster();	// @audit-issue
```
[104](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/bridge/SequencerInbox.sol#L104-L104), [109](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/bridge/SequencerInbox.sol#L109-L109), [209](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/bridge/SequencerInbox.sol#L209-L209), [375](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/bridge/SequencerInbox.sol#L375-L375), [440](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/bridge/SequencerInbox.sol#L440-L440), [507](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/bridge/SequencerInbox.sol#L507-L507), [568](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/bridge/SequencerInbox.sol#L568-L568), [591](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/bridge/SequencerInbox.sol#L591-L591), 


```solidity
Path: ./src/rollup/RollupUserLogic.sol

258:        require(msg.sender == anyTrustFastConfirmer, "NOT_FAST_CONFIRMER");	// @audit-issue
```
[258](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/RollupUserLogic.sol#L258-L258), 


#### Recommendation

To optimize the validation of `msg.sender` in your Solidity code, consider using assembly to achieve this with the minimum number of opcodes required. You can refer to the detailed report [Here](https://code4rena.com/reports/2023-05-juicebox#g-06-use-assembly-to-validate-msgsender) for more insights and examples on efficient implementation.

### Use assembly to write hashes
Considering using [assembly](https://medium.com/@kalexotsu/understanding-solidity-assembly-hashing-a-string-from-calldata-fbd2ece82263) to write hashes, as it's possible to save a considerable amount of gas.


```solidity
Path: ./src/bridge/SequencerInbox.sol

667:        return (keccak256(header), timeBounds);	// @audit-issue

717:        return (keccak256(bytes.concat(header, data)), timeBounds);	// @audit-issue

744:            keccak256(bytes.concat(header, DATA_BLOB_HEADER_FLAG, abi.encodePacked(dataHashes))),	// @audit-issue

785:            keccak256(spendingReportMsg)	// @audit-issue

904:        uint256 ksWord = uint256(keccak256(bytes.concat(hex"fe", keccak256(keysetBytes))));	// @audit-issue
```
[667](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/bridge/SequencerInbox.sol#L667-L667), [717](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/bridge/SequencerInbox.sol#L717-L717), [744](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/bridge/SequencerInbox.sol#L744-L744), [785](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/bridge/SequencerInbox.sol#L785-L785), [904](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/bridge/SequencerInbox.sol#L904-L904), 


```solidity
Path: ./src/rollup/RollupLib.sol

44:            keccak256(	// @audit-issue

62:            keccak256(	// @audit-issue
```
[44](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/RollupLib.sol#L44-L44), [62](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/RollupLib.sol#L62-L62), 


```solidity
Path: ./src/rollup/BOLDUpgradeAction.sol

103:            keccak256(abi.encodePacked(executionState.globalState.hash(), inboxMaxCount, executionState.machineStatus));	// @audit-issue

498:        bytes32 rollupSalt = keccak256(abi.encode(config));	// @audit-issue

500:            Create2Upgradeable.computeAddress(rollupSalt, keccak256(type(RollupProxy).creationCode));	// @audit-issue
```
[103](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/BOLDUpgradeAction.sol#L103-L103), [498](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/BOLDUpgradeAction.sol#L498-L498), [500](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/BOLDUpgradeAction.sol#L500-L500), 


```solidity
Path: ./src/rollup/AssertionState.sol

23:        return keccak256(abi.encode(state));	// @audit-issue
```
[23](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/AssertionState.sol#L23-L23), 


```solidity
Path: ./src/rollup/RollupCreator.sol

188:        RollupProxy rollup = new RollupProxy{salt: keccak256(abi.encode(deployParams))}();	// @audit-issue
```
[188](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/RollupCreator.sol#L188-L188), 


```solidity
Path: ./src/challengeV2/libraries/MerkleTreeLib.sol

126:                        accum = keccak256(abi.encodePacked(accum, bytes32(0)));	// @audit-issue

132:                accum = keccak256(abi.encodePacked(val, accum));	// @audit-issue

135:                accum = keccak256(abi.encodePacked(accum, bytes32(0)));	// @audit-issue

213:                        accumHash = keccak256(abi.encodePacked(me[i], accumHash));	// @audit-issue

241:        return appendCompleteSubTree(me, 0, keccak256(abi.encodePacked(leaf)));	// @audit-issue

363:        bytes32 calculatedRoot = MerkleLib.calculateRoot(proof, index, keccak256(abi.encodePacked(leaf)));	// @audit-issue
```
[126](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/challengeV2/libraries/MerkleTreeLib.sol#L126-L126), [132](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/challengeV2/libraries/MerkleTreeLib.sol#L132-L132), [135](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/challengeV2/libraries/MerkleTreeLib.sol#L135-L135), [213](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/challengeV2/libraries/MerkleTreeLib.sol#L213-L213), [241](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/challengeV2/libraries/MerkleTreeLib.sol#L241-L241), [363](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/challengeV2/libraries/MerkleTreeLib.sol#L363-L363), 


```solidity
Path: ./src/challengeV2/libraries/ChallengeEdgeLib.sol

173:        return keccak256(abi.encodePacked(level, originId, startHeight, startHistoryRoot, endHeight));	// @audit-issue

197:        return keccak256(	// @audit-issue
```
[173](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/challengeV2/libraries/ChallengeEdgeLib.sol#L173-L173), [197](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/challengeV2/libraries/ChallengeEdgeLib.sol#L197-L197), 


```solidity
Path: ./src/assertionStakingPool/StakingPoolCreatorUtils.sol

14:        bytes32 bytecodeHash = keccak256(abi.encodePacked(creationCode, args));	// @audit-issue
```
[14](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/assertionStakingPool/StakingPoolCreatorUtils.sol#L14-L14), 


#### Recommendation

To achieve gas savings in your Solidity code when writing hashes, consider using assembly, as it can significantly reduce gas consumption. You can refer to this [article](https://medium.com/@kalexotsu/understanding-solidity-assembly-hashing-a-string-from-calldata-fbd2ece82263) for insights on how to efficiently implement hash operations.
## NonCritical Risk Issues


### Non-compliant `IERC20` tokens may revert with `transfer`
Some `IERC20` tokens (e.g. `BNB`, `OMG`, `USDT`) do not implement the standard properly, but they are still accepted by most code that accepts `ERC20` tokens.

For example, `USDT` transfer functions on L1 do not return booleans: when casted to `IERC20`, their function signatures do not match, and therefore the calls made will revert.

```solidity
Path: ./src/rollup/RollupUserLogic.sol

215:            IERC20(stakeToken).safeTransfer(loserStakeEscrow, assertion.beforeStateData.configData.requiredStake);	// @audit-issue

295:                IERC20(stakeToken).safeTransfer(loserStakeEscrow, assertion.beforeStateData.configData.requiredStake);	// @audit-issue

362:        IERC20(stakeToken).safeTransfer(msg.sender, amount);	// @audit-issue

367:        IERC20(stakeToken).safeTransferFrom(msg.sender, address(this), tokenAmount);	// @audit-issue
```
[215](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/RollupUserLogic.sol#L215-L215), [295](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/RollupUserLogic.sol#L295-L295), [362](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/RollupUserLogic.sol#L362-L362), [367](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/RollupUserLogic.sol#L367-L367), 


```solidity
Path: ./src/rollup/RollupCreator.sol

312:            IERC20(_nativeToken).safeTransferFrom(msg.sender, _inbox, totalFee);	// @audit-issue
```
[312](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/RollupCreator.sol#L312-L312), 


```solidity
Path: ./src/challengeV2/EdgeChallengeManager.sol

434:            st.safeTransferFrom(msg.sender, receiver, sa);	// @audit-issue

581:            st.safeTransfer(edge.staker, sa);	// @audit-issue
```
[434](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/challengeV2/EdgeChallengeManager.sol#L434-L434), [581](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/challengeV2/EdgeChallengeManager.sol#L581-L581), 


```solidity
Path: ./src/assertionStakingPool/AbsBoldStakingPool.sol

35:        IERC20(stakeToken).safeTransferFrom(msg.sender, address(this), amount);	// @audit-issue

51:        IERC20(stakeToken).safeTransfer(msg.sender, amount);	// @audit-issue
```
[35](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/assertionStakingPool/AbsBoldStakingPool.sol#L35-L35), [51](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/assertionStakingPool/AbsBoldStakingPool.sol#L51-L51), 


#### Recommendation

When dealing with tokens that may not fully comply with the `IERC20` standard, it's important to exercise caution and carefully verify the behavior of the specific token in question. In cases where tokens do not return booleans for transfer functions, consider implementing additional error-handling mechanisms to account for potential failures. This may include checking the token balance before and after the transfer to detect any discrepancies or using try-catch blocks to handle potential exceptions. Ensuring robust error handling can help your smart contract interact more gracefully with non-compliant tokens while maintaining security and reliability.

### Floating Pragma
A "floating pragma" in Solidity refers to the practice of using a pragma statement that does not specify a fixed compiler version but instead allows the contract to be compiled with any compatible compiler version. This issue arises when pragma statements like `pragma solidity ^0.8.0;` are used without a specific version number, allowing the contract to be compiled with the latest available compiler version. This can lead to various compatibility and stability issues.


```solidity
Path: ./src/bridge/SequencerInbox.sol

5:pragma solidity ^0.8.0;	// @audit-issue
```
[5](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/bridge/SequencerInbox.sol#L5-L5), 


```solidity
Path: ./src/bridge/DelayBuffer.sol

5:pragma solidity ^0.8.0;	// @audit-issue
```
[5](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/bridge/DelayBuffer.sol#L5-L5), 


```solidity
Path: ./src/rollup/IRollupLogic.sol

5:pragma solidity ^0.8.0;	// @audit-issue
```
[5](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/IRollupLogic.sol#L5-L5), 


```solidity
Path: ./src/rollup/RollupLib.sol

5:pragma solidity ^0.8.0;	// @audit-issue
```
[5](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/RollupLib.sol#L5-L5), 


```solidity
Path: ./src/rollup/BOLDUpgradeAction.sol

5:pragma solidity ^0.8.0;	// @audit-issue
```
[5](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/BOLDUpgradeAction.sol#L5-L5), 


```solidity
Path: ./src/rollup/Assertion.sol

5:pragma solidity ^0.8.0;	// @audit-issue
```
[5](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/Assertion.sol#L5-L5), 


```solidity
Path: ./src/rollup/AssertionState.sol

5:pragma solidity ^0.8.0;	// @audit-issue
```
[5](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/AssertionState.sol#L5-L5), 


```solidity
Path: ./src/rollup/BridgeCreator.sol

5:pragma solidity ^0.8.0;	// @audit-issue
```
[5](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/BridgeCreator.sol#L5-L5), 


```solidity
Path: ./src/rollup/RollupCore.sol

5:pragma solidity ^0.8.0;	// @audit-issue
```
[5](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/RollupCore.sol#L5-L5), 


```solidity
Path: ./src/rollup/IRollupCore.sol

5:pragma solidity ^0.8.0;	// @audit-issue
```
[5](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/IRollupCore.sol#L5-L5), 


```solidity
Path: ./src/rollup/RollupUserLogic.sol

5:pragma solidity ^0.8.0;	// @audit-issue
```
[5](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/RollupUserLogic.sol#L5-L5), 


```solidity
Path: ./src/rollup/RollupCreator.sol

5:pragma solidity ^0.8.0;	// @audit-issue
```
[5](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/RollupCreator.sol#L5-L5), 


```solidity
Path: ./src/rollup/RollupAdminLogic.sol

5:pragma solidity ^0.8.0;	// @audit-issue
```
[5](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/RollupAdminLogic.sol#L5-L5), 


```solidity
Path: ./src/rollup/IRollupAdmin.sol

5:pragma solidity ^0.8.0;	// @audit-issue
```
[5](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/IRollupAdmin.sol#L5-L5), 


```solidity
Path: ./src/rollup/Config.sol

5:pragma solidity ^0.8.0;	// @audit-issue
```
[5](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/Config.sol#L5-L5), 


```solidity
Path: ./src/rollup/RollupProxy.sol

5:pragma solidity ^0.8.0;	// @audit-issue
```
[5](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/RollupProxy.sol#L5-L5), 


```solidity
Path: ./src/libraries/Error.sol

5:pragma solidity ^0.8.4;	// @audit-issue
```
[5](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/libraries/Error.sol#L5-L5), 


```solidity
Path: ./src/challengeV2/IAssertionChain.sol

5:pragma solidity ^0.8.17;	// @audit-issue
```
[5](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/challengeV2/IAssertionChain.sol#L5-L5), 


```solidity
Path: ./src/challengeV2/EdgeChallengeManager.sol

5:pragma solidity ^0.8.17;	// @audit-issue
```
[5](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/challengeV2/EdgeChallengeManager.sol#L5-L5), 


```solidity
Path: ./src/challengeV2/libraries/ArrayUtilsLib.sol

5:pragma solidity ^0.8.17;	// @audit-issue
```
[5](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/challengeV2/libraries/ArrayUtilsLib.sol#L5-L5), 


```solidity
Path: ./src/challengeV2/libraries/EdgeChallengeManagerLib.sol

5:pragma solidity ^0.8.17;	// @audit-issue
```
[5](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/challengeV2/libraries/EdgeChallengeManagerLib.sol#L5-L5), 


```solidity
Path: ./src/challengeV2/libraries/MerkleTreeLib.sol

5:pragma solidity ^0.8.17;	// @audit-issue
```
[5](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/challengeV2/libraries/MerkleTreeLib.sol#L5-L5), 


```solidity
Path: ./src/challengeV2/libraries/ChallengeEdgeLib.sol

5:pragma solidity ^0.8.17;	// @audit-issue
```
[5](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/challengeV2/libraries/ChallengeEdgeLib.sol#L5-L5), 


```solidity
Path: ./src/challengeV2/libraries/UintUtilsLib.sol

5:pragma solidity ^0.8.17;	// @audit-issue
```
[5](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/challengeV2/libraries/UintUtilsLib.sol#L5-L5), 


```solidity
Path: ./src/challengeV2/libraries/ChallengeErrors.sol

5:pragma solidity ^0.8.17;	// @audit-issue
```
[5](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/challengeV2/libraries/ChallengeErrors.sol#L5-L5), 


```solidity
Path: ./src/challengeV2/libraries/Enums.sol

5:pragma solidity ^0.8.17;	// @audit-issue
```
[5](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/challengeV2/libraries/Enums.sol#L5-L5), 


```solidity
Path: ./src/assertionStakingPool/AssertionStakingPoolCreator.sol

6:pragma solidity ^0.8.0;	// @audit-issue
```
[6](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/assertionStakingPool/AssertionStakingPoolCreator.sol#L6-L6), 


```solidity
Path: ./src/assertionStakingPool/EdgeStakingPool.sol

5:pragma solidity ^0.8.0;	// @audit-issue
```
[5](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/assertionStakingPool/EdgeStakingPool.sol#L5-L5), 


```solidity
Path: ./src/assertionStakingPool/StakingPoolCreatorUtils.sol

6:pragma solidity ^0.8.0;	// @audit-issue
```
[6](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/assertionStakingPool/StakingPoolCreatorUtils.sol#L6-L6), 


```solidity
Path: ./src/assertionStakingPool/EdgeStakingPoolCreator.sol

6:pragma solidity ^0.8.0;	// @audit-issue
```
[6](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/assertionStakingPool/EdgeStakingPoolCreator.sol#L6-L6), 


```solidity
Path: ./src/assertionStakingPool/AssertionStakingPool.sol

6:pragma solidity ^0.8.0;	// @audit-issue
```
[6](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/assertionStakingPool/AssertionStakingPool.sol#L6-L6), 


```solidity
Path: ./src/assertionStakingPool/AbsBoldStakingPool.sol

5:pragma solidity ^0.8.0;	// @audit-issue
```
[5](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/assertionStakingPool/AbsBoldStakingPool.sol#L5-L5), 


```solidity
Path: ./src/assertionStakingPool/interfaces/IAssertionStakingPool.sol

5:pragma solidity ^0.8.0;	// @audit-issue
```
[5](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/assertionStakingPool/interfaces/IAssertionStakingPool.sol#L5-L5), 


```solidity
Path: ./src/assertionStakingPool/interfaces/IEdgeStakingPool.sol

5:pragma solidity ^0.8.0;	// @audit-issue
```
[5](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/assertionStakingPool/interfaces/IEdgeStakingPool.sol#L5-L5), 


```solidity
Path: ./src/assertionStakingPool/interfaces/IEdgeStakingPoolCreator.sol

5:pragma solidity ^0.8.0;	// @audit-issue
```
[5](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/assertionStakingPool/interfaces/IEdgeStakingPoolCreator.sol#L5-L5), 


```solidity
Path: ./src/assertionStakingPool/interfaces/IAbsBoldStakingPool.sol

5:pragma solidity ^0.8.0;	// @audit-issue
```
[5](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/assertionStakingPool/interfaces/IAbsBoldStakingPool.sol#L5-L5), 


```solidity
Path: ./src/assertionStakingPool/interfaces/IAssertionStakingPoolCreator.sol

5:pragma solidity ^0.8.0;	// @audit-issue
```
[5](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/assertionStakingPool/interfaces/IAssertionStakingPoolCreator.sol#L5-L5), 


#### Recommendation

Consider locking the pragma version whenever possible and avoid using a floating pragma in the final deployment. [Consider known bugs](https://github.com/ethereum/solidity/releases) for the compiler version that is chosen.

### `tx.origin == msg.sender` control blocks MultiSig wallets
The use of the control check `tx.origin == msg.sender` in certain functions of the smart contract can impede multisig wallet users. This security measure, while preventing certain types of attacks, also restricts multisig wallets from calling these functions, as the immediate sender (the multisig contract) differs from the original transaction initiator.


```solidity
Path: ./src/bridge/SequencerInbox.sol

375:        if (msg.sender != tx.origin) revert NotOrigin();	// @audit-issue

440:        if (msg.sender != tx.origin) revert NotOrigin();	// @audit-issue
```
[375](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/bridge/SequencerInbox.sol#L375-L375), [440](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/bridge/SequencerInbox.sol#L440-L440), 


#### Recommendation

Consider revising the contract logic to accommodate multisig wallet interactions, perhaps by implementing alternative security measures or allowing specific multisig wallets. This adjustment would maintain security while enhancing usability for multisig wallet users.

### Ownership Irrevocability Vulnerability
The smart contract under inspection inherits from the `Ownable` library, which provides basic authorization control functions, simplifying the implementation of user permissions. However, the contract does not provide a mechanism to transfer ownership to another address or account, and it retains the default `renounceOwnership` function from `Ownable`.  
Given this, once the owner renounces ownership using the `renounceOwnership` function, the contract becomes ownerless. As evidenced in the provided transaction logs, after the `renounceOwnership` function is called, attempts to call functions that require owner permissions fail with the error message: `"Ownable: caller is not the owner."`  
This state renders the contract's adjustable parameters immutable and potentially makes the contract useless for any future administrative changes that might be necessary.

```solidity
Path: ./src/rollup/BridgeCreator.sol

21:contract BridgeCreator is Ownable {	// @audit-issue
```
[21](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/BridgeCreator.sol#L21-L21), 


```solidity
Path: ./src/rollup/RollupCreator.sol

17:contract RollupCreator is Ownable {	// @audit-issue
```
[17](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/RollupCreator.sol#L17-L17), 


#### Recommendation


To mitigate this vulnerability:
* Override the renounceOwnership function to revert transactions: By overriding this function to simply revert any transaction, it will become impossible for the contract owner to unintentionally (or intentionally) render the contract ownerless and thus immutable.
* Implement an ownership transfer function: While the Ownable library does provide a transferOwnership function, if this is not present or has been removed from the current contract, it should be re-implemented to ensure there is a way to transfer ownership in future scenarios.


### Unneeded initializations of bool variable to `false`.
In Solidity, it is common practice to initialize variables with default values when declaring them. However, initializing `bool`variables to `false` when they are not subsequently used in the code can lead to unnecessary gas consumption and code clutter. This issue points out instances where such initializations are present but serve no functional purpose.

```solidity
Path: ./src/bridge/SequencerInbox.sol

187:        bool actualIsUsingFeeToken = false;	// @audit-issue
```
[187](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/bridge/SequencerInbox.sol#L187-L187), 


#### Recommendation


It is recommended not to initialize boolean variables to `false` to save some Gas.


### Unneeded initializations of integer variable to `0`.
In Solidity, it is common practice to initialize variables with default values when declaring them. However, initializing integer variables to `0` when they are not subsequently used in the code can lead to unnecessary gas consumption and code clutter. This issue points out instances where such initializations are present but serve no functional purpose.

```solidity
Path: ./src/bridge/SequencerInbox.sol

317:        bytes32 prevDelayedAcc = 0;	// @audit-issue
```
[317](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/bridge/SequencerInbox.sol#L317-L317), 


```solidity
Path: ./src/rollup/BOLDUpgradeAction.sol

350:        for (uint64 i = 0; i < stakerCount; i++) {	// @audit-issue

528:            for (uint256 i = 0; i < validators.length; i++) {	// @audit-issue
```
[350](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/BOLDUpgradeAction.sol#L350-L350), [528](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/BOLDUpgradeAction.sol#L528-L528), 


```solidity
Path: ./src/rollup/RollupCreator.sol

225:        for (uint256 i = 0; i < deployParams.batchPosters.length; i++) {	// @audit-issue

235:            for (uint256 i = 0; i < deployParams.validators.length; i++) {	// @audit-issue
```
[225](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/RollupCreator.sol#L225-L225), [235](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/RollupCreator.sol#L235-L235), 


```solidity
Path: ./src/rollup/RollupAdminLogic.sol

184:        for (uint256 i = 0; i < _validator.length; i++) {	// @audit-issue

230:        for (uint256 i = 0; i < staker.length; i++) {	// @audit-issue
```
[184](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/RollupAdminLogic.sol#L184-L184), [230](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/RollupAdminLogic.sol#L230-L230), 


```solidity
Path: ./src/challengeV2/EdgeChallengeManager.sol

492:        for (uint256 i = 0; i < edgeIds.length; i++) {	// @audit-issue

517:        uint64 assertionBlocks = 0;	// @audit-issue
```
[492](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/challengeV2/EdgeChallengeManager.sol#L492-L492), [517](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/challengeV2/EdgeChallengeManager.sol#L517-L517), 


```solidity
Path: ./src/challengeV2/libraries/ArrayUtilsLib.sol

15:        for (uint256 i = 0; i < arr.length; i++) {	// @audit-issue

47:        for (uint256 i = 0; i < arr1.length; i++) {	// @audit-issue

50:        for (uint256 i = 0; i < arr2.length; i++) {	// @audit-issue
```
[15](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/challengeV2/libraries/ArrayUtilsLib.sol#L15-L15), [47](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/challengeV2/libraries/ArrayUtilsLib.sol#L47-L47), [50](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/challengeV2/libraries/ArrayUtilsLib.sol#L50-L50), 


```solidity
Path: ./src/challengeV2/libraries/MerkleTreeLib.sol

114:        bytes32 accum = 0;	// @audit-issue

115:        for (uint256 i = 0; i < me.length; i++) {	// @audit-issue

188:        for (uint256 i = 0; i < me.length; i++) {	// @audit-issue

293:        uint256 sum = 0;	// @audit-issue

294:        for (uint256 i = 0; i < me.length; i++) {	// @audit-issue

326:        uint256 proofIndex = 0;	// @audit-issue
```
[114](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/challengeV2/libraries/MerkleTreeLib.sol#L114-L114), [115](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/challengeV2/libraries/MerkleTreeLib.sol#L115-L115), [188](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/challengeV2/libraries/MerkleTreeLib.sol#L188-L188), [293](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/challengeV2/libraries/MerkleTreeLib.sol#L293-L293), [294](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/challengeV2/libraries/MerkleTreeLib.sol#L294-L294), [326](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/challengeV2/libraries/MerkleTreeLib.sol#L326-L326), 


#### Recommendation


It is recommended not to initialize integer variables to `0` to save some Gas.


### Use transfer libraries instead of low level calls
Consider using `SafeTransferLib.safeTransferETH` or `Address.sendValue` for clearer semantic meaning instead of using a low level call.

```solidity
Path: ./src/rollup/RollupCreator.sol

304:            (bool sent, ) = msg.sender.call{value: address(this).balance}("");	// @audit-issue
```
[304](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/RollupCreator.sol#L304-L304), 


#### Recommendation

To improve code readability and safety, consider using higher-level transfer libraries like `SafeTransferLib.safeTransferETH` or `Address.sendValue` instead of low-level calls for handling Ether transfers. These libraries provide clearer semantic meaning and help prevent common pitfalls associated with low-level calls.

### Unused arguments should be removed or implemented
In Solidity, functions often have arguments that are intended for specific operations or logic within the function. However, sometimes these arguments remain unused in the function body, either due to changes during development or oversight. Unused arguments in functions can lead to confusion, making the code less readable and potentially misleading for other developers who might use or audit the contract. Moreover, they can create a false impression of the function's purpose and behavior. It's crucial to either implement these arguments in the function's logic as originally intended or remove them to ensure clarity and efficiency of the code.

```solidity
Path: ./src/bridge/SequencerInbox.sol

360:        IGasRefunder	// @audit-issue: None
```
[360](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/bridge/SequencerInbox.sol#L360-L360), 


```solidity
Path: ./src/rollup/RollupAdminLogic.sol

166:    function _authorizeUpgrade(address newImplementation) internal override {}	// @audit-issue: newImplementation

171:    function _authorizeSecondaryUpgrade(address newImplementation) internal override {}	// @audit-issue: newImplementation
```
[166](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/RollupAdminLogic.sol#L166-L166), [171](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/RollupAdminLogic.sol#L171-L171), 


#### Recommendation

Eliminate unused arguments in Solidity function definitions to enhance code clarity and efficiency. If an argument is currently not utilized in the function's logic, assess its potential future utility. If it serves no purpose, removing it simplifies the function signature and aligns the code more closely with its actual operation, contributing to a cleaner and more understandable contract structure.

### `else`-block not required
One level of nesting can be removed by not having an `else` block when the `if`-block returns, and `if (foo) { return 1; } else { return 2; }` becomes `if (foo) { return 1; } return 2;`


```solidity
Path: ./src/bridge/SequencerInbox.sol

279:        if (_chainIdChanged()) {
280:            return (1, 1, 1, 1);
281:        } else {	// @audit-issue
282:            return (delayBlocks, futureBlocks, delaySeconds, futureSeconds);
283:        }
```
[281](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/bridge/SequencerInbox.sol#L279-L283), 


```solidity
Path: ./src/rollup/RollupCore.sol

146:        if (_hostChainIsArbitrum) {
147:            uint256 blockNum = _assertionCreatedAtArbSysBlock[assertionHash];
148:            require(blockNum > 0, "NO_ASSERTION");
149:            return blockNum;
150:        } else {	// @audit-issue
151:            AssertionNode storage assertion = getAssertionStorage(assertionHash);
152:            assertion.requireExists();
153:            return assertion.createdAtBlock;
154:        }
```
[150](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/RollupCore.sol#L146-L154), 


```solidity
Path: ./src/challengeV2/EdgeChallengeManager.sol

596:        } else if (eType == EdgeType.SmallStep) {
597:            return LAYERZERO_SMALLSTEPEDGE_HEIGHT;
598:        } else {	// @audit-issue
599:            revert InvalidEdgeType(eType);
600:        }
```
[598](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/challengeV2/EdgeChallengeManager.sol#L596-L600), 


```solidity
Path: ./src/challengeV2/libraries/EdgeChallengeManagerLib.sol

220:        if (ChallengeEdgeLib.levelToType(args.level, numBigStepLevel) == EdgeType.Block) {
221:            // origin id is the assertion which is the root of challenge
222:            // all rivals and their children share the same origin id - it is a link to the information
223:            // they agree on
224:            bytes32 originId = ard.predecessorId;
225:
226:            // Sanity check: The assertion reference data should be related to the claim
227:            // Of course the caller can provide whatever args they wish, so this is really just a helpful
228:            // check to avoid mistakes
229:            if (ard.assertionHash == 0) {
230:                revert AssertionHashEmpty();
231:            }
232:            if (ard.assertionHash != args.claimId) {
233:                revert AssertionHashMismatch(ard.assertionHash, args.claimId);
234:            }
235:
236:            // if the assertion is already confirmed or rejected then it cant be referenced as a claim
237:            if (!ard.isPending) {
238:                revert AssertionNotPending();
239:            }
240:
241:            // if the claim doesnt have a sibling then it is undisputed, there's no need
242:            // to open challenge edges for it
243:            if (!ard.hasSibling) {
244:                revert AssertionNoSibling();
245:            }
246:
247:            // parse the inclusion proof for later use
248:            if (args.proof.length == 0) {
249:                revert EmptyEdgeSpecificProof();
250:            }
251:            (bytes32[] memory inclusionProof,,) =
252:                abi.decode(args.proof, (bytes32[], AssertionStateData, AssertionStateData));
253:
254:            // check the start and end execution states exist, the block hash entry should be non zero
255:            if (ard.startState.machineStatus == MachineStatus.RUNNING) {
256:                revert EmptyStartMachineStatus();
257:            }
258:            if (ard.endState.machineStatus == MachineStatus.RUNNING) {
259:                revert EmptyEndMachineStatus();
260:            }
261:
262:            // Create machine hashes out of the proven state
263:            bytes32 startStateHash = oneStepProofEntry.getMachineHash(ard.startState.toExecutionState());
264:            bytes32 endStateHash = oneStepProofEntry.getMachineHash(ard.endState.toExecutionState());
265:
266:            return (ProofData(startStateHash, endStateHash, inclusionProof), originId);
267:        } else {	// @audit-issue
268:            // Claim must be length one. If it is unrivaled then its unrivaled time is ticking up, so there's
269:            // no need to create claims against it
270:            if (!hasLengthOneRival(store, args.claimId)) {
271:                revert ClaimEdgeNotLengthOneRival(args.claimId);
272:            }
273:
274:            // hasLengthOneRival checks existance, so we can use getNoCheck
275:            ChallengeEdge storage claimEdge = getNoCheck(store, args.claimId);
276:
277:            // origin id is the mutual id of the claim
278:            // all rivals and their children share the same origin id - it is a link to the information
279:            // they agree on
280:            bytes32 originId = claimEdge.mutualId();
281:
282:            // once a claim is confirmed it's status can never become pending again, so there is no point
283:            // opening a challenge that references it
284:            if (claimEdge.status != EdgeStatus.Pending) {
285:                revert ClaimEdgeNotPending();
286:            }
287:
288:            // the edge must be a level up from the claim
289:            if (args.level != nextEdgeLevel(claimEdge.level, numBigStepLevel)) {
290:                revert ClaimEdgeInvalidLevel(args.level, claimEdge.level);
291:            }
292:
293:            // parse the proofs
294:            if (args.proof.length == 0) {
295:                revert EmptyEdgeSpecificProof();
296:            }
297:            (
298:                bytes32 startState,
299:                bytes32 endState,
300:                bytes32[] memory claimStartInclusionProof,
301:                bytes32[] memory claimEndInclusionProof,
302:                bytes32[] memory edgeInclusionProof
303:            ) = abi.decode(args.proof, (bytes32, bytes32, bytes32[], bytes32[], bytes32[]));
304:
305:            // if the start and end states are consistent with the claim edge
306:            // this guarantees that the edge we're creating is a 'continuation' of the claim edge, it is
307:            // a commitment to the states that between start and end states of the claim
308:            MerkleTreeLib.verifyInclusionProof(
309:                claimEdge.startHistoryRoot, startState, claimEdge.startHeight, claimStartInclusionProof
310:            );
311:
312:            // it's doubly important to check the end state since if the end state since the claim id is
313:            // not part of the edge id, so we need to ensure that it's not possible to create two edges of the
314:            // same id, but with different claim id. Ensuring that the end state is linked to the claim,
315:            // and later ensuring that the end state is part of the history commitment of the new edge ensures
316:            // that the end history root of the new edge will be different for different claim ids, and therefore
317:            // the edge ids will be different
318:            MerkleTreeLib.verifyInclusionProof(
319:                claimEdge.endHistoryRoot, endState, claimEdge.endHeight, claimEndInclusionProof
320:            );
321:
322:            return (ProofData(startState, endState, edgeInclusionProof), originId);
323:        }

551:        if (firstRival == UNRIVALED) {
552:            return block.number - store.edges[edgeId].createdAtBlock;
553:        } else {	// @audit-issue
554:            // Sanity check: it's not possible an edge does not exist for a first rival record
555:            if (!store.edges[firstRival].exists()) {
556:                revert EdgeNotExists(firstRival);
557:            }
558:
559:            // rivals exist for this edge
560:            uint256 firstRivalCreatedAtBlock = store.edges[firstRival].createdAtBlock;
561:            uint256 edgeCreatedAtBlock = store.edges[edgeId].createdAtBlock;
562:            if (firstRivalCreatedAtBlock > edgeCreatedAtBlock) {
563:                // if this edge was created before the first rival then we return the difference
564:                // in createdAtBlock number
565:                return firstRivalCreatedAtBlock - edgeCreatedAtBlock;
566:            } else {
567:                // if this was created at the same time as, or after the the first rival
568:                // then we return 0
569:                return 0;
570:            }
571:        }

562:            if (firstRivalCreatedAtBlock > edgeCreatedAtBlock) {
563:                // if this edge was created before the first rival then we return the difference
564:                // in createdAtBlock number
565:                return firstRivalCreatedAtBlock - edgeCreatedAtBlock;
566:            } else {	// @audit-issue
567:                // if this was created at the same time as, or after the the first rival
568:                // then we return 0
569:                return 0;
570:            }
```
[267](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/challengeV2/libraries/EdgeChallengeManagerLib.sol#L220-L323), [553](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/challengeV2/libraries/EdgeChallengeManagerLib.sol#L551-L571), [566](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/challengeV2/libraries/EdgeChallengeManagerLib.sol#L562-L570), 


```solidity
Path: ./src/challengeV2/libraries/ChallengeEdgeLib.sol

284:        } else if (level == numBigStepLevels + 1) {
285:            return EdgeType.SmallStep;
286:        } else {	// @audit-issue
287:            revert LevelTooHigh(level, numBigStepLevels);
288:        }
```
[286](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/challengeV2/libraries/ChallengeEdgeLib.sol#L284-L288), 


```solidity
Path: ./src/assertionStakingPool/StakingPoolCreatorUtils.sol

16:        if (Address.isContract(pool)) {
17:            return pool;
18:        } else {	// @audit-issue
19:            revert PoolDoesntExist();
20:        }
```
[18](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/assertionStakingPool/StakingPoolCreatorUtils.sol#L16-L20), 


#### Recommendation

Consider simplifying code by removing unnecessary `else` blocks when the `if` block returns. You can achieve cleaner and more concise code by directly returning a value after the `if` block instead of using an `else` block for a subsequent return statement.

### Unused import
The identifier is imported but never used within the file.

```solidity
Path: ./src/bridge/SequencerInbox.sol

7:import {	// @audit-issue: BadPostUpgradeInit not used in the contract.
8:    AlreadyInit,
9:    HadZeroInit,
10:    BadPostUpgradeInit,
11:    NotOrigin,
12:    DataTooLarge,
13:    DelayedBackwards,
14:    DelayedTooFar,
15:    ForceIncludeBlockTooSoon,
16:    ForceIncludeTimeTooSoon,
17:    IncorrectMessagePreimage,
18:    NotBatchPoster,
19:    BadSequencerNumber,
20:    AlreadyValidDASKeyset,
21:    NoSuchKeyset,
22:    NotForked,
23:    NotBatchPosterManager,
24:    RollupNotChanged,
25:    DataBlobsNotSupported,
26:    InitParamZero,
27:    MissingDataHashes,
28:    NotOwner,
29:    InvalidHeaderFlag,
30:    NativeTokenMismatch,
31:    BadMaxTimeVariation,
32:    Deprecated,
33:    NotDelayBufferable,
34:    InvalidDelayedAccPreimage,
35:    DelayProofRequired,
36:    BadBufferConfig,
37:    ExtraGasNotUint64,
38:    KeysetTooLarge
39:} from "../libraries/Error.sol";

7:import {	// @audit-issue: ForceIncludeTimeTooSoon not used in the contract.
8:    AlreadyInit,
9:    HadZeroInit,
10:    BadPostUpgradeInit,
11:    NotOrigin,
12:    DataTooLarge,
13:    DelayedBackwards,
14:    DelayedTooFar,
15:    ForceIncludeBlockTooSoon,
16:    ForceIncludeTimeTooSoon,
17:    IncorrectMessagePreimage,
18:    NotBatchPoster,
19:    BadSequencerNumber,
20:    AlreadyValidDASKeyset,
21:    NoSuchKeyset,
22:    NotForked,
23:    NotBatchPosterManager,
24:    RollupNotChanged,
25:    DataBlobsNotSupported,
26:    InitParamZero,
27:    MissingDataHashes,
28:    NotOwner,
29:    InvalidHeaderFlag,
30:    NativeTokenMismatch,
31:    BadMaxTimeVariation,
32:    Deprecated,
33:    NotDelayBufferable,
34:    InvalidDelayedAccPreimage,
35:    DelayProofRequired,
36:    BadBufferConfig,
37:    ExtraGasNotUint64,
38:    KeysetTooLarge
39:} from "../libraries/Error.sol";

49:import {L1MessageType_batchPostingReport} from "../libraries/MessageTypes.sol";	// @audit-issue: L1MessageType_batchPostingReport not used in the contract.
```
[7](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/bridge/SequencerInbox.sol#L7-L39), [7](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/bridge/SequencerInbox.sol#L7-L39), [49](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/bridge/SequencerInbox.sol#L49-L49), 


```solidity
Path: ./src/rollup/RollupUserLogic.sol

13:import {ETH_POS_BLOCK_TIME} from "../libraries/Constants.sol";	// @audit-issue: ETH_POS_BLOCK_TIME not used in the contract.
```
[13](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/./src/rollup/RollupUserLogic.sol#L13-L13), 


#### Recommendation

Regularly review your Solidity code to remove unused imports. This practice declutters the codebase, making it easier to understand and maintain. In addition, consider using tools or IDE features that can automatically detect and highlight unused imports for cleanup. Keeping imports limited to only what is necessary helps maintain a clear understanding of the contract's dependencies and reduces potential confusion for developers working on or reviewing the code.

### Excessive Authorization in Contract Functions
A contract where a high percentage of functions require authorization (e.g., restricted to the contract owner or specific roles) may indicate over-centralization or excessive control. This could limit the contract's flexibility, reduce trust among users, and potentially create bottleneck points that could be exploited or become failure points. While some level of control is necessary for administrative purposes, overly restrictive access can detract from the decentralized nature of blockchain applications and concentrate too much power in the hands of a few.

```solidity
Path: ./src/rollup/BridgeCreator.sol

21:contract BridgeCreator is Ownable {	// @audit-issue: %66.66666666666666 amount of external/public and non-view/non-pure functions are required authorization to call.
	List of total functions: `createBridge`, `updateERC20Templates`, `updateTemplates`
	List of functions that require authorization: `updateERC20Templates`, `updateTemplates`
