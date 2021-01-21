---
title: 洛谷题解 P1028 【数的计算】
tags:
  - OI题解
  - 洛谷
categories:
  - OI题解
keywords:
  - OI
  - C++
  - 洛谷P1028【数的计算】
  - 题解
  - 记忆化搜索
description: 洛谷P1028【数的计算】C++语言的记忆化搜索写法
copyright: true
mathjax: false
top: false
comments: true
date: 2017-12-24 08:00:00
---

> 原题链接：[ P1028 数的计算 - 洛谷 | 计算机科学教育新生态](https://www.luogu.com.cn/problem/P1028)

<!--more-->

## 分析

一、这题不要想复杂了。这里在做的时候无需再前方加数可以直接传上次加的数进去。

二、作为Unaccepted过的OIer，本人得出一个经验：此题**递归只能拿到25分**（因耗时太长，后面15个点直接RE），所以要记住已计算过的数值。

------------


## 代码
### 方法一:递归
```cpp
#include<iostream>
using namespace std;
int g;//记住有多少数。因为是全局变量，无需赋初值。
void js(int s)
{
    g++;//s本身也算一个数，所以g++
    for (int i=1; i<=s/2; i++)//循环计算
        js(i);
}
int main()
{
    int n;
    cin>>n;
    js(n);
    cout<<g;
    return 0;
}
```
此方法25分。

### 方法二：记忆化搜索

```cpp
    #include<iostream>
    #include<cstring>//memset函数需要
    using namespace std;
    int f[1005];//用数组来记忆
    int js(int s)//“计算”函数
    {
        if (f[s]!=-1)//如果f[s]的值不是-1，表示数s已被计算
            return f[s];//所以直接输出
        int g=1;//g=1是因为s本身也算一个数
        for (int i=1; i<=s/2; i++)//循环计算
            g+=js(i);
        f[s]=g;//记住s的值
        return g;//返回
    }
    int main()
    {
        int n;
        cin>>n;
//        memset(f,-1,sizeof(f));//将f赋初值为-1.
//上面方法较为危险（因为memset是按字节格式化的）
//为了安全起见请使用循环大法，这里不再赘述
        cout<<js(n);
        return 0;
    }
```
此方法满分。

------------

经过讲解是不是很简单呢？