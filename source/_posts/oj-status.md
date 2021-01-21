---
title: OJ常见评测状态
date: 2018-01-29 08:00:00
tags:
  - OI笔记
  - 小知识
categories:
  - OI笔记
keywords:
  - OI
  - C++
  - OJ
  - 小知识
description: OJ(Online Judge，在线测评系统)中的许多评测状态
copyright: true
mathjax: true
top: false
comments: true
---

> OJ(**O**nline **J**udge，在线测评系统)中有许多评测状态，许多新手都看不懂。今天让我们来看一看一些常用的评测状态。

<!--more-->

<center><b>各种常见评测状态</b></center>

| 英文全拼 | 英文简写 | 中文 | 解释/解决方法 |
| :------: | :------: | :------: | :---------------: |
| Waiting  | WT | （正在）等待 | 你的代码在等待评测 。 |
| Compiling | —— | （正在）编译 | 你的代码正在被编译。 |
| Running/Judging | RU/JU | 正在运行&评测 | 你的代码在运行&评测 。 |
| Accepted | AC | 通过评测 | 你的代码没有问题，已通过评测。 |
| Compile Error | CE | 编译错误 | 你的代码编译错误，请检查语法。 |
| Wrong Answer | WA | 答案错误 | 仅用样例测试的程序不一定正确，一定还有忽略的或没想到的地方。 |
| Presentation Error | PE | 格式错误 | 格式错误。再看一下题目中对格式的要求。 |
| Time Limit Exceeded | TLE | 时间超限 | 时间超出限制。检查一下是否有死循环或更快的方法。 |
| Memory Limit Exceeded | MLE | 内存超限 | 内存超出限制。变量数量可能需要压缩。 |
| Runtime Error | RE | 运行时错误 | 即传说中的崩溃。非法的内存访问，数组越界 等都有可能造成。 |
| Output Limit Exceeded | OLE | 输出超限 | 输出超出限制。你输出的东西太多了。（不常见） |
| Unknown Error | UKE | 未知错误 | 出现未知错误。最玄学的一种。（不常见） |

本地由于编译器与运行环境不同，有可能部分代码会出现“本地通过，提交错误的情况”。