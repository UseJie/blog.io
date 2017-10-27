---
layout: post
title:  C_DataStructure_顺序表实现
date: 2017-10-26
categories: C_DataStructure
tages: 顺序表C语言实现
description: 
---

## 顺序表描述

	* 使用到的预定义如下:
	``` c
	#define ElemType int 
	#define OVERERROR 1
	#define status int 
	#define MAXSIZE 100

    * 用C定义一个结构体 `SqList` 里面有表内容和表的长度。代码如下：

    ``` c
    typedef struct SqList {
    	ElemType *elem; //ElemType 是表类型，是预定义类型
    	int length;
    }SqList;

    * 初始化顺序表的函数 InitList()，代码如下:

    ``` c
    status InitList(SqList *L)
    {
    	L->elem = (ElemType *) malloc (sizeof(ElemType) * MAXSIZE);
    	if(!L->elem)
    	{
    		printf("initial error!");
    		exit(OVERERROR);// #define OVERERROR 1
    	}
    	L->length = 0;
    	return 0;
    }
    ** 注：InitList()函数中的参数表不能是 `SqList &L` C语言没有这种用法，这是C＋＋的用法**

    * 往顺序表插入值的函数insertSqList()，代码如下：
    ``` c
    status insertSqList(SqList *L, int i, ElemType e)
    {
    	if(i < 1 || i > L->length - 1) {
			printf("insert address error!");
			exit(OVERERROR);
		}
		if(L -> length >= MAXSIZE) {
			printf("not enougth storage");
			exit(OVERERROR);
		}
		//是否插在首尾
		if(i >= 1 && i <= L -> length -1) {
			for(int k = L -> length; k > i; k--) {
				L->elem[k] = L->elem[k-1];
			}
		}
		L->length++;
		L->elem[i] = e;
    	return 0;
    } 

    * 删除函数DeleteElem()，代码如下：
    ``` c
    status DeleteElem(SqList *L, int i)
    {
    	if(i < 1 || i > L->length - 1) {
			printf("insert address error!");
			exit(OVERERROR);
		}
		if(i >= 1 && i <= L -> length -1) {
			for(int k = i - 1; k <= L->length - 1; k++) {
				L->elem[k] = L->elem[k+1];
			}
		}
		L->length--;

    	return 0;
    }

    * 取值函数GetElem()，代码如下:
    ``` c
    status GetElem(SqList *L, int i)
    {
    	if(i < 1 || i > L->length) {
			printf("get number error!");
			exit(OVERERROR);
		}
		return L->elem[i - 1];
	}

	* 定位函数LocatedElem()，代码如下:
	``` c
	status LocatedElem(SqList *L, ElemType e)
	{
		for(int i = 0; i < L->length; i++) {
			if(L->elem[i] == e) return i;
		}
		//可以用快速排序实现，时间复杂度会有所下降
		return 0;
	}

	＊ 为了方便写多一个打印顺序表函数PrintSqList()，如下：
	``` c
	void PrintSqList(SqList *L)
	{
		for(int i = 0; I < L->length; i++) {
			printf("L->elem[%d] = %d \n", i, L->elem[i]);
		}
	}

	＊ 主函数是用来测试，代码如下：
	``` c
	int main(void)
	{
		SqList L;
		InitList(&L);
		printf("1- initial List sucess!");
		printf("\n2- please input List length:\n");
		scanf("%d", &L.length);
		printf("Start input SqList\n");
		for(int i = 0; i < L.length; i++) {
			printf("please input the NO.%d elem\n", i);
			scanf("%d", &L.elem[i]);
		}
		PrintSqList(&L);
		ElemType e;
		printf("3- insert number e to SqList\n");
		scanf("%d", &e);
		insertSqList(&L, 2, e);
		PrintSqList(&L);
		printf("4- get nunber!\n");
		printf("	please input you want to get number's address!\n");
		int j;
		scanf("%d", &j);
		printf("	the NO.%d address's number is %d\n", j, GetElem(&L, j));
		printf("5- input you want to delete\n");
		scanf("%d", &j);
		DeleteElem(&L, j);
		PrintSqList(&L);
		printf("6- input you want to located number e\n");
		scanf("%d", &j);
		printf("the %d's address is %d\n", j, LocatedElem(&L, j));
		PrintSqList(&L);
		L.elem = NULL;
		free(L.elem);
		return 0; 
		L.elem = NULL;//内存被释放要将将指针指向NULL
	}