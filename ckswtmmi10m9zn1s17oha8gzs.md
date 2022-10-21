# Do you know that null is an object in JavaScript?

Interesting, isn't it? In JavaScript, `null` is an `object`. Here is the screenshot from _Chrome Developer Tool_.

![JavaScript-null-is-object.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1632410402713/LWPYGKvKv.png)

## Background ◀️
I have started reading *You Don't Know JS* by [Mr. Kyle Simpson](https://github.com/getify) and in [chapter 2](https://github.com/getify/You-Dont-Know-JS/blob/1st-ed/up%20%26%20going/ch2.md), I got to know something interesting about `null` that I wanted to share in a quick blog with all of you.

## Why? 😮

The built-in types available in JavaScript are as follows.

-   `string`
-   `number`
-   `boolean`
-   `null` and `undefined`
-   `object`
-   `symbol`

To know the type of data, we can use one operator called `typeof`. This operator when used with data yields the type of that data. Let's try to find out if we get types correctly for different types of data.

%[https://codepen.io/taditdash/pen/GRoxxGK]

On the CodePen ([https://codepen.io/taditdash/pen/GRoxxGK](https://codepen.io/taditdash/pen/GRoxxGK)) embedded above, it clearly shows an appropriate type for different data types except for `null`. This is weird but true.

Actually, this is a bug and it is like this from the beginning. Now, this can't be fixed as a lot of code is depending on it for a long time. If this is going to be fixed, it will definitely break in legacy apps.

## Let me know! 🙏 

What do you think? Do you think it is a feature or a bug? How have used this as an advantage?

## Stay Updated 📧  📰 

If you enjoyed reading the blog and you would like to see more of such blogs in the future, do _"Subscribe to my newsletter and never miss my upcoming articles"_ that you see here on top of this page.

## Updates 👍

After I posted this blog on social media, I got one reply from one of the most popular Gurus [Mr. Sanjay Vyas](https://twitter.com/SanjayVyas), who is well known for his unique style of teaching with concept visualization. Here is his website - [https://conceptvisuals.in/](https://conceptvisuals.in/)

Here is the screenshot from Twitter.

![Mr.-Sanjav-Vyas-Reply.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1632410629954/8nmseY0FT.png)

This means `null` looks like an object, however, it does not have the characteristics. This brings a lot of value to its implementation where the developer can design the code keeping these caveats in mind.

This is the beauty of the community, where like-minded people share knowledge between themselves. I am very lucky to be a part of the tech community where I am meeting people like Sanjay Sir every day.

Thank you Sanjay Sir and everyone who read this blog. Have a nice day. 😃