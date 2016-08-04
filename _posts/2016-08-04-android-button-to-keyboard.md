---
layout: post
title: 手机硬件按钮映射到GM中虚拟按键的代码
excerpt: "Android手机开发需要了解的Tips。"
category: GMS相关
comments: false
tag:
- GMS
- android
- 开发Tips
---

## 手机硬件按钮映射到GM中虚拟按键的代码

![Nexus](/images/diary_img/nexus_111.png)

按上图：

* 首页 —— 不可以修改（系统用于返回主屏幕）；
* 菜单 —— 键盘的“M”键，即：ord("M")；
* 返回 —— Backspace键，即vk_backspace；
* 搜索 —— Ctrl键，即vk_control；