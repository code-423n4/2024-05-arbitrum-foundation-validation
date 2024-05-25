## L-1: Unprotected initializer

Consider protecting the initializer functions with modifiers.


- Found in src/rollup/BOLDUpgradeAction.sol [Line: 84](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/rollup/BOLDUpgradeAction.sol#L84)

    ```solidity
	    function postUpgradeInit(BufferConfig memory bufferConfig_) external;
    ```

- Found in src/rollup/RollupCore.sol [Line: 225](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/rollup/RollupCore.sol#L225)

	```solidity
	    function initializeCore(AssertionNode memory initialAssertion, bytes32 assertionHash) internal {
	```

- Found in src/rollup/RollupProxy.sol [Line: 12](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/rollup/RollupProxy.sol#L12)

	```solidity
	    function initializeProxy(Config memory config, ContractDependencies memory connectedContracts)
	```


## L-2: Missing checks for `address(0)` when assigning values to address state variables

Check for `address(0)` when assigning values to address state variables.

- Found in src/bridge/SequencerInbox.sol [Line: 898](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/bridge/SequencerInbox.sol#L898)

	```solidity
	        isBatchPoster[addr] = isBatchPoster_;`
	```

- Found in src/bridge/SequencerInbox.sol [Line: 937](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/bridge/SequencerInbox.sol#L937)

	```solidity
	        isSequencer[addr] = isSequencer_;
	```

- Found in src/challengeV2/EdgeChallengeManager.sol [Line: 330](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/challengeV2/EdgeChallengeManager.sol#L330)

	```solidity
	        stakeToken = _stakeToken;
	```

- Found in src/rollup/RollupAdminLogic.sol [Line: 118](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/rollup/RollupAdminLogic.sol#L118)

	```solidity
	        outbox = _outbox;
	```

- Found in src/rollup/RollupAdminLogic.sol [Line: 300](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/rollup/RollupAdminLogic.sol#L300)

	```solidity
	        inbox = newInbox;
	```

- Found in src/rollup/RollupAdminLogic.sol [Line: 318](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/rollup/RollupAdminLogic.sol#L318)

	```solidity
	        anyTrustFastConfirmer = _anyTrustFastConfirmer;
	```

- Found in src/rollup/RollupAdminLogic.sol [Line: 327](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/rollup/RollupAdminLogic.sol#L327)

	```solidity
	        challengeManager = IEdgeChallengeManager(_challengeManager);
	```

- Found in src/rollup/RollupCore.sol [Line: 277](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/rollup/RollupCore.sol#L277)

	```solidity
	        _stakerMap[stakerAddress] = Staker(depositAmount, _latestConfirmed, stakerIndex, true, withdrawalAddress);
	```

- Found in src/rollup/RollupCreator.sol [Line: 73](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/rollup/RollupCreator.sol#L73)

	```solidity
	        bridgeCreator = _bridgeCreator;
	```

- Found in src/rollup/RollupCreator.sol [Line: 74](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/rollup/RollupCreator.sol#L74)

	```solidity
	        osp = _osp;
	```

- Found in src/rollup/RollupCreator.sol [Line: 75](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/rollup/RollupCreator.sol#L75)

	```solidity
	        challengeManagerTemplate = _challengeManagerLogic;
	```

- Found in src/rollup/RollupCreator.sol [Line: 76](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/rollup/RollupCreator.sol#L76)

	```solidity
	        rollupAdminLogic = _rollupAdminLogic;
	```

- Found in src/rollup/RollupCreator.sol [Line: 77](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/rollup/RollupCreator.sol#L77)

	```solidity
	        rollupUserLogic = _rollupUserLogic;
	```

- Found in src/rollup/RollupCreator.sol [Line: 78](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/rollup/RollupCreator.sol#L78)

	```solidity
	        upgradeExecutorLogic = _upgradeExecutorLogic;
	```

- Found in src/rollup/RollupCreator.sol [Line: 79](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/rollup/RollupCreator.sol#L79)

	```solidity
	        validatorWalletCreator = _validatorWalletCreator;
	```

- Found in src/rollup/RollupCreator.sol [Line: 80](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/rollup/RollupCreator.sol#L80)

	```solidity
	        l2FactoriesDeployer = _l2FactoriesDeployer;
	```


## L-3: `public` functions not used internally could be marked `external`

Instead of marking a function as `public`, consider marking it as `external` if it is not used internally.


- Found in src/rollup/RollupCore.sol [Line: 116](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/rollup/RollupCore.sol#L116)

	```solidity
	    function sequencerInbox() public view virtual returns (ISequencerInbox) {
	```

- Found in src/rollup/RollupCore.sol [Line: 134](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/rollup/RollupCore.sol#L134)

	```solidity
	    function getAssertion(bytes32 assertionHash) public view override returns (AssertionNode memory) {
	```

- Found in src/rollup/RollupCore.sol [Line: 217](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/rollup/RollupCore.sol#L217)

	```solidity
	    function stakerCount() public view override returns (uint64) {
	```


## L-4: Define and use `constant` variables instead of using literals

If the same constant literal value is used multiple times, create a constant state variable and reference it throughout the contract.

- Found in src/bridge/SequencerInbox.sol [Line: 713](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/bridge/SequencerInbox.sol#L713)

	```solidity
	                bytes32 dasKeysetHash = bytes32(data[1:33]);
	```


## L-5: Event is missing `indexed` fields

Index event fields make the field more quickly accessible to off-chain tools that parse events. However, note that each index field costs extra gas during emission, so it's not necessarily best to index the maximum allowed per event (three fields). Each event should use three indexed fields if there are three or more fields, and gas usage is not particularly of concern for the events in question. If there are fewer than three fields, all of the fields should be indexed.

- Found in src/assertionStakingPool/interfaces/IAbsBoldStakingPool.sol [Line: 9](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/assertionStakingPool/interfaces/IAbsBoldStakingPool.sol#L9)

	```solidity
	    event StakeDeposited(address indexed sender, uint256 amount);
	```

- Found in src/assertionStakingPool/interfaces/IAbsBoldStakingPool.sol [Line: 11](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/assertionStakingPool/interfaces/IAbsBoldStakingPool.sol#L11)

	```solidity
	    event StakeWithdrawn(address indexed sender, uint256 amount);
	```

- Found in src/assertionStakingPool/interfaces/IAssertionStakingPoolCreator.sol [Line: 12](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/assertionStakingPool/interfaces/IAssertionStakingPoolCreator.sol#L12)

	```solidity
	    event NewAssertionPoolCreated(
	```

- Found in src/bridge/ISequencerInbox.sol [Line: 41](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/bridge/ISequencerInbox.sol#L41)

	```solidity
	    event SequencerBatchData(uint256 indexed batchSequenceNumber, bytes data);
	```

- Found in src/bridge/ISequencerInbox.sol [Line: 44](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/bridge/ISequencerInbox.sol#L44)

	```solidity
	    event SetValidKeyset(bytes32 indexed keysetHash, bytes keysetBytes);
	```

- Found in src/challengeV2/EdgeChallengeManager.sol [Line: 243](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/challengeV2/EdgeChallengeManager.sol#L243)

	```solidity
	    event EdgeConfirmedByTime(bytes32 indexed edgeId, bytes32 indexed mutualId, uint256 totalTimeUnrivaled);
	```

- Found in src/challengeV2/EdgeChallengeManager.sol [Line: 253](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/challengeV2/EdgeChallengeManager.sol#L253)

	```solidity
	    event TimerCacheUpdated(bytes32 indexed edgeId, uint256 newValue);
	```

- Found in src/challengeV2/EdgeChallengeManager.sol [Line: 260](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/challengeV2/EdgeChallengeManager.sol#L260)

	```solidity
	    event EdgeRefunded(bytes32 indexed edgeId, bytes32 indexed mutualId, address stakeToken, uint256 stakeAmount);
	```

- Found in src/rollup/IRollupCore.sol [Line: 26](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/rollup/IRollupCore.sol#L26)

	```solidity
	    event AssertionCreated(
	```

- Found in src/rollup/IRollupCore.sol [Line: 38](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/rollup/IRollupCore.sol#L38)

	```solidity
	    event AssertionConfirmed(bytes32 indexed assertionHash, bytes32 blockHash, bytes32 sendRoot);
	```

- Found in src/rollup/IRollupCore.sol [Line: 40](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/rollup/IRollupCore.sol#L40)

	```solidity
	    event RollupChallengeStarted(
	```

- Found in src/rollup/IRollupCore.sol [Line: 44](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/rollup/IRollupCore.sol#L44)

	```solidity
	    event UserStakeUpdated(address indexed user, address indexed withdrawalAddress, uint256 initialBalance, uint256 finalBalance);
	```

- Found in src/rollup/IRollupCore.sol [Line: 46](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/rollup/IRollupCore.sol#L46)

	```solidity
	    event UserWithdrawableFundsUpdated(address indexed user, uint256 initialBalance, uint256 finalBalance);
	```

- Found in src/rollup/RollupCreator.sol [Line: 20](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/rollup/RollupCreator.sol#L20)

	```solidity
	    event RollupCreated(
	```
