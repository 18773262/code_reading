---
title: Go语言学习路线 - 3.准备篇:打造个人专属的学习环境
date: 2021-04-05 12:00:00
categories: 
- 成长分享
tags:
- Go-Study
---

![Go-Study](https://i.loli.net/2021/02/28/BnVH86E5owhsaFd.jpg)



## 为何我们需要持续学习

**终身成长** 一词已被广泛认可，意味着我们将比前人花费更多的时间在 **学习成长** 中，才能将个人的认知跟上社会的步伐。且不论是否应该放慢脚步，但我们大部分人不得不跟随社会的节奏，**持续学习并提高自己**。

相信有不少朋友跟我一样，在学习的过程中经常会 **半途而废**。那么我在这里分享一些方法和技巧（包括但不仅限于Go语言），希望能给大家带来一些启发。

这部分内容依旧会带有一些强烈的个人主观色彩，大家按需选用~



## 心理建设

在正式开始聊工具和方法前，我先聊聊自己学习前的心理建设。这一点看过去 **很“软”** ，但我吃过很多次亏：

**与其在学习的过程中，给自己找100个理由放弃，还不如在一开始就否定这些理由。** 

以Go语言为例，常见的放弃理由如下：

- Go真的能长期“火”下去吗？
- Go的就业面不广，是否另选其它编程语言
- 学了基础的Go语法后，没有实践的机会
- 一段时间提升很不明显，感觉什么都懂、但什么都不精通

我就是抱着这样的想法，走走停停，错过了很多快速提升的时期；不过也是由于这段经历，让我对许多朋友的想法有切身体会。今天我不会对着上面的问题一一回复，只强调一个重点：

**学技术带着功利心（跳槽、升职）是正常且必要的，毕竟只有解决问题的技术才是有价值的。Go语言是非常依赖“云原生”这一体系的：它实现了云原生的基石-Kubernetes及其余组件，也依赖云原生、提供了非常优雅的微服务解决方案。如今公有云和私有云的建设如火如荼，注定是一个不可逆的过程，所以Go语言是一个需求很大的方向。**



## 学习环境的准备

下面，正式进入准备的细节：

### 操作系统

尽管Go语言支持跨操作系统，但我还是强烈建议大家使用Mac OS，关键在于 **提效**。

>  既然可以花7分力气做一件事，为什么需要10分呢？

不排除后期Windows系统越来越完善，但目前来看，所有的大厂提供给开发者都是Macbook，这点就不言而喻了吧。如果你有在windows/Linux环境上高效开发的经验，欢迎与大家分享~



### Go语言版本

在[官网](https://golang.google.cn/dl/)任意挑选。

如果公司没有要求，那就直接上最新的版本吧~

> 如果公司还在用1.13之前的版本，可以尝试着跟领导沟通，升级到较新的版本。
>
> 使用低版本会不断发现不兼容某些开源库的情况，比如有些依赖库引入了context的特性



### 代码编辑器

强烈建议准备 VSCode + Goland ！对，不用二选一，而是两个都要！

- VSCode对各类语言、组件兼容都很好，面对**轻量级**的开发时完全可以胜任

- Goland在面对**重量级**项目时效果很棒，尤其是对重构项目时，效率能提升一大截

这里提供两个官网： [VSCode](https://code.visualstudio.com/) / [Goland](https://www.jetbrains.com/go/)

> 这两款软件的配置，前期尽量用默认的即可。
>
> 而如果有大量私人化的配置，记得将整个配置方案导出并保存。



### 其余提效工具

- [git](https://git-scm.com/) 不要把git单纯地当作公司的版本管理工具，它更是你私人代码的管理工具
- [iTerm2 + Oh My Zsh](https://segmentfault.com/a/1190000014992947) 这是在Mac下我非常喜欢的一套终端配置方案，大家可以借鉴
- 笔记类：这块大家按自己的习惯选用，常见的如 印象笔记、Microsoft TODO、typora、幕布、系统自带的笔记本等
- 上网助手：技术渠道有不少是在国外的网站上，不清楚具体访问方法的话，可以多和周围的开发者交流

> 欢迎大家留言谈谈自己最喜爱的工具，分享给我~



## Markdown技术写作

作为一个技术工作者，文档是一个必备技能。我们不应把写文档当作一个负担，大部分的时候它是一种沟通与协作上的提效工具。

这里不得不提一下Markdown，它的语法简单，产出的文档样式也满足基本的场景。大家可以根据[这个链接](https://www.markdown.xyz/basic-syntax/)或者自行搜索教程。

> 学习Markdown就是一个很小且价值很高的技术点，可以拿这个作为练手，先使用起来。
>
> 补充一句：Markdown在社区中的支持度不同，但基本大同小异。为了兼容性，少用html的相关特性。

Markdown尽管简单，也有很多语法点，建议大家分阶段使用：

1. 标题、粗体、代码、链接、列表
2. 图片、引用、分隔线、表格
3. 其它

第一阶段的5种语法已经可以满足日常的文档协作，第二阶段的特性可以让文档更具专业性，而其余特性完全可以在使用到时再去查询。

**切忌一次性想掌握全部，分阶段使用才是最有效的学习路径。**

这里推荐一个我常用的本地Markdown文档写作工具 - [typora](https://typora.io/) 。尽管有Web文档工具支持在线编辑，但我更喜欢本地编辑后再复制过去，这样也方便留档。



## 个人博客系统

### 为什么要玩博客

1. **根本价值** - 作为个人的知识输出，沉淀到文档
2. **附带价值** - 面试前后，让心仪的公司更好地了解你
3. **待续价值** - 形成 **正反馈**，持续激励自我

> 有些人玩博客会将价值颠倒，比如将面试筹码作为根本价值，那么这个技术博客就会明显变味。

### 搭建教程

搭建博客系统的方法有很多，我这边推荐一个 [hexo + github pages](https://segmentfault.com/a/1190000017986794) 的。

这种博客的优点在于2点：

1. 发布非常方便、非常方便、非常方便！
2. 原始文档为Markdown，可在本地编辑、存档

### 写博客的Tips

1. **降低“成本”** - 让一篇博客从创作到发布变得简单，这点比较依赖博客系统，例如上面的 hexo+github pages
2. **分享作品** - 分享个人的文章，有利于形成“正反馈”；对于比较腼腆的朋友，可以在小规模的圈子中先进行尝试
3. **多元化** - 博客不仅仅停留在技术上，工作上的心得或者生活上的感悟，都可以写进来
4. **适当拆分** - 不要过分追求长篇大作或者系列形式的文章，*小步快走* 在这里也适用



## 总结

打造个人专属的学习环境，我认为主要包括三块：

1. 个人心态 - 坚持
2. 开发环境 - 快速便捷
3. 正反馈路线 - 文档博客

当然，你可以根据实际情况，添加一些个人专属的内容：

- 如果你是windows用户，你需要搞一套虚拟机
- 如果你已有一套成熟的文档系统，那就继续使用
- 如果你想快速地了解Go而不计划深入，那么没必要过于完善学习环境

希望大家在 **心理** 和 **环境** 都做好充分的准备后，再去走这条长期的技术学习路线，并能坚持下来。



> Github: https://github.com/Junedayday/code_reading
>
> Blog: http://junes.tech/
>
> Bilibili: https://space.bilibili.com/293775192
>
> 公众号: golangcoding
>
>  ![二维码](https://i.loli.net/2021/02/28/RPzy7Hjc9GZ8I3e.jpg)
