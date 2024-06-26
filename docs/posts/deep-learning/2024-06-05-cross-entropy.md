---
title: 信息论与交叉熵
date: 2024-06-05
tags:
    - 信息论
    - 压缩
    - 熵
---

一点点信息论的皮毛,寻找深度学习中交叉熵的解释时了解到的,感觉很有意思

---

## 信息论与熵

信息论的核心思想是量化数据中的信息内容

香农在1948年发表的论文“通信的数学理论”中指出,任何信息都存在冗余,冗余大小与信息中每个符号的出现概率或者说不确定性有关

而`信息熵`可以定义为: 信息中排除了冗余后的平均信息量

具体对于一段信息分布x,它的熵可以表示为:

$H(x)=-\sum{P_ilogP_i}$

## 信息量与熵

> "信息量太大了"似乎成为了互联网的习惯用语之一

打个比方,假如我们在看小说/电影

当我们看到剧情A的时候,我们会不自觉的猜测下面的剧情B

很多时候小说/电影剧本写的很典,当我们看到剧情A就可以猜对剧情B[^1],此时我们看到后面的剧情不会惊讶(因为已经猜中了)

但是如果我们猜错了，那么我们可能会感到**惊讶**

从另一个角度来说实际上如果我们能猜中下一步的剧情B,可以证明对于我们来说这段剧情的信息是很有限的

克劳德·香农决定用`信息量`来量化这种**惊讶**程度,记为$-logP_i$

在这里$P_i$可以类比为我们事先赋予的剧情B发生的概率

当我们赋予剧情B较低的概率时，如果发生了,我们的惊异会更大，对于我们来说该事件的`信息量`也就更大

现在重新回顾上面`信息熵`的公式,不难发现实际上就是我们对于得到真实概率时信息量的期望



## 交叉熵

如果把熵理解为“知道真实概率的人所经历的惊讶程度”，那么什么是交叉熵？

交叉熵从P到Q,记为$H(P,Q)$, 我们可以把交叉熵理解为为“主观概率为Q的观察者在看到根据概率P生成的数据时的预期惊异”

显然当$P=Q$有交叉熵最低$H_P$



## 题外话-信息量与压缩

信息论是预测时的惊讶程度

> 下面全引自 [动手学习深度学习](https://zh.d2l.ai/chapter_linear-networks/softmax-regression.html#id13)

而压缩与预测有什么关系呢？ 想象一下，我们有一个要压缩的数据流。 如果我们很容易预测下一个数据，那么这个数据就很容易压缩。 为什么呢？ 举一个极端的例子，假如数据流中的每个数据完全相同，这会是一个非常无聊的数据流。 由于它们总是相同的，我们总是知道下一个数据是什么。 所以，为了传递数据流的内容，我们不必传输任何信息。也就是说，“下一个数据是xx”这个事件毫无信息量。


## 参考

- [如何理解信息熵](https://www.bilibili.com/video/BV1oX4y1w7aG/)
- [动手学习深度学习](https://zh.d2l.ai/chapter_linear-networks/softmax-regression.html#id14)

## 注释


[^1]: 比如天才->废材开局后面是捡到老爷爷然后三十年河东,在我小时候还是很流行的   