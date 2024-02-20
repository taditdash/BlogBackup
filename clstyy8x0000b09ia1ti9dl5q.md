---
title: "Understanding Method Invocation Verification with Moq's Verifiable Constructs"
datePublished: Tue Feb 20 2024 06:12:55 GMT+0000 (Coordinated Universal Time)
cuid: clstyy8x0000b09ia1ti9dl5q
slug: understanding-method-invocation-verification-with-moqs-verifiable-constructs
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1708409526769/5ad2fa7b-ad1c-4dba-9921-14b171f1d957.jpeg
tags: unit-testing, net, moq

---

## Introduction

I encountered a scenario where I needed to test if a method inside another method was actually invoked. This led me to learn about the `Verifiable` construct in the *Moq* library. 💻 It provides a concrete way to ensure that the calls configured in the mock object are indeed invoked. ℹ

## Example 🚀

Suppose a `CartsController` has a `CreateOrder` method that calls the `GetCartItems` method within it:

```csharp
public async Task<IActionResult> CreateOrder(OrderViewModel orderViewModel)
{
    var cartItems = await _cartService.GetCartItems(orderViewModel.CartId);
	
	// More codes...

	return View("OrderCreated");
}
```

A unit test for this method can be written to verify whether `GetCartItems` is actually invoked or not. Let's see how we can achieve this.

## How to do? 🤷‍♀️

Mark the mock setup for the method as `Verifiable` and then call the `Verify` method on the mock object.

Here is a code snippet for one unit test case:

```csharp
// Mock setup inside the unit test for the GetCartItems method.
_cartServiceMock.Setup(x => x.GetCartItems(It.IsAny<int>())).ReturnsAsync(() => cartItems).Verifiable();
  
// The following CreateOrder calls the GetCartItems inside it.
var result = await cartsController.CreateOrder(orderModel);

// Now we can verify
_cartServiceMock.Verify();
```

Notice that we set up a method `GetCartItems` to be Verifiable. Then, we called the method inside the `CartsController` to create an order. The `CreateOrder` method calls the `GetCartItems` method inside it.

So, `_cartServiceMock.Verify();` will now be successful as it invoked the `GetCartItems` method.

If for some reason it does not, then the test will throw an exception like in the following screenshot.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1708334224845/49b02942-993d-480f-ac4a-1a09b044a111.png align="center")

## Feedback

I hope it is clear. Let me know if you have any doubts. 💪 Share, if you care. 🙌

## Reference

1. [Moq GitHub Repository](https://github.com/devlooped/moq)
    
2. [Moq Documentation on Verifications](https://docs.educationsmediagroup.com/unit-testing-csharp/moq/verifications)