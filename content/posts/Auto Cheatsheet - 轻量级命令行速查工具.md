---
title: Auto Cheatsheet - 轻量级命令行速查工具
share: "true"
categories:
  - Blog
tags:
  - Blog
  - Develop
  - Command
  - Cheatsheet
description: Auto Cheatsheet 是一个轻量级的桌面应用，专为开发者设计，用于快速查看和管理命令行速查表。通过悬浮球界面，你可以随时随地访问常用命令，无需离开当前工作流程。
author: TRG
dir: posts
date: 2025-11-27T12:32:07+08:00
showToc: "true"
ShowReadingTime: "true"
ShowWordCount: "true"
ShowRssButtonInSectionTermList: "true"
UseHugoToc: "true"
---
**GitHub**: [auto_cheatsheet](https://github.com/TecReaGroup/auto_cheatsheet)
## 项目简介

Auto Cheatsheet 是一个轻量级的桌面应用，专为开发者设计，用于快速查看和管理命令行速查表。通过悬浮球界面，你可以随时随地访问常用命令，无需离开当前工作流程。
<p align = "center">
  <img src="https://github.com/TecReaGroup/auto_cheatsheet/blob/master/asset/images/main_menu.png?raw=true" width="30%" />
  <img src="https://github.com/TecReaGroup/auto_cheatsheet/blob/master/asset/images/svg_viewer.png?raw=true" width="30%" />
</p>
### YAML 文件

LLM 自动生成 YAML 文件，也支持自己编写 YAML 文件，自动生成 SVG 速查表：

```yaml

filename: git_cheatsheet

terminal_title: Git 常用命令

sections:

  - title: 基础操作

    commands:

      - command: git init

        description: 初始化仓库

      - command: git clone <url>

        description: 克隆远程仓库

```


最后感慨一下 `pyside` 写 `UI` 好麻烦啊，怀念 `Flutter` 了