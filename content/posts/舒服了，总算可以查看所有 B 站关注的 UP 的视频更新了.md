---
title: 舒服了，总算可以查看所有 B 站关注的 UP 的视频更新了
share: "true"
categories:
  - Blog
  - Develop
tags:
  - Blog
  - 插件
  - B站
description: 查看所有 B 站关注的 UP 的视频更新
author: TRG
dir: posts
date: 2025-12-18T06:29:22+08:00
showToc: "true"
ShowReadingTime: "true"
ShowWordCount: "true"
ShowRssButtonInSectionTermList: "true"
UseHugoToc: "true"
---

Preview：
![Pasted image 20251218061807.png](/images/Pasted%20image%2020251218061807.png)

插件：[Release 1.4.10 plus · TecReaGroup/BewlyCat](https://github.com/TecReaGroup/BewlyCat/releases/tag/release)
原仓库（已经 PR）：[keleus/BewlyCat: BewlyCat——基于BewlyBewly开发的Bilibili拓展](https://github.com/keleus/BewlyCat)

B 站其实算是简中资源比较优秀了，但是它的推广机制，还有查看关注的 UP 机制和算法很恶心。简单点说就是它只展示小几十个 UP 的更新，但是我关注了不就是为了看它们视频吗？？不推送也就算了，动态里还不给加载完。

所以拓展了一下这个插件，从而实现所有的 UP 更新都可以查看（由于没找到 B 站预留的 UP 最近的视频动态时间的 api，所以直接处理它们的动态，因此降低了访问速率，防止被 BAN, 具体优先级如下）

![Pasted image 20251218062633.png](/images/Pasted%20image%2020251218062633.png)

![Pasted image 20251218062457.png](/images/Pasted%20image%2020251218062457.png)

