---
title: Mac Book苹果电脑修改启动台应用程序图标排列
date: 2022-11-08 08:39:43
permalink: 
categories: 教程
tags: [Mac Book, MacOS]
description: Mac Book的图标会过大，页面图标太少，因此自己设置一下
copyright: true 
mathjax: true
---

Mac自带的图标排列比较大，我们想把图标缩小一下

![image-20221124092201788](https://my-typora-photos.oss-cn-beijing.aliyuncs.com/img/202211240922269.png)

 打开终端（terminal）并输入：

### 1、设置图标有多少列

```bash
defaults write com.apple.dock springboard-columns -int 10
```

### 2、设置图标有多少行

```bash
defaults write com.apple.dock springboard-rows -int 8
```

### 3、重置Launchpad,并重启

```bash
defaults write com.apple.dock ResetLaunchPad -bool true;killall Dock
```

### 4、解决电脑重启之后启动台又变回去了，在终端输入以下命令

```bash
rm ~/Library/Application\ Support/Dock/*.db && killall Dock
```

```bash
defaults write com.apple.dock ResetLaunchPad -bool true && killall Dock
```

最后将系统默认的启动台里面的`其他`文件夹名称改一下就行



<script type="text/javascript" src="//rf.revolvermaps.com/0/0/8.js?i=58cydkuoizw&amp;m=0&amp;c=ff0000&amp;cr1=ffffff&amp;f=arial&amp;l=33" async="async"></script>
