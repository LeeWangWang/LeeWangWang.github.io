---
title: Linux使用常见问题汇总
date: 2022-04-20 09:25:41
permalink: 
categories: Linux
tags: [Linux]
description: 记录自己使用Linux中的任何问题，当作备忘录
copyright: true 
mathjax: true
---

# 1 初次进入Linux系统鼠标不见了

按下ctrl+alt即可切换出鼠标

# 2 Ubuntu 界面太小了（正方形）

右上角点击设置

![img](https://my-typora-photos.oss-cn-beijing.aliyuncs.com/img/202211201050271.png)

选择设备

<img src="https://my-typora-photos.oss-cn-beijing.aliyuncs.com/img/202211201050633.png" alt="img" width="60%;" />

 分辨率切换至1440*900

<img src="https://my-typora-photos.oss-cn-beijing.aliyuncs.com/img/202211201051750.png" alt="img" width="60%;" />

# 3 找不到ubutun的共享文件夹

打开文件夹，进入计算机

<img src="https://my-typora-photos.oss-cn-beijing.aliyuncs.com/img/202211201052925.png" alt="img" width="60%;" />

进入`mnt/hgfs`，该目录下就是共享文件夹的位置

<img src="https://my-typora-photos.oss-cn-beijing.aliyuncs.com/img/202211201052652.png" alt="img" width="60%;" />

在终端中进入直接使用命令

```bash
cd /mnt/hgfs
```



<script type="text/javascript" src="//rf.revolvermaps.com/0/0/8.js?i=58cydkuoizw&amp;m=0&amp;c=ff0000&amp;cr1=ffffff&amp;f=arial&amp;l=33" async="async"></script>
