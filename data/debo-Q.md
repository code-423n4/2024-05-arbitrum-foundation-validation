# LOW-1 - The compiler pragma version is floating

Avoid using floating pragmas for contracts that are not libraries.

So, for libraries floating pragmas allow cross-functionality. But, for non-library contracts this is a security risk.

To the point, old versions which floating pragmas allow, have old security vulnerabilities that have been patched in the new fixed version.

Hence, using floating versions makes your contracts vulnerable to old known or unknown security bugs, which you would unwittingly deploy to the blockchain.

Please adopt fixed and newish pragma version.

# AbsBoldStakingPool.sol
# Line 5> 
# bug flaw> pragma solidity ^0.8.0;
# bug fix> pragma solidity 0.8.4;
``` ```
``` ```
# AssertionStakingPool.sol
# Line 6> 
# bug flaw> pragma solidity ^0.8.0;
# bug fix> pragma solidity 0.8.4;
``` ```
``` ```
# AssertionStakingPoolCreator.sol
# Line 6> 
# bug flaw> pragma solidity ^0.8.0;
# bug fix> pragma solidity 0.8.4;
``` ```
``` ```
# EdgeStakingPool.sol
# Line 5> 
# bug flaw> pragma solidity ^0.8.0;
# bug fix> pragma solidity 0.8.4;
``` ```
``` ```
# EdgeStakingPoolCreator.sol
# Line 6> 
# bug flaw> pragma solidity ^0.8.0;
# bug fix> pragma solidity 0.8.4;
``` ```
``` ```
# StakingPoolCreatorUtils.sol
# Line 6> 
# bug flaw> pragma solidity ^0.8.0;
# bug fix> pragma solidity 0.8.4;
``` ```
``` ```
# IAbsBoldStakingPool.sol
# Line 5> 
# bug flaw> pragma solidity ^0.8.0;
# bug fix> pragma solidity 0.8.4;
``` ```
``` ```
# IAssertionStakingPool.sol
# Line 5> 
# bug flaw> pragma solidity ^0.8.0;
# bug fix> pragma solidity 0.8.4;
``` ```
``` ```
# IEdgeStakingPool.sol
# Line 5> 
# bug flaw> pragma solidity ^0.8.0;
# bug fix> pragma solidity 0.8.4;
``` ```
``` ```
# IEdgeStakingPoolCreator.sol
# Line 5> 
# bug flaw> pragma solidity ^0.8.0;
# bug fix> pragma solidity 0.8.4;
``` ```
``` ```
# IEdgeStakingPoolCreator.sol
# Line 5> 
# bug flaw> pragma solidity ^0.8.0;
# bug fix> pragma solidity 0.8.4;
``` ```
``` ```
# SequencerInbox.sol
# Line 5> 
# bug flaw> pragma solidity >=0.6.9 <0.9.0;
# bug fix> pragma solidity 0.8.11;
``` ```
``` ```
# EdgeChallengeManager.sol
# Line 5> 
# bug flaw> pragma solidity ^0.8.17;
# bug fix> pragma solidity 0.8.26;
``` ```
``` ```
# IAssertionChain.sol
# Line 5> 
# bug flaw> pragma solidity ^0.8.17;
# bug fix> pragma solidity 0.8.26;
``` ```
``` ```
# rollup/Assertion.sol
# Line 5> 
# bug flaw> pragma solidity ^0.8.0;
# bug fix> pragma solidity 0.8.4;
``` ```
``` ```
# rollup/AssertionState.sol
# Line 5> 
# bug flaw> pragma solidity ^0.8.0;
# bug fix> pragma solidity 0.8.4;
``` ```
``` ```
# rollup/BOLDUpgradeAction.sol
# Line 5> 
# bug flaw> pragma solidity ^0.8.0;
# bug fix> pragma solidity 0.8.4;
``` ```
``` ```
# rollup/BridgeCreator.sol
# Line 5> 
# bug flaw> pragma solidity ^0.8.0;
# bug fix> pragma solidity 0.8.4;
``` ```
``` ```
# rollup/Config.sol
# Line 5> 
# bug flaw> pragma solidity ^0.8.0;
# bug fix> pragma solidity 0.8.4;
``` ```
``` ```
# rollup/IRollupAdmin.sol
# Line 5> 
# bug flaw> pragma solidity ^0.8.0;
# bug fix> pragma solidity 0.8.4;
``` ```
``` ```
# rollup/IRollupCore.sol
# Line 5> 
# bug flaw> pragma solidity ^0.8.0;
# bug fix> pragma solidity 0.8.4;
``` ```
``` ```
# rollup/IRollupLogic.sol
# Line 5> 
# bug flaw> pragma solidity ^0.8.0;
# bug fix> pragma solidity 0.8.4;
``` ```
``` ```
# rollup/RollupAdminLogic.sol
# Line 5> 
# bug flaw> pragma solidity ^0.8.0;
# bug fix> pragma solidity 0.8.4;
``` ```
``` ```
# rollup/RollupCore.sol
# Line 5> 
# bug flaw> pragma solidity ^0.8.0;
# bug fix> pragma solidity 0.8.4;
``` ```
``` ```
# rollup/RollupCreator.sol
# Line 5> 
# bug flaw> pragma solidity ^0.8.0;
# bug fix> pragma solidity 0.8.4;
``` ```
``` ```
# rollup/RollupProxy.sol
# Line 5> 
# bug flaw> pragma solidity ^0.8.0;
# bug fix> pragma solidity 0.8.4;
``` ```
``` ```
# rollup/RollupUserLogic.sol
# Line 5> 
# bug flaw> pragma solidity ^0.8.0;
# bug fix> pragma solidity 0.8.4;