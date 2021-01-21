---
title: Codeforces R624(Div.3)A 题解
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
  - CF624-Div3-A-【Add Odd or Subtract Even】
description: Codeforces Round #624 (Div. 3) A题【Add Odd or Subtract Even】题解
copyright: true
mathjax: true
top: false
comments: true
date: 2020-03-06 20:41:05
---

Codeforces Round #624 (Div. 3) A题【Add Odd or Subtract Even】题解

> 原题链接：[Problem - 1311A - Codeforces](https://codeforces.com/problemset/problem/1311/A)或[CF1311A Add Odd or Subtract Even - 洛谷 | 计算机科学教育新生态](https://www.luogu.com.cn/problem/CF1311A)

<!--more-->

咱们先稍微转一下，加上正奇数就改变了一个数的奇偶性，反之不变；而差为奇数说明两个数之间奇偶性不同，反之相同；另外，由于每次操作数字不限制，要多少有多少，所以我们的问题只剩下奇偶性问题。

再理一下情况：（有个typo，请见谅，如果无法加载请[手动观看](https://cdn.luogu.com.cn/upload/image_hosting/rbfx9ai7.png)）

![](https://cdn.luogu.com.cn/upload/image_hosting/rbfx9ai7.png)

1. 这还用说嘛
2. 因为减法操作不会改变奇偶性，然而两数奇偶性不同，就要先把a减到$b-1$（$b-1$与a奇偶性相同，其实不一定减1，减任意一个奇数都行），再加个1（减多少，加多少）
3. 因为减法操作不会改变奇偶性，而且两数奇偶性相同，就直接把a减到b
4. 因为加法操作会改变奇偶性，而且两数奇偶性不同，就直接把a加到b
5. 因为加法操作会改变奇偶性，而加到b以上后两数之差为奇数，可是只能减偶数，无解

怎么样，是不是像极了数学里令人~~作呕~~着迷的分类讨论呢？

最后，上核心代码！

```cpp
if (a==b)
	cout<<0;
else if (a<b)
{
	if ((b-a)%2==0)
//		cout<<2; 这里一开始没考虑到无解，但是AC了o_O，大家自己改一改吧
	else
		cout<<1;
}
else /*(a>b)*/
{
	if ((b-a)%2==0)
		cout<<1;
	else
		cout<<2;
}
cout<<endl;//最后统一换行，减少码量
```

