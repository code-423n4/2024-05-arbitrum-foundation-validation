## Low Findings

| Issue  |                                                                                  |
| ------ | -------------------------------------------------------------------------------- |
| [L-01] | Solidity pragma should be specific, not wide                                     |
| [L-02] | Missing checks for `address(0)` when assigning values to address state variables |
| [L-03] | `public` functions not used internally could be marked `external`                |
| [L-04] | Empty block                                                                      |
| [L-05] | Embedding modifier in private function reduces contract size                     |
| [L-06] | Activate the optimizer                                                           |
| [L-07] | Missing contract-existence checks before low-Level calls                         |
| [L-08] | Unused returns                                                                   |
| [L-09] | Deprecated ether transfer method vulnerability: Not future-proof                 |
| [L-10] | Unsafe casting                                                                   |

## Non-Critical Findings

| Issue  |                                                                                  |
| ------ | -------------------------------------------------------------------------------- |
| [N-01] | Utilize `constant` variables instead of hardcoded literals                       |
| [N-02] | Large literal values multiples of 10000 can be replaced with scientific notation |
| [N-03] | Internal functions called only once can be inlined                               |
| [N-04] | Unused custom Error                                                              |
| [N-05] | Loop contains `require`/`revert` statements                                      |
| [N-06] | State variables could be declared as `constant`                                  |
| [N-07] | Function/Constructor argument names not in mixedCase                             |
| [N-08] | Dead code must be removed                                                        |
| [N-09] | High cyclomatic complexity                                                       |
| [N-10] | Optimize boolean constant usage                                                  |
| [N-11] | Unused imports across files                                                      |
| [N-12] | Unused state variables                                                           |
| [N-13] | No events for important state changes                                            |
| [N-14] | Consider using a struct rather than having many function input parameters        |
| [N-15] | Consider using descriptive constants when passing zero as a function argument    |
| [N-16] | Custom error has no error details                                                |
| [N-17] | Consider emitting an event at the end of the constructor                         |
| [N-18] | Consider using named returns                                                     |
| [N-19] | Events missing `msg.sender` information                                          |
| [N-20] | Leverage Recent Solidity Features with 0.8.23                                    |
| [N-21] | Simultaneous use of `revert` and `require` statements in Solidity contracts      |
| [N-22] | Outdated Solidity version                                                        |
| [N-23] | Non-uppercase naming for immutable variables                                     |
| [N-24] | Consider using named mappings                                                    |
| [N-25] | Contracts should have full test coverage                                         |
| [N-26] | `Non-external/public` state variables should begin with an underscore            |
| [N-27] | Non-external functions should be prefixed with an underscore                     |
| [N-28] | Proper use of get as a function name prefix                                      |

## Issue Counts by Category

| Category     | No. of Issues |
| ------------ | ------------- |
| Low          | 10            |
| Non-critical | 28            |

## Low Findings Details

### [L-01] Solidity pragma should be specific, not wide

Consider using a specific version of Solidity in your contracts instead of a wide version. For example, instead of `pragma solidity ^0.8.0;`, use `pragma solidity 0.8.0;`. This practice helps to ensure that your contracts remain compatible with the intended version of Solidity and reduces the risk of unexpected behavior due to changes introduced in newer versions

<details>
<summary><i>Affected Code Snippets</i></summary>

- Found in src/assertionStakingPool/AbsBoldStakingPool.sol [Line: 5](https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/assertionStakingPool/AbsBoldStakingPool.sol#L5)

  ```solidity
  pragma solidity ^0.8.0;
  ```

- Found in src/assertionStakingPool/AssertionStakingPool.sol [Line: 6](https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/assertionStakingPool/AssertionStakingPool.sol#L6)

  ```solidity
  pragma solidity ^0.8.0;
  ```

- Found in src/assertionStakingPool/AssertionStakingPoolCreator.sol [Line: 6](https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/assertionStakingPool/AssertionStakingPoolCreator.sol#L6)

  ```solidity
  pragma solidity ^0.8.0;
  ```

- Found in src/assertionStakingPool/EdgeStakingPool.sol [Line: 5](https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/assertionStakingPool/EdgeStakingPool.sol#L5)

  ```solidity
  pragma solidity ^0.8.0;
  ```

- Found in src/assertionStakingPool/EdgeStakingPoolCreator.sol [Line: 6](https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/assertionStakingPool/EdgeStakingPoolCreator.sol#L6)

  ```solidity
  pragma solidity ^0.8.0;
  ```

- Found in src/assertionStakingPool/StakingPoolCreatorUtils.sol [Line: 6](https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/assertionStakingPool/StakingPoolCreatorUtils.sol#L6)

  ```solidity
  pragma solidity ^0.8.0;
  ```

- Found in src/assertionStakingPool/interfaces/IAbsBoldStakingPool.sol [Line: 5](https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/assertionStakingPool/interfaces/IAbsBoldStakingPool.sol#L5)

  ```solidity
  pragma solidity ^0.8.0;
  ```

- Found in src/assertionStakingPool/interfaces/IAssertionStakingPool.sol [Line: 5](https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/assertionStakingPool/interfaces/IAssertionStakingPool.sol#L5)

  ```solidity
  pragma solidity ^0.8.0;
  ```

- Found in src/assertionStakingPool/interfaces/IAssertionStakingPoolCreator.sol [Line: 5](https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/assertionStakingPool/interfaces/IAssertionStakingPoolCreator.sol#L5)

  ```solidity
  pragma solidity ^0.8.0;
  ```

- Found in src/assertionStakingPool/interfaces/IEdgeStakingPool.sol [Line: 5](https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/assertionStakingPool/interfaces/IEdgeStakingPool.sol#L5)

  ```solidity
  pragma solidity ^0.8.0;
  ```

- Found in src/assertionStakingPool/interfaces/IEdgeStakingPoolCreator.sol [Line: 5](https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/assertionStakingPool/interfaces/IEdgeStakingPoolCreator.sol#L5)

  ```solidity
  pragma solidity ^0.8.0;
  ```

- Found in src/bridge/DelayBuffer.sol [Line: 5](https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/bridge/DelayBuffer.sol#L5)

  ```solidity
  pragma solidity ^0.8.0;
  ```

- Found in src/bridge/DelayBufferTypes.sol [Line: 7](https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/bridge/DelayBufferTypes.sol#L7)

  ```solidity
  pragma solidity >=0.6.9 <0.9.0;
  ```

- Found in src/bridge/ISequencerInbox.sol [Line: 6](https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/bridge/ISequencerInbox.sol#L6)

  ```solidity
  pragma solidity >=0.6.9 <0.9.0;
  ```

- Found in src/bridge/SequencerInbox.sol [Line: 5](https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/bridge/SequencerInbox.sol#L5)

  ```solidity
  pragma solidity ^0.8.0;
  ```

- Found in src/challengeV2/EdgeChallengeManager.sol [Line: 5](https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/challengeV2/EdgeChallengeManager.sol#L5)

  ```solidity
  pragma solidity ^0.8.17;
  ```

- Found in src/challengeV2/IAssertionChain.sol [Line: 5](https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/challengeV2/IAssertionChain.sol#L5)

  ```solidity
  pragma solidity ^0.8.17;
  ```

- Found in src/challengeV2/libraries/ArrayUtilsLib.sol [Line: 5](https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/challengeV2/libraries/ArrayUtilsLib.sol#L5)

  ```solidity
  pragma solidity ^0.8.17;
  ```

- Found in src/challengeV2/libraries/ChallengeEdgeLib.sol [Line: 5](https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/challengeV2/libraries/ChallengeEdgeLib.sol#L5)

  ```solidity
  pragma solidity ^0.8.17;
  ```

- Found in src/challengeV2/libraries/ChallengeErrors.sol [Line: 5](https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/challengeV2/libraries/ChallengeErrors.sol#L5)

  ```solidity
  pragma solidity ^0.8.17;
  ```

- Found in src/challengeV2/libraries/EdgeChallengeManagerLib.sol [Line: 5](https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/challengeV2/libraries/EdgeChallengeManagerLib.sol#L5)

  ```solidity
  pragma solidity ^0.8.17;
  ```

- Found in src/challengeV2/libraries/Enums.sol [Line: 5](https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/challengeV2/libraries/Enums.sol#L5)

  ```solidity
  pragma solidity ^0.8.17;
  ```

- Found in src/challengeV2/libraries/MerkleTreeLib.sol [Line: 5](https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/challengeV2/libraries/MerkleTreeLib.sol#L5)

  ```solidity
  pragma solidity ^0.8.17;
  ```

- Found in src/challengeV2/libraries/UintUtilsLib.sol [Line: 5](https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/challengeV2/libraries/UintUtilsLib.sol#L5)

  ```solidity
  pragma solidity ^0.8.17;
  ```

- Found in src/libraries/Error.sol [Line: 5](https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/libraries/Error.sol#L5)

  ```solidity
  pragma solidity ^0.8.4;
  ```

- Found in src/rollup/Assertion.sol [Line: 5](https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/rollup/Assertion.sol#L5)

  ```solidity
  pragma solidity ^0.8.0;
  ```

- Found in src/rollup/AssertionState.sol [Line: 5](https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/rollup/AssertionState.sol#L5)

  ```solidity
  pragma solidity ^0.8.0;
  ```

- Found in src/rollup/BOLDUpgradeAction.sol [Line: 5](https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/rollup/BOLDUpgradeAction.sol#L5)

  ```solidity
  pragma solidity ^0.8.0;
  ```

- Found in src/rollup/BridgeCreator.sol [Line: 5](https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/rollup/BridgeCreator.sol#L5)

  ```solidity
  pragma solidity ^0.8.0;
  ```

- Found in src/rollup/Config.sol [Line: 5](https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/rollup/Config.sol#L5)

  ```solidity
  pragma solidity ^0.8.0;
  ```

- Found in src/rollup/IRollupAdmin.sol [Line: 5](https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/rollup/IRollupAdmin.sol#L5)

  ```solidity
  pragma solidity ^0.8.0;
  ```

- Found in src/rollup/IRollupCore.sol [Line: 5](https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/rollup/IRollupCore.sol#L5)

  ```solidity
  pragma solidity ^0.8.0;
  ```

- Found in src/rollup/IRollupLogic.sol [Line: 5](https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/rollup/IRollupLogic.sol#L5)

  ```solidity
  pragma solidity ^0.8.0;
  ```

- Found in src/rollup/RollupAdminLogic.sol [Line: 5](https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/rollup/RollupAdminLogic.sol#L5)

  ```solidity
  pragma solidity ^0.8.0;
  ```

- Found in src/rollup/RollupCore.sol [Line: 5](https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/rollup/RollupCore.sol#L5)

  ```solidity
  pragma solidity ^0.8.0;
  ```

- Found in src/rollup/RollupCreator.sol [Line: 5](https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/rollup/RollupCreator.sol#L5)

  ```solidity
  pragma solidity ^0.8.0;
  ```

- Found in src/rollup/RollupLib.sol [Line: 5](https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/rollup/RollupLib.sol#L5)

  ```solidity
  pragma solidity ^0.8.0;
  ```

- Found in src/rollup/RollupProxy.sol [Line: 5](https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/rollup/RollupProxy.sol#L5)

  ```solidity
  pragma solidity ^0.8.0;
  ```

- Found in src/rollup/RollupUserLogic.sol [Line: 5](https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/rollup/RollupUserLogic.sol#L5)

  ```solidity
  pragma solidity ^0.8.0;
  ```

</details>

### [L-02] Missing checks for `address(0)` when assigning values to address state variables

Ensure to check for `address(0)` when assigning values to address state variables. This helps to prevent unintended behavior, such as assigning null addresses, which can lead to vulnerabilities or unexpected outcomes in your smart contracts.

<details>
<summary><i>Affected Code Snippets</i></summary>

- Found in src/bridge/SequencerInbox.sol [Line: 898](https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/bridge/SequencerInbox.sol#L898)

```solidity
        isBatchPoster[addr] = isBatchPoster_;
```

- Found in src/bridge/SequencerInbox.sol [Line: 937](https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/bridge/SequencerInbox.sol#L937)

  ```solidity
          isSequencer[addr] = isSequencer_;
  ```

- Found in src/rollup/RollupAdminLogic.sol [Line: 118](https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/rollup/RollupAdminLogic.sol#L118)

  ```solidity
          outbox = _outbox;
  ```

- Found in src/rollup/RollupAdminLogic.sol [Line: 300](https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/rollup/RollupAdminLogic.sol#L300)

  ```solidity
          inbox = newInbox;
  ```

- Found in src/rollup/RollupAdminLogic.sol [Line: 318](https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/rollup/RollupAdminLogic.sol#L318)

  ```solidity
          anyTrustFastConfirmer = _anyTrustFastConfirmer;
  ```

- Found in src/rollup/RollupAdminLogic.sol [Line: 327](https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/rollup/RollupAdminLogic.sol#L327)

  ```solidity
          challengeManager = IEdgeChallengeManager(_challengeManager);
  ```

- Found in src/rollup/RollupCore.sol [Line: 277](https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/rollup/RollupCore.sol#L277)

  ```solidity
          _stakerMap[stakerAddress] = Staker(depositAmount, _latestConfirmed, stakerIndex, true, withdrawalAddress);
  ```

- Found in src/rollup/RollupCreator.sol [Line: 73](https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/rollup/RollupCreator.sol#L73)

  ```solidity
          bridgeCreator = _bridgeCreator;
  ```

- Found in src/rollup/RollupCreator.sol [Line: 74](https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/rollup/RollupCreator.sol#L74)

  ```solidity
          osp = _osp;
  ```

- Found in src/rollup/RollupCreator.sol [Line: 75](https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/rollup/RollupCreator.sol#L75)

  ```solidity
          challengeManagerTemplate = _challengeManagerLogic;
  ```

- Found in src/rollup/RollupCreator.sol [Line: 76](https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/rollup/RollupCreator.sol#L76)

  ```solidity
          rollupAdminLogic = _rollupAdminLogic;
  ```

- Found in src/rollup/RollupCreator.sol [Line: 77](https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/rollup/RollupCreator.sol#L77)

  ```solidity
          rollupUserLogic = _rollupUserLogic;
  ```

- Found in src/rollup/RollupCreator.sol [Line: 78](https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/rollup/RollupCreator.sol#L78)

  ```solidity
          upgradeExecutorLogic = _upgradeExecutorLogic;
  ```

- Found in src/rollup/RollupCreator.sol [Line: 79](https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/rollup/RollupCreator.sol#L79)

  ```solidity
          validatorWalletCreator = _validatorWalletCreator;
  ```

- Found in src/rollup/RollupCreator.sol [Line: 80](https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/rollup/RollupCreator.sol#L80)

  ```solidity
          l2FactoriesDeployer = _l2FactoriesDeployer;
  ```

</details>

<br>

**Clarification: A similar issue was identified by 4naly3er, but it did not detect these instances. For more details, refer to 4naly3er report [here](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/4naly3er-report.md#L-4).**

### [L-03] `public` functions not used internally could be marked `external`

Evaluate whether unused `public` functions can be marked as `external` if they are not used internally. This can optimize clarity in your contract code, ensure appropriate function scoping, and potentially save gas costs.

<details>
<summary><i>Affected Code Snippets</i></summary>

- Found in src/rollup/RollupCore.sol [Line: 116](https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/rollup/RollupCore.sol#L116)

```solidity
    function sequencerInbox() public view virtual returns (ISequencerInbox) {
```

- Found in src/rollup/RollupCore.sol [Line: 134](https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/rollup/RollupCore.sol#L134)

  ```solidity
      function getAssertion(bytes32 assertionHash) public view override returns (AssertionNode memory) {
  ```

- Found in src/rollup/RollupCore.sol [Line: 217](https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/rollup/RollupCore.sol#L217)

  ```solidity
      function stakerCount() public view override returns (uint64) {
  ```

</details>

<br>

**Clarification: A similar issue was identified by 4naly3er, but it did not detect these instances. For more details, refer to issue [N-34](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/4naly3er-report.md#N-34) from the 4naly3er report.**

### [L-04] Empty block

Empty blocks serve no purpose and can clutter the codebase. Consider removing them to optimize code readability and maintainability.

<details>
<summary><i>Affected Code Snippets</i></summary>

- Found in src/rollup/RollupAdminLogic.sol [Line: 166](https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/rollup/RollupAdminLogic.sol#L166)

```solidity
    function _authorizeUpgrade(address newImplementation) internal override {}
```

- Found in src/rollup/RollupAdminLogic.sol [Line: 171](https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/rollup/RollupAdminLogic.sol#L171)

  ```solidity
      function _authorizeSecondaryUpgrade(address newImplementation) internal override {}
  ```

</details>

### [L-05] Embedding modifier in private function reduces contract size

Consider consolidating the logic of a modifier within a private function to optimize contract size. Employing a private visibility, which is more efficient for function calls compared to internal visibility, is advisable since the modifier will exclusively invoke this function internally within the contract.

For example, the modifier referenced below could be refactored as demonstrated:
[SequencerInbox.sol#L103-L106](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/bridge/SequencerInbox.sol#L103-L106)

```diff
-    modifier onlyRollupOwner() {
+    function _onlyRollupOwner() private view {
         if (msg.sender != rollup.owner()) revert NotOwner(msg.sender, rollup.owner());
+    }
+
+    modifier onlyRollupOwner() {
+        _onlyRollupOwner();
    }
```

### [L-06] Activate the optimizer

Before deploying your contract, activate the optimizer when compiling using the following command:

```bash
solc --optimize --bin sourceFile.sol
```

By default, the optimizer will optimize the contract assuming it is called 200 times across its lifetime. If you want the initial contract deployment to be cheaper and the later function executions to be more expensive, set it to --optimize-runs=1. Conversely, if you expect many transactions and do not care for higher deployment cost and output size, set --optimize-runs to a high number.

```javascript
module.exports = {
  solidity: {
    version: "0.8.19",
    settings: {
      optimizer: {
        enabled: true,
        runs: 1000,
      },
    },
  },
};
```

For further information, please visit [this site](https://docs.soliditylang.org/en/v0.5.4/using-the-compiler.html#using-the-commandline-compiler).

### [L-07] Missing contract-existence checks before low-Level calls

When making low-level calls, it's crucial to ensure the existence of the contract at the specified address. If the contract doesn't exist at the given address, low-level calls will still return success, potentially causing errors in the code execution. Therefore, alongside zero-address checks, adding an additional check to verify that

.code.length > 0 before making low-level calls would be recommended.

<details>
<summary><i>Affected Code Snippets</i></summary>

- Found in src/rollup/RollupCreator.sol [Line: 304](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/rollup/RollupCreator.sol#L304)

</details>

### [L-08] Unused returns

The project contains functions that return values which are not being utilized, leading to potential inefficiencies and unnecessary complexity. Removing unused return statements will streamline the code, reducing gas costs and optimizing overall code clarity and maintainability.

<details>
<summary><i>Affected Code Snippets</i></summary>

- Found in src/assertionStakingPool/AssertionStakingPool.sol [Line: 56](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/assertionStakingPool/AssertionStakingPool.sol#L56)

```solidity
IRollupUser(rollup).withdrawStakerFunds();
```

- Found in src/challengeV2/libraries/EdgeChallengeManagerLib.sol [Line:678](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/challengeV2/libraries/EdgeChallengeManagerLib.sol#L678)

```solidity
ChallengeEdgeLib.levelToType(nextLevel, numBigStepLevel);
```

</details>

### [L-09] Deprecated ether transfer method vulnerability: Not future-proof

The contract's `RollupCreator::_deployFactories()` function currently relies on the deprecated `transfer(...)` method for Ether transfers, which can pose a risk of malfunctioning due to potential changes in gas costs. To bolster security and ensure the contract remains resilient in the face of evolving gas cost dynamics, it is advisable to replace occurrences of `transfer(...)` with more robust alternatives like `call(...)`.

Problematic code: [RollupCreator.sol#L300](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/rollup/RollupCreator.sol#L300)

```solidity
 l2FactoriesDeployer.perform{value: cost}(_inbox, _nativeToken, _maxFeePerGas);
```

The issue arises from the usage of the `l2FactoriesDeployer.perform` function. If we examine how this function is implemented, we will see that it simply uses `transfer` on the `payable msg.sender`:

```solidity
    function perform(
        address _inbox,
        address _nativeToken,
        uint256 _maxFeePerGas
    ) external payable {
        ...
        // if paying with ETH refund the caller
        if (!isUsingFeeToken) {
            payable(msg.sender).transfer(address(this).balance);
        }
    }
```

So, by calling `l2FactoriesDeployer.perform` in the `RollupCreator.sol` a risk for the robustness of the system is introduced due to the facts mentioned above, and it is recommended to employ `call` for ETH transfer rather than `transfer` or `send`!

### [L-10] Unsafe casting

The project uses downcasting from `uint256` to `uint64`, which can cause data loss and unintended behavior if the value exceeds the target type's range Use OpenZeppelin's SafeCast library to safely downcast, preventing potential truncation and ensuring data integrity.

<details>
<summary><i>Affected Code Snippets</i></summary>

- Found in src/bridge/SequencerInbox.sol [Line: 648](https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/bridge/SequencerInbox.sol#L648)

```solidity
            uint64(afterDelayedMessagesRead)
```

- Found in src/bridge/SequencerInbox.sol [Line: 915](https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/bridge/SequencerInbox.sol#L915)

```solidity
            creationBlock: uint64(creationBlock)
```

- Found in src/rollup/RollupCore.sol [Line: 495](https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/rollup/RollupCore.sol#L495)

```solidity
            nextInboxPosition: uint64(nextInboxPosition)
```

</details>

## Non-Critical Findings Details

### [N-01] Utilize `constant` variables instead of hardcoded literals

Magic numbers, hardcoded numerical values within code, can hinder readability and maintainability. Employing constants in lieu of magic numbers optimizes code clarity and maintainability.

<details>
<summary><i>Affected Code Snippets</i></summary>

- Found in src/bridge/SequencerInbox.sol [Line: 711](https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/bridge/SequencerInbox.sol#L711)

  ```solidity
              if (data[0] & DAS_MESSAGE_HEADER_FLAG != 0 && data.length >= 33) {
  ```

- Found in src/bridge/SequencerInbox.sol [Line: 713](https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/bridge/SequencerInbox.sol#L713)

  ```solidity
                  bytes32 dasKeysetHash = bytes32(data[1:33]);
  ```

- Found in src/challengeV2/libraries/UintUtilsLib.sol [Line: 34](https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/challengeV2/libraries/UintUtilsLib.sol#L34)

  ```solidity
              x >>= 128;
  ```

- Found in src/challengeV2/libraries/UintUtilsLib.sol [Line: 35](https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/challengeV2/libraries/UintUtilsLib.sol#L35)

  ```solidity
              msb += 128;
  ```

- Found in src/challengeV2/libraries/UintUtilsLib.sol [Line: 39](https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/challengeV2/libraries/UintUtilsLib.sol#L39)

  ```solidity
              x >>= 64;
  ```

- Found in src/challengeV2/libraries/UintUtilsLib.sol [Line: 40](https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/challengeV2/libraries/UintUtilsLib.sol#L40)

  ```solidity
              msb += 64;
  ```

- Found in src/challengeV2/libraries/UintUtilsLib.sol [Line: 44](https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/challengeV2/libraries/UintUtilsLib.sol#L44)

  ```solidity
              x >>= 32;
  ```

- Found in src/challengeV2/libraries/UintUtilsLib.sol [Line: 45](https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/challengeV2/libraries/UintUtilsLib.sol#L45)

  ```solidity
              msb += 32;
  ```

- Found in src/challengeV2/libraries/UintUtilsLib.sol [Line: 49](https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/challengeV2/libraries/UintUtilsLib.sol#L49)

  ```solidity
              x >>= 16;
  ```

- Found in src/challengeV2/libraries/UintUtilsLib.sol [Line: 50](https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/challengeV2/libraries/UintUtilsLib.sol#L50)

  ```solidity
              msb += 16;
  ```

- Found in src/challengeV2/libraries/UintUtilsLib.sol [Line: 54](https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/challengeV2/libraries/UintUtilsLib.sol#L54)

  ```solidity
              x >>= 8;
  ```

- Found in src/challengeV2/libraries/UintUtilsLib.sol [Line: 55](https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/challengeV2/libraries/UintUtilsLib.sol#L55)

  ```solidity
              msb += 8;
  ```

- Found in src/challengeV2/libraries/UintUtilsLib.sol [Line: 59](https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/challengeV2/libraries/UintUtilsLib.sol#L59)

  ```solidity
              x >>= 4;
  ```

- Found in src/challengeV2/libraries/UintUtilsLib.sol [Line: 60](https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/challengeV2/libraries/UintUtilsLib.sol#L60)

  ```solidity
              msb += 4;
  ```

- Found in src/rollup/BOLDUpgradeAction.sol [Line: 347](https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/rollup/BOLDUpgradeAction.sol#L347)

  ```solidity
          if (stakerCount > 50) {
  ```

- Found in src/rollup/BOLDUpgradeAction.sol [Line: 348](https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/rollup/BOLDUpgradeAction.sol#L348)

  ```solidity
              stakerCount = 50;
  ```

  </details>

### [N-02] Large literal values multiples of 10000 can be replaced with scientific notation

Consider using `e` notation, for example: `1e18`, instead of its full numeric value for optimized code readability and maintainability.

<details>
<summary><i>Affected Code Snippets</i></summary>

- Found in src/bridge/DelayBuffer.sol [Line: 17](https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/bridge/DelayBuffer.sol#L17)

  ```solidity
      uint256 public constant BASIS = 10000;
  ```

</details>

### [N-03] Internal functions called only once can be inlined

Consolidate logic by inlining internal functions that are called only once. This optimization can reduce the number of function calls and increase code readability.

<details>
<summary><i>Affected Code Snippets</i></summary>

- Found in src/bridge/DelayBuffer.sol [Line: 33](https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/bridge/DelayBuffer.sol#L33)

  ```solidity
      function calcBuffer(
  ```

- Found in src/bridge/DelayBuffer.sol [Line: 82](https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/bridge/DelayBuffer.sol#L82)

  ```solidity
      function calcPendingBuffer(BufferData storage self, uint64 blockNumber)
  ```

- Found in src/bridge/DelayBuffer.sol [Line: 104](https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/bridge/DelayBuffer.sol#L104)

  ```solidity
      function isSynced(BufferData storage self) internal view returns (bool) {
  ```

- Found in src/bridge/SequencerInbox.sol [Line: 216](https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/bridge/SequencerInbox.sol#L216)

  ```solidity
      function getTimeBounds() internal view virtual returns (IBridge.TimeBounds memory) {
  ```

- Found in src/bridge/SequencerInbox.sol [Line: 659](https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/bridge/SequencerInbox.sol#L659)

  ```solidity
      function formEmptyDataHash(uint256 afterDelayedMessagesRead)
  ```

- Found in src/bridge/SequencerInbox.sol [Line: 675](https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/bridge/SequencerInbox.sol#L675)

  ```solidity
      function isValidCallDataFlag(bytes1 headerByte) internal pure returns (bool) {
  ```

- Found in src/bridge/SequencerInbox.sol [Line: 688](https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/bridge/SequencerInbox.sol#L688)

  ```solidity
      function formCallDataHash(bytes calldata data, uint256 afterDelayedMessagesRead)
  ```

- Found in src/bridge/SequencerInbox.sol [Line: 725](https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/bridge/SequencerInbox.sol#L725)

  ```solidity
      function formBlobDataHash(uint256 afterDelayedMessagesRead)
  ```

- Found in src/challengeV2/libraries/ChallengeEdgeLib.sol [Line: 258](https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/challengeV2/libraries/ChallengeEdgeLib.sol#L258)

  ```solidity
      function isLayerZero(ChallengeEdge storage edge) internal view returns (bool) {
  ```

- Found in src/challengeV2/libraries/EdgeChallengeManagerLib.sol [Line: 327](https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/challengeV2/libraries/EdgeChallengeManagerLib.sol#L327)

  ```solidity
      function isPowerOfTwo(uint256 x) internal pure returns (bool) {
  ```

- Found in src/challengeV2/libraries/EdgeChallengeManagerLib.sol [Line: 483](https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/challengeV2/libraries/EdgeChallengeManagerLib.sol#L483)

  ```solidity
      function hasLengthOneRival(EdgeStore storage store, bytes32 edgeId) internal view returns (bool) {
  ```

- Found in src/challengeV2/libraries/EdgeChallengeManagerLib.sol [Line: 576](https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/challengeV2/libraries/EdgeChallengeManagerLib.sol#L576)

  ```solidity
      function mandatoryBisectionHeight(uint256 start, uint256 end) internal pure returns (uint256) {
  ```

- Found in src/challengeV2/libraries/MerkleTreeLib.sol [Line: 251](https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/challengeV2/libraries/MerkleTreeLib.sol#L251)

  ```solidity
      function maximumAppendBetween(uint256 startSize, uint256 endSize) internal pure returns (uint256) {
  ```

- Found in src/challengeV2/libraries/UintUtilsLib.sol [Line: 29](https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/challengeV2/libraries/UintUtilsLib.sol#L29)

  ```solidity
      function mostSignificantBit(uint256 x) internal pure returns (uint256 msb) {
  ```

- Found in src/rollup/RollupCore.sol [Line: 225](https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/rollup/RollupCore.sol#L225)

  ```solidity
      function initializeCore(AssertionNode memory initialAssertion, bytes32 assertionHash) internal {
  ```

- Found in src/rollup/RollupCore.sol [Line: 274](https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/rollup/RollupCore.sol#L274)

  ```solidity
      function createNewStake(address stakerAddress, uint256 depositAmount, address withdrawalAddress) internal {
  ```

- Found in src/rollup/RollupCore.sol [Line: 286](https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/rollup/RollupCore.sol#L286)

  ```solidity
      function increaseStakeBy(address stakerAddress, uint256 amountAdded) internal {
  ```

- Found in src/rollup/RollupCore.sol [Line: 317](https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/rollup/RollupCore.sol#L317)

  ```solidity
      function withdrawStaker(address stakerAddress) internal {
  ```

- Found in src/rollup/RollupCore.sol [Line: 331](https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/rollup/RollupCore.sol#L331)

  ```solidity
      function withdrawFunds(address account) internal returns (uint256) {
  ```

- Found in src/rollup/RollupCreator.sol [Line: 85](https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/rollup/RollupCreator.sol#L85)

  ```solidity
      function createChallengeManager(address rollupAddr, address proxyAdminAddr, Config memory config)
  ```

- Found in src/rollup/RollupLib.sol [Line: 37](https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/rollup/RollupLib.sol#L37)

  ```solidity
      function assertionHash(
  ```

- Found in src/rollup/RollupLib.sol [Line: 54](https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/rollup/RollupLib.sol#L54)

  ```solidity
      function configHash(
  ```

</details>

### [N-04] Unused custom Error

It is recommended that the definition be removed when custom error is unused

<details>
<summary><i>Affected Code Snippets</i></summary>

- Found in src/challengeV2/libraries/ChallengeErrors.sol [Line: 40](https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/challengeV2/libraries/ChallengeErrors.sol#L40)

  ```solidity
  error EdgeTypeNotBlock(uint8 level);
  ```

- Found in src/challengeV2/libraries/ChallengeErrors.sol [Line: 56](https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/challengeV2/libraries/ChallengeErrors.sol#L56)

  ```solidity
  error EdgeClaimMismatch(bytes32 edgeId, bytes32 claimingEdgeId);
  ```

- Found in src/challengeV2/libraries/ChallengeErrors.sol [Line: 60](https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/challengeV2/libraries/ChallengeErrors.sol#L60)

  ```solidity
  error EdgeNotAncestor(
  ```

- Found in src/libraries/Error.sol [Line: 14](https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/libraries/Error.sol#L14)

  ```solidity
  error BadPostUpgradeInit();
  ```

- Found in src/libraries/Error.sol [Line: 24](https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/libraries/Error.sol#L24)

  ```solidity
  error NotRollup(address sender, address rollup);
  ```

- Found in src/libraries/Error.sol [Line: 36](https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/libraries/Error.sol#L36)

  ```solidity
  error NotContract(address addr);
  ```

- Found in src/libraries/Error.sol [Line: 41](https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/libraries/Error.sol#L41)

  ```solidity
  error MerkleProofTooLong(uint256 actualLength, uint256 maxProofLength);
  ```

- Found in src/libraries/Error.sol [Line: 47](https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/libraries/Error.sol#L47)

  ```solidity
  error NotRollupOrOwner(address sender, address rollup, address owner);
  ```

- Found in src/libraries/Error.sol [Line: 53](https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/libraries/Error.sol#L53)

  ```solidity
  error NotDelayedInbox(address sender);
  ```

- Found in src/libraries/Error.sol [Line: 57](https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/libraries/Error.sol#L57)

  ```solidity
  error NotSequencerInbox(address sender);
  ```

- Found in src/libraries/Error.sol [Line: 61](https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/libraries/Error.sol#L61)

  ```solidity
  error NotOutbox(address sender);
  ```

- Found in src/libraries/Error.sol [Line: 65](https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/libraries/Error.sol#L65)

  ```solidity
  error InvalidOutboxSet(address outbox);
  ```

- Found in src/libraries/Error.sol [Line: 69](https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/libraries/Error.sol#L69)

  ```solidity
  error InvalidTokenSet(address token);
  ```

- Found in src/libraries/Error.sol [Line: 73](https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/libraries/Error.sol#L73)

  ```solidity
  error CallTargetNotAllowed(address target);
  ```

- Found in src/libraries/Error.sol [Line: 76](https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/libraries/Error.sol#L76)

  ```solidity
  error CallNotAllowed();
  ```

- Found in src/libraries/Error.sol [Line: 81](https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/libraries/Error.sol#L81)

  ```solidity
  error AlreadyPaused();
  ```

- Found in src/libraries/Error.sol [Line: 84](https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/libraries/Error.sol#L84)

  ```solidity
  error AlreadyUnpaused();
  ```

- Found in src/libraries/Error.sol [Line: 87](https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/libraries/Error.sol#L87)

  ```solidity
  error Paused();
  ```

- Found in src/libraries/Error.sol [Line: 90](https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/libraries/Error.sol#L90)

  ```solidity
  error InsufficientValue(uint256 expected, uint256 actual);
  ```

- Found in src/libraries/Error.sol [Line: 93](https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/libraries/Error.sol#L93)

  ```solidity
  error InsufficientSubmissionCost(uint256 expected, uint256 actual);
  ```

- Found in src/libraries/Error.sol [Line: 96](https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/libraries/Error.sol#L96)

  ```solidity
  error NotAllowedOrigin(address origin);
  ```

- Found in src/libraries/Error.sol [Line: 100](https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/libraries/Error.sol#L100)

  ```solidity
  error RetryableData(
  ```

- Found in src/libraries/Error.sol [Line: 114](https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/libraries/Error.sol#L114)

  ```solidity
  error L1Forked();
  ```

- Found in src/libraries/Error.sol [Line: 120](https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/libraries/Error.sol#L120)

  ```solidity
  error GasLimitTooLarge();
  ```

- Found in src/libraries/Error.sol [Line: 126](https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/libraries/Error.sol#L126)

  ```solidity
  error ProofTooLong(uint256 proofLength);
  ```

- Found in src/libraries/Error.sol [Line: 131](https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/libraries/Error.sol#L131)

  ```solidity
  error PathNotMinimal(uint256 index, uint256 maxIndex);
  ```

- Found in src/libraries/Error.sol [Line: 135](https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/libraries/Error.sol#L135)

  ```solidity
  error UnknownRoot(bytes32 root);
  ```

- Found in src/libraries/Error.sol [Line: 139](https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/libraries/Error.sol#L139)

  ```solidity
  error AlreadySpent(uint256 index);
  ```

- Found in src/libraries/Error.sol [Line: 142](https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/libraries/Error.sol#L142)

  ```solidity
  error BridgeCallFailed();
  ```

- Found in src/libraries/Error.sol [Line: 156](https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/libraries/Error.sol#L156)

  ```solidity
  error ForceIncludeTimeTooSoon();
  ```

- Found in src/libraries/Error.sol [Line: 168](https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/libraries/Error.sol#L168)

  ```solidity
  error BadSequencerMessageNumber(uint256 stored, uint256 received);
  ```

</details>

### [N-05] Loop contains `require`/`revert` statements

Avoid `require` / `revert` statements in a loop because a single bad item can cause the whole transaction to fail. It's better to forgive on fail and return failed elements post processing of the loop

<details>
<summary><i>Affected Code Snippets</i></summary>

- Found in src/challengeV2/libraries/MerkleTreeLib.sol [Line: 188](https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/challengeV2/libraries/MerkleTreeLib.sol#L188)

  ```solidity
          for (uint256 i = 0; i < me.length; i++) {
  ```

- Found in src/challengeV2/libraries/MerkleTreeLib.sol [Line: 332](https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/challengeV2/libraries/MerkleTreeLib.sol#L332)

  ```solidity
          while (size < postSize) {
  ```

- Found in src/rollup/BOLDUpgradeAction.sol [Line: 528](https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/rollup/BOLDUpgradeAction.sol#L528)

  ```solidity
              for (uint256 i = 0; i < validators.length; i++) {
  ```

</details>

### [N-06] State variables could be declared as `constant`

State variables that remain unchanged after deployment should be declared `constant` to save gas. Add the `constant` attribute to these state variables.

<details>
<summary><i>Affected Code Snippets</i></summary>

- Found in src/rollup/RollupCore.sol [Line: 27](https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/rollup/RollupCore.sol#L27)

```solidity
uint256 public chainId;
```

- Found in src/rollup/RollupCore.sol [Line: 85](https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/rollup/RollupCore.sol#L85)

```solidity
IBridge public bridge;
```

- Found in src/rollup/RollupCore.sol [Line: 87](https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/rollup/RollupCore.sol#L87)

```solidity
IRollupEventInbox public rollupEventInbox;
```

- Found in src/rollup/RollupCore.sol [Line: 93](https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/rollup/RollupCore.sol#L93)

```solidity
 address public stakeToken;
```

- Found in src/rollup/RollupCore.sol [Line: 106](https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/rollup/RollupCore.sol#L106)

```solidity
uint256 public rollupDeploymentBlock;
```

</details>

### [N-07] Function/Constructor argument names not in mixedCase

Underscore before of after function argument names is a common convention in Solidity NOT a documentation requirement.

Function arguments should use mixedCase for readability and consistency with Solidity style guidelines.
Examples of recommended practice include: initialSupply, account, recipientAddress, senderAddress, newOwner.
[More information in Documentation](https://docs.soliditylang.org/en/v0.8.20/style-guide.html#function-argument-names)

Rule exceptions

- Allow constant variable name/symbol/decimals to be lowercase (ERC20).
- Allow `_` at the beginning of the mixedCase match for `private variables` and `unused parameters`.

<details>
<summary><i>Affected Code Snippets</i></summary>

- Found in src/bridge/ISequencerInbox.sol [Line: 139](https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/bridge/ISequencerInbox.sol#L139)

```solidity
forceInclusion(
        uint256 _totalDelayedMessagesRead,
        uint8 kind,
        uint64[2] calldata l1BlockAndTime,
        uint256 baseFeeL1,
        address sender,
        bytes32 messageDataHash
    )
```

- Found in src/bridge/SequencerInbox.sol [Line: 287](https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/bridge/SequencerInbox.sol#L287)

```solidity
forceInclusion(
        uint256 _totalDelayedMessagesRead,
        uint8 kind,
        uint64[2] calldata l1BlockAndTime,
        uint256 baseFeeL1,
        address sender,
        bytes32 messageDataHash
    )
```

- Found in src/bridge/ISequencerInbox.sol [Line: 247](https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/bridge/ISequencerInbox.sol#L247)

```solidity
setMaxTimeVariation(MaxTimeVariation memory maxTimeVariation_)
```

- Found in src/bridge/ISequencerInbox.sol [Line: 254](https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/bridge/ISequencerInbox.sol#L254)

```solidity
setIsBatchPoster(address addr, bool isBatchPoster_)
```

- Found in src/bridge/ISequencerInbox.sol [Line: 274](https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/bridge/ISequencerInbox.sol#L274)

```solidity
setIsSequencer(address addr, bool isSequencer_)
```

</details>

### [N-08] Dead code must be removed

Unused code is declared in the contract but never utilized. This can lead to unnecessary memory allocation and increased contract size, which ultimately affects gas costs. It is recommended to remove the dead code to optimize gas costs, overal size of the contract, as well as it's readability and maintanability!

<details>
<summary><i>Affected Code Snippets</i></summary>

- Found in src/challengeV2/libraries/ArrayUtilsLib.sol [Lines: 13-20](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/challengeV2/libraries/ArrayUtilsLib.sol#L13-L20)

```solidity
 function append(bytes32[] memory arr, bytes32 newItem) internal pure returns (bytes32[] memory) {
        bytes32[] memory clone = new bytes32[](arr.length + 1);
        for (uint256 i = 0; i < arr.length; i++) {
            clone[i] = arr[i];
        }
        clone[clone.length - 1] = newItem;
        return clone;
    }
```

- Found in src/challengeV2/libraries/ArrayUtilsLib.sol [Lines: 45-54](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/challengeV2/libraries/ArrayUtilsLib.sol#L45-L54)

```solidity
    function concat(bytes32[] memory arr1, bytes32[] memory arr2) internal pure returns (bytes32[] memory) {
        bytes32[] memory full = new bytes32[](arr1.length + arr2.length);
        for (uint256 i = 0; i < arr1.length; i++) {
            full[i] = arr1[i];
        }
        for (uint256 i = 0; i < arr2.length; i++) {
            full[arr1.length + i] = arr2[i];
        }
        return full;
    }
```

</details>

### [N-09] High cyclomatic complexity

Functions with high cyclomatic complexity are harder to understand, test, and maintain. Consider breaking down these blocks into more manageable units, by splitting things into utility functions, by reducing nesting, and by using early returns.

<details>
<summary><i>Affected Code Snippets</i></summary>

- Found in src/challengeV2/libraries/EdgeChallengeManagerLib.sol [Lines: 213-324](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/challengeV2/libraries/EdgeChallengeManagerLib.sol#L213-L324)

```solidity
function layerZeroTypeSpecificChecks(
        EdgeStore storage store,
        CreateEdgeArgs calldata args,
        AssertionReferenceData memory ard,
        IOneStepProofEntry oneStepProofEntry,
        uint8 numBigStepLevel
    ) private view returns (ProofData memory, bytes32) {
        if (ChallengeEdgeLib.levelToType(args.level, numBigStepLevel) == EdgeType.Block) {
            // origin id is the assertion which is the root of challenge
            // all rivals and their children share the same origin id - it is a link to the information
            // they agree on
            bytes32 originId = ard.predecessorId;

            // Sanity check: The assertion reference data should be related to the claim
            // Of course the caller can provide whatever args they wish, so this is really just a helpful
            // check to avoid mistakes
            if (ard.assertionHash == 0) {
                revert AssertionHashEmpty();
            }
            if (ard.assertionHash != args.claimId) {
                revert AssertionHashMismatch(ard.assertionHash, args.claimId);
            }

            // if the assertion is already confirmed or rejected then it cant be referenced as a claim
            if (!ard.isPending) {
                revert AssertionNotPending();
            }

            // if the claim doesnt have a sibling then it is undisputed, there's no need
            // to open challenge edges for it
            if (!ard.hasSibling) {
                revert AssertionNoSibling();
            }

            // parse the inclusion proof for later use
            if (args.proof.length == 0) {
                revert EmptyEdgeSpecificProof();
            }
            (bytes32[] memory inclusionProof,,) =
                abi.decode(args.proof, (bytes32[], AssertionStateData, AssertionStateData));

            // check the start and end execution states exist, the block hash entry should be non zero
            if (ard.startState.machineStatus == MachineStatus.RUNNING) {
                revert EmptyStartMachineStatus();
            }
            if (ard.endState.machineStatus == MachineStatus.RUNNING) {
                revert EmptyEndMachineStatus();
            }

            // Create machine hashes out of the proven state
            bytes32 startStateHash = oneStepProofEntry.getMachineHash(ard.startState.toExecutionState());
            bytes32 endStateHash = oneStepProofEntry.getMachineHash(ard.endState.toExecutionState());

            return (ProofData(startStateHash, endStateHash, inclusionProof), originId);
        } else {
            // Claim must be length one. If it is unrivaled then its unrivaled time is ticking up, so there's
            // no need to create claims against it
            if (!hasLengthOneRival(store, args.claimId)) {
                revert ClaimEdgeNotLengthOneRival(args.claimId);
            }

            // hasLengthOneRival checks existance, so we can use getNoCheck
            ChallengeEdge storage claimEdge = getNoCheck(store, args.claimId);

            // origin id is the mutual id of the claim
            // all rivals and their children share the same origin id - it is a link to the information
            // they agree on
            bytes32 originId = claimEdge.mutualId();

            // once a claim is confirmed it's status can never become pending again, so there is no point
            // opening a challenge that references it
            if (claimEdge.status != EdgeStatus.Pending) {
                revert ClaimEdgeNotPending();
            }

            // the edge must be a level up from the claim
            if (args.level != nextEdgeLevel(claimEdge.level, numBigStepLevel)) {
                revert ClaimEdgeInvalidLevel(args.level, claimEdge.level);
            }

            // parse the proofs
            if (args.proof.length == 0) {
                revert EmptyEdgeSpecificProof();
            }
            (
                bytes32 startState,
                bytes32 endState,
                bytes32[] memory claimStartInclusionProof,
                bytes32[] memory claimEndInclusionProof,
                bytes32[] memory edgeInclusionProof
            ) = abi.decode(args.proof, (bytes32, bytes32, bytes32[], bytes32[], bytes32[]));

            // if the start and end states are consistent with the claim edge
            // this guarantees that the edge we're creating is a 'continuation' of the claim edge, it is
            // a commitment to the states that between start and end states of the claim
            MerkleTreeLib.verifyInclusionProof(
                claimEdge.startHistoryRoot, startState, claimEdge.startHeight, claimStartInclusionProof
            );

            // it's doubly important to check the end state since if the end state since the claim id is
            // not part of the edge id, so we need to ensure that it's not possible to create two edges of the
            // same id, but with different claim id. Ensuring that the end state is linked to the claim,
            // and later ensuring that the end state is part of the history commitment of the new edge ensures
            // that the end history root of the new edge will be different for different claim ids, and therefore
            // the edge ids will be different
            MerkleTreeLib.verifyInclusionProof(
                claimEdge.endHistoryRoot, endState, claimEdge.endHeight, claimEndInclusionProof
            );

            return (ProofData(startState, endState, edgeInclusionProof), originId);
        }
    }
```

</details>

### [N-10] Optimize boolean constant usage

Simplify comparisons by using the boolean constants directly instead of comparing them explicitly. For example, use if (x) instead of if (x == true) or if (!x) instead of if (x == false).

<details>
<summary><i>Affected Code Snippets</i></summary>

- Found in src/challengeV2/libraries/ChallengeEdgeLib.sol [Line: 271](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/challengeV2/libraries/ChallengeEdgeLib.sol#L271)

```solidity
if (edge.refunded == true) {
```

</details>

### [N-11] Unused imports across files

During the audit, multiple unused imports were identified across files. Consider removing them.

<details>
<summary><i>Affected Code Snippets</i></summary>

- Found in src/rollup/IRollupCore.sol [Line: 8](https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/rollup/IRollupCore.sol#L8)

```solidity
import "../bridge/IBridge.sol";
```

- Found in src/rollup/Config.sol [Line: 10](https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/rollup/Config.sol#L10)

```solidity
import "../bridge/IBridge.sol";
```

- Found in src/rollup/RollupLib.sol [Line: 10](https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/rollup/RollupLib.sol#L10)

```solidity
import "../bridge/IBridge.sol";
```

- Found in src/rollup/RollupCore.sol [Line: 17](https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/rollup/RollupCore.sol#L17)

```solidity
import "../bridge/IBridge.sol";
```

- Found in src/rollup/BridgeCreator.sol [Line: 17](https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/rollup/BridgeCreator.sol#L17)

```solidity
import "../bridge/IBridge.sol";
```

- Found in src/challengeV2/IAssertionChain.sol [Line: 7](https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/challengeV2/IAssertionChain.sol#L7)

```solidity
import "../bridge/IBridge.sol";
```

- Found in src/bridge/SequencerInbox.sol [Line: 45](https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/bridge/SequencerInbox.sol#L45)

```solidity
import "../precompiles/ArbGasInfo.sol";
```

- Found in src/bridge/SequencerInbox.sol [Line: 50](https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/bridge/SequencerInbox.sol#L50)

```solidity
import "../libraries/DelegateCallAware.sol";
```

- Found in src/bridge/SequencerInbox.sol [Line: 53](https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/bridge/SequencerInbox.sol#L53)

```solidity
import "../libraries/ArbitrumChecker.sol";
```

- Found in src/rollup/RollupCore.sol [Line: 20](https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/rollup/RollupCore.sol#L20)

```solidity
import "../libraries/ArbitrumChecker.sol";
```

- Found in src/rollup/IRollupCore.sol [Line: 10](https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/rollup/IRollupCore.sol#L10)

```solidity
import "../bridge/IInboxBase.sol";
```

- Found in src/rollup/Config.sol [Line: 12](https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/rollup/Config.sol#L12)

```solidity
import "../bridge/IInboxBase.sol";
```

- Found in src/rollup/RollupLib.sol [Line: 12](https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/rollup/RollupLib.sol#L12)

```solidity
import "../bridge/IInboxBase.sol";
```

- Found in src/assertionStakingPool/EdgeStakingPool.sol [Line: 9](https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/assertionStakingPool/EdgeStakingPool.sol#L9)

```solidity
import "../challengeV2/EdgeChallengeManager.sol";
```

- Found in src/rollup/IRollupCore.sol [Line: 12](https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/rollup/IRollupCore.sol#L12)

```solidity
import "../challengeV2/EdgeChallengeManager.sol";
```

- Found in src/rollup/Config.sol [Line: 15](https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/rollup/Config.sol#L15)

```solidity
import "../challengeV2/EdgeChallengeManager.sol";
```

- Found in src/rollup/RollupLib.sol [Line: 15](https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/rollup/RollupLib.sol#L15)

```solidity
import "../challengeV2/EdgeChallengeManager.sol";
```

- Found in src/rollup/RollupCore.sol [Line: 19](https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/rollup/RollupCore.sol#L19)

```solidity
import "../challengeV2/EdgeChallengeManager.sol";
```

- Found in src/rollup/BOLDUpgradeAction.sol [Line: 8](https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/rollup/BOLDUpgradeAction.sol#L8)

```solidity
import "@openzeppelin/contracts/proxy/transparent/ProxyAdmin.sol";
```

- Found in src/rollup/BridgeCreator.sol [Line: 19](https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/rollup/BridgeCreator.sol#L19)

```solidity
import "@openzeppelin/contracts/proxy/transparent/ProxyAdmin.sol";
```

- Found in src/rollup/RollupCreator.sol [Line: 11](https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/rollup/RollupCreator.sol#L11)

```solidity
import "@openzeppelin/contracts/proxy/transparent/ProxyAdmin.sol";
```

- Found in src/assertionStakingPool/StakingPoolCreatorUtils.sol [Line: 9](https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/assertionStakingPool/StakingPoolCreatorUtils.sol#L9)

```solidity
import "@openzeppelin/contracts/utils/Address.sol";
```

- Found in src/rollup/RollupCreator.sol [Line: 10](https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/rollup/RollupCreator.sol#L10)

```solidity
import "@offchainlabs/upgrade-executor/src/IUpgradeExecutor.sol";
```

- Found in src/rollup/IRollupAdmin.sol [Line: 8](https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/rollup/IRollupAdmin.sol#L8)

```solidity
import "../bridge/ISequencerInbox.sol";
```

- Found in src/rollup/IRollupLogic.sol [Line: 8](https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/rollup/IRollupLogic.sol#L8)

```solidity
import "../bridge/ISequencerInbox.sol";
```

- Found in src/rollup/Config.sol [Line: 9](https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/rollup/Config.sol#L9)

```solidity
import "../bridge/ISequencerInbox.sol";
```

- Found in src/rollup/RollupAdminLogic.sol [Line: 11](https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/rollup/RollupAdminLogic.sol#L11)

```solidity
import "../bridge/ISequencerInbox.sol";
```

- Found in src/rollup/RollupLib.sol [Line: 8](https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/rollup/RollupLib.sol#L8)

```solidity
import "../bridge/ISequencerInbox.sol";
```

- Found in src/rollup/RollupCore.sol [Line: 16](https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/rollup/RollupCore.sol#L16)

```solidity
import "../bridge/ISequencerInbox.sol";
```

- Found in src/bridge/SequencerInbox.sol [Line: 46](https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/bridge/SequencerInbox.sol#L46)

```solidity
import "../precompiles/ArbSys.sol";
```

- Found in src/rollup/BridgeCreator.sol [Line: 8](https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/rollup/BridgeCreator.sol#L8)

```solidity
import "../bridge/SequencerInbox.sol";
```

- Found in src/rollup/BridgeCreator.sol [Line: 7](https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/rollup/BridgeCreator.sol#L7)

```solidity
import "../bridge/Bridge.sol";
```

- Found in src/rollup/AssertionState.sol [Line: 8](https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/rollup/AssertionState.sol#L8)

```solidity
import "../state/Machine.sol";
```

- Found in src/rollup/Config.sol [Line: 8](https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/rollup/Config.sol#L8)

```solidity
import "../state/Machine.sol";
```

- Found in src/rollup/RollupCore.sol [Line: 14](https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/rollup/RollupCore.sol#L14)

```solidity
import "../state/Machine.sol";
```

- Found in src/challengeV2/EdgeChallengeManager.sol [Line: 12](https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/challengeV2/EdgeChallengeManager.sol#L12)

```solidity
import "../state/Machine.sol";
```

- Found in src/rollup/AssertionState.sol [Line: 7](https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/rollup/AssertionState.sol#L7)

```solidity
import "../state/GlobalState.sol";
```

- Found in src/rollup/Config.sol [Line: 7](https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/rollup/Config.sol#L7)

```solidity
import "../state/GlobalState.sol";
```

- Found in src/rollup/RollupLib.sol [Line: 7](https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/rollup/RollupLib.sol#L7)

```solidity
import "../state/GlobalState.sol";
```

- Found in src/bridge/ISequencerInbox.sol [Line: 11](https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/bridge/ISequencerInbox.sol#L11)

```solidity
import "./IBridge.sol";
```

- Found in src/bridge/SequencerInbox.sol [Line: 40](https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/bridge/SequencerInbox.sol#L40)

```solidity
import "./IBridge.sol";
```

- Found in src/bridge/ISequencerInbox.sol [Line: 9](https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/bridge/ISequencerInbox.sol#L9)

```solidity
import "../libraries/IGasRefunder.sol";
```

- Found in src/bridge/ISequencerInbox.sol [Line: 10](https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/bridge/ISequencerInbox.sol#L10)

```solidity
import "./IDelayedMessageProvider.sol";
```

- Found in src/bridge/ISequencerInbox.sol [Line: 12](https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/bridge/ISequencerInbox.sol#L12)

```solidity
import "./Messages.sol";
```

- Found in src/bridge/DelayBufferTypes.sol [Line: 5](https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/bridge/DelayBufferTypes.sol#L5)

```solidity
import "./Messages.sol";
```

- Found in src/bridge/SequencerInbox.sol [Line: 44](https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/bridge/SequencerInbox.sol#L44)

```solidity
import "./Messages.sol";
```

- Found in src/bridge/DelayBuffer.sol [Line: 7](https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/bridge/DelayBuffer.sol#L7)

```solidity
import "./Messages.sol";
```

- Found in src/bridge/ISequencerInbox.sol [Line: 13](https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/bridge/ISequencerInbox.sol#L13)

```solidity
import "./DelayBufferTypes.sol";
```

- Found in src/bridge/DelayBuffer.sol [Line: 8](https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/bridge/DelayBuffer.sol#L8)

```solidity
import "./DelayBufferTypes.sol";
```

- Found in src/assertionStakingPool/EdgeStakingPool.sol [Line: 12](https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/assertionStakingPool/EdgeStakingPool.sol#L12)

```solidity
import "@openzeppelin/contracts/token/ERC20/utils/SafeERC20.sol";
```

- Found in src/challengeV2/EdgeChallengeManager.sol [Line: 15](https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/challengeV2/EdgeChallengeManager.sol#L15)

```solidity
import "@openzeppelin/contracts/token/ERC20/utils/SafeERC20.sol";
```

- Found in src/bridge/SequencerInbox.sol [Line: 41](https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/bridge/SequencerInbox.sol#L41)

```solidity
import "./IInboxBase.sol";
```

- Found in src/bridge/SequencerInbox.sol [Line: 42](https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/bridge/SequencerInbox.sol#L42)

```solidity
import "./ISequencerInbox.sol";
```

- Found in src/bridge/SequencerInbox.sol [Line: 43](https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/bridge/SequencerInbox.sol#L43)

```solidity
import "../rollup/IRollupLogic.sol";
```

- Found in src/assertionStakingPool/AssertionStakingPool.sol [Line: 9](https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/assertionStakingPool/AssertionStakingPool.sol#L9)

```solidity
import "../rollup/IRollupLogic.sol";
```

- Found in src/bridge/SequencerInbox.sol [Line: 47](https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/bridge/SequencerInbox.sol#L47)

```solidity
import "../libraries/IReader4844.sol";
```

- Found in src/bridge/SequencerInbox.sol [Line: 55](https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/bridge/SequencerInbox.sol#L55)

```solidity
import "./DelayBuffer.sol";
```

- Found in src/assertionStakingPool/EdgeStakingPoolCreator.sol [Line: 8](https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/assertionStakingPool/EdgeStakingPoolCreator.sol#L8)

```solidity
import "./EdgeStakingPool.sol";
```

- Found in src/assertionStakingPool/EdgeStakingPoolCreator.sol [Line: 9](https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/assertionStakingPool/EdgeStakingPoolCreator.sol#L9)

```solidity
import "./StakingPoolCreatorUtils.sol";
```

- Found in src/assertionStakingPool/AssertionStakingPoolCreator.sol [Line: 9](https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/assertionStakingPool/AssertionStakingPoolCreator.sol#L9)

```solidity
import "./StakingPoolCreatorUtils.sol";
```

- Found in src/assertionStakingPool/EdgeStakingPoolCreator.sol [Line: 10](https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/assertionStakingPool/EdgeStakingPoolCreator.sol#L10)

```solidity
import "./interfaces/IEdgeStakingPoolCreator.sol";
```

- Found in src/assertionStakingPool/AssertionStakingPool.sol [Line: 10](https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/assertionStakingPool/AssertionStakingPool.sol#L10)

```solidity
import "./AbsBoldStakingPool.sol";
```

- Found in src/assertionStakingPool/EdgeStakingPool.sol [Line: 7](https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/assertionStakingPool/EdgeStakingPool.sol#L7)

```solidity
import "./AbsBoldStakingPool.sol";
```

- Found in src/assertionStakingPool/AssertionStakingPool.sol [Line: 11](https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/assertionStakingPool/AssertionStakingPool.sol#L11)

```solidity
import "./interfaces/IAssertionStakingPool.sol";
```

- Found in src/assertionStakingPool/StakingPoolCreatorUtils.sol [Line: 8](https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/assertionStakingPool/StakingPoolCreatorUtils.sol#L8)

```solidity
import "@openzeppelin/contracts/utils/Create2.sol";
```

- Found in src/assertionStakingPool/EdgeStakingPool.sol [Line: 8](https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/assertionStakingPool/EdgeStakingPool.sol#L8)

```solidity
import "./interfaces/IEdgeStakingPool.sol";
```

- Found in src/assertionStakingPool/AssertionStakingPoolCreator.sol [Line: 8](https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/assertionStakingPool/AssertionStakingPoolCreator.sol#L8)

```solidity
import "./AssertionStakingPool.sol";
```

- Found in src/assertionStakingPool/AssertionStakingPoolCreator.sol [Line: 10](https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/assertionStakingPool/AssertionStakingPoolCreator.sol#L10)

```solidity
import "./interfaces/IAssertionStakingPoolCreator.sol";
```

- Found in src/assertionStakingPool/interfaces/IEdgeStakingPoolCreator.sol [Line: 7](https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/assertionStakingPool/interfaces/IEdgeStakingPoolCreator.sol#L7)

```solidity
import "./IEdgeStakingPool.sol";
```

- Found in src/assertionStakingPool/interfaces/IAssertionStakingPoolCreator.sol [Line: 7](https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/assertionStakingPool/interfaces/IAssertionStakingPoolCreator.sol#L7)

```solidity
import "../../rollup/IRollupLogic.sol";
```

- Found in src/assertionStakingPool/interfaces/IAssertionStakingPool.sol [Line: 7](https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/assertionStakingPool/interfaces/IAssertionStakingPool.sol#L7)

```solidity
import "../../rollup/IRollupLogic.sol";
```

- Found in src/assertionStakingPool/interfaces/IAssertionStakingPoolCreator.sol [Line: 8](https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/assertionStakingPool/interfaces/IAssertionStakingPoolCreator.sol#L8)

```solidity
import "./IAssertionStakingPool.sol";
```

- Found in src/assertionStakingPool/interfaces/IEdgeStakingPool.sol [Line: 7](https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/assertionStakingPool/interfaces/IEdgeStakingPool.sol#L7)

```solidity
import "../../challengeV2/EdgeChallengeManager.sol";
```

- Found in src/assertionStakingPool/interfaces/IEdgeStakingPool.sol [Line: 8](https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/assertionStakingPool/interfaces/IEdgeStakingPool.sol#L8)

```solidity
import "./IAbsBoldStakingPool.sol";
```

- Found in src/assertionStakingPool/interfaces/IAssertionStakingPool.sol [Line: 8](https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/assertionStakingPool/interfaces/IAssertionStakingPool.sol#L8)

```solidity
import "./IAbsBoldStakingPool.sol";
```

- Found in src/rollup/RollupProxy.sol [Line: 7](https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/rollup/RollupProxy.sol#L7)

```solidity
import "../libraries/AdminFallbackProxy.sol";
```

- Found in src/rollup/RollupProxy.sol [Line: 8](https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/rollup/RollupProxy.sol#L8)

```solidity
import "./IRollupAdmin.sol";
```

- Found in src/rollup/RollupAdminLogic.sol [Line: 7](https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/rollup/RollupAdminLogic.sol#L7)

```solidity
import "./IRollupAdmin.sol";
```

- Found in src/rollup/RollupCreator.sol [Line: 8](https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/rollup/RollupCreator.sol#L8)

```solidity
import "./IRollupAdmin.sol";
```

- Found in src/rollup/RollupProxy.sol [Line: 9](https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/rollup/RollupProxy.sol#L9)

```solidity
import "./Config.sol";
```

- Found in src/rollup/IRollupAdmin.sol [Line: 11](https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/rollup/IRollupAdmin.sol#L11)

```solidity
import "./Config.sol";
```

- Found in src/rollup/IRollupCore.sol [Line: 7](https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/rollup/IRollupCore.sol#L7)

```solidity
import "./Assertion.sol";
```

- Found in src/rollup/RollupLib.sol [Line: 13](https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/rollup/RollupLib.sol#L13)

```solidity
import "./Assertion.sol";
```

- Found in src/rollup/RollupCore.sol [Line: 9](https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/rollup/RollupCore.sol#L9)

```solidity
import "./Assertion.sol";
```

- Found in src/rollup/IRollupCore.sol [Line: 9](https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/rollup/IRollupCore.sol#L9)

```solidity
import "../bridge/IOutbox.sol";
```

- Found in src/rollup/IRollupAdmin.sol [Line: 9](https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/rollup/IRollupAdmin.sol#L9)

```solidity
import "../bridge/IOutbox.sol";
```

- Found in src/rollup/IRollupLogic.sol [Line: 9](https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/rollup/IRollupLogic.sol#L9)

```solidity
import "../bridge/IOutbox.sol";
```

- Found in src/rollup/Config.sol [Line: 11](https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/rollup/Config.sol#L11)

```solidity
import "../bridge/IOutbox.sol";
```

- Found in src/rollup/RollupAdminLogic.sol [Line: 10](https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/rollup/RollupAdminLogic.sol#L10)

```solidity
import "../bridge/IOutbox.sol";
```

- Found in src/rollup/RollupLib.sol [Line: 11](https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/rollup/RollupLib.sol#L11)

```solidity
import "../bridge/IOutbox.sol";
```

- Found in src/rollup/RollupCore.sol [Line: 18](https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/rollup/RollupCore.sol#L18)

```solidity
import "../bridge/IOutbox.sol";
```

- Found in src/rollup/IRollupCore.sol [Line: 11](https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/rollup/IRollupCore.sol#L11)

```solidity
import "./IRollupEventInbox.sol";
```

- Found in src/rollup/Config.sol [Line: 13](https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/rollup/Config.sol#L13)

```solidity
import "./IRollupEventInbox.sol";
```

- Found in src/rollup/RollupLib.sol [Line: 14](https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/rollup/RollupLib.sol#L14)

```solidity
import "./IRollupEventInbox.sol";
```

- Found in src/rollup/RollupCore.sol [Line: 11](https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/rollup/RollupCore.sol#L11)

```solidity
import "./IRollupEventInbox.sol";
```

- Found in src/rollup/IRollupCore.sol [Line: 13](https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/rollup/IRollupCore.sol#L13)

```solidity
import "../challengeV2/IAssertionChain.sol";
```

- Found in src/rollup/Assertion.sol [Line: 7](https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/rollup/Assertion.sol#L7)

```solidity
import "./AssertionState.sol";
```

- Found in src/rollup/IRollupAdmin.sol [Line: 7](https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/rollup/IRollupAdmin.sol#L7)

```solidity
import "./IRollupCore.sol";
```

- Found in src/rollup/IRollupLogic.sol [Line: 7](https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/rollup/IRollupLogic.sol#L7)

```solidity
import "./IRollupCore.sol";
```

- Found in src/rollup/RollupCore.sol [Line: 12](https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/rollup/RollupCore.sol#L12)

```solidity
import "./IRollupCore.sol";
```

- Found in src/rollup/IRollupAdmin.sol [Line: 10](https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/rollup/IRollupAdmin.sol#L10)

```solidity
import "../bridge/IOwnable.sol";
```

- Found in src/rollup/IRollupLogic.sol [Line: 10](https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/rollup/IRollupLogic.sol#L10)

```solidity
import "../bridge/IOwnable.sol";
```

- Found in src/rollup/AssertionState.sol [Line: 9](https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/rollup/AssertionState.sol#L9)

```solidity
import "../osp/IOneStepProofEntry.sol";
```

- Found in src/challengeV2/IAssertionChain.sol [Line: 8](https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/challengeV2/IAssertionChain.sol#L8)

```solidity
import "../osp/IOneStepProofEntry.sol";
```

- Found in src/rollup/Config.sol [Line: 14](https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/rollup/Config.sol#L14)

```solidity
import "./IRollupLogic.sol";
```

- Found in src/rollup/RollupAdminLogic.sol [Line: 8](https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/rollup/RollupAdminLogic.sol#L8)

```solidity
import "./IRollupLogic.sol";
```

- Found in src/rollup/RollupUserLogic.sol [Line: 12](https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/rollup/RollupUserLogic.sol#L12)

```solidity
import "./IRollupLogic.sol";
```

- Found in src/rollup/RollupAdminLogic.sol [Line: 9](https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/rollup/RollupAdminLogic.sol#L9)

```solidity
import "./RollupCore.sol";
```

- Found in src/rollup/RollupUserLogic.sol [Line: 11](https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/rollup/RollupUserLogic.sol#L11)

```solidity
import "./RollupCore.sol";
```

- Found in src/rollup/RollupAdminLogic.sol [Line: 12](https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/rollup/RollupAdminLogic.sol#L12)

```solidity
import "../libraries/DoubleLogicUUPSUpgradeable.sol";
```

- Found in src/rollup/RollupAdminLogic.sol [Line: 13](https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/rollup/RollupAdminLogic.sol#L13)

```solidity
import "@openzeppelin/contracts/proxy/beacon/UpgradeableBeacon.sol";
```

- Found in src/rollup/BOLDUpgradeAction.sol [Line: 7](https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/rollup/BOLDUpgradeAction.sol#L7)

```solidity
import "@openzeppelin/contracts-upgradeable/utils/Create2Upgradeable.sol";
```

- Found in src/rollup/BOLDUpgradeAction.sol [Line: 9](https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/rollup/BOLDUpgradeAction.sol#L9)

```solidity
import "./RollupProxy.sol";
```

- Found in src/rollup/RollupCreator.sol [Line: 7](https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/rollup/RollupCreator.sol#L7)

```solidity
import "./RollupProxy.sol";
```

- Found in src/rollup/BOLDUpgradeAction.sol [Line: 10](https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/rollup/BOLDUpgradeAction.sol#L10)

```solidity
import "./RollupLib.sol";
```

- Found in src/rollup/RollupCore.sol [Line: 10](https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/rollup/RollupCore.sol#L10)

```solidity
import "./RollupLib.sol";
```

- Found in src/rollup/BOLDUpgradeAction.sol [Line: 11](https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/rollup/BOLDUpgradeAction.sol#L11)

```solidity
import "./RollupAdminLogic.sol";
```

- Found in src/rollup/RollupCreator.sol [Line: 12](https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/rollup/RollupCreator.sol#L12)

```solidity
import "@openzeppelin/contracts/proxy/transparent/TransparentUpgradeableProxy.sol";
```

- Found in src/rollup/RollupUserLogic.sol [Line: 10](https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/rollup/RollupUserLogic.sol#L10)

```solidity
import "../libraries/UUPSNotUpgradeable.sol";
```

- Found in src/rollup/BridgeCreator.sol [Line: 9](https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/rollup/BridgeCreator.sol#L9)

```solidity
import "../bridge/Inbox.sol";
```

- Found in src/rollup/BridgeCreator.sol [Line: 10](https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/rollup/BridgeCreator.sol#L10)

```solidity
import "../bridge/Outbox.sol";
```

- Found in src/rollup/BridgeCreator.sol [Line: 11](https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/rollup/BridgeCreator.sol#L11)

```solidity
import "./RollupEventInbox.sol";
```

- Found in src/rollup/BridgeCreator.sol [Line: 12](https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/rollup/BridgeCreator.sol#L12)

```solidity
import "../bridge/ERC20Bridge.sol";
```

- Found in src/rollup/BridgeCreator.sol [Line: 13](https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/rollup/BridgeCreator.sol#L13)

```solidity
import "../bridge/ERC20Inbox.sol";
```

- Found in src/rollup/BridgeCreator.sol [Line: 14](https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/rollup/BridgeCreator.sol#L14)

```solidity
import "../rollup/ERC20RollupEventInbox.sol";
```

- Found in src/rollup/BridgeCreator.sol [Line: 15](https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/rollup/BridgeCreator.sol#L15)

```solidity
import "../bridge/ERC20Outbox.sol";
```

- Found in src/rollup/RollupCreator.sol [Line: 9](https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/rollup/RollupCreator.sol#L9)

```solidity
import "./BridgeCreator.sol";
```

- Found in src/challengeV2/EdgeChallengeManager.sol [Line: 7](https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/challengeV2/EdgeChallengeManager.sol#L7)

```solidity
import "../rollup/Assertion.sol";
```

- Found in src/challengeV2/IAssertionChain.sol [Line: 9](https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/challengeV2/IAssertionChain.sol#L9)

```solidity
import "../rollup/Assertion.sol";
```

- Found in src/challengeV2/EdgeChallengeManager.sol [Line: 8](https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/challengeV2/EdgeChallengeManager.sol#L8)

```solidity
import "./libraries/UintUtilsLib.sol";
```

- Found in src/challengeV2/EdgeChallengeManager.sol [Line: 9](https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/challengeV2/EdgeChallengeManager.sol#L9)

```solidity
import "./IAssertionChain.sol";
```

- Found in src/challengeV2/EdgeChallengeManager.sol [Line: 10](https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/challengeV2/EdgeChallengeManager.sol#L10)

```solidity
import "./libraries/EdgeChallengeManagerLib.sol";
```

- Found in src/challengeV2/EdgeChallengeManager.sol [Line: 11](https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/challengeV2/EdgeChallengeManager.sol#L11)

```solidity
import "../libraries/Constants.sol";
```

- Found in src/challengeV2/libraries/ChallengeErrors.sol [Line: 7](https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/challengeV2/libraries/ChallengeErrors.sol#L7)

```solidity
import "./Enums.sol";
```

- Found in src/challengeV2/libraries/ChallengeEdgeLib.sol [Line: 7](https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/challengeV2/libraries/ChallengeEdgeLib.sol#L7)

```solidity
import "./Enums.sol";
```

- Found in src/challengeV2/libraries/EdgeChallengeManagerLib.sol [Line: 7](https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/challengeV2/libraries/EdgeChallengeManagerLib.sol#L7)

```solidity
import "./UintUtilsLib.sol";
```

- Found in src/challengeV2/libraries/MerkleTreeLib.sol [Line: 9](https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/challengeV2/libraries/MerkleTreeLib.sol#L9)

```solidity
import "./UintUtilsLib.sol";
```

- Found in src/challengeV2/libraries/EdgeChallengeManagerLib.sol [Line: 8](https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/challengeV2/libraries/EdgeChallengeManagerLib.sol#L8)

```solidity
import "./MerkleTreeLib.sol";
```

- Found in src/challengeV2/libraries/EdgeChallengeManagerLib.sol [Line: 9](https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/challengeV2/libraries/EdgeChallengeManagerLib.sol#L9)

```solidity
import "./ChallengeEdgeLib.sol";
```

- Found in src/challengeV2/libraries/EdgeChallengeManagerLib.sol [Line: 10](https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/challengeV2/libraries/EdgeChallengeManagerLib.sol#L10)

```solidity
import "../../osp/IOneStepProofEntry.sol";
```

- Found in src/challengeV2/libraries/EdgeChallengeManagerLib.sol [Line: 11](https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/challengeV2/libraries/EdgeChallengeManagerLib.sol#L11)

```solidity
import "../../rollup/AssertionState.sol";
```

- Found in src/challengeV2/libraries/EdgeChallengeManagerLib.sol [Line: 12](https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/challengeV2/libraries/EdgeChallengeManagerLib.sol#L12)

```solidity
import "../../libraries/Constants.sol";
```

- Found in src/challengeV2/libraries/EdgeChallengeManagerLib.sol [Line: 13](https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/challengeV2/libraries/EdgeChallengeManagerLib.sol#L13)

```solidity
import "./ChallengeErrors.sol";
```

- Found in src/challengeV2/libraries/ChallengeEdgeLib.sol [Line: 8](https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/challengeV2/libraries/ChallengeEdgeLib.sol#L8)

```solidity
import "./ChallengeErrors.sol";
```

- Found in src/challengeV2/libraries/MerkleTreeLib.sol [Line: 7](https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/challengeV2/libraries/MerkleTreeLib.sol#L7)

```solidity
import "../../libraries/MerkleLib.sol";
```

- Found in src/challengeV2/libraries/MerkleTreeLib.sol [Line: 8](https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/challengeV2/libraries/MerkleTreeLib.sol#L8)

```solidity
import "./ArrayUtilsLib.sol";
```

</details>

### [N-12] Missing inline documentation for function parameters

Function parameters in Solidity code lack inline documentation. Documenting function parameters helps clarify the purpose and usage of each parameter, optimizing the readability and maintainability of the code. Consider adding inline documentation for each function parameter to provide clear information about their purpose and usage.

<details>
<summary><i>Affected Code Snippets</i></summary>

- Found in src/bridge/ISequencerInbox.sol [Line: 148](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/bridge/ISequencerInbox.sol#L148)

```solidity
function inboxAccs(uint256 index) external view returns (bytes32);
```

- Found in src/bridge/ISequencerInbox.sol [Line: 152](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/bridge/ISequencerInbox.sol#L152)

```solidity
function isValidKeysetHash(bytes32 ksHash) external view returns (bool);
```

- Found in src/bridge/ISequencerInbox.sol [Line: 155](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/bridge/ISequencerInbox.sol#L155)

```solidity
function getKeysetCreationBlock(bytes32 ksHash) external view returns (uint256);
```

- Found in src/bridge/ISequencerInbox.sol [Line: 171](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/bridge/ISequencerInbox.sol#L171)

```solidity
function addSequencerL2BatchFromOrigin(
uint256 sequenceNumber,
bytes calldata data,
uint256 afterDelayedMessagesRead,
IGasRefunder gasRefunder
) external;
```

- Found in src/bridge/ISequencerInbox.sol [Line: 179](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/bridge/ISequencerInbox.sol#L179)

```solidity
function addSequencerL2BatchFromOrigin(
uint256 sequenceNumber,
bytes calldata data,
uint256 afterDelayedMessagesRead,
IGasRefunder gasRefunder,
uint256 prevMessageCount,
uint256 newMessageCount
) external;
```

- Found in src/bridge/ISequencerInbox.sol [Line: 188](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/bridge/ISequencerInbox.sol#L188)

```solidity
function addSequencerL2Batch(
uint256 sequenceNumber,
bytes calldata data,
uint256 afterDelayedMessagesRead,
IGasRefunder gasRefunder,
uint256 prevMessageCount,
uint256 newMessageCount
) external;
```

- Found in src/bridge/ISequencerInbox.sol [Line: 197](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/bridge/ISequencerInbox.sol#L197)

```solidity
function addSequencerL2BatchFromBlobs(
uint256 sequenceNumber,
uint256 afterDelayedMessagesRead,
IGasRefunder gasRefunder,
uint256 prevMessageCount,
uint256 newMessageCount
) external;
```

- Found in src/bridge/ISequencerInbox.sol [Line: 207](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/bridge/ISequencerInbox.sol#L207)

```solidity
function addSequencerL2BatchFromBlobsDelayProof(
uint256 sequenceNumber,
uint256 afterDelayedMessagesRead,
IGasRefunder gasRefunder,
uint256 prevMessageCount,
uint256 newMessageCount,
DelayProof calldata delayProof
) external;
```

- Found in src/bridge/ISequencerInbox.sol [Line: 219](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/bridge/ISequencerInbox.sol#L219)

```solidity
function addSequencerL2BatchFromOriginDelayProof(
uint256 sequenceNumber,
bytes calldata data,
uint256 afterDelayedMessagesRead,
IGasRefunder gasRefunder,
uint256 prevMessageCount,
uint256 newMessageCount,
DelayProof calldata delayProof
) external;
```

- Found in src/bridge/ISequencerInbox.sol [Line: 231](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/bridge/ISequencerInbox.sol#L231)

```solidity
function addSequencerL2BatchDelayProof(
uint256 sequenceNumber,
bytes calldata data,
uint256 afterDelayedMessagesRead,
IGasRefunder gasRefunder,
uint256 prevMessageCount,
uint256 newMessageCount,
DelayProof calldata delayProof
) external;
```

- Found in src/bridge/ISequencerInbox.sol [Line: 247](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/bridge/ISequencerInbox.sol#L247)

```solidity
function setMaxTimeVariation(MaxTimeVariation memory maxTimeVariation_) external;
```

- Found in src/bridge/ISequencerInbox.sol [Line: 254](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/bridge/ISequencerInbox.sol#L254)

```solidity
function setIsBatchPoster(address addr, bool isBatchPoster_) external;
```

- Found in src/bridge/ISequencerInbox.sol [Line: 260](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/bridge/ISequencerInbox.sol#L260)

```solidity
function setValidKeyset(bytes calldata keysetBytes) external;
```

- Found in src/bridge/ISequencerInbox.sol [Line: 266](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/bridge/ISequencerInbox.sol#L266)

```solidity
function invalidateKeysetHash(bytes32 ksHash) external;
```

- Found in src/bridge/ISequencerInbox.sol [Line: 274](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/bridge/ISequencerInbox.sol#L274)

```solidity
function setIsSequencer(address addr, bool isSequencer_) external;
```

- Found in src/bridge/ISequencerInbox.sol [Line: 280](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/bridge/ISequencerInbox.sol#L280)

```solidity
function setBatchPosterManager(address newBatchPosterManager) external;
```

- Found in src/bridge/ISequencerInbox.sol [Line: 287](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/bridge/ISequencerInbox.sol#L287)

```solidity
function initialize(
IBridge bridge_,
MaxTimeVariation calldata maxTimeVariation_,
BufferConfig calldata bufferConfig_
) external;
```

- Found in src/bridge/SequencerInbox.sol [Line: 165](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/bridge/SequencerInbox.sol#L165)

```solidity
function postUpgradeInit(BufferConfig memory bufferConfig_)
external
onlyDelegated
onlyProxyOwner
{
```

- Found in src/bridge/SequencerInbox.sol [Line: 181](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/bridge/SequencerInbox.sol#L181)

```solidity
function initialize(
IBridge bridge_,
ISequencerInbox.MaxTimeVariation calldata maxTimeVariation_,
BufferConfig memory bufferConfig_
) external onlyDelegated {
```

- Found in src/bridge/SequencerInbox.sol [Line: 291](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/bridge/SequencerInbox.sol#L291)

```solidity
function forceInclusion(
uint256 _totalDelayedMessagesRead,
uint8 kind,
uint64[2] calldata l1BlockAndTime,
uint256 baseFeeL1,
address sender,
bytes32 messageDataHash
) external {
```

- Found in src/bridge/SequencerInbox.sol [Line: 360](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/bridge/SequencerInbox.sol#L360)

```solidity
function addSequencerL2BatchFromOrigin(
uint256,
bytes calldata,
uint256,
IGasRefunder
) external pure {
```

- Found in src/bridge/SequencerInbox.sol [Line: 370](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/bridge/SequencerInbox.sol#L370)

```solidity
function addSequencerL2BatchFromOrigin(
uint256 sequenceNumber,
bytes calldata data,
uint256 afterDelayedMessagesRead,
IGasRefunder gasRefunder,
uint256 prevMessageCount,
uint256 newMessageCount
) external refundsGas(gasRefunder, IReader4844(address(0))) {
```

- Found in src/bridge/SequencerInbox.sol [Line: 394](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/bridge/SequencerInbox.sol#L394)

```solidity
function addSequencerL2BatchFromBlobs(
uint256 sequenceNumber,
uint256 afterDelayedMessagesRead,
IGasRefunder gasRefunder,
uint256 prevMessageCount,
uint256 newMessageCount
) external refundsGas(gasRefunder, reader4844) {
```

- Found in src/bridge/SequencerInbox.sol [Line: 413](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/bridge/SequencerInbox.sol#L413)

```solidity
function addSequencerL2BatchFromBlobsDelayProof(
uint256 sequenceNumber,
uint256 afterDelayedMessagesRead,
IGasRefunder gasRefunder,
uint256 prevMessageCount,
uint256 newMessageCount,
DelayProof calldata delayProof
) external refundsGas(gasRefunder, reader4844) {
```

- Found in src/bridge/SequencerInbox.sol [Line: 434](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/bridge/SequencerInbox.sol#L434)

```solidity
function addSequencerL2BatchFromOriginDelayProof(
uint256 sequenceNumber,
bytes calldata data,
uint256 afterDelayedMessagesRead,
IGasRefunder gasRefunder,
uint256 prevMessageCount,
uint256 newMessageCount,
DelayProof calldata delayProof
) external refundsGas(gasRefunder, IReader4844(address(0))) {
```

- Found in src/bridge/SequencerInbox.sol [Line: 459](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/bridge/SequencerInbox.sol#L459)

```solidity
function addSequencerL2BatchFromBlobsImpl(
uint256 sequenceNumber,
uint256 afterDelayedMessagesRead,
uint256 prevMessageCount,
uint256 newMessageCount
) internal {
```

- Found in src/bridge/SequencerInbox.sol [Line: 516](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/bridge/SequencerInbox.sol#L516)

```solidity
function addSequencerL2BatchFromCalldataImpl(
uint256 sequenceNumber,
bytes calldata data,
uint256 afterDelayedMessagesRead,
uint256 prevMessageCount,
uint256 newMessageCount,
bool isFromOrigin
) internal {
```

- Found in src/bridge/SequencerInbox.sol [Line: 564](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/bridge/SequencerInbox.sol#L564)

```solidity
function addSequencerL2Batch(
uint256 sequenceNumber,
bytes calldata data,
uint256 afterDelayedMessagesRead,
IGasRefunder gasRefunder,
uint256 prevMessageCount,
uint256 newMessageCount
) external override refundsGas(gasRefunder, IReader4844(address(0))) {
```

- Found in src/bridge/SequencerInbox.sol [Line: 586](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/bridge/SequencerInbox.sol#L586)

```solidity
function addSequencerL2BatchDelayProof(
uint256 sequenceNumber,
bytes calldata data,
uint256 afterDelayedMessagesRead,
IGasRefunder gasRefunder,
uint256 prevMessageCount,
uint256 newMessageCount,
DelayProof calldata delayProof
) external refundsGas(gasRefunder, IReader4844(address(0))) {
```

- Found in src/bridge/SequencerInbox.sol [Line: 609](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/bridge/SequencerInbox.sol#L609)

```solidity
function delayProofImpl(uint256 afterDelayedMessagesRead, DelayProof memory delayProof)
internal
{
```

- Found in src/bridge/SequencerInbox.sol [Line: 632](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/bridge/SequencerInbox.sol#L632)

```solidity
function isDelayProofRequired(uint256 afterDelayedMessagesRead) internal view returns (bool) {
```

- Found in src/bridge/SequencerInbox.sol [Line: 641](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/bridge/SequencerInbox.sol#L641)

```solidity
function packHeader(uint256 afterDelayedMessagesRead)
internal
view
returns (bytes memory, IBridge.TimeBounds memory)
{
```

- Found in src/bridge/SequencerInbox.sol [Line: 692](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/bridge/SequencerInbox.sol#L692)

```solidity
function formCallDataHash(bytes calldata data, uint256 afterDelayedMessagesRead)
internal
view
returns (bytes32, IBridge.TimeBounds memory)
{
```

- Found in src/bridge/SequencerInbox.sol [Line: 759](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/bridge/SequencerInbox.sol#L759)

```solidity
function submitBatchSpendingReport(
bytes32 dataHash,
uint256 seqMessageIndex,
uint256 gasPrice,
uint256 extraGas
) internal {
```

- Found in src/bridge/SequencerInbox.sol [Line: 795](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/bridge/SequencerInbox.sol#L795)

```solidity
function addSequencerL2BatchImpl(
bytes32 dataHash,
uint256 afterDelayedMessagesRead,
uint256 calldataLengthPosted,
uint256 prevMessageCount,
uint256 newMessageCount
)
internal
returns (
uint256 seqMessageIndex,
bytes32 beforeAcc,
bytes32 delayedAcc,
bytes32 acc
)
{
```

- Found in src/bridge/SequencerInbox.sol [Line: 828](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/bridge/SequencerInbox.sol#L828)

```solidity
function inboxAccs(uint256 index) external view returns (bytes32) {
```

- Found in src/bridge/SequencerInbox.sol [Line: 837](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/bridge/SequencerInbox.sol#L837)

```solidity
function forceInclusionDeadline(uint64 blockNumber) external view returns (uint64) {
```

- Found in src/bridge/SequencerInbox.sol [Line: 847](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/bridge/SequencerInbox.sol#L847)

```solidity
function delayBufferableBlocks(uint64 _buffer) internal view returns (uint64) {
```

- Found in src/bridge/SequencerInbox.sol [Line: 851](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/bridge/SequencerInbox.sol#L851)

```solidity
function _setBufferConfig(BufferConfig memory bufferConfig_) internal {
```

- Found in src/bridge/SequencerInbox.sol [Line: 871](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/bridge/SequencerInbox.sol#L871)

```solidity
function _setMaxTimeVariation(ISequencerInbox.MaxTimeVariation memory maxTimeVariation_)
internal
{
```

- Found in src/bridge/SequencerInbox.sol [Line: 889](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/bridge/SequencerInbox.sol#L889)

```solidity
function setMaxTimeVariation(ISequencerInbox.MaxTimeVariation memory maxTimeVariation_)
external
onlyRollupOwner
{
```

- Found in src/bridge/SequencerInbox.sol [Line: 898](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/bridge/SequencerInbox.sol#L898)

```solidity
function setIsBatchPoster(address addr, bool isBatchPoster_)
external
onlyRollupOwnerOrBatchPosterManager
{
```

- Found in src/bridge/SequencerInbox.sol [Line: 907](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/bridge/SequencerInbox.sol#L907)

```solidity
function setValidKeyset(bytes calldata keysetBytes) external onlyRollupOwner {
```

- Found in src/bridge/SequencerInbox.sol [Line: 926](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/bridge/SequencerInbox.sol#L926)

```solidity
function invalidateKeysetHash(bytes32 ksHash) external onlyRollupOwner {
```

- Found in src/bridge/SequencerInbox.sol [Line: 937](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/bridge/SequencerInbox.sol#L937)

```solidity
function setIsSequencer(address addr, bool isSequencer_)
external
onlyRollupOwnerOrBatchPosterManager
{
```

- Found in src/bridge/SequencerInbox.sol [Line: 946](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/bridge/SequencerInbox.sol#L946)

```solidity
function setBatchPosterManager(address newBatchPosterManager) external onlyRollupOwner {
```

- Found in src/bridge/SequencerInbox.sol [Line: 951](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/bridge/SequencerInbox.sol#L951)

```solidity
function setBufferConfig(BufferConfig memory bufferConfig_) external onlyRollupOwner {
```

- Found in src/bridge/SequencerInbox.sol [Line: 956](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/bridge/SequencerInbox.sol#L956)

```solidity
function isValidKeysetHash(bytes32 ksHash) external view returns (bool) {
```

- Found in src/bridge/SequencerInbox.sol [Line: 961](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/bridge/SequencerInbox.sol#L961)

```solidity
function getKeysetCreationBlock(bytes32 ksHash) external view returns (uint256) {
```

- Found in src/bridge/DelayBuffer.sol [Line: 68](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/bridge/DelayBuffer.sol#L68)

```solidity
function update(BufferData storage self, uint64 blockNumber) internal {
```

- Found in src/bridge/DelayBuffer.sol [Line: 82](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/bridge/DelayBuffer.sol#L82)

```solidity
function calcPendingBuffer(BufferData storage self, uint64 blockNumber)
internal
view
returns (uint64)
{
```

- Found in src/bridge/DelayBuffer.sol [Line: 104](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/bridge/DelayBuffer.sol#L104)

```solidity
function isSynced(BufferData storage self) internal view returns (bool) {
```

- Found in src/bridge/DelayBuffer.sol [Line: 108](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/bridge/DelayBuffer.sol#L108)

```solidity
function isUpdatable(BufferData storage self) internal view returns (bool) {
```

- Found in src/bridge/DelayBuffer.sol [Line: 115](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/bridge/DelayBuffer.sol#L115)

```solidity
function isValidBufferConfig(BufferConfig memory config) internal pure returns (bool) {
```

- Found in src/assertionStakingPool/EdgeStakingPoolCreator.sol [Line: 15](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/assertionStakingPool/EdgeStakingPoolCreator.sol#L15)

```solidity
function createPool(
address challengeManager,
bytes32 edgeId
) external returns (IEdgeStakingPool) {
```

- Found in src/assertionStakingPool/EdgeStakingPoolCreator.sol [Line: 25](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/assertionStakingPool/EdgeStakingPoolCreator.sol#L25)

```solidity
function getPool(
address challengeManager,
bytes32 edgeId
) public view returns (IEdgeStakingPool) {
```

- Found in src/assertionStakingPool/AssertionStakingPool.sol [Line: 40](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/assertionStakingPool/AssertionStakingPool.sol#L40)

```solidity
function createAssertion(AssertionInputs calldata assertionInputs) external {
```

- Found in src/assertionStakingPool/StakingPoolCreatorUtils.sol [Line: 13](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/assertionStakingPool/StakingPoolCreatorUtils.sol#L13)

```solidity
function getPool(bytes memory creationCode, bytes memory args) internal view returns (address) {
```

- Found in src/assertionStakingPool/EdgeStakingPool.sol [Line: 44](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/assertionStakingPool/EdgeStakingPool.sol#L44)

```solidity
function createEdge(CreateEdgeArgs calldata args) external {
```

- Found in src/assertionStakingPool/AbsBoldStakingPool.sol [Line: 29](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/assertionStakingPool/AbsBoldStakingPool.sol#L29)

```solidity
function depositIntoPool(uint256 amount) external {
```

- Found in src/assertionStakingPool/AbsBoldStakingPool.sol [Line: 41](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/assertionStakingPool/AbsBoldStakingPool.sol#L41)

```solidity
function withdrawFromPool(uint256 amount) public {
```

- Found in src/assertionStakingPool/AssertionStakingPoolCreator.sol [Line: 15](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/assertionStakingPool/AssertionStakingPoolCreator.sol#L15)

```solidity
function createPool(
address _rollup,
bytes32 _assertionHash
) external returns (IAssertionStakingPool) {
```

- Found in src/assertionStakingPool/AssertionStakingPoolCreator.sol [Line: 25](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/assertionStakingPool/AssertionStakingPoolCreator.sol#L25)

```solidity
function getPool(
address _rollup,
bytes32 _assertionHash
) public view returns (IAssertionStakingPool) {
```

- Found in src/assertionStakingPool/interfaces/IEdgeStakingPool.sol [Line: 15](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/assertionStakingPool/interfaces/IEdgeStakingPool.sol#L15)

```solidity
function createEdge(CreateEdgeArgs calldata args) external;
```

- Found in src/assertionStakingPool/interfaces/IAssertionStakingPool.sol [Line: 12](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/assertionStakingPool/interfaces/IAssertionStakingPool.sol#L12)

```solidity
function createAssertion(AssertionInputs calldata assertionInputs) external;
```

- Found in src/rollup/RollupProxy.sol [Line: 12](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/rollup/RollupProxy.sol#L12)

```solidity
function initializeProxy(Config memory config, ContractDependencies memory connectedContracts)
external
{
```

- Found in src/rollup/IRollupCore.sol [Line: 77](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/rollup/IRollupCore.sol#L77)

```solidity
function getAssertion(bytes32 assertionHash) external view returns (AssertionNode memory);
```

- Found in src/rollup/IRollupCore.sol [Line: 86](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/rollup/IRollupCore.sol#L86)

```solidity
function getAssertionCreationBlockForLogLookup(bytes32 assertionHash) external view returns (uint256);
```

- Found in src/rollup/IRollupCore.sol [Line: 93](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/rollup/IRollupCore.sol#L93)

```solidity
function getStakerAddress(uint64 stakerNum) external view returns (address);
```

- Found in src/rollup/IRollupCore.sol [Line: 100](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/rollup/IRollupCore.sol#L100)

```solidity
function isStaked(address staker) external view returns (bool);
```

- Found in src/rollup/IRollupCore.sol [Line: 107](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/rollup/IRollupCore.sol#L107)

```solidity
function latestStakedAssertion(address staker) external view returns (bytes32);
```

- Found in src/rollup/IRollupCore.sol [Line: 114](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/rollup/IRollupCore.sol#L114)

```solidity
function amountStaked(address staker) external view returns (uint256);
```

- Found in src/rollup/IRollupCore.sol [Line: 121](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/rollup/IRollupCore.sol#L121)

```solidity
function getStaker(address staker) external view returns (Staker memory);
```

- Found in src/rollup/IRollupCore.sol [Line: 128](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/rollup/IRollupCore.sol#L128)

```solidity
function withdrawableFunds(address owner) external view returns (uint256);
```

- Found in src/rollup/Assertion.sol [Line: 70](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/rollup/Assertion.sol#L70)

```solidity
function createAssertion(
bool _isFirstChild,
bytes32 _configHash
) internal view returns (AssertionNode memory) {
```

- Found in src/rollup/Assertion.sol [Line: 85](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/rollup/Assertion.sol#L85)

```solidity
function childCreated(AssertionNode storage self) internal {
```

- Found in src/rollup/Assertion.sol [Line: 93](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/rollup/Assertion.sol#L93)

```solidity
function requireExists(AssertionNode memory self) internal pure {
```

- Found in src/rollup/IRollupAdmin.sol [Line: 16](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/rollup/IRollupAdmin.sol#L16)

```solidity
function initialize(Config calldata config, ContractDependencies calldata connectedContracts) external;
```

- Found in src/rollup/IRollupAdmin.sol [Line: 22](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/rollup/IRollupAdmin.sol#L22)

```solidity
function setOutbox(IOutbox _outbox) external;
```

- Found in src/rollup/IRollupAdmin.sol [Line: 28](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/rollup/IRollupAdmin.sol#L28)

```solidity
function removeOldOutbox(address _outbox) external;
```

- Found in src/rollup/IRollupAdmin.sol [Line: 35](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/rollup/IRollupAdmin.sol#L35)

```solidity
function setDelayedInbox(address _inbox, bool _enabled) external;
```

- Found in src/rollup/IRollupAdmin.sol [Line: 54](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/rollup/IRollupAdmin.sol#L54)

```solidity
function setValidator(address[] memory _validator, bool[] memory _val) external;
```

- Found in src/rollup/IRollupAdmin.sol [Line: 60](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/rollup/IRollupAdmin.sol#L60)

```solidity
function setOwner(address newOwner) external;
```

- Found in src/rollup/IRollupAdmin.sol [Line: 66](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/rollup/IRollupAdmin.sol#L66)

```solidity
function setMinimumAssertionPeriod(uint256 newPeriod) external;
```

- Found in src/rollup/IRollupAdmin.sol [Line: 72](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/rollup/IRollupAdmin.sol#L72)

```solidity
function setConfirmPeriodBlocks(uint64 newConfirmPeriod) external;
```

- Found in src/rollup/IRollupAdmin.sol [Line: 78](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/rollup/IRollupAdmin.sol#L78)

```solidity
function setBaseStake(uint256 newBaseStake) external;
```

- Found in src/rollup/IRollupAdmin.sol [Line: 80](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/rollup/IRollupAdmin.sol#L80)

```solidity
function forceRefundStaker(address[] memory stacker) external;
```

- Found in src/rollup/IRollupAdmin.sol [Line: 82](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/rollup/IRollupAdmin.sol#L82)

```solidity
function forceCreateAssertion(
bytes32 prevAssertionHash,
AssertionInputs calldata assertion,
bytes32 expectedAssertionHash
) external;
```

- Found in src/rollup/IRollupAdmin.sol [Line: 88](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/rollup/IRollupAdmin.sol#L88)

```solidity
function forceConfirmAssertion(
bytes32 assertionHash,
bytes32 parentAssertionHash,
AssertionState calldata confirmState,
bytes32 inboxAcc
) external;
```

- Found in src/rollup/IRollupAdmin.sol [Line: 95](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/rollup/IRollupAdmin.sol#L95)

```solidity
function setLoserStakeEscrow(address newLoserStakerEscrow) external;
```

- Found in src/rollup/IRollupAdmin.sol [Line: 101](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/rollup/IRollupAdmin.sol#L101)

```solidity
function setWasmModuleRoot(bytes32 newWasmModuleRoot) external;
```

- Found in src/rollup/IRollupAdmin.sol [Line: 107](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/rollup/IRollupAdmin.sol#L107)

```solidity
function setSequencerInbox(address _sequencerInbox) external;
```

- Found in src/rollup/IRollupAdmin.sol [Line: 113](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/rollup/IRollupAdmin.sol#L113)

```solidity
function setValidatorWhitelistDisabled(bool _validatorWhitelistDisabled) external;
```

- Found in src/rollup/IRollupAdmin.sol [Line: 119](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/rollup/IRollupAdmin.sol#L119)

```solidity
function setChallengeManager(address _challengeManager) external;
```

- Found in src/rollup/IRollupLogic.sol [Line: 15](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/rollup/IRollupLogic.sol#L15)

```solidity
function initialize(address stakeToken) external view;
```

- Found in src/rollup/IRollupLogic.sol [Line: 21](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/rollup/IRollupLogic.sol#L21)

```solidity
function confirmAssertion(
bytes32 assertionHash,
bytes32 prevAssertionHash,
AssertionState calldata confirmState,
bytes32 winningEdgeId,
ConfigData calldata prevConfig,
bytes32 inboxAcc
) external;
```

- Found in src/rollup/IRollupLogic.sol [Line: 30](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/rollup/IRollupLogic.sol#L30)

```solidity
function stakeOnNewAssertion(AssertionInputs calldata assertion, bytes32 expectedAssertionHash) external;
```

- Found in src/rollup/IRollupLogic.sol [Line: 34](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/rollup/IRollupLogic.sol#L34)

```solidity
function reduceDeposit(uint256 target) external;
```

- Found in src/rollup/IRollupLogic.sol [Line: 38](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/rollup/IRollupLogic.sol#L38)

```solidity
function newStakeOnNewAssertion(
uint256 tokenAmount,
AssertionInputs calldata assertion,
bytes32 expectedAssertionHash
) external;
```

- Found in src/rollup/IRollupLogic.sol [Line: 44](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/rollup/IRollupLogic.sol#L44)

```solidity
function newStakeOnNewAssertion(
uint256 tokenAmount,
AssertionInputs calldata assertion,
bytes32 expectedAssertionHash,
address withdrawalAddress
) external;
```

- Found in src/rollup/IRollupLogic.sol [Line: 51](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/rollup/IRollupLogic.sol#L51)

```solidity
function addToDeposit(address stakerAddress, uint256 tokenAmount) external;
```

- Found in src/rollup/AssertionState.sol [Line: 18](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/rollup/AssertionState.sol#L18)

```solidity
function toExecutionState(AssertionState memory state) internal pure returns (ExecutionState memory) {
```

- Found in src/rollup/AssertionState.sol [Line: 22](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/rollup/AssertionState.sol#L22)

```solidity
function hash(AssertionState memory state) internal pure returns (bytes32) {
```

- Found in src/rollup/RollupAdminLogic.sol [Line: 18](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/rollup/RollupAdminLogic.sol#L18)

```solidity
function initialize(Config calldata config, ContractDependencies calldata connectedContracts)
external
override
onlyProxy
initializer
{
```

- Found in src/rollup/RollupAdminLogic.sol [Line: 117](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/rollup/RollupAdminLogic.sol#L117)

```solidity
function setOutbox(IOutbox _outbox) external override {
```

- Found in src/rollup/RollupAdminLogic.sol [Line: 127](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/rollup/RollupAdminLogic.sol#L127)

```solidity
function removeOldOutbox(address _outbox) external override {
```

- Found in src/rollup/RollupAdminLogic.sol [Line: 138](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/rollup/RollupAdminLogic.sol#L138)

```solidity
function setDelayedInbox(address _inbox, bool _enabled) external override {
```

- Found in src/rollup/RollupAdminLogic.sol [Line: 166](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/rollup/RollupAdminLogic.sol#L166)

```solidity
function _authorizeUpgrade(address newImplementation) internal override {}
```

- Found in src/rollup/RollupAdminLogic.sol [Line: 171](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/rollup/RollupAdminLogic.sol#L171)

```solidity
function _authorizeSecondaryUpgrade(address newImplementation) internal override {}
```

- Found in src/rollup/RollupAdminLogic.sol [Line: 180](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/rollup/RollupAdminLogic.sol#L180)

```solidity
function setValidator(address[] calldata _validator, bool[] calldata _val) external override {
```

- Found in src/rollup/RollupAdminLogic.sol [Line: 195](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/rollup/RollupAdminLogic.sol#L195)

```solidity
function setOwner(address newOwner) external override {
```

- Found in src/rollup/RollupAdminLogic.sol [Line: 204](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/rollup/RollupAdminLogic.sol#L204)

```solidity
function setMinimumAssertionPeriod(uint256 newPeriod) external override {
```

- Found in src/rollup/RollupAdminLogic.sol [Line: 213](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/rollup/RollupAdminLogic.sol#L213)

```solidity
function setConfirmPeriodBlocks(uint64 newConfirmPeriod) external override {
```

- Found in src/rollup/RollupAdminLogic.sol [Line: 223](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/rollup/RollupAdminLogic.sol#L223)

```solidity
function setBaseStake(uint256 newBaseStake) external override {
```

- Found in src/rollup/RollupAdminLogic.sol [Line: 228](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/rollup/RollupAdminLogic.sol#L228)

```solidity
function forceRefundStaker(address[] calldata staker) external override whenPaused {
```

- Found in src/rollup/RollupAdminLogic.sol [Line: 237](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/rollup/RollupAdminLogic.sol#L237)

```solidity
function forceCreateAssertion(
bytes32 prevAssertionHash,
AssertionInputs calldata assertion,
bytes32 expectedAssertionHash
) external override whenPaused {
```

- Found in src/rollup/RollupAdminLogic.sol [Line: 258](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/rollup/RollupAdminLogic.sol#L258)

```solidity
function forceConfirmAssertion(
bytes32 assertionHash,
bytes32 parentAssertionHash,
AssertionState calldata confirmState,
bytes32 inboxAcc
) external override whenPaused {
```

- Found in src/rollup/RollupAdminLogic.sol [Line: 269](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/rollup/RollupAdminLogic.sol#L269)

```solidity
function setLoserStakeEscrow(address newLoserStakerEscrow) external override {
```

- Found in src/rollup/RollupAdminLogic.sol [Line: 281](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/rollup/RollupAdminLogic.sol#L281)

```solidity
function setWasmModuleRoot(bytes32 newWasmModuleRoot) external override {
```

- Found in src/rollup/RollupAdminLogic.sol [Line: 290](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/rollup/RollupAdminLogic.sol#L290)

```solidity
function setSequencerInbox(address _sequencerInbox) external override {
```

- Found in src/rollup/RollupAdminLogic.sol [Line: 299](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/rollup/RollupAdminLogic.sol#L299)

```solidity
function setInbox(IInboxBase newInbox) external {
```

- Found in src/rollup/RollupAdminLogic.sol [Line: 308](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/rollup/RollupAdminLogic.sol#L308)

```solidity
function setValidatorWhitelistDisabled(bool _validatorWhitelistDisabled) external {
```

- Found in src/rollup/RollupAdminLogic.sol [Line: 317](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/rollup/RollupAdminLogic.sol#L317)

```solidity
function setAnyTrustFastConfirmer(address _anyTrustFastConfirmer) external {
```

- Found in src/rollup/RollupAdminLogic.sol [Line: 326](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/rollup/RollupAdminLogic.sol#L326)

```solidity
function setChallengeManager(address _challengeManager) external {
```

- Found in src/rollup/RollupLib.sol [Line: 23](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/rollup/RollupLib.sol#L23)

```solidity
function assertionHash(
bytes32 parentAssertionHash,
AssertionState memory afterState,
bytes32 inboxAcc
) internal pure returns (bytes32) {
```

- Found in src/rollup/RollupLib.sol [Line: 37](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/rollup/RollupLib.sol#L37)

```solidity
function assertionHash(
bytes32 parentAssertionHash,
bytes32 afterStateHash,
bytes32 inboxAcc
) internal pure returns (bytes32) {
```

- Found in src/rollup/RollupLib.sol [Line: 54](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/rollup/RollupLib.sol#L54)

```solidity
function configHash(
bytes32 wasmModuleRoot,
uint256 requiredStake,
address challengeManager,
uint64 confirmPeriodBlocks,
uint64 nextInboxPosition
) internal pure returns (bytes32) {
```

- Found in src/rollup/RollupLib.sol [Line: 73](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/rollup/RollupLib.sol#L73)

```solidity
function validateConfigHash(
ConfigData calldata configData,
bytes32 _configHash
) internal pure {
```

- Found in src/rollup/BOLDUpgradeAction.sol [Line: 69](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/rollup/BOLDUpgradeAction.sol#L69)

```solidity
function getNode(uint64 nodeNum) external view returns (Node memory);
```

- Found in src/rollup/BOLDUpgradeAction.sol [Line: 70](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/rollup/BOLDUpgradeAction.sol#L70)

```solidity
function getStakerAddress(uint64 stakerNum) external view returns (address);
```

- Found in src/rollup/BOLDUpgradeAction.sol [Line: 72](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/rollup/BOLDUpgradeAction.sol#L72)

```solidity
function getStaker(address staker) external view returns (OldStaker memory);
```

- Found in src/rollup/BOLDUpgradeAction.sol [Line: 73](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/rollup/BOLDUpgradeAction.sol#L73)

```solidity
function isValidator(address validator) external view returns (bool);
```

- Found in src/rollup/BOLDUpgradeAction.sol [Line: 78](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/rollup/BOLDUpgradeAction.sol#L78)

```solidity
function forceRefundStaker(address[] memory stacker) external;
```

- Found in src/rollup/BOLDUpgradeAction.sol [Line: 84](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/rollup/BOLDUpgradeAction.sol#L84)

```solidity
function postUpgradeInit(BufferConfig memory bufferConfig_) external;
```

- Found in src/rollup/BOLDUpgradeAction.sol [Line: 101](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/rollup/BOLDUpgradeAction.sol#L101)

```solidity
function stateHash(ExecutionState calldata executionState, uint256 inboxMaxCount) public pure returns (bytes32) {
```

- Found in src/rollup/BOLDUpgradeAction.sol [Line: 106](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/rollup/BOLDUpgradeAction.sol#L106)

```solidity
function set(bytes32 h, ExecutionState calldata executionState, uint256 inboxMaxCount) public {
```

- Found in src/rollup/BOLDUpgradeAction.sol [Line: 112](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/rollup/BOLDUpgradeAction.sol#L112)

```solidity
function get(bytes32 h) public view returns (ExecutionState memory executionState, uint256 inboxMaxCount) {
```

- Found in src/rollup/BOLDUpgradeAction.sol [Line: 138](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/rollup/BOLDUpgradeAction.sol#L138)

```solidity
function getNode(uint64 nodeNum) external view returns (Node memory) {
```

- Found in src/rollup/BOLDUpgradeAction.sol [Line: 142](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/rollup/BOLDUpgradeAction.sol#L142)

```solidity
function getStakerAddress(uint64 stakerNum) external view returns (address) {
```

- Found in src/rollup/BOLDUpgradeAction.sol [Line: 150](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/rollup/BOLDUpgradeAction.sol#L150)

```solidity
function getStaker(address staker) external view returns (OldStaker memory) {
```

- Found in src/rollup/BOLDUpgradeAction.sol [Line: 154](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/rollup/BOLDUpgradeAction.sol#L154)

```solidity
function isValidator(address validator) external view returns (bool) {
```

- Found in src/rollup/BOLDUpgradeAction.sol [Line: 411](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/rollup/BOLDUpgradeAction.sol#L411)

```solidity
function upgradeSurroundingContracts(address newRollupAddress) private {
```

- Found in src/rollup/BOLDUpgradeAction.sol [Line: 464](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/rollup/BOLDUpgradeAction.sol#L464)

```solidity
function perform(address[] memory validators) external {
```

- Found in src/rollup/RollupCore.sol [Line: 126](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/rollup/RollupCore.sol#L126)

```solidity
function getAssertionStorage(bytes32 assertionHash) internal view returns (AssertionNode storage) {
```

- Found in src/rollup/RollupCore.sol [Line: 134](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/rollup/RollupCore.sol#L134)

```solidity
function getAssertion(bytes32 assertionHash) public view override returns (AssertionNode memory) {
```

- Found in src/rollup/RollupCore.sol [Line: 145](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/rollup/RollupCore.sol#L145)

```solidity
function getAssertionCreationBlockForLogLookup(bytes32 assertionHash) external view override returns (uint256) {
```

- Found in src/rollup/RollupCore.sol [Line: 162](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/rollup/RollupCore.sol#L162)

```solidity
function getStakerAddress(uint64 stakerNum) external view override returns (address) {
```

- Found in src/rollup/RollupCore.sol [Line: 171](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/rollup/RollupCore.sol#L171)

```solidity
function isStaked(address staker) public view override returns (bool) {
```

- Found in src/rollup/RollupCore.sol [Line: 180](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/rollup/RollupCore.sol#L180)

```solidity
function latestStakedAssertion(address staker) public view override returns (bytes32) {
```

- Found in src/rollup/RollupCore.sol [Line: 189](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/rollup/RollupCore.sol#L189)

```solidity
function amountStaked(address staker) public view override returns (uint256) {
```

- Found in src/rollup/RollupCore.sol [Line: 198](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/rollup/RollupCore.sol#L198)

```solidity
function getStaker(address staker) external view override returns (Staker memory) {
```

- Found in src/rollup/RollupCore.sol [Line: 207](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/rollup/RollupCore.sol#L207)

```solidity
function withdrawableFunds(address user) external view override returns (uint256) {
```

- Found in src/rollup/RollupCore.sol [Line: 225](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/rollup/RollupCore.sol#L225)

```solidity
function initializeCore(AssertionNode memory initialAssertion, bytes32 assertionHash) internal {
```

- Found in src/rollup/RollupCore.sol [Line: 236](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/rollup/RollupCore.sol#L236)

```solidity
function confirmAssertionInternal(
bytes32 assertionHash,
bytes32 parentAssertionHash,
AssertionState calldata confirmState,
bytes32 inboxAcc
) internal {
```

- Found in src/rollup/RollupCore.sol [Line: 274](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/rollup/RollupCore.sol#L274)

```solidity
function createNewStake(address stakerAddress, uint256 depositAmount, address withdrawalAddress) internal {
```

- Found in src/rollup/RollupCore.sol [Line: 286](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/rollup/RollupCore.sol#L286)

```solidity
function increaseStakeBy(address stakerAddress, uint256 amountAdded) internal {
```

- Found in src/rollup/RollupCore.sol [Line: 300](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/rollup/RollupCore.sol#L300)

```solidity
function reduceStakeTo(address stakerAddress, uint256 target) internal returns (uint256) {
```

- Found in src/rollup/RollupCore.sol [Line: 317](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/rollup/RollupCore.sol#L317)

```solidity
function withdrawStaker(address stakerAddress) internal {
```

- Found in src/rollup/RollupCore.sol [Line: 331](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/rollup/RollupCore.sol#L331)

```solidity
function withdrawFunds(address account) internal returns (uint256) {
```

- Found in src/rollup/RollupCore.sol [Line: 343](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/rollup/RollupCore.sol#L343)

```solidity
function increaseWithdrawableFunds(address account, uint256 amount) internal {
```

- Found in src/rollup/RollupCore.sol [Line: 355](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/rollup/RollupCore.sol#L355)

```solidity
function deleteStaker(address stakerAddress) private {
```

- Found in src/rollup/RollupCore.sol [Line: 365](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/rollup/RollupCore.sol#L365)

```solidity
function createNewAssertion(
AssertionInputs calldata assertion,
bytes32 prevAssertionHash,
bytes32 expectedAssertionHash
) internal returns (bytes32 newAssertionHash, bool overflowAssertion) {
```

- Found in src/rollup/RollupCore.sol [Line: 532](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/rollup/RollupCore.sol#L532)

```solidity
function getFirstChildCreationBlock(bytes32 assertionHash) external view returns (uint64) {
```

- Found in src/rollup/RollupCore.sol [Line: 536](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/rollup/RollupCore.sol#L536)

```solidity
function getSecondChildCreationBlock(bytes32 assertionHash) external view returns (uint64) {
```

- Found in src/rollup/RollupCore.sol [Line: 540](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/rollup/RollupCore.sol#L540)

```solidity
function validateAssertionHash(
bytes32 assertionHash,
AssertionState calldata state,
bytes32 prevAssertionHash,
bytes32 inboxAcc
) external pure {
```

- Found in src/rollup/RollupCore.sol [Line: 549](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/rollup/RollupCore.sol#L549)

```solidity
function validateConfig(bytes32 assertionHash, ConfigData calldata configData) external view {
```

- Found in src/rollup/RollupCore.sol [Line: 553](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/rollup/RollupCore.sol#L553)

```solidity
function isFirstChild(bytes32 assertionHash) external view returns (bool) {
```

- Found in src/rollup/RollupCore.sol [Line: 557](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/rollup/RollupCore.sol#L557)

```solidity
function isPending(bytes32 assertionHash) external view returns (bool) {
```

- Found in src/rollup/RollupCore.sol [Line: 565](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/rollup/RollupCore.sol#L565)

```solidity
function requireInactiveStaker(address stakerAddress) internal view {
```

- Found in src/rollup/RollupUserLogic.sol [Line: 27](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/rollup/RollupUserLogic.sol#L27)

```solidity
function initialize(address _stakeToken) external view override onlyProxy {
```

- Found in src/rollup/RollupUserLogic.sol [Line: 82](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/rollup/RollupUserLogic.sol#L82)

```solidity
function confirmAssertion(
bytes32 assertionHash,
bytes32 prevAssertionHash,
AssertionState calldata confirmState,
bytes32 winningEdgeId,
ConfigData calldata prevConfig,
bytes32 inboxAcc
) external onlyValidator whenNotPaused {
```

- Found in src/rollup/RollupUserLogic.sol [Line: 137](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/rollup/RollupUserLogic.sol#L137)

```solidity
function _newStake(uint256 depositAmount, address withdrawalAddress) internal onlyValidator whenNotPaused {
```

- Found in src/rollup/RollupUserLogic.sol [Line: 150](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/rollup/RollupUserLogic.sol#L150)

```solidity
function computeAssertionHash(bytes32 prevAssertionHash, AssertionState calldata state, bytes32 inboxAcc)
external
pure
returns (bytes32)
{
```

- Found in src/rollup/RollupUserLogic.sol [Line: 163](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/rollup/RollupUserLogic.sol#L163)

```solidity
function stakeOnNewAssertion(AssertionInputs calldata assertion, bytes32 expectedAssertionHash)
public
onlyValidator
whenNotPaused
{
```

- Found in src/rollup/RollupUserLogic.sol [Line: 232](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/rollup/RollupUserLogic.sol#L232)

```solidity
function _addToDeposit(address stakerAddress, uint256 depositAmount) internal onlyValidator whenNotPaused {
```

- Found in src/rollup/RollupUserLogic.sol [Line: 241](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/rollup/RollupUserLogic.sol#L241)

```solidity
function reduceDeposit(uint256 target) external onlyValidator whenNotPaused {
```

- Found in src/rollup/RollupUserLogic.sol [Line: 252](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/rollup/RollupUserLogic.sol#L252)

```solidity
function fastConfirmAssertion(
bytes32 assertionHash,
bytes32 parentAssertionHash,
AssertionState calldata confirmState,
bytes32 inboxAcc
) public whenNotPaused {
```

- Found in src/rollup/RollupUserLogic.sol [Line: 273](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/rollup/RollupUserLogic.sol#L273)

```solidity
function fastConfirmNewAssertion(AssertionInputs calldata assertion, bytes32 expectedAssertionHash)
external
whenNotPaused
{
```

- Found in src/rollup/RollupUserLogic.sol [Line: 316](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/rollup/RollupUserLogic.sol#L316)

```solidity
function newStakeOnNewAssertion(
uint256 tokenAmount,
AssertionInputs calldata assertion,
bytes32 expectedAssertionHash
) external {
```

- Found in src/rollup/RollupUserLogic.sol [Line: 331](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/rollup/RollupUserLogic.sol#L331)

```solidity
function newStakeOnNewAssertion(
uint256 tokenAmount,
AssertionInputs calldata assertion,
bytes32 expectedAssertionHash,
address withdrawalAddress
) public {
```

- Found in src/rollup/RollupUserLogic.sol [Line: 349](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/rollup/RollupUserLogic.sol#L349)

```solidity
function addToDeposit(address stakerAddress, uint256 tokenAmount) external onlyValidator whenNotPaused {
```

- Found in src/rollup/RollupUserLogic.sol [Line: 366](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/rollup/RollupUserLogic.sol#L366)

```solidity
function receiveTokens(uint256 tokenAmount) private {
```

- Found in src/rollup/BridgeCreator.sol [Line: 53](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/rollup/BridgeCreator.sol#L53)

```solidity
function updateTemplates(BridgeTemplates calldata _newTemplates) external onlyOwner {
```

- Found in src/rollup/BridgeCreator.sol [Line: 58](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/rollup/BridgeCreator.sol#L58)

```solidity
function updateERC20Templates(BridgeTemplates calldata _newTemplates) external onlyOwner {
```

- Found in src/rollup/BridgeCreator.sol [Line: 63](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/rollup/BridgeCreator.sol#L63)

```solidity
function _createBridge(
address adminProxy,
BridgeTemplates memory templates,
bool isDelayBufferable
) internal returns (BridgeContracts memory) {
```

- Found in src/rollup/BridgeCreator.sol [Line: 99](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/rollup/BridgeCreator.sol#L99)

```solidity
function createBridge(
address adminProxy,
address rollup,
address nativeToken,
ISequencerInbox.MaxTimeVariation calldata maxTimeVariation,
BufferConfig calldata bufferConfig
) external returns (BridgeContracts memory) {
```

- Found in src/rollup/RollupCreator.sol [Line: 63](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/rollup/RollupCreator.sol#L63)

```solidity
function setTemplates(
BridgeCreator _bridgeCreator,
IOneStepProofEntry _osp,
IEdgeChallengeManager _challengeManagerLogic,
IRollupAdmin _rollupAdminLogic,
IRollupUser _rollupUserLogic,
IUpgradeExecutor _upgradeExecutorLogic,
address _validatorWalletCreator,
DeployHelper _l2FactoriesDeployer
) external onlyOwner {
```

- Found in src/rollup/RollupCreator.sol [Line: 85](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/rollup/RollupCreator.sol#L85)

```solidity
function createChallengeManager(address rollupAddr, address proxyAdminAddr, Config memory config)
internal
returns (IEdgeChallengeManager)
{
```

- Found in src/rollup/RollupCreator.sol [Line: 137](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/rollup/RollupCreator.sol#L137)

```solidity
function createRollup(RollupDeploymentParams memory deployParams)
public
payable
returns (address)
{
```

- Found in src/rollup/RollupCreator.sol [Line: 267](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/rollup/RollupCreator.sol#L267)

```solidity
function _deployUpgradeExecutor(address rollupOwner, ProxyAdmin proxyAdmin)
internal
returns (address)
{
```

- Found in src/rollup/RollupCreator.sol [Line: 287](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/rollup/RollupCreator.sol#L287)

```solidity
function _deployFactories(
address _inbox,
address _nativeToken,
uint256 _maxFeePerGas
) internal {
```

- Found in src/challengeV2/EdgeChallengeManager.sol [Line: 54](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/challengeV2/EdgeChallengeManager.sol#L54)

```solidity
function createLayerZeroEdge(CreateEdgeArgs calldata args) external returns (bytes32);
```

- Found in src/challengeV2/EdgeChallengeManager.sol [Line: 68](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/challengeV2/EdgeChallengeManager.sol#L68)

```solidity
function bisectEdge(bytes32 edgeId, bytes32 bisectionHistoryRoot, bytes calldata prefixProof)
external
returns (bytes32, bytes32);
```

- Found in src/challengeV2/EdgeChallengeManager.sol [Line: 80](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/challengeV2/EdgeChallengeManager.sol#L80)

```solidity
function confirmEdgeByTime(bytes32 edgeId, AssertionStateData calldata claimStateData) external;
```

- Found in src/challengeV2/EdgeChallengeManager.sol [Line: 109](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/challengeV2/EdgeChallengeManager.sol#L109)

```solidity
function confirmEdgeByOneStepProof(
bytes32 edgeId,
OneStepData calldata oneStepData,
ConfigData calldata prevConfig,
bytes32[] calldata beforeHistoryInclusionProof,
bytes32[] calldata afterHistoryInclusionProof
) external;
```

- Found in src/challengeV2/EdgeChallengeManager.sol [Line: 123](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/challengeV2/EdgeChallengeManager.sol#L123)

```solidity
function getLayerZeroEndHeight(EdgeType eType) external view returns (uint256);
```

- Found in src/challengeV2/EdgeChallengeManager.sol [Line: 171](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/challengeV2/EdgeChallengeManager.sol#L171)

```solidity
function confirmedRival(bytes32 mutualId) external view returns (bytes32);
```

- Found in src/challengeV2/EdgeChallengeManager.sol [Line: 191](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/challengeV2/EdgeChallengeManager.sol#L191)

```solidity
function firstRival(bytes32 mutualId) external view returns (bytes32);
```

- Found in src/challengeV2/EdgeChallengeManager.sol [Line: 195](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/challengeV2/EdgeChallengeManager.sol#L195)

```solidity
function hasMadeLayerZeroRival(address account, bytes32 mutualId) external view returns (bool);
```

- Found in src/challengeV2/EdgeChallengeManager.sol [Line: 371](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/challengeV2/EdgeChallengeManager.sol#L371)

```solidity
function createLayerZeroEdge(CreateEdgeArgs calldata args) external returns (bytes32) {
```

- Found in src/challengeV2/EdgeChallengeManager.sol [Line: 451](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/challengeV2/EdgeChallengeManager.sol#L451)

```solidity
function bisectEdge(bytes32 edgeId, bytes32 bisectionHistoryRoot, bytes calldata prefixProof)
external
returns (bytes32, bytes32)
{
```

- Found in src/challengeV2/EdgeChallengeManager.sol [Line: 511](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/challengeV2/EdgeChallengeManager.sol#L511)

```solidity
function confirmEdgeByTime(bytes32 edgeId, AssertionStateData calldata claimStateData) public {
```

- Found in src/challengeV2/EdgeChallengeManager.sol [Line: 539](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/challengeV2/EdgeChallengeManager.sol#L539)

```solidity
function confirmEdgeByOneStepProof(
bytes32 edgeId,
OneStepData calldata oneStepData,
ConfigData calldata prevConfig,
bytes32[] calldata beforeHistoryInclusionProof,
bytes32[] calldata afterHistoryInclusionProof
) public {
```

- Found in src/challengeV2/EdgeChallengeManager.sol [Line: 591](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/challengeV2/EdgeChallengeManager.sol#L591)

```solidity
function getLayerZeroEndHeight(EdgeType eType) public view returns (uint256) {
```

- Found in src/challengeV2/EdgeChallengeManager.sol [Line: 672](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/challengeV2/EdgeChallengeManager.sol#L672)

```solidity
function hasMadeLayerZeroRival(address account, bytes32 mutualId) external view returns (bool) {
```

- Found in src/challengeV2/IAssertionChain.sol [Line: 15](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/challengeV2/IAssertionChain.sol#L15)

```solidity
function validateAssertionHash(
bytes32 assertionHash,
AssertionState calldata state,
bytes32 prevAssertionHash,
bytes32 inboxAcc
) external view;
```

- Found in src/challengeV2/IAssertionChain.sol [Line: 21](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/challengeV2/IAssertionChain.sol#L21)

```solidity
function validateConfig(bytes32 assertionHash, ConfigData calldata configData) external view;
```

- Found in src/challengeV2/IAssertionChain.sol [Line: 22](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/challengeV2/IAssertionChain.sol#L22)

```solidity
function getFirstChildCreationBlock(bytes32 assertionHash) external view returns (uint64);
```

- Found in src/challengeV2/IAssertionChain.sol [Line: 23](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/challengeV2/IAssertionChain.sol#L23)

```solidity
function getSecondChildCreationBlock(bytes32 assertionHash) external view returns (uint64);
```

- Found in src/challengeV2/IAssertionChain.sol [Line: 24](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/challengeV2/IAssertionChain.sol#L24)

```solidity
function isFirstChild(bytes32 assertionHash) external view returns (bool);
```

- Found in src/challengeV2/IAssertionChain.sol [Line: 25](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/challengeV2/IAssertionChain.sol#L25)

```solidity
function isPending(bytes32 assertionHash) external view returns (bool);
```

- Found in src/challengeV2/libraries/EdgeChallengeManagerLib.sol [Line: 141](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/challengeV2/libraries/EdgeChallengeManagerLib.sol#L141)

```solidity
function get(EdgeStore storage store, bytes32 edgeId) internal view returns (ChallengeEdge storage) {
```

- Found in src/challengeV2/libraries/EdgeChallengeManagerLib.sol [Line: 152](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/challengeV2/libraries/EdgeChallengeManagerLib.sol#L152)

```solidity
function getNoCheck(EdgeStore storage store, bytes32 edgeId) internal view returns (ChallengeEdge storage) {
```

- Found in src/challengeV2/libraries/EdgeChallengeManagerLib.sol [Line: 160](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/challengeV2/libraries/EdgeChallengeManagerLib.sol#L160)

```solidity
function add(EdgeStore storage store, ChallengeEdge memory edge) internal returns (EdgeAddedData memory) {
```

- Found in src/challengeV2/libraries/EdgeChallengeManagerLib.sol [Line: 213](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/challengeV2/libraries/EdgeChallengeManagerLib.sol#L213)

```solidity
function layerZeroTypeSpecificChecks(
EdgeStore storage store,
CreateEdgeArgs calldata args,
AssertionReferenceData memory ard,
IOneStepProofEntry oneStepProofEntry,
uint8 numBigStepLevel
) private view returns (ProofData memory, bytes32) {
```

- Found in src/challengeV2/libraries/EdgeChallengeManagerLib.sol [Line: 327](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/challengeV2/libraries/EdgeChallengeManagerLib.sol#L327)

```solidity
function isPowerOfTwo(uint256 x) internal pure returns (bool) {
```

- Found in src/challengeV2/libraries/EdgeChallengeManagerLib.sol [Line: 344](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/challengeV2/libraries/EdgeChallengeManagerLib.sol#L344)

```solidity
function layerZeroCommonChecks(ProofData memory proofData, CreateEdgeArgs calldata args, uint256 expectedEndHeight)
private
pure
returns (bytes32)
{
```

- Found in src/challengeV2/libraries/EdgeChallengeManagerLib.sol [Line: 391](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/challengeV2/libraries/EdgeChallengeManagerLib.sol#L391)

```solidity
function toLayerZeroEdge(bytes32 originId, bytes32 startHistoryRoot, CreateEdgeArgs calldata args)
private
view
returns (ChallengeEdge memory)
{
```

- Found in src/challengeV2/libraries/EdgeChallengeManagerLib.sol [Line: 411](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/challengeV2/libraries/EdgeChallengeManagerLib.sol#L411)

```solidity
function createLayerZeroEdge(
EdgeStore storage store,
CreateEdgeArgs calldata args,
AssertionReferenceData memory ard,
IOneStepProofEntry oneStepProofEntry,
uint256 expectedEndHeight,
uint8 numBigStepLevel,
bool whitelistEnabled
) internal returns (EdgeAddedData memory) {
```

- Found in src/challengeV2/libraries/EdgeChallengeManagerLib.sol [Line: 443](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/challengeV2/libraries/EdgeChallengeManagerLib.sol#L443)

```solidity
function getPrevAssertionHash(EdgeStore storage store, bytes32 edgeId) internal view returns (bytes32) {
```

- Found in src/challengeV2/libraries/EdgeChallengeManagerLib.sol [Line: 463](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/challengeV2/libraries/EdgeChallengeManagerLib.sol#L463)

```solidity
function hasRival(EdgeStore storage store, bytes32 edgeId) internal view returns (bool) {
```

- Found in src/challengeV2/libraries/EdgeChallengeManagerLib.sol [Line: 483](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/challengeV2/libraries/EdgeChallengeManagerLib.sol#L483)

```solidity
function hasLengthOneRival(EdgeStore storage store, bytes32 edgeId) internal view returns (bool) {
```

- Found in src/challengeV2/libraries/EdgeChallengeManagerLib.sol [Line: 488](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/challengeV2/libraries/EdgeChallengeManagerLib.sol#L488)

```solidity
function timeUnrivaledTotal(EdgeStore storage store, bytes32 edgeId) internal view returns (uint256) {
```

- Found in src/challengeV2/libraries/EdgeChallengeManagerLib.sol [Line: 502](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/challengeV2/libraries/EdgeChallengeManagerLib.sol#L502)

```solidity
function updateTimerCache(EdgeStore storage store, bytes32 edgeId, uint256 newValue)
internal
returns (bool, uint256)
{
```

- Found in src/challengeV2/libraries/EdgeChallengeManagerLib.sol [Line: 516](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/challengeV2/libraries/EdgeChallengeManagerLib.sol#L516)

```solidity
function updateTimerCacheByChildren(EdgeStore storage store, bytes32 edgeId) internal returns (bool, uint256) {
```

- Found in src/challengeV2/libraries/EdgeChallengeManagerLib.sol [Line: 520](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/challengeV2/libraries/EdgeChallengeManagerLib.sol#L520)

```solidity
function updateTimerCacheByClaim(
EdgeStore storage store,
bytes32 edgeId,
bytes32 claimingEdgeId,
uint8 numBigStepLevel
) internal returns (bool, uint256) {
```

- Found in src/challengeV2/libraries/EdgeChallengeManagerLib.sol [Line: 537](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/challengeV2/libraries/EdgeChallengeManagerLib.sol#L537)

```solidity
function timeUnrivaled(EdgeStore storage store, bytes32 edgeId) internal view returns (uint256) {
```

- Found in src/challengeV2/libraries/EdgeChallengeManagerLib.sol [Line: 576](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/challengeV2/libraries/EdgeChallengeManagerLib.sol#L576)

```solidity
function mandatoryBisectionHeight(uint256 start, uint256 end) internal pure returns (uint256) {
```

- Found in src/challengeV2/libraries/EdgeChallengeManagerLib.sol [Line: 604](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/challengeV2/libraries/EdgeChallengeManagerLib.sol#L604)

```solidity
function bisectEdge(EdgeStore storage store, bytes32 edgeId, bytes32 bisectionHistoryRoot, bytes memory prefixProof)
internal
returns (bytes32, EdgeAddedData memory, EdgeAddedData memory)
{
```

- Found in src/challengeV2/libraries/EdgeChallengeManagerLib.sol [Line: 662](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/challengeV2/libraries/EdgeChallengeManagerLib.sol#L662)

```solidity
function setConfirmedRival(EdgeStore storage store, bytes32 edgeId) internal {
```

- Found in src/challengeV2/libraries/EdgeChallengeManagerLib.sol [Line: 689](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/challengeV2/libraries/EdgeChallengeManagerLib.sol#L689)

```solidity
function checkClaimIdLink(EdgeStore storage store, bytes32 edgeId, bytes32 claimingEdgeId, uint8 numBigStepLevel)
private
view
{
```

- Found in src/challengeV2/libraries/EdgeChallengeManagerLib.sol [Line: 723](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/challengeV2/libraries/EdgeChallengeManagerLib.sol#L723)

```solidity
function confirmEdgeByTime(
EdgeStore storage store,
bytes32 edgeId,
uint64 claimedAssertionUnrivaledBlocks,
uint64 confirmationThresholdBlock
) internal returns (uint256) {
```

- Found in src/challengeV2/libraries/EdgeChallengeManagerLib.sol [Line: 766](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/challengeV2/libraries/EdgeChallengeManagerLib.sol#L766)

```solidity
function confirmEdgeByOneStepProof(
EdgeStore storage store,
bytes32 edgeId,
IOneStepProofEntry oneStepProofEntry,
OneStepData calldata oneStepData,
ExecutionContext memory execCtx,
bytes32[] calldata beforeHistoryInclusionProof,
bytes32[] calldata afterHistoryInclusionProof,
uint8 numBigStepLevel,
uint256 bigStepHeight,
uint256 smallStepHeight
) internal {
```

- Found in src/challengeV2/libraries/ChallengeEdgeLib.sol [Line: 69](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/challengeV2/libraries/ChallengeEdgeLib.sol#L69)

```solidity
function newEdgeChecks(
bytes32 originId,
bytes32 startHistoryRoot,
uint256 startHeight,
bytes32 endHistoryRoot,
uint256 endHeight
) internal pure {
```

- Found in src/challengeV2/libraries/ChallengeEdgeLib.sol [Line: 93](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/challengeV2/libraries/ChallengeEdgeLib.sol#L93)

```solidity
function newLayerZeroEdge(
bytes32 originId,
bytes32 startHistoryRoot,
uint256 startHeight,
bytes32 endHistoryRoot,
uint256 endHeight,
bytes32 claimId,
address staker,
uint8 level
) internal view returns (ChallengeEdge memory) {
```

- Found in src/challengeV2/libraries/ChallengeEdgeLib.sol [Line: 133](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/challengeV2/libraries/ChallengeEdgeLib.sol#L133)

```solidity
function newChildEdge(
bytes32 originId,
bytes32 startHistoryRoot,
uint256 startHeight,
bytes32 endHistoryRoot,
uint256 endHeight,
uint8 level
) internal view returns (ChallengeEdge memory) {
```

- Found in src/challengeV2/libraries/ChallengeEdgeLib.sol [Line: 166](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/challengeV2/libraries/ChallengeEdgeLib.sol#L166)

```solidity
function mutualIdComponent(
uint8 level,
bytes32 originId,
uint256 startHeight,
bytes32 startHistoryRoot,
uint256 endHeight
) internal pure returns (bytes32) {
```

- Found in src/challengeV2/libraries/ChallengeEdgeLib.sol [Line: 180](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/challengeV2/libraries/ChallengeEdgeLib.sol#L180)

```solidity
function mutualId(ChallengeEdge storage ce) internal view returns (bytes32) {
```

- Found in src/challengeV2/libraries/ChallengeEdgeLib.sol [Line: 184](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/challengeV2/libraries/ChallengeEdgeLib.sol#L184)

```solidity
function mutualIdMem(ChallengeEdge memory ce) internal pure returns (bytes32) {
```

- Found in src/challengeV2/libraries/ChallengeEdgeLib.sol [Line: 189](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/challengeV2/libraries/ChallengeEdgeLib.sol#L189)

```solidity
function idComponent(
uint8 level,
bytes32 originId,
uint256 startHeight,
bytes32 startHistoryRoot,
uint256 endHeight,
bytes32 endHistoryRoot
) internal pure returns (bytes32) {
```

- Found in src/challengeV2/libraries/ChallengeEdgeLib.sol [Line: 208](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/challengeV2/libraries/ChallengeEdgeLib.sol#L208)

```solidity
function idMem(ChallengeEdge memory edge) internal pure returns (bytes32) {
```

- Found in src/challengeV2/libraries/ChallengeEdgeLib.sol [Line: 215](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/challengeV2/libraries/ChallengeEdgeLib.sol#L215)

```solidity
function id(ChallengeEdge storage edge) internal view returns (bytes32) {
```

- Found in src/challengeV2/libraries/ChallengeEdgeLib.sol [Line: 222](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/challengeV2/libraries/ChallengeEdgeLib.sol#L222)

```solidity
function exists(ChallengeEdge storage edge) internal view returns (bool) {
```

- Found in src/challengeV2/libraries/ChallengeEdgeLib.sol [Line: 228](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/challengeV2/libraries/ChallengeEdgeLib.sol#L228)

```solidity
function length(ChallengeEdge storage edge) internal view returns (uint256) {
```

- Found in src/challengeV2/libraries/ChallengeEdgeLib.sol [Line: 239](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/challengeV2/libraries/ChallengeEdgeLib.sol#L239)

```solidity
function setChildren(ChallengeEdge storage edge, bytes32 lowerChildId, bytes32 upperChildId) internal {
```

- Found in src/challengeV2/libraries/ChallengeEdgeLib.sol [Line: 249](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/challengeV2/libraries/ChallengeEdgeLib.sol#L249)

```solidity
function setConfirmed(ChallengeEdge storage edge) internal {
```

- Found in src/challengeV2/libraries/ChallengeEdgeLib.sol [Line: 258](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/challengeV2/libraries/ChallengeEdgeLib.sol#L258)

```solidity
function isLayerZero(ChallengeEdge storage edge) internal view returns (bool) {
```

- Found in src/challengeV2/libraries/ChallengeEdgeLib.sol [Line: 264](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/challengeV2/libraries/ChallengeEdgeLib.sol#L264)

```solidity
function setRefunded(ChallengeEdge storage edge) internal {
```

- Found in src/challengeV2/libraries/ChallengeEdgeLib.sol [Line: 279](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/challengeV2/libraries/ChallengeEdgeLib.sol#L279)

```solidity
function levelToType(uint8 level, uint8 numBigStepLevels) internal pure returns (EdgeType eType) {
```

- Found in src/challengeV2/libraries/ArrayUtilsLib.sol [Line: 45](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/challengeV2/libraries/ArrayUtilsLib.sol#L45)

```solidity
function concat(bytes32[] memory arr1, bytes32[] memory arr2) internal pure returns (bytes32[] memory) {
```

</details>

### [N-13] No events for important state changes

Events are vital for Ethereum smart contracts to notify external systems about crucial state changes. However, there are places in the codebase that fail to emit an event upon important state changes. This omission prevents external systems from efficiently monitoring, reducing transparency. Consider emitting events for every important state change!

<details>
<summary><i>Affected Code Snippets</i></summary>

- Found in src/bridge/SequencerInbox.sol [Line: 889](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/bridge/SequencerInbox.sol#L889)

```solidity
   function setMaxTimeVariation(ISequencerInbox.MaxTimeVariation memory maxTimeVariation_)
```

- Found in src/bridge/SequencerInbox.sol [Line: 898](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/bridge/SequencerInbox.sol#L898)

```solidity
   function setIsBatchPoster(address addr, bool isBatchPoster_)
```

- Found in src/bridge/SequencerInbox.sol [Line: 907](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/bridge/SequencerInbox.sol#L907)

```solidity
   function setValidKeyset(bytes calldata keysetBytes) external onlyRollupOwner {
```

- Found in src/bridge/SequencerInbox.sol [Line: 937](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/bridge/SequencerInbox.sol#L937)

```solidity
   function setIsSequencer(address addr, bool isSequencer_)
```

- Found in src/bridge/SequencerInbox.sol [Line: 942](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/bridge/SequencerInbox.sol#L942)

```solidity
  function setBatchPosterManager(address newBatchPosterManager) external onlyRollupOwner {
```

- Found in src/bridge/SequencerInbox.sol [Line: 947](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/bridge/SequencerInbox.sol#L947)

```solidity
  function setBufferConfig(BufferConfig memory bufferConfig_) external onlyRollupOwner {
```

- Found in src/rollup/RollupAdminLogic.sol [Line: 26](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/rollup/RollupAdminLogic.sol#L26)

```solidity
   connectedContracts.bridge.setDelayedInbox(address(connectedContracts.inbox), true);
```

- Found in src/rollup/RollupAdminLogic.sol [Line: 27](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/rollup/RollupAdminLogic.sol#L27)

```solidity
   connectedContracts.bridge.setSequencerInbox(address(connectedContracts.sequencerInbox));
```

- Found in src/rollup/RollupAdminLogic.sol [Line: 31](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/rollup/RollupAdminLogic.sol#L31)

```solidity
   connectedContracts.bridge.setOutbox(address(connectedContracts.outbox), true);
```

- Found in src/rollup/RollupAdminLogic.sol [Line: 36](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/rollup/RollupAdminLogic.sol#L36)

```solidity
   connectedContracts.bridge.setDelayedInbox(address(connectedContracts.rollupEventInbox), true);
```

- Found in src/rollup/RollupAdminLogic.sol [Line: 117](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/rollup/RollupAdminLogic.sol#L117)

```solidity
   function setOutbox(IOutbox _outbox) external override {
```

- Found in src/rollup/RollupAdminLogic.sol [Line: 119](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/rollup/RollupAdminLogic.sol#L119)

```solidity
   bridge.setOutbox(address(_outbox), true);
```

- Found in src/rollup/RollupAdminLogic.sol [Line: 129](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/rollup/RollupAdminLogic.sol#L129)

```solidity
   bridge.setOutbox(_outbox, false);
```

- Found in src/rollup/RollupAdminLogic.sol [Line: 138](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/rollup/RollupAdminLogic.sol#L138)

```solidity
   function setDelayedInbox(address _inbox, bool _enabled) external override {
```

- Found in src/rollup/RollupAdminLogic.sol [Line: 139](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/rollup/RollupAdminLogic.sol#L139)

```solidity
   bridge.setDelayedInbox(address(_inbox), _enabled);
```

- Found in src/rollup/RollupAdminLogic.sol [Line: 180](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/rollup/RollupAdminLogic.sol#L180)

```solidity
   function setValidator(address[] calldata _validator, bool[] calldata _val) external override {
```

- Found in src/rollup/RollupAdminLogic.sol [Line: 195](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/rollup/RollupAdminLogic.sol#L195)

```solidity
   function setOwner(address newOwner) external override {
```

- Found in src/rollup/RollupAdminLogic.sol [Line: 204](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/rollup/RollupAdminLogic.sol#L204)

```solidity
   function setMinimumAssertionPeriod(uint256 newPeriod) external override {
```

- Found in src/rollup/RollupAdminLogic.sol [Line: 213](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/rollup/RollupAdminLogic.sol#L213)

```solidity
   function setConfirmPeriodBlocks(uint64 newConfirmPeriod) external override {
```

- Found in src/rollup/RollupAdminLogic.sol [Line: 223](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/rollup/RollupAdminLogic.sol#L223)

```solidity
   function setBaseStake(uint256 newBaseStake) external override {
```

- Found in src/rollup/RollupAdminLogic.sol [Line: 269](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/rollup/RollupAdminLogic.sol#L269)

```solidity
   function setLoserStakeEscrow(address newLoserStakerEscrow) external override {
```

- Found in src/rollup/RollupAdminLogic.sol [Line: 281](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/rollup/RollupAdminLogic.sol#L281)

```solidity
   function setWasmModuleRoot(bytes32 newWasmModuleRoot) external override {
```

- Found in src/rollup/RollupAdminLogic.sol [Line: 290](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/rollup/RollupAdminLogic.sol#L290)

```solidity
   function setSequencerInbox(address _sequencerInbox) external override {
```

- Found in src/rollup/RollupAdminLogic.sol [Line: 291](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/rollup/RollupAdminLogic.sol#L291)

```solidity
   bridge.setSequencerInbox(_sequencerInbox);
```

- Found in src/rollup/RollupAdminLogic.sol [Line: 299](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/rollup/RollupAdminLogic.sol#L299)

```solidity
   function setInbox(IInboxBase newInbox) external {
```

- Found in src/rollup/RollupAdminLogic.sol [Line: 308](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/rollup/RollupAdminLogic.sol#L308)

```solidity
   function setValidatorWhitelistDisabled(bool _validatorWhitelistDisabled) external {
```

- Found in src/rollup/RollupAdminLogic.sol [Line: 317](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/rollup/RollupAdminLogic.sol#L317)

```solidity
   function setAnyTrustFastConfirmer(address _anyTrustFastConfirmer) external {
```

- Found in src/rollup/RollupAdminLogic.sol [Line: 326](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/rollup/RollupAdminLogic.sol#L326)

```solidity
   function setChallengeManager(address _challengeManager) external {
```

- Found in src/rollup/BOLDUpgradeAction.sol [Line: 106](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/rollup/BOLDUpgradeAction.sol#L106)

```solidity
   function set(bytes32 h, ExecutionState calldata executionState, uint256 inboxMaxCount) public {
```

- Found in src/rollup/BOLDUpgradeAction.sol [Line: 532](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/rollup/BOLDUpgradeAction.sol#L532)

```solidity
   IRollupAdmin(address(rollup)).setValidator(validators, _vals);
```

- Found in src/rollup/BOLDUpgradeAction.sol [Line: 535](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/rollup/BOLDUpgradeAction.sol#L535)

```solidity
   IRollupAdmin(address(rollup)).setValidatorWhitelistDisabled(DISABLE_VALIDATOR_WHITELIST);
```

- Found in src/rollup/BOLDUpgradeAction.sol [Line: 538](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/rollup/BOLDUpgradeAction.sol#L538)

```solidity
   IRollupAdmin(address(rollup)).setOwner(actualOwner);
```

- Found in src/rollup/RollupCreator.sol [Line: 63](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/rollup/RollupCreator.sol#L63)

```solidity
   function setTemplates(
```

- Found in src/rollup/RollupCreator.sol [Line: 226](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/rollup/RollupCreator.sol#L226)

```solidity
   bridgeContracts.sequencerInbox.setIsBatchPoster(deployParams.batchPosters[i], true);
```

- Found in src/rollup/RollupCreator.sol [Line: 229](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/rollup/RollupCreator.sol#L229)

```solidity
   bridgeContracts.sequencerInbox.setBatchPosterManager(deployParams.batchPosterManager);
```

- Found in src/rollup/RollupCreator.sol [Line: 238](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/rollup/RollupCreator.sol#L238)

```solidity
   IRollupAdmin(address(rollup)).setValidator(deployParams.validators, _vals);
```

- Found in src/rollup/RollupCreator.sol [Line: 241](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/rollup/RollupCreator.sol#L241)

```solidity
   IRollupAdmin(address(rollup)).setOwner(address(upgradeExecutor));
```

- Found in src/challengeV2/EdgeChallengeManager.sol [Line: 575](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/challengeV2/EdgeChallengeManager.sol#L575)

```solidity
   edge.setRefunded();
```

- Found in src/challengeV2/libraries/EdgeChallengeManagerLib.sol [Line: 654](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/challengeV2/libraries/EdgeChallengeManagerLib.sol#L654)

```solidity
   store.edges[edgeId].setChildren(lowerChildId, upperChildAdded.edgeId);
```

- Found in src/challengeV2/libraries/EdgeChallengeManagerLib.sol [Line: 662](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/challengeV2/libraries/EdgeChallengeManagerLib.sol#L662)

```solidity
   function setConfirmedRival(EdgeStore storage store, bytes32 edgeId) internal {
```

- Found in src/challengeV2/libraries/EdgeChallengeManagerLib.sol [Line: 746](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/challengeV2/libraries/EdgeChallengeManagerLib.sol#L746)

```solidity
   store.edges[edgeId].setConfirmed();
```

- Found in src/challengeV2/libraries/EdgeChallengeManagerLib.sol [Line: 749](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/challengeV2/libraries/EdgeChallengeManagerLib.sol#L749)

```solidity
   setConfirmedRival(store, edgeId);
```

- Found in src/challengeV2/libraries/EdgeChallengeManagerLib.sol [Line: 826](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/challengeV2/libraries/EdgeChallengeManagerLib.sol#L826)

```solidity
   setConfirmedRival(store, edgeId);
```

- Found in src/challengeV2/libraries/EdgeChallengeManagerLib.sol [Line: 829](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/challengeV2/libraries/EdgeChallengeManagerLib.sol#L829)

```solidity
   store.edges[edgeId].setConfirmed();
```

- Found in src/challengeV2/libraries/ChallengeEdgeLib.sol [Line: 239](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/challengeV2/libraries/ChallengeEdgeLib.sol#L239)

```solidity
   function setChildren(ChallengeEdge storage edge, bytes32 lowerChildId, bytes32 upperChildId) internal {
```

- Found in src/challengeV2/libraries/ChallengeEdgeLib.sol [Line: 249](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/challengeV2/libraries/ChallengeEdgeLib.sol#L249)

```solidity
   function setConfirmed(ChallengeEdge storage edge) internal {
```

- Found in src/challengeV2/libraries/ChallengeEdgeLib.sol [Line: 264](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/challengeV2/libraries/ChallengeEdgeLib.sol#L264)

```solidity
    function setRefunded(ChallengeEdge storage edge) internal {
```

</details>

### [N-14] Consider using a struct rather than having many function input parameters

Functions with many parameters can become difficult to read and maintain. Using a struct to encapsulate these parameters can increase code readability, increase reusability, and reduce the likelihood of errors. Consider refactoring functions that take more than three parameters to use a struct instead.

<details>
<summary><i>Affected Code Snippets</i></summary>

- Found in src/bridge/ISequencerInbox.sol [Line: 171](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/bridge/ISequencerInbox.sol#L171)

```solidity
function addSequencerL2BatchFromOrigin(uint256 sequenceNumber, bytes calldata data, uint256 afterDelayedMessagesRead, IGasRefunder gasRefunder
    );
```

- Found in src/bridge/ISequencerInbox.sol [Line: 179](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/bridge/ISequencerInbox.sol#L179)

```solidity
function addSequencerL2BatchFromOrigin(uint256 sequenceNumber, bytes calldata data, uint256 afterDelayedMessagesRead, IGasRefunder gasRefunder, uint256 prevMessageCount, uint256 newMessageCount
    );
```

- Found in src/bridge/ISequencerInbox.sol [Line: 188](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/bridge/ISequencerInbox.sol#L188)

```solidity
function addSequencerL2Batch(uint256 sequenceNumber, bytes calldata data, uint256 afterDelayedMessagesRead, IGasRefunder gasRefunder, uint256 prevMessageCount, uint256 newMessageCount
    );
```

- Found in src/bridge/ISequencerInbox.sol [Line: 197](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/bridge/ISequencerInbox.sol#L197)

```solidity
function addSequencerL2BatchFromBlobs(uint256 sequenceNumber, uint256 afterDelayedMessagesRead, IGasRefunder gasRefunder, uint256 prevMessageCount, uint256 newMessageCount
    );
```

- Found in src/bridge/ISequencerInbox.sol [Line: 207](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/bridge/ISequencerInbox.sol#L207)

```solidity
function addSequencerL2BatchFromBlobsDelayProof(uint256 sequenceNumber, uint256 afterDelayedMessagesRead, IGasRefunder gasRefunder, uint256 prevMessageCount, uint256 newMessageCount, DelayProof calldata delayProof
    );
```

- Found in src/bridge/ISequencerInbox.sol [Line: 219](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/bridge/ISequencerInbox.sol#L219)

```solidity
function addSequencerL2BatchFromOriginDelayProof(uint256 sequenceNumber, bytes calldata data, uint256 afterDelayedMessagesRead, IGasRefunder gasRefunder, uint256 prevMessageCount, uint256 newMessageCount, DelayProof calldata delayProof
    );
```

- Found in src/bridge/ISequencerInbox.sol [Line: 231](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/bridge/ISequencerInbox.sol#L231)

```solidity
function addSequencerL2BatchDelayProof(uint256 sequenceNumber, bytes calldata data, uint256 afterDelayedMessagesRead, IGasRefunder gasRefunder, uint256 prevMessageCount, uint256 newMessageCount, DelayProof calldata delayProof
    );
```

- Found in src/bridge/SequencerInbox.sol [Line: 291](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/bridge/SequencerInbox.sol#L291)

```solidity
function forceInclusion(uint256 _totalDelayedMessagesRead, uint8 kind, calldata l1BlockAndTime, uint256 baseFeeL1, address sender, bytes32 messageDataHash
    );
```

- Found in src/bridge/SequencerInbox.sol [Line: 370](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/bridge/SequencerInbox.sol#L370)

```solidity
function addSequencerL2BatchFromOrigin(uint256 sequenceNumber, bytes calldata data, uint256 afterDelayedMessagesRead, IGasRefunder gasRefunder, uint256 prevMessageCount, uint256 newMessageCount
    );
```

- Found in src/bridge/SequencerInbox.sol [Line: 394](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/bridge/SequencerInbox.sol#L394)

```solidity
function addSequencerL2BatchFromBlobs(uint256 sequenceNumber, uint256 afterDelayedMessagesRead, IGasRefunder gasRefunder, uint256 prevMessageCount, uint256 newMessageCount
    );
```

- Found in src/bridge/SequencerInbox.sol [Line: 413](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/bridge/SequencerInbox.sol#L413)

```solidity
function addSequencerL2BatchFromBlobsDelayProof(uint256 sequenceNumber, uint256 afterDelayedMessagesRead, IGasRefunder gasRefunder, uint256 prevMessageCount, uint256 newMessageCount, DelayProof calldata delayProof
    );
```

- Found in src/bridge/SequencerInbox.sol [Line: 434](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/bridge/SequencerInbox.sol#L434)

```solidity
function addSequencerL2BatchFromOriginDelayProof(uint256 sequenceNumber, bytes calldata data, uint256 afterDelayedMessagesRead, IGasRefunder gasRefunder, uint256 prevMessageCount, uint256 newMessageCount, DelayProof calldata delayProof
    );
```

- Found in src/bridge/SequencerInbox.sol [Line: 459](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/bridge/SequencerInbox.sol#L459)

```solidity
function addSequencerL2BatchFromBlobsImpl(uint256 sequenceNumber, uint256 afterDelayedMessagesRead, uint256 prevMessageCount, uint256 newMessageCount
    );
```

- Found in src/bridge/SequencerInbox.sol [Line: 516](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/bridge/SequencerInbox.sol#L516)

```solidity
function addSequencerL2BatchFromCalldataImpl(uint256 sequenceNumber, bytes calldata data, uint256 afterDelayedMessagesRead, uint256 prevMessageCount, uint256 newMessageCount, bool isFromOrigin
    );
```

- Found in src/bridge/SequencerInbox.sol [Line: 564](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/bridge/SequencerInbox.sol#L564)

```solidity
function addSequencerL2Batch(uint256 sequenceNumber, bytes calldata data, uint256 afterDelayedMessagesRead, IGasRefunder gasRefunder, uint256 prevMessageCount, uint256 newMessageCount
    );
```

- Found in src/bridge/SequencerInbox.sol [Line: 586](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/bridge/SequencerInbox.sol#L586)

```solidity
function addSequencerL2BatchDelayProof(uint256 sequenceNumber, bytes calldata data, uint256 afterDelayedMessagesRead, IGasRefunder gasRefunder, uint256 prevMessageCount, uint256 newMessageCount, DelayProof calldata delayProof
    );
```

- Found in src/bridge/SequencerInbox.sol [Line: 759](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/bridge/SequencerInbox.sol#L759)

```solidity
function submitBatchSpendingReport(bytes32 dataHash, uint256 seqMessageIndex, uint256 gasPrice, uint256 extraGas
    );
```

- Found in src/bridge/SequencerInbox.sol [Line: 795](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/bridge/SequencerInbox.sol#L795)

```solidity
function addSequencerL2BatchImpl(bytes32 dataHash, uint256 afterDelayedMessagesRead, uint256 calldataLengthPosted, uint256 prevMessageCount, uint256 newMessageCount
    );
```

- Found in src/bridge/DelayBuffer.sol [Line: 33](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/bridge/DelayBuffer.sol#L33)

```solidity
function calcBuffer(uint256 start, uint256 end, uint256 buffer, uint256 sequenced, uint256 threshold, uint256 max, uint256 replenishRateInBasis
    );
```

- Found in src/rollup/IRollupAdmin.sol [Line: 88](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/rollup/IRollupAdmin.sol#L88)

```solidity
function forceConfirmAssertion(bytes32 assertionHash, bytes32 parentAssertionHash, AssertionState calldata confirmState, bytes32 inboxAcc
    );
```

- Found in src/rollup/IRollupLogic.sol [Line: 21](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/rollup/IRollupLogic.sol#L21)

```solidity
function confirmAssertion(bytes32 assertionHash, bytes32 prevAssertionHash, AssertionState calldata confirmState, bytes32 winningEdgeId, ConfigData calldata prevConfig, bytes32 inboxAcc
    );
```

- Found in src/rollup/IRollupLogic.sol [Line: 44](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/rollup/IRollupLogic.sol#L44)

```solidity
function newStakeOnNewAssertion(uint256 tokenAmount, AssertionInputs calldata assertion, bytes32 expectedAssertionHash, address withdrawalAddress
    );
```

- Found in src/rollup/RollupAdminLogic.sol [Line: 258](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/rollup/RollupAdminLogic.sol#L258)

```solidity
function forceConfirmAssertion(bytes32 assertionHash, bytes32 parentAssertionHash, AssertionState calldata confirmState, bytes32 inboxAcc
    );
```

- Found in src/rollup/RollupLib.sol [Line: 54](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/rollup/RollupLib.sol#L54)

```solidity
function configHash(bytes32 wasmModuleRoot, uint256 requiredStake, address challengeManager, uint64 confirmPeriodBlocks, uint64 nextInboxPosition
    );
```

- Found in src/rollup/RollupCore.sol [Line: 236](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/rollup/RollupCore.sol#L236)

```solidity
function confirmAssertionInternal(bytes32 assertionHash, bytes32 parentAssertionHash, AssertionState calldata confirmState, bytes32 inboxAcc
    );
```

- Found in src/rollup/RollupCore.sol [Line: 540](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/rollup/RollupCore.sol#L540)

```solidity
function validateAssertionHash(bytes32 assertionHash, AssertionState calldata state, bytes32 prevAssertionHash, bytes32 inboxAcc
    );
```

- Found in src/rollup/RollupUserLogic.sol [Line: 82](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/rollup/RollupUserLogic.sol#L82)

```solidity
function confirmAssertion(bytes32 assertionHash, bytes32 prevAssertionHash, AssertionState calldata confirmState, bytes32 winningEdgeId, ConfigData calldata prevConfig, bytes32 inboxAcc
    );
```

- Found in src/rollup/RollupUserLogic.sol [Line: 252](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/rollup/RollupUserLogic.sol#L252)

```solidity
function fastConfirmAssertion(bytes32 assertionHash, bytes32 parentAssertionHash, AssertionState calldata confirmState, bytes32 inboxAcc
    );
```

- Found in src/rollup/RollupUserLogic.sol [Line: 331](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/rollup/RollupUserLogic.sol#L331)

```solidity
function newStakeOnNewAssertion(uint256 tokenAmount, AssertionInputs calldata assertion, bytes32 expectedAssertionHash, address withdrawalAddress
    );
```

- Found in src/rollup/BridgeCreator.sol [Line: 99](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/rollup/BridgeCreator.sol#L99)

```solidity
function createBridge(address adminProxy, address rollup, address nativeToken, MaxTimeVariation calldata maxTimeVariation, BufferConfig calldata bufferConfig
    );
```

- Found in src/rollup/RollupCreator.sol [Line: 63](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/rollup/RollupCreator.sol#L63)

```solidity
function setTemplates(BridgeCreator _bridgeCreator, IOneStepProofEntry _osp, IEdgeChallengeManager _challengeManagerLogic, IRollupAdmin _rollupAdminLogic, IRollupUser _rollupUserLogic, IUpgradeExecutor _upgradeExecutorLogic, address _validatorWalletCreator, DeployHelper _l2FactoriesDeployer
    );
```

- Found in src/challengeV2/EdgeChallengeManager.sol [Line: 34](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/challengeV2/EdgeChallengeManager.sol#L34)

```solidity
function initialize(IAssertionChain _assertionChain, uint64 _challengePeriodBlocks, IOneStepProofEntry _oneStepProofEntry, uint256 layerZeroBlockEdgeHeight, uint256 layerZeroBigStepEdgeHeight, uint256 layerZeroSmallStepEdgeHeight, IERC20 _stakeToken, address _excessStakeReceiver, uint8 _numBigStepLevel, calldata _stakeAmounts
    );
```

- Found in src/challengeV2/EdgeChallengeManager.sol [Line: 109](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/challengeV2/EdgeChallengeManager.sol#L109)

```solidity
function confirmEdgeByOneStepProof(bytes32 edgeId, OneStepData calldata oneStepData, ConfigData calldata prevConfig, calldata beforeHistoryInclusionProof, calldata afterHistoryInclusionProof
    );
```

- Found in src/challengeV2/EdgeChallengeManager.sol [Line: 132](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/challengeV2/EdgeChallengeManager.sol#L132)

```solidity
function calculateEdgeId(uint8 level, bytes32 originId, uint256 startHeight, bytes32 startHistoryRoot, uint256 endHeight, bytes32 endHistoryRoot
    );
```

- Found in src/challengeV2/EdgeChallengeManager.sol [Line: 148](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/challengeV2/EdgeChallengeManager.sol#L148)

```solidity
function calculateMutualId(uint8 level, bytes32 originId, uint256 startHeight, bytes32 startHistoryRoot, uint256 endHeight
    );
```

- Found in src/challengeV2/EdgeChallengeManager.sol [Line: 305](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/challengeV2/EdgeChallengeManager.sol#L305)

```solidity
function initialize(IAssertionChain _assertionChain, uint64 _challengePeriodBlocks, IOneStepProofEntry _oneStepProofEntry, uint256 layerZeroBlockEdgeHeight, uint256 layerZeroBigStepEdgeHeight, uint256 layerZeroSmallStepEdgeHeight, IERC20 _stakeToken, address _excessStakeReceiver, uint8 _numBigStepLevel, calldata _stakeAmounts
    );
```

- Found in src/challengeV2/EdgeChallengeManager.sol [Line: 604](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/challengeV2/EdgeChallengeManager.sol#L604)

```solidity
function calculateEdgeId(uint8 level, bytes32 originId, uint256 startHeight, bytes32 startHistoryRoot, uint256 endHeight, bytes32 endHistoryRoot
    );
```

- Found in src/challengeV2/EdgeChallengeManager.sol [Line: 616](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/challengeV2/EdgeChallengeManager.sol#L616)

```solidity
function calculateMutualId(uint8 level, bytes32 originId, uint256 startHeight, bytes32 startHistoryRoot, uint256 endHeight
    );
```

- Found in src/challengeV2/IAssertionChain.sol [Line: 15](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/challengeV2/IAssertionChain.sol#L15)

```solidity
function validateAssertionHash(bytes32 assertionHash, AssertionState calldata state, bytes32 prevAssertionHash, bytes32 inboxAcc
    );
```

- Found in src/challengeV2/libraries/EdgeChallengeManagerLib.sol [Line: 213](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/challengeV2/libraries/EdgeChallengeManagerLib.sol#L213)

```solidity
function layerZeroTypeSpecificChecks(EdgeStore storage store, CreateEdgeArgs calldata args, AssertionReferenceData memory ard, IOneStepProofEntry oneStepProofEntry, uint8 numBigStepLevel
    );
```

- Found in src/challengeV2/libraries/EdgeChallengeManagerLib.sol [Line: 411](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/challengeV2/libraries/EdgeChallengeManagerLib.sol#L411)

```solidity
function createLayerZeroEdge(EdgeStore storage store, CreateEdgeArgs calldata args, AssertionReferenceData memory ard, IOneStepProofEntry oneStepProofEntry, uint256 expectedEndHeight, uint8 numBigStepLevel, bool whitelistEnabled
    );
```

- Found in src/challengeV2/libraries/EdgeChallengeManagerLib.sol [Line: 520](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/challengeV2/libraries/EdgeChallengeManagerLib.sol#L520)

```solidity
function updateTimerCacheByClaim(EdgeStore storage store, bytes32 edgeId, bytes32 claimingEdgeId, uint8 numBigStepLevel
    );
```

- Found in src/challengeV2/libraries/EdgeChallengeManagerLib.sol [Line: 604](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/challengeV2/libraries/EdgeChallengeManagerLib.sol#L604)

```solidity
function bisectEdge(EdgeStore storage store, bytes32 edgeId, bytes32 bisectionHistoryRoot, bytes memory prefixProof);
```

- Found in src/challengeV2/libraries/EdgeChallengeManagerLib.sol [Line: 689](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/challengeV2/libraries/EdgeChallengeManagerLib.sol#L689)

```solidity
function checkClaimIdLink(EdgeStore storage store, bytes32 edgeId, bytes32 claimingEdgeId, uint8 numBigStepLevel);
```

- Found in src/challengeV2/libraries/EdgeChallengeManagerLib.sol [Line: 723](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/challengeV2/libraries/EdgeChallengeManagerLib.sol#L723)

```solidity
function confirmEdgeByTime(EdgeStore storage store, bytes32 edgeId, uint64 claimedAssertionUnrivaledBlocks, uint64 confirmationThresholdBlock
    );
```

- Found in src/challengeV2/libraries/EdgeChallengeManagerLib.sol [Line: 766](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/challengeV2/libraries/EdgeChallengeManagerLib.sol#L766)

```solidity
function confirmEdgeByOneStepProof(EdgeStore storage store, bytes32 edgeId, IOneStepProofEntry oneStepProofEntry, OneStepData calldata oneStepData, ExecutionContext memory execCtx, calldata beforeHistoryInclusionProof, calldata afterHistoryInclusionProof, uint8 numBigStepLevel, uint256 bigStepHeight, uint256 smallStepHeight
    );
```

- Found in src/challengeV2/libraries/ChallengeEdgeLib.sol [Line: 69](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/challengeV2/libraries/ChallengeEdgeLib.sol#L69)

```solidity
function newEdgeChecks(bytes32 originId, bytes32 startHistoryRoot, uint256 startHeight, bytes32 endHistoryRoot, uint256 endHeight
    );
```

- Found in src/challengeV2/libraries/ChallengeEdgeLib.sol [Line: 93](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/challengeV2/libraries/ChallengeEdgeLib.sol#L93)

```solidity
function newLayerZeroEdge(bytes32 originId, bytes32 startHistoryRoot, uint256 startHeight, bytes32 endHistoryRoot, uint256 endHeight, bytes32 claimId, address staker, uint8 level
    );
```

- Found in src/challengeV2/libraries/ChallengeEdgeLib.sol [Line: 133](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/challengeV2/libraries/ChallengeEdgeLib.sol#L133)

```solidity
function newChildEdge(bytes32 originId, bytes32 startHistoryRoot, uint256 startHeight, bytes32 endHistoryRoot, uint256 endHeight, uint8 level
    );
```

- Found in src/challengeV2/libraries/ChallengeEdgeLib.sol [Line: 166](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/challengeV2/libraries/ChallengeEdgeLib.sol#L166)

```solidity
function mutualIdComponent(uint8 level, bytes32 originId, uint256 startHeight, bytes32 startHistoryRoot, uint256 endHeight
    );
```

- Found in src/challengeV2/libraries/ChallengeEdgeLib.sol [Line: 189](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/challengeV2/libraries/ChallengeEdgeLib.sol#L189)

```solidity
function idComponent(uint8 level, bytes32 originId, uint256 startHeight, bytes32 startHistoryRoot, uint256 endHeight, bytes32 endHistoryRoot
    );
```

</details>

### [N-15] Consider using descriptive constants when passing zero as a function argument

In instances where utilizing a zero parameter is essential, it is recommended to employ descriptive constants or an enum instead of directly integrating zero within function calls. This strategy aids in clearly articulating the caller's intention and minimizes the risk of errors. Emitting zero also not recomended, as it is not clear what the intention is.

<details>
<summary><i>Affected Code Snippets</i></summary>

- Found in src/bridge/SequencerInbox.sol [Line: 341](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/bridge/SequencerInbox.sol#L341):

```solidity
addSequencerL2BatchImpl(
                dataHash,
                __totalDelayedMessagesRead,
                0,
                prevSeqMsgCount,
                newSeqMsgCount
            );
```

- Found in src/bridge/SequencerInbox.sol [Line: 479](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/bridge/SequencerInbox.sol#L479):

```solidity
addSequencerL2BatchImpl(
                dataHash,
                afterDelayedMessagesRead,
                0,
                prevMessageCount,
                newMessageCount
            );
```

- Found in src/bridge/SequencerInbox.sol [Line: 533](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/bridge/SequencerInbox.sol#L533):

```solidity
addSequencerL2BatchImpl(
                dataHash,
                afterDelayedMessagesRead,
                isFromOrigin ? data.length : 0,
                prevMessageCount,
                newMessageCount
            );
```

- Found in src/bridge/SequencerInbox.sol [Line: 709](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/bridge/SequencerInbox.sol#L709):

```solidity
InvalidHeaderFlag(data[0]);
```

- Found in src/bridge/SequencerInbox.sol [Line: 824](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/bridge/SequencerInbox.sol#L824):

```solidity
submitBatchSpendingReport(dataHash, seqMessageIndex, block.basefee, 0);
```

- Found in src/bridge/SequencerInbox.sol [Line: 894](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/bridge/SequencerInbox.sol#L894):

```solidity
OwnerFunctionCalled(0);
```

- Found in src/rollup/RollupAdminLogic.sol [Line: 63](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/rollup/RollupAdminLogic.sol#L63):

```solidity
bytes32(0);
```

- Found in src/rollup/RollupAdminLogic.sol [Line: 64](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/rollup/RollupAdminLogic.sol#L64):

```solidity
bytes32(0);
```

- Found in src/rollup/RollupAdminLogic.sol [Line: 120](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/rollup/RollupAdminLogic.sol#L120):

```solidity
OwnerFunctionCalled(0);
```

- Found in src/rollup/RollupAdminLogic.sol [Line: 181](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/rollup/RollupAdminLogic.sol#L181):

```solidity
require(_validator.length > 0, "EMPTY_ARRAY");
```

- Found in src/rollup/RollupAdminLogic.sol [Line: 214](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/rollup/RollupAdminLogic.sol#L214):

```solidity
require(newConfirmPeriod > 0, "INVALID_CONFIRM_PERIOD");
```

- Found in src/rollup/RollupAdminLogic.sol [Line: 229](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/rollup/RollupAdminLogic.sol#L229):

```solidity
require(staker.length > 0, "EMPTY_ARRAY");
```

- Found in src/rollup/RollupAdminLogic.sol [Line: 232](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/rollup/RollupAdminLogic.sol#L232):

```solidity
reduceStakeTo(staker[i], 0);
```

- Found in src/rollup/BOLDUpgradeAction.sol [Line: 114](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/rollup/BOLDUpgradeAction.sol#L114):

```solidity
require(inboxMaxCount != 0, "Hash not yet set");
```

- Found in src/rollup/RollupCore.sol [Line: 148](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/rollup/RollupCore.sol#L148):

```solidity
require(blockNum > 0, "NO_ASSERTION");
```

- Found in src/rollup/RollupCore.sol [Line: 278](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/rollup/RollupCore.sol#L278):

```solidity
UserStakeUpdated(stakerAddress, withdrawalAddress, 0, depositAmount);
```

- Found in src/rollup/RollupCore.sol [Line: 323](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/rollup/RollupCore.sol#L323):

```solidity
UserStakeUpdated(stakerAddress, withdrawalAddress, initialStaked, 0);
```

- Found in src/rollup/RollupCore.sol [Line: 335](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/rollup/RollupCore.sol#L335):

```solidity
UserWithdrawableFundsUpdated(account, amount, 0);
```

- Found in src/rollup/RollupCore.sol [Line: 427](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/rollup/RollupCore.sol#L427):

```solidity
require(afterStateCmpMaxInbox <= 0, "INBOX_TOO_FAR");
```

- Found in src/rollup/RollupCore.sol [Line: 466](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/rollup/RollupCore.sol#L466):

```solidity
require(afterInboxPosition != 0, "EMPTY_INBOX_COUNT");
```

- Found in src/rollup/RollupCore.sol [Line: 523](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/rollup/RollupCore.sol#L523):

```solidity
bytes32(0);
```

- Found in src/rollup/RollupCore.sol [Line: 524](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/rollup/RollupCore.sol#L524):

```solidity
bytes32(0);
```

- Found in src/rollup/RollupUserLogic.sol [Line: 120](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/rollup/RollupUserLogic.sol#L120):

```solidity
require(winningEdge.confirmedAtBlock != 0, "ZERO_CONFIRMED_AT_BLOCK");
```

- Found in src/rollup/RollupUserLogic.sol [Line: 360](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/rollup/RollupUserLogic.sol#L360):

```solidity
require(amount > 0, "NO_FUNDS_TO_WITHDRAW");
```

- Found in src/challengeV2/libraries/EdgeChallengeManagerLib.sol [Line: 396](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/challengeV2/libraries/EdgeChallengeManagerLib.sol#L396):

```solidity
newLayerZeroEdge(
            originId, startHistoryRoot, 0, args.endHistoryRoot, args.endHeight, args.claimId, msg.sender, args.level
        );
```

- Found in src/challengeV2/libraries/ChallengeEdgeLib.sol [Line: 259](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/challengeV2/libraries/ChallengeEdgeLib.sol#L259):

```solidity
address(0);
```

- Found in src/challengeV2/libraries/MerkleTreeLib.sol [Line: 111](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/challengeV2/libraries/MerkleTreeLib.sol#L111):

```solidity
require(me.length > 0, "Empty merkle expansion");
```

- Found in src/challengeV2/libraries/MerkleTreeLib.sol [Line: 159](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/challengeV2/libraries/MerkleTreeLib.sol#L159):

```solidity
require(subtreeRoot != 0, "Cannot append empty subtree");
```

- Found in src/challengeV2/libraries/MerkleTreeLib.sol [Line: 195](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/challengeV2/libraries/MerkleTreeLib.sol#L195):

```solidity
require(me[i] == 0, "Append above least significant bit");
```

- Found in src/challengeV2/libraries/MerkleTreeLib.sol [Line: 228](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/challengeV2/libraries/MerkleTreeLib.sol#L228):

```solidity
require(next[next.length - 1] != 0, "Last entry zero");
```

- Found in src/challengeV2/libraries/MerkleTreeLib.sol [Line: 320](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/challengeV2/libraries/MerkleTreeLib.sol#L320):

```solidity
require(preSize > 0, "Pre-size cannot be 0");
```

- Found in src/challengeV2/libraries/MerkleTreeLib.sol [Line: 320](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/challengeV2/libraries/MerkleTreeLib.sol#L320):

```solidity
require(preSize > 0, "Pre-size cannot be 0");
```

- Found in src/challengeV2/libraries/MerkleTreeLib.sol [Line: 329](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/challengeV2/libraries/MerkleTreeLib.sol#L329):

```solidity
slice(preExpansion, 0, preExpansion.length);
```

- Found in src/challengeV2/libraries/UintUtilsLib.sol [Line: 15](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/challengeV2/libraries/UintUtilsLib.sol#L15):

```solidity
require(x > 0, "Zero has no significant bits");
```

- Found in src/challengeV2/libraries/UintUtilsLib.sol [Line: 30](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/challengeV2/libraries/UintUtilsLib.sol#L30):

```solidity
require(x != 0, "Zero has no significant bits");
```

</details>

### [N-16] Custom error has no error details

Take advantage of custom error's return value property.

An important feature of Custom Error is that values such as address, tokenID, msg.value can be written inside the () sign, providing a serious advantage in debugging and examining the revert details.

<details>
<summary><i>Affected Code Snippets</i></summary>

- Found in src/libraries/Error.sol [Line: 204](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/libraries/Error.sol#L204):

```solidity
error NativeTokenMismatch();
```

- Found in src/libraries/Error.sol [Line: 76](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/libraries/Error.sol#L76):

```solidity
error CallNotAllowed();
```

- Found in src/libraries/Error.sol [Line: 120](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/libraries/Error.sol#L120):

```solidity
error GasLimitTooLarge();
```

- Found in src/libraries/Error.sol [Line: 142](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/libraries/Error.sol#L142):

```solidity
error BridgeCallFailed();
```

- Found in src/libraries/Error.sol [Line: 147](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/libraries/Error.sol#L147):

```solidity
error DelayedBackwards();
```

- Found in src/libraries/Error.sol [Line: 150](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/libraries/Error.sol#L150):

```solidity
error DelayedTooFar();
```

- Found in src/libraries/Error.sol [Line: 153](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/libraries/Error.sol#L153):

```solidity
error ForceIncludeBlockTooSoon();
```

- Found in src/libraries/Error.sol [Line: 156](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/libraries/Error.sol#L156):

```solidity
error ForceIncludeTimeTooSoon();
```

- Found in src/libraries/Error.sol [Line: 159](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/libraries/Error.sol#L159):

```solidity
error IncorrectMessagePreimage();
```

- Found in src/libraries/Error.sol [Line: 162](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/libraries/Error.sol#L162):

```solidity
error NotBatchPoster();
```

- Found in src/libraries/Error.sol [Line: 204](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/libraries/Error.sol#L204):

```solidity
error NativeTokenMismatch();
```

- Found in src/libraries/Error.sol [Line: 210](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/libraries/Error.sol#L210):

```solidity
error BadMaxTimeVariation();
```

- Found in src/libraries/Error.sol [Line: 213](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/libraries/Error.sol#L213):

```solidity
error BadBufferConfig();
```

- Found in src/libraries/Error.sol [Line: 216](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/libraries/Error.sol#L216):

```solidity
error ExtraGasNotUint64();
```

- Found in src/libraries/Error.sol [Line: 219](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/libraries/Error.sol#L219):

```solidity
error KeysetTooLarge();
```

- Found in src/assertionStakingPool/StakingPoolCreatorUtils.sol [Line: 12](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/assertionStakingPool/StakingPoolCreatorUtils.sol#L12):

```solidity
error PoolDoesntExist();
```

- Found in src/challengeV2/libraries/ChallengeErrors.sol [Line: 14](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/challengeV2/libraries/ChallengeErrors.sol#L14):

```solidity
error AssertionHashEmpty();
```

- Found in src/challengeV2/libraries/ChallengeErrors.sol [Line: 18](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/challengeV2/libraries/ChallengeErrors.sol#L18):

```solidity
error AssertionNotPending();
```

- Found in src/challengeV2/libraries/ChallengeErrors.sol [Line: 20](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/challengeV2/libraries/ChallengeErrors.sol#L20):

```solidity
error AssertionNoSibling();
```

- Found in src/challengeV2/libraries/ChallengeErrors.sol [Line: 22](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/challengeV2/libraries/ChallengeErrors.sol#L22):

```solidity
error EmptyEdgeSpecificProof();
```

- Found in src/challengeV2/libraries/ChallengeErrors.sol [Line: 24](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/challengeV2/libraries/ChallengeErrors.sol#L24):

```solidity
error EmptyStartMachineStatus();
```

- Found in src/challengeV2/libraries/ChallengeErrors.sol [Line: 26](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/challengeV2/libraries/ChallengeErrors.sol#L26):

```solidity
error EmptyEndMachineStatus();
```

- Found in src/challengeV2/libraries/ChallengeErrors.sol [Line: 28](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/challengeV2/libraries/ChallengeErrors.sol#L28):

```solidity
error ClaimEdgeNotPending();
```

</details>

### [N-17] Consider emitting an event at the end of the constructor

This will allow users to easily exactly pinpoint when and by whom a contract was constructed.

<details>
<summary><i>Affected Code Snippets</i></summary>

- Found in src/bridge/SequencerInbox.sol [Line: 144](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/bridge/SequencerInbox.sol#L144):

```solidity
constructor(
```

- Found in src/assertionStakingPool/AssertionStakingPool.sol [Line: 31](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/assertionStakingPool/AssertionStakingPool.sol#L31):

```solidity
constructor(
```

- Found in src/assertionStakingPool/EdgeStakingPool.sol [Line: 35](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/assertionStakingPool/EdgeStakingPool.sol#L35):

```solidity
constructor(
```

- Found in src/assertionStakingPool/AbsBoldStakingPool.sol [Line: 24](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/assertionStakingPool/AbsBoldStakingPool.sol#L24):

```solidity
constructor(address _stakeToken) {
```

- Found in src/rollup/BOLDUpgradeAction.sol [Line: 126](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/rollup/BOLDUpgradeAction.sol#L126):

```solidity
constructor(IOldRollup _rollup) {
```

- Found in src/rollup/BOLDUpgradeAction.sol [Line: 169](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/rollup/BOLDUpgradeAction.sol#L169):

```solidity
constructor(uint256[] memory __array) {
```

- Found in src/rollup/BOLDUpgradeAction.sol [Line: 287](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/rollup/BOLDUpgradeAction.sol#L287):

```solidity
constructor(
```

- Found in src/rollup/BridgeCreator.sol [Line: 45](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/rollup/BridgeCreator.sol#L45):

```solidity
constructor(
```

- Found in src/rollup/RollupCreator.sol [Line: 58](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/rollup/RollupCreator.sol#L58):

```solidity
constructor() Ownable() {}
```

- Found in src/challengeV2/EdgeChallengeManager.sol [Line: 300](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/challengeV2/EdgeChallengeManager.sol#L300):

```solidity
constructor() {
```

</details>

### [N-18] Consider using named returns

Using named returns makes the code more self-documenting, makes it easier to fill out NatSpec, and in some cases can save gas. The cases below are where there currently is at most one return statement, which is optimal for named returns.

<details>
<summary><i>Affected Code Snippets</i></summary>

- Found in src/challengeV2/EdgeChallengeManager.sol [Line: 371](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/challengeV2/EdgeChallengeManager.sol#L371):

```solidity
function createLayerZeroEdge(CreateEdgeArgs calldata args) external returns (bytes32)
```

- Found in src/challengeV2/EdgeChallengeManager.sol [Line: 451](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/challengeV2/EdgeChallengeManager.sol#L451):

```solidity
function bisectEdge(bytes32 edgeId, bytes32 bisectionHistoryRoot, bytes calldata prefixProof)
        external
        returns (bytes32, bytes32)
```

- Found in src/challengeV2/EdgeChallengeManager.sol [Line: 591](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/challengeV2/EdgeChallengeManager.sol#L591):

```solidity
function getLayerZeroEndHeight(EdgeType eType) public view returns (uint256)
```

- Found in src/challengeV2/EdgeChallengeManager.sol [Line: 604](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/challengeV2/EdgeChallengeManager.sol#L604):

```solidity
function calculateEdgeId(
        uint8 level,
        bytes32 originId,
        uint256 startHeight,
        bytes32 startHistoryRoot,
        uint256 endHeight,
        bytes32 endHistoryRoot
    ) public pure returns (bytes32)
```

- Found in src/challengeV2/EdgeChallengeManager.sol [Line: 616](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/challengeV2/EdgeChallengeManager.sol#L616):

```solidity
function calculateMutualId(
        uint8 level,
        bytes32 originId,
        uint256 startHeight,
        bytes32 startHistoryRoot,
        uint256 endHeight
    ) public pure returns (bytes32)
```

- Found in src/challengeV2/EdgeChallengeManager.sol [Line: 627](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/challengeV2/EdgeChallengeManager.sol#L627):

```solidity
function edgeExists(bytes32 edgeId) public view returns (bool)
```

- Found in src/challengeV2/EdgeChallengeManager.sol [Line: 637](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/challengeV2/EdgeChallengeManager.sol#L637):

```solidity
function edgeLength(bytes32 edgeId) public view returns (uint256)
```

- Found in src/challengeV2/EdgeChallengeManager.sol [Line: 642](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/challengeV2/EdgeChallengeManager.sol#L642):

```solidity
function hasRival(bytes32 edgeId) public view returns (bool)
```

- Found in src/challengeV2/EdgeChallengeManager.sol [Line: 647](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/challengeV2/EdgeChallengeManager.sol#L647):

```solidity
function confirmedRival(bytes32 mutualId) public view returns (bytes32)
```

- Found in src/challengeV2/EdgeChallengeManager.sol [Line: 652](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/challengeV2/EdgeChallengeManager.sol#L652):

```solidity
function hasLengthOneRival(bytes32 edgeId) public view returns (bool)
```

- Found in src/challengeV2/EdgeChallengeManager.sol [Line: 657](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/challengeV2/EdgeChallengeManager.sol#L657):

```solidity
function timeUnrivaled(bytes32 edgeId) public view returns (uint256)
```

- Found in src/challengeV2/EdgeChallengeManager.sol [Line: 662](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/challengeV2/EdgeChallengeManager.sol#L662):

```solidity
function getPrevAssertionHash(bytes32 edgeId) public view returns (bytes32)
```

- Found in src/challengeV2/EdgeChallengeManager.sol [Line: 667](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/challengeV2/EdgeChallengeManager.sol#L667):

```solidity
function firstRival(bytes32 mutualId) public view returns (bytes32)
```

- Found in src/challengeV2/EdgeChallengeManager.sol [Line: 672](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/challengeV2/EdgeChallengeManager.sol#L672):

```solidity
function hasMadeLayerZeroRival(address account, bytes32 mutualId) external view returns (bool)
```

- Found in src/challengeV2/IAssertionChain.sol [Line: 14](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/challengeV2/IAssertionChain.sol#L14):

```solidity
function bridge() external view returns (IBridge);
    function validateAssertionHash(
        bytes32 assertionHash,
        AssertionState calldata state,
        bytes32 prevAssertionHash,
        bytes32 inboxAcc
    ) external view;
    function validateConfig(bytes32 assertionHash, ConfigData calldata configData) external view;
    function getFirstChildCreationBlock(bytes32 assertionHash) external view returns (uint64);
    function getSecondChildCreationBlock(bytes32 assertionHash) external view returns (uint64);
    function isFirstChild(bytes32 assertionHash) external view returns (bool);
    function isPending(bytes32 assertionHash) external view returns (bool);
    function isValidator(address) external view returns (bool);
    function validatorWhitelistDisabled() external view returns (bool);
}
```

- Found in src/challengeV2/IAssertionChain.sol [Line: 22](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/challengeV2/IAssertionChain.sol#L22):

```solidity
function getFirstChildCreationBlock(bytes32 assertionHash) external view returns (uint64);
    function getSecondChildCreationBlock(bytes32 assertionHash) external view returns (uint64);
    function isFirstChild(bytes32 assertionHash) external view returns (bool);
    function isPending(bytes32 assertionHash) external view returns (bool);
    function isValidator(address) external view returns (bool);
    function validatorWhitelistDisabled() external view returns (bool);
}
```

- Found in src/challengeV2/IAssertionChain.sol [Line: 23](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/challengeV2/IAssertionChain.sol#L23):

```solidity
function getSecondChildCreationBlock(bytes32 assertionHash) external view returns (uint64);
    function isFirstChild(bytes32 assertionHash) external view returns (bool);
    function isPending(bytes32 assertionHash) external view returns (bool);
    function isValidator(address) external view returns (bool);
    function validatorWhitelistDisabled() external view returns (bool);
}
```

- Found in src/challengeV2/IAssertionChain.sol [Line: 24](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/challengeV2/IAssertionChain.sol#L24):

```solidity
function isFirstChild(bytes32 assertionHash) external view returns (bool);
    function isPending(bytes32 assertionHash) external view returns (bool);
    function isValidator(address) external view returns (bool);
    function validatorWhitelistDisabled() external view returns (bool);
}
```

- Found in src/challengeV2/IAssertionChain.sol [Line: 25](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/challengeV2/IAssertionChain.sol#L25):

```solidity
function isPending(bytes32 assertionHash) external view returns (bool);
    function isValidator(address) external view returns (bool);
    function validatorWhitelistDisabled() external view returns (bool);
}
```

- Found in src/challengeV2/IAssertionChain.sol [Line: 26](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/challengeV2/IAssertionChain.sol#L26):

```solidity
function isValidator(address) external view returns (bool);
    function validatorWhitelistDisabled() external view returns (bool);
}
```

- Found in src/challengeV2/IAssertionChain.sol [Line: 27](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/challengeV2/IAssertionChain.sol#L27):

```solidity
function validatorWhitelistDisabled() external view returns (bool);
}
```

- Found in src/challengeV2/libraries/EdgeChallengeManagerLib.sol [Line: 327](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/challengeV2/libraries/EdgeChallengeManagerLib.sol#L327):

```solidity
function isPowerOfTwo(uint256 x) internal pure returns (bool)
```

- Found in src/challengeV2/libraries/EdgeChallengeManagerLib.sol [Line: 344](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/challengeV2/libraries/EdgeChallengeManagerLib.sol#L344):

```solidity
function layerZeroCommonChecks(ProofData memory proofData, CreateEdgeArgs calldata args, uint256 expectedEndHeight)
        private
        pure
        returns (bytes32)
```

- Found in src/challengeV2/libraries/EdgeChallengeManagerLib.sol [Line: 443](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/challengeV2/libraries/EdgeChallengeManagerLib.sol#L443):

```solidity
function getPrevAssertionHash(EdgeStore storage store, bytes32 edgeId) internal view returns (bytes32)
```

- Found in src/challengeV2/libraries/EdgeChallengeManagerLib.sol [Line: 463](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/challengeV2/libraries/EdgeChallengeManagerLib.sol#L463):

```solidity
function hasRival(EdgeStore storage store, bytes32 edgeId) internal view returns (bool)
```

- Found in src/challengeV2/libraries/EdgeChallengeManagerLib.sol [Line: 483](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/challengeV2/libraries/EdgeChallengeManagerLib.sol#L483):

```solidity
function hasLengthOneRival(EdgeStore storage store, bytes32 edgeId) internal view returns (bool)
```

- Found in src/challengeV2/libraries/EdgeChallengeManagerLib.sol [Line: 488](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/challengeV2/libraries/EdgeChallengeManagerLib.sol#L488):

```solidity
function timeUnrivaledTotal(EdgeStore storage store, bytes32 edgeId) internal view returns (uint256)
```

- Found in src/challengeV2/libraries/EdgeChallengeManagerLib.sol [Line: 502](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/challengeV2/libraries/EdgeChallengeManagerLib.sol#L502):

```solidity
function updateTimerCache(EdgeStore storage store, bytes32 edgeId, uint256 newValue)
        internal
        returns (bool, uint256)
```

- Found in src/challengeV2/libraries/EdgeChallengeManagerLib.sol [Line: 516](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/challengeV2/libraries/EdgeChallengeManagerLib.sol#L516):

```solidity
function updateTimerCacheByChildren(EdgeStore storage store, bytes32 edgeId) internal returns (bool, uint256)
```

- Found in src/challengeV2/libraries/EdgeChallengeManagerLib.sol [Line: 520](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/challengeV2/libraries/EdgeChallengeManagerLib.sol#L520):

```solidity
function updateTimerCacheByClaim(
        EdgeStore storage store,
        bytes32 edgeId,
        bytes32 claimingEdgeId,
        uint8 numBigStepLevel
    ) internal returns (bool, uint256)
```

- Found in src/challengeV2/libraries/EdgeChallengeManagerLib.sol [Line: 537](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/challengeV2/libraries/EdgeChallengeManagerLib.sol#L537):

```solidity
function timeUnrivaled(EdgeStore storage store, bytes32 edgeId) internal view returns (uint256)
```

- Found in src/challengeV2/libraries/EdgeChallengeManagerLib.sol [Line: 576](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/challengeV2/libraries/EdgeChallengeManagerLib.sol#L576):

```solidity
function mandatoryBisectionHeight(uint256 start, uint256 end) internal pure returns (uint256)
```

- Found in src/challengeV2/libraries/EdgeChallengeManagerLib.sol [Line: 604](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/challengeV2/libraries/EdgeChallengeManagerLib.sol#L604):

```solidity
function bisectEdge(EdgeStore storage store, bytes32 edgeId, bytes32 bisectionHistoryRoot, bytes memory prefixProof)
        internal
        returns (bytes32, EdgeAddedData memory, EdgeAddedData memory)
```

- Found in src/challengeV2/libraries/EdgeChallengeManagerLib.sol [Line: 674](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/challengeV2/libraries/EdgeChallengeManagerLib.sol#L674):

```solidity
function nextEdgeLevel(uint8 level, uint8 numBigStepLevel) internal pure returns (uint8)
```

- Found in src/challengeV2/libraries/EdgeChallengeManagerLib.sol [Line: 723](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/challengeV2/libraries/EdgeChallengeManagerLib.sol#L723):

```solidity
function confirmEdgeByTime(
        EdgeStore storage store,
        bytes32 edgeId,
        uint64 claimedAssertionUnrivaledBlocks,
        uint64 confirmationThresholdBlock
    ) internal returns (uint256)
```

- Found in src/challengeV2/libraries/ChallengeEdgeLib.sol [Line: 166](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/challengeV2/libraries/ChallengeEdgeLib.sol#L166):

```solidity
function mutualIdComponent(
        uint8 level,
        bytes32 originId,
        uint256 startHeight,
        bytes32 startHistoryRoot,
        uint256 endHeight
    ) internal pure returns (bytes32)
```

- Found in src/challengeV2/libraries/ChallengeEdgeLib.sol [Line: 180](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/challengeV2/libraries/ChallengeEdgeLib.sol#L180):

```solidity
function mutualId(ChallengeEdge storage ce) internal view returns (bytes32)
```

- Found in src/challengeV2/libraries/ChallengeEdgeLib.sol [Line: 184](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/challengeV2/libraries/ChallengeEdgeLib.sol#L184):

```solidity
function mutualIdMem(ChallengeEdge memory ce) internal pure returns (bytes32)
```

- Found in src/challengeV2/libraries/ChallengeEdgeLib.sol [Line: 189](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/challengeV2/libraries/ChallengeEdgeLib.sol#L189):

```solidity
function idComponent(
        uint8 level,
        bytes32 originId,
        uint256 startHeight,
        bytes32 startHistoryRoot,
        uint256 endHeight,
        bytes32 endHistoryRoot
    ) internal pure returns (bytes32)
```

- Found in src/challengeV2/libraries/ChallengeEdgeLib.sol [Line: 208](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/challengeV2/libraries/ChallengeEdgeLib.sol#L208):

```solidity
function idMem(ChallengeEdge memory edge) internal pure returns (bytes32)
```

- Found in src/challengeV2/libraries/ChallengeEdgeLib.sol [Line: 215](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/challengeV2/libraries/ChallengeEdgeLib.sol#L215):

```solidity
function id(ChallengeEdge storage edge) internal view returns (bytes32)
```

- Found in src/challengeV2/libraries/ChallengeEdgeLib.sol [Line: 222](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/challengeV2/libraries/ChallengeEdgeLib.sol#L222):

```solidity
function exists(ChallengeEdge storage edge) internal view returns (bool)
```

- Found in src/challengeV2/libraries/ChallengeEdgeLib.sol [Line: 228](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/challengeV2/libraries/ChallengeEdgeLib.sol#L228):

```solidity
function length(ChallengeEdge storage edge) internal view returns (uint256)
```

- Found in src/challengeV2/libraries/ChallengeEdgeLib.sol [Line: 258](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/challengeV2/libraries/ChallengeEdgeLib.sol#L258):

```solidity
function isLayerZero(ChallengeEdge storage edge) internal view returns (bool)
```

- Found in src/challengeV2/libraries/MerkleTreeLib.sol [Line: 110](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/challengeV2/libraries/MerkleTreeLib.sol#L110):

```solidity
function root(bytes32[] memory me) internal pure returns (bytes32)
```

- Found in src/challengeV2/libraries/MerkleTreeLib.sol [Line: 251](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/challengeV2/libraries/MerkleTreeLib.sol#L251):

```solidity
function maximumAppendBetween(uint256 startSize, uint256 endSize) internal pure returns (uint256)
```

- Found in src/challengeV2/libraries/MerkleTreeLib.sol [Line: 292](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/challengeV2/libraries/MerkleTreeLib.sol#L292):

```solidity
function treeSize(bytes32[] memory me) internal pure returns (uint256)
```

</details>

### [N-19] Events missing `msg.sender` information

Events emitted in public or external functions lack sender information, making it difficult to trace the origin of these events. Include `msg.sender` information in events emitted by public or external functions to make traceability and debugging easier.

<details>
<summary><i>Affected Code Snippets</i></summary>

- Found in src/bridge/SequencerInbox.sol [Line: 348](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/bridge/SequencerInbox.sol#L348):

```solidity
emit SequencerBatchDelivered(
            seqMessageIndex,
            beforeAcc,
            afterAcc,
            delayedAcc,
            totalDelayedMessagesRead,
            timeBounds,
            IBridge.BatchDataLocation.NoData
        );
```

- Found in src/bridge/SequencerInbox.sol [Line: 492](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/bridge/SequencerInbox.sol#L492):

```solidity
emit SequencerBatchDelivered(
            sequenceNumber,
            beforeAcc,
            afterAcc,
            delayedAcc,
            totalDelayedMessagesRead,
            timeBounds,
            IBridge.BatchDataLocation.Blob
        );
```

- Found in src/bridge/SequencerInbox.sol [Line: 546](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/bridge/SequencerInbox.sol#L546):

```solidity
emit SequencerBatchDelivered(
            seqMessageIndex,
            beforeAcc,
            afterAcc,
            delayedAcc,
            totalDelayedMessagesRead,
            timeBounds,
            isFromOrigin
                ? IBridge.BatchDataLocation.TxInput
                : IBridge.BatchDataLocation.SeparateBatchEvent
        );
```

- Found in src/bridge/SequencerInbox.sol [Line: 559](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/bridge/SequencerInbox.sol#L559):

```solidity
emit SequencerBatchData(seqMessageIndex, data);
```

- Found in src/bridge/SequencerInbox.sol [Line: 792](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/bridge/SequencerInbox.sol#L792):

```solidity
emit InboxMessageDelivered(msgNum, spendingReportMsg);
```

- Found in src/bridge/SequencerInbox.sol [Line: 921](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/bridge/SequencerInbox.sol#L921):

```solidity
emit SetValidKeyset(ksHash, keysetBytes);
```

- Found in src/bridge/SequencerInbox.sol [Line: 922](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/bridge/SequencerInbox.sol#L922):

```solidity
emit OwnerFunctionCalled(2);
```

- Found in src/bridge/SequencerInbox.sol [Line: 932](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/bridge/SequencerInbox.sol#L932):

```solidity
emit InvalidateKeyset(ksHash);
```

- Found in src/rollup/BOLDUpgradeAction.sol [Line: 109](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/rollup/BOLDUpgradeAction.sol#L109):

```solidity
emit HashSet(h, executionState, inboxMaxCount);
```

- Found in src/rollup/RollupCore.sol [Line: 266](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/rollup/RollupCore.sol#L266):

```solidity
emit AssertionConfirmed(assertionHash, blockHash, sendRoot);
```

- Found in src/rollup/RollupCore.sol [Line: 278](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/rollup/RollupCore.sol#L278):

```solidity
emit UserStakeUpdated(stakerAddress, withdrawalAddress, 0, depositAmount);
```

- Found in src/rollup/RollupCore.sol [Line: 291](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/rollup/RollupCore.sol#L291):

```solidity
emit UserStakeUpdated(stakerAddress, staker.withdrawalAddress, initialStaked, finalStaked);
```

- Found in src/rollup/RollupCore.sol [Line: 308](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/rollup/RollupCore.sol#L308):

```solidity
emit UserStakeUpdated(stakerAddress, withdrawalAddress, current, target);
```

- Found in src/rollup/RollupCore.sol [Line: 323](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/rollup/RollupCore.sol#L323):

```solidity
emit UserStakeUpdated(stakerAddress, withdrawalAddress, initialStaked, 0);
```

- Found in src/rollup/RollupCore.sol [Line: 335](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/rollup/RollupCore.sol#L335):

```solidity
emit UserWithdrawableFundsUpdated(account, amount, 0);
```

- Found in src/rollup/RollupCore.sol [Line: 348](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/rollup/RollupCore.sol#L348):

```solidity
emit UserWithdrawableFundsUpdated(account, initialWithdrawable, finalWithdrawable);
```

- Found in src/rollup/BridgeCreator.sol [Line: 55](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/rollup/BridgeCreator.sol#L55):

```solidity
emit TemplatesUpdated();
```

- Found in src/rollup/BridgeCreator.sol [Line: 60](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/rollup/BridgeCreator.sol#L60):

```solidity
emit ERC20TemplatesUpdated();
```

- Found in src/rollup/RollupCreator.sol [Line: 81](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/rollup/RollupCreator.sol#L81):

```solidity
emit TemplatesUpdated();
```

- Found in src/challengeV2/EdgeChallengeManager.sol [Line: 437](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/challengeV2/EdgeChallengeManager.sol#L437):

```solidity
emit EdgeAdded(
            edgeAdded.edgeId,
            edgeAdded.mutualId,
            edgeAdded.originId,
            edgeAdded.claimId,
            edgeAdded.length,
            edgeAdded.level,
            edgeAdded.hasRival,
            edgeAdded.isLayerZero
        );
```

- Found in src/challengeV2/EdgeChallengeManager.sol [Line: 462](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/challengeV2/EdgeChallengeManager.sol#L462):

```solidity
emit EdgeAdded(
                lowerChildAdded.edgeId,
                lowerChildAdded.mutualId,
                lowerChildAdded.originId,
                lowerChildAdded.claimId,
                lowerChildAdded.length,
                lowerChildAdded.level,
                lowerChildAdded.hasRival,
                lowerChildAdded.isLayerZero
            );
```

- Found in src/challengeV2/EdgeChallengeManager.sol [Line: 474](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/challengeV2/EdgeChallengeManager.sol#L474):

```solidity
emit EdgeAdded(
            upperChildAdded.edgeId,
            upperChildAdded.mutualId,
            upperChildAdded.originId,
            upperChildAdded.claimId,
            upperChildAdded.length,
            upperChildAdded.level,
            upperChildAdded.hasRival,
            upperChildAdded.isLayerZero
        );
```

- Found in src/challengeV2/EdgeChallengeManager.sol [Line: 485](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/challengeV2/EdgeChallengeManager.sol#L485):

```solidity
emit EdgeBisected(edgeId, lowerChildId, upperChildAdded.edgeId, lowerChildAlreadyExists);
```

- Found in src/challengeV2/EdgeChallengeManager.sol [Line: 494](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/challengeV2/EdgeChallengeManager.sol#L494):

```solidity
emit TimerCacheUpdated(edgeIds[i], newValue);
```

- Found in src/challengeV2/EdgeChallengeManager.sol [Line: 501](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/challengeV2/EdgeChallengeManager.sol#L501):

```solidity
emit TimerCacheUpdated(edgeId, newValue);
```

- Found in src/challengeV2/EdgeChallengeManager.sol [Line: 507](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/challengeV2/EdgeChallengeManager.sol#L507):

```solidity
emit TimerCacheUpdated(edgeId, newValue);
```

</details>

### [N-20] Leverage recent Solidity features with 0.8.23

The recent Solidity updates introduce significant features and optimizations aimed at optimizing contract code clarity and maintainability. Notably, the introduction of push0 streamlines code by enabling the placement of 0 on the stack for EVM versions from 'Shanghai' onwards.

Furthermore, Solidity now extends NatSpec documentation support to enum and struct definitions, optimizing code documentation comprehensiveness and insightfulness.

Moreover, the re-implementation of UnusedAssignEliminator and UnusedStoreEliminator in the Solidity optimizer allows for the removal of unused assignments within deeply nested loops. This results in cleaner, more efficient contract code, reducing clutter and potential points of confusion during code review or debugging.

Utilizing these features and optimizations is recommended to strengthen the robustness and readability of smart contracts.

### [N-21] Simultaneous use of `revert` and `require` statements in Solidity contracts

The contract employs both `require()/revert()` and custom errors for error handling. For clarity and maintainability, it's advisable to use a consistent error handling method within each file.

<details>
<summary><i>Affected Code Snippets</i></summary>

- Found in [src/challengeV2/libraries/MerkleTreeLib.sol](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/challengeV2/libraries/MerkleTreeLib.sol)
</details>

### [N-22] Outdated Solidity version

The current Solidity version used in the contract is outdated. Consider using a more recent version for advanced features and security.

0.8.4: bytes.concat() instead of abi.encodePacked(,)

0.8.12: string.concat() instead of abi.encodePacked(,)

0.8.13: Ability to use using for with a list of free functions

0.8.14: ABI Encoder: When ABI-encoding values from calldata that contain nested arrays, correctly validate the nested array length against calldatasize() in all cases. Override Checker: Allow changing data location for parameters only when overriding external functions.

0.8.15: Code Generation: Avoid writing dirty bytes to storage when copying bytes arrays. Yul Optimizer: Keep all memory side-effects of inline assembly blocks.

0.8.16: Code Generation: Fix data corruption that affected ABI-encoding of calldata values represented by tuples: structs at any nesting level; argument lists of external functions, events and errors; return value lists of external functions. The 32 leading bytes of the first dynamically-encoded value in the tuple would get zeroed when the last component contained a statically-encoded array.

0.8.17: Yul Optimizer: Prevent the incorrect removal of storage writes before calls to Yul functions that conditionally terminate the external EVM call.

<details>
<summary><i>Affected Code Snippets</i></summary>

- Found in src/bridge/SequencerInbox.sol [Line: 5](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/bridge/SequencerInbox.sol#L5)

```solidity
pragma solidity ^0.8.0;
```

- Found in src/bridge/DelayBuffer.sol [Line: 5](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/bridge/DelayBuffer.sol#L5)

```solidity
pragma solidity ^0.8.0;
```

- Found in src/assertionStakingPool/EdgeStakingPoolCreator.sol [Line: 6](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/assertionStakingPool/EdgeStakingPoolCreator.sol#L6)

```solidity
pragma solidity ^0.8.0;
```

- Found in src/assertionStakingPool/AssertionStakingPool.sol [Line: 6](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/assertionStakingPool/AssertionStakingPool.sol#L6)

```solidity
pragma solidity ^0.8.0;
```

- Found in src/assertionStakingPool/StakingPoolCreatorUtils.sol [Line: 6](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/assertionStakingPool/StakingPoolCreatorUtils.sol#L6)

```solidity
pragma solidity ^0.8.0;
```

- Found in src/assertionStakingPool/EdgeStakingPool.sol [Line: 5](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/assertionStakingPool/EdgeStakingPool.sol#L5)

```solidity
pragma solidity ^0.8.0;
```

- Found in src/assertionStakingPool/AbsBoldStakingPool.sol [Line: 5](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/assertionStakingPool/AbsBoldStakingPool.sol#L5)

```solidity
pragma solidity ^0.8.0;
```

- Found in src/assertionStakingPool/AssertionStakingPoolCreator.sol [Line: 6](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/assertionStakingPool/AssertionStakingPoolCreator.sol#L6)

```solidity
pragma solidity ^0.8.0;
```

- Found in src/assertionStakingPool/interfaces/IEdgeStakingPoolCreator.sol [Line: 5](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/assertionStakingPool/interfaces/IEdgeStakingPoolCreator.sol#L5)

```solidity
pragma solidity ^0.8.0;
```

- Found in src/assertionStakingPool/interfaces/IAssertionStakingPoolCreator.sol [Line: 5](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/assertionStakingPool/interfaces/IAssertionStakingPoolCreator.sol#L5)

```solidity
pragma solidity ^0.8.0;
```

- Found in src/assertionStakingPool/interfaces/IAbsBoldStakingPool.sol [Line: 5](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/assertionStakingPool/interfaces/IAbsBoldStakingPool.sol#L5)

```solidity
pragma solidity ^0.8.0;
```

- Found in src/assertionStakingPool/interfaces/IEdgeStakingPool.sol [Line: 5](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/assertionStakingPool/interfaces/IEdgeStakingPool.sol#L5)

```solidity
pragma solidity ^0.8.0;
```

- Found in src/assertionStakingPool/interfaces/IAssertionStakingPool.sol [Line: 5](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/assertionStakingPool/interfaces/IAssertionStakingPool.sol#L5)

```solidity
pragma solidity ^0.8.0;
```

- Found in src/rollup/RollupProxy.sol [Line: 5](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/rollup/RollupProxy.sol#L5)

```solidity
pragma solidity ^0.8.0;
```

- Found in src/rollup/IRollupCore.sol [Line: 5](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/rollup/IRollupCore.sol#L5)

```solidity
pragma solidity ^0.8.0;
```

- Found in src/rollup/Assertion.sol [Line: 5](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/rollup/Assertion.sol#L5)

```solidity
pragma solidity ^0.8.0;
```

- Found in src/rollup/IRollupAdmin.sol [Line: 5](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/rollup/IRollupAdmin.sol#L5)

```solidity
pragma solidity ^0.8.0;
```

- Found in src/rollup/IRollupLogic.sol [Line: 5](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/rollup/IRollupLogic.sol#L5)

```solidity
pragma solidity ^0.8.0;
```

- Found in src/rollup/AssertionState.sol [Line: 5](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/rollup/AssertionState.sol#L5)

```solidity
pragma solidity ^0.8.0;
```

- Found in src/rollup/Config.sol [Line: 5](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/rollup/Config.sol#L5)

```solidity
pragma solidity ^0.8.0;
```

- Found in src/rollup/RollupAdminLogic.sol [Line: 5](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/rollup/RollupAdminLogic.sol#L5)

```solidity
pragma solidity ^0.8.0;
```

- Found in src/rollup/RollupLib.sol [Line: 5](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/rollup/RollupLib.sol#L5)

```solidity
pragma solidity ^0.8.0;
```

- Found in src/rollup/BOLDUpgradeAction.sol [Line: 5](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/rollup/BOLDUpgradeAction.sol#L5)

```solidity
pragma solidity ^0.8.0;
```

- Found in src/rollup/RollupCore.sol [Line: 5](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/rollup/RollupCore.sol#L5)

```solidity
pragma solidity ^0.8.0;
```

- Found in src/rollup/RollupUserLogic.sol [Line: 5](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/rollup/RollupUserLogic.sol#L5)

```solidity
pragma solidity ^0.8.0;
```

- Found in src/rollup/BridgeCreator.sol [Line: 5](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/rollup/BridgeCreator.sol#L5)

```solidity
pragma solidity ^0.8.0;
```

- Found in src/rollup/RollupCreator.sol [Line: 5](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/rollup/RollupCreator.sol#L5)

```solidity
pragma solidity ^0.8.0;
```

</details>

### [N-23] Non-uppercase naming for immutable variables

The contract contains immutable variables that are not named using uppercase or constant-case conventions. Immutable variables should be named in uppercase letters with underscores separating words to increase code readability and indicate their special status. Adhering to this naming convention helps distinguish immutable variables from regular variables, making the code easier to understand and maintain.

<details>
<summary><i>Affected Code Snippets</i></summary>

- Found in src/bridge/SequencerInbox.sol [Line: 120](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/bridge/SequencerInbox.sol#L120)

```solidity
immutable reader4844
```

- Found in src/bridge/SequencerInbox.sol [Line: 132](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/bridge/SequencerInbox.sol#L132)

```solidity
immutable maxDataSize
```

- Found in src/bridge/SequencerInbox.sol [Line: 133](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/bridge/SequencerInbox.sol#L133)

```solidity
immutable deployTimeChainId
```

- Found in src/bridge/SequencerInbox.sol [Line: 135](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/bridge/SequencerInbox.sol#L135)

```solidity
immutable hostChainIsArbitrum
```

- Found in src/bridge/SequencerInbox.sol [Line: 137](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/bridge/SequencerInbox.sol#L137)

```solidity
immutable isUsingFeeToken
```

- Found in src/bridge/SequencerInbox.sol [Line: 139](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/bridge/SequencerInbox.sol#L139)

```solidity
immutable isDelayBufferable
```

- Found in src/assertionStakingPool/AssertionStakingPool.sol [Line: 25](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/assertionStakingPool/AssertionStakingPool.sol#L25)

```solidity
immutable rollup
```

- Found in src/assertionStakingPool/AssertionStakingPool.sol [Line: 27](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/assertionStakingPool/AssertionStakingPool.sol#L27)

```solidity
immutable assertionHash
```

- Found in src/assertionStakingPool/EdgeStakingPool.sol [Line: 29](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/assertionStakingPool/EdgeStakingPool.sol#L29)

```solidity
immutable challengeManager
```

- Found in src/assertionStakingPool/EdgeStakingPool.sol [Line: 31](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/assertionStakingPool/EdgeStakingPool.sol#L31)

```solidity
immutable edgeId
```

- Found in src/assertionStakingPool/AbsBoldStakingPool.sol [Line: 20](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/assertionStakingPool/AbsBoldStakingPool.sol#L20)

```solidity
immutable stakeToken
```

- Found in src/rollup/BOLDUpgradeAction.sol [Line: 124](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/rollup/BOLDUpgradeAction.sol#L124)

```solidity
immutable rollup
```

- Found in src/rollup/BOLDUpgradeAction.sol [Line: 165](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/rollup/BOLDUpgradeAction.sol#L165)

```solidity
immutable pointer
```

- Found in src/rollup/RollupCore.sol [Line: 112](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/rollup/RollupCore.sol#L112)

```solidity
immutable _hostChainIsArbitrum
```

- Found in src/rollup/RollupUserLogic.sol [Line: 31](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/rollup/RollupUserLogic.sol#L31)

```solidity
immutable deployTimeChainId
```

- Found in src/rollup/RollupCreator.sol [Line: 143](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/rollup/RollupCreator.sol#L143)

```solidity
immutable maxDataSize
```

</details>

### [N-24] Consider using named mappings

As of Solidity version 0.8.18, it is possible to use named mappings to clarify the purpose of each mapping in the code. It is recommended to use this feature for code readability and maintainability.

<details>
<summary><i>Affected Code Snippets</i></summary>

- Found in src/bridge/SequencerInbox.sol [Line: 95](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/bridge/SequencerInbox.sol#L95)

```solidity
mapping(address => bool) public isBatchPoster;
```

- Found in src/bridge/SequencerInbox.sol [Line: 119](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/bridge/SequencerInbox.sol#L119)

```solidity
mapping(address => bool) public isSequencer;
```

- Found in src/assertionStakingPool/AbsBoldStakingPool.sol [Line: 22](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/assertionStakingPool/AbsBoldStakingPool.sol#L22)

```solidity
mapping(address => uint256) public depositBalance;
```

- Found in src/rollup/BOLDUpgradeAction.sol [Line: 99](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/rollup/BOLDUpgradeAction.sol#L99)

```solidity
mapping(bytes32 => bytes) internal preImages;
```

- Found in src/rollup/RollupCore.sol [Line: 114](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/rollup/RollupCore.sol#L114)

```solidity
mapping(bytes32 => uint256) internal _assertionCreatedAtArbSysBlock;
```

- Found in src/challengeV2/libraries/EdgeChallengeManagerLib.sol [Line: 76](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/challengeV2/libraries/EdgeChallengeManagerLib.sol#L76)

```solidity
mapping(bytes32 => ChallengeEdge) edges;
```

- Found in src/challengeV2/libraries/EdgeChallengeManagerLib.sol [Line: 81](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/challengeV2/libraries/EdgeChallengeManagerLib.sol#L81)

```solidity
mapping(bytes32 => bytes32) firstRivals;
```

- Found in src/challengeV2/libraries/EdgeChallengeManagerLib.sol [Line: 84](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/challengeV2/libraries/EdgeChallengeManagerLib.sol#L84)

```solidity
mapping(bytes32 => bytes32) confirmedRivals;
```

- Found in src/challengeV2/libraries/EdgeChallengeManagerLib.sol [Line: 86](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/challengeV2/libraries/EdgeChallengeManagerLib.sol#L86)

```solidity
mapping(address => mapping(bytes32 => bool)) hasMadeLayerZeroRival;
```

</details>

### [N-25] Contracts should have full test coverage

Full test coverage for all contracts is recommended. While 100% coverage doesn't guarantee the absence of bugs, it helps catch simple bugs and reduces regressions during code modifications. Achieving full coverage often requires refactoring code into more modular components, each testable separately. This leads to lower interdependencies and results in code that is easier to understand and audit.

### [N-26] `Non-external/public` state variables should begin with an underscore

Non-external/public state variables not beginning with an underscore deviate from the Solidity Style Guide, potentially leading to confusion regarding their visibility and use within the contract. Refactor the state variable names to begin with an underscore, aligning with the Solidity Style Guide and increasing code readability and consistency.

<details>
<summary><i>Affected Code Snippets</i></summary>

- Found in: src/bridge/SequencerInbox.sol [Line: 123](https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/bridge/SequencerInbox.sol#L123)

```solidity
    uint64 internal delayBlocks;
```

- Found in: src/bridge/SequencerInbox.sol [Line: 124](https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/bridge/SequencerInbox.sol#L124)

```solidity
    uint64 internal futureBlocks;
```

- Found in: src/bridge/SequencerInbox.sol [Line: 125](https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/bridge/SequencerInbox.sol#L125)

```solidity
    uint64 internal delaySeconds;
```

- Found in: src/bridge/SequencerInbox.sol [Line: 126](https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/bridge/SequencerInbox.sol#L126)

```solidity
    uint64 internal futureSeconds;
```

- Found in: src/rollup/BOLDUpgradeAction.sol [Line: 99](https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/rollup/BOLDUpgradeAction.sol#L99)

```solidity
    mapping(bytes32 => bytes) internal preImages;
```

- Found in: src/challengeV2/EdgeChallengeManager.sol [Line: 266](https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/challengeV2/EdgeChallengeManager.sol#L266)

```solidity
    EdgeStore internal store;
```

</details>

### [N-27] Non-external functions should be prefixed with an underscore

In Solidity, it's recommended to start the names of functions that aren't meant for external use with an underscore (\_). This naming convention helps prevent confusion about a function's visibility and purpose within a smart contract. By consistently using underscores for internal functions, you'll optimize the readability and maintainability of your codebase.

<details>
<summary><i>Affected Code Snippets</i></summary>

- Found in: src/bridge/DelayBuffer.sol [Line: 68](https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/bridge/DelayBuffer.sol#L68)

```solidity
    function update(BufferData storage self, uint64 blockNumber) internal {
```

- Found in: src/assertionStakingPool/StakingPoolCreatorUtils.sol [Line: 13](https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/assertionStakingPool/StakingPoolCreatorUtils.sol#L13)

```solidity
    function getPool(bytes memory creationCode, bytes memory args) internal view returns (address) {
```

- Found in: src/rollup/Assertion.sol [Line: 85](https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/rollup/Assertion.sol#L85)

```solidity
    function childCreated(AssertionNode storage self) internal {
```

- Found in: src/rollup/AssertionState.sol [Line: 18](https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/rollup/AssertionState.sol#L18)

```solidity
    function toExecutionState(AssertionState memory state) internal pure returns (ExecutionState memory) {
```

- Found in: src/rollup/RollupCreator.sol [Line: 85](https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/rollup/RollupCreator.sol#L85)

```solidity
    function createChallengeManager(address rollupAddr, address proxyAdminAddr, Config memory config)
```

- Found in: src/challengeV2/libraries/EdgeChallengeManagerLib.sol [Line: 141](https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/challengeV2/libraries/EdgeChallengeManagerLib.sol#L141)

```solidity
    function get(EdgeStore storage store, bytes32 edgeId) internal view returns (ChallengeEdge storage) {
```

- Found in: src/challengeV2/libraries/ChallengeEdgeLib.sol [Line: 180](https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/challengeV2/libraries/ChallengeEdgeLib.sol#L180)

```solidity
    function mutualId(ChallengeEdge storage ce) internal view returns (bytes32) {
```

- Found in: src/challengeV2/libraries/ArrayUtilsLib.sol [Line: 13](https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/challengeV2/libraries/ArrayUtilsLib.sol#L13)

```solidity
    function append(bytes32[] memory arr, bytes32 newItem) internal pure returns (bytes32[] memory) {
```

- Found in: src/challengeV2/libraries/MerkleTreeLib.sol [Line: 110](https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/challengeV2/libraries/MerkleTreeLib.sol#L110)

```solidity
    function root(bytes32[] memory me) internal pure returns (bytes32) {
```

- Found in: src/challengeV2/libraries/UintUtilsLib.sol [Line: 14](https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/challengeV2/libraries/UintUtilsLib.sol#L14)

```solidity
    function leastSignificantBit(uint256 x) internal pure returns (uint256 msb) {
```

</details>

### [N-28] Proper use of get as a function name prefix

Clear function names can increase readability. Follow a standard convertion function names such as using get for getter (view/pure) functions.

<details>
<summary><i>Affected Code Snippets</i></summary>

- Found in src/challengeV2/EdgeChallengeManager.sol [Lines: 148-195](https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/challengeV2/EdgeChallengeManager.sol#L148-L195)

````solidity

function calculateMutualId(
uint8 level,
bytes32 originId,
uint256 startHeight,
bytes32 startHistoryRoot,
uint256 endHeight
) external pure returns (bytes32);

function edgeExists(bytes32 edgeId) external view returns (bool);

function getEdge(bytes32 edgeId) external view returns (ChallengeEdge memory);

function edgeLength(bytes32 edgeId) external view returns (uint256);


function hasRival(bytes32 edgeId) external view returns (bool);


function confirmedRival(bytes32 mutualId) external view returns (bytes32);

function hasLengthOneRival(bytes32 edgeId) external view returns (bool);

function timeUnrivaled(bytes32 edgeId) external view returns (uint256);

function getPrevAssertionHash(bytes32 edgeId) external view returns (bytes32);

function firstRival(bytes32 mutualId) external view returns (bytes32);

function hasMadeLayerZeroRival(address account, bytes32 mutualId) external view returns (bool);
}



- Found in src/rollup/RollupCore.sol [Lines: 116-147](https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/rollup/RollupCore.sol#L116-L147)

```solidity
function sequencerInbox() public view virtual returns (ISequencerInbox) {


function getAssertionStorage(bytes32 assertionHash) internal view returns (AssertionNode storage) {


function getAssertion(bytes32 assertionHash) public view override returns (AssertionNode memory) {
}

function getAssertionCreationBlockForLogLookup(bytes32 assertionHash) external view override returns (uint256) {
````

- Found in src/rollup/RollupUserLogic.sol [Lines: 27-57](https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/rollup/RollupUserLogic.sol#L27-L57)

```solidity
function initialize(address _stakeToken) external view override onlyProxy {

uint256 internal immutable deployTimeChainId = block.chainid;

function _chainIdChanged() internal view returns (bool) {


function _validatorIsAfk() internal view returns (bool) {
```

</details>