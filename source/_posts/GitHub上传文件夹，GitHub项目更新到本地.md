---
title: GitHub上传文件夹，GitHub项目更新到本地
date: 2022-05-07 09:50:41
permalink: 
categories: 教程
tags: [GitHub, git]
description: 程序员离不开GitHub，要学会熟练的使用GitHub
copyright: true 
mathjax: true
---

# 1 在Github创建一个项目（设置公开）

# 2. 在本地的文件夹clone改项目

```bash
git clone https://github.com/Github名/项目名
```

<img src="https://my-typora-photos.oss-cn-beijing.aliyuncs.com/img/202211201042111.png" alt="GitHub主界面" width="100%;" />

# 3 Copy文件

将要上传的文件移动到clone下来的文件夹中。

# 4 使用git命令上传

## 4.1 初始化git

```bash
git init
```

## 4.2 添加所有文件到git

```bash
git add .
```

## 4.3 添加提交信息

```bash
git commit -m "提交的信息"
```

## 4.4 上传文件

```bash
git push
```

# 5 更新到本地

## 5.1 查看远程仓库

```bash
git remote -v
```

## 5.2 从远程获取最新版本到本地

```bash
git fetch origin main
```

```bash
git fetch origin master
```

## 5.3 把远程下载下来的代码合并到本地仓库

```bash
git merge origin
```

```bash
git merge master
```

# 6 上传失败

## 6.1 报错信息

```bash
fatal: unable to access 'https://github.com: Failed to connect to github.com port 443 after 21074 ms: Timed out
```

```bash
fatal: unable to access 'https://github.com': LibreSSL SSL_connect: SSL_ERROR_SYSCALL in connection to github.com:443
```

开启了VPN，关闭即可

```bash
git config --global --unset http.proxy
```

```bash
git config --global --unset https.proxy
```

设置代理

```bash
git config --global https.proxy http://127.0.0.1:1080
```

```bash
git config --global https.proxy https://127.0.0.1:1080
```

## 6.2 报错信息

```bash
fatal: unable to access 'https://github.com': OpenSSL SSL_read: Connection was aborted, errno 10053
```

1. 网络不稳定，多尝试几次
2. 更改网络认证设置

```bash
git config http.sslVerify "false"
```



<script type="text/javascript" src="//rf.revolvermaps.com/0/0/8.js?i=58cydkuoizw&amp;m=0&amp;c=ff0000&amp;cr1=ffffff&amp;f=arial&amp;l=33" async="async"></script>
