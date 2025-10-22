---
title: LG G7 刷机教程
share: "true"
categories:
  - Blog
tags:
  - Blog
  - LG-G7-刷机教程
  - LG
  - esim
  - euicc
  - 刷机
description: LG G7 刷机教程
author: TRG
dir: posts
date: 2025-10-22T03:46:35+08:00
showToc: "true"
ShowReadingTime: "true"
ShowWordCount: "true"
ShowRssButtonInSectionTermList: "true"
UseHugoToc: "true"
---
### **LG 手机刷机指南

推荐使用`冷亦辰官改系统`，不太涉及细节操作，主要为刷机教程总览，细节操作多为引用（若引用失效，自行上网搜索类似教程，也可以逛逛 XDA 论坛）

资源汇总：
- [萤火虫刷机资源汇总](https://www.yhcres.top/02-%E6%89%8B%E6%9C%BA%E5%B9%B3%E6%9D%BF/LG/LG%20G7)：很全的资源，没事可以多逛逛
- [LG G7 ThinQ 123云盘](https://www.123865.com/s/I6y1Td-CcDF3)：LG G7 相关资源

用到的工具：
- 自行下载 `ADB/Fastboot` `9008` `QPST` `LGUP`[工具汇总](https://www.yhcres.top/02-%E6%89%8B%E6%9C%BA%E5%B9%B3%E6%9D%BF/LG/01.LG%E5%88%B7%E6%9C%BA%E5%B7%A5%E5%85%B7/%E5%88%B7%E6%9C%BA%E5%B7%A5%E5%85%B7)

流程大概就是：
- 解锁 bl
- LGUP 刷入 KDZ
- QPST 备份并刷入分区
- Fastboot 刷入冷亦辰 官改系统
- QPST 恢复分区文件
- 进入Recovery， 删除 Data 数据，重启**两次**手机（第一次启动后，可能出现导航栏仅“返回”键可用或状态栏无法下拉的情况，**重启手机**即可解决。）
- 刷入 Magisk 模块，以及 LSPosed 等工具

#### 一、刷机前：准备与检查

在开始刷机之前，请务必完成以下检查步骤：

1.  **开箱录像**
    建议在打开手机包装时录制视频，以备不时之需。

2.  **查询 IMEI**
    *   开机后，在拨号界面输入 `*#06#` 查看手机的 IMEI 码。
    *   将查询到的 IMEI 码记录下来，并粘贴到以下链接的 `=` 后面，然后用浏览器打开进行查询：`https://csmg.lgmobile.com:49002/svc/popup/model_check.jsp?esn=`

3.  **确认机型**
    请确保你的手机**不是**以下版本，因为它们可能无法或难以刷机：
    *   LG V30 (932 版本)
    *   LG G7 (T-Mobile 版本)
    *   大部分日版机型 (部分可刷，但兼容性差)

4.  **检查 BL 锁**
    *   确认手机已经解锁 Bootloader (BL)。通常，已解锁的手机在开机时会显示一个特定的提示动画。
    *   如果未解锁，请前往相关机型论坛查找并遵循解锁教程（简单的话就是进 `fastboot` 电脑运行 `fastboot oem unlock`，详见：[G7刷机保姆级教程(超详细) - 知乎](https://zhuanlan.zhihu.com/p/638748372)）。

---

#### 二、系统刷入

通常有三种格式，对应不同的刷入方法：

*   **TWRP / 卡刷包 (.zip)**
    *   **优点：** 无需电脑。
    *   **方法：** 将刷机包放入手机存储，通过 TWRP 或 OrangeFox Recovery 等第三方恢复模式刷入。

*   **Fastboot 线刷包**
    *   **需要：** 电脑、可靠的数据线、Fastboot 驱动。
    *   **方法：** 让手机进入 Fastboot 模式，然后连接电脑，双击运行刷机脚本（通常是 .bat 文件）。

*   **9008 线刷包**
    *   **系统分区文件操作需要：** 电脑、数据线、QPST 软件、9008 驱动及 elf 分区表文件。
    *   **方法：** 这是一种在手机无法正常启动时的底层救砖方法。
	
-   **Download Mode**
	-   LG 系统自带刷机模式，可以直接 LGUP 刷入 KDZ（注意需要分区完整，不然进不去 Download 模式，这时候需要用 QPST 刷入原来的分区文件）

实际操作：
1. LGUP 刷入 KDZ（系统版本为：[韩版底包G710NO30h_00_OPEN_KR_OP_0930.kdz](https://www.yhcres.top/02-%E6%89%8B%E6%9C%BA%E5%B9%B3%E6%9D%BF/LG/LG%20G7/KDZ-%E6%9C%AA/Android9/G710N)）
2. QPST 备份并刷入分区，注意基带和 abl 的备份！若忘记 [救砖包](https://www.yhcres.top/02-%E6%89%8B%E6%9C%BA%E5%B9%B3%E6%9D%BF/LG/LG%20G7/9008%E6%95%91%E7%A0%96%E5%8C%85) 里有分区备份，刷入即可
   以上内容相关操作教程：[酷安](https://www.coolapk.com/feed/64567424?s=MzkwMDc1ZTExNTE2NjE4ZzY4Zjg4Njgzegi1531&shareUid=22111768&shareFrom=com.coolapk.app_15.3.1)

3. Fastboot 刷入[冷亦辰官改系统](https://www.yhcres.top/02-%E6%89%8B%E6%9C%BA%E5%B9%B3%E6%9D%BF/LG/LG%20G7/%E7%AC%AC%E4%B8%89%E6%96%B9ROM-%E6%9C%AA/%E5%AE%98%E6%94%B9/%E5%86%B7%E4%BA%A6%E8%BE%B0-30h-2022.8.11)：直接下载后解压，运行主文件，按照它的引导操作即可
4. QPST 恢复 abl 分区文件，不然一直卡 fastboot，甚至影响 Download 模式（具体操作参考 2. QPST 相关操作）
5. 进入Recovery， 删除 Data 数据，重启**两次**手机（第一次启动后，可能出现导航栏仅“返回”键可用或状态栏无法下拉的情况，**重启手机**即可解决。）


---


#### 四、性能优化与高级玩法

为了获得更强大的功能和更流畅的体验，可以进行以下高级设置：

1.  **获取 Root 权限**
    推荐使用 Alpha 版 Magisk (阿尔法面具) 配合 Shamiko 模块来隐藏 Root 状态，以兼容更多应用。

2.  **安装 LSPosed 框架**
    安装配套的 LSPosed 框架后，你就可以使用各种强大的 Xposed 模块。

3.  **常用模块推荐**
    *   **救砖模块：** 防止因误操作导致手机变砖。
    *   **快充模块：** 优化充电速度和效率。
    *   **调度模块：** 智能调节 CPU 运行策略，平衡性能与功耗。
    *   **openEUICC**:  EUICC 这类 esim 卡的操作
---

#### 五、官改系统的核心优势

相比 MIUI、Flyme 或类原生等第三方系统，LG 官改系统拥有以下显著优势：

1.  **VoLTE 通话：** 完美支持高清语音通话，而大多数第三方系统无法开启。
2.  **电信支持：** 可以正常使用中国电信网络，第三方系统同样难以支持。
3.  **完整 Hi-Fi 体验：** 能够完全发挥 LG 手机内置独立 DAC 的音质优势，而第三方系统通常只能实现“半残”或无效的 Hi-Fi。
4.  **高稳定性：** 系统 Bug 极少，运行稳定，不会出现第三方系统常见的“睡死”或无故卡在 Fastboot 模式等问题，数据更有保障。
5.  **Quick 按键支持：** 可以自定义机身侧面的独立按键功能，实现一键或双击快速启动应用。
6.  **强大的小窗功能：** 支持同时打开最多 5 个小窗应用并自由缩放。当窗口超过 5 个时，最早打开的会自动缩小为悬浮球，方便随时调用。
7.  **硬件功能最大化：** 完美驱动所有硬件，如 Hi-Fi、2K 屏幕
8.  **更优的续航：** 通过禁用谷歌服务、配合优秀的调度策略和后台管理，官改系统能实现比第三方和类原生系统更长的续航时间。

实际体验的话，esim 沃达丰信号很不错，esim.gg 爱沙尼亚的信号不咋地。官改系统，流畅度，续航都还不错，功能也完整，自带几个主题很不错，总的来说 LG G7 + pdd 小白卡 总共 200 左右，体验 esim 并且可以实现几乎隔离的系统（隐私很不错），超值

---

#### 参考资料：
- [酷安](https://www.coolapk.com/feed/49594277?s=MTY5MDI0NGExNTE2NjE4ZzY4Zjg3ZTkyegi1531&shareUid=22111768&shareFrom=com.coolapk.app_15.3.1)
- [知乎](https://zhuanlan.zhihu.com/p/638748372)
...