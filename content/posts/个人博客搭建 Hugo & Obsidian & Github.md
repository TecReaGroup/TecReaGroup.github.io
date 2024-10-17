---
title: 个人博客搭建 Hugo & Obsidian & Github
share: "true"
categories:
  - Blog
tags:
  - Blog
  - Hugo
  - Obsidian
  - Github
description: 个人博客搭建记录
author: TRG
dir: posts
date: 2024-10-17T03:21:28+08:00
showToc: "true"
ShowReadingTime: "true"
ShowWordCount: "true"
ShowRssButtonInSectionTermList: "true"
UseHugoToc: "true"
---
主流程:

![Blog Flow.png](/images/Blog%20Flow.png)

笔记软件: [Obsidian]({{< relref "https://obsidian.md" >}}/)
框架: [Hugo](https://gohugo.io/)
主题:  [PaperMod](https://adityatelange.github.io/hugo-PaperMod/) (不同主题可能有不同的配置需求)
远程同步: [Git](https://git-scm.com/)
渲染&发布: Github Action & Github Page
Dns托管: [Cloudflare](https://cloudflare.com/)

## Hugo 安装 & 配置

### 下载

首先在 [Release](https://github.com/gohugoio/hugo/releases) 下载最新版本的 Hugo 压缩包 (Blog 写于 Hugo 0.135.0 版本)
Windows 则选择例如: `hugo_0.135.0_Windows-64bit.zip`

### 安装

下载后解压, 并且选择合适路径和名称

### 添加环境变量

在设置中的 `系统` -> `关于` 进入 `高级系统设置`, 再从 `高级` 中进入 `环境变量`, 在 `Path` 中添加刚才解压 Hugo 所在的路径

### 验证

在命令行中查询 Hugo 版本来验证: (若无特殊说明, Shell 命令默认于 Hugo 创建的项目主文件夹下)

```shell
hugo version
```

### 文件介绍

需要创建缺少的文件
- `content`: 
  - `content/posts`: 用于放博客内容
  - **`content/search.md`**: 用于博客搜索功能
```md
---
title: "Search"
layout: search
---
```
  - **`content/categories/categories.md`**: 用于启用 categories 分类
```md
---
title: "categories"
layout: "categories"
---
```

- `public`: 项目导出的文件
- `static`: 
  - **`static/icon.svg`** 网页图标
- `themes`: 主题
  - `themes/PaperMod`: PaperMod 主题的相关代码
- **`.github/workflows/actions.yaml`**: Github Actions 相关代码, [Hugo Actions 参考参数](https://github.com/TecReaGroup/TecReaGroup.github.io/tree/main/.github/workflows)
- `hugo.yaml`: Hugo 相关配置文件

### 安装 & 配置 主题

参考 [PaperMod](https://adityatelange.github.io/hugo-PaperMod/) 进行配置
注意:

- `buildFuture: true` 防止时区问题导致的渲染问题(发布时间于未来则不渲染)

参考个人配置文件 [Hugo.yaml](https://github.com/TecReaGroup/TecReaGroup.github.io/blob/main/hugo.yaml) (按需要根据自己情况修改):

### 创建文章

创建文章命令:

```shell
hugo new post <name>
```

配置步骤详见: [PaperMod](https://adityatelange.github.io/hugo-PaperMod/)
注意: 

- 时间格式(参考下方代码, 若配置错误, 可能导致渲染失败), 更多信息 [time.Format](https://gohugo.io/functions/time/format/)

参考文章模板 (Obsidian 建议创建相同的模板): 

```md
---
title: 博客介绍
share: "true"
categories:
  - Blog
tags:
  - 介绍
description: 
author: TRG
dir: posts
showToc: "true"
ShowReadingTime: "true"
ShowWordCount: "true"
ShowRssButtonInSectionTermList: "true"
UseHugoToc: "true"
date: 2024-10-16T12:16:04+08:00
---
```

### 测试网页

在博客主文件夹下运行命令: 

```shell
hugo server -D
```

再打开输出的网址即可

## Github 配置

### Github 仓库

创建相应的 Github 仓库, 并且使用 Git 远程连接, 再上传本地 Git 保存后的文件

### 配置 Actions 文件

见[文件介绍](#文件介绍)

### Github Pages 配置

将 Source 选择为 Github Actions


![Enveloppe Github Pages.png](/images/Enveloppe%20Github%20Pages.png)

#### DNS

将自己域名填入 Custom domain, 再在 Cloudflare 中添加以下记录: 

![Cloudflare DNS.png](/images/Cloudflare%20DNS.png)
## Obsidian 安装 & 配置

官网安装 [Obsidian]({{< relref "https://obsidian.md" >}}/)

### 插件 Enveloppe

安装插件: 浏览, 搜索 Enveloppe, 安装即可: 

![Plugin.png](/images/Plugin.png)

配置 Enveloppe 参数: [Enveloppe Config](https://github.com/miaogaolin/obsidian-github-publisher-hugo/blob/main/settings.json)

![Enveloppe Config.png](/images/Enveloppe%20Config.png)

再配置 Github 参数: 

![Enveloppe Github Config.png](/images/Enveloppe%20Github%20Config.png)

写完博客后 `ctrl + p` 打开 Obsidian 的命令再搜索 Enveloppe Refresh ... 相关的命令执行即可将文章远程同步和发布

### Obsidian 参考模板

时间: (注意 Time format)

![Templates Time.png](/images/Templates%20Time.png)

模板 (Templates):

![Templates Property.png](/images/Templates%20Property.png)

使用时点击左侧插入模板即可:

![Templates Insert.png](/images/Templates%20Insert.png)

---
## 参考链接

- [obsidian如何自动发布hugo博客](https://renyili.org/post/obsidian%E5%A6%82%E4%BD%95%E8%87%AA%E5%8A%A8%E5%8F%91%E5%B8%83hugo%E5%8D%9A%E5%AE%A2/)
- [Hugo + GitHub Action，搭建你的博客自动发布系统](https://www.pseudoyu.com/zh/2022/05/29/deploy_your_blog_using_hugo_and_github_action/)
- [使用 Obsidian 免费建个人博客](https://www.printlove.cn/obsidian-blog/)
- [PaperMod](https://adityatelange.github.io/hugo-PaperMod/)