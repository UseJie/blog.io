---
layout: post
title:  java interface
date: 2020-03-12
categories:  Collect
tages: [Collect]
description: 
---

### 在Java9版本中，接口的内容可以有：

* 成员变量其实是常量 格式：

	[public] [static] [final] 数据类型 常量名称 = 数据值;

	注意：
		常量必须进行复制，而且一旦赋值不能改变
		常量名称完全大写，用下划线进行分隔

* 接口中最重要的是抽象方法 格式：

	public abstract 返回类型 方法名(参数列表);

	注意：实现类必须覆盖充血接口所有的抽象方法，除非是虾类是抽象类。

* 从Java 8开始，接口中允许定义默认方法 格式

	[public] default 返回类型 方法名称(参数列表){方法体}

* 从Java 8开始，接口允许定义静态方法 格式

	[public] static 返回类型 方法名称(参数列表){方法体}

注意：应该通过接口名称进行调用，不能通过实现类对象调用接口静态方法

* 从Java 9开始，接口里允许定义私有方法 格式

	private 返回类型 方法名(参数列表){方法体}

	private static 返回类型 方法名(参数列表){方法体}


