| Title                                                                                                     |
|-----------------------------------------------------------------------------------------------------------|
| [QA-01] invalid validation in some `RollupCore` parameters _(Multiple Instances)                          |
| [QA-02] `abi.encodePacked()` should not be used with dynamic types when passing the result to a hash function such as `keccak256()` |
| [QA-03] Absence of timelock to critical functions                                                          |
| [QA-04] Logic Issue invalid validation                                                                     |
| [QA-05] `SequencerInbox.getTimeBounds` Function check breaks the intended functionality                      |
| [QA-06] checks if the assertionChain, oneStepProofEntry, and stakeToken parameters are not equal to the zero address in the initialize function |
| [QA-07] Invalid validation in some function `EdgeChallengeManager.createLayerZeroEdge` struct CreateEdgeArgs |
| [QA-08] Modifiers invoked only once can be shoe-horned into the function                                    |
| [QA-09] `RollupUserLogic.withdrawStakerFunds` function vulnerable to reentrancy attacks                     |
| [QA-10] Potential for edge data manipulation                                                                |
| [QA-11] Potential for denial-of-service (DoS) attacks `multiUpdateTimeCacheByChildren`                      |
| [QA-12] Potential for front-running attacks `refundStake`                                                    |
| [QA-13] Typos _(Multiple Instances)                                                                         |


## [QA-01] invalid validation in some `RollupCore` parameters _(Multiple Instances)

Impact

`RollupCore` has some internal functions that require input validation before executing parameterised logic in some functions. This input validation is very important to ensure that the operations performed by the contract run as expected and to prevent attacks or user errors. Here are some of the functions that require input validation:

Here are the instances:

https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/rollup/RollupCore.sol#L274

https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/rollup/RollupCore.sol#L286

https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/rollup/RollupCore.sol#L300

https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/rollup/RollupCore.sol#L317

https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/rollup/RollupCore.sol#L331

https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/rollup/RollupCore.sol#L343

https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/rollup/RollupCore.sol#L365

Proof of Concept

`getAssertionStorage`:
Ensure `_assertions[assertionHash]` exists before accessing it.

`confirmAssertionInternal`:
Ensure `assertionHash` is non-zero.
Add validation to ensure `parentAssertionHash` is the parent of `assertionHash`.

`createNewStake`:
Ensure `depositAmount` is greater than zero.
Validate `withdrawalAddress` is not empty or zero address.

`increaseStakeBy`:
Validate `amountAdded` is more than zero.
Ensure `stakerAddress` is a valid staker before accessing and modifying its data.

`reduceStakeTo`:
Ensure the target is greater than or equal to zero and not more than the current stake amount.

`withdrawStaker`:
Ensure `stakerAddress` is a valid and active staker (`isStaked`).

`withdrawFunds`:
Ensure the `account` actually has withdrawable funds.
Validate that the withdrawn amount is not more than the withdrawable balance.

`increaseWithdrawableFunds`:
Ensure the amount is greater than zero before increasing the withdrawable funds.

`createNewAssertion`:
Add validation to ensure `prevAssertionHash` is valid before use.
Validate that `assertion.beforeStateData.configData` matches `prevAssertionHash`.


## [QA-02] `abi.encodePacked()` should not be used with dynamic types when passing the result to a hash function such as `keccak256()`

Use `abi.encode()` instead which will pad items to 32 bytes, which will [prevent hash collisions](https://docs.soliditylang.org/en/v0.8.13/abi-spec.html#non-standard-packed-mode) (e.g. `abi.encodePacked(0x123,0x456)` => `0x123456` => `abi.encodePacked(0x1,0x23456)`, but `abi.encode(0x123,0x456)` => `0x0...1230...456`). 

Unless there is a compelling reason, `abi.encode` should be preferred. If there is only one argument to `abi.encodePacked()` it can often be cast to `bytes()` or `bytes32()` [instead](https://ethereum.stackexchange.com/questions/30912/how-to-compare-strings-in-solidity#answer-82739).
If all arguments are strings and or bytes, `bytes.concat()` should be used instead.


Here are the instances: 

https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/bridge/SequencerInbox.sol#L643-L644

https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/bridge/SequencerInbox.sol#L744

https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/bridge/SequencerInbox.sol#L774

https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/challengeV2/libraries/MerkleTreeLib.sol#L125-L137

https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/challengeV2/libraries/MerkleTreeLib.sol#L213

https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/challengeV2/libraries/MerkleTreeLib.sol#L241

https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/challengeV2/libraries/MerkleTreeLib.sol#L359-L365

https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/libraries/MerkleLib.sol#L16-L17

https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/rollup/BOLDUpgradeAction.sol#L103

https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/rollup/RollupLib.sol#L43

https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/rollup/RollupLib.sol#L63



## [QA-03] Absence of timelock to critical functions

It is a good practice to give time for users to react and adjust to critical changes. A timelock provides more guarantees and reduces the level of trust required, thus decreasing risk for users. It also indicates that the project is legitimate (less risk of a malicious Manager making a frontrunning/sandwich attack on the fees). Consider adding a timelock to the _setMaxTimeVariation function and RollupAdminLogic contract 

https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/bridge/SequencerInbox.sol#L867-L883

https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/rollup/RollupAdminLogic.sol#L107-L329


## [QA-04] Logic Issue invalid validation 

The minor logic issue here lies in the redundancy of the assignment when deleting a staker. The function `deleteStaker` removes a staker from the `_stakerList` array and `_stakerMap`. It first retrieves the staker's index and checks if the staker is already staked. Then, it proceeds to delete the staker from the list and map.

However, if the staker to be deleted is already the last one in the array, the function still performs the replacement of the last staker with itself before calling `pop()` to remove it. While functionally correct, this redundant step of self-replacement before removal is unnecessary and could potentially confuse readers of the code.

https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/rollup/RollupCore.sol#L355


Suggested Improvement:

To make the code cleaner and avoid unnecessary operations, you can add a check to see if the token to remove is already the last one in the array:

``` 
function deleteStaker(address stakerAddress) private {
    Staker storage staker = _stakerMap[stakerAddress];
    require(staker.isStaked, "NOT_STAKED");
    uint64 stakerIndex = staker.index;
    
    // Check if the staker to remove is already the last one in the array
    if (stakerIndex != _stakerList.length - 1) {
        // If not, swap it with the last staker in the array
        _stakerList[stakerIndex] = _stakerList[_stakerList.length - 1];
        _stakerMap[_stakerList[stakerIndex]].index = stakerIndex;
    }
    
    // Remove the last element from the array
    _stakerList.pop();
    
    // Delete the staker from the map
    delete _stakerMap[stakerAddress];
}

```

## [QA-05] `SequencerInbox.getTimeBounds` Function check breaks the intended functionality
The problem occurs because the `block.timestamp` check used only has to exceed delaySeconds_. However, you should ensure that the cooldown time has expired before a claim is allowed.

The solution to this problem is to check whether the cooldown time has expired before the claim is allowed

https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/bridge/SequencerInbox.sol#L216-L233

Recommendation:
```solidity
    // Calculate the cooldown end time
    uint64 cooldownEndTime = uint64(block.timestamp) - delaySeconds_;

    // Ensure the cooldown period has fully elapsed
    if (cooldownEndTime > delaySeconds_) {
        bounds.minTimestamp = cooldownEndTime;
    }
```


## [QA-06] checks if the assertionChain, oneStepProofEntry, and stakeToken parameters are not equal to the zero address in the initialize function

https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/challengeV2/EdgeChallengeManager.sol#L305-L364

## [QA-07] Invalid validation in some function `EdgeChallengeManager.createLayerZeroEdge` struct CreateEdgeArgs 

Instances:

https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/challengeV2/libraries/EdgeChallengeManagerLib.sol#L25-L62

https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/challengeV2/EdgeChallengeManager.sol#L371

Recommendation:

```solidity
    // Additional input validation checks
    require(args.level >= 0 && args.level <= MAX_LEVEL, "Invalid level");
    require(args.endHeight >= 0 && args.endHeight <= MAX_HEIGHT, "Invalid end height");
    require(args.claimId != bytes32(0), "Invalid claim ID");
    require(args.endHistoryRoot != bytes32(0), "Invalid end history root");
    require(args.prefixProof.length > 0, "Invalid prefix proof");
    require(args.proof.length > 0, "Invalid proof");
```

## [QA-08] Modifiers invoked only once can be shoe-horned into the function

Instances:

https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/bridge/SequencerInbox.sol#L102-L113

https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/rollup/RollupUserLogic.sol#L20-L23


## [QA-09] `RollupUserLogic.withdrawStakerFunds` function vulnerable to reentrancy attacks

An attacker deposited some tokens in the contract using the newStakeOnNewAssertion() function.
The attacker then exploits a vulnerability in the withdrawStakerFunds() function by repeatedly calling it from within a fallback function or another function called during the withdrawal process.
During the withdrawal process, the attacker triggers a fallback function or another function that calls withdrawStakerFunds() again, allowing the attacker to continue withdrawing funds indefinitely until the contract balance is exhausted.

https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/rollup/RollupUserLogic.sol#L358-L364

https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/rollup/RollupUserLogic.sol#L331-L342

Recommendation:

The use of withdrawFunds() should be placed after all validations and effects have been applied, so that no external interactions occur after the withdrawal process. Additionally, using nonReentrant modifiers or similar mechanisms can also help protect against reentrancy attacks.

## [QA-10] Potential for edge data manipulation

The updateTimerCacheByChildren and updateTimerCacheByClaim functions can be called by anyone, which could allow an attacker to manipulate the timer cache data for edges.

https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/challengeV2/EdgeChallengeManager.sol#L500-L510

## [QA-11] Potential for denial-of-service (DoS) attacks `multiUpdateTimeCacheByChildren`

function iterates over an array of edge IDs, which could lead to a DoS attack if an attacker provides a large array. Consider implementing a mechanism to limit the size of the input array.

https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/challengeV2/EdgeChallengeManager.sol#L492-L497

Limit the number of edges that can be updated in a single transaction: To prevent DoS attacks in the multiUpdateTimeCacheByChildren function, limit the number of edges that can be updated in a single transaction. This can be done by introducing a maximum limit for the number of edges that can be passed as an argument to the function.

## [QA-12] Potential for front-running attacks `refundStake`

function can be front-run by an attacker, which could lead to unintended behavior or loss of funds. Consider implementing a mechanism to prevent front-running attacks.

https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/challengeV2/EdgeChallengeManager.sol#L573-L586

To prevent front-running attacks in the refundStake function, introduce a random delay before processing the refund request. This can be done using a random number generator or by using a timestamp-based delay mechanism.

## [QA-13] Typos _(Multiple Instances)

Typo: Missing comma after "bisected"
https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/challengeV2/libraries/ChallengeEdgeLib.sol#L33

Typo: Hyphen instead of space between "mini" and "stake"
https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/challengeV2/libraries/ChallengeEdgeLib.sol#L44

Typo: Incomplete comment
https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/challengeV2/libraries/ChallengeEdgeLib.sol#L69

// TODO: but doesn't specify what needs to be done. It's advisable to provide more details on what needs to be completed or addressed in that comment.

https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/challengeV2/libraries/ChallengeEdgeLib.sol#L63

// Maybe it could be clarified a little, for example:
```
// Internal function to work around stack limit during contract deployment
```
https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/rollup/RollupCreator.sol#L84

// be more specific

```
// Deploy factories based on the provided parameters
```
https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/rollup/RollupCreator.sol#L299-L300

https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/rollup/RollupCreator.sol#L314