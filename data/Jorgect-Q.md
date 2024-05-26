# LOW REPORT

## [L-01] Not implementing `disableInitializer()`.

`disableInitializer` function is used to restrict the implementation for been initialized. this is important since the implementation can be mess up.

### Impact:

Implementations contract can be initialize potentially leading to some other problems 

### Tool used.
Manual review

### Recommendation
Consider implement disable initializer in the sequencer implementation and in the rollup implementation.

## [L-02]  initialize function is not implementing any access control in the `sequencerInbox`

`Initialize` function depending on how the contract will be deployed initialize function need to have access control because an attacker can front run the deployment and initialize the contract with his own values that the case of the initialize function in the `sequencerInbox`.

```solidity
function initialize(
        IBridge bridge_,
        ISequencerInbox.MaxTimeVariation calldata maxTimeVariation_,
        BufferConfig memory bufferConfig_
    ) external onlyDelegated {
        if (bridge != IBridge(address(0))) revert AlreadyInit();
        if (bridge_ == IBridge(address(0))) revert HadZeroInit();

        // Make sure logic contract was created by proper value for 'isUsingFeeToken'.
        // Bridge in ETH based chains doesn't implement nativeToken(). In future it might implement it and return address(0)
        bool actualIsUsingFeeToken = false;
        try IERC20Bridge(address(bridge_)).nativeToken() returns (address feeToken) {
            if (feeToken != address(0)) {
                actualIsUsingFeeToken = true;
            }
        } catch {}
        if (isUsingFeeToken != actualIsUsingFeeToken) {
            revert NativeTokenMismatch();
        }

        bridge = bridge_;
        rollup = bridge_.rollup();

        _setMaxTimeVariation(maxTimeVariation_);

        if (isDelayBufferable) {
            _setBufferConfig(bufferConfig_);
        }
    }
```
[[Link]](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/bridge/SequencerInbox.sol#L177C5-L205C6)

### Impact
The `sequencerInbox` can be malicious initialize.

### Tool used
Manual

### Recommendation
Consider add access control to the initialize function.



