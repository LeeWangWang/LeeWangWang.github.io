---
title: java基础——Java分层架构概念
tags: [Java]
copyright: true
mathjax: true
date: 2019-01-02 14:39:10
permalink:
categories: Java
description:
---

# service是业务层

DAO (Data Access Object) 数据访问

<img src="https://my-typora-photos.oss-cn-beijing.aliyuncs.com/img/202211211440371.png" alt="img" width="40%;" />

**1.JAVA中Action层, Service层 ，modle层 和 Dao层的功能区分？（下面所描述的service层就是biz）**

首先这是现在最基本的分层方式，结合了`SSH`架构。`modle`层就是对应的数据库表的实体类。

`Dao`层是使用了`Hibernate`连接数据库、操作数据库（增删改查）。

以上的Hibernate，Struts，都需要注入到`Spring`的配置文件中，Spring把这些联系起来，成为一个整体

其他答案：

action 是业务层的一部分，是一个管理器 （总开关）（作用是取掉转）（取出前台界面的数据，调用biz方法，转发到下一个action或者页面）模型成（model）一般是实体对象(把现实的的事物变成java中的对象)作用是一暂时存储数据方便持久化（存入数据库或者写入文件）而是 作为一个包裹封装一些数据来在不同的层以及各种java对象中使用   dao是数据访问层  就是用来访问数据库实现数据的持久化（把内存中的数据永久保存到硬盘中）

其他答案：
Action是一个控制器 Dao主要做数据库的交互工作 Modle 是模型存放你的实体类 Biz 做相应的业务逻辑处理  



**2.java中dao层和biz层的区别是什么？（自己百度的结果，不代表本人观点）**

刚学编程的时候，都是在service里直接调用dao，service里面就new一个dao类对象，调用，其他有意义的事没做，也不明白有这个有什么用，参加工作久了以后就会知道，业务才是工作中的重中之重。

我们都知道，标准主流现在的编程方式都是采用`MVC`综合设计模式，`MVC`本身不属于设计模式的一种，它描述的是一种结构，最终目的达到解耦，解耦说的意思是你更改某一层代码，不会影响我其他层代码，如果你会像`spring`这样的框架，你会了解面向接口编程，表示层调用控制层，控制层调用业务层，业务层调用数据访问层。初期也许都是new对象去调用下一层，比如你在业务层new一个`DAO`类的对象，调用`DAO`类方法访问数据库，这样写是不对的因为在业务层中是不应该含有具体对象，最多只能有引用，如果有具体对象存在，就耦合了。当那个对象不存在，我还要修改业务的代码，这不符合逻辑。好比主板上内存坏了，我换内存，没必要连主板一起换。我不用知道内存是哪家生产，不用知道多大容量只要是内存都可以插上这个接口使用。这就是`MVC`的意义。 接下来说你感觉`service`的意义，其实因为你现在做东西分层次不是那么严格，在一个你们做东西业务本身也少，举个最简单的例子，你做一个分页的功能，数据1000条，你20条在一个页，你可以把这个功能写成工具类封装起来，然后在业务层里调用这个封装的方法，这才是业务里真正干得事，只要没访问数据库的，都要在业务里写。

其他优秀答案：

(1)、假设现在你做这个功能会用到user表和权限表，那么你前台的页面访问action，action再去调用用户模块service，用户模块service判断你是操作user表还是权限表，如果你操作的是user表则service的实现类就去调用userDAO。如果是操作的是权限表则调用权限的DAO

(2)、也就是说DAO一定是和数据库的每张表一一对应，而service则不是。明白的没？其实你一个项目个service和一个DAO其实也一样可以操作数据库，只不过那要是表非常多，出问题了，那找起来多麻烦，而且太乱了 。

(3)、好处就是你的整个项目非常系统化，和数据库的表能一致，而且功能模块化，这样以后维护或者改错比较容易，性能也高一些  至于你说的为什么要用service层封装，我认为：一般来说，某一个程序的有些业务流程需要连接数据库，有些不需要与数据库打交道而直接是一些业务处理，这样就需要我们整合起来到service中去，这样可以起到一个更好的开发与维护的作用，同时也是MVC设计模式中model层功能的体现



**3.java中的action是什么，DAO又是什么？**
Action类 是 [ 获得Form表单数据，并处理逻辑的类 ]
DAO(Data Access Object) 是一个接口实现 [ 通过SessionFactory获得操作数据库的会话，并实现一些基本的删除 添加 修改数据，在servlet中更实际化业务操作 ]



**4.什么是Pojo类？**
简单的Java对象（Plain Old Java Objects）实际就是普通JavaBeans,使用POJO名称是为了避免和EJB混淆起来, 而且简称比较直接. 其中有一些属性及其getter setter方法的类,有时可以作为value object或dto(Data Transform Object)来使用.当然,如果你有一个简单的运算属性也是可以的,但不允许有业务方法,也不能携带有connection之类的方法。  



5.pojo类和vo类分别是什么
vo有两种说法,一个是viewObject,一个是valueObject..
	就拿前者来说吧,它只负责封装页面传递过来的数据,这和PO有些不同..
	就拿struts1来说,ActionForm就是一个典型的viewObject. 而valueObject是页面与页面之间的传递时保存值的对象....
	总的来说,PO是最终传给BO以及BO传个DAO的东西,他很多情况下与我们真正的数据库表想对应.
	而viewObject是一个页面上提交后的数据,不一定完全和PO的属性相同.... 



<script type="text/javascript" src="//rf.revolvermaps.com/0/0/8.js?i=58cydkuoizw&amp;m=0&amp;c=ff0000&amp;cr1=ffffff&amp;f=arial&amp;l=33" async="async"></script>
