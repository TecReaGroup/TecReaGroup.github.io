---
tags:
  - test
title: test
share: "true"
dir: '"posts"'
---

---
date: "{{date}}" # 创建时间，我这边生成的格式是 YYYY-MM-DDTHH:mm:ssZ-
tags: 
	- 标签1
	- 标签2
title: "{{title}}"
slug: "{{time}}" # 自定义 URL 中文章的访问名称，默认用时间戳填充模板格式为X
share: true  # 配合 Github Publisher插件用的,true表示 obsidian 的文章可以发布
canonicalURL: "" # 之前文章在其他地方被发布的地址，避免搜索引擎重复，设置了该属性会优先展示 canonicalURL 执行的文章
keywords:   # 用于 SEO 优化，也可以不配置该内容默认会使用 tags 的内容
	- 关键字1
	- 关键字2
description: "" # 文章的描述 SEO 优化，为空时默认会截取文章前面的内容
series: "系列" # 系列文章
lastmod:  # 文章最后更新的时间
lang: "cn" # 默认不用写，配置文件会设置默认 cn 中文，en 英文等等
cover:
    image: "" # 文章封面图片地址
author: # 作者名称
dir: "posts" # 搭配 Github Publisher 插件设置文章上传的目录
---


# Test doc

