---
title: Go语言技巧 - 16.【Go泛型】何时使用泛型
date: 2022-06-07 12:00:00
categories: 
- 成长分享
tags:
- Go-Tip
---

![go-tip](https://cloud-fitter-1305666920.cos.ap-beijing.myqcloud.com/go-study.jpeg)

## 导语

本文重点依赖于 https://go.dev/blog/when-generics 这篇博客，有时间的可以自行阅读。

本文会结合个人的理解与经验，强调其中的重点。

<!-- more -->

## 两个示例

文章给出了两个示例，我们看一下签名，了解其功能即可：

```go
// case 1
// 两个泛型Key,Val，Key是可比较的类型，而Val是任意类型
func MapKeys[Key comparable, Val any](m map[Key]Val) []Key {
}
```

```go
// case 2
// T表示任意类型，它被嵌入到具体的数据结构 Tree[T any] 和 node[T any] 中
type Tree[T any] struct {
    cmp  func(T, T) int
    root *node[T]
}

type node[T any] struct {
    left, right  *node[T]
    val          T
}

func (bt *Tree[T]) find(val T) **node[T] {
}
```

## 示例一分析

示例一就是将泛型直接用到的 **函数签名中的变量类型**。

它的特点主要是：能力受限于基础类型，只有关键词any和comparable两种。所以，这种方式适合基础类型的基本操作，如针对map/slice的遍历、求和等。

文章也强调了：由于它无法在编译期用静态类型检查，所以在运行时会慢一点。这点性能损失对普通应用来说完全可以忽略。

## 示例二分析

示例二非常重要，值得我们反复阅读。

先提炼一下，它的泛型`T`体现在两块：

1. 数据结构的命名 - `Tree[T any]`和` node[T any]`，这里的泛型不做任何限制，只表示**数据结构**；
2. 关键性的计算功能 - `cmp  func(T, T) int`，这里是**泛型T的计算能力的关键实现**；

所以，这就是一种 **数据结构与计算分离的实现**。

在这个例子中，泛型`T`表示任意类型。由于它的数据结构的不确定性，自然就无法进行计算；这时引入的`cmp`函数，则是将`T`的计算逻辑作为输入

## 泛型中更倾向于用函数，而不是方法

上面示例二明显比示例一更具通用性。我们重点分析一下`cmp`这个函数。

在传统的面向对象中，我们倾向于使用方法来定义某个功能，比如`(t1 T)cmp (t2 T) int `这样的方法，但这是有依赖的。试想一下，如果你接着写这个方法的实现，势必会写到`t1`与`t2`这两个数据结构的对比了。绕了一圈，我们还是不得不面对`func(T, T) int`这么一个函数。

所以，在Go泛型中，最有效的方式就是直接传入这个函数，由开发者自行实现。

## 泛型与接口

泛型和接口有不少相似之处，比如上面的泛型需要传入`cmp`这个一个对比函数，而如果用接口，往往也需要自己实现接口相关的方法。

但是，我们切勿混淆两者。我们仔细去思考两者的实现，会发现两者的关键性差异：

- 泛型：泛型往往更强调的是数据结构的共同特征，相关的函数只是起到辅助功能，并且处理逻辑要完全一致；
- 接口：接口不关心具体的数据结构，而强调要实现对应的相关方法；

所以，**泛型更多的是从数据结构来思考共同特征，会偏向于过程性思维，适合底层的基础工具库；而接口则是用方法来抽象各种对象，是面向对象的思维，适合中、高层的编程**。

## 指导性原则

最后，作者总结了一个指导性原则：

**当你反复地写类似的代码时，而这些代码之间的差异只是数据结构不同，那你就可以考虑使用泛型。**

这里有2个特点：

1. **反复性**：如果只是写两三次就能解决的，就没必要使用泛型了；
2. **非逻辑类问题**：如果是计算逻辑有差异，那也不能使用泛型；

换一句话来说，**先写重复性代码，再提炼成泛型**，不要过早引入泛型。

## 总结

总体来说，Go的泛型提供了新的语法糖，主要针对底层库的提效，并非解决重复性coding的银弹。



> Github: https://github.com/Junedayday/code_reading
>
> Blog: http://junes.tech/
>
> Bilibili: https://space.bilibili.com/293775192
>
> 公众号: golangcoding
>
> ![二维码](https://cloud-fitter-1305666920.cos.ap-beijing.myqcloud.com/my_wechat.jpeg)
>
> 
