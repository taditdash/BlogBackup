---
title: "Uncaught IndexSizeError: Failed to execute ‘getImageData’ on ‘CanvasRenderingContext2D’: The source width is 0."
datePublished: Tue Oct 04 2016 12:30:16 GMT+0000 (Coordinated Universal Time)
cuid: clj2usm8c000c09mac90yapu7
slug: uncaught-indexsizeerror-failed-to-execute-getimagedata-on-canvasrenderingcontext2d-the-source-width-is-0
tags: image-processing, javascript, canvas, image-compression

---

## Introduction

In this post, we will discuss a problem, which I recently came across while working with images in coding.

## Background

The work was to take one image from the file upload control and then compress it using Canvas before uploading it to the server. I used a plugin, but let’s not go into that. We will directly come to the point where this problem can happen.

## Problem

So, the line that we are talking about is like below.

`var canvas = canvas.getContext('2d') .getImageData(0, 0, imgWidth, imgHeight);`

We are sending the image width and height to [getImageData](https://developer.mozilla.org/en-US/docs/Web/API/CanvasRenderingContext2D/getImageData). However, if you analyze the error message, it says that the width is 0.

## Solution

With further research on the developer console, while debugging, I found that the width and height are actually populated in some other properties named as `naturalWidth` and `naturalHeight`.  
Therefore, we can write the code like below.

```javascript
var imgWidth = image.width || image.naturalWidth;

var imgHeight = image.height || image.naturalHeight;

var canvas = canvas.getContext('2d') .getImageData(0, 0, imgWidth, imgHeight);
```

Now your program should work as expected without errors.

### More on naturalHeight and naturalWidth from [MDN](https://developer.mozilla.org/en-US/docs/Web/API/HTMLImageElement)

`HTMLImageElement.naturalHeight` (Read only)

Returns a `unsigned long` representing the intrinsic height of the image in CSS pixels, if it is available; else, it shows `0`.

`HTMLImageElement.naturalWidth` (Read only)

Returns a `unsigned long` representing the intrinsic width of the image in CSS pixels, if it is available; otherwise, it will show `0`.

## Feedback

If you like this blog, feel free to share it in your circle and save someone’s time. Please comment below, if you have any inputs for me.

Thanks for reading. Have a nice day ahead.