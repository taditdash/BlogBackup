---
title: "Demystifying the Deployment of a .NET 6 Application on Windows Server with IIS 🚀"
datePublished: Mon Jul 24 2023 08:51:47 GMT+0000 (Coordinated Universal Time)
cuid: clkgmptfp00050am7eeiy4r3p
slug: demystifying-the-deployment-of-a-net-6-application-on-windows-server-with-iis
cover: https://cdn.hashnode.com/res/hashnode/image/stock/unsplash/rUTpMpG6GEQ/upload/96d1416ffa2521fa5d159e4e515a93d1.jpeg
tags: deployment, iis, web-api, net-60, hosting-bundle

---

# Introduction

📝 Deploying a .NET 6 application on a Windows server with IIS can be a thrilling yet challenging task. In this blog post, we will explore the steps our team followed, the hurdles we encountered, and the solution that ultimately led to success.

Join me on this journey as we unravel the mystery of the elusive *"HTTP Error 500.31 - Failed to load* [*ASP.NET*](http://ASP.NET) *Core runtime." 🕵️‍♂️*

# Deployment Steps 📢

Let's look at the high-level steps that we followed to build and deploy the .NET 6 WebAPI.

## Step 1: Installing the Latest [ASP.NET](http://ASP.NET) Core Hosting Bundle 💻

The first step we took was installing the essential [ASP.NET](http://ASP.NET) Core Hosting bundle from Microsoft Official. At the time of our deployment, .NET 7 was the latest, and we downloaded the bundle from the [link](https://dotnet.microsoft.com/en-us/download/dotnet/7.0).

Take a look at the screenshot below highlighting the Hosting Bundle area.

![Downloading the ASP.NET Core Hosting Bundle 7.0](https://cdn.hashnode.com/res/hashnode/image/upload/v1689754663869/d0933e7d-38e4-4b7a-b17a-571810291d18.png align="center")

## Step 2: Publishing the .NET 6 WebAPI Project 🚀

With the Hosting Bundle installed on our local machine, we proceeded to publish the .NET 6 WebAPI project as a framework-dependent build. This process ensures that the application will run seamlessly on the target server.

Check out the screenshot below to get a glimpse of the publish settings.

![Framework Dependent Deployment Mode .NET](https://cdn.hashnode.com/res/hashnode/image/upload/v1690188163530/ea4bef25-5981-400d-b23c-08a24f1b185e.png align="center")

## Step 3: Moving Artefacts to the Windows Server 📂

Once the build artefacts were generated, we transferred them to the Windows Server, preparing for the deployment process.

## Step 4: IIS Configuration and Application Pool Setup ⚙️

To deploy the application, we followed the typical IIS steps, creating a new Application Pool with the .NET CLR version set to "*No Managed Code*". This configuration is crucial for running .NET Core applications in IIS.

Have a look at the screenshot below for an example of this setup.

![IIS Application Pool No Managed Code](https://cdn.hashnode.com/res/hashnode/image/upload/v1689755585299/d9513c76-9bf1-4b72-83d9-c9fbad8c9742.png align="center")

# Encountering the Mysterious HTTP Error 500.31 ❓

Despite our meticulous preparation, we faced an unexpected roadblock when browsing the application from IIS. The dreaded "HTTP Error 500.31 - Failed to load [ASP.NET](http://ASP.NET) Core runtime" message appeared, leaving us puzzled. The Hosting Bundle installation should have included the necessary runtime, but it seemed unclear why it failed.

Here is the screenshot of the error from the browser.

![HTTP Error 500.31](https://cdn.hashnode.com/res/hashnode/image/upload/v1689755005489/fd0b7c21-ea29-4a8e-ad2b-c2048901bcc3.jpeg align="center")

# Unravelling the Solution 💡

Undeterred, we launched into extensive research and tried various approaches involving the Application Pool and IIS settings, but to no avail. It wasn't until we stumbled upon online discussions about the Hosting Bundle's backward compatibility that we gained a breakthrough.

# The Missing Piece [ASP.NET](http://ASP.NET) Hosting Bundle 6 ✨

After multiple trials and errors, we finally achieved success by installing the [ASP.NET](http://ASP.NET) Hosting Bundle 6. This seemingly simple step proved to be the key that unlocked the solution, resolving the enigmatic HTTP Error 500.31.

![Downloading the ASP.NET Core Hosting Bundle 6.0](https://cdn.hashnode.com/res/hashnode/image/upload/v1689754750906/79c76769-c712-4cb4-8918-6ed96857350c.png align="center")

# Conclusion

Our journey to deploy a .NET 6 application on a Windows Server with IIS was a rollercoaster of challenges and discoveries. By sharing my experiences and uncovering the importance of using the compatible Hosting Bundle, I hope to save you from similar headaches during your own deployments.

# 🌟 Feedback

I'd love to hear your thoughts! Leave a comment below if you found this blog post helpful or if you have any questions.

Happy deploying! 😊