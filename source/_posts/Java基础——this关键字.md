---
title: Java基础——this关键字
tags: [Java, 编程语言]
copyright: true
mathjax: true
date: 2018-09-20 09:56:52
permalink:
categories: Java
description: Java基础备忘录
---

## 1 this是什么？

1. **this是一个引用类型**
2. **在堆中的每一个对象都有this**
3. **this保存内存地址只指向自身**

------

## 2 this能用在什么地方

### 2.1 this可以用在成员方法中

1. **谁去调用这个成员方法，this就代表谁**
2. **this指的就是当前对象（“this.”可以省略）**

```java
public class ThisTest_01 {
	public static void main(String[] args) {
 
		//创建对象
		Employee e1 = new Employee(123,"zhangsan");
		e1.work();
		
		//创建对象
		Employee e2 = new Employee(456,"lisi");
		e2.work();
		e1.m1();
	}
}
 
class Employee{
	//员工编号
	int empno;
	//员工姓名
	String name;
	//C0nstructor(无参数构造方法)
	Employee() {}
	//Constructor(有参数构造方法)
	Employee(int _empno,String _name){
		empno = _empno;
		name = _name;
	}
	
	public void work() {
		//this就是当前对象，谁去调用这个方法，this就代表谁
		//this指的就是当前对象
		//this.可以省略
		System.out.println(this.name + "在工作");
	}
	
	//成员方法
	public void m1() {
		this.m2();
		m2();
	}
	
	//成员方法
	public void m2() {
		System.out.println("Testing");
	}
	
}
```

### 2.2 this可以用在构造方法中

1. **语法：this(实参);**
2. **过程：通过一个构造方法调用另一个构造方法**
3. **目的：代码重用**

```java
public class ThisTest_02 {
	public static void main(String[] args) {
    /*
		//创建对象
		MyDate data1 = new MyDate(2018,8,22);

		System.out.println(data1.year + "年" + data1.month + "月" + data1.day + "日");
		*/
		
		//创建对象
		MyDate t3 = new MyDate();
		System.out.println(t3.year + "年" + t3.month + "月" + t3.day + "日");
	}
}
 
class MyDate{
	
	//Field(属性)
	int year;
	int month;
	int day;
	
	//Constructor(构造方法)
	//需求：在创建日期对象时，默认日期时1970-1-1
	//无参数构造方法
	MyDate() {
		//this(实参)必须处于构造方法的第一行
		this(1970, 1, 1);
		/*
		this.year = 1970;
		this.month = 1;
		this.day = 1;
		*/
	}
	
	//含参数构造方法
	MyDate(int _year,int _month,int _day){
		year = _year;
		month = _month;
		day = _day;
	}
	
}
```

### 2.3 this可以用来区分成员变量和局部变量

```java
public class ThisTest_03 {
 
	public static void main(String[] args) {
		
		//创建对象m1，名字：king
		Manager m1 = new Manager("King");
		
		//创建对象m2
		Manager m2 = new Manager();
		//设置名字：wang
		m2.setName("Wang");
		
		//打印
		System.out.println(m1.getName());
		System.out.println(m2.getName());
	}
 
}
 
//类：经理
class Manager{
	
	//Field
	private String name;
	
	//Constructor
	Manager(){}
	
	Manager(String name) {
		this.name = name;
	}
	
	//Method
	//成员方法：设置名字
	public void setName(String name) {
		this.name = name;
	}
	
	//成员方法：获取名字
	public String getName() {
		return this.name;
	}
	
}
```

### 2.4 this不能用在静态方法中

1. 静态方法的执行不需要Java对象，直接引用类名的方式访问
2. this指当前对象，而静态变量中没有对象

```java
public class ThisTest_04 {
	String str;
	//入口
	public static void main(String[] args) {
		Person.m1();
		//str是成员变量，必须由 引用. 访问
		//错误：
		//System.out.println(str);
		ThisTest_04 tt = new ThisTest_04();
		System.out.println(tt.str);
	}
}
 
class Person{
	
	//Field(属性)
	String name;
	
	//Constructor(无参数构造方法)
	Person() {}
	
	//Constructor(有参数构造方法)
	Person(String name){
		this.name = name;
	}
	
	public static void m1() {
		Person p1 = new Person();
		p1.name = "张三";
		System.out.println(p1.name);
	}
}
```

this();通过一个语法调用另外一个构造方法(代码重用)

this(实参);必须处于构造方法的第一行



<script type="text/javascript" src="//rf.revolvermaps.com/0/0/8.js?i=58cydkuoizw&amp;m=0&amp;c=ff0000&amp;cr1=ffffff&amp;f=arial&amp;l=33" async="async"></script>
