---
title: 国外 VPS 使用 CDN 加速方案
share: "true"
categories:
  - Blog
tags:
  - Blog
description: 国外 VPS 使用 CDN 加速方案
author: TRG
dir: posts
date: 2025-06-18T02:43:58+08:00
showToc: "true"
ShowReadingTime: "true"
ShowWordCount: "true"
ShowRssButtonInSectionTermList: "true"
UseHugoToc: "true"
---

## 概述

由于多种因素导致国内到国际网络在不使用专线的情况下很糟糕，因此本文主要讲述国外线路不好的 VPS 建站后怎么加速访问

## CDN 简介

首先需要明确套国内 CDN 效果不一定好，如下表所示，例如阿里云 CDN 最后一公里很优秀但是国际回源路径很糟糕，哪怕国内阿里云到国际阿里云节点（猜测不是走内部网络），这导致未命中缓存时回源访问很慢降低总体体验，因此下文也就主要讨论如何加快回源速度

| **路径方向**       | **中文术语**  | **英文术语**          | **描述**                                      |
| -------------- | --------- | ----------------- | ------------------------------------------- |
| **CDN → 源服务器** | **回源路径**  | Origin Fetch Path | CDN 节点发现缓存过期或没有缓存时，返回源头服务器获取数据的路径。          |
| **CDN → 用户**   | **最后一公里** | Last Mile         | CDN 将已经缓存好的内容，从离用户最近的边缘节点发送到用户设备（电脑/手机）的路径。 |


## 解决方案

方案：
- Cloudflare Pro 可以，但是有点贵
- 阿里云 GA 就是优化国际回源路径，很贵
- 线路机中转

Q：加快回源速度 和 国内访问源站 的需求一样，抽象一下就是 流量 出国这一段怎么优化
A：尝试了许多发现还是用线路机中转比较稳定

因为 源 VPS 国际路线也不咋地，所以肯定 `源 VPS <- Cloudflare`
那么加上国外线路机就是 `源 VPS <- Cloudflare <- 中转机 <- 用户`

## 个人实际方案
![CDN.png](/images/CDN.png)

### 注意
#### 中转节点 到 Cloudflare 的 Nginx 代理

我使用的是 `Nginx Proxy Manager`

1. 访问域名直接 DNS 解析到 中转服务器，然后 SSL 直接申请免费证书
2. 注意开启 `SNI`（截图里 `proxy_ssl_server_name on;`） 不然 `Cloudflare 502`
3. 追求速度而不在意缓存，所以关闭了 buffer（即 流式模式），反正 Cloudflare 已经有一层缓存了
4. 然后 Cloudflare 里面开个 中转服务器白名单
![Nginx Proxy Manager.png](/images/Nginx%20Proxy%20Manager.png)
![Cloudflare ip access.png](/images/Cloudflare%20ip%20access.png)


#### Cloudflare 回源

因为已经是国际流量了就不用优选什么的了
直接配置 访问域名 回源到 源站域名（源站开启 Cloudflare 代理优化线路）

![Cloudflare origin.png](/images/Cloudflare%20origin.png)

#### 不想处理端口什么的，统一源服务器转发代理

就是一个域名对应一个服务直接转发到本地对应的端口（注意 docker 部署中 Nginx Proxy Manager转发地址不要填 localhost，图方便我直接填了源 VPS 公网地址）

## 其他方案 & 存在的问题问题

- 用户 → 国内 阿里云 CDN 节点 → 源站 回源线路太慢了  
- 用户 → 国内 阿里云 CDN 节点 → cf优选 → 源站 不知道为什么带宽很小  
- 用户 → 国内 阿里云 CDN 节点 → 国外 阿里云 CDN 节点 → cf优选 → 源站 延迟高，带宽小，猜测阿里云内外流量走的普通线路