2024-05-arbitrum-foundation QA Report
___
## Table of Contents
1. [Summary](#summary)

    1. [Low Risk Issues](#summary-low-risk-issues)

1. [Details](#details)

    1. [Low Risk Issues](#details-low-risk-issues)
___
## <a id="summary"></a> Summary

### <a id="summary-low-risk-issues"></a> Low Risk Issues
There are 104 instances over 14 issues.
|      ID       | Description                                                                                                          | Count |
| :-----------: | :------------------------------------------------------------------------------------------------------------------- | ----: |
| [L-01](#l-01) | Casting of `block.timestamp` can reduce the lifespan of a contract                                                   |     2 |
| [L-02](#l-02) | `constructor`/`initialize` function lacks parameter validation                                                       |     7 |
| [L-03](#l-03) | Critical functions should be a two step procedure                                                                    |     8 |
| [L-04](#l-04) | Execution at deadlines should be allowed                                                                             |     1 |
| [L-05](#l-05) | `for` and `while` loops in `public` or `external` functions should be avoided due to high gas costs and possible DOS |     6 |
| [L-06](#l-06) | `internal` function calls within loops                                                                               |     3 |
| [L-07](#l-07) | Large transfers may not work with some `ERC20` tokens                                                                |     9 |
| [L-08](#l-08) | Missing zero address check in constructor/initializer                                                                |     6 |
| [L-09](#l-09) | Missing zero address check in functions with address parameters                                                      |    49 |
| [L-10](#l-10) | Numbers downcast to `address`es may result in collisions                                                             |     1 |
| [L-11](#l-11) | `onlyOwner` functions not accessible if owner renounces ownership                                                    |     3 |
| [L-12](#l-12) | Upgradeable contract is not using OpenZeppelin upgradeable contracts/libraries                                       |     1 |
| [L-13](#l-13) | Use of `assert()`                                                                                                    |     2 |
| [L-14](#l-14) | Vulnerable versions of packages are being used                                                                       |     6 |

## <a id="details"></a> Details

### <a id="details-low-risk-issues"></a> Low Risk Issues
#### <a id="l-01"></a> \[L-01\] Casting of `block.timestamp` can reduce the lifespan of a contract
##### Description:
Contract timekeeping may break earlier than the Ethereum network itself will stop working. When a timestamp is downcast from `uint256` to `uint32`, the value will wrap in the year 2106, and the contracts will break. Other downcasts will have different end dates. Consider whether the contract is intended to live past the size of the type being used.

##### Recommendation:
Consider removing the casting to ensure future functionality.

##### Instances:
There are 2 instances of this issue.
```solidity
File: src/bridge/SequencerInbox.sol

225:             bounds.minTimestamp = uint64(block.timestamp) - delaySeconds_;

227:         bounds.maxTimestamp = uint64(block.timestamp) + futureSeconds_;
```

| File Link                                                                                                               | Instance Count | Instance Links                                                                                                                                                                                                              |
| :---------------------------------------------------------------------------------------------------------------------- | -------------: | :-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| [SequencerInbox.sol](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/bridge/SequencerInbox.sol) |              2 | [225](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/bridge/SequencerInbox.sol#L225),[227](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/bridge/SequencerInbox.sol#L227) |
___
#### <a id="l-02"></a> \[L-02\] `constructor`/`initialize` function lacks parameter validation
##### Description:
Constructors and initialization functions play a critical role in contracts by setting important initial states when the contract is first deployed before the system starts. The parameters passed to the constructor and initialization functions directly affect the behavior of the contract / protocol. If incorrect parameters are provided, the system may fail to run, behave abnormally, be unstable, or lack security. Therefore, it is crucial to carefully check each parameter in the constructor and initialization functions. If an exception is found, the transaction should be rolled back.

##### Recommendation:
Consider whether reasonable bounds checks for variables would be useful.

##### Instances:
There are 7 instances of this issue.
<details><summary>View 7 Instances</summary>

```solidity
File: src/assertionStakingPool/AssertionStakingPool.sol

/// @audit parameter not validated: _assertionHash
31:     constructor(
32:         address _rollup,
33:         bytes32 _assertionHash
34:     ) AbsBoldStakingPool(IRollupCore(_rollup).stakeToken()) {
```

| File Link                                                                                                                                         | Instance Count | Instance Link                                                                                                                   |
| :------------------------------------------------------------------------------------------------------------------------------------------------ | -------------: | :------------------------------------------------------------------------------------------------------------------------------ |
| [AssertionStakingPool.sol](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/assertionStakingPool/AssertionStakingPool.sol) |              1 | [31](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/assertionStakingPool/AssertionStakingPool.sol#L31) |
___
```solidity
File: src/assertionStakingPool/EdgeStakingPool.sol

/// @audit parameter not validated: _edgeId
35:     constructor(
36:         address _challengeManager,
37:         bytes32 _edgeId
38:     ) AbsBoldStakingPool(address(EdgeChallengeManager(_challengeManager).stakeToken())) {
```

| File Link                                                                                                                               | Instance Count | Instance Link                                                                                                              |
| :-------------------------------------------------------------------------------------------------------------------------------------- | -------------: | :------------------------------------------------------------------------------------------------------------------------- |
| [EdgeStakingPool.sol](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/assertionStakingPool/EdgeStakingPool.sol) |              1 | [35](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/assertionStakingPool/EdgeStakingPool.sol#L35) |
___
```solidity
File: src/bridge/SequencerInbox.sol

/// @audit parameter not validated: _maxDataSize
140:     constructor(
141:         uint256 _maxDataSize,
142:         IReader4844 reader4844_,
143:         bool _isUsingFeeToken,
144:         bool _isDelayBufferable
145:     ) {
```

| File Link                                                                                                               | Instance Count | Instance Link                                                                                                 |
| :---------------------------------------------------------------------------------------------------------------------- | -------------: | :------------------------------------------------------------------------------------------------------------ |
| [SequencerInbox.sol](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/bridge/SequencerInbox.sol) |              1 | [140](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/bridge/SequencerInbox.sol#L140) |
___
```solidity
File: src/rollup/BOLDUpgradeAction.sol

/// @audit parameter not validated: __array
169:     constructor(uint256[] memory __array) {

/// @audit parameters not validated: contracts, implementations, settings
287:     constructor(
288:         Contracts memory contracts,
289:         ProxyAdmins memory proxyAdmins,
290:         Implementations memory implementations,
291:         Settings memory settings
292:     ) {
```

| File Link                                                                                                                     | Instance Count | Instance Links                                                                                                                                                                                                                    |
| :---------------------------------------------------------------------------------------------------------------------------- | -------------: | :-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| [BOLDUpgradeAction.sol](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/rollup/BOLDUpgradeAction.sol) |              2 | [169](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/rollup/BOLDUpgradeAction.sol#L169),[287](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/rollup/BOLDUpgradeAction.sol#L287) |
___
```solidity
File: src/rollup/BridgeCreator.sol

/// @audit parameters not validated: _ethBasedTemplates, _erc20BasedTemplates
45:     constructor(
46:         BridgeTemplates memory _ethBasedTemplates,
47:         BridgeTemplates memory _erc20BasedTemplates
48:     ) Ownable() {
```

| File Link                                                                                                             | Instance Count | Instance Link                                                                                              |
| :-------------------------------------------------------------------------------------------------------------------- | -------------: | :--------------------------------------------------------------------------------------------------------- |
| [BridgeCreator.sol](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/rollup/BridgeCreator.sol) |              1 | [45](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/rollup/BridgeCreator.sol#L45) |
___
```solidity
File: src/rollup/RollupAdminLogic.sol

/// @audit parameter not validated: connectedContracts
18:     function initialize(Config calldata config, ContractDependencies calldata connectedContracts)
19:         external
20:         override
21:         onlyProxy
22:         initializer
23:     {
```

| File Link                                                                                                                   | Instance Count | Instance Link                                                                                                 |
| :-------------------------------------------------------------------------------------------------------------------------- | -------------: | :------------------------------------------------------------------------------------------------------------ |
| [RollupAdminLogic.sol](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/rollup/RollupAdminLogic.sol) |              1 | [18](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/rollup/RollupAdminLogic.sol#L18) |
___
</details>

#### <a id="l-03"></a> \[L-03\] Critical functions should be a two step procedure
##### Description:
Critical functions in Solidity contracts should follow a two-step procedure to enhance security, minimize human error, and ensure proper access control. By dividing sensitive operations into two distinct phases, such as initiation and confirmation, developers can introduce a safeguard against unintended actions or unauthorized access.

##### Instances:
There are 8 instances of this issue.
<details><summary>View 8 Instances</summary>

```solidity
File: src/bridge/SequencerInbox.sol

885:     function setMaxTimeVariation(ISequencerInbox.MaxTimeVariation memory maxTimeVariation_)
886:         external
887:         onlyRollupOwner
888:     {

894:     function setIsBatchPoster(address addr, bool isBatchPoster_)
895:         external
896:         onlyRollupOwnerOrBatchPosterManager
897:     {

933:     function setIsSequencer(address addr, bool isSequencer_)
934:         external
935:         onlyRollupOwnerOrBatchPosterManager
936:     {

942:     function setBatchPosterManager(address newBatchPosterManager) external onlyRollupOwner {

947:     function setBufferConfig(BufferConfig memory bufferConfig_) external onlyRollupOwner {
```

| File Link                                                                                                               | Instance Count | Instance Links                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                        |
| :---------------------------------------------------------------------------------------------------------------------- | -------------: | :-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| [SequencerInbox.sol](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/bridge/SequencerInbox.sol) |              5 | [885](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/bridge/SequencerInbox.sol#L885),[894](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/bridge/SequencerInbox.sol#L894),[933](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/bridge/SequencerInbox.sol#L933),[942](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/bridge/SequencerInbox.sol#L942),[947](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/bridge/SequencerInbox.sol#L947) |
___
```solidity
File: src/rollup/BridgeCreator.sol

53:     function updateTemplates(BridgeTemplates calldata _newTemplates) external onlyOwner {

58:     function updateERC20Templates(BridgeTemplates calldata _newTemplates) external onlyOwner {
```

| File Link                                                                                                             | Instance Count | Instance Links                                                                                                                                                                                                        |
| :-------------------------------------------------------------------------------------------------------------------- | -------------: | :-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| [BridgeCreator.sol](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/rollup/BridgeCreator.sol) |              2 | [53](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/rollup/BridgeCreator.sol#L53),[58](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/rollup/BridgeCreator.sol#L58) |
___
```solidity
File: src/rollup/RollupCreator.sol

63:     function setTemplates(
64:         BridgeCreator _bridgeCreator,
65:         IOneStepProofEntry _osp,
66:         IEdgeChallengeManager _challengeManagerLogic,
67:         IRollupAdmin _rollupAdminLogic,
68:         IRollupUser _rollupUserLogic,
69:         IUpgradeExecutor _upgradeExecutorLogic,
70:         address _validatorWalletCreator,
71:         DeployHelper _l2FactoriesDeployer
72:     ) external onlyOwner {
```

| File Link                                                                                                             | Instance Count | Instance Link                                                                                              |
| :-------------------------------------------------------------------------------------------------------------------- | -------------: | :--------------------------------------------------------------------------------------------------------- |
| [RollupCreator.sol](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/rollup/RollupCreator.sol) |              1 | [63](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/rollup/RollupCreator.sol#L63) |
___
</details>

#### <a id="l-04"></a> \[L-04\] Execution at deadlines should be allowed
##### Description:
The condition may be wrong in these cases since when `block.timestamp` is equal to the value being compared to using  `>` or `<` these blocks will not be executed.

##### Instances:
There is 1 instance of this issue.
```solidity
File: src/bridge/SequencerInbox.sol

224:         if (block.timestamp > delaySeconds_) {
```

| File Link                                                                                                               | Instance Count | Instance Link                                                                                                 |
| :---------------------------------------------------------------------------------------------------------------------- | -------------: | :------------------------------------------------------------------------------------------------------------ |
| [SequencerInbox.sol](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/bridge/SequencerInbox.sol) |              1 | [224](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/bridge/SequencerInbox.sol#L224) |
___
#### <a id="l-05"></a> \[L-05\] `for` and `while` loops in `public` or `external` functions should be avoided due to high gas costs and possible DOS
##### Description:
In Solidity, `for` and `while` loops can potentially cause denial of service (DOS) attacks if not handled carefully. DOS attacks can occur when an attacker intentionally exploits the gas cost of a function, causing it to run out of gas or making it too expensive for other users to call. Below are some scenarios where `for` or `while` loops can lead to DOS attacks: Nested `for` and `while` loops can become exceptionally gas expensive and should be used sparingly.

##### Instances:
There are 6 instances of this issue.
<details><summary>View 6 Instances</summary>

```solidity
File: src/challengeV2/EdgeChallengeManager.sol

/// @audit public function multiUpdateTimeCacheByChildren()
492:         for (uint256 i = 0; i < edgeIds.length; i++) {
```

| File Link                                                                                                                                | Instance Count | Instance Link                                                                                                            |
| :--------------------------------------------------------------------------------------------------------------------------------------- | -------------: | :----------------------------------------------------------------------------------------------------------------------- |
| [EdgeChallengeManager.sol](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/challengeV2/EdgeChallengeManager.sol) |              1 | [492](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/challengeV2/EdgeChallengeManager.sol#L492) |
___
```solidity
File: src/rollup/BOLDUpgradeAction.sol

/// @audit external function perform()
528:             for (uint256 i = 0; i < validators.length; i++) {
```

| File Link                                                                                                                     | Instance Count | Instance Link                                                                                                    |
| :---------------------------------------------------------------------------------------------------------------------------- | -------------: | :--------------------------------------------------------------------------------------------------------------- |
| [BOLDUpgradeAction.sol](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/rollup/BOLDUpgradeAction.sol) |              1 | [528](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/rollup/BOLDUpgradeAction.sol#L528) |
___
```solidity
File: src/rollup/RollupAdminLogic.sol

/// @audit external function setValidator()
184:         for (uint256 i = 0; i < _validator.length; i++) {

/// @audit external function forceRefundStaker()
230:         for (uint256 i = 0; i < staker.length; i++) {
```

| File Link                                                                                                                   | Instance Count | Instance Links                                                                                                                                                                                                                  |
| :-------------------------------------------------------------------------------------------------------------------------- | -------------: | :------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| [RollupAdminLogic.sol](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/rollup/RollupAdminLogic.sol) |              2 | [184](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/rollup/RollupAdminLogic.sol#L184),[230](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/rollup/RollupAdminLogic.sol#L230) |
___
```solidity
File: src/rollup/RollupCreator.sol

/// @audit public function createRollup()
225:         for (uint256 i = 0; i < deployParams.batchPosters.length; i++) {

/// @audit public function createRollup()
235:             for (uint256 i = 0; i < deployParams.validators.length; i++) {
```

| File Link                                                                                                             | Instance Count | Instance Links                                                                                                                                                                                                            |
| :-------------------------------------------------------------------------------------------------------------------- | -------------: | :------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| [RollupCreator.sol](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/rollup/RollupCreator.sol) |              2 | [225](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/rollup/RollupCreator.sol#L225),[235](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/rollup/RollupCreator.sol#L235) |
___
</details>

#### <a id="l-06"></a> \[L-06\] `internal` function calls within loops
##### Description:
Making internal function calls within loops in Solidity can lead to inefficient gas usage, potential bottlenecks, and increased vulnerability to denial of service (DOS) attacks. Each function call consumes gas, and when executed within a loop, the gas cost multiplies, potentially causing the transaction to run out of gas or exceed block gas limits. This can result in transaction failure or unpredictable behavior.

##### Instances:
There are 3 instances of this issue.
```solidity
File: src/challengeV2/libraries/EdgeChallengeManagerLib.sol

/// @audit get()
451:             edge = get(store, lowerLevelId);
```

| File Link                                                                                                                                                | Instance Count | Instance Link                                                                                                                         |
| :------------------------------------------------------------------------------------------------------------------------------------------------------- | -------------: | :------------------------------------------------------------------------------------------------------------------------------------ |
| [EdgeChallengeManagerLib.sol](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/challengeV2/libraries/EdgeChallengeManagerLib.sol) |              1 | [451](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/challengeV2/libraries/EdgeChallengeManagerLib.sol#L451) |
___
```solidity
File: src/challengeV2/libraries/MerkleTreeLib.sol

/// @audit maximumAppendBetween()
333:             uint256 level = maximumAppendBetween(size, postSize);

/// @audit appendCompleteSubTree()
336:             exp = appendCompleteSubTree(exp, level, proof[proofIndex]);
```

| File Link                                                                                                                            | Instance Count | Instance Links                                                                                                                                                                                                                                          |
| :----------------------------------------------------------------------------------------------------------------------------------- | -------------: | :------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| [MerkleTreeLib.sol](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/challengeV2/libraries/MerkleTreeLib.sol) |              2 | [333](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/challengeV2/libraries/MerkleTreeLib.sol#L333),[336](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/challengeV2/libraries/MerkleTreeLib.sol#L336) |
___
#### <a id="l-07"></a> \[L-07\] Large transfers may not work with some `ERC20` tokens
##### Description:
Some `IERC20` implementations (e.g., `UNI`, `COMP`) may fail if the valued transferred is larger than `uint96`. [Source](https://github.com/d-xo/weird-erc20/blob/main/src/Uint96.sol).

##### Recommendation:
Check the actual balance before and after vs. the expected balance.

##### Instances:
There are 9 instances of this issue.
<details><summary>View 9 Instances</summary>

```solidity
File: src/assertionStakingPool/AbsBoldStakingPool.sol

/// @audit uint256 amount
35:         IERC20(stakeToken).safeTransferFrom(msg.sender, address(this), amount);

/// @audit uint256 amount
51:         IERC20(stakeToken).safeTransfer(msg.sender, amount);
```

| File Link                                                                                                                                     | Instance Count | Instance Links                                                                                                                                                                                                                                              |
| :-------------------------------------------------------------------------------------------------------------------------------------------- | -------------: | :---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| [AbsBoldStakingPool.sol](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/assertionStakingPool/AbsBoldStakingPool.sol) |              2 | [35](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/assertionStakingPool/AbsBoldStakingPool.sol#L35),[51](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/assertionStakingPool/AbsBoldStakingPool.sol#L51) |
___
```solidity
File: src/challengeV2/EdgeChallengeManager.sol

/// @audit uint256 sa
434:             st.safeTransferFrom(msg.sender, receiver, sa);

/// @audit uint256 sa
581:             st.safeTransfer(edge.staker, sa);
```

| File Link                                                                                                                                | Instance Count | Instance Links                                                                                                                                                                                                                                    |
| :--------------------------------------------------------------------------------------------------------------------------------------- | -------------: | :------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| [EdgeChallengeManager.sol](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/challengeV2/EdgeChallengeManager.sol) |              2 | [434](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/challengeV2/EdgeChallengeManager.sol#L434),[581](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/challengeV2/EdgeChallengeManager.sol#L581) |
___
```solidity
File: src/rollup/RollupCreator.sol

/// @audit uint256 totalFee
312:             IERC20(_nativeToken).safeTransferFrom(msg.sender, _inbox, totalFee);
```

| File Link                                                                                                             | Instance Count | Instance Link                                                                                                |
| :-------------------------------------------------------------------------------------------------------------------- | -------------: | :----------------------------------------------------------------------------------------------------------- |
| [RollupCreator.sol](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/rollup/RollupCreator.sol) |              1 | [312](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/rollup/RollupCreator.sol#L312) |
___
```solidity
File: src/rollup/RollupUserLogic.sol

/// @audit uint256 requiredStake
215:             IERC20(stakeToken).safeTransfer(loserStakeEscrow, assertion.beforeStateData.configData.requiredStake);

/// @audit uint256 requiredStake
295:                 IERC20(stakeToken).safeTransfer(loserStakeEscrow, assertion.beforeStateData.configData.requiredStake);

/// @audit uint256 amount
362:         IERC20(stakeToken).safeTransfer(msg.sender, amount);

/// @audit uint256 tokenAmount
367:         IERC20(stakeToken).safeTransferFrom(msg.sender, address(this), tokenAmount);
```

| File Link                                                                                                                 | Instance Count | Instance Links                                                                                                                                                                                                                                                                                                                                                                                                                                              |
| :------------------------------------------------------------------------------------------------------------------------ | -------------: | :---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| [RollupUserLogic.sol](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/rollup/RollupUserLogic.sol) |              4 | [215](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/rollup/RollupUserLogic.sol#L215),[295](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/rollup/RollupUserLogic.sol#L295),[362](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/rollup/RollupUserLogic.sol#L362),[367](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/rollup/RollupUserLogic.sol#L367) |
___
</details>

#### <a id="l-08"></a> \[L-08\] Missing zero address check in constructor/initializer
##### Description:
Constructors and initializer functions often take address parameters to initialize important components of a contract, such as the owner or linked contracts. However, without validation, there is a risk that an address parameter could be mistakenly set to the zero address (0x0) due to an error or an oversight during contract deployment. A zero address in a crucial role can cause serious issues, as it cannot perform actions like a normal address. Any funds sent to it will be irretrievable. It is therefore crucial to include a zero address check in constructors to prevent such problems. If a zero address is detected, the constructor should revert the transaction.

##### Recommendation:
Consider adding explicit zero-address validation prior to use of `address` parameters in constructors.

##### Instances:
There are 6 instances of this issue.
<details><summary>View 6 Instances</summary>

```solidity
File: src/assertionStakingPool/AbsBoldStakingPool.sol

/// @audit Not checked against address zero: _stakeToken
24:     constructor(address _stakeToken) {
```

| File Link                                                                                                                                     | Instance Count | Instance Link                                                                                                                 |
| :-------------------------------------------------------------------------------------------------------------------------------------------- | -------------: | :---------------------------------------------------------------------------------------------------------------------------- |
| [AbsBoldStakingPool.sol](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/assertionStakingPool/AbsBoldStakingPool.sol) |              1 | [24](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/assertionStakingPool/AbsBoldStakingPool.sol#L24) |
___
```solidity
File: src/assertionStakingPool/AssertionStakingPool.sol

/// @audit Not checked against address zero: _rollup
31:     constructor(
32:         address _rollup,
33:         bytes32 _assertionHash
34:     ) AbsBoldStakingPool(IRollupCore(_rollup).stakeToken()) {
```

| File Link                                                                                                                                         | Instance Count | Instance Link                                                                                                                   |
| :------------------------------------------------------------------------------------------------------------------------------------------------ | -------------: | :------------------------------------------------------------------------------------------------------------------------------ |
| [AssertionStakingPool.sol](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/assertionStakingPool/AssertionStakingPool.sol) |              1 | [31](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/assertionStakingPool/AssertionStakingPool.sol#L31) |
___
```solidity
File: src/assertionStakingPool/EdgeStakingPool.sol

/// @audit Not checked against address zero: _challengeManager
35:     constructor(
36:         address _challengeManager,
37:         bytes32 _edgeId
38:     ) AbsBoldStakingPool(address(EdgeChallengeManager(_challengeManager).stakeToken())) {
```

| File Link                                                                                                                               | Instance Count | Instance Link                                                                                                              |
| :-------------------------------------------------------------------------------------------------------------------------------------- | -------------: | :------------------------------------------------------------------------------------------------------------------------- |
| [EdgeStakingPool.sol](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/assertionStakingPool/EdgeStakingPool.sol) |              1 | [35](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/assertionStakingPool/EdgeStakingPool.sol#L35) |
___
```solidity
File: src/bridge/SequencerInbox.sol

/// @audit Not checked against address zero: reader4844_
140:     constructor(
141:         uint256 _maxDataSize,
142:         IReader4844 reader4844_,
143:         bool _isUsingFeeToken,
144:         bool _isDelayBufferable
145:     ) {
```

| File Link                                                                                                               | Instance Count | Instance Link                                                                                                 |
| :---------------------------------------------------------------------------------------------------------------------- | -------------: | :------------------------------------------------------------------------------------------------------------ |
| [SequencerInbox.sol](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/bridge/SequencerInbox.sol) |              1 | [140](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/bridge/SequencerInbox.sol#L140) |
___
```solidity
File: src/challengeV2/EdgeChallengeManager.sol

/// @audit Not checked against address zero: _stakeToken
305:     function initialize(
306:         IAssertionChain _assertionChain,
307:         uint64 _challengePeriodBlocks,
308:         IOneStepProofEntry _oneStepProofEntry,
309:         uint256 layerZeroBlockEdgeHeight,
310:         uint256 layerZeroBigStepEdgeHeight,
311:         uint256 layerZeroSmallStepEdgeHeight,
312:         IERC20 _stakeToken,
313:         address _excessStakeReceiver,
314:         uint8 _numBigStepLevel,
315:         uint256[] calldata _stakeAmounts
316:     ) public initializer {
```

| File Link                                                                                                                                | Instance Count | Instance Link                                                                                                            |
| :--------------------------------------------------------------------------------------------------------------------------------------- | -------------: | :----------------------------------------------------------------------------------------------------------------------- |
| [EdgeChallengeManager.sol](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/challengeV2/EdgeChallengeManager.sol) |              1 | [305](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/challengeV2/EdgeChallengeManager.sol#L305) |
___
```solidity
File: src/rollup/BOLDUpgradeAction.sol

/// @audit Not checked against address zero: _rollup
126:     constructor(IOldRollup _rollup) {
```

| File Link                                                                                                                     | Instance Count | Instance Link                                                                                                    |
| :---------------------------------------------------------------------------------------------------------------------------- | -------------: | :--------------------------------------------------------------------------------------------------------------- |
| [BOLDUpgradeAction.sol](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/rollup/BOLDUpgradeAction.sol) |              1 | [126](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/rollup/BOLDUpgradeAction.sol#L126) |
___
</details>

#### <a id="l-09"></a> \[L-09\] Missing zero address check in functions with address parameters
##### Description:
A zero address in a crucial role can cause serious issues, as it cannot perform actions like a normal address. Any funds sent to it will be irretrievable. Even for protected functions, an explicit zero address check can prevent user errors due to typos, copy/paste errors, and similar.

##### Recommendation:
Consider adding explicit zero-address validation prior to use of `address` parameters in functions.

##### Instances:
There are 49 instances of this issue.
<details><summary>View 49 Instances</summary>

```solidity
File: src/assertionStakingPool/AssertionStakingPoolCreator.sol

/// @audit Not checked against address zero: _rollup
15:     function createPool(
16:         address _rollup,
17:         bytes32 _assertionHash
18:     ) external returns (IAssertionStakingPool) {

/// @audit Not checked against address zero: _rollup
25:     function getPool(
26:         address _rollup,
27:         bytes32 _assertionHash
28:     ) public view returns (IAssertionStakingPool) {
```

| File Link                                                                                                                                                       | Instance Count | Instance Links                                                                                                                                                                                                                                                                |
| :-------------------------------------------------------------------------------------------------------------------------------------------------------------- | -------------: | :---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| [AssertionStakingPoolCreator.sol](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/assertionStakingPool/AssertionStakingPoolCreator.sol) |              2 | [15](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/assertionStakingPool/AssertionStakingPoolCreator.sol#L15),[25](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/assertionStakingPool/AssertionStakingPoolCreator.sol#L25) |
___
```solidity
File: src/assertionStakingPool/EdgeStakingPoolCreator.sol

/// @audit Not checked against address zero: challengeManager
15:     function createPool(
16:         address challengeManager,
17:         bytes32 edgeId
18:     ) external returns (IEdgeStakingPool) {

/// @audit Not checked against address zero: challengeManager
25:     function getPool(
26:         address challengeManager,
27:         bytes32 edgeId
28:     ) public view returns (IEdgeStakingPool) {
```

| File Link                                                                                                                                             | Instance Count | Instance Links                                                                                                                                                                                                                                                      |
| :---------------------------------------------------------------------------------------------------------------------------------------------------- | -------------: | :------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| [EdgeStakingPoolCreator.sol](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/assertionStakingPool/EdgeStakingPoolCreator.sol) |              2 | [15](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/assertionStakingPool/EdgeStakingPoolCreator.sol#L15),[25](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/assertionStakingPool/EdgeStakingPoolCreator.sol#L25) |
___
```solidity
File: src/bridge/SequencerInbox.sol

/// @audit Not checked against address zero: sender
287:     function forceInclusion(
288:         uint256 _totalDelayedMessagesRead,
289:         uint8 kind,
290:         uint64[2] calldata l1BlockAndTime,
291:         uint256 baseFeeL1,
292:         address sender,
293:         bytes32 messageDataHash
294:     ) external {

/// @audit Not checked against address zero:
356:     function addSequencerL2BatchFromOrigin(
357:         uint256,
358:         bytes calldata,
359:         uint256,
360:         IGasRefunder
361:     ) external pure {

/// @audit Not checked against address zero: gasRefunder
366:     function addSequencerL2BatchFromOrigin(
367:         uint256 sequenceNumber,
368:         bytes calldata data,
369:         uint256 afterDelayedMessagesRead,
370:         IGasRefunder gasRefunder,
371:         uint256 prevMessageCount,
372:         uint256 newMessageCount
373:     ) external refundsGas(gasRefunder, IReader4844(address(0))) {

/// @audit Not checked against address zero: gasRefunder
390:     function addSequencerL2BatchFromBlobs(
391:         uint256 sequenceNumber,
392:         uint256 afterDelayedMessagesRead,
393:         IGasRefunder gasRefunder,
394:         uint256 prevMessageCount,
395:         uint256 newMessageCount
396:     ) external refundsGas(gasRefunder, reader4844) {

/// @audit Not checked against address zero: gasRefunder
409:     function addSequencerL2BatchFromBlobsDelayProof(
410:         uint256 sequenceNumber,
411:         uint256 afterDelayedMessagesRead,
412:         IGasRefunder gasRefunder,
413:         uint256 prevMessageCount,
414:         uint256 newMessageCount,
415:         DelayProof calldata delayProof
416:     ) external refundsGas(gasRefunder, reader4844) {

/// @audit Not checked against address zero: gasRefunder
430:     function addSequencerL2BatchFromOriginDelayProof(
431:         uint256 sequenceNumber,
432:         bytes calldata data,
433:         uint256 afterDelayedMessagesRead,
434:         IGasRefunder gasRefunder,
435:         uint256 prevMessageCount,
436:         uint256 newMessageCount,
437:         DelayProof calldata delayProof
438:     ) external refundsGas(gasRefunder, IReader4844(address(0))) {

/// @audit Not checked against address zero: gasRefunder
560:     function addSequencerL2Batch(
561:         uint256 sequenceNumber,
562:         bytes calldata data,
563:         uint256 afterDelayedMessagesRead,
564:         IGasRefunder gasRefunder,
565:         uint256 prevMessageCount,
566:         uint256 newMessageCount
567:     ) external override refundsGas(gasRefunder, IReader4844(address(0))) {

/// @audit Not checked against address zero: gasRefunder
582:     function addSequencerL2BatchDelayProof(
583:         uint256 sequenceNumber,
584:         bytes calldata data,
585:         uint256 afterDelayedMessagesRead,
586:         IGasRefunder gasRefunder,
587:         uint256 prevMessageCount,
588:         uint256 newMessageCount,
589:         DelayProof calldata delayProof
590:     ) external refundsGas(gasRefunder, IReader4844(address(0))) {

/// @audit Not checked against address zero: addr
894:     function setIsBatchPoster(address addr, bool isBatchPoster_)
895:         external
896:         onlyRollupOwnerOrBatchPosterManager
897:     {

/// @audit Not checked against address zero: addr
933:     function setIsSequencer(address addr, bool isSequencer_)
934:         external
935:         onlyRollupOwnerOrBatchPosterManager
936:     {

/// @audit Not checked against address zero: newBatchPosterManager
942:     function setBatchPosterManager(address newBatchPosterManager) external onlyRollupOwner {
```

| File Link                                                                                                               | Instance Count | Instance Links                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                            |
| :---------------------------------------------------------------------------------------------------------------------- | -------------: | :-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| [SequencerInbox.sol](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/bridge/SequencerInbox.sol) |             11 | [287](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/bridge/SequencerInbox.sol#L287),[356](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/bridge/SequencerInbox.sol#L356),[366](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/bridge/SequencerInbox.sol#L366),[390](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/bridge/SequencerInbox.sol#L390),[409](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/bridge/SequencerInbox.sol#L409),[430](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/bridge/SequencerInbox.sol#L430),[560](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/bridge/SequencerInbox.sol#L560),[582](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/bridge/SequencerInbox.sol#L582),[894](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/bridge/SequencerInbox.sol#L894),[933](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/bridge/SequencerInbox.sol#L933),[942](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/bridge/SequencerInbox.sol#L942) |
___
```solidity
File: src/challengeV2/EdgeChallengeManager.sol

/// @audit Not checked against address zero: account
672:     function hasMadeLayerZeroRival(address account, bytes32 mutualId) external view returns (bool) {
```

| File Link                                                                                                                                | Instance Count | Instance Link                                                                                                            |
| :--------------------------------------------------------------------------------------------------------------------------------------- | -------------: | :----------------------------------------------------------------------------------------------------------------------- |
| [EdgeChallengeManager.sol](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/challengeV2/EdgeChallengeManager.sol) |              1 | [672](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/challengeV2/EdgeChallengeManager.sol#L672) |
___
```solidity
File: src/challengeV2/libraries/EdgeChallengeManagerLib.sol

/// @audit Not checked against address zero: oneStepProofEntry
213:     function layerZeroTypeSpecificChecks(
214:         EdgeStore storage store,
215:         CreateEdgeArgs calldata args,
216:         AssertionReferenceData memory ard,
217:         IOneStepProofEntry oneStepProofEntry,
218:         uint8 numBigStepLevel
219:     ) private view returns (ProofData memory, bytes32) {

/// @audit Not checked against address zero: oneStepProofEntry
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
```

| File Link                                                                                                                                                | Instance Count | Instance Links                                                                                                                                                                                                                                                              |
| :------------------------------------------------------------------------------------------------------------------------------------------------------- | -------------: | :-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| [EdgeChallengeManagerLib.sol](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/challengeV2/libraries/EdgeChallengeManagerLib.sol) |              2 | [213](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/challengeV2/libraries/EdgeChallengeManagerLib.sol#L213),[766](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/challengeV2/libraries/EdgeChallengeManagerLib.sol#L766) |
___
```solidity
File: src/rollup/BOLDUpgradeAction.sol

/// @audit Not checked against address zero: staker
150:     function getStaker(address staker) external view returns (OldStaker memory) {

/// @audit Not checked against address zero: validator
154:     function isValidator(address validator) external view returns (bool) {
```

| File Link                                                                                                                     | Instance Count | Instance Links                                                                                                                                                                                                                    |
| :---------------------------------------------------------------------------------------------------------------------------- | -------------: | :-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| [BOLDUpgradeAction.sol](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/rollup/BOLDUpgradeAction.sol) |              2 | [150](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/rollup/BOLDUpgradeAction.sol#L150),[154](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/rollup/BOLDUpgradeAction.sol#L154) |
___
```solidity
File: src/rollup/BridgeCreator.sol

/// @audit Not checked against address zero: adminProxy
63:     function _createBridge(
64:         address adminProxy,
65:         BridgeTemplates memory templates,
66:         bool isDelayBufferable
67:     ) internal returns (BridgeContracts memory) {

/// @audit Not checked against address zero: adminProxy, rollup
 99:     function createBridge(
100:         address adminProxy,
101:         address rollup,
102:         address nativeToken,
103:         ISequencerInbox.MaxTimeVariation calldata maxTimeVariation,
104:         BufferConfig calldata bufferConfig
105:     ) external returns (BridgeContracts memory) {
```

| File Link                                                                                                             | Instance Count | Instance Links                                                                                                                                                                                                        |
| :-------------------------------------------------------------------------------------------------------------------- | -------------: | :-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| [BridgeCreator.sol](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/rollup/BridgeCreator.sol) |              2 | [63](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/rollup/BridgeCreator.sol#L63),[99](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/rollup/BridgeCreator.sol#L99) |
___
```solidity
File: src/rollup/RollupAdminLogic.sol

/// @audit Not checked against address zero: _outbox
127:     function removeOldOutbox(address _outbox) external override {

/// @audit Not checked against address zero: newOwner
195:     function setOwner(address newOwner) external override {

/// @audit Not checked against address zero: _sequencerInbox
290:     function setSequencerInbox(address _sequencerInbox) external override {

/// @audit Not checked against address zero: newInbox
299:     function setInbox(IInboxBase newInbox) external {

/// @audit Not checked against address zero: _anyTrustFastConfirmer
317:     function setAnyTrustFastConfirmer(address _anyTrustFastConfirmer) external {

/// @audit Not checked against address zero: _challengeManager
326:     function setChallengeManager(address _challengeManager) external {
```

| File Link                                                                                                                   | Instance Count | Instance Links                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                  |
| :-------------------------------------------------------------------------------------------------------------------------- | -------------: | :---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| [RollupAdminLogic.sol](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/rollup/RollupAdminLogic.sol) |              6 | [127](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/rollup/RollupAdminLogic.sol#L127),[195](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/rollup/RollupAdminLogic.sol#L195),[290](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/rollup/RollupAdminLogic.sol#L290),[299](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/rollup/RollupAdminLogic.sol#L299),[317](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/rollup/RollupAdminLogic.sol#L317),[326](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/rollup/RollupAdminLogic.sol#L326) |
___
```solidity
File: src/rollup/RollupCore.sol

/// @audit Not checked against address zero: staker
171:     function isStaked(address staker) public view override returns (bool) {

/// @audit Not checked against address zero: staker
180:     function latestStakedAssertion(address staker) public view override returns (bytes32) {

/// @audit Not checked against address zero: staker
189:     function amountStaked(address staker) public view override returns (uint256) {

/// @audit Not checked against address zero: staker
198:     function getStaker(address staker) external view override returns (Staker memory) {

/// @audit Not checked against address zero: user
207:     function withdrawableFunds(address user) external view override returns (uint256) {

/// @audit Not checked against address zero: stakerAddress, withdrawalAddress
274:     function createNewStake(address stakerAddress, uint256 depositAmount, address withdrawalAddress) internal {

/// @audit Not checked against address zero: stakerAddress
286:     function increaseStakeBy(address stakerAddress, uint256 amountAdded) internal {

/// @audit Not checked against address zero: stakerAddress
300:     function reduceStakeTo(address stakerAddress, uint256 target) internal returns (uint256) {

/// @audit Not checked against address zero: stakerAddress
317:     function withdrawStaker(address stakerAddress) internal {

/// @audit Not checked against address zero: account
331:     function withdrawFunds(address account) internal returns (uint256) {

/// @audit Not checked against address zero: account
343:     function increaseWithdrawableFunds(address account, uint256 amount) internal {

/// @audit Not checked against address zero: stakerAddress
355:     function deleteStaker(address stakerAddress) private {

/// @audit Not checked against address zero: stakerAddress
565:     function requireInactiveStaker(address stakerAddress) internal view {
```

| File Link                                                                                                       | Instance Count | Instance Links                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                    |
| :-------------------------------------------------------------------------------------------------------------- | -------------: | :-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| [RollupCore.sol](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/rollup/RollupCore.sol) |             13 | [171](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/rollup/RollupCore.sol#L171),[180](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/rollup/RollupCore.sol#L180),[189](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/rollup/RollupCore.sol#L189),[198](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/rollup/RollupCore.sol#L198),[207](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/rollup/RollupCore.sol#L207),[274](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/rollup/RollupCore.sol#L274),[286](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/rollup/RollupCore.sol#L286),[300](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/rollup/RollupCore.sol#L300),[317](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/rollup/RollupCore.sol#L317),[331](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/rollup/RollupCore.sol#L331),[343](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/rollup/RollupCore.sol#L343),[355](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/rollup/RollupCore.sol#L355),[565](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/rollup/RollupCore.sol#L565) |
___
```solidity
File: src/rollup/RollupCreator.sol

/// @audit Not checked against address zero: _bridgeCreator, _osp, _challengeManagerLogic, _rollupAdminLogic, _rollupUserLogic, _upgradeExecutorLogic, _validatorWalletCreator, _l2FactoriesDeployer
63:     function setTemplates(
64:         BridgeCreator _bridgeCreator,
65:         IOneStepProofEntry _osp,
66:         IEdgeChallengeManager _challengeManagerLogic,
67:         IRollupAdmin _rollupAdminLogic,
68:         IRollupUser _rollupUserLogic,
69:         IUpgradeExecutor _upgradeExecutorLogic,
70:         address _validatorWalletCreator,
71:         DeployHelper _l2FactoriesDeployer
72:     ) external onlyOwner {

/// @audit Not checked against address zero: rollupAddr, proxyAdminAddr
85:     function createChallengeManager(address rollupAddr, address proxyAdminAddr, Config memory config)
86:         internal
87:         returns (IEdgeChallengeManager)
88:     {

/// @audit Not checked against address zero: rollupOwner
267:     function _deployUpgradeExecutor(address rollupOwner, ProxyAdmin proxyAdmin)
268:         internal
269:         returns (address)
270:     {

/// @audit Not checked against address zero: _inbox
287:     function _deployFactories(
288:         address _inbox,
289:         address _nativeToken,
290:         uint256 _maxFeePerGas
291:     ) internal {
```

| File Link                                                                                                             | Instance Count | Instance Links                                                                                                                                                                                                                                                                                                                                                                                                                                  |
| :-------------------------------------------------------------------------------------------------------------------- | -------------: | :---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| [RollupCreator.sol](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/rollup/RollupCreator.sol) |              4 | [63](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/rollup/RollupCreator.sol#L63),[85](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/rollup/RollupCreator.sol#L85),[267](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/rollup/RollupCreator.sol#L267),[287](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/rollup/RollupCreator.sol#L287) |
___
```solidity
File: src/rollup/RollupLib.sol

/// @audit Not checked against address zero: challengeManager
54:     function configHash(
55:         bytes32 wasmModuleRoot,
56:         uint256 requiredStake,
57:         address challengeManager,
58:         uint64 confirmPeriodBlocks,
59:         uint64 nextInboxPosition
60:     ) internal pure returns (bytes32) {
```

| File Link                                                                                                     | Instance Count | Instance Link                                                                                          |
| :------------------------------------------------------------------------------------------------------------ | -------------: | :----------------------------------------------------------------------------------------------------- |
| [RollupLib.sol](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/rollup/RollupLib.sol) |              1 | [54](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/rollup/RollupLib.sol#L54) |
___
```solidity
File: src/rollup/RollupUserLogic.sol

/// @audit Not checked against address zero: withdrawalAddress
137:     function _newStake(uint256 depositAmount, address withdrawalAddress) internal onlyValidator whenNotPaused {

/// @audit Not checked against address zero: stakerAddress
232:     function _addToDeposit(address stakerAddress, uint256 depositAmount) internal onlyValidator whenNotPaused {

/// @audit Not checked against address zero: stakerAddress
349:     function addToDeposit(address stakerAddress, uint256 tokenAmount) external onlyValidator whenNotPaused {
```

| File Link                                                                                                                 | Instance Count | Instance Links                                                                                                                                                                                                                                                                                                                               |
| :------------------------------------------------------------------------------------------------------------------------ | -------------: | :------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| [RollupUserLogic.sol](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/rollup/RollupUserLogic.sol) |              3 | [137](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/rollup/RollupUserLogic.sol#L137),[232](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/rollup/RollupUserLogic.sol#L232),[349](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/rollup/RollupUserLogic.sol#L349) |
___
</details>

#### <a id="l-10"></a> \[L-10\] Numbers downcast to `address`es may result in collisions
##### Description:
If a number is downcast to an `address` the upper bytes are truncated, which may mean that more than one value will map to the same `address`.

##### Instances:
There is 1 instance of this issue.
```solidity
File: src/rollup/BridgeCreator.sol

75:                     address(
76:                         isDelayBufferable
77:                             ? templates.delayBufferableSequencerInbox
78:                             : templates.sequencerInbox
79:                     ),
```

| File Link                                                                                                             | Instance Count | Instance Link                                                                                              |
| :-------------------------------------------------------------------------------------------------------------------- | -------------: | :--------------------------------------------------------------------------------------------------------- |
| [BridgeCreator.sol](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/rollup/BridgeCreator.sol) |              1 | [75](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/rollup/BridgeCreator.sol#L75) |
___
#### <a id="l-11"></a> \[L-11\] `onlyOwner` functions not accessible if owner renounces ownership
##### Description:
The owner is able to perform certain privileged activities, but it's possible to set the owner to `address(0)`. This can represent a certain risk if the ownership is renounced for any other reason than by design. Renouncing ownership will leave the contract without an owner, therefore limiting any functionality that needs authority.

##### Instances:
There are 3 instances of this issue.
```solidity
File: src/rollup/BridgeCreator.sol

53:     function updateTemplates(BridgeTemplates calldata _newTemplates) external onlyOwner {

58:     function updateERC20Templates(BridgeTemplates calldata _newTemplates) external onlyOwner {
```

| File Link                                                                                                             | Instance Count | Instance Links                                                                                                                                                                                                        |
| :-------------------------------------------------------------------------------------------------------------------- | -------------: | :-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| [BridgeCreator.sol](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/rollup/BridgeCreator.sol) |              2 | [53](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/rollup/BridgeCreator.sol#L53),[58](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/rollup/BridgeCreator.sol#L58) |
___
```solidity
File: src/rollup/RollupCreator.sol

63:     function setTemplates(
64:         BridgeCreator _bridgeCreator,
65:         IOneStepProofEntry _osp,
66:         IEdgeChallengeManager _challengeManagerLogic,
67:         IRollupAdmin _rollupAdminLogic,
68:         IRollupUser _rollupUserLogic,
69:         IUpgradeExecutor _upgradeExecutorLogic,
70:         address _validatorWalletCreator,
71:         DeployHelper _l2FactoriesDeployer
72:     ) external onlyOwner {
```

| File Link                                                                                                             | Instance Count | Instance Link                                                                                              |
| :-------------------------------------------------------------------------------------------------------------------- | -------------: | :--------------------------------------------------------------------------------------------------------- |
| [RollupCreator.sol](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/rollup/RollupCreator.sol) |              1 | [63](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/rollup/RollupCreator.sol#L63) |
___
#### <a id="l-12"></a> \[L-12\] Upgradeable contract is not using OpenZeppelin upgradeable contracts/libraries
##### Description:
An upgradeable contract is using the non-upgradeable, standard version of an OpenZeppelin library.

##### Recommendation:
When possible, use the contracts from `@openzeppelin/contracts-upgradeable` instead of `@openzeppelin/contracts`. See [openzeppelin-contracts-upgradeable](https://github.com/OpenZeppelin/openzeppelin-contracts-upgradeable/tree/master/contracts) for a list of available upgradeable contracts.

##### Instances:
There is 1 instance of this issue.
```solidity
File: src/rollup/RollupUserLogic.sol

7: import "@openzeppelin/contracts/token/ERC20/IERC20.sol";
```

| File Link                                                                                                                 | Instance Count | Instance Link                                                                                              |
| :------------------------------------------------------------------------------------------------------------------------ | -------------: | :--------------------------------------------------------------------------------------------------------- |
| [RollupUserLogic.sol](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/rollup/RollupUserLogic.sol) |              1 | [7](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/rollup/RollupUserLogic.sol#L7) |
___
#### <a id="l-13"></a> \[L-13\] Use of `assert()`
##### Description:
Hitting an `assert()` creates an error of type `Panic(uint256)` instead of `Error(string)`. Per the [Solidity documentation](https://docs.soliditylang.org/en/latest/control-structures.html#panic-via-assert-and-error-via-require), "_Assert should only be used to test for internal errors, and to check invariants. Properly functioning code should never create a Panic, not even on invalid external input. If this happens, then there is a bug in your contract which you should fix._".

##### Recommendation:
Use `require()` rather than `assert()`. It should be used to ensure valid conditions that cannot be detected until execution time. This includes conditions on inputs or return values from calls to external contracts.

##### Instances:
There are 2 instances of this issue.
```solidity
File: src/bridge/SequencerInbox.sol

651:         assert(header.length == HEADER_LENGTH);
```

| File Link                                                                                                               | Instance Count | Instance Link                                                                                                 |
| :---------------------------------------------------------------------------------------------------------------------- | -------------: | :------------------------------------------------------------------------------------------------------------ |
| [SequencerInbox.sol](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/bridge/SequencerInbox.sol) |              1 | [651](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/bridge/SequencerInbox.sol#L651) |
___
```solidity
File: src/challengeV2/libraries/MerkleTreeLib.sol

340:             assert(size <= postSize);
```

| File Link                                                                                                                            | Instance Count | Instance Link                                                                                                               |
| :----------------------------------------------------------------------------------------------------------------------------------- | -------------: | :-------------------------------------------------------------------------------------------------------------------------- |
| [MerkleTreeLib.sol](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/challengeV2/libraries/MerkleTreeLib.sol) |              1 | [340](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/challengeV2/libraries/MerkleTreeLib.sol#L340) |
___
#### <a id="l-14"></a> \[L-14\] Vulnerable versions of packages are being used
##### Description:
This project's dependencies are vulnerable to the Common Vulnerabilities and Exposures (CVEs) listed below.

##### Recommendation:
Although the CVEs may involve code not in use by this project, consider switching to more recent versions of these packages that do not have these vulnerabilities, to avoid trying to determine whether there is vulnerable code from these packages in use.

##### Instances:
There are 6 instances of this issue.
<details><summary>View 6 Instances</summary>

1. [CVE-2023-26488](https://nvd.nist.gov/vuln/detail/CVE-2023-26488) - Severity: <span style="color:yellow">**Medium**</span> - OpenZeppelin Contracts is a library for secure smart contract development. The ERC721Consecutive contract designed for minting NFTs in batches does not update balances when a batch has size 1 and consists of a single token. Subsequent transfers from the receiver of that token may overflow the balance as reported by `balanceOf`. The issue exclusively presents with batches of size 1. The issue has been patched in 4.8.2.
1. [CVE-2023-30541](https://nvd.nist.gov/vuln/detail/CVE-2023-30541) - Severity: <span style="color:yellow">**Medium**</span> - OpenZeppelin Contracts is a library for secure smart contract development. A function in the implementation contract may be inaccessible if its selector clashes with one of the proxy's own selectors. Specifically, if the clashing function has a different signature with incompatible ABI encoding, the proxy could revert while attempting to decode the arguments from calldata. The probability of an accidental clash is negligible, but one could be caused deliberately and could cause a reduction in availability. The issue has been fixed in version 4.8.3. As a workaround if a function appears to be inaccessible for this reason, it may be possible to craft the calldata such that ABI decoding does not fail at the proxy and the function is properly proxied through.

1. [CVE-2023-30542](https://nvd.nist.gov/vuln/detail/CVE-2023-30542) - Severity: <span style="color:red">**High**</span> - OpenZeppelin Contracts is a library for secure smart contract development. The proposal creation entrypoint (`propose`) in `GovernorCompatibilityBravo` allows the creation of proposals with a `signatures` array shorter than the `calldatas` array. This causes the additional elements of the latter to be ignored, and if the proposal succeeds the corresponding actions would eventually execute without any calldata. The `ProposalCreated` event correctly represents what will eventually execute, but the proposal parameters as queried through `getActions` appear to respect the original intended calldata. This issue has been patched in 4.8.3. As a workaround, ensure that all proposals that pass through governance have equal length `signatures` and `calldatas` parameters.

1. [CVE-2023-34234](https://nvd.nist.gov/vuln/detail/CVE-2023-34234) - Severity: <span style="color:yellow">**Medium**</span> - OpenZeppelin Contracts is a library for smart contract development. By frontrunning the creation of a proposal, an attacker can become the proposer and gain the ability to cancel it. The attacker can do this repeatedly to try to prevent a proposal from being proposed at all. This impacts the `Governor` contract in v4.9.0 only, and the `GovernorCompatibilityBravo` contract since v4.3.0. This problem has been patched in 4.9.1 by introducing opt-in frontrunning protection. Users are advised to upgrade. Users unable to upgrade may submit the proposal creation transaction to an endpoint with frontrunning protection as a workaround.

1. [CVE-2023-34459](https://nvd.nist.gov/vuln/detail/CVE-2023-34459) - Severity: <span style="color:yellow">**Medium**</span> - OpenZeppelin Contracts is a library for smart contract development. Starting in version 4.7.0 and prior to version 4.9.2, when the `verifyMultiProof`, `verifyMultiProofCalldata`, `procesprocessMultiProof`, or `processMultiProofCalldat` functions are in use, it is possible to construct merkle trees that allow forging a valid multiproof for an arbitrary set of leaves. A contract may be vulnerable if it uses multiproofs for verification and the merkle tree that is processed includes a node with value 0 at depth 1 (just under the root). This could happen inadvertedly for balanced trees with 3 leaves or less, if the leaves are not hashed. This could happen deliberately if a malicious tree builder includes such a node in the tree. A contract is not vulnerable if it uses single-leaf proving (`verify`, `verifyCalldata`, `processProof`, or `processProofCalldata`), or if it uses multiproofs with a known tree that has hashed leaves. Standard merkle trees produced or validated with the @openzeppelin/merkle-tree library are safe. The problem has been patched in version 4.9.2. Some workarounds are available. For those using multiproofs: When constructing merkle trees hash the leaves and do not insert empty nodes in your trees. Using the @openzeppelin/merkle-tree package eliminates this issue. Do not accept user-provided merkle roots without reconstructing at least the first level of the tree. Verify the merkle tree structure by reconstructing it from the leaves.

1. [CVE-2023-40014](https://nvd.nist.gov/vuln/detail/CVE-2023-40014) - Severity: <span style="color:yellow">**Medium**</span> - OpenZeppelin Contracts is a library for secure smart contract development. Starting in version 4.0.0 and prior to version 4.9.3, contracts using `ERC2771Context` along with a custom trusted forwarder may see `_msgSender` return `address(0)` in calls that originate from the forwarder with calldata shorter than 20 bytes. This combination of circumstances does not appear to be common, in particular it is not the case for `MinimalForwarder` from OpenZeppelin Contracts, or any deployed forwarder the team is aware of, given that the signer address is appended to all calls that originate from these forwarders. The problem has been patched in v4.9.3.


</details>
