---
title: "Detect Changes to Spectrum Colorpicker"
datePublished: Tue Mar 29 2016 14:31:12 GMT+0000 (Coordinated Universal Time)
cuid: cljqwebxb000a0ajs5g5h4wbh
slug: detect-changes-to-spectrum-colorpicker
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1686903823198/60c80859-d7ef-438d-92d3-adecd621ab0a.png
tags: jquery, javascript, color-picker

---

## Introduction

In this blog, we will see how to manage the default value of the color picker so that we can detect if the color is changed.

## Background

In my current project, the requirement came to check if there are changes on the page on a button click and show a modal alerting the user that “There are changes, do you want to save?”. I found a script that can be triggered to check the changes on the page. It worked perfectly with all input, select and textarea controls.

But if I have a *color picker* on the page, then it always tells me that "you have changes", even if I did not change the color in the picker. Let me explain more. The *color picker* used is [Spectrum](https://bgrins.github.io/spectrum/).

## Step by Step

Suppose, I have one `input`, `select` and `textarea` on my page. One button to check if we have any change on these controls meaning if we edited/changed the field values.

```xml
<input />
 
<select>
    <option value="1">1</option>
    <option value="2" selected="selected">2</option>
    <option value="3">3</option>
</select>
 
<textarea>Hello World</textarea>
 
<button onclick="CheckForChanges()">
    Check For Changes
</button>
```

Now let’s check the click event code.

```javascript
function CheckForChanges() {
  if (GetHasChanges()) {
      alert("Yes we have changes!!!");
  } else {
      alert("No changes!!!");
  }
}
```

I am not posting the `GetHasChanges` function here, you can see it in the jsfiddle [Demo](https://jsfiddle.net/taditdash/upzy3ajp/).  
So, see the picture below which tells what is before you click the button and what happens after you edit some field and click the button. It perfectly checking that we have a change.

![Before and After Changes Done](https://cdn.hashnode.com/res/hashnode/image/upload/v1686903813499/82dae33e-e208-4c63-b0eb-370c019bf75f.png align="left")

Before and After Changes Done

### With Colorpicker

Let’s add a colorpicker now.

```xml
<input id="colorpicker" style="display:none;" value="#000" />
```

```javascript
$(document).ready(function() {
  $('#colorpicker').spectrum({
    preferredFormat: "hex"
  });
});
```

**Demo –** [**Demo With a Colorpicker**](https://jsfiddle.net/taditdash/upzy3ajp/15/)  
As you see in the picture below, everything is perfect.

![Detecting Changes with Colorpicker](https://cdn.hashnode.com/res/hashnode/image/upload/v1686903815496/80adfd89-b080-402c-be2c-0e7bb0ef3eac.png align="left")

Detecting Changes with Colorpicker

### Implementing Input Field inside the Colorpicker

This can be done by setting the `showInput` property to `true`

```javascript
$(document).ready(function() {
  $('#colorpicker').spectrum({
    showInput: true,
    preferredFormat: "hex"
  });
});
```

![Spectrum Colorpicker With ShowInput True](https://cdn.hashnode.com/res/hashnode/image/upload/v1686903817443/293c8408-2031-4fb1-92d2-d07816b31e96.png align="center")

Spectrum Colorpicker With ShowInput True

What do we get by doing this? Just a new input field inside the *colorpicker* so that we can give color hex.

Let’s get back to what we were doing.  
OOPS!!! With no change, it is now saying that **“Yes we have changes!!!”**. See the picture below.

![Checking changes with ShowInput true in Spectrum Colorpicker](https://cdn.hashnode.com/res/hashnode/image/upload/v1686903819589/6a75cf52-72b9-4c4b-a5da-60aa061f83ca.png align="center")

Checking changes with ShowInput true in Spectrum Colorpicker

**Demo –** [**Demo to check changes with ShowInput true in Spectrum Colorpicker**](https://jsfiddle.net/taditdash/upzy3ajp/16/)  
So, I have not picked any color, still, it's detecting changes. We will find out the problem in the next paragraph.

## Research

I started research from the Developer tool and debugged the method which is checking the changes. What I found, was very interesting.

![Debugging GetHasChanges Function in Developer Tool](https://cdn.hashnode.com/res/hashnode/image/upload/v1686903821766/3a6fae3a-ca0e-4753-855e-732d9cb5c1a4.png align="left")

Debugging GetHasChanges Function in Developer Tool

So, as you see, it is detecting the change for an input. I, then, found it inside the HTML.

```xml
<input class="sp-input" type="text" spellcheck="false">
```

This is the same input that is inside the *colorpicker*. The problem it detected a change because it does not have a default value in place and the value given to it is the color we provided (**#000**).

## Solution

Have you guessed the solution!!! It’s easy. We just need to provide the default value as the same color value. Thus, it will only detect the change when an actual change is made. The final code looks like below. Highlighted the codes used to assign the default value.

```javascript
$(document).ready(function() {
  $('#colorpicker').spectrum({
    showInput: true,
    preferredFormat: "hex"
  });
 
  $('.sp-container .sp-input').each(function() {
    this.defaultValue = this.value;
  });
});
```

**Demo –** [**Final Demo Detecting Colorpicker Change**](https://jsfiddle.net/taditdash/upzy3ajp/)

## Feedback

I would definitely appreciate it if you give feedback on my blog. If you find it interesting and useful, then please share it with your friends and colleagues.

Thanks for reading, have a nice day!!!