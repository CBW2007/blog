---
title: Codeforces R626(Div.2)A 题解
tags:
  - OI题解
  - Codeforces
  - 精品文章
categories:
  - OI题解
keywords:
  - Codeforces
  - C++
  - 题解
  - CF626-Div2-A-【Even Subset Sum Problem】
description: Codeforces Round #626 (Div. 2) A题【Even Subset Sum Problem】题解
copyright: true
mathjax: false
top: false
comments: true
date: 2020-03-10 19:37:45
---

Codeforces Round #626 (Div. 2) A题【Even Subset Sum Problem】题解

> 原题链接：[Problem - 1323A - Codeforces](https://codeforces.com/problemset/problem/1323/A)或[CF1323A Even Subset Sum Problem - 洛谷 | 计算机科学教育新生态](https://www.luogu.com.cn/problem/CF1323A)

<!--more-->

这题还是很水的，跟着题意模拟就行了，但是我在review其他大佬的代码时，发现了一种稍微不一样的思路：

1. 判断数组中有无偶数，有的话就他一个人构成一个子集
2. 如果没有偶数，且数组中只有一个数（此时必为奇数），那么就他一个奇数，怎么也构不成偶数
3. 如果数组由两个及以上的纯奇数组成，**那么随便取两个就好啦**，因为这时数组里只有奇数，奇数+奇数=偶数，为了方便，就固定取前两个

核心代码：

```cpp
int n;
cin>>n;
bool flag=false;
for (int i=1;i<=n;i++)
{
	int ai;
	cin>>ai;
	if (ai%2==0&&!flag)//如果有偶数
	{
		cout<<1<<endl;//当前这个就行了
		cout<<i<<endl;
		flag=true;//标记一下，避免重复
	}
}
if (flag)//避免重复
	continue;
if (n<=1)//无解情况
	cout<<-1<<endl;
else
{
	cout<<2<<endl;//前两个之和必为偶数
	cout<<1<<" "<<2<<endl;
}
```

