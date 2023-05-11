---
title: K60学习笔记（2）——无法下载程序（J-Link解锁）
tags: [K60, C语言, 嵌入式]
copyright: true
mathjax: true
date: 2019-03-03 15:37:37
permalink:
categories: 嵌入式
description:
---

K60上锁后是下载不了程序的，因此就需要解锁芯片

上锁原因：

​	1.很可能是占用了Jlink的引脚及：PTA1 - PTA5
​	2.下载线连接不稳定
​	3.Jlink坏了，换一个试试
​	4.电脑驱动版本问题
​	5.IAR软件配置问题

如果Jlink锁了就打开JlinkCommonder，然后按住复位键输入unlock kinetis 回车



<script type="text/javascript" src="//rf.revolvermaps.com/0/0/8.js?i=58cydkuoizw&amp;m=0&amp;c=ff0000&amp;cr1=ffffff&amp;f=arial&amp;l=33" async="async"></script>
