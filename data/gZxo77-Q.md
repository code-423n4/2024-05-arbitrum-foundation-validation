###[L-1]in the ***assertionStakingPool::AssertionStakingPool.sok*** there is a missing check statement that cheks if the amount requierd is the acttual amount with can cuse poeple loss of funds if by mistake they will deposit a higher amount Root 
***Description***A missing requierd amout check can lead to a possible mistake of the assertion maker depositing higher amount then requierd  wich can lead   to a lock of funds of the staked wich means a loss of funds 

"""
 
        function createAssertion(AssertionInputs calldata         assertionInputs) external {
        //Audit can add an if statment for peope to not exeecd the deposited amount
        uint256 requiredStake = assertionInputs.beforeStateData.configData.requiredStake;
        // approve spending from rollup for newStakeOnNewAssertion call
        IERC20(stakeToken).safeIncreaseAllowance(rollup, requiredStake);
        // reverts if pool doesn't have enough stake and if assertion has already been asserted
        IRollupUser(rollup).newStakeOnNewAssertion(requiredStake, assertionInputs, assertionHash, address(this));
    }
  

"""



***Proof of Concept***:
1.A person what to make assertion  
2.A person depositing money and by mistake deposit more that the requierd amount wich leads to a lock up of the funds 

***Recommended Mitigation***:
Adding a check at the start of the function to check if the amount deposited is the amount requierd 