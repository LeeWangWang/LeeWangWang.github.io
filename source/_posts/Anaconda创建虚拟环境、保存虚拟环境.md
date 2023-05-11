---
title: Anaconda创建虚拟环境、保存虚拟环境
date: 2021-10-20 20:58:51
permalink: 
categories: 程序人生
tags: [Anaconda, python]
description: 记录下自己Anaconda创建虚拟环境的步骤
copyright: true 
mathjax: true
---

# 1 查看已经创建的虚拟环境

```bash
conda info --env  或 conda info -e
```

# 2 创建虚拟环境

```bash
conda create -n env_1 python=3.8
```



## 3 进入（激活）虚拟环境

```bash
conda activate env_1
```

# 4 更换国内镜像源

```bash
conda config --add channels https://mirrors.tuna.tsinghua.edu.cn/anaconda/pkgs/free/
```

```bash
conda config --add channels https://mirrors.tuna.tsinghua.edu.cn/anaconda/cloud/conda-forge
```

```bash
conda config --add channels https://mirrors.tuna.tsinghua.edu.cn/anaconda/cloud/msys2/
```

# 5 安装、卸载、更新各种第三方包(3选1)

安装

```bash
pip install numpy==1.17.0
```

```bash
pip3 install numpy==1.17.0
```

```bash
conda install numpy==1.17.0
```

卸载

```bash
conda remove numpy
```

更新

```bash
conda update numpy==1.16.0
```

# 6 激活、退出、删除虚拟环境

激活

```bash
conda active env_1
```

退出

```bash
conda deactivate
```

删除

```bash
conda remove -n env_1 --all
```

# 7 查看虚拟环境信息

查看所有已安装包

```bash
conda list
```

查看配置

```bash
conda config --show
```

# 8 配置Jupyter Notebook

设置jupyter notebook在虚拟环境中运行

```bash
conda install ipykernel
```

```bash
ipython kernel install --user --name=env_1
```

查看安装的内核和位置

```bash
jupyter kernelspec list
```

移除指定kernel

```bash
jupyter kernelspec remove env_1
```

jupyter notebook代码补全功能

安装`Nbextensions`插件

```bash
pip install jupyter_contrib_nbextensions -i https://pypi.tuna.tsinghua.edu.cn/simple
```

```bash
jupyter contrib nbextension install --user --skip-running-check
```

打开Jupyter Notebook

<img src="https://my-typora-photos.oss-cn-beijing.aliyuncs.com/img/202211202127894.png" alt="Jupyter Notebook界面" width="100%;" />

勾选`Hinterland`即可，记得Disable Configuration......

<img src="https://my-typora-photos.oss-cn-beijing.aliyuncs.com/img/202211202129471.png" alt="nbextension界面" width="100%;" />

如果代码补全功能不能用，请执行以下代码

```
conda install jedi==0.17.0
```

把env_1换成自己创建的就行
再打开jupyter notebook新建文件可以看到虚拟环境

# 9 保存虚拟环境

导出`conda`的包，注意是当前环境

```bash
conda env export > test.yaml
```

导出pip的包

```bash
pip freeze > requirements.txt
```

# 10 导入虚拟环境

（1）载入虚拟环境

```bash
conda env create -f test.yaml
```

（2）进入该环境

```bash
conda activate test
```

（3）加载pip包

```bash
pip install -r requirements.txt
```

# 11 安装pytorch

选择合适的版本: https://pytorch.org/get-started/locally/

# 12 检验pytorch是否安装成功

```python
import torch
print(torch.__version__)
print("gpu", torch.cuda.is_available())
```



<script type="text/javascript" src="//rf.revolvermaps.com/0/0/8.js?i=58cydkuoizw&amp;m=0&amp;c=ff0000&amp;cr1=ffffff&amp;f=arial&amp;l=33" async="async"></script>
