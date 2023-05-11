---
title: Jupyter Notebook虚拟环境不能自动补全代码
date: 2021-09-27 22:42:45
permalink: 
categories: 教程
tags: [python, Jupyter Notebook]
description: 编程人员还是需要代码自动提示能提高效率
copyright: true 
mathjax: true
---

### 1 安装`Nbextensions`插件

```bash
pip install jupyter_contrib_nbextensions -i https://pypi.tuna.tsinghua.edu.cn/simple
```

```bash
jupyter contrib nbextension install --user --skip-running-check
```

### 2 打开Jupyter Notebook

![image-20221120212749958](https://my-typora-photos.oss-cn-beijing.aliyuncs.com/img/202211202127894.png)

### 3 勾选`Hinterland`即可，记得Disable Configuration......

![image-20221120212913046](https://my-typora-photos.oss-cn-beijing.aliyuncs.com/img/202211202129471.png)

### 4 如果代码补全功能不能用，请执行以下代码

```bash
conda install jedi==0.17.0
```



<script type="text/javascript" src="//rf.revolvermaps.com/0/0/8.js?i=58cydkuoizw&amp;m=0&amp;c=ff0000&amp;cr1=ffffff&amp;f=arial&amp;l=33" async="async"></script>
