
# Low Issues

## L1. Missing validation for `parentAssertionHash` existence
There is no check to ensure that parentAssertionHash exists.

[Link to code](https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/rollup/RollupUserLogic.sol#L258)

```solidity
File: src/rollup/RollupUserLogic.sol#L258
    function fastConfirmAssertion(
        bytes32 assertionHash,
        bytes32 parentAssertionHash,
        AssertionState calldata confirmState,
        bytes32 inboxAcc
    ) public whenNotPaused {
        require(msg.sender == anyTrustFastConfirmer, "NOT_FAST_CONFIRMER");//@audit getAssertionStorage(parentAssertionHash).requireExists();
        // this skip deadline, prev, challenge validations 
        confirmAssertionInternal(assertionHash, parentAssertionHash, confirmState, inboxAcc);
    }
```

### Recommended Mitigation Steps
It's recommended to add a check if parentAssertionHash is existed.

```diff
    function fastConfirmAssertion(
        bytes32 assertionHash,
        bytes32 parentAssertionHash,
        AssertionState calldata confirmState,
        bytes32 inboxAcc
    ) public whenNotPaused {
        require(msg.sender == anyTrustFastConfirmer, "NOT_FAST_CONFIRMER");
+        getAssertionStorage(parentAssertionHash).requireExists();
        // this skip deadline, prev, challenge validations 
        confirmAssertionInternal(assertionHash, parentAssertionHash, confirmState, inboxAcc);
    }
```

## L2. The `setSequencerInbox` function is missing a check that sequencerInbox.totalDelayedMessagesRead() is 0.

[Link to code](https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/rollup/RollupAdminLogic.sol#L290)

```solidity
File: src/rollup/RollupAdminLogic.sol#L290
    function setSequencerInbox(address _sequencerInbox) external override {
        bridge.setSequencerInbox(_sequencerInbox); // @audit missing checking if sequencerInbox.totalDelayedMessagesRead() is zero
        emit OwnerFunctionCalled(27);
    }
```

### Recommended Mitigation Steps
It's recommended to check the totalDelayedMessagesRead when setting the sequencerInbox.

```diff
    function setSequencerInbox(address _sequencerInbox) external override {
        bridge.setSequencerInbox(_sequencerInbox);
+        if (ISequencerInbox(_sequencerInbox).totalDelayedMessagesRead() == 0) {
+            ISequencerInbox(_sequencerInbox).addSequencerL2Batch(0, "", 1, IGasRefunder(address(0)), 0, 1);
+        }
        emit OwnerFunctionCalled(27);
    }   
```


## L3. When `amountStaked` is zero, the staker should be deleted from stakers mapping

[Link to code](https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/rollup/RollupCore.sol#L306)

```solidity
File: src/rollup/RollupCore.sol#L306
    function reduceStakeTo(address stakerAddress, uint256 target) internal returns (uint256) {
        Staker storage staker = _stakerMap[stakerAddress];
        address withdrawalAddress = staker.withdrawalAddress;
        uint256 current = staker.amountStaked;
        require(target <= current, "TOO_LITTLE_STAKE");
        uint256 amountWithdrawn = current - target;
        staker.amountStaked = target;// @audit target can be 0?
        increaseWithdrawableFunds(withdrawalAddress, amountWithdrawn);
        emit UserStakeUpdated(stakerAddress, withdrawalAddress, current, target);
        return amountWithdrawn;
    }
```

### Recommended Mitigation Steps
It's recommended to call `deleteStaker` if `amountStaked` is zero.

```diff
    function reduceStakeTo(address stakerAddress, uint256 target) internal returns (uint256) {
        Staker storage staker = _stakerMap[stakerAddress];
        address withdrawalAddress = staker.withdrawalAddress;
        uint256 current = staker.amountStaked;
        require(target <= current, "TOO_LITTLE_STAKE");
        uint256 amountWithdrawn = current - target;
        staker.amountStaked = target;
        increaseWithdrawableFunds(withdrawalAddress, amountWithdrawn);
+        if (target == 0) deleteStaker(stakerAddress);
        emit UserStakeUpdated(stakerAddress, withdrawalAddress, current, target);
        return amountWithdrawn;
    }
```


## L4. The `onlyValidator` modifier is unnecessary in the `returnOldDeposit` function
If the `validatorWhitelistDisabled` flag is toggled from true to false, a staker cannot withdraw their deposit while the flag remains false.

[Link to code](https://github.com/code-423n4/2024-05-arbitrum-foundation/tree/main/src/rollup/RollupUserLogic.sol#L222)

```solidity
File: src/rollup/RollupUserLogic.sol#L222
    function returnOldDeposit() external override onlyValidator whenNotPaused {
        requireInactiveStaker(msg.sender); // @audit onlyValidator can do this? validatorWhitelistDisabled = true and again it's false, when user is not validator, he can't withdraw
        withdrawStaker(msg.sender);
    }
```

### Recommended Mitigation Steps
It's recommended to remove onlyValidator modifier from the returnOldDeposit function.

```diff
-    function returnOldDeposit() external override onlyValidator whenNotPaused {
+    function returnOldDeposit() external override whenNotPaused {
        requireInactiveStaker(msg.sender);
        withdrawStaker(msg.sender);
    }
```


# Non Critical Issues

## NC1. `_assertionCreatedAtArbSysBlock` is not initialized in the initializeCore function

When hostChain is Arbitrum, this initialization function doesn't initialize the _assertionCreatedAtArbSysBlock variable.
This means `getAssertionCreationBlockForLogLookup` will revert with the initialHash.
Although this does not cause any reverts in `RollUpAdminLogic` contract, it is recommended to initialize `_assertionCreatedAtArbSysBlock` within `RollupCore` contract.
[Link to code](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/rollup/RollupCore.sol#L225)

```solidity
    function initializeCore(AssertionNode memory initialAssertion, bytes32 assertionHash) internal {
        __Pausable_init();
        initialAssertion.status = AssertionStatus.Confirmed;
        _assertions[assertionHash] = initialAssertion;
        _latestConfirmed = assertionHash; // @audit why not set if (_hostChainIsArbitrum) _assertionCreatedAtArbSysBlock[assertionHash] = 1 or initialAssertion.createdAtBlock;
    }
```

### Recommended Mitigation Steps
It's recommended to add the initialization logic for setting the _assertionCreatedAtArbSysBlock variable.

```diff
    function initializeCore(AssertionNode memory initialAssertion, bytes32 assertionHash) internal {
        __Pausable_init();
        initialAssertion.status = AssertionStatus.Confirmed;
        _assertions[assertionHash] = initialAssertion;
        _latestConfirmed = assertionHash;
+        if (_hostChainIsArbitrum) {
+            _assertionCreatedAtArbSysBlock[assertionHash] = ArbSys(address(100)).arbBlockNumber();
+        }
    }   
```


## NC2. Before deleting a staker, the amountStake should be verified
Ensure the amountStake is 0 before calling deleteStaker. 
Additionally, it is recommended to update the `withdrawStaker` function to set the amountStake to 0.

[Link to code](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/rollup/RollupCore.sol#L357)

```solidity
    function deleteStaker(address stakerAddress) private {
        Staker storage staker = _stakerMap[stakerAddress];
        require(staker.isStaked, "NOT_STAKED");//@audit staker.amountStaked == 0?
        uint64 stakerIndex = staker.index;
        _stakerList[stakerIndex] = _stakerList[_stakerList.length - 1];
        _stakerMap[_stakerList[stakerIndex]].index = stakerIndex;
        _stakerList.pop();
        delete _stakerMap[stakerAddress];
    }
```

### Recommended Mitigation Steps

```diff
File:   src/rollup/RollupCore.sol#L317
    function withdrawStaker(address stakerAddress) internal {
        Staker storage staker = _stakerMap[stakerAddress];
        address withdrawalAddress = staker.withdrawalAddress;
        uint256 initialStaked = staker.amountStaked;
        increaseWithdrawableFunds(withdrawalAddress, initialStaked);
+        staker.amountStaked = 0;
        deleteStaker(stakerAddress);
        emit UserStakeUpdated(stakerAddress, withdrawalAddress, initialStaked, 0);
    }
File:   src/rollup/RollupCore.sol#L355
    function deleteStaker(address stakerAddress) private {
        Staker storage staker = _stakerMap[stakerAddress];
        require(staker.isStaked, "NOT_STAKED");
+        require(staker.amountStaked == 0, "NOT_ZERO");
        uint64 stakerIndex = staker.index;
        _stakerList[stakerIndex] = _stakerList[_stakerList.length - 1];
        _stakerMap[_stakerList[stakerIndex]].index = stakerIndex;
        _stakerList.pop();
        delete _stakerMap[stakerAddress];
    }   
```

## NC3. Duplicated modifier (onlyValidator, whenNotPaused) being used in the `addToDeposit` function
Since it is already applied in the `_addToDeposit` function, it doesn't need to be used in addToDeposit.

[Link to code](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/rollup/RollupUserLogic.sol#L349)

```solidity
File:   src/rollup/RollupUserLogic.sol#L349
    function addToDeposit(address stakerAddress, uint256 tokenAmount) external onlyValidator whenNotPaused { //@audit _addToDeposit() duplicated checking modifier
        _addToDeposit(stakerAddress, tokenAmount);
        /// @dev This is an external call, safe because it's at the end of the function
        receiveTokens(tokenAmount);
    }
File:   src/rollup/RollupUserLogic.sol#L232
    function _addToDeposit(address stakerAddress, uint256 depositAmount) internal onlyValidator whenNotPaused {
        require(isStaked(stakerAddress), "NOT_STAKED");
        increaseStakeBy(stakerAddress, depositAmount);
    }
```

### Recommended Mitigation Steps

```diff
File:   src/rollup/RollupUserLogic.sol#L349
-    function addToDeposit(address stakerAddress, uint256 tokenAmount) external onlyValidator whenNotPaused {
+    function addToDeposit(address stakerAddress, uint256 tokenAmount) external {
        _addToDeposit(stakerAddress, tokenAmount);
        /// @dev This is an external call, safe because it's at the end of the function
        receiveTokens(tokenAmount);
    }
```
