---
layout: post
title:  stack and heap
date: 2020-03-12
categories:  Collect
tages: [Collect]
description: 
---

## 前言

这篇文章翻译之：https://www.programmerinterview.com/data-structures/difference-between-stack-and-heap/
主要的原因是一直对堆栈（stack）和堆（heap）的作用和区别，这次主要是通过这篇文章来梳理，并且把它翻译过来，方便以后查看。

## 堆栈和堆之间的区别在哪里？

堆栈和堆的区别会对许多人造成困扰。所以，我们通过列出一系例关于堆栈和堆的Q&A，这对我们理解堆栈和堆很有帮助。

### 堆栈和堆存储在哪里

它们都存储在计算机的RAM（Random Access Memory）中。因为RAM有刷新机制（refresher）和虚拟内存，可以通过这篇文章了解：https://www.programmerinterview.com/index.php/operating-systems/how-virtual-memory-works/

### 线程在堆栈和堆中是怎么交互的？

### 堆栈和堆在多线程中是怎么工作的？

在一个多线程应用中，每一个线程都会有自己的堆栈，但是，所有不同的线程将会共享堆。因为在多线程应用中不同的线程共享堆意味着，线程之间必须进行某种协调，以使它们不会尝试同时访问和操作堆中的同一块内存。

### 一个对象（object）可以被存储在堆栈而不是堆中吗？

是的，一个对象可以被存储在堆栈中。如果在函数内部创建对象而不使用“new”运算符，则它将在堆栈上而不是堆上创建和存储对象。 假设我们有一个名为Member的C++类，我们想为其创建一个对象。 我们还有一个叫做somefunction（）的函数。 代码如下所示：

```c
void somefunction( )
{
/* create an object "m" of class Member
    this will be put on the stack since the 
    "new" keyword is not used, and we are 
   creating the object inside a function
*/
  
  Member m;

} //the object "m" is destroyed once the function ends
```
因此，一旦功能运行完成，即“超出范围”，对象“m”便被销毁。 函数运行完成后，将删除堆栈上用于对象“m”的内存。

如果我们想在一个函数中创建一个在堆上的对象，这既是代码的样子：
```c
void somefunction( )
{
/* create an object "m" of class Member
    this will be put on the heap since the 
    "new" keyword is used, and we are 
   creating the object inside a function
*/
  
  Member* m = new Member( ) ;
  
  /* the object "m" must be deleted
      otherwise a memory leak occurs
  */

  delete m; 
} 
```
在上面的代码中，您可以看到使用“new”关键字在函数内部创建了“m”对象。 这意味着将在堆上创建“m”。 但是，由于“m”是使用“new”关键字创建的，因此这也意味着我们也必须自行删除“ m”对象-否则，我们最终会得到一个内存泄漏。

### 堆栈上的内存与堆上的内存相比能持续多长时间？

一旦函数调用运行完毕，专门为此函数调用创建的堆栈上的所有数据都将被自动删除。堆上的所有数据都将保留在那里，直到由程序员手动将其删除为止。

### 堆栈大小可以增加吗？ 堆的大小可以增加吗？

堆栈设置为固定大小，并且不能超过其固定大小（尽管某些语言的扩展名允许这样做）。因此，如果堆栈上没有足够的空间来处理分配给它的内存，则会发生堆栈溢出。 当调用许多嵌套函数时，或者存在无限递归调用时，通常会发生这种情况。如果heap的当前大小太小无法容纳新的内存，则操作系统可以将更多的内存添加到heap中。这就是heap和stack之间最大的区别之一。（详细的操作系统对内存的分配可以查阅相关计算机系统机构的书，推荐可以看一下深入理解计算机系统结构（CSAPP））。

### 堆栈和堆如何实现？

实现实际上取决于语言，编译器和运行时–堆栈和堆的实现细节始终取决于所使用的语言和编译器而有所不同。但是，总的来说，一种语言中的堆栈和堆用于完成与另一种语言中的堆栈和堆相同的操作。

### 哪个更快-堆栈还是堆？又为什么呢？

堆栈比堆快得多。这是因为在堆栈上分配内存的方式。在堆栈上分配内存就像向上移动堆栈指针一样简单。

### 如何在堆栈和堆上重新分配内存？

当变量超出范围时，堆栈上的数据将自动释放。但是，在C和C++等语言中，程序员必须使用内置关键字之一（例如free，delete或delete []）手动删除堆上存储的数据。其他语言（例如Java和.NET）使用垃圾回收来自动从堆中删除内存，而程序员无需执行任何操作。

### 堆栈和堆可能出什么问题？

如果堆栈内存不足，则称为堆栈溢出–可能导致程序崩溃。堆可能存在碎片问题，当堆上的可用内存存储为不连续（或断开）的块时，就会发生碎片问题-因为已用的内存块位于未使用的内存块之间。当发生过多碎片时，可能无法分配新的内存，因为这样的事实，即使有足够的内存来进行所需的分配，但在一个大块中可能也没有足够的内存来满足所需的内存量。

### 我应该使用哪一个-堆栈还是堆？

对于刚接触编程的人来说，使用堆栈可能是个好主意，因为它比较容易。
因为堆栈很小，所以当您确切知道数据将需要多少内存时，或者如果您知道数据的大小很小时，您可能希望使用它。当您知道您的数据将需要大量内存，或者您不确定需要多少内存（例如动态数组）时，最好使用堆。

