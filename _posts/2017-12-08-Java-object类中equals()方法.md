---
layout: post
title:  Java_object_equals()
date: 2017-10-17
categories: Java语法基础
tages: [Java]
description: 
---

#object类中的equals():

```java
public boolean equals (object obj){
	return (this == obj);
}
```

  可以看出｀＝＝｀两边的是引用，所以它们是内存地址的比较。看下例代码：

```java
public class Test01 {
	public static void main(String[] args) {
		object o1 = new object();
		object o2 = new object();

		System.out.println(o1.equals(o2));//输出false
	}
} 
```

  所以在实际的开发中我们应该对equals()进行重写，例如String类中的equals()方法已经重写，看下例代码：

```java
//需求：只有当id和名字相同时，才能确定是同一个人
public class Test02 {
	public static void main(String[] args) {
		Stars s1 = new Stars(100, "张敬轩");
		Stars s2 = new Stars(100, "张敬轩");

		System.out.println(s1.equals(s2)); //输出false
		System.out.println(s1.name.equals(s2.name));//输出true                            
	}
}

class Stars {
	int id;
	String name;
	Stars(int id, String name) {
		this.id = id;
		this.name = name;
	}
}
```

