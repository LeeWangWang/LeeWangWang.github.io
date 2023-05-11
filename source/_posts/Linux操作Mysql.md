---
title: Linux操作Mysql
tags: [Linux, Mysql]
copyright: true
mathjax: true
theme: default
password:
abstract: 文章被加密了, 请输入密码查看.
message: 您好, 这里需要密码.
wrong_pass_message: 抱歉, 这个密码看着不太对, 请再试试.
wrong_hash_message: 抱歉, 这个文章不能被校验, 不过您还是能看看解密后的内容.
date: 2023-03-22 18:29:43
permalink:
categories:
description: 总结自己碰到的所有问题，解决办法来自网上。
---

# 卸载Mysql

1.快速删除

```bash
yum remove  mysql mysql-server mysql-libs mysql-server
```

2.查找残留程序

```bash
rpm -qa | grep mysql

rpm -qa | grep mariadb
```

3.删除残留程序

```bash
rpm -e --nodeps mariadb-libs-5.5.68-1.el7.x86_64
```

4.查找残留目录

```bash
whereis mysql
```

5.逐条删除目录

```
rm –rf /usr/local/mysql
```

# 安装Mysql

1.先创建要解压到的目录

```bash
mkdir /usr/local/mysql
```

2.随后解压

```bash
tar -zxvf mysql-5.7.25-1.el7.x86_64.rpm-bundle.tar.gz -C /usr/local/mysql
```

3.按顺序安装rpm包

```bash
rpm -ivh mysql-community-common-5.7.25-1.el7.x86_64.rpm
rpm -ivh mysql-community-libs-5.7.25-1.el7.x86_64.rpm
rpm -ivh mysql-community-devel-5.7.25-1.el7.x86_64.rpm
rpm -ivh mysql-community-libs-compat-5.7.25-1.el7.x86_64.rpm
rpm -ivh mysql-community-client-5.7.25-1.el7.x86_64.rpm
rpm -ivh mysql-community-server-5.7.25-1.el7.x86_64.rpm
```

# 启动mysql

1.查看MySQL服务状态

```bash
systemctl status mysqld
```

2.停止Mysql服务

```bash
systemctl stop mysqld.service
```

3.启动MySQL服务

```bash
systemctl start mysqld
```

查看已经启动的服务

```bash
netstat -tunlp

netstat -tunlp | grep mysql
```

4.查看MySQL进程

```bash
ps -df | grep mysql
```

5.设置开机时自动启动MySQL服务，避免每次开机都要启动MySQL

```bash
systemctl enable mysqld
```

# 登录MySqL

1.查看日志内容中包含password的行信息

```bash
cat /var/log/mysqld.log |grep 'A temporary password is generated'
```

2.根据查询到的密码来登录MySQL

```bash
mysql -uroot -p
```

3.登录成功之后修改密码

- 设置密码长度最低位数

    ```bash
    set global validate_password_length=4;
    ```

- 设置密码安全等级低，便于密码可修改为root

    ```bash
    set global validate_password_policy=LOW;
    ```

- 设置密码为root

    ```
    set password = password('root');
    ```

- 开启访问权限

    ```bash
    grant all on *.* to 'root'@'%' identified by 'root';
    ```

- 刷新权限

    ```bash
    flush privileges;
    ```

4.重启Mysql

```bash
service mysqld restart  
```

# 设置Mysql允许远程连接

1.设置防火墙，允许3306端口通过

2.登录mysql

```bash
mysql -u root -p
```

3.查看mysql库中的user表的host字段

```sql
use mysql;
```

```sql
select user,host from user;
```

4.修改root用户的host字段

```sql
update user set host="%" where user="root";
```

5.使本次修改立即生效

```sql
flush privileges;
```

# 查看当前数据库内容

1.登录mysql

```bash
mysql -u root -p
```

2.显示所有的数据库

```sql
show databases;
```

3.选择数据库

```sql
use xxx;
```

4.显示表

```sql
show tables;
```

5.直接查询语句，显示表数据

```sql
select * from tbl;
```

6.导入sql脚本

```sql
# 选择
mysql>use abc;
# 编码
mysql>set names utf8;
# 导入
mysql>source /usr/abcs.sql;
```



<script type="text/javascript" src="//rf.revolvermaps.com/0/0/8.js?i=58cydkuoizw&amp;m=0&amp;c=ff0000&amp;cr1=ffffff&amp;f=arial&amp;l=33" async="async"></script>
