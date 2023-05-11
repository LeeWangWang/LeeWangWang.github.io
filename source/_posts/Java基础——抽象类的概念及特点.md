---
title: Java基础——抽象类的概念及特点
tags: [Java, 编程语言]
copyright: true
mathjax: true
date: 2018-09-24 10:06:51
permalink:
categories: Java
description: Java基础备忘录
---

**1.如何定义抽象类、抽象方法**

​	abstract关键字修饰

**2.抽象类无法被实例化**

​	因为它不是具体的类。（但是有构造方法）

**3.抽象类有构造方法，是给子类创建对象的**

**4.抽象类中可以定义抽象方法**

​	语法：在方法的修饰列表中添加abstract关键字，并且以“;”结束，不能带有“{}”
​	public abstract void m1();

**5.抽象类中不一定有抽象方法，抽象方法一定在抽象类中**

**6.一个非抽象类继承抽象类，必须将抽象类中的抽象方法覆盖、实现、重写**

**7.抽象类的成员特点：**

​	成员变量：
​		既可以是变量也可以是常量。
​	构造方法：
​		有构造方法，用于子类访问父类数据的初始化。
​	成员方法：
​		抽象类中方法既可以是抽象的，也可以是非抽象方法。
​	在父类中：
​		非抽象方法：子类继承的事情，提高代码的复用性
​		抽象方法：强制要求子类做的事情。

**8.抽象类中注意的问题：**

​	一个类如果没有抽象方法，可以是抽象类，即抽象类中可以完全没有抽象方法。
​	这样类的主要目的就是不让创建该类对象。

**9.abstract关键字不可以与哪些关键字使用。**

* <font color=red><b>private冲突：</b></font>private修饰的成员不能被继承，从而不可以被子类重写，abstract修饰的是要求被重写的。
* <font color=red><b>final冲突：</b></font>final修饰的成员是最终成员，不能被重写，所以冲突，static 无意义；
* <font color=red><b>static冲突：</b></font>static修饰成员用类名可以直接访问，但是abstract修饰成员没有方法体，所以访问没有方法体的成员无意义。

```java
public abstract class Test {
 
	public static void main(String[] args) {
		//抽象类不能被实例化
		//Teat_01 a = new Test_01();
		B b = new C();// A  B  C 
		A a = new B();// A  B
		C c = new C();// A  B  C 
	}
 
	public abstract void m1();
}
 
//父类：A
class A{
	A(){
		System.out.print(" A ");
	}
	
}
 
//子类1：B 继承父类A
class B extends A{
	B(){
		System.out.print(" B ");
	}
}
 
//子类2：C 继承父类B
class C extends B{
	C(){
		System.out.print(" C ");
	}
}
```



<script type="text/javascript" src="//rf.revolvermaps.com/0/0/8.js?i=58cydkuoizw&amp;m=0&amp;c=ff0000&amp;cr1=ffffff&amp;f=arial&amp;l=33" async="async"></script>
