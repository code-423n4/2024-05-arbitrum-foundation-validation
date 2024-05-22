## QA REPORT

##

## [L-1] ``withdrawalAddress`` is not checked with address(0)

User input MUST be scrutinized. The withdrawal address is CRITICAL for retrieving staked funds. If withdrawalAddress is set to 0x0, the validator CANNOT withdraw funds and will be PERMANENTLY stuck in the contract.

```solidity
FILE: 2024-05-arbitrum-foundation/src/rollup/RollupCore.sol

 /**
     * @notice Create a new stake at latest confirmed assertion
     * @param stakerAddress Address of the new staker
     * @param depositAmount Stake amount of the new staker
     */
    function createNewStake(address stakerAddress, uint256 depositAmount, address withdrawalAddress) internal {
        uint64 stakerIndex = uint64(_stakerList.length);
        _stakerList.push(stakerAddress);
        _stakerMap[stakerAddress] = Staker(depositAmount, _latestConfirmed, stakerIndex, true, withdrawalAddress);
        emit UserStakeUpdated(stakerAddress, withdrawalAddress, 0, depositAmount);
    }


``` 
https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/rollup/RollupCore.sol#L269-L279

### Recommended Mitigation

Add address(0) check for ``withdrawalAddress ``


```diff

 function createNewStake(address stakerAddress, uint256 depositAmount, address withdrawalAddress) internal {
+ require(withdrawalAddress != address(0),"zero address");
        uint64 stakerIndex = uint64(_stakerList.length);
        _stakerList.push(stakerAddress);
        _stakerMap[stakerAddress] = Staker(depositAmount, _latestConfirmed, stakerIndex, true, withdrawalAddress);
        emit UserStakeUpdated(stakerAddress, withdrawalAddress, 0, depositAmount);
    }

``` 

