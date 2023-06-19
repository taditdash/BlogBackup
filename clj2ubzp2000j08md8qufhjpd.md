---
title: "Unable to Start Debugging on the Web Server. The Web Server is not Configured correctly."
datePublished: Wed Nov 02 2016 12:52:57 GMT+0000 (Coordinated Universal Time)
cuid: clj2ubzp2000j08md8qufhjpd
slug: unable-to-start-debugging-on-the-web-server-the-web-server-is-not-configured-correctly
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1686903787564/bcbbdf50-4a9a-40d3-ab55-17ddc99c3d6e.png
tags: visual-studio, aspnet, web-server, iis, dzone

---

![Visual Studio Error](https://cdn.hashnode.com/res/hashnode/image/upload/v1686903780407/2360634d-468b-4620-80c1-6a3c517ccd4c.png align="center")

## Introduction

This blog is regarding one issue which happened a couple of days back while building a demo app.

## Background

One of the freshers in my company had this issue and I tried to resolve it. The opportunity is huge when you try to put yourself in their boot. They do crazy things and break the application. However, as my tech name is “*BugTrapper*“, so I started my research.

## Problem

Then I found that the application is hosted in IIS with an IP in the binding.

![iis-binding](https://cdn.hashnode.com/res/hashnode/image/upload/v1686903782480/60f7c709-b075-4ebb-8d21-696d1d9022c7.png align="center")

Now, I wanted to check the *Project Url* in the *Project Properties*. This is what I saw.

![project-properties](https://cdn.hashnode.com/res/hashnode/image/upload/v1686903784568/e7f5d433-e4e2-4968-a6e9-b4fb29183ce9.png align="left")

So, it’s obvious now. The problem is the URL mismatch.

## Solution

I just updated the *Project Url* to the IP mentioned in IIS. Voila!!! All started working at the next moment.

## Have you ever Faced This?

If yes, please comment below. Let’s discuss this. Like and share if you want to save someone’s time. 😃