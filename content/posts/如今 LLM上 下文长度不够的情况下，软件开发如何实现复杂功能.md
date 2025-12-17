---
title: 如今 LLM上 下文长度不够的情况下，软件开发如何实现复杂功能
share: "true"
categories:
  - Develop
  - Blog
tags:
  - Blog
  - 软件开发
description: 如今 LLM上 下文长度不够的情况下，软件开发如何实现复杂功能
author: TRG
dir: posts
date: 2025-12-17T11:59:16+08:00
showToc: "true"
ShowReadingTime: "true"
ShowWordCount: "true"
ShowRssButtonInSectionTermList: "true"
UseHugoToc: "true"
---
只适用于 vibe coding  
今天的实践感悟：当下 LLM 的上下文长度不够，并且随着上下文长度的增加会不可避免的降智，很难实现复杂功能（主要是功能如果比较多，且涉及到大量逻辑规划和debug）

解决方案：

1. 自己查阅资料后（心里有这个底），ai生成设计方案，再不断修改
2. 不断迭代代码（不断创建新窗口）

prompt样例：

1. 只是分析而不要修改文件：前后端还有什么不符合设计文档sync_logic.md的地方吗？或者可能存在的错误逻辑,中文回答
    
2. 直接重构代码，修复所有问题，不用考虑迁移问题。前端代码在：./lib，后端代码在：./server
    

注意在每一次迭代中人工审阅它的方案，适当讨论，并优化原来的设计方案

迭代到基本实现设计方案再进行功能测试