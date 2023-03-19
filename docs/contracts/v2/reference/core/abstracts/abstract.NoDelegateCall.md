# NoDelegateCall

[Git Source](https://github.com/sablierhq/v2-core/blob/6223a7bce69cdec996b0a95cb95d0f04cdb809be/docs/contracts/v2/reference/core/abstracts)

This contract implements logic to prevent delegate calls.

## State Variables

### \_original

_The address of the original contract that was deployed._

```solidity
address private immutable _original;
```

## Functions

### constructor

_Sets the original contract address._

```solidity
constructor();
```

### noDelegateCall

Prevents delegate calls.

```solidity
modifier noDelegateCall();
```

### \_preventDelegateCall

_This function checks whether a delegate call is being made. A private function is used instead of inlining this logic
in a modifier because Solidity copies modifiers into every function that uses them. The `_original` address would get
copied in every place the modifier is used, which would increase the contract size. By using a function instead, we can
avoid this duplication of code and reduce the overall size of the contract._

```solidity
function _preventDelegateCall() private view;
```