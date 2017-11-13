---
layout: post
title:  Java_abstract关键字学习总结
date: 2017-10-17
categories: Java语法基础
tages: Java
description: 
---

##abstract 关键字

1. 适用范围(方法)

 * 定义抽象类、抽象方法

[例]：

```java
	public abstract class AbstractDemo {
		public abstract void g();
		public abstract void f();
	}
```

**[注]:**

	1). abstract 方法只能定义在抽象类中。
	
	2). 抽象方法不用实现实际的方法体。

* 继承抽象类：

	1). 普通子类继承抽象父类:

	```java
	public abstract class AbstractDemo {
		public abstract void g();
		public abstract void f();
	}
	class ExtDemo1 extends AbstractDemo {
		public abstract void g(){}
		public abstract void f(){}
	}
	```

	**[注]**：子类必须给出抽象父类的所有抽象方法的方法体。

	2). 使用抽象子类继承抽象父类：

	```java
	public abstract class AbstractDemo {
		public abstract void g();
		public abstract void f();
	}
	abstract class ExtDemo2 extends AbstractDemo {
		public abstract void t();
		public void g(){}
	}
	class ExtDemo3 extends ExtDemo2 {
		public void t(){}
		Public void g(){}
		public void f(){}
	}
	```

	**[注]**抽象子类可以不用给出全部的抽象方法，但会继承父类的抽象方法。


2. 规则和注意事项

	1). 如果抽象类的子类不为抽象类，则子类必须实现父类的所有抽象方法；
	2). 抽象方法或抽象类不能定义为最终的，即abstract不能与final共存；
	3). 抽象方法不能声明为静态的；（前面三点参照赵卓君主编的《Java程序设计》）
	4). 使用abstract关键字时，可以不用刻意记忆与什么共存是违法的，只需要记住abstract的含义是抽象定义类，这个类必须要被继承下去，那么与继承相违背的关键字就要考虑它的正确性。


3. 使用abstract的好处

	1).- 在实际开发中，一开始设计整个功能是，可以不用考虑方法具体如何实现的。
	2).- 与后面的interface关键字一样可以体现出面向对象的多态性。（统一控制）


4. 实例(代码参照《THINKING IN JAVA》)
	* 实现统一控制

```java
	import java.*;

	abstract class Instrument4 {
		int i;//storage allocated for each
		public abstract void play();
		public String what() {
			return "Instrument4";
		}
		public abstract void adjust();
	}

	class Wind4 extends Instrument4 {
		public void play() {
			System.out.println("Wind4.play()");
		}
		public String what() {
			return "Wind4";
		}
		public void adjust() {}
	}

	class Percussion4 extends Instrument4 {
		public void play() {
			System.out.println("Percussion.play()");
		}
		public String what() {
			return "Percussion4";
		}
		public void adjust() {}
	}

	class Stringed4 extends Instrument4 {
		public void play() {
			System.out.println("Stringed4.play()");
		}
		public String what() {
			return "Stringed4";
		}
		public void adjust() {}
	}

	class Bross4 extends Wind4 {
		public void play() {
			System.out.println("Bross.play()");
		}
		public void adjust() {
			System.out.println("Bross4.objust()");
		}
	}

	class Woodwind4 extends Wind4 {
		public void play() {
			System.out.println("Woodwind4.play()");
		}
		public String waht() {
			return "Woodwind4";
		}
	}

	public class Music4 {
		static void tune(Instrument4 i) {
			i.play();
		}
		static void tuneALL(Instrument4[] e) {
			for(int i = 0; i < e.length; i++) {
				tune(e[i]);
			}
		}
		public static void main(String[] args) {
			Instrument4[] orchestra = new Instrument4[5];
			int i = 0;

			orchestra[i++] = new Wind4();
			orchestra[i++] = new Percussion4();
			orchestra[i++] = new Stringed4();
			orchestra[i++] = new Bross4();
			orchestra[i++] = new Woodwind4();
			tuneALL(orchestra);
		}
	}
```
> 输出结果：
>> Wind4.play()
>> Percussion.play()
>> Stringed4.play()
>> Bross.play()
>> Woodwind4.play()
