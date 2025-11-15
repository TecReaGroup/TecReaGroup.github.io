---
title: 开发记录 Sticker Share
share: "true"
categories:
  - Develop
tags:
  - Blog
  - Flutter
  - APP
  - Sticker
description: 管理和分享动画贴纸到各种消息平台
author: TRG
dir: posts
date: 2025-11-15T02:58:26+08:00
showToc: "true"
ShowReadingTime: "true"
ShowWordCount: "true"
ShowRssButtonInSectionTermList: "true"
UseHugoToc: "true"
---
Github 地址: [Sticker-Share.](https://github.com/TecReaGroup/Sticker-Share)

Sticker Share：管理和分享动画贴纸到各种消息平台

<p align = "center">

  <img src="wechat.jpg" width="30%" />

  <img src="homeScreen.jpg" width="30%" />

  <img src="wechat.jpg" width="30%" />

</p>

## 说明
Sticker 下载工具：[Telegram Stickers Download](https://github.com/TecReaGroup/telgram_stickers_download)
目前只有安卓端测试过，以下为安卓端具体情况

| App | Status | Notes |
|-----|------|------|
| WeChat | Tested | Send to preview cannot load |
| QQ | Tested | Fully supported |
| Discord | Tested | Fully supported |
| X | Tested | Fully supported |
| Messenger | Tested | Fully supported |
| Telegram | Tested | Automatically converts to image |
| WhatsApp | Untested | To be tested |
| LINE | Untested | To be tested |

## 使用方法
### 管理贴纸包
1. **浏览贴纸包**: 顶部可横向滚动的包选择器
2. **切换贴纸包**: 在主网格上左右滑动导航
3. **标记收藏**: 长按包名称切换收藏状态
4. **筛选收藏**: 点击心形图标仅显示收藏的包

### 分享贴纸
1. **点击贴纸**: 打开分享对话框
2. **选择应用**: 从已安装的消息应用中选择
3. **分享**: 以 GIF 格式分享

感慨：开发基本功能简单，UI/UX 的打磨还是太消耗时间了