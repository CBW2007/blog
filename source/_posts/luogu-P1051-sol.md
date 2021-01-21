---
title: 洛谷题解 P1051 【谁拿了最多奖学金】
tags:
  - OI题解
  - 洛谷
categories:
  - OI题解
keywords:
  - OI
  - C++
  - 洛谷P1051【谁拿了最多奖学金】
  - 题解
  - 模拟
description: 洛谷P1051【谁拿了最多奖学金】C++语言的不排序写法
copyright: true
mathjax: true
top: false
comments: true
date: 2018-05-28 08:00:00
---

> 原题链接：[ P1051 谁拿了最多奖学金 - 洛谷 | 计算机科学教育新生态](https://www.luogu.com.cn/problem/P1028)

<!--more-->

这题虽然是NOIP2005提高组t1，不过难度甚至连 `普及-` 都不到。此题根本无需STL排序，不知为各位为何大佬都写这么多，我这位蒟蒻的代码只有30多行。

此题只需读一个数据处理一个即可，既省时间，又省内存。代码如下：

```cpp
#include<iostream>//头文件
#include<cstring>
using namespace std;
int main()
{
    int n,maxn=0,ans=0;//maxn为最大奖学金的总数，ans是所有人奖学金的总数
    char s[25];//获得最多奖学金的人的姓名
    cin>>n;
    for (int i=1; i<=n; i++)
    {
        char name[25],tf_s,tf_x;//name姓名，tf_s学生干部，tf_x西部省份学生
        int score_p,score_c,l,money=0;//score_p期末平均成绩，score_c班级评议成绩，money学生奖学金的数量
        cin>>name>>score_p>>score_c>>tf_s>>tf_x>>l;
        if (score_p>80&&l>=1)//期末平均成绩高于80分
            money+=8000;
        if (score_p>85&&score_c>80)//期末平均成绩高于85分，班级评议成绩高于80分
            money+=4000;
        if (score_p>90)//期末平均成绩高于90分
            money+=2000;
        if (score_p>85&&tf_x=='Y')//期末平均成绩高于85分的西部省份学生
            money+=1000;
        if (score_c>80&&tf_s=='Y')//班级评议成绩高于80分的学生干部
            money+=850;
        ans+=money;//总钱数累加
        if (money>max)//如果奖学金最多
        {
            max=money;//最多奖学金数量为当前奖学金
            strcpy(s,name);//复制名字
        }
    }
    cout<<s<<endl<<max<<endl<<ans;//输出
    return 0;
}
```

目测别人的时间复杂度：$O(n log_2 n)$（因为快排） 我的：$O(n)$

目测别人的辅助空间：$O(n)$ 我的：$O(1)$

因为本人还是个新手OIer，发表的题解还有许多不足之处，如果有人指出，本人将虚心接受。