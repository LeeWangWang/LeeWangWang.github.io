---
title: Hexo常见报错
tags: [Hexo]
copyright: true
mathjax: true
theme: default
date: 2022-11-24 10:33:37
permalink:
categories: 教程
description: 记录下自己使用Hexo遇见的所有报错
---

# 1 问题1

Hexo出现`error：spawn failed`错误的解决方法

![image-20221124103531614](https://my-typora-photos.oss-cn-beijing.aliyuncs.com/img/202211241035624.png)

原因：git进行push或者hexo d的时候改变了一些.deploy_git文件下的内容。

解决办法：

## 1.1 解决方法一

删除`.deploy_git`文件夹

执行命令

```
git config --global core.autocrlf false
```

重新执行Hexo命令

```bash
hexo clean
hexo g
hexo d
```

## 1.2 解决方法二

删除`.deploy_git`, `public`两个文件夹

<img src="https://my-typora-photos.oss-cn-beijing.aliyuncs.com/img/202211241036896.png" alt="image-20221124103636360" width="80%;" />

重新执行Hexo命令

```bash
hexo clean
hexo g
hexo d
```



<script type="text/javascript" src="//rf.revolvermaps.com/0/0/8.js?i=58cydkuoizw&amp;m=0&amp;c=ff0000&amp;cr1=ffffff&amp;f=arial&amp;l=33" async="async"></script>
