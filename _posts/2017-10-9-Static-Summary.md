---
layout: post
title: Java_static关键字学习总结
date: 2017-10-9
categories: Java语法基础
tags: Java
description: 
---


# static作用描述

## static关键字可以修饰方法、成员变量、成员常量、代码块。

**[注］：static不能修饰局部变量，具体原因可以从static的内存分配得以区别。**

1. 静态变量
``` java
	class StaticDemo {
		static int m;
		int n;
		char c;
	}
	public class TestStaticDemo {
		public static void main(String[] args) {
			StaticDemo sd1 = new StaticDemo();
			StaticDemo sd2 = new StaticDemo();
		}
	}
```

**在Java虚拟机内部，第一次使用类时初始化该类中的所有静态变量，以后不再初始化。**

2. 静态变量在内存中的表示

``` java
	public class CreditCard {
	  	private double maxOverdraft = 1000; //透支额度
	  	//信用卡账户的属性，表示余额
	  	private double balance = 0;
	  	//向账户中存款，存款金额为amount元
	  	public void deposit(double amount) {
	  		balance = balance + amount;	
	  	}
	 	public boolean withdraw(double amount) {
	  		if(amount <= balance) {
	  			balance = balance - amount;
	  			return turn;
	  		}
	  		else {
	  			return false;
	 	 	}
	  	}
	  	public double getBalance() {
	  		return balance;
	  	} 
	  	public static void main(String[] args) {
	  		System.out.println("susses");
	  	}
	  }
 ```

3. 静态代码块示例

``` java
	  public class StaticBlock {
	  	static {
	  		System.out.println("静态代码块!");
	  	}
	  }
```

4. 静态成员的初始化1

``` java
	  class Pint {
	  	static int npoints;
	  	int x, y;
	  	Point root;
	  }
	  public class TestStaticInit {
	  	public static void main(Sting[] args) {
	  		System.out.println("npoints=" + Point.npoints);
	  		Point p = new Point();
	  		System.out.println("p.x=" + p.x + ", p.y=" + p.y);
	  		System.out.println("p.root=" + p.root);
	  	}
	  }
```

5. 静态成员初始化2

``` java
	  class Insect {
	  	int i = 9;
	  	int j;
	  	Insect() {
	  		prt("i= " + i + ", j=" +j);
	  		j = 39;
	  	}
	  	static int x1 = prt("static Insect x1 initialized");
	  	static int prt(String s) {
	  		System.out.println(s);
	  		return  47;
	  	}
	  }
	  public class Beetle extends Insect {
	  	int k = prt("Beetle.k initialized");
	  	Beetle() {
	  		prt("k= " + k);
	  		prt("j= " + j);
	  	}
	  	static int x2 = prt("static Beetle.x2 initialized");
	  	static int prt(String s) {
	  		System.out.println(s);
	  		return 63;
	  	}
	  	public static void main(String[] args) {
	  		prt("Beetle constructor");
	  		Beetle b = new Beetle();
	  	}
	  }
``` 

   > 值得注意的是本类的静态属性**maxOverdraft**，如果类CreditCard有zhang3和li4两个对象的话，那么**naxOverdraft**  是在该类的内存的公共区。
   > 静态属性占用的内存在公共区，它的改变影响到类的所有对象。这个特性也使得在类的内部定义的常量一般都做成静态的，可节约资源。

6. 在类外部访问某类中的静态变量（常量）的语法格式：
> 类名.成员变量（常量）例如：
>> CrditCard.maxOverdraft;
   
**[注]** : 

* 静态变量和一般的成员变量不同，一个类的所有对象的静态变量在内存中都只有一个存储位置，每个对象的静态变量都指向内存中同一个地址，它在所有的对象之间共享数据。（共享同一个地址空间，并且都可以使用且可以修改。）

* 在面向对象中，使用该关键字修饰的内容表示该内容是隶属于整个类，而不是直接隶属于该类的某一个对象的。

* "对象.成员成员变量"这样的语法格式进行访问是允许的，但不建议使用，因为有一些类无法创建对象。(抽象类)

* static 关键字不能修饰局部变量。局部变量包括普通成员方法和构造方法中声明的变量，或局部语句块中声明的变量。
  
* 静态方法中只能访问静态属性或直接调用静态方法。
