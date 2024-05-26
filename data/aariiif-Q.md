## L/N - 01  Lack of Input Validation
https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/rollup/RollupCreator.sol#L137-L265

The `createRollup` function does not perform any input validation on the `RollupDeploymentParams` struct. While the code checks the `maxDataSize` against the templates, it does not validate other fields in the `RollupDeploymentParams` struct, such as the validators array, `batchPosters` array, or `batchPosterManager` address.

**Consequences**

If the validators array contains invalid addresses or duplicates, it could lead to unexpected behavior or errors when setting validators.
If the `batchPosters` array contains invalid addresses or duplicates, it could lead to unexpected behavior or errors when setting batch posters.
If the `batchPosterManager` address is invalid or not a contract address, it could lead to unexpected behavior or errors when setting the batch poster manager.

**Mitigation**
Implement input validation checks for the `RollupDeploymentParams` struct fields to ensure that the provided addresses are valid and that there are no duplicates in the validators and `batchPosters` arrays. This can help prevent potential errors and unexpected behavior.

## L/N - 12 Consider using a constructor instead of a separate function for setting templates
https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/rollup/RollupCreator.sol#L63-L82

Instead of having a separate function `setTemplates` to initialize the contract's state variables, you could move this logic to the constructor. This would ensure that the contract is properly initialized upon deployment and prevent the risk of forgetting to call `setTemplates` or calling it with incorrect parameters.

## L/N - 07 Validate Input Parameters, Use Events for Logging and Consider Using a Factory Pattern.
https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/rollup/RollupCreator.sol#L85-L113

1. The function does not perform any validation on the input parameters, such as checking if the `rollupAddr`, `proxyAdminAddr`, or config values are valid. Adding input validation can help prevent unexpected behavior and improve the overall security of the code.

2. The function does not emit any events, which can be useful for logging and debugging purposes. Emitting events when important actions occur, such as the creation of a new `ChallengeManager` contract, can aid in monitoring and auditing the system.

3. Instead of creating a new instance of the `TransparentUpgradeableProxy` contract within the `createChallengeManager` function, you could consider using a factory pattern. This would involve creating a separate contract responsible for deploying and managing instances of the `ChallengeManager` contract, which could improve code organization and reusability.

## L/N - 03 Unintended behavior
https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/rollup/RollupCreator.sol#L137-L265

The function checks the `maxDataSize` for the `SequencerInbox`, `DelayBufferableSequencerInbox`, and Inbox contracts against the provided `deployParams.maxDataSize`. However, it does not check if the `deployParams.maxDataSize` itself is valid or within the expected range.

If the `deployParams.maxDataSize` is set to an invalid or unexpected value, the function will still proceed with the deployment, potentially leading to inconsistencies or errors in the deployed contracts.

Consider adding an additional check to ensure that `deployParams.maxDataSize` falls within a valid range before proceeding with the deployment. This check could be implemented as a separate function or as a modifier to the `createRollup` function.
```solidity
modifier validMaxDataSize(uint256 maxDataSize) {
    // Add your validation logic here
    // For example, you could check if maxDataSize is within a specific range
    require(maxDataSize >= minDataSize && maxDataSize <= maxDataSize, "Invalid maxDataSize");
    _;
}

function createRollup(RollupDeploymentParams memory deployParams)
    public
    payable
    validMaxDataSize(deployParams.maxDataSize)
    returns (address)
{
    // ... (rest of the function remains the same)
}
```

## L/N - 09 Avoid Magic Numbers, Use Solidity's Built-in Array Initialization, Consider Using OpenZeppelin's Proxy Contracts
https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/rollup/RollupCreator.sol#L267-L285

```solidity
    function _deployUpgradeExecutor(address rollupOwner, ProxyAdmin proxyAdmin)
        internal
        returns (address)
    {
        IUpgradeExecutor upgradeExecutor = IUpgradeExecutor(
            address(
                new TransparentUpgradeableProxy(
                    address(upgradeExecutorLogic),
                    address(proxyAdmin),
                    bytes("")
                )
            )
        );
        address[] memory executors = new address[](1);
        executors[0] = rollupOwner;
        upgradeExecutor.initialize(address(upgradeExecutor), executors);


        return address(upgradeExecutor);
    }
```
Avoid Magic Numbers Instead of hardcoding the value `1` for the length of the `executors` array, it would be better to use a constant or a named variable to make the code more readable and easier to maintain.

Use Solidity's Built-in Array Initialization Instead of creating an array and then assigning a value to its first element, you can use Solidity's built-in array initialization syntax: `address[] memory executors = [rollupOwner];`. This makes the code more concise and easier to read.

Consider Using OpenZeppelin's Proxy Contracts well-audited and widely-used proxy contracts, such as `TransparentUpgradeableProxy` and `ProxyAdmin`. If you're not already using OpenZeppelin, it might be worth considering to leverage their battle-tested implementations and reduce the risk of introducing vulnerabilities.

## L/N - 05 Improvement on `_deployFactories` function
https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/rollup/RollupCreator.sol#L287-L318
```solidity
    function _deployFactories(
        address _inbox,
        address _nativeToken,
        uint256 _maxFeePerGas
    ) internal {
        if (_nativeToken == address(0)) {
            // we need to fund 4 retryable tickets
            uint256 cost = l2FactoriesDeployer.getDeploymentTotalCost(
                IInboxBase(_inbox),
                _maxFeePerGas
            );


            // do it
            l2FactoriesDeployer.perform{value: cost}(_inbox, _nativeToken, _maxFeePerGas);


            // refund the caller
            // solhint-disable-next-line avoid-low-level-calls
            (bool sent, ) = msg.sender.call{value: address(this).balance}("");
            require(sent, "Refund failed");
        } else {
            // Transfer fee token amount needed to pay for retryable fees to the inbox.
            uint256 totalFee = l2FactoriesDeployer.getDeploymentTotalCost(
                IInboxBase(_inbox),
                _maxFeePerGas
            );
            IERC20(_nativeToken).safeTransferFrom(msg.sender, _inbox, totalFee);


            // do it
            l2FactoriesDeployer.perform(_inbox, _nativeToken, _maxFeePerGas);
        }
    }
}
```

Use Modifiers or Separate Functions for Validation Instead of checking the condition `if (_nativeToken == address(0))` within the function, consider using a modifier or a separate function to validate the input parameters.

The code uses a low-level call to refund the remaining balance to the sender. While this may be necessary in some cases, it can be more secure and readable to use a higher-level method like transfer or send if possible.

The variable `_maxFeePerGas` follows a different naming convention than the other parameters (`_inbox` and `_nativeToken`). It would be better to use a consistent naming convention throughout the codebase for better readability and maintainability.