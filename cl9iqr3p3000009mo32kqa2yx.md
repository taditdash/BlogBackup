# Add Inline JavaScript and use Variables in Pug

# Background
Recently, I started revamping my personal website and used an opensource template from Github - [startbootstrap-freelancer](https://github.com/StartBootstrap/startbootstrap-freelancer). When I started, I saw an ```index.pug``` file inside the project that is driving the whole HTML. It was new and interesting. I was able to fairly understand and make changes. Let's discuss one of the problems that I faced with it and how I solved it.

# Problem
In my blog, there is a footer where I am showing the current year. Here it is.

![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1666347315021/EwG3iEYDm.png align="left")

However, it was static and I wanted to make it dynamic. Meaning, going forward, no need to modify the HTML again and again. The first thing came to my mind is.

```
new Date().getFullYear();
``` 
Now, the thing is, we just need to take this code and place it at the correct place inside the HTML file templated by the ```index.pug```. 

# Investigation
When I checked the code inside the ```index.pug```, I saw this.
```
// Copyright Section
div.copyright.py-4.text-center.text-white
    .container
        small Copyright &copy; 
        a(href='http://taditdash.com')
            | Tadit Dash
        | 2021
```
Basically, this pug code will generate a division with mentioned classes and then another container division inside it. At last, the two children would be a small Copyright text and an anchor.

Here is the rendered HTML screenshot from the Chrome developer tool.

![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1666356242422/FBLf6J0Tg.png align="left")

Now the challenge is to remove the static 2021 and replace it with the dynamic year from the JavaScript Date Object.

# Solution
Upon searching on the internet I got some answers those talked about including inline JavaScript inside the pug file, however, they did not really talk about how to take one JavaScript variable and display it in the pug.

Let's understand how to include an inline JavaScript block inside the pug file. Very easy! Have a look.
```
script.
    var currentYear = new Date().getFullYear();
```
Notice the dot (.) after ```script```. This is important. If not present, then it will think of ```script``` as an HTML element.

Alright. We get the current dynamic year. Now, we need to display it inside the footer where it is intended. Unfortunately, I could not able to find any straightforward way to directly use this ```currentYear``` variable with any HTML element.

Thus, I tried a different approach. With JavaScript, it will be easy to find an element and push the content inside it. Let's see the updated code.
```
script.
    document.getElementById('year').textContent = new Date().getFullYear();
```
Okay, so just need to declare an element with id ```year```. I have added a ```span```. Let's add that.
```
// Copyright Section
div.copyright.py-4.text-center.text-white
    .container
        small Copyright &copy; 
        a(href='http://taditdash.com')
            | Tadit Dash
        | 
        span#year
```
So, the static year is replaced with a ```span``` with id ```year```. A small thing though. The span is declared on the next line after the bar (|). Otherwise, it will just be regarded as plain text and not an HTML element. 

This magically worked. In case you want to check out my version of the repo, visit - [taditdash/startbootstrap-freelancer](https://github.com/taditdash/startbootstrap-freelancer/)

# Feedback
Your feedback is very important to me. Don't hesitate to comment.

Thanks for reading. Have a nice day! 😍🙌💾
