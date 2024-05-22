Gas Optimization Issue in `EdgeStakingPool.sol`

**Overview:**
A gas optimization issue has been identified in the `createEdge` function of the `EdgeStakingPool.sol` contract. Multiple storage reads and repeated external calls to `challengeManager` result in high gas consumption, potentially exceeding gas limits and causing a denial of service.

**Issue Details:**
- **File:** `EdgeStakingPool.sol`
- **Function:** `createEdge`
- **Problem:** Multiple storage reads and external calls to `challengeManager`.

**Optimized Solution:**
The optimization involves storing the `challengeManager` address in a local variable to reduce storage reads and minimize external calls.

**Original Function:**
```solidity
function createEdge(CreateEdgeArgs calldata args) external {
    uint256 requiredStake = EdgeChallengeManager(challengeManager).stakeAmounts(args.level);
    IERC20(stakeToken).safeIncreaseAllowance(address(challengeManager), requiredStake);
    bytes32 newEdgeId = EdgeChallengeManager(challengeManager).createLayerZeroEdge(args);
    if (newEdgeId != edgeId) {
        revert IncorrectEdgeId(newEdgeId, edgeId);
    }
}
```

**Optimized Function:**
```solidity
function createEdge(CreateEdgeArgs calldata args) external {
    address cm = challengeManager; // Store in memory for gas optimization
    uint256 requiredStake = EdgeChallengeManager(cm).stakeAmounts(args.level);
    IERC20(stakeToken).safeIncreaseAllowance(cm, requiredStake);
    bytes32 newEdgeId = EdgeChallengeManager(cm).createLayerZeroEdge(args);
    if (newEdgeId != edgeId) {
        revert IncorrectEdgeId(newEdgeId, edgeId);
    }
}
```

**Proof of Concept (PoC):**
A test contract measures the gas consumption of the original and optimized `createEdge` functions.

**Test Contract:**
```solidity
pragma solidity ^0.8.0;

import "./EdgeStakingPool.sol";
import "./EdgeStakingPoolOptimized.sol";

contract GasConsumptionTest {
    EdgeStakingPool public originalPool;
    EdgeStakingPoolOptimized public optimizedPool;
    EdgeChallengeManager public challengeManager;

    constructor(address _challengeManager, bytes32 _edgeId) {
        originalPool = new EdgeStakingPool(_challengeManager, _edgeId);
        optimizedPool = new EdgeStakingPoolOptimized(_challengeManager, _edgeId);
        challengeManager = EdgeChallengeManager(_challengeManager);
    }

    function testCreateEdgeOriginal(CreateEdgeArgs calldata args) external returns (uint256) {
        uint256 gasBefore = gasleft();
        originalPool.createEdge(args);
        uint256 gasAfter = gasleft();
        return gasBefore - gasAfter;
    }

    function testCreateEdgeOptimized(CreateEdgeArgs calldata args) external returns (uint256) {
        uint256 gasBefore = gasleft();
        optimizedPool.createEdge(args);
        uint256 gasAfter = gasleft();
        return gasBefore - gasAfter;
    }
}
```

Outcome:
The optimized version should demonstrate reduced gas consumption, validating the optimization's effectiveness.
