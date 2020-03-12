---
layout: post
title:  Collect
date: 2020-03-12
categories:  Collect
tages: [Collect]
description: 
---

##前言
	这篇文章翻译之：https://www.programmerinterview.com/data-structures/difference-between-stack-and-heap/
	主要的原因是一直对堆和栈的作用和区别，这次主要是通过这篇文章来梳理，并且把它翻译过来，方便以后查看。

##stack和heap之间的区别在哪里？
	stack和heap的区别会对许多人造成困扰。所以，我们通过列出一系例关于stack和heap的Q&A，这对我们理解stack和heap很有帮助。

###stack和heap存储在哪里
	它们都存储在计算机的RAM（Random Access Memory）中。因为RAM有刷新机制（refresher）和虚拟内存，可以通过这篇文章了解：https://www.programmerinterview.com/index.php/operating-systems/how-virtual-memory-works/

###线程在stack和heap中是怎么交互的？
###stack和heap在多线程中是怎么工作的？
	在一个多线程应用中，每一个线程都会有自己的stack，但是，所有不同的线程将会共享heap。因为在多线程应用中不同的线程共享heap意味着，线程之间必须进行