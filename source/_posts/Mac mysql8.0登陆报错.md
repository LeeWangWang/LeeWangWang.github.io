---
title: Mac mysql8.0登陆报错
tags: [MySql]
copyright: true
mathjax: true
theme: default
password:
abstract: 文章被加密了, 请输入密码查看.
message: 您好, 这里需要密码.
wrong_pass_message: 抱歉, 这个密码看着不太对, 请再试试.
wrong_hash_message: 抱歉, 这个文章不能被校验, 不过您还是能看看解密后的内容.
date: 2023-03-22 09:02:43
permalink:
categories: 报错解决
description: 总结自己遇到的错误
---

# 1. 登陆mysql报错

启动mysql

```sql
sudo /usr/local/mysql/support-files/mysql.server start
```

终端登陆mysql

```sql
mysql -u root -p
```

发现输入密码后报错了，输了几个密码后还是这样

```sql
% Enter password: 123456
% ERROR 1045 (28000): Access denied for user 'root'@'localhost' (using password: YES)
```

# 2. 停止mysql

终端执行

```
sudo /usr/local/mysql/support-files/mysql.server stop
```

# 3.启动MySql的安全模式

1 终端跳转到bin目录下

```
cd /usr/local/mysql/bin
```

2 执行命令，获取权限

```powershell
sudo su
```

3 输入你电脑的密码

```powershell
Password:123456
```

4 密码输完后会有一个 sh-3.2#

在sh-3.2# 下输入：

```
./mysqld_safe --skip-grant-tables &
```

5 禁止mysql验证，原来停掉的mysql会重新启动

```sql
[1] 2514
sh-3.2# 2023-03-11T12:34:01.6NZ mysqld_safe Logging to '/usr/local/mysql-8.0.32-macos13-x86_64/data/wangwangdeMacBook-Pro.local.err'.
2023-03-11T12:34:01.6NZ mysqld_safe Starting mysqld daemon with databases from /usr/local/mysql-8.0.32-macos13-x86_64/data
```

# 4.开始重置密码

1 原来的终端不动，重新打开一个新的终端，
执行命令跳过验证进入：

```sql
mysql -u -root
```

2 切换到mysql

```sql
use mysql;
```

3 把root的密码改为空

```sql
update user set authentication_string='' where user='root';
```

4 刷新权限

```sql
flush privileges;
```

5 执行命令

```sql
ALTER USER 'root'@'localhost' IDENTIFIED WITH mysql_native_password BY '123456';" 
```

6 退出登录

```sql
exit
```

7 重启mysql后，再重新登陆一下mysql

5.重置完成



<script type="text/javascript" src="//rf.revolvermaps.com/0/0/8.js?i=58cydkuoizw&amp;m=0&amp;c=ff0000&amp;cr1=ffffff&amp;f=arial&amp;l=33" async="async"></script>
