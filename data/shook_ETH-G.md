[G-01] x + y is more efficient than using += for state variables.

src/assertionStakingPool/AbsBoldStakingPool.sol

line 34 - depositBalance[msg.sender] += amount;


[G-02] Nesting if-statements is cheaper than using &&
Using a triple if statement instead of logical AND (&&) can provide similar short-circuiting behavior whereas double if is slightly more efficient.

src/bridge/AbsBridge.sol

line 115 - if (
            sequencerReportedSubMessageCount != prevMessageCount &&
            prevMessageCount != 0 &&
            sequencerReportedSubMessageCount != 0
    ) 


[G-03] When using elements that are smaller than 32 bytes, your contract’s gas usage may be higher.This is because the EVM operates on 32 bytes at a time.Therefore, if the element is smaller than that, the EVM must use more 
operations in order to reduce the size of the element from 32 bytes to the desired size.

src/bridge/AbsBridge.sol

line 151 - function addMessageToDelayedAccumulator(
        uint8 kind,
        address sender,
        uint64 blockNumber,
        uint64 blockTimestamp,
        uint256 baseFeeL1,
        bytes32 messageDataHash
    )

line 173 - function addMessageToDelayedAccumulator(
        uint8 kind,
        address sender,
        uint64 blockNumber,
        uint64 blockTimestamp,
        uint256 baseFeeL1,
        bytes32 messageDataHash
    )


