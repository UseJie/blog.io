---
layout: post
title: AndrewNg-ML-Instruction
date: 2018-02-25
categories: blog
tages: [ML]
description: 
---

# Instruction

## 机器学习
  模仿人类大脑的算法。
  机器自己学习
  机器学习的发展归因于网络和自动化技术的快速发展

## Machine Learning definition:

1. Arthur Samud(1959),Machine Learning Field of study that gives computers the ability to learn whitout being explicithy programmed.

2. Tom Mitchell(1998) Well-posed Learning Problem: A computer program is said to learn from experience E with respect to some task T and some performance measure P, if its performance on T, as measured by P, improves with experience "E".

## Machine Learning algorithms:
  - Supervised learning 监督学习
  - Unsupervised learning 非（无）监督学习
  这是最常用的两大类

  - Others: Reinforcenment learning, recommender system.

### Supervised Learning:
 1. 分类问题
 2. 回归问题
 意指要预测一个连续值的输出

### Unspervised Learning:
  1. 聚类算法(离散值)
  没有给出非监督学习的算法一个正确的答案。

### Model Representation:
  Supervised learning: Given the "rigth answer" for each example in the data.
### Regression Problem:
  Predict real-valued output.

### Notation:
    m = Number of traning examples.

    x's = "input" variable/features.
    
    y,s = "output" Variable/"target" variable.
    
    (x,y) --- one traning example.
    
    (x^(i),y^(i)) --- i^th traning example.

<<<<<<< HEAD
```flow

st=>start: Start

e=>end: End
op1=>operation: My Operation|past
op2=>operation: Stuff|current
sub1=>subroutine: My Subroutine|invalid
cond=>condition: Yes 
or No?|approved:>http://www.baidu.com
c2=>condition: Good idea|rejected
io=>inputoutput: catch something...|request

st->op1(right)->cond
cond(yes, right)->c2
cond(no)->sub1(left)->op1
c2(yes)->io->e
c2(no)->op2->e
```

graph LR
    subgraph 例子
    B-->B1[箭头]
    C---C1[无箭头]
    D-->|文字|D1[文字]
    E-.->E1[虚线]
    F==>F1[粗线]
    end
    subgraph 传递的方式
    A[分类]
    A-->A1[有无箭头]
    A-->A2[有无文字]
    A-->A3[线的形状]
    end
    
 
