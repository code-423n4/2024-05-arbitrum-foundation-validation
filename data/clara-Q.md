### Low Risk Issues

| |Issue|Instances|
|-|:-|:-:|
| [[L001](#l001---contracts-are-designed-to-receive-eth-but-do-not-implement-function-for-withdrawal)] | Contracts are designed to receive ETH but do not implement function for withdrawal | 1 |
| [[L002](#l002---functions-calling-contractsaddresses-with-transfer-hooks-are-missing-reentrancy-guards)] | Functions calling contracts/addresses with transfer hooks are missing reentrancy guards | 2 |
| [[L003](#l003---int-casting-blocktimestamp-can-reduce-the-lifespan-of-a-contract)] | Int casting `block.timestamp` can reduce the lifespan of a contract | 1 |
| [[L004](#l004---no-limits-when-setting-state-variable-amounts)] | No limits when setting state variable amounts | 5 |
| [[L005](#l005---pausing-withdrawals-is-unfair-to-the-users)] | Pausing withdrawals is unfair to the users | 1 |
| [[L006](#l006---constructorinitialize-function-lacks-parameter-validation)] | constructor/initialize function lacks parameter validation | 5 |
| [[L007](#l007---for-loops-in-public-or-external-functions-should-be-avoided-due-to-high-gas-costs-and-possible-dos)] | For loops in `public` or `external` functions should be avoided due to high gas costs and possible DOS | 4 |
| [[L008](#l008---external-calls-in-an-unbounded-for-loop-may-result-in-a-dos)] | External calls in an unbounded for-loop may result in a DoS | 4 |
| [[L009](#l009---contracts-are-not-using-their-oz-upgradeable-counterparts)] | Contracts are not using their OZ Upgradeable counterparts | 11 |
| [[L010](#l010---consider-implementing-two-step-procedure-for-updating-protocol-addresses)] | Consider implementing two-step procedure for updating protocol addresses | 2 |
| [[L011](#l011---missing-checks-for-address0x0-in-the-constructor)] | Missing checks for address(0x0) in the constructor | 3 |
| [[L012](#l012---governance-functions-should-be-controlled-by-time-locks)] | Governance functions should be controlled by time locks | 3 |
| [[L013](#l013---code-does-not-follow-the-best-practice-of-check-effects-interaction)] | Code does not follow the best practice of check-effects-interaction | 3 |
| [[L014](#l014---missing-checks-for-address0x0-when-updating-address-state-variables)] | Missing checks for address(0x0) when updating address state variables | 7 |
| [[L015](#l015---the-setter-does-not-set-a-state-variable-or-call-a-fuction)] | The setter does not set a state variable or call a fuction | 2 |
| [[L016](#l016---prefer-continue-over-revert-model-in-iteration)] | Prefer continue over revert model in iteration | 2 |
| [[L017](#l017---abiencodepacked-should-not-be-used-with-dynamic-types-when-passing-the-result-to-a-hash-function-such-as-keccak256)] | `abi.encodePacked()` should not be used with dynamic types when passing the result to a hash function such as `keccak256()` | 10 |
| [[L018](#l018---initializers-could-be-front-run)] | Initializers could be front-run | 2 |
| [[L019](#l019---loss-of-precision-due-to-division-by-large-numbers)] | Loss of precision due to division by large numbers | 1 |
| [[L020](#l020---array-lengths-not-checked)] | Array lengths not checked | 2 |
| [[L021](#l021---require-should-be-used-instead-of-assert)] | `require()` should be used instead of `assert()` | 2 |
| [[L022](#l022---missing-checks-for-address0x0-when-assigning-values-to-address-state-variables)] | Missing checks for `address(0x0)` when assigning values to address state variables | 2 |
| [[L023](#l023---upgradeable-contract-is-missing-a-__gap50-storage-variable-to-allow-for-new-storage-variables-in-later-versions)] | Upgradeable contract is missing a __gap[50] storage variable to allow for new storage variables in later versions | 2 |
| [[L024](#l024---use-ownable2step-rather-than-ownable)] | Use `Ownable2Step` rather than `Ownable` | 2 |
| [[L025](#l025---unsafe-downcast)] | Unsafe downcast | 3 |
| [[L026](#l026---upgradeable-contract-not-initialized)] | Upgradeable contract not initialized | 2 |
| [[L027](#l027---use-of-txorigin-is-unsafe-in-almost-every-context)] | Use of `tx.origin` is unsafe in almost every context | 1 |
| [[L028](#l028---setters-should-have-initial-value-check)] | Setters should have initial value check | 3 |
| [[L029](#l029---empty-receivepayable-fallback-function-does-not-authorize-requests)] | Empty `receive()`/`payable fallback()` function does not authorize requests | 1 |

### Non-critical Issues

| |Issue|Instances|
|-|:-|:-:|
| [[NC001](#nc001---library-declarations-should-have-natspec-title-annotations)] | Library declarations should have Natspec @title annotations | 5 |
| [[NC002](#nc002---library-declarations-should-have-natspec-author-annotations)] | Library declarations should have Natspec @author annotations | 10 |
| [[NC003](#nc003---library-declarations-should-have-natspec-notice-annotations)] | Library declarations should have Natspec @notice annotations | 4 |
| [[NC004](#nc004---library-declarations-should-have-natspec-dev-annotations)] | Library declarations should have Natspec @dev annotations | 10 |
| [[NC005](#nc005---modifier-definitions-should-have-natspec-notice-annotations)] | Modifier definitions should have Natspec @notice annotations | 2 |
| [[NC006](#nc006---modifier-definitions-should-have-natspec-dev-annotations)] | Modifier definitions should have Natspec @dev annotations | 2 |
| [[NC007](#nc007---contract-definitions-should-have-natspec-title-annotations)] | Contract definitions should have Natspec @title annotations | 10 |
| [[NC008](#nc008---contract-definitions-should-have-natspec-author-annotations)] | Contract definitions should have Natspec @author annotations | 12 |
| [[NC009](#nc009---contract-definitions-should-have-natspec-notice-annotations)] | Contract definitions should have Natspec @notice annotations | 5 |
| [[NC010](#nc010---contract-definitions-should-have-natspec-dev-annotations)] | Contract definitions should have Natspec @dev annotations | 11 |
| [[NC011](#nc011---event-definitions-should-have-natspec-notice-annotations)] | Event definitions should have Natspec @notice annotations | 6 |
| [[NC012](#nc012---state-variable-declarations-should-have-natspec-notice-annotations)] | State variable declarations should have Natspec @notice annotations | 13 |
| [[NC013](#nc013---state-variable-declarations-should-have-natspec-dev-annotations)] | State variable declarations should have Natspec @dev annotations | 12 |
| [[NC014](#nc014---functions-should-have-natspec-return-annotations)] | Functions should have Natspec @return annotations | 28 |
| [[NC015](#nc015---functions-should-have-natspec-param-annotations)] | Functions should have Natspec @param annotations | 21 |
| [[NC016](#nc016---missing-events-in-sensitive-functions)] | Missing events in sensitive functions | 1 |
| [[NC017](#nc017---if-statement-control-structures-do-not-comply-with-best-practices)] | If statement control structures do not comply with best practices | 4 |
| [[NC018](#nc018---a-event-should-be-emitted-if-a-non-immutable-state-variable-is-set-in-a-constructor)] | A event should be emitted if a non immutable state variable is set in a constructor | 2 |
| [[NC019](#nc019---public-state-arrays-should-have-a-getter-to-return-all-elements)] | Public state arrays should have a getter to return all elements | 1 |
| [[NC020](#nc020---it-is-best-practice-to-use-linear-inheritance)] | It is best practice to use linear inheritance | 6 |
| [[NC021](#nc021---consider-only-defining-one-libraryinterfacecontract-per-sol-file)] | Consider only defining one library/interface/contract per sol file | 2 |
| [[NC022](#nc022---use-a-struct-to-encapsulate-multiple-function-parameters)] | Use a struct to encapsulate multiple function parameters | 12 |
| [[NC023](#nc023---avoid-defining-a-function-in-a-single-line-including-its-contents)] | Avoid defining a function in a single line including it's contents | 2 |
| [[NC024](#nc024---empty-bytes-check-is-missing)] | Empty bytes check is missing | 4 |
| [[NC025](#nc025---defining-all-externalpublic-functions-in-contract-interfaces)] | Defining All External/Public Functions in Contract Interfaces | 2 |
| [[NC026](#nc026---avoid-declaring-variables-with-the-names-of-defined-functions-within-the-project)] | Avoid declaring variables with the names of defined functions within the project | 1 |
| [[NC027](#nc027---consider-disabling-renounceownership)] | Consider disabling `renounceOwnership()` | 2 |
| [[NC028](#nc028---not-using-the-named-return-variables-anywhere-in-the-function-is-confusing)] | Not using the named return variables anywhere in the function is confusing | 2 |
| [[NC029](#nc029---unused-arguments-in-override-functions)] | Unused arguments in override functions | 2 |
| [[NC030](#nc030---non-libraryinterface-files-should-use-fixed-compiler-versions-not-floating-ones)] | Non-library/interface files should use fixed compiler versions, not floating ones | 12 |
| [[NC031](#nc031---expressions-for-constant-values-such-as-a-call-to-keccak256-should-use-immutable-rather-than-constant)] | Expressions for constant values such as a call to `keccak256()`, should use `immutable` rather than `constant` | 1 |
| [[NC032](#nc032---empty-function-body---consider-commenting-why)] | Empty Function Body - Consider commenting why | 1 |
| [[NC033](#nc033---contracts-should-have-full-test-coverage)] | Contracts should have full test coverage | 1 |
| [[NC034](#nc034---large-or-complicated-code-bases-should-implement-invariant-tests)] | Large or complicated code bases should implement invariant tests | 1 |
| [[NC035](#nc035---long-functions-should-be-refactored-into-multiple-smaller-functions)] | Long functions should be refactored into multiple, smaller, functions | 9 |
| [[NC036](#nc036---consider-using-blocknumber-instead-of-blocktimestamp)] | Consider using `block.number` instead of `block.timestamp` | 1 |
| [[NC037](#nc037---consider-bounding-input-array-length)] | Consider bounding input array length | 1 |
| [[NC038](#nc038---large-numeric-literals-should-use-underscores-for-readability)] | Large numeric literals should use underscores for readability | 3 |
| [[NC039](#nc039---implement-some-type-of-version-counter-that-will-be-incremented-automatically-for-contract-upgrades)] | Implement some type of version counter that will be incremented automatically for contract upgrades | 1 |
| [[NC040](#nc040---cast-to-bytes-or-bytes32-for-clearer-semantic-meaning)] | Cast to `bytes` or `bytes32` for clearer semantic meaning | 1 |
| [[NC041](#nc041---variables-should-be-named-in-mixedcase-style)] | Variables should be named in mixedCase style | 5 |
| [[NC042](#nc042---consider-using-named-mappings)] | Consider using named mappings | 5 |
| [[NC043](#nc043---use-allowlistdenylist-rather-than-whitelistblacklist)] | Use allowlist/denylist rather than whitelist/blacklist | 10 |
| [[NC044](#nc044---function-names-should-use-lowercamelcase)] | Function names should use lowerCamelCase | 1 |
| [[NC045](#nc045---consider-adding-a-deny-list)] | Consider adding a deny-list | 12 |
| [[NC046](#nc046---custom-errors-should-be-used-rather-than-revertrequire)] | Custom errors should be used rather than `revert()`/`require()` | 5 |
| [[NC047](#nc047---pragma-experimental-abiencoderv2-is-deprecated)] | pragma experimental ABIEncoderV2 is deprecated | 1 |
| [[NC048](#nc048---top-level-declarations-should-be-separated-by-two-blank-lines)] | Top level declarations should be separated by two blank lines | 6 |
| [[NC049](#nc049---duplicate-import-statements)] | Duplicate import statements | 1 |
| [[NC050](#nc050---interfaces-should-be-defined-in-separate-files-from-their-usage)] | Interfaces should be defined in separate files from their usage | 2 |
| [[NC051](#nc051---use-a-more-recent-version-of-solidity)] | Use a more recent version of solidity | 4 |
| [[NC052](#nc052---custom-error-has-no-error-details)] | Custom error has no error details | 4 |
| [[NC053](#nc053---overridden-function-has-no-body)] | Overridden function has no body | 1 |
| [[NC054](#nc054---consider-moving-msgsender-checks-to-a-common-authorization-modifier)] | Consider moving `msg.sender` checks to a common authorization `modifier` | 1 |
| [[NC055](#nc055---unused-error-definition)] | Unused `error` definition | 28 |
| [[NC056](#nc056---events-are-missing-sender-information)] | Events are missing sender information | 6 |
| [[NC057](#nc057---spdx-license-identifier-should-be-on-the-first-line)] | SPDX-License-Identifier should be on the first line | 39 |
| [[NC058](#nc058---enum-values-should-be-used-in-place-of-constant-array-indexes)] | Enum values should be used in place of constant array indexes | 3 |
| [[NC059](#nc059---zero-as-a-function-argument-should-have-a-descriptive-meaning)] | Zero as a function argument should have a descriptive meaning | 10 |
| [[NC060](#nc060---function-names-should-differ-to-make-the-code-more-readable)] | Function names should differ to make the code more readable | 261 |
| [[NC061](#nc061---it-is-standard-for-all-external-and-public-functions-to-be-override-from-an-interface)] | It is standard for all external and public functions to be override from an interface | 12 |
| [[NC062](#nc062---consider-adding-formal-verification-proofs)] | Consider adding formal verification proofs | 1 |
| [[NC063](#nc063---public-state-variables-shouldnt-have-a-preceding-_-in-their-name)] | Public state variables shouldn't have a preceding _ in their name | 2 |
| [[NC064](#nc064---large-multiples-of-ten-should-use-scientific-notation-eg-1e6-rather-than-decimal-literals-eg-1000000-for-readability)] | Large multiples of ten should use scientific notation (e.g. 1e6) rather than decimal literals (e.g. 1000000), for readability | 1 |
| [[NC065](#nc065---common-functions-should-be-refactored-to-a-common-base-contract)] | Common functions should be refactored to a common base contract | 10 |
| [[NC066](#nc066---polymorphic-functions-make-security-audits-more-time-consuming-and-error-prone)] | Polymorphic functions make security audits more time-consuming and error-prone | 9 |
| [[NC067](#nc067---error-messages-should-descriptive-rather-that-cryptic)] | Error messages should descriptive, rather that cryptic | 4 |
| [[NC068](#nc068---missing-timelock-for-critical-parameter-change)] | Missing timelock for critical parameter change | 2 |
| [[NC069](#nc069---setters-should-prevent-re-setting-of-the-same-value)] | Setters should prevent re-setting of the same value | 4 |
| [[NC070](#nc070---high-cyclomatic-complexity)] | High cyclomatic complexity | 5 |
| [[NC071](#nc071---use-of-override-is-unnecessary)] | Use of override is unnecessary | 33 |
| [[NC072](#nc072---non-externalpublic-function-names-should-begin-with-an-underscore)] | Non-`external`/`public` function names should begin with an underscore | 4 |
| [[NC073](#nc073---unused-import)] | Unused import | 2 |
| [[NC074](#nc074---use-stringconcat-on-strings-instead-of-abiencodepacked-for-clearer-semantic-meaning)] | Use `string.concat()` on strings instead of `abi.encodePacked()` for clearer semantic meaning | 2 |
| [[NC075](#nc075---unused-function-parameter)] | Unused function parameter | 1 |
| [[NC076](#nc076---put-all-system-wide-constants-in-one-file)] | Put all system-wide constants in one file | 11 |
| [[NC077](#nc077---add-inline-comments-for-unnamed-variables)] | Add inline comments for unnamed variables | 1 |
| [[NC078](#nc078---consider-adding-emergency-stop-functionality)] | Consider adding emergency-stop functionality | 2 |
| [[NC079](#nc079---named-imports-of-parent-contracts-are-missing)] | Named imports of parent contracts are missing | 18 |
| [[NC080](#nc080---unspecific-compiler-version-pragma)] | Unspecific Compiler Version Pragma | 2 |
| [[NC081](#nc081---use-bytesconcat-on-bytes-instead-of-abiencodepacked-for-clearer-semantic-meaning)] | Use `bytes.concat()` on bytes instead of `abi.encodePacked()` for clearer semantic meaning | 4 |
| [[NC082](#nc082---consider-using-safetransferlibsafetransfereth-or-addresssendvalue-for-clearer-semantic-meaning)] | Consider using `SafeTransferLib.safeTransferETH()` or `Address.sendValue()` for clearer semantic meaning | 1 |
| [[NC083](#nc083---style-guide-state-and-local-variables-should-be-named-using-lowercamelcase)] | Style guide: State and local variables should be named using lowerCamelCase | 3 |
| [[NC084](#nc084---unnecessary-cast)] | Unnecessary cast | 4 |
| [[NC085](#nc085---use-the-latest-solidity-prior-to-0820-if-on-l2s-for-deployment)] | Use the latest solidity (prior to 0.8.20 if on L2s) for deployment | 39 |
| [[NC086](#nc086---events-should-use-parameters-to-convey-information)] | Events should use parameters to convey information | 2 |
| [[NC087](#nc087---visibility-should-be-set-explicitly-rather-than-defaulting-to-internal)] | Visibility should be set explicitly rather than defaulting to internal | 1 |
| [[NC088](#nc088---event-declarations-should-have-natspec-param-annotations)] | Event declarations should have NatSpec @param annotations | 8 |
| [[NC089](#nc089---event-declarations-should-have-natspec-dev-annotations)] | Event declarations should have NatSpec @dev annotations | 10 |
| [[NC090](#nc090---function-definitions-should-have-natspec-dev-annotations)] | Function definitions should have NatSpec @dev annotations | 33 |
| [[NC091](#nc091---function-definitions-should-have-natspec-notice-annotations)] | Function definitions should have NatSpec @notice annotations | 26 |
| [[NC092](#nc092---interface-declarations-should-have-natspec-title-annotations)] | Interface declarations should have NatSpec @title annotations | 10 |
| [[NC093](#nc093---interface-declarations-should-have-natspec-author-annotations)] | Interface declarations should have NatSpec @author annotations | 12 |
| [[NC094](#nc094---interface-declarations-should-have-natspec-notice-annotations)] | Interface declarations should have NatSpec @notice annotations | 11 |
| [[NC095](#nc095---interface-declarations-should-have-natspec-dev-annotations)] | Interface declarations should have NatSpec @dev annotations | 12 |
| [[NC096](#nc096---abstract-contract-declarations-should-have-natspec-title-annotations)] | Abstract contract declarations should have NatSpec @title annotations | 2 |
| [[NC097](#nc097---abstract-contract-declarations-should-have-natspec-author-annotations)] | Abstract contract declarations should have NatSpec @author annotations | 2 |
| [[NC098](#nc098---abstract-contract-declarations-should-have-natspec-notice-annotations)] | Abstract contract declarations should have NatSpec @notice annotations | 1 |
| [[NC099](#nc099---abstract-contract-declarations-should-have-natspec-dev-annotations)] | Abstract contract declarations should have Natspec @dev annotations | 1 |
| [[NC100](#nc100---todo-left-in-the-code)] | TODO Left in the code | 1 |
| [[NC101](#nc101---constants-should-be-defined-rather-than-using-magic-numbers)] | Constants should be defined rather than using magic numbers | 6 |
| [[NC102](#nc102---event-is-not-properly-indexed)] | Event is not properly indexed | 1 |
| [[NC103](#nc103---function-ordering-does-not-follow-the-solidity-style-guide)] | Function ordering does not follow the Solidity style guide | 11 |
| [[NC104](#nc104---imports-could-be-organized-more-systematically)] | Imports could be organized more systematically | 19 |
| [[NC105](#nc105---constants-in-comparisons-should-appear-on-the-left-side)] | Constants in comparisons should appear on the left side | 15 |
| [[NC106](#nc106---else-block-not-required)] | else-block not required | 6 |
| [[NC107](#nc107---events-may-be-emitted-out-of-order-due-to-reentrancy)] | Events may be emitted out of order due to reentrancy | 4 |
| [[NC108](#nc108---if-statement-can-be-converted-to-a-ternary)] | If-statement can be converted to a ternary | 3 |
| [[NC109](#nc109---import-declarations-should-import-specific-identifiers-rather-than-the-whole-file)] | Import declarations should import specific identifiers, rather than the whole file | 10 |
| [[NC110](#nc110---public-functions-not-called-by-the-contract-should-be-declared-external-instead)] | Public functions not called by the contract should be declared external instead | 4 |
| [[NC111](#nc111---constant-redefined-elsewhere)] | Constant redefined elsewhere | 1 |
| [[NC112](#nc112---multiple-addressid-mappings-can-be-combined-into-a-single-mapping-of-an-addressid-to-a-struct-for-readability)] | Multiple `address`/ID mappings can be combined into a single `mapping` of an `address`/ID to a `struct`, for readability | 2 |
| [[NC113](#nc113---duplicated-requirerevert-checks-should-be-refactored-to-a-modifier-or-function)] | Duplicated `require()`/`revert()` checks should be refactored to a modifier or function | 2 |
| [[NC114](#nc114---variables-need-not-be-initialized-to-zero)] | Variables need not be initialized to zero | 6 |
| [[NC115](#nc115---use-a-more-recent-version-of-solidity)] | Use a more recent version of solidity | 10 |
| [[NC116](#nc116---variable-names-that-consist-of-all-capital-letters-should-be-reserved-for-constantimmutable-variables)] | Variable names that consist of all capital letters should be reserved for constant/immutable variables | 2 |
| [[NC117](#nc117---consider-using-delete-rather-than-assigning-falsezero-to-clear-values)] | Consider using delete rather than assigning false/zero to clear values | 3 |
| [[NC118](#nc118---variable-names-for-immutables-should-use-constant_case)] | Variable names for `immutable`s should use CONSTANT_CASE | 7 |
| [[NC119](#nc119---lines-are-too-long)] | Lines are too long | 102 |
| [[NC120](#nc120---file-is-missing-natspec-comments)] | File is missing NatSpec comments | 7 |
| [[NC121](#nc121---function-declarations-should-have-natspec-descriptions)] | Function declarations should have NatSpec descriptions | 22 |
| [[NC122](#nc122---contract-declarations-should-have-notice-tags)] | Contract declarations should have `@notice` tags | 24 |
| [[NC123](#nc123---error-declarations-should-have-natspec-descriptions)] | Error declarations should have NatSpec descriptions | 1 |
| [[NC124](#nc0124---contract-does-not-follow-the-solidity-style-guides-suggested-layout-ordering)] | Contract does not follow the Solidity style guide's suggested layout ordering | 4 |
| [[NC125](#nc125---non-externalpublic-variable-names-should-begin-with-an-underscore)] | Non-external/public variable names should begin with an underscore | 4 |



Total: Low 90 instances over 29 issues


## L001 - Contracts are designed to receive ETH but do not implement function for withdrawal:

The following contracts can receive ETH but can not withdraw, ETH is occasionally sent by users will be stuck in those contracts. This functionality also applies to baseTokens resulting in locked tokens and loss of funds.


```solidity
File: src/rollup/RollupCreator.sol


61          receive() external payable {}


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/rollup/RollupCreator.sol#L0:0

## L002 - Functions calling contracts/addresses with transfer hooks are missing reentrancy guards:

Even if the function follows the best practice of check-effects-interaction, not using a reentrancy guard when there may be transfer hooks to unknown or untrusted ERC20 tokens will open the users of this protocol up to [read-only reentrancies](https://chainsecurity.com/curve-lp-oracle-manipulation-post-mortem/) with no way to protect against it, except by block-listing the whole protocol.


```solidity
File: src/assertionStakingPool/AbsBoldStakingPool.sol


51              IERC20(stakeToken).safeTransfer(msg.sender, amount);
35              IERC20(stakeToken).safeTransferFrom(msg.sender, address(this), amount);


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/assertionStakingPool/AbsBoldStakingPool.sol#L0:0

```solidity
File: src/rollup/RollupUserLogic.sol


215                 IERC20(stakeToken).safeTransfer(loserStakeEscrow, assertion.beforeStateData.configData.requiredStake);
362             IERC20(stakeToken).safeTransfer(msg.sender, amount);
295                     IERC20(stakeToken).safeTransfer(loserStakeEscrow, assertion.beforeStateData.configData.requiredStake);


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/rollup/RollupUserLogic.sol#L0:0

## L003 - Int casting `block.timestamp` can reduce the lifespan of a contract:

Consider removing casting to ensure future functionality.


```solidity
File: src/bridge/SequencerInbox.sol


225                 bounds.minTimestamp = uint64(block.timestamp) - delaySeconds_;
227             bounds.maxTimestamp = uint64(block.timestamp) + futureSeconds_;


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/bridge/SequencerInbox.sol#L0:0

## L004 - No limits when setting state variable amounts:

It is important to ensure state variables numbers are set to a reasonable value.


<details>
<summary>Click to show 5 findings</summary>

```solidity
File: src/bridge/SequencerInbox.sol


146             maxDataSize = _maxDataSize;
878             delayBlocks = uint64(maxTimeVariation_.delayBlocks);
879             futureBlocks = uint64(maxTimeVariation_.futureBlocks);
880             delaySeconds = uint64(maxTimeVariation_.delaySeconds);
881             futureSeconds = uint64(maxTimeVariation_.futureSeconds);


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/bridge/SequencerInbox.sol#L0:0

```solidity
File: src/challengeV2/EdgeChallengeManager.sol


339             LAYERZERO_BLOCKEDGE_HEIGHT = layerZeroBlockEdgeHeight;
343             LAYERZERO_BIGSTEPEDGE_HEIGHT = layerZeroBigStepEdgeHeight;
347             LAYERZERO_SMALLSTEPEDGE_HEIGHT = layerZeroSmallStepEdgeHeight;


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/challengeV2/EdgeChallengeManager.sol#L0:0

```solidity
File: src/challengeV2/libraries/EdgeChallengeManagerLib.sol


510                 store.edges[edgeId].totalTimeUnrivaledCache = uint64(newValue);


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/challengeV2/libraries/EdgeChallengeManagerLib.sol#L0:0

```solidity
File: src/rollup/RollupAdminLogic.sol


205             minimumAssertionPeriod = newPeriod;
224             baseStake = newBaseStake;


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/rollup/RollupAdminLogic.sol#L0:0

```solidity
File: src/rollup/RollupCore.sol


360             _stakerMap[_stakerList[stakerIndex]].index = stakerIndex;


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/rollup/RollupCore.sol#L0:0

</details>

## L005 - Pausing withdrawals is unfair to the users:

Users should always have the possibility of accessing their own funds, but when these functions are paused, their funds will be locked until the contracts are unpaused.


```solidity
File: src/rollup/RollupUserLogic.sol


358         function withdrawStakerFunds() external override whenNotPaused returns (uint256) {


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/rollup/RollupUserLogic.sol#L0:0

## L006 - constructor/initialize function lacks parameter validation:

In Solidity, when values are being assigned in constructors to unsigned or integer variables, it's crucial to ensure the provided values adhere to the protocol's specific operational boundaries as laid out in the project specifications and documentation. If the constructors lack appropriate validation checks, there's a risk of setting state variables with values that could cause unexpected and potentially detrimental behavior within the contract's operations, violating the intended logic of the protocol. This can compromise the contract's security and impact the maintainability and reliability of the system. In order to avoid such issues, it is recommended to incorporate rigorous validation checks in constructors. These checks should align with the project's defined rules and constraints, making use of Solidity's built-in require function to enforce these conditions. If the validation checks fail, the require function will cause the transaction to revert, ensuring the integrity and adherence to the protocol's expected behavior.


<details>
<summary>Click to show 5 findings</summary>

```solidity
File: src/assertionStakingPool/AbsBoldStakingPool.sol


24          constructor(address _stakeToken) {
25              stakeToken = _stakeToken;
26          }


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/assertionStakingPool/AbsBoldStakingPool.sol#L0:0

```solidity
File: src/assertionStakingPool/AssertionStakingPool.sol


31          constructor(
32              address _rollup,
33              bytes32 _assertionHash
34          ) AbsBoldStakingPool(IRollupCore(_rollup).stakeToken()) {
35              rollup = _rollup;
36              assertionHash = _assertionHash;
37          }


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/assertionStakingPool/AssertionStakingPool.sol#L0:0

```solidity
File: src/assertionStakingPool/EdgeStakingPool.sol


35          constructor(
36              address _challengeManager,
37              bytes32 _edgeId
38          ) AbsBoldStakingPool(address(EdgeChallengeManager(_challengeManager).stakeToken())) {
39              challengeManager = _challengeManager;
40              edgeId = _edgeId;
41          }


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/assertionStakingPool/EdgeStakingPool.sol#L0:0

```solidity
File: src/rollup/BOLDUpgradeAction.sol


126         constructor(IOldRollup _rollup) {
127             rollup = _rollup;
128         }
169         constructor(uint256[] memory __array) {
170             _array = __array;
171         }
287         constructor(
288             Contracts memory contracts,
289             ProxyAdmins memory proxyAdmins,
290             Implementations memory implementations,
291             Settings memory settings
292         ) {
293             L1_TIMELOCK = contracts.l1Timelock;
294             OLD_ROLLUP = contracts.rollup;
295             BRIDGE = contracts.bridge;
296             SEQ_INBOX = contracts.sequencerInbox;
297             REI = contracts.rollupEventInbox;
298             OUTBOX = contracts.outbox;
299             INBOX = contracts.inbox;
300             OSP = contracts.osp;
301     
302             PROXY_ADMIN_OUTBOX = ProxyAdmin(proxyAdmins.outbox);
303             PROXY_ADMIN_BRIDGE = ProxyAdmin(proxyAdmins.bridge);
304             PROXY_ADMIN_REI = ProxyAdmin(proxyAdmins.rei);
305             PROXY_ADMIN_SEQUENCER_INBOX = ProxyAdmin(proxyAdmins.seqInbox);
306             PROXY_ADMIN_INBOX = ProxyAdmin(proxyAdmins.inbox);
307             PREIMAGE_LOOKUP = new StateHashPreImageLookup();
308             ROLLUP_READER = new RollupReader(contracts.rollup);
309     
310             IMPL_BRIDGE = implementations.bridge;
311             IMPL_SEQUENCER_INBOX = implementations.seqInbox;
312             IMPL_INBOX = implementations.inbox;
313             IMPL_REI = implementations.rei;
314             IMPL_OUTBOX = implementations.outbox;
315             IMPL_PATCHED_OLD_ROLLUP_USER = implementations.oldRollupUser;
316             IMPL_NEW_ROLLUP_USER = implementations.newRollupUser;
317             IMPL_NEW_ROLLUP_ADMIN = implementations.newRollupAdmin;
318             IMPL_CHALLENGE_MANAGER = implementations.challengeManager;
319     
320             CHAIN_ID = settings.chainId;
321             CONFIRM_PERIOD_BLOCKS = settings.confirmPeriodBlocks;
322             CHALLENGE_PERIOD_BLOCKS = settings.challengePeriodBlocks;
323             STAKE_TOKEN = settings.stakeToken;
324             STAKE_AMOUNT = settings.stakeAmt;
325             MINI_STAKE_AMOUNTS_STORAGE = address(new ConstantArrayStorage(settings.miniStakeAmounts));
326             ANY_TRUST_FAST_CONFIRMER = settings.anyTrustFastConfirmer;
327             DISABLE_VALIDATOR_WHITELIST = settings.disableValidatorWhitelist;
328             BLOCK_LEAF_SIZE = settings.blockLeafSize;
329             BIGSTEP_LEAF_SIZE = settings.bigStepLeafSize;
330             SMALLSTEP_LEAF_SIZE = settings.smallStepLeafSize;
331             NUM_BIGSTEP_LEVEL = settings.numBigStepLevel;
332             CHALLENGE_GRACE_PERIOD_BLOCKS = settings.challengeGracePeriodBlocks;
333             IS_DELAY_BUFFERABLE = settings.isDelayBufferable;
334             MAX = settings.bufferConfig.max;
335             THRESHOLD = settings.bufferConfig.threshold;
336             REPLENISH_RATE_IN_BASIS = settings.bufferConfig.replenishRateInBasis;
337         }


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/rollup/BOLDUpgradeAction.sol#L0:0

```solidity
File: src/rollup/BridgeCreator.sol


45          constructor(
46              BridgeTemplates memory _ethBasedTemplates,
47              BridgeTemplates memory _erc20BasedTemplates
48          ) Ownable() {
49              ethBasedTemplates = _ethBasedTemplates;
50              erc20BasedTemplates = _erc20BasedTemplates;
51          }


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/rollup/BridgeCreator.sol#L0:0

</details>

## L007 - For loops in `public` or `external` functions should be avoided due to high gas costs and possible DOS:

In Solidity, for loops can potentially cause Denial of Service (DoS) attacks if not handled carefully. DoS attacks can occur when an attacker intentionally exploits the gas cost of a function, causing it to run out of gas or making it too expensive for other users to call. Below are some scenarios where for loops can lead to DoS attacks: Nested for loops can become exceptionally gas expensive and should be used sparingly.


<details>
<summary>Click to show 4 findings</summary>

```solidity
File: src/challengeV2/EdgeChallengeManager.sol


491         function multiUpdateTimeCacheByChildren(bytes32[] calldata edgeIds) public {
492             for (uint256 i = 0; i < edgeIds.length; i++) {
493                 (bool updated, uint256 newValue) = store.updateTimerCacheByChildren(edgeIds[i]);
494                 if (updated) emit TimerCacheUpdated(edgeIds[i], newValue);
495             }
496         }


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/challengeV2/EdgeChallengeManager.sol#L0:0

```solidity
File: src/rollup/BOLDUpgradeAction.sol


464         function perform(address[] memory validators) external {
465             // tidy up the old rollup - pause it and refund stakes
466             cleanupOldRollup();
467     
468             // create the config, we do this now so that we compute the expected rollup address
469             Config memory config = createConfig();
470     
471             // deploy the new challenge manager
472             IEdgeChallengeManager challengeManager = IEdgeChallengeManager(
473                 address(
474                     new TransparentUpgradeableProxy(
475                         address(IMPL_CHALLENGE_MANAGER),
476                         address(PROXY_ADMIN_BRIDGE), // use the same proxy admin as the bridge
477                         ""
478                     )
479                 )
480             );
481     
482             // now that all the dependent contracts are pointed at the new address we can
483             // deploy and init the new rollup
484             ContractDependencies memory connectedContracts = ContractDependencies({
485                 bridge: IBridge(BRIDGE),
486                 sequencerInbox: ISequencerInbox(SEQ_INBOX),
487                 inbox: IInboxBase(INBOX),
488                 outbox: IOutbox(OUTBOX),
489                 rollupEventInbox: IRollupEventInbox(REI),
490                 challengeManager: challengeManager,
491                 rollupAdminLogic: IMPL_NEW_ROLLUP_ADMIN,
492                 rollupUserLogic: IRollupUser(IMPL_NEW_ROLLUP_USER),
493                 validatorWalletCreator: ROLLUP_READER.validatorWalletCreator()
494             });
495     
496             // upgrade the surrounding contracts eg bridge, outbox, seq inbox, rollup event inbox
497             // to set of the new rollup address
498             bytes32 rollupSalt = keccak256(abi.encode(config));
499             address expectedRollupAddress =
500                 Create2Upgradeable.computeAddress(rollupSalt, keccak256(type(RollupProxy).creationCode));
501             upgradeSurroundingContracts(expectedRollupAddress);
502     
503             challengeManager.initialize({
504                 _assertionChain: IAssertionChain(expectedRollupAddress),
505                 _challengePeriodBlocks: CHALLENGE_PERIOD_BLOCKS,
506                 _oneStepProofEntry: OSP,
507                 layerZeroBlockEdgeHeight: config.layerZeroBlockEdgeHeight,
508                 layerZeroBigStepEdgeHeight: config.layerZeroBigStepEdgeHeight,
509                 layerZeroSmallStepEdgeHeight: config.layerZeroSmallStepEdgeHeight,
510                 _stakeToken: IERC20(config.stakeToken),
511                 _stakeAmounts: config.miniStakeValues,
512                 _excessStakeReceiver: L1_TIMELOCK,
513                 _numBigStepLevel: config.numBigStepLevel
514             });
515     
516             RollupProxy rollup = new RollupProxy{salt: rollupSalt}();
517             require(address(rollup) == expectedRollupAddress, "UNEXPCTED_ROLLUP_ADDR");
518     
519             // initialize the rollup with this contract as owner to set batch poster and validators
520             // it will transfer the ownership back to the actual owner later
521             address actualOwner = config.owner;
522             config.owner = address(this);
523     
524             rollup.initializeProxy(config, connectedContracts);
525     
526             if (validators.length != 0) {
527                 bool[] memory _vals = new bool[](validators.length);
528                 for (uint256 i = 0; i < validators.length; i++) {
529                     require(ROLLUP_READER.isValidator(validators[i]), "UNEXPECTED_NEW_VALIDATOR");
530                     _vals[i] = true;
531                 }
532                 IRollupAdmin(address(rollup)).setValidator(validators, _vals);
533             }
534             if (DISABLE_VALIDATOR_WHITELIST) {
535                 IRollupAdmin(address(rollup)).setValidatorWhitelistDisabled(DISABLE_VALIDATOR_WHITELIST);
536             }
537     
538             IRollupAdmin(address(rollup)).setOwner(actualOwner);
539     
540             emit RollupMigrated(expectedRollupAddress, address(challengeManager));
541         }


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/rollup/BOLDUpgradeAction.sol#L0:0

```solidity
File: src/rollup/RollupAdminLogic.sol


180         function setValidator(address[] calldata _validator, bool[] calldata _val) external override {
181             require(_validator.length > 0, "EMPTY_ARRAY");
182             require(_validator.length == _val.length, "WRONG_LENGTH");
183     
184             for (uint256 i = 0; i < _validator.length; i++) {
185                 isValidator[_validator[i]] = _val[i];
186             }
187             emit OwnerFunctionCalled(6);
188         }
228         function forceRefundStaker(address[] calldata staker) external override whenPaused {
229             require(staker.length > 0, "EMPTY_ARRAY");
230             for (uint256 i = 0; i < staker.length; i++) {
231                 requireInactiveStaker(staker[i]);
232                 reduceStakeTo(staker[i], 0);
233             }
234             emit OwnerFunctionCalled(22);
235         }


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/rollup/RollupAdminLogic.sol#L0:0

```solidity
File: src/rollup/RollupCreator.sol


137         function createRollup(RollupDeploymentParams memory deployParams)
138             public
139             payable
140             returns (address)
141         {
142             {
143                 // Make sure the immutable maxDataSize is as expected
144                 (
145                     ,
146                     ISequencerInbox ethSequencerInbox,
147                     ISequencerInbox ethDelayBufferableSequencerInbox,
148                     IInboxBase ethInbox,
149                     ,
150     
151                 ) = bridgeCreator.ethBasedTemplates();
152                 require(
153                     deployParams.maxDataSize == ethSequencerInbox.maxDataSize(),
154                     "SI_MAX_DATA_SIZE_MISMATCH"
155                 );
156                 require(
157                     deployParams.maxDataSize == ethDelayBufferableSequencerInbox.maxDataSize(),
158                     "SI_MAX_DATA_SIZE_MISMATCH"
159                 );
160                 require(deployParams.maxDataSize == ethInbox.maxDataSize(), "I_MAX_DATA_SIZE_MISMATCH");
161     
162                 (
163                     ,
164                     ISequencerInbox erc20SequencerInbox,
165                     ISequencerInbox erc20DelayBufferableSequencerInbox,
166                     IInboxBase erc20Inbox,
167                     ,
168     
169                 ) = bridgeCreator.erc20BasedTemplates();
170                 require(
171                     deployParams.maxDataSize == erc20SequencerInbox.maxDataSize(),
172                     "SI_MAX_DATA_SIZE_MISMATCH"
173                 );
174                 require(
175                     deployParams.maxDataSize == erc20DelayBufferableSequencerInbox.maxDataSize(),
176                     "SI_MAX_DATA_SIZE_MISMATCH"
177                 );
178                 require(
179                     deployParams.maxDataSize == erc20Inbox.maxDataSize(),
180                     "I_MAX_DATA_SIZE_MISMATCH"
181                 );
182             }
183     
184             // create proxy admin which will manage bridge contracts
185             ProxyAdmin proxyAdmin = new ProxyAdmin();
186     
187             // Create the rollup proxy to figure out the address and initialize it later
188             RollupProxy rollup = new RollupProxy{salt: keccak256(abi.encode(deployParams))}();
189     
190             BridgeCreator.BridgeContracts memory bridgeContracts = bridgeCreator.createBridge(
191                 address(proxyAdmin),
192                 address(rollup),
193                 deployParams.nativeToken,
194                 deployParams.config.sequencerInboxMaxTimeVariation,
195                 deployParams.config.bufferConfig
196             );
197     
198             IEdgeChallengeManager challengeManager = createChallengeManager(address(rollup), address(proxyAdmin), deployParams.config);
199     
200             // deploy and init upgrade executor
201             address upgradeExecutor = _deployUpgradeExecutor(deployParams.config.owner, proxyAdmin);
202     
203             // upgradeExecutor shall be proxyAdmin's owner
204             proxyAdmin.transferOwnership(address(upgradeExecutor));
205     
206             // initialize the rollup with this contract as owner to set batch poster and validators
207             // it will transfer the ownership to the upgrade executor later
208             deployParams.config.owner = address(this);
209             rollup.initializeProxy(
210                 deployParams.config,
211                 ContractDependencies({
212                     bridge: bridgeContracts.bridge,
213                     sequencerInbox: bridgeContracts.sequencerInbox,
214                     inbox: bridgeContracts.inbox,
215                     outbox: bridgeContracts.outbox,
216                     rollupEventInbox: bridgeContracts.rollupEventInbox,
217                     challengeManager: challengeManager,
218                     rollupAdminLogic: address(rollupAdminLogic),
219                     rollupUserLogic: rollupUserLogic,
220                     validatorWalletCreator: validatorWalletCreator
221                 })
222             );
223     
224             // Setting batch posters and batch poster manager
225             for (uint256 i = 0; i < deployParams.batchPosters.length; i++) {
226                 bridgeContracts.sequencerInbox.setIsBatchPoster(deployParams.batchPosters[i], true);
227             }
228             if (deployParams.batchPosterManager != address(0)) {
229                 bridgeContracts.sequencerInbox.setBatchPosterManager(deployParams.batchPosterManager);
230             }
231     
232             // Call setValidator on the newly created rollup contract just if validator set is not empty
233             if (deployParams.validators.length != 0) {
234                 bool[] memory _vals = new bool[](deployParams.validators.length);
235                 for (uint256 i = 0; i < deployParams.validators.length; i++) {
236                     _vals[i] = true;
237                 }
238                 IRollupAdmin(address(rollup)).setValidator(deployParams.validators, _vals);
239             }
240     
241             IRollupAdmin(address(rollup)).setOwner(address(upgradeExecutor));
242     
243             if (deployParams.deployFactoriesToL2) {
244                 _deployFactories(
245                     address(bridgeContracts.inbox),
246                     deployParams.nativeToken,
247                     deployParams.maxFeePerGasForRetryables
248                 );
249             }
250     
251             emit RollupCreated(
252                 address(rollup),
253                 deployParams.nativeToken,
254                 address(bridgeContracts.inbox),
255                 address(bridgeContracts.outbox),
256                 address(bridgeContracts.rollupEventInbox),
257                 address(challengeManager),
258                 address(proxyAdmin),
259                 address(bridgeContracts.sequencerInbox),
260                 address(bridgeContracts.bridge),
261                 address(upgradeExecutor),
262                 address(validatorWalletCreator)
263             );
264             return address(rollup);
265         }


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/rollup/RollupCreator.sol#L0:0

</details>

## L008 - External calls in an unbounded for-loop may result in a DoS:

Consider limiting the number of iterations in for-loops that make external calls.


<details>
<summary>Click to show 4 findings</summary>

```solidity
File: src/challengeV2/EdgeChallengeManager.sol


492             for (uint256 i = 0; i < edgeIds.length; i++) {


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/challengeV2/EdgeChallengeManager.sol#L0:0

```solidity
File: src/challengeV2/libraries/MerkleTreeLib.sol


115             for (uint256 i = 0; i < me.length; i++) {
188             for (uint256 i = 0; i < me.length; i++) {


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/challengeV2/libraries/MerkleTreeLib.sol#L0:0

```solidity
File: src/rollup/BOLDUpgradeAction.sol


528                 for (uint256 i = 0; i < validators.length; i++) {


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/rollup/BOLDUpgradeAction.sol#L0:0

```solidity
File: src/rollup/RollupAdminLogic.sol


230             for (uint256 i = 0; i < staker.length; i++) {


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/rollup/RollupAdminLogic.sol#L0:0

</details>

## L009 - Contracts are not using their OZ Upgradeable counterparts:

The non-upgradeable standard version of OpenZeppelin’s library is inherited/used by the contracts. It would be safer to use the upgradeable versions of the library contracts to avoid unexpected behavior.

Use the contracts from `@openzeppelin/contracts-upgradeable` instead of `@openzeppelin/contracts` where applicable. See https://github.com/OpenZeppelin/openzeppelin-contracts-upgradeable/tree/master/contracts for a list of available upgradeable contracts


<details>
<summary>Click to show 11 findings</summary>

```solidity
File: src/assertionStakingPool/AbsBoldStakingPool.sol


8       import {SafeERC20} from "cool/node_modules/@openzeppelin/contracts/token/ERC20/utils/SafeERC20.sol";
7       import {IERC20} from "cool/node_modules/@openzeppelin/contracts/token/ERC20/IERC20.sol";


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/assertionStakingPool/AbsBoldStakingPool.sol#L0:0

```solidity
File: src/assertionStakingPool/AssertionStakingPool.sol


8       import "cool/node_modules/@openzeppelin/contracts/token/ERC20/IERC20.sol";


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/assertionStakingPool/AssertionStakingPool.sol#L0:0

```solidity
File: src/assertionStakingPool/EdgeStakingPool.sol


12      import "cool/node_modules/@openzeppelin/contracts/token/ERC20/utils/SafeERC20.sol";
11      import "cool/node_modules/@openzeppelin/contracts/token/ERC20/IERC20.sol";


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/assertionStakingPool/EdgeStakingPool.sol#L0:0

```solidity
File: src/assertionStakingPool/StakingPoolCreatorUtils.sol


8       import "cool/node_modules/@openzeppelin/contracts/utils/Create2.sol";
9       import "cool/node_modules/@openzeppelin/contracts/utils/Address.sol";


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/assertionStakingPool/StakingPoolCreatorUtils.sol#L0:0

```solidity
File: src/challengeV2/EdgeChallengeManager.sol


14      import "cool/node_modules/@openzeppelin/contracts-upgradeable/proxy/utils/Initializable.sol";
15      import "cool/node_modules/@openzeppelin/contracts/token/ERC20/utils/SafeERC20.sol";


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/challengeV2/EdgeChallengeManager.sol#L0:0

```solidity
File: src/rollup/BOLDUpgradeAction.sol


8       import "cool/node_modules/@openzeppelin/contracts/proxy/transparent/ProxyAdmin.sol";
7       import "cool/node_modules/@openzeppelin/contracts-upgradeable/utils/Create2Upgradeable.sol";


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/rollup/BOLDUpgradeAction.sol#L0:0

```solidity
File: src/rollup/BridgeCreator.sol


19      import "cool/node_modules/@openzeppelin/contracts/proxy/transparent/ProxyAdmin.sol";
18      import "cool/node_modules/@openzeppelin/contracts/access/Ownable.sol";


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/rollup/BridgeCreator.sol#L0:0

```solidity
File: src/rollup/RollupAdminLogic.sol


13      import "cool/node_modules/@openzeppelin/contracts/proxy/beacon/UpgradeableBeacon.sol";


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/rollup/RollupAdminLogic.sol#L0:0

```solidity
File: src/rollup/RollupCore.sol


7       import "cool/node_modules/@openzeppelin/contracts-upgradeable/security/PausableUpgradeable.sol";


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/rollup/RollupCore.sol#L0:0

```solidity
File: src/rollup/RollupCreator.sol


15      import {SafeERC20, IERC20} from "cool/node_modules/@openzeppelin/contracts/token/ERC20/utils/SafeERC20.sol";
12      import "cool/node_modules/@openzeppelin/contracts/proxy/transparent/TransparentUpgradeableProxy.sol";
11      import "cool/node_modules/@openzeppelin/contracts/proxy/transparent/ProxyAdmin.sol";
13      import "cool/node_modules/@openzeppelin/contracts/access/Ownable.sol";


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/rollup/RollupCreator.sol#L0:0

```solidity
File: src/rollup/RollupUserLogic.sol


7       import "cool/node_modules/@openzeppelin/contracts/token/ERC20/IERC20.sol";


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/rollup/RollupUserLogic.sol#L0:0

</details>

## L010 - Consider implementing two-step procedure for updating protocol addresses:

Lack of two-step procedure for critical operations leaves them error-prone. Consider adding two step procedure on the critical functions. See similar findings in previous Code4rena contests for reference: https://code4rena.com/reports/2022-06-illuminate/#2-critical-changes-should-use-two-step-procedure


```solidity
File: src/bridge/SequencerInbox.sol


894         function setIsBatchPoster(address addr, bool isBatchPoster_)
933         function setIsSequencer(address addr, bool isSequencer_)
942         function setBatchPosterManager(address newBatchPosterManager) external onlyRollupOwner {


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/bridge/SequencerInbox.sol#L0:0

```solidity
File: src/rollup/RollupCreator.sol


63          function setTemplates(


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/rollup/RollupCreator.sol#L0:0

## L011 - Missing checks for address(0x0) in the constructor:

  


```solidity
File: src/assertionStakingPool/AbsBoldStakingPool.sol


25              stakeToken = _stakeToken;


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/assertionStakingPool/AbsBoldStakingPool.sol#L0:0

```solidity
File: src/assertionStakingPool/AssertionStakingPool.sol


35              rollup = _rollup;


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/assertionStakingPool/AssertionStakingPool.sol#L0:0

```solidity
File: src/assertionStakingPool/EdgeStakingPool.sol


39              challengeManager = _challengeManager;


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/assertionStakingPool/EdgeStakingPool.sol#L0:0

## L012 - Governance functions should be controlled by time locks:

Governance functions (such as upgrading contracts, setting critical parameters) should be controlled using time locks to introduce a delay between a proposal and its execution. This gives users time to exit before a potentially dangerous or malicious operation is applied.


```solidity
File: src/rollup/BridgeCreator.sol


53          function updateTemplates(BridgeTemplates calldata _newTemplates) external onlyOwner {

58          function updateERC20Templates(BridgeTemplates calldata _newTemplates) external onlyOwner {

```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/rollup/BridgeCreator.sol#L58:61

```solidity
File: src/rollup/RollupCreator.sol


63          function setTemplates(
64              BridgeCreator _bridgeCreator,
65              IOneStepProofEntry _osp,
66              IEdgeChallengeManager _challengeManagerLogic,
67              IRollupAdmin _rollupAdminLogic,
68              IRollupUser _rollupUserLogic,
69              IUpgradeExecutor _upgradeExecutorLogic,
70              address _validatorWalletCreator,
71              DeployHelper _l2FactoriesDeployer
72          ) external onlyOwner {

```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/rollup/RollupCreator.sol#L63:82

## L013 - Code does not follow the best practice of check-effects-interaction:

Code should follow the best-practice of [check-effects-interaction](https://blockchain-academy.hs-mittweida.de/courses/solidity-coding-beginners-to-intermediate/lessons/solidity-11-coding-patterns/topic/checks-effects-interactions/), where state variables are updated before any external calls are made. Doing so prevents a large class of reentrancy bugs.


```solidity
File: src/bridge/SequencerInbox.sol


/// @audit formBlobDataHash() called prior to this assignment
/// @audit contains nested function call bytes.concat() 
/// @audit located in file cool/src/bridge/SequencerInbox.sol  
816             totalDelayedMessagesRead = afterDelayedMessagesRead;


/// @audit formCallDataHash() called prior to this assignment
/// @audit contains nested function call bytes.concat() 
/// @audit located in file cool/src/bridge/SequencerInbox.sol  
816             totalDelayedMessagesRead = afterDelayedMessagesRead;


/// @audit bytes.concat() called prior to this assignment
913             dasKeySetInfo[ksHash] = DasKeySetInfo({
914                 isValidKeyset: true,
915                 creationBlock: uint64(creationBlock)
916             });


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/bridge/SequencerInbox.sol#L913:916

## L014 - Missing checks for address(0x0) when updating address state variables:

issing checks for address(0x0) when updating address state variables


<details>
<summary>Click to show 7 findings</summary>

```solidity
File: src/assertionStakingPool/AbsBoldStakingPool.sol


25              stakeToken = _stakeToken;


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/assertionStakingPool/AbsBoldStakingPool.sol#L0:0

```solidity
File: src/assertionStakingPool/AssertionStakingPool.sol


35              rollup = _rollup;


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/assertionStakingPool/AssertionStakingPool.sol#L0:0

```solidity
File: src/assertionStakingPool/EdgeStakingPool.sol


39              challengeManager = _challengeManager;


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/assertionStakingPool/EdgeStakingPool.sol#L0:0

```solidity
File: src/bridge/SequencerInbox.sol


943             batchPosterManager = newBatchPosterManager;


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/bridge/SequencerInbox.sol#L0:0

```solidity
File: src/rollup/BOLDUpgradeAction.sol


325             MINI_STAKE_AMOUNTS_STORAGE = address(new ConstantArrayStorage(settings.miniStakeAmounts));


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/rollup/BOLDUpgradeAction.sol#L0:0

```solidity
File: src/rollup/RollupAdminLogic.sol


318             anyTrustFastConfirmer = _anyTrustFastConfirmer;


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/rollup/RollupAdminLogic.sol#L0:0

```solidity
File: src/rollup/RollupCreator.sol


79              validatorWalletCreator = _validatorWalletCreator;
208             deployParams.config.owner = address(this);


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/rollup/RollupCreator.sol#L0:0

</details>

## L015 - The setter does not set a state variable or call a fuction:

  


```solidity
File: src/bridge/ISequencerInbox.sol


247         function setMaxTimeVariation(MaxTimeVariation memory maxTimeVariation_) external;
254         function setIsBatchPoster(address addr, bool isBatchPoster_) external;
260         function setValidKeyset(bytes calldata keysetBytes) external;
274         function setIsSequencer(address addr, bool isSequencer_) external;
280         function setBatchPosterManager(address newBatchPosterManager) external;


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/bridge/ISequencerInbox.sol#L0:0

```solidity
File: src/rollup/IRollupAdmin.sol


22          function setOutbox(IOutbox _outbox) external;
35          function setDelayedInbox(address _inbox, bool _enabled) external;
54          function setValidator(address[] memory _validator, bool[] memory _val) external;
60          function setOwner(address newOwner) external;
66          function setMinimumAssertionPeriod(uint256 newPeriod) external;
72          function setConfirmPeriodBlocks(uint64 newConfirmPeriod) external;
78          function setBaseStake(uint256 newBaseStake) external;
95          function setLoserStakeEscrow(address newLoserStakerEscrow) external;
101         function setWasmModuleRoot(bytes32 newWasmModuleRoot) external;
107         function setSequencerInbox(address _sequencerInbox) external;
113         function setValidatorWhitelistDisabled(bool _validatorWhitelistDisabled) external;
119         function setChallengeManager(address _challengeManager) external;


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/rollup/IRollupAdmin.sol#L0:0

## L016 - Prefer continue over revert model in iteration:

Preferably, it's better to skip operations on array indices when a condition is not met instead of reverting the entire transaction. Reverting could be exploited by malicious actors who might intentionally introduce array objects failing conditional checks, disrupting group operations. It's advisable to skip array indices rather than revert, unless there are valid security or logic reasons for doing otherwise


```solidity
File: src/challengeV2/libraries/MerkleTreeLib.sol


188             for (uint256 i = 0; i < me.length; i++) {
189                 // we can only append at the level of the smallest complete sub tree or below
190                 // appending above this level would mean create "holes" in the tree
191                 // we can find the smallest complete sub tree by looking for the first entry in the merkle expansion
192                 if (i < level) {
193                     // we're below the level we want to append - no complete sub trees allowed down here
194                     // if the level is 0 there are no complete subtrees, and we therefore cannot be too low
195                     require(me[i] == 0, "Append above least significant bit");
196                 } else {
197                     // we're at or above the level
198                     if (accumHash == 0) {
199                         // no more changes to propagate upwards - just fill the tree
200                         next[i] = me[i];
201                     } else {
202                         // we have a change to propagate
203                         if (me[i] == 0) {
204                             // if the level is currently empty we can just add the change
205                             next[i] = accumHash;
206                             // and then there's nothing more to propagate
207                             accumHash = 0;
208                         } else {
209                             // if the level is not currently empty then we combine it with propagation
210                             // change, and propagate that to the level above. This level is now part of a complete subtree
211                             // so we zero it out
212                             next[i] = 0;
213                             accumHash = keccak256(abi.encodePacked(me[i], accumHash));
214                         }
215                     }
216                 }
217             }


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/challengeV2/libraries/MerkleTreeLib.sol#L0:0

```solidity
File: src/rollup/BOLDUpgradeAction.sol


528                 for (uint256 i = 0; i < validators.length; i++) {
529                     require(ROLLUP_READER.isValidator(validators[i]), "UNEXPECTED_NEW_VALIDATOR");
530                     _vals[i] = true;
531                 }


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/rollup/BOLDUpgradeAction.sol#L0:0




## L017 - `abi.encodePacked()` should not be used with dynamic types when passing the result to a hash function such as `keccak256()`:

Use `abi.encode()` instead which will pad items to 32 bytes, which will [prevent hash collisions](https://docs.soliditylang.org/en/v0.8.13/abi-spec.html#non-standard-packed-mode) (e.g. `abi.encodePacked(0x123,0x456)` => `0x123456` => `abi.encodePacked(0x1,0x23456)`, but `abi.encode(0x123,0x456)` => `0x0...1230...456`). Unless there is a compelling reason, `abi.encode` should be preferred. If there is only one argument to `abi.encodePacked()` it can often be cast to `bytes()` or `bytes32()` [instead](https://ethereum.stackexchange.com/questions/30912/how-to-compare-strings-in-solidity#answer-82739). If all arguments are strings and or bytes, `bytes.concat()` should be used instead.


<details>
<summary>Click to show 10 findings</summary>

```solidity
File: src/assertionStakingPool/StakingPoolCreatorUtils.sol


bytes32 bytecodeHash = keccak256(abi.encodePacked(creationCode, args));

```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/assertionStakingPool/StakingPoolCreatorUtils.sol#L14:14   

```solidity
File: src/challengeV2/libraries/ChallengeEdgeLib.sol


return keccak256(abi.encodePacked(level, originId, startHeight, startHistoryRoot, endHeight));

```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/challengeV2/libraries/ChallengeEdgeLib.sol#L173:173

```solidity
File: src/challengeV2/libraries/EdgeChallengeManagerLib.sol


bytes32 public constant UNRIVALED = keccak256(abi.encodePacked("UNRIVALED"));

```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/challengeV2/libraries/EdgeChallengeManagerLib.sol#L135:135

```solidity
File: src/challengeV2/libraries/MerkleTreeLib.sol


accum = keccak256(abi.encodePacked(accum, bytes32(0)));

accum = keccak256(abi.encodePacked(val, accum));

accum = keccak256(abi.encodePacked(accum, bytes32(0)));

accumHash = keccak256(abi.encodePacked(me[i], accumHash));

return appendCompleteSubTree(me, 0, keccak256(abi.encodePacked(leaf)));

bytes32 calculatedRoot = MerkleLib.calculateRoot(proof, index, keccak256(abi.encodePacked(leaf)));

```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/challengeV2/libraries/MerkleTreeLib.sol#L363:363

```solidity
File: src/rollup/BOLDUpgradeAction.sol


keccak256(abi.encodePacked(executionState.globalState.hash(), inboxMaxCount, executionState.machineStatus));

```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/rollup/BOLDUpgradeAction.sol#L103:103

</details>

## L018 - Initializers could be front-run:

Initializers could be front-run, allowing an attacker to either set their own values, take ownership of the contract, and in the best case forcing a re-deployment


```solidity
File: src/challengeV2/EdgeChallengeManager.sol


305         function initialize(
306             IAssertionChain _assertionChain,
307             uint64 _challengePeriodBlocks,
308             IOneStepProofEntry _oneStepProofEntry,
309             uint256 layerZeroBlockEdgeHeight,
310             uint256 layerZeroBigStepEdgeHeight,
311             uint256 layerZeroSmallStepEdgeHeight,
312             IERC20 _stakeToken,
313             address _excessStakeReceiver,
314             uint8 _numBigStepLevel,
315             uint256[] calldata _stakeAmounts
316         ) public initializer {
317             if (address(_assertionChain) == address(0)) {
318                 revert EmptyAssertionChain();
319             }
320             assertionChain = _assertionChain;
321             if (address(_oneStepProofEntry) == address(0)) {
322                 revert EmptyOneStepProofEntry();
323             }
324             oneStepProofEntry = _oneStepProofEntry;
325             if (_challengePeriodBlocks == 0) {
326                 revert EmptyChallengePeriod();
327             }
328             challengePeriodBlocks = _challengePeriodBlocks;
329     
330             stakeToken = _stakeToken;
331             if (_excessStakeReceiver == address(0)) {
332                 revert EmptyStakeReceiver();
333             }
334             excessStakeReceiver = _excessStakeReceiver;
335     
336             if (!EdgeChallengeManagerLib.isPowerOfTwo(layerZeroBlockEdgeHeight)) {
337                 revert NotPowerOfTwo(layerZeroBlockEdgeHeight);
338             }
339             LAYERZERO_BLOCKEDGE_HEIGHT = layerZeroBlockEdgeHeight;
340             if (!EdgeChallengeManagerLib.isPowerOfTwo(layerZeroBigStepEdgeHeight)) {
341                 revert NotPowerOfTwo(layerZeroBigStepEdgeHeight);
342             }
343             LAYERZERO_BIGSTEPEDGE_HEIGHT = layerZeroBigStepEdgeHeight;
344             if (!EdgeChallengeManagerLib.isPowerOfTwo(layerZeroSmallStepEdgeHeight)) {
345                 revert NotPowerOfTwo(layerZeroSmallStepEdgeHeight);
346             }
347             LAYERZERO_SMALLSTEPEDGE_HEIGHT = layerZeroSmallStepEdgeHeight;
348     
349             // ensure that there is at least on of each type of level
350             if (_numBigStepLevel == 0) {
351                 revert ZeroBigStepLevels();
352             }
353             // ensure there's also space for the block level and the small step level
354             // in total level parameters
355             if (_numBigStepLevel > 253) {
356                 revert BigStepLevelsTooMany(_numBigStepLevel);
357             }
358             NUM_BIGSTEP_LEVEL = _numBigStepLevel;
359     
360             if (_numBigStepLevel + 2 != _stakeAmounts.length) {
361                 revert StakeAmountsMismatch(_stakeAmounts.length, _numBigStepLevel + 2);
362             }
363             stakeAmounts = _stakeAmounts;
364         }


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/challengeV2/EdgeChallengeManager.sol#L0:0

```solidity
File: src/rollup/RollupAdminLogic.sol


18          function initialize(Config calldata config, ContractDependencies calldata connectedContracts)
19              external
20              override
21              onlyProxy
22              initializer
23          {
24              rollupDeploymentBlock = block.number;
25              bridge = connectedContracts.bridge;
26              connectedContracts.bridge.setDelayedInbox(address(connectedContracts.inbox), true);
27              connectedContracts.bridge.setSequencerInbox(address(connectedContracts.sequencerInbox));
28      
29              inbox = connectedContracts.inbox;
30              outbox = connectedContracts.outbox;
31              connectedContracts.bridge.setOutbox(address(connectedContracts.outbox), true);
32              rollupEventInbox = connectedContracts.rollupEventInbox;
33      
34              // dont need to connect and initialize the event inbox if it's already been initialized
35              if (!bridge.allowedDelayedInboxes(address(connectedContracts.rollupEventInbox))) {
36                  connectedContracts.bridge.setDelayedInbox(address(connectedContracts.rollupEventInbox), true);
37                  connectedContracts.rollupEventInbox.rollupInitialized(config.chainId, config.chainConfig);
38              }
39      
40              if (connectedContracts.sequencerInbox.totalDelayedMessagesRead() == 0) {
41                  connectedContracts.sequencerInbox.addSequencerL2Batch(0, "", 1, IGasRefunder(address(0)), 0, 1);
42              }
43      
44              validatorWalletCreator = connectedContracts.validatorWalletCreator;
45              challengeManager = connectedContracts.challengeManager;
46      
47              confirmPeriodBlocks = config.confirmPeriodBlocks;
48              chainId = config.chainId;
49              baseStake = config.baseStake;
50              wasmModuleRoot = config.wasmModuleRoot;
51              // A little over 15 minutes
52              minimumAssertionPeriod = 75;
53              challengeGracePeriodBlocks = config.challengeGracePeriodBlocks;
54      
55              // loser stake is now sent directly to loserStakeEscrow, it must not
56              // be address(0) because some token do not allow transfers to address(0)
57              require(config.loserStakeEscrow != address(0), "INVALID_ESCROW_0");
58              loserStakeEscrow = config.loserStakeEscrow;
59      
60              stakeToken = config.stakeToken;
61              anyTrustFastConfirmer = config.anyTrustFastConfirmer;
62      
63              bytes32 parentAssertionHash = bytes32(0);
64              bytes32 inboxAcc = bytes32(0);
65              bytes32 genesisHash = RollupLib.assertionHash({
66                  parentAssertionHash: parentAssertionHash,
67                  afterStateHash: config.genesisAssertionState.hash(),
68                  inboxAcc: inboxAcc
69              });
70      
71              uint256 currentInboxCount = bridge.sequencerMessageCount();
72              // ensure to move the inbox forward by at least one message
73              if (currentInboxCount == config.genesisInboxCount) {
74                  currentInboxCount += 1;
75              }
76              AssertionNode memory initialAssertion = AssertionNodeLib.createAssertion(
77                  true,
78                  RollupLib.configHash({
79                      wasmModuleRoot: wasmModuleRoot,
80                      requiredStake: baseStake,
81                      challengeManager: address(challengeManager),
82                      confirmPeriodBlocks: confirmPeriodBlocks,
83                      nextInboxPosition: uint64(currentInboxCount)
84                  })
85              );
86              initializeCore(initialAssertion, genesisHash);
87      
88              AssertionInputs memory assertionInputs;
89              assertionInputs.afterState = config.genesisAssertionState;
90              emit AssertionCreated(
91                  genesisHash,
92                  parentAssertionHash,
93                  assertionInputs,
94                  inboxAcc,
95                  currentInboxCount,
96                  wasmModuleRoot,
97                  baseStake,
98                  address(challengeManager),
99                  confirmPeriodBlocks
100             );
101             if (_hostChainIsArbitrum) {
102                 _assertionCreatedAtArbSysBlock[genesisHash] = ArbSys(address(100)).arbBlockNumber();
103             }
104     
105             emit RollupInitialized(config.wasmModuleRoot, config.chainId);
106         }


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/rollup/RollupAdminLogic.sol#L0:0

## L019 - Loss of precision due to division by large numbers:

Division by large numbers may result in the result being zero, due to solidity not supporting fractions. Consider requiring a minimum amount for the numerator to ensure that it is always larger than the denominator.


```solidity
File: src/bridge/DelayBuffer.sol


46              buffer += (elapsed * replenishRateInBasis) / BASIS;


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/bridge/DelayBuffer.sol#L0:0

## L020 - Array lengths not checked:

If the length of the arrays are not required to be of the same length, user operations may not be fully executed due to a mismatch in the number of items iterated over, versus the number of items provided in the second array.


```solidity
File: src/challengeV2/EdgeChallengeManager.sol


539         function confirmEdgeByOneStepProof(
540             bytes32 edgeId,
541             OneStepData calldata oneStepData,
542             ConfigData calldata prevConfig,
543             bytes32[] calldata beforeHistoryInclusionProof,
544             bytes32[] calldata afterHistoryInclusionProof
545         ) public {
546             bytes32 prevAssertionHash = store.getPrevAssertionHash(edgeId);
547     
548             assertionChain.validateConfig(prevAssertionHash, prevConfig);
549     
550             ExecutionContext memory execCtx = ExecutionContext({
551                 maxInboxMessagesRead: prevConfig.nextInboxPosition,
552                 bridge: assertionChain.bridge(),
553                 initialWasmModuleRoot: prevConfig.wasmModuleRoot
554             });
555     
556             store.confirmEdgeByOneStepProof(
557                 edgeId,
558                 oneStepProofEntry,
559                 oneStepData,
560                 execCtx,
561                 beforeHistoryInclusionProof,
562                 afterHistoryInclusionProof,
563                 NUM_BIGSTEP_LEVEL,
564                 LAYERZERO_BIGSTEPEDGE_HEIGHT,
565                 LAYERZERO_SMALLSTEPEDGE_HEIGHT
566             );
567     
568             emit EdgeConfirmedByOneStepProof(edgeId, store.edges[edgeId].mutualId());
569         }


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/challengeV2/EdgeChallengeManager.sol#L0:0

```solidity
File: src/challengeV2/libraries/EdgeChallengeManagerLib.sol


766         function confirmEdgeByOneStepProof(
767             EdgeStore storage store,
768             bytes32 edgeId,
769             IOneStepProofEntry oneStepProofEntry,
770             OneStepData calldata oneStepData,
771             ExecutionContext memory execCtx,
772             bytes32[] calldata beforeHistoryInclusionProof,
773             bytes32[] calldata afterHistoryInclusionProof,
774             uint8 numBigStepLevel,
775             uint256 bigStepHeight,
776             uint256 smallStepHeight
777         ) internal {
778             if (!store.edges[edgeId].exists()) {
779                 revert EdgeNotExists(edgeId);
780             }
781     
782             // edge must of type SmallStep
783             if (ChallengeEdgeLib.levelToType(store.edges[edgeId].level, numBigStepLevel) != EdgeType.SmallStep) {
784                 revert EdgeTypeNotSmallStep(store.edges[edgeId].level);
785             }
786     
787             // edge must be length one to execute one step proofs against
788             if (store.edges[edgeId].length() != 1) {
789                 revert EdgeNotLengthOne(store.edges[edgeId].length());
790             }
791     
792             // Get the machine step that corresponds to the start height of this edge
793             // To do this we sum the machine steps of the edges in each of the preceeding levels.
794             // We do not include the block height, since each step at the block level is a new block
795             // and new blocks reset the machine step to 0.
796             uint256 machineStep = store.edges[edgeId].startHeight;
797             {
798                 bytes32 cursor = edgeId;
799                 uint256 stepSize = smallStepHeight;
800                 while (store.edges[cursor].level > 1) {
801                     bytes32 nextEdgeId = store.edges[cursor].originId;
802                     // We can traverse to previous levels using the origin id
803                     cursor = store.firstRivals[nextEdgeId];
804                     // sum the stepSize * offset from 0 at this level
805                     machineStep += stepSize * store.edges[cursor].startHeight;
806                     // the step size at each level is the product of the heights at all succeeding levels
807                     stepSize *= bigStepHeight;
808                 }
809             }
810     
811             // the state in the onestep data must be committed to by the startHistoryRoot
812             MerkleTreeLib.verifyInclusionProof(
813                 store.edges[edgeId].startHistoryRoot, oneStepData.beforeHash, machineStep, beforeHistoryInclusionProof
814             );
815     
816             // execute the single step to produce the after state
817             bytes32 afterHash =
818                 oneStepProofEntry.proveOneStep(execCtx, machineStep, oneStepData.beforeHash, oneStepData.proof);
819     
820             // check that the after state was indeed committed to by the endHistoryRoot
821             MerkleTreeLib.verifyInclusionProof(
822                 store.edges[edgeId].endHistoryRoot, afterHash, machineStep + 1, afterHistoryInclusionProof
823             );
824     
825             // also checks that no other rival has been confirmed
826             setConfirmedRival(store, edgeId);
827     
828             // we also check the edge is pending in setConfirmed()
829             store.edges[edgeId].setConfirmed();
830             store.edges[edgeId].totalTimeUnrivaledCache = type(uint64).max;
831         }


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/challengeV2/libraries/EdgeChallengeManagerLib.sol#L0:0

## L021 - `require()` should be used instead of `assert()`:

Prior to solidity version 0.8.0, hitting an assert consumes the remainder of the transaction's available gas rather than returning it, as require()/revert() do. assert() should be avoided even past solidity version 0.8.0 as its documentation states that 'The assert function creates an error of type Panic(uint256). ... Properly functioning code should never create a Panic, not even on invalid external input. If this happens, then there is a bug in your contract which you should fix'.


```solidity
File: src/bridge/SequencerInbox.sol


651             assert(header.length == HEADER_LENGTH);


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/bridge/SequencerInbox.sol#L0:0

```solidity
File: src/challengeV2/libraries/MerkleTreeLib.sol


340                 assert(size <= postSize);


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/challengeV2/libraries/MerkleTreeLib.sol#L0:0

## L022 - Missing checks for `address(0x0)` when assigning values to address state variables:

This issue arises when an address state variable is assigned a value without a preceding check to ensure it isn't address(0x0). This can lead to unexpected behavior as address(0x0) often represents an uninitialized address.


```solidity
File: src/bridge/SequencerInbox.sol


943             batchPosterManager = newBatchPosterManager;


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/bridge/SequencerInbox.sol#L0:0

```solidity
File: src/rollup/RollupCreator.sol


79              validatorWalletCreator = _validatorWalletCreator;


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/rollup/RollupCreator.sol#L0:0

## L023 - Upgradeable contract is missing a __gap[50] storage variable to allow for new storage variables in later versions:

This issue arises when an upgradeable contract doesn't include a __gap[50] storage variable. This variable is crucial for facilitating future upgrades and preserving storage layout.


```solidity
File: src/challengeV2/EdgeChallengeManager.sol


18      interface IEdgeChallengeManager {
206     contract EdgeChallengeManager is IEdgeChallengeManager, Initializable {


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/challengeV2/EdgeChallengeManager.sol#L0:0

```solidity
File: src/rollup/RollupAdminLogic.sol


15      contract RollupAdminLogic is RollupCore, IRollupAdmin, DoubleLogicUUPSUpgradeable {


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/rollup/RollupAdminLogic.sol#L0:0

## L024 - Use `Ownable2Step` rather than `Ownable`:

`Ownable2Step` and `Ownable2StepUpgradeable` prevent the contract ownership from mistakenly being transferred to an address that cannot handle it (e.g. due to a typo in the address), by requiring that the recipient of the owner permissions actively accept via a contract call of its own.


```solidity
File: src/rollup/BridgeCreator.sol


21      contract BridgeCreator is Ownable {


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/rollup/BridgeCreator.sol#L0:0

```solidity
File: src/rollup/RollupCreator.sol


17      contract RollupCreator is Ownable {


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/rollup/RollupCreator.sol#L0:0

## L025 - Unsafe downcast:

When a type is downcast to a smaller type, the higher order bits are truncated, effectively applying a modulo to the original value. Without any other checks, this wrapping will lead to unexpected behavior and bugs.


```solidity
File: src/bridge/SequencerInbox.sol


780                 uint64(extraGas)
227             bounds.maxTimestamp = uint64(block.timestamp) + futureSeconds_;
648                 uint64(afterDelayedMessagesRead)
225                 bounds.minTimestamp = uint64(block.timestamp) - delaySeconds_;


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/bridge/SequencerInbox.sol#L0:0

```solidity
File: src/challengeV2/libraries/EdgeChallengeManagerLib.sol


510                 store.edges[edgeId].totalTimeUnrivaledCache = uint64(newValue);


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/challengeV2/libraries/EdgeChallengeManagerLib.sol#L0:0

```solidity
File: src/rollup/RollupCore.sol


275             uint64 stakerIndex = uint64(_stakerList.length);
218             return uint64(_stakerList.length);


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/rollup/RollupCore.sol#L0:0

## L026 - Upgradeable contract not initialized:

Upgradeable contracts are initialized via an initializer function rather than by a constructor. Leaving such a contract uninitialized may lead to it being taken over by a malicious user.


```solidity
File: src/challengeV2/EdgeChallengeManager.sol


206     contract EdgeChallengeManager is IEdgeChallengeManager, Initializable {


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/challengeV2/EdgeChallengeManager.sol#L0:0

```solidity
File: src/rollup/RollupAdminLogic.sol


15      contract RollupAdminLogic is RollupCore, IRollupAdmin, DoubleLogicUUPSUpgradeable {


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/rollup/RollupAdminLogic.sol#L0:0

## L027 - Use of `tx.origin` is unsafe in almost every context:

According to [Vitalik Buterin](https://ethereum.stackexchange.com/questions/196/how-do-i-make-my-dapp-serenity-proof), contracts should _not_ `assume that tx.origin will continue to be usable or meaningful`. An example of this is [EIP-3074](https://eips.ethereum.org/EIPS/eip-3074#allowing-txorigin-as-signer-1) which explicitly mentions the intention to change its semantics when it's used with new op codes. There have also been calls to [remove](https://github.com/ethereum/solidity/issues/683) `tx.origin`, and there are [security issues](solidity.readthedocs.io/en/v0.4.24/security-considerations.html#tx-origin) associated with using it for authorization. For these reasons, it's best to completely avoid the feature.


```solidity
File: src/bridge/SequencerInbox.sol


375             if (msg.sender != tx.origin) revert NotOrigin();
440             if (msg.sender != tx.origin) revert NotOrigin();
507             if (msg.sender == tx.origin && !isUsingFeeToken) {
764             address batchPoster = tx.origin;


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/bridge/SequencerInbox.sol#L0:0

## L028 - Setters should have initial value check:

Setters should have initial value check to prevent assigning wrong value to the variable. Assginment of wrong value can lead to unexpected behavior of the contract.


```solidity
File: src/bridge/SequencerInbox.sol


847         function _setBufferConfig(BufferConfig memory bufferConfig_) internal {
848             if (!isDelayBufferable) revert NotDelayBufferable();
849             if (!DelayBuffer.isValidBufferConfig(bufferConfig_)) revert BadBufferConfig();
850     
851             if (buffer.bufferBlocks == 0 || buffer.bufferBlocks > bufferConfig_.max) {
852                 buffer.bufferBlocks = bufferConfig_.max;
853             }
854             if (buffer.bufferBlocks < bufferConfig_.threshold) {
855                 buffer.bufferBlocks = bufferConfig_.threshold;
856             }
857             buffer.max = bufferConfig_.max;
858             buffer.threshold = bufferConfig_.threshold;
859             buffer.replenishRateInBasis = bufferConfig_.replenishRateInBasis;
860     
861             // if all delayed messages are read, the buffer is considered synced
862             if (bridge.delayedMessageCount() == totalDelayedMessagesRead) {
863                 buffer.update(uint64(block.number));
864             }
865         }
867         function _setMaxTimeVariation(ISequencerInbox.MaxTimeVariation memory maxTimeVariation_)
868             internal
869         {
870             if (
871                 maxTimeVariation_.delayBlocks > type(uint64).max ||
872                 maxTimeVariation_.futureBlocks > type(uint64).max ||
873                 maxTimeVariation_.delaySeconds > type(uint64).max ||
874                 maxTimeVariation_.futureSeconds > type(uint64).max
875             ) {
876                 revert BadMaxTimeVariation();
877             }
878             delayBlocks = uint64(maxTimeVariation_.delayBlocks);
879             futureBlocks = uint64(maxTimeVariation_.futureBlocks);
880             delaySeconds = uint64(maxTimeVariation_.delaySeconds);
881             futureSeconds = uint64(maxTimeVariation_.futureSeconds);
882         }
885         function setMaxTimeVariation(ISequencerInbox.MaxTimeVariation memory maxTimeVariation_)
886             external
887             onlyRollupOwner
888         {
889             _setMaxTimeVariation(maxTimeVariation_);
890             emit OwnerFunctionCalled(0);
891         }
894         function setIsBatchPoster(address addr, bool isBatchPoster_)
895             external
896             onlyRollupOwnerOrBatchPosterManager
897         {
898             isBatchPoster[addr] = isBatchPoster_;
899             emit OwnerFunctionCalled(1);
900         }
903         function setValidKeyset(bytes calldata keysetBytes) external onlyRollupOwner {
904             uint256 ksWord = uint256(keccak256(bytes.concat(hex"fe", keccak256(keysetBytes))));
905             bytes32 ksHash = bytes32(ksWord ^ (1 << 255));
906             if (keysetBytes.length >= 64 * 1024) revert KeysetTooLarge();
907     
908             if (dasKeySetInfo[ksHash].isValidKeyset) revert AlreadyValidDASKeyset(ksHash);
909             uint256 creationBlock = block.number;
910             if (hostChainIsArbitrum) {
911                 creationBlock = ArbSys(address(100)).arbBlockNumber();
912             }
913             dasKeySetInfo[ksHash] = DasKeySetInfo({
914                 isValidKeyset: true,
915                 creationBlock: uint64(creationBlock)
916             });
917             emit SetValidKeyset(ksHash, keysetBytes);
918             emit OwnerFunctionCalled(2);
919         }
933         function setIsSequencer(address addr, bool isSequencer_)
934             external
935             onlyRollupOwnerOrBatchPosterManager
936         {
937             isSequencer[addr] = isSequencer_;
938             emit OwnerFunctionCalled(4); // Owner in this context can also be batch poster manager
939         }
942         function setBatchPosterManager(address newBatchPosterManager) external onlyRollupOwner {
943             batchPosterManager = newBatchPosterManager;
944             emit OwnerFunctionCalled(5);
945         }
947         function setBufferConfig(BufferConfig memory bufferConfig_) external onlyRollupOwner {
948             _setBufferConfig(bufferConfig_);
949             emit OwnerFunctionCalled(6);
950         }


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/bridge/SequencerInbox.sol#L0:0

```solidity
File: src/rollup/RollupAdminLogic.sol


117         function setOutbox(IOutbox _outbox) external override {
118             outbox = _outbox;
119             bridge.setOutbox(address(_outbox), true);
120             emit OwnerFunctionCalled(0);
121         }
138         function setDelayedInbox(address _inbox, bool _enabled) external override {
139             bridge.setDelayedInbox(address(_inbox), _enabled);
140             emit OwnerFunctionCalled(2);
141         }
180         function setValidator(address[] calldata _validator, bool[] calldata _val) external override {
181             require(_validator.length > 0, "EMPTY_ARRAY");
182             require(_validator.length == _val.length, "WRONG_LENGTH");
183     
184             for (uint256 i = 0; i < _validator.length; i++) {
185                 isValidator[_validator[i]] = _val[i];
186             }
187             emit OwnerFunctionCalled(6);
188         }
195         function setOwner(address newOwner) external override {
196             _changeAdmin(newOwner);
197             emit OwnerFunctionCalled(7);
198         }
204         function setMinimumAssertionPeriod(uint256 newPeriod) external override {
205             minimumAssertionPeriod = newPeriod;
206             emit OwnerFunctionCalled(8);
207         }
223         function setBaseStake(uint256 newBaseStake) external override {
224             baseStake = newBaseStake;
225             emit OwnerFunctionCalled(12);
226         }
281         function setWasmModuleRoot(bytes32 newWasmModuleRoot) external override {
282             wasmModuleRoot = newWasmModuleRoot;
283             emit OwnerFunctionCalled(26);
284         }
290         function setSequencerInbox(address _sequencerInbox) external override {
291             bridge.setSequencerInbox(_sequencerInbox);
292             emit OwnerFunctionCalled(27);
293         }
299         function setInbox(IInboxBase newInbox) external {
300             inbox = newInbox;
301             emit OwnerFunctionCalled(28);
302         }
308         function setValidatorWhitelistDisabled(bool _validatorWhitelistDisabled) external {
309             validatorWhitelistDisabled = _validatorWhitelistDisabled;
310             emit OwnerFunctionCalled(30);
311         }
317         function setAnyTrustFastConfirmer(address _anyTrustFastConfirmer) external {
318             anyTrustFastConfirmer = _anyTrustFastConfirmer;
319             emit OwnerFunctionCalled(31);
320         }
326         function setChallengeManager(address _challengeManager) external {
327             challengeManager = IEdgeChallengeManager(_challengeManager);
328             emit OwnerFunctionCalled(32);
329         }


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/rollup/RollupAdminLogic.sol#L0:0

```solidity
File: src/rollup/RollupCreator.sol


63          function setTemplates(
64              BridgeCreator _bridgeCreator,
65              IOneStepProofEntry _osp,
66              IEdgeChallengeManager _challengeManagerLogic,
67              IRollupAdmin _rollupAdminLogic,
68              IRollupUser _rollupUserLogic,
69              IUpgradeExecutor _upgradeExecutorLogic,
70              address _validatorWalletCreator,
71              DeployHelper _l2FactoriesDeployer
72          ) external onlyOwner {
73              bridgeCreator = _bridgeCreator;
74              osp = _osp;
75              challengeManagerTemplate = _challengeManagerLogic;
76              rollupAdminLogic = _rollupAdminLogic;
77              rollupUserLogic = _rollupUserLogic;
78              upgradeExecutorLogic = _upgradeExecutorLogic;
79              validatorWalletCreator = _validatorWalletCreator;
80              l2FactoriesDeployer = _l2FactoriesDeployer;
81              emit TemplatesUpdated();
82          }


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/rollup/RollupCreator.sol#L0:0

## L029 - Empty `receive()`/`payable fallback()` function does not authorize requests:

If the intention is for the Ether to be used, the function should call another function, otherwise it should revert (e.g. `require(msg.sender == address(weth))`). Having no access control on the function means that someone may send Ether to the contract, and have no way to get anything back out, which is a loss of funds. If the concern is having to spend a small amount of gas to check the sender against an immutable address, the code should at least have a function to rescue unused Ether.


```solidity
File: src/rollup/RollupCreator.sol


61          receive() external payable {}


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/rollup/RollupCreator.sol#L0:0








## Non-critical Issues

Total: 1218 instances over 125 issues


## NC001 - Library declarations should have Natspec @title annotations:

A title that should describe the contract/interface


<details>
<summary>Click to show 5 findings</summary>

```solidity
File: src/assertionStakingPool/StakingPoolCreatorUtils.sol


11      library StakingPoolCreatorUtils {


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/assertionStakingPool/StakingPoolCreatorUtils.sol#L0:0

```solidity
File: src/challengeV2/libraries/ChallengeEdgeLib.sol


67      library ChallengeEdgeLib {


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/challengeV2/libraries/ChallengeEdgeLib.sol#L0:0

```solidity
File: src/rollup/Assertion.sol


66      library AssertionNodeLib {


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/rollup/Assertion.sol#L0:0

```solidity
File: src/rollup/AssertionState.sol


17      library AssertionStateLib {


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/rollup/AssertionState.sol#L0:0

```solidity
File: src/rollup/RollupLib.sol


17      library RollupLib {


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/rollup/RollupLib.sol#L0:0

</details>

## NC002 - Library declarations should have Natspec @author annotations:

The name of the author


<details>
<summary>Click to show 10 findings</summary>

```solidity
File: src/assertionStakingPool/StakingPoolCreatorUtils.sol


11      library StakingPoolCreatorUtils {


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/assertionStakingPool/StakingPoolCreatorUtils.sol#L0:0

```solidity
File: src/bridge/DelayBuffer.sol


16      library DelayBuffer {


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/bridge/DelayBuffer.sol#L0:0

```solidity
File: src/challengeV2/libraries/ArrayUtilsLib.sol


9       library ArrayUtilsLib {


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/challengeV2/libraries/ArrayUtilsLib.sol#L0:0

```solidity
File: src/challengeV2/libraries/ChallengeEdgeLib.sol


67      library ChallengeEdgeLib {


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/challengeV2/libraries/ChallengeEdgeLib.sol#L0:0

```solidity
File: src/challengeV2/libraries/EdgeChallengeManagerLib.sol


129     library EdgeChallengeManagerLib {


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/challengeV2/libraries/EdgeChallengeManagerLib.sol#L0:0

```solidity
File: src/challengeV2/libraries/MerkleTreeLib.sol


102     library MerkleTreeLib {


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/challengeV2/libraries/MerkleTreeLib.sol#L0:0

```solidity
File: src/challengeV2/libraries/UintUtilsLib.sol


9       library UintUtilsLib {


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/challengeV2/libraries/UintUtilsLib.sol#L0:0

```solidity
File: src/rollup/Assertion.sol


66      library AssertionNodeLib {


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/rollup/Assertion.sol#L0:0

```solidity
File: src/rollup/AssertionState.sol


17      library AssertionStateLib {


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/rollup/AssertionState.sol#L0:0

```solidity
File: src/rollup/RollupLib.sol


17      library RollupLib {


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/rollup/RollupLib.sol#L0:0

</details>

## NC003 - Library declarations should have Natspec @notice annotations:

Explain to an end user what this does


<details>
<summary>Click to show 4 findings</summary>

```solidity
File: src/assertionStakingPool/StakingPoolCreatorUtils.sol


11      library StakingPoolCreatorUtils {


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/assertionStakingPool/StakingPoolCreatorUtils.sol#L0:0

```solidity
File: src/challengeV2/libraries/ChallengeEdgeLib.sol


67      library ChallengeEdgeLib {


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/challengeV2/libraries/ChallengeEdgeLib.sol#L0:0

```solidity
File: src/rollup/AssertionState.sol


17      library AssertionStateLib {


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/rollup/AssertionState.sol#L0:0

```solidity
File: src/rollup/RollupLib.sol


17      library RollupLib {


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/rollup/RollupLib.sol#L0:0

</details>

## NC004 - Library declarations should have Natspec @dev annotations:

Explain to a developer any extra details


<details>
<summary>Click to show 10 findings</summary>

```solidity
File: src/assertionStakingPool/StakingPoolCreatorUtils.sol


11      library StakingPoolCreatorUtils {


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/assertionStakingPool/StakingPoolCreatorUtils.sol#L0:0

```solidity
File: src/bridge/DelayBuffer.sol


16      library DelayBuffer {


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/bridge/DelayBuffer.sol#L0:0

```solidity
File: src/challengeV2/libraries/ArrayUtilsLib.sol


9       library ArrayUtilsLib {


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/challengeV2/libraries/ArrayUtilsLib.sol#L0:0

```solidity
File: src/challengeV2/libraries/ChallengeEdgeLib.sol


67      library ChallengeEdgeLib {


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/challengeV2/libraries/ChallengeEdgeLib.sol#L0:0

```solidity
File: src/challengeV2/libraries/EdgeChallengeManagerLib.sol


129     library EdgeChallengeManagerLib {


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/challengeV2/libraries/EdgeChallengeManagerLib.sol#L0:0

```solidity
File: src/challengeV2/libraries/MerkleTreeLib.sol


102     library MerkleTreeLib {


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/challengeV2/libraries/MerkleTreeLib.sol#L0:0

```solidity
File: src/challengeV2/libraries/UintUtilsLib.sol


9       library UintUtilsLib {


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/challengeV2/libraries/UintUtilsLib.sol#L0:0

```solidity
File: src/rollup/Assertion.sol


66      library AssertionNodeLib {


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/rollup/Assertion.sol#L0:0

```solidity
File: src/rollup/AssertionState.sol


17      library AssertionStateLib {


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/rollup/AssertionState.sol#L0:0

```solidity
File: src/rollup/RollupLib.sol


17      library RollupLib {


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/rollup/RollupLib.sol#L0:0

</details>

## NC005 - Modifier definitions should have Natspec @notice annotations:

Explain to an end user what this does


```solidity
File: src/bridge/SequencerInbox.sol


103         modifier onlyRollupOwner() {
108         modifier onlyRollupOwnerOrBatchPosterManager() {


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/bridge/SequencerInbox.sol#L0:0

```solidity
File: src/rollup/RollupUserLogic.sol


20          modifier onlyValidator() {


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/rollup/RollupUserLogic.sol#L0:0

## NC006 - Modifier definitions should have Natspec @dev annotations:

Explain to a developer any extra details


```solidity
File: src/bridge/SequencerInbox.sol


103         modifier onlyRollupOwner() {
108         modifier onlyRollupOwnerOrBatchPosterManager() {


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/bridge/SequencerInbox.sol#L0:0

```solidity
File: src/rollup/RollupUserLogic.sol


20          modifier onlyValidator() {


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/rollup/RollupUserLogic.sol#L0:0

## NC007 - Contract definitions should have Natspec @title annotations:

 title that should describe the contract


<details>
<summary>Click to show 10 findings</summary>

```solidity
File: src/assertionStakingPool/AssertionStakingPool.sol


21      contract AssertionStakingPool is AbsBoldStakingPool, IAssertionStakingPool {


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/assertionStakingPool/AssertionStakingPool.sol#L0:0

```solidity
File: src/assertionStakingPool/AssertionStakingPoolCreator.sol


13      contract AssertionStakingPoolCreator is IAssertionStakingPoolCreator {


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/assertionStakingPool/AssertionStakingPoolCreator.sol#L0:0

```solidity
File: src/assertionStakingPool/EdgeStakingPool.sol


25      contract EdgeStakingPool is AbsBoldStakingPool, IEdgeStakingPool {


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/assertionStakingPool/EdgeStakingPool.sol#L0:0

```solidity
File: src/assertionStakingPool/EdgeStakingPoolCreator.sol


13      contract EdgeStakingPoolCreator is IEdgeStakingPoolCreator {


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/assertionStakingPool/EdgeStakingPoolCreator.sol#L0:0

```solidity
File: src/rollup/BOLDUpgradeAction.sol


166     contract ConstantArrayStorage {


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/rollup/BOLDUpgradeAction.sol#L0:0

```solidity
File: src/rollup/BridgeCreator.sol


21      contract BridgeCreator is Ownable {


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/rollup/BridgeCreator.sol#L0:0

```solidity
File: src/rollup/RollupAdminLogic.sol


15      contract RollupAdminLogic is RollupCore, IRollupAdmin, DoubleLogicUUPSUpgradeable {


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/rollup/RollupAdminLogic.sol#L0:0

```solidity
File: src/rollup/RollupCreator.sol


17      contract RollupCreator is Ownable {


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/rollup/RollupCreator.sol#L0:0

```solidity
File: src/rollup/RollupProxy.sol


11      contract RollupProxy is AdminFallbackProxy {


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/rollup/RollupProxy.sol#L0:0

```solidity
File: src/rollup/RollupUserLogic.sol


15      contract RollupUserLogic is RollupCore, UUPSNotUpgradeable, IRollupUser {


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/rollup/RollupUserLogic.sol#L0:0

</details>

## NC008 - Contract definitions should have Natspec @author annotations:

The name of the author


<details>
<summary>Click to show 12 findings</summary>

```solidity
File: src/assertionStakingPool/AssertionStakingPool.sol


21      contract AssertionStakingPool is AbsBoldStakingPool, IAssertionStakingPool {


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/assertionStakingPool/AssertionStakingPool.sol#L0:0

```solidity
File: src/assertionStakingPool/AssertionStakingPoolCreator.sol


13      contract AssertionStakingPoolCreator is IAssertionStakingPoolCreator {


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/assertionStakingPool/AssertionStakingPoolCreator.sol#L0:0

```solidity
File: src/assertionStakingPool/EdgeStakingPool.sol


25      contract EdgeStakingPool is AbsBoldStakingPool, IEdgeStakingPool {


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/assertionStakingPool/EdgeStakingPool.sol#L0:0

```solidity
File: src/assertionStakingPool/EdgeStakingPoolCreator.sol


13      contract EdgeStakingPoolCreator is IEdgeStakingPoolCreator {


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/assertionStakingPool/EdgeStakingPoolCreator.sol#L0:0

```solidity
File: src/bridge/SequencerInbox.sol


64      contract SequencerInbox is DelegateCallAware, GasRefundEnabled, ISequencerInbox {


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/bridge/SequencerInbox.sol#L0:0

```solidity
File: src/challengeV2/EdgeChallengeManager.sol


206     contract EdgeChallengeManager is IEdgeChallengeManager, Initializable {


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/challengeV2/EdgeChallengeManager.sol#L0:0

```solidity
File: src/rollup/BOLDUpgradeAction.sol


94      contract StateHashPreImageLookup {
123     contract RollupReader is IOldRollup {
166     contract ConstantArrayStorage {
182     contract BOLDUpgradeAction {


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/rollup/BOLDUpgradeAction.sol#L0:0

```solidity
File: src/rollup/BridgeCreator.sol


21      contract BridgeCreator is Ownable {


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/rollup/BridgeCreator.sol#L0:0

```solidity
File: src/rollup/RollupAdminLogic.sol


15      contract RollupAdminLogic is RollupCore, IRollupAdmin, DoubleLogicUUPSUpgradeable {


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/rollup/RollupAdminLogic.sol#L0:0

```solidity
File: src/rollup/RollupCreator.sol


17      contract RollupCreator is Ownable {


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/rollup/RollupCreator.sol#L0:0

```solidity
File: src/rollup/RollupProxy.sol


11      contract RollupProxy is AdminFallbackProxy {


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/rollup/RollupProxy.sol#L0:0

```solidity
File: src/rollup/RollupUserLogic.sol


15      contract RollupUserLogic is RollupCore, UUPSNotUpgradeable, IRollupUser {


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/rollup/RollupUserLogic.sol#L0:0

</details>

## NC009 - Contract definitions should have Natspec @notice annotations:

Explain to an end user what this does


<details>
<summary>Click to show 5 findings</summary>

```solidity
File: src/rollup/BridgeCreator.sol


21      contract BridgeCreator is Ownable {


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/rollup/BridgeCreator.sol#L0:0

```solidity
File: src/rollup/RollupAdminLogic.sol


15      contract RollupAdminLogic is RollupCore, IRollupAdmin, DoubleLogicUUPSUpgradeable {


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/rollup/RollupAdminLogic.sol#L0:0

```solidity
File: src/rollup/RollupCreator.sol


17      contract RollupCreator is Ownable {


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/rollup/RollupCreator.sol#L0:0

```solidity
File: src/rollup/RollupProxy.sol


11      contract RollupProxy is AdminFallbackProxy {


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/rollup/RollupProxy.sol#L0:0

```solidity
File: src/rollup/RollupUserLogic.sol


15      contract RollupUserLogic is RollupCore, UUPSNotUpgradeable, IRollupUser {


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/rollup/RollupUserLogic.sol#L0:0

</details>

## NC010 - Contract definitions should have Natspec @dev annotations:

Explain to a developer any extra details


<details>
<summary>Click to show 11 findings</summary>

```solidity
File: src/assertionStakingPool/AssertionStakingPool.sol


21      contract AssertionStakingPool is AbsBoldStakingPool, IAssertionStakingPool {


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/assertionStakingPool/AssertionStakingPool.sol#L0:0

```solidity
File: src/assertionStakingPool/AssertionStakingPoolCreator.sol


13      contract AssertionStakingPoolCreator is IAssertionStakingPoolCreator {


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/assertionStakingPool/AssertionStakingPoolCreator.sol#L0:0

```solidity
File: src/assertionStakingPool/EdgeStakingPoolCreator.sol


13      contract EdgeStakingPoolCreator is IEdgeStakingPoolCreator {


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/assertionStakingPool/EdgeStakingPoolCreator.sol#L0:0

```solidity
File: src/bridge/SequencerInbox.sol


64      contract SequencerInbox is DelegateCallAware, GasRefundEnabled, ISequencerInbox {


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/bridge/SequencerInbox.sol#L0:0

```solidity
File: src/challengeV2/EdgeChallengeManager.sol


206     contract EdgeChallengeManager is IEdgeChallengeManager, Initializable {


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/challengeV2/EdgeChallengeManager.sol#L0:0

```solidity
File: src/rollup/BOLDUpgradeAction.sol


94      contract StateHashPreImageLookup {
123     contract RollupReader is IOldRollup {
166     contract ConstantArrayStorage {
182     contract BOLDUpgradeAction {


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/rollup/BOLDUpgradeAction.sol#L0:0

```solidity
File: src/rollup/BridgeCreator.sol


21      contract BridgeCreator is Ownable {


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/rollup/BridgeCreator.sol#L0:0

```solidity
File: src/rollup/RollupAdminLogic.sol


15      contract RollupAdminLogic is RollupCore, IRollupAdmin, DoubleLogicUUPSUpgradeable {


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/rollup/RollupAdminLogic.sol#L0:0

```solidity
File: src/rollup/RollupCreator.sol


17      contract RollupCreator is Ownable {


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/rollup/RollupCreator.sol#L0:0

```solidity
File: src/rollup/RollupProxy.sol


11      contract RollupProxy is AdminFallbackProxy {


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/rollup/RollupProxy.sol#L0:0

```solidity
File: src/rollup/RollupUserLogic.sol


15      contract RollupUserLogic is RollupCore, UUPSNotUpgradeable, IRollupUser {


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/rollup/RollupUserLogic.sol#L0:0

</details>

## NC011 - Event definitions should have Natspec @notice annotations:

Explain to an end user what this does


<details>
<summary>Click to show 6 findings</summary>

```solidity
File: src/bridge/ISequencerInbox.sol


28          event SequencerBatchDelivered(
38          event OwnerFunctionCalled(uint256 indexed id);
41          event SequencerBatchData(uint256 indexed batchSequenceNumber, bytes data);
44          event SetValidKeyset(bytes32 indexed keysetHash, bytes keysetBytes);
47          event InvalidateKeyset(bytes32 indexed keysetHash);


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/bridge/ISequencerInbox.sol#L0:0

```solidity
File: src/rollup/BOLDUpgradeAction.sol


56          event NodeCreated(
97          event HashSet(bytes32 h, ExecutionState executionState, uint256 inboxMaxCount);
235         event RollupMigrated(address rollup, address challengeManager);


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/rollup/BOLDUpgradeAction.sol#L0:0

```solidity
File: src/rollup/BridgeCreator.sol


25          event TemplatesUpdated();
26          event ERC20TemplatesUpdated();


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/rollup/BridgeCreator.sol#L0:0

```solidity
File: src/rollup/IRollupAdmin.sol


14          event OwnerFunctionCalled(uint256 indexed id);


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/rollup/IRollupAdmin.sol#L0:0

```solidity
File: src/rollup/IRollupCore.sol


24          event RollupInitialized(bytes32 machineHash, uint256 chainId);
26          event AssertionCreated(
38          event AssertionConfirmed(bytes32 indexed assertionHash, bytes32 blockHash, bytes32 sendRoot);
40          event RollupChallengeStarted(
44          event UserStakeUpdated(address indexed user, address indexed withdrawalAddress, uint256 initialBalance, uint256 finalBalance);
46          event UserWithdrawableFundsUpdated(address indexed user, uint256 initialBalance, uint256 finalBalance);


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/rollup/IRollupCore.sol#L0:0

```solidity
File: src/rollup/RollupCreator.sol


20          event RollupCreated(
33          event TemplatesUpdated();


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/rollup/RollupCreator.sol#L0:0

</details>

## NC012 - State variable declarations should have Natspec @notice annotations:

Explain to an end user what this does


<details>
<summary>Click to show 13 findings</summary>

```solidity
File: src/assertionStakingPool/AbsBoldStakingPool.sol


20          address public immutable stakeToken;
22          mapping(address => uint256) public depositBalance;


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/assertionStakingPool/AbsBoldStakingPool.sol#L0:0

```solidity
File: src/assertionStakingPool/AssertionStakingPool.sol


25          address public immutable rollup;
27          bytes32 public immutable assertionHash;


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/assertionStakingPool/AssertionStakingPool.sol#L0:0

```solidity
File: src/assertionStakingPool/EdgeStakingPool.sol


29          address public immutable challengeManager;
31          bytes32 public immutable edgeId;


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/assertionStakingPool/EdgeStakingPool.sol#L0:0

```solidity
File: src/bridge/DelayBuffer.sol


17          uint256 public constant BASIS = 10000;


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/bridge/DelayBuffer.sol#L0:0

```solidity
File: src/bridge/SequencerInbox.sol


65          uint256 public totalDelayedMessagesRead;
67          IBridge public bridge;
70          uint256 public constant HEADER_LENGTH = 40;
73          bytes1 public constant DATA_AUTHENTICATED_FLAG = 0x40;
76          bytes1 public constant DATA_BLOB_HEADER_FLAG = DATA_AUTHENTICATED_FLAG | 0x10;
79          bytes1 public constant DAS_MESSAGE_HEADER_FLAG = 0x80;
82          bytes1 public constant TREE_DAS_MESSAGE_HEADER_FLAG = 0x08;
85          bytes1 public constant BROTLI_MESSAGE_HEADER_FLAG = 0x00;
88          bytes1 public constant ZERO_HEAVY_MESSAGE_HEADER_FLAG = 0x20;
91          uint256 internal constant GAS_PER_BLOB = 1 << 17;
93          IOwnable public rollup;
95          mapping(address => bool) public isBatchPoster;
99          ISequencerInbox.MaxTimeVariation private __LEGACY_MAX_TIME_VARIATION;
101         mapping(bytes32 => DasKeySetInfo) public dasKeySetInfo;
115         mapping(address => bool) public isSequencer;
116         IReader4844 public immutable reader4844;
119         uint64 internal delayBlocks;
120         uint64 internal futureBlocks;
121         uint64 internal delaySeconds;
122         uint64 internal futureSeconds;
125         address public batchPosterManager;
128         uint256 public immutable maxDataSize;
129         uint256 internal immutable deployTimeChainId = block.chainid;
131         bool internal immutable hostChainIsArbitrum = ArbitrumChecker.runningOnArbitrum();
133         bool public immutable isUsingFeeToken;
135         bool public immutable isDelayBufferable;
138         BufferData public buffer;


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/bridge/SequencerInbox.sol#L0:0

```solidity
File: src/challengeV2/EdgeChallengeManager.sol


266         EdgeStore internal store;
288         IOneStepProofEntry public override oneStepProofEntry;


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/challengeV2/EdgeChallengeManager.sol#L0:0

```solidity
File: src/challengeV2/libraries/EdgeChallengeManagerLib.sol


135         bytes32 public constant UNRIVALED = keccak256(abi.encodePacked("UNRIVALED"));


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/challengeV2/libraries/EdgeChallengeManagerLib.sol#L0:0

```solidity
File: src/challengeV2/libraries/MerkleTreeLib.sol


104         uint256 public constant MAX_LEVEL = 64;


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/challengeV2/libraries/MerkleTreeLib.sol#L0:0

```solidity
File: src/rollup/BOLDUpgradeAction.sol


99          mapping(bytes32 => bytes) internal preImages;
124         IOldRollup public immutable rollup;
167         uint256[] _array;
185         uint256 public immutable BLOCK_LEAF_SIZE;
186         uint256 public immutable BIGSTEP_LEAF_SIZE;
187         uint256 public immutable SMALLSTEP_LEAF_SIZE;
188         uint8 public immutable NUM_BIGSTEP_LEVEL;
190         address public immutable L1_TIMELOCK;
191         IOldRollup public immutable OLD_ROLLUP;
192         address public immutable BRIDGE;
193         address public immutable SEQ_INBOX;
194         address public immutable REI;
195         address public immutable OUTBOX;
196         address public immutable INBOX;
198         uint64 public immutable CONFIRM_PERIOD_BLOCKS;
199         uint64 public immutable CHALLENGE_PERIOD_BLOCKS;
200         address public immutable STAKE_TOKEN;
201         uint256 public immutable STAKE_AMOUNT;
202         uint256 public immutable CHAIN_ID;
203         address public immutable ANY_TRUST_FAST_CONFIRMER;
204         bool public immutable DISABLE_VALIDATOR_WHITELIST;
205         uint64 public immutable CHALLENGE_GRACE_PERIOD_BLOCKS;
206         address public immutable MINI_STAKE_AMOUNTS_STORAGE;
207         bool public immutable IS_DELAY_BUFFERABLE;
209         uint64 public immutable MAX;
210         uint64 public immutable THRESHOLD;
211         uint64 public immutable REPLENISH_RATE_IN_BASIS;
213         IOneStepProofEntry public immutable OSP;
215         ProxyAdmin public immutable PROXY_ADMIN_OUTBOX;
216         ProxyAdmin public immutable PROXY_ADMIN_BRIDGE;
217         ProxyAdmin public immutable PROXY_ADMIN_REI;
218         ProxyAdmin public immutable PROXY_ADMIN_SEQUENCER_INBOX;
219         ProxyAdmin public immutable PROXY_ADMIN_INBOX;
220         StateHashPreImageLookup public immutable PREIMAGE_LOOKUP;
221         RollupReader public immutable ROLLUP_READER;
224         address public immutable IMPL_BRIDGE;
225         address public immutable IMPL_SEQUENCER_INBOX;
226         address public immutable IMPL_INBOX;
227         address public immutable IMPL_REI;
228         address public immutable IMPL_OUTBOX;
230         address public immutable IMPL_PATCHED_OLD_ROLLUP_USER;
231         address public immutable IMPL_NEW_ROLLUP_USER;
232         address public immutable IMPL_NEW_ROLLUP_ADMIN;
233         address public immutable IMPL_CHALLENGE_MANAGER;


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/rollup/BOLDUpgradeAction.sol#L0:0

```solidity
File: src/rollup/BridgeCreator.sol


22          BridgeTemplates public ethBasedTemplates;
23          BridgeTemplates public erc20BasedTemplates;


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/rollup/BridgeCreator.sol#L0:0

```solidity
File: src/rollup/RollupCore.sol


27          uint256 public chainId;
31          uint64 public confirmPeriodBlocks;
74          uint256 public baseStake;
76          bytes32 public wasmModuleRoot;
78          IEdgeChallengeManager public challengeManager;
82          uint64 public challengeGracePeriodBlocks;
84          IInboxBase public inbox;
85          IBridge public bridge;
86          IOutbox public outbox;
87          IRollupEventInbox public rollupEventInbox;
89          address public validatorWalletCreator;
92          address public loserStakeEscrow;
93          address public stakeToken;
94          uint256 public minimumAssertionPeriod;
96          mapping(address => bool) public isValidator;
98          bytes32 private _latestConfirmed;
99          mapping(bytes32 => AssertionNode) private _assertions;
101         address[] private _stakerList;
102         mapping(address => Staker) public _stakerMap;
104         mapping(address => uint256) private _withdrawableFunds;
105         uint256 public totalWithdrawableFunds;
106         uint256 public rollupDeploymentBlock;
108         bool public validatorWhitelistDisabled;
109         address public anyTrustFastConfirmer;
112         bool internal immutable _hostChainIsArbitrum = ArbitrumChecker.runningOnArbitrum();
114         mapping(bytes32 => uint256) internal _assertionCreatedAtArbSysBlock;


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/rollup/RollupCore.sol#L0:0

```solidity
File: src/rollup/RollupCreator.sol


47          BridgeCreator public bridgeCreator;
48          IOneStepProofEntry public osp;
49          IEdgeChallengeManager public challengeManagerTemplate;
50          IRollupAdmin public rollupAdminLogic;
51          IRollupUser public rollupUserLogic;
52          IUpgradeExecutor public upgradeExecutorLogic;
54          address public validatorWalletCreator;
56          DeployHelper public l2FactoriesDeployer;


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/rollup/RollupCreator.sol#L0:0

```solidity
File: src/rollup/RollupUserLogic.sol


31          uint256 internal immutable deployTimeChainId = block.chainid;


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/rollup/RollupUserLogic.sol#L0:0

</details>

## NC013 - State variable declarations should have Natspec @dev annotations:

Explain to a developer any extra details


<details>
<summary>Click to show 12 findings</summary>

```solidity
File: src/assertionStakingPool/AbsBoldStakingPool.sol


20          address public immutable stakeToken;
22          mapping(address => uint256) public depositBalance;


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/assertionStakingPool/AbsBoldStakingPool.sol#L0:0

```solidity
File: src/assertionStakingPool/AssertionStakingPool.sol


25          address public immutable rollup;
27          bytes32 public immutable assertionHash;


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/assertionStakingPool/AssertionStakingPool.sol#L0:0

```solidity
File: src/assertionStakingPool/EdgeStakingPool.sol


29          address public immutable challengeManager;
31          bytes32 public immutable edgeId;


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/assertionStakingPool/EdgeStakingPool.sol#L0:0

```solidity
File: src/bridge/DelayBuffer.sol


17          uint256 public constant BASIS = 10000;


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/bridge/DelayBuffer.sol#L0:0

```solidity
File: src/bridge/SequencerInbox.sol


65          uint256 public totalDelayedMessagesRead;
67          IBridge public bridge;
70          uint256 public constant HEADER_LENGTH = 40;
73          bytes1 public constant DATA_AUTHENTICATED_FLAG = 0x40;
76          bytes1 public constant DATA_BLOB_HEADER_FLAG = DATA_AUTHENTICATED_FLAG | 0x10;
79          bytes1 public constant DAS_MESSAGE_HEADER_FLAG = 0x80;
82          bytes1 public constant TREE_DAS_MESSAGE_HEADER_FLAG = 0x08;
85          bytes1 public constant BROTLI_MESSAGE_HEADER_FLAG = 0x00;
88          bytes1 public constant ZERO_HEAVY_MESSAGE_HEADER_FLAG = 0x20;
91          uint256 internal constant GAS_PER_BLOB = 1 << 17;
93          IOwnable public rollup;
95          mapping(address => bool) public isBatchPoster;
99          ISequencerInbox.MaxTimeVariation private __LEGACY_MAX_TIME_VARIATION;
101         mapping(bytes32 => DasKeySetInfo) public dasKeySetInfo;
115         mapping(address => bool) public isSequencer;
116         IReader4844 public immutable reader4844;
119         uint64 internal delayBlocks;
120         uint64 internal futureBlocks;
121         uint64 internal delaySeconds;
122         uint64 internal futureSeconds;
125         address public batchPosterManager;
128         uint256 public immutable maxDataSize;
129         uint256 internal immutable deployTimeChainId = block.chainid;
131         bool internal immutable hostChainIsArbitrum = ArbitrumChecker.runningOnArbitrum();
133         bool public immutable isUsingFeeToken;
135         bool public immutable isDelayBufferable;
138         BufferData public buffer;


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/bridge/SequencerInbox.sol#L0:0

```solidity
File: src/challengeV2/EdgeChallengeManager.sol


273         address public excessStakeReceiver;
276         IERC20 public stakeToken;
279         uint256[] public stakeAmounts;
282         uint64 public challengePeriodBlocks;
285         IAssertionChain public assertionChain;
288         IOneStepProofEntry public override oneStepProofEntry;
291         uint256 public LAYERZERO_BLOCKEDGE_HEIGHT;
293         uint256 public LAYERZERO_BIGSTEPEDGE_HEIGHT;
295         uint256 public LAYERZERO_SMALLSTEPEDGE_HEIGHT;
298         uint8 public NUM_BIGSTEP_LEVEL;


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/challengeV2/EdgeChallengeManager.sol#L0:0

```solidity
File: src/challengeV2/libraries/MerkleTreeLib.sol


104         uint256 public constant MAX_LEVEL = 64;


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/challengeV2/libraries/MerkleTreeLib.sol#L0:0

```solidity
File: src/rollup/BOLDUpgradeAction.sol


99          mapping(bytes32 => bytes) internal preImages;
124         IOldRollup public immutable rollup;
167         uint256[] _array;
185         uint256 public immutable BLOCK_LEAF_SIZE;
186         uint256 public immutable BIGSTEP_LEAF_SIZE;
187         uint256 public immutable SMALLSTEP_LEAF_SIZE;
188         uint8 public immutable NUM_BIGSTEP_LEVEL;
190         address public immutable L1_TIMELOCK;
191         IOldRollup public immutable OLD_ROLLUP;
192         address public immutable BRIDGE;
193         address public immutable SEQ_INBOX;
194         address public immutable REI;
195         address public immutable OUTBOX;
196         address public immutable INBOX;
198         uint64 public immutable CONFIRM_PERIOD_BLOCKS;
199         uint64 public immutable CHALLENGE_PERIOD_BLOCKS;
200         address public immutable STAKE_TOKEN;
201         uint256 public immutable STAKE_AMOUNT;
202         uint256 public immutable CHAIN_ID;
203         address public immutable ANY_TRUST_FAST_CONFIRMER;
204         bool public immutable DISABLE_VALIDATOR_WHITELIST;
205         uint64 public immutable CHALLENGE_GRACE_PERIOD_BLOCKS;
206         address public immutable MINI_STAKE_AMOUNTS_STORAGE;
207         bool public immutable IS_DELAY_BUFFERABLE;
209         uint64 public immutable MAX;
210         uint64 public immutable THRESHOLD;
211         uint64 public immutable REPLENISH_RATE_IN_BASIS;
213         IOneStepProofEntry public immutable OSP;
215         ProxyAdmin public immutable PROXY_ADMIN_OUTBOX;
216         ProxyAdmin public immutable PROXY_ADMIN_BRIDGE;
217         ProxyAdmin public immutable PROXY_ADMIN_REI;
218         ProxyAdmin public immutable PROXY_ADMIN_SEQUENCER_INBOX;
219         ProxyAdmin public immutable PROXY_ADMIN_INBOX;
220         StateHashPreImageLookup public immutable PREIMAGE_LOOKUP;
221         RollupReader public immutable ROLLUP_READER;
224         address public immutable IMPL_BRIDGE;
225         address public immutable IMPL_SEQUENCER_INBOX;
226         address public immutable IMPL_INBOX;
227         address public immutable IMPL_REI;
228         address public immutable IMPL_OUTBOX;
230         address public immutable IMPL_PATCHED_OLD_ROLLUP_USER;
231         address public immutable IMPL_NEW_ROLLUP_USER;
232         address public immutable IMPL_NEW_ROLLUP_ADMIN;
233         address public immutable IMPL_CHALLENGE_MANAGER;


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/rollup/BOLDUpgradeAction.sol#L0:0

```solidity
File: src/rollup/BridgeCreator.sol


22          BridgeTemplates public ethBasedTemplates;
23          BridgeTemplates public erc20BasedTemplates;


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/rollup/BridgeCreator.sol#L0:0

```solidity
File: src/rollup/RollupCore.sol


27          uint256 public chainId;
31          uint64 public confirmPeriodBlocks;
74          uint256 public baseStake;
76          bytes32 public wasmModuleRoot;
78          IEdgeChallengeManager public challengeManager;
82          uint64 public challengeGracePeriodBlocks;
84          IInboxBase public inbox;
85          IBridge public bridge;
86          IOutbox public outbox;
87          IRollupEventInbox public rollupEventInbox;
89          address public validatorWalletCreator;
92          address public loserStakeEscrow;
93          address public stakeToken;
94          uint256 public minimumAssertionPeriod;
96          mapping(address => bool) public isValidator;
98          bytes32 private _latestConfirmed;
99          mapping(bytes32 => AssertionNode) private _assertions;
101         address[] private _stakerList;
102         mapping(address => Staker) public _stakerMap;
104         mapping(address => uint256) private _withdrawableFunds;
105         uint256 public totalWithdrawableFunds;
106         uint256 public rollupDeploymentBlock;
108         bool public validatorWhitelistDisabled;
109         address public anyTrustFastConfirmer;
112         bool internal immutable _hostChainIsArbitrum = ArbitrumChecker.runningOnArbitrum();
114         mapping(bytes32 => uint256) internal _assertionCreatedAtArbSysBlock;


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/rollup/RollupCore.sol#L0:0

```solidity
File: src/rollup/RollupCreator.sol


47          BridgeCreator public bridgeCreator;
48          IOneStepProofEntry public osp;
49          IEdgeChallengeManager public challengeManagerTemplate;
50          IRollupAdmin public rollupAdminLogic;
51          IRollupUser public rollupUserLogic;
52          IUpgradeExecutor public upgradeExecutorLogic;
54          address public validatorWalletCreator;
56          DeployHelper public l2FactoriesDeployer;


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/rollup/RollupCreator.sol#L0:0

```solidity
File: src/rollup/RollupUserLogic.sol


31          uint256 internal immutable deployTimeChainId = block.chainid;
49          uint256 public constant VALIDATOR_AFK_BLOCKS = 201600;


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/rollup/RollupUserLogic.sol#L0:0

</details>

## NC014 - Functions should have Natspec @return annotations:

Documents the return variables of a contract’s function


<details>
<summary>Click to show 28 findings</summary>

```solidity
File: src/assertionStakingPool/AssertionStakingPoolCreator.sol


15          function createPool(
25          function getPool(


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/assertionStakingPool/AssertionStakingPoolCreator.sol#L0:0

```solidity
File: src/assertionStakingPool/EdgeStakingPoolCreator.sol


15          function createPool(
25          function getPool(


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/assertionStakingPool/EdgeStakingPoolCreator.sol#L0:0

```solidity
File: src/assertionStakingPool/StakingPoolCreatorUtils.sol


13          function getPool(bytes memory creationCode, bytes memory args) internal view returns (address) {


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/assertionStakingPool/StakingPoolCreatorUtils.sol#L0:0

```solidity
File: src/assertionStakingPool/interfaces/IAbsBoldStakingPool.sol


30          function stakeToken() external view returns (address);
34          function depositBalance(address account) external view returns (uint256);


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/assertionStakingPool/interfaces/IAbsBoldStakingPool.sol#L0:0

```solidity
File: src/assertionStakingPool/interfaces/IAssertionStakingPool.sol


27          function rollup() external view returns (address);
30          function assertionHash() external view returns (bytes32);


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/assertionStakingPool/interfaces/IAssertionStakingPool.sol#L0:0

```solidity
File: src/assertionStakingPool/interfaces/IAssertionStakingPoolCreator.sol


21          function createPool(
29          function getPool(


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/assertionStakingPool/interfaces/IAssertionStakingPoolCreator.sol#L0:0

```solidity
File: src/assertionStakingPool/interfaces/IEdgeStakingPool.sol


18          function challengeManager() external view returns (address);
21          function edgeId() external view returns (bytes32);


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/assertionStakingPool/interfaces/IEdgeStakingPool.sol#L0:0

```solidity
File: src/assertionStakingPool/interfaces/IEdgeStakingPoolCreator.sol


16          function createPool(
24          function getPool(


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/assertionStakingPool/interfaces/IEdgeStakingPoolCreator.sol#L0:0

```solidity
File: src/bridge/DelayBuffer.sol


33          function calcBuffer(
82          function calcPendingBuffer(BufferData storage self, uint64 blockNumber)
104         function isSynced(BufferData storage self) internal view returns (bool) {
108         function isUpdatable(BufferData storage self) internal view returns (bool) {
115         function isValidBufferConfig(BufferConfig memory config) internal pure returns (bool) {


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/bridge/DelayBuffer.sol#L0:0

```solidity
File: src/bridge/ISequencerInbox.sol


49          function totalDelayedMessagesRead() external view returns (uint256);
51          function bridge() external view returns (IBridge);
55          function HEADER_LENGTH() external view returns (uint256);
61          function DATA_AUTHENTICATED_FLAG() external view returns (bytes1);
67          function DATA_BLOB_HEADER_FLAG() external view returns (bytes1);
73          function DAS_MESSAGE_HEADER_FLAG() external view returns (bytes1);
79          function TREE_DAS_MESSAGE_HEADER_FLAG() external view returns (bytes1);
85          function BROTLI_MESSAGE_HEADER_FLAG() external view returns (bytes1);
91          function ZERO_HEAVY_MESSAGE_HEADER_FLAG() external view returns (bytes1);
93          function rollup() external view returns (IOwnable);
95          function isBatchPoster(address) external view returns (bool);
97          function isSequencer(address) external view returns (bool);
100         function isDelayBufferable() external view returns (bool);
102         function maxDataSize() external view returns (uint256);
106         function batchPosterManager() external view returns (address);
114         function maxTimeVariation()
124         function dasKeySetInfo(bytes32) external view returns (bool, uint64);
148         function inboxAccs(uint256 index) external view returns (bytes32);
150         function batchCount() external view returns (uint256);
152         function isValidKeysetHash(bytes32 ksHash) external view returns (bool);
155         function getKeysetCreationBlock(bytes32 ksHash) external view returns (uint256);


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/bridge/ISequencerInbox.sol#L0:0

```solidity
File: src/bridge/SequencerInbox.sol


157         function _chainIdChanged() internal view returns (bool) {
216         function getTimeBounds() internal view virtual returns (IBridge.TimeBounds memory) {
244         function maxTimeVariation()
269         function maxTimeVariationInternal()
628         function isDelayProofRequired(uint256 afterDelayedMessagesRead) internal view returns (bool) {
637         function packHeader(uint256 afterDelayedMessagesRead)
675         function isValidCallDataFlag(bytes1 headerByte) internal pure returns (bool) {
791         function addSequencerL2BatchImpl(
824         function inboxAccs(uint256 index) external view returns (bytes32) {
828         function batchCount() external view returns (uint256) {
833         function forceInclusionDeadline(uint64 blockNumber) external view returns (uint64) {
843         function delayBufferableBlocks(uint64 _buffer) internal view returns (uint64) {
952         function isValidKeysetHash(bytes32 ksHash) external view returns (bool) {
957         function getKeysetCreationBlock(bytes32 ksHash) external view returns (uint256) {


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/bridge/SequencerInbox.sol#L0:0

```solidity
File: src/challengeV2/EdgeChallengeManager.sol


47          function challengePeriodBlocks() external view returns (uint64);
50          function oneStepProofEntry() external view returns (IOneStepProofEntry);
54          function createLayerZeroEdge(CreateEdgeArgs calldata args) external returns (bytes32);
123         function getLayerZeroEndHeight(EdgeType eType) external view returns (uint256);
132         function calculateEdgeId(
148         function calculateMutualId(
157         function edgeExists(bytes32 edgeId) external view returns (bool);
160         function getEdge(bytes32 edgeId) external view returns (ChallengeEdge memory);
163         function edgeLength(bytes32 edgeId) external view returns (uint256);
167         function hasRival(bytes32 edgeId) external view returns (bool);
171         function confirmedRival(bytes32 mutualId) external view returns (bytes32);
174         function hasLengthOneRival(bytes32 edgeId) external view returns (bool);
180         function timeUnrivaled(bytes32 edgeId) external view returns (uint256);
185         function getPrevAssertionHash(bytes32 edgeId) external view returns (bytes32);
191         function firstRival(bytes32 mutualId) external view returns (bytes32);
195         function hasMadeLayerZeroRival(address account, bytes32 mutualId) external view returns (bool);
371         function createLayerZeroEdge(CreateEdgeArgs calldata args) external returns (bytes32) {
451         function bisectEdge(bytes32 edgeId, bytes32 bisectionHistoryRoot, bytes calldata prefixProof)
591         function getLayerZeroEndHeight(EdgeType eType) public view returns (uint256) {
604         function calculateEdgeId(
616         function calculateMutualId(
627         function edgeExists(bytes32 edgeId) public view returns (bool) {
632         function getEdge(bytes32 edgeId) public view returns (ChallengeEdge memory) {
637         function edgeLength(bytes32 edgeId) public view returns (uint256) {
642         function hasRival(bytes32 edgeId) public view returns (bool) {
647         function confirmedRival(bytes32 mutualId) public view returns (bytes32) {
652         function hasLengthOneRival(bytes32 edgeId) public view returns (bool) {
657         function timeUnrivaled(bytes32 edgeId) public view returns (uint256) {
662         function getPrevAssertionHash(bytes32 edgeId) public view returns (bytes32) {
667         function firstRival(bytes32 mutualId) public view returns (bytes32) {
672         function hasMadeLayerZeroRival(address account, bytes32 mutualId) external view returns (bool) {


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/challengeV2/EdgeChallengeManager.sol#L0:0

```solidity
File: src/challengeV2/IAssertionChain.sol


14          function bridge() external view returns (IBridge);
22          function getFirstChildCreationBlock(bytes32 assertionHash) external view returns (uint64);
23          function getSecondChildCreationBlock(bytes32 assertionHash) external view returns (uint64);
24          function isFirstChild(bytes32 assertionHash) external view returns (bool);
25          function isPending(bytes32 assertionHash) external view returns (bool);
26          function isValidator(address) external view returns (bool);
27          function validatorWhitelistDisabled() external view returns (bool);


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/challengeV2/IAssertionChain.sol#L0:0

```solidity
File: src/challengeV2/libraries/ArrayUtilsLib.sol


13          function append(bytes32[] memory arr, bytes32 newItem) internal pure returns (bytes32[] memory) {
27          function slice(bytes32[] memory arr, uint256 startIndex, uint256 endIndex)
45          function concat(bytes32[] memory arr1, bytes32[] memory arr2) internal pure returns (bytes32[] memory) {


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/challengeV2/libraries/ArrayUtilsLib.sol#L0:0

```solidity
File: src/challengeV2/libraries/ChallengeEdgeLib.sol


93          function newLayerZeroEdge(
133         function newChildEdge(
166         function mutualIdComponent(
180         function mutualId(ChallengeEdge storage ce) internal view returns (bytes32) {
184         function mutualIdMem(ChallengeEdge memory ce) internal pure returns (bytes32) {
189         function idComponent(
208         function idMem(ChallengeEdge memory edge) internal pure returns (bytes32) {
215         function id(ChallengeEdge storage edge) internal view returns (bytes32) {
222         function exists(ChallengeEdge storage edge) internal view returns (bool) {
228         function length(ChallengeEdge storage edge) internal view returns (uint256) {
258         function isLayerZero(ChallengeEdge storage edge) internal view returns (bool) {
279         function levelToType(uint8 level, uint8 numBigStepLevels) internal pure returns (EdgeType eType) {


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/challengeV2/libraries/ChallengeEdgeLib.sol#L0:0

```solidity
File: src/challengeV2/libraries/EdgeChallengeManagerLib.sol


141         function get(EdgeStore storage store, bytes32 edgeId) internal view returns (ChallengeEdge storage) {
152         function getNoCheck(EdgeStore storage store, bytes32 edgeId) internal view returns (ChallengeEdge storage) {
160         function add(EdgeStore storage store, ChallengeEdge memory edge) internal returns (EdgeAddedData memory) {
327         function isPowerOfTwo(uint256 x) internal pure returns (bool) {
344         function layerZeroCommonChecks(ProofData memory proofData, CreateEdgeArgs calldata args, uint256 expectedEndHeight)
391         function toLayerZeroEdge(bytes32 originId, bytes32 startHistoryRoot, CreateEdgeArgs calldata args)
411         function createLayerZeroEdge(
443         function getPrevAssertionHash(EdgeStore storage store, bytes32 edgeId) internal view returns (bytes32) {
463         function hasRival(EdgeStore storage store, bytes32 edgeId) internal view returns (bool) {
483         function hasLengthOneRival(EdgeStore storage store, bytes32 edgeId) internal view returns (bool) {
488         function timeUnrivaledTotal(EdgeStore storage store, bytes32 edgeId) internal view returns (uint256) {
516         function updateTimerCacheByChildren(EdgeStore storage store, bytes32 edgeId) internal returns (bool, uint256) {
520         function updateTimerCacheByClaim(
537         function timeUnrivaled(EdgeStore storage store, bytes32 edgeId) internal view returns (uint256) {
576         function mandatoryBisectionHeight(uint256 start, uint256 end) internal pure returns (uint256) {
674         function nextEdgeLevel(uint8 level, uint8 numBigStepLevel) internal pure returns (uint8) {
723         function confirmEdgeByTime(


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/challengeV2/libraries/EdgeChallengeManagerLib.sol#L0:0

```solidity
File: src/challengeV2/libraries/MerkleTreeLib.sol


110         function root(bytes32[] memory me) internal pure returns (bytes32) {
151         function appendCompleteSubTree(bytes32[] memory me, uint256 level, bytes32 subtreeRoot)
238         function appendLeaf(bytes32[] memory me, bytes32 leaf) internal pure returns (bytes32[] memory) {
251         function maximumAppendBetween(uint256 startSize, uint256 endSize) internal pure returns (uint256) {
292         function treeSize(bytes32[] memory me) internal pure returns (uint256) {


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/challengeV2/libraries/MerkleTreeLib.sol#L0:0

```solidity
File: src/challengeV2/libraries/UintUtilsLib.sol


14          function leastSignificantBit(uint256 x) internal pure returns (uint256 msb) {
29          function mostSignificantBit(uint256 x) internal pure returns (uint256 msb) {


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/challengeV2/libraries/UintUtilsLib.sol#L0:0

```solidity
File: src/rollup/Assertion.sol


70          function createAssertion(


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/rollup/Assertion.sol#L0:0

```solidity
File: src/rollup/AssertionState.sol


18          function toExecutionState(AssertionState memory state) internal pure returns (ExecutionState memory) {
22          function hash(AssertionState memory state) internal pure returns (bytes32) {


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/rollup/AssertionState.sol#L0:0

```solidity
File: src/rollup/BOLDUpgradeAction.sol


67          function wasmModuleRoot() external view returns (bytes32);
68          function latestConfirmed() external view returns (uint64);
69          function getNode(uint64 nodeNum) external view returns (Node memory);
70          function getStakerAddress(uint64 stakerNum) external view returns (address);
71          function stakerCount() external view returns (uint64);
72          function getStaker(address staker) external view returns (OldStaker memory);
73          function isValidator(address validator) external view returns (bool);
74          function validatorWalletCreator() external view returns (address);
101         function stateHash(ExecutionState calldata executionState, uint256 inboxMaxCount) public pure returns (bytes32) {
112         function get(bytes32 h) public view returns (ExecutionState memory executionState, uint256 inboxMaxCount) {
130         function wasmModuleRoot() external view returns (bytes32) {
134         function latestConfirmed() external view returns (uint64) {
138         function getNode(uint64 nodeNum) external view returns (Node memory) {
142         function getStakerAddress(uint64 stakerNum) external view returns (address) {
146         function stakerCount() external view returns (uint64) {
150         function getStaker(address staker) external view returns (OldStaker memory) {
154         function isValidator(address validator) external view returns (bool) {
158         function validatorWalletCreator() external view returns (address) {
173         function array() public view returns (uint256[] memory) {
367         function createConfig() private view returns (Config memory) {


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/rollup/BOLDUpgradeAction.sol#L0:0

```solidity
File: src/rollup/BridgeCreator.sol


63          function _createBridge(
99          function createBridge(


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/rollup/BridgeCreator.sol#L0:0

```solidity
File: src/rollup/IRollupCore.sol


48          function confirmPeriodBlocks() external view returns (uint64);
50          function chainId() external view returns (uint256);
52          function baseStake() external view returns (uint256);
54          function wasmModuleRoot() external view returns (bytes32);
56          function bridge() external view returns (IBridge);
58          function sequencerInbox() external view returns (ISequencerInbox);
60          function outbox() external view returns (IOutbox);
62          function rollupEventInbox() external view returns (IRollupEventInbox);
64          function challengeManager() external view returns (IEdgeChallengeManager);
66          function loserStakeEscrow() external view returns (address);
68          function stakeToken() external view returns (address);
70          function minimumAssertionPeriod() external view returns (uint256);
72          function genesisAssertionHash() external pure returns (bytes32);
77          function getAssertion(bytes32 assertionHash) external view returns (AssertionNode memory);
86          function getAssertionCreationBlockForLogLookup(bytes32 assertionHash) external view returns (uint256);


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/rollup/IRollupCore.sol#L0:0

```solidity
File: src/rollup/IRollupLogic.sol


36          function withdrawStakerFunds() external returns (uint256);


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/rollup/IRollupLogic.sol#L0:0

```solidity
File: src/rollup/RollupCore.sol


116         function sequencerInbox() public view virtual returns (ISequencerInbox) {
134         function getAssertion(bytes32 assertionHash) public view override returns (AssertionNode memory) {
145         function getAssertionCreationBlockForLogLookup(bytes32 assertionHash) external view override returns (uint256) {
365         function createNewAssertion(
520         function genesisAssertionHash() external pure returns (bytes32) {
532         function getFirstChildCreationBlock(bytes32 assertionHash) external view returns (uint64) {
536         function getSecondChildCreationBlock(bytes32 assertionHash) external view returns (uint64) {
553         function isFirstChild(bytes32 assertionHash) external view returns (bool) {
557         function isPending(bytes32 assertionHash) external view returns (bool) {


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/rollup/RollupCore.sol#L0:0

```solidity
File: src/rollup/RollupCreator.sol


85          function createChallengeManager(address rollupAddr, address proxyAdminAddr, Config memory config)
267         function _deployUpgradeExecutor(address rollupOwner, ProxyAdmin proxyAdmin)


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/rollup/RollupCreator.sol#L0:0

```solidity
File: src/rollup/RollupLib.sol


23          function assertionHash(
37          function assertionHash(
54          function configHash(


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/rollup/RollupLib.sol#L0:0

```solidity
File: src/rollup/RollupUserLogic.sol


33          function _chainIdChanged() internal view returns (bool) {
51          function _validatorIsAfk() internal view returns (bool) {
150         function computeAssertionHash(bytes32 prevAssertionHash, AssertionState calldata state, bytes32 inboxAcc)
308         function owner() external view returns (address) {
358         function withdrawStakerFunds() external override whenNotPaused returns (uint256) {


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/rollup/RollupUserLogic.sol#L0:0

</details>

## NC015 - Functions should have Natspec @param annotations:

Documents a parameter just like in Doxygen (must be followed by parameter name)


<details>
<summary>Click to show 21 findings</summary>

```solidity
File: src/assertionStakingPool/AbsBoldStakingPool.sol


24          constructor(address _stakeToken) {
29          function depositIntoPool(uint256 amount) external {
41          function withdrawFromPool(uint256 amount) public {
57          function withdrawFromPool() external {


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/assertionStakingPool/AbsBoldStakingPool.sol#L0:0

```solidity
File: src/assertionStakingPool/AssertionStakingPool.sol


40          function createAssertion(AssertionInputs calldata assertionInputs) external {
49          function makeStakeWithdrawable() public {
55          function withdrawStakeBackIntoPool() public {
60          function makeStakeWithdrawableAndWithdrawBackIntoPool() external {


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/assertionStakingPool/AssertionStakingPool.sol#L0:0

```solidity
File: src/assertionStakingPool/AssertionStakingPoolCreator.sol


15          function createPool(
25          function getPool(


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/assertionStakingPool/AssertionStakingPoolCreator.sol#L0:0

```solidity
File: src/assertionStakingPool/EdgeStakingPool.sol


44          function createEdge(CreateEdgeArgs calldata args) external {


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/assertionStakingPool/EdgeStakingPool.sol#L0:0

```solidity
File: src/assertionStakingPool/EdgeStakingPoolCreator.sol


15          function createPool(
25          function getPool(


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/assertionStakingPool/EdgeStakingPoolCreator.sol#L0:0

```solidity
File: src/assertionStakingPool/StakingPoolCreatorUtils.sol


13          function getPool(bytes memory creationCode, bytes memory args) internal view returns (address) {


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/assertionStakingPool/StakingPoolCreatorUtils.sol#L0:0

```solidity
File: src/bridge/DelayBuffer.sol


104         function isSynced(BufferData storage self) internal view returns (bool) {
108         function isUpdatable(BufferData storage self) internal view returns (bool) {
115         function isValidBufferConfig(BufferConfig memory config) internal pure returns (bool) {


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/bridge/DelayBuffer.sol#L0:0

```solidity
File: src/bridge/SequencerInbox.sol


140         constructor(
157         function _chainIdChanged() internal view returns (bool) {
161         function postUpgradeInit(BufferConfig memory bufferConfig_)
177         function initialize(
208         function updateRollupAddress() external {
216         function getTimeBounds() internal view virtual returns (IBridge.TimeBounds memory) {
236         function removeDelayAfterFork() external {
244         function maxTimeVariation()
269         function maxTimeVariationInternal()
287         function forceInclusion(
356         function addSequencerL2BatchFromOrigin(
366         function addSequencerL2BatchFromOrigin(
390         function addSequencerL2BatchFromBlobs(
409         function addSequencerL2BatchFromBlobsDelayProof(
430         function addSequencerL2BatchFromOriginDelayProof(
455         function addSequencerL2BatchFromBlobsImpl(
512         function addSequencerL2BatchFromCalldataImpl(
560         function addSequencerL2Batch(
582         function addSequencerL2BatchDelayProof(
605         function delayProofImpl(uint256 afterDelayedMessagesRead, DelayProof memory delayProof)
628         function isDelayProofRequired(uint256 afterDelayedMessagesRead) internal view returns (bool) {
637         function packHeader(uint256 afterDelayedMessagesRead)
791         function addSequencerL2BatchImpl(
824         function inboxAccs(uint256 index) external view returns (bytes32) {
828         function batchCount() external view returns (uint256) {
833         function forceInclusionDeadline(uint64 blockNumber) external view returns (uint64) {
843         function delayBufferableBlocks(uint64 _buffer) internal view returns (uint64) {
847         function _setBufferConfig(BufferConfig memory bufferConfig_) internal {
867         function _setMaxTimeVariation(ISequencerInbox.MaxTimeVariation memory maxTimeVariation_)
885         function setMaxTimeVariation(ISequencerInbox.MaxTimeVariation memory maxTimeVariation_)
894         function setIsBatchPoster(address addr, bool isBatchPoster_)
903         function setValidKeyset(bytes calldata keysetBytes) external onlyRollupOwner {
922         function invalidateKeysetHash(bytes32 ksHash) external onlyRollupOwner {
933         function setIsSequencer(address addr, bool isSequencer_)
942         function setBatchPosterManager(address newBatchPosterManager) external onlyRollupOwner {
947         function setBufferConfig(BufferConfig memory bufferConfig_) external onlyRollupOwner {
952         function isValidKeysetHash(bytes32 ksHash) external view returns (bool) {
957         function getKeysetCreationBlock(bytes32 ksHash) external view returns (uint256) {


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/bridge/SequencerInbox.sol#L0:0

```solidity
File: src/challengeV2/EdgeChallengeManager.sol


300         constructor() {
305         function initialize(
371         function createLayerZeroEdge(CreateEdgeArgs calldata args) external returns (bytes32) {
451         function bisectEdge(bytes32 edgeId, bytes32 bisectionHistoryRoot, bytes calldata prefixProof)
491         function multiUpdateTimeCacheByChildren(bytes32[] calldata edgeIds) public {
499         function updateTimerCacheByChildren(bytes32 edgeId) public {
505         function updateTimerCacheByClaim(bytes32 edgeId, bytes32 claimingEdgeId) public {
511         function confirmEdgeByTime(bytes32 edgeId, AssertionStateData calldata claimStateData) public {
539         function confirmEdgeByOneStepProof(
572         function refundStake(bytes32 edgeId) public {
591         function getLayerZeroEndHeight(EdgeType eType) public view returns (uint256) {
604         function calculateEdgeId(
616         function calculateMutualId(
627         function edgeExists(bytes32 edgeId) public view returns (bool) {
632         function getEdge(bytes32 edgeId) public view returns (ChallengeEdge memory) {
637         function edgeLength(bytes32 edgeId) public view returns (uint256) {
642         function hasRival(bytes32 edgeId) public view returns (bool) {
647         function confirmedRival(bytes32 mutualId) public view returns (bytes32) {
652         function hasLengthOneRival(bytes32 edgeId) public view returns (bool) {
657         function timeUnrivaled(bytes32 edgeId) public view returns (uint256) {
662         function getPrevAssertionHash(bytes32 edgeId) public view returns (bytes32) {
667         function firstRival(bytes32 mutualId) public view returns (bytes32) {
672         function hasMadeLayerZeroRival(address account, bytes32 mutualId) external view returns (bool) {


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/challengeV2/EdgeChallengeManager.sol#L0:0

```solidity
File: src/challengeV2/libraries/ChallengeEdgeLib.sol


69          function newEdgeChecks(
93          function newLayerZeroEdge(
133         function newChildEdge(
166         function mutualIdComponent(
180         function mutualId(ChallengeEdge storage ce) internal view returns (bytes32) {
184         function mutualIdMem(ChallengeEdge memory ce) internal pure returns (bytes32) {
189         function idComponent(
208         function idMem(ChallengeEdge memory edge) internal pure returns (bytes32) {
215         function id(ChallengeEdge storage edge) internal view returns (bytes32) {
222         function exists(ChallengeEdge storage edge) internal view returns (bool) {
228         function length(ChallengeEdge storage edge) internal view returns (uint256) {
239         function setChildren(ChallengeEdge storage edge, bytes32 lowerChildId, bytes32 upperChildId) internal {
249         function setConfirmed(ChallengeEdge storage edge) internal {
258         function isLayerZero(ChallengeEdge storage edge) internal view returns (bool) {
264         function setRefunded(ChallengeEdge storage edge) internal {
279         function levelToType(uint8 level, uint8 numBigStepLevels) internal pure returns (EdgeType eType) {


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/challengeV2/libraries/ChallengeEdgeLib.sol#L0:0

```solidity
File: src/challengeV2/libraries/EdgeChallengeManagerLib.sol


327         function isPowerOfTwo(uint256 x) internal pure returns (bool) {
391         function toLayerZeroEdge(bytes32 originId, bytes32 startHistoryRoot, CreateEdgeArgs calldata args)
488         function timeUnrivaledTotal(EdgeStore storage store, bytes32 edgeId) internal view returns (uint256) {
502         function updateTimerCache(EdgeStore storage store, bytes32 edgeId, uint256 newValue)
516         function updateTimerCacheByChildren(EdgeStore storage store, bytes32 edgeId) internal returns (bool, uint256) {
520         function updateTimerCacheByClaim(
537         function timeUnrivaled(EdgeStore storage store, bytes32 edgeId) internal view returns (uint256) {
576         function mandatoryBisectionHeight(uint256 start, uint256 end) internal pure returns (uint256) {
662         function setConfirmedRival(EdgeStore storage store, bytes32 edgeId) internal {


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/challengeV2/libraries/EdgeChallengeManagerLib.sol#L0:0

```solidity
File: src/rollup/Assertion.sol


70          function createAssertion(
85          function childCreated(AssertionNode storage self) internal {
93          function requireExists(AssertionNode memory self) internal pure {


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/rollup/Assertion.sol#L0:0

```solidity
File: src/rollup/AssertionState.sol


18          function toExecutionState(AssertionState memory state) internal pure returns (ExecutionState memory) {
22          function hash(AssertionState memory state) internal pure returns (bytes32) {


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/rollup/AssertionState.sol#L0:0

```solidity
File: src/rollup/BOLDUpgradeAction.sol


101         function stateHash(ExecutionState calldata executionState, uint256 inboxMaxCount) public pure returns (bytes32) {
106         function set(bytes32 h, ExecutionState calldata executionState, uint256 inboxMaxCount) public {
112         function get(bytes32 h) public view returns (ExecutionState memory executionState, uint256 inboxMaxCount) {
126         constructor(IOldRollup _rollup) {
130         function wasmModuleRoot() external view returns (bytes32) {
134         function latestConfirmed() external view returns (uint64) {
138         function getNode(uint64 nodeNum) external view returns (Node memory) {
142         function getStakerAddress(uint64 stakerNum) external view returns (address) {
146         function stakerCount() external view returns (uint64) {
150         function getStaker(address staker) external view returns (OldStaker memory) {
154         function isValidator(address validator) external view returns (bool) {
158         function validatorWalletCreator() external view returns (address) {
169         constructor(uint256[] memory __array) {
173         function array() public view returns (uint256[] memory) {
287         constructor(
341         function cleanupOldRollup() private {
367         function createConfig() private view returns (Config memory) {
411         function upgradeSurroundingContracts(address newRollupAddress) private {
433         function upgradeSequencerInbox() private {
464         function perform(address[] memory validators) external {


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/rollup/BOLDUpgradeAction.sol#L0:0

```solidity
File: src/rollup/BridgeCreator.sol


45          constructor(
53          function updateTemplates(BridgeTemplates calldata _newTemplates) external onlyOwner {
58          function updateERC20Templates(BridgeTemplates calldata _newTemplates) external onlyOwner {
63          function _createBridge(
99          function createBridge(


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/rollup/BridgeCreator.sol#L0:0

```solidity
File: src/rollup/RollupAdminLogic.sol


18          function initialize(Config calldata config, ContractDependencies calldata connectedContracts)
150         function pause() external override {
158         function resume() external override {
166         function _authorizeUpgrade(address newImplementation) internal override {}
171         function _authorizeSecondaryUpgrade(address newImplementation) internal override {}
228         function forceRefundStaker(address[] calldata staker) external override whenPaused {
237         function forceCreateAssertion(
258         function forceConfirmAssertion(
269         function setLoserStakeEscrow(address newLoserStakerEscrow) external override {


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/rollup/RollupAdminLogic.sol#L0:0

```solidity
File: src/rollup/RollupCore.sol


116         function sequencerInbox() public view virtual returns (ISequencerInbox) {
134         function getAssertion(bytes32 assertionHash) public view override returns (AssertionNode memory) {
145         function getAssertionCreationBlockForLogLookup(bytes32 assertionHash) external view override returns (uint256) {
212         function latestConfirmed() public view override returns (bytes32) {
217         function stakerCount() public view override returns (uint64) {
236         function confirmAssertionInternal(
365         function createNewAssertion(
520         function genesisAssertionHash() external pure returns (bytes32) {
532         function getFirstChildCreationBlock(bytes32 assertionHash) external view returns (uint64) {
536         function getSecondChildCreationBlock(bytes32 assertionHash) external view returns (uint64) {
540         function validateAssertionHash(
549         function validateConfig(bytes32 assertionHash, ConfigData calldata configData) external view {
553         function isFirstChild(bytes32 assertionHash) external view returns (bool) {
557         function isPending(bytes32 assertionHash) external view returns (bool) {


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/rollup/RollupCore.sol#L0:0

```solidity
File: src/rollup/RollupCreator.sol


58          constructor() Ownable() {}
61          receive() external payable {}
63          function setTemplates(
85          function createChallengeManager(address rollupAddr, address proxyAdminAddr, Config memory config)
267         function _deployUpgradeExecutor(address rollupOwner, ProxyAdmin proxyAdmin)
287         function _deployFactories(


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/rollup/RollupCreator.sol#L0:0

```solidity
File: src/rollup/RollupLib.sol


23          function assertionHash(
37          function assertionHash(
54          function configHash(
73          function validateConfigHash(


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/rollup/RollupLib.sol#L0:0

```solidity
File: src/rollup/RollupProxy.sol


12          function initializeProxy(Config memory config, ContractDependencies memory connectedContracts)


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/rollup/RollupProxy.sol#L0:0

```solidity
File: src/rollup/RollupUserLogic.sol


27          function initialize(address _stakeToken) external view override onlyProxy {
33          function _chainIdChanged() internal view returns (bool) {
51          function _validatorIsAfk() internal view returns (bool) {
62          function removeWhitelistAfterFork() external {
71          function removeWhitelistAfterValidatorAfk() external {
222         function returnOldDeposit() external override onlyValidator whenNotPaused {
252         function fastConfirmAssertion(
273         function fastConfirmNewAssertion(AssertionInputs calldata assertion, bytes32 expectedAssertionHash)
308         function owner() external view returns (address) {
316         function newStakeOnNewAssertion(
358         function withdrawStakerFunds() external override whenNotPaused returns (uint256) {
366         function receiveTokens(uint256 tokenAmount) private {


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/rollup/RollupUserLogic.sol#L0:0

</details>

## NC016 - Missing events in sensitive functions:

Sensitive setter functions in smart contracts often alter critical state variables. Without events emitted in these functions, external observers or dApps cannot easily track or react to these state changes. Missing events can obscure contract activity, hampering transparency and making integration more challenging. To resolve this, incorporate appropriate event emissions within these functions. Events offer an efficient way to log crucial changes, aiding in real-time tracking and post-transaction verification..


```solidity
File: src/bridge/SequencerInbox.sol


847         function _setBufferConfig(BufferConfig memory bufferConfig_) internal {
848             if (!isDelayBufferable) revert NotDelayBufferable();
849             if (!DelayBuffer.isValidBufferConfig(bufferConfig_)) revert BadBufferConfig();
850     
851             if (buffer.bufferBlocks == 0 || buffer.bufferBlocks > bufferConfig_.max) {
852                 buffer.bufferBlocks = bufferConfig_.max;
853             }
854             if (buffer.bufferBlocks < bufferConfig_.threshold) {
855                 buffer.bufferBlocks = bufferConfig_.threshold;
856             }
857             buffer.max = bufferConfig_.max;
858             buffer.threshold = bufferConfig_.threshold;
859             buffer.replenishRateInBasis = bufferConfig_.replenishRateInBasis;
860     
861             // if all delayed messages are read, the buffer is considered synced
862             if (bridge.delayedMessageCount() == totalDelayedMessagesRead) {
863                 buffer.update(uint64(block.number));
864             }
865         }
867         function _setMaxTimeVariation(ISequencerInbox.MaxTimeVariation memory maxTimeVariation_)
868             internal
869         {
870             if (
871                 maxTimeVariation_.delayBlocks > type(uint64).max ||
872                 maxTimeVariation_.futureBlocks > type(uint64).max ||
873                 maxTimeVariation_.delaySeconds > type(uint64).max ||
874                 maxTimeVariation_.futureSeconds > type(uint64).max
875             ) {
876                 revert BadMaxTimeVariation();
877             }
878             delayBlocks = uint64(maxTimeVariation_.delayBlocks);
879             futureBlocks = uint64(maxTimeVariation_.futureBlocks);
880             delaySeconds = uint64(maxTimeVariation_.delaySeconds);
881             futureSeconds = uint64(maxTimeVariation_.futureSeconds);
882         }


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/bridge/SequencerInbox.sol#L0:0

## NC017 - If statement control structures do not comply with best practices:

If statements which include a single line do not need to have curly brackets, however according to the Solidiity style guide the line of code executed upon the if statement condition being met should still be on the next line, not on the same line as the if statement declaration.


<details>
<summary>Click to show 4 findings</summary>

```solidity
File: src/bridge/SequencerInbox.sol


104             if (msg.sender != rollup.owner()) revert NotOwner(msg.sender, rollup.owner());
148                 if (reader4844_ != IReader4844(address(0))) revert DataBlobsNotSupported();
150                 if (reader4844_ == IReader4844(address(0))) revert InitParamZero("Reader4844");
166             if (!isDelayBufferable) revert NotDelayBufferable();
182             if (bridge != IBridge(address(0))) revert AlreadyInit();
183             if (bridge_ == IBridge(address(0))) revert HadZeroInit();
212             if (rollup == newRollup) revert RollupNotChanged();
237             if (!_chainIdChanged()) revert NotForked();
295             if (_totalDelayedMessagesRead <= totalDelayedMessagesRead) revert DelayedBackwards();
314             if (l1BlockAndTime[0] + delayBlocks_ >= block.number) revert ForceIncludeBlockTooSoon();
375             if (msg.sender != tx.origin) revert NotOrigin();
376             if (!isBatchPoster[msg.sender]) revert NotBatchPoster();
377             if (isDelayProofRequired(afterDelayedMessagesRead)) revert DelayProofRequired();
397             if (!isBatchPoster[msg.sender]) revert NotBatchPoster();
398             if (isDelayProofRequired(afterDelayedMessagesRead)) revert DelayProofRequired();
417             if (!isBatchPoster[msg.sender]) revert NotBatchPoster();
418             if (!isDelayBufferable) revert NotDelayBufferable();
440             if (msg.sender != tx.origin) revert NotOrigin();
441             if (!isBatchPoster[msg.sender]) revert NotBatchPoster();
442             if (!isDelayBufferable) revert NotDelayBufferable();
501             if (hostChainIsArbitrum) revert DataBlobsNotSupported();
568             if (!isBatchPoster[msg.sender] && msg.sender != address(rollup)) revert NotBatchPoster();
569             if (isDelayProofRequired(afterDelayedMessagesRead)) revert DelayProofRequired();
591             if (!isBatchPoster[msg.sender] && msg.sender != address(rollup)) revert NotBatchPoster();
592             if (!isDelayBufferable) revert NotDelayBufferable();
694             if (fullDataLen > maxDataSize) revert DataTooLarge(fullDataLen, maxDataSize);
705                 if (!isValidCallDataFlag(data[0])) revert InvalidHeaderFlag(data[0]);
714                     if (!dasKeySetInfo[dasKeysetHash].isValidKeyset) revert NoSuchKeyset(dasKeysetHash);
736             if (dataHashes.length == 0) revert MissingDataHashes();
773             if (extraGas > type(uint64).max) revert ExtraGasNotUint64();
806             if (afterDelayedMessagesRead < totalDelayedMessagesRead) revert DelayedBackwards();
807             if (afterDelayedMessagesRead > bridge.delayedMessageCount()) revert DelayedTooFar();
848             if (!isDelayBufferable) revert NotDelayBufferable();
849             if (!DelayBuffer.isValidBufferConfig(bufferConfig_)) revert BadBufferConfig();
906             if (keysetBytes.length >= 64 * 1024) revert KeysetTooLarge();
908             if (dasKeySetInfo[ksHash].isValidKeyset) revert AlreadyValidDASKeyset(ksHash);
923             if (!dasKeySetInfo[ksHash].isValidKeyset) revert NoSuchKeyset(ksHash);
959             if (ksInfo.creationBlock == 0) revert NoSuchKeyset(ksHash);


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/bridge/SequencerInbox.sol#L0:0

```solidity
File: src/challengeV2/EdgeChallengeManager.sol


494                 if (updated) emit TimerCacheUpdated(edgeIds[i], newValue);
501             if (updated) emit TimerCacheUpdated(edgeId, newValue);
507             if (updated) emit TimerCacheUpdated(edgeId, newValue);


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/challengeV2/EdgeChallengeManager.sol#L0:0

```solidity
File: src/challengeV2/libraries/UintUtilsLib.sol


68              if (x >= 0x2) msb += 1;


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/challengeV2/libraries/UintUtilsLib.sol#L0:0

```solidity
File: src/rollup/RollupUserLogic.sol


53              if (latestConfirmedAssertion.createdAtBlock == 0) return false;


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/rollup/RollupUserLogic.sol#L0:0

</details>

## NC018 - A event should be emitted if a non immutable state variable is set in a constructor:

  


```solidity
File: src/rollup/BOLDUpgradeAction.sol


169         constructor(uint256[] memory __array) {
170             _array = __array;
171         }


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/rollup/BOLDUpgradeAction.sol#L0:0

```solidity
File: src/rollup/BridgeCreator.sol


45          constructor(
46              BridgeTemplates memory _ethBasedTemplates,
47              BridgeTemplates memory _erc20BasedTemplates
48          ) Ownable() {
49              ethBasedTemplates = _ethBasedTemplates;
50              erc20BasedTemplates = _erc20BasedTemplates;
51          }


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/rollup/BridgeCreator.sol#L0:0

## NC019 - Public state arrays should have a getter to return all elements:

In Solidity, public state variables automatically generate a getter function. For non-array types, this is straightforward: it simply returns the value. However, for arrays, the automatically generated getter only allows retrieval of an element at a specific index, not the entire array. This is mainly to prevent unintentional high gas costs, as returning the entire array can be expensive if it's large. If developers want to retrieve the whole array, they must explicitly define a function, as auto-generation could inadvertently expose contracts to gas-related vulnerabilities or lead to unwanted behavior for larger arrays.


```solidity
File: src/challengeV2/EdgeChallengeManager.sol


279         uint256[] public stakeAmounts;


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/challengeV2/EdgeChallengeManager.sol#L0:0

## NC020 - It is best practice to use linear inheritance:

In Solidity, complex inheritance structures can obfuscate code understanding, introducing potential security risks. Multiple inheritance, especially with overlapping function names or state variables, can cause unintentional overrides or ambiguous behavior. Resolution: Strive for linear and simple inheritance chains. Avoid diamond or circular inheritance patterns. Clearly document the purpose and relationships of base contracts, ensuring that overrides are intentional. Tools like Remix or Hardhat can visualize inheritance chains, assisting in verification. Keeping inheritance streamlined aids in better code readability, reduces potential errors, and ensures smoother audits and upgrades.


<details>
<summary>Click to show 6 findings</summary>

```solidity
File: src/assertionStakingPool/AssertionStakingPool.sol


21      contract AssertionStakingPool is AbsBoldStakingPool, IAssertionStakingPool {


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/assertionStakingPool/AssertionStakingPool.sol#L0:0

```solidity
File: src/assertionStakingPool/EdgeStakingPool.sol


25      contract EdgeStakingPool is AbsBoldStakingPool, IEdgeStakingPool {


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/assertionStakingPool/EdgeStakingPool.sol#L0:0

```solidity
File: src/bridge/SequencerInbox.sol


64      contract SequencerInbox is DelegateCallAware, GasRefundEnabled, ISequencerInbox {


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/bridge/SequencerInbox.sol#L0:0

```solidity
File: src/challengeV2/EdgeChallengeManager.sol


206     contract EdgeChallengeManager is IEdgeChallengeManager, Initializable {


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/challengeV2/EdgeChallengeManager.sol#L0:0

```solidity
File: src/rollup/RollupAdminLogic.sol


15      contract RollupAdminLogic is RollupCore, IRollupAdmin, DoubleLogicUUPSUpgradeable {


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/rollup/RollupAdminLogic.sol#L0:0

```solidity
File: src/rollup/RollupUserLogic.sol


15      contract RollupUserLogic is RollupCore, UUPSNotUpgradeable, IRollupUser {


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/rollup/RollupUserLogic.sol#L0:0

</details>

## NC021 - Consider only defining one library/interface/contract per sol file:

Combining multiple libraries, interfaces, or contracts in a single  file can lead to clutter, reduced readability, and versioning issues. **Resolution**: Adopt the best practice of defining only one library, interface, or contract per Solidity file. This modular approach enhances clarity, simplifies unit testing, and streamlines code review. Furthermore, segregating components makes version management easier, as updates to one component won't necessitate changes to a file housing multiple unrelated components. Structured file management can further assist in avoiding naming collisions and ensure smoother integration into larger systems or DApps.


```solidity
File: src/challengeV2/EdgeChallengeManager.sol


18      interface IEdgeChallengeManager {
19          /// @notice Initialize the EdgeChallengeManager. EdgeChallengeManagers are upgradeable
20          ///         so use the initializer paradigm
21          /// @param _assertionChain              The assertion chain contract
22          /// @param _challengePeriodBlocks       The amount of cumulative time an edge must spend unrivaled before it can be confirmed
23          ///                                     This should be the censorship period + the cumulative amount of time needed to do any
24          ///                                     offchain calculation. We currently estimate around 10 mins for each layer zero edge and 1
25          ///                                     one minute for each other edge.
26          /// @param _oneStepProofEntry           The one step proof logic
27          /// @param layerZeroBlockEdgeHeight     The end height of layer zero edges of type Block
28          /// @param layerZeroBigStepEdgeHeight   The end height of layer zero edges of type BigStep
29          /// @param layerZeroSmallStepEdgeHeight The end height of layer zero edges of type SmallStep
30          /// @param _stakeToken                  The token that stake will be provided in when creating zero layer block edges
31          /// @param _excessStakeReceiver         The address that excess stake will be sent to when 2nd+ block edge is created
32          /// @param _numBigStepLevel             The number of bigstep levels
33          /// @param _stakeAmounts                The stake amount for each level. (first element is for block level)
34          function initialize(
35              IAssertionChain _assertionChain,
36              uint64 _challengePeriodBlocks,
37              IOneStepProofEntry _oneStepProofEntry,
38              uint256 layerZeroBlockEdgeHeight,
39              uint256 layerZeroBigStepEdgeHeight,
40              uint256 layerZeroSmallStepEdgeHeight,
41              IERC20 _stakeToken,
42              address _excessStakeReceiver,
43              uint8 _numBigStepLevel,
44              uint256[] calldata _stakeAmounts
45          ) external;
46      
47          function challengePeriodBlocks() external view returns (uint64);
48      
49          /// @notice The one step proof resolver used to decide between rival SmallStep edges of length 1
50          function oneStepProofEntry() external view returns (IOneStepProofEntry);
51      
52          /// @notice Performs necessary checks and creates a new layer zero edge
53          /// @param args             Edge creation args
54          function createLayerZeroEdge(CreateEdgeArgs calldata args) external returns (bytes32);
55      
56          /// @notice Bisect an edge. This creates two child edges:
57          ///         lowerChild: has the same start root and height as this edge, but a different end root and height
58          ///         upperChild: has the same end root and height as this edge, but a different start root and height
59          ///         The lower child end root and height are equal to the upper child start root and height. This height
60          ///         is the mandatoryBisectionHeight.
61          ///         The lower child may already exist, however it's not possible for the upper child to exist as that would
62          ///         mean that the edge has already been bisected
63          /// @param edgeId               Edge to bisect
64          /// @param bisectionHistoryRoot The new history root to be used in the lower and upper children
65          /// @param prefixProof          A proof to show that the bisectionHistoryRoot commits to a prefix of the current endHistoryRoot
66          /// @return lowerChildId        The id of the newly created lower child edge
67          /// @return upperChildId        The id of the newly created upper child edge
68          function bisectEdge(bytes32 edgeId, bytes32 bisectionHistoryRoot, bytes calldata prefixProof)
69              external
70              returns (bytes32, bytes32);
71      
72          /// @notice An edge can be confirmed if the total amount of time it and a single chain of its direct ancestors
73          ///         has spent unrivaled is greater than the challenge period.
74          /// @dev    Edges inherit time from their parents, so the sum of unrivaled timers is compared against the threshold.
75          ///         Given that an edge cannot become unrivaled after becoming rivaled, once the threshold is passed
76          ///         it will always remain passed. The direct ancestors of an edge are linked by parent-child links for edges
77          ///         of the same level, and claimId-edgeId links for zero layer edges that claim an edge in the level below.
78          ///         This method also includes the amount of time the assertion being claimed spent without a sibling
79          /// @param edgeId                   The id of the edge to confirm
80          function confirmEdgeByTime(bytes32 edgeId, AssertionStateData calldata claimStateData) external;
81      
82          /// @notice Update multiple edges' timer cache by their children. Equivalent to calling updateTimerCacheByChildren for each edge.
83          /// @param edgeIds The ids of the edges to update
84          function multiUpdateTimeCacheByChildren(bytes32[] calldata edgeIds) external;
85      
86          /// @notice If a confirmed edge exists whose claim id is equal to this edge, then this edge can be confirmed
87          /// @dev    When zero layer edges are created they reference an edge, or assertion, in the level below. If a zero layer
88          ///         edge is confirmed, it becomes possible to also confirm the edge that it claims
89          /// @param edgeId           The id of the edge to confirm
90          /// @notice Update an edge's timer cache by its children.
91          ///         Sets the edge's timer cache to its timeUnrivaled + (minimum timer cache of its children).
92          ///         This function should not be used for edges without children.
93          /// @param edgeId The id of the edge to update
94          function updateTimerCacheByChildren(bytes32 edgeId) external;
95      
96          /// @notice Given a one step fork edge and an edge with matching claim id,
97          ///         set the one step fork edge's timer cache to its timeUnrivaled + claiming edge's timer cache.
98          /// @param edgeId           The id of the edge to update
99          /// @param claimingEdgeId   The id of the edge which has a claimId equal to edgeId
100         function updateTimerCacheByClaim(bytes32 edgeId, bytes32 claimingEdgeId) external;
101     
102         /// @notice Confirm an edge by executing a one step proof
103         /// @dev    One step proofs can only be executed against edges that have length one and of type SmallStep
104         /// @param edgeId                       The id of the edge to confirm
105         /// @param oneStepData                  Input data to the one step proof
106         /// @param prevConfig                     Data about the config set in prev
107         /// @param beforeHistoryInclusionProof  Proof that the state which is the start of the edge is committed to by the startHistoryRoot
108         /// @param afterHistoryInclusionProof   Proof that the state which is the end of the edge is committed to by the endHistoryRoot
109         function confirmEdgeByOneStepProof(
110             bytes32 edgeId,
111             OneStepData calldata oneStepData,
112             ConfigData calldata prevConfig,
113             bytes32[] calldata beforeHistoryInclusionProof,
114             bytes32[] calldata afterHistoryInclusionProof
115         ) external;
116     
117         /// @notice When zero layer block edges are created a stake is also provided
118         ///         The stake on this edge can be refunded if the edge is confirme
119         function refundStake(bytes32 edgeId) external;
120     
121         /// @notice Zero layer edges have to be a fixed height.
122         ///         This function returns the end height for a given edge type
123         function getLayerZeroEndHeight(EdgeType eType) external view returns (uint256);
124     
125         /// @notice Calculate the unique id of an edge
126         /// @param level            The level of the edge
127         /// @param originId         The origin id of the edge
128         /// @param startHeight      The start height of the edge
129         /// @param startHistoryRoot The start history root of the edge
130         /// @param endHeight        The end height of the edge
131         /// @param endHistoryRoot   The end history root of the edge
132         function calculateEdgeId(
133             uint8 level,
134             bytes32 originId,
135             uint256 startHeight,
136             bytes32 startHistoryRoot,
137             uint256 endHeight,
138             bytes32 endHistoryRoot
139         ) external pure returns (bytes32);
140     
141         /// @notice Calculate the mutual id of the edge
142         ///         Edges that are rivals share the same mutual id
143         /// @param level            The level of the edge
144         /// @param originId         The origin id of the edge
145         /// @param startHeight      The start height of the edge
146         /// @param startHistoryRoot The start history root of the edge
147         /// @param endHeight        The end height of the edge
148         function calculateMutualId(
149             uint8 level,
150             bytes32 originId,
151             uint256 startHeight,
152             bytes32 startHistoryRoot,
153             uint256 endHeight
154         ) external pure returns (bytes32);
155     
156         /// @notice Has the edge already been stored in the manager
157         function edgeExists(bytes32 edgeId) external view returns (bool);
158     
159         /// @notice Get full edge data for an edge
160         function getEdge(bytes32 edgeId) external view returns (ChallengeEdge memory);
161     
162         /// @notice The length of the edge, from start height to end height
163         function edgeLength(bytes32 edgeId) external view returns (uint256);
164     
165         /// @notice Does this edge currently have one or more rivals
166         ///         Rival edges share the same mutual id
167         function hasRival(bytes32 edgeId) external view returns (bool);
168     
169         /// @notice The confirmed rival of this mutual id
170         ///         Returns 0 if one does not exist
171         function confirmedRival(bytes32 mutualId) external view returns (bytes32);
172     
173         /// @notice Does the edge have at least one rival, and it has length one
174         function hasLengthOneRival(bytes32 edgeId) external view returns (bool);
175     
176         /// @notice The amount of time this edge has spent without rivals
177         ///         This value is increasing whilst an edge is unrivaled, once a rival is created
178         ///         it is fixed. If an edge has rivals from the moment it is created then it will have
179         ///         a zero time unrivaled
180         function timeUnrivaled(bytes32 edgeId) external view returns (uint256);
181     
182         /// @notice Get the id of the prev assertion that this edge is originates from
183         /// @dev    Uses the parent chain to traverse upwards SmallStep->BigStep->Block->Assertion
184         ///         until it gets to the origin assertion
185         function getPrevAssertionHash(bytes32 edgeId) external view returns (bytes32);
186     
187         /// @notice Fetch the raw first rival record for the given mutual id
188         /// @dev    Returns 0 if there is no edge with the given mutual id
189         ///         Returns a magic value if there is one edge but it is unrivaled
190         ///         Returns the id of the second edge created with the mutual id, if > 1 exists
191         function firstRival(bytes32 mutualId) external view returns (bytes32);
192     
193         /// @notice True if an account has made a layer zero edge with the given mutual id.
194         ///         This is only tracked when the validator whitelist is enabled
195         function hasMadeLayerZeroRival(address account, bytes32 mutualId) external view returns (bool);
196     }
197     
198     /// @title  A challenge manager that uses edge structures to decide between Assertions
199     /// @notice When two assertions are created that have the same predecessor the protocol needs to decide which of the two is correct
200     ///         This challenge manager allows the staker who has created the valid assertion to enforce that it will be confirmed, and all
201     ///         other rival assertions will be rejected. The challenge is all-vs-all in that all assertions with the same
202     ///         predecessor will vie for succession against each other. Stakers compete by creating edges that reference the assertion they
203     ///         believe in. These edges are then bisected, reducing the size of the disagreement with each bisection, and narrowing in on the
204     ///         exact point of disagreement. Eventually, at step size 1, the step can be proved on-chain directly proving that the related assertion
205     ///         must be invalid.
206     contract EdgeChallengeManager is IEdgeChallengeManager, Initializable {


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/challengeV2/EdgeChallengeManager.sol#L0:0

```solidity
File: src/rollup/BOLDUpgradeAction.sol


49      interface IOldRollup {
50          struct Assertion {
51              ExecutionState beforeState;
52              ExecutionState afterState;
53              uint64 numBlocks;
54          }
55      
56          event NodeCreated(
57              uint64 indexed nodeNum,
58              bytes32 indexed parentNodeHash,
59              bytes32 indexed nodeHash,
60              bytes32 executionHash,
61              Assertion assertion,
62              bytes32 afterInboxBatchAcc,
63              bytes32 wasmModuleRoot,
64              uint256 inboxMaxCount
65          );
66      
67          function wasmModuleRoot() external view returns (bytes32);
68          function latestConfirmed() external view returns (uint64);
69          function getNode(uint64 nodeNum) external view returns (Node memory);
70          function getStakerAddress(uint64 stakerNum) external view returns (address);
71          function stakerCount() external view returns (uint64);
72          function getStaker(address staker) external view returns (OldStaker memory);
73          function isValidator(address validator) external view returns (bool);
74          function validatorWalletCreator() external view returns (address);
75      }
76      
77      interface IOldRollupAdmin {


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/rollup/BOLDUpgradeAction.sol#L0:0

## NC022 - Use a struct to encapsulate multiple function parameters:

Using a struct to encapsulate multiple parameters in Solidity functions can significantly enhance code readability and maintainability. Instead of passing a long list of arguments, which can be error-prone and hard to manage, a struct allows grouping related data into a single, coherent entity. This approach simplifies function signatures and makes the code more organized. It also enhances code clarity, as developers can easily understand the relationship between the parameters. Moreover, it aids in future code modifications and expansions, as adding or modifying a parameter only requires changes in the struct definition, rather than in every function that uses these parameters.


<details>
<summary>Click to show 12 findings</summary>

```solidity
File: src/bridge/DelayBuffer.sol


33          function calcBuffer(
34              uint256 start,
35              uint256 end,
36              uint256 buffer,
37              uint256 sequenced,
38              uint256 threshold,
39              uint256 max,
40              uint256 replenishRateInBasis
41          ) internal pure returns (uint256) {


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/bridge/DelayBuffer.sol#L0:0

```solidity
File: src/bridge/ISequencerInbox.sol


139         function forceInclusion(
140             uint256 _totalDelayedMessagesRead,
141             uint8 kind,
142             uint64[2] calldata l1BlockAndTime,
143             uint256 baseFeeL1,
144             address sender,
145             bytes32 messageDataHash
179         function addSequencerL2BatchFromOrigin(
180             uint256 sequenceNumber,
181             bytes calldata data,
182             uint256 afterDelayedMessagesRead,
183             IGasRefunder gasRefunder,
184             uint256 prevMessageCount,
185             uint256 newMessageCount
188         function addSequencerL2Batch(
189             uint256 sequenceNumber,
190             bytes calldata data,
191             uint256 afterDelayedMessagesRead,
192             IGasRefunder gasRefunder,
193             uint256 prevMessageCount,
194             uint256 newMessageCount
197         function addSequencerL2BatchFromBlobs(
198             uint256 sequenceNumber,
199             uint256 afterDelayedMessagesRead,
200             IGasRefunder gasRefunder,
201             uint256 prevMessageCount,
202             uint256 newMessageCount
207         function addSequencerL2BatchFromBlobsDelayProof(
208             uint256 sequenceNumber,
209             uint256 afterDelayedMessagesRead,
210             IGasRefunder gasRefunder,
211             uint256 prevMessageCount,
212             uint256 newMessageCount,
213             DelayProof calldata delayProof
219         function addSequencerL2BatchFromOriginDelayProof(
220             uint256 sequenceNumber,
221             bytes calldata data,
222             uint256 afterDelayedMessagesRead,
223             IGasRefunder gasRefunder,
224             uint256 prevMessageCount,
225             uint256 newMessageCount,
226             DelayProof calldata delayProof
231         function addSequencerL2BatchDelayProof(
232             uint256 sequenceNumber,
233             bytes calldata data,
234             uint256 afterDelayedMessagesRead,
235             IGasRefunder gasRefunder,
236             uint256 prevMessageCount,
237             uint256 newMessageCount,
238             DelayProof calldata delayProof


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/bridge/ISequencerInbox.sol#L0:0

```solidity
File: src/bridge/SequencerInbox.sol


287         function forceInclusion(
288             uint256 _totalDelayedMessagesRead,
289             uint8 kind,
290             uint64[2] calldata l1BlockAndTime,
291             uint256 baseFeeL1,
292             address sender,
293             bytes32 messageDataHash
294         ) external {
366         function addSequencerL2BatchFromOrigin(
367             uint256 sequenceNumber,
368             bytes calldata data,
369             uint256 afterDelayedMessagesRead,
370             IGasRefunder gasRefunder,
371             uint256 prevMessageCount,
372             uint256 newMessageCount
373         ) external refundsGas(gasRefunder, IReader4844(address(0))) {
390         function addSequencerL2BatchFromBlobs(
391             uint256 sequenceNumber,
392             uint256 afterDelayedMessagesRead,
393             IGasRefunder gasRefunder,
394             uint256 prevMessageCount,
395             uint256 newMessageCount
396         ) external refundsGas(gasRefunder, reader4844) {
409         function addSequencerL2BatchFromBlobsDelayProof(
410             uint256 sequenceNumber,
411             uint256 afterDelayedMessagesRead,
412             IGasRefunder gasRefunder,
413             uint256 prevMessageCount,
414             uint256 newMessageCount,
415             DelayProof calldata delayProof
416         ) external refundsGas(gasRefunder, reader4844) {
430         function addSequencerL2BatchFromOriginDelayProof(
431             uint256 sequenceNumber,
432             bytes calldata data,
433             uint256 afterDelayedMessagesRead,
434             IGasRefunder gasRefunder,
435             uint256 prevMessageCount,
436             uint256 newMessageCount,
437             DelayProof calldata delayProof
438         ) external refundsGas(gasRefunder, IReader4844(address(0))) {
512         function addSequencerL2BatchFromCalldataImpl(
513             uint256 sequenceNumber,
514             bytes calldata data,
515             uint256 afterDelayedMessagesRead,
516             uint256 prevMessageCount,
517             uint256 newMessageCount,
518             bool isFromOrigin
519         ) internal {
560         function addSequencerL2Batch(
561             uint256 sequenceNumber,
562             bytes calldata data,
563             uint256 afterDelayedMessagesRead,
564             IGasRefunder gasRefunder,
565             uint256 prevMessageCount,
566             uint256 newMessageCount
567         ) external override refundsGas(gasRefunder, IReader4844(address(0))) {
582         function addSequencerL2BatchDelayProof(
583             uint256 sequenceNumber,
584             bytes calldata data,
585             uint256 afterDelayedMessagesRead,
586             IGasRefunder gasRefunder,
587             uint256 prevMessageCount,
588             uint256 newMessageCount,
589             DelayProof calldata delayProof
590         ) external refundsGas(gasRefunder, IReader4844(address(0))) {
791         function addSequencerL2BatchImpl(
792             bytes32 dataHash,
793             uint256 afterDelayedMessagesRead,
794             uint256 calldataLengthPosted,
795             uint256 prevMessageCount,
796             uint256 newMessageCount
797         )
798             internal
799             returns (
800                 uint256 seqMessageIndex,
801                 bytes32 beforeAcc,
802                 bytes32 delayedAcc,
803                 bytes32 acc
804             )
805         {


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/bridge/SequencerInbox.sol#L0:0

```solidity
File: src/challengeV2/EdgeChallengeManager.sol


34          function initialize(
35              IAssertionChain _assertionChain,
36              uint64 _challengePeriodBlocks,
37              IOneStepProofEntry _oneStepProofEntry,
38              uint256 layerZeroBlockEdgeHeight,
39              uint256 layerZeroBigStepEdgeHeight,
40              uint256 layerZeroSmallStepEdgeHeight,
41              IERC20 _stakeToken,
42              address _excessStakeReceiver,
43              uint8 _numBigStepLevel,
44              uint256[] calldata _stakeAmounts
109         function confirmEdgeByOneStepProof(
110             bytes32 edgeId,
111             OneStepData calldata oneStepData,
112             ConfigData calldata prevConfig,
113             bytes32[] calldata beforeHistoryInclusionProof,
114             bytes32[] calldata afterHistoryInclusionProof
132         function calculateEdgeId(
133             uint8 level,
134             bytes32 originId,
135             uint256 startHeight,
136             bytes32 startHistoryRoot,
137             uint256 endHeight,
138             bytes32 endHistoryRoot
148         function calculateMutualId(
149             uint8 level,
150             bytes32 originId,
151             uint256 startHeight,
152             bytes32 startHistoryRoot,
153             uint256 endHeight
305         function initialize(
306             IAssertionChain _assertionChain,
307             uint64 _challengePeriodBlocks,
308             IOneStepProofEntry _oneStepProofEntry,
309             uint256 layerZeroBlockEdgeHeight,
310             uint256 layerZeroBigStepEdgeHeight,
311             uint256 layerZeroSmallStepEdgeHeight,
312             IERC20 _stakeToken,
313             address _excessStakeReceiver,
314             uint8 _numBigStepLevel,
315             uint256[] calldata _stakeAmounts
316         ) public initializer {
539         function confirmEdgeByOneStepProof(
540             bytes32 edgeId,
541             OneStepData calldata oneStepData,
542             ConfigData calldata prevConfig,
543             bytes32[] calldata beforeHistoryInclusionProof,
544             bytes32[] calldata afterHistoryInclusionProof
545         ) public {
604         function calculateEdgeId(
605             uint8 level,
606             bytes32 originId,
607             uint256 startHeight,
608             bytes32 startHistoryRoot,
609             uint256 endHeight,
610             bytes32 endHistoryRoot
611         ) public pure returns (bytes32) {
616         function calculateMutualId(
617             uint8 level,
618             bytes32 originId,
619             uint256 startHeight,
620             bytes32 startHistoryRoot,
621             uint256 endHeight
622         ) public pure returns (bytes32) {


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/challengeV2/EdgeChallengeManager.sol#L0:0

```solidity
File: src/challengeV2/libraries/ChallengeEdgeLib.sol


69          function newEdgeChecks(
70              bytes32 originId,
71              bytes32 startHistoryRoot,
72              uint256 startHeight,
73              bytes32 endHistoryRoot,
74              uint256 endHeight
75          ) internal pure {
93          function newLayerZeroEdge(
94              bytes32 originId,
95              bytes32 startHistoryRoot,
96              uint256 startHeight,
97              bytes32 endHistoryRoot,
98              uint256 endHeight,
99              bytes32 claimId,
100             address staker,
101             uint8 level
102         ) internal view returns (ChallengeEdge memory) {
133         function newChildEdge(
134             bytes32 originId,
135             bytes32 startHistoryRoot,
136             uint256 startHeight,
137             bytes32 endHistoryRoot,
138             uint256 endHeight,
139             uint8 level
140         ) internal view returns (ChallengeEdge memory) {
166         function mutualIdComponent(
167             uint8 level,
168             bytes32 originId,
169             uint256 startHeight,
170             bytes32 startHistoryRoot,
171             uint256 endHeight
172         ) internal pure returns (bytes32) {
189         function idComponent(
190             uint8 level,
191             bytes32 originId,
192             uint256 startHeight,
193             bytes32 startHistoryRoot,
194             uint256 endHeight,
195             bytes32 endHistoryRoot
196         ) internal pure returns (bytes32) {


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/challengeV2/libraries/ChallengeEdgeLib.sol#L0:0

```solidity
File: src/challengeV2/libraries/EdgeChallengeManagerLib.sol


213         function layerZeroTypeSpecificChecks(
214             EdgeStore storage store,
215             CreateEdgeArgs calldata args,
216             AssertionReferenceData memory ard,
217             IOneStepProofEntry oneStepProofEntry,
218             uint8 numBigStepLevel
219         ) private view returns (ProofData memory, bytes32) {
411         function createLayerZeroEdge(
412             EdgeStore storage store,
413             CreateEdgeArgs calldata args,
414             AssertionReferenceData memory ard,
415             IOneStepProofEntry oneStepProofEntry,
416             uint256 expectedEndHeight,
417             uint8 numBigStepLevel,
418             bool whitelistEnabled
419         ) internal returns (EdgeAddedData memory) {
766         function confirmEdgeByOneStepProof(
767             EdgeStore storage store,
768             bytes32 edgeId,
769             IOneStepProofEntry oneStepProofEntry,
770             OneStepData calldata oneStepData,
771             ExecutionContext memory execCtx,
772             bytes32[] calldata beforeHistoryInclusionProof,
773             bytes32[] calldata afterHistoryInclusionProof,
774             uint8 numBigStepLevel,
775             uint256 bigStepHeight,
776             uint256 smallStepHeight
777         ) internal {


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/challengeV2/libraries/EdgeChallengeManagerLib.sol#L0:0

```solidity
File: src/challengeV2/libraries/MerkleTreeLib.sol


312         function verifyPrefixProof(
313             bytes32 preRoot,
314             uint256 preSize,
315             bytes32 postRoot,
316             uint256 postSize,
317             bytes32[] memory preExpansion,
318             bytes32[] memory proof
319         ) internal pure {


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/challengeV2/libraries/MerkleTreeLib.sol#L0:0

```solidity
File: src/rollup/BridgeCreator.sol


99          function createBridge(
100             address adminProxy,
101             address rollup,
102             address nativeToken,
103             ISequencerInbox.MaxTimeVariation calldata maxTimeVariation,
104             BufferConfig calldata bufferConfig
105         ) external returns (BridgeContracts memory) {


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/rollup/BridgeCreator.sol#L0:0

```solidity
File: src/rollup/IRollupLogic.sol


21          function confirmAssertion(
22              bytes32 assertionHash,
23              bytes32 prevAssertionHash,
24              AssertionState calldata confirmState,
25              bytes32 winningEdgeId,
26              ConfigData calldata prevConfig,
27              bytes32 inboxAcc


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/rollup/IRollupLogic.sol#L0:0

```solidity
File: src/rollup/RollupCreator.sol


63          function setTemplates(
64              BridgeCreator _bridgeCreator,
65              IOneStepProofEntry _osp,
66              IEdgeChallengeManager _challengeManagerLogic,
67              IRollupAdmin _rollupAdminLogic,
68              IRollupUser _rollupUserLogic,
69              IUpgradeExecutor _upgradeExecutorLogic,
70              address _validatorWalletCreator,
71              DeployHelper _l2FactoriesDeployer
72          ) external onlyOwner {


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/rollup/RollupCreator.sol#L0:0

```solidity
File: src/rollup/RollupLib.sol


54          function configHash(
55              bytes32 wasmModuleRoot,
56              uint256 requiredStake,
57              address challengeManager,
58              uint64 confirmPeriodBlocks,
59              uint64 nextInboxPosition
60          ) internal pure returns (bytes32) {


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/rollup/RollupLib.sol#L0:0

```solidity
File: src/rollup/RollupUserLogic.sol


82          function confirmAssertion(
83              bytes32 assertionHash,
84              bytes32 prevAssertionHash,
85              AssertionState calldata confirmState,
86              bytes32 winningEdgeId,
87              ConfigData calldata prevConfig,
88              bytes32 inboxAcc
89          ) external onlyValidator whenNotPaused {


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/rollup/RollupUserLogic.sol#L0:0

</details>

## NC023 - Avoid defining a function in a single line including it's contents:

  


```solidity
File: src/rollup/RollupAdminLogic.sol


166         function _authorizeUpgrade(address newImplementation) internal override {}
171         function _authorizeSecondaryUpgrade(address newImplementation) internal override {}


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/rollup/RollupAdminLogic.sol#L0:0

```solidity
File: src/rollup/RollupCreator.sol


58          constructor() Ownable() {}
61          receive() external payable {}


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/rollup/RollupCreator.sol#L0:0

## NC024 - Empty bytes check is missing:

When developing smart contracts in Solidity, it's crucial to validate the inputs of your functions. This includes ensuring that the bytes parameters are not empty, especially when they represent crucial data such as addresses, identifiers, or raw data that the contract needs to process.Missing empty bytes checks can lead to unexpected behaviour in your contract.For instance, certain operations might fail, produce incorrect results, or consume unnecessary gas when performed with empty bytes.  Moreover, missing input validation can potentially expose your contract to malicious activity, including exploitation of unhandled edge cases.To mitigate these issues, always validate that bytes parameters are not empty when the logic of your contract requires it.


<details>
<summary>Click to show 4 findings</summary>

```solidity
File: src/assertionStakingPool/StakingPoolCreatorUtils.sol


13          function getPool(bytes memory creationCode, bytes memory args) internal view returns (address) {


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/assertionStakingPool/StakingPoolCreatorUtils.sol#L0:0

```solidity
File: src/bridge/SequencerInbox.sol


366         function addSequencerL2BatchFromOrigin(
367             uint256 sequenceNumber,
368             bytes calldata data,
369             uint256 afterDelayedMessagesRead,
370             IGasRefunder gasRefunder,
371             uint256 prevMessageCount,
372             uint256 newMessageCount
373         ) external refundsGas(gasRefunder, IReader4844(address(0))) {
430         function addSequencerL2BatchFromOriginDelayProof(
431             uint256 sequenceNumber,
432             bytes calldata data,
433             uint256 afterDelayedMessagesRead,
434             IGasRefunder gasRefunder,
435             uint256 prevMessageCount,
436             uint256 newMessageCount,
437             DelayProof calldata delayProof
438         ) external refundsGas(gasRefunder, IReader4844(address(0))) {
512         function addSequencerL2BatchFromCalldataImpl(
513             uint256 sequenceNumber,
514             bytes calldata data,
515             uint256 afterDelayedMessagesRead,
516             uint256 prevMessageCount,
517             uint256 newMessageCount,
518             bool isFromOrigin
519         ) internal {
560         function addSequencerL2Batch(
561             uint256 sequenceNumber,
562             bytes calldata data,
563             uint256 afterDelayedMessagesRead,
564             IGasRefunder gasRefunder,
565             uint256 prevMessageCount,
566             uint256 newMessageCount
567         ) external override refundsGas(gasRefunder, IReader4844(address(0))) {
582         function addSequencerL2BatchDelayProof(
583             uint256 sequenceNumber,
584             bytes calldata data,
585             uint256 afterDelayedMessagesRead,
586             IGasRefunder gasRefunder,
587             uint256 prevMessageCount,
588             uint256 newMessageCount,
589             DelayProof calldata delayProof
590         ) external refundsGas(gasRefunder, IReader4844(address(0))) {
688         function formCallDataHash(bytes calldata data, uint256 afterDelayedMessagesRead)
903         function setValidKeyset(bytes calldata keysetBytes) external onlyRollupOwner {


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/bridge/SequencerInbox.sol#L0:0

```solidity
File: src/challengeV2/EdgeChallengeManager.sol


451         function bisectEdge(bytes32 edgeId, bytes32 bisectionHistoryRoot, bytes calldata prefixProof)


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/challengeV2/EdgeChallengeManager.sol#L0:0

```solidity
File: src/challengeV2/libraries/EdgeChallengeManagerLib.sol


604         function bisectEdge(EdgeStore storage store, bytes32 edgeId, bytes32 bisectionHistoryRoot, bytes memory prefixProof)


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/challengeV2/libraries/EdgeChallengeManagerLib.sol#L0:0

</details>

## NC025 - Defining All External/Public Functions in Contract Interfaces:

It is preferable to have all the external and public function in an interface to make using them easier by developers. This helps ensure the whole API is extracted in a interface.


```solidity
File: src/rollup/RollupCreator.sol


137         function createRollup(RollupDeploymentParams memory deployParams)


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/rollup/RollupCreator.sol#L0:0

```solidity
File: src/rollup/RollupUserLogic.sol


163         function stakeOnNewAssertion(AssertionInputs calldata assertion, bytes32 expectedAssertionHash)
252         function fastConfirmAssertion(
253             bytes32 assertionHash,
254             bytes32 parentAssertionHash,
255             AssertionState calldata confirmState,
256             bytes32 inboxAcc
257         ) public whenNotPaused {
331         function newStakeOnNewAssertion(
332             uint256 tokenAmount,
333             AssertionInputs calldata assertion,
334             bytes32 expectedAssertionHash,
335             address withdrawalAddress
336         ) public {


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/rollup/RollupUserLogic.sol#L0:0

## NC026 - Avoid declaring variables with the names of defined functions within the project:

Having such variables can create confusion in both developers and in users of the project. Consider renaming these variables to improve code clarity.


```solidity
File: src/rollup/BOLDUpgradeAction.sol


344             uint64 stakerCount = ROLLUP_READER.stakerCount();


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/rollup/BOLDUpgradeAction.sol#L0:0




## NC027 - Consider disabling `renounceOwnership()`:

If the plan for your project does not include eventually giving up all ownership control, consider overwriting OpenZeppelin's Ownable's `renounceOwnership()` function in order to disable it.


```solidity
File: src/rollup/BridgeCreator.sol


21      contract BridgeCreator is Ownable {


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/rollup/BridgeCreator.sol#L0:0

```solidity
File: src/rollup/RollupCreator.sol


17      contract RollupCreator is Ownable {


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/rollup/RollupCreator.sol#L0:0

## NC028 - Not using the named return variables anywhere in the function is confusing:

Consider changing the return variable to be an unnamed one, since the variable is never assigned, nor is it returned by name


```solidity
File: src/challengeV2/libraries/ChallengeEdgeLib.sol


279         function levelToType(uint8 level, uint8 numBigStepLevels) internal pure returns (EdgeType eType) {


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/challengeV2/libraries/ChallengeEdgeLib.sol#L0:0

```solidity
File: src/challengeV2/libraries/UintUtilsLib.sol


14          function leastSignificantBit(uint256 x) internal pure returns (uint256 msb) {


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/challengeV2/libraries/UintUtilsLib.sol#L0:0

## NC029 - Unused arguments in override functions:

Arguments in overridden functions that are unused should have their names removed or commented out to avoid compiler warnings.


```solidity
File: src/bridge/SequencerInbox.sol


564             IGasRefunder gasRefunder,


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/bridge/SequencerInbox.sol#L0:0

```solidity
File: src/rollup/RollupAdminLogic.sol


166         function _authorizeUpgrade(address newImplementation) internal override {}
171         function _authorizeSecondaryUpgrade(address newImplementation) internal override {}


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/rollup/RollupAdminLogic.sol#L0:0

## NC030 - Non-library/interface files should use fixed compiler versions, not floating ones:

Using a floating compiler version like ^0.8.16 or >=0.8.16 can lead to unexpected behavior if the compiler version used differs from the one intended. It's recommended to specify a fixed compiler version for non-library/interface files.


<details>
<summary>Click to show 12 findings</summary>

```solidity
File: src/assertionStakingPool/AssertionStakingPool.sol


6       pragma solidity ^0.8.0;


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/assertionStakingPool/AssertionStakingPool.sol#L0:0

```solidity
File: src/assertionStakingPool/AssertionStakingPoolCreator.sol


6       pragma solidity ^0.8.0;


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/assertionStakingPool/AssertionStakingPoolCreator.sol#L0:0

```solidity
File: src/assertionStakingPool/EdgeStakingPool.sol


5       pragma solidity ^0.8.0;


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/assertionStakingPool/EdgeStakingPool.sol#L0:0

```solidity
File: src/assertionStakingPool/EdgeStakingPoolCreator.sol


6       pragma solidity ^0.8.0;


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/assertionStakingPool/EdgeStakingPoolCreator.sol#L0:0

```solidity
File: src/bridge/SequencerInbox.sol


5       pragma solidity ^0.8.0;


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/bridge/SequencerInbox.sol#L0:0

```solidity
File: src/challengeV2/EdgeChallengeManager.sol


5       pragma solidity ^0.8.17;


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/challengeV2/EdgeChallengeManager.sol#L0:0

```solidity
File: src/rollup/BOLDUpgradeAction.sol


5       pragma solidity ^0.8.0;


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/rollup/BOLDUpgradeAction.sol#L0:0

```solidity
File: src/rollup/BridgeCreator.sol


5       pragma solidity ^0.8.0;


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/rollup/BridgeCreator.sol#L0:0

```solidity
File: src/rollup/RollupAdminLogic.sol


5       pragma solidity ^0.8.0;


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/rollup/RollupAdminLogic.sol#L0:0

```solidity
File: src/rollup/RollupCreator.sol


5       pragma solidity ^0.8.0;


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/rollup/RollupCreator.sol#L0:0

```solidity
File: src/rollup/RollupProxy.sol


5       pragma solidity ^0.8.0;


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/rollup/RollupProxy.sol#L0:0

```solidity
File: src/rollup/RollupUserLogic.sol


5       pragma solidity ^0.8.0;


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/rollup/RollupUserLogic.sol#L0:0

</details>

## NC031 - Expressions for constant values such as a call to `keccak256()`, should use `immutable` rather than `constant`:

While it **doesn't save any gas** because the compiler knows that developers often make this mistake, it's still best to use the right tool for the task at hand. There is a difference between `constant` variables and `immutable` variables, and they should each be used in their appropriate contexts. `constants` should be used for literal values written into the code, and `immutable` variables should be used for expressions, or values calculated in, or passed into the constructor.


```solidity
File: src/challengeV2/libraries/EdgeChallengeManagerLib.sol


135         bytes32 public constant UNRIVALED = keccak256(abi.encodePacked("UNRIVALED"));


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/challengeV2/libraries/EdgeChallengeManagerLib.sol#L0:0

## NC032 - Empty Function Body - Consider commenting why:

  


```solidity
File: src/rollup/RollupAdminLogic.sol


166         function _authorizeUpgrade(address newImplementation) internal override {}
171         function _authorizeSecondaryUpgrade(address newImplementation) internal override {}


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/rollup/RollupAdminLogic.sol#L0:0

## NC033 - Contracts should have full test coverage:

While 100% code coverage does not guarantee that there are no bugs, it often will catch easy-to-find bugs, and will ensure that there are fewer regressions when the code invariably has to be modified. Furthermore, in order to get full coverage, code authors will often have to re-organize their code so that it is more modular, so that each component can be tested separately, which reduces interdependencies between modules and layers, and makes for code that is easier to reason about and audit.


```solidity
File: Various Files


None

```

## NC034 - Large or complicated code bases should implement invariant tests:

Large code bases, or code with lots of inline-assembly, complicated math, or complicated interactions between multiple contracts, should implement invariant fuzzing tests. Invariant fuzzers such as Echidna require the test writer to come up with invariants which should not be violated under any circumstances, and the fuzzer tests various inputs and function calls to ensure that the invariants always hold. Even code with 100% code coverage can still have bugs due to the order of the operations a user performs, and invariant fuzzers, with properly and extensively-written invariants, can close this testing gap significantly.


```solidity
File: Various Files


None

```

## NC035 - Long functions should be refactored into multiple, smaller, functions:

  


<details>
<summary>Click to show 9 findings</summary>

```solidity
File: src/bridge/SequencerInbox.sol


287         function forceInclusion(
288             uint256 _totalDelayedMessagesRead,
289             uint8 kind,
290             uint64[2] calldata l1BlockAndTime,
291             uint256 baseFeeL1,
292             address sender,
293             bytes32 messageDataHash
294         ) external {
295             if (_totalDelayedMessagesRead <= totalDelayedMessagesRead) revert DelayedBackwards();
296             bytes32 messageHash = Messages.messageHash(
297                 kind,
298                 sender,
299                 l1BlockAndTime[0],
300                 l1BlockAndTime[1],
301                 _totalDelayedMessagesRead - 1,
302                 baseFeeL1,
303                 messageDataHash
304             );
305     
306             uint256 delayBlocks_ = delayBlocks;
307     
308             if (isDelayBufferable) {
309                 // proactively apply any pending delay buffer updates before the force included message l1BlockAndTime
310                 buffer.update(l1BlockAndTime[0]);
311                 delayBlocks_ = delayBufferableBlocks(buffer.bufferBlocks);
312             }
313             // Can only force-include after the Sequencer-only window has expired.
314             if (l1BlockAndTime[0] + delayBlocks_ >= block.number) revert ForceIncludeBlockTooSoon();
315     
316             // Verify that message hash represents the last message sequence of delayed message to be included
317             bytes32 prevDelayedAcc = 0;
318             if (_totalDelayedMessagesRead > 1) {
319                 prevDelayedAcc = bridge.delayedInboxAccs(_totalDelayedMessagesRead - 2);
320             }
321             if (
322                 bridge.delayedInboxAccs(_totalDelayedMessagesRead - 1) !=
323                 Messages.accumulateInboxMessage(prevDelayedAcc, messageHash)
324             ) revert IncorrectMessagePreimage();
325     
326             (bytes32 dataHash, IBridge.TimeBounds memory timeBounds) = formEmptyDataHash(
327                 _totalDelayedMessagesRead
328             );
329             uint256 __totalDelayedMessagesRead = _totalDelayedMessagesRead;
330             uint256 prevSeqMsgCount = bridge.sequencerReportedSubMessageCount();
331             uint256 newSeqMsgCount = prevSeqMsgCount; // force inclusion should not modify sequencer message count
332             (
333                 uint256 seqMessageIndex,
334                 bytes32 beforeAcc,
335                 bytes32 delayedAcc,
336                 bytes32 afterAcc
337             ) = addSequencerL2BatchImpl(
338                     dataHash,
339                     __totalDelayedMessagesRead,
340                     0,
341                     prevSeqMsgCount,
342                     newSeqMsgCount
343                 );
344             emit SequencerBatchDelivered(
345                 seqMessageIndex,
346                 beforeAcc,
347                 afterAcc,
348                 delayedAcc,
349                 totalDelayedMessagesRead,
350                 timeBounds,
351                 IBridge.BatchDataLocation.NoData
352             );
353         }
455         function addSequencerL2BatchFromBlobsImpl(
456             uint256 sequenceNumber,
457             uint256 afterDelayedMessagesRead,
458             uint256 prevMessageCount,
459             uint256 newMessageCount
460         ) internal {
461             (
462                 bytes32 dataHash,
463                 IBridge.TimeBounds memory timeBounds,
464                 uint256 blobGas
465             ) = formBlobDataHash(afterDelayedMessagesRead);
466     
467             // we use addSequencerL2BatchImpl for submitting the message
468             // normally this would also submit a batch spending report but that is skipped if we pass
469             // an empty call data size, then we submit a separate batch spending report later
470             (
471                 uint256 seqMessageIndex,
472                 bytes32 beforeAcc,
473                 bytes32 delayedAcc,
474                 bytes32 afterAcc
475             ) = addSequencerL2BatchImpl(
476                     dataHash,
477                     afterDelayedMessagesRead,
478                     0,
479                     prevMessageCount,
480                     newMessageCount
481                 );
482     
483             // ~uint256(0) is type(uint256).max, but ever so slightly cheaper
484             if (seqMessageIndex != sequenceNumber && sequenceNumber != ~uint256(0)) {
485                 revert BadSequencerNumber(seqMessageIndex, sequenceNumber);
486             }
487     
488             emit SequencerBatchDelivered(
489                 sequenceNumber,
490                 beforeAcc,
491                 afterAcc,
492                 delayedAcc,
493                 totalDelayedMessagesRead,
494                 timeBounds,
495                 IBridge.BatchDataLocation.Blob
496             );
497     
498             // blobs are currently not supported on host arbitrum chains, when support is added it may
499             // consume gas in a different way to L1, so explicitly block host arb chains so that if support for blobs
500             // on arb is added it will need to explicitly turned on in the sequencer inbox
501             if (hostChainIsArbitrum) revert DataBlobsNotSupported();
502     
503             // submit a batch spending report to refund the entity that produced the blob batch data
504             // same as using calldata, we only submit spending report if the caller is the origin of the tx
505             // such that one cannot "double-claim" batch posting refund in the same tx
506             // solhint-disable-next-line avoid-tx-origin
507             if (msg.sender == tx.origin && !isUsingFeeToken) {
508                 submitBatchSpendingReport(dataHash, seqMessageIndex, block.basefee, blobGas);
509             }
510         }


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/bridge/SequencerInbox.sol#L0:0

```solidity
File: src/challengeV2/EdgeChallengeManager.sol


305         function initialize(
306             IAssertionChain _assertionChain,
307             uint64 _challengePeriodBlocks,
308             IOneStepProofEntry _oneStepProofEntry,
309             uint256 layerZeroBlockEdgeHeight,
310             uint256 layerZeroBigStepEdgeHeight,
311             uint256 layerZeroSmallStepEdgeHeight,
312             IERC20 _stakeToken,
313             address _excessStakeReceiver,
314             uint8 _numBigStepLevel,
315             uint256[] calldata _stakeAmounts
316         ) public initializer {
317             if (address(_assertionChain) == address(0)) {
318                 revert EmptyAssertionChain();
319             }
320             assertionChain = _assertionChain;
321             if (address(_oneStepProofEntry) == address(0)) {
322                 revert EmptyOneStepProofEntry();
323             }
324             oneStepProofEntry = _oneStepProofEntry;
325             if (_challengePeriodBlocks == 0) {
326                 revert EmptyChallengePeriod();
327             }
328             challengePeriodBlocks = _challengePeriodBlocks;
329     
330             stakeToken = _stakeToken;
331             if (_excessStakeReceiver == address(0)) {
332                 revert EmptyStakeReceiver();
333             }
334             excessStakeReceiver = _excessStakeReceiver;
335     
336             if (!EdgeChallengeManagerLib.isPowerOfTwo(layerZeroBlockEdgeHeight)) {
337                 revert NotPowerOfTwo(layerZeroBlockEdgeHeight);
338             }
339             LAYERZERO_BLOCKEDGE_HEIGHT = layerZeroBlockEdgeHeight;
340             if (!EdgeChallengeManagerLib.isPowerOfTwo(layerZeroBigStepEdgeHeight)) {
341                 revert NotPowerOfTwo(layerZeroBigStepEdgeHeight);
342             }
343             LAYERZERO_BIGSTEPEDGE_HEIGHT = layerZeroBigStepEdgeHeight;
344             if (!EdgeChallengeManagerLib.isPowerOfTwo(layerZeroSmallStepEdgeHeight)) {
345                 revert NotPowerOfTwo(layerZeroSmallStepEdgeHeight);
346             }
347             LAYERZERO_SMALLSTEPEDGE_HEIGHT = layerZeroSmallStepEdgeHeight;
348     
349             // ensure that there is at least on of each type of level
350             if (_numBigStepLevel == 0) {
351                 revert ZeroBigStepLevels();
352             }
353             // ensure there's also space for the block level and the small step level
354             // in total level parameters
355             if (_numBigStepLevel > 253) {
356                 revert BigStepLevelsTooMany(_numBigStepLevel);
357             }
358             NUM_BIGSTEP_LEVEL = _numBigStepLevel;
359     
360             if (_numBigStepLevel + 2 != _stakeAmounts.length) {
361                 revert StakeAmountsMismatch(_stakeAmounts.length, _numBigStepLevel + 2);
362             }
363             stakeAmounts = _stakeAmounts;
364         }
371         function createLayerZeroEdge(CreateEdgeArgs calldata args) external returns (bytes32) {
372             // Check if whitelist is enabled in the Rollup
373             // We only enforce whitelist in this function as it may exhaust resources
374             bool whitelistEnabled = !assertionChain.validatorWhitelistDisabled();
375     
376             if (whitelistEnabled && !assertionChain.isValidator(msg.sender)) {
377                 revert NotValidator(msg.sender);
378             }
379     
380             EdgeAddedData memory edgeAdded;
381             EdgeType eType = ChallengeEdgeLib.levelToType(args.level, NUM_BIGSTEP_LEVEL);
382             uint256 expectedEndHeight = getLayerZeroEndHeight(eType);
383             AssertionReferenceData memory ard;
384     
385             if (eType == EdgeType.Block) {
386                 // for block type edges we need to provide some extra assertion data context
387                 if (args.proof.length == 0) {
388                     revert EmptyEdgeSpecificProof();
389                 }
390                 (, AssertionStateData memory predecessorStateData, AssertionStateData memory claimStateData) =
391                     abi.decode(args.proof, (bytes32[], AssertionStateData, AssertionStateData));
392     
393                 assertionChain.validateAssertionHash(
394                     args.claimId, claimStateData.assertionState, claimStateData.prevAssertionHash, claimStateData.inboxAcc
395                 );
396     
397                 assertionChain.validateAssertionHash(
398                     claimStateData.prevAssertionHash,
399                     predecessorStateData.assertionState,
400                     predecessorStateData.prevAssertionHash,
401                     predecessorStateData.inboxAcc
402                 );
403     
404                 if (args.endHistoryRoot != claimStateData.assertionState.endHistoryRoot) {
405                     revert EndHistoryRootMismatch(args.endHistoryRoot, claimStateData.assertionState.endHistoryRoot);
406                 }
407     
408                 ard = AssertionReferenceData(
409                     args.claimId,
410                     claimStateData.prevAssertionHash,
411                     assertionChain.isPending(args.claimId),
412                     assertionChain.getSecondChildCreationBlock(claimStateData.prevAssertionHash) > 0,
413                     predecessorStateData.assertionState,
414                     claimStateData.assertionState
415                 );
416             }
417             edgeAdded = store.createLayerZeroEdge(
418                 args, ard, oneStepProofEntry, expectedEndHeight, NUM_BIGSTEP_LEVEL, whitelistEnabled
419             );
420     
421             IERC20 st = stakeToken;
422             uint256 sa = stakeAmounts[args.level];
423             // when a zero layer edge is created it must include stake amount. Each time a zero layer
424             // edge is created it forces the honest participants to do some work, so we want to disincentive
425             // their creation. The amount should also be enough to pay for the gas costs incurred by the honest
426             // participant. This can be arranged out of bound by the excess stake receiver.
427             // The contract initializer can disable staking by setting zeros for token or amount, to change
428             // this a new challenge manager needs to be deployed and its address updated in the assertion chain
429             if (address(st) != address(0) && sa != 0) {
430                 // since only one edge in a group of rivals can ever be confirmed, we know that we
431                 // will never need to refund more than one edge. Therefore we can immediately send
432                 // all stakes provided after the first one to an excess stake receiver.
433                 address receiver = edgeAdded.hasRival ? excessStakeReceiver : address(this);
434                 st.safeTransferFrom(msg.sender, receiver, sa);
435             }
436     
437             emit EdgeAdded(
438                 edgeAdded.edgeId,
439                 edgeAdded.mutualId,
440                 edgeAdded.originId,
441                 edgeAdded.claimId,
442                 edgeAdded.length,
443                 edgeAdded.level,
444                 edgeAdded.hasRival,
445                 edgeAdded.isLayerZero
446             );
447             return edgeAdded.edgeId;
448         }


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/challengeV2/EdgeChallengeManager.sol#L0:0

```solidity
File: src/challengeV2/libraries/EdgeChallengeManagerLib.sol


213         function layerZeroTypeSpecificChecks(
214             EdgeStore storage store,
215             CreateEdgeArgs calldata args,
216             AssertionReferenceData memory ard,
217             IOneStepProofEntry oneStepProofEntry,
218             uint8 numBigStepLevel
219         ) private view returns (ProofData memory, bytes32) {
220             if (ChallengeEdgeLib.levelToType(args.level, numBigStepLevel) == EdgeType.Block) {
221                 // origin id is the assertion which is the root of challenge
222                 // all rivals and their children share the same origin id - it is a link to the information
223                 // they agree on
224                 bytes32 originId = ard.predecessorId;
225     
226                 // Sanity check: The assertion reference data should be related to the claim
227                 // Of course the caller can provide whatever args they wish, so this is really just a helpful
228                 // check to avoid mistakes
229                 if (ard.assertionHash == 0) {
230                     revert AssertionHashEmpty();
231                 }
232                 if (ard.assertionHash != args.claimId) {
233                     revert AssertionHashMismatch(ard.assertionHash, args.claimId);
234                 }
235     
236                 // if the assertion is already confirmed or rejected then it cant be referenced as a claim
237                 if (!ard.isPending) {
238                     revert AssertionNotPending();
239                 }
240     
241                 // if the claim doesnt have a sibling then it is undisputed, there's no need
242                 // to open challenge edges for it
243                 if (!ard.hasSibling) {
244                     revert AssertionNoSibling();
245                 }
246     
247                 // parse the inclusion proof for later use
248                 if (args.proof.length == 0) {
249                     revert EmptyEdgeSpecificProof();
250                 }
251                 (bytes32[] memory inclusionProof,,) =
252                     abi.decode(args.proof, (bytes32[], AssertionStateData, AssertionStateData));
253     
254                 // check the start and end execution states exist, the block hash entry should be non zero
255                 if (ard.startState.machineStatus == MachineStatus.RUNNING) {
256                     revert EmptyStartMachineStatus();
257                 }
258                 if (ard.endState.machineStatus == MachineStatus.RUNNING) {
259                     revert EmptyEndMachineStatus();
260                 }
261     
262                 // Create machine hashes out of the proven state
263                 bytes32 startStateHash = oneStepProofEntry.getMachineHash(ard.startState.toExecutionState());
264                 bytes32 endStateHash = oneStepProofEntry.getMachineHash(ard.endState.toExecutionState());
265     
266                 return (ProofData(startStateHash, endStateHash, inclusionProof), originId);
267             } else {
268                 // Claim must be length one. If it is unrivaled then its unrivaled time is ticking up, so there's
269                 // no need to create claims against it
270                 if (!hasLengthOneRival(store, args.claimId)) {
271                     revert ClaimEdgeNotLengthOneRival(args.claimId);
272                 }
273     
274                 // hasLengthOneRival checks existance, so we can use getNoCheck
275                 ChallengeEdge storage claimEdge = getNoCheck(store, args.claimId);
276     
277                 // origin id is the mutual id of the claim
278                 // all rivals and their children share the same origin id - it is a link to the information
279                 // they agree on
280                 bytes32 originId = claimEdge.mutualId();
281     
282                 // once a claim is confirmed it's status can never become pending again, so there is no point
283                 // opening a challenge that references it
284                 if (claimEdge.status != EdgeStatus.Pending) {
285                     revert ClaimEdgeNotPending();
286                 }
287     
288                 // the edge must be a level up from the claim
289                 if (args.level != nextEdgeLevel(claimEdge.level, numBigStepLevel)) {
290                     revert ClaimEdgeInvalidLevel(args.level, claimEdge.level);
291                 }
292     
293                 // parse the proofs
294                 if (args.proof.length == 0) {
295                     revert EmptyEdgeSpecificProof();
296                 }
297                 (
298                     bytes32 startState,
299                     bytes32 endState,
300                     bytes32[] memory claimStartInclusionProof,
301                     bytes32[] memory claimEndInclusionProof,
302                     bytes32[] memory edgeInclusionProof
303                 ) = abi.decode(args.proof, (bytes32, bytes32, bytes32[], bytes32[], bytes32[]));
304     
305                 // if the start and end states are consistent with the claim edge
306                 // this guarantees that the edge we're creating is a 'continuation' of the claim edge, it is
307                 // a commitment to the states that between start and end states of the claim
308                 MerkleTreeLib.verifyInclusionProof(
309                     claimEdge.startHistoryRoot, startState, claimEdge.startHeight, claimStartInclusionProof
310                 );
311     
312                 // it's doubly important to check the end state since if the end state since the claim id is
313                 // not part of the edge id, so we need to ensure that it's not possible to create two edges of the
314                 // same id, but with different claim id. Ensuring that the end state is linked to the claim,
315                 // and later ensuring that the end state is part of the history commitment of the new edge ensures
316                 // that the end history root of the new edge will be different for different claim ids, and therefore
317                 // the edge ids will be different
318                 MerkleTreeLib.verifyInclusionProof(
319                     claimEdge.endHistoryRoot, endState, claimEdge.endHeight, claimEndInclusionProof
320                 );
321     
322                 return (ProofData(startState, endState, edgeInclusionProof), originId);
323             }
324         }
604         function bisectEdge(EdgeStore storage store, bytes32 edgeId, bytes32 bisectionHistoryRoot, bytes memory prefixProof)
605             internal
606             returns (bytes32, EdgeAddedData memory, EdgeAddedData memory)
607         {
608             if (store.edges[edgeId].status != EdgeStatus.Pending) {
609                 revert EdgeNotPending(edgeId, store.edges[edgeId].status);
610             }
611             if (!hasRival(store, edgeId)) {
612                 revert EdgeUnrivaled(edgeId);
613             }
614     
615             // cannot bisect an edge twice
616             // has rival above checks the edge - so no need to check again
617             ChallengeEdge memory ce = getNoCheck(store, edgeId);
618     
619             // bisections occur at deterministic heights, this ensures that
620             // rival edges bisect at the same height, and create the same child if they agree
621             uint256 middleHeight = mandatoryBisectionHeight(ce.startHeight, ce.endHeight);
622             {
623                 (bytes32[] memory preExpansion, bytes32[] memory proof) = abi.decode(prefixProof, (bytes32[], bytes32[]));
624                 MerkleTreeLib.verifyPrefixProof(
625                     bisectionHistoryRoot, middleHeight + 1, ce.endHistoryRoot, ce.endHeight + 1, preExpansion, proof
626                 );
627             }
628     
629             bytes32 lowerChildId;
630             EdgeAddedData memory lowerChildAdded;
631             {
632                 // midpoint proof it valid, create and store the children
633                 ChallengeEdge memory lowerChild = ChallengeEdgeLib.newChildEdge(
634                     ce.originId, ce.startHistoryRoot, ce.startHeight, bisectionHistoryRoot, middleHeight, ce.level
635                 );
636                 lowerChildId = lowerChild.idMem();
637                 // it's possible that the store already has the lower child if it was created by a rival
638                 // (aka a merge move)
639                 if (!store.edges[lowerChildId].exists()) {
640                     lowerChildAdded = add(store, lowerChild);
641                 }
642             }
643     
644             EdgeAddedData memory upperChildAdded;
645             {
646                 ChallengeEdge memory upperChild = ChallengeEdgeLib.newChildEdge(
647                     ce.originId, bisectionHistoryRoot, middleHeight, ce.endHistoryRoot, ce.endHeight, ce.level
648                 );
649     
650                 // add checks existence and throws if the id already exists
651                 upperChildAdded = add(store, upperChild);
652             }
653     
654             store.edges[edgeId].setChildren(lowerChildId, upperChildAdded.edgeId);
655     
656             return (lowerChildId, lowerChildAdded, upperChildAdded);
657         }
766         function confirmEdgeByOneStepProof(
767             EdgeStore storage store,
768             bytes32 edgeId,
769             IOneStepProofEntry oneStepProofEntry,
770             OneStepData calldata oneStepData,
771             ExecutionContext memory execCtx,
772             bytes32[] calldata beforeHistoryInclusionProof,
773             bytes32[] calldata afterHistoryInclusionProof,
774             uint8 numBigStepLevel,
775             uint256 bigStepHeight,
776             uint256 smallStepHeight
777         ) internal {
778             if (!store.edges[edgeId].exists()) {
779                 revert EdgeNotExists(edgeId);
780             }
781     
782             // edge must of type SmallStep
783             if (ChallengeEdgeLib.levelToType(store.edges[edgeId].level, numBigStepLevel) != EdgeType.SmallStep) {
784                 revert EdgeTypeNotSmallStep(store.edges[edgeId].level);
785             }
786     
787             // edge must be length one to execute one step proofs against
788             if (store.edges[edgeId].length() != 1) {
789                 revert EdgeNotLengthOne(store.edges[edgeId].length());
790             }
791     
792             // Get the machine step that corresponds to the start height of this edge
793             // To do this we sum the machine steps of the edges in each of the preceeding levels.
794             // We do not include the block height, since each step at the block level is a new block
795             // and new blocks reset the machine step to 0.
796             uint256 machineStep = store.edges[edgeId].startHeight;
797             {
798                 bytes32 cursor = edgeId;
799                 uint256 stepSize = smallStepHeight;
800                 while (store.edges[cursor].level > 1) {
801                     bytes32 nextEdgeId = store.edges[cursor].originId;
802                     // We can traverse to previous levels using the origin id
803                     cursor = store.firstRivals[nextEdgeId];
804                     // sum the stepSize * offset from 0 at this level
805                     machineStep += stepSize * store.edges[cursor].startHeight;
806                     // the step size at each level is the product of the heights at all succeeding levels
807                     stepSize *= bigStepHeight;
808                 }
809             }
810     
811             // the state in the onestep data must be committed to by the startHistoryRoot
812             MerkleTreeLib.verifyInclusionProof(
813                 store.edges[edgeId].startHistoryRoot, oneStepData.beforeHash, machineStep, beforeHistoryInclusionProof
814             );
815     
816             // execute the single step to produce the after state
817             bytes32 afterHash =
818                 oneStepProofEntry.proveOneStep(execCtx, machineStep, oneStepData.beforeHash, oneStepData.proof);
819     
820             // check that the after state was indeed committed to by the endHistoryRoot
821             MerkleTreeLib.verifyInclusionProof(
822                 store.edges[edgeId].endHistoryRoot, afterHash, machineStep + 1, afterHistoryInclusionProof
823             );
824     
825             // also checks that no other rival has been confirmed
826             setConfirmedRival(store, edgeId);
827     
828             // we also check the edge is pending in setConfirmed()
829             store.edges[edgeId].setConfirmed();
830             store.edges[edgeId].totalTimeUnrivaledCache = type(uint64).max;
831         }


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/challengeV2/libraries/EdgeChallengeManagerLib.sol#L0:0

```solidity
File: src/challengeV2/libraries/MerkleTreeLib.sol


151         function appendCompleteSubTree(bytes32[] memory me, uint256 level, bytes32 subtreeRoot)
152             internal
153             pure
154             returns (bytes32[] memory)
155         {
156             // we use number representations of the levels elsewhere, so we need to ensure we're appending a leve
157             // that's too high to use in uint
158             require(level < MAX_LEVEL, "Level too high");
159             require(subtreeRoot != 0, "Cannot append empty subtree");
160             require(me.length <= MAX_LEVEL, "Merkle expansion too large");
161     
162             if (me.length == 0) {
163                 bytes32[] memory empty = new bytes32[](level + 1);
164                 empty[level] = subtreeRoot;
165                 return empty;
166             }
167     
168             // This technically isn't necessary since it would be caught by the i < level check
169             // on the last loop of the for-loop below, but we add it for a clearer error message
170             require(level < me.length, "Level greater than highest level of current expansion");
171     
172             bytes32 accumHash = subtreeRoot;
173             uint256 meSize = treeSize(me);
174             uint256 postSize = meSize + 2 ** level;
175     
176             // if by appending the sub tree we increase the numbe of most sig bits of the size, that means
177             // we'll need more space in the expansion to describe the tree, so we enlarge by one
178             bytes32[] memory next = UintUtilsLib.mostSignificantBit(postSize) > UintUtilsLib.mostSignificantBit(meSize)
179                 ? new bytes32[](me.length + 1)
180                 : new bytes32[](me.length);
181     
182             // ensure we're never creating an expansion that's too big
183             require(next.length <= MAX_LEVEL, "Append creates oversize tree");
184     
185             // loop through all the levels in self and try to append the new subtree
186             // since each node has two children by appending a subtree we may complete another one
187             // in the level above. So we move through the levels updating the result at each level
188             for (uint256 i = 0; i < me.length; i++) {
189                 // we can only append at the level of the smallest complete sub tree or below
190                 // appending above this level would mean create "holes" in the tree
191                 // we can find the smallest complete sub tree by looking for the first entry in the merkle expansion
192                 if (i < level) {
193                     // we're below the level we want to append - no complete sub trees allowed down here
194                     // if the level is 0 there are no complete subtrees, and we therefore cannot be too low
195                     require(me[i] == 0, "Append above least significant bit");
196                 } else {
197                     // we're at or above the level
198                     if (accumHash == 0) {
199                         // no more changes to propagate upwards - just fill the tree
200                         next[i] = me[i];
201                     } else {
202                         // we have a change to propagate
203                         if (me[i] == 0) {
204                             // if the level is currently empty we can just add the change
205                             next[i] = accumHash;
206                             // and then there's nothing more to propagate
207                             accumHash = 0;
208                         } else {
209                             // if the level is not currently empty then we combine it with propagation
210                             // change, and propagate that to the level above. This level is now part of a complete subtree
211                             // so we zero it out
212                             next[i] = 0;
213                             accumHash = keccak256(abi.encodePacked(me[i], accumHash));
214                         }
215                     }
216                 }
217             }
218     
219             // we had a final change to propagate above the existing highest complete sub tree
220             // so we have a new highest complete sub tree in the level above - this was why we
221             // increased the storeage above
222             if (accumHash != 0) {
223                 next[next.length - 1] = accumHash;
224             }
225     
226             // it should never be possible to achieve this ever we sized the array correctly
227             // so this is just a sanity check
228             require(next[next.length - 1] != 0, "Last entry zero");
229     
230             return next;
231         }


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/challengeV2/libraries/MerkleTreeLib.sol#L0:0

```solidity
File: src/rollup/BOLDUpgradeAction.sol


464         function perform(address[] memory validators) external {
465             // tidy up the old rollup - pause it and refund stakes
466             cleanupOldRollup();
467     
468             // create the config, we do this now so that we compute the expected rollup address
469             Config memory config = createConfig();
470     
471             // deploy the new challenge manager
472             IEdgeChallengeManager challengeManager = IEdgeChallengeManager(
473                 address(
474                     new TransparentUpgradeableProxy(
475                         address(IMPL_CHALLENGE_MANAGER),
476                         address(PROXY_ADMIN_BRIDGE), // use the same proxy admin as the bridge
477                         ""
478                     )
479                 )
480             );
481     
482             // now that all the dependent contracts are pointed at the new address we can
483             // deploy and init the new rollup
484             ContractDependencies memory connectedContracts = ContractDependencies({
485                 bridge: IBridge(BRIDGE),
486                 sequencerInbox: ISequencerInbox(SEQ_INBOX),
487                 inbox: IInboxBase(INBOX),
488                 outbox: IOutbox(OUTBOX),
489                 rollupEventInbox: IRollupEventInbox(REI),
490                 challengeManager: challengeManager,
491                 rollupAdminLogic: IMPL_NEW_ROLLUP_ADMIN,
492                 rollupUserLogic: IRollupUser(IMPL_NEW_ROLLUP_USER),
493                 validatorWalletCreator: ROLLUP_READER.validatorWalletCreator()
494             });
495     
496             // upgrade the surrounding contracts eg bridge, outbox, seq inbox, rollup event inbox
497             // to set of the new rollup address
498             bytes32 rollupSalt = keccak256(abi.encode(config));
499             address expectedRollupAddress =
500                 Create2Upgradeable.computeAddress(rollupSalt, keccak256(type(RollupProxy).creationCode));
501             upgradeSurroundingContracts(expectedRollupAddress);
502     
503             challengeManager.initialize({
504                 _assertionChain: IAssertionChain(expectedRollupAddress),
505                 _challengePeriodBlocks: CHALLENGE_PERIOD_BLOCKS,
506                 _oneStepProofEntry: OSP,
507                 layerZeroBlockEdgeHeight: config.layerZeroBlockEdgeHeight,
508                 layerZeroBigStepEdgeHeight: config.layerZeroBigStepEdgeHeight,
509                 layerZeroSmallStepEdgeHeight: config.layerZeroSmallStepEdgeHeight,
510                 _stakeToken: IERC20(config.stakeToken),
511                 _stakeAmounts: config.miniStakeValues,
512                 _excessStakeReceiver: L1_TIMELOCK,
513                 _numBigStepLevel: config.numBigStepLevel
514             });
515     
516             RollupProxy rollup = new RollupProxy{salt: rollupSalt}();
517             require(address(rollup) == expectedRollupAddress, "UNEXPCTED_ROLLUP_ADDR");
518     
519             // initialize the rollup with this contract as owner to set batch poster and validators
520             // it will transfer the ownership back to the actual owner later
521             address actualOwner = config.owner;
522             config.owner = address(this);
523     
524             rollup.initializeProxy(config, connectedContracts);
525     
526             if (validators.length != 0) {
527                 bool[] memory _vals = new bool[](validators.length);
528                 for (uint256 i = 0; i < validators.length; i++) {
529                     require(ROLLUP_READER.isValidator(validators[i]), "UNEXPECTED_NEW_VALIDATOR");
530                     _vals[i] = true;
531                 }
532                 IRollupAdmin(address(rollup)).setValidator(validators, _vals);
533             }
534             if (DISABLE_VALIDATOR_WHITELIST) {
535                 IRollupAdmin(address(rollup)).setValidatorWhitelistDisabled(DISABLE_VALIDATOR_WHITELIST);
536             }
537     
538             IRollupAdmin(address(rollup)).setOwner(actualOwner);
539     
540             emit RollupMigrated(expectedRollupAddress, address(challengeManager));
541         }


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/rollup/BOLDUpgradeAction.sol#L0:0

```solidity
File: src/rollup/RollupAdminLogic.sol


18          function initialize(Config calldata config, ContractDependencies calldata connectedContracts)
19              external
20              override
21              onlyProxy
22              initializer
23          {
24              rollupDeploymentBlock = block.number;
25              bridge = connectedContracts.bridge;
26              connectedContracts.bridge.setDelayedInbox(address(connectedContracts.inbox), true);
27              connectedContracts.bridge.setSequencerInbox(address(connectedContracts.sequencerInbox));
28      
29              inbox = connectedContracts.inbox;
30              outbox = connectedContracts.outbox;
31              connectedContracts.bridge.setOutbox(address(connectedContracts.outbox), true);
32              rollupEventInbox = connectedContracts.rollupEventInbox;
33      
34              // dont need to connect and initialize the event inbox if it's already been initialized
35              if (!bridge.allowedDelayedInboxes(address(connectedContracts.rollupEventInbox))) {
36                  connectedContracts.bridge.setDelayedInbox(address(connectedContracts.rollupEventInbox), true);
37                  connectedContracts.rollupEventInbox.rollupInitialized(config.chainId, config.chainConfig);
38              }
39      
40              if (connectedContracts.sequencerInbox.totalDelayedMessagesRead() == 0) {
41                  connectedContracts.sequencerInbox.addSequencerL2Batch(0, "", 1, IGasRefunder(address(0)), 0, 1);
42              }
43      
44              validatorWalletCreator = connectedContracts.validatorWalletCreator;
45              challengeManager = connectedContracts.challengeManager;
46      
47              confirmPeriodBlocks = config.confirmPeriodBlocks;
48              chainId = config.chainId;
49              baseStake = config.baseStake;
50              wasmModuleRoot = config.wasmModuleRoot;
51              // A little over 15 minutes
52              minimumAssertionPeriod = 75;
53              challengeGracePeriodBlocks = config.challengeGracePeriodBlocks;
54      
55              // loser stake is now sent directly to loserStakeEscrow, it must not
56              // be address(0) because some token do not allow transfers to address(0)
57              require(config.loserStakeEscrow != address(0), "INVALID_ESCROW_0");
58              loserStakeEscrow = config.loserStakeEscrow;
59      
60              stakeToken = config.stakeToken;
61              anyTrustFastConfirmer = config.anyTrustFastConfirmer;
62      
63              bytes32 parentAssertionHash = bytes32(0);
64              bytes32 inboxAcc = bytes32(0);
65              bytes32 genesisHash = RollupLib.assertionHash({
66                  parentAssertionHash: parentAssertionHash,
67                  afterStateHash: config.genesisAssertionState.hash(),
68                  inboxAcc: inboxAcc
69              });
70      
71              uint256 currentInboxCount = bridge.sequencerMessageCount();
72              // ensure to move the inbox forward by at least one message
73              if (currentInboxCount == config.genesisInboxCount) {
74                  currentInboxCount += 1;
75              }
76              AssertionNode memory initialAssertion = AssertionNodeLib.createAssertion(
77                  true,
78                  RollupLib.configHash({
79                      wasmModuleRoot: wasmModuleRoot,
80                      requiredStake: baseStake,
81                      challengeManager: address(challengeManager),
82                      confirmPeriodBlocks: confirmPeriodBlocks,
83                      nextInboxPosition: uint64(currentInboxCount)
84                  })
85              );
86              initializeCore(initialAssertion, genesisHash);
87      
88              AssertionInputs memory assertionInputs;
89              assertionInputs.afterState = config.genesisAssertionState;
90              emit AssertionCreated(
91                  genesisHash,
92                  parentAssertionHash,
93                  assertionInputs,
94                  inboxAcc,
95                  currentInboxCount,
96                  wasmModuleRoot,
97                  baseStake,
98                  address(challengeManager),
99                  confirmPeriodBlocks
100             );
101             if (_hostChainIsArbitrum) {
102                 _assertionCreatedAtArbSysBlock[genesisHash] = ArbSys(address(100)).arbBlockNumber();
103             }
104     
105             emit RollupInitialized(config.wasmModuleRoot, config.chainId);
106         }


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/rollup/RollupAdminLogic.sol#L0:0

```solidity
File: src/rollup/RollupCore.sol


365         function createNewAssertion(
366             AssertionInputs calldata assertion,
367             bytes32 prevAssertionHash,
368             bytes32 expectedAssertionHash
369         ) internal returns (bytes32 newAssertionHash, bool overflowAssertion) {
370             // Validate the config hash
371             RollupLib.validateConfigHash(
372                 assertion.beforeStateData.configData, getAssertionStorage(prevAssertionHash).configHash
373             );
374     
375             // reading inbox messages always terminates in either a finished or errored state
376             // although the challenge protocol that any invalid terminal state will be proven incorrect
377             // we can do a quick sanity check here
378             require(
379                 assertion.afterState.machineStatus == MachineStatus.FINISHED
380                     || assertion.afterState.machineStatus == MachineStatus.ERRORED,
381                 "BAD_AFTER_STATUS"
382             );
383     
384             // validate the provided before state is correct by checking that it's part of the prev assertion hash
385             require(
386                 RollupLib.assertionHash(
387                     assertion.beforeStateData.prevPrevAssertionHash,
388                     assertion.beforeState,
389                     assertion.beforeStateData.sequencerBatchAcc
390                 ) == prevAssertionHash,
391                 "INVALID_BEFORE_STATE"
392             );
393     
394             // The rollup cannot advance from an errored state
395             // If it reaches an errored state it must be corrected by an administrator
396             // This will involve updating the wasm root and creating an alternative assertion
397             // that consumes the correct number of inbox messages, and correctly transitions to the
398             // FINISHED state so that normal progress can continue
399             require(assertion.beforeState.machineStatus == MachineStatus.FINISHED, "BAD_PREV_STATUS");
400     
401             AssertionNode storage prevAssertion = getAssertionStorage(prevAssertionHash);
402             // Required inbox position through which the next assertion (the one after this new assertion) must consume
403             uint256 nextInboxPosition;
404             bytes32 sequencerBatchAcc;
405             {
406                 // This new assertion consumes the messages from prevInboxPosition to afterInboxPosition
407                 GlobalState calldata afterGS = assertion.afterState.globalState;
408                 GlobalState calldata beforeGS = assertion.beforeState.globalState;
409     
410                 // there are 3 kinds of assertions that can be made. Assertions must be made when they fill the maximum number
411                 // of blocks, or when they process all messages up to prev.nextInboxPosition. When they fill the max
412                 // blocks, but dont manage to process all messages, we call this an "overflow" assertion.
413                 // 1. ERRORED assertion
414                 //    The machine finished in an ERRORED state. This can happen with processing any
415                 //    messages, or moving the position in the message.
416                 // 2. FINISHED assertion that did not overflow
417                 //    The machine finished as normal, and fully processed all the messages up to prev.nextInboxPosition.
418                 //    In this case the inbox position must equal prev.nextInboxPosition and position in message must be 0
419                 // 3. FINISHED assertion that did overflow
420                 //    The machine finished as normal, but didn't process all messages in the inbox.
421                 //    The inbox can be anywhere between the previous assertion's position and the nextInboxPosition, exclusive.
422     
423                 //    All types of assertion must have inbox position in the range prev.inboxPosition <= x <= prev.nextInboxPosition
424                 require(afterGS.comparePositions(beforeGS) >= 0, "INBOX_BACKWARDS");
425                 int256 afterStateCmpMaxInbox =
426                     afterGS.comparePositionsAgainstStartOfBatch(assertion.beforeStateData.configData.nextInboxPosition);
427                 require(afterStateCmpMaxInbox <= 0, "INBOX_TOO_FAR");
428     
429                 if (assertion.afterState.machineStatus != MachineStatus.ERRORED && afterStateCmpMaxInbox < 0) {
430                     // If we didn't reach the target next inbox position, this is an overflow assertion.
431                     overflowAssertion = true;
432                     // This shouldn't be necessary, but might as well constrain the assertion to be non-empty
433                     require(afterGS.comparePositions(beforeGS) > 0, "OVERFLOW_STANDSTILL");
434                 }
435                 // Inbox position at the time of this assertion being created
436                 uint256 currentInboxPosition = bridge.sequencerMessageCount();
437                 // Cannot read more messages than currently exist in the inbox
438                 require(afterGS.comparePositionsAgainstStartOfBatch(currentInboxPosition) <= 0, "INBOX_PAST_END");
439     
440                 // under normal circumstances prev.nextInboxPosition is guaranteed to exist
441                 // because we populate it from bridge.sequencerMessageCount(). However, when
442                 // the inbox message count doesnt change we artificially increase it by 1 as explained below
443                 // in this case we need to ensure when the assertion is made the inbox messages are available
444                 // to ensure that a valid assertion can actually be made.
445                 require(
446                     assertion.beforeStateData.configData.nextInboxPosition <= currentInboxPosition, "INBOX_NOT_POPULATED"
447                 );
448     
449                 // The next assertion must consume all the messages that are currently found in the inbox
450                 uint256 afterInboxPosition = afterGS.getInboxPosition();
451                 if (afterInboxPosition == currentInboxPosition) {
452                     // No new messages have been added to the inbox since the last assertion
453                     // In this case if we set the next inbox position to the current one we would be insisting that
454                     // the next assertion process no messages. So instead we increment the next inbox position to current
455                     // plus one, so that the next assertion will process exactly one message.
456                     // Thus, no assertion can be empty (except the genesis assertion, which is created
457                     // via a different codepath).
458                     nextInboxPosition = currentInboxPosition + 1;
459                 } else {
460                     nextInboxPosition = currentInboxPosition;
461                 }
462     
463                 // only the genesis assertion processes no messages, and that assertion is created
464                 // when we initialize this contract. Therefore, all assertions created here should have a non
465                 // zero inbox position.
466                 require(afterInboxPosition != 0, "EMPTY_INBOX_COUNT");
467     
468                 // Fetch the inbox accumulator for this message count. Fetching this and checking against it
469                 // allows the assertion creator to ensure they're creating an assertion against the expected
470                 // inbox messages
471                 sequencerBatchAcc = bridge.sequencerInboxAccs(afterInboxPosition - 1);
472             }
473     
474             newAssertionHash = RollupLib.assertionHash(prevAssertionHash, assertion.afterState, sequencerBatchAcc);
475     
476             // allow an assertion creator to ensure that they're creating their assertion against the expected state
477             require(
478                 newAssertionHash == expectedAssertionHash || expectedAssertionHash == bytes32(0),
479                 "UNEXPECTED_ASSERTION_HASH"
480             );
481     
482             // the assertion hash is unique - it's only possible to have one correct assertion hash
483             // per assertion. Therefore we can check if this assertion has already been made, and if so
484             // we can revert
485             require(getAssertionStorage(newAssertionHash).status == AssertionStatus.NoAssertion, "ASSERTION_SEEN");
486     
487             // state updates
488             AssertionNode memory newAssertion = AssertionNodeLib.createAssertion(
489                 prevAssertion.firstChildBlock == 0, // assumes block 0 is impossible
490                 RollupLib.configHash({
491                     wasmModuleRoot: wasmModuleRoot,
492                     requiredStake: baseStake,
493                     challengeManager: address(challengeManager),
494                     confirmPeriodBlocks: confirmPeriodBlocks,
495                     nextInboxPosition: uint64(nextInboxPosition)
496                 })
497             );
498     
499             // Fetch a storage reference to prevAssertion since we copied our other one into memory
500             // and we don't have enough stack available to keep to keep the previous storage reference around
501             prevAssertion.childCreated();
502             _assertions[newAssertionHash] = newAssertion;
503     
504             emit AssertionCreated(
505                 newAssertionHash,
506                 prevAssertionHash,
507                 assertion,
508                 sequencerBatchAcc,
509                 nextInboxPosition,
510                 wasmModuleRoot,
511                 baseStake,
512                 address(challengeManager),
513                 confirmPeriodBlocks
514             );
515             if (_hostChainIsArbitrum) {
516                 _assertionCreatedAtArbSysBlock[newAssertionHash] = ArbSys(address(100)).arbBlockNumber();
517             }
518         }


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/rollup/RollupCore.sol#L0:0

```solidity
File: src/rollup/RollupCreator.sol


137         function createRollup(RollupDeploymentParams memory deployParams)
138             public
139             payable
140             returns (address)
141         {
142             {
143                 // Make sure the immutable maxDataSize is as expected
144                 (
145                     ,
146                     ISequencerInbox ethSequencerInbox,
147                     ISequencerInbox ethDelayBufferableSequencerInbox,
148                     IInboxBase ethInbox,
149                     ,
150     
151                 ) = bridgeCreator.ethBasedTemplates();
152                 require(
153                     deployParams.maxDataSize == ethSequencerInbox.maxDataSize(),
154                     "SI_MAX_DATA_SIZE_MISMATCH"
155                 );
156                 require(
157                     deployParams.maxDataSize == ethDelayBufferableSequencerInbox.maxDataSize(),
158                     "SI_MAX_DATA_SIZE_MISMATCH"
159                 );
160                 require(deployParams.maxDataSize == ethInbox.maxDataSize(), "I_MAX_DATA_SIZE_MISMATCH");
161     
162                 (
163                     ,
164                     ISequencerInbox erc20SequencerInbox,
165                     ISequencerInbox erc20DelayBufferableSequencerInbox,
166                     IInboxBase erc20Inbox,
167                     ,
168     
169                 ) = bridgeCreator.erc20BasedTemplates();
170                 require(
171                     deployParams.maxDataSize == erc20SequencerInbox.maxDataSize(),
172                     "SI_MAX_DATA_SIZE_MISMATCH"
173                 );
174                 require(
175                     deployParams.maxDataSize == erc20DelayBufferableSequencerInbox.maxDataSize(),
176                     "SI_MAX_DATA_SIZE_MISMATCH"
177                 );
178                 require(
179                     deployParams.maxDataSize == erc20Inbox.maxDataSize(),
180                     "I_MAX_DATA_SIZE_MISMATCH"
181                 );
182             }
183     
184             // create proxy admin which will manage bridge contracts
185             ProxyAdmin proxyAdmin = new ProxyAdmin();
186     
187             // Create the rollup proxy to figure out the address and initialize it later
188             RollupProxy rollup = new RollupProxy{salt: keccak256(abi.encode(deployParams))}();
189     
190             BridgeCreator.BridgeContracts memory bridgeContracts = bridgeCreator.createBridge(
191                 address(proxyAdmin),
192                 address(rollup),
193                 deployParams.nativeToken,
194                 deployParams.config.sequencerInboxMaxTimeVariation,
195                 deployParams.config.bufferConfig
196             );
197     
198             IEdgeChallengeManager challengeManager = createChallengeManager(address(rollup), address(proxyAdmin), deployParams.config);
199     
200             // deploy and init upgrade executor
201             address upgradeExecutor = _deployUpgradeExecutor(deployParams.config.owner, proxyAdmin);
202     
203             // upgradeExecutor shall be proxyAdmin's owner
204             proxyAdmin.transferOwnership(address(upgradeExecutor));
205     
206             // initialize the rollup with this contract as owner to set batch poster and validators
207             // it will transfer the ownership to the upgrade executor later
208             deployParams.config.owner = address(this);
209             rollup.initializeProxy(
210                 deployParams.config,
211                 ContractDependencies({
212                     bridge: bridgeContracts.bridge,
213                     sequencerInbox: bridgeContracts.sequencerInbox,
214                     inbox: bridgeContracts.inbox,
215                     outbox: bridgeContracts.outbox,
216                     rollupEventInbox: bridgeContracts.rollupEventInbox,
217                     challengeManager: challengeManager,
218                     rollupAdminLogic: address(rollupAdminLogic),
219                     rollupUserLogic: rollupUserLogic,
220                     validatorWalletCreator: validatorWalletCreator
221                 })
222             );
223     
224             // Setting batch posters and batch poster manager
225             for (uint256 i = 0; i < deployParams.batchPosters.length; i++) {
226                 bridgeContracts.sequencerInbox.setIsBatchPoster(deployParams.batchPosters[i], true);
227             }
228             if (deployParams.batchPosterManager != address(0)) {
229                 bridgeContracts.sequencerInbox.setBatchPosterManager(deployParams.batchPosterManager);
230             }
231     
232             // Call setValidator on the newly created rollup contract just if validator set is not empty
233             if (deployParams.validators.length != 0) {
234                 bool[] memory _vals = new bool[](deployParams.validators.length);
235                 for (uint256 i = 0; i < deployParams.validators.length; i++) {
236                     _vals[i] = true;
237                 }
238                 IRollupAdmin(address(rollup)).setValidator(deployParams.validators, _vals);
239             }
240     
241             IRollupAdmin(address(rollup)).setOwner(address(upgradeExecutor));
242     
243             if (deployParams.deployFactoriesToL2) {
244                 _deployFactories(
245                     address(bridgeContracts.inbox),
246                     deployParams.nativeToken,
247                     deployParams.maxFeePerGasForRetryables
248                 );
249             }
250     
251             emit RollupCreated(
252                 address(rollup),
253                 deployParams.nativeToken,
254                 address(bridgeContracts.inbox),
255                 address(bridgeContracts.outbox),
256                 address(bridgeContracts.rollupEventInbox),
257                 address(challengeManager),
258                 address(proxyAdmin),
259                 address(bridgeContracts.sequencerInbox),
260                 address(bridgeContracts.bridge),
261                 address(upgradeExecutor),
262                 address(validatorWalletCreator)
263             );
264             return address(rollup);
265         }


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/rollup/RollupCreator.sol#L0:0

```solidity
File: src/rollup/RollupUserLogic.sol


163         function stakeOnNewAssertion(AssertionInputs calldata assertion, bytes32 expectedAssertionHash)
164             public
165             onlyValidator
166             whenNotPaused
167         {
168             // Early revert on duplicated assertion if expectedAssertionHash is set
169             require(
170                 expectedAssertionHash == bytes32(0)
171                     || getAssertionStorage(expectedAssertionHash).status == AssertionStatus.NoAssertion,
172                 "EXPECTED_ASSERTION_SEEN"
173             );
174     
175             require(isStaked(msg.sender), "NOT_STAKED");
176     
177             // requiredStake is user supplied, will be verified against configHash later
178             // the prev's requiredStake is used to make sure all children have the same stake
179             // the staker may have more than enough stake, and the entire stake will be locked
180             // we cannot do a refund here because the staker may be staker on an unconfirmed ancestor that requires more stake
181             // excess stake can be removed by calling reduceDeposit when the staker is inactive
182             require(amountStaked(msg.sender) >= assertion.beforeStateData.configData.requiredStake, "INSUFFICIENT_STAKE");
183     
184             bytes32 prevAssertion = RollupLib.assertionHash(
185                 assertion.beforeStateData.prevPrevAssertionHash,
186                 assertion.beforeState,
187                 assertion.beforeStateData.sequencerBatchAcc
188             );
189             getAssertionStorage(prevAssertion).requireExists();
190     
191             // Staker can create new assertion only if
192             // a) its last staked assertion is the prev; or
193             // b) its last staked assertion have a child
194             bytes32 lastAssertion = latestStakedAssertion(msg.sender);
195             require(
196                 lastAssertion == prevAssertion || getAssertionStorage(lastAssertion).firstChildBlock > 0,
197                 "STAKED_ON_ANOTHER_BRANCH"
198             );
199     
200             (bytes32 newAssertionHash, bool overflowAssertion) =
201                 createNewAssertion(assertion, prevAssertion, expectedAssertionHash);
202             _stakerMap[msg.sender].latestStakedAssertion = newAssertionHash;
203     
204             if (!overflowAssertion) {
205                 uint256 timeSincePrev = block.number - getAssertionStorage(prevAssertion).createdAtBlock;
206                 // Verify that assertion meets the minimum Delta time requirement
207                 require(timeSincePrev >= minimumAssertionPeriod, "TIME_DELTA");
208             }
209     
210             if (!getAssertionStorage(newAssertionHash).isFirstChild) {
211                 // We assume assertion.beforeStateData is valid here as it will be validated in createNewAssertion
212                 // only 1 of the children can be confirmed and get their stake refunded
213                 // so we send the other children's stake to the loserStakeEscrow
214                 // NOTE: if the losing staker have staked more than requiredStake, the excess stake will be stuck
215                 IERC20(stakeToken).safeTransfer(loserStakeEscrow, assertion.beforeStateData.configData.requiredStake);
216             }
217         }


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/rollup/RollupUserLogic.sol#L0:0

</details>

## NC036 - Consider using `block.number` instead of `block.timestamp`:

`block.timestamp` is vulnerable to miner manipulation and creates a potential front-running vulnerability. Consider using `block.number` instead.


```solidity
File: src/bridge/SequencerInbox.sol


224             if (block.timestamp > delaySeconds_) {
225                 bounds.minTimestamp = uint64(block.timestamp) - delaySeconds_;
227             bounds.maxTimestamp = uint64(block.timestamp) + futureSeconds_;
775                 block.timestamp,


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/bridge/SequencerInbox.sol#L0:0

## NC037 - Consider bounding input array length:

The functions below take in an unbounded array, and make function calls for entries in the array. While the function will revert if it eventually runs out of gas, it may be a nicer user experience to `require()` that the length of the array is below some reasonable maximum, so that the user doesn't have to use up a full transaction's gas only to see that the transaction reverts.


```solidity
File: src/challengeV2/EdgeChallengeManager.sol


492             for (uint256 i = 0; i < edgeIds.length; i++) {
493                 (bool updated, uint256 newValue) = store.updateTimerCacheByChildren(edgeIds[i]);
494                 if (updated) emit TimerCacheUpdated(edgeIds[i], newValue);
495             }


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/challengeV2/EdgeChallengeManager.sol#L0:0

## NC038 - Large numeric literals should use underscores for readability:

At a glance, it's quite difficult to understand how big this number is. Use underscores to make values more clear.


```solidity
File: src/bridge/DelayBuffer.sol


17          uint256 public constant BASIS = 10000;


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/bridge/DelayBuffer.sol#L0:0

```solidity
File: src/bridge/SequencerInbox.sol


906             if (keysetBytes.length >= 64 * 1024) revert KeysetTooLarge();


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/bridge/SequencerInbox.sol#L0:0

```solidity
File: src/rollup/RollupUserLogic.sol


49          uint256 public constant VALIDATOR_AFK_BLOCKS = 201600;


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/rollup/RollupUserLogic.sol#L0:0

## NC039 - Implement some type of version counter that will be incremented automatically for contract upgrades:

As part of the upgradeability of Proxies , the contract can be upgraded multiple times, where it is a systematic approach to record the version of each upgrade. For instance, you could implement this: uint256 public authorizeUpgradeCounter; function _authorizeUpgrade(address newImplementation) internal { authorizeUpgradeCounter+=1; }


```solidity
File: src/rollup/RollupAdminLogic.sol


166         function _authorizeUpgrade(address newImplementation) internal override {}


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/rollup/RollupAdminLogic.sol#L0:0

## NC040 - Cast to `bytes` or `bytes32` for clearer semantic meaning:

Using a [cast](https://ethereum.stackexchange.com/questions/30912/how-to-compare-strings-in-solidity#answer-82739) on a single argument, rather than `abi.encodePacked()` makes the intended operation more clear, leading to less reviewer confusion.


```solidity
File: src/challengeV2/libraries/MerkleTreeLib.sol


241             return appendCompleteSubTree(me, 0, keccak256(abi.encodePacked(leaf)));


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/challengeV2/libraries/MerkleTreeLib.sol#L0:0

## NC041 - Variables should be named in mixedCase style:

As the [Solidity Style Guide](https://docs.soliditylang.org/en/latest/style-guide.html#naming-styles) suggests: arguments, local variables and mutable state variables should be named in mixedCase style.


<details>
<summary>Click to show 5 findings</summary>

```solidity
File: src/bridge/ISequencerInbox.sol


274         function setIsSequencer(address addr, bool isSequencer_) external;
290             BufferConfig calldata bufferConfig_
254         function setIsBatchPoster(address addr, bool isBatchPoster_) external;
247         function setMaxTimeVariation(MaxTimeVariation memory maxTimeVariation_) external;
288             IBridge bridge_,
289             MaxTimeVariation calldata maxTimeVariation_,


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/bridge/ISequencerInbox.sol#L0:0

```solidity
File: src/bridge/SequencerInbox.sol


178             IBridge bridge_,
933         function setIsSequencer(address addr, bool isSequencer_)
142             IReader4844 reader4844_,
894         function setIsBatchPoster(address addr, bool isBatchPoster_)
180             BufferConfig memory bufferConfig_
161         function postUpgradeInit(BufferConfig memory bufferConfig_)
306             uint256 delayBlocks_ = delayBlocks;
219                 uint64 delayBlocks_,
220                 uint64 futureBlocks_,
221                 uint64 delaySeconds_,
222                 uint64 futureSeconds_
99          ISequencerInbox.MaxTimeVariation private __LEGACY_MAX_TIME_VARIATION;
179             ISequencerInbox.MaxTimeVariation calldata maxTimeVariation_,
867         function _setMaxTimeVariation(ISequencerInbox.MaxTimeVariation memory maxTimeVariation_)
847         function _setBufferConfig(BufferConfig memory bufferConfig_) internal {
947         function setBufferConfig(BufferConfig memory bufferConfig_) external onlyRollupOwner {
255                 uint64 delayBlocks_,
256                 uint64 futureBlocks_,
257                 uint64 delaySeconds_,
258                 uint64 futureSeconds_
885         function setMaxTimeVariation(ISequencerInbox.MaxTimeVariation memory maxTimeVariation_)
329             uint256 __totalDelayedMessagesRead = _totalDelayedMessagesRead;


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/bridge/SequencerInbox.sol#L0:0

```solidity
File: src/challengeV2/EdgeChallengeManager.sol


298         uint8 public NUM_BIGSTEP_LEVEL;
293         uint256 public LAYERZERO_BIGSTEPEDGE_HEIGHT;
291         uint256 public LAYERZERO_BLOCKEDGE_HEIGHT;
295         uint256 public LAYERZERO_SMALLSTEPEDGE_HEIGHT;


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/challengeV2/EdgeChallengeManager.sol#L0:0

```solidity
File: src/rollup/BOLDUpgradeAction.sol


169         constructor(uint256[] memory __array) {
84          function postUpgradeInit(BufferConfig memory bufferConfig_) external;


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/rollup/BOLDUpgradeAction.sol#L0:0

```solidity
File: src/rollup/RollupCore.sol


407                 GlobalState calldata afterGS = assertion.afterState.globalState;
408                 GlobalState calldata beforeGS = assertion.beforeState.globalState;


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/rollup/RollupCore.sol#L0:0

</details>

## NC042 - Consider using named mappings:

Consider moving to solidity version 0.8.18 or later, and using [named mappings](https://ethereum.stackexchange.com/a/145555) to make it easier to understand the purpose of each mapping.


<details>
<summary>Click to show 5 findings</summary>

```solidity
File: src/assertionStakingPool/AbsBoldStakingPool.sol


22          mapping(address => uint256) public depositBalance;


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/assertionStakingPool/AbsBoldStakingPool.sol#L0:0

```solidity
File: src/bridge/SequencerInbox.sol


95          mapping(address => bool) public isBatchPoster;
101         mapping(bytes32 => DasKeySetInfo) public dasKeySetInfo;
115         mapping(address => bool) public isSequencer;


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/bridge/SequencerInbox.sol#L0:0

```solidity
File: src/challengeV2/libraries/EdgeChallengeManagerLib.sol


76          mapping(bytes32 => ChallengeEdge) edges;
81          mapping(bytes32 => bytes32) firstRivals;
84          mapping(bytes32 => bytes32) confirmedRivals;
86          mapping(address => mapping(bytes32 => bool)) hasMadeLayerZeroRival;
86          mapping(address => mapping(bytes32 => bool)) hasMadeLayerZeroRival;


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/challengeV2/libraries/EdgeChallengeManagerLib.sol#L0:0

```solidity
File: src/rollup/BOLDUpgradeAction.sol


99          mapping(bytes32 => bytes) internal preImages;


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/rollup/BOLDUpgradeAction.sol#L0:0

```solidity
File: src/rollup/RollupCore.sol


96          mapping(address => bool) public isValidator;
99          mapping(bytes32 => AssertionNode) private _assertions;
102         mapping(address => Staker) public _stakerMap;
104         mapping(address => uint256) private _withdrawableFunds;
114         mapping(bytes32 => uint256) internal _assertionCreatedAtArbSysBlock;


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/rollup/RollupCore.sol#L0:0

</details>

## NC043 - Use allowlist/denylist rather than whitelist/blacklist:

Use alternative variants, e.g. allowlist/denylist instead of whitelist/blacklist.


<details>
<summary>Click to show 10 findings</summary>

```solidity
File: src/challengeV2/EdgeChallengeManager.sol


194         ///         This is only tracked when the validator whitelist is enabled
372             // Check if whitelist is enabled in the Rollup
373             // We only enforce whitelist in this function as it may exhaust resources
374             bool whitelistEnabled = !assertionChain.validatorWhitelistDisabled();
376             if (whitelistEnabled && !assertionChain.isValidator(msg.sender)) {
418                 args, ard, oneStepProofEntry, expectedEndHeight, NUM_BIGSTEP_LEVEL, whitelistEnabled


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/challengeV2/EdgeChallengeManager.sol#L0:0

```solidity
File: src/challengeV2/IAssertionChain.sol


27          function validatorWhitelistDisabled() external view returns (bool);


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/challengeV2/IAssertionChain.sol#L0:0

```solidity
File: src/challengeV2/libraries/ChallengeErrors.sol


107     /// @dev Thrown when the validator whitelist is enabled and the account attempting to create a layer zero edge is not whitelisted


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/challengeV2/libraries/ChallengeErrors.sol#L0:0

```solidity
File: src/challengeV2/libraries/EdgeChallengeManagerLib.sol


418             bool whitelistEnabled
428             // if the validator whitelist is enabled, we can enforce that a single party cannot create two layer zero edges that rival each other
429             // if the validator whitelist is disabled, this check serves no purpose since an attacker can create new accounts
430             if (whitelistEnabled) {


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/challengeV2/libraries/EdgeChallengeManagerLib.sol#L0:0

```solidity
File: src/rollup/BOLDUpgradeAction.sol


204         bool public immutable DISABLE_VALIDATOR_WHITELIST;
245             bool disableValidatorWhitelist;
327             DISABLE_VALIDATOR_WHITELIST = settings.disableValidatorWhitelist;
534             if (DISABLE_VALIDATOR_WHITELIST) {
535                 IRollupAdmin(address(rollup)).setValidatorWhitelistDisabled(DISABLE_VALIDATOR_WHITELIST);


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/rollup/BOLDUpgradeAction.sol#L0:0

```solidity
File: src/rollup/IRollupAdmin.sol


48           * @notice Set the addresses of the validator whitelist
51           * @param _validator addresses to set in the whitelist
52           * @param _val value to set in the whitelist for corresponding address
110          * @notice set the validatorWhitelistDisabled flag
111          * @param _validatorWhitelistDisabled new value of validatorWhitelistDisabled, i.e. true = disabled
113         function setValidatorWhitelistDisabled(bool _validatorWhitelistDisabled) external;


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/rollup/IRollupAdmin.sol#L0:0

```solidity
File: src/rollup/IRollupLogic.sol


17          function removeWhitelistAfterFork() external;
19          function removeWhitelistAfterValidatorAfk() external;


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/rollup/IRollupLogic.sol#L0:0

```solidity
File: src/rollup/RollupAdminLogic.sol


174          * @notice Set the addresses of the validator whitelist
177          * @param _validator addresses to set in the whitelist
178          * @param _val value to set in the whitelist for corresponding address
305          * @notice set the validatorWhitelistDisabled flag
306          * @param _validatorWhitelistDisabled new value of validatorWhitelistDisabled, i.e. true = disabled
308         function setValidatorWhitelistDisabled(bool _validatorWhitelistDisabled) external {
309             validatorWhitelistDisabled = _validatorWhitelistDisabled;


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/rollup/RollupAdminLogic.sol#L0:0

```solidity
File: src/rollup/RollupCore.sol


108         bool public validatorWhitelistDisabled;


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/rollup/RollupCore.sol#L0:0

```solidity
File: src/rollup/RollupUserLogic.sol


21              require(isValidator[msg.sender] || validatorWhitelistDisabled, "NOT_VALIDATOR");
38           * @notice Number of blocks since the last confirmed assertion before the validator whitelist is removed
41           *         a further 14 days before the validator whitelist is removed.
62          function removeWhitelistAfterFork() external {
63              require(!validatorWhitelistDisabled, "WHITELIST_DISABLED");
65              validatorWhitelistDisabled = true;
69           * @notice Remove the whitelist after the validator has been inactive for too long
71          function removeWhitelistAfterValidatorAfk() external {
72              require(!validatorWhitelistDisabled, "WHITELIST_DISABLED");
74              validatorWhitelistDisabled = true;


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/rollup/RollupUserLogic.sol#L0:0

</details>

## NC044 - Function names should use lowerCamelCase:

According to the Solidity [style guide](https://docs.soliditylang.org/en/latest/style-guide.html#function-names) function names should be in `mixedCase` (lowerCamelCase).


```solidity
File: src/bridge/ISequencerInbox.sol


55          function HEADER_LENGTH() external view returns (uint256);
61          function DATA_AUTHENTICATED_FLAG() external view returns (bytes1);
67          function DATA_BLOB_HEADER_FLAG() external view returns (bytes1);
73          function DAS_MESSAGE_HEADER_FLAG() external view returns (bytes1);
79          function TREE_DAS_MESSAGE_HEADER_FLAG() external view returns (bytes1);
85          function BROTLI_MESSAGE_HEADER_FLAG() external view returns (bytes1);
91          function ZERO_HEAVY_MESSAGE_HEADER_FLAG() external view returns (bytes1);


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/bridge/ISequencerInbox.sol#L0:0

## NC045 - Consider adding a deny-list:

Doing so will significantly increase centralization, but will help to prevent hackers from using stolen tokens.


<details>
<summary>Click to show 12 findings</summary>

```solidity
File: src/assertionStakingPool/AssertionStakingPool.sol


21      contract AssertionStakingPool is AbsBoldStakingPool, IAssertionStakingPool {


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/assertionStakingPool/AssertionStakingPool.sol#L0:0

```solidity
File: src/assertionStakingPool/AssertionStakingPoolCreator.sol


13      contract AssertionStakingPoolCreator is IAssertionStakingPoolCreator {


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/assertionStakingPool/AssertionStakingPoolCreator.sol#L0:0

```solidity
File: src/assertionStakingPool/EdgeStakingPool.sol


25      contract EdgeStakingPool is AbsBoldStakingPool, IEdgeStakingPool {


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/assertionStakingPool/EdgeStakingPool.sol#L0:0

```solidity
File: src/assertionStakingPool/EdgeStakingPoolCreator.sol


13      contract EdgeStakingPoolCreator is IEdgeStakingPoolCreator {


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/assertionStakingPool/EdgeStakingPoolCreator.sol#L0:0

```solidity
File: src/bridge/SequencerInbox.sol


64      contract SequencerInbox is DelegateCallAware, GasRefundEnabled, ISequencerInbox {


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/bridge/SequencerInbox.sol#L0:0

```solidity
File: src/challengeV2/EdgeChallengeManager.sol


206     contract EdgeChallengeManager is IEdgeChallengeManager, Initializable {


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/challengeV2/EdgeChallengeManager.sol#L0:0

```solidity
File: src/rollup/BOLDUpgradeAction.sol


94      contract StateHashPreImageLookup {
123     contract RollupReader is IOldRollup {
166     contract ConstantArrayStorage {
182     contract BOLDUpgradeAction {


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/rollup/BOLDUpgradeAction.sol#L0:0

```solidity
File: src/rollup/BridgeCreator.sol


21      contract BridgeCreator is Ownable {


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/rollup/BridgeCreator.sol#L0:0

```solidity
File: src/rollup/RollupAdminLogic.sol


15      contract RollupAdminLogic is RollupCore, IRollupAdmin, DoubleLogicUUPSUpgradeable {


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/rollup/RollupAdminLogic.sol#L0:0

```solidity
File: src/rollup/RollupCreator.sol


17      contract RollupCreator is Ownable {


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/rollup/RollupCreator.sol#L0:0

```solidity
File: src/rollup/RollupProxy.sol


11      contract RollupProxy is AdminFallbackProxy {


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/rollup/RollupProxy.sol#L0:0

```solidity
File: src/rollup/RollupUserLogic.sol


15      contract RollupUserLogic is RollupCore, UUPSNotUpgradeable, IRollupUser {


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/rollup/RollupUserLogic.sol#L0:0

</details>

## NC046 - Custom errors should be used rather than `revert()`/`require()`:

Custom errors are available from solidity version 0.8.4. Custom errors are more easily processed in `try`-`catch` blocks, and are easier to re-use and maintain.


<details>
<summary>Click to show 5 findings</summary>

```solidity
File: src/bridge/SequencerInbox.sol


362             revert Deprecated();


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/bridge/SequencerInbox.sol#L0:0

```solidity
File: src/rollup/BOLDUpgradeAction.sol


107             require(h == stateHash(executionState, inboxMaxCount), "Invalid hash");
114             require(inboxMaxCount != 0, "Hash not yet set");
378             require(
453             require(
457             require(
517             require(address(rollup) == expectedRollupAddress, "UNEXPCTED_ROLLUP_ADDR");
529                     require(ROLLUP_READER.isValidator(validators[i]), "UNEXPECTED_NEW_VALIDATOR");


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/rollup/BOLDUpgradeAction.sol#L0:0

```solidity
File: src/rollup/RollupAdminLogic.sol


57              require(config.loserStakeEscrow != address(0), "INVALID_ESCROW_0");
128             require(_outbox != address(outbox), "CUR_OUTBOX");
181             require(_validator.length > 0, "EMPTY_ARRAY");
182             require(_validator.length == _val.length, "WRONG_LENGTH");
214             require(newConfirmPeriod > 0, "INVALID_CONFIRM_PERIOD");
229             require(staker.length > 0, "EMPTY_ARRAY");
272             require(newLoserStakerEscrow != address(0), "INVALID_ESCROW_0");


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/rollup/RollupAdminLogic.sol#L0:0

```solidity
File: src/rollup/RollupCreator.sol


152                 require(
156                 require(
160                 require(deployParams.maxDataSize == ethInbox.maxDataSize(), "I_MAX_DATA_SIZE_MISMATCH");
170                 require(
174                 require(
178                 require(
305                 require(sent, "Refund failed");


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/rollup/RollupCreator.sol#L0:0

```solidity
File: src/rollup/RollupUserLogic.sol


21              require(isValidator[msg.sender] || validatorWhitelistDisabled, "NOT_VALIDATOR");
28              require(_stakeToken != address(0), "NEED_STAKE_TOKEN");
63              require(!validatorWhitelistDisabled, "WHITELIST_DISABLED");
64              require(_chainIdChanged(), "CHAIN_ID_NOT_CHANGED");
72              require(!validatorWhitelistDisabled, "WHITELIST_DISABLED");
73              require(_validatorIsAfk(), "VALIDATOR_NOT_AFK");
110             require(block.number >= assertion.createdAtBlock + prevConfig.confirmPeriodBlocks, "BEFORE_DEADLINE");
113             require(prevAssertionHash == latestConfirmed(), "PREV_NOT_LATEST_CONFIRMED");
118                 require(winningEdge.claimId == assertionHash, "NOT_WINNER");
119                 require(winningEdge.status == EdgeStatus.Confirmed, "EDGE_NOT_CONFIRMED");
120                 require(winningEdge.confirmedAtBlock != 0, "ZERO_CONFIRMED_AT_BLOCK");
124                 require(
139             require(!isStaked(msg.sender), "ALREADY_STAKED");
169             require(
175             require(isStaked(msg.sender), "NOT_STAKED");
182             require(amountStaked(msg.sender) >= assertion.beforeStateData.configData.requiredStake, "INSUFFICIENT_STAKE");
195             require(
207                 require(timeSincePrev >= minimumAssertionPeriod, "TIME_DELTA");
233             require(isStaked(stakerAddress), "NOT_STAKED");
258             require(msg.sender == anyTrustFastConfirmer, "NOT_FAST_CONFIRMER");
278             require(expectedAssertionHash != bytes32(0), "EXPECTED_ASSERTION_HASH");
337             require(withdrawalAddress != address(0), "EMPTY_WITHDRAWAL_ADDRESS");
360             require(amount > 0, "NO_FUNDS_TO_WITHDRAW");


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/rollup/RollupUserLogic.sol#L0:0

</details>

## NC047 - pragma experimental ABIEncoderV2 is deprecated:

Use pragma abicoder v2 instead.


```solidity
File: src/bridge/ISequencerInbox.sol


7       pragma experimental ABIEncoderV2;


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/bridge/ISequencerInbox.sol#L0:0

## NC048 - Top level declarations should be separated by two blank lines:

  


<details>
<summary>Click to show 6 findings</summary>

```solidity
File: src/bridge/DelayBufferTypes.sol


34      


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/bridge/DelayBufferTypes.sol#L0:0

```solidity
File: src/challengeV2/libraries/ChallengeEdgeLib.sol


66      


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/challengeV2/libraries/ChallengeEdgeLib.sol#L0:0

```solidity
File: src/rollup/Assertion.sol


47      
38      
54      


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/rollup/Assertion.sol#L0:0

```solidity
File: src/rollup/AssertionState.sol


16      


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/rollup/AssertionState.sol#L0:0

```solidity
File: src/rollup/BOLDUpgradeAction.sol


39      
76      
82      
48      


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/rollup/BOLDUpgradeAction.sol#L0:0

```solidity
File: src/rollup/Config.sol


40      


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/rollup/Config.sol#L0:0

</details>

## NC049 - Duplicate import statements:

This issue arises when the same file is imported multiple times.


```solidity
File: src/rollup/RollupUserLogic.sol


12      import "./IRollupLogic.sol";


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/rollup/RollupUserLogic.sol#L0:0

## NC050 - Interfaces should be defined in separate files from their usage:

This issue arises when the interfaces are defined in the same files where they are used. They should be separated into different files for better readability and reusability.


```solidity
File: src/challengeV2/EdgeChallengeManager.sol


18      interface IEdgeChallengeManager {
19          /// @notice Initialize the EdgeChallengeManager. EdgeChallengeManagers are upgradeable
20          ///         so use the initializer paradigm
21          /// @param _assertionChain              The assertion chain contract
22          /// @param _challengePeriodBlocks       The amount of cumulative time an edge must spend unrivaled before it can be confirmed
23          ///                                     This should be the censorship period + the cumulative amount of time needed to do any
24          ///                                     offchain calculation. We currently estimate around 10 mins for each layer zero edge and 1
25          ///                                     one minute for each other edge.
26          /// @param _oneStepProofEntry           The one step proof logic
27          /// @param layerZeroBlockEdgeHeight     The end height of layer zero edges of type Block
28          /// @param layerZeroBigStepEdgeHeight   The end height of layer zero edges of type BigStep
29          /// @param layerZeroSmallStepEdgeHeight The end height of layer zero edges of type SmallStep
30          /// @param _stakeToken                  The token that stake will be provided in when creating zero layer block edges
31          /// @param _excessStakeReceiver         The address that excess stake will be sent to when 2nd+ block edge is created
32          /// @param _numBigStepLevel             The number of bigstep levels
33          /// @param _stakeAmounts                The stake amount for each level. (first element is for block level)
34          function initialize(
35              IAssertionChain _assertionChain,
36              uint64 _challengePeriodBlocks,
37              IOneStepProofEntry _oneStepProofEntry,
38              uint256 layerZeroBlockEdgeHeight,
39              uint256 layerZeroBigStepEdgeHeight,
40              uint256 layerZeroSmallStepEdgeHeight,
41              IERC20 _stakeToken,
42              address _excessStakeReceiver,
43              uint8 _numBigStepLevel,
44              uint256[] calldata _stakeAmounts
45          ) external;
46      
47          function challengePeriodBlocks() external view returns (uint64);
48      
49          /// @notice The one step proof resolver used to decide between rival SmallStep edges of length 1
50          function oneStepProofEntry() external view returns (IOneStepProofEntry);
51      
52          /// @notice Performs necessary checks and creates a new layer zero edge
53          /// @param args             Edge creation args
54          function createLayerZeroEdge(CreateEdgeArgs calldata args) external returns (bytes32);
55      
56          /// @notice Bisect an edge. This creates two child edges:
57          ///         lowerChild: has the same start root and height as this edge, but a different end root and height
58          ///         upperChild: has the same end root and height as this edge, but a different start root and height
59          ///         The lower child end root and height are equal to the upper child start root and height. This height
60          ///         is the mandatoryBisectionHeight.
61          ///         The lower child may already exist, however it's not possible for the upper child to exist as that would
62          ///         mean that the edge has already been bisected
63          /// @param edgeId               Edge to bisect
64          /// @param bisectionHistoryRoot The new history root to be used in the lower and upper children
65          /// @param prefixProof          A proof to show that the bisectionHistoryRoot commits to a prefix of the current endHistoryRoot
66          /// @return lowerChildId        The id of the newly created lower child edge
67          /// @return upperChildId        The id of the newly created upper child edge
68          function bisectEdge(bytes32 edgeId, bytes32 bisectionHistoryRoot, bytes calldata prefixProof)
69              external
70              returns (bytes32, bytes32);
71      
72          /// @notice An edge can be confirmed if the total amount of time it and a single chain of its direct ancestors
73          ///         has spent unrivaled is greater than the challenge period.
74          /// @dev    Edges inherit time from their parents, so the sum of unrivaled timers is compared against the threshold.
75          ///         Given that an edge cannot become unrivaled after becoming rivaled, once the threshold is passed
76          ///         it will always remain passed. The direct ancestors of an edge are linked by parent-child links for edges
77          ///         of the same level, and claimId-edgeId links for zero layer edges that claim an edge in the level below.
78          ///         This method also includes the amount of time the assertion being claimed spent without a sibling
79          /// @param edgeId                   The id of the edge to confirm
80          function confirmEdgeByTime(bytes32 edgeId, AssertionStateData calldata claimStateData) external;
81      
82          /// @notice Update multiple edges' timer cache by their children. Equivalent to calling updateTimerCacheByChildren for each edge.
83          /// @param edgeIds The ids of the edges to update
84          function multiUpdateTimeCacheByChildren(bytes32[] calldata edgeIds) external;
85      
86          /// @notice If a confirmed edge exists whose claim id is equal to this edge, then this edge can be confirmed
87          /// @dev    When zero layer edges are created they reference an edge, or assertion, in the level below. If a zero layer
88          ///         edge is confirmed, it becomes possible to also confirm the edge that it claims
89          /// @param edgeId           The id of the edge to confirm
90          /// @notice Update an edge's timer cache by its children.
91          ///         Sets the edge's timer cache to its timeUnrivaled + (minimum timer cache of its children).
92          ///         This function should not be used for edges without children.
93          /// @param edgeId The id of the edge to update
94          function updateTimerCacheByChildren(bytes32 edgeId) external;
95      
96          /// @notice Given a one step fork edge and an edge with matching claim id,
97          ///         set the one step fork edge's timer cache to its timeUnrivaled + claiming edge's timer cache.
98          /// @param edgeId           The id of the edge to update
99          /// @param claimingEdgeId   The id of the edge which has a claimId equal to edgeId
100         function updateTimerCacheByClaim(bytes32 edgeId, bytes32 claimingEdgeId) external;
101     
102         /// @notice Confirm an edge by executing a one step proof
103         /// @dev    One step proofs can only be executed against edges that have length one and of type SmallStep
104         /// @param edgeId                       The id of the edge to confirm
105         /// @param oneStepData                  Input data to the one step proof
106         /// @param prevConfig                     Data about the config set in prev
107         /// @param beforeHistoryInclusionProof  Proof that the state which is the start of the edge is committed to by the startHistoryRoot
108         /// @param afterHistoryInclusionProof   Proof that the state which is the end of the edge is committed to by the endHistoryRoot
109         function confirmEdgeByOneStepProof(
110             bytes32 edgeId,
111             OneStepData calldata oneStepData,
112             ConfigData calldata prevConfig,
113             bytes32[] calldata beforeHistoryInclusionProof,
114             bytes32[] calldata afterHistoryInclusionProof
115         ) external;
116     
117         /// @notice When zero layer block edges are created a stake is also provided
118         ///         The stake on this edge can be refunded if the edge is confirme
119         function refundStake(bytes32 edgeId) external;
120     
121         /// @notice Zero layer edges have to be a fixed height.
122         ///         This function returns the end height for a given edge type
123         function getLayerZeroEndHeight(EdgeType eType) external view returns (uint256);
124     
125         /// @notice Calculate the unique id of an edge
126         /// @param level            The level of the edge
127         /// @param originId         The origin id of the edge
128         /// @param startHeight      The start height of the edge
129         /// @param startHistoryRoot The start history root of the edge
130         /// @param endHeight        The end height of the edge
131         /// @param endHistoryRoot   The end history root of the edge
132         function calculateEdgeId(
133             uint8 level,
134             bytes32 originId,
135             uint256 startHeight,
136             bytes32 startHistoryRoot,
137             uint256 endHeight,
138             bytes32 endHistoryRoot
139         ) external pure returns (bytes32);
140     
141         /// @notice Calculate the mutual id of the edge
142         ///         Edges that are rivals share the same mutual id
143         /// @param level            The level of the edge
144         /// @param originId         The origin id of the edge
145         /// @param startHeight      The start height of the edge
146         /// @param startHistoryRoot The start history root of the edge
147         /// @param endHeight        The end height of the edge
148         function calculateMutualId(
149             uint8 level,
150             bytes32 originId,
151             uint256 startHeight,
152             bytes32 startHistoryRoot,
153             uint256 endHeight
154         ) external pure returns (bytes32);
155     
156         /// @notice Has the edge already been stored in the manager
157         function edgeExists(bytes32 edgeId) external view returns (bool);
158     
159         /// @notice Get full edge data for an edge
160         function getEdge(bytes32 edgeId) external view returns (ChallengeEdge memory);
161     
162         /// @notice The length of the edge, from start height to end height
163         function edgeLength(bytes32 edgeId) external view returns (uint256);
164     
165         /// @notice Does this edge currently have one or more rivals
166         ///         Rival edges share the same mutual id
167         function hasRival(bytes32 edgeId) external view returns (bool);
168     
169         /// @notice The confirmed rival of this mutual id
170         ///         Returns 0 if one does not exist
171         function confirmedRival(bytes32 mutualId) external view returns (bytes32);
172     
173         /// @notice Does the edge have at least one rival, and it has length one
174         function hasLengthOneRival(bytes32 edgeId) external view returns (bool);
175     
176         /// @notice The amount of time this edge has spent without rivals
177         ///         This value is increasing whilst an edge is unrivaled, once a rival is created
178         ///         it is fixed. If an edge has rivals from the moment it is created then it will have
179         ///         a zero time unrivaled
180         function timeUnrivaled(bytes32 edgeId) external view returns (uint256);
181     
182         /// @notice Get the id of the prev assertion that this edge is originates from
183         /// @dev    Uses the parent chain to traverse upwards SmallStep->BigStep->Block->Assertion
184         ///         until it gets to the origin assertion
185         function getPrevAssertionHash(bytes32 edgeId) external view returns (bytes32);
186     
187         /// @notice Fetch the raw first rival record for the given mutual id
188         /// @dev    Returns 0 if there is no edge with the given mutual id
189         ///         Returns a magic value if there is one edge but it is unrivaled
190         ///         Returns the id of the second edge created with the mutual id, if > 1 exists
191         function firstRival(bytes32 mutualId) external view returns (bytes32);
192     
193         /// @notice True if an account has made a layer zero edge with the given mutual id.
194         ///         This is only tracked when the validator whitelist is enabled
195         function hasMadeLayerZeroRival(address account, bytes32 mutualId) external view returns (bool);
196     }


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/challengeV2/EdgeChallengeManager.sol#L0:0

```solidity
File: src/rollup/BOLDUpgradeAction.sol


49      interface IOldRollup {
50          struct Assertion {
51              ExecutionState beforeState;
52              ExecutionState afterState;
53              uint64 numBlocks;
54          }
55      
56          event NodeCreated(
57              uint64 indexed nodeNum,
58              bytes32 indexed parentNodeHash,
59              bytes32 indexed nodeHash,
60              bytes32 executionHash,
61              Assertion assertion,
62              bytes32 afterInboxBatchAcc,
63              bytes32 wasmModuleRoot,
64              uint256 inboxMaxCount
65          );
66      
67          function wasmModuleRoot() external view returns (bytes32);
68          function latestConfirmed() external view returns (uint64);
69          function getNode(uint64 nodeNum) external view returns (Node memory);
70          function getStakerAddress(uint64 stakerNum) external view returns (address);
71          function stakerCount() external view returns (uint64);
72          function getStaker(address staker) external view returns (OldStaker memory);
73          function isValidator(address validator) external view returns (bool);
74          function validatorWalletCreator() external view returns (address);
75      }
77      interface IOldRollupAdmin {
78          function forceRefundStaker(address[] memory stacker) external;
79          function pause() external;
80          function resume() external;
81      }
83      interface ISeqInboxPostUpgradeInit {
84          function postUpgradeInit(BufferConfig memory bufferConfig_) external;
85      }


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/rollup/BOLDUpgradeAction.sol#L0:0

## NC051 - Use a more recent version of solidity:

Use a solidity version of at least 0.8.12 to get string.concat() to be used instead of abi.encodePacked(<str>,<str>)


<details>
<summary>Click to show 4 findings</summary>

```solidity
File: src/assertionStakingPool/StakingPoolCreatorUtils.sol


6       pragma solidity ^0.8.0;


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/assertionStakingPool/StakingPoolCreatorUtils.sol#L0:0

```solidity
File: src/bridge/SequencerInbox.sol


5       pragma solidity ^0.8.0;


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/bridge/SequencerInbox.sol#L0:0

```solidity
File: src/rollup/BOLDUpgradeAction.sol


5       pragma solidity ^0.8.0;


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/rollup/BOLDUpgradeAction.sol#L0:0

```solidity
File: src/rollup/RollupLib.sol


5       pragma solidity ^0.8.0;


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/rollup/RollupLib.sol#L0:0

</details>

## NC052 - Custom error has no error details:

Consider adding parameters to the error to indicate which user or values caused the failure.


<details>
<summary>Click to show 4 findings</summary>

```solidity
File: src/assertionStakingPool/StakingPoolCreatorUtils.sol


12          error PoolDoesntExist();


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/assertionStakingPool/StakingPoolCreatorUtils.sol#L0:0

```solidity
File: src/assertionStakingPool/interfaces/IAbsBoldStakingPool.sol


14          error ZeroAmount();


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/assertionStakingPool/interfaces/IAbsBoldStakingPool.sol#L0:0

```solidity
File: src/challengeV2/libraries/ChallengeErrors.sol


14      error AssertionHashEmpty();
18      error AssertionNotPending();
20      error AssertionNoSibling();
22      error EmptyEdgeSpecificProof();
24      error EmptyStartMachineStatus();
26      error EmptyEndMachineStatus();
28      error ClaimEdgeNotPending();
38      error EmptyPrefixProof();
44      error EmptyFirstRival();
68      error EmptyOriginId();
72      error EmptyStartRoot();
74      error EmptyEndRoot();
76      error EmptyStaker();
78      error EmptyClaimId();
86      error EmptyAssertionChain();
88      error EmptyOneStepProofEntry();
90      error EmptyChallengePeriod();
92      error EmptyStakeReceiver();
98      error ZeroBigStepLevels();


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/challengeV2/libraries/ChallengeErrors.sol#L0:0

```solidity
File: src/libraries/Error.sol


8       error AlreadyInit();
11      error HadZeroInit();
14      error BadPostUpgradeInit();
27      error NotOrigin();
76      error CallNotAllowed();
81      error AlreadyPaused();
84      error AlreadyUnpaused();
87      error Paused();
114     error L1Forked();
117     error NotForked();
120     error GasLimitTooLarge();
142     error BridgeCallFailed();
147     error DelayedBackwards();
150     error DelayedTooFar();
153     error ForceIncludeBlockTooSoon();
156     error ForceIncludeTimeTooSoon();
159     error IncorrectMessagePreimage();
162     error NotBatchPoster();
180     error DataBlobsNotSupported();
183     error DelayProofRequired();
186     error InvalidDelayedAccPreimage();
189     error NotDelayBufferable();
195     error MissingDataHashes();
198     error RollupNotChanged();
204     error NativeTokenMismatch();
207     error Deprecated();
210     error BadMaxTimeVariation();
213     error BadBufferConfig();
216     error ExtraGasNotUint64();
219     error KeysetTooLarge();


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/libraries/Error.sol#L0:0

</details>

## NC053 - Overridden function has no body:

Consider adding a NatSpec comment describing why the function doesn't need a body and or the purpose it serves.


```solidity
File: src/rollup/RollupAdminLogic.sol


171         function _authorizeSecondaryUpgrade(address newImplementation) internal override {}
166         function _authorizeUpgrade(address newImplementation) internal override {}


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/rollup/RollupAdminLogic.sol#L0:0

## NC054 - Consider moving `msg.sender` checks to a common authorization `modifier`:

  


```solidity
File: src/rollup/RollupUserLogic.sol


182             require(amountStaked(msg.sender) >= assertion.beforeStateData.configData.requiredStake, "INSUFFICIENT_STAKE");
175             require(isStaked(msg.sender), "NOT_STAKED");
139             require(!isStaked(msg.sender), "ALREADY_STAKED");
258             require(msg.sender == anyTrustFastConfirmer, "NOT_FAST_CONFIRMER");


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/rollup/RollupUserLogic.sol#L0:0

## NC055 - Unused `error` definition:

Note that there may be cases where an error superficially appears to be used, but this is only because there are multiple definitions of the error in different files. In such cases, the error definition should be moved into a separate file. The instances below are the unused definitions.


<details>
<summary>Click to show 28 findings</summary>

```solidity
File: src/challengeV2/libraries/ChallengeErrors.sol


error EdgeTypeNotBlock(uint8 level);

error EdgeClaimMismatch(bytes32 edgeId, bytes32 claimingEdgeId);

error EdgeNotAncestor(
    bytes32 edgeId, bytes32 lowerChildId, bytes32 upperChildId, bytes32 ancestorEdgeId, bytes32 claimId
);

```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/challengeV2/libraries/ChallengeErrors.sol#L60:62

```solidity
File: src/libraries/Error.sol


error NotRollup(address sender, address rollup);

error NotContract(address addr);

error MerkleProofTooLong(uint256 actualLength, uint256 maxProofLength);

error NotRollupOrOwner(address sender, address rollup, address owner);

error NotDelayedInbox(address sender);

error NotSequencerInbox(address sender);

error NotOutbox(address sender);

error InvalidOutboxSet(address outbox);

error InvalidTokenSet(address token);

error CallTargetNotAllowed(address target);

error CallNotAllowed();

error AlreadyPaused();

error AlreadyUnpaused();

error InsufficientValue(uint256 expected, uint256 actual);

error InsufficientSubmissionCost(uint256 expected, uint256 actual);

error NotAllowedOrigin(address origin);

error RetryableData(
    address from,
    address to,
    uint256 l2CallValue,
    uint256 deposit,
    uint256 maxSubmissionCost,
    address excessFeeRefundAddress,
    address callValueRefundAddress,
    uint256 gasLimit,
    uint256 maxFeePerGas,
    bytes data
);

error L1Forked();

error GasLimitTooLarge();

error ProofTooLong(uint256 proofLength);

error PathNotMinimal(uint256 index, uint256 maxIndex);

error UnknownRoot(bytes32 root);

error AlreadySpent(uint256 index);

error BridgeCallFailed();

error BadSequencerMessageNumber(uint256 stored, uint256 received);

```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/libraries/Error.sol#L168:168

</details>

## NC056 - Events are missing sender information:

When an action is triggered based on a user's action, not being able to filter based on who triggered the action makes event processing a lot more cumbersome. Including the msg.sender the events of these types of action will make events much more useful to end users. Include `msg.sender` in the event output.


<details>
<summary>Click to show 6 findings</summary>

```solidity
File: src/assertionStakingPool/AssertionStakingPoolCreator.sol


20              emit NewAssertionPoolCreated(_rollup, _assertionHash, address(assertionPool));


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/assertionStakingPool/AssertionStakingPoolCreator.sol#L0:0

```solidity
File: src/assertionStakingPool/EdgeStakingPoolCreator.sol


20              emit NewEdgeStakingPoolCreated(challengeManager, edgeId);


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/assertionStakingPool/EdgeStakingPoolCreator.sol#L0:0

```solidity
File: src/bridge/SequencerInbox.sol


344             emit SequencerBatchDelivered(
345                 seqMessageIndex,
346                 beforeAcc,
347                 afterAcc,
348                 delayedAcc,
349                 totalDelayedMessagesRead,
350                 timeBounds,
351                 IBridge.BatchDataLocation.NoData
352             );
890             emit OwnerFunctionCalled(0);
899             emit OwnerFunctionCalled(1);
917             emit SetValidKeyset(ksHash, keysetBytes);
918             emit OwnerFunctionCalled(2);
928             emit InvalidateKeyset(ksHash);
929             emit OwnerFunctionCalled(3);
938             emit OwnerFunctionCalled(4); // Owner in this context can also be batch poster manager
944             emit OwnerFunctionCalled(5);
949             emit OwnerFunctionCalled(6);


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/bridge/SequencerInbox.sol#L0:0

```solidity
File: src/challengeV2/EdgeChallengeManager.sol


437             emit EdgeAdded(
438                 edgeAdded.edgeId,
439                 edgeAdded.mutualId,
440                 edgeAdded.originId,
441                 edgeAdded.claimId,
442                 edgeAdded.length,
443                 edgeAdded.level,
444                 edgeAdded.hasRival,
445                 edgeAdded.isLayerZero
446             );
462                 emit EdgeAdded(
463                     lowerChildAdded.edgeId,
464                     lowerChildAdded.mutualId,
465                     lowerChildAdded.originId,
466                     lowerChildAdded.claimId,
467                     lowerChildAdded.length,
468                     lowerChildAdded.level,
469                     lowerChildAdded.hasRival,
470                     lowerChildAdded.isLayerZero
471                 );
474             emit EdgeAdded(
475                 upperChildAdded.edgeId,
476                 upperChildAdded.mutualId,
477                 upperChildAdded.originId,
478                 upperChildAdded.claimId,
479                 upperChildAdded.length,
480                 upperChildAdded.level,
481                 upperChildAdded.hasRival,
482                 upperChildAdded.isLayerZero
483             );
485             emit EdgeBisected(edgeId, lowerChildId, upperChildAdded.edgeId, lowerChildAlreadyExists);


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/challengeV2/EdgeChallengeManager.sol#L0:0

```solidity
File: src/rollup/BOLDUpgradeAction.sol


540             emit RollupMigrated(expectedRollupAddress, address(challengeManager));


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/rollup/BOLDUpgradeAction.sol#L0:0

```solidity
File: src/rollup/RollupAdminLogic.sol


90              emit AssertionCreated(
91                  genesisHash,
92                  parentAssertionHash,
93                  assertionInputs,
94                  inboxAcc,
95                  currentInboxCount,
96                  wasmModuleRoot,
97                  baseStake,
98                  address(challengeManager),
99                  confirmPeriodBlocks
100             );
105             emit RollupInitialized(config.wasmModuleRoot, config.chainId);
120             emit OwnerFunctionCalled(0);
130             emit OwnerFunctionCalled(1);
140             emit OwnerFunctionCalled(2);
152             emit OwnerFunctionCalled(3);
160             emit OwnerFunctionCalled(4);
187             emit OwnerFunctionCalled(6);
197             emit OwnerFunctionCalled(7);
206             emit OwnerFunctionCalled(8);
216             emit OwnerFunctionCalled(9);
225             emit OwnerFunctionCalled(12);
234             emit OwnerFunctionCalled(22);
255             emit OwnerFunctionCalled(23);
266             emit OwnerFunctionCalled(24);
274             emit OwnerFunctionCalled(25);
283             emit OwnerFunctionCalled(26);
292             emit OwnerFunctionCalled(27);
301             emit OwnerFunctionCalled(28);
310             emit OwnerFunctionCalled(30);
319             emit OwnerFunctionCalled(31);
328             emit OwnerFunctionCalled(32);


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/rollup/RollupAdminLogic.sol#L0:0

</details>

## NC057 - SPDX-License-Identifier should be on the first line:

The SPDX-License-Identifier is not on the first line of the file, it should always be on the first line.


<details>
<summary>Click to show 39 findings</summary>

```solidity
File: src/assertionStakingPool/AbsBoldStakingPool.sol


1       // Copyright 2021-2022, Offchain Labs, Inc.


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/assertionStakingPool/AbsBoldStakingPool.sol#L0:0

```solidity
File: src/assertionStakingPool/AssertionStakingPool.sol


1       // Copyright 2021-2022, Offchain Labs, Inc.


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/assertionStakingPool/AssertionStakingPool.sol#L0:0

```solidity
File: src/assertionStakingPool/AssertionStakingPoolCreator.sol


1       // Copyright 2021-2022, Offchain Labs, Inc.


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/assertionStakingPool/AssertionStakingPoolCreator.sol#L0:0

```solidity
File: src/assertionStakingPool/EdgeStakingPool.sol


1       // Copyright 2021-2022, Offchain Labs, Inc.


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/assertionStakingPool/EdgeStakingPool.sol#L0:0

```solidity
File: src/assertionStakingPool/EdgeStakingPoolCreator.sol


1       // Copyright 2021-2022, Offchain Labs, Inc.


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/assertionStakingPool/EdgeStakingPoolCreator.sol#L0:0

```solidity
File: src/assertionStakingPool/StakingPoolCreatorUtils.sol


1       // Copyright 2021-2022, Offchain Labs, Inc.


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/assertionStakingPool/StakingPoolCreatorUtils.sol#L0:0

```solidity
File: src/assertionStakingPool/interfaces/IAbsBoldStakingPool.sol


1       // Copyright 2021-2022, Offchain Labs, Inc.


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/assertionStakingPool/interfaces/IAbsBoldStakingPool.sol#L0:0

```solidity
File: src/assertionStakingPool/interfaces/IAssertionStakingPool.sol


1       // Copyright 2021-2022, Offchain Labs, Inc.


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/assertionStakingPool/interfaces/IAssertionStakingPool.sol#L0:0

```solidity
File: src/assertionStakingPool/interfaces/IAssertionStakingPoolCreator.sol


1       // Copyright 2021-2022, Offchain Labs, Inc.


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/assertionStakingPool/interfaces/IAssertionStakingPoolCreator.sol#L0:0

```solidity
File: src/assertionStakingPool/interfaces/IEdgeStakingPool.sol


1       // Copyright 2021-2022, Offchain Labs, Inc.


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/assertionStakingPool/interfaces/IEdgeStakingPool.sol#L0:0

```solidity
File: src/assertionStakingPool/interfaces/IEdgeStakingPoolCreator.sol


1       // Copyright 2021-2022, Offchain Labs, Inc.


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/assertionStakingPool/interfaces/IEdgeStakingPoolCreator.sol#L0:0

```solidity
File: src/bridge/DelayBuffer.sol


1       // Copyright 2021-2022, Offchain Labs, Inc.


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/bridge/DelayBuffer.sol#L0:0

```solidity
File: src/bridge/DelayBufferTypes.sol


1       // Copyright 2021-2022, Offchain Labs, Inc.


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/bridge/DelayBufferTypes.sol#L0:0

```solidity
File: src/bridge/ISequencerInbox.sol


1       // Copyright 2021-2022, Offchain Labs, Inc.


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/bridge/ISequencerInbox.sol#L0:0

```solidity
File: src/bridge/SequencerInbox.sol


1       // Copyright 2021-2022, Offchain Labs, Inc.


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/bridge/SequencerInbox.sol#L0:0

```solidity
File: src/challengeV2/EdgeChallengeManager.sol


1       // Copyright 2023, Offchain Labs, Inc.


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/challengeV2/EdgeChallengeManager.sol#L0:0

```solidity
File: src/challengeV2/IAssertionChain.sol


1       // Copyright 2023, Offchain Labs, Inc.


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/challengeV2/IAssertionChain.sol#L0:0

```solidity
File: src/challengeV2/libraries/ArrayUtilsLib.sol


1       // Copyright 2023, Offchain Labs, Inc.


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/challengeV2/libraries/ArrayUtilsLib.sol#L0:0

```solidity
File: src/challengeV2/libraries/ChallengeEdgeLib.sol


1       // Copyright 2023, Offchain Labs, Inc.


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/challengeV2/libraries/ChallengeEdgeLib.sol#L0:0

```solidity
File: src/challengeV2/libraries/ChallengeErrors.sol


1       // Copyright 2023, Offchain Labs, Inc.


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/challengeV2/libraries/ChallengeErrors.sol#L0:0

```solidity
File: src/challengeV2/libraries/EdgeChallengeManagerLib.sol


1       // Copyright 2023, Offchain Labs, Inc.


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/challengeV2/libraries/EdgeChallengeManagerLib.sol#L0:0

```solidity
File: src/challengeV2/libraries/Enums.sol


1       // Copyright 2023, Offchain Labs, Inc.


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/challengeV2/libraries/Enums.sol#L0:0

```solidity
File: src/challengeV2/libraries/MerkleTreeLib.sol


1       // Copyright 2023, Offchain Labs, Inc.


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/challengeV2/libraries/MerkleTreeLib.sol#L0:0

```solidity
File: src/challengeV2/libraries/UintUtilsLib.sol


1       // Copyright 2023, Offchain Labs, Inc.


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/challengeV2/libraries/UintUtilsLib.sol#L0:0

```solidity
File: src/libraries/Error.sol


1       // Copyright 2021-2022, Offchain Labs, Inc.


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/libraries/Error.sol#L0:0

```solidity
File: src/rollup/Assertion.sol


1       // Copyright 2021-2022, Offchain Labs, Inc.


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/rollup/Assertion.sol#L0:0

```solidity
File: src/rollup/AssertionState.sol


1       // Copyright 2021-2022, Offchain Labs, Inc.


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/rollup/AssertionState.sol#L0:0

```solidity
File: src/rollup/BOLDUpgradeAction.sol


1       // Copyright 2021-2022, Offchain Labs, Inc.


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/rollup/BOLDUpgradeAction.sol#L0:0

```solidity
File: src/rollup/BridgeCreator.sol


1       // Copyright 2021-2022, Offchain Labs, Inc.


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/rollup/BridgeCreator.sol#L0:0

```solidity
File: src/rollup/Config.sol


1       // Copyright 2021-2022, Offchain Labs, Inc.


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/rollup/Config.sol#L0:0

```solidity
File: src/rollup/IRollupAdmin.sol


1       // Copyright 2021-2022, Offchain Labs, Inc.


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/rollup/IRollupAdmin.sol#L0:0

```solidity
File: src/rollup/IRollupCore.sol


1       // Copyright 2021-2022, Offchain Labs, Inc.


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/rollup/IRollupCore.sol#L0:0

```solidity
File: src/rollup/IRollupLogic.sol


1       // Copyright 2021-2022, Offchain Labs, Inc.


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/rollup/IRollupLogic.sol#L0:0

```solidity
File: src/rollup/RollupAdminLogic.sol


1       // Copyright 2021-2022, Offchain Labs, Inc.


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/rollup/RollupAdminLogic.sol#L0:0

```solidity
File: src/rollup/RollupCore.sol


1       // Copyright 2021-2022, Offchain Labs, Inc.


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/rollup/RollupCore.sol#L0:0

```solidity
File: src/rollup/RollupCreator.sol


1       // Copyright 2021-2022, Offchain Labs, Inc.


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/rollup/RollupCreator.sol#L0:0

```solidity
File: src/rollup/RollupLib.sol


1       // Copyright 2021-2022, Offchain Labs, Inc.


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/rollup/RollupLib.sol#L0:0

```solidity
File: src/rollup/RollupProxy.sol


1       // Copyright 2021-2022, Offchain Labs, Inc.


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/rollup/RollupProxy.sol#L0:0

```solidity
File: src/rollup/RollupUserLogic.sol


1       // Copyright 2021-2022, Offchain Labs, Inc.


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/rollup/RollupUserLogic.sol#L0:0

</details>

## NC058 - Enum values should be used in place of constant array indexes:

Create a commented enum value to use in place of constant array indexes, this makes the code far easier to understand.


```solidity
File: src/bridge/SequencerInbox.sol


299                 l1BlockAndTime[0],
300                 l1BlockAndTime[1],
310                 buffer.update(l1BlockAndTime[0]);
314             if (l1BlockAndTime[0] + delayBlocks_ >= block.number) revert ForceIncludeBlockTooSoon();
705                 if (!isValidCallDataFlag(data[0])) revert InvalidHeaderFlag(data[0]);
705                 if (!isValidCallDataFlag(data[0])) revert InvalidHeaderFlag(data[0]);
711                 if (data[0] & DAS_MESSAGE_HEADER_FLAG != 0 && data.length >= 33) {


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/bridge/SequencerInbox.sol#L0:0

```solidity
File: src/rollup/BOLDUpgradeAction.sol


355                     stakersToRefund[0] = stakerAddr;


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/rollup/BOLDUpgradeAction.sol#L0:0

```solidity
File: src/rollup/RollupCreator.sol


281             executors[0] = rollupOwner;


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/rollup/RollupCreator.sol#L0:0

## NC059 - Zero as a function argument should have a descriptive meaning:

Consider using descriptive constants or an enum instead of passing zero directly on function calls, as that might be error-prone, to fully describe the caller's intention.


<details>
<summary>Click to show 10 findings</summary>

```solidity
File: src/assertionStakingPool/StakingPoolCreatorUtils.sol


15              address pool = Create2.computeAddress(0, bytecodeHash, address(this));


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/assertionStakingPool/StakingPoolCreatorUtils.sol#L0:0

```solidity
File: src/bridge/SequencerInbox.sol


337             ) = addSequencerL2BatchImpl(
338                     dataHash,
339                     __totalDelayedMessagesRead,
340                     0,
341                     prevSeqMsgCount,
342                     newSeqMsgCount
343                 );
475             ) = addSequencerL2BatchImpl(
476                     dataHash,
477                     afterDelayedMessagesRead,
478                     0,
479                     prevMessageCount,
480                     newMessageCount
481                 );
484             if (seqMessageIndex != sequenceNumber && sequenceNumber != ~uint256(0)) {
538             if (seqMessageIndex != sequenceNumber && sequenceNumber != ~uint256(0)) {
820                 submitBatchSpendingReport(dataHash, seqMessageIndex, block.basefee, 0);
890             emit OwnerFunctionCalled(0);
899             emit OwnerFunctionCalled(1);
918             emit OwnerFunctionCalled(2);
929             emit OwnerFunctionCalled(3);
938             emit OwnerFunctionCalled(4); // Owner in this context can also be batch poster manager
944             emit OwnerFunctionCalled(5);
949             emit OwnerFunctionCalled(6);


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/bridge/SequencerInbox.sol#L0:0

```solidity
File: src/challengeV2/libraries/ChallengeEdgeLib.sol


112             return ChallengeEdge({
113                 originId: originId,
114                 startHeight: startHeight,
115                 startHistoryRoot: startHistoryRoot,
116                 endHeight: endHeight,
117                 endHistoryRoot: endHistoryRoot,
118                 lowerChildId: 0,
119                 upperChildId: 0,
120                 createdAtBlock: uint64(block.number),
121                 claimId: claimId,
122                 staker: staker,
123                 status: EdgeStatus.Pending,
124                 level: level,
125                 refunded: false,
126                 confirmedAtBlock: 0,
127                 totalTimeUnrivaledCache: 0
128             });
143             return ChallengeEdge({
144                 originId: originId,
145                 startHeight: startHeight,
146                 startHistoryRoot: startHistoryRoot,
147                 endHeight: endHeight,
148                 endHistoryRoot: endHistoryRoot,
149                 lowerChildId: 0,
150                 upperChildId: 0,
151                 createdAtBlock: uint64(block.number),
152                 claimId: 0,
153                 staker: address(0),
154                 status: EdgeStatus.Pending,
155                 level: level,
156                 refunded: false,
157                 confirmedAtBlock: 0,
158                 totalTimeUnrivaledCache: 0
159             });


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/challengeV2/libraries/ChallengeEdgeLib.sol#L0:0

```solidity
File: src/challengeV2/libraries/EdgeChallengeManagerLib.sol


351             bytes32 startHistoryRoot = MerkleTreeLib.root(MerkleTreeLib.appendLeaf(new bytes32[](0), proofData.startState));
383             MerkleTreeLib.verifyPrefixProof(
384                 startHistoryRoot, 1, args.endHistoryRoot, args.endHeight + 1, preExpansion, preProof
385             );
396             return ChallengeEdgeLib.newLayerZeroEdge(
397                 originId, startHistoryRoot, 0, args.endHistoryRoot, args.endHeight, args.claimId, msg.sender, args.level
398             );
490             if (store.edges[edgeId].lowerChildId != bytes32(0)) {
665             if (confirmedRivalId != bytes32(0)) {


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/challengeV2/libraries/EdgeChallengeManagerLib.sol#L0:0

```solidity
File: src/challengeV2/libraries/MerkleTreeLib.sol


126                             accum = keccak256(abi.encodePacked(accum, bytes32(0)));
135                     accum = keccak256(abi.encodePacked(accum, bytes32(0)));
241             return appendCompleteSubTree(me, 0, keccak256(abi.encodePacked(leaf)));
329             bytes32[] memory exp = ArrayUtilsLib.slice(preExpansion, 0, preExpansion.length);


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/challengeV2/libraries/MerkleTreeLib.sol#L0:0

```solidity
File: src/rollup/BOLDUpgradeAction.sol


354                     address[] memory stakersToRefund = new address[](1);


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/rollup/BOLDUpgradeAction.sol#L0:0

```solidity
File: src/rollup/RollupAdminLogic.sol


41                  connectedContracts.sequencerInbox.addSequencerL2Batch(0, "", 1, IGasRefunder(address(0)), 0, 1);
63              bytes32 parentAssertionHash = bytes32(0);
64              bytes32 inboxAcc = bytes32(0);
120             emit OwnerFunctionCalled(0);
130             emit OwnerFunctionCalled(1);
140             emit OwnerFunctionCalled(2);
152             emit OwnerFunctionCalled(3);
160             emit OwnerFunctionCalled(4);
187             emit OwnerFunctionCalled(6);
197             emit OwnerFunctionCalled(7);
206             emit OwnerFunctionCalled(8);
216             emit OwnerFunctionCalled(9);
225             emit OwnerFunctionCalled(12);
232                 reduceStakeTo(staker[i], 0);
234             emit OwnerFunctionCalled(22);
255             emit OwnerFunctionCalled(23);
266             emit OwnerFunctionCalled(24);
274             emit OwnerFunctionCalled(25);
283             emit OwnerFunctionCalled(26);
292             emit OwnerFunctionCalled(27);
301             emit OwnerFunctionCalled(28);
310             emit OwnerFunctionCalled(30);
319             emit OwnerFunctionCalled(31);
328             emit OwnerFunctionCalled(32);


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/rollup/RollupAdminLogic.sol#L0:0

```solidity
File: src/rollup/RollupCore.sol


127             require(assertionHash != bytes32(0), "ASSERTION_ID_CANNOT_BE_ZERO");
278             emit UserStakeUpdated(stakerAddress, withdrawalAddress, 0, depositAmount);
323             emit UserStakeUpdated(stakerAddress, withdrawalAddress, initialStaked, 0);
335             emit UserWithdrawableFundsUpdated(account, amount, 0);
478                 newAssertionHash == expectedAssertionHash || expectedAssertionHash == bytes32(0),
522             AssertionState memory emptyAssertionState = AssertionState(emptyGlobalState, MachineStatus.FINISHED, bytes32(0));
523             bytes32 parentAssertionHash = bytes32(0);
524             bytes32 inboxAcc = bytes32(0);


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/rollup/RollupCore.sol#L0:0

```solidity
File: src/rollup/RollupCreator.sol


280             address[] memory executors = new address[](1);


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/rollup/RollupCreator.sol#L0:0

```solidity
File: src/rollup/RollupUserLogic.sol


170                 expectedAssertionHash == bytes32(0)
278             require(expectedAssertionHash != bytes32(0), "EXPECTED_ASSERTION_HASH");


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/rollup/RollupUserLogic.sol#L0:0

</details>

## NC060 - Function names should differ to make the code more readable:

In Solidity, while function overriding allows for functions with the same name to coexist, it is advisable to avoid this practice to enhance code readability and maintainability. Having multiple functions with the same name, even with different parameters or in inherited contracts, can cause confusion and increase the likelihood of errors during development, testing, and debugging. Using distinct and descriptive function names not only clarifies the purpose and behavior of each function, but also helps prevent unintended function calls or incorrect overriding. By adopting a clear and consistent naming convention, developers can create more comprehensible and maintainable smart contracts.


<details>
<summary>Click to show 261 findings</summary>

```solidity
File: src/assertionStakingPool/AbsBoldStakingPool.sol


    function depositIntoPool(uint256 amount) external {
        if (amount == 0) {
            revert ZeroAmount();
        }

        depositBalance[msg.sender] += amount;
        IERC20(stakeToken).safeTransferFrom(msg.sender, address(this), amount);

        emit StakeDeposited(msg.sender, amount);
    }

    function withdrawFromPool(uint256 amount) public {
        if (amount == 0) {
            revert ZeroAmount();
        }
        uint256 balance = depositBalance[msg.sender];
        if (amount > balance) {
            revert AmountExceedsBalance(msg.sender, amount, balance);
        }

        depositBalance[msg.sender] = balance - amount;
        IERC20(stakeToken).safeTransfer(msg.sender, amount);
        
        emit StakeWithdrawn(msg.sender, amount);
    }

    function withdrawFromPool() external {
        withdrawFromPool(depositBalance[msg.sender]);
    }

```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/assertionStakingPool/AbsBoldStakingPool.sol#L57:59

```solidity
File: src/assertionStakingPool/interfaces/IAbsBoldStakingPool.sol


    function depositIntoPool(uint256 amount) external;

    function withdrawFromPool(uint256 amount) external;

    function withdrawFromPool() external;

    function stakeToken() external view returns (address);

```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/assertionStakingPool/interfaces/IAbsBoldStakingPool.sol#L30:30

```solidity
File: src/assertionStakingPool/AssertionStakingPool.sol


    function createAssertion(AssertionInputs calldata assertionInputs) external {
        uint256 requiredStake = assertionInputs.beforeStateData.configData.requiredStake;
        // approve spending from rollup for newStakeOnNewAssertion call
        IERC20(stakeToken).safeIncreaseAllowance(rollup, requiredStake);
        // reverts if pool doesn't have enough stake and if assertion has already been asserted
        IRollupUser(rollup).newStakeOnNewAssertion(requiredStake, assertionInputs, assertionHash, address(this));
    }

    function makeStakeWithdrawable() public {
        // this checks for active staker
        IRollupUser(rollup).returnOldDeposit();
    }

    function withdrawStakeBackIntoPool() public {
        IRollupUser(rollup).withdrawStakerFunds();
    }

    function makeStakeWithdrawableAndWithdrawBackIntoPool() external {
        makeStakeWithdrawable();
        withdrawStakeBackIntoPool();
    }

```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/assertionStakingPool/AssertionStakingPool.sol#L60:63

```solidity
File: src/assertionStakingPool/interfaces/IAssertionStakingPool.sol


    function createAssertion(AssertionInputs calldata assertionInputs) external;

    function makeStakeWithdrawable() external;

    function withdrawStakeBackIntoPool() external;

    function makeStakeWithdrawableAndWithdrawBackIntoPool() external;

    function rollup() external view returns (address);

    function assertionHash() external view returns (bytes32);

```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/assertionStakingPool/interfaces/IAssertionStakingPool.sol#L30:30

```solidity
File: src/rollup/Assertion.sol


    function createAssertion(
        bool _isFirstChild,
        bytes32 _configHash
    ) internal view returns (AssertionNode memory) {
        AssertionNode memory assertion;
        assertion.createdAtBlock = uint64(block.number);
        assertion.isFirstChild = _isFirstChild;
        assertion.configHash = _configHash;
        assertion.status = AssertionStatus.Pending;
        return assertion;
    }

```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/rollup/Assertion.sol#L70:80

```solidity
File: src/assertionStakingPool/AssertionStakingPoolCreator.sol


    function createPool(
        address _rollup,
        bytes32 _assertionHash
    ) external returns (IAssertionStakingPool) {
        AssertionStakingPool assertionPool = new AssertionStakingPool{salt: 0}(_rollup, _assertionHash);
        emit NewAssertionPoolCreated(_rollup, _assertionHash, address(assertionPool));
        return assertionPool;
    }

    function getPool(
        address _rollup,
        bytes32 _assertionHash
    ) public view returns (IAssertionStakingPool) {
        return IAssertionStakingPool(
            StakingPoolCreatorUtils.getPool(
                type(AssertionStakingPool).creationCode, 
                abi.encode(_rollup, _assertionHash)
            )
        );
    }

```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/assertionStakingPool/AssertionStakingPoolCreator.sol#L25:35

```solidity
File: src/assertionStakingPool/EdgeStakingPoolCreator.sol


    function createPool(
        address challengeManager,
        bytes32 edgeId
    ) external returns (IEdgeStakingPool) {
        EdgeStakingPool pool = new EdgeStakingPool{salt: 0}(challengeManager, edgeId);
        emit NewEdgeStakingPoolCreated(challengeManager, edgeId);
        return pool;
    }

    function getPool(
        address challengeManager,
        bytes32 edgeId
    ) public view returns (IEdgeStakingPool) {
        return IEdgeStakingPool(
            StakingPoolCreatorUtils.getPool(
                type(EdgeStakingPool).creationCode,
                abi.encode(challengeManager, edgeId)
            )
        );
    }

```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/assertionStakingPool/EdgeStakingPoolCreator.sol#L25:35

```solidity
File: src/assertionStakingPool/interfaces/IAssertionStakingPoolCreator.sol


    function createPool(
        address _rollup,
        bytes32 _assertionHash
    ) external returns (IAssertionStakingPool);

    function getPool(
        address _rollup,
        bytes32 _assertionHash
    ) external view returns (IAssertionStakingPool);

```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/assertionStakingPool/interfaces/IAssertionStakingPoolCreator.sol#L29:32

```solidity
File: src/assertionStakingPool/interfaces/IEdgeStakingPoolCreator.sol


    function createPool(
        address challengeManager,
        bytes32 edgeId
    ) external returns (IEdgeStakingPool);

    function getPool(
        address challengeManager,
        bytes32 edgeId
    ) external view returns (IEdgeStakingPool);

```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/assertionStakingPool/interfaces/IEdgeStakingPoolCreator.sol#L24:27

```solidity
File: src/assertionStakingPool/StakingPoolCreatorUtils.sol


    function getPool(bytes memory creationCode, bytes memory args) internal view returns (address) {
        bytes32 bytecodeHash = keccak256(abi.encodePacked(creationCode, args));
        address pool = Create2.computeAddress(0, bytecodeHash, address(this));
        if (Address.isContract(pool)) {
            return pool;
        } else {
            revert PoolDoesntExist();
        }
    }

```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/assertionStakingPool/StakingPoolCreatorUtils.sol#L13:21

```solidity
File: src/assertionStakingPool/EdgeStakingPool.sol


    function createEdge(CreateEdgeArgs calldata args) external {
        uint256 requiredStake = EdgeChallengeManager(challengeManager).stakeAmounts(args.level);
        IERC20(stakeToken).safeIncreaseAllowance(address(challengeManager), requiredStake);
        bytes32 newEdgeId = EdgeChallengeManager(challengeManager).createLayerZeroEdge(args);
        if (newEdgeId != edgeId) {
            revert IncorrectEdgeId(newEdgeId, edgeId);
        }
    }

```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/assertionStakingPool/EdgeStakingPool.sol#L44:51

```solidity
File: src/assertionStakingPool/interfaces/IEdgeStakingPool.sol


    function createEdge(CreateEdgeArgs calldata args) external;

    function challengeManager() external view returns (address);

```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/assertionStakingPool/interfaces/IEdgeStakingPool.sol#L18:18

```solidity
File: src/rollup/IRollupCore.sol


    function stakeToken() external view returns (address);

    function challengeManager() external view returns (IEdgeChallengeManager);

    function bridge() external view returns (IBridge);

    function wasmModuleRoot() external view returns (bytes32);

    function latestConfirmed() external view returns (bytes32);

    function getStakerAddress(uint64 stakerNum) external view returns (address);

    function stakerCount() external view returns (uint64);

    function getStaker(address staker) external view returns (Staker memory);

    function sequencerInbox() external view returns (ISequencerInbox);

    function genesisAssertionHash() external pure returns (bytes32);

    function getAssertion(bytes32 assertionHash) external view returns (AssertionNode memory);

    function getAssertionCreationBlockForLogLookup(bytes32 assertionHash) external view returns (uint256);

    function isStaked(address staker) external view returns (bool);

    function latestStakedAssertion(address staker) external view returns (bytes32);

    function amountStaked(address staker) external view returns (uint256);

    function withdrawableFunds(address owner) external view returns (uint256);

```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/rollup/IRollupCore.sol#L128:128

```solidity
File: src/bridge/ISequencerInbox.sol


    function rollup() external view returns (IOwnable);

    function bridge() external view returns (IBridge);

    function maxTimeVariation()
        external
        view
        returns (
            uint256 delayBlocks,
            uint256 futureBlocks,
            uint256 delaySeconds,
            uint256 futureSeconds
        );

    function removeDelayAfterFork() external;

    function forceInclusion(
        uint256 _totalDelayedMessagesRead,
        uint8 kind,
        uint64[2] calldata l1BlockAndTime,
        uint256 baseFeeL1,
        address sender,
        bytes32 messageDataHash
    ) external;

    function inboxAccs(uint256 index) external view returns (bytes32);

    function batchCount() external view returns (uint256);

    function isValidKeysetHash(bytes32 ksHash) external view returns (bool);

    function getKeysetCreationBlock(bytes32 ksHash) external view returns (uint256);

    function forceInclusionDeadline(uint64 blockNumber)
        external
        view
        returns (uint64 blockNumberDeadline);

    function addSequencerL2BatchFromOrigin(
        uint256 sequenceNumber,
        bytes calldata data,
        uint256 afterDelayedMessagesRead,
        IGasRefunder gasRefunder
    ) external;

    function addSequencerL2BatchFromOrigin(
        uint256 sequenceNumber,
        bytes calldata data,
        uint256 afterDelayedMessagesRead,
        IGasRefunder gasRefunder,
        uint256 prevMessageCount,
        uint256 newMessageCount
    ) external;

    function addSequencerL2Batch(
        uint256 sequenceNumber,
        bytes calldata data,
        uint256 afterDelayedMessagesRead,
        IGasRefunder gasRefunder,
        uint256 prevMessageCount,
        uint256 newMessageCount
    ) external;

    function addSequencerL2BatchFromBlobs(
        uint256 sequenceNumber,
        uint256 afterDelayedMessagesRead,
        IGasRefunder gasRefunder,
        uint256 prevMessageCount,
        uint256 newMessageCount
    ) external;

    function addSequencerL2BatchFromBlobsDelayProof(
        uint256 sequenceNumber,
        uint256 afterDelayedMessagesRead,
        IGasRefunder gasRefunder,
        uint256 prevMessageCount,
        uint256 newMessageCount,
        DelayProof calldata delayProof
    ) external;

    function addSequencerL2BatchFromOriginDelayProof(
        uint256 sequenceNumber,
        bytes calldata data,
        uint256 afterDelayedMessagesRead,
        IGasRefunder gasRefunder,
        uint256 prevMessageCount,
        uint256 newMessageCount,
        DelayProof calldata delayProof
    ) external;

    function addSequencerL2BatchDelayProof(
        uint256 sequenceNumber,
        bytes calldata data,
        uint256 afterDelayedMessagesRead,
        IGasRefunder gasRefunder,
        uint256 prevMessageCount,
        uint256 newMessageCount,
        DelayProof calldata delayProof
    ) external;

    function setMaxTimeVariation(MaxTimeVariation memory maxTimeVariation_) external;

    function setIsBatchPoster(address addr, bool isBatchPoster_) external;

    function setValidKeyset(bytes calldata keysetBytes) external;

    function invalidateKeysetHash(bytes32 ksHash) external;

    function setIsSequencer(address addr, bool isSequencer_) external;

    function setBatchPosterManager(address newBatchPosterManager) external;

    function updateRollupAddress() external;

    function initialize(
        IBridge bridge_,
        MaxTimeVariation calldata maxTimeVariation_,
        BufferConfig calldata bufferConfig_
    ) external;

```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/bridge/ISequencerInbox.sol#L287:291

```solidity
File: src/rollup/RollupLib.sol


    function assertionHash(
        bytes32 parentAssertionHash,
        AssertionState memory afterState,
        bytes32 inboxAcc
    ) internal pure returns (bytes32) {
        // we can no longer have `hasSibling` in the assertion hash as it would allow identical assertions
        return assertionHash(
            parentAssertionHash,
            afterState.hash(),
            inboxAcc
        );
    }

    function assertionHash(
        bytes32 parentAssertionHash,
        bytes32 afterStateHash,
        bytes32 inboxAcc
    ) internal pure returns (bytes32) {
        // we can no longer have `hasSibling` in the assertion hash as it would allow identical assertions
        return
            keccak256(
                abi.encodePacked(
                    parentAssertionHash,
                    afterStateHash,
                    inboxAcc
                )
            );
    }

```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/rollup/RollupLib.sol#L37:51

```solidity
File: src/challengeV2/IAssertionChain.sol


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

```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/challengeV2/IAssertionChain.sol#L26:26

```solidity
File: src/bridge/SequencerInbox.sol


    function maxTimeVariation()
        external
        view
        returns (
            uint256,
            uint256,
            uint256,
            uint256
        )
    {
        (
            uint64 delayBlocks_,
            uint64 futureBlocks_,
            uint64 delaySeconds_,
            uint64 futureSeconds_
        ) = maxTimeVariationInternal();

        return (
            uint256(delayBlocks_),
            uint256(futureBlocks_),
            uint256(delaySeconds_),
            uint256(futureSeconds_)
        );
    }

    function removeDelayAfterFork() external {
        if (!_chainIdChanged()) revert NotForked();
        delayBlocks = 1;
        futureBlocks = 1;
        delaySeconds = 1;
        futureSeconds = 1;
    }

    function forceInclusion(
        uint256 _totalDelayedMessagesRead,
        uint8 kind,
        uint64[2] calldata l1BlockAndTime,
        uint256 baseFeeL1,
        address sender,
        bytes32 messageDataHash
    ) external {
        if (_totalDelayedMessagesRead <= totalDelayedMessagesRead) revert DelayedBackwards();
        bytes32 messageHash = Messages.messageHash(
            kind,
            sender,
            l1BlockAndTime[0],
            l1BlockAndTime[1],
            _totalDelayedMessagesRead - 1,
            baseFeeL1,
            messageDataHash
        );

        uint256 delayBlocks_ = delayBlocks;

        if (isDelayBufferable) {
            // proactively apply any pending delay buffer updates before the force included message l1BlockAndTime
            buffer.update(l1BlockAndTime[0]);
            delayBlocks_ = delayBufferableBlocks(buffer.bufferBlocks);
        }
        // Can only force-include after the Sequencer-only window has expired.
        if (l1BlockAndTime[0] + delayBlocks_ >= block.number) revert ForceIncludeBlockTooSoon();

        // Verify that message hash represents the last message sequence of delayed message to be included
        bytes32 prevDelayedAcc = 0;
        if (_totalDelayedMessagesRead > 1) {
            prevDelayedAcc = bridge.delayedInboxAccs(_totalDelayedMessagesRead - 2);
        }
        if (
            bridge.delayedInboxAccs(_totalDelayedMessagesRead - 1) !=
            Messages.accumulateInboxMessage(prevDelayedAcc, messageHash)
        ) revert IncorrectMessagePreimage();

        (bytes32 dataHash, IBridge.TimeBounds memory timeBounds) = formEmptyDataHash(
            _totalDelayedMessagesRead
        );
        uint256 __totalDelayedMessagesRead = _totalDelayedMessagesRead;
        uint256 prevSeqMsgCount = bridge.sequencerReportedSubMessageCount();
        uint256 newSeqMsgCount = prevSeqMsgCount; // force inclusion should not modify sequencer message count
        (
            uint256 seqMessageIndex,
            bytes32 beforeAcc,
            bytes32 delayedAcc,
            bytes32 afterAcc
        ) = addSequencerL2BatchImpl(
                dataHash,
                __totalDelayedMessagesRead,
                0,
                prevSeqMsgCount,
                newSeqMsgCount
            );
        emit SequencerBatchDelivered(
            seqMessageIndex,
            beforeAcc,
            afterAcc,
            delayedAcc,
            totalDelayedMessagesRead,
            timeBounds,
            IBridge.BatchDataLocation.NoData
        );
    }

    function inboxAccs(uint256 index) external view returns (bytes32) {
        return bridge.sequencerInboxAccs(index);
    }

    function batchCount() external view returns (uint256) {
        return bridge.sequencerMessageCount();
    }

    function isValidKeysetHash(bytes32 ksHash) external view returns (bool) {
        return dasKeySetInfo[ksHash].isValidKeyset;
    }

    function getKeysetCreationBlock(bytes32 ksHash) external view returns (uint256) {
        DasKeySetInfo memory ksInfo = dasKeySetInfo[ksHash];
        if (ksInfo.creationBlock == 0) revert NoSuchKeyset(ksHash);
        return uint256(ksInfo.creationBlock);
    }

    function forceInclusionDeadline(uint64 blockNumber) external view returns (uint64) {
        uint64 _delayBlocks = delayBlocks;
        if (isDelayBufferable) {
            uint64 _buffer = buffer.calcPendingBuffer(blockNumber);
            _delayBlocks = delayBufferableBlocks(_buffer);
        }
        return blockNumber + _delayBlocks;
    }

    function addSequencerL2BatchFromOrigin(
        uint256,
        bytes calldata,
        uint256,
        IGasRefunder
    ) external pure {
        revert Deprecated();
    }

    function addSequencerL2BatchFromOrigin(
        uint256 sequenceNumber,
        bytes calldata data,
        uint256 afterDelayedMessagesRead,
        IGasRefunder gasRefunder,
        uint256 prevMessageCount,
        uint256 newMessageCount
    ) external refundsGas(gasRefunder, IReader4844(address(0))) {
        // solhint-disable-next-line avoid-tx-origin
        if (msg.sender != tx.origin) revert NotOrigin();
        if (!isBatchPoster[msg.sender]) revert NotBatchPoster();
        if (isDelayProofRequired(afterDelayedMessagesRead)) revert DelayProofRequired();

        addSequencerL2BatchFromCalldataImpl(
            sequenceNumber,
            data,
            afterDelayedMessagesRead,
            prevMessageCount,
            newMessageCount,
            true
        );
    }

    function addSequencerL2Batch(
        uint256 sequenceNumber,
        bytes calldata data,
        uint256 afterDelayedMessagesRead,
        IGasRefunder gasRefunder,
        uint256 prevMessageCount,
        uint256 newMessageCount
    ) external override refundsGas(gasRefunder, IReader4844(address(0))) {
        if (!isBatchPoster[msg.sender] && msg.sender != address(rollup)) revert NotBatchPoster();
        if (isDelayProofRequired(afterDelayedMessagesRead)) revert DelayProofRequired();

        addSequencerL2BatchFromCalldataImpl(
            sequenceNumber,
            data,
            afterDelayedMessagesRead,
            prevMessageCount,
            newMessageCount,
            false
        );
    }

    function addSequencerL2BatchFromBlobs(
        uint256 sequenceNumber,
        uint256 afterDelayedMessagesRead,
        IGasRefunder gasRefunder,
        uint256 prevMessageCount,
        uint256 newMessageCount
    ) external refundsGas(gasRefunder, reader4844) {
        if (!isBatchPoster[msg.sender]) revert NotBatchPoster();
        if (isDelayProofRequired(afterDelayedMessagesRead)) revert DelayProofRequired();

        addSequencerL2BatchFromBlobsImpl(
            sequenceNumber,
            afterDelayedMessagesRead,
            prevMessageCount,
            newMessageCount
        );
    }

    function addSequencerL2BatchFromBlobsDelayProof(
        uint256 sequenceNumber,
        uint256 afterDelayedMessagesRead,
        IGasRefunder gasRefunder,
        uint256 prevMessageCount,
        uint256 newMessageCount,
        DelayProof calldata delayProof
    ) external refundsGas(gasRefunder, reader4844) {
        if (!isBatchPoster[msg.sender]) revert NotBatchPoster();
        if (!isDelayBufferable) revert NotDelayBufferable();

        delayProofImpl(afterDelayedMessagesRead, delayProof);
        addSequencerL2BatchFromBlobsImpl(
            sequenceNumber,
            afterDelayedMessagesRead,
            prevMessageCount,
            newMessageCount
        );
    }

    function addSequencerL2BatchFromOriginDelayProof(
        uint256 sequenceNumber,
        bytes calldata data,
        uint256 afterDelayedMessagesRead,
        IGasRefunder gasRefunder,
        uint256 prevMessageCount,
        uint256 newMessageCount,
        DelayProof calldata delayProof
    ) external refundsGas(gasRefunder, IReader4844(address(0))) {
        // solhint-disable-next-line avoid-tx-origin
        if (msg.sender != tx.origin) revert NotOrigin();
        if (!isBatchPoster[msg.sender]) revert NotBatchPoster();
        if (!isDelayBufferable) revert NotDelayBufferable();

        delayProofImpl(afterDelayedMessagesRead, delayProof);
        addSequencerL2BatchFromCalldataImpl(
            sequenceNumber,
            data,
            afterDelayedMessagesRead,
            prevMessageCount,
            newMessageCount,
            true
        );
    }

    function addSequencerL2BatchDelayProof(
        uint256 sequenceNumber,
        bytes calldata data,
        uint256 afterDelayedMessagesRead,
        IGasRefunder gasRefunder,
        uint256 prevMessageCount,
        uint256 newMessageCount,
        DelayProof calldata delayProof
    ) external refundsGas(gasRefunder, IReader4844(address(0))) {
        if (!isBatchPoster[msg.sender] && msg.sender != address(rollup)) revert NotBatchPoster();
        if (!isDelayBufferable) revert NotDelayBufferable();

        delayProofImpl(afterDelayedMessagesRead, delayProof);
        addSequencerL2BatchFromCalldataImpl(
            sequenceNumber,
            data,
            afterDelayedMessagesRead,
            prevMessageCount,
            newMessageCount,
            false
        );
    }

    function setMaxTimeVariation(ISequencerInbox.MaxTimeVariation memory maxTimeVariation_)
        external
        onlyRollupOwner
    {
        _setMaxTimeVariation(maxTimeVariation_);
        emit OwnerFunctionCalled(0);
    }

    function setIsBatchPoster(address addr, bool isBatchPoster_)
        external
        onlyRollupOwnerOrBatchPosterManager
    {
        isBatchPoster[addr] = isBatchPoster_;
        emit OwnerFunctionCalled(1);
    }

    function setValidKeyset(bytes calldata keysetBytes) external onlyRollupOwner {
        uint256 ksWord = uint256(keccak256(bytes.concat(hex"fe", keccak256(keysetBytes))));
        bytes32 ksHash = bytes32(ksWord ^ (1 << 255));
        if (keysetBytes.length >= 64 * 1024) revert KeysetTooLarge();

        if (dasKeySetInfo[ksHash].isValidKeyset) revert AlreadyValidDASKeyset(ksHash);
        uint256 creationBlock = block.number;
        if (hostChainIsArbitrum) {
            creationBlock = ArbSys(address(100)).arbBlockNumber();
        }
        dasKeySetInfo[ksHash] = DasKeySetInfo({
            isValidKeyset: true,
            creationBlock: uint64(creationBlock)
        });
        emit SetValidKeyset(ksHash, keysetBytes);
        emit OwnerFunctionCalled(2);
    }

    function invalidateKeysetHash(bytes32 ksHash) external onlyRollupOwner {
        if (!dasKeySetInfo[ksHash].isValidKeyset) revert NoSuchKeyset(ksHash);
        // we don't delete the block creation value since its used to fetch the SetValidKeyset
        // event efficiently. The event provides the hash preimage of the key.
        // this is still needed when syncing the chain after a keyset is invalidated.
        dasKeySetInfo[ksHash].isValidKeyset = false;
        emit InvalidateKeyset(ksHash);
        emit OwnerFunctionCalled(3);
    }

    function setIsSequencer(address addr, bool isSequencer_)
        external
        onlyRollupOwnerOrBatchPosterManager
    {
        isSequencer[addr] = isSequencer_;
        emit OwnerFunctionCalled(4); // Owner in this context can also be batch poster manager
    }

    function setBatchPosterManager(address newBatchPosterManager) external onlyRollupOwner {
        batchPosterManager = newBatchPosterManager;
        emit OwnerFunctionCalled(5);
    }

    function updateRollupAddress() external {
        if (msg.sender != IOwnable(rollup).owner())
            revert NotOwner(msg.sender, IOwnable(rollup).owner());
        IOwnable newRollup = bridge.rollup();
        if (rollup == newRollup) revert RollupNotChanged();
        rollup = newRollup;
    }

    function initialize(
        IBridge bridge_,
        ISequencerInbox.MaxTimeVariation calldata maxTimeVariation_,
        BufferConfig memory bufferConfig_
    ) external onlyDelegated {
        if (bridge != IBridge(address(0))) revert AlreadyInit();
        if (bridge_ == IBridge(address(0))) revert HadZeroInit();

        // Make sure logic contract was created by proper value for 'isUsingFeeToken'.
        // Bridge in ETH based chains doesn't implement nativeToken(). In future it might implement it and return address(0)
        bool actualIsUsingFeeToken = false;
        try IERC20Bridge(address(bridge_)).nativeToken() returns (address feeToken) {
            if (feeToken != address(0)) {
                actualIsUsingFeeToken = true;
            }
        } catch {}
        if (isUsingFeeToken != actualIsUsingFeeToken) {
            revert NativeTokenMismatch();
        }

        bridge = bridge_;
        rollup = bridge_.rollup();

        _setMaxTimeVariation(maxTimeVariation_);

        if (isDelayBufferable) {
            _setBufferConfig(bufferConfig_);
        }
    }

    function _chainIdChanged() internal view returns (bool) {
        return deployTimeChainId != block.chainid;
    }

    function postUpgradeInit(BufferConfig memory bufferConfig_)
        external
        onlyDelegated
        onlyProxyOwner
    {
        if (!isDelayBufferable) revert NotDelayBufferable();

        // Assuming we would not upgrade from a version that does not have the buffer initialized
        // If that is the case, postUpgradeInit do not need to be called
        if (buffer.bufferBlocks != 0) {
            revert AlreadyInit();
        }

        _setBufferConfig(bufferConfig_);
    }

```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/bridge/SequencerInbox.sol#L161:175

```solidity
File: src/challengeV2/EdgeChallengeManager.sol


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
        uint256[] calldata _stakeAmounts
    ) external;

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
        uint256[] calldata _stakeAmounts
    ) public initializer {
        if (address(_assertionChain) == address(0)) {
            revert EmptyAssertionChain();
        }
        assertionChain = _assertionChain;
        if (address(_oneStepProofEntry) == address(0)) {
            revert EmptyOneStepProofEntry();
        }
        oneStepProofEntry = _oneStepProofEntry;
        if (_challengePeriodBlocks == 0) {
            revert EmptyChallengePeriod();
        }
        challengePeriodBlocks = _challengePeriodBlocks;

        stakeToken = _stakeToken;
        if (_excessStakeReceiver == address(0)) {
            revert EmptyStakeReceiver();
        }
        excessStakeReceiver = _excessStakeReceiver;

        if (!EdgeChallengeManagerLib.isPowerOfTwo(layerZeroBlockEdgeHeight)) {
            revert NotPowerOfTwo(layerZeroBlockEdgeHeight);
        }
        LAYERZERO_BLOCKEDGE_HEIGHT = layerZeroBlockEdgeHeight;
        if (!EdgeChallengeManagerLib.isPowerOfTwo(layerZeroBigStepEdgeHeight)) {
            revert NotPowerOfTwo(layerZeroBigStepEdgeHeight);
        }
        LAYERZERO_BIGSTEPEDGE_HEIGHT = layerZeroBigStepEdgeHeight;
        if (!EdgeChallengeManagerLib.isPowerOfTwo(layerZeroSmallStepEdgeHeight)) {
            revert NotPowerOfTwo(layerZeroSmallStepEdgeHeight);
        }
        LAYERZERO_SMALLSTEPEDGE_HEIGHT = layerZeroSmallStepEdgeHeight;

        // ensure that there is at least on of each type of level
        if (_numBigStepLevel == 0) {
            revert ZeroBigStepLevels();
        }
        // ensure there's also space for the block level and the small step level
        // in total level parameters
        if (_numBigStepLevel > 253) {
            revert BigStepLevelsTooMany(_numBigStepLevel);
        }
        NUM_BIGSTEP_LEVEL = _numBigStepLevel;

        if (_numBigStepLevel + 2 != _stakeAmounts.length) {
            revert StakeAmountsMismatch(_stakeAmounts.length, _numBigStepLevel + 2);
        }
        stakeAmounts = _stakeAmounts;
    }

    function createLayerZeroEdge(CreateEdgeArgs calldata args) external returns (bytes32);

    function createLayerZeroEdge(CreateEdgeArgs calldata args) external returns (bytes32) {
        // Check if whitelist is enabled in the Rollup
        // We only enforce whitelist in this function as it may exhaust resources
        bool whitelistEnabled = !assertionChain.validatorWhitelistDisabled();

        if (whitelistEnabled && !assertionChain.isValidator(msg.sender)) {
            revert NotValidator(msg.sender);
        }

        EdgeAddedData memory edgeAdded;
        EdgeType eType = ChallengeEdgeLib.levelToType(args.level, NUM_BIGSTEP_LEVEL);
        uint256 expectedEndHeight = getLayerZeroEndHeight(eType);
        AssertionReferenceData memory ard;

        if (eType == EdgeType.Block) {
            // for block type edges we need to provide some extra assertion data context
            if (args.proof.length == 0) {
                revert EmptyEdgeSpecificProof();
            }
            (, AssertionStateData memory predecessorStateData, AssertionStateData memory claimStateData) =
                abi.decode(args.proof, (bytes32[], AssertionStateData, AssertionStateData));

            assertionChain.validateAssertionHash(
                args.claimId, claimStateData.assertionState, claimStateData.prevAssertionHash, claimStateData.inboxAcc
            );

            assertionChain.validateAssertionHash(
                claimStateData.prevAssertionHash,
                predecessorStateData.assertionState,
                predecessorStateData.prevAssertionHash,
                predecessorStateData.inboxAcc
            );

            if (args.endHistoryRoot != claimStateData.assertionState.endHistoryRoot) {
                revert EndHistoryRootMismatch(args.endHistoryRoot, claimStateData.assertionState.endHistoryRoot);
            }

            ard = AssertionReferenceData(
                args.claimId,
                claimStateData.prevAssertionHash,
                assertionChain.isPending(args.claimId),
                assertionChain.getSecondChildCreationBlock(claimStateData.prevAssertionHash) > 0,
                predecessorStateData.assertionState,
                claimStateData.assertionState
            );
        }
        edgeAdded = store.createLayerZeroEdge(
            args, ard, oneStepProofEntry, expectedEndHeight, NUM_BIGSTEP_LEVEL, whitelistEnabled
        );

        IERC20 st = stakeToken;
        uint256 sa = stakeAmounts[args.level];
        // when a zero layer edge is created it must include stake amount. Each time a zero layer
        // edge is created it forces the honest participants to do some work, so we want to disincentive
        // their creation. The amount should also be enough to pay for the gas costs incurred by the honest
        // participant. This can be arranged out of bound by the excess stake receiver.
        // The contract initializer can disable staking by setting zeros for token or amount, to change
        // this a new challenge manager needs to be deployed and its address updated in the assertion chain
        if (address(st) != address(0) && sa != 0) {
            // since only one edge in a group of rivals can ever be confirmed, we know that we
            // will never need to refund more than one edge. Therefore we can immediately send
            // all stakes provided after the first one to an excess stake receiver.
            address receiver = edgeAdded.hasRival ? excessStakeReceiver : address(this);
            st.safeTransferFrom(msg.sender, receiver, sa);
        }

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
        return edgeAdded.edgeId;
    }

    function bisectEdge(bytes32 edgeId, bytes32 bisectionHistoryRoot, bytes calldata prefixProof)
        external
        returns (bytes32, bytes32);

    function bisectEdge(bytes32 edgeId, bytes32 bisectionHistoryRoot, bytes calldata prefixProof)
        external
        returns (bytes32, bytes32)
    {
        (bytes32 lowerChildId, EdgeAddedData memory lowerChildAdded, EdgeAddedData memory upperChildAdded) =
            store.bisectEdge(edgeId, bisectionHistoryRoot, prefixProof);

        bool lowerChildAlreadyExists = lowerChildAdded.edgeId == 0;
        // the lower child might already exist, if it didnt then a new
        // edge was added
        if (!lowerChildAlreadyExists) {
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
        }
        // upper child is always added
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

        emit EdgeBisected(edgeId, lowerChildId, upperChildAdded.edgeId, lowerChildAlreadyExists);

        return (lowerChildId, upperChildAdded.edgeId);
    }

    function confirmEdgeByTime(bytes32 edgeId, AssertionStateData calldata claimStateData) external;

    function confirmEdgeByTime(bytes32 edgeId, AssertionStateData calldata claimStateData) public {
        ChallengeEdge storage topEdge = store.get(edgeId);
        if (!topEdge.isLayerZero()) {
            revert EdgeNotLayerZero(topEdge.id(), topEdge.staker, topEdge.claimId);
        }

        uint64 assertionBlocks = 0;
        // if the edge is block level and the assertion being claimed against was the first child of its predecessor
        // then we are able to count the time between the first and second child as time towards
        // the this edge
        bool isBlockLevel = ChallengeEdgeLib.levelToType(topEdge.level, NUM_BIGSTEP_LEVEL) == EdgeType.Block;
        if (isBlockLevel && assertionChain.isFirstChild(topEdge.claimId)) {
            assertionChain.validateAssertionHash(
                topEdge.claimId,
                claimStateData.assertionState,
                claimStateData.prevAssertionHash,
                claimStateData.inboxAcc
            );
            assertionBlocks = assertionChain.getSecondChildCreationBlock(claimStateData.prevAssertionHash)
                - assertionChain.getFirstChildCreationBlock(claimStateData.prevAssertionHash);
        }

        uint256 totalTimeUnrivaled = store.confirmEdgeByTime(edgeId, assertionBlocks, challengePeriodBlocks);

        emit EdgeConfirmedByTime(edgeId, store.edges[edgeId].mutualId(), totalTimeUnrivaled);
    }

    function multiUpdateTimeCacheByChildren(bytes32[] calldata edgeIds) external;

    function multiUpdateTimeCacheByChildren(bytes32[] calldata edgeIds) public {
        for (uint256 i = 0; i < edgeIds.length; i++) {
            (bool updated, uint256 newValue) = store.updateTimerCacheByChildren(edgeIds[i]);
            if (updated) emit TimerCacheUpdated(edgeIds[i], newValue);
        }
    }

    function updateTimerCacheByChildren(bytes32 edgeId) external;

    function updateTimerCacheByChildren(bytes32 edgeId) public {
        (bool updated, uint256 newValue) = store.updateTimerCacheByChildren(edgeId);
        if (updated) emit TimerCacheUpdated(edgeId, newValue);
    }

    function updateTimerCacheByClaim(bytes32 edgeId, bytes32 claimingEdgeId) external;

    function updateTimerCacheByClaim(bytes32 edgeId, bytes32 claimingEdgeId) public {
        (bool updated, uint256 newValue) = store.updateTimerCacheByClaim(edgeId, claimingEdgeId, NUM_BIGSTEP_LEVEL);
        if (updated) emit TimerCacheUpdated(edgeId, newValue);
    }

    function confirmEdgeByOneStepProof(
        bytes32 edgeId,
        OneStepData calldata oneStepData,
        ConfigData calldata prevConfig,
        bytes32[] calldata beforeHistoryInclusionProof,
        bytes32[] calldata afterHistoryInclusionProof
    ) external;

    function confirmEdgeByOneStepProof(
        bytes32 edgeId,
        OneStepData calldata oneStepData,
        ConfigData calldata prevConfig,
        bytes32[] calldata beforeHistoryInclusionProof,
        bytes32[] calldata afterHistoryInclusionProof
    ) public {
        bytes32 prevAssertionHash = store.getPrevAssertionHash(edgeId);

        assertionChain.validateConfig(prevAssertionHash, prevConfig);

        ExecutionContext memory execCtx = ExecutionContext({
            maxInboxMessagesRead: prevConfig.nextInboxPosition,
            bridge: assertionChain.bridge(),
            initialWasmModuleRoot: prevConfig.wasmModuleRoot
        });

        store.confirmEdgeByOneStepProof(
            edgeId,
            oneStepProofEntry,
            oneStepData,
            execCtx,
            beforeHistoryInclusionProof,
            afterHistoryInclusionProof,
            NUM_BIGSTEP_LEVEL,
            LAYERZERO_BIGSTEPEDGE_HEIGHT,
            LAYERZERO_SMALLSTEPEDGE_HEIGHT
        );

        emit EdgeConfirmedByOneStepProof(edgeId, store.edges[edgeId].mutualId());
    }

    function refundStake(bytes32 edgeId) external;

    function refundStake(bytes32 edgeId) public {
        ChallengeEdge storage edge = store.get(edgeId);
        // setting refunded also do checks that the edge cannot be refunded twice
        edge.setRefunded();

        IERC20 st = stakeToken;
        uint256 sa = stakeAmounts[edge.level];
        // no need to refund with the token or amount where zero'd out
        if (address(st) != address(0) && sa != 0) {
            st.safeTransfer(edge.staker, sa);
        }

        emit EdgeRefunded(edgeId, store.edges[edgeId].mutualId(), address(st), sa);
    }

    function getLayerZeroEndHeight(EdgeType eType) external view returns (uint256);

    function getLayerZeroEndHeight(EdgeType eType) public view returns (uint256) {
        if (eType == EdgeType.Block) {
            return LAYERZERO_BLOCKEDGE_HEIGHT;
        } else if (eType == EdgeType.BigStep) {
            return LAYERZERO_BIGSTEPEDGE_HEIGHT;
        } else if (eType == EdgeType.SmallStep) {
            return LAYERZERO_SMALLSTEPEDGE_HEIGHT;
        } else {
            revert InvalidEdgeType(eType);
        }
    }

    function calculateEdgeId(
        uint8 level,
        bytes32 originId,
        uint256 startHeight,
        bytes32 startHistoryRoot,
        uint256 endHeight,
        bytes32 endHistoryRoot
    ) external pure returns (bytes32);

    function calculateEdgeId(
        uint8 level,
        bytes32 originId,
        uint256 startHeight,
        bytes32 startHistoryRoot,
        uint256 endHeight,
        bytes32 endHistoryRoot
    ) public pure returns (bytes32) {
        return ChallengeEdgeLib.idComponent(level, originId, startHeight, startHistoryRoot, endHeight, endHistoryRoot);
    }

    function calculateMutualId(
        uint8 level,
        bytes32 originId,
        uint256 startHeight,
        bytes32 startHistoryRoot,
        uint256 endHeight
    ) external pure returns (bytes32);

    function calculateMutualId(
        uint8 level,
        bytes32 originId,
        uint256 startHeight,
        bytes32 startHistoryRoot,
        uint256 endHeight
    ) public pure returns (bytes32) {
        return ChallengeEdgeLib.mutualIdComponent(level, originId, startHeight, startHistoryRoot, endHeight);
    }

    function edgeExists(bytes32 edgeId) external view returns (bool);

    function edgeExists(bytes32 edgeId) public view returns (bool) {
        return store.edges[edgeId].exists();
    }

    function getEdge(bytes32 edgeId) external view returns (ChallengeEdge memory);

    function getEdge(bytes32 edgeId) public view returns (ChallengeEdge memory) {
        return store.get(edgeId);
    }

    function edgeLength(bytes32 edgeId) external view returns (uint256);

    function edgeLength(bytes32 edgeId) public view returns (uint256) {
        return store.get(edgeId).length();
    }

    function hasRival(bytes32 edgeId) external view returns (bool);

    function hasRival(bytes32 edgeId) public view returns (bool) {
        return store.hasRival(edgeId);
    }

    function confirmedRival(bytes32 mutualId) external view returns (bytes32);

    function confirmedRival(bytes32 mutualId) public view returns (bytes32) {
        return store.confirmedRivals[mutualId];
    }

    function hasLengthOneRival(bytes32 edgeId) external view returns (bool);

    function hasLengthOneRival(bytes32 edgeId) public view returns (bool) {
        return store.hasLengthOneRival(edgeId);
    }

    function timeUnrivaled(bytes32 edgeId) external view returns (uint256);

    function timeUnrivaled(bytes32 edgeId) public view returns (uint256) {
        return store.timeUnrivaled(edgeId);
    }

    function getPrevAssertionHash(bytes32 edgeId) external view returns (bytes32);

    function getPrevAssertionHash(bytes32 edgeId) public view returns (bytes32) {
        return store.getPrevAssertionHash(edgeId);
    }

    function firstRival(bytes32 mutualId) external view returns (bytes32);

    function firstRival(bytes32 mutualId) public view returns (bytes32) {
        return store.firstRivals[mutualId];
    }

    function hasMadeLayerZeroRival(address account, bytes32 mutualId) external view returns (bool);

    function hasMadeLayerZeroRival(address account, bytes32 mutualId) external view returns (bool) {
        return store.hasMadeLayerZeroRival[account][mutualId];
    }

```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/challengeV2/EdgeChallengeManager.sol#L672:674

```solidity
File: src/rollup/IRollupAdmin.sol


    function initialize(Config calldata config, ContractDependencies calldata connectedContracts) external;

    function forceRefundStaker(address[] memory stacker) external;

    function pause() external;

    function resume() external;

    function setOutbox(IOutbox _outbox) external;

    function removeOldOutbox(address _outbox) external;

    function setDelayedInbox(address _inbox, bool _enabled) external;

    function setValidator(address[] memory _validator, bool[] memory _val) external;

    function setOwner(address newOwner) external;

    function setMinimumAssertionPeriod(uint256 newPeriod) external;

    function setConfirmPeriodBlocks(uint64 newConfirmPeriod) external;

    function setBaseStake(uint256 newBaseStake) external;

    function forceCreateAssertion(
        bytes32 prevAssertionHash,
        AssertionInputs calldata assertion,
        bytes32 expectedAssertionHash
    ) external;

    function forceConfirmAssertion(
        bytes32 assertionHash,
        bytes32 parentAssertionHash,
        AssertionState calldata confirmState,
        bytes32 inboxAcc
    ) external;

    function setLoserStakeEscrow(address newLoserStakerEscrow) external;

    function setWasmModuleRoot(bytes32 newWasmModuleRoot) external;

    function setSequencerInbox(address _sequencerInbox) external;

    function setValidatorWhitelistDisabled(bool _validatorWhitelistDisabled) external;

    function setChallengeManager(address _challengeManager) external;

```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/rollup/IRollupAdmin.sol#L119:119

```solidity
File: src/rollup/IRollupLogic.sol


    function initialize(address stakeToken) external view;

    function removeWhitelistAfterFork() external;

    function removeWhitelistAfterValidatorAfk() external;

    function confirmAssertion(
        bytes32 assertionHash,
        bytes32 prevAssertionHash,
        AssertionState calldata confirmState,
        bytes32 winningEdgeId,
        ConfigData calldata prevConfig,
        bytes32 inboxAcc
    ) external;

    function stakeOnNewAssertion(AssertionInputs calldata assertion, bytes32 expectedAssertionHash) external;

    function returnOldDeposit() external;

    function reduceDeposit(uint256 target) external;

    function withdrawStakerFunds() external returns (uint256);

    function newStakeOnNewAssertion(
        uint256 tokenAmount,
        AssertionInputs calldata assertion,
        bytes32 expectedAssertionHash
    ) external;

    function newStakeOnNewAssertion(
        uint256 tokenAmount,
        AssertionInputs calldata assertion,
        bytes32 expectedAssertionHash,
        address withdrawalAddress
    ) external;

    function addToDeposit(address stakerAddress, uint256 tokenAmount) external;

```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/rollup/IRollupLogic.sol#L51:51

```solidity
File: src/rollup/RollupAdminLogic.sol


    function initialize(Config calldata config, ContractDependencies calldata connectedContracts)
        external
        override
        onlyProxy
        initializer
    {
        rollupDeploymentBlock = block.number;
        bridge = connectedContracts.bridge;
        connectedContracts.bridge.setDelayedInbox(address(connectedContracts.inbox), true);
        connectedContracts.bridge.setSequencerInbox(address(connectedContracts.sequencerInbox));

        inbox = connectedContracts.inbox;
        outbox = connectedContracts.outbox;
        connectedContracts.bridge.setOutbox(address(connectedContracts.outbox), true);
        rollupEventInbox = connectedContracts.rollupEventInbox;

        // dont need to connect and initialize the event inbox if it's already been initialized
        if (!bridge.allowedDelayedInboxes(address(connectedContracts.rollupEventInbox))) {
            connectedContracts.bridge.setDelayedInbox(address(connectedContracts.rollupEventInbox), true);
            connectedContracts.rollupEventInbox.rollupInitialized(config.chainId, config.chainConfig);
        }

        if (connectedContracts.sequencerInbox.totalDelayedMessagesRead() == 0) {
            connectedContracts.sequencerInbox.addSequencerL2Batch(0, "", 1, IGasRefunder(address(0)), 0, 1);
        }

        validatorWalletCreator = connectedContracts.validatorWalletCreator;
        challengeManager = connectedContracts.challengeManager;

        confirmPeriodBlocks = config.confirmPeriodBlocks;
        chainId = config.chainId;
        baseStake = config.baseStake;
        wasmModuleRoot = config.wasmModuleRoot;
        // A little over 15 minutes
        minimumAssertionPeriod = 75;
        challengeGracePeriodBlocks = config.challengeGracePeriodBlocks;

        // loser stake is now sent directly to loserStakeEscrow, it must not
        // be address(0) because some token do not allow transfers to address(0)
        require(config.loserStakeEscrow != address(0), "INVALID_ESCROW_0");
        loserStakeEscrow = config.loserStakeEscrow;

        stakeToken = config.stakeToken;
        anyTrustFastConfirmer = config.anyTrustFastConfirmer;

        bytes32 parentAssertionHash = bytes32(0);
        bytes32 inboxAcc = bytes32(0);
        bytes32 genesisHash = RollupLib.assertionHash({
            parentAssertionHash: parentAssertionHash,
            afterStateHash: config.genesisAssertionState.hash(),
            inboxAcc: inboxAcc
        });

        uint256 currentInboxCount = bridge.sequencerMessageCount();
        // ensure to move the inbox forward by at least one message
        if (currentInboxCount == config.genesisInboxCount) {
            currentInboxCount += 1;
        }
        AssertionNode memory initialAssertion = AssertionNodeLib.createAssertion(
            true,
            RollupLib.configHash({
                wasmModuleRoot: wasmModuleRoot,
                requiredStake: baseStake,
                challengeManager: address(challengeManager),
                confirmPeriodBlocks: confirmPeriodBlocks,
                nextInboxPosition: uint64(currentInboxCount)
            })
        );
        initializeCore(initialAssertion, genesisHash);

        AssertionInputs memory assertionInputs;
        assertionInputs.afterState = config.genesisAssertionState;
        emit AssertionCreated(
            genesisHash,
            parentAssertionHash,
            assertionInputs,
            inboxAcc,
            currentInboxCount,
            wasmModuleRoot,
            baseStake,
            address(challengeManager),
            confirmPeriodBlocks
        );
        if (_hostChainIsArbitrum) {
            _assertionCreatedAtArbSysBlock[genesisHash] = ArbSys(address(100)).arbBlockNumber();
        }

        emit RollupInitialized(config.wasmModuleRoot, config.chainId);
    }

    function forceRefundStaker(address[] calldata staker) external override whenPaused {
        require(staker.length > 0, "EMPTY_ARRAY");
        for (uint256 i = 0; i < staker.length; i++) {
            requireInactiveStaker(staker[i]);
            reduceStakeTo(staker[i], 0);
        }
        emit OwnerFunctionCalled(22);
    }

    function pause() external override {
        _pause();
        emit OwnerFunctionCalled(3);
    }

    function resume() external override {
        _unpause();
        emit OwnerFunctionCalled(4);
    }

    function setOutbox(IOutbox _outbox) external override {
        outbox = _outbox;
        bridge.setOutbox(address(_outbox), true);
        emit OwnerFunctionCalled(0);
    }

    function removeOldOutbox(address _outbox) external override {
        require(_outbox != address(outbox), "CUR_OUTBOX");
        bridge.setOutbox(_outbox, false);
        emit OwnerFunctionCalled(1);
    }

    function setDelayedInbox(address _inbox, bool _enabled) external override {
        bridge.setDelayedInbox(address(_inbox), _enabled);
        emit OwnerFunctionCalled(2);
    }

    function setValidator(address[] calldata _validator, bool[] calldata _val) external override {
        require(_validator.length > 0, "EMPTY_ARRAY");
        require(_validator.length == _val.length, "WRONG_LENGTH");

        for (uint256 i = 0; i < _validator.length; i++) {
            isValidator[_validator[i]] = _val[i];
        }
        emit OwnerFunctionCalled(6);
    }

    function setOwner(address newOwner) external override {
        _changeAdmin(newOwner);
        emit OwnerFunctionCalled(7);
    }

    function setMinimumAssertionPeriod(uint256 newPeriod) external override {
        minimumAssertionPeriod = newPeriod;
        emit OwnerFunctionCalled(8);
    }

    function setConfirmPeriodBlocks(uint64 newConfirmPeriod) external override {
        require(newConfirmPeriod > 0, "INVALID_CONFIRM_PERIOD");
        confirmPeriodBlocks = newConfirmPeriod;
        emit OwnerFunctionCalled(9);
    }

    function setBaseStake(uint256 newBaseStake) external override {
        baseStake = newBaseStake;
        emit OwnerFunctionCalled(12);
    }

    function forceCreateAssertion(
        bytes32 prevAssertionHash,
        AssertionInputs calldata assertion,
        bytes32 expectedAssertionHash
    ) external override whenPaused {
        // To update the wasm module root in the case of a bug:
        // 0. pause the contract
        // 1. update the wasm module root in the contract
        // 2. update the config hash of the assertion after which you wish to use the new wasm module root (functionality not written yet)
        // 3. force refund the stake of the current leaf assertion(s)
        // 4. create a new assertion using the assertion with the updated config has as a prev
        // 5. force confirm it - this is necessary to set latestConfirmed on the correct line
        // 6. unpause the contract

        // Normally, a new assertion is created using its prev's confirmPeriodBlocks
        // in the case of a force create, we use the rollup's current confirmPeriodBlocks
        createNewAssertion(assertion, prevAssertionHash, expectedAssertionHash);

        emit OwnerFunctionCalled(23);
    }

    function forceConfirmAssertion(
        bytes32 assertionHash,
        bytes32 parentAssertionHash,
        AssertionState calldata confirmState,
        bytes32 inboxAcc
    ) external override whenPaused {
        // this skip deadline, prev, challenge validations
        confirmAssertionInternal(assertionHash, parentAssertionHash, confirmState, inboxAcc);
        emit OwnerFunctionCalled(24);
    }

    function setLoserStakeEscrow(address newLoserStakerEscrow) external override {
        // loser stake is now sent directly to loserStakeEscrow, it must not
        // be address(0) because some token do not allow transfers to address(0)
        require(newLoserStakerEscrow != address(0), "INVALID_ESCROW_0");
        loserStakeEscrow = newLoserStakerEscrow;
        emit OwnerFunctionCalled(25);
    }

    function setWasmModuleRoot(bytes32 newWasmModuleRoot) external override {
        wasmModuleRoot = newWasmModuleRoot;
        emit OwnerFunctionCalled(26);
    }

    function setSequencerInbox(address _sequencerInbox) external override {
        bridge.setSequencerInbox(_sequencerInbox);
        emit OwnerFunctionCalled(27);
    }

    function setValidatorWhitelistDisabled(bool _validatorWhitelistDisabled) external {
        validatorWhitelistDisabled = _validatorWhitelistDisabled;
        emit OwnerFunctionCalled(30);
    }

    function setChallengeManager(address _challengeManager) external {
        challengeManager = IEdgeChallengeManager(_challengeManager);
        emit OwnerFunctionCalled(32);
    }

```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/rollup/RollupAdminLogic.sol#L326:329

```solidity
File: src/rollup/RollupUserLogic.sol


    function initialize(address _stakeToken) external view override onlyProxy {
        require(_stakeToken != address(0), "NEED_STAKE_TOKEN");
    }

    function _chainIdChanged() internal view returns (bool) {
        return deployTimeChainId != block.chainid;
    }

    function removeWhitelistAfterFork() external {
        require(!validatorWhitelistDisabled, "WHITELIST_DISABLED");
        require(_chainIdChanged(), "CHAIN_ID_NOT_CHANGED");
        validatorWhitelistDisabled = true;
    }

    function removeWhitelistAfterValidatorAfk() external {
        require(!validatorWhitelistDisabled, "WHITELIST_DISABLED");
        require(_validatorIsAfk(), "VALIDATOR_NOT_AFK");
        validatorWhitelistDisabled = true;
    }

    function confirmAssertion(
        bytes32 assertionHash,
        bytes32 prevAssertionHash,
        AssertionState calldata confirmState,
        bytes32 winningEdgeId,
        ConfigData calldata prevConfig,
        bytes32 inboxAcc
    ) external onlyValidator whenNotPaused {
        /*
        * To confirm an assertion, the following must be true:
        * 1. The assertion must be pending
        * 2. The assertion's deadline must have passed
        * 3. The assertion's prev must be latest confirmed
        * 4. The assertion's prev's child confirm deadline must have passed
        * 5. If the assertion's prev has more than 1 child, the assertion must be the winner of the challenge
        *
        * Note that we do not need to ever reject invalid assertion because they can never confirm
        *      and the stake on them is swept to the loserStakeEscrow as soon as the leaf is created
        */

        // The assertion's must exists and be pending and will be validated in RollupCore.confirmAssertionInternal
        AssertionNode storage assertion = getAssertionStorage(assertionHash);

        // prevAssertionHash is user supplied, but will be validated in RollupCore.confirmAssertionInternal
        AssertionNode storage prevAssertion = getAssertionStorage(prevAssertionHash);
        RollupLib.validateConfigHash(prevConfig, prevAssertion.configHash);

        // Check that deadline has passed
        require(block.number >= assertion.createdAtBlock + prevConfig.confirmPeriodBlocks, "BEFORE_DEADLINE");

        // Check that prev is latest confirmed
        require(prevAssertionHash == latestConfirmed(), "PREV_NOT_LATEST_CONFIRMED");

        if (prevAssertion.secondChildBlock > 0) {
            // if the prev has more than 1 child, check if this assertion is the challenge winner
            ChallengeEdge memory winningEdge = IEdgeChallengeManager(prevConfig.challengeManager).getEdge(winningEdgeId);
            require(winningEdge.claimId == assertionHash, "NOT_WINNER");
            require(winningEdge.status == EdgeStatus.Confirmed, "EDGE_NOT_CONFIRMED");
            require(winningEdge.confirmedAtBlock != 0, "ZERO_CONFIRMED_AT_BLOCK");
            // an additional number of blocks is added to ensure that the result of the challenge is widely
            // observable before it causes an assertion to be confirmed. After a winning edge is found, it will
            // always be challengeGracePeriodBlocks before an assertion can be confirmed
            require(
                block.number >= winningEdge.confirmedAtBlock + challengeGracePeriodBlocks,
                "CHALLENGE_GRACE_PERIOD_NOT_PASSED"
            );
        }

        confirmAssertionInternal(assertionHash, prevAssertionHash, confirmState, inboxAcc);
    }

    function stakeOnNewAssertion(AssertionInputs calldata assertion, bytes32 expectedAssertionHash)
        public
        onlyValidator
        whenNotPaused
    {
        // Early revert on duplicated assertion if expectedAssertionHash is set
        require(
            expectedAssertionHash == bytes32(0)
                || getAssertionStorage(expectedAssertionHash).status == AssertionStatus.NoAssertion,
            "EXPECTED_ASSERTION_SEEN"
        );

        require(isStaked(msg.sender), "NOT_STAKED");

        // requiredStake is user supplied, will be verified against configHash later
        // the prev's requiredStake is used to make sure all children have the same stake
        // the staker may have more than enough stake, and the entire stake will be locked
        // we cannot do a refund here because the staker may be staker on an unconfirmed ancestor that requires more stake
        // excess stake can be removed by calling reduceDeposit when the staker is inactive
        require(amountStaked(msg.sender) >= assertion.beforeStateData.configData.requiredStake, "INSUFFICIENT_STAKE");

        bytes32 prevAssertion = RollupLib.assertionHash(
            assertion.beforeStateData.prevPrevAssertionHash,
            assertion.beforeState,
            assertion.beforeStateData.sequencerBatchAcc
        );
        getAssertionStorage(prevAssertion).requireExists();

        // Staker can create new assertion only if
        // a) its last staked assertion is the prev; or
        // b) its last staked assertion have a child
        bytes32 lastAssertion = latestStakedAssertion(msg.sender);
        require(
            lastAssertion == prevAssertion || getAssertionStorage(lastAssertion).firstChildBlock > 0,
            "STAKED_ON_ANOTHER_BRANCH"
        );

        (bytes32 newAssertionHash, bool overflowAssertion) =
            createNewAssertion(assertion, prevAssertion, expectedAssertionHash);
        _stakerMap[msg.sender].latestStakedAssertion = newAssertionHash;

        if (!overflowAssertion) {
            uint256 timeSincePrev = block.number - getAssertionStorage(prevAssertion).createdAtBlock;
            // Verify that assertion meets the minimum Delta time requirement
            require(timeSincePrev >= minimumAssertionPeriod, "TIME_DELTA");
        }

        if (!getAssertionStorage(newAssertionHash).isFirstChild) {
            // We assume assertion.beforeStateData is valid here as it will be validated in createNewAssertion
            // only 1 of the children can be confirmed and get their stake refunded
            // so we send the other children's stake to the loserStakeEscrow
            // NOTE: if the losing staker have staked more than requiredStake, the excess stake will be stuck
            IERC20(stakeToken).safeTransfer(loserStakeEscrow, assertion.beforeStateData.configData.requiredStake);
        }
    }

    function returnOldDeposit() external override onlyValidator whenNotPaused {
        requireInactiveStaker(msg.sender);
        withdrawStaker(msg.sender);
    }

    function reduceDeposit(uint256 target) external onlyValidator whenNotPaused {
        requireInactiveStaker(msg.sender);
        // amount will be checked when creating an assertion
        reduceStakeTo(msg.sender, target);
    }

    function withdrawStakerFunds() external override whenNotPaused returns (uint256) {
        uint256 amount = withdrawFunds(msg.sender);
        require(amount > 0, "NO_FUNDS_TO_WITHDRAW");
        // This is safe because it occurs after all checks and effects
        IERC20(stakeToken).safeTransfer(msg.sender, amount);
        return amount;
    }

    function newStakeOnNewAssertion(
        uint256 tokenAmount,
        AssertionInputs calldata assertion,
        bytes32 expectedAssertionHash
    ) external {
        newStakeOnNewAssertion(tokenAmount, assertion, expectedAssertionHash, msg.sender);
    }

    function newStakeOnNewAssertion(
        uint256 tokenAmount,
        AssertionInputs calldata assertion,
        bytes32 expectedAssertionHash,
        address withdrawalAddress
    ) public {
        require(withdrawalAddress != address(0), "EMPTY_WITHDRAWAL_ADDRESS");
        _newStake(tokenAmount, withdrawalAddress);
        stakeOnNewAssertion(assertion, expectedAssertionHash);
        /// @dev This is an external call, safe because it's at the end of the function
        receiveTokens(tokenAmount);
    }

    function addToDeposit(address stakerAddress, uint256 tokenAmount) external onlyValidator whenNotPaused {
        _addToDeposit(stakerAddress, tokenAmount);
        /// @dev This is an external call, safe because it's at the end of the function
        receiveTokens(tokenAmount);
    }

```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/rollup/RollupUserLogic.sol#L349:353

```solidity
File: src/rollup/BOLDUpgradeAction.sol


    function postUpgradeInit(BufferConfig memory bufferConfig_) external;

    function isValidator(address validator) external view returns (bool);

    function isValidator(address validator) external view returns (bool) {
        return rollup.isValidator(validator);
    }

    function get(bytes32 h) public view returns (ExecutionState memory executionState, uint256 inboxMaxCount) {
        (executionState, inboxMaxCount) = abi.decode(preImages[h], (ExecutionState, uint256));
        require(inboxMaxCount != 0, "Hash not yet set");
    }

    function wasmModuleRoot() external view returns (bytes32);

    function wasmModuleRoot() external view returns (bytes32) {
        return rollup.wasmModuleRoot();
    }

    function latestConfirmed() external view returns (uint64);

    function latestConfirmed() external view returns (uint64) {
        return rollup.latestConfirmed();
    }

    function getNode(uint64 nodeNum) external view returns (Node memory);

    function getNode(uint64 nodeNum) external view returns (Node memory) {
        return rollup.getNode(nodeNum);
    }

    function getStakerAddress(uint64 stakerNum) external view returns (address);

    function getStakerAddress(uint64 stakerNum) external view returns (address) {
        return rollup.getStakerAddress(stakerNum);
    }

    function stakerCount() external view returns (uint64);

    function stakerCount() external view returns (uint64) {
        return rollup.stakerCount();
    }

    function getStaker(address staker) external view returns (OldStaker memory);

    function getStaker(address staker) external view returns (OldStaker memory) {
        return rollup.getStaker(staker);
    }

    function validatorWalletCreator() external view returns (address);

    function validatorWalletCreator() external view returns (address) {
        return rollup.validatorWalletCreator();
    }

    function forceRefundStaker(address[] memory stacker) external;

    function pause() external;

    function resume() external;

```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/rollup/BOLDUpgradeAction.sol#L80:80

```solidity
File: src/challengeV2/libraries/EdgeChallengeManagerLib.sol


    function createLayerZeroEdge(
        EdgeStore storage store,
        CreateEdgeArgs calldata args,
        AssertionReferenceData memory ard,
        IOneStepProofEntry oneStepProofEntry,
        uint256 expectedEndHeight,
        uint8 numBigStepLevel,
        bool whitelistEnabled
    ) internal returns (EdgeAddedData memory) {
        // each edge type requires some specific checks
        (ProofData memory proofData, bytes32 originId) =
            layerZeroTypeSpecificChecks(store, args, ard, oneStepProofEntry, numBigStepLevel);
        // all edge types share some common checks
        (bytes32 startHistoryRoot) = layerZeroCommonChecks(proofData, args, expectedEndHeight);
        // we only wrap the struct creation in a function as doing so with exceeds the stack limit
        ChallengeEdge memory ce = toLayerZeroEdge(originId, startHistoryRoot, args);

        // if the validator whitelist is enabled, we can enforce that a single party cannot create two layer zero edges that rival each other
        // if the validator whitelist is disabled, this check serves no purpose since an attacker can create new accounts
        if (whitelistEnabled) {
            bytes32 mutualId = ce.mutualIdMem();
            if (store.hasMadeLayerZeroRival[msg.sender][mutualId]) {
                revert AccountHasMadeLayerZeroRival(msg.sender, mutualId);
            }
            store.hasMadeLayerZeroRival[msg.sender][mutualId] = true;
        }

        return add(store, ce);
    }

    function bisectEdge(EdgeStore storage store, bytes32 edgeId, bytes32 bisectionHistoryRoot, bytes memory prefixProof)
        internal
        returns (bytes32, EdgeAddedData memory, EdgeAddedData memory)
    {
        if (store.edges[edgeId].status != EdgeStatus.Pending) {
            revert EdgeNotPending(edgeId, store.edges[edgeId].status);
        }
        if (!hasRival(store, edgeId)) {
            revert EdgeUnrivaled(edgeId);
        }

        // cannot bisect an edge twice
        // has rival above checks the edge - so no need to check again
        ChallengeEdge memory ce = getNoCheck(store, edgeId);

        // bisections occur at deterministic heights, this ensures that
        // rival edges bisect at the same height, and create the same child if they agree
        uint256 middleHeight = mandatoryBisectionHeight(ce.startHeight, ce.endHeight);
        {
            (bytes32[] memory preExpansion, bytes32[] memory proof) = abi.decode(prefixProof, (bytes32[], bytes32[]));
            MerkleTreeLib.verifyPrefixProof(
                bisectionHistoryRoot, middleHeight + 1, ce.endHistoryRoot, ce.endHeight + 1, preExpansion, proof
            );
        }

        bytes32 lowerChildId;
        EdgeAddedData memory lowerChildAdded;
        {
            // midpoint proof it valid, create and store the children
            ChallengeEdge memory lowerChild = ChallengeEdgeLib.newChildEdge(
                ce.originId, ce.startHistoryRoot, ce.startHeight, bisectionHistoryRoot, middleHeight, ce.level
            );
            lowerChildId = lowerChild.idMem();
            // it's possible that the store already has the lower child if it was created by a rival
            // (aka a merge move)
            if (!store.edges[lowerChildId].exists()) {
                lowerChildAdded = add(store, lowerChild);
            }
        }

        EdgeAddedData memory upperChildAdded;
        {
            ChallengeEdge memory upperChild = ChallengeEdgeLib.newChildEdge(
                ce.originId, bisectionHistoryRoot, middleHeight, ce.endHistoryRoot, ce.endHeight, ce.level
            );

            // add checks existence and throws if the id already exists
            upperChildAdded = add(store, upperChild);
        }

        store.edges[edgeId].setChildren(lowerChildId, upperChildAdded.edgeId);

        return (lowerChildId, lowerChildAdded, upperChildAdded);
    }

    function confirmEdgeByTime(
        EdgeStore storage store,
        bytes32 edgeId,
        uint64 claimedAssertionUnrivaledBlocks,
        uint64 confirmationThresholdBlock
    ) internal returns (uint256) {
        if (!store.edges[edgeId].exists()) {
            revert EdgeNotExists(edgeId);
        }

        uint256 totalTimeUnrivaled = timeUnrivaledTotal(store, edgeId);

        // since sibling assertions have the same predecessor, they can be viewed as
        // rival edges. Adding the assertion unrivaled time allows us to start the confirmation
        // timer from the moment the first assertion is made, rather than having to wait until the
        // second assertion is made.
        totalTimeUnrivaled += claimedAssertionUnrivaledBlocks;

        if (totalTimeUnrivaled < confirmationThresholdBlock) {
            revert InsufficientConfirmationBlocks(totalTimeUnrivaled, confirmationThresholdBlock);
        }

        // we also check the edge is pending in setConfirmed()
        store.edges[edgeId].setConfirmed();

        // also checks that no other rival has been confirmed
        setConfirmedRival(store, edgeId);

        return totalTimeUnrivaled;
    }

    function updateTimerCacheByChildren(EdgeStore storage store, bytes32 edgeId) internal returns (bool, uint256) {
        return updateTimerCache(store, edgeId, timeUnrivaledTotal(store, edgeId));
    }

    function updateTimerCacheByClaim(
        EdgeStore storage store,
        bytes32 edgeId,
        bytes32 claimingEdgeId,
        uint8 numBigStepLevel
    ) internal returns (bool, uint256) {
        // calculate the time unrivaled without inheritance
        uint256 totalTimeUnrivaled = timeUnrivaled(store, edgeId);
        checkClaimIdLink(store, edgeId, claimingEdgeId, numBigStepLevel);
        totalTimeUnrivaled += store.edges[claimingEdgeId].totalTimeUnrivaledCache;
        return updateTimerCache(store, edgeId, totalTimeUnrivaled);
    }

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
        if (!store.edges[edgeId].exists()) {
            revert EdgeNotExists(edgeId);
        }

        // edge must of type SmallStep
        if (ChallengeEdgeLib.levelToType(store.edges[edgeId].level, numBigStepLevel) != EdgeType.SmallStep) {
            revert EdgeTypeNotSmallStep(store.edges[edgeId].level);
        }

        // edge must be length one to execute one step proofs against
        if (store.edges[edgeId].length() != 1) {
            revert EdgeNotLengthOne(store.edges[edgeId].length());
        }

        // Get the machine step that corresponds to the start height of this edge
        // To do this we sum the machine steps of the edges in each of the preceeding levels.
        // We do not include the block height, since each step at the block level is a new block
        // and new blocks reset the machine step to 0.
        uint256 machineStep = store.edges[edgeId].startHeight;
        {
            bytes32 cursor = edgeId;
            uint256 stepSize = smallStepHeight;
            while (store.edges[cursor].level > 1) {
                bytes32 nextEdgeId = store.edges[cursor].originId;
                // We can traverse to previous levels using the origin id
                cursor = store.firstRivals[nextEdgeId];
                // sum the stepSize * offset from 0 at this level
                machineStep += stepSize * store.edges[cursor].startHeight;
                // the step size at each level is the product of the heights at all succeeding levels
                stepSize *= bigStepHeight;
            }
        }

        // the state in the onestep data must be committed to by the startHistoryRoot
        MerkleTreeLib.verifyInclusionProof(
            store.edges[edgeId].startHistoryRoot, oneStepData.beforeHash, machineStep, beforeHistoryInclusionProof
        );

        // execute the single step to produce the after state
        bytes32 afterHash =
            oneStepProofEntry.proveOneStep(execCtx, machineStep, oneStepData.beforeHash, oneStepData.proof);

        // check that the after state was indeed committed to by the endHistoryRoot
        MerkleTreeLib.verifyInclusionProof(
            store.edges[edgeId].endHistoryRoot, afterHash, machineStep + 1, afterHistoryInclusionProof
        );

        // also checks that no other rival has been confirmed
        setConfirmedRival(store, edgeId);

        // we also check the edge is pending in setConfirmed()
        store.edges[edgeId].setConfirmed();
        store.edges[edgeId].totalTimeUnrivaledCache = type(uint64).max;
    }

    function hasRival(EdgeStore storage store, bytes32 edgeId) internal view returns (bool) {
        if (!store.edges[edgeId].exists()) {
            revert EdgeNotExists(edgeId);
        }

        // rivals have the same mutual id
        bytes32 mutualId = store.edges[edgeId].mutualId();
        bytes32 firstRival = store.firstRivals[mutualId];
        // Sanity check: it should never be possible to create an edge without having an entry in firstRivals
        if (firstRival == 0) {
            revert EmptyFirstRival();
        }

        // can only have no rival if the firstRival is the UNRIVALED magic hash
        return firstRival != UNRIVALED;
    }

    function hasLengthOneRival(EdgeStore storage store, bytes32 edgeId) internal view returns (bool) {
        // must be length 1 and have rivals - all rivals have the same length
        return (hasRival(store, edgeId) && store.edges[edgeId].length() == 1);
    }

    function timeUnrivaled(EdgeStore storage store, bytes32 edgeId) internal view returns (uint256) {
        if (!store.edges[edgeId].exists()) {
            revert EdgeNotExists(edgeId);
        }

        bytes32 mutualId = store.edges[edgeId].mutualId();
        bytes32 firstRival = store.firstRivals[mutualId];
        // Sanity check: it's not possible to have a 0 first rival for an edge that exists
        if (firstRival == 0) {
            revert EmptyFirstRival();
        }

        // this edge has no rivals, the time is still going up
        // we give the current amount of time unrivaled
        if (firstRival == UNRIVALED) {
            return block.number - store.edges[edgeId].createdAtBlock;
        } else {
            // Sanity check: it's not possible an edge does not exist for a first rival record
            if (!store.edges[firstRival].exists()) {
                revert EdgeNotExists(firstRival);
            }

            // rivals exist for this edge
            uint256 firstRivalCreatedAtBlock = store.edges[firstRival].createdAtBlock;
            uint256 edgeCreatedAtBlock = store.edges[edgeId].createdAtBlock;
            if (firstRivalCreatedAtBlock > edgeCreatedAtBlock) {
                // if this edge was created before the first rival then we return the difference
                // in createdAtBlock number
                return firstRivalCreatedAtBlock - edgeCreatedAtBlock;
            } else {
                // if this was created at the same time as, or after the the first rival
                // then we return 0
                return 0;
            }
        }
    }

    function getPrevAssertionHash(EdgeStore storage store, bytes32 edgeId) internal view returns (bytes32) {
        ChallengeEdge storage edge = get(store, edgeId);
        while (edge.level > 0) {
            // the origin id gives us a link to the lower level
            // we know a first rival must exist, since otherwise we would not have had a one step fork
            // and we wouldnt be able to go to the next level
            // we can use the first rival to get an edge id, and from there get the next origin id
            bytes32 lowerLevelId = store.firstRivals[edge.originId];
            edge = get(store, lowerLevelId);
        }

        // For Block type edges the origin id is the assertion hash of claim prev
        return edge.originId;
    }

    function get(EdgeStore storage store, bytes32 edgeId) internal view returns (ChallengeEdge storage) {
        if (!store.edges[edgeId].exists()) {
            revert EdgeNotExists(edgeId);
        }
        return store.edges[edgeId];
    }

```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/challengeV2/libraries/EdgeChallengeManagerLib.sol#L141:146

```solidity
File: src/rollup/RollupCore.sol


    function validateAssertionHash(
        bytes32 assertionHash,
        AssertionState calldata state,
        bytes32 prevAssertionHash,
        bytes32 inboxAcc
    ) external pure {
        require(assertionHash == RollupLib.assertionHash(prevAssertionHash, state, inboxAcc), "INVALID_ASSERTION_HASH");
    }

    function validateConfig(bytes32 assertionHash, ConfigData calldata configData) external view {
        RollupLib.validateConfigHash(configData, getAssertionStorage(assertionHash).configHash);
    }

    function getFirstChildCreationBlock(bytes32 assertionHash) external view returns (uint64) {
        return getAssertionStorage(assertionHash).firstChildBlock;
    }

    function getSecondChildCreationBlock(bytes32 assertionHash) external view returns (uint64) {
        return getAssertionStorage(assertionHash).secondChildBlock;
    }

    function isFirstChild(bytes32 assertionHash) external view returns (bool) {
        return getAssertionStorage(assertionHash).isFirstChild;
    }

    function isPending(bytes32 assertionHash) external view returns (bool) {
        return getAssertionStorage(assertionHash).status == AssertionStatus.Pending;
    }

    function latestConfirmed() public view override returns (bytes32) {
        return _latestConfirmed;
    }

    function getStakerAddress(uint64 stakerNum) external view override returns (address) {
        return _stakerList[stakerNum];
    }

    function stakerCount() public view override returns (uint64) {
        return uint64(_stakerList.length);
    }

    function getStaker(address staker) external view override returns (Staker memory) {
        return _stakerMap[staker];
    }

    function sequencerInbox() public view virtual returns (ISequencerInbox) {
        return ISequencerInbox(bridge.sequencerInbox());
    }

    function genesisAssertionHash() external pure returns (bytes32) {
        GlobalState memory emptyGlobalState;
        AssertionState memory emptyAssertionState = AssertionState(emptyGlobalState, MachineStatus.FINISHED, bytes32(0));
        bytes32 parentAssertionHash = bytes32(0);
        bytes32 inboxAcc = bytes32(0);
        return RollupLib.assertionHash({
            parentAssertionHash: parentAssertionHash,
            afterState: emptyAssertionState,
            inboxAcc: inboxAcc
        });
    }

    function getAssertion(bytes32 assertionHash) public view override returns (AssertionNode memory) {
        return getAssertionStorage(assertionHash);
    }

    function getAssertionCreationBlockForLogLookup(bytes32 assertionHash) external view override returns (uint256) {
        if (_hostChainIsArbitrum) {
            uint256 blockNum = _assertionCreatedAtArbSysBlock[assertionHash];
            require(blockNum > 0, "NO_ASSERTION");
            return blockNum;
        } else {
            AssertionNode storage assertion = getAssertionStorage(assertionHash);
            assertion.requireExists();
            return assertion.createdAtBlock;
        }
    }

    function isStaked(address staker) public view override returns (bool) {
        return _stakerMap[staker].isStaked;
    }

    function latestStakedAssertion(address staker) public view override returns (bytes32) {
        return _stakerMap[staker].latestStakedAssertion;
    }

    function amountStaked(address staker) public view override returns (uint256) {
        return _stakerMap[staker].amountStaked;
    }

    function withdrawableFunds(address user) external view override returns (uint256) {
        return _withdrawableFunds[user];
    }

```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/rollup/RollupCore.sol#L207:209

</details>

## NC061 - It is standard for all external and public functions to be override from an interface:

This is to ensure the whole API is extracted in an interface


<details>
<summary>Click to show 12 findings</summary>

```solidity
File: src/assertionStakingPool/AssertionStakingPool.sol


40          function createAssertion(AssertionInputs calldata assertionInputs) external {
41              uint256 requiredStake = assertionInputs.beforeStateData.configData.requiredStake;
42              // approve spending from rollup for newStakeOnNewAssertion call
43              IERC20(stakeToken).safeIncreaseAllowance(rollup, requiredStake);
44              // reverts if pool doesn't have enough stake and if assertion has already been asserted
45              IRollupUser(rollup).newStakeOnNewAssertion(requiredStake, assertionInputs, assertionHash, address(this));
46          }
49          function makeStakeWithdrawable() public {
50              // this checks for active staker
51              IRollupUser(rollup).returnOldDeposit();
52          }
55          function withdrawStakeBackIntoPool() public {
56              IRollupUser(rollup).withdrawStakerFunds();
57          }
60          function makeStakeWithdrawableAndWithdrawBackIntoPool() external {
61              makeStakeWithdrawable();
62              withdrawStakeBackIntoPool();
63          }


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/assertionStakingPool/AssertionStakingPool.sol#L0:0

```solidity
File: src/assertionStakingPool/AssertionStakingPoolCreator.sol


15          function createPool(
16              address _rollup,
17              bytes32 _assertionHash
18          ) external returns (IAssertionStakingPool) {
19              AssertionStakingPool assertionPool = new AssertionStakingPool{salt: 0}(_rollup, _assertionHash);
20              emit NewAssertionPoolCreated(_rollup, _assertionHash, address(assertionPool));
21              return assertionPool;
22          }
25          function getPool(
26              address _rollup,
27              bytes32 _assertionHash
28          ) public view returns (IAssertionStakingPool) {
29              return IAssertionStakingPool(
30                  StakingPoolCreatorUtils.getPool(
31                      type(AssertionStakingPool).creationCode, 
32                      abi.encode(_rollup, _assertionHash)
33                  )
34              );
35          }


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/assertionStakingPool/AssertionStakingPoolCreator.sol#L0:0

```solidity
File: src/assertionStakingPool/EdgeStakingPool.sol


44          function createEdge(CreateEdgeArgs calldata args) external {
45              uint256 requiredStake = EdgeChallengeManager(challengeManager).stakeAmounts(args.level);
46              IERC20(stakeToken).safeIncreaseAllowance(address(challengeManager), requiredStake);
47              bytes32 newEdgeId = EdgeChallengeManager(challengeManager).createLayerZeroEdge(args);
48              if (newEdgeId != edgeId) {
49                  revert IncorrectEdgeId(newEdgeId, edgeId);
50              }
51          }


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/assertionStakingPool/EdgeStakingPool.sol#L0:0

```solidity
File: src/assertionStakingPool/EdgeStakingPoolCreator.sol


15          function createPool(
16              address challengeManager,
17              bytes32 edgeId
18          ) external returns (IEdgeStakingPool) {
19              EdgeStakingPool pool = new EdgeStakingPool{salt: 0}(challengeManager, edgeId);
20              emit NewEdgeStakingPoolCreated(challengeManager, edgeId);
21              return pool;
22          }
25          function getPool(
26              address challengeManager,
27              bytes32 edgeId
28          ) public view returns (IEdgeStakingPool) {
29              return IEdgeStakingPool(
30                  StakingPoolCreatorUtils.getPool(
31                      type(EdgeStakingPool).creationCode,
32                      abi.encode(challengeManager, edgeId)
33                  )
34              );
35          }


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/assertionStakingPool/EdgeStakingPoolCreator.sol#L0:0

```solidity
File: src/bridge/SequencerInbox.sol


161         function postUpgradeInit(BufferConfig memory bufferConfig_)
162             external
163             onlyDelegated
164             onlyProxyOwner
165         {
166             if (!isDelayBufferable) revert NotDelayBufferable();
167     
168             // Assuming we would not upgrade from a version that does not have the buffer initialized
169             // If that is the case, postUpgradeInit do not need to be called
170             if (buffer.bufferBlocks != 0) {
171                 revert AlreadyInit();
172             }
173     
174             _setBufferConfig(bufferConfig_);
175         }
177         function initialize(
178             IBridge bridge_,
179             ISequencerInbox.MaxTimeVariation calldata maxTimeVariation_,
180             BufferConfig memory bufferConfig_
181         ) external onlyDelegated {
182             if (bridge != IBridge(address(0))) revert AlreadyInit();
183             if (bridge_ == IBridge(address(0))) revert HadZeroInit();
184     
185             // Make sure logic contract was created by proper value for 'isUsingFeeToken'.
186             // Bridge in ETH based chains doesn't implement nativeToken(). In future it might implement it and return address(0)
187             bool actualIsUsingFeeToken = false;
188             try IERC20Bridge(address(bridge_)).nativeToken() returns (address feeToken) {
189                 if (feeToken != address(0)) {
190                     actualIsUsingFeeToken = true;
191                 }
192             } catch {}
193             if (isUsingFeeToken != actualIsUsingFeeToken) {
194                 revert NativeTokenMismatch();
195             }
196     
197             bridge = bridge_;
198             rollup = bridge_.rollup();
199     
200             _setMaxTimeVariation(maxTimeVariation_);
201     
202             if (isDelayBufferable) {
203                 _setBufferConfig(bufferConfig_);
204             }
205         }
208         function updateRollupAddress() external {
209             if (msg.sender != IOwnable(rollup).owner())
210                 revert NotOwner(msg.sender, IOwnable(rollup).owner());
211             IOwnable newRollup = bridge.rollup();
212             if (rollup == newRollup) revert RollupNotChanged();
213             rollup = newRollup;
214         }
236         function removeDelayAfterFork() external {
237             if (!_chainIdChanged()) revert NotForked();
238             delayBlocks = 1;
239             futureBlocks = 1;
240             delaySeconds = 1;
241             futureSeconds = 1;
242         }
244         function maxTimeVariation()
245             external
246             view
247             returns (
248                 uint256,
249                 uint256,
250                 uint256,
251                 uint256
252             )
253         {
254             (
255                 uint64 delayBlocks_,
256                 uint64 futureBlocks_,
257                 uint64 delaySeconds_,
258                 uint64 futureSeconds_
259             ) = maxTimeVariationInternal();
260     
261             return (
262                 uint256(delayBlocks_),
263                 uint256(futureBlocks_),
264                 uint256(delaySeconds_),
265                 uint256(futureSeconds_)
266             );
267         }
287         function forceInclusion(
288             uint256 _totalDelayedMessagesRead,
289             uint8 kind,
290             uint64[2] calldata l1BlockAndTime,
291             uint256 baseFeeL1,
292             address sender,
293             bytes32 messageDataHash
294         ) external {
295             if (_totalDelayedMessagesRead <= totalDelayedMessagesRead) revert DelayedBackwards();
296             bytes32 messageHash = Messages.messageHash(
297                 kind,
298                 sender,
299                 l1BlockAndTime[0],
300                 l1BlockAndTime[1],
301                 _totalDelayedMessagesRead - 1,
302                 baseFeeL1,
303                 messageDataHash
304             );
305     
306             uint256 delayBlocks_ = delayBlocks;
307     
308             if (isDelayBufferable) {
309                 // proactively apply any pending delay buffer updates before the force included message l1BlockAndTime
310                 buffer.update(l1BlockAndTime[0]);
311                 delayBlocks_ = delayBufferableBlocks(buffer.bufferBlocks);
312             }
313             // Can only force-include after the Sequencer-only window has expired.
314             if (l1BlockAndTime[0] + delayBlocks_ >= block.number) revert ForceIncludeBlockTooSoon();
315     
316             // Verify that message hash represents the last message sequence of delayed message to be included
317             bytes32 prevDelayedAcc = 0;
318             if (_totalDelayedMessagesRead > 1) {
319                 prevDelayedAcc = bridge.delayedInboxAccs(_totalDelayedMessagesRead - 2);
320             }
321             if (
322                 bridge.delayedInboxAccs(_totalDelayedMessagesRead - 1) !=
323                 Messages.accumulateInboxMessage(prevDelayedAcc, messageHash)
324             ) revert IncorrectMessagePreimage();
325     
326             (bytes32 dataHash, IBridge.TimeBounds memory timeBounds) = formEmptyDataHash(
327                 _totalDelayedMessagesRead
328             );
329             uint256 __totalDelayedMessagesRead = _totalDelayedMessagesRead;
330             uint256 prevSeqMsgCount = bridge.sequencerReportedSubMessageCount();
331             uint256 newSeqMsgCount = prevSeqMsgCount; // force inclusion should not modify sequencer message count
332             (
333                 uint256 seqMessageIndex,
334                 bytes32 beforeAcc,
335                 bytes32 delayedAcc,
336                 bytes32 afterAcc
337             ) = addSequencerL2BatchImpl(
338                     dataHash,
339                     __totalDelayedMessagesRead,
340                     0,
341                     prevSeqMsgCount,
342                     newSeqMsgCount
343                 );
344             emit SequencerBatchDelivered(
345                 seqMessageIndex,
346                 beforeAcc,
347                 afterAcc,
348                 delayedAcc,
349                 totalDelayedMessagesRead,
350                 timeBounds,
351                 IBridge.BatchDataLocation.NoData
352             );
353         }
356         function addSequencerL2BatchFromOrigin(
357             uint256,
358             bytes calldata,
359             uint256,
360             IGasRefunder
361         ) external pure {
362             revert Deprecated();
363         }
366         function addSequencerL2BatchFromOrigin(
367             uint256 sequenceNumber,
368             bytes calldata data,
369             uint256 afterDelayedMessagesRead,
370             IGasRefunder gasRefunder,
371             uint256 prevMessageCount,
372             uint256 newMessageCount
373         ) external refundsGas(gasRefunder, IReader4844(address(0))) {
374             // solhint-disable-next-line avoid-tx-origin
375             if (msg.sender != tx.origin) revert NotOrigin();
376             if (!isBatchPoster[msg.sender]) revert NotBatchPoster();
377             if (isDelayProofRequired(afterDelayedMessagesRead)) revert DelayProofRequired();
378     
379             addSequencerL2BatchFromCalldataImpl(
380                 sequenceNumber,
381                 data,
382                 afterDelayedMessagesRead,
383                 prevMessageCount,
384                 newMessageCount,
385                 true
386             );
387         }
390         function addSequencerL2BatchFromBlobs(
391             uint256 sequenceNumber,
392             uint256 afterDelayedMessagesRead,
393             IGasRefunder gasRefunder,
394             uint256 prevMessageCount,
395             uint256 newMessageCount
396         ) external refundsGas(gasRefunder, reader4844) {
397             if (!isBatchPoster[msg.sender]) revert NotBatchPoster();
398             if (isDelayProofRequired(afterDelayedMessagesRead)) revert DelayProofRequired();
399     
400             addSequencerL2BatchFromBlobsImpl(
401                 sequenceNumber,
402                 afterDelayedMessagesRead,
403                 prevMessageCount,
404                 newMessageCount
405             );
406         }
409         function addSequencerL2BatchFromBlobsDelayProof(
410             uint256 sequenceNumber,
411             uint256 afterDelayedMessagesRead,
412             IGasRefunder gasRefunder,
413             uint256 prevMessageCount,
414             uint256 newMessageCount,
415             DelayProof calldata delayProof
416         ) external refundsGas(gasRefunder, reader4844) {
417             if (!isBatchPoster[msg.sender]) revert NotBatchPoster();
418             if (!isDelayBufferable) revert NotDelayBufferable();
419     
420             delayProofImpl(afterDelayedMessagesRead, delayProof);
421             addSequencerL2BatchFromBlobsImpl(
422                 sequenceNumber,
423                 afterDelayedMessagesRead,
424                 prevMessageCount,
425                 newMessageCount
426             );
427         }
430         function addSequencerL2BatchFromOriginDelayProof(
431             uint256 sequenceNumber,
432             bytes calldata data,
433             uint256 afterDelayedMessagesRead,
434             IGasRefunder gasRefunder,
435             uint256 prevMessageCount,
436             uint256 newMessageCount,
437             DelayProof calldata delayProof
438         ) external refundsGas(gasRefunder, IReader4844(address(0))) {
439             // solhint-disable-next-line avoid-tx-origin
440             if (msg.sender != tx.origin) revert NotOrigin();
441             if (!isBatchPoster[msg.sender]) revert NotBatchPoster();
442             if (!isDelayBufferable) revert NotDelayBufferable();
443     
444             delayProofImpl(afterDelayedMessagesRead, delayProof);
445             addSequencerL2BatchFromCalldataImpl(
446                 sequenceNumber,
447                 data,
448                 afterDelayedMessagesRead,
449                 prevMessageCount,
450                 newMessageCount,
451                 true
452             );
453         }
560         function addSequencerL2Batch(
561             uint256 sequenceNumber,
562             bytes calldata data,
563             uint256 afterDelayedMessagesRead,
564             IGasRefunder gasRefunder,
565             uint256 prevMessageCount,
566             uint256 newMessageCount
567         ) external override refundsGas(gasRefunder, IReader4844(address(0))) {
568             if (!isBatchPoster[msg.sender] && msg.sender != address(rollup)) revert NotBatchPoster();
569             if (isDelayProofRequired(afterDelayedMessagesRead)) revert DelayProofRequired();
570     
571             addSequencerL2BatchFromCalldataImpl(
572                 sequenceNumber,
573                 data,
574                 afterDelayedMessagesRead,
575                 prevMessageCount,
576                 newMessageCount,
577                 false
578             );
579         }
582         function addSequencerL2BatchDelayProof(
583             uint256 sequenceNumber,
584             bytes calldata data,
585             uint256 afterDelayedMessagesRead,
586             IGasRefunder gasRefunder,
587             uint256 prevMessageCount,
588             uint256 newMessageCount,
589             DelayProof calldata delayProof
590         ) external refundsGas(gasRefunder, IReader4844(address(0))) {
591             if (!isBatchPoster[msg.sender] && msg.sender != address(rollup)) revert NotBatchPoster();
592             if (!isDelayBufferable) revert NotDelayBufferable();
593     
594             delayProofImpl(afterDelayedMessagesRead, delayProof);
595             addSequencerL2BatchFromCalldataImpl(
596                 sequenceNumber,
597                 data,
598                 afterDelayedMessagesRead,
599                 prevMessageCount,
600                 newMessageCount,
601                 false
602             );
603         }
824         function inboxAccs(uint256 index) external view returns (bytes32) {
825             return bridge.sequencerInboxAccs(index);
826         }
828         function batchCount() external view returns (uint256) {
829             return bridge.sequencerMessageCount();
830         }
833         function forceInclusionDeadline(uint64 blockNumber) external view returns (uint64) {
834             uint64 _delayBlocks = delayBlocks;
835             if (isDelayBufferable) {
836                 uint64 _buffer = buffer.calcPendingBuffer(blockNumber);
837                 _delayBlocks = delayBufferableBlocks(_buffer);
838             }
839             return blockNumber + _delayBlocks;
840         }
885         function setMaxTimeVariation(ISequencerInbox.MaxTimeVariation memory maxTimeVariation_)
886             external
887             onlyRollupOwner
888         {
889             _setMaxTimeVariation(maxTimeVariation_);
890             emit OwnerFunctionCalled(0);
891         }
894         function setIsBatchPoster(address addr, bool isBatchPoster_)
895             external
896             onlyRollupOwnerOrBatchPosterManager
897         {
898             isBatchPoster[addr] = isBatchPoster_;
899             emit OwnerFunctionCalled(1);
900         }
903         function setValidKeyset(bytes calldata keysetBytes) external onlyRollupOwner {
904             uint256 ksWord = uint256(keccak256(bytes.concat(hex"fe", keccak256(keysetBytes))));
905             bytes32 ksHash = bytes32(ksWord ^ (1 << 255));
906             if (keysetBytes.length >= 64 * 1024) revert KeysetTooLarge();
907     
908             if (dasKeySetInfo[ksHash].isValidKeyset) revert AlreadyValidDASKeyset(ksHash);
909             uint256 creationBlock = block.number;
910             if (hostChainIsArbitrum) {
911                 creationBlock = ArbSys(address(100)).arbBlockNumber();
912             }
913             dasKeySetInfo[ksHash] = DasKeySetInfo({
914                 isValidKeyset: true,
915                 creationBlock: uint64(creationBlock)
916             });
917             emit SetValidKeyset(ksHash, keysetBytes);
918             emit OwnerFunctionCalled(2);
919         }
922         function invalidateKeysetHash(bytes32 ksHash) external onlyRollupOwner {
923             if (!dasKeySetInfo[ksHash].isValidKeyset) revert NoSuchKeyset(ksHash);
924             // we don't delete the block creation value since its used to fetch the SetValidKeyset
925             // event efficiently. The event provides the hash preimage of the key.
926             // this is still needed when syncing the chain after a keyset is invalidated.
927             dasKeySetInfo[ksHash].isValidKeyset = false;
928             emit InvalidateKeyset(ksHash);
929             emit OwnerFunctionCalled(3);
930         }
933         function setIsSequencer(address addr, bool isSequencer_)
934             external
935             onlyRollupOwnerOrBatchPosterManager
936         {
937             isSequencer[addr] = isSequencer_;
938             emit OwnerFunctionCalled(4); // Owner in this context can also be batch poster manager
939         }
942         function setBatchPosterManager(address newBatchPosterManager) external onlyRollupOwner {
943             batchPosterManager = newBatchPosterManager;
944             emit OwnerFunctionCalled(5);
945         }
947         function setBufferConfig(BufferConfig memory bufferConfig_) external onlyRollupOwner {
948             _setBufferConfig(bufferConfig_);
949             emit OwnerFunctionCalled(6);
950         }
952         function isValidKeysetHash(bytes32 ksHash) external view returns (bool) {
953             return dasKeySetInfo[ksHash].isValidKeyset;
954         }
957         function getKeysetCreationBlock(bytes32 ksHash) external view returns (uint256) {
958             DasKeySetInfo memory ksInfo = dasKeySetInfo[ksHash];
959             if (ksInfo.creationBlock == 0) revert NoSuchKeyset(ksHash);
960             return uint256(ksInfo.creationBlock);
961         }


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/bridge/SequencerInbox.sol#L0:0

```solidity
File: src/challengeV2/EdgeChallengeManager.sol


305         function initialize(
306             IAssertionChain _assertionChain,
307             uint64 _challengePeriodBlocks,
308             IOneStepProofEntry _oneStepProofEntry,
309             uint256 layerZeroBlockEdgeHeight,
310             uint256 layerZeroBigStepEdgeHeight,
311             uint256 layerZeroSmallStepEdgeHeight,
312             IERC20 _stakeToken,
313             address _excessStakeReceiver,
314             uint8 _numBigStepLevel,
315             uint256[] calldata _stakeAmounts
316         ) public initializer {
317             if (address(_assertionChain) == address(0)) {
318                 revert EmptyAssertionChain();
319             }
320             assertionChain = _assertionChain;
321             if (address(_oneStepProofEntry) == address(0)) {
322                 revert EmptyOneStepProofEntry();
323             }
324             oneStepProofEntry = _oneStepProofEntry;
325             if (_challengePeriodBlocks == 0) {
326                 revert EmptyChallengePeriod();
327             }
328             challengePeriodBlocks = _challengePeriodBlocks;
329     
330             stakeToken = _stakeToken;
331             if (_excessStakeReceiver == address(0)) {
332                 revert EmptyStakeReceiver();
333             }
334             excessStakeReceiver = _excessStakeReceiver;
335     
336             if (!EdgeChallengeManagerLib.isPowerOfTwo(layerZeroBlockEdgeHeight)) {
337                 revert NotPowerOfTwo(layerZeroBlockEdgeHeight);
338             }
339             LAYERZERO_BLOCKEDGE_HEIGHT = layerZeroBlockEdgeHeight;
340             if (!EdgeChallengeManagerLib.isPowerOfTwo(layerZeroBigStepEdgeHeight)) {
341                 revert NotPowerOfTwo(layerZeroBigStepEdgeHeight);
342             }
343             LAYERZERO_BIGSTEPEDGE_HEIGHT = layerZeroBigStepEdgeHeight;
344             if (!EdgeChallengeManagerLib.isPowerOfTwo(layerZeroSmallStepEdgeHeight)) {
345                 revert NotPowerOfTwo(layerZeroSmallStepEdgeHeight);
346             }
347             LAYERZERO_SMALLSTEPEDGE_HEIGHT = layerZeroSmallStepEdgeHeight;
348     
349             // ensure that there is at least on of each type of level
350             if (_numBigStepLevel == 0) {
351                 revert ZeroBigStepLevels();
352             }
353             // ensure there's also space for the block level and the small step level
354             // in total level parameters
355             if (_numBigStepLevel > 253) {
356                 revert BigStepLevelsTooMany(_numBigStepLevel);
357             }
358             NUM_BIGSTEP_LEVEL = _numBigStepLevel;
359     
360             if (_numBigStepLevel + 2 != _stakeAmounts.length) {
361                 revert StakeAmountsMismatch(_stakeAmounts.length, _numBigStepLevel + 2);
362             }
363             stakeAmounts = _stakeAmounts;
364         }
371         function createLayerZeroEdge(CreateEdgeArgs calldata args) external returns (bytes32) {
372             // Check if whitelist is enabled in the Rollup
373             // We only enforce whitelist in this function as it may exhaust resources
374             bool whitelistEnabled = !assertionChain.validatorWhitelistDisabled();
375     
376             if (whitelistEnabled && !assertionChain.isValidator(msg.sender)) {
377                 revert NotValidator(msg.sender);
378             }
379     
380             EdgeAddedData memory edgeAdded;
381             EdgeType eType = ChallengeEdgeLib.levelToType(args.level, NUM_BIGSTEP_LEVEL);
382             uint256 expectedEndHeight = getLayerZeroEndHeight(eType);
383             AssertionReferenceData memory ard;
384     
385             if (eType == EdgeType.Block) {
386                 // for block type edges we need to provide some extra assertion data context
387                 if (args.proof.length == 0) {
388                     revert EmptyEdgeSpecificProof();
389                 }
390                 (, AssertionStateData memory predecessorStateData, AssertionStateData memory claimStateData) =
391                     abi.decode(args.proof, (bytes32[], AssertionStateData, AssertionStateData));
392     
393                 assertionChain.validateAssertionHash(
394                     args.claimId, claimStateData.assertionState, claimStateData.prevAssertionHash, claimStateData.inboxAcc
395                 );
396     
397                 assertionChain.validateAssertionHash(
398                     claimStateData.prevAssertionHash,
399                     predecessorStateData.assertionState,
400                     predecessorStateData.prevAssertionHash,
401                     predecessorStateData.inboxAcc
402                 );
403     
404                 if (args.endHistoryRoot != claimStateData.assertionState.endHistoryRoot) {
405                     revert EndHistoryRootMismatch(args.endHistoryRoot, claimStateData.assertionState.endHistoryRoot);
406                 }
407     
408                 ard = AssertionReferenceData(
409                     args.claimId,
410                     claimStateData.prevAssertionHash,
411                     assertionChain.isPending(args.claimId),
412                     assertionChain.getSecondChildCreationBlock(claimStateData.prevAssertionHash) > 0,
413                     predecessorStateData.assertionState,
414                     claimStateData.assertionState
415                 );
416             }
417             edgeAdded = store.createLayerZeroEdge(
418                 args, ard, oneStepProofEntry, expectedEndHeight, NUM_BIGSTEP_LEVEL, whitelistEnabled
419             );
420     
421             IERC20 st = stakeToken;
422             uint256 sa = stakeAmounts[args.level];
423             // when a zero layer edge is created it must include stake amount. Each time a zero layer
424             // edge is created it forces the honest participants to do some work, so we want to disincentive
425             // their creation. The amount should also be enough to pay for the gas costs incurred by the honest
426             // participant. This can be arranged out of bound by the excess stake receiver.
427             // The contract initializer can disable staking by setting zeros for token or amount, to change
428             // this a new challenge manager needs to be deployed and its address updated in the assertion chain
429             if (address(st) != address(0) && sa != 0) {
430                 // since only one edge in a group of rivals can ever be confirmed, we know that we
431                 // will never need to refund more than one edge. Therefore we can immediately send
432                 // all stakes provided after the first one to an excess stake receiver.
433                 address receiver = edgeAdded.hasRival ? excessStakeReceiver : address(this);
434                 st.safeTransferFrom(msg.sender, receiver, sa);
435             }
436     
437             emit EdgeAdded(
438                 edgeAdded.edgeId,
439                 edgeAdded.mutualId,
440                 edgeAdded.originId,
441                 edgeAdded.claimId,
442                 edgeAdded.length,
443                 edgeAdded.level,
444                 edgeAdded.hasRival,
445                 edgeAdded.isLayerZero
446             );
447             return edgeAdded.edgeId;
448         }
451         function bisectEdge(bytes32 edgeId, bytes32 bisectionHistoryRoot, bytes calldata prefixProof)
452             external
453             returns (bytes32, bytes32)
454         {
455             (bytes32 lowerChildId, EdgeAddedData memory lowerChildAdded, EdgeAddedData memory upperChildAdded) =
456                 store.bisectEdge(edgeId, bisectionHistoryRoot, prefixProof);
457     
458             bool lowerChildAlreadyExists = lowerChildAdded.edgeId == 0;
459             // the lower child might already exist, if it didnt then a new
460             // edge was added
461             if (!lowerChildAlreadyExists) {
462                 emit EdgeAdded(
463                     lowerChildAdded.edgeId,
464                     lowerChildAdded.mutualId,
465                     lowerChildAdded.originId,
466                     lowerChildAdded.claimId,
467                     lowerChildAdded.length,
468                     lowerChildAdded.level,
469                     lowerChildAdded.hasRival,
470                     lowerChildAdded.isLayerZero
471                 );
472             }
473             // upper child is always added
474             emit EdgeAdded(
475                 upperChildAdded.edgeId,
476                 upperChildAdded.mutualId,
477                 upperChildAdded.originId,
478                 upperChildAdded.claimId,
479                 upperChildAdded.length,
480                 upperChildAdded.level,
481                 upperChildAdded.hasRival,
482                 upperChildAdded.isLayerZero
483             );
484     
485             emit EdgeBisected(edgeId, lowerChildId, upperChildAdded.edgeId, lowerChildAlreadyExists);
486     
487             return (lowerChildId, upperChildAdded.edgeId);
488         }
491         function multiUpdateTimeCacheByChildren(bytes32[] calldata edgeIds) public {
492             for (uint256 i = 0; i < edgeIds.length; i++) {
493                 (bool updated, uint256 newValue) = store.updateTimerCacheByChildren(edgeIds[i]);
494                 if (updated) emit TimerCacheUpdated(edgeIds[i], newValue);
495             }
496         }
499         function updateTimerCacheByChildren(bytes32 edgeId) public {
500             (bool updated, uint256 newValue) = store.updateTimerCacheByChildren(edgeId);
501             if (updated) emit TimerCacheUpdated(edgeId, newValue);
502         }
505         function updateTimerCacheByClaim(bytes32 edgeId, bytes32 claimingEdgeId) public {
506             (bool updated, uint256 newValue) = store.updateTimerCacheByClaim(edgeId, claimingEdgeId, NUM_BIGSTEP_LEVEL);
507             if (updated) emit TimerCacheUpdated(edgeId, newValue);
508         }
511         function confirmEdgeByTime(bytes32 edgeId, AssertionStateData calldata claimStateData) public {
512             ChallengeEdge storage topEdge = store.get(edgeId);
513             if (!topEdge.isLayerZero()) {
514                 revert EdgeNotLayerZero(topEdge.id(), topEdge.staker, topEdge.claimId);
515             }
516     
517             uint64 assertionBlocks = 0;
518             // if the edge is block level and the assertion being claimed against was the first child of its predecessor
519             // then we are able to count the time between the first and second child as time towards
520             // the this edge
521             bool isBlockLevel = ChallengeEdgeLib.levelToType(topEdge.level, NUM_BIGSTEP_LEVEL) == EdgeType.Block;
522             if (isBlockLevel && assertionChain.isFirstChild(topEdge.claimId)) {
523                 assertionChain.validateAssertionHash(
524                     topEdge.claimId,
525                     claimStateData.assertionState,
526                     claimStateData.prevAssertionHash,
527                     claimStateData.inboxAcc
528                 );
529                 assertionBlocks = assertionChain.getSecondChildCreationBlock(claimStateData.prevAssertionHash)
530                     - assertionChain.getFirstChildCreationBlock(claimStateData.prevAssertionHash);
531             }
532     
533             uint256 totalTimeUnrivaled = store.confirmEdgeByTime(edgeId, assertionBlocks, challengePeriodBlocks);
534     
535             emit EdgeConfirmedByTime(edgeId, store.edges[edgeId].mutualId(), totalTimeUnrivaled);
536         }
539         function confirmEdgeByOneStepProof(
540             bytes32 edgeId,
541             OneStepData calldata oneStepData,
542             ConfigData calldata prevConfig,
543             bytes32[] calldata beforeHistoryInclusionProof,
544             bytes32[] calldata afterHistoryInclusionProof
545         ) public {
546             bytes32 prevAssertionHash = store.getPrevAssertionHash(edgeId);
547     
548             assertionChain.validateConfig(prevAssertionHash, prevConfig);
549     
550             ExecutionContext memory execCtx = ExecutionContext({
551                 maxInboxMessagesRead: prevConfig.nextInboxPosition,
552                 bridge: assertionChain.bridge(),
553                 initialWasmModuleRoot: prevConfig.wasmModuleRoot
554             });
555     
556             store.confirmEdgeByOneStepProof(
557                 edgeId,
558                 oneStepProofEntry,
559                 oneStepData,
560                 execCtx,
561                 beforeHistoryInclusionProof,
562                 afterHistoryInclusionProof,
563                 NUM_BIGSTEP_LEVEL,
564                 LAYERZERO_BIGSTEPEDGE_HEIGHT,
565                 LAYERZERO_SMALLSTEPEDGE_HEIGHT
566             );
567     
568             emit EdgeConfirmedByOneStepProof(edgeId, store.edges[edgeId].mutualId());
569         }
572         function refundStake(bytes32 edgeId) public {
573             ChallengeEdge storage edge = store.get(edgeId);
574             // setting refunded also do checks that the edge cannot be refunded twice
575             edge.setRefunded();
576     
577             IERC20 st = stakeToken;
578             uint256 sa = stakeAmounts[edge.level];
579             // no need to refund with the token or amount where zero'd out
580             if (address(st) != address(0) && sa != 0) {
581                 st.safeTransfer(edge.staker, sa);
582             }
583     
584             emit EdgeRefunded(edgeId, store.edges[edgeId].mutualId(), address(st), sa);
585         }
591         function getLayerZeroEndHeight(EdgeType eType) public view returns (uint256) {
592             if (eType == EdgeType.Block) {
593                 return LAYERZERO_BLOCKEDGE_HEIGHT;
594             } else if (eType == EdgeType.BigStep) {
595                 return LAYERZERO_BIGSTEPEDGE_HEIGHT;
596             } else if (eType == EdgeType.SmallStep) {
597                 return LAYERZERO_SMALLSTEPEDGE_HEIGHT;
598             } else {
599                 revert InvalidEdgeType(eType);
600             }
601         }
604         function calculateEdgeId(
605             uint8 level,
606             bytes32 originId,
607             uint256 startHeight,
608             bytes32 startHistoryRoot,
609             uint256 endHeight,
610             bytes32 endHistoryRoot
611         ) public pure returns (bytes32) {
612             return ChallengeEdgeLib.idComponent(level, originId, startHeight, startHistoryRoot, endHeight, endHistoryRoot);
613         }
616         function calculateMutualId(
617             uint8 level,
618             bytes32 originId,
619             uint256 startHeight,
620             bytes32 startHistoryRoot,
621             uint256 endHeight
622         ) public pure returns (bytes32) {
623             return ChallengeEdgeLib.mutualIdComponent(level, originId, startHeight, startHistoryRoot, endHeight);
624         }
627         function edgeExists(bytes32 edgeId) public view returns (bool) {
628             return store.edges[edgeId].exists();
629         }
632         function getEdge(bytes32 edgeId) public view returns (ChallengeEdge memory) {
633             return store.get(edgeId);
634         }
637         function edgeLength(bytes32 edgeId) public view returns (uint256) {
638             return store.get(edgeId).length();
639         }
642         function hasRival(bytes32 edgeId) public view returns (bool) {
643             return store.hasRival(edgeId);
644         }
647         function confirmedRival(bytes32 mutualId) public view returns (bytes32) {
648             return store.confirmedRivals[mutualId];
649         }
652         function hasLengthOneRival(bytes32 edgeId) public view returns (bool) {
653             return store.hasLengthOneRival(edgeId);
654         }
657         function timeUnrivaled(bytes32 edgeId) public view returns (uint256) {
658             return store.timeUnrivaled(edgeId);
659         }
662         function getPrevAssertionHash(bytes32 edgeId) public view returns (bytes32) {
663             return store.getPrevAssertionHash(edgeId);
664         }
667         function firstRival(bytes32 mutualId) public view returns (bytes32) {
668             return store.firstRivals[mutualId];
669         }
672         function hasMadeLayerZeroRival(address account, bytes32 mutualId) external view returns (bool) {
673             return store.hasMadeLayerZeroRival[account][mutualId];
674         }


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/challengeV2/EdgeChallengeManager.sol#L0:0

```solidity
File: src/rollup/BOLDUpgradeAction.sol


101         function stateHash(ExecutionState calldata executionState, uint256 inboxMaxCount) public pure returns (bytes32) {
102             return
103                 keccak256(abi.encodePacked(executionState.globalState.hash(), inboxMaxCount, executionState.machineStatus));
104         }
106         function set(bytes32 h, ExecutionState calldata executionState, uint256 inboxMaxCount) public {
107             require(h == stateHash(executionState, inboxMaxCount), "Invalid hash");
108             preImages[h] = abi.encode(executionState, inboxMaxCount);
109             emit HashSet(h, executionState, inboxMaxCount);
110         }
112         function get(bytes32 h) public view returns (ExecutionState memory executionState, uint256 inboxMaxCount) {
113             (executionState, inboxMaxCount) = abi.decode(preImages[h], (ExecutionState, uint256));
114             require(inboxMaxCount != 0, "Hash not yet set");
115         }
130         function wasmModuleRoot() external view returns (bytes32) {
131             return rollup.wasmModuleRoot();
132         }
134         function latestConfirmed() external view returns (uint64) {
135             return rollup.latestConfirmed();
136         }
138         function getNode(uint64 nodeNum) external view returns (Node memory) {
139             return rollup.getNode(nodeNum);
140         }
142         function getStakerAddress(uint64 stakerNum) external view returns (address) {
143             return rollup.getStakerAddress(stakerNum);
144         }
146         function stakerCount() external view returns (uint64) {
147             return rollup.stakerCount();
148         }
150         function getStaker(address staker) external view returns (OldStaker memory) {
151             return rollup.getStaker(staker);
152         }
154         function isValidator(address validator) external view returns (bool) {
155             return rollup.isValidator(validator);
156         }
158         function validatorWalletCreator() external view returns (address) {
159             return rollup.validatorWalletCreator();
160         }
173         function array() public view returns (uint256[] memory) {
174             return _array;
175         }
464         function perform(address[] memory validators) external {
465             // tidy up the old rollup - pause it and refund stakes
466             cleanupOldRollup();
467     
468             // create the config, we do this now so that we compute the expected rollup address
469             Config memory config = createConfig();
470     
471             // deploy the new challenge manager
472             IEdgeChallengeManager challengeManager = IEdgeChallengeManager(
473                 address(
474                     new TransparentUpgradeableProxy(
475                         address(IMPL_CHALLENGE_MANAGER),
476                         address(PROXY_ADMIN_BRIDGE), // use the same proxy admin as the bridge
477                         ""
478                     )
479                 )
480             );
481     
482             // now that all the dependent contracts are pointed at the new address we can
483             // deploy and init the new rollup
484             ContractDependencies memory connectedContracts = ContractDependencies({
485                 bridge: IBridge(BRIDGE),
486                 sequencerInbox: ISequencerInbox(SEQ_INBOX),
487                 inbox: IInboxBase(INBOX),
488                 outbox: IOutbox(OUTBOX),
489                 rollupEventInbox: IRollupEventInbox(REI),
490                 challengeManager: challengeManager,
491                 rollupAdminLogic: IMPL_NEW_ROLLUP_ADMIN,
492                 rollupUserLogic: IRollupUser(IMPL_NEW_ROLLUP_USER),
493                 validatorWalletCreator: ROLLUP_READER.validatorWalletCreator()
494             });
495     
496             // upgrade the surrounding contracts eg bridge, outbox, seq inbox, rollup event inbox
497             // to set of the new rollup address
498             bytes32 rollupSalt = keccak256(abi.encode(config));
499             address expectedRollupAddress =
500                 Create2Upgradeable.computeAddress(rollupSalt, keccak256(type(RollupProxy).creationCode));
501             upgradeSurroundingContracts(expectedRollupAddress);
502     
503             challengeManager.initialize({
504                 _assertionChain: IAssertionChain(expectedRollupAddress),
505                 _challengePeriodBlocks: CHALLENGE_PERIOD_BLOCKS,
506                 _oneStepProofEntry: OSP,
507                 layerZeroBlockEdgeHeight: config.layerZeroBlockEdgeHeight,
508                 layerZeroBigStepEdgeHeight: config.layerZeroBigStepEdgeHeight,
509                 layerZeroSmallStepEdgeHeight: config.layerZeroSmallStepEdgeHeight,
510                 _stakeToken: IERC20(config.stakeToken),
511                 _stakeAmounts: config.miniStakeValues,
512                 _excessStakeReceiver: L1_TIMELOCK,
513                 _numBigStepLevel: config.numBigStepLevel
514             });
515     
516             RollupProxy rollup = new RollupProxy{salt: rollupSalt}();
517             require(address(rollup) == expectedRollupAddress, "UNEXPCTED_ROLLUP_ADDR");
518     
519             // initialize the rollup with this contract as owner to set batch poster and validators
520             // it will transfer the ownership back to the actual owner later
521             address actualOwner = config.owner;
522             config.owner = address(this);
523     
524             rollup.initializeProxy(config, connectedContracts);
525     
526             if (validators.length != 0) {
527                 bool[] memory _vals = new bool[](validators.length);
528                 for (uint256 i = 0; i < validators.length; i++) {
529                     require(ROLLUP_READER.isValidator(validators[i]), "UNEXPECTED_NEW_VALIDATOR");
530                     _vals[i] = true;
531                 }
532                 IRollupAdmin(address(rollup)).setValidator(validators, _vals);
533             }
534             if (DISABLE_VALIDATOR_WHITELIST) {
535                 IRollupAdmin(address(rollup)).setValidatorWhitelistDisabled(DISABLE_VALIDATOR_WHITELIST);
536             }
537     
538             IRollupAdmin(address(rollup)).setOwner(actualOwner);
539     
540             emit RollupMigrated(expectedRollupAddress, address(challengeManager));
541         }


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/rollup/BOLDUpgradeAction.sol#L0:0

```solidity
File: src/rollup/BridgeCreator.sol


53          function updateTemplates(BridgeTemplates calldata _newTemplates) external onlyOwner {
54              ethBasedTemplates = _newTemplates;
55              emit TemplatesUpdated();
56          }
58          function updateERC20Templates(BridgeTemplates calldata _newTemplates) external onlyOwner {
59              erc20BasedTemplates = _newTemplates;
60              emit ERC20TemplatesUpdated();
61          }
99          function createBridge(
100             address adminProxy,
101             address rollup,
102             address nativeToken,
103             ISequencerInbox.MaxTimeVariation calldata maxTimeVariation,
104             BufferConfig calldata bufferConfig
105         ) external returns (BridgeContracts memory) {
106             // create delay bufferable sequencer inbox if threshold is non-zero
107             bool isDelayBufferable = bufferConfig.threshold != 0;
108     
109             // create ETH-based bridge if address zero is provided for native token, otherwise create ERC20-based bridge
110             BridgeContracts memory frame = _createBridge(
111                 adminProxy,
112                 nativeToken == address(0) ? ethBasedTemplates : erc20BasedTemplates,
113                 isDelayBufferable
114             );
115     
116             // init contracts
117             if (nativeToken == address(0)) {
118                 IEthBridge(address(frame.bridge)).initialize(IOwnable(rollup));
119             } else {
120                 IERC20Bridge(address(frame.bridge)).initialize(IOwnable(rollup), nativeToken);
121             }
122             frame.sequencerInbox.initialize(IBridge(frame.bridge), maxTimeVariation, bufferConfig);
123             frame.inbox.initialize(frame.bridge, frame.sequencerInbox);
124             frame.rollupEventInbox.initialize(frame.bridge);
125             frame.outbox.initialize(frame.bridge);
126     
127             return frame;
128         }


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/rollup/BridgeCreator.sol#L0:0

```solidity
File: src/rollup/RollupAdminLogic.sol


18          function initialize(Config calldata config, ContractDependencies calldata connectedContracts)
19              external
20              override
21              onlyProxy
22              initializer
23          {
24              rollupDeploymentBlock = block.number;
25              bridge = connectedContracts.bridge;
26              connectedContracts.bridge.setDelayedInbox(address(connectedContracts.inbox), true);
27              connectedContracts.bridge.setSequencerInbox(address(connectedContracts.sequencerInbox));
28      
29              inbox = connectedContracts.inbox;
30              outbox = connectedContracts.outbox;
31              connectedContracts.bridge.setOutbox(address(connectedContracts.outbox), true);
32              rollupEventInbox = connectedContracts.rollupEventInbox;
33      
34              // dont need to connect and initialize the event inbox if it's already been initialized
35              if (!bridge.allowedDelayedInboxes(address(connectedContracts.rollupEventInbox))) {
36                  connectedContracts.bridge.setDelayedInbox(address(connectedContracts.rollupEventInbox), true);
37                  connectedContracts.rollupEventInbox.rollupInitialized(config.chainId, config.chainConfig);
38              }
39      
40              if (connectedContracts.sequencerInbox.totalDelayedMessagesRead() == 0) {
41                  connectedContracts.sequencerInbox.addSequencerL2Batch(0, "", 1, IGasRefunder(address(0)), 0, 1);
42              }
43      
44              validatorWalletCreator = connectedContracts.validatorWalletCreator;
45              challengeManager = connectedContracts.challengeManager;
46      
47              confirmPeriodBlocks = config.confirmPeriodBlocks;
48              chainId = config.chainId;
49              baseStake = config.baseStake;
50              wasmModuleRoot = config.wasmModuleRoot;
51              // A little over 15 minutes
52              minimumAssertionPeriod = 75;
53              challengeGracePeriodBlocks = config.challengeGracePeriodBlocks;
54      
55              // loser stake is now sent directly to loserStakeEscrow, it must not
56              // be address(0) because some token do not allow transfers to address(0)
57              require(config.loserStakeEscrow != address(0), "INVALID_ESCROW_0");
58              loserStakeEscrow = config.loserStakeEscrow;
59      
60              stakeToken = config.stakeToken;
61              anyTrustFastConfirmer = config.anyTrustFastConfirmer;
62      
63              bytes32 parentAssertionHash = bytes32(0);
64              bytes32 inboxAcc = bytes32(0);
65              bytes32 genesisHash = RollupLib.assertionHash({
66                  parentAssertionHash: parentAssertionHash,
67                  afterStateHash: config.genesisAssertionState.hash(),
68                  inboxAcc: inboxAcc
69              });
70      
71              uint256 currentInboxCount = bridge.sequencerMessageCount();
72              // ensure to move the inbox forward by at least one message
73              if (currentInboxCount == config.genesisInboxCount) {
74                  currentInboxCount += 1;
75              }
76              AssertionNode memory initialAssertion = AssertionNodeLib.createAssertion(
77                  true,
78                  RollupLib.configHash({
79                      wasmModuleRoot: wasmModuleRoot,
80                      requiredStake: baseStake,
81                      challengeManager: address(challengeManager),
82                      confirmPeriodBlocks: confirmPeriodBlocks,
83                      nextInboxPosition: uint64(currentInboxCount)
84                  })
85              );
86              initializeCore(initialAssertion, genesisHash);
87      
88              AssertionInputs memory assertionInputs;
89              assertionInputs.afterState = config.genesisAssertionState;
90              emit AssertionCreated(
91                  genesisHash,
92                  parentAssertionHash,
93                  assertionInputs,
94                  inboxAcc,
95                  currentInboxCount,
96                  wasmModuleRoot,
97                  baseStake,
98                  address(challengeManager),
99                  confirmPeriodBlocks
100             );
101             if (_hostChainIsArbitrum) {
102                 _assertionCreatedAtArbSysBlock[genesisHash] = ArbSys(address(100)).arbBlockNumber();
103             }
104     
105             emit RollupInitialized(config.wasmModuleRoot, config.chainId);
106         }
117         function setOutbox(IOutbox _outbox) external override {
118             outbox = _outbox;
119             bridge.setOutbox(address(_outbox), true);
120             emit OwnerFunctionCalled(0);
121         }
127         function removeOldOutbox(address _outbox) external override {
128             require(_outbox != address(outbox), "CUR_OUTBOX");
129             bridge.setOutbox(_outbox, false);
130             emit OwnerFunctionCalled(1);
131         }
138         function setDelayedInbox(address _inbox, bool _enabled) external override {
139             bridge.setDelayedInbox(address(_inbox), _enabled);
140             emit OwnerFunctionCalled(2);
141         }
150         function pause() external override {
151             _pause();
152             emit OwnerFunctionCalled(3);
153         }
158         function resume() external override {
159             _unpause();
160             emit OwnerFunctionCalled(4);
161         }
180         function setValidator(address[] calldata _validator, bool[] calldata _val) external override {
181             require(_validator.length > 0, "EMPTY_ARRAY");
182             require(_validator.length == _val.length, "WRONG_LENGTH");
183     
184             for (uint256 i = 0; i < _validator.length; i++) {
185                 isValidator[_validator[i]] = _val[i];
186             }
187             emit OwnerFunctionCalled(6);
188         }
195         function setOwner(address newOwner) external override {
196             _changeAdmin(newOwner);
197             emit OwnerFunctionCalled(7);
198         }
204         function setMinimumAssertionPeriod(uint256 newPeriod) external override {
205             minimumAssertionPeriod = newPeriod;
206             emit OwnerFunctionCalled(8);
207         }
213         function setConfirmPeriodBlocks(uint64 newConfirmPeriod) external override {
214             require(newConfirmPeriod > 0, "INVALID_CONFIRM_PERIOD");
215             confirmPeriodBlocks = newConfirmPeriod;
216             emit OwnerFunctionCalled(9);
217         }
223         function setBaseStake(uint256 newBaseStake) external override {
224             baseStake = newBaseStake;
225             emit OwnerFunctionCalled(12);
226         }
228         function forceRefundStaker(address[] calldata staker) external override whenPaused {
229             require(staker.length > 0, "EMPTY_ARRAY");
230             for (uint256 i = 0; i < staker.length; i++) {
231                 requireInactiveStaker(staker[i]);
232                 reduceStakeTo(staker[i], 0);
233             }
234             emit OwnerFunctionCalled(22);
235         }
237         function forceCreateAssertion(
238             bytes32 prevAssertionHash,
239             AssertionInputs calldata assertion,
240             bytes32 expectedAssertionHash
241         ) external override whenPaused {
242             // To update the wasm module root in the case of a bug:
243             // 0. pause the contract
244             // 1. update the wasm module root in the contract
245             // 2. update the config hash of the assertion after which you wish to use the new wasm module root (functionality not written yet)
246             // 3. force refund the stake of the current leaf assertion(s)
247             // 4. create a new assertion using the assertion with the updated config has as a prev
248             // 5. force confirm it - this is necessary to set latestConfirmed on the correct line
249             // 6. unpause the contract
250     
251             // Normally, a new assertion is created using its prev's confirmPeriodBlocks
252             // in the case of a force create, we use the rollup's current confirmPeriodBlocks
253             createNewAssertion(assertion, prevAssertionHash, expectedAssertionHash);
254     
255             emit OwnerFunctionCalled(23);
256         }
258         function forceConfirmAssertion(
259             bytes32 assertionHash,
260             bytes32 parentAssertionHash,
261             AssertionState calldata confirmState,
262             bytes32 inboxAcc
263         ) external override whenPaused {
264             // this skip deadline, prev, challenge validations
265             confirmAssertionInternal(assertionHash, parentAssertionHash, confirmState, inboxAcc);
266             emit OwnerFunctionCalled(24);
267         }
269         function setLoserStakeEscrow(address newLoserStakerEscrow) external override {
270             // loser stake is now sent directly to loserStakeEscrow, it must not
271             // be address(0) because some token do not allow transfers to address(0)
272             require(newLoserStakerEscrow != address(0), "INVALID_ESCROW_0");
273             loserStakeEscrow = newLoserStakerEscrow;
274             emit OwnerFunctionCalled(25);
275         }
281         function setWasmModuleRoot(bytes32 newWasmModuleRoot) external override {
282             wasmModuleRoot = newWasmModuleRoot;
283             emit OwnerFunctionCalled(26);
284         }
290         function setSequencerInbox(address _sequencerInbox) external override {
291             bridge.setSequencerInbox(_sequencerInbox);
292             emit OwnerFunctionCalled(27);
293         }
299         function setInbox(IInboxBase newInbox) external {
300             inbox = newInbox;
301             emit OwnerFunctionCalled(28);
302         }
308         function setValidatorWhitelistDisabled(bool _validatorWhitelistDisabled) external {
309             validatorWhitelistDisabled = _validatorWhitelistDisabled;
310             emit OwnerFunctionCalled(30);
311         }
317         function setAnyTrustFastConfirmer(address _anyTrustFastConfirmer) external {
318             anyTrustFastConfirmer = _anyTrustFastConfirmer;
319             emit OwnerFunctionCalled(31);
320         }
326         function setChallengeManager(address _challengeManager) external {
327             challengeManager = IEdgeChallengeManager(_challengeManager);
328             emit OwnerFunctionCalled(32);
329         }


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/rollup/RollupAdminLogic.sol#L0:0

```solidity
File: src/rollup/RollupCreator.sol


61          receive() external payable {}
63          function setTemplates(
64              BridgeCreator _bridgeCreator,
65              IOneStepProofEntry _osp,
66              IEdgeChallengeManager _challengeManagerLogic,
67              IRollupAdmin _rollupAdminLogic,
68              IRollupUser _rollupUserLogic,
69              IUpgradeExecutor _upgradeExecutorLogic,
70              address _validatorWalletCreator,
71              DeployHelper _l2FactoriesDeployer
72          ) external onlyOwner {
73              bridgeCreator = _bridgeCreator;
74              osp = _osp;
75              challengeManagerTemplate = _challengeManagerLogic;
76              rollupAdminLogic = _rollupAdminLogic;
77              rollupUserLogic = _rollupUserLogic;
78              upgradeExecutorLogic = _upgradeExecutorLogic;
79              validatorWalletCreator = _validatorWalletCreator;
80              l2FactoriesDeployer = _l2FactoriesDeployer;
81              emit TemplatesUpdated();
82          }
137         function createRollup(RollupDeploymentParams memory deployParams)
138             public
139             payable
140             returns (address)
141         {
142             {
143                 // Make sure the immutable maxDataSize is as expected
144                 (
145                     ,
146                     ISequencerInbox ethSequencerInbox,
147                     ISequencerInbox ethDelayBufferableSequencerInbox,
148                     IInboxBase ethInbox,
149                     ,
150     
151                 ) = bridgeCreator.ethBasedTemplates();
152                 require(
153                     deployParams.maxDataSize == ethSequencerInbox.maxDataSize(),
154                     "SI_MAX_DATA_SIZE_MISMATCH"
155                 );
156                 require(
157                     deployParams.maxDataSize == ethDelayBufferableSequencerInbox.maxDataSize(),
158                     "SI_MAX_DATA_SIZE_MISMATCH"
159                 );
160                 require(deployParams.maxDataSize == ethInbox.maxDataSize(), "I_MAX_DATA_SIZE_MISMATCH");
161     
162                 (
163                     ,
164                     ISequencerInbox erc20SequencerInbox,
165                     ISequencerInbox erc20DelayBufferableSequencerInbox,
166                     IInboxBase erc20Inbox,
167                     ,
168     
169                 ) = bridgeCreator.erc20BasedTemplates();
170                 require(
171                     deployParams.maxDataSize == erc20SequencerInbox.maxDataSize(),
172                     "SI_MAX_DATA_SIZE_MISMATCH"
173                 );
174                 require(
175                     deployParams.maxDataSize == erc20DelayBufferableSequencerInbox.maxDataSize(),
176                     "SI_MAX_DATA_SIZE_MISMATCH"
177                 );
178                 require(
179                     deployParams.maxDataSize == erc20Inbox.maxDataSize(),
180                     "I_MAX_DATA_SIZE_MISMATCH"
181                 );
182             }
183     
184             // create proxy admin which will manage bridge contracts
185             ProxyAdmin proxyAdmin = new ProxyAdmin();
186     
187             // Create the rollup proxy to figure out the address and initialize it later
188             RollupProxy rollup = new RollupProxy{salt: keccak256(abi.encode(deployParams))}();
189     
190             BridgeCreator.BridgeContracts memory bridgeContracts = bridgeCreator.createBridge(
191                 address(proxyAdmin),
192                 address(rollup),
193                 deployParams.nativeToken,
194                 deployParams.config.sequencerInboxMaxTimeVariation,
195                 deployParams.config.bufferConfig
196             );
197     
198             IEdgeChallengeManager challengeManager = createChallengeManager(address(rollup), address(proxyAdmin), deployParams.config);
199     
200             // deploy and init upgrade executor
201             address upgradeExecutor = _deployUpgradeExecutor(deployParams.config.owner, proxyAdmin);
202     
203             // upgradeExecutor shall be proxyAdmin's owner
204             proxyAdmin.transferOwnership(address(upgradeExecutor));
205     
206             // initialize the rollup with this contract as owner to set batch poster and validators
207             // it will transfer the ownership to the upgrade executor later
208             deployParams.config.owner = address(this);
209             rollup.initializeProxy(
210                 deployParams.config,
211                 ContractDependencies({
212                     bridge: bridgeContracts.bridge,
213                     sequencerInbox: bridgeContracts.sequencerInbox,
214                     inbox: bridgeContracts.inbox,
215                     outbox: bridgeContracts.outbox,
216                     rollupEventInbox: bridgeContracts.rollupEventInbox,
217                     challengeManager: challengeManager,
218                     rollupAdminLogic: address(rollupAdminLogic),
219                     rollupUserLogic: rollupUserLogic,
220                     validatorWalletCreator: validatorWalletCreator
221                 })
222             );
223     
224             // Setting batch posters and batch poster manager
225             for (uint256 i = 0; i < deployParams.batchPosters.length; i++) {
226                 bridgeContracts.sequencerInbox.setIsBatchPoster(deployParams.batchPosters[i], true);
227             }
228             if (deployParams.batchPosterManager != address(0)) {
229                 bridgeContracts.sequencerInbox.setBatchPosterManager(deployParams.batchPosterManager);
230             }
231     
232             // Call setValidator on the newly created rollup contract just if validator set is not empty
233             if (deployParams.validators.length != 0) {
234                 bool[] memory _vals = new bool[](deployParams.validators.length);
235                 for (uint256 i = 0; i < deployParams.validators.length; i++) {
236                     _vals[i] = true;
237                 }
238                 IRollupAdmin(address(rollup)).setValidator(deployParams.validators, _vals);
239             }
240     
241             IRollupAdmin(address(rollup)).setOwner(address(upgradeExecutor));
242     
243             if (deployParams.deployFactoriesToL2) {
244                 _deployFactories(
245                     address(bridgeContracts.inbox),
246                     deployParams.nativeToken,
247                     deployParams.maxFeePerGasForRetryables
248                 );
249             }
250     
251             emit RollupCreated(
252                 address(rollup),
253                 deployParams.nativeToken,
254                 address(bridgeContracts.inbox),
255                 address(bridgeContracts.outbox),
256                 address(bridgeContracts.rollupEventInbox),
257                 address(challengeManager),
258                 address(proxyAdmin),
259                 address(bridgeContracts.sequencerInbox),
260                 address(bridgeContracts.bridge),
261                 address(upgradeExecutor),
262                 address(validatorWalletCreator)
263             );
264             return address(rollup);
265         }


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/rollup/RollupCreator.sol#L0:0

```solidity
File: src/rollup/RollupProxy.sol


12          function initializeProxy(Config memory config, ContractDependencies memory connectedContracts)
13              external
14          {
15              if (
16                  _getAdmin() == address(0) &&
17                  _getImplementation() == address(0) &&
18                  _getSecondaryImplementation() == address(0)
19              ) {
20                  _initialize(
21                      address(connectedContracts.rollupAdminLogic),
22                      abi.encodeCall(
23                          IRollupAdmin.initialize,
24                          (config,
25                          connectedContracts)
26                      ),
27                      address(connectedContracts.rollupUserLogic),
28                      abi.encodeCall(IRollupUser.initialize, (config.stakeToken)),
29                      config.owner
30                  );
31              } else {
32                  _fallback();
33              }
34          }


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/rollup/RollupProxy.sol#L0:0

```solidity
File: src/rollup/RollupUserLogic.sol


27          function initialize(address _stakeToken) external view override onlyProxy {
28              require(_stakeToken != address(0), "NEED_STAKE_TOKEN");
29          }
62          function removeWhitelistAfterFork() external {
63              require(!validatorWhitelistDisabled, "WHITELIST_DISABLED");
64              require(_chainIdChanged(), "CHAIN_ID_NOT_CHANGED");
65              validatorWhitelistDisabled = true;
66          }
71          function removeWhitelistAfterValidatorAfk() external {
72              require(!validatorWhitelistDisabled, "WHITELIST_DISABLED");
73              require(_validatorIsAfk(), "VALIDATOR_NOT_AFK");
74              validatorWhitelistDisabled = true;
75          }
82          function confirmAssertion(
83              bytes32 assertionHash,
84              bytes32 prevAssertionHash,
85              AssertionState calldata confirmState,
86              bytes32 winningEdgeId,
87              ConfigData calldata prevConfig,
88              bytes32 inboxAcc
89          ) external onlyValidator whenNotPaused {
90              /*
91              * To confirm an assertion, the following must be true:
92              * 1. The assertion must be pending
93              * 2. The assertion's deadline must have passed
94              * 3. The assertion's prev must be latest confirmed
95              * 4. The assertion's prev's child confirm deadline must have passed
96              * 5. If the assertion's prev has more than 1 child, the assertion must be the winner of the challenge
97              *
98              * Note that we do not need to ever reject invalid assertion because they can never confirm
99              *      and the stake on them is swept to the loserStakeEscrow as soon as the leaf is created
100             */
101     
102             // The assertion's must exists and be pending and will be validated in RollupCore.confirmAssertionInternal
103             AssertionNode storage assertion = getAssertionStorage(assertionHash);
104     
105             // prevAssertionHash is user supplied, but will be validated in RollupCore.confirmAssertionInternal
106             AssertionNode storage prevAssertion = getAssertionStorage(prevAssertionHash);
107             RollupLib.validateConfigHash(prevConfig, prevAssertion.configHash);
108     
109             // Check that deadline has passed
110             require(block.number >= assertion.createdAtBlock + prevConfig.confirmPeriodBlocks, "BEFORE_DEADLINE");
111     
112             // Check that prev is latest confirmed
113             require(prevAssertionHash == latestConfirmed(), "PREV_NOT_LATEST_CONFIRMED");
114     
115             if (prevAssertion.secondChildBlock > 0) {
116                 // if the prev has more than 1 child, check if this assertion is the challenge winner
117                 ChallengeEdge memory winningEdge = IEdgeChallengeManager(prevConfig.challengeManager).getEdge(winningEdgeId);
118                 require(winningEdge.claimId == assertionHash, "NOT_WINNER");
119                 require(winningEdge.status == EdgeStatus.Confirmed, "EDGE_NOT_CONFIRMED");
120                 require(winningEdge.confirmedAtBlock != 0, "ZERO_CONFIRMED_AT_BLOCK");
121                 // an additional number of blocks is added to ensure that the result of the challenge is widely
122                 // observable before it causes an assertion to be confirmed. After a winning edge is found, it will
123                 // always be challengeGracePeriodBlocks before an assertion can be confirmed
124                 require(
125                     block.number >= winningEdge.confirmedAtBlock + challengeGracePeriodBlocks,
126                     "CHALLENGE_GRACE_PERIOD_NOT_PASSED"
127                 );
128             }
129     
130             confirmAssertionInternal(assertionHash, prevAssertionHash, confirmState, inboxAcc);
131         }
150         function computeAssertionHash(bytes32 prevAssertionHash, AssertionState calldata state, bytes32 inboxAcc)
151             external
152             pure
153             returns (bytes32)
154         {
155             return RollupLib.assertionHash(prevAssertionHash, state, inboxAcc);
156         }
163         function stakeOnNewAssertion(AssertionInputs calldata assertion, bytes32 expectedAssertionHash)
164             public
165             onlyValidator
166             whenNotPaused
167         {
168             // Early revert on duplicated assertion if expectedAssertionHash is set
169             require(
170                 expectedAssertionHash == bytes32(0)
171                     || getAssertionStorage(expectedAssertionHash).status == AssertionStatus.NoAssertion,
172                 "EXPECTED_ASSERTION_SEEN"
173             );
174     
175             require(isStaked(msg.sender), "NOT_STAKED");
176     
177             // requiredStake is user supplied, will be verified against configHash later
178             // the prev's requiredStake is used to make sure all children have the same stake
179             // the staker may have more than enough stake, and the entire stake will be locked
180             // we cannot do a refund here because the staker may be staker on an unconfirmed ancestor that requires more stake
181             // excess stake can be removed by calling reduceDeposit when the staker is inactive
182             require(amountStaked(msg.sender) >= assertion.beforeStateData.configData.requiredStake, "INSUFFICIENT_STAKE");
183     
184             bytes32 prevAssertion = RollupLib.assertionHash(
185                 assertion.beforeStateData.prevPrevAssertionHash,
186                 assertion.beforeState,
187                 assertion.beforeStateData.sequencerBatchAcc
188             );
189             getAssertionStorage(prevAssertion).requireExists();
190     
191             // Staker can create new assertion only if
192             // a) its last staked assertion is the prev; or
193             // b) its last staked assertion have a child
194             bytes32 lastAssertion = latestStakedAssertion(msg.sender);
195             require(
196                 lastAssertion == prevAssertion || getAssertionStorage(lastAssertion).firstChildBlock > 0,
197                 "STAKED_ON_ANOTHER_BRANCH"
198             );
199     
200             (bytes32 newAssertionHash, bool overflowAssertion) =
201                 createNewAssertion(assertion, prevAssertion, expectedAssertionHash);
202             _stakerMap[msg.sender].latestStakedAssertion = newAssertionHash;
203     
204             if (!overflowAssertion) {
205                 uint256 timeSincePrev = block.number - getAssertionStorage(prevAssertion).createdAtBlock;
206                 // Verify that assertion meets the minimum Delta time requirement
207                 require(timeSincePrev >= minimumAssertionPeriod, "TIME_DELTA");
208             }
209     
210             if (!getAssertionStorage(newAssertionHash).isFirstChild) {
211                 // We assume assertion.beforeStateData is valid here as it will be validated in createNewAssertion
212                 // only 1 of the children can be confirmed and get their stake refunded
213                 // so we send the other children's stake to the loserStakeEscrow
214                 // NOTE: if the losing staker have staked more than requiredStake, the excess stake will be stuck
215                 IERC20(stakeToken).safeTransfer(loserStakeEscrow, assertion.beforeStateData.configData.requiredStake);
216             }
217         }
222         function returnOldDeposit() external override onlyValidator whenNotPaused {
223             requireInactiveStaker(msg.sender);
224             withdrawStaker(msg.sender);
225         }
241         function reduceDeposit(uint256 target) external onlyValidator whenNotPaused {
242             requireInactiveStaker(msg.sender);
243             // amount will be checked when creating an assertion
244             reduceStakeTo(msg.sender, target);
245         }
252         function fastConfirmAssertion(
253             bytes32 assertionHash,
254             bytes32 parentAssertionHash,
255             AssertionState calldata confirmState,
256             bytes32 inboxAcc
257         ) public whenNotPaused {
258             require(msg.sender == anyTrustFastConfirmer, "NOT_FAST_CONFIRMER");
259             // this skip deadline, prev, challenge validations
260             confirmAssertionInternal(assertionHash, parentAssertionHash, confirmState, inboxAcc);
261         }
273         function fastConfirmNewAssertion(AssertionInputs calldata assertion, bytes32 expectedAssertionHash)
274             external
275             whenNotPaused
276         {
277             // Must supply expectedAssertionHash to fastConfirmNewAssertion
278             require(expectedAssertionHash != bytes32(0), "EXPECTED_ASSERTION_HASH");
279             AssertionStatus status = getAssertionStorage(expectedAssertionHash).status;
280     
281             bytes32 prevAssertion = RollupLib.assertionHash(
282                 assertion.beforeStateData.prevPrevAssertionHash,
283                 assertion.beforeState,
284                 assertion.beforeStateData.sequencerBatchAcc
285             );
286             getAssertionStorage(prevAssertion).requireExists();
287     
288             if (status == AssertionStatus.NoAssertion) {
289                 // If not exists, we create the new assertion
290                 (bytes32 newAssertionHash,) = createNewAssertion(assertion, prevAssertion, expectedAssertionHash);
291                 if (!getAssertionStorage(newAssertionHash).isFirstChild) {
292                     // only 1 of the children can be confirmed and get their stake refunded
293                     // so we send the other children's stake to the loserStakeEscrow
294                     // NOTE: if the losing staker have staked more than requiredStake, the excess stake will be stuck
295                     IERC20(stakeToken).safeTransfer(loserStakeEscrow, assertion.beforeStateData.configData.requiredStake);
296                 }
297             }
298     
299             // This would revert if the assertion is already confirmed
300             fastConfirmAssertion(
301                 expectedAssertionHash,
302                 prevAssertion,
303                 assertion.afterState,
304                 bridge.sequencerInboxAccs(assertion.afterState.globalState.getInboxPosition() - 1)
305             );
306         }
308         function owner() external view returns (address) {
309             return _getAdmin();
310         }
316         function newStakeOnNewAssertion(
317             uint256 tokenAmount,
318             AssertionInputs calldata assertion,
319             bytes32 expectedAssertionHash
320         ) external {
321             newStakeOnNewAssertion(tokenAmount, assertion, expectedAssertionHash, msg.sender);
322         }
331         function newStakeOnNewAssertion(
332             uint256 tokenAmount,
333             AssertionInputs calldata assertion,
334             bytes32 expectedAssertionHash,
335             address withdrawalAddress
336         ) public {
337             require(withdrawalAddress != address(0), "EMPTY_WITHDRAWAL_ADDRESS");
338             _newStake(tokenAmount, withdrawalAddress);
339             stakeOnNewAssertion(assertion, expectedAssertionHash);
340             /// @dev This is an external call, safe because it's at the end of the function
341             receiveTokens(tokenAmount);
342         }
349         function addToDeposit(address stakerAddress, uint256 tokenAmount) external onlyValidator whenNotPaused {
350             _addToDeposit(stakerAddress, tokenAmount);
351             /// @dev This is an external call, safe because it's at the end of the function
352             receiveTokens(tokenAmount);
353         }
358         function withdrawStakerFunds() external override whenNotPaused returns (uint256) {
359             uint256 amount = withdrawFunds(msg.sender);
360             require(amount > 0, "NO_FUNDS_TO_WITHDRAW");
361             // This is safe because it occurs after all checks and effects
362             IERC20(stakeToken).safeTransfer(msg.sender, amount);
363             return amount;
364         }


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/rollup/RollupUserLogic.sol#L0:0

</details>

## NC062 - Consider adding formal verification proofs:

Consider using formal verification to mathematically prove that your code does what is intended, and does not have any edge cases with unexpected behavior. The solidity compiler itself has this functionality [built in based off of SMTChecker](https://docs.soliditylang.org/en/latest/smtchecker.html#smtchecker-and-formal-verification).


```solidity
File: Various Files


None

```

## NC063 - Public state variables shouldn't have a preceding _ in their name:

Remove the _ from the state variable name, ensure you also refactor where these state variables are internally called.


```solidity
File: src/rollup/BOLDUpgradeAction.sol


167         uint256[] _array;


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/rollup/BOLDUpgradeAction.sol#L0:0

```solidity
File: src/rollup/RollupCore.sol


102         mapping(address => Staker) public _stakerMap;


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/rollup/RollupCore.sol#L0:0

## NC064 - Large multiples of ten should use scientific notation (e.g. 1e6) rather than decimal literals (e.g. 1000000), for readability:

Using scientific notation for large multiples of ten improves code readability. Instead of writing large decimal literals, consider using scientific notation.


```solidity
File: src/bridge/DelayBuffer.sol


17          uint256 public constant BASIS = 10000;


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/bridge/DelayBuffer.sol#L0:0

## NC065 - Common functions should be refactored to a common base contract:

The functions below have the same implementation as is seen in other files. The functions should be refactored into functions of a common base contract.


<details>
<summary>Click to show 10 findings</summary>

```solidity
File: src/rollup/IRollupCore.sol


/// @audit seen in cool/src/assertionStakingPool/interfaces/IAbsBoldStakingPool.sol
    function stakeToken() external view returns (address);

/// @audit seen in cool/src/bridge/ISequencerInbox.sol
    function bridge() external view returns (IBridge);

/// @audit seen in cool/src/rollup/BOLDUpgradeAction.sol
    function wasmModuleRoot() external view returns (bytes32);

/// @audit seen in cool/src/rollup/BOLDUpgradeAction.sol
    function getStakerAddress(uint64 stakerNum) external view returns (address);

/// @audit seen in cool/src/rollup/BOLDUpgradeAction.sol
    function stakerCount() external view returns (uint64);

```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/rollup/IRollupCore.sol#L133:133

```solidity
File: src/challengeV2/IAssertionChain.sol


/// @audit seen in cool/src/bridge/ISequencerInbox.sol
    function bridge() external view returns (IBridge);

```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/challengeV2/IAssertionChain.sol#L14:14

```solidity
File: src/rollup/RollupUserLogic.sol


/// @audit seen in cool/src/bridge/SequencerInbox.sol
    function _chainIdChanged() internal view returns (bool) {
        return deployTimeChainId != block.chainid;
    }

```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/rollup/RollupUserLogic.sol#L33:35

```solidity
File: src/rollup/IRollupAdmin.sol


/// @audit seen in cool/src/rollup/BOLDUpgradeAction.sol
    function forceRefundStaker(address[] memory stacker) external;

/// @audit seen in cool/src/rollup/BOLDUpgradeAction.sol
    function pause() external;

/// @audit seen in cool/src/rollup/BOLDUpgradeAction.sol
    function resume() external;

```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/rollup/IRollupAdmin.sol#L45:45

</details>

## NC066 - Polymorphic functions make security audits more time-consuming and error-prone:

The instances below point to one of two functions with the same name. Consider naming each function differently, in order to make code navigation and analysis easier.


<details>
<summary>Click to show 9 findings</summary>

```solidity
File: src/assertionStakingPool/AbsBoldStakingPool.sol


57          function withdrawFromPool() external {


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/assertionStakingPool/AbsBoldStakingPool.sol#L0:0

```solidity
File: src/assertionStakingPool/interfaces/IAbsBoldStakingPool.sol


27          function withdrawFromPool() external;


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/assertionStakingPool/interfaces/IAbsBoldStakingPool.sol#L0:0

```solidity
File: src/bridge/ISequencerInbox.sol


179         function addSequencerL2BatchFromOrigin(


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/bridge/ISequencerInbox.sol#L0:0

```solidity
File: src/bridge/SequencerInbox.sol


366         function addSequencerL2BatchFromOrigin(


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/bridge/SequencerInbox.sol#L0:0

```solidity
File: src/challengeV2/EdgeChallengeManager.sol


305         function initialize(
371         function createLayerZeroEdge(CreateEdgeArgs calldata args) external returns (bytes32) {
451         function bisectEdge(bytes32 edgeId, bytes32 bisectionHistoryRoot, bytes calldata prefixProof)
511         function confirmEdgeByTime(bytes32 edgeId, AssertionStateData calldata claimStateData) public {
491         function multiUpdateTimeCacheByChildren(bytes32[] calldata edgeIds) public {
499         function updateTimerCacheByChildren(bytes32 edgeId) public {
505         function updateTimerCacheByClaim(bytes32 edgeId, bytes32 claimingEdgeId) public {
539         function confirmEdgeByOneStepProof(
572         function refundStake(bytes32 edgeId) public {
591         function getLayerZeroEndHeight(EdgeType eType) public view returns (uint256) {
604         function calculateEdgeId(
616         function calculateMutualId(
627         function edgeExists(bytes32 edgeId) public view returns (bool) {
632         function getEdge(bytes32 edgeId) public view returns (ChallengeEdge memory) {
637         function edgeLength(bytes32 edgeId) public view returns (uint256) {
642         function hasRival(bytes32 edgeId) public view returns (bool) {
647         function confirmedRival(bytes32 mutualId) public view returns (bytes32) {
652         function hasLengthOneRival(bytes32 edgeId) public view returns (bool) {
657         function timeUnrivaled(bytes32 edgeId) public view returns (uint256) {
662         function getPrevAssertionHash(bytes32 edgeId) public view returns (bytes32) {
667         function firstRival(bytes32 mutualId) public view returns (bytes32) {
672         function hasMadeLayerZeroRival(address account, bytes32 mutualId) external view returns (bool) {


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/challengeV2/EdgeChallengeManager.sol#L0:0

```solidity
File: src/rollup/BOLDUpgradeAction.sol


130         function wasmModuleRoot() external view returns (bytes32) {
134         function latestConfirmed() external view returns (uint64) {
138         function getNode(uint64 nodeNum) external view returns (Node memory) {
142         function getStakerAddress(uint64 stakerNum) external view returns (address) {
146         function stakerCount() external view returns (uint64) {
150         function getStaker(address staker) external view returns (OldStaker memory) {
154         function isValidator(address validator) external view returns (bool) {
158         function validatorWalletCreator() external view returns (address) {
169         constructor(uint256[] memory __array) {


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/rollup/BOLDUpgradeAction.sol#L0:0

```solidity
File: src/rollup/IRollupLogic.sol


44          function newStakeOnNewAssertion(


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/rollup/IRollupLogic.sol#L0:0

```solidity
File: src/rollup/RollupLib.sol


37          function assertionHash(


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/rollup/RollupLib.sol#L0:0

```solidity
File: src/rollup/RollupUserLogic.sol


331         function newStakeOnNewAssertion(


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/rollup/RollupUserLogic.sol#L0:0

</details>

## NC067 - Error messages should descriptive, rather that cryptic:

  


<details>
<summary>Click to show 4 findings</summary>

```solidity
File: src/rollup/BOLDUpgradeAction.sol


517             require(address(rollup) == expectedRollupAddress, "UNEXPCTED_ROLLUP_ADDR");
529                     require(ROLLUP_READER.isValidator(validators[i]), "UNEXPECTED_NEW_VALIDATOR");


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/rollup/BOLDUpgradeAction.sol#L0:0

```solidity
File: src/rollup/RollupAdminLogic.sol


57              require(config.loserStakeEscrow != address(0), "INVALID_ESCROW_0");
128             require(_outbox != address(outbox), "CUR_OUTBOX");
181             require(_validator.length > 0, "EMPTY_ARRAY");
182             require(_validator.length == _val.length, "WRONG_LENGTH");
214             require(newConfirmPeriod > 0, "INVALID_CONFIRM_PERIOD");
229             require(staker.length > 0, "EMPTY_ARRAY");
272             require(newLoserStakerEscrow != address(0), "INVALID_ESCROW_0");


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/rollup/RollupAdminLogic.sol#L0:0

```solidity
File: src/rollup/RollupCreator.sol


152                 require(
156                 require(
160                 require(deployParams.maxDataSize == ethInbox.maxDataSize(), "I_MAX_DATA_SIZE_MISMATCH");
170                 require(
174                 require(
178                 require(


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/rollup/RollupCreator.sol#L0:0

```solidity
File: src/rollup/RollupUserLogic.sol


21              require(isValidator[msg.sender] || validatorWhitelistDisabled, "NOT_VALIDATOR");
28              require(_stakeToken != address(0), "NEED_STAKE_TOKEN");
63              require(!validatorWhitelistDisabled, "WHITELIST_DISABLED");
64              require(_chainIdChanged(), "CHAIN_ID_NOT_CHANGED");
72              require(!validatorWhitelistDisabled, "WHITELIST_DISABLED");
73              require(_validatorIsAfk(), "VALIDATOR_NOT_AFK");
110             require(block.number >= assertion.createdAtBlock + prevConfig.confirmPeriodBlocks, "BEFORE_DEADLINE");
113             require(prevAssertionHash == latestConfirmed(), "PREV_NOT_LATEST_CONFIRMED");
118                 require(winningEdge.claimId == assertionHash, "NOT_WINNER");
119                 require(winningEdge.status == EdgeStatus.Confirmed, "EDGE_NOT_CONFIRMED");
120                 require(winningEdge.confirmedAtBlock != 0, "ZERO_CONFIRMED_AT_BLOCK");
124                 require(
139             require(!isStaked(msg.sender), "ALREADY_STAKED");
169             require(
175             require(isStaked(msg.sender), "NOT_STAKED");
182             require(amountStaked(msg.sender) >= assertion.beforeStateData.configData.requiredStake, "INSUFFICIENT_STAKE");
195             require(
207                 require(timeSincePrev >= minimumAssertionPeriod, "TIME_DELTA");
233             require(isStaked(stakerAddress), "NOT_STAKED");
258             require(msg.sender == anyTrustFastConfirmer, "NOT_FAST_CONFIRMER");
278             require(expectedAssertionHash != bytes32(0), "EXPECTED_ASSERTION_HASH");
337             require(withdrawalAddress != address(0), "EMPTY_WITHDRAWAL_ADDRESS");
360             require(amount > 0, "NO_FUNDS_TO_WITHDRAW");


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/rollup/RollupUserLogic.sol#L0:0

</details>

## NC068 - Missing timelock for critical parameter change:

Timelocks prevent users from being surprised by changes.


```solidity
File: src/bridge/SequencerInbox.sol


943             batchPosterManager = newBatchPosterManager;


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/bridge/SequencerInbox.sol#L0:0

```solidity
File: src/rollup/RollupCreator.sol


73              bridgeCreator = _bridgeCreator;
74              osp = _osp;
75              challengeManagerTemplate = _challengeManagerLogic;
76              rollupAdminLogic = _rollupAdminLogic;
77              rollupUserLogic = _rollupUserLogic;
78              upgradeExecutorLogic = _upgradeExecutorLogic;
79              validatorWalletCreator = _validatorWalletCreator;
80              l2FactoriesDeployer = _l2FactoriesDeployer;


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/rollup/RollupCreator.sol#L0:0

## NC069 - Setters should prevent re-setting of the same value:

This especially problematic when the setter also emits the same value, which may be confusing to offline parsers.


<details>
<summary>Click to show 4 findings</summary>

```solidity
File: src/bridge/SequencerInbox.sol


847         function _setBufferConfig(BufferConfig memory bufferConfig_) internal {
848             if (!isDelayBufferable) revert NotDelayBufferable();
849             if (!DelayBuffer.isValidBufferConfig(bufferConfig_)) revert BadBufferConfig();
850     
851             if (buffer.bufferBlocks == 0 || buffer.bufferBlocks > bufferConfig_.max) {
852                 buffer.bufferBlocks = bufferConfig_.max;
853             }
854             if (buffer.bufferBlocks < bufferConfig_.threshold) {
855                 buffer.bufferBlocks = bufferConfig_.threshold;
856             }
857             buffer.max = bufferConfig_.max;
858             buffer.threshold = bufferConfig_.threshold;
859             buffer.replenishRateInBasis = bufferConfig_.replenishRateInBasis;
860     
861             // if all delayed messages are read, the buffer is considered synced
862             if (bridge.delayedMessageCount() == totalDelayedMessagesRead) {
863                 buffer.update(uint64(block.number));
864             }
865         }
867         function _setMaxTimeVariation(ISequencerInbox.MaxTimeVariation memory maxTimeVariation_)
868             internal
869         {
870             if (
871                 maxTimeVariation_.delayBlocks > type(uint64).max ||
872                 maxTimeVariation_.futureBlocks > type(uint64).max ||
873                 maxTimeVariation_.delaySeconds > type(uint64).max ||
874                 maxTimeVariation_.futureSeconds > type(uint64).max
875             ) {
876                 revert BadMaxTimeVariation();
877             }
878             delayBlocks = uint64(maxTimeVariation_.delayBlocks);
879             futureBlocks = uint64(maxTimeVariation_.futureBlocks);
880             delaySeconds = uint64(maxTimeVariation_.delaySeconds);
881             futureSeconds = uint64(maxTimeVariation_.futureSeconds);
882         }
885         function setMaxTimeVariation(ISequencerInbox.MaxTimeVariation memory maxTimeVariation_)
886             external
887             onlyRollupOwner
888         {
889             _setMaxTimeVariation(maxTimeVariation_);
890             emit OwnerFunctionCalled(0);
891         }
894         function setIsBatchPoster(address addr, bool isBatchPoster_)
895             external
896             onlyRollupOwnerOrBatchPosterManager
897         {
898             isBatchPoster[addr] = isBatchPoster_;
899             emit OwnerFunctionCalled(1);
900         }
903         function setValidKeyset(bytes calldata keysetBytes) external onlyRollupOwner {
904             uint256 ksWord = uint256(keccak256(bytes.concat(hex"fe", keccak256(keysetBytes))));
905             bytes32 ksHash = bytes32(ksWord ^ (1 << 255));
906             if (keysetBytes.length >= 64 * 1024) revert KeysetTooLarge();
907     
908             if (dasKeySetInfo[ksHash].isValidKeyset) revert AlreadyValidDASKeyset(ksHash);
909             uint256 creationBlock = block.number;
910             if (hostChainIsArbitrum) {
911                 creationBlock = ArbSys(address(100)).arbBlockNumber();
912             }
913             dasKeySetInfo[ksHash] = DasKeySetInfo({
914                 isValidKeyset: true,
915                 creationBlock: uint64(creationBlock)
916             });
917             emit SetValidKeyset(ksHash, keysetBytes);
918             emit OwnerFunctionCalled(2);
919         }
933         function setIsSequencer(address addr, bool isSequencer_)
934             external
935             onlyRollupOwnerOrBatchPosterManager
936         {
937             isSequencer[addr] = isSequencer_;
938             emit OwnerFunctionCalled(4); // Owner in this context can also be batch poster manager
939         }
942         function setBatchPosterManager(address newBatchPosterManager) external onlyRollupOwner {
943             batchPosterManager = newBatchPosterManager;
944             emit OwnerFunctionCalled(5);
945         }
947         function setBufferConfig(BufferConfig memory bufferConfig_) external onlyRollupOwner {
948             _setBufferConfig(bufferConfig_);
949             emit OwnerFunctionCalled(6);
950         }


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/bridge/SequencerInbox.sol#L0:0

```solidity
File: src/rollup/BOLDUpgradeAction.sol


106         function set(bytes32 h, ExecutionState calldata executionState, uint256 inboxMaxCount) public {
107             require(h == stateHash(executionState, inboxMaxCount), "Invalid hash");
108             preImages[h] = abi.encode(executionState, inboxMaxCount);
109             emit HashSet(h, executionState, inboxMaxCount);
110         }


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/rollup/BOLDUpgradeAction.sol#L0:0

```solidity
File: src/rollup/RollupAdminLogic.sol


117         function setOutbox(IOutbox _outbox) external override {
118             outbox = _outbox;
119             bridge.setOutbox(address(_outbox), true);
120             emit OwnerFunctionCalled(0);
121         }
138         function setDelayedInbox(address _inbox, bool _enabled) external override {
139             bridge.setDelayedInbox(address(_inbox), _enabled);
140             emit OwnerFunctionCalled(2);
141         }
180         function setValidator(address[] calldata _validator, bool[] calldata _val) external override {
181             require(_validator.length > 0, "EMPTY_ARRAY");
182             require(_validator.length == _val.length, "WRONG_LENGTH");
183     
184             for (uint256 i = 0; i < _validator.length; i++) {
185                 isValidator[_validator[i]] = _val[i];
186             }
187             emit OwnerFunctionCalled(6);
188         }
195         function setOwner(address newOwner) external override {
196             _changeAdmin(newOwner);
197             emit OwnerFunctionCalled(7);
198         }
204         function setMinimumAssertionPeriod(uint256 newPeriod) external override {
205             minimumAssertionPeriod = newPeriod;
206             emit OwnerFunctionCalled(8);
207         }
213         function setConfirmPeriodBlocks(uint64 newConfirmPeriod) external override {
214             require(newConfirmPeriod > 0, "INVALID_CONFIRM_PERIOD");
215             confirmPeriodBlocks = newConfirmPeriod;
216             emit OwnerFunctionCalled(9);
217         }
223         function setBaseStake(uint256 newBaseStake) external override {
224             baseStake = newBaseStake;
225             emit OwnerFunctionCalled(12);
226         }
269         function setLoserStakeEscrow(address newLoserStakerEscrow) external override {
270             // loser stake is now sent directly to loserStakeEscrow, it must not
271             // be address(0) because some token do not allow transfers to address(0)
272             require(newLoserStakerEscrow != address(0), "INVALID_ESCROW_0");
273             loserStakeEscrow = newLoserStakerEscrow;
274             emit OwnerFunctionCalled(25);
275         }
281         function setWasmModuleRoot(bytes32 newWasmModuleRoot) external override {
282             wasmModuleRoot = newWasmModuleRoot;
283             emit OwnerFunctionCalled(26);
284         }
290         function setSequencerInbox(address _sequencerInbox) external override {
291             bridge.setSequencerInbox(_sequencerInbox);
292             emit OwnerFunctionCalled(27);
293         }
299         function setInbox(IInboxBase newInbox) external {
300             inbox = newInbox;
301             emit OwnerFunctionCalled(28);
302         }
308         function setValidatorWhitelistDisabled(bool _validatorWhitelistDisabled) external {
309             validatorWhitelistDisabled = _validatorWhitelistDisabled;
310             emit OwnerFunctionCalled(30);
311         }
317         function setAnyTrustFastConfirmer(address _anyTrustFastConfirmer) external {
318             anyTrustFastConfirmer = _anyTrustFastConfirmer;
319             emit OwnerFunctionCalled(31);
320         }
326         function setChallengeManager(address _challengeManager) external {
327             challengeManager = IEdgeChallengeManager(_challengeManager);
328             emit OwnerFunctionCalled(32);
329         }


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/rollup/RollupAdminLogic.sol#L0:0

```solidity
File: src/rollup/RollupCreator.sol


63          function setTemplates(
64              BridgeCreator _bridgeCreator,
65              IOneStepProofEntry _osp,
66              IEdgeChallengeManager _challengeManagerLogic,
67              IRollupAdmin _rollupAdminLogic,
68              IRollupUser _rollupUserLogic,
69              IUpgradeExecutor _upgradeExecutorLogic,
70              address _validatorWalletCreator,
71              DeployHelper _l2FactoriesDeployer
72          ) external onlyOwner {
73              bridgeCreator = _bridgeCreator;
74              osp = _osp;
75              challengeManagerTemplate = _challengeManagerLogic;
76              rollupAdminLogic = _rollupAdminLogic;
77              rollupUserLogic = _rollupUserLogic;
78              upgradeExecutorLogic = _upgradeExecutorLogic;
79              validatorWalletCreator = _validatorWalletCreator;
80              l2FactoriesDeployer = _l2FactoriesDeployer;
81              emit TemplatesUpdated();
82          }


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/rollup/RollupCreator.sol#L0:0

</details>

## NC070 - High cyclomatic complexity:

Consider breaking down these blocks into more manageable units, by splitting things into utility functions, by reducing nesting, and by using early returns.


<details>
<summary>Click to show 5 findings</summary>

```solidity
File: src/bridge/DelayBuffer.sol


33          function calcBuffer(
34              uint256 start,
35              uint256 end,
36              uint256 buffer,
37              uint256 sequenced,
38              uint256 threshold,
39              uint256 max,
40              uint256 replenishRateInBasis
41          ) internal pure returns (uint256) {
42              uint256 elapsed = end > start ? end - start : 0;
43              uint256 delay = sequenced > start ? sequenced - start : 0;
44              // replenishment rounds down and will not overflow since all inputs including
45              // replenishRateInBasis are cast from uint64 in calcPendingBuffer
46              buffer += (elapsed * replenishRateInBasis) / BASIS;
47      
48              uint256 unexpectedDelay = delay > threshold ? delay - threshold : 0;
49              if (unexpectedDelay > elapsed) {
50                  unexpectedDelay = elapsed;
51              }
52      
53              // decrease the buffer
54              if (buffer > unexpectedDelay) {
55                  buffer -= unexpectedDelay;
56                  if (buffer > threshold) {
57                      // saturating above at the max
58                      return buffer > max ? max : buffer;
59                  }
60              }
61              // saturating below at the threshold
62              return threshold;
63          }


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/bridge/DelayBuffer.sol#L0:0

```solidity
File: src/challengeV2/EdgeChallengeManager.sol


305         function initialize(
306             IAssertionChain _assertionChain,
307             uint64 _challengePeriodBlocks,
308             IOneStepProofEntry _oneStepProofEntry,
309             uint256 layerZeroBlockEdgeHeight,
310             uint256 layerZeroBigStepEdgeHeight,
311             uint256 layerZeroSmallStepEdgeHeight,
312             IERC20 _stakeToken,
313             address _excessStakeReceiver,
314             uint8 _numBigStepLevel,
315             uint256[] calldata _stakeAmounts
316         ) public initializer {
317             if (address(_assertionChain) == address(0)) {
318                 revert EmptyAssertionChain();
319             }
320             assertionChain = _assertionChain;
321             if (address(_oneStepProofEntry) == address(0)) {
322                 revert EmptyOneStepProofEntry();
323             }
324             oneStepProofEntry = _oneStepProofEntry;
325             if (_challengePeriodBlocks == 0) {
326                 revert EmptyChallengePeriod();
327             }
328             challengePeriodBlocks = _challengePeriodBlocks;
329     
330             stakeToken = _stakeToken;
331             if (_excessStakeReceiver == address(0)) {
332                 revert EmptyStakeReceiver();
333             }
334             excessStakeReceiver = _excessStakeReceiver;
335     
336             if (!EdgeChallengeManagerLib.isPowerOfTwo(layerZeroBlockEdgeHeight)) {
337                 revert NotPowerOfTwo(layerZeroBlockEdgeHeight);
338             }
339             LAYERZERO_BLOCKEDGE_HEIGHT = layerZeroBlockEdgeHeight;
340             if (!EdgeChallengeManagerLib.isPowerOfTwo(layerZeroBigStepEdgeHeight)) {
341                 revert NotPowerOfTwo(layerZeroBigStepEdgeHeight);
342             }
343             LAYERZERO_BIGSTEPEDGE_HEIGHT = layerZeroBigStepEdgeHeight;
344             if (!EdgeChallengeManagerLib.isPowerOfTwo(layerZeroSmallStepEdgeHeight)) {
345                 revert NotPowerOfTwo(layerZeroSmallStepEdgeHeight);
346             }
347             LAYERZERO_SMALLSTEPEDGE_HEIGHT = layerZeroSmallStepEdgeHeight;
348     
349             // ensure that there is at least on of each type of level
350             if (_numBigStepLevel == 0) {
351                 revert ZeroBigStepLevels();
352             }
353             // ensure there's also space for the block level and the small step level
354             // in total level parameters
355             if (_numBigStepLevel > 253) {
356                 revert BigStepLevelsTooMany(_numBigStepLevel);
357             }
358             NUM_BIGSTEP_LEVEL = _numBigStepLevel;
359     
360             if (_numBigStepLevel + 2 != _stakeAmounts.length) {
361                 revert StakeAmountsMismatch(_stakeAmounts.length, _numBigStepLevel + 2);
362             }
363             stakeAmounts = _stakeAmounts;
364         }


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/challengeV2/EdgeChallengeManager.sol#L0:0

```solidity
File: src/challengeV2/libraries/EdgeChallengeManagerLib.sol


213         function layerZeroTypeSpecificChecks(
214             EdgeStore storage store,
215             CreateEdgeArgs calldata args,
216             AssertionReferenceData memory ard,
217             IOneStepProofEntry oneStepProofEntry,
218             uint8 numBigStepLevel
219         ) private view returns (ProofData memory, bytes32) {
220             if (ChallengeEdgeLib.levelToType(args.level, numBigStepLevel) == EdgeType.Block) {
221                 // origin id is the assertion which is the root of challenge
222                 // all rivals and their children share the same origin id - it is a link to the information
223                 // they agree on
224                 bytes32 originId = ard.predecessorId;
225     
226                 // Sanity check: The assertion reference data should be related to the claim
227                 // Of course the caller can provide whatever args they wish, so this is really just a helpful
228                 // check to avoid mistakes
229                 if (ard.assertionHash == 0) {
230                     revert AssertionHashEmpty();
231                 }
232                 if (ard.assertionHash != args.claimId) {
233                     revert AssertionHashMismatch(ard.assertionHash, args.claimId);
234                 }
235     
236                 // if the assertion is already confirmed or rejected then it cant be referenced as a claim
237                 if (!ard.isPending) {
238                     revert AssertionNotPending();
239                 }
240     
241                 // if the claim doesnt have a sibling then it is undisputed, there's no need
242                 // to open challenge edges for it
243                 if (!ard.hasSibling) {
244                     revert AssertionNoSibling();
245                 }
246     
247                 // parse the inclusion proof for later use
248                 if (args.proof.length == 0) {
249                     revert EmptyEdgeSpecificProof();
250                 }
251                 (bytes32[] memory inclusionProof,,) =
252                     abi.decode(args.proof, (bytes32[], AssertionStateData, AssertionStateData));
253     
254                 // check the start and end execution states exist, the block hash entry should be non zero
255                 if (ard.startState.machineStatus == MachineStatus.RUNNING) {
256                     revert EmptyStartMachineStatus();
257                 }
258                 if (ard.endState.machineStatus == MachineStatus.RUNNING) {
259                     revert EmptyEndMachineStatus();
260                 }
261     
262                 // Create machine hashes out of the proven state
263                 bytes32 startStateHash = oneStepProofEntry.getMachineHash(ard.startState.toExecutionState());
264                 bytes32 endStateHash = oneStepProofEntry.getMachineHash(ard.endState.toExecutionState());
265     
266                 return (ProofData(startStateHash, endStateHash, inclusionProof), originId);
267             } else {
268                 // Claim must be length one. If it is unrivaled then its unrivaled time is ticking up, so there's
269                 // no need to create claims against it
270                 if (!hasLengthOneRival(store, args.claimId)) {
271                     revert ClaimEdgeNotLengthOneRival(args.claimId);
272                 }
273     
274                 // hasLengthOneRival checks existance, so we can use getNoCheck
275                 ChallengeEdge storage claimEdge = getNoCheck(store, args.claimId);
276     
277                 // origin id is the mutual id of the claim
278                 // all rivals and their children share the same origin id - it is a link to the information
279                 // they agree on
280                 bytes32 originId = claimEdge.mutualId();
281     
282                 // once a claim is confirmed it's status can never become pending again, so there is no point
283                 // opening a challenge that references it
284                 if (claimEdge.status != EdgeStatus.Pending) {
285                     revert ClaimEdgeNotPending();
286                 }
287     
288                 // the edge must be a level up from the claim
289                 if (args.level != nextEdgeLevel(claimEdge.level, numBigStepLevel)) {
290                     revert ClaimEdgeInvalidLevel(args.level, claimEdge.level);
291                 }
292     
293                 // parse the proofs
294                 if (args.proof.length == 0) {
295                     revert EmptyEdgeSpecificProof();
296                 }
297                 (
298                     bytes32 startState,
299                     bytes32 endState,
300                     bytes32[] memory claimStartInclusionProof,
301                     bytes32[] memory claimEndInclusionProof,
302                     bytes32[] memory edgeInclusionProof
303                 ) = abi.decode(args.proof, (bytes32, bytes32, bytes32[], bytes32[], bytes32[]));
304     
305                 // if the start and end states are consistent with the claim edge
306                 // this guarantees that the edge we're creating is a 'continuation' of the claim edge, it is
307                 // a commitment to the states that between start and end states of the claim
308                 MerkleTreeLib.verifyInclusionProof(
309                     claimEdge.startHistoryRoot, startState, claimEdge.startHeight, claimStartInclusionProof
310                 );
311     
312                 // it's doubly important to check the end state since if the end state since the claim id is
313                 // not part of the edge id, so we need to ensure that it's not possible to create two edges of the
314                 // same id, but with different claim id. Ensuring that the end state is linked to the claim,
315                 // and later ensuring that the end state is part of the history commitment of the new edge ensures
316                 // that the end history root of the new edge will be different for different claim ids, and therefore
317                 // the edge ids will be different
318                 MerkleTreeLib.verifyInclusionProof(
319                     claimEdge.endHistoryRoot, endState, claimEdge.endHeight, claimEndInclusionProof
320                 );
321     
322                 return (ProofData(startState, endState, edgeInclusionProof), originId);
323             }
324         }


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/challengeV2/libraries/EdgeChallengeManagerLib.sol#L0:0

```solidity
File: src/challengeV2/libraries/MerkleTreeLib.sol


151         function appendCompleteSubTree(bytes32[] memory me, uint256 level, bytes32 subtreeRoot)
152             internal
153             pure
154             returns (bytes32[] memory)
155         {
156             // we use number representations of the levels elsewhere, so we need to ensure we're appending a leve
157             // that's too high to use in uint
158             require(level < MAX_LEVEL, "Level too high");
159             require(subtreeRoot != 0, "Cannot append empty subtree");
160             require(me.length <= MAX_LEVEL, "Merkle expansion too large");
161     
162             if (me.length == 0) {
163                 bytes32[] memory empty = new bytes32[](level + 1);
164                 empty[level] = subtreeRoot;
165                 return empty;
166             }
167     
168             // This technically isn't necessary since it would be caught by the i < level check
169             // on the last loop of the for-loop below, but we add it for a clearer error message
170             require(level < me.length, "Level greater than highest level of current expansion");
171     
172             bytes32 accumHash = subtreeRoot;
173             uint256 meSize = treeSize(me);
174             uint256 postSize = meSize + 2 ** level;
175     
176             // if by appending the sub tree we increase the numbe of most sig bits of the size, that means
177             // we'll need more space in the expansion to describe the tree, so we enlarge by one
178             bytes32[] memory next = UintUtilsLib.mostSignificantBit(postSize) > UintUtilsLib.mostSignificantBit(meSize)
179                 ? new bytes32[](me.length + 1)
180                 : new bytes32[](me.length);
181     
182             // ensure we're never creating an expansion that's too big
183             require(next.length <= MAX_LEVEL, "Append creates oversize tree");
184     
185             // loop through all the levels in self and try to append the new subtree
186             // since each node has two children by appending a subtree we may complete another one
187             // in the level above. So we move through the levels updating the result at each level
188             for (uint256 i = 0; i < me.length; i++) {
189                 // we can only append at the level of the smallest complete sub tree or below
190                 // appending above this level would mean create "holes" in the tree
191                 // we can find the smallest complete sub tree by looking for the first entry in the merkle expansion
192                 if (i < level) {
193                     // we're below the level we want to append - no complete sub trees allowed down here
194                     // if the level is 0 there are no complete subtrees, and we therefore cannot be too low
195                     require(me[i] == 0, "Append above least significant bit");
196                 } else {
197                     // we're at or above the level
198                     if (accumHash == 0) {
199                         // no more changes to propagate upwards - just fill the tree
200                         next[i] = me[i];
201                     } else {
202                         // we have a change to propagate
203                         if (me[i] == 0) {
204                             // if the level is currently empty we can just add the change
205                             next[i] = accumHash;
206                             // and then there's nothing more to propagate
207                             accumHash = 0;
208                         } else {
209                             // if the level is not currently empty then we combine it with propagation
210                             // change, and propagate that to the level above. This level is now part of a complete subtree
211                             // so we zero it out
212                             next[i] = 0;
213                             accumHash = keccak256(abi.encodePacked(me[i], accumHash));
214                         }
215                     }
216                 }
217             }
218     
219             // we had a final change to propagate above the existing highest complete sub tree
220             // so we have a new highest complete sub tree in the level above - this was why we
221             // increased the storeage above
222             if (accumHash != 0) {
223                 next[next.length - 1] = accumHash;
224             }
225     
226             // it should never be possible to achieve this ever we sized the array correctly
227             // so this is just a sanity check
228             require(next[next.length - 1] != 0, "Last entry zero");
229     
230             return next;
231         }


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/challengeV2/libraries/MerkleTreeLib.sol#L0:0

```solidity
File: src/challengeV2/libraries/UintUtilsLib.sol


29          function mostSignificantBit(uint256 x) internal pure returns (uint256 msb) {
30              require(x != 0, "Zero has no significant bits");
31      
32              // x >= 2 ** 128
33              if (x >= 0x100000000000000000000000000000000) {
34                  x >>= 128;
35                  msb += 128;
36              }
37              // x >= 2 ** 64
38              if (x >= 0x10000000000000000) {
39                  x >>= 64;
40                  msb += 64;
41              }
42              // x >= 2 ** 32
43              if (x >= 0x100000000) {
44                  x >>= 32;
45                  msb += 32;
46              }
47              // x >= 2 ** 16
48              if (x >= 0x10000) {
49                  x >>= 16;
50                  msb += 16;
51              }
52              // x >= 2 ** 8
53              if (x >= 0x100) {
54                  x >>= 8;
55                  msb += 8;
56              }
57              // x >= 2 ** 4
58              if (x >= 0x10) {
59                  x >>= 4;
60                  msb += 4;
61              }
62              // x >= 2 ** 2
63              if (x >= 0x4) {
64                  x >>= 2;
65                  msb += 2;
66              }
67              // x >= 2 ** 1
68              if (x >= 0x2) msb += 1;
69          }


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/challengeV2/libraries/UintUtilsLib.sol#L0:0

</details>

## NC071 - Use of override is unnecessary:

Starting with Solidity version 0.8.8, using the override keyword when the function solely overrides an interface function, and the function doesn't exist in multiple base contracts, is unnecessary.


<details>
<summary>Click to show 33 findings</summary>

```solidity
File: src/bridge/SequencerInbox.sol


    function addSequencerL2Batch(
        uint256 sequenceNumber,
        bytes calldata data,
        uint256 afterDelayedMessagesRead,
        IGasRefunder gasRefunder,
        uint256 prevMessageCount,
        uint256 newMessageCount
    ) external override refundsGas(gasRefunder, IReader4844(address(0))) {
        if (!isBatchPoster[msg.sender] && msg.sender != address(rollup)) revert NotBatchPoster();
        if (isDelayProofRequired(afterDelayedMessagesRead)) revert DelayProofRequired();

        addSequencerL2BatchFromCalldataImpl(
            sequenceNumber,
            data,
            afterDelayedMessagesRead,
            prevMessageCount,
            newMessageCount,
            false
        );
    }

```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/bridge/SequencerInbox.sol#L560:579

```solidity
File: src/rollup/RollupAdminLogic.sol


    function initialize(Config calldata config, ContractDependencies calldata connectedContracts)
        external
        override
        onlyProxy
        initializer
    {
        rollupDeploymentBlock = block.number;
        bridge = connectedContracts.bridge;
        connectedContracts.bridge.setDelayedInbox(address(connectedContracts.inbox), true);
        connectedContracts.bridge.setSequencerInbox(address(connectedContracts.sequencerInbox));

        inbox = connectedContracts.inbox;
        outbox = connectedContracts.outbox;
        connectedContracts.bridge.setOutbox(address(connectedContracts.outbox), true);
        rollupEventInbox = connectedContracts.rollupEventInbox;

        // dont need to connect and initialize the event inbox if it's already been initialized
        if (!bridge.allowedDelayedInboxes(address(connectedContracts.rollupEventInbox))) {
            connectedContracts.bridge.setDelayedInbox(address(connectedContracts.rollupEventInbox), true);
            connectedContracts.rollupEventInbox.rollupInitialized(config.chainId, config.chainConfig);
        }

        if (connectedContracts.sequencerInbox.totalDelayedMessagesRead() == 0) {
            connectedContracts.sequencerInbox.addSequencerL2Batch(0, "", 1, IGasRefunder(address(0)), 0, 1);
        }

        validatorWalletCreator = connectedContracts.validatorWalletCreator;
        challengeManager = connectedContracts.challengeManager;

        confirmPeriodBlocks = config.confirmPeriodBlocks;
        chainId = config.chainId;
        baseStake = config.baseStake;
        wasmModuleRoot = config.wasmModuleRoot;
        // A little over 15 minutes
        minimumAssertionPeriod = 75;
        challengeGracePeriodBlocks = config.challengeGracePeriodBlocks;

        // loser stake is now sent directly to loserStakeEscrow, it must not
        // be address(0) because some token do not allow transfers to address(0)
        require(config.loserStakeEscrow != address(0), "INVALID_ESCROW_0");
        loserStakeEscrow = config.loserStakeEscrow;

        stakeToken = config.stakeToken;
        anyTrustFastConfirmer = config.anyTrustFastConfirmer;

        bytes32 parentAssertionHash = bytes32(0);
        bytes32 inboxAcc = bytes32(0);
        bytes32 genesisHash = RollupLib.assertionHash({
            parentAssertionHash: parentAssertionHash,
            afterStateHash: config.genesisAssertionState.hash(),
            inboxAcc: inboxAcc
        });

        uint256 currentInboxCount = bridge.sequencerMessageCount();
        // ensure to move the inbox forward by at least one message
        if (currentInboxCount == config.genesisInboxCount) {
            currentInboxCount += 1;
        }
        AssertionNode memory initialAssertion = AssertionNodeLib.createAssertion(
            true,
            RollupLib.configHash({
                wasmModuleRoot: wasmModuleRoot,
                requiredStake: baseStake,
                challengeManager: address(challengeManager),
                confirmPeriodBlocks: confirmPeriodBlocks,
                nextInboxPosition: uint64(currentInboxCount)
            })
        );
        initializeCore(initialAssertion, genesisHash);

        AssertionInputs memory assertionInputs;
        assertionInputs.afterState = config.genesisAssertionState;
        emit AssertionCreated(
            genesisHash,
            parentAssertionHash,
            assertionInputs,
            inboxAcc,
            currentInboxCount,
            wasmModuleRoot,
            baseStake,
            address(challengeManager),
            confirmPeriodBlocks
        );
        if (_hostChainIsArbitrum) {
            _assertionCreatedAtArbSysBlock[genesisHash] = ArbSys(address(100)).arbBlockNumber();
        }

        emit RollupInitialized(config.wasmModuleRoot, config.chainId);
    }

    function setOutbox(IOutbox _outbox) external override {
        outbox = _outbox;
        bridge.setOutbox(address(_outbox), true);
        emit OwnerFunctionCalled(0);
    }

    function removeOldOutbox(address _outbox) external override {
        require(_outbox != address(outbox), "CUR_OUTBOX");
        bridge.setOutbox(_outbox, false);
        emit OwnerFunctionCalled(1);
    }

    function setDelayedInbox(address _inbox, bool _enabled) external override {
        bridge.setDelayedInbox(address(_inbox), _enabled);
        emit OwnerFunctionCalled(2);
    }

    function pause() external override {
        _pause();
        emit OwnerFunctionCalled(3);
    }

    function resume() external override {
        _unpause();
        emit OwnerFunctionCalled(4);
    }

    function _authorizeUpgrade(address newImplementation) internal override {}

    function _authorizeSecondaryUpgrade(address newImplementation) internal override {}

    function setValidator(address[] calldata _validator, bool[] calldata _val) external override {
        require(_validator.length > 0, "EMPTY_ARRAY");
        require(_validator.length == _val.length, "WRONG_LENGTH");

        for (uint256 i = 0; i < _validator.length; i++) {
            isValidator[_validator[i]] = _val[i];
        }
        emit OwnerFunctionCalled(6);
    }

    function setOwner(address newOwner) external override {
        _changeAdmin(newOwner);
        emit OwnerFunctionCalled(7);
    }

    function setMinimumAssertionPeriod(uint256 newPeriod) external override {
        minimumAssertionPeriod = newPeriod;
        emit OwnerFunctionCalled(8);
    }

    function setConfirmPeriodBlocks(uint64 newConfirmPeriod) external override {
        require(newConfirmPeriod > 0, "INVALID_CONFIRM_PERIOD");
        confirmPeriodBlocks = newConfirmPeriod;
        emit OwnerFunctionCalled(9);
    }

    function setBaseStake(uint256 newBaseStake) external override {
        baseStake = newBaseStake;
        emit OwnerFunctionCalled(12);
    }

    function forceRefundStaker(address[] calldata staker) external override whenPaused {
        require(staker.length > 0, "EMPTY_ARRAY");
        for (uint256 i = 0; i < staker.length; i++) {
            requireInactiveStaker(staker[i]);
            reduceStakeTo(staker[i], 0);
        }
        emit OwnerFunctionCalled(22);
    }

    function forceCreateAssertion(
        bytes32 prevAssertionHash,
        AssertionInputs calldata assertion,
        bytes32 expectedAssertionHash
    ) external override whenPaused {
        // To update the wasm module root in the case of a bug:
        // 0. pause the contract
        // 1. update the wasm module root in the contract
        // 2. update the config hash of the assertion after which you wish to use the new wasm module root (functionality not written yet)
        // 3. force refund the stake of the current leaf assertion(s)
        // 4. create a new assertion using the assertion with the updated config has as a prev
        // 5. force confirm it - this is necessary to set latestConfirmed on the correct line
        // 6. unpause the contract

        // Normally, a new assertion is created using its prev's confirmPeriodBlocks
        // in the case of a force create, we use the rollup's current confirmPeriodBlocks
        createNewAssertion(assertion, prevAssertionHash, expectedAssertionHash);

        emit OwnerFunctionCalled(23);
    }

    function forceConfirmAssertion(
        bytes32 assertionHash,
        bytes32 parentAssertionHash,
        AssertionState calldata confirmState,
        bytes32 inboxAcc
    ) external override whenPaused {
        // this skip deadline, prev, challenge validations
        confirmAssertionInternal(assertionHash, parentAssertionHash, confirmState, inboxAcc);
        emit OwnerFunctionCalled(24);
    }

    function setLoserStakeEscrow(address newLoserStakerEscrow) external override {
        // loser stake is now sent directly to loserStakeEscrow, it must not
        // be address(0) because some token do not allow transfers to address(0)
        require(newLoserStakerEscrow != address(0), "INVALID_ESCROW_0");
        loserStakeEscrow = newLoserStakerEscrow;
        emit OwnerFunctionCalled(25);
    }

    function setWasmModuleRoot(bytes32 newWasmModuleRoot) external override {
        wasmModuleRoot = newWasmModuleRoot;
        emit OwnerFunctionCalled(26);
    }

    function setSequencerInbox(address _sequencerInbox) external override {
        bridge.setSequencerInbox(_sequencerInbox);
        emit OwnerFunctionCalled(27);
    }

```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/rollup/RollupAdminLogic.sol#L290:293

```solidity
File: src/rollup/RollupUserLogic.sol


    function initialize(address _stakeToken) external view override onlyProxy {
        require(_stakeToken != address(0), "NEED_STAKE_TOKEN");
    }

    function returnOldDeposit() external override onlyValidator whenNotPaused {
        requireInactiveStaker(msg.sender);
        withdrawStaker(msg.sender);
    }

    function withdrawStakerFunds() external override whenNotPaused returns (uint256) {
        uint256 amount = withdrawFunds(msg.sender);
        require(amount > 0, "NO_FUNDS_TO_WITHDRAW");
        // This is safe because it occurs after all checks and effects
        IERC20(stakeToken).safeTransfer(msg.sender, amount);
        return amount;
    }

```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/rollup/RollupUserLogic.sol#L358:364

```solidity
File: src/rollup/RollupCore.sol


    function getAssertion(bytes32 assertionHash) public view override returns (AssertionNode memory) {
        return getAssertionStorage(assertionHash);
    }

    function getAssertionCreationBlockForLogLookup(bytes32 assertionHash) external view override returns (uint256) {
        if (_hostChainIsArbitrum) {
            uint256 blockNum = _assertionCreatedAtArbSysBlock[assertionHash];
            require(blockNum > 0, "NO_ASSERTION");
            return blockNum;
        } else {
            AssertionNode storage assertion = getAssertionStorage(assertionHash);
            assertion.requireExists();
            return assertion.createdAtBlock;
        }
    }

    function getStakerAddress(uint64 stakerNum) external view override returns (address) {
        return _stakerList[stakerNum];
    }

    function isStaked(address staker) public view override returns (bool) {
        return _stakerMap[staker].isStaked;
    }

    function latestStakedAssertion(address staker) public view override returns (bytes32) {
        return _stakerMap[staker].latestStakedAssertion;
    }

    function amountStaked(address staker) public view override returns (uint256) {
        return _stakerMap[staker].amountStaked;
    }

    function getStaker(address staker) external view override returns (Staker memory) {
        return _stakerMap[staker];
    }

    function withdrawableFunds(address user) external view override returns (uint256) {
        return _withdrawableFunds[user];
    }

    function latestConfirmed() public view override returns (bytes32) {
        return _latestConfirmed;
    }

    function stakerCount() public view override returns (uint64) {
        return uint64(_stakerList.length);
    }

```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/rollup/RollupCore.sol#L217:219

</details>

## NC072 - Non-`external`/`public` function names should begin with an underscore:

According to the Solidity Style Guide, non-`external`/`public` function names should begin with an underscore


<details>
<summary>Click to show 4 findings</summary>

```solidity
File: src/bridge/SequencerInbox.sol


216         function getTimeBounds() internal view virtual returns (IBridge.TimeBounds memory) {
269         function maxTimeVariationInternal()
455         function addSequencerL2BatchFromBlobsImpl(
512         function addSequencerL2BatchFromCalldataImpl(
605         function delayProofImpl(uint256 afterDelayedMessagesRead, DelayProof memory delayProof)
628         function isDelayProofRequired(uint256 afterDelayedMessagesRead) internal view returns (bool) {
637         function packHeader(uint256 afterDelayedMessagesRead)
659         function formEmptyDataHash(uint256 afterDelayedMessagesRead)
675         function isValidCallDataFlag(bytes1 headerByte) internal pure returns (bool) {
688         function formCallDataHash(bytes calldata data, uint256 afterDelayedMessagesRead)
725         function formBlobDataHash(uint256 afterDelayedMessagesRead)
755         function submitBatchSpendingReport(
791         function addSequencerL2BatchImpl(
843         function delayBufferableBlocks(uint64 _buffer) internal view returns (uint64) {


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/bridge/SequencerInbox.sol#L0:0

```solidity
File: src/rollup/BOLDUpgradeAction.sol


341         function cleanupOldRollup() private {
367         function createConfig() private view returns (Config memory) {
411         function upgradeSurroundingContracts(address newRollupAddress) private {
433         function upgradeSequencerInbox() private {


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/rollup/BOLDUpgradeAction.sol#L0:0

```solidity
File: src/rollup/RollupCreator.sol


85          function createChallengeManager(address rollupAddr, address proxyAdminAddr, Config memory config)


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/rollup/RollupCreator.sol#L0:0

```solidity
File: src/rollup/RollupUserLogic.sol


366         function receiveTokens(uint256 tokenAmount) private {


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/rollup/RollupUserLogic.sol#L0:0

</details>

## NC073 - Unused import:

The identifier is imported but never used within the file


```solidity
File: src/bridge/SequencerInbox.sol


7       import {
8           AlreadyInit,
9           HadZeroInit,
10          BadPostUpgradeInit,
11          NotOrigin,
12          DataTooLarge,
13          DelayedBackwards,
14          DelayedTooFar,
15          ForceIncludeBlockTooSoon,
16          ForceIncludeTimeTooSoon,
17          IncorrectMessagePreimage,
18          NotBatchPoster,
19          BadSequencerNumber,
20          AlreadyValidDASKeyset,
21          NoSuchKeyset,
22          NotForked,
23          NotBatchPosterManager,
24          RollupNotChanged,
25          DataBlobsNotSupported,
26          InitParamZero,
27          MissingDataHashes,
28          NotOwner,
29          InvalidHeaderFlag,
30          NativeTokenMismatch,
31          BadMaxTimeVariation,
32          Deprecated,
33          NotDelayBufferable,
34          InvalidDelayedAccPreimage,
35          DelayProofRequired,
36          BadBufferConfig,
37          ExtraGasNotUint64,
38          KeysetTooLarge
39      } from "../libraries/Error.sol";
7       import {
8           AlreadyInit,
9           HadZeroInit,
10          BadPostUpgradeInit,
11          NotOrigin,
12          DataTooLarge,
13          DelayedBackwards,
14          DelayedTooFar,
15          ForceIncludeBlockTooSoon,
16          ForceIncludeTimeTooSoon,
17          IncorrectMessagePreimage,
18          NotBatchPoster,
19          BadSequencerNumber,
20          AlreadyValidDASKeyset,
21          NoSuchKeyset,
22          NotForked,
23          NotBatchPosterManager,
24          RollupNotChanged,
25          DataBlobsNotSupported,
26          InitParamZero,
27          MissingDataHashes,
28          NotOwner,
29          InvalidHeaderFlag,
30          NativeTokenMismatch,
31          BadMaxTimeVariation,
32          Deprecated,
33          NotDelayBufferable,
34          InvalidDelayedAccPreimage,
35          DelayProofRequired,
36          BadBufferConfig,
37          ExtraGasNotUint64,
38          KeysetTooLarge
39      } from "../libraries/Error.sol";
49      import {L1MessageType_batchPostingReport} from "../libraries/MessageTypes.sol";


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/bridge/SequencerInbox.sol#L0:0

```solidity
File: src/rollup/RollupUserLogic.sol


13      import {ETH_POS_BLOCK_TIME} from "../libraries/Constants.sol";


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/rollup/RollupUserLogic.sol#L0:0

## NC074 - Use `string.concat()` on strings instead of `abi.encodePacked()` for clearer semantic meaning:

Starting with version 0.8.12, Solidity has the `string.concat()` function, which allows one to concatenate a list of strings, without extra padding. Using this function rather than `abi.encodePacked()` makes the intended operation more clear, leading to less reviewer confusion.


```solidity
File: src/challengeV2/libraries/EdgeChallengeManagerLib.sol


135         bytes32 public constant UNRIVALED = keccak256(abi.encodePacked("UNRIVALED"));
135         bytes32 public constant UNRIVALED = keccak256(abi.encodePacked("UNRIVALED"));


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/challengeV2/libraries/EdgeChallengeManagerLib.sol#L0:0

```solidity
File: src/challengeV2/libraries/MerkleTreeLib.sol


241             return appendCompleteSubTree(me, 0, keccak256(abi.encodePacked(leaf)));
363             bytes32 calculatedRoot = MerkleLib.calculateRoot(proof, index, keccak256(abi.encodePacked(leaf)));


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/challengeV2/libraries/MerkleTreeLib.sol#L0:0

## NC075 - Unused function parameter:

Comment out the variable name to suppress compiler warnings.


```solidity
File: src/rollup/RollupAdminLogic.sol


166         function _authorizeUpgrade(address newImplementation) internal override {}
171         function _authorizeSecondaryUpgrade(address newImplementation) internal override {}


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/rollup/RollupAdminLogic.sol#L0:0

## NC076 - Put all system-wide constants in one file:

Putting all the system-wide constants in a single file improves code readability, makes it easier to understand the basic configuration and limitations of the system, and makes maintenance easier.


<details>
<summary>Click to show 11 findings</summary>

```solidity
File: src/bridge/DelayBuffer.sol


17          uint256 public constant BASIS = 10000;


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/bridge/DelayBuffer.sol#L17:17

```solidity
File: src/bridge/SequencerInbox.sol


70          uint256 public constant HEADER_LENGTH = 40;


73          bytes1 public constant DATA_AUTHENTICATED_FLAG = 0x40;


76          bytes1 public constant DATA_BLOB_HEADER_FLAG = DATA_AUTHENTICATED_FLAG | 0x10;


79          bytes1 public constant DAS_MESSAGE_HEADER_FLAG = 0x80;


82          bytes1 public constant TREE_DAS_MESSAGE_HEADER_FLAG = 0x08;


85          bytes1 public constant BROTLI_MESSAGE_HEADER_FLAG = 0x00;


88          bytes1 public constant ZERO_HEAVY_MESSAGE_HEADER_FLAG = 0x20;


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/bridge/SequencerInbox.sol#L88:88

```solidity
File: src/challengeV2/libraries/EdgeChallengeManagerLib.sol


135         bytes32 public constant UNRIVALED = keccak256(abi.encodePacked("UNRIVALED"));


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/challengeV2/libraries/EdgeChallengeManagerLib.sol#L135:135

```solidity
File: src/challengeV2/libraries/MerkleTreeLib.sol


104         uint256 public constant MAX_LEVEL = 64;


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/challengeV2/libraries/MerkleTreeLib.sol#L104:104

```solidity
File: src/rollup/RollupUserLogic.sol


49          uint256 public constant VALIDATOR_AFK_BLOCKS = 201600;


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/rollup/RollupUserLogic.sol#L49:49

</details>

## NC077 - Add inline comments for unnamed variables:

`function foo(address x, address)` -> `function foo(address x, address /* y */)`


```solidity
File: src/bridge/SequencerInbox.sol


356         function addSequencerL2BatchFromOrigin(
357             uint256,
358             bytes calldata,
359             uint256,
360             IGasRefunder
361         ) external pure {


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/bridge/SequencerInbox.sol#L0:0

## NC078 - Consider adding emergency-stop functionality:

Adding a way to quickly halt protocol functionality in an emergency, rather than having to pause individual contracts one-by-one, will make in-progress hack mitigation faster and much less stressful.


```solidity
File: src/rollup/BridgeCreator.sol


21      contract BridgeCreator is Ownable {


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/rollup/BridgeCreator.sol#L0:0

```solidity
File: src/rollup/RollupCreator.sol


17      contract RollupCreator is Ownable {


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/rollup/RollupCreator.sol#L0:0

## NC079 - Named imports of parent contracts are missing:

  


<details>
<summary>Click to show 18 findings</summary>

```solidity
File: src/assertionStakingPool/AssertionStakingPool.sol


21      contract AssertionStakingPool is AbsBoldStakingPool, IAssertionStakingPool {


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/assertionStakingPool/AssertionStakingPool.sol#L0:0

```solidity
File: src/assertionStakingPool/AssertionStakingPoolCreator.sol


13      contract AssertionStakingPoolCreator is IAssertionStakingPoolCreator {


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/assertionStakingPool/AssertionStakingPoolCreator.sol#L0:0

```solidity
File: src/assertionStakingPool/EdgeStakingPool.sol


25      contract EdgeStakingPool is AbsBoldStakingPool, IEdgeStakingPool {


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/assertionStakingPool/EdgeStakingPool.sol#L0:0

```solidity
File: src/assertionStakingPool/EdgeStakingPoolCreator.sol


13      contract EdgeStakingPoolCreator is IEdgeStakingPoolCreator {


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/assertionStakingPool/EdgeStakingPoolCreator.sol#L0:0

```solidity
File: src/assertionStakingPool/interfaces/IAssertionStakingPool.sol


10      interface IAssertionStakingPool is IAbsBoldStakingPool {


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/assertionStakingPool/interfaces/IAssertionStakingPool.sol#L0:0

```solidity
File: src/assertionStakingPool/interfaces/IEdgeStakingPool.sol


10      interface IEdgeStakingPool is IAbsBoldStakingPool {


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/assertionStakingPool/interfaces/IEdgeStakingPool.sol#L0:0

```solidity
File: src/bridge/ISequencerInbox.sol


15      interface ISequencerInbox is IDelayedMessageProvider {


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/bridge/ISequencerInbox.sol#L0:0

```solidity
File: src/bridge/SequencerInbox.sol


64      contract SequencerInbox is DelegateCallAware, GasRefundEnabled, ISequencerInbox {


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/bridge/SequencerInbox.sol#L0:0

```solidity
File: src/challengeV2/EdgeChallengeManager.sol


206     contract EdgeChallengeManager is IEdgeChallengeManager, Initializable {


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/challengeV2/EdgeChallengeManager.sol#L0:0

```solidity
File: src/rollup/BOLDUpgradeAction.sol


123     contract RollupReader is IOldRollup {


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/rollup/BOLDUpgradeAction.sol#L0:0

```solidity
File: src/rollup/BridgeCreator.sol


21      contract BridgeCreator is Ownable {


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/rollup/BridgeCreator.sol#L0:0

```solidity
File: src/rollup/IRollupCore.sol


15      interface IRollupCore is IAssertionChain {


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/rollup/IRollupCore.sol#L0:0

```solidity
File: src/rollup/IRollupLogic.sol


12      interface IRollupUser is IRollupCore, IOwnable {


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/rollup/IRollupLogic.sol#L0:0

```solidity
File: src/rollup/RollupAdminLogic.sol


15      contract RollupAdminLogic is RollupCore, IRollupAdmin, DoubleLogicUUPSUpgradeable {


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/rollup/RollupAdminLogic.sol#L0:0

```solidity
File: src/rollup/RollupCore.sol


22      abstract contract RollupCore is IRollupCore, PausableUpgradeable {


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/rollup/RollupCore.sol#L0:0

```solidity
File: src/rollup/RollupCreator.sol


17      contract RollupCreator is Ownable {


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/rollup/RollupCreator.sol#L0:0

```solidity
File: src/rollup/RollupProxy.sol


11      contract RollupProxy is AdminFallbackProxy {


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/rollup/RollupProxy.sol#L0:0

```solidity
File: src/rollup/RollupUserLogic.sol


15      contract RollupUserLogic is RollupCore, UUPSNotUpgradeable, IRollupUser {


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/rollup/RollupUserLogic.sol#L0:0

</details>

## NC080 - Unspecific Compiler Version Pragma:

  


```solidity
File: src/bridge/DelayBufferTypes.sol


pragma solidity >=0.6.9 <0.9.0;

```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/bridge/DelayBufferTypes.sol#L7:7

```solidity
File: src/bridge/ISequencerInbox.sol


pragma solidity >=0.6.9 <0.9.0;

```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/bridge/ISequencerInbox.sol#L6:6

## NC081 - Use `bytes.concat()` on bytes instead of `abi.encodePacked()` for clearer semantic meaning:

Starting with version 0.8.4, Solidity has the `bytes.concat()` function, which allows one to concatenate a list of bytes/strings, without extra padding. Using this function rather than `abi.encodePacked()` makes the intended operation more clear, leading to less reviewer confusion.


<details>
<summary>Click to show 4 findings</summary>

```solidity
File: src/assertionStakingPool/StakingPoolCreatorUtils.sol


14              bytes32 bytecodeHash = keccak256(abi.encodePacked(creationCode, args));


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/assertionStakingPool/StakingPoolCreatorUtils.sol#L0:0

```solidity
File: src/challengeV2/libraries/ChallengeEdgeLib.sol


198                 abi.encodePacked(
199                     mutualIdComponent(level, originId, startHeight, startHistoryRoot, endHeight), endHistoryRoot
200                 )


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/challengeV2/libraries/ChallengeEdgeLib.sol#L0:0

```solidity
File: src/challengeV2/libraries/MerkleTreeLib.sol


213                             accumHash = keccak256(abi.encodePacked(me[i], accumHash));
132                     accum = keccak256(abi.encodePacked(val, accum));
241             return appendCompleteSubTree(me, 0, keccak256(abi.encodePacked(leaf)));
126                             accum = keccak256(abi.encodePacked(accum, bytes32(0)));
363             bytes32 calculatedRoot = MerkleLib.calculateRoot(proof, index, keccak256(abi.encodePacked(leaf)));
135                     accum = keccak256(abi.encodePacked(accum, bytes32(0)));


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/challengeV2/libraries/MerkleTreeLib.sol#L0:0

```solidity
File: src/rollup/RollupLib.sol


45                      abi.encodePacked(
46                          parentAssertionHash,
47                          afterStateHash,
48                          inboxAcc
49                      )


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/rollup/RollupLib.sol#L0:0

</details>

## NC082 - Consider using `SafeTransferLib.safeTransferETH()` or `Address.sendValue()` for clearer semantic meaning:

These Functions indicate their purpose with their name more clearly than using low-level calls.


```solidity
File: src/rollup/RollupCreator.sol


304                 (bool sent, ) = msg.sender.call{value: address(this).balance}("");


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/rollup/RollupCreator.sol#L0:0

## NC083 - Style guide: State and local variables should be named using lowerCamelCase:

The Solidity style guide says to use mixedCase for local and state variable names. Note that while OpenZeppelin may not follow this advice, it still is the recommended way of naming variables.


```solidity
File: src/bridge/SequencerInbox.sol


99          ISequencerInbox.MaxTimeVariation private __LEGACY_MAX_TIME_VARIATION;
329             uint256 __totalDelayedMessagesRead = _totalDelayedMessagesRead;


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/bridge/SequencerInbox.sol#L0:0

```solidity
File: src/challengeV2/EdgeChallengeManager.sol


291         uint256 public LAYERZERO_BLOCKEDGE_HEIGHT;
293         uint256 public LAYERZERO_BIGSTEPEDGE_HEIGHT;
295         uint256 public LAYERZERO_SMALLSTEPEDGE_HEIGHT;
298         uint8 public NUM_BIGSTEP_LEVEL;


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/challengeV2/EdgeChallengeManager.sol#L0:0

```solidity
File: src/rollup/BOLDUpgradeAction.sol


185         uint256 public immutable BLOCK_LEAF_SIZE;
186         uint256 public immutable BIGSTEP_LEAF_SIZE;
187         uint256 public immutable SMALLSTEP_LEAF_SIZE;
188         uint8 public immutable NUM_BIGSTEP_LEVEL;
190         address public immutable L1_TIMELOCK;
191         IOldRollup public immutable OLD_ROLLUP;
192         address public immutable BRIDGE;
193         address public immutable SEQ_INBOX;
194         address public immutable REI;
195         address public immutable OUTBOX;
196         address public immutable INBOX;
198         uint64 public immutable CONFIRM_PERIOD_BLOCKS;
199         uint64 public immutable CHALLENGE_PERIOD_BLOCKS;
200         address public immutable STAKE_TOKEN;
201         uint256 public immutable STAKE_AMOUNT;
202         uint256 public immutable CHAIN_ID;
203         address public immutable ANY_TRUST_FAST_CONFIRMER;
204         bool public immutable DISABLE_VALIDATOR_WHITELIST;
205         uint64 public immutable CHALLENGE_GRACE_PERIOD_BLOCKS;
206         address public immutable MINI_STAKE_AMOUNTS_STORAGE;
207         bool public immutable IS_DELAY_BUFFERABLE;
209         uint64 public immutable MAX;
210         uint64 public immutable THRESHOLD;
211         uint64 public immutable REPLENISH_RATE_IN_BASIS;
213         IOneStepProofEntry public immutable OSP;
215         ProxyAdmin public immutable PROXY_ADMIN_OUTBOX;
216         ProxyAdmin public immutable PROXY_ADMIN_BRIDGE;
217         ProxyAdmin public immutable PROXY_ADMIN_REI;
218         ProxyAdmin public immutable PROXY_ADMIN_SEQUENCER_INBOX;
219         ProxyAdmin public immutable PROXY_ADMIN_INBOX;
220         StateHashPreImageLookup public immutable PREIMAGE_LOOKUP;
221         RollupReader public immutable ROLLUP_READER;
224         address public immutable IMPL_BRIDGE;
225         address public immutable IMPL_SEQUENCER_INBOX;
226         address public immutable IMPL_INBOX;
227         address public immutable IMPL_REI;
228         address public immutable IMPL_OUTBOX;
230         address public immutable IMPL_PATCHED_OLD_ROLLUP_USER;
231         address public immutable IMPL_NEW_ROLLUP_USER;
232         address public immutable IMPL_NEW_ROLLUP_ADMIN;
233         address public immutable IMPL_CHALLENGE_MANAGER;


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/rollup/BOLDUpgradeAction.sol#L0:0

## NC084 - Unnecessary cast:

The variable is being cast to its own type


<details>
<summary>Click to show 4 findings</summary>

```solidity
File: src/assertionStakingPool/EdgeStakingPool.sol


46              IERC20(stakeToken).safeIncreaseAllowance(address(challengeManager), requiredStake);


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/assertionStakingPool/EdgeStakingPool.sol#L0:0

```solidity
File: src/rollup/BOLDUpgradeAction.sol


475                         address(IMPL_CHALLENGE_MANAGER),


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/rollup/BOLDUpgradeAction.sol#L0:0

```solidity
File: src/rollup/RollupAdminLogic.sol


139             bridge.setDelayedInbox(address(_inbox), _enabled);


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/rollup/RollupAdminLogic.sol#L0:0

```solidity
File: src/rollup/RollupCreator.sol


204             proxyAdmin.transferOwnership(address(upgradeExecutor));
241             IRollupAdmin(address(rollup)).setOwner(address(upgradeExecutor));
261                 address(upgradeExecutor),
262                 address(validatorWalletCreator)


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/rollup/RollupCreator.sol#L0:0

</details>

## NC085 - Use the latest solidity (prior to 0.8.20 if on L2s) for deployment:

Since deployed contracts should not use floating pragmas, I've flagged all instances where a version prior to 0.8.19 is allowed by the version pragma


<details>
<summary>Click to show 39 findings</summary>

```solidity
File: src/assertionStakingPool/AbsBoldStakingPool.sol


5       pragma solidity ^0.8.0;


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/assertionStakingPool/AbsBoldStakingPool.sol#L0:0

```solidity
File: src/assertionStakingPool/AssertionStakingPool.sol


6       pragma solidity ^0.8.0;


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/assertionStakingPool/AssertionStakingPool.sol#L0:0

```solidity
File: src/assertionStakingPool/AssertionStakingPoolCreator.sol


6       pragma solidity ^0.8.0;


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/assertionStakingPool/AssertionStakingPoolCreator.sol#L0:0

```solidity
File: src/assertionStakingPool/EdgeStakingPool.sol


5       pragma solidity ^0.8.0;


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/assertionStakingPool/EdgeStakingPool.sol#L0:0

```solidity
File: src/assertionStakingPool/EdgeStakingPoolCreator.sol


6       pragma solidity ^0.8.0;


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/assertionStakingPool/EdgeStakingPoolCreator.sol#L0:0

```solidity
File: src/assertionStakingPool/StakingPoolCreatorUtils.sol


6       pragma solidity ^0.8.0;


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/assertionStakingPool/StakingPoolCreatorUtils.sol#L0:0

```solidity
File: src/assertionStakingPool/interfaces/IAbsBoldStakingPool.sol


5       pragma solidity ^0.8.0;


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/assertionStakingPool/interfaces/IAbsBoldStakingPool.sol#L0:0

```solidity
File: src/assertionStakingPool/interfaces/IAssertionStakingPool.sol


5       pragma solidity ^0.8.0;


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/assertionStakingPool/interfaces/IAssertionStakingPool.sol#L0:0

```solidity
File: src/assertionStakingPool/interfaces/IAssertionStakingPoolCreator.sol


5       pragma solidity ^0.8.0;


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/assertionStakingPool/interfaces/IAssertionStakingPoolCreator.sol#L0:0

```solidity
File: src/assertionStakingPool/interfaces/IEdgeStakingPool.sol


5       pragma solidity ^0.8.0;


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/assertionStakingPool/interfaces/IEdgeStakingPool.sol#L0:0

```solidity
File: src/assertionStakingPool/interfaces/IEdgeStakingPoolCreator.sol


5       pragma solidity ^0.8.0;


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/assertionStakingPool/interfaces/IEdgeStakingPoolCreator.sol#L0:0

```solidity
File: src/bridge/DelayBuffer.sol


5       pragma solidity ^0.8.0;


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/bridge/DelayBuffer.sol#L0:0

```solidity
File: src/bridge/DelayBufferTypes.sol


7       pragma solidity >=0.6.9 <0.9.0;


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/bridge/DelayBufferTypes.sol#L0:0

```solidity
File: src/bridge/ISequencerInbox.sol


6       pragma solidity >=0.6.9 <0.9.0;


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/bridge/ISequencerInbox.sol#L0:0

```solidity
File: src/bridge/SequencerInbox.sol


5       pragma solidity ^0.8.0;


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/bridge/SequencerInbox.sol#L0:0

```solidity
File: src/challengeV2/EdgeChallengeManager.sol


5       pragma solidity ^0.8.17;


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/challengeV2/EdgeChallengeManager.sol#L0:0

```solidity
File: src/challengeV2/IAssertionChain.sol


5       pragma solidity ^0.8.17;


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/challengeV2/IAssertionChain.sol#L0:0

```solidity
File: src/challengeV2/libraries/ArrayUtilsLib.sol


5       pragma solidity ^0.8.17;


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/challengeV2/libraries/ArrayUtilsLib.sol#L0:0

```solidity
File: src/challengeV2/libraries/ChallengeEdgeLib.sol


5       pragma solidity ^0.8.17;


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/challengeV2/libraries/ChallengeEdgeLib.sol#L0:0

```solidity
File: src/challengeV2/libraries/ChallengeErrors.sol


5       pragma solidity ^0.8.17;


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/challengeV2/libraries/ChallengeErrors.sol#L0:0

```solidity
File: src/challengeV2/libraries/EdgeChallengeManagerLib.sol


5       pragma solidity ^0.8.17;


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/challengeV2/libraries/EdgeChallengeManagerLib.sol#L0:0

```solidity
File: src/challengeV2/libraries/Enums.sol


5       pragma solidity ^0.8.17;


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/challengeV2/libraries/Enums.sol#L0:0

```solidity
File: src/challengeV2/libraries/MerkleTreeLib.sol


5       pragma solidity ^0.8.17;


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/challengeV2/libraries/MerkleTreeLib.sol#L0:0

```solidity
File: src/challengeV2/libraries/UintUtilsLib.sol


5       pragma solidity ^0.8.17;


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/challengeV2/libraries/UintUtilsLib.sol#L0:0

```solidity
File: src/libraries/Error.sol


5       pragma solidity ^0.8.4;


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/libraries/Error.sol#L0:0

```solidity
File: src/rollup/Assertion.sol


5       pragma solidity ^0.8.0;


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/rollup/Assertion.sol#L0:0

```solidity
File: src/rollup/AssertionState.sol


5       pragma solidity ^0.8.0;


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/rollup/AssertionState.sol#L0:0

```solidity
File: src/rollup/BOLDUpgradeAction.sol


5       pragma solidity ^0.8.0;


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/rollup/BOLDUpgradeAction.sol#L0:0

```solidity
File: src/rollup/BridgeCreator.sol


5       pragma solidity ^0.8.0;


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/rollup/BridgeCreator.sol#L0:0

```solidity
File: src/rollup/Config.sol


5       pragma solidity ^0.8.0;


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/rollup/Config.sol#L0:0

```solidity
File: src/rollup/IRollupAdmin.sol


5       pragma solidity ^0.8.0;


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/rollup/IRollupAdmin.sol#L0:0

```solidity
File: src/rollup/IRollupCore.sol


5       pragma solidity ^0.8.0;


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/rollup/IRollupCore.sol#L0:0

```solidity
File: src/rollup/IRollupLogic.sol


5       pragma solidity ^0.8.0;


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/rollup/IRollupLogic.sol#L0:0

```solidity
File: src/rollup/RollupAdminLogic.sol


5       pragma solidity ^0.8.0;


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/rollup/RollupAdminLogic.sol#L0:0

```solidity
File: src/rollup/RollupCore.sol


5       pragma solidity ^0.8.0;


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/rollup/RollupCore.sol#L0:0

```solidity
File: src/rollup/RollupCreator.sol


5       pragma solidity ^0.8.0;


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/rollup/RollupCreator.sol#L0:0

```solidity
File: src/rollup/RollupLib.sol


5       pragma solidity ^0.8.0;


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/rollup/RollupLib.sol#L0:0

```solidity
File: src/rollup/RollupProxy.sol


5       pragma solidity ^0.8.0;


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/rollup/RollupProxy.sol#L0:0

```solidity
File: src/rollup/RollupUserLogic.sol


5       pragma solidity ^0.8.0;


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/rollup/RollupUserLogic.sol#L0:0

</details>

## NC086 - Events should use parameters to convey information:

For example, rather than using event Paused() and event Unpaused(), use event PauseState(address indexed whoChangedIt, bool wasPaused, bool isNowPaused)


```solidity
File: src/rollup/BridgeCreator.sol


55              emit TemplatesUpdated();
60              emit ERC20TemplatesUpdated();


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/rollup/BridgeCreator.sol#L0:0

```solidity
File: src/rollup/RollupCreator.sol


81              emit TemplatesUpdated();


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/rollup/RollupCreator.sol#L0:0

## NC087 - Visibility should be set explicitly rather than defaulting to internal:

Visibility of state variables should be set explicitly rather than defaulting to internal.


```solidity
File: src/rollup/BOLDUpgradeAction.sol


167         uint256[] _array;


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/rollup/BOLDUpgradeAction.sol#L0:0

## NC088 - Event declarations should have NatSpec @param annotations:

Documents a parameter just like in Doxygen (must be followed by parameter name)


<details>
<summary>Click to show 8 findings</summary>

```solidity
File: src/assertionStakingPool/interfaces/IAbsBoldStakingPool.sol


9           event StakeDeposited(address indexed sender, uint256 amount);
11          event StakeWithdrawn(address indexed sender, uint256 amount);


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/assertionStakingPool/interfaces/IAbsBoldStakingPool.sol#L0:0

```solidity
File: src/assertionStakingPool/interfaces/IAssertionStakingPoolCreator.sol


12          event NewAssertionPoolCreated(


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/assertionStakingPool/interfaces/IAssertionStakingPoolCreator.sol#L0:0

```solidity
File: src/assertionStakingPool/interfaces/IEdgeStakingPoolCreator.sol


11          event NewEdgeStakingPoolCreated(address indexed challengeManager, bytes32 indexed edgeId);


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/assertionStakingPool/interfaces/IEdgeStakingPoolCreator.sol#L0:0

```solidity
File: src/bridge/ISequencerInbox.sol


28          event SequencerBatchDelivered(
38          event OwnerFunctionCalled(uint256 indexed id);
41          event SequencerBatchData(uint256 indexed batchSequenceNumber, bytes data);
44          event SetValidKeyset(bytes32 indexed keysetHash, bytes keysetBytes);
47          event InvalidateKeyset(bytes32 indexed keysetHash);


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/bridge/ISequencerInbox.sol#L0:0

```solidity
File: src/rollup/BOLDUpgradeAction.sol


56          event NodeCreated(
97          event HashSet(bytes32 h, ExecutionState executionState, uint256 inboxMaxCount);
235         event RollupMigrated(address rollup, address challengeManager);


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/rollup/BOLDUpgradeAction.sol#L0:0

```solidity
File: src/rollup/IRollupAdmin.sol


14          event OwnerFunctionCalled(uint256 indexed id);


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/rollup/IRollupAdmin.sol#L0:0

```solidity
File: src/rollup/IRollupCore.sol


24          event RollupInitialized(bytes32 machineHash, uint256 chainId);
26          event AssertionCreated(
38          event AssertionConfirmed(bytes32 indexed assertionHash, bytes32 blockHash, bytes32 sendRoot);
40          event RollupChallengeStarted(
44          event UserStakeUpdated(address indexed user, address indexed withdrawalAddress, uint256 initialBalance, uint256 finalBalance);
46          event UserWithdrawableFundsUpdated(address indexed user, uint256 initialBalance, uint256 finalBalance);


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/rollup/IRollupCore.sol#L0:0

```solidity
File: src/rollup/RollupCreator.sol


20          event RollupCreated(


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/rollup/RollupCreator.sol#L0:0

</details>

## NC089 - Event declarations should have NatSpec @dev annotations:

Explain to a developer any extra details


<details>
<summary>Click to show 10 findings</summary>

```solidity
File: src/assertionStakingPool/interfaces/IAbsBoldStakingPool.sol


9           event StakeDeposited(address indexed sender, uint256 amount);
11          event StakeWithdrawn(address indexed sender, uint256 amount);


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/assertionStakingPool/interfaces/IAbsBoldStakingPool.sol#L0:0

```solidity
File: src/assertionStakingPool/interfaces/IAssertionStakingPoolCreator.sol


12          event NewAssertionPoolCreated(


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/assertionStakingPool/interfaces/IAssertionStakingPoolCreator.sol#L0:0

```solidity
File: src/assertionStakingPool/interfaces/IEdgeStakingPoolCreator.sol


11          event NewEdgeStakingPoolCreated(address indexed challengeManager, bytes32 indexed edgeId);


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/assertionStakingPool/interfaces/IEdgeStakingPoolCreator.sol#L0:0

```solidity
File: src/bridge/ISequencerInbox.sol


28          event SequencerBatchDelivered(
38          event OwnerFunctionCalled(uint256 indexed id);


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/bridge/ISequencerInbox.sol#L0:0

```solidity
File: src/challengeV2/EdgeChallengeManager.sol


219         event EdgeAdded(
235         event EdgeBisected(
243         event EdgeConfirmedByTime(bytes32 indexed edgeId, bytes32 indexed mutualId, uint256 totalTimeUnrivaled);
248         event EdgeConfirmedByOneStepProof(bytes32 indexed edgeId, bytes32 indexed mutualId);
253         event TimerCacheUpdated(bytes32 indexed edgeId, uint256 newValue);
260         event EdgeRefunded(bytes32 indexed edgeId, bytes32 indexed mutualId, address stakeToken, uint256 stakeAmount);


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/challengeV2/EdgeChallengeManager.sol#L0:0

```solidity
File: src/rollup/BOLDUpgradeAction.sol


56          event NodeCreated(
97          event HashSet(bytes32 h, ExecutionState executionState, uint256 inboxMaxCount);
235         event RollupMigrated(address rollup, address challengeManager);


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/rollup/BOLDUpgradeAction.sol#L0:0

```solidity
File: src/rollup/BridgeCreator.sol


25          event TemplatesUpdated();
26          event ERC20TemplatesUpdated();


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/rollup/BridgeCreator.sol#L0:0

```solidity
File: src/rollup/IRollupAdmin.sol


14          event OwnerFunctionCalled(uint256 indexed id);


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/rollup/IRollupAdmin.sol#L0:0

```solidity
File: src/rollup/IRollupCore.sol


24          event RollupInitialized(bytes32 machineHash, uint256 chainId);
26          event AssertionCreated(
38          event AssertionConfirmed(bytes32 indexed assertionHash, bytes32 blockHash, bytes32 sendRoot);
40          event RollupChallengeStarted(
44          event UserStakeUpdated(address indexed user, address indexed withdrawalAddress, uint256 initialBalance, uint256 finalBalance);
46          event UserWithdrawableFundsUpdated(address indexed user, uint256 initialBalance, uint256 finalBalance);


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/rollup/IRollupCore.sol#L0:0

```solidity
File: src/rollup/RollupCreator.sol


20          event RollupCreated(
33          event TemplatesUpdated();


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/rollup/RollupCreator.sol#L0:0

</details>

## NC090 - Function definitions should have NatSpec @dev annotations:

Explain to a developer any extra details


<details>
<summary>Click to show 33 findings</summary>

```solidity
File: src/assertionStakingPool/AbsBoldStakingPool.sol


24          constructor(address _stakeToken) {
29          function depositIntoPool(uint256 amount) external {
41          function withdrawFromPool(uint256 amount) public {
57          function withdrawFromPool() external {


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/assertionStakingPool/AbsBoldStakingPool.sol#L0:0

```solidity
File: src/assertionStakingPool/AssertionStakingPool.sol


31          constructor(
40          function createAssertion(AssertionInputs calldata assertionInputs) external {
49          function makeStakeWithdrawable() public {
55          function withdrawStakeBackIntoPool() public {
60          function makeStakeWithdrawableAndWithdrawBackIntoPool() external {


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/assertionStakingPool/AssertionStakingPool.sol#L0:0

```solidity
File: src/assertionStakingPool/AssertionStakingPoolCreator.sol


15          function createPool(
25          function getPool(


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/assertionStakingPool/AssertionStakingPoolCreator.sol#L0:0

```solidity
File: src/assertionStakingPool/EdgeStakingPool.sol


35          constructor(
44          function createEdge(CreateEdgeArgs calldata args) external {


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/assertionStakingPool/EdgeStakingPool.sol#L0:0

```solidity
File: src/assertionStakingPool/EdgeStakingPoolCreator.sol


15          function createPool(
25          function getPool(


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/assertionStakingPool/EdgeStakingPoolCreator.sol#L0:0

```solidity
File: src/assertionStakingPool/StakingPoolCreatorUtils.sol


13          function getPool(bytes memory creationCode, bytes memory args) internal view returns (address) {


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/assertionStakingPool/StakingPoolCreatorUtils.sol#L0:0

```solidity
File: src/assertionStakingPool/interfaces/IAbsBoldStakingPool.sol


20          function depositIntoPool(uint256 amount) external;
24          function withdrawFromPool(uint256 amount) external;
27          function withdrawFromPool() external;
30          function stakeToken() external view returns (address);
34          function depositBalance(address account) external view returns (uint256);


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/assertionStakingPool/interfaces/IAbsBoldStakingPool.sol#L0:0

```solidity
File: src/assertionStakingPool/interfaces/IAssertionStakingPool.sol


12          function createAssertion(AssertionInputs calldata assertionInputs) external;
24          function makeStakeWithdrawableAndWithdrawBackIntoPool() external;
27          function rollup() external view returns (address);
30          function assertionHash() external view returns (bytes32);


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/assertionStakingPool/interfaces/IAssertionStakingPool.sol#L0:0

```solidity
File: src/assertionStakingPool/interfaces/IAssertionStakingPoolCreator.sol


21          function createPool(
29          function getPool(


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/assertionStakingPool/interfaces/IAssertionStakingPoolCreator.sol#L0:0

```solidity
File: src/assertionStakingPool/interfaces/IEdgeStakingPool.sol


15          function createEdge(CreateEdgeArgs calldata args) external;
18          function challengeManager() external view returns (address);
21          function edgeId() external view returns (bytes32);


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/assertionStakingPool/interfaces/IEdgeStakingPool.sol#L0:0

```solidity
File: src/assertionStakingPool/interfaces/IEdgeStakingPoolCreator.sol


16          function createPool(
24          function getPool(


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/assertionStakingPool/interfaces/IEdgeStakingPoolCreator.sol#L0:0

```solidity
File: src/bridge/DelayBuffer.sol


68          function update(BufferData storage self, uint64 blockNumber) internal {
108         function isUpdatable(BufferData storage self) internal view returns (bool) {
115         function isValidBufferConfig(BufferConfig memory config) internal pure returns (bool) {


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/bridge/DelayBuffer.sol#L0:0

```solidity
File: src/bridge/ISequencerInbox.sol


49          function totalDelayedMessagesRead() external view returns (uint256);
51          function bridge() external view returns (IBridge);
93          function rollup() external view returns (IOwnable);
95          function isBatchPoster(address) external view returns (bool);
97          function isSequencer(address) external view returns (bool);
100         function isDelayBufferable() external view returns (bool);
102         function maxDataSize() external view returns (uint256);
106         function batchPosterManager() external view returns (address);
124         function dasKeySetInfo(bytes32) external view returns (bool, uint64);
127         function removeDelayAfterFork() external;
139         function forceInclusion(
148         function inboxAccs(uint256 index) external view returns (bytes32);
150         function batchCount() external view returns (uint256);
152         function isValidKeysetHash(bytes32 ksHash) external view returns (bool);
155         function getKeysetCreationBlock(bytes32 ksHash) external view returns (uint256);
188         function addSequencerL2Batch(
197         function addSequencerL2BatchFromBlobs(
247         function setMaxTimeVariation(MaxTimeVariation memory maxTimeVariation_) external;
254         function setIsBatchPoster(address addr, bool isBatchPoster_) external;
260         function setValidKeyset(bytes calldata keysetBytes) external;
266         function invalidateKeysetHash(bytes32 ksHash) external;
280         function setBatchPosterManager(address newBatchPosterManager) external;
283         function updateRollupAddress() external;
287         function initialize(


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/bridge/ISequencerInbox.sol#L0:0

```solidity
File: src/bridge/SequencerInbox.sol


140         constructor(
157         function _chainIdChanged() internal view returns (bool) {
161         function postUpgradeInit(BufferConfig memory bufferConfig_)
177         function initialize(
208         function updateRollupAddress() external {
216         function getTimeBounds() internal view virtual returns (IBridge.TimeBounds memory) {
236         function removeDelayAfterFork() external {
244         function maxTimeVariation()
269         function maxTimeVariationInternal()
287         function forceInclusion(
356         function addSequencerL2BatchFromOrigin(
366         function addSequencerL2BatchFromOrigin(
390         function addSequencerL2BatchFromBlobs(
409         function addSequencerL2BatchFromBlobsDelayProof(
430         function addSequencerL2BatchFromOriginDelayProof(
455         function addSequencerL2BatchFromBlobsImpl(
512         function addSequencerL2BatchFromCalldataImpl(
560         function addSequencerL2Batch(
582         function addSequencerL2BatchDelayProof(
605         function delayProofImpl(uint256 afterDelayedMessagesRead, DelayProof memory delayProof)
628         function isDelayProofRequired(uint256 afterDelayedMessagesRead) internal view returns (bool) {
637         function packHeader(uint256 afterDelayedMessagesRead)
791         function addSequencerL2BatchImpl(
824         function inboxAccs(uint256 index) external view returns (bytes32) {
828         function batchCount() external view returns (uint256) {
833         function forceInclusionDeadline(uint64 blockNumber) external view returns (uint64) {
843         function delayBufferableBlocks(uint64 _buffer) internal view returns (uint64) {
847         function _setBufferConfig(BufferConfig memory bufferConfig_) internal {
867         function _setMaxTimeVariation(ISequencerInbox.MaxTimeVariation memory maxTimeVariation_)
885         function setMaxTimeVariation(ISequencerInbox.MaxTimeVariation memory maxTimeVariation_)
894         function setIsBatchPoster(address addr, bool isBatchPoster_)
903         function setValidKeyset(bytes calldata keysetBytes) external onlyRollupOwner {
922         function invalidateKeysetHash(bytes32 ksHash) external onlyRollupOwner {
933         function setIsSequencer(address addr, bool isSequencer_)
942         function setBatchPosterManager(address newBatchPosterManager) external onlyRollupOwner {
947         function setBufferConfig(BufferConfig memory bufferConfig_) external onlyRollupOwner {
952         function isValidKeysetHash(bytes32 ksHash) external view returns (bool) {
957         function getKeysetCreationBlock(bytes32 ksHash) external view returns (uint256) {


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/bridge/SequencerInbox.sol#L0:0

```solidity
File: src/challengeV2/EdgeChallengeManager.sol


34          function initialize(
47          function challengePeriodBlocks() external view returns (uint64);
50          function oneStepProofEntry() external view returns (IOneStepProofEntry);
54          function createLayerZeroEdge(CreateEdgeArgs calldata args) external returns (bytes32);
68          function bisectEdge(bytes32 edgeId, bytes32 bisectionHistoryRoot, bytes calldata prefixProof)
84          function multiUpdateTimeCacheByChildren(bytes32[] calldata edgeIds) external;
100         function updateTimerCacheByClaim(bytes32 edgeId, bytes32 claimingEdgeId) external;
119         function refundStake(bytes32 edgeId) external;
123         function getLayerZeroEndHeight(EdgeType eType) external view returns (uint256);
132         function calculateEdgeId(
148         function calculateMutualId(
157         function edgeExists(bytes32 edgeId) external view returns (bool);
160         function getEdge(bytes32 edgeId) external view returns (ChallengeEdge memory);
163         function edgeLength(bytes32 edgeId) external view returns (uint256);
167         function hasRival(bytes32 edgeId) external view returns (bool);
171         function confirmedRival(bytes32 mutualId) external view returns (bytes32);
174         function hasLengthOneRival(bytes32 edgeId) external view returns (bool);
180         function timeUnrivaled(bytes32 edgeId) external view returns (uint256);
195         function hasMadeLayerZeroRival(address account, bytes32 mutualId) external view returns (bool);
300         constructor() {
305         function initialize(
371         function createLayerZeroEdge(CreateEdgeArgs calldata args) external returns (bytes32) {
451         function bisectEdge(bytes32 edgeId, bytes32 bisectionHistoryRoot, bytes calldata prefixProof)
491         function multiUpdateTimeCacheByChildren(bytes32[] calldata edgeIds) public {
499         function updateTimerCacheByChildren(bytes32 edgeId) public {
505         function updateTimerCacheByClaim(bytes32 edgeId, bytes32 claimingEdgeId) public {
511         function confirmEdgeByTime(bytes32 edgeId, AssertionStateData calldata claimStateData) public {
539         function confirmEdgeByOneStepProof(
572         function refundStake(bytes32 edgeId) public {
591         function getLayerZeroEndHeight(EdgeType eType) public view returns (uint256) {
604         function calculateEdgeId(
616         function calculateMutualId(
627         function edgeExists(bytes32 edgeId) public view returns (bool) {
632         function getEdge(bytes32 edgeId) public view returns (ChallengeEdge memory) {
637         function edgeLength(bytes32 edgeId) public view returns (uint256) {
642         function hasRival(bytes32 edgeId) public view returns (bool) {
647         function confirmedRival(bytes32 mutualId) public view returns (bytes32) {
652         function hasLengthOneRival(bytes32 edgeId) public view returns (bool) {
657         function timeUnrivaled(bytes32 edgeId) public view returns (uint256) {
662         function getPrevAssertionHash(bytes32 edgeId) public view returns (bytes32) {
667         function firstRival(bytes32 mutualId) public view returns (bytes32) {
672         function hasMadeLayerZeroRival(address account, bytes32 mutualId) external view returns (bool) {


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/challengeV2/EdgeChallengeManager.sol#L0:0

```solidity
File: src/challengeV2/IAssertionChain.sol


14          function bridge() external view returns (IBridge);
15          function validateAssertionHash(
21          function validateConfig(bytes32 assertionHash, ConfigData calldata configData) external view;
22          function getFirstChildCreationBlock(bytes32 assertionHash) external view returns (uint64);
23          function getSecondChildCreationBlock(bytes32 assertionHash) external view returns (uint64);
24          function isFirstChild(bytes32 assertionHash) external view returns (bool);
25          function isPending(bytes32 assertionHash) external view returns (bool);
26          function isValidator(address) external view returns (bool);
27          function validatorWhitelistDisabled() external view returns (bool);


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/challengeV2/IAssertionChain.sol#L0:0

```solidity
File: src/challengeV2/libraries/ArrayUtilsLib.sol


13          function append(bytes32[] memory arr, bytes32 newItem) internal pure returns (bytes32[] memory) {
45          function concat(bytes32[] memory arr1, bytes32[] memory arr2) internal pure returns (bytes32[] memory) {


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/challengeV2/libraries/ArrayUtilsLib.sol#L0:0

```solidity
File: src/challengeV2/libraries/ChallengeEdgeLib.sol


69          function newEdgeChecks(
93          function newLayerZeroEdge(
133         function newChildEdge(
166         function mutualIdComponent(
180         function mutualId(ChallengeEdge storage ce) internal view returns (bytes32) {
184         function mutualIdMem(ChallengeEdge memory ce) internal pure returns (bytes32) {
189         function idComponent(
215         function id(ChallengeEdge storage edge) internal view returns (bytes32) {
222         function exists(ChallengeEdge storage edge) internal view returns (bool) {
228         function length(ChallengeEdge storage edge) internal view returns (uint256) {
258         function isLayerZero(ChallengeEdge storage edge) internal view returns (bool) {
279         function levelToType(uint8 level, uint8 numBigStepLevels) internal pure returns (EdgeType eType) {


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/challengeV2/libraries/ChallengeEdgeLib.sol#L0:0

```solidity
File: src/challengeV2/libraries/EdgeChallengeManagerLib.sol


327         function isPowerOfTwo(uint256 x) internal pure returns (bool) {
344         function layerZeroCommonChecks(ProofData memory proofData, CreateEdgeArgs calldata args, uint256 expectedEndHeight)
391         function toLayerZeroEdge(bytes32 originId, bytes32 startHistoryRoot, CreateEdgeArgs calldata args)
411         function createLayerZeroEdge(
443         function getPrevAssertionHash(EdgeStore storage store, bytes32 edgeId) internal view returns (bytes32) {
463         function hasRival(EdgeStore storage store, bytes32 edgeId) internal view returns (bool) {
483         function hasLengthOneRival(EdgeStore storage store, bytes32 edgeId) internal view returns (bool) {
488         function timeUnrivaledTotal(EdgeStore storage store, bytes32 edgeId) internal view returns (uint256) {
516         function updateTimerCacheByChildren(EdgeStore storage store, bytes32 edgeId) internal returns (bool, uint256) {
520         function updateTimerCacheByClaim(
537         function timeUnrivaled(EdgeStore storage store, bytes32 edgeId) internal view returns (uint256) {
604         function bisectEdge(EdgeStore storage store, bytes32 edgeId, bytes32 bisectionHistoryRoot, bytes memory prefixProof)
674         function nextEdgeLevel(uint8 level, uint8 numBigStepLevel) internal pure returns (uint8) {


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/challengeV2/libraries/EdgeChallengeManagerLib.sol#L0:0

```solidity
File: src/challengeV2/libraries/MerkleTreeLib.sol


292         function treeSize(bytes32[] memory me) internal pure returns (uint256) {
359         function verifyInclusionProof(bytes32 rootHash, bytes32 leaf, uint256 index, bytes32[] memory proof)


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/challengeV2/libraries/MerkleTreeLib.sol#L0:0

```solidity
File: src/rollup/Assertion.sol


70          function createAssertion(
85          function childCreated(AssertionNode storage self) internal {
93          function requireExists(AssertionNode memory self) internal pure {


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/rollup/Assertion.sol#L0:0

```solidity
File: src/rollup/AssertionState.sol


18          function toExecutionState(AssertionState memory state) internal pure returns (ExecutionState memory) {
22          function hash(AssertionState memory state) internal pure returns (bytes32) {


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/rollup/AssertionState.sol#L0:0

```solidity
File: src/rollup/BOLDUpgradeAction.sol


67          function wasmModuleRoot() external view returns (bytes32);
68          function latestConfirmed() external view returns (uint64);
69          function getNode(uint64 nodeNum) external view returns (Node memory);
70          function getStakerAddress(uint64 stakerNum) external view returns (address);
71          function stakerCount() external view returns (uint64);
72          function getStaker(address staker) external view returns (OldStaker memory);
73          function isValidator(address validator) external view returns (bool);
74          function validatorWalletCreator() external view returns (address);
78          function forceRefundStaker(address[] memory stacker) external;
79          function pause() external;
80          function resume() external;
84          function postUpgradeInit(BufferConfig memory bufferConfig_) external;
101         function stateHash(ExecutionState calldata executionState, uint256 inboxMaxCount) public pure returns (bytes32) {
106         function set(bytes32 h, ExecutionState calldata executionState, uint256 inboxMaxCount) public {
112         function get(bytes32 h) public view returns (ExecutionState memory executionState, uint256 inboxMaxCount) {
126         constructor(IOldRollup _rollup) {
130         function wasmModuleRoot() external view returns (bytes32) {
134         function latestConfirmed() external view returns (uint64) {
138         function getNode(uint64 nodeNum) external view returns (Node memory) {
142         function getStakerAddress(uint64 stakerNum) external view returns (address) {
146         function stakerCount() external view returns (uint64) {
150         function getStaker(address staker) external view returns (OldStaker memory) {
154         function isValidator(address validator) external view returns (bool) {
158         function validatorWalletCreator() external view returns (address) {
169         constructor(uint256[] memory __array) {
173         function array() public view returns (uint256[] memory) {
287         constructor(
411         function upgradeSurroundingContracts(address newRollupAddress) private {
433         function upgradeSequencerInbox() private {
464         function perform(address[] memory validators) external {


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/rollup/BOLDUpgradeAction.sol#L0:0

```solidity
File: src/rollup/BridgeCreator.sol


45          constructor(
53          function updateTemplates(BridgeTemplates calldata _newTemplates) external onlyOwner {
58          function updateERC20Templates(BridgeTemplates calldata _newTemplates) external onlyOwner {
63          function _createBridge(
99          function createBridge(


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/rollup/BridgeCreator.sol#L0:0

```solidity
File: src/rollup/IRollupAdmin.sol


16          function initialize(Config calldata config, ContractDependencies calldata connectedContracts) external;
22          function setOutbox(IOutbox _outbox) external;
28          function removeOldOutbox(address _outbox) external;
35          function setDelayedInbox(address _inbox, bool _enabled) external;
40          function pause() external;
45          function resume() external;
60          function setOwner(address newOwner) external;
66          function setMinimumAssertionPeriod(uint256 newPeriod) external;
72          function setConfirmPeriodBlocks(uint64 newConfirmPeriod) external;
78          function setBaseStake(uint256 newBaseStake) external;
80          function forceRefundStaker(address[] memory stacker) external;
82          function forceCreateAssertion(
88          function forceConfirmAssertion(
95          function setLoserStakeEscrow(address newLoserStakerEscrow) external;
101         function setWasmModuleRoot(bytes32 newWasmModuleRoot) external;
107         function setSequencerInbox(address _sequencerInbox) external;
113         function setValidatorWhitelistDisabled(bool _validatorWhitelistDisabled) external;
119         function setChallengeManager(address _challengeManager) external;


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/rollup/IRollupAdmin.sol#L0:0

```solidity
File: src/rollup/IRollupCore.sol


48          function confirmPeriodBlocks() external view returns (uint64);
50          function chainId() external view returns (uint256);
52          function baseStake() external view returns (uint256);
54          function wasmModuleRoot() external view returns (bytes32);
56          function bridge() external view returns (IBridge);
58          function sequencerInbox() external view returns (ISequencerInbox);
60          function outbox() external view returns (IOutbox);
62          function rollupEventInbox() external view returns (IRollupEventInbox);
64          function challengeManager() external view returns (IEdgeChallengeManager);
66          function loserStakeEscrow() external view returns (address);
68          function stakeToken() external view returns (address);
70          function minimumAssertionPeriod() external view returns (uint256);
72          function genesisAssertionHash() external pure returns (bytes32);
77          function getAssertion(bytes32 assertionHash) external view returns (AssertionNode memory);
93          function getStakerAddress(uint64 stakerNum) external view returns (address);
100         function isStaked(address staker) external view returns (bool);
107         function latestStakedAssertion(address staker) external view returns (bytes32);
114         function amountStaked(address staker) external view returns (uint256);
121         function getStaker(address staker) external view returns (Staker memory);
128         function withdrawableFunds(address owner) external view returns (uint256);
130         function latestConfirmed() external view returns (bytes32);
133         function stakerCount() external view returns (uint64);


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/rollup/IRollupCore.sol#L0:0

```solidity
File: src/rollup/IRollupLogic.sol


17          function removeWhitelistAfterFork() external;
19          function removeWhitelistAfterValidatorAfk() external;
21          function confirmAssertion(
30          function stakeOnNewAssertion(AssertionInputs calldata assertion, bytes32 expectedAssertionHash) external;
32          function returnOldDeposit() external;
34          function reduceDeposit(uint256 target) external;
36          function withdrawStakerFunds() external returns (uint256);
38          function newStakeOnNewAssertion(
44          function newStakeOnNewAssertion(
51          function addToDeposit(address stakerAddress, uint256 tokenAmount) external;


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/rollup/IRollupLogic.sol#L0:0

```solidity
File: src/rollup/RollupAdminLogic.sol


18          function initialize(Config calldata config, ContractDependencies calldata connectedContracts)
117         function setOutbox(IOutbox _outbox) external override {
127         function removeOldOutbox(address _outbox) external override {
138         function setDelayedInbox(address _inbox, bool _enabled) external override {
158         function resume() external override {
204         function setMinimumAssertionPeriod(uint256 newPeriod) external override {
213         function setConfirmPeriodBlocks(uint64 newConfirmPeriod) external override {
223         function setBaseStake(uint256 newBaseStake) external override {
228         function forceRefundStaker(address[] calldata staker) external override whenPaused {
237         function forceCreateAssertion(
258         function forceConfirmAssertion(
269         function setLoserStakeEscrow(address newLoserStakerEscrow) external override {
281         function setWasmModuleRoot(bytes32 newWasmModuleRoot) external override {
290         function setSequencerInbox(address _sequencerInbox) external override {
299         function setInbox(IInboxBase newInbox) external {
308         function setValidatorWhitelistDisabled(bool _validatorWhitelistDisabled) external {
317         function setAnyTrustFastConfirmer(address _anyTrustFastConfirmer) external {
326         function setChallengeManager(address _challengeManager) external {


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/rollup/RollupAdminLogic.sol#L0:0

```solidity
File: src/rollup/RollupCore.sol


116         function sequencerInbox() public view virtual returns (ISequencerInbox) {
134         function getAssertion(bytes32 assertionHash) public view override returns (AssertionNode memory) {
162         function getStakerAddress(uint64 stakerNum) external view override returns (address) {
171         function isStaked(address staker) public view override returns (bool) {
180         function latestStakedAssertion(address staker) public view override returns (bytes32) {
189         function amountStaked(address staker) public view override returns (uint256) {
198         function getStaker(address staker) external view override returns (Staker memory) {
207         function withdrawableFunds(address user) external view override returns (uint256) {
212         function latestConfirmed() public view override returns (bytes32) {
217         function stakerCount() public view override returns (uint64) {
225         function initializeCore(AssertionNode memory initialAssertion, bytes32 assertionHash) internal {
274         function createNewStake(address stakerAddress, uint256 depositAmount, address withdrawalAddress) internal {
286         function increaseStakeBy(address stakerAddress, uint256 amountAdded) internal {
300         function reduceStakeTo(address stakerAddress, uint256 target) internal returns (uint256) {
317         function withdrawStaker(address stakerAddress) internal {
331         function withdrawFunds(address account) internal returns (uint256) {
343         function increaseWithdrawableFunds(address account, uint256 amount) internal {
355         function deleteStaker(address stakerAddress) private {
365         function createNewAssertion(
520         function genesisAssertionHash() external pure returns (bytes32) {
532         function getFirstChildCreationBlock(bytes32 assertionHash) external view returns (uint64) {
536         function getSecondChildCreationBlock(bytes32 assertionHash) external view returns (uint64) {
540         function validateAssertionHash(
549         function validateConfig(bytes32 assertionHash, ConfigData calldata configData) external view {
553         function isFirstChild(bytes32 assertionHash) external view returns (bool) {
557         function isPending(bytes32 assertionHash) external view returns (bool) {
565         function requireInactiveStaker(address stakerAddress) internal view {


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/rollup/RollupCore.sol#L0:0

```solidity
File: src/rollup/RollupCreator.sol


58          constructor() Ownable() {}
61          receive() external payable {}
63          function setTemplates(
85          function createChallengeManager(address rollupAddr, address proxyAdminAddr, Config memory config)
267         function _deployUpgradeExecutor(address rollupOwner, ProxyAdmin proxyAdmin)
287         function _deployFactories(


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/rollup/RollupCreator.sol#L0:0

```solidity
File: src/rollup/RollupLib.sol


23          function assertionHash(
37          function assertionHash(
54          function configHash(
73          function validateConfigHash(


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/rollup/RollupLib.sol#L0:0

```solidity
File: src/rollup/RollupProxy.sol


12          function initializeProxy(Config memory config, ContractDependencies memory connectedContracts)


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/rollup/RollupProxy.sol#L0:0

```solidity
File: src/rollup/RollupUserLogic.sol


33          function _chainIdChanged() internal view returns (bool) {
51          function _validatorIsAfk() internal view returns (bool) {
62          function removeWhitelistAfterFork() external {
71          function removeWhitelistAfterValidatorAfk() external {
82          function confirmAssertion(
137         function _newStake(uint256 depositAmount, address withdrawalAddress) internal onlyValidator whenNotPaused {
150         function computeAssertionHash(bytes32 prevAssertionHash, AssertionState calldata state, bytes32 inboxAcc)
163         function stakeOnNewAssertion(AssertionInputs calldata assertion, bytes32 expectedAssertionHash)
222         function returnOldDeposit() external override onlyValidator whenNotPaused {
232         function _addToDeposit(address stakerAddress, uint256 depositAmount) internal onlyValidator whenNotPaused {
241         function reduceDeposit(uint256 target) external onlyValidator whenNotPaused {
252         function fastConfirmAssertion(
273         function fastConfirmNewAssertion(AssertionInputs calldata assertion, bytes32 expectedAssertionHash)
308         function owner() external view returns (address) {
316         function newStakeOnNewAssertion(
331         function newStakeOnNewAssertion(
349         function addToDeposit(address stakerAddress, uint256 tokenAmount) external onlyValidator whenNotPaused {
358         function withdrawStakerFunds() external override whenNotPaused returns (uint256) {
366         function receiveTokens(uint256 tokenAmount) private {


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/rollup/RollupUserLogic.sol#L0:0

</details>

## NC091 - Function definitions should have NatSpec @notice annotations:

Explain to an end user what this does


<details>
<summary>Click to show 26 findings</summary>

```solidity
File: src/assertionStakingPool/AbsBoldStakingPool.sol


24          constructor(address _stakeToken) {
29          function depositIntoPool(uint256 amount) external {
41          function withdrawFromPool(uint256 amount) public {
57          function withdrawFromPool() external {


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/assertionStakingPool/AbsBoldStakingPool.sol#L0:0

```solidity
File: src/assertionStakingPool/AssertionStakingPool.sol


31          constructor(
40          function createAssertion(AssertionInputs calldata assertionInputs) external {
49          function makeStakeWithdrawable() public {
55          function withdrawStakeBackIntoPool() public {
60          function makeStakeWithdrawableAndWithdrawBackIntoPool() external {


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/assertionStakingPool/AssertionStakingPool.sol#L0:0

```solidity
File: src/assertionStakingPool/AssertionStakingPoolCreator.sol


15          function createPool(
25          function getPool(


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/assertionStakingPool/AssertionStakingPoolCreator.sol#L0:0

```solidity
File: src/assertionStakingPool/EdgeStakingPool.sol


35          constructor(
44          function createEdge(CreateEdgeArgs calldata args) external {


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/assertionStakingPool/EdgeStakingPool.sol#L0:0

```solidity
File: src/assertionStakingPool/EdgeStakingPoolCreator.sol


15          function createPool(
25          function getPool(


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/assertionStakingPool/EdgeStakingPoolCreator.sol#L0:0

```solidity
File: src/assertionStakingPool/StakingPoolCreatorUtils.sol


13          function getPool(bytes memory creationCode, bytes memory args) internal view returns (address) {


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/assertionStakingPool/StakingPoolCreatorUtils.sol#L0:0

```solidity
File: src/bridge/DelayBuffer.sol


108         function isUpdatable(BufferData storage self) internal view returns (bool) {
115         function isValidBufferConfig(BufferConfig memory config) internal pure returns (bool) {


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/bridge/DelayBuffer.sol#L0:0

```solidity
File: src/bridge/ISequencerInbox.sol


49          function totalDelayedMessagesRead() external view returns (uint256);
51          function bridge() external view returns (IBridge);
55          function HEADER_LENGTH() external view returns (uint256);
61          function DATA_AUTHENTICATED_FLAG() external view returns (bytes1);
67          function DATA_BLOB_HEADER_FLAG() external view returns (bytes1);
73          function DAS_MESSAGE_HEADER_FLAG() external view returns (bytes1);
79          function TREE_DAS_MESSAGE_HEADER_FLAG() external view returns (bytes1);
85          function BROTLI_MESSAGE_HEADER_FLAG() external view returns (bytes1);
91          function ZERO_HEAVY_MESSAGE_HEADER_FLAG() external view returns (bytes1);
93          function rollup() external view returns (IOwnable);
95          function isBatchPoster(address) external view returns (bool);
97          function isSequencer(address) external view returns (bool);
102         function maxDataSize() external view returns (uint256);
114         function maxTimeVariation()
124         function dasKeySetInfo(bytes32) external view returns (bool, uint64);
148         function inboxAccs(uint256 index) external view returns (bytes32);
150         function batchCount() external view returns (uint256);
152         function isValidKeysetHash(bytes32 ksHash) external view returns (bool);
171         function addSequencerL2BatchFromOrigin(
179         function addSequencerL2BatchFromOrigin(
188         function addSequencerL2Batch(
197         function addSequencerL2BatchFromBlobs(
207         function addSequencerL2BatchFromBlobsDelayProof(
219         function addSequencerL2BatchFromOriginDelayProof(
231         function addSequencerL2BatchDelayProof(
287         function initialize(


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/bridge/ISequencerInbox.sol#L0:0

```solidity
File: src/bridge/SequencerInbox.sol


140         constructor(
157         function _chainIdChanged() internal view returns (bool) {
161         function postUpgradeInit(BufferConfig memory bufferConfig_)
177         function initialize(
216         function getTimeBounds() internal view virtual returns (IBridge.TimeBounds memory) {
236         function removeDelayAfterFork() external {
244         function maxTimeVariation()
269         function maxTimeVariationInternal()
287         function forceInclusion(
356         function addSequencerL2BatchFromOrigin(
366         function addSequencerL2BatchFromOrigin(
390         function addSequencerL2BatchFromBlobs(
409         function addSequencerL2BatchFromBlobsDelayProof(
430         function addSequencerL2BatchFromOriginDelayProof(
455         function addSequencerL2BatchFromBlobsImpl(
512         function addSequencerL2BatchFromCalldataImpl(
560         function addSequencerL2Batch(
582         function addSequencerL2BatchDelayProof(
605         function delayProofImpl(uint256 afterDelayedMessagesRead, DelayProof memory delayProof)
628         function isDelayProofRequired(uint256 afterDelayedMessagesRead) internal view returns (bool) {
637         function packHeader(uint256 afterDelayedMessagesRead)
659         function formEmptyDataHash(uint256 afterDelayedMessagesRead)
675         function isValidCallDataFlag(bytes1 headerByte) internal pure returns (bool) {
688         function formCallDataHash(bytes calldata data, uint256 afterDelayedMessagesRead)
725         function formBlobDataHash(uint256 afterDelayedMessagesRead)
755         function submitBatchSpendingReport(
791         function addSequencerL2BatchImpl(
824         function inboxAccs(uint256 index) external view returns (bytes32) {
828         function batchCount() external view returns (uint256) {
833         function forceInclusionDeadline(uint64 blockNumber) external view returns (uint64) {
847         function _setBufferConfig(BufferConfig memory bufferConfig_) internal {
867         function _setMaxTimeVariation(ISequencerInbox.MaxTimeVariation memory maxTimeVariation_)
885         function setMaxTimeVariation(ISequencerInbox.MaxTimeVariation memory maxTimeVariation_)
894         function setIsBatchPoster(address addr, bool isBatchPoster_)
903         function setValidKeyset(bytes calldata keysetBytes) external onlyRollupOwner {
922         function invalidateKeysetHash(bytes32 ksHash) external onlyRollupOwner {
933         function setIsSequencer(address addr, bool isSequencer_)
942         function setBatchPosterManager(address newBatchPosterManager) external onlyRollupOwner {
947         function setBufferConfig(BufferConfig memory bufferConfig_) external onlyRollupOwner {
952         function isValidKeysetHash(bytes32 ksHash) external view returns (bool) {
957         function getKeysetCreationBlock(bytes32 ksHash) external view returns (uint256) {


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/bridge/SequencerInbox.sol#L0:0

```solidity
File: src/challengeV2/EdgeChallengeManager.sol


47          function challengePeriodBlocks() external view returns (uint64);
300         constructor() {
305         function initialize(
371         function createLayerZeroEdge(CreateEdgeArgs calldata args) external returns (bytes32) {
451         function bisectEdge(bytes32 edgeId, bytes32 bisectionHistoryRoot, bytes calldata prefixProof)
491         function multiUpdateTimeCacheByChildren(bytes32[] calldata edgeIds) public {
499         function updateTimerCacheByChildren(bytes32 edgeId) public {
505         function updateTimerCacheByClaim(bytes32 edgeId, bytes32 claimingEdgeId) public {
511         function confirmEdgeByTime(bytes32 edgeId, AssertionStateData calldata claimStateData) public {
539         function confirmEdgeByOneStepProof(
572         function refundStake(bytes32 edgeId) public {
591         function getLayerZeroEndHeight(EdgeType eType) public view returns (uint256) {
604         function calculateEdgeId(
616         function calculateMutualId(
627         function edgeExists(bytes32 edgeId) public view returns (bool) {
632         function getEdge(bytes32 edgeId) public view returns (ChallengeEdge memory) {
637         function edgeLength(bytes32 edgeId) public view returns (uint256) {
642         function hasRival(bytes32 edgeId) public view returns (bool) {
647         function confirmedRival(bytes32 mutualId) public view returns (bytes32) {
652         function hasLengthOneRival(bytes32 edgeId) public view returns (bool) {
657         function timeUnrivaled(bytes32 edgeId) public view returns (uint256) {
662         function getPrevAssertionHash(bytes32 edgeId) public view returns (bytes32) {
667         function firstRival(bytes32 mutualId) public view returns (bytes32) {
672         function hasMadeLayerZeroRival(address account, bytes32 mutualId) external view returns (bool) {


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/challengeV2/EdgeChallengeManager.sol#L0:0

```solidity
File: src/challengeV2/IAssertionChain.sol


14          function bridge() external view returns (IBridge);
15          function validateAssertionHash(
21          function validateConfig(bytes32 assertionHash, ConfigData calldata configData) external view;
22          function getFirstChildCreationBlock(bytes32 assertionHash) external view returns (uint64);
23          function getSecondChildCreationBlock(bytes32 assertionHash) external view returns (uint64);
24          function isFirstChild(bytes32 assertionHash) external view returns (bool);
25          function isPending(bytes32 assertionHash) external view returns (bool);
26          function isValidator(address) external view returns (bool);
27          function validatorWhitelistDisabled() external view returns (bool);


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/challengeV2/IAssertionChain.sol#L0:0

```solidity
File: src/challengeV2/libraries/ChallengeEdgeLib.sol


184         function mutualIdMem(ChallengeEdge memory ce) internal pure returns (bytes32) {


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/challengeV2/libraries/ChallengeEdgeLib.sol#L0:0

```solidity
File: src/challengeV2/libraries/EdgeChallengeManagerLib.sol


488         function timeUnrivaledTotal(EdgeStore storage store, bytes32 edgeId) internal view returns (uint256) {
516         function updateTimerCacheByChildren(EdgeStore storage store, bytes32 edgeId) internal returns (bool, uint256) {
520         function updateTimerCacheByClaim(


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/challengeV2/libraries/EdgeChallengeManagerLib.sol#L0:0

```solidity
File: src/rollup/Assertion.sol


93          function requireExists(AssertionNode memory self) internal pure {


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/rollup/Assertion.sol#L0:0

```solidity
File: src/rollup/AssertionState.sol


18          function toExecutionState(AssertionState memory state) internal pure returns (ExecutionState memory) {
22          function hash(AssertionState memory state) internal pure returns (bytes32) {


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/rollup/AssertionState.sol#L0:0

```solidity
File: src/rollup/BOLDUpgradeAction.sol


67          function wasmModuleRoot() external view returns (bytes32);
68          function latestConfirmed() external view returns (uint64);
69          function getNode(uint64 nodeNum) external view returns (Node memory);
70          function getStakerAddress(uint64 stakerNum) external view returns (address);
71          function stakerCount() external view returns (uint64);
72          function getStaker(address staker) external view returns (OldStaker memory);
73          function isValidator(address validator) external view returns (bool);
74          function validatorWalletCreator() external view returns (address);
78          function forceRefundStaker(address[] memory stacker) external;
79          function pause() external;
80          function resume() external;
84          function postUpgradeInit(BufferConfig memory bufferConfig_) external;
101         function stateHash(ExecutionState calldata executionState, uint256 inboxMaxCount) public pure returns (bytes32) {
106         function set(bytes32 h, ExecutionState calldata executionState, uint256 inboxMaxCount) public {
112         function get(bytes32 h) public view returns (ExecutionState memory executionState, uint256 inboxMaxCount) {
126         constructor(IOldRollup _rollup) {
130         function wasmModuleRoot() external view returns (bytes32) {
134         function latestConfirmed() external view returns (uint64) {
138         function getNode(uint64 nodeNum) external view returns (Node memory) {
142         function getStakerAddress(uint64 stakerNum) external view returns (address) {
146         function stakerCount() external view returns (uint64) {
150         function getStaker(address staker) external view returns (OldStaker memory) {
154         function isValidator(address validator) external view returns (bool) {
158         function validatorWalletCreator() external view returns (address) {
169         constructor(uint256[] memory __array) {
173         function array() public view returns (uint256[] memory) {
287         constructor(
341         function cleanupOldRollup() private {
367         function createConfig() private view returns (Config memory) {
411         function upgradeSurroundingContracts(address newRollupAddress) private {
433         function upgradeSequencerInbox() private {
464         function perform(address[] memory validators) external {


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/rollup/BOLDUpgradeAction.sol#L0:0

```solidity
File: src/rollup/BridgeCreator.sol


45          constructor(
53          function updateTemplates(BridgeTemplates calldata _newTemplates) external onlyOwner {
58          function updateERC20Templates(BridgeTemplates calldata _newTemplates) external onlyOwner {
63          function _createBridge(
99          function createBridge(


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/rollup/BridgeCreator.sol#L0:0

```solidity
File: src/rollup/IRollupAdmin.sol


16          function initialize(Config calldata config, ContractDependencies calldata connectedContracts) external;
80          function forceRefundStaker(address[] memory stacker) external;
82          function forceCreateAssertion(
88          function forceConfirmAssertion(
95          function setLoserStakeEscrow(address newLoserStakerEscrow) external;


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/rollup/IRollupAdmin.sol#L0:0

```solidity
File: src/rollup/IRollupCore.sol


48          function confirmPeriodBlocks() external view returns (uint64);
50          function chainId() external view returns (uint256);
52          function baseStake() external view returns (uint256);
54          function wasmModuleRoot() external view returns (bytes32);
56          function bridge() external view returns (IBridge);
58          function sequencerInbox() external view returns (ISequencerInbox);
60          function outbox() external view returns (IOutbox);
62          function rollupEventInbox() external view returns (IRollupEventInbox);
64          function challengeManager() external view returns (IEdgeChallengeManager);
66          function loserStakeEscrow() external view returns (address);
68          function stakeToken() external view returns (address);
70          function minimumAssertionPeriod() external view returns (uint256);
72          function genesisAssertionHash() external pure returns (bytes32);
130         function latestConfirmed() external view returns (bytes32);
133         function stakerCount() external view returns (uint64);


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/rollup/IRollupCore.sol#L0:0

```solidity
File: src/rollup/IRollupLogic.sol


15          function initialize(address stakeToken) external view;
17          function removeWhitelistAfterFork() external;
19          function removeWhitelistAfterValidatorAfk() external;
21          function confirmAssertion(
30          function stakeOnNewAssertion(AssertionInputs calldata assertion, bytes32 expectedAssertionHash) external;
32          function returnOldDeposit() external;
34          function reduceDeposit(uint256 target) external;
36          function withdrawStakerFunds() external returns (uint256);
38          function newStakeOnNewAssertion(
44          function newStakeOnNewAssertion(
51          function addToDeposit(address stakerAddress, uint256 tokenAmount) external;


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/rollup/IRollupLogic.sol#L0:0

```solidity
File: src/rollup/RollupAdminLogic.sol


18          function initialize(Config calldata config, ContractDependencies calldata connectedContracts)
228         function forceRefundStaker(address[] calldata staker) external override whenPaused {
237         function forceCreateAssertion(
258         function forceConfirmAssertion(
269         function setLoserStakeEscrow(address newLoserStakerEscrow) external override {


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/rollup/RollupAdminLogic.sol#L0:0

```solidity
File: src/rollup/RollupCore.sol


116         function sequencerInbox() public view virtual returns (ISequencerInbox) {
212         function latestConfirmed() public view override returns (bytes32) {
217         function stakerCount() public view override returns (uint64) {
236         function confirmAssertionInternal(
365         function createNewAssertion(
520         function genesisAssertionHash() external pure returns (bytes32) {
532         function getFirstChildCreationBlock(bytes32 assertionHash) external view returns (uint64) {
536         function getSecondChildCreationBlock(bytes32 assertionHash) external view returns (uint64) {
540         function validateAssertionHash(
549         function validateConfig(bytes32 assertionHash, ConfigData calldata configData) external view {
553         function isFirstChild(bytes32 assertionHash) external view returns (bool) {
557         function isPending(bytes32 assertionHash) external view returns (bool) {


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/rollup/RollupCore.sol#L0:0

```solidity
File: src/rollup/RollupCreator.sol


58          constructor() Ownable() {}
61          receive() external payable {}
63          function setTemplates(
85          function createChallengeManager(address rollupAddr, address proxyAdminAddr, Config memory config)
267         function _deployUpgradeExecutor(address rollupOwner, ProxyAdmin proxyAdmin)
287         function _deployFactories(


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/rollup/RollupCreator.sol#L0:0

```solidity
File: src/rollup/RollupLib.sol


23          function assertionHash(
37          function assertionHash(
54          function configHash(
73          function validateConfigHash(


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/rollup/RollupLib.sol#L0:0

```solidity
File: src/rollup/RollupProxy.sol


12          function initializeProxy(Config memory config, ContractDependencies memory connectedContracts)


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/rollup/RollupProxy.sol#L0:0

```solidity
File: src/rollup/RollupUserLogic.sol


27          function initialize(address _stakeToken) external view override onlyProxy {
33          function _chainIdChanged() internal view returns (bool) {
51          function _validatorIsAfk() internal view returns (bool) {
62          function removeWhitelistAfterFork() external {
308         function owner() external view returns (address) {
366         function receiveTokens(uint256 tokenAmount) private {


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/rollup/RollupUserLogic.sol#L0:0

</details>

## NC092 - Interface declarations should have NatSpec @title annotations:

A title that should describe the contract/interface


<details>
<summary>Click to show 10 findings</summary>

```solidity
File: src/assertionStakingPool/interfaces/IAbsBoldStakingPool.sol


7       interface IAbsBoldStakingPool {


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/assertionStakingPool/interfaces/IAbsBoldStakingPool.sol#L0:0

```solidity
File: src/assertionStakingPool/interfaces/IAssertionStakingPool.sol


10      interface IAssertionStakingPool is IAbsBoldStakingPool {


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/assertionStakingPool/interfaces/IAssertionStakingPool.sol#L0:0

```solidity
File: src/assertionStakingPool/interfaces/IAssertionStakingPoolCreator.sol


10      interface IAssertionStakingPoolCreator {


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/assertionStakingPool/interfaces/IAssertionStakingPoolCreator.sol#L0:0

```solidity
File: src/assertionStakingPool/interfaces/IEdgeStakingPool.sol


10      interface IEdgeStakingPool is IAbsBoldStakingPool {


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/assertionStakingPool/interfaces/IEdgeStakingPool.sol#L0:0

```solidity
File: src/assertionStakingPool/interfaces/IEdgeStakingPoolCreator.sol


9       interface IEdgeStakingPoolCreator {


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/assertionStakingPool/interfaces/IEdgeStakingPoolCreator.sol#L0:0

```solidity
File: src/bridge/ISequencerInbox.sol


15      interface ISequencerInbox is IDelayedMessageProvider {


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/bridge/ISequencerInbox.sol#L0:0

```solidity
File: src/rollup/BOLDUpgradeAction.sol


49      interface IOldRollup {
77      interface IOldRollupAdmin {
83      interface ISeqInboxPostUpgradeInit {


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/rollup/BOLDUpgradeAction.sol#L0:0

```solidity
File: src/rollup/IRollupAdmin.sol


13      interface IRollupAdmin {


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/rollup/IRollupAdmin.sol#L0:0

```solidity
File: src/rollup/IRollupCore.sol


15      interface IRollupCore is IAssertionChain {


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/rollup/IRollupCore.sol#L0:0

```solidity
File: src/rollup/IRollupLogic.sol


12      interface IRollupUser is IRollupCore, IOwnable {


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/rollup/IRollupLogic.sol#L0:0

</details>

## NC093 - Interface declarations should have NatSpec @author annotations:

The name of the author


<details>
<summary>Click to show 12 findings</summary>

```solidity
File: src/assertionStakingPool/interfaces/IAbsBoldStakingPool.sol


7       interface IAbsBoldStakingPool {


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/assertionStakingPool/interfaces/IAbsBoldStakingPool.sol#L0:0

```solidity
File: src/assertionStakingPool/interfaces/IAssertionStakingPool.sol


10      interface IAssertionStakingPool is IAbsBoldStakingPool {


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/assertionStakingPool/interfaces/IAssertionStakingPool.sol#L0:0

```solidity
File: src/assertionStakingPool/interfaces/IAssertionStakingPoolCreator.sol


10      interface IAssertionStakingPoolCreator {


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/assertionStakingPool/interfaces/IAssertionStakingPoolCreator.sol#L0:0

```solidity
File: src/assertionStakingPool/interfaces/IEdgeStakingPool.sol


10      interface IEdgeStakingPool is IAbsBoldStakingPool {


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/assertionStakingPool/interfaces/IEdgeStakingPool.sol#L0:0

```solidity
File: src/assertionStakingPool/interfaces/IEdgeStakingPoolCreator.sol


9       interface IEdgeStakingPoolCreator {


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/assertionStakingPool/interfaces/IEdgeStakingPoolCreator.sol#L0:0

```solidity
File: src/bridge/ISequencerInbox.sol


15      interface ISequencerInbox is IDelayedMessageProvider {


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/bridge/ISequencerInbox.sol#L0:0

```solidity
File: src/challengeV2/EdgeChallengeManager.sol


18      interface IEdgeChallengeManager {


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/challengeV2/EdgeChallengeManager.sol#L0:0

```solidity
File: src/challengeV2/IAssertionChain.sol


13      interface IAssertionChain {


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/challengeV2/IAssertionChain.sol#L0:0

```solidity
File: src/rollup/BOLDUpgradeAction.sol


49      interface IOldRollup {
77      interface IOldRollupAdmin {
83      interface ISeqInboxPostUpgradeInit {


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/rollup/BOLDUpgradeAction.sol#L0:0

```solidity
File: src/rollup/IRollupAdmin.sol


13      interface IRollupAdmin {


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/rollup/IRollupAdmin.sol#L0:0

```solidity
File: src/rollup/IRollupCore.sol


15      interface IRollupCore is IAssertionChain {


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/rollup/IRollupCore.sol#L0:0

```solidity
File: src/rollup/IRollupLogic.sol


12      interface IRollupUser is IRollupCore, IOwnable {


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/rollup/IRollupLogic.sol#L0:0

</details>

## NC094 - Interface declarations should have NatSpec @notice annotations:

Explain to an end user what this does


<details>
<summary>Click to show 11 findings</summary>

```solidity
File: src/assertionStakingPool/interfaces/IAbsBoldStakingPool.sol


7       interface IAbsBoldStakingPool {


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/assertionStakingPool/interfaces/IAbsBoldStakingPool.sol#L0:0

```solidity
File: src/assertionStakingPool/interfaces/IAssertionStakingPool.sol


10      interface IAssertionStakingPool is IAbsBoldStakingPool {


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/assertionStakingPool/interfaces/IAssertionStakingPool.sol#L0:0

```solidity
File: src/assertionStakingPool/interfaces/IAssertionStakingPoolCreator.sol


10      interface IAssertionStakingPoolCreator {


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/assertionStakingPool/interfaces/IAssertionStakingPoolCreator.sol#L0:0

```solidity
File: src/assertionStakingPool/interfaces/IEdgeStakingPool.sol


10      interface IEdgeStakingPool is IAbsBoldStakingPool {


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/assertionStakingPool/interfaces/IEdgeStakingPool.sol#L0:0

```solidity
File: src/assertionStakingPool/interfaces/IEdgeStakingPoolCreator.sol


9       interface IEdgeStakingPoolCreator {


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/assertionStakingPool/interfaces/IEdgeStakingPoolCreator.sol#L0:0

```solidity
File: src/bridge/ISequencerInbox.sol


15      interface ISequencerInbox is IDelayedMessageProvider {


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/bridge/ISequencerInbox.sol#L0:0

```solidity
File: src/challengeV2/EdgeChallengeManager.sol


18      interface IEdgeChallengeManager {


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/challengeV2/EdgeChallengeManager.sol#L0:0

```solidity
File: src/rollup/BOLDUpgradeAction.sol


49      interface IOldRollup {
77      interface IOldRollupAdmin {
83      interface ISeqInboxPostUpgradeInit {


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/rollup/BOLDUpgradeAction.sol#L0:0

```solidity
File: src/rollup/IRollupAdmin.sol


13      interface IRollupAdmin {


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/rollup/IRollupAdmin.sol#L0:0

```solidity
File: src/rollup/IRollupCore.sol


15      interface IRollupCore is IAssertionChain {


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/rollup/IRollupCore.sol#L0:0

```solidity
File: src/rollup/IRollupLogic.sol


12      interface IRollupUser is IRollupCore, IOwnable {


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/rollup/IRollupLogic.sol#L0:0

</details>

## NC095 - Interface declarations should have NatSpec @dev annotations:

Explain to a developer any extra details


<details>
<summary>Click to show 12 findings</summary>

```solidity
File: src/assertionStakingPool/interfaces/IAbsBoldStakingPool.sol


7       interface IAbsBoldStakingPool {


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/assertionStakingPool/interfaces/IAbsBoldStakingPool.sol#L0:0

```solidity
File: src/assertionStakingPool/interfaces/IAssertionStakingPool.sol


10      interface IAssertionStakingPool is IAbsBoldStakingPool {


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/assertionStakingPool/interfaces/IAssertionStakingPool.sol#L0:0

```solidity
File: src/assertionStakingPool/interfaces/IAssertionStakingPoolCreator.sol


10      interface IAssertionStakingPoolCreator {


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/assertionStakingPool/interfaces/IAssertionStakingPoolCreator.sol#L0:0

```solidity
File: src/assertionStakingPool/interfaces/IEdgeStakingPool.sol


10      interface IEdgeStakingPool is IAbsBoldStakingPool {


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/assertionStakingPool/interfaces/IEdgeStakingPool.sol#L0:0

```solidity
File: src/assertionStakingPool/interfaces/IEdgeStakingPoolCreator.sol


9       interface IEdgeStakingPoolCreator {


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/assertionStakingPool/interfaces/IEdgeStakingPoolCreator.sol#L0:0

```solidity
File: src/bridge/ISequencerInbox.sol


15      interface ISequencerInbox is IDelayedMessageProvider {


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/bridge/ISequencerInbox.sol#L0:0

```solidity
File: src/challengeV2/EdgeChallengeManager.sol


18      interface IEdgeChallengeManager {


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/challengeV2/EdgeChallengeManager.sol#L0:0

```solidity
File: src/challengeV2/IAssertionChain.sol


13      interface IAssertionChain {


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/challengeV2/IAssertionChain.sol#L0:0

```solidity
File: src/rollup/BOLDUpgradeAction.sol


49      interface IOldRollup {
77      interface IOldRollupAdmin {
83      interface ISeqInboxPostUpgradeInit {


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/rollup/BOLDUpgradeAction.sol#L0:0

```solidity
File: src/rollup/IRollupAdmin.sol


13      interface IRollupAdmin {


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/rollup/IRollupAdmin.sol#L0:0

```solidity
File: src/rollup/IRollupCore.sol


15      interface IRollupCore is IAssertionChain {


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/rollup/IRollupCore.sol#L0:0

```solidity
File: src/rollup/IRollupLogic.sol


12      interface IRollupUser is IRollupCore, IOwnable {


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/rollup/IRollupLogic.sol#L0:0

</details>

## NC096 - Abstract contract declarations should have NatSpec @title annotations:

A title that should describe the contract/interface


```solidity
File: src/assertionStakingPool/AbsBoldStakingPool.sol


16      abstract contract AbsBoldStakingPool is IAbsBoldStakingPool {


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/assertionStakingPool/AbsBoldStakingPool.sol#L0:0

```solidity
File: src/rollup/RollupCore.sol


22      abstract contract RollupCore is IRollupCore, PausableUpgradeable {


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/rollup/RollupCore.sol#L0:0

## NC097 - Abstract contract declarations should have NatSpec @author annotations:

The name of the author


```solidity
File: src/assertionStakingPool/AbsBoldStakingPool.sol


16      abstract contract AbsBoldStakingPool is IAbsBoldStakingPool {


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/assertionStakingPool/AbsBoldStakingPool.sol#L0:0

```solidity
File: src/rollup/RollupCore.sol


22      abstract contract RollupCore is IRollupCore, PausableUpgradeable {


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/rollup/RollupCore.sol#L0:0

## NC098 - Abstract contract declarations should have NatSpec @notice annotations:

Explain to an end user what this does


```solidity
File: src/rollup/RollupCore.sol


22      abstract contract RollupCore is IRollupCore, PausableUpgradeable {


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/rollup/RollupCore.sol#L0:0

## NC099 - Abstract contract declarations should have Natspec @dev annotations:

Explain to a developer any extra details


```solidity
File: src/rollup/RollupCore.sol


22      abstract contract RollupCore is IRollupCore, PausableUpgradeable {


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/rollup/RollupCore.sol#L0:0






## NC100 - TODO Left in the code:

TODOs may signal that a feature is missing or not ready for audit, consider resolving the issue and removing the TODO comment


```solidity
File: src/challengeV2/libraries/ChallengeEdgeLib.sol


/// @notice TODO

```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/challengeV2/libraries/ChallengeEdgeLib.sol#L63:63

## NC101 - Constants should be defined rather than using magic numbers:

Even assembly can benefit from using readable constants instead of hex/numeric literals.


<details>
<summary>Click to show 6 findings</summary>

```solidity
File: src/bridge/SequencerInbox.sol


711                 if (data[0] & DAS_MESSAGE_HEADER_FLAG != 0 && data.length >= 33) {
713                     bytes32 dasKeysetHash = bytes32(data[1:33]);
770                 uint256 l1Fees = ArbGasInfo(address(0x6c)).getCurrentTxL1GasFees();
905             bytes32 ksHash = bytes32(ksWord ^ (1 << 255));
906             if (keysetBytes.length >= 64 * 1024) revert KeysetTooLarge();
911                 creationBlock = ArbSys(address(100)).arbBlockNumber();
929             emit OwnerFunctionCalled(3);
938             emit OwnerFunctionCalled(4); // Owner in this context can also be batch poster manager
944             emit OwnerFunctionCalled(5);
949             emit OwnerFunctionCalled(6);


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/bridge/SequencerInbox.sol#L0:0

```solidity
File: src/challengeV2/EdgeChallengeManager.sol


355             if (_numBigStepLevel > 253) {


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/challengeV2/EdgeChallengeManager.sol#L0:0

```solidity
File: src/challengeV2/libraries/UintUtilsLib.sol


33              if (x >= 0x100000000000000000000000000000000) {
34                  x >>= 128;
35                  msb += 128;
38              if (x >= 0x10000000000000000) {
39                  x >>= 64;
40                  msb += 64;
43              if (x >= 0x100000000) {
44                  x >>= 32;
45                  msb += 32;
48              if (x >= 0x10000) {
49                  x >>= 16;
50                  msb += 16;
53              if (x >= 0x100) {
54                  x >>= 8;
55                  msb += 8;
58              if (x >= 0x10) {
59                  x >>= 4;
60                  msb += 4;
63              if (x >= 0x4) {
68              if (x >= 0x2) msb += 1;


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/challengeV2/libraries/UintUtilsLib.sol#L0:0

```solidity
File: src/rollup/BOLDUpgradeAction.sol


347             if (stakerCount > 50) {
348                 stakerCount = 50;


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/rollup/BOLDUpgradeAction.sol#L0:0

```solidity
File: src/rollup/RollupAdminLogic.sol


52              minimumAssertionPeriod = 75;
102                 _assertionCreatedAtArbSysBlock[genesisHash] = ArbSys(address(100)).arbBlockNumber();
152             emit OwnerFunctionCalled(3);
160             emit OwnerFunctionCalled(4);
187             emit OwnerFunctionCalled(6);
197             emit OwnerFunctionCalled(7);
206             emit OwnerFunctionCalled(8);
216             emit OwnerFunctionCalled(9);
225             emit OwnerFunctionCalled(12);
234             emit OwnerFunctionCalled(22);
255             emit OwnerFunctionCalled(23);
266             emit OwnerFunctionCalled(24);
274             emit OwnerFunctionCalled(25);
283             emit OwnerFunctionCalled(26);
292             emit OwnerFunctionCalled(27);
301             emit OwnerFunctionCalled(28);
310             emit OwnerFunctionCalled(30);
319             emit OwnerFunctionCalled(31);
328             emit OwnerFunctionCalled(32);


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/rollup/RollupAdminLogic.sol#L0:0

```solidity
File: src/rollup/RollupCore.sol


516                 _assertionCreatedAtArbSysBlock[newAssertionHash] = ArbSys(address(100)).arbBlockNumber();


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/rollup/RollupCore.sol#L0:0

</details>

## NC102 - Event is not properly indexed:

Index event fields make the field more quickly accessible to off-chain tools that parse events. This is especially useful when it comes to filtering based on an address. However, note that each index field costs extra gas during emission, so it's not necessarily best to index the maximum allowed per event (three fields). Where applicable, each event should use three indexed fields if there are three or more fields, and gas usage is not particularly of concern for the events in question. If there are fewer than three applicable fields, all of the applicable fields should be indexed.


```solidity
File: src/rollup/BOLDUpgradeAction.sol


235         event RollupMigrated(address rollup, address challengeManager);


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/rollup/BOLDUpgradeAction.sol#L0:0

## NC103 - Function ordering does not follow the Solidity style guide:

According to the [Solidity style guide](https://docs.soliditylang.org/en/v0.8.17/style-guide.html#order-of-functions), functions should be laid out in the following order :`constructor()`, `receive()`, `fallback()`, `external`, `public`, `internal`, `private`, but the cases below do not follow this pattern.


<details>
<summary>Click to show 11 findings</summary>

```solidity
File: src/assertionStakingPool/AbsBoldStakingPool.sol


/// @auditbase public functions should not come before external functions
    function withdrawFromPool() external {

```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/assertionStakingPool/AbsBoldStakingPool.sol#L57:57

```solidity
File: src/assertionStakingPool/AssertionStakingPool.sol


/// @auditbase public functions should not come before external functions
    function makeStakeWithdrawableAndWithdrawBackIntoPool() external {

```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/assertionStakingPool/AssertionStakingPool.sol#L60:60

```solidity
File: src/bridge/SequencerInbox.sol


/// @auditbase internal functions should not come before external functions
    function postUpgradeInit(BufferConfig memory bufferConfig_)
        external
        onlyDelegated
        onlyProxyOwner
    {

```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/bridge/SequencerInbox.sol#L161:165

```solidity
File: src/challengeV2/EdgeChallengeManager.sol


/// @auditbase public functions should not come before external functions
    function createLayerZeroEdge(CreateEdgeArgs calldata args) external returns (bytes32) {

```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/challengeV2/EdgeChallengeManager.sol#L371:371

```solidity
File: src/challengeV2/libraries/EdgeChallengeManagerLib.sol


/// @auditbase private functions should not come before internal functions
    function isPowerOfTwo(uint256 x) internal pure returns (bool) {

```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/challengeV2/libraries/EdgeChallengeManagerLib.sol#L327:327

```solidity
File: src/rollup/BOLDUpgradeAction.sol


/// @auditbase private functions should not come before external functions
    function perform(address[] memory validators) external {

```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/rollup/BOLDUpgradeAction.sol#L464:464

```solidity
File: src/rollup/BridgeCreator.sol


/// @auditbase internal functions should not come before external functions
    function createBridge(
        address adminProxy,
        address rollup,
        address nativeToken,
        ISequencerInbox.MaxTimeVariation calldata maxTimeVariation,
        BufferConfig calldata bufferConfig
    ) external returns (BridgeContracts memory) {

```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/rollup/BridgeCreator.sol#L99:105

```solidity
File: src/rollup/RollupAdminLogic.sol


/// @auditbase internal functions should not come before external functions
    function setValidator(address[] calldata _validator, bool[] calldata _val) external override {

```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/rollup/RollupAdminLogic.sol#L180:180

```solidity
File: src/rollup/RollupCore.sol


/// @auditbase internal functions should not come before public functions
    function getAssertion(bytes32 assertionHash) public view override returns (AssertionNode memory) {

```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/rollup/RollupCore.sol#L134:134

```solidity
File: src/rollup/RollupCreator.sol


/// @auditbase internal functions should not come before public functions
    function createRollup(RollupDeploymentParams memory deployParams)
        public
        payable
        returns (address)
    {

```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/rollup/RollupCreator.sol#L137:141

```solidity
File: src/rollup/RollupUserLogic.sol


/// @auditbase internal functions should not come before external functions
    function removeWhitelistAfterFork() external {

```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/rollup/RollupUserLogic.sol#L62:62

</details>

## NC104 - Imports could be organized more systematically:

This issue arises when the contract's interface is not imported first, followed by each of the interfaces it uses, followed by all other files.


<details>
<summary>Click to show 19 findings</summary>

```solidity
File: src/assertionStakingPool/AbsBoldStakingPool.sol


9       import {IAbsBoldStakingPool} from "./interfaces/IAbsBoldStakingPool.sol";


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/assertionStakingPool/AbsBoldStakingPool.sol#L0:0

```solidity
File: src/assertionStakingPool/AssertionStakingPool.sol


11      import "./interfaces/IAssertionStakingPool.sol";


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/assertionStakingPool/AssertionStakingPool.sol#L0:0

```solidity
File: src/assertionStakingPool/AssertionStakingPoolCreator.sol


10      import "./interfaces/IAssertionStakingPoolCreator.sol";


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/assertionStakingPool/AssertionStakingPoolCreator.sol#L0:0

```solidity
File: src/assertionStakingPool/EdgeStakingPool.sol


8       import "./interfaces/IEdgeStakingPool.sol";


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/assertionStakingPool/EdgeStakingPool.sol#L0:0

```solidity
File: src/assertionStakingPool/EdgeStakingPoolCreator.sol


10      import "./interfaces/IEdgeStakingPoolCreator.sol";


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/assertionStakingPool/EdgeStakingPoolCreator.sol#L0:0

```solidity
File: src/assertionStakingPool/interfaces/IEdgeStakingPool.sol


8       import "./IAbsBoldStakingPool.sol";


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/assertionStakingPool/interfaces/IEdgeStakingPool.sol#L0:0

```solidity
File: src/bridge/SequencerInbox.sol


40      import "./IBridge.sol";


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/bridge/SequencerInbox.sol#L0:0

```solidity
File: src/challengeV2/EdgeChallengeManager.sol


9       import "./IAssertionChain.sol";


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/challengeV2/EdgeChallengeManager.sol#L0:0

```solidity
File: src/challengeV2/libraries/EdgeChallengeManagerLib.sol


10      import "../../osp/IOneStepProofEntry.sol";


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/challengeV2/libraries/EdgeChallengeManagerLib.sol#L0:0

```solidity
File: src/rollup/AssertionState.sol


9       import "../osp/IOneStepProofEntry.sol";


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/rollup/AssertionState.sol#L0:0

```solidity
File: src/rollup/BridgeCreator.sol


17      import "../bridge/IBridge.sol";


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/rollup/BridgeCreator.sol#L0:0

```solidity
File: src/rollup/Config.sol


9       import "../bridge/ISequencerInbox.sol";


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/rollup/Config.sol#L0:0

```solidity
File: src/rollup/IRollupCore.sol


8       import "../bridge/IBridge.sol";


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/rollup/IRollupCore.sol#L0:0

```solidity
File: src/rollup/RollupAdminLogic.sol


10      import "../bridge/IOutbox.sol";


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/rollup/RollupAdminLogic.sol#L0:0

```solidity
File: src/rollup/RollupCore.sol


11      import "./IRollupEventInbox.sol";


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/rollup/RollupCore.sol#L0:0

```solidity
File: src/rollup/RollupCreator.sol


8       import "./IRollupAdmin.sol";


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/rollup/RollupCreator.sol#L0:0

```solidity
File: src/rollup/RollupLib.sol


8       import "../bridge/ISequencerInbox.sol";


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/rollup/RollupLib.sol#L0:0

```solidity
File: src/rollup/RollupProxy.sol


8       import "./IRollupAdmin.sol";


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/rollup/RollupProxy.sol#L0:0

```solidity
File: src/rollup/RollupUserLogic.sol


12      import "./IRollupLogic.sol";


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/rollup/RollupUserLogic.sol#L0:0

</details>

## NC105 - Constants in comparisons should appear on the left side:

This issue arises when constants in comparisons appear on the right side, which can lead to typo bugs.


<details>
<summary>Click to show 15 findings</summary>

```solidity
File: src/assertionStakingPool/AbsBoldStakingPool.sol


30              if (amount == 0) {
42              if (amount == 0) {


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/assertionStakingPool/AbsBoldStakingPool.sol#L0:0

```solidity
File: src/bridge/DelayBuffer.sol


117                 config.threshold != 0 &&
118                 config.max != 0 &&


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/bridge/DelayBuffer.sol#L0:0

```solidity
File: src/bridge/SequencerInbox.sol


170             if (buffer.bufferBlocks != 0) {
318             if (_totalDelayedMessagesRead > 1) {
702             if (data.length > 0) {
711                 if (data[0] & DAS_MESSAGE_HEADER_FLAG != 0 && data.length >= 33) {
736             if (dataHashes.length == 0) revert MissingDataHashes();
746                 block.basefee > 0 ? blobCost / block.basefee : 0
818             if (calldataLengthPosted > 0 && !isUsingFeeToken) {
851             if (buffer.bufferBlocks == 0 || buffer.bufferBlocks > bufferConfig_.max) {
959             if (ksInfo.creationBlock == 0) revert NoSuchKeyset(ksHash);


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/bridge/SequencerInbox.sol#L0:0

```solidity
File: src/challengeV2/EdgeChallengeManager.sol


325             if (_challengePeriodBlocks == 0) {
350             if (_numBigStepLevel == 0) {
355             if (_numBigStepLevel > 253) {
387                 if (args.proof.length == 0) {
412                     assertionChain.getSecondChildCreationBlock(claimStateData.prevAssertionHash) > 0,
429             if (address(st) != address(0) && sa != 0) {
458             bool lowerChildAlreadyExists = lowerChildAdded.edgeId == 0;
580             if (address(st) != address(0) && sa != 0) {


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/challengeV2/EdgeChallengeManager.sol#L0:0

```solidity
File: src/challengeV2/libraries/ChallengeEdgeLib.sol


76              if (originId == 0) {
82              if (startHistoryRoot == 0) {
85              if (endHistoryRoot == 0) {
106             if (claimId == 0) {
224             return edge.createdAtBlock != 0;
231             if (len == 0) {
240             if (edge.lowerChildId != 0 || edge.upperChildId != 0) {
259             return edge.claimId != 0 && edge.staker != address(0);
271             if (edge.refunded == true) {
280             if (level == 0) {


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/challengeV2/libraries/ChallengeEdgeLib.sol#L0:0

```solidity
File: src/challengeV2/libraries/EdgeChallengeManagerLib.sol


182             if (firstRival == 0) {
198                 firstRival != 0,
199                 edge.claimId != 0
229                 if (ard.assertionHash == 0) {
248                 if (args.proof.length == 0) {
294                 if (args.proof.length == 0) {
329             if (x == 0) {
337             return ((x & y) == 0);
378             if (args.prefixProof.length == 0) {
445             while (edge.level > 0) {
472             if (firstRival == 0) {
485             return (hasRival(store, edgeId) && store.edges[edgeId].length() == 1);
545             if (firstRival == 0) {
577             if (end - start < 2) {
580             if (end - start == 2) {
788             if (store.edges[edgeId].length() != 1) {
800                 while (store.edges[cursor].level > 1) {


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/challengeV2/libraries/EdgeChallengeManagerLib.sol#L0:0

```solidity
File: src/challengeV2/libraries/MerkleTreeLib.sol


111             require(me.length > 0, "Empty merkle expansion");
117                 if (accum == 0) {
118                     if (val != 0) {
129                 } else if (val != 0) {
159             require(subtreeRoot != 0, "Cannot append empty subtree");
162             if (me.length == 0) {
195                     require(me[i] == 0, "Append above least significant bit");
198                     if (accumHash == 0) {
203                         if (me[i] == 0) {
222             if (accumHash != 0) {
228             require(next[next.length - 1] != 0, "Last entry zero");
275             if (y != 0) {
282             if (z != 0) {
295                 if (me[i] != 0) {
320             require(preSize > 0, "Pre-size cannot be 0");


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/challengeV2/libraries/MerkleTreeLib.sol#L0:0

```solidity
File: src/challengeV2/libraries/UintUtilsLib.sol


15              require(x > 0, "Zero has no significant bits");
30              require(x != 0, "Zero has no significant bits");
33              if (x >= 0x100000000000000000000000000000000) {
38              if (x >= 0x10000000000000000) {
43              if (x >= 0x100000000) {
48              if (x >= 0x10000) {
53              if (x >= 0x100) {
58              if (x >= 0x10) {
63              if (x >= 0x4) {
68              if (x >= 0x2) msb += 1;


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/challengeV2/libraries/UintUtilsLib.sol#L0:0

```solidity
File: src/rollup/Assertion.sol


86              if (self.firstChildBlock == 0) {
88              } else if (self.secondChildBlock == 0) {


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/rollup/Assertion.sol#L0:0

```solidity
File: src/rollup/BOLDUpgradeAction.sol


114             require(inboxMaxCount != 0, "Hash not yet set");
347             if (stakerCount > 50) {
353                 if (staker.isStaked && staker.currentChallenge == 0) {
526             if (validators.length != 0) {


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/rollup/BOLDUpgradeAction.sol#L0:0

```solidity
File: src/rollup/BridgeCreator.sol


107             bool isDelayBufferable = bufferConfig.threshold != 0;


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/rollup/BridgeCreator.sol#L0:0

```solidity
File: src/rollup/RollupAdminLogic.sol


40              if (connectedContracts.sequencerInbox.totalDelayedMessagesRead() == 0) {
181             require(_validator.length > 0, "EMPTY_ARRAY");
214             require(newConfirmPeriod > 0, "INVALID_CONFIRM_PERIOD");
229             require(staker.length > 0, "EMPTY_ARRAY");


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/rollup/RollupAdminLogic.sol#L0:0

```solidity
File: src/rollup/RollupCore.sol


148                 require(blockNum > 0, "NO_ASSERTION");
424                 require(afterGS.comparePositions(beforeGS) >= 0, "INBOX_BACKWARDS");
427                 require(afterStateCmpMaxInbox <= 0, "INBOX_TOO_FAR");
429                 if (assertion.afterState.machineStatus != MachineStatus.ERRORED && afterStateCmpMaxInbox < 0) {
433                     require(afterGS.comparePositions(beforeGS) > 0, "OVERFLOW_STANDSTILL");
438                 require(afterGS.comparePositionsAgainstStartOfBatch(currentInboxPosition) <= 0, "INBOX_PAST_END");
466                 require(afterInboxPosition != 0, "EMPTY_INBOX_COUNT");
489                 prevAssertion.firstChildBlock == 0, // assumes block 0 is impossible
572             bool haveChild = getAssertionStorage(lastestAssertion).firstChildBlock > 0;


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/rollup/RollupCore.sol#L0:0

```solidity
File: src/rollup/RollupCreator.sol


233             if (deployParams.validators.length != 0) {


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/rollup/RollupCreator.sol#L0:0

```solidity
File: src/rollup/RollupUserLogic.sol


53              if (latestConfirmedAssertion.createdAtBlock == 0) return false;
56              if (latestConfirmedAssertion.firstChildBlock > 0) {
115             if (prevAssertion.secondChildBlock > 0) {
120                 require(winningEdge.confirmedAtBlock != 0, "ZERO_CONFIRMED_AT_BLOCK");
196                 lastAssertion == prevAssertion || getAssertionStorage(lastAssertion).firstChildBlock > 0,
360             require(amount > 0, "NO_FUNDS_TO_WITHDRAW");


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/rollup/RollupUserLogic.sol#L0:0

</details>

## NC106 - else-block not required:

One level of nesting can be removed by not having an else block when the if-block returns


<details>
<summary>Click to show 6 findings</summary>

```solidity
File: src/assertionStakingPool/StakingPoolCreatorUtils.sol


16              if (Address.isContract(pool)) {
17                  return pool;
18              } else {
19                  revert PoolDoesntExist();
20              }


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/assertionStakingPool/StakingPoolCreatorUtils.sol#L0:0

```solidity
File: src/bridge/SequencerInbox.sol


279             if (_chainIdChanged()) {
280                 return (1, 1, 1, 1);
281             } else {
282                 return (delayBlocks, futureBlocks, delaySeconds, futureSeconds);
283             }


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/bridge/SequencerInbox.sol#L0:0

```solidity
File: src/challengeV2/EdgeChallengeManager.sol


592             if (eType == EdgeType.Block) {
593                 return LAYERZERO_BLOCKEDGE_HEIGHT;
594             } else if (eType == EdgeType.BigStep) {
595                 return LAYERZERO_BIGSTEPEDGE_HEIGHT;
596             } else if (eType == EdgeType.SmallStep) {
597                 return LAYERZERO_SMALLSTEPEDGE_HEIGHT;
598             } else {
599                 revert InvalidEdgeType(eType);
600             }
594             } else if (eType == EdgeType.BigStep) {
595                 return LAYERZERO_BIGSTEPEDGE_HEIGHT;
596             } else if (eType == EdgeType.SmallStep) {
597                 return LAYERZERO_SMALLSTEPEDGE_HEIGHT;
598             } else {
599                 revert InvalidEdgeType(eType);
600             }
596             } else if (eType == EdgeType.SmallStep) {
597                 return LAYERZERO_SMALLSTEPEDGE_HEIGHT;
598             } else {
599                 revert InvalidEdgeType(eType);
600             }


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/challengeV2/EdgeChallengeManager.sol#L0:0

```solidity
File: src/challengeV2/libraries/ChallengeEdgeLib.sol


280             if (level == 0) {
281                 return EdgeType.Block;
282             } else if (level <= numBigStepLevels) {
283                 return EdgeType.BigStep;
284             } else if (level == numBigStepLevels + 1) {
285                 return EdgeType.SmallStep;
286             } else {
287                 revert LevelTooHigh(level, numBigStepLevels);
288             }
282             } else if (level <= numBigStepLevels) {
283                 return EdgeType.BigStep;
284             } else if (level == numBigStepLevels + 1) {
285                 return EdgeType.SmallStep;
286             } else {
287                 revert LevelTooHigh(level, numBigStepLevels);
288             }
284             } else if (level == numBigStepLevels + 1) {
285                 return EdgeType.SmallStep;
286             } else {
287                 revert LevelTooHigh(level, numBigStepLevels);
288             }


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/challengeV2/libraries/ChallengeEdgeLib.sol#L0:0

```solidity
File: src/challengeV2/libraries/EdgeChallengeManagerLib.sol


220             if (ChallengeEdgeLib.levelToType(args.level, numBigStepLevel) == EdgeType.Block) {
221                 // origin id is the assertion which is the root of challenge
222                 // all rivals and their children share the same origin id - it is a link to the information
223                 // they agree on
224                 bytes32 originId = ard.predecessorId;
225     
226                 // Sanity check: The assertion reference data should be related to the claim
227                 // Of course the caller can provide whatever args they wish, so this is really just a helpful
228                 // check to avoid mistakes
229                 if (ard.assertionHash == 0) {
230                     revert AssertionHashEmpty();
231                 }
232                 if (ard.assertionHash != args.claimId) {
233                     revert AssertionHashMismatch(ard.assertionHash, args.claimId);
234                 }
235     
236                 // if the assertion is already confirmed or rejected then it cant be referenced as a claim
237                 if (!ard.isPending) {
238                     revert AssertionNotPending();
239                 }
240     
241                 // if the claim doesnt have a sibling then it is undisputed, there's no need
242                 // to open challenge edges for it
243                 if (!ard.hasSibling) {
244                     revert AssertionNoSibling();
245                 }
246     
247                 // parse the inclusion proof for later use
248                 if (args.proof.length == 0) {
249                     revert EmptyEdgeSpecificProof();
250                 }
251                 (bytes32[] memory inclusionProof,,) =
252                     abi.decode(args.proof, (bytes32[], AssertionStateData, AssertionStateData));
253     
254                 // check the start and end execution states exist, the block hash entry should be non zero
255                 if (ard.startState.machineStatus == MachineStatus.RUNNING) {
256                     revert EmptyStartMachineStatus();
257                 }
258                 if (ard.endState.machineStatus == MachineStatus.RUNNING) {
259                     revert EmptyEndMachineStatus();
260                 }
261     
262                 // Create machine hashes out of the proven state
263                 bytes32 startStateHash = oneStepProofEntry.getMachineHash(ard.startState.toExecutionState());
264                 bytes32 endStateHash = oneStepProofEntry.getMachineHash(ard.endState.toExecutionState());
265     
266                 return (ProofData(startStateHash, endStateHash, inclusionProof), originId);
267             } else {
268                 // Claim must be length one. If it is unrivaled then its unrivaled time is ticking up, so there's
269                 // no need to create claims against it
270                 if (!hasLengthOneRival(store, args.claimId)) {
271                     revert ClaimEdgeNotLengthOneRival(args.claimId);
272                 }
273     
274                 // hasLengthOneRival checks existance, so we can use getNoCheck
275                 ChallengeEdge storage claimEdge = getNoCheck(store, args.claimId);
276     
277                 // origin id is the mutual id of the claim
278                 // all rivals and their children share the same origin id - it is a link to the information
279                 // they agree on
280                 bytes32 originId = claimEdge.mutualId();
281     
282                 // once a claim is confirmed it's status can never become pending again, so there is no point
283                 // opening a challenge that references it
284                 if (claimEdge.status != EdgeStatus.Pending) {
285                     revert ClaimEdgeNotPending();
286                 }
287     
288                 // the edge must be a level up from the claim
289                 if (args.level != nextEdgeLevel(claimEdge.level, numBigStepLevel)) {
290                     revert ClaimEdgeInvalidLevel(args.level, claimEdge.level);
291                 }
292     
293                 // parse the proofs
294                 if (args.proof.length == 0) {
295                     revert EmptyEdgeSpecificProof();
296                 }
297                 (
298                     bytes32 startState,
299                     bytes32 endState,
300                     bytes32[] memory claimStartInclusionProof,
301                     bytes32[] memory claimEndInclusionProof,
302                     bytes32[] memory edgeInclusionProof
303                 ) = abi.decode(args.proof, (bytes32, bytes32, bytes32[], bytes32[], bytes32[]));
304     
305                 // if the start and end states are consistent with the claim edge
306                 // this guarantees that the edge we're creating is a 'continuation' of the claim edge, it is
307                 // a commitment to the states that between start and end states of the claim
308                 MerkleTreeLib.verifyInclusionProof(
309                     claimEdge.startHistoryRoot, startState, claimEdge.startHeight, claimStartInclusionProof
310                 );
311     
312                 // it's doubly important to check the end state since if the end state since the claim id is
313                 // not part of the edge id, so we need to ensure that it's not possible to create two edges of the
314                 // same id, but with different claim id. Ensuring that the end state is linked to the claim,
315                 // and later ensuring that the end state is part of the history commitment of the new edge ensures
316                 // that the end history root of the new edge will be different for different claim ids, and therefore
317                 // the edge ids will be different
318                 MerkleTreeLib.verifyInclusionProof(
319                     claimEdge.endHistoryRoot, endState, claimEdge.endHeight, claimEndInclusionProof
320                 );
321     
322                 return (ProofData(startState, endState, edgeInclusionProof), originId);
323             }
551             if (firstRival == UNRIVALED) {
552                 return block.number - store.edges[edgeId].createdAtBlock;
553             } else {
554                 // Sanity check: it's not possible an edge does not exist for a first rival record
555                 if (!store.edges[firstRival].exists()) {
556                     revert EdgeNotExists(firstRival);
557                 }
558     
559                 // rivals exist for this edge
560                 uint256 firstRivalCreatedAtBlock = store.edges[firstRival].createdAtBlock;
561                 uint256 edgeCreatedAtBlock = store.edges[edgeId].createdAtBlock;
562                 if (firstRivalCreatedAtBlock > edgeCreatedAtBlock) {
563                     // if this edge was created before the first rival then we return the difference
564                     // in createdAtBlock number
565                     return firstRivalCreatedAtBlock - edgeCreatedAtBlock;
566                 } else {
567                     // if this was created at the same time as, or after the the first rival
568                     // then we return 0
569                     return 0;
570                 }
571             }
562                 if (firstRivalCreatedAtBlock > edgeCreatedAtBlock) {
563                     // if this edge was created before the first rival then we return the difference
564                     // in createdAtBlock number
565                     return firstRivalCreatedAtBlock - edgeCreatedAtBlock;
566                 } else {
567                     // if this was created at the same time as, or after the the first rival
568                     // then we return 0
569                     return 0;
570                 }


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/challengeV2/libraries/EdgeChallengeManagerLib.sol#L0:0

```solidity
File: src/rollup/RollupCore.sol


146             if (_hostChainIsArbitrum) {
147                 uint256 blockNum = _assertionCreatedAtArbSysBlock[assertionHash];
148                 require(blockNum > 0, "NO_ASSERTION");
149                 return blockNum;
150             } else {
151                 AssertionNode storage assertion = getAssertionStorage(assertionHash);
152                 assertion.requireExists();
153                 return assertion.createdAtBlock;
154             }


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/rollup/RollupCore.sol#L0:0

</details>

## NC107 - Events may be emitted out of order due to reentrancy:

Ensure that events follow the best practice of check-effects-interaction, and are emitted before external calls


<details>
<summary>Click to show 4 findings</summary>

```solidity
File: src/assertionStakingPool/AbsBoldStakingPool.sol


/// @audit safeTransferFrom() called before event
37              emit StakeDeposited(msg.sender, amount);


/// @audit safeTransfer() called before event
53              emit StakeWithdrawn(msg.sender, amount);


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/assertionStakingPool/AbsBoldStakingPool.sol#L53:53

```solidity
File: src/challengeV2/EdgeChallengeManager.sol


/// @audit safeTransferFrom() called before event
437             emit EdgeAdded(
438                 edgeAdded.edgeId,
439                 edgeAdded.mutualId,
440                 edgeAdded.originId,
441                 edgeAdded.claimId,
442                 edgeAdded.length,
443                 edgeAdded.level,
444                 edgeAdded.hasRival,
445                 edgeAdded.isLayerZero
446             );


/// @audit safeTransfer() called before event
584             emit EdgeRefunded(edgeId, store.edges[edgeId].mutualId(), address(st), sa);


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/challengeV2/EdgeChallengeManager.sol#L584:584

</details>

## NC108 - If-statement can be converted to a ternary:

The code can be made more compact while also increasing readability by converting the following if-statements to ternaries (e.g. foo += (x > y) ? a : b)


```solidity
File: src/bridge/SequencerInbox.sol


279             if (_chainIdChanged()) {
280                 return (1, 1, 1, 1);
281             } else {
282                 return (delayBlocks, futureBlocks, delaySeconds, futureSeconds);
283             }


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/bridge/SequencerInbox.sol#L0:0

```solidity
File: src/challengeV2/libraries/EdgeChallengeManagerLib.sol


562                 if (firstRivalCreatedAtBlock > edgeCreatedAtBlock) {
563                     // if this edge was created before the first rival then we return the difference
564                     // in createdAtBlock number
565                     return firstRivalCreatedAtBlock - edgeCreatedAtBlock;
566                 } else {
567                     // if this was created at the same time as, or after the the first rival
568                     // then we return 0
569                     return 0;
570                 }


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/challengeV2/libraries/EdgeChallengeManagerLib.sol#L0:0

```solidity
File: src/rollup/RollupCore.sol


451                 if (afterInboxPosition == currentInboxPosition) {
452                     // No new messages have been added to the inbox since the last assertion
453                     // In this case if we set the next inbox position to the current one we would be insisting that
454                     // the next assertion process no messages. So instead we increment the next inbox position to current
455                     // plus one, so that the next assertion will process exactly one message.
456                     // Thus, no assertion can be empty (except the genesis assertion, which is created
457                     // via a different codepath).
458                     nextInboxPosition = currentInboxPosition + 1;
459                 } else {
460                     nextInboxPosition = currentInboxPosition;
461                 }


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/rollup/RollupCore.sol#L0:0

## NC109 - Import declarations should import specific identifiers, rather than the whole file:

Using import declarations of the form import {<identifier_name>} from 'some/file.sol' avoids polluting the symbol namespace making flattened files smaller, and speeds up compilation


<details>
<summary>Click to show 10 findings</summary>

```solidity
File: src/assertionStakingPool/AssertionStakingPool.sol


8       import "cool/node_modules/@openzeppelin/contracts/token/ERC20/IERC20.sol";


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/assertionStakingPool/AssertionStakingPool.sol#L0:0

```solidity
File: src/assertionStakingPool/EdgeStakingPool.sol


11      import "cool/node_modules/@openzeppelin/contracts/token/ERC20/IERC20.sol";
12      import "cool/node_modules/@openzeppelin/contracts/token/ERC20/utils/SafeERC20.sol";


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/assertionStakingPool/EdgeStakingPool.sol#L0:0

```solidity
File: src/assertionStakingPool/StakingPoolCreatorUtils.sol


8       import "cool/node_modules/@openzeppelin/contracts/utils/Create2.sol";
9       import "cool/node_modules/@openzeppelin/contracts/utils/Address.sol";


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/assertionStakingPool/StakingPoolCreatorUtils.sol#L0:0

```solidity
File: src/challengeV2/EdgeChallengeManager.sol


14      import "cool/node_modules/@openzeppelin/contracts-upgradeable/proxy/utils/Initializable.sol";
15      import "cool/node_modules/@openzeppelin/contracts/token/ERC20/utils/SafeERC20.sol";


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/challengeV2/EdgeChallengeManager.sol#L0:0

```solidity
File: src/rollup/BOLDUpgradeAction.sol


7       import "cool/node_modules/@openzeppelin/contracts-upgradeable/utils/Create2Upgradeable.sol";
8       import "cool/node_modules/@openzeppelin/contracts/proxy/transparent/ProxyAdmin.sol";


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/rollup/BOLDUpgradeAction.sol#L0:0

```solidity
File: src/rollup/BridgeCreator.sol


18      import "cool/node_modules/@openzeppelin/contracts/access/Ownable.sol";
19      import "cool/node_modules/@openzeppelin/contracts/proxy/transparent/ProxyAdmin.sol";


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/rollup/BridgeCreator.sol#L0:0

```solidity
File: src/rollup/RollupAdminLogic.sol


13      import "cool/node_modules/@openzeppelin/contracts/proxy/beacon/UpgradeableBeacon.sol";


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/rollup/RollupAdminLogic.sol#L0:0

```solidity
File: src/rollup/RollupCore.sol


7       import "cool/node_modules/@openzeppelin/contracts-upgradeable/security/PausableUpgradeable.sol";


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/rollup/RollupCore.sol#L0:0

```solidity
File: src/rollup/RollupCreator.sol


11      import "cool/node_modules/@openzeppelin/contracts/proxy/transparent/ProxyAdmin.sol";
12      import "cool/node_modules/@openzeppelin/contracts/proxy/transparent/TransparentUpgradeableProxy.sol";
13      import "cool/node_modules/@openzeppelin/contracts/access/Ownable.sol";


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/rollup/RollupCreator.sol#L0:0

```solidity
File: src/rollup/RollupUserLogic.sol


7       import "cool/node_modules/@openzeppelin/contracts/token/ERC20/IERC20.sol";


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/rollup/RollupUserLogic.sol#L0:0

</details>

## NC110 - Public functions not called by the contract should be declared external instead:

Contracts [are allowed](https://docs.soliditylang.org/en/latest/contracts.html#function-overriding) to override their parents' functions and change the visibility from `external` to `public`.


<details>
<summary>Click to show 4 findings</summary>

```solidity
File: src/challengeV2/EdgeChallengeManager.sol


305         function initialize(
306             IAssertionChain _assertionChain,
307             uint64 _challengePeriodBlocks,
308             IOneStepProofEntry _oneStepProofEntry,
309             uint256 layerZeroBlockEdgeHeight,
310             uint256 layerZeroBigStepEdgeHeight,
311             uint256 layerZeroSmallStepEdgeHeight,
312             IERC20 _stakeToken,
313             address _excessStakeReceiver,
314             uint8 _numBigStepLevel,
315             uint256[] calldata _stakeAmounts
316         ) public initializer {
317             if (address(_assertionChain) == address(0)) {
318                 revert EmptyAssertionChain();
319             }
320             assertionChain = _assertionChain;
321             if (address(_oneStepProofEntry) == address(0)) {
322                 revert EmptyOneStepProofEntry();
323             }
324             oneStepProofEntry = _oneStepProofEntry;
325             if (_challengePeriodBlocks == 0) {
326                 revert EmptyChallengePeriod();
327             }
328             challengePeriodBlocks = _challengePeriodBlocks;
329     
330             stakeToken = _stakeToken;
331             if (_excessStakeReceiver == address(0)) {
332                 revert EmptyStakeReceiver();
333             }
334             excessStakeReceiver = _excessStakeReceiver;
335     
336             if (!EdgeChallengeManagerLib.isPowerOfTwo(layerZeroBlockEdgeHeight)) {
337                 revert NotPowerOfTwo(layerZeroBlockEdgeHeight);
338             }
339             LAYERZERO_BLOCKEDGE_HEIGHT = layerZeroBlockEdgeHeight;
340             if (!EdgeChallengeManagerLib.isPowerOfTwo(layerZeroBigStepEdgeHeight)) {
341                 revert NotPowerOfTwo(layerZeroBigStepEdgeHeight);
342             }
343             LAYERZERO_BIGSTEPEDGE_HEIGHT = layerZeroBigStepEdgeHeight;
344             if (!EdgeChallengeManagerLib.isPowerOfTwo(layerZeroSmallStepEdgeHeight)) {
345                 revert NotPowerOfTwo(layerZeroSmallStepEdgeHeight);
346             }
347             LAYERZERO_SMALLSTEPEDGE_HEIGHT = layerZeroSmallStepEdgeHeight;
348     
349             // ensure that there is at least on of each type of level
350             if (_numBigStepLevel == 0) {
351                 revert ZeroBigStepLevels();
352             }
353             // ensure there's also space for the block level and the small step level
354             // in total level parameters
355             if (_numBigStepLevel > 253) {
356                 revert BigStepLevelsTooMany(_numBigStepLevel);
357             }
358             NUM_BIGSTEP_LEVEL = _numBigStepLevel;
359     
360             if (_numBigStepLevel + 2 != _stakeAmounts.length) {
361                 revert StakeAmountsMismatch(_stakeAmounts.length, _numBigStepLevel + 2);
362             }
363             stakeAmounts = _stakeAmounts;
364         }
491         function multiUpdateTimeCacheByChildren(bytes32[] calldata edgeIds) public {
492             for (uint256 i = 0; i < edgeIds.length; i++) {
493                 (bool updated, uint256 newValue) = store.updateTimerCacheByChildren(edgeIds[i]);
494                 if (updated) emit TimerCacheUpdated(edgeIds[i], newValue);
495             }
496         }
572         function refundStake(bytes32 edgeId) public {
573             ChallengeEdge storage edge = store.get(edgeId);
574             // setting refunded also do checks that the edge cannot be refunded twice
575             edge.setRefunded();
576     
577             IERC20 st = stakeToken;
578             uint256 sa = stakeAmounts[edge.level];
579             // no need to refund with the token or amount where zero'd out
580             if (address(st) != address(0) && sa != 0) {
581                 st.safeTransfer(edge.staker, sa);
582             }
583     
584             emit EdgeRefunded(edgeId, store.edges[edgeId].mutualId(), address(st), sa);
585         }
604         function calculateEdgeId(
605             uint8 level,
606             bytes32 originId,
607             uint256 startHeight,
608             bytes32 startHistoryRoot,
609             uint256 endHeight,
610             bytes32 endHistoryRoot
611         ) public pure returns (bytes32) {
612             return ChallengeEdgeLib.idComponent(level, originId, startHeight, startHistoryRoot, endHeight, endHistoryRoot);
613         }
616         function calculateMutualId(
617             uint8 level,
618             bytes32 originId,
619             uint256 startHeight,
620             bytes32 startHistoryRoot,
621             uint256 endHeight
622         ) public pure returns (bytes32) {
623             return ChallengeEdgeLib.mutualIdComponent(level, originId, startHeight, startHistoryRoot, endHeight);
624         }
627         function edgeExists(bytes32 edgeId) public view returns (bool) {
628             return store.edges[edgeId].exists();
629         }
632         function getEdge(bytes32 edgeId) public view returns (ChallengeEdge memory) {
633             return store.get(edgeId);
634         }
637         function edgeLength(bytes32 edgeId) public view returns (uint256) {
638             return store.get(edgeId).length();
639         }
647         function confirmedRival(bytes32 mutualId) public view returns (bytes32) {
648             return store.confirmedRivals[mutualId];
649         }
667         function firstRival(bytes32 mutualId) public view returns (bytes32) {
668             return store.firstRivals[mutualId];
669         }


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/challengeV2/EdgeChallengeManager.sol#L0:0

```solidity
File: src/rollup/BOLDUpgradeAction.sol


106         function set(bytes32 h, ExecutionState calldata executionState, uint256 inboxMaxCount) public {
107             require(h == stateHash(executionState, inboxMaxCount), "Invalid hash");
108             preImages[h] = abi.encode(executionState, inboxMaxCount);
109             emit HashSet(h, executionState, inboxMaxCount);
110         }


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/rollup/BOLDUpgradeAction.sol#L0:0

```solidity
File: src/rollup/RollupCore.sol


134         function getAssertion(bytes32 assertionHash) public view override returns (AssertionNode memory) {
135             return getAssertionStorage(assertionHash);
136         }
217         function stakerCount() public view override returns (uint64) {
218             return uint64(_stakerList.length);
219         }


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/rollup/RollupCore.sol#L0:0

```solidity
File: src/rollup/RollupCreator.sol


137         function createRollup(RollupDeploymentParams memory deployParams)
138             public
139             payable
140             returns (address)
141         {
142             {
143                 // Make sure the immutable maxDataSize is as expected
144                 (
145                     ,
146                     ISequencerInbox ethSequencerInbox,
147                     ISequencerInbox ethDelayBufferableSequencerInbox,
148                     IInboxBase ethInbox,
149                     ,
150     
151                 ) = bridgeCreator.ethBasedTemplates();
152                 require(
153                     deployParams.maxDataSize == ethSequencerInbox.maxDataSize(),
154                     "SI_MAX_DATA_SIZE_MISMATCH"
155                 );
156                 require(
157                     deployParams.maxDataSize == ethDelayBufferableSequencerInbox.maxDataSize(),
158                     "SI_MAX_DATA_SIZE_MISMATCH"
159                 );
160                 require(deployParams.maxDataSize == ethInbox.maxDataSize(), "I_MAX_DATA_SIZE_MISMATCH");
161     
162                 (
163                     ,
164                     ISequencerInbox erc20SequencerInbox,
165                     ISequencerInbox erc20DelayBufferableSequencerInbox,
166                     IInboxBase erc20Inbox,
167                     ,
168     
169                 ) = bridgeCreator.erc20BasedTemplates();
170                 require(
171                     deployParams.maxDataSize == erc20SequencerInbox.maxDataSize(),
172                     "SI_MAX_DATA_SIZE_MISMATCH"
173                 );
174                 require(
175                     deployParams.maxDataSize == erc20DelayBufferableSequencerInbox.maxDataSize(),
176                     "SI_MAX_DATA_SIZE_MISMATCH"
177                 );
178                 require(
179                     deployParams.maxDataSize == erc20Inbox.maxDataSize(),
180                     "I_MAX_DATA_SIZE_MISMATCH"
181                 );
182             }
183     
184             // create proxy admin which will manage bridge contracts
185             ProxyAdmin proxyAdmin = new ProxyAdmin();
186     
187             // Create the rollup proxy to figure out the address and initialize it later
188             RollupProxy rollup = new RollupProxy{salt: keccak256(abi.encode(deployParams))}();
189     
190             BridgeCreator.BridgeContracts memory bridgeContracts = bridgeCreator.createBridge(
191                 address(proxyAdmin),
192                 address(rollup),
193                 deployParams.nativeToken,
194                 deployParams.config.sequencerInboxMaxTimeVariation,
195                 deployParams.config.bufferConfig
196             );
197     
198             IEdgeChallengeManager challengeManager = createChallengeManager(address(rollup), address(proxyAdmin), deployParams.config);
199     
200             // deploy and init upgrade executor
201             address upgradeExecutor = _deployUpgradeExecutor(deployParams.config.owner, proxyAdmin);
202     
203             // upgradeExecutor shall be proxyAdmin's owner
204             proxyAdmin.transferOwnership(address(upgradeExecutor));
205     
206             // initialize the rollup with this contract as owner to set batch poster and validators
207             // it will transfer the ownership to the upgrade executor later
208             deployParams.config.owner = address(this);
209             rollup.initializeProxy(
210                 deployParams.config,
211                 ContractDependencies({
212                     bridge: bridgeContracts.bridge,
213                     sequencerInbox: bridgeContracts.sequencerInbox,
214                     inbox: bridgeContracts.inbox,
215                     outbox: bridgeContracts.outbox,
216                     rollupEventInbox: bridgeContracts.rollupEventInbox,
217                     challengeManager: challengeManager,
218                     rollupAdminLogic: address(rollupAdminLogic),
219                     rollupUserLogic: rollupUserLogic,
220                     validatorWalletCreator: validatorWalletCreator
221                 })
222             );
223     
224             // Setting batch posters and batch poster manager
225             for (uint256 i = 0; i < deployParams.batchPosters.length; i++) {
226                 bridgeContracts.sequencerInbox.setIsBatchPoster(deployParams.batchPosters[i], true);
227             }
228             if (deployParams.batchPosterManager != address(0)) {
229                 bridgeContracts.sequencerInbox.setBatchPosterManager(deployParams.batchPosterManager);
230             }
231     
232             // Call setValidator on the newly created rollup contract just if validator set is not empty
233             if (deployParams.validators.length != 0) {
234                 bool[] memory _vals = new bool[](deployParams.validators.length);
235                 for (uint256 i = 0; i < deployParams.validators.length; i++) {
236                     _vals[i] = true;
237                 }
238                 IRollupAdmin(address(rollup)).setValidator(deployParams.validators, _vals);
239             }
240     
241             IRollupAdmin(address(rollup)).setOwner(address(upgradeExecutor));
242     
243             if (deployParams.deployFactoriesToL2) {
244                 _deployFactories(
245                     address(bridgeContracts.inbox),
246                     deployParams.nativeToken,
247                     deployParams.maxFeePerGasForRetryables
248                 );
249             }
250     
251             emit RollupCreated(
252                 address(rollup),
253                 deployParams.nativeToken,
254                 address(bridgeContracts.inbox),
255                 address(bridgeContracts.outbox),
256                 address(bridgeContracts.rollupEventInbox),
257                 address(challengeManager),
258                 address(proxyAdmin),
259                 address(bridgeContracts.sequencerInbox),
260                 address(bridgeContracts.bridge),
261                 address(upgradeExecutor),
262                 address(validatorWalletCreator)
263             );
264             return address(rollup);
265         }


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/rollup/RollupCreator.sol#L0:0

</details>

## NC111 - Constant redefined elsewhere:

Consider defining in only one contract so that values cannot become out of sync when only one location is updated. A cheap way to store constants in a single location is to create an internal constant in a library. If the variable is a local cache of another contract's value, consider making the cache variable internal or private, which will require external users to query the contract with the source of truth, so that callers don't get out of sync.


```solidity
File: src/rollup/BOLDUpgradeAction.sol


    IOldRollup public immutable rollup;

```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/rollup/BOLDUpgradeAction.sol#L124:124

## NC112 - Multiple `address`/ID mappings can be combined into a single `mapping` of an `address`/ID to a `struct`, for readability:

Well-organized data structures make code reviews easier, which may lead to fewer bugs. Consider combining related mappings into mappings to structs, so it's clear what data is related


```solidity
File: src/challengeV2/libraries/EdgeChallengeManagerLib.sol


76          mapping(bytes32 => ChallengeEdge) edges;
77          /// @notice A mapping of mutualId to edge id. Rivals share the same mutual id, and here we
78          ///         store the edge id of the second edge that was created with the same mutual id - the first rival
79          ///         When only one edge exists for a specific mutual id then a special magic string hash is stored instead
80          ///         of the first rival id, to signify that a single edge does exist with this mutual id
81          mapping(bytes32 => bytes32) firstRivals;
82          /// @notice A mapping of mutualId to the edge id of the confirmed rival with that mutualId
83          /// @dev    Each group of rivals (edges sharing mutual id) can only have at most one confirmed edge
84          mapping(bytes32 => bytes32) confirmedRivals;


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/challengeV2/libraries/EdgeChallengeManagerLib.sol#L0:0

```solidity
File: src/rollup/RollupCore.sol


102         mapping(address => Staker) public _stakerMap;
103     
104         mapping(address => uint256) private _withdrawableFunds;


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/rollup/RollupCore.sol#L0:0

## NC113 - Duplicated `require()`/`revert()` checks should be refactored to a modifier or function:

The compiler will inline the function, which will avoid JUMP instructions usually associated with functions.


```solidity
File: src/challengeV2/libraries/MerkleTreeLib.sol


112             require(me.length <= MAX_LEVEL, "Merkle expansion too large");


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/challengeV2/libraries/MerkleTreeLib.sol#L0:0

```solidity
File: src/rollup/RollupUserLogic.sol


63              require(!validatorWhitelistDisabled, "WHITELIST_DISABLED");


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/rollup/RollupUserLogic.sol#L0:0

## NC114 - Variables need not be initialized to zero:

The default value for variables is zero, so initializing them to zero is superfluous.


<details>
<summary>Click to show 6 findings</summary>

```solidity
File: src/challengeV2/EdgeChallengeManager.sol


492             for (uint256 i = 0; i < edgeIds.length; i++) {


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/challengeV2/EdgeChallengeManager.sol#L0:0

```solidity
File: src/challengeV2/libraries/ArrayUtilsLib.sol


15              for (uint256 i = 0; i < arr.length; i++) {
47              for (uint256 i = 0; i < arr1.length; i++) {
50              for (uint256 i = 0; i < arr2.length; i++) {


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/challengeV2/libraries/ArrayUtilsLib.sol#L0:0

```solidity
File: src/challengeV2/libraries/MerkleTreeLib.sol


115             for (uint256 i = 0; i < me.length; i++) {
188             for (uint256 i = 0; i < me.length; i++) {
294             for (uint256 i = 0; i < me.length; i++) {


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/challengeV2/libraries/MerkleTreeLib.sol#L0:0

```solidity
File: src/rollup/BOLDUpgradeAction.sol


350             for (uint64 i = 0; i < stakerCount; i++) {
528                 for (uint256 i = 0; i < validators.length; i++) {


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/rollup/BOLDUpgradeAction.sol#L0:0

```solidity
File: src/rollup/RollupAdminLogic.sol


184             for (uint256 i = 0; i < _validator.length; i++) {
230             for (uint256 i = 0; i < staker.length; i++) {


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/rollup/RollupAdminLogic.sol#L0:0

```solidity
File: src/rollup/RollupCreator.sol


225             for (uint256 i = 0; i < deployParams.batchPosters.length; i++) {
235                 for (uint256 i = 0; i < deployParams.validators.length; i++) {


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/rollup/RollupCreator.sol#L0:0

</details>

## NC115 - Use a more recent version of solidity:

Use a solidity version of at least 0.8.13 to get the ability to use `using for` with a list of free functions.


<details>
<summary>Click to show 10 findings</summary>

```solidity
File: src/assertionStakingPool/AbsBoldStakingPool.sol


5       pragma solidity ^0.8.0;


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/assertionStakingPool/AbsBoldStakingPool.sol#L0:0

```solidity
File: src/assertionStakingPool/AssertionStakingPool.sol


6       pragma solidity ^0.8.0;


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/assertionStakingPool/AssertionStakingPool.sol#L0:0

```solidity
File: src/assertionStakingPool/EdgeStakingPool.sol


5       pragma solidity ^0.8.0;


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/assertionStakingPool/EdgeStakingPool.sol#L0:0

```solidity
File: src/bridge/SequencerInbox.sol


5       pragma solidity ^0.8.0;


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/bridge/SequencerInbox.sol#L0:0

```solidity
File: src/rollup/BOLDUpgradeAction.sol


5       pragma solidity ^0.8.0;


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/rollup/BOLDUpgradeAction.sol#L0:0

```solidity
File: src/rollup/RollupAdminLogic.sol


5       pragma solidity ^0.8.0;


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/rollup/RollupAdminLogic.sol#L0:0

```solidity
File: src/rollup/RollupCore.sol


5       pragma solidity ^0.8.0;


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/rollup/RollupCore.sol#L0:0

```solidity
File: src/rollup/RollupCreator.sol


5       pragma solidity ^0.8.0;


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/rollup/RollupCreator.sol#L0:0

```solidity
File: src/rollup/RollupLib.sol


5       pragma solidity ^0.8.0;


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/rollup/RollupLib.sol#L0:0

```solidity
File: src/rollup/RollupUserLogic.sol


5       pragma solidity ^0.8.0;


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/rollup/RollupUserLogic.sol#L0:0

</details>

## NC116 - Variable names that consist of all capital letters should be reserved for constant/immutable variables:

If the variable needs to be different based on which class it comes from, a view/pure function should be used instead.


```solidity
File: src/bridge/SequencerInbox.sol


99          ISequencerInbox.MaxTimeVariation private __LEGACY_MAX_TIME_VARIATION;


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/bridge/SequencerInbox.sol#L0:0

```solidity
File: src/challengeV2/EdgeChallengeManager.sol


291         uint256 public LAYERZERO_BLOCKEDGE_HEIGHT;
293         uint256 public LAYERZERO_BIGSTEPEDGE_HEIGHT;
295         uint256 public LAYERZERO_SMALLSTEPEDGE_HEIGHT;
298         uint8 public NUM_BIGSTEP_LEVEL;


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/challengeV2/EdgeChallengeManager.sol#L0:0

## NC117 - Consider using delete rather than assigning false/zero to clear values:

The `delete` keyword more closely matches the semantics of what is being done, and draws more attention to the changing of state, which may lead to a more thorough audit of its associated logic.


```solidity
File: src/bridge/SequencerInbox.sol


927             dasKeySetInfo[ksHash].isValidKeyset = false;


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/bridge/SequencerInbox.sol#L0:0

```solidity
File: src/challengeV2/libraries/MerkleTreeLib.sol


212                             next[i] = 0;


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/challengeV2/libraries/MerkleTreeLib.sol#L0:0

```solidity
File: src/rollup/RollupCore.sol


333             _withdrawableFunds[account] = 0;


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/rollup/RollupCore.sol#L0:0

## NC118 - Variable names for `immutable`s should use CONSTANT_CASE:

For `immutable` variable names, each word should use all capital letters, with underscores separating each word (CONSTANT_CASE).


<details>
<summary>Click to show 7 findings</summary>

```solidity
File: src/assertionStakingPool/AbsBoldStakingPool.sol


20          address public immutable stakeToken;


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/assertionStakingPool/AbsBoldStakingPool.sol#L0:0

```solidity
File: src/assertionStakingPool/AssertionStakingPool.sol


25          address public immutable rollup;
27          bytes32 public immutable assertionHash;


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/assertionStakingPool/AssertionStakingPool.sol#L0:0

```solidity
File: src/assertionStakingPool/EdgeStakingPool.sol


29          address public immutable challengeManager;
31          bytes32 public immutable edgeId;


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/assertionStakingPool/EdgeStakingPool.sol#L0:0

```solidity
File: src/bridge/SequencerInbox.sol


116         IReader4844 public immutable reader4844;
128         uint256 public immutable maxDataSize;
129         uint256 internal immutable deployTimeChainId = block.chainid;
131         bool internal immutable hostChainIsArbitrum = ArbitrumChecker.runningOnArbitrum();
133         bool public immutable isUsingFeeToken;
135         bool public immutable isDelayBufferable;


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/bridge/SequencerInbox.sol#L0:0

```solidity
File: src/rollup/BOLDUpgradeAction.sol


124         IOldRollup public immutable rollup;


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/rollup/BOLDUpgradeAction.sol#L0:0

```solidity
File: src/rollup/RollupCore.sol


112         bool internal immutable _hostChainIsArbitrum = ArbitrumChecker.runningOnArbitrum();


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/rollup/RollupCore.sol#L0:0

```solidity
File: src/rollup/RollupUserLogic.sol


31          uint256 internal immutable deployTimeChainId = block.chainid;


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/rollup/RollupUserLogic.sol#L0:0

</details>

## NC119 - Lines are too long:

Usually lines in source code are limited to 80 characters. Today's screens are much larger so it's reasonable to stretch this in some cases. The solidity style guide recommends a maximumum line length of 120 characters, so the lines below should be split when they reach that length.


<details>
<summary>Click to show 102 findings</summary>

```solidity
File: src/assertionStakingPool/AbsBoldStakingPool.sol


///         If the total deposited amount exceeds the required amount, any depositor can withdraw some stake early even after the protocol move has been made.

```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/assertionStakingPool/AbsBoldStakingPool.sol#L13:13

```solidity
File: src/assertionStakingPool/AssertionStakingPoolCreator.sol


/// @notice Creates staking pool contract for a target assertion. Can be used for any child Arbitrum chain running on top of the deployed AssertionStakingPoolCreator's chain.

```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/assertionStakingPool/AssertionStakingPoolCreator.sol#L12:12

```solidity
File: src/assertionStakingPool/interfaces/IAssertionStakingPool.sol


/// @notice Create assertion. Callable only if required stake has been reached and assertion has not been asserted yet.

/// @dev Separate call from withdrawStakeBackIntoPool since returnOldDeposit reverts with 0 balance (in e.g., case of admin forceRefundStaker)

/// @dev Separate call from makeStakeWithdrawable since returnOldDeposit reverts with 0 balance (in e.g., case of admin forceRefundStaker)

```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/assertionStakingPool/interfaces/IAssertionStakingPool.sol#L20:20

```solidity
File: src/bridge/DelayBuffer.sol


/// @dev    Depletion is limited by the elapsed blocks in the delayed message queue to avoid double counting and potential L2 reorgs.

///         should count once as a single 100 block delay, not twice as a 200 block delay. This also prevents L2 reorg risk in edge cases.

///         Eg. If the buffer is 300 blocks, decrementing the buffer when processing the first batch would allow the second delay message to be force included before the sequencer could add the second batch.

///         Eg. when the sequencer recovers from an outage, it is able to wait threshold > finality time before queueing delayed messages to avoid L1 reorgs.

```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/bridge/DelayBuffer.sol#L24:24

```solidity
File: src/bridge/ISequencerInbox.sol


/// @notice The maximum amount of time variatin between a message being posted on the L1 and being executed on the L2

///      See: https://github.com/OffchainLabs/nitro/blob/69de0603abf6f900a4128cab7933df60cad54ded/arbstate/das_reader.go

///      See: https://github.com/OffchainLabs/nitro/blob/69de0603abf6f900a4128cab7933df60cad54ded/arbstate/das_reader.go

///      See: https://github.com/OffchainLabs/nitro/blob/69de0603abf6f900a4128cab7933df60cad54ded/arbstate/das_reader.go

///      See: https://github.com/OffchainLabs/nitro/blob/69de0603abf6f900a4128cab7933df60cad54ded/arbstate/das_reader.go

///      See: https://github.com/OffchainLabs/nitro/blob/69de0603abf6f900a4128cab7933df60cad54ded/arbstate/das_reader.go

///      See: https://github.com/OffchainLabs/nitro/blob/69de0603abf6f900a4128cab7933df60cad54ded/arbstate/das_reader.go

///         messages so it's only necessary to call this if the sequencer is down, or not including any delayed messages.

///         This is only relevant when the buffer is less than the delayBlocks (unhappy case), otherwise force inclusion deadline is fixed at delayBlocks.

```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/bridge/ISequencerInbox.sol#L159:159

```solidity
File: src/bridge/SequencerInbox.sol


* @notice Contains the inbox accumulator which is the ordering of all data and transactions to be processed by the rollup.

// Bridge in ETH based chains doesn't implement nativeToken(). In future it might implement it and return address(0)

///         We need to ensure that this data cannot cause a collision with data supplied via another method (eg blobs)

///         This also safe guards unused flags for future use, as we know they would have been disallowed up until this point

// The first data byte cannot be the same as any that have been set via other methods (eg 4844 blob header) as this

// das batches expect to have the type byte set, followed by the keyset (so they should have at least 33 bytes)

```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/bridge/SequencerInbox.sol#L708:708

```solidity
File: src/challengeV2/EdgeChallengeManager.sol


/// @param _challengePeriodBlocks       The amount of cumulative time an edge must spend unrivaled before it can be confirmed

///                                     This should be the censorship period + the cumulative amount of time needed to do any

///                                     offchain calculation. We currently estimate around 10 mins for each layer zero edge and 1

/// @param _stakeToken                  The token that stake will be provided in when creating zero layer block edges

/// @param _excessStakeReceiver         The address that excess stake will be sent to when 2nd+ block edge is created

/// @param prefixProof          A proof to show that the bisectionHistoryRoot commits to a prefix of the current endHistoryRoot

/// @notice Update multiple edges' timer cache by their children. Equivalent to calling updateTimerCacheByChildren for each edge.

/// @dev    When zero layer edges are created they reference an edge, or assertion, in the level below. If a zero layer

/// @param beforeHistoryInclusionProof  Proof that the state which is the start of the edge is committed to by the startHistoryRoot

/// @param afterHistoryInclusionProof   Proof that the state which is the end of the edge is committed to by the endHistoryRoot

/// @notice When two assertions are created that have the same predecessor the protocol needs to decide which of the two is correct

///         This challenge manager allows the staker who has created the valid assertion to enforce that it will be confirmed, and all

///         predecessor will vie for succession against each other. Stakers compete by creating edges that reference the assertion they

///         believe in. These edges are then bisected, reducing the size of the disagreement with each bisection, and narrowing in on the

///         exact point of disagreement. Eventually, at step size 1, the step can be proved on-chain directly proving that the related assertion

/// @notice An edge can be confirmed if the cumulative time (in blocks) unrivaled of it and a direct chain of ancestors is greater than a threshold

///         This excess stake receiver can then choose to refund the gas of participants who aided in the confirmation

```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/challengeV2/EdgeChallengeManager.sol#L271:271

```solidity
File: src/challengeV2/libraries/ChallengeEdgeLib.sol


///         For a SmallStep edge the origin id is the 'mutual' id of the length one BigStep edge being claimed by the zero layer ancestors of this edge

///         For a BigStep edge the origin id is the 'mutual' id of the length one Block edge being claimed by the zero layer ancestors of this edge

///         For a Block edge the origin id is the assertion hash of the assertion that is the root of the challenge - all edges in this challenge agree

/// @notice A root of all the states in the history up to the endHeight. Since endHeight > startHeight, the startHistoryRoot must

///         lower child is populated here, until that time this value is 0. The lower child has startHistoryRoot and startHeight

///         equal to this edge, but endHistoryRoot and endHeight equal to some prefix of the endHistoryRoot of this edge

///         upper child is populated here, until that time this value is 0. The upper child has startHistoryRoot and startHeight

///         equal to some prefix of the endHistoryRoot of this edge, and endHistoryRoot and endHeight equal to this edge

///         Rivals have the same start height, start history root and end height. They also have the same origin id and level.

///         Rivals have the same start height, start history root and end height. They also have the same origin id and level.

///         the whole struct into memory, so we're explicit here that this should be used for edges already in memory.

```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/challengeV2/libraries/ChallengeEdgeLib.sol#L207:207

```solidity
File: src/challengeV2/libraries/ChallengeErrors.sol


/// @dev Thrown when the validator whitelist is enabled and the account attempting to create a layer zero edge is not whitelisted

```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/challengeV2/libraries/ChallengeErrors.sol#L107:107

```solidity
File: src/challengeV2/libraries/EdgeChallengeManagerLib.sol


///         The first (level 0) being of type Block, followed by n (set by NUM_BIGSTEP_LEVEL) levels of type BigStep, and finally

///         of length one is reached before proceeding to the next level. The first edge in each level (the layer zero edge)

///         Finally in the last level, a SmallStep edge is added that claims a lower level length one BigStep edge, and these

///         bytes32[]: Claim start inclusion proof - proof to show the start state is the first state in the claim edge

/// @notice A mapping of account -> mutualId -> bool indicating if the account has created a layer zero edge with a mutual id

///                             The created edge must be shown to be consistent with the states in the assertion chain

/// @return                     Data parsed from the proof, or fetched from elsewhere. Also the origin id for the edge to be created.

// if the validator whitelist is enabled, we can enforce that a single party cannot create two layer zero edges that rival each other

// if the validator whitelist is disabled, this check serves no purpose since an attacker can create new accounts

/// @param prefixProof          A proof to show that the bisectionHistoryRoot commits to a prefix of the current endHistoryRoot

/// @notice An edge can be confirmed if the total amount of time (in blocks) it and a single chain of its direct ancestors

/// @param claimedAssertionUnrivaledBlocks  The number of blocks that the assertion ultimately being claimed by this edge spent unrivaled

/// @param confirmationThresholdBlock       The number of blocks that the total unrivaled time of an ancestor chain needs to exceed in

/// @param beforeHistoryInclusionProof  Proof that the state which is the start of the edge is committed to by the startHistoryRoot

/// @param afterHistoryInclusionProof   Proof that the state which is the end of the edge is committed to by the endHistoryRoot

```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/challengeV2/libraries/EdgeChallengeManagerLib.sol#L762:762

```solidity
File: src/challengeV2/libraries/MerkleTreeLib.sol


// it's important that we hash the leaf, this ensures that this leaf cannot be a collision with any other non leaf

```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/challengeV2/libraries/MerkleTreeLib.sol#L239:239

```solidity
File: src/libraries/Error.sol


/// @dev Thrown when batches are posted without buffer proof, this is only allowed in a sync state or when no new delayed messages are read

```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/libraries/Error.sol#L182:182

```solidity
File: src/rollup/Assertion.sol


// This value starts at zero and is set to a value when the first child is created. After that it is constant until the assertion is destroyed or the owner destroys pending assertions

// This value starts at zero and is set to a value when the second child is created. After that it is constant until the assertion is destroyed or the owner destroys pending assertions

// A hash of the context available at the time of this assertions creation. It should contain information that is not specific

// to this assertion, but instead to the environment at the time of creation. This is necessary to store on the assertion

// as this environment can change and we need to know what it was like at the time this assertion was created. An example

// changes we need to know that previous assertions were made under a different root, so that we can understand that they

// were valid at the time. So when resolving a challenge by one step, the edge challenge manager finds the wasm module root

```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/rollup/Assertion.sol#L34:34

```solidity
File: src/rollup/BOLDUpgradeAction.sol


// This value starts at zero and is set to a value when the first child is created. After that it is constant until the node is destroyed or the owner destroys pending nodes

chainConfig: "", // we can use an empty chain config it wont be used in the rollup initialization because we check if the rei is already connected there

```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/rollup/BOLDUpgradeAction.sol#L396:396

```solidity
File: src/rollup/IRollupCore.sol


event UserStakeUpdated(address indexed user, address indexed withdrawalAddress, uint256 initialBalance, uint256 finalBalance);

* Unlike the assertion's createdAtBlock field, this will be the ArbSys blockNumber if the host chain is an Arbitrum chain.

```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/rollup/IRollupCore.sol#L81:81

```solidity
File: src/rollup/RollupAdminLogic.sol


* The RollupAdmin may execute a check against the Rollup's latest assertion num or the OldChallengeManager, then execute this function atomically with it.

// 2. update the config hash of the assertion after which you wish to use the new wasm module root (functionality not written yet)

```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/rollup/RollupAdminLogic.sol#L245:245

```solidity
File: src/rollup/RollupCore.sol


// but it is the parent of the assertion the validator is trying to create, then we know that by the time the assertion

// The stake required to create an assertion can be updated by the rollup owner. A required stake value is stored on each

* Unlike the assertion's createdAtBlock field, this will be the ArbSys blockNumber if the host chain is an Arbitrum chain.

*          and check if the assertionHash is currently pending. If all checks pass, the assertion will be confirmed.

// there are 3 kinds of assertions that can be made. Assertions must be made when they fill the maximum number

//    The inbox can be anywhere between the previous assertion's position and the nextInboxPosition, exclusive.

//    All types of assertion must have inbox position in the range prev.inboxPosition <= x <= prev.nextInboxPosition

AssertionState memory emptyAssertionState = AssertionState(emptyGlobalState, MachineStatus.FINISHED, bytes32(0));

```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/rollup/RollupCore.sol#L522:522

```solidity
File: src/rollup/RollupCreator.sol


*          - nativeToken   Address of the custom fee token used by rollup. If rollup is ETH-based address(0) should be provided

*          - deployFactoriesToL2 Whether to deploy L2 factories using retryable tickets. If true, retryables need to be paid for in native currency.

*                          Deploying factories via retryable tickets at rollup creation time is the most reliable method to do it since it

*                          doesn't require paying the L1 gas. If deployment is not done as part of rollup creation TX, there is a risk that

*                          anyone can try to deploy factories and potentially burn the nonce 0 (ie. due to gas price spike when doing direct

*                          L2 TX). That would mean we permanently lost capability to deploy deterministic factory at expected address.

IEdgeChallengeManager challengeManager = createChallengeManager(address(rollup), address(proxyAdmin), deployParams.config);

```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/rollup/RollupCreator.sol#L198:198

```solidity
File: src/rollup/RollupUserLogic.sol


ChallengeEdge memory winningEdge = IEdgeChallengeManager(prevConfig.challengeManager).getEdge(winningEdgeId);

// we cannot do a refund here because the staker may be staker on an unconfirmed ancestor that requires more stake

* @notice Refund a staker that is currently staked on an assertion that either has a chlid assertion or is the latest confirmed assertion.

* @notice Reduce the amount staked for the sender (difference between initial amount staked and target is creditted back to the sender).

```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/rollup/RollupUserLogic.sol#L238:238

</details>

## NC120 - File is missing NatSpec comments:

The file does not contain any of the NatSpec comments (@inheritdoc, @param, @return, @notice), which are important for documentation and user confirmation.


<details>
<summary>Click to show 7 findings</summary>

```solidity
File: src/assertionStakingPool/StakingPoolCreatorUtils.sol


// Copyright 2021-2022, Offchain Labs, Inc.
// For license information, see https://github.com/OffchainLabs/nitro-contracts/blob/main/LICENSE
// SPDX-License-Identifier: BUSL-1.1
//

pragma solidity ^0.8.0;

import "cool/node_modules/@openzeppelin/contracts/utils/Create2.sol";
import "cool/node_modules/@openzeppelin/contracts/utils/Address.sol";

library StakingPoolCreatorUtils {
    error PoolDoesntExist();
    function getPool(bytes memory creationCode, bytes memory args) internal view returns (address) {
        bytes32 bytecodeHash = keccak256(abi.encodePacked(creationCode, args));
        address pool = Create2.computeAddress(0, bytecodeHash, address(this));
        if (Address.isContract(pool)) {
            return pool;
        } else {
            revert PoolDoesntExist();
        }
    }
}


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/assertionStakingPool/StakingPoolCreatorUtils.sol#L1:1

```solidity
File: src/challengeV2/libraries/ChallengeErrors.sol


// Copyright 2023, Offchain Labs, Inc.
// For license information, see https://github.com/offchainlabs/bold/blob/main/LICENSE
// SPDX-License-Identifier: BUSL-1.1
//
pragma solidity ^0.8.17;

import "./Enums.sol";

/// @dev The edge is not currently stored
error EdgeNotExists(bytes32 edgeId);
/// @dev The edge has already been stored
error EdgeAlreadyExists(bytes32 edgeId);
/// @dev The provided assertion hash was empty
error AssertionHashEmpty();
/// @dev The assertion hashes are not the same, but should have been
error AssertionHashMismatch(bytes32 h1, bytes32 h2);
/// @dev The assertion is not currently pending
error AssertionNotPending();
/// @dev The assertion has no sibling
error AssertionNoSibling();
/// @dev The edge type specific proof data is empty
error EmptyEdgeSpecificProof();
/// @dev The start machine status is empty
error EmptyStartMachineStatus();
/// @dev The end machine status is empty
error EmptyEndMachineStatus();
/// @dev The claim edge is not pending
error ClaimEdgeNotPending();
/// @dev The claim edge does not have a length one rival
error ClaimEdgeNotLengthOneRival(bytes32 claimId);
/// @dev The claim edge has an invalid level
error ClaimEdgeInvalidLevel(uint8 argLevel, uint8 claimLevel);
/// @dev The val is not a power of two
error NotPowerOfTwo(uint256 val);
/// @dev The height has an unexpected value
error InvalidEndHeight(uint256 actualHeight, uint256 expectedHeight);
/// @dev The prefix proof is empty
error EmptyPrefixProof();
/// @dev The edge is not of type Block
error EdgeTypeNotBlock(uint8 level);
/// @dev The edge is not of type SmallStep
error EdgeTypeNotSmallStep(uint8 level);
/// @dev The first rival record is empty
error EmptyFirstRival();
/// @dev The difference between two heights is less than 2
error HeightDiffLtTwo(uint256 h1, uint256 h2);
/// @dev The edge is not pending
error EdgeNotPending(bytes32 edgeId, EdgeStatus status);
/// @dev The edge is unrivaled
error EdgeUnrivaled(bytes32 edgeId);
/// @dev The edge is not confirmed
error EdgeNotConfirmed(bytes32 edgeId, EdgeStatus);
/// @dev The edge level is unexpected
error EdgeLevelInvalid(bytes32 edgeId1, bytes32 edgeId2, uint8 level1, uint8 level2);
/// @dev The claim id on the claimingEdge does not match the provided edge id
error EdgeClaimMismatch(bytes32 edgeId, bytes32 claimingEdgeId);
/// @dev The origin id is not equal to the mutual id
error OriginIdMutualIdMismatch(bytes32 mutualId, bytes32 originId);
/// @dev The edge does not have a valid ancestor link
error EdgeNotAncestor(
    bytes32 edgeId, bytes32 lowerChildId, bytes32 upperChildId, bytes32 ancestorEdgeId, bytes32 claimId
);
/// @dev The total number of blocks is not above the threshold
error InsufficientConfirmationBlocks(uint256 totalBlocks, uint256 thresholdBlocks);
/// @dev The edge is not of length one
error EdgeNotLengthOne(uint256 length);
/// @dev No origin id supplied when creating an edge
error EmptyOriginId();
/// @dev Invalid heights supplied when creating an edge
error InvalidHeights(uint256 start, uint256 end);
/// @dev No start root supplied when creating an edge
error EmptyStartRoot();
/// @dev No end root supplied when creating an edge
error EmptyEndRoot();
/// @dev No staker supplied when creating a layer zero edge
error EmptyStaker();
/// @dev No claim id supplied when creating a layer zero edge
error EmptyClaimId();
/// @dev Children already set on edge
error ChildrenAlreadySet(bytes32 edgeId, bytes32 lowerChildId, bytes32 upperChildId);
/// @dev Edge is not a layer zero edge
error EdgeNotLayerZero(bytes32 edgeId, address staker, bytes32 claimId);
/// @dev The edge staker has already been refunded
error EdgeAlreadyRefunded(bytes32 edgeId);
/// @dev No assertion chain address supplied
error EmptyAssertionChain();
/// @dev No one step proof entry address supplied
error EmptyOneStepProofEntry();
/// @dev No challenge period supplied
error EmptyChallengePeriod();
/// @dev No stake receiver address supplied
error EmptyStakeReceiver();
/// @dev Stake amounts does not match number of levels
error StakeAmountsMismatch(uint256 stakeLevels, uint256 numLevels);
/// @dev A rival edge is already confirmed
error RivalEdgeConfirmed(bytes32 edgeId, bytes32 confirmedRivalId);
/// @dev Thrown when big step levels is set to 0
error ZeroBigStepLevels();
/// @dev Thrown when there are too many big step levels requested
error BigStepLevelsTooMany(uint8 levels);
/// @dev Thrown when the level does not correspond to a valid type
error LevelTooHigh(uint8 level, uint8 numBigStepLevels);
/// @dev Thrown for unrecognised edge types
error InvalidEdgeType(EdgeType edgeType);
/// @dev Thrown when endHistoryRoot not matching the assertion
error EndHistoryRootMismatch(bytes32 endHistoryRoot, bytes32 assertionEndRoot);
/// @dev Thrown when the validator whitelist is enabled and the account attempting to create a layer zero edge is not whitelisted
error NotValidator(address account);
/// @dev Thrown when an account has already created a rivalling layer zero edge
error AccountHasMadeLayerZeroRival(address account, bytes32 mutualId);

```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/challengeV2/libraries/ChallengeErrors.sol#L1:1

```solidity
File: src/rollup/AssertionState.sol


// Copyright 2021-2022, Offchain Labs, Inc.
// For license information, see https://github.com/OffchainLabs/nitro-contracts/blob/main/LICENSE
// SPDX-License-Identifier: BUSL-1.1

pragma solidity ^0.8.0;

import "../state/GlobalState.sol";
import "../state/Machine.sol";
import "../osp/IOneStepProofEntry.sol";

struct AssertionState {
    GlobalState globalState;
    MachineStatus machineStatus;
    bytes32 endHistoryRoot;
}

library AssertionStateLib {
    function toExecutionState(AssertionState memory state) internal pure returns (ExecutionState memory) {
        return ExecutionState(state.globalState, state.machineStatus);
    }

    function hash(AssertionState memory state) internal pure returns (bytes32) {
        return keccak256(abi.encode(state));
    }
}


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/rollup/AssertionState.sol#L1:1

```solidity
File: src/rollup/BridgeCreator.sol


// Copyright 2021-2022, Offchain Labs, Inc.
// For license information, see https://github.com/OffchainLabs/nitro-contracts/blob/main/LICENSE
// SPDX-License-Identifier: BUSL-1.1

pragma solidity ^0.8.0;

import "../bridge/Bridge.sol";
import "../bridge/SequencerInbox.sol";
import "../bridge/Inbox.sol";
import "../bridge/Outbox.sol";
import "./RollupEventInbox.sol";
import "../bridge/ERC20Bridge.sol";
import "../bridge/ERC20Inbox.sol";
import "../rollup/ERC20RollupEventInbox.sol";
import "../bridge/ERC20Outbox.sol";

import "../bridge/IBridge.sol";
import "cool/node_modules/@openzeppelin/contracts/access/Ownable.sol";
import "cool/node_modules/@openzeppelin/contracts/proxy/transparent/ProxyAdmin.sol";

contract BridgeCreator is Ownable {
    BridgeTemplates public ethBasedTemplates;
    BridgeTemplates public erc20BasedTemplates;

    event TemplatesUpdated();
    event ERC20TemplatesUpdated();

    struct BridgeTemplates {
        IBridge bridge;
        ISequencerInbox sequencerInbox;
        ISequencerInbox delayBufferableSequencerInbox;
        IInboxBase inbox;
        IRollupEventInbox rollupEventInbox;
        IOutbox outbox;
    }

    struct BridgeContracts {
        IBridge bridge;
        IInboxBase inbox;
        ISequencerInbox sequencerInbox;
        IRollupEventInbox rollupEventInbox;
        IOutbox outbox;
    }

    constructor(
        BridgeTemplates memory _ethBasedTemplates,
        BridgeTemplates memory _erc20BasedTemplates
    ) Ownable() {
        ethBasedTemplates = _ethBasedTemplates;
        erc20BasedTemplates = _erc20BasedTemplates;
    }

    function updateTemplates(BridgeTemplates calldata _newTemplates) external onlyOwner {
        ethBasedTemplates = _newTemplates;
        emit TemplatesUpdated();
    }

    function updateERC20Templates(BridgeTemplates calldata _newTemplates) external onlyOwner {
        erc20BasedTemplates = _newTemplates;
        emit ERC20TemplatesUpdated();
    }

    function _createBridge(
        address adminProxy,
        BridgeTemplates memory templates,
        bool isDelayBufferable
    ) internal returns (BridgeContracts memory) {
        BridgeContracts memory frame;
        frame.bridge = IBridge(
            address(new TransparentUpgradeableProxy(address(templates.bridge), adminProxy, ""))
        );
        frame.sequencerInbox = ISequencerInbox(
            address(
                new TransparentUpgradeableProxy(
                    address(
                        isDelayBufferable
                            ? templates.delayBufferableSequencerInbox
                            : templates.sequencerInbox
                    ),
                    adminProxy,
                    ""
                )
            )
        );
        frame.inbox = IInboxBase(
            address(new TransparentUpgradeableProxy(address(templates.inbox), adminProxy, ""))
        );
        frame.rollupEventInbox = IRollupEventInbox(
            address(
                new TransparentUpgradeableProxy(address(templates.rollupEventInbox), adminProxy, "")
            )
        );
        frame.outbox = IOutbox(
            address(new TransparentUpgradeableProxy(address(templates.outbox), adminProxy, ""))
        );
        return frame;
    }

    function createBridge(
        address adminProxy,
        address rollup,
        address nativeToken,
        ISequencerInbox.MaxTimeVariation calldata maxTimeVariation,
        BufferConfig calldata bufferConfig
    ) external returns (BridgeContracts memory) {
        // create delay bufferable sequencer inbox if threshold is non-zero
        bool isDelayBufferable = bufferConfig.threshold != 0;

        // create ETH-based bridge if address zero is provided for native token, otherwise create ERC20-based bridge
        BridgeContracts memory frame = _createBridge(
            adminProxy,
            nativeToken == address(0) ? ethBasedTemplates : erc20BasedTemplates,
            isDelayBufferable
        );

        // init contracts
        if (nativeToken == address(0)) {
            IEthBridge(address(frame.bridge)).initialize(IOwnable(rollup));
        } else {
            IERC20Bridge(address(frame.bridge)).initialize(IOwnable(rollup), nativeToken);
        }
        frame.sequencerInbox.initialize(IBridge(frame.bridge), maxTimeVariation, bufferConfig);
        frame.inbox.initialize(frame.bridge, frame.sequencerInbox);
        frame.rollupEventInbox.initialize(frame.bridge);
        frame.outbox.initialize(frame.bridge);

        return frame;
    }
}


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/rollup/BridgeCreator.sol#L1:1

```solidity
File: src/rollup/IRollupLogic.sol


// Copyright 2021-2022, Offchain Labs, Inc.
// For license information, see https://github.com/OffchainLabs/nitro-contracts/blob/main/LICENSE
// SPDX-License-Identifier: BUSL-1.1

pragma solidity ^0.8.0;

import "./IRollupCore.sol";
import "../bridge/ISequencerInbox.sol";
import "../bridge/IOutbox.sol";
import "../bridge/IOwnable.sol";

interface IRollupUser is IRollupCore, IOwnable {
    /// @dev the user logic just validated configuration and shouldn't write to state during init
    /// this allows the admin logic to ensure consistency on parameters.
    function initialize(address stakeToken) external view;

    function removeWhitelistAfterFork() external;

    function removeWhitelistAfterValidatorAfk() external;

    function confirmAssertion(
        bytes32 assertionHash,
        bytes32 prevAssertionHash,
        AssertionState calldata confirmState,
        bytes32 winningEdgeId,
        ConfigData calldata prevConfig,
        bytes32 inboxAcc
    ) external;

    function stakeOnNewAssertion(AssertionInputs calldata assertion, bytes32 expectedAssertionHash) external;

    function returnOldDeposit() external;

    function reduceDeposit(uint256 target) external;

    function withdrawStakerFunds() external returns (uint256);

    function newStakeOnNewAssertion(
        uint256 tokenAmount,
        AssertionInputs calldata assertion,
        bytes32 expectedAssertionHash
    ) external;

    function newStakeOnNewAssertion(
        uint256 tokenAmount,
        AssertionInputs calldata assertion,
        bytes32 expectedAssertionHash,
        address withdrawalAddress
    ) external;

    function addToDeposit(address stakerAddress, uint256 tokenAmount) external;
}


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/rollup/IRollupLogic.sol#L1:1

```solidity
File: src/rollup/RollupLib.sol


// Copyright 2021-2022, Offchain Labs, Inc.
// For license information, see https://github.com/OffchainLabs/nitro-contracts/blob/main/LICENSE
// SPDX-License-Identifier: BUSL-1.1

pragma solidity ^0.8.0;

import "../state/GlobalState.sol";
import "../bridge/ISequencerInbox.sol";

import "../bridge/IBridge.sol";
import "../bridge/IOutbox.sol";
import "../bridge/IInboxBase.sol";
import "./Assertion.sol";
import "./IRollupEventInbox.sol";
import "../challengeV2/EdgeChallengeManager.sol";

library RollupLib {
    using GlobalStateLib for GlobalState;
    using AssertionStateLib for AssertionState;

    // The `assertionHash` contains all the information needed to determine an assertion's validity.
    // This helps protect validators against reorgs by letting them bind their assertion to the current chain state.
    function assertionHash(
        bytes32 parentAssertionHash,
        AssertionState memory afterState,
        bytes32 inboxAcc
    ) internal pure returns (bytes32) {
        // we can no longer have `hasSibling` in the assertion hash as it would allow identical assertions
        return assertionHash(
            parentAssertionHash,
            afterState.hash(),
            inboxAcc
        );
    }

    // Takes in a hash of the afterState instead of the afterState itself
    function assertionHash(
        bytes32 parentAssertionHash,
        bytes32 afterStateHash,
        bytes32 inboxAcc
    ) internal pure returns (bytes32) {
        // we can no longer have `hasSibling` in the assertion hash as it would allow identical assertions
        return
            keccak256(
                abi.encodePacked(
                    parentAssertionHash,
                    afterStateHash,
                    inboxAcc
                )
            );
    }

    // All these should be emited in AssertionCreated event
    function configHash(
        bytes32 wasmModuleRoot,
        uint256 requiredStake,
        address challengeManager,
        uint64 confirmPeriodBlocks,
        uint64 nextInboxPosition
    ) internal pure returns (bytes32) {
        return
            keccak256(
                abi.encodePacked(
                    wasmModuleRoot,
                    requiredStake,
                    challengeManager,
                    confirmPeriodBlocks,
                    nextInboxPosition
                )
            );
    }

    function validateConfigHash(
        ConfigData calldata configData,
        bytes32 _configHash
    ) internal pure {
        require(
            _configHash
                == configHash(
                    configData.wasmModuleRoot,
                    configData.requiredStake,
                    configData.challengeManager,
                    configData.confirmPeriodBlocks,
                    configData.nextInboxPosition
                ),
            "CONFIG_HASH_MISMATCH"
        );
    }
}


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/rollup/RollupLib.sol#L1:1

```solidity
File: src/rollup/RollupProxy.sol


// Copyright 2021-2022, Offchain Labs, Inc.
// For license information, see https://github.com/OffchainLabs/nitro-contracts/blob/main/LICENSE
// SPDX-License-Identifier: BUSL-1.1

pragma solidity ^0.8.0;

import "../libraries/AdminFallbackProxy.sol";
import "./IRollupAdmin.sol";
import "./Config.sol";

contract RollupProxy is AdminFallbackProxy {
    function initializeProxy(Config memory config, ContractDependencies memory connectedContracts)
        external
    {
        if (
            _getAdmin() == address(0) &&
            _getImplementation() == address(0) &&
            _getSecondaryImplementation() == address(0)
        ) {
            _initialize(
                address(connectedContracts.rollupAdminLogic),
                abi.encodeCall(
                    IRollupAdmin.initialize,
                    (config,
                    connectedContracts)
                ),
                address(connectedContracts.rollupUserLogic),
                abi.encodeCall(IRollupUser.initialize, (config.stakeToken)),
                config.owner
            );
        } else {
            _fallback();
        }
    }
}


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/rollup/RollupProxy.sol#L1:1

</details>

## NC121 - Function declarations should have NatSpec descriptions:

Function declarations should be preceded by a NatSpec comment.


<details>
<summary>Click to show 22 findings</summary>

```solidity
File: src/assertionStakingPool/AbsBoldStakingPool.sol


24          constructor(address _stakeToken) {


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/assertionStakingPool/AbsBoldStakingPool.sol#L0:0

```solidity
File: src/assertionStakingPool/StakingPoolCreatorUtils.sol


13          function getPool(bytes memory creationCode, bytes memory args) internal view returns (address) {


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/assertionStakingPool/StakingPoolCreatorUtils.sol#L0:0

```solidity
File: src/bridge/DelayBuffer.sol


108         function isUpdatable(BufferData storage self) internal view returns (bool) {
115         function isValidBufferConfig(BufferConfig memory config) internal pure returns (bool) {


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/bridge/DelayBuffer.sol#L0:0

```solidity
File: src/bridge/ISequencerInbox.sol


49          function totalDelayedMessagesRead() external view returns (uint256);
51          function bridge() external view returns (IBridge);
93          function rollup() external view returns (IOwnable);
95          function isBatchPoster(address) external view returns (bool);
97          function isSequencer(address) external view returns (bool);
102         function maxDataSize() external view returns (uint256);
124         function dasKeySetInfo(bytes32) external view returns (bool, uint64);
148         function inboxAccs(uint256 index) external view returns (bytes32);
150         function batchCount() external view returns (uint256);
152         function isValidKeysetHash(bytes32 ksHash) external view returns (bool);
188         function addSequencerL2Batch(
197         function addSequencerL2BatchFromBlobs(
287         function initialize(


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/bridge/ISequencerInbox.sol#L0:0

```solidity
File: src/bridge/SequencerInbox.sol


140         constructor(
161         function postUpgradeInit(BufferConfig memory bufferConfig_)
177         function initialize(
216         function getTimeBounds() internal view virtual returns (IBridge.TimeBounds memory) {
244         function maxTimeVariation()
269         function maxTimeVariationInternal()
455         function addSequencerL2BatchFromBlobsImpl(
512         function addSequencerL2BatchFromCalldataImpl(
605         function delayProofImpl(uint256 afterDelayedMessagesRead, DelayProof memory delayProof)
628         function isDelayProofRequired(uint256 afterDelayedMessagesRead) internal view returns (bool) {
637         function packHeader(uint256 afterDelayedMessagesRead)
791         function addSequencerL2BatchImpl(
824         function inboxAccs(uint256 index) external view returns (bytes32) {
828         function batchCount() external view returns (uint256) {
947         function setBufferConfig(BufferConfig memory bufferConfig_) external onlyRollupOwner {
952         function isValidKeysetHash(bytes32 ksHash) external view returns (bool) {


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/bridge/SequencerInbox.sol#L0:0

```solidity
File: src/challengeV2/EdgeChallengeManager.sol


47          function challengePeriodBlocks() external view returns (uint64);
300         constructor() {


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/challengeV2/EdgeChallengeManager.sol#L0:0

```solidity
File: src/challengeV2/IAssertionChain.sol


14          function bridge() external view returns (IBridge);
15          function validateAssertionHash(
21          function validateConfig(bytes32 assertionHash, ConfigData calldata configData) external view;
22          function getFirstChildCreationBlock(bytes32 assertionHash) external view returns (uint64);
23          function getSecondChildCreationBlock(bytes32 assertionHash) external view returns (uint64);
24          function isFirstChild(bytes32 assertionHash) external view returns (bool);
25          function isPending(bytes32 assertionHash) external view returns (bool);
26          function isValidator(address) external view returns (bool);
27          function validatorWhitelistDisabled() external view returns (bool);


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/challengeV2/IAssertionChain.sol#L0:0

```solidity
File: src/challengeV2/libraries/ChallengeEdgeLib.sol


184         function mutualIdMem(ChallengeEdge memory ce) internal pure returns (bytes32) {


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/challengeV2/libraries/ChallengeEdgeLib.sol#L0:0

```solidity
File: src/challengeV2/libraries/EdgeChallengeManagerLib.sol


488         function timeUnrivaledTotal(EdgeStore storage store, bytes32 edgeId) internal view returns (uint256) {
516         function updateTimerCacheByChildren(EdgeStore storage store, bytes32 edgeId) internal returns (bool, uint256) {
520         function updateTimerCacheByClaim(


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/challengeV2/libraries/EdgeChallengeManagerLib.sol#L0:0

```solidity
File: src/rollup/Assertion.sol


93          function requireExists(AssertionNode memory self) internal pure {


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/rollup/Assertion.sol#L0:0

```solidity
File: src/rollup/AssertionState.sol


18          function toExecutionState(AssertionState memory state) internal pure returns (ExecutionState memory) {
22          function hash(AssertionState memory state) internal pure returns (bytes32) {


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/rollup/AssertionState.sol#L0:0

```solidity
File: src/rollup/BOLDUpgradeAction.sol


67          function wasmModuleRoot() external view returns (bytes32);
68          function latestConfirmed() external view returns (uint64);
69          function getNode(uint64 nodeNum) external view returns (Node memory);
70          function getStakerAddress(uint64 stakerNum) external view returns (address);
71          function stakerCount() external view returns (uint64);
72          function getStaker(address staker) external view returns (OldStaker memory);
73          function isValidator(address validator) external view returns (bool);
74          function validatorWalletCreator() external view returns (address);
78          function forceRefundStaker(address[] memory stacker) external;
79          function pause() external;
80          function resume() external;
84          function postUpgradeInit(BufferConfig memory bufferConfig_) external;
101         function stateHash(ExecutionState calldata executionState, uint256 inboxMaxCount) public pure returns (bytes32) {
106         function set(bytes32 h, ExecutionState calldata executionState, uint256 inboxMaxCount) public {
112         function get(bytes32 h) public view returns (ExecutionState memory executionState, uint256 inboxMaxCount) {
126         constructor(IOldRollup _rollup) {
130         function wasmModuleRoot() external view returns (bytes32) {
134         function latestConfirmed() external view returns (uint64) {
138         function getNode(uint64 nodeNum) external view returns (Node memory) {
142         function getStakerAddress(uint64 stakerNum) external view returns (address) {
146         function stakerCount() external view returns (uint64) {
150         function getStaker(address staker) external view returns (OldStaker memory) {
154         function isValidator(address validator) external view returns (bool) {
158         function validatorWalletCreator() external view returns (address) {
169         constructor(uint256[] memory __array) {
173         function array() public view returns (uint256[] memory) {
287         constructor(
411         function upgradeSurroundingContracts(address newRollupAddress) private {
433         function upgradeSequencerInbox() private {
464         function perform(address[] memory validators) external {


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/rollup/BOLDUpgradeAction.sol#L0:0

```solidity
File: src/rollup/BridgeCreator.sol


45          constructor(
53          function updateTemplates(BridgeTemplates calldata _newTemplates) external onlyOwner {
58          function updateERC20Templates(BridgeTemplates calldata _newTemplates) external onlyOwner {
99          function createBridge(


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/rollup/BridgeCreator.sol#L0:0

```solidity
File: src/rollup/IRollupAdmin.sol


16          function initialize(Config calldata config, ContractDependencies calldata connectedContracts) external;
80          function forceRefundStaker(address[] memory stacker) external;
82          function forceCreateAssertion(
88          function forceConfirmAssertion(
95          function setLoserStakeEscrow(address newLoserStakerEscrow) external;


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/rollup/IRollupAdmin.sol#L0:0

```solidity
File: src/rollup/IRollupCore.sol


48          function confirmPeriodBlocks() external view returns (uint64);
50          function chainId() external view returns (uint256);
52          function baseStake() external view returns (uint256);
54          function wasmModuleRoot() external view returns (bytes32);
56          function bridge() external view returns (IBridge);
58          function sequencerInbox() external view returns (ISequencerInbox);
60          function outbox() external view returns (IOutbox);
62          function rollupEventInbox() external view returns (IRollupEventInbox);
64          function challengeManager() external view returns (IEdgeChallengeManager);
66          function loserStakeEscrow() external view returns (address);
68          function stakeToken() external view returns (address);
70          function minimumAssertionPeriod() external view returns (uint256);
72          function genesisAssertionHash() external pure returns (bytes32);


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/rollup/IRollupCore.sol#L0:0

```solidity
File: src/rollup/IRollupLogic.sol


17          function removeWhitelistAfterFork() external;
19          function removeWhitelistAfterValidatorAfk() external;
21          function confirmAssertion(
30          function stakeOnNewAssertion(AssertionInputs calldata assertion, bytes32 expectedAssertionHash) external;
32          function returnOldDeposit() external;
34          function reduceDeposit(uint256 target) external;
36          function withdrawStakerFunds() external returns (uint256);
38          function newStakeOnNewAssertion(
44          function newStakeOnNewAssertion(
51          function addToDeposit(address stakerAddress, uint256 tokenAmount) external;


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/rollup/IRollupLogic.sol#L0:0

```solidity
File: src/rollup/RollupAdminLogic.sol


18          function initialize(Config calldata config, ContractDependencies calldata connectedContracts)
228         function forceRefundStaker(address[] calldata staker) external override whenPaused {
237         function forceCreateAssertion(
258         function forceConfirmAssertion(
269         function setLoserStakeEscrow(address newLoserStakerEscrow) external override {


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/rollup/RollupAdminLogic.sol#L0:0

```solidity
File: src/rollup/RollupCore.sol


116         function sequencerInbox() public view virtual returns (ISequencerInbox) {
365         function createNewAssertion(
520         function genesisAssertionHash() external pure returns (bytes32) {
532         function getFirstChildCreationBlock(bytes32 assertionHash) external view returns (uint64) {
536         function getSecondChildCreationBlock(bytes32 assertionHash) external view returns (uint64) {
540         function validateAssertionHash(
549         function validateConfig(bytes32 assertionHash, ConfigData calldata configData) external view {
553         function isFirstChild(bytes32 assertionHash) external view returns (bool) {
557         function isPending(bytes32 assertionHash) external view returns (bool) {


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/rollup/RollupCore.sol#L0:0

```solidity
File: src/rollup/RollupCreator.sol


58          constructor() Ownable() {}
61          receive() external payable {}
63          function setTemplates(
85          function createChallengeManager(address rollupAddr, address proxyAdminAddr, Config memory config)


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/rollup/RollupCreator.sol#L0:0

```solidity
File: src/rollup/RollupLib.sol


23          function assertionHash(
37          function assertionHash(
54          function configHash(
73          function validateConfigHash(


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/rollup/RollupLib.sol#L0:0

```solidity
File: src/rollup/RollupProxy.sol


12          function initializeProxy(Config memory config, ContractDependencies memory connectedContracts)


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/rollup/RollupProxy.sol#L0:0

```solidity
File: src/rollup/RollupUserLogic.sol


62          function removeWhitelistAfterFork() external {
308         function owner() external view returns (address) {
366         function receiveTokens(uint256 tokenAmount) private {


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/rollup/RollupUserLogic.sol#L0:0

</details>

## NC122 - Contract declarations should have `@notice` tags:

`@notice` is used to explain to end users what the contract does, and the compiler interprets `///` or `/**` comments as this tag if one wasn't explicitly provided.


<details>
<summary>Click to show 24 findings</summary>

```solidity
File: src/assertionStakingPool/StakingPoolCreatorUtils.sol


11      library StakingPoolCreatorUtils {


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/assertionStakingPool/StakingPoolCreatorUtils.sol#L0:0

```solidity
File: src/assertionStakingPool/interfaces/IAbsBoldStakingPool.sol


7       interface IAbsBoldStakingPool {


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/assertionStakingPool/interfaces/IAbsBoldStakingPool.sol#L0:0

```solidity
File: src/assertionStakingPool/interfaces/IAssertionStakingPool.sol


10      interface IAssertionStakingPool is IAbsBoldStakingPool {


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/assertionStakingPool/interfaces/IAssertionStakingPool.sol#L0:0

```solidity
File: src/assertionStakingPool/interfaces/IAssertionStakingPoolCreator.sol


10      interface IAssertionStakingPoolCreator {


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/assertionStakingPool/interfaces/IAssertionStakingPoolCreator.sol#L0:0

```solidity
File: src/assertionStakingPool/interfaces/IEdgeStakingPool.sol


10      interface IEdgeStakingPool is IAbsBoldStakingPool {


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/assertionStakingPool/interfaces/IEdgeStakingPool.sol#L0:0

```solidity
File: src/assertionStakingPool/interfaces/IEdgeStakingPoolCreator.sol


9       interface IEdgeStakingPoolCreator {


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/assertionStakingPool/interfaces/IEdgeStakingPoolCreator.sol#L0:0

```solidity
File: src/bridge/DelayBuffer.sol


16      library DelayBuffer {


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/bridge/DelayBuffer.sol#L0:0

```solidity
File: src/bridge/ISequencerInbox.sol


15      interface ISequencerInbox is IDelayedMessageProvider {


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/bridge/ISequencerInbox.sol#L0:0

```solidity
File: src/bridge/SequencerInbox.sol


64      contract SequencerInbox is DelegateCallAware, GasRefundEnabled, ISequencerInbox {


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/bridge/SequencerInbox.sol#L0:0

```solidity
File: src/challengeV2/EdgeChallengeManager.sol


18      interface IEdgeChallengeManager {


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/challengeV2/EdgeChallengeManager.sol#L0:0

```solidity
File: src/challengeV2/libraries/ChallengeEdgeLib.sol


67      library ChallengeEdgeLib {


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/challengeV2/libraries/ChallengeEdgeLib.sol#L0:0

```solidity
File: src/rollup/Assertion.sol


66      library AssertionNodeLib {


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/rollup/Assertion.sol#L0:0

```solidity
File: src/rollup/AssertionState.sol


17      library AssertionStateLib {


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/rollup/AssertionState.sol#L0:0

```solidity
File: src/rollup/BOLDUpgradeAction.sol


49      interface IOldRollup {
77      interface IOldRollupAdmin {
83      interface ISeqInboxPostUpgradeInit {


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/rollup/BOLDUpgradeAction.sol#L0:0

```solidity
File: src/rollup/BridgeCreator.sol


21      contract BridgeCreator is Ownable {


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/rollup/BridgeCreator.sol#L0:0

```solidity
File: src/rollup/IRollupAdmin.sol


13      interface IRollupAdmin {


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/rollup/IRollupAdmin.sol#L0:0

```solidity
File: src/rollup/IRollupCore.sol


15      interface IRollupCore is IAssertionChain {


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/rollup/IRollupCore.sol#L0:0

```solidity
File: src/rollup/IRollupLogic.sol


12      interface IRollupUser is IRollupCore, IOwnable {


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/rollup/IRollupLogic.sol#L0:0

```solidity
File: src/rollup/RollupAdminLogic.sol


15      contract RollupAdminLogic is RollupCore, IRollupAdmin, DoubleLogicUUPSUpgradeable {


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/rollup/RollupAdminLogic.sol#L0:0

```solidity
File: src/rollup/RollupCore.sol


22      abstract contract RollupCore is IRollupCore, PausableUpgradeable {


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/rollup/RollupCore.sol#L0:0

```solidity
File: src/rollup/RollupCreator.sol


17      contract RollupCreator is Ownable {


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/rollup/RollupCreator.sol#L0:0

```solidity
File: src/rollup/RollupLib.sol


17      library RollupLib {


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/rollup/RollupLib.sol#L0:0

```solidity
File: src/rollup/RollupProxy.sol


11      contract RollupProxy is AdminFallbackProxy {


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/rollup/RollupProxy.sol#L0:0

```solidity
File: src/rollup/RollupUserLogic.sol


15      contract RollupUserLogic is RollupCore, UUPSNotUpgradeable, IRollupUser {


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/rollup/RollupUserLogic.sol#L0:0

</details>

## NC123 - Error declarations should have NatSpec descriptions:

  


```solidity
File: src/assertionStakingPool/StakingPoolCreatorUtils.sol


12          error PoolDoesntExist();


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/assertionStakingPool/StakingPoolCreatorUtils.sol#L0:0

## NC124 - Contract does not follow the Solidity style guide's suggested layout ordering:

The [style guide](https://docs.soliditylang.org/en/v0.8.16/style-guide.html#order-of-layout) says that, within a contract, the ordering should be 1) Type declarations, 2) State variables, 3) Events, 4) Modifiers, and 5) Functions, but the contract(s) below do not follow this ordering.


<details>
<summary>Click to show 4 findings</summary>

```solidity
File: src/bridge/ISequencerInbox.sol


108         struct DasKeySetInfo {


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/bridge/ISequencerInbox.sol#L0:0

```solidity
File: src/rollup/BOLDUpgradeAction.sol


237         struct Settings {


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/rollup/BOLDUpgradeAction.sol#L0:0

```solidity
File: src/rollup/BridgeCreator.sol


28          struct BridgeTemplates {


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/rollup/BridgeCreator.sol#L0:0

```solidity
File: src/rollup/RollupCreator.sol


35          struct RollupDeploymentParams {


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/rollup/RollupCreator.sol#L0:0

</details>

## NC125 - Non-external/public variable names should begin with an underscore:

According to the Solidity Style Guide, non-external/public variable names should begin with an underscore


<details>
<summary>Click to show 4 findings</summary>

```solidity
File: src/bridge/SequencerInbox.sol


119         uint64 internal delayBlocks;
120         uint64 internal futureBlocks;
121         uint64 internal delaySeconds;
122         uint64 internal futureSeconds;
129         uint256 internal immutable deployTimeChainId = block.chainid;
131         bool internal immutable hostChainIsArbitrum = ArbitrumChecker.runningOnArbitrum();


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/bridge/SequencerInbox.sol#L0:0

```solidity
File: src/challengeV2/EdgeChallengeManager.sol


266         EdgeStore internal store;


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/challengeV2/EdgeChallengeManager.sol#L0:0

```solidity
File: src/rollup/BOLDUpgradeAction.sol


99          mapping(bytes32 => bytes) internal preImages;


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/rollup/BOLDUpgradeAction.sol#L0:0

```solidity
File: src/rollup/RollupUserLogic.sol


31          uint256 internal immutable deployTimeChainId = block.chainid;


```

https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/rollup/RollupUserLogic.sol#L0:0

</details>

