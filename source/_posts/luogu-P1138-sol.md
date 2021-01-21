---
title: 洛谷题解 P1138 【第k小整数】
tags:
  - OI题解
  - 洛谷
categories:
  - OI题解
keywords:
  - OI
  - C++
  - 洛谷P1028【第k小整数】
  - 题解
  - set
description: 洛谷P1028【第k小整数】C++语言的STL-set写法
copyright: true
mathjax: false
top: false
comments: true
date: 2019-05-22 20:22:16
---

> 原题链接：[ P1028 第k小整数 - 洛谷 | 计算机科学教育新生态](https://www.luogu.com.cn/problem/P1138)

<!--more-->

**STL大法吼啊！**

## 分析

这道题有两个步骤：排序、去重。

解决这个问题的方法有很多：sort+遍历去重、unique、其他高端数据结构等。我本来想选第一种方法的，后来我突然想起有一种STL可以自动去重+排序，那就是**set**，那岂不是很简单？（美滋滋）~~结果更难了~~

## SET用法解析

需要包含的头文件：

```cpp
#include<set>
```

它的定义方法：

```cpp
set<type> name;
//例子：定义int型，取名为a
set<int> a;
```

我们要用到的函数：

```cpp
iterator begin(); //指向第一个元素的迭代器
iterator end(); //指向最后一个元素的迭代器
pair insert(const type &val); //在集合中插入val元素，并返回指向该元素的迭代器和一个布尔值来说明val是否成功的被插入了
size_type size(); //返回元素数目
```

遍历方法：

```cpp
int cnt=0;//用于记录遍历到第几个了
for (set<int>::iterator i=a.begin();i!=a.end();i++)
{
	cnt++;
	if (cnt==k)//达到终点
		cout<<*i;
}
```

更多STL工具见文末！

## 应用在此题中

首先，我们可以使用`insert`函数用来插入元素。然后使用size来判断元素够不够 k 个，最后按照上文的方法进行遍历即可！

本文代码：

```cpp
#include<iostream>
#include<set>
using namespace std;
set<int> a;//定义集合
int main()
{
	int n,k;
	cin>>n>>k;
	for (int i=1;i<=n;i++)
	{
		int x;
		cin>>x;
		a.insert(x);//插入元素
	}
	if (a.size()>=k)//判断元素数量是否足够
	{
		int cnt=0;//标记遍历到了第几个
		for (set<int>::iterator i=a.begin();i!=a.end();i++)//遍历
		{
			cnt++;
			if (cnt==k)//到达目的地
				cout<<*i;//输出
		}
	}
	else
		cout<<"NO RESULT";//输出无解
	return 0;//完结撒花ヽ(≧∀≦)ﾉ
}
```

附：[c&cppAPI.chm](https://share.weiyun.com/5QK95ED)
