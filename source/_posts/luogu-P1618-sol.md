---
title: 洛谷题解 P1618 【三连击（升级版）】
tags:
  - OI题解
  - 洛谷
categories:
  - OI题解
keywords:
  - OI
  - C++
  - 洛谷P1618【三连击（升级版）】
  - 题解
  - 枚举
description: 洛谷P1618【三连击（升级版）】C++语言的枚举写法
copyright: true
mathjax: true
top: false
comments: true
date: 2018-05-22 08:00:00
---

> 原题链接：[ P1618 三连击（升级版） - 洛谷 | 计算机科学教育新生态](https://www.luogu.com.cn/problem/P1618)

<!--more-->

其实这题挺简单，没做过的先去试试[【P1008】三连击](https://www.luogu.com.cn/problem/P1008)

## 分析

思路与P1008相同。

具体思路：

一、枚举1~999的所有数为第一个数，然后分别乘$a,b,c$。这就省去了三重循环，变为一重，在数据非常大时效果更明显。（其实无需循环至999~~，只是懒得算了而已~~）

二、定义一个数组，记录1~9的使用量。

------------

## 代码

### 1.0版

```cpp
#include<iostream>
#include<cstring>
using namespace std;
int jishu(int n)//统计出现了多少数
{
    int m[10],s=0;
    memset(m,0,sizeof(m));//初始化数组
    while (n!=0)//剥离数字并记录
    {
        m[n%10]++;
        n/=10;
    }
    for (int j=0; j<=9; j++)//记录出现了多少种数字
        if (m[j]>=1) s++;
    return s;
}
int main()
{
    int a,b,c;
    bool o=false;//假设没有找到
    cin>>a>>b>>c;//输入
    for (int i=111; i<=999; i++)//循环
    {
        int x,y,z;
        x=i*a;
        y=i*b;
        z=i*c;
        if (x<=999&&y<=999&&z<=999)//如果三个数均为三位数
    	    if (jishu(x*1000000+y*1000+z)==9)//统计出现了多少数
    	    {
                cout<<x<<" "<<y<<" "<<z<<endl;//输出
                o=true;//我找到了！！！
            }
    }
    if (o==false)//如果没找到
    	cout<<"No!!!";//输出我没找到。
    return 0;
}
```

这个方法只能得60分。为什么呢？看case#1

input：

	1 2 3

answer：

	192 384 576
	219 438 657
	273 546 819
	327 654 981

output:

	192 384 576
	219 438 657
	267 534 801
	273 546 819
	327 654 981

看到267 534 801了吗？是0惹的祸。0本身是不应该算进去的。

### 2.0版

```cpp
#include<iostream>
#include<cstring>
using namespace std;
int jishu(int n)
{
    int m[10],s=0;
    memset(m,0,sizeof(m));
    while (n!=0)
    {
        m[n%10]++;
        n/=10;
    }
    for (int j=1; j<=9; j++)//从1开始
        if (m[j]>=1) s++;
    return s;
}
int main()
{
    int a,b,c;
    bool o=false;
    cin>>a>>b>>c;
    for (int i=111; i<=999; i++)
    {
        int x,y,z;
        x=i*a;
        y=i*b;
        z=i*c;
        if (x<=999&&y<=999&&z<=999)
    	    if (jishu(x*1000000+y*1000+z)==9)
    	    {
                cout<<x<<" "<<y<<" "<<z<<endl;
                o=true;
            }
    }
    if (o==false)
    	cout<<"No!!!";
    return 0;
}
```
总体思路差不多，我就不多说了。可是一提交80了。再看case#5

input:

	123 456 789

answer:

	123 456 789

output:

	（空）

有可能$a,b,c$是多位数啊！应该循环从1就开始

### 3.0版

```cpp
#include<iostream>
#include<cstring>
using namespace std;
int jishu(int n)//统计出现了多少数
{
    int m[10],s=0;
    memset(m,0,sizeof(m));//初始化数组
    while (n!=0)//剥离数字并记录
    {
        m[n%10]++;
        n/=10;
    }
    for (int j=1; j<=9; j++)//记录出现了多少种数字（从1开始！！！）
        if (m[j]>=1) s++;
    return s;
}
int main()
{
    int a,b,c;
    bool o=false;//假设没有找到
    cin>>a>>b>>c;
    for (int i=1; i<=999; i++)//循环（从1开始！！！）
    {
        int x,y,z;
        x=i*a;
        y=i*b;
        z=i*c;
        if (x<=999&&y<=999&&z<=999)//如果三个数均为三位数
    	    if (jishu(x*1000000+y*1000+z)==9)//统计出现了多少种数
    	    {
                cout<<x<<" "<<y<<" "<<z<<endl;
                o=true;//我找到了！！！
            }
    }
    if (o==false)//如果没找到
    	cout<<"No!!!";
    return 0;
}
```

终于AC了！