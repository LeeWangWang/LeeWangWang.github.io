---
title: 深度学习使用GPU常见问题
date: 2022-03-23 22:49:07
permalink: 
categories: 深度学习 
tags: [GPU, 深度学习, Linux, python]
description: 记录下自己学习深度学习时在使用GPU进行加速遇到的各种问题
copyright: true 
mathjax: true
---

## 1. Linux查看GPU的使用情况

在终端中输入nvidia-smi命令

<img src="https://my-typora-photos.oss-cn-beijing.aliyuncs.com/img/202211211357715.png" alt="nvidia-smi命令" width="67%;" />

## 2. Linux查看CPU的使用情况

在终端中输入top命令，使用ctrl+c退出

<img src="https://my-typora-photos.oss-cn-beijing.aliyuncs.com/img/202211211358451.png" alt="top命令" width="zoom: 67%;" />

## 3. Linux解压zip压缩文件

使用命令 unzip test.zip

## 4. GPU一般的温度

一般保持在30~60℃是比较安全的，夏天显卡温度多数在50℃-85℃之间也是正常的范围。但是如果长时间保持60℃以上的话会对显卡有损耗。

## 5. GPU利用率低

<img src="https://my-typora-photos.oss-cn-beijing.aliyuncs.com/img/202211211358489.png" alt="GPU利用率" width="67%;" />

很多时候利用GPU进行`深度学习`加速，GPU的利用率才25%左右，加速效果不是很明显，因此我们可以提高Batch_size或者对DataLoder进行切片操作，一次性将更多的数据放入GPU里面。

## 6. 查看使用的GPU信息

```python
if torch.cuda.is_available():
    device = torch.device("cuda")
    print('有 %d 个 GPU(s) 可用' % torch.cuda.device_count())
    print('我们将使用的GPU是:', torch.cuda.get_device_name(0))
else:
    print('没有GPU可用, 使用CPU替代')
    device = torch.device("cpu")
```



<script type="text/javascript" src="//rf.revolvermaps.com/0/0/8.js?i=58cydkuoizw&amp;m=0&amp;c=ff0000&amp;cr1=ffffff&amp;f=arial&amp;l=33" async="async"></script>
