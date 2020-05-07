---
title:  EM 算法
layout: post
categories: 算法
tags: EM algorithm math 
use_math: true
---
---------

# EM
## 琴生不等式

> f是个凸函数，X是个随机变量，则有
$E[f(X)] \geq f(EX)$

其实就是函数值的线性组合大于自变量线性组合的函数值。以两个取值为例，从几何上看，就是函数值连线上的值比函数高。

如果f是个严格凸函数，那么等号仅在X以概率1成立X=EX,即X是个常数。


## EM算法

设有数据集
$$\{\mathbf{x}^{(1)},...,\mathbf{x}^{(m)}\}$$,我们要调整模型参数$\boldsymbol{\theta}$。设极大似然估计为
\begin{equation}
L(\boldsymbol{\theta})=\sum_{i=1}^mlog(p(\mathbf{x}^{(i)}|\boldsymbol{\theta}))
\end{equation}
将隐变量写出
\begin{equation}
L(\boldsymbol{\theta})=\sum_{i=1}^m log(\sum_{\mathbf{z}^{(i)\}\}p(\mathbf{x}^{(i)},\mathbf{z}^{(i)}|\boldsymbol{\theta}))
\end{equation}
直接求解比较困难，我们建立一个迭代算法。令$Q_i$是$\mathbf{z}^{(i)}$的某个分布，则$\sum_{\mathbf{z}^{(i)\}\}Q_i(\mathbf{z}^{(i)})=1$,且$Q_i\geq 0$

\begin{align}
    L(\boldsymbol{\theta})a) & =\sum_{i=1}^mlog(p(\mathbf{x}^{(i)}|\boldsymbol{\theta}))
\end{align}
\begin{align}
    & = \sum_{i=1}^m log\sum_{\mathbf{z}^{(i)\}\}Q_i(\mathbf{z}^{(i)})\frac{p(\mathbf{x}^{(i)},\mathbf{z}^{(i)}|\boldsymbol{\theta})}\{\{Q_i(\mathbf{z}^{(i)})\}\}
\end{align}
\begin{align}
    & = \sum_{i=1}^m logE_\{\{\mathbf{z}^{(i)}\sim Q_i\}\}\frac{p(\mathbf{x}^{(i)},\mathbf{z}^{(i)}|\boldsymbol{\theta})}\{\{Q_i(\mathbf{z}^{(i)})\}\}
\end{align}


利用琴生不等式
\begin{align}
L(\boldsymbol{\theta}) \geq \sum_{i=1}^m E_{\mathbf{z}^{(i)}\sim Q_i}log\frac{p(\mathbf{x}^{(i)},\mathbf{z}^{(i)}|\boldsymbol{\theta})}\{\{Q_i(\mathbf{z}^{(i)})\}\}
\end{align}
\begin{align}
=\sum_{i=1}^m \sum_{\mathbf{z}^{(i)\}\}Q_i(\mathbf{z}^{(i)})log\frac{p(\mathbf{x}^{(i)},\mathbf{z}^{(i)}|\boldsymbol{\theta})}\{\{Q_i(\mathbf{z}^{(i)})\}\}
\end{align}
为了使得上面这个估算式子与$L(\boldsymbol{\theta})$尽可能接近，注意到等号成立的条件，我们可以令
\begin{align}
\frac{p(\mathbf{x}^{(i)},\mathbf{z}^{(i)}|\boldsymbol{\theta})}\{\{Q_i(\mathbf{z}^{(i)})\}\}=c
\end{align}
其中，c为常数。如果分母乘到右边，两边对$\mathbf{z}^{(i)}$求和，则有
$c=\sum_{\mathbf{z}^{(i)\}\}p(\mathbf{x}^{(i)},\mathbf{z}^{(i)}|\boldsymbol{\theta})=p(\mathbf{x}^{(i)}|\boldsymbol{\theta})$
从而有$Q_i(\mathbf{z}^{(i)})=\frac{p(\mathbf{x}^{(i)},\mathbf{z}^{(i)}|\boldsymbol{\theta})}{p(\mathbf{x}^{(i)}|\boldsymbol{\theta})}=p(\mathbf{z}^{(i)}|\mathbf{x}^{(i)},\boldsymbol{\theta})$
其实是个后验分布。上面这个就是E步 \\
M步如下
$\boldsymbol{\theta}:=argmax_{\boldsymbol{\theta\}\}\sum_i\sum_{\mathbf{z}^{(i)\}\}Q_i(\mathbf{z}^{(i)})log\frac{p(\mathbf{x}^{(i)},\mathbf{z}^{(i)}|\boldsymbol{\theta})}\{\{Q_i(\mathbf{z}^{(i)})\}\}$
由于z是用上一轮的$\theta$计算的，在最大化$\theta$过程中分母中Q(z)不影响新的$\theta的最大化$，因此有时候为了简化定义Q函数
$Q(\boldsymbol{\theta},\boldsymbol{\theta}^{old})=\sum_i\sum_{\mathbf{z}^{(i)\}\}Q_i(\mathbf{z}^{(i)})log{p(\mathbf{x}^{(i)},\mathbf{z}^{(i)}|\boldsymbol{\theta})}$
上升的逻辑如下图所示
![在这里插入图片描述](https://img-blog.csdnimg.cn/20200507180622319.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3NoeXJlY2tkYw==,size_16,color_FFFFFF,t_70)

E步可以将
$$l(\boldsymbol{\theta}|\boldsymbol{\theta}_n)$$拉升到$$L(\boldsymbol{\theta}_n)$$处，M步是寻找$$l(\boldsymbol{\theta}|\boldsymbol{\theta}_n)$$处的极值得到$$\boldsymbol{\theta}_{n+1}$$，$$在\boldsymbol{\theta}_{n+1}$$处继续使用E步就可以把曲线再次拉升到$$L(\boldsymbol{\theta}_{n+1})$$处。循环往复可以得到$$L(\boldsymbol{\theta})$$的极值点，但是有可能陷入局部极值。
公式证明如下：
设$$Q^{(t)}_i(\mathbf{z}^{(i)})=p(\mathbf{z}^{(i)}|\mathbf{x}^{(i)},\boldsymbol{\theta}^{(t)})$$
则
\begin{align}
L(\boldsymbol{\theta}^{(t)})=\sum_{i} \sum_{\mathbf{z}^{(i)\}\}Q^{(t)}_i(\mathbf{z}^{(i)})log\frac{p(\mathbf{x}^{(i)},\mathbf{z}{(i)}|\boldsymbol{\theta}^{(t)})}\{\{Q^{(t)}_i(\mathbf{z}^{(i)})\}\}
\end{align}


\begin{align}
L(\boldsymbol{\theta}^{(t+1)}) \geq \sum_{i} \sum_{\mathbf{z}^{(i)\}\}Q^{(t)}_i(\mathbf{z}^{(i)})log\frac{p(\mathbf{x}^{(i)},\mathbf{z}^{(i)}|\boldsymbol{\theta}^{(t+1)})}\{\{Q^{(t)}_i(\mathbf{z}^{(i)})\}\}
\end{align}

\begin{align}
\geq \sum_{i} \sum_{\mathbf{z}^{(i)\}\}Q^{(t)}_i(\mathbf{z}^{(i)})log\frac{p(\mathbf{x}^{(i)},\mathbf{z}^{(i)}|\boldsymbol{\theta}^{(t)})}\{\{Q^{(t)}_i(\mathbf{z}^{(i)})\}\}=L(\boldsymbol{\theta}^{(t)})
\end{align}
第一个不等号是由琴生不等式获得的,第二个不等号是因为我们取了argmax，所以新得到的$$\boldsymbol{\theta}$$使得函数值更大。
总结：E步就是计算隐变量的后验，M步就是寻找最大化辅助函数值的参数。
