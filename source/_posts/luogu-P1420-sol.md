---
title: 洛谷题解 P1420 【最长连号】
tags:
  - OI题解
  - 洛谷
  - 精品文章
categories:
  - OI题解
keywords:
  - OI
  - C++
  - 洛谷P1420【数的计算】
  - 题解
description: 洛谷P1420【数的计算】C++语言的不用数组写法
copyright: true
mathjax: false
top: false
comments: true
date: 2018-07-27 08:00:00
---

> 原题链接：[ P1420 数的计算 - 洛谷 | 计算机科学教育新生态](https://www.luogu.com.cn/problem/P1420)

<!--more-->

此题其实不用数组也能通过，只不过稍微有些难理解。

定义两个变量a,b。其中，a表示上一个数，b表示新读入的数。

按样例来说，a,b的交替是这样的：

	10
	3 5 6 2 3 4 5 6 8 9

|  i   |  1   |  2   |  3   |  4   |  5   |  6   |  7   |  8   |  9   |  10  |
| :--: | :--: | :--: | :--: | :--: | :--: | :--: | :--: | :--: | :--: | :--: |
|  a   |  3   |  3   |  5   |  6   |  2   |  3   |  4   |  5   |  6   |  8   |
|  b   |      |  5   |  6   |  2   |  3   |  4   |  5   |  6   |  8   |  9   |

代码如下：

```cpp
#include<iostream>
using namespace std;
int main()
{
    int n,a,b,s=1,maxn=0;//s代表当前连续长度，默认为1（因为第一个自己也算一个）；maxn代表最大连续长度。
    cin>>n;
    cin>>a;//输入第一个数
    for (int i=2; i<=n; i++)//注意从第二个数开始，因为第一个已读过
    {
        cin>>b;//输入当前数
        if (b-a==1)//如果与上一个数相差1
            s++;//当前连续长度+1
        else
        {
            if (s>maxn)//如果当前连续长度（不算自己）比最大连续长度长
                maxn=s;//更新最大连续长度
            s=1;//初始化（自己也算一个！）
        }
        a=b;//成为即将的“上一个数”
    }
    cout<<maxn;
    return 0;
}
```