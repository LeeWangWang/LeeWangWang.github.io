---
title: Linux常用命令
tags: [Linux]
copyright: true
mathjax: true
theme: default
password:
abstract: 文章被加密了, 请输入密码查看.
message: 您好, 这里需要密码.
wrong_pass_message: 抱歉, 这个密码看着不太对, 请再试试.
wrong_hash_message: 抱歉, 这个文章不能被校验, 不过您还是能看看解密后的内容.
date: 2023-03-22 10:04:57
permalink:
categories: 软件使用教程
description: 总结自己用到的所有Linux命令
---

# Linux常用命令

## Linux命令常用技巧

- `Tab`键自动补全
- 连续按两次`Tab`键，给出操作提示
- 使用上下箭头快速调出曾经使用过的命令
- 使用`Clear`命令或者快捷键`Ctrl`+`L`实现清屏

## Linux命令格式

```bash
command [-options] [parameter]
```

> 说明：
>
> - `command`：命令名
> - `[-options]`：选项，可用来对命令进行控制，也可以省略
> - `[parameter]`：传给命令的参数，可以是0个，1个或多个
>
> 注意：
>
> - `[]`代表可选命令名
> - 选项，参数之间需要用空格进行分隔

## 文件目录操作命令

### ls

> 作用：列出当前目录下的文件和文件夹。
>
> 用法：`ls [-al] [dir]`
>
> 说明：
>
> - `-a`：显示所有文件及目录（以`.`开头的隐藏文件也会列出）
> - `-l`：除文件名外，还会讲文件的形态、权限、拥有者、文件大小等详细信息列出
>
> 

### cd

> 作用：切换目录。
>
> 用法：`cd [dirName]`
>
> 说明：
>
> - `~`表示用户的home目录
> - `.`表示当前所在的目录
> - `..`表示当前位置的上级目录

### mkdir

> 作用：创建一个新目录。
>
> 用法：`mkdir[-p] dirName`
>
> 说明：
>
> - `-p`：确保目录名称存在，不存在的就创建一个。通过此选项，可以实现多层目录同时创建

```bash
# 在当前目录下，建立一个名为linuxCast的子目录
mkdir linuxCast

# 在工作目录下的linuxCast目录中建立一个名为test的子目录，若linuxCast目录不存在，则建立一个
mkdir-p linuxCast/test
```

### rmdir

> 作用：删除空目录。
>
> 用法：`rmdir [-p] dirName`
>
> 说明：
>
> - `-p`：当子目录被删除后使父目录为空目录的话，则一并删除

```bash
# 删除名为linuxCast的空目录
rmdir linuxCast

# 删除linuxCast目录中名为test的子目录，若test目录删除后linuxCast目录变为空目录，则也被删除
rmdir -p linuxCast/test

# 删除名称以linuxCast开始的空目录
rmdir linuxCast*
```

### rm

> 作用：删除文件或目录。
>
> 用法：`rm [-rf] name`
>
> 说明：
>
> - `-r`：将目录及目录中所有文件（目录）逐一删除，即递归删除
> - `-f`：无需确认，直接删除
> - `name`：要删除的文件/目录，支持通配符

## 拷贝移动命令

### cp

> 作用：复制文件或目录。
>
> 用法：`cp [-r] source dest`
>
> 说明：
>
> - `-r`：如果复制的是目录需要使用此选项，此时将复制该目录下所有的子目录和文件
> - `source`：要复制的资源（文件/目录）
> - `dest`：要移动到的位置

```bash
# 将hello.txt复制到linuxCast目录中
cp hello.txt linuxCast/

# 将hello.txt复制到当前目录，并改名为hi.txt
cp hello.txt ./ hi.txt

# 将linuxCast目录和目录下所有文件复制到blog目录下
cp -r linuxCast/ ./blog/

# 将linuxCast目录下所有文件复制blog目录下
cp -r linuxCast/* ./blog/
```

### mv

>作用：为文件或目录改名、或将文件或目录移动到其它位置。
>
>用法：`mv source dest`
>
>说明：
>
>- `source`：要移动的资源（文件/目录）
>- `dest`：要移动到的位置

```bash
# 将hello.txt改名为hi.txt
mv hello.txt hi.txt

# 将文件hi.txt移动到blog目录中
mv hi.txt blogl

# 将hi.txt移动到blog目录中，并改名为hello.txt
mv hi.txt blog/hello.txt

# 如果blog目录不存在，将linuxCast目录改名为blog
mv linuxCast/ blogl

# 如果blog目录存在，将linuxCast目录移动到blog目录中
mv linuxCast/ blogl
```

## 文本查看编辑命令

### cat

>作用：查看文件内容。
>
>用法：`cat [-n] fileName`
>
>说明：
>
>* `-n`：由1开始对所有输出的行数编号

```bash
# 查看/etc目录下的profile文件内容
cat /etc/profile

# 查看/etc目录下的profile文件内容，显示行号
cat -n /etc/profile
```

### grep

>作用：在文件中查找指定的字符串。
>
>用法：`grep word fileName`
>
>说明：
>
>- `word：`查找的文本
>- `fileName：`从哪个文件中种找

### find

>作用：在文件系统中查找文件。
>
>用法：`find dirName -option fileName`
>
>说明：
>
>- `dirName`：指定目录
>- `-option`：一般指定`-name`（根据文件名称来查找）
>- `fileName`：可以使用通配符的方式

```bash
# 在所有文件夹下查找helloworld.log文件
find / -name helloworld.log

# 在当前目录及其子目录下查找.java结尾文件
find . -name "*.java"

# 在/linuxCast目录及其子目录下查找.java结尾的文件
find /linuxCast -name "*.java"
```

### vi

>作用：对文件内容进行编辑。
>
>用法：`vi fileName`
>
>说明：
>
>- `vim`是从`vi`发展来的一个功能更加强大的文本编辑工具，在编辑文件时可以对文本内容进行着色，方便我们对文件进行编辑处理，所以实际工作中`vim`更加常用。
>- 要使用`vim`命令，需要我们自己完成安装。可以使用下面的命令来完成安装：`yum install vim`

### vim

>作用：对文件内容进行编辑。
>
>用法：`vim fileName`
>
>说明：
>
>- 在使用vim命令编辑文件时，如果指定的文件存在则直接打开此文件。如果指定的文件不存在则新建文件。
>- vim在进行文本编辑时共分为三种模式，分别是`命令模式`（Command mode），`插入模式`（Insert mode）和`底行模式`（Last line mode）。这三种模式之间可以相互切换。我们在使用vim时一定要注意我们当前所处的是哪种模式。
>
>针对vim中的三种模式说明如下：
>
>1. 命令模式
>    命令模式下可以查看文件内容、移动光标（上下左右箭头、`gg`(开头)、`G`（末尾））
>    通过vim命令打开文件后，默认进入命令模式
>    另外两种模式需要首先进入命令模式，才能进入彼此
>2. 插入模式
>    插入模式下可以对文件内容进行编辑
>    在命令模式下按下[i,a,o]任意一个，可以进入插入模式。进入插入模式后，下方会出现`INSERT`字样
>    在插入模式下按下ESC键，回到命令模式
>3. 底行模式
>    底行模式下可以通过命令对文件内容进行查找、显示行号、退出等操作
>    在命令模式下按下[:,/]任意一个，可以进入底行模式
>    通过 `/` 方式进入底行模式后，可以对文件内容进行查找
>    通过 `:` 方式进入底行模式后，可以输入`wq`（保存并退出）、`q！`（不保存退出）、`set nu`（显示行号）

## 文件压缩、解压命令

### tar

>作用：对文件进行打包、解包、压缩、解压。
>
>用法：`tar [-zcxvf] fileName [files]`
>
>说明：
>
>* 包文件后缀为`.tar`表示只是完成了打包，并没有压缩
>* 包文件后缀为`.tar.gz`表示打包的同时还进行了压缩，也可以用`.tgz`作为简写
>
>- `-z`： 代表的是gzip，通过gzip命令处理文件，gzip可以对文件压缩或者解压
>- `-c`： 代表的是create，即创建新的包文件
>- `-x`： 代表的是extract，实现从包文件中还原文件
>- `-v`： 代表的是verbose，显示命令的执行过程
>- `-f`： 代表的是file，用于指定包文件的名称
>- `c`和`x`是互斥的，解压和压缩不能同时进行

```bash
# 将当前目录下所有文件打包，打包后的文件名为hello.tar
tar -cvf hello.tar ./*

# 将当前目录下所有文件打包并压缩，打包后的文件名为hello.tar.gz
tar -czvf hello.tar.gz ./*

# 将hello.tar.gz中的文件解压缩
tar -zxvf hello.tar.gz
```

### unzip

> 作用：对文件进行解压。
>
> 用法：`zunzip fileName`

## 其它命令

### chmod

>作用：更改文件或目录的权限。
>
>

### chwon

>作用：更改文件或目录的所有者。
>
>

### ssh

>作用：远程登录到另一台计算机。
>
>

### scp

>作用：在计算机之间复制文件。
>
>

### wget

>作用：从Web下载文件。
>
>用法：`wget url [path]`

### curl

>作用：从Web下载文件并显示在终端上。
>
>

<script type="text/javascript" src="//rf.revolvermaps.com/0/0/8.js?i=58cydkuoizw&amp;m=0&amp;c=ff0000&amp;cr1=ffffff&amp;f=arial&amp;l=33" async="async"></script>
