---
title: Hexo搭建个人博客
date: 2022-11-19 10:30:32
permalink: 
categories: 教程
tags: [Hexo]
description: 单纯作为自己搭建博客的流程记录
copyright: true 
mathjax: true 
---

# 1 环境安装

## 1.1 安装HomeBrew

使用brew镜像安装脚本

```bash
/bin/bash -c "$(curl -fsSL https://gitee.com/ineo6/homebrew-install/raw/master/install.sh)"
```

可能会有安装提示失败，请自行Google

查看自己的MacBook是否安装brew，执行以下命令

```bash
brew
```

<img src="https://my-typora-photos.oss-cn-beijing.aliyuncs.com/img/202211191043456.png" alt="image-20221119104354687" width="70%;" />

## 1.2 安装Node.js

可以先查看自己的MacBook是否已经安装了Node

```bash
node -v
```

<img src="https://my-typora-photos.oss-cn-beijing.aliyuncs.com/img/202211191046800.png" alt="image-20221119104605289" width="50%;" />

如果没有安装，执行以下命令

```bash
brew install node
```

## 1.3 安装Hexo

可以直接使用node安装hexo，【-g在全局进行安装】

```bash
npm install hexo-cli -g
```

## 1.4 安装git

检查MacBook是否安装git

```bash
git --version
```

<img src="https://my-typora-photos.oss-cn-beijing.aliyuncs.com/img/202211191052572.png" alt="image-20221119105231016" width="50%;" />

如果没有安装，使用brew安装git

```bash
brew install git
```

GitHub账号的创建以及git的配置请自行Google

# 2 使用Hexo

在本地创建一个文件夹，明明为“MyBlog”，在终端里面进入该文件夹

## 2.1 初次使用

1. 初始化目录

```bash
hexo init
```

2. 开启本地服务

```bash
hexo s
```

<img src="https://my-typora-photos.oss-cn-beijing.aliyuncs.com/img/202211191404038.png" alt="image-20221119140403639" width="57%;" />

在浏览器中输入http://localhost:4000/，即可访问博客首页

## 2.2 连接GitHub

打开`_config.yml`文件，修改内容

<img src="https://my-typora-photos.oss-cn-beijing.aliyuncs.com/img/202211191406953.png" alt="image-20221119140651960" width="60%;" />

修改为自己的GitHub链接，密钥如何配置，请自行Google

<img src="https://my-typora-photos.oss-cn-beijing.aliyuncs.com/img/202211191410822.png" alt="image-20221119141039195" width="60%;" />

## 2.3 Hexo新建博客

1. 创建一个新的博客

```bash
hexo new "新博客"
```

2. 在`MyBlogs/source/_posts`中找到`新博客.md`文件，可以编辑内容
3. 清理历史缓存

```bash
heco clean
```

4. 产生静态网页

```bash
hexo g
```

5. 部署到GitHub Page上

```bash
hexo d
```

# 3 Hexo修改主题

使用终端定位到博客文件夹

```bash
git clone -b master https://github.com/jerryc127/hexo-theme-butterfly.git themes/butterfly
```

修改Hexo根目录下的`_config.yml`文件，把主题改为`butterfly`

<img src="https://my-typora-photos.oss-cn-beijing.aliyuncs.com/img/202211191419405.png" alt="image-20221119141937438" width="50%;" />

# 4 Hexo博客配置

## 4.1 Front-**matter**

Front-matter 是 markdown 文件最上方以 --- 分隔的区域，用于指定个别档案的变数。

* Page Front-matter 用于<font color='orange'>页面</font>配置
* Post Front-matter 用于<font color='orange'>文章页</font>配置

> 如果标注可选的参数，可根据自己需要添加，不用全部都写在markdown里

### 4.1.1 Page Front-matter

```markdown
title:
date:
updated:
type:
comments:
description:
keywords:
top_img:
mathjax:
katex:
aside:
aplayer:
highlight_shrink:
```

| 写法             | 解释                                                         |
| ---------------- | ------------------------------------------------------------ |
| title            | 【必需】页面标题                                             |
| date             | 【必需】页面创建日期                                         |
| type             | 【必需】标签、分类和友情链接三个页面需要配置                 |
| update           | 【可选】页面更新日期                                         |
| description      | 【可选】页面描述                                             |
| keywords         | 【可选】页面关键字                                           |
| comments         | 【可选】显示页面评论模块(默认 true)                          |
| top_img          | 【可选】页面顶部图片                                         |
| mathjax          | 【可选】显示mathjax(当设置mathjax的per_page: false时，才需要配置，默认 false) |
| katex            | 【可选】显示katex(当设置katex的per_page: false时，才需要配置，默认 false) |
| aside            | 【可选】显示侧边栏 (默认 true)                               |
| aplayer          | 【可选】在需要的页面加载aplayer的js和css,请参考`音乐`配置    |
| Highlight_shrink | 【可选】配置代码框是否展开(true/false)(默认为设置中highlight_shrink的配置) |

### 4.1.2 Post Front-matter

```markdown
title:
date:
updated:
tags:
categories:
keywords:
description:
top_img:
comments:
cover:
toc:
toc_number:
toc_style_simple:
copyright:
copyright_author:
copyright_author_href:
copyright_url:
copyright_info:
mathjax:
katex:
aplayer:
highlight_shrink:
aside:
```

| 写法                  | 解释                                                         |
| --------------------- | ------------------------------------------------------------ |
| title                 | 【必需】文章标题                                             |
| date                  | 【必需】文章创建日期                                         |
| updated               | 【可选】文章更新日期                                         |
| tags                  | 【可选】文章标签                                             |
| categories            | 【可选】文章分类                                             |
| keywords              | 【可选】文章关键字                                           |
| description           | 【可选】文章描述                                             |
| Top_img               | 【可选】文章顶部图片                                         |
| cover                 | 【可选】文章缩略图(如果没有设置top_img,文章页顶部将显示缩略图，可设为false/图片地址/留空) |
| comments              | 【可选】显示文章评论模块(默认 true)                          |
| toc                   | 【可选】显示文章TOC(默认为设置中toc的enable配置)             |
| toc_number            | 【可选】显示toc_number(默认为设置中toc的number配置)          |
| toc_style_simple      | 【可选】显示 toc 简洁模式                                    |
| copyright             | 【可选】显示文章版权模块(默认为设置中post_copyright的enable配置) |
| copyright_auther      | 【可选】文章版权模块的`文章作者`                             |
| copyright_author_href | 【可选】文章版权模块的`文章作者`链接                         |
| copyright_url         | 【可选】文章版权模块的`文章连结`链接                         |
| copyright_info        | 【可选】文章版权模块的`版权声明`文字                         |
| mathjax               | 【可选】显示mathjax(当设置mathjax的per_page: false时，才需要配置，默认 false) |
| katex                 | 【可选】显示katex(当设置katex的per_page: false时，才需要配置，默认 false) |
| aplayer               | 【可选】在需要的页面加载aplayer的js和css,请参考文章下面的音乐 配置 |
| highlight_shrink      | 【可选】配置代码框是否展开(true/false)(默认为设置中highlight_shrink的配置) |
| aside                 | 【可选】显示侧边栏 (默认 true)                               |

## 4.2 Hexo新建博文自定义模版

打开博客文件夹目录下的`scaffolds`文件夹

<img src="https://my-typora-photos.oss-cn-beijing.aliyuncs.com/img/202211202253191.png" alt="Hexo博客文件夹" width="67%;" />

修改`post.md`文件

```markdown
title: {{ title }}  //文章标题
date: {{ date }}    //文章创建时间
permalink:          //文章显示连接
categories:         //文章匪类目录
tags: []            //文章标签，可多个，用，隔开
description:        //文章描述
image:              //自定义的文章摘要图片，只在页面展示，文章内消失
copyright: true     //增加底部的版权信息（需要配置）
```

# 5 官方资料

官网：https://hexo.io/

官方文档：https://hexo.io/docs/

文体中心：https://hexo.io/docs/troubleshooting.html

GitHub：https://github.com/hexojs/hexo/issues



<script type="text/javascript" src="//rf.revolvermaps.com/0/0/8.js?i=58cydkuoizw&amp;m=0&amp;c=ff0000&amp;cr1=ffffff&amp;f=arial&amp;l=33" async="async"></script>

