---
title: 小白卡教程 以及 BUG：手机设置里禁 sim 卡槽后 EUICC 无法使用解决方法
share: "true"
categories:
  - Blog
tags:
  - Blog
  - esim
  - euicc
description: 小白卡教程 以及 BUG：手机设置里禁 sim 卡槽后 EUICC 无法使用解决方法
author: TRG
dir: posts
date: 2025-10-17T01:26:29+08:00
showToc: "true"
ShowReadingTime: "true"
ShowWordCount: "true"
ShowRssButtonInSectionTermList: "true"
UseHugoToc: "true"
---


## 前言：
我是用的是 PDD EUICC 卡 俗称小白卡，原因只有一个：便宜，才 20 多米（有稍微贵一点的，只是存储大一点，能存更多的卡号，大部分存储都在 几百到几千 KB），缺点：有一些 Bug
使用途径什么的我就不多强调了，主要就是低成本拥有海外号码

## EUICC 简介
AI 总结：
![Pasted image 20251017130124.png](/images/Pasted%20image%2020251017130124.png)

正确情况下安卓插入 EUICC 卡后，直接打开 EasyEuicc，然后写入 esim，就可以启用或者更换 Esim
注意！！！开启 EasyEuicc 设置里面禁止禁用 EUICC 的 sim 卡槽

软件下载地址：
[Releases - PeterCxy/OpenEUICC - Angry.Im Software Forge](https://gitea.angry.im/PeterCxy/OpenEUICC/releases)
## BUG：手机设置里禁 sim 卡槽后 EUICC 无法使用
"So MIUI ** you!"
但说实话，EUICC 也比较新有 BUG 也挺正常的
折腾了一两天，大概原因是因为 MIUI（一加上测试了没有这个 BUG） 或者 安卓 BUG，导致禁 sim 卡槽或者一些其他操作会导致 EUICC 无法读写，卡被锁了
其他 EUICC，像 9esim Xesim ESTK 什么的较新的版本应该是会对这个问题优化，但是比小白卡贵那么多有点不值得了。。。


![Pasted image 20251017131654.png](/images/Pasted%20image%2020251017131654.png)

解决方法：
-  root 手机刷入模块后使用
-  买读卡器电脑上读写

这里介绍第一种解决方法：

1. root 手机 刷入 Magisk 和 LSPosed
2. 刷入 [OpenEUICC_for_Magisk](https://github.com/hzy132/OpenEUICC_for_Magisk/releases/tag/3\(696\)-c74c1f3) 到 Magisk
3. 还是不行的话，刷入 [OMAPI-Bypass](https://github.com/QueallyTech/OMAPI-Bypass/releases) 到 LSPosed 并对 EasyEuicc 启用

打开 EasyEuicc 后就可以看到可以正常使用了，锁解开了，并且别的手机上也可以正常使用

The End：
下一篇博客讲 LG G7 刷机的故事