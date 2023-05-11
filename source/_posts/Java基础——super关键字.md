---
title: Java基础——super关键字
tags: [Java, 编程语言]
copyright: true
mathjax: true
date: 2018-09-22 10:02:20
permalink:
categories: Java
description: Java基础备忘录
---

## 1 super关键字的概念

* super不是引用类型，存储的不是内存地址，指向不是父类对象

* super代表的市当前子类对象中的父类型特征

## 2 super什么时候用？

* 子类和父类都有某个数据
* 在子类中访问父类属性时

## 3 super可以用在什么地方？

* 可以用在成员方法中，不能用在静态方法中

* 可以用在构造方法中

super();用在构造方法中

​	语法：super(实参);

如果第一行没有super();或this();系统会默认调用super();

super();和this();只能用在第一行，故不能共存

super();通过子类的构造方法去调用父类的构造方法，不会创建对象

​	作用：给当前子类对象中的父类型特征赋值   

在Java语言中只要创建对象，那么Object中的无参数构造方法一定会被执行

看下面两个例子

例1

创建两个类，通过子类继承父类，在子类中调用父类方法，来观察super();的用法。

1.父类：Account

2.子类：DebitAccount

```java
//“员工”父类：提供方法和属性
class Employee {
	String name = "张三";
	
	public void work() {
		System.out.println("员工在工作!");
	}
}
 
//“经理”子类继承“员工”父类
public class Manager extends Employee{
	
	String name = "李四";
	
	public void work() {
		System.out.println("经理在工作!");
	}
	
	public void m1() {
		work();//经理在工作
		super.work();//员工在工作
		System.out.println(this.name);//李四
		System.out.println(name);//李四
		System.out.println(super.name);//张三
	}
}
 
//测试类，用来测试（super.方法;）的运行结果
public class Test_02 {
	public static void main(String [] args) {
		Manager manager = new Manager();
		manager.m1();
	}
}
 
/*
运行结果：
    经理在工作!
    员工在工作!
    李四
    李四
    张三
*/
```



<script type="text/javascript" src="//rf.revolvermaps.com/0/0/8.js?i=58cydkuoizw&amp;m=0&amp;c=ff0000&amp;cr1=ffffff&amp;f=arial&amp;l=33" async="async"></script>
