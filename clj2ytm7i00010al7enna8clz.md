---
title: "SourceTree Issue: The Mercurial team strongly encourages all users to upgrade to 3.7.3 due to security vulnerability"
datePublished: Fri Jul 22 2016 12:30:18 GMT+0000 (Coordinated Universal Time)
cuid: clj2ytm7i00010al7enna8clz
slug: sourcetree-issue-the-mercurial-team-strongly-encourages-all-users-to-upgrade-to-373-due-to-security-vulnerability
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1686903799740/aceca839-3d82-4638-8366-15716920a744.png
tags: mercurial, git, scm, sourcetree, source-code-management

---

## Introduction

If you see the above issue when you update the [SourceTree](https://www.sourcetreeapp.com/), then follow the steps mentioned below to resolve it. For those who don’t know, it is a free *Git* and *Mercurial* client for *Windows* or *Mac*, which makes source code management easier with a GUI.

## Background

I appreciate how the *SourceTree* team is continuously improving the software and making it more user-friendly. But today, when I updated it to the latest version and opened it again, I saw a weird issue popped up, instead of the *SourceTree* window.

![SourceTree Error](https://cdn.hashnode.com/res/hashnode/image/upload/v1686903794598/b3ca3035-6c73-4c3a-b7cf-95ff19da6e94.png align="center")

The issue is…

`The Mercurial team strongly encourages all users to upgrade to 3.7.3 due to security vulnerability`

## What is Mercurial?

> [Mercurial](https://www.mercurial-scm.org/) is a free, distributed source control management tool. It efficiently handles projects of any size and offers an easy and intuitive interface.

## Problem

The version of the *Mercurial* on your system is old and it has some security vulnerabilities, which they have fixed and updated with the latest version. If we dig more into the upgrade notes, the below is what you will find.

![Mercurial Security Vulnerability Fixes](https://cdn.hashnode.com/res/hashnode/image/upload/v1686903796911/32c0692e-db30-4363-bc66-597f28021eb9.png align="center")

## Solution

Go to [Mercurial Download](https://www.mercurial-scm.org/wiki/Download) Page. Download the latest package according to your system configuration. Now, *SourceTree* should work as expected.

![Mercurial Downloads](https://cdn.hashnode.com/res/hashnode/image/upload/v1686903798516/0af5d3d9-fb87-4959-a32c-9af04e04e7a7.png align="center")