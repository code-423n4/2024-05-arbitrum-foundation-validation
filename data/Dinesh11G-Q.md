
## Don't Initialize Variables with Default Value

  2024-05-arbitrum-foundation/src/bridge/SequencerInbox.sol::187 => bool actualIsUsingFeeToken = false;
  2024-05-arbitrum-foundation/src/challengeV2/EdgeChallengeManager.sol::517 => uint64 assertionBlocks = 0;
  2024-05-arbitrum-foundation/src/challengeV2/libraries/MerkleTreeLib.sol::293 => uint256 sum = 0;
  2024-05-arbitrum-foundation/src/challengeV2/libraries/MerkleTreeLib.sol::326 => uint256 proofIndex = 0;

Uninitialized variables are assigned with the types default value.

Explicitly initializing a variable with it's default value costs unnecessary gas.

Example
🤦 Bad:

uint256 x = 0;
bool y = false;
🚀 Good:

uint256 x;
bool y;


====================================================================


## Cache Array Length Outside of Loop

  2024-05-arbitrum-foundation/src/rollup/RollupCreator.sol::225 => for (uint256 i = 0; i < deployParams.batchPosters.length; i++) {

Caching the array length outside a loop saves reading it on each iteration, as long as the array's length is not changed during the loop.

Example
🤦 Bad:

`for (uint256 i = 0; i < array.length; i++) {
    // invariant: array's length is not changed
}`

🚀 Good:

`uint256 len = array.length
for (uint256 i = 0; i < len; i++) {
    // invariant: array's length is not changed
}`


======================================================================

## Use `!= 0` instead of `> 0` for Unsigned Integer Comparison
  2024-05-arbitrum-foundation/src/challengeV2/libraries/UintUtilsLib.sol::15 => require(x > 0, "Zero has no significant bits");

When dealing with unsigned integer types, comparisons with != 0 are cheaper than with > 0.

Example
🤦 Bad:

`// `a` being of type unsigned integer
require(a > 0, "!a > 0");`

🚀 Good:

`// `a` being of type unsigned integer
require(a != 0, "!a > 0");`


================================================================================

## Use `immutable` for OpenZeppelin `AccessControl's` Roles Declarations

Access roles marked as `constant` results in computing the `keccak256` operation each time the variable is used because assigned operations for `constant` variables are re-evaluated every time.

  2024-05-arbitrum-foundation/src/challengeV2/libraries/EdgeChallengeManagerLib.sol::135 => bytes32 public constant UNRIVALED = keccak256(abi.encodePacked("UNRIVALED"));

Changing the variables to `immutable` results in computing the hash only once on deployment, leading to gas savings.

Example
🤦 Bad:

`bytes32 public constant GOVERNOR_ROLE = keccak256("GOVERNOR_ROLE");`
🚀 Good:

`bytes32 public immutable GOVERNOR_ROLE = keccak256("GOVERNOR_ROLE");`
Background Information

===========================================================================

## Optimizing Gas Usage in Smart Contract Hashing Function

Switching from `abi.encode` to `abi.encodePacked` for the hashing process could significantly reduce the gas cost associated with the operation. By eliminating unnecessary padding, `abi.encodePacked` produces a more compact binary representation of the data, thereby reducing the amount of data that needs to be processed and stored.

https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/rollup/AssertionState.sol#L23

-- return keccak256(abi.encode(state));

++ return keccak256(abi.encodePacked(state));



