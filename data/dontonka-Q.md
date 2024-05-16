### **[[ Low - 1 ]]** 
In `EdgeStakingPoolCreator::createPool` you should add the `contract address` in the event as otherwise it can be lost easily. That would be also more consistent with `AssertionStakingPoolCreator.sol`.

```diff
    /// @notice Event emitted when a new staking pool is created
-   event NewEdgeStakingPoolCreated(address indexed challengeManager, bytes32 indexed edgeId);
+   event NewEdgeStakingPoolCreated(address indexed challengeManager, bytes32 indexed edgeId, address edgePool);


contract EdgeStakingPoolCreator is IEdgeStakingPoolCreator {
    /// @inheritdoc IEdgeStakingPoolCreator
    function createPool(
        address challengeManager,
        bytes32 edgeId
    ) external returns (IEdgeStakingPool) {
        EdgeStakingPool pool = new EdgeStakingPool{salt: 0}(challengeManager, edgeId);
-       emit NewEdgeStakingPoolCreated(challengeManager, edgeId);
+       emit NewEdgeStakingPoolCreated(challengeManager, edgeId, address(pool)); 
        return pool;
    }
```
https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/assertionStakingPool/EdgeStakingPoolCreator.sol#L20