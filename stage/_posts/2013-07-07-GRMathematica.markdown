---
layout: post
title: 做广义相对论基本计算的Mathematica包
category: physics
tags: [Time machine, Superluminal]
mathjax: ture
---

## 缘由

使用符号计算软件Mathmatica做广义相对论计算的包有很多, 最知名的如<a href="http://grtensor.phy.queensu.ca/">GRTensor</a>. 但是我觉得这些包都太庞大, 功能过多, 使用不便, 因为就我个人而言, 这些包中很多功能实际上用不到.

为此, 我自己写了一个只有七个函数的简单包<a href="https://files.dropbox.com/u/36755974/GR.m" title="点此下载" >GR</a>, 可以计算Einstein张量, 克里斯多菲尔记号, 外尔张量等. 您可以随便改动或传播这个包, 不用注明出处.

需要提到的是, 这个包并非完全由我原创. 不过是把<a href="http://web.physics.ucsb.edu/~hartle/">Gravity: An Introduction to Einstein's General Relativity</a>附加的代码封装成了包. 在这个过程中我做了些小改动. James Hartle的这本书是学习广义相对论的名著, 如果您觉着这个包好用, 感谢Hartle老先生好了, 譬如买他一本书聊表谢意.

实际上用来做符号计算的软件很多, 如Maxima, Cadabra, Maple, Reduce等等. Maxima是符号计算软件之父, 使用Lisp语言, Mathematica[^1]从它身上借鉴了非常多的东西, Mathematica本身也是使用符号语言. Cadabra底层使用C++语言, 但是软件本身语法使用"Latex语言", 这对科技工作者基本就是自然语言了. Cadabra本意是为弦论学家设计的符号计算软件, 功能极其强大. 更让人惊喜的是它的输出界面如同Latex排版的一样, 极其漂亮. 但Cadabra还不是很成熟. 至于Maple大家都知道是老牌符号计算软件了, 输出界面也很漂亮, 内置了非常多的物理数学包, 相当专业. 至于Ruduce, 那也是祖师级的符号推导软件. 当年我老师的师兄去霍金的研究组做博后, 回来说自己的一大收获就是学会了使用Ruduce, 可见Ruduce当年的风靡程度.

## 使用方法

在你安装Mathmatica的目录, 找到Addons文件夹, 将这个包存放在LegacyPackages底下. 这样在Mathmatia启动时, 包会被自动导入.

然后使用命令

	<<GR`

导入<strong>GR</strong>包. 注意这个包的名字就是它的文件名, 如果你还有其它的包和这个包名字冲突, 将会报错.

## 使用说明

以Vaidya黑洞在double null 坐标表示为例:

 $$ \displaystyle ds^{2}=-2f(u,v)dudv+r^{2}(u,v)d\Omega^{2}$$
 
 比如计算其Einstein张量:

$$ \scriptsize\displaystyle \text{Einstein}\left[\left\{\{0,-f[u,v],0,0\},\{-f[u,v],0,0,0\},\left\{0,0,r[u,v]^2,0\right\},\left\{0,0,0,r[u,v]^2\text{Sin}[\theta ]^2\right\}\right\},\{u,v,\theta ,\phi \}\right]$$

计算结果举例如下:

$$ \text{GR Private}~~ G_{uu}\frac{2 f^{(1,0)}[u,v] r^{(1,0)}[u,v]-2 f[u,v] r^{(2,0)}[u,v]}{f[u,v] r[u,v]}$$

$$ \text{GR Private}~~G_{vu}\frac{f[u,v]+2 r^{(0,1)}[u,v] r^{(1,0)}[u,v]+2 r[u,v] r^{(1,1)}[u,v]}{r[u,v]^2}$$

从这个例子你可以看出使用方法非常简单: GR包内建了七个函数:

    Chri "计算度规的联络系数"
    Riemann "计算Riemann曲率张量"
    Ricci "计算Ricci张量"
    Ricalar "计算Ricci标量"
    Einstein "计算Einstein张量"
    Kretschmanscalar "计算Kretschman标量"
    Weyl "计算Weyl曲率张量"

 每个函数的参数都是一样的:

    函数[度规,坐标]

 注意度规的格式是矩阵, 而坐标是数组. 这在上面的例子中已经清楚的给出来了. 当然最好在Mathmatica中打开这个包, 自己看看源文件, 这样可以一目了然.

[^1]: 您可能已经注意到了Mathematica的取名方式和iPhone, iPad类似, 这不奇怪. 要知道Wolfram和Jobs是好朋友, Mathematica这名字正是Jobs建议的! 很多人对Wolfram把Mathematica做成收费软件颇有微词, 毕竟Mathematica开始是作为大学的一个研究项目, 后来竟被Wolfram做成私人产品, 并且成了以自己名字命名的公司, 而且目前是世界最大的计算软件公司之一. 不过现在想来, Wolfram有自己的策略. 符号软件是个小众软件, 如果找不到盈利模式它的开发速度将会非常缓慢. 而且如果没有商业模式运作, 符号软件的用户界面也不一定友好. Wolfram把Mathematica做成商业, 早就了Mathematica成为最好用的符号软件. 而且, Wolfram对Mathematica的盗版是放任的, 要知道Mathematica5的序列号竟然也能激活Mathematica8, Wolfram相当于是让那些买不起正版Mathematica软件的人免费使用产品, 也算是业界良心吧! 当然如果你有科研经费, 建议你还是用正版. 相比之下Maxima曾经如日中天, 后来商业化不如Mathematica成功, 随后被开源, 但是Maxima依然不如Mathematica好用. 当然得益于开源, Maxima的Emacs界面那是无与伦比!
