---
title: "🔒🛡️ Demystifying Angular 16 Route Guard 🛡️🔒"
datePublished: Sat Jul 08 2023 07:48:53 GMT+0000 (Coordinated Universal Time)
cuid: cljtpfaf300010amihl0zdvic
slug: demystifying-angular-16-route-guard
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1688802308645/84f8b1aa-be87-4a7c-bf96-0feb08d9502e.jpeg
tags: routing, angular, angular16

---

Welcome back, fellow Angular enthusiasts! Today, we're diving into the intriguing world of Angular 16 Route Guards. 🚀

# 💡 Introduction💡

Angular 16 Route Guards are powerful tools that help us control navigation and access to specific routes in our Angular 16 applications. With these guards, we can protect certain routes from unauthorized access or perform additional checks before allowing users to proceed. One such guard we'll explore today is the ProductDetailGuard. Let's unravel its secrets! 🕵️‍♂️

# 🔍 Background 🔍

My use case is very simple and it mimics a real application use case. Here it is.

* `ProductDetail` Component will only load if the URL contains a `ProductId > 0`
    
* Anything else will be rejected and redirected to `Product` Component
    

Let's explore the code!

# 🔐 The ProductDetailGuard Code 🔐

```typescript
import { inject } from '@angular/core';
import { CanActivateFn, Router } from '@angular/router';

export const ProductDetailGuard: CanActivateFn = (route, state) => {
  return Number(route.paramMap.get('id')) > 0
    ? true
    : inject(Router).createUrlTree(['/products']);
};
```

In the code snippet above, we define the `ProductDetailGuard` as a `CanActivateFn`. This type of guard is responsible for determining whether a user can activate (access) a particular route.

The guard function receives two parameters: `route` and `state`. The `route` parameter contains information about the current route, while `state` provides details about the router state.

## 🚧 Guarding the Product Detail Route 🚧

The purpose of our `ProductDetailGuard` is to protect the route that displays detailed information about a product. It ensures that the user can only access the route if the `ProductId` provided in the route parameters is a positive number (`Number(route.paramMap.get('id')) > 0`).

If the condition is met, the guard returns `true`, allowing the user to proceed to the desired route.

## ⛔ Redirecting Unauthorized Users ⛔

On the other hand, if the condition evaluates to `false`, indicating an invalid or unauthorized access attempt, the guard takes action.

It uses the `inject` function from `@angular/core` to access the Angular injector and retrieve an instance of the `Router`.

With the `Router` instance in hand, it creates a URL tree using `createUrlTree(['/products'])`. This URL tree represents the desired destination, in this case, the `/products` route.

By returning the URL tree, the guard effectively redirects unauthorized users back to the products listing page.

# 🛡️ Putting the Guard into Action 🛡️

To activate our `ProductDetailGuard`, we need to integrate it into our application's routing configuration. Within the route definition for the product detail route, we can assign the guard using the `canActivate` property. For example:

```typescript
{
  path: 'products/:id',
  component: ProductDetailComponent,
  canActivate: [ProductDetailGuard]
}
```

By attaching the `ProductDetailGuard` to the `canActivate` property, we ensure that the guard is invoked before allowing access to the `ProductDetailComponent`.

This way, we add an extra layer of security to our application, safeguarding the product detail page from unauthorized users.

# 🔒🔓 Strengthen Your Angular Application with Route Guards 🔓🔒

Route guards are an essential part of building secure and robust Angular applications. With guards like the `ProductDetailGuard`, we can control access to routes, protect sensitive information, and guide users towards the appropriate sections of our application.

By leveraging these powerful tools, we enhance the user experience and ensure that our application remains reliable and trustworthy.

So, next time you find yourself needing to restrict access to certain routes or perform additional checks before allowing navigation, remember to employ Angular 16 Route Guards. Your application and your users will thank you! 💪

# 📝🗣️ Feedback! 🗣️📝

I would greatly appreciate your feedback on this blog post! Please take a moment to share your thoughts, suggestions, or any questions you may have in the comments below. Your feedback is incredibly valuable to me as it helps me improve and provide you with even better content in the future. Thank you for your support and for taking the time to share your input!