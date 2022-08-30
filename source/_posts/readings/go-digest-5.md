---
title: 技术阅读摘要 - 5.Go语言面试概述类问题
date: 2022-08-07 12:00:00
categories: 
- 成长分享
tags:
- Digest
---

## 概览

目前，Go语言在中国市场虽然蓬勃发展，但相较于JAVA语言的成熟面试体系，Go缺少了很多“八股文”性质的资料，出现了两个问题：

1. 对新手来说，知识很难体系化；
2. 对面试者来说，遇到的问题千奇百怪，甚至面试官之间的答案也不一样

那么，我将挑选五个概述类的问题，并给出我的思考，希望能对大家带来帮助。

<!-- more -->

## 1.谈谈你对Go语言的错误处理的思考

```go
if err != nil {
  return err
}
```

在谈论这个话题前，我们最好先掌握两个知识点：

1. 了解以JAVA体系为代表的try-catch模式的错误处理方式
2. Go语言error封装的常见技巧

我们的回答先围绕这两个点展开：

1. Go语言对错误处理的设计是偏向于过程性的。虽然会牺牲一定的简洁性、增加代码冗余，但在阅读代码时，我们能明确地知道，错误是在方法的哪一行产生的；
2. 推荐使用`github.com/pkg/errors`这个Go官方推荐的库（具体方法可以参考 [我的博客](https://junedayday.github.io/2021/05/07/go-tip/go-tip-3/)）。简单来说，将错误进行堆栈化，丰富错误所包含的信息。

关于这个问题，你要谈到的三个关键点是：

1. error处理的代码会导致冗余，牺牲一定的简洁性，但阅读者可以清晰地看到错误产生的源头；
2. 熟悉对error处理的技巧，如`bufio.Scanner`将error封装到结构体中；
3. 官方思路 - 以`github.com/pkg/errors`为代表的，将error进行堆栈化处理；

## 2.谈谈你对Go程序故障的排查心得

线下问题相对简单，可以通过 **单元测试** 或者 **代码调试** 的手段进行排查。

我们讨论的重点是线上程序，我将思路分为3类：

1. 可观测性：重点是监控指标metrics与链路追踪tracing
2. Go语言自带的pprof：主要用来分析复杂的程序瓶颈
3. 操作系统层面的工具：包括CPU、磁盘、网络等，如tracert、tcpdump等

一般情况下，第1类成本最低，能解决绝大部分的问题，是稳定性重点建设的目标。

## 3.你认为Go语言的弊端有什么？

我将从小到大、谈谈Go语言的三个问题（主要与JAVA进行对比）：

1. 基础库：基础库提供的能力比较受限，这就导致大量各异的轮子被发明出来，很难统一；
2. 代码风格：风格迥异，如新手容易写出过程性的代码，资深人员会写出面向接口、高度抽象的代码；
3. 编程框架：业界没有统一的Go框架，框架间思路也差异很大；

总体来说，Go现状依然是百家齐鸣。这对语言的丰富性来说是个好事，但对工程项目来说，很难统一约束，**多样性会导致可维护性变差**。

## 4.如何体现你的Go语言水平

展示Go语言的能力发展分为两个方向：底层与上层。

底层能力包括：源码理解、GMP、性能问题、runtime、编译器等方向，体现出了计算机基础功底。一般来说，在底层这块进一步深钻的话，技术栈需要重点扩充操作系统与网络方向，而编程语言上也需要有一定C++的能力。

上层能力又可以区分为两块：工程化能力与特定业务领域的能力。通俗点说，工程化是怎么写出可维护的、优雅的Go代码，考验的是经验与基本功；特定业务领域能力则是掌握怎么用Go语言的特性或者特定库，去解决对应的领域问题，如云原生、区块链。

## 5.什么样的项目适合用Go语言开发

单从语言来看，任何一门语言都具备可替代性。那么Go语言的核心竞争力是什么呢？我看重的是两点；**业务生态与语言特性**，其中生态的重要性远超语言特性。

先聊一下业务生态。成熟的生态会沉淀相关的工具或现成库，大幅度减少开发成本，逆主流的语言意味着重建生态。比如说，Kubernetes沉淀了Go相关的大量插件与工具，区块链领域也基本都是Go语言的天下。

在没有绝对统治力的生态下、或者重建生态的成本很低，语言自身的特性才有参考价值。比如在devops领域，常见的有Python、Go、PHP，以及少量的JAVA。这时，Go语言以学习成本低、高性能等因素，脱颖而出，成为首选。

## 总结

本文和大家聊了5个Go语言概述类问题，它们相对于底层问题更容易快速记忆。

希望能为大家在学习Go语言的过程中带来启发，也可以帮助大家在面试的回答中展现出亮点。



> Github: https://github.com/Junedayday/code_reading
>
> Blog: http://junes.tech/
>
> Bilibili: https://space.bilibili.com/293775192
>
> 公众号: golangcoding
>
>  ![二维码](https://i.loli.net/2021/02/28/RPzy7Hjc9GZ8I3e.jpg)
