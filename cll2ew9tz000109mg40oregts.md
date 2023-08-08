---
title: "Addition of two Numbers in AngularJS"
datePublished: Tue Feb 24 2015 08:03:10 GMT+0000 (Coordinated Universal Time)
cuid: cll2ew9tz000109mg40oregts
slug: addition-of-two-numbers-in-angularjs
tags: angularjs, html5, angular-js, number, sum

---

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1686903917240/e11be2f4-863b-4fb4-b6a0-b5fcdd646cb5.png align="center")

Recently, I have started learning AngularJS. *AngularJS* is a *JavaScript* Framework that helps you declare more HTML Tag Attributes with compelling functionality.

## Let’s Code Something

The first thing, which I tried to do, is to add two numbers and show the result in a `TextBox`. I coded like below…

```xml
<div ng-app="">
    <p>First Number:
        <input type="text" ng-model="a" />
    </p>
    <p>Second Number:
        <input type="text" ng-model="b" />
    </p>
    <p>Sum: {{ a + b }}</p>
</div>
```

### Couple of Notes

* The `ng-model` directive binds the value of the input field to the application variable name. So, the variable `"a"` will contain first `TextBox` Value and `"b"` will contain the second `TextBox` value.
    
* **{{ expression }}** is used to dynamically bind the result of the expression. Thus, while typing on the `TextBoxes`, this place will populate with the result of the expression, which is our expected summation.
    

### Alright, Let’s See What Happened Next

The following screenshot would tell you what happened after that.

![Sum of Two Numbers using TextBoxes](https://cdn.hashnode.com/res/hashnode/image/upload/v1686903918558/e7e7453f-85ed-4436-a80a-a5799a887f69.png align="center")

It is actually not adding, but concatenating the numbers. Why did this happen? That is because the values inside the `TextBoxes` are always a string. They are not numbers. Thus, the “+” operator would help them concatenate.

## Looking for Solutions !!!

Now, I researched and found two solutions.

### Solution 1 – Using Double Negation

Very beautiful hack. Code as…

```xml
<div ng-app="">
    <h3>Using Double Negation</h3>
 
    <p>First Number:
        <input type="text" ng-model="a" />
    </p>
    <p>Second Number:
        <input type="text" ng-model="b" />
    </p>
    <p>Sum: {{ a -- b }}</p>
</div>
```

### Solution 2 – Using HTML5 Input Type Number

This is the most preferable way of achieving this task as it uses *HTML5* Input Type `Number`. So, when we use this `Number` Type, then the “+” operator will work because the values are numbers by default.

```xml
<div ng-app="">
    <h3>Using Input Type Number</h3>
 
    <p>First Number:
        <input type="number" ng-model="c" />
    </p>
    <p>Second Number:
        <input type="number" ng-model="d" />
    </p>
    <p>Sum: {{ c + d }}</p>
</div>
```

![Sum of Two Numbers in AngularJS](https://cdn.hashnode.com/res/hashnode/image/upload/v1686903919661/7cf1af95-40c4-400b-903c-fba386e9df11.png align="center")

## Demo

*jsfiddle* link – [Sum of two Numbers using AngularJS](http://jsfiddle.net/taditdash/726o7wpd/)

## Going Forward

I hope you liked the Blog. Thanks for reading. As I progress and find more interesting stuff, I will share it in my future Blog posts. Happy coding. 😀