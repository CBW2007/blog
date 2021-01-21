---
title: Codeforces R622(Div.2)A 题解
tags:
  - OI题解
  - Codeforces
categories:
  - OI题解
keywords:
  - Codeforces
  - C++
  - 题解
  - CF622-Div2-A-【Fast Food Restaurant】
description: Codeforces Round #622 (Div. 2) A题【Fast Food Restaurant】动规方式题解
copyright: true
mathjax: false
top: false
comments: true
date: 2020-03-03 14:28:12
---

Codeforces Round #622 (Div. 2) A题【Fast Food Restaurant】题解

> 原题链接：[Problem - A - Codeforces](https://codeforces.com/contest/1313/problem/A)或[CF1313A Fast Food Restaurant - 洛谷 | 计算机科学教育新生态](https://www.luogu.com.cn/problem/CF1313A)

<!--more-->

## 简化题意

一共有3种食物A、B、C，每一种食物可以选至多1个或不选（也就是说要么不拿，要么只拿一个）。现在已知A,B,C各有多少份，在每个人都至少要拿任意一份食物时，问最多能派发给多少人。

## 思路

1. 打表，因为数据范围小，勉勉强强还行
2. 暴力，数据范围小，也比较简单
3. **动规，这也是我们的重头戏**

没错，动规！这道题其实可以看做多维费用背包（没见过的可以去OI-wiki恶补一下：[Link](https://oi-wiki.org/dp/knapsack/#_6)），有3种东西，饭店持有的数量可以看做背包容量，而物品就需要枚举一下所有可能性，最后看最多能选多少物品。

## 代码

```cpp
#include<iostream>
#include<cstring>
using namespace std;
int cost[7][3]={{1,0,0},{0,1,0},{0,0,1},{1,1,0},{1,0,1},{0,1,1},{1,1,1}};//每种可能性各需要每种食物多少个
int dp[20][20][20];
int main()
{
	int t;
	cin>>t;//多组数据
	while (t--)
	{
		memset(dp,0,sizeof(dp));//首先每次清零
		int a,b,c;
		cin>>a>>b>>c;//输入每种食物各有多少个
//		dp[0][0][0]=1;//这个我一开始弄错了，在所有食物一个都没有时不应该有方案
		for (int k=0;k<7;k++)//背包模板
			for (int ai=a;ai>=cost[k][0];ai--)//因为每种食物只能选一次，故倒序（01背包）
				for (int bi=b;bi>=cost[k][1];bi--)
					for (int ci=c;ci>=cost[k][2];ci--)
						dp[ai][bi][ci]=max(dp[ai][bi][ci],dp[ai-cost[k][0]][bi-cost[k][1]][ci-cost[k][2]]+1);//背包动规，懂的自然懂
		cout<<dp[a][b][c]<<endl;//在每种食物数量最多的时候肯定最优啦，输出~
	}
	return 0;
}
```

