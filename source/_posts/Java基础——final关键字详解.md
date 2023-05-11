---
title: Java基础——final关键字详解
tags: [Java, 编程语言]
copyright: true
mathjax: true
date: 2018-09-18 09:51:41
permalink:
categories: Java
description: Java基础备忘录
---

Java语言基础之final

* <font color=blue><b>final是一个修饰符，可以修饰类、方法、变量</b></font>
* <font color=blue><b>final修饰的类无法继承</b></font>
* <font color=blue><b>final修饰的方法无法被重写</b></font>
* <font color=blue><b>final修饰的局部变量，一旦赋值，不可再改变</b></font>
* <font color=blue><b>final修饰的成员变量必须手动初始化，或者构造方法完成之前</b></font>
* <font color=blue><b>final修饰的成员变量一般与static联用</b></font>

例：public static final double PI = 3.14;  所有的常量必须大写

其实这样的原因的就是给一些固定的数据起个阅读性较强的名称。

不加 final 修饰不是也可以使用吗？ 那么这个值是一个变量，是可以更改的。加了 final，程序更为严谨。常量名称定义时，有规范，所有字母都大写，如果由多个单词组成，中间用 _连接。

```java
public class A {
	
	final int a;
	
	public A(){
		a = 10;
	}
	
	public final void m1() {
		final int i = 100;
		//不能重新赋值
		//i = 100;
	};
}
/*
class B extends A{
	public void m1();
}
*/
```



<script type="text/javascript" src="//rf.revolvermaps.com/0/0/8.js?i=58cydkuoizw&amp;m=0&amp;c=ff0000&amp;cr1=ffffff&amp;f=arial&amp;l=33" async="async"></script>
