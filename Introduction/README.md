# 机器学习简介
课程第一周主要是介绍了机器学习的基本概念、模型和cost function的概念、参数优化的算法以及向量、矩阵在Matlab中的基本操作。
下文将对上述内容逐一进行描述：
## 1. 机器学习是什么
Andrew Ng分别引用了两位学者的话来定义机器学习的概念。Arthur Samuel曾说“机器学习赋予了计算机可以在没有明确编码的情况下自我学习的能力。” 
更为现代的定义是由 Tom Mitchell给出的，"A computer program is said to learn from experience E with respect to some class of tasks T and performance measure P, if its performance at tasks in T, as measured by P, improves with experience E." 举个例子：垃圾邮件分类程序，将邮件分类为spam 或者 no-spam是task T，以往的邮件标记为experience E，分类的正确与否为P。

通常，机器学习可以分为两类，监督学习(Supervised Learning)与非监督学习(Unsupervised Learning)：
- 监督学习：提供数据集以及正确的输出结果，通过算法模型寻找输入数据与输出结果间的关系。 监督学习一般可以分为两种：“回归问题”和“分类问题”。回归问题是指试图预测的结果是连续性的数据，也就是说需要将输入数据集map到一些continuous function。而在分类问题中，我们试图去预测离散的输出结果，也就是说要将输入变量映射到离散的分类。
- 非监督学习：非监督学习可以让我们在不知道想要的结果是什么的情况下，计算机按照输入变量的性质将数据分为不同组，性质相近的数据会被配置在一组中。数据能够呈现出特定的结构，即便我们不知道是哪些变量起了决定性因素。例子：聚类，K-Means；非聚类：鸡尾酒聚会算法。
## 2. 模型呈现：
这一节内容主要讲了变量的标记，以及模型结构。
下图为监督学习的模型结构，利用训练集结合相应的学习算法，得到一个可以很好预测输出结果y的方程h(x)。通过将test set中变量x带入h(x)，可以预测y。

![Image of Model Representation](https://user-images.githubusercontent.com/31018275/30253289-170e1280-9650-11e7-8068-923ad449643b.png)

为了评判模型h(x)是否准确的预测了变量y，这里引入了Cost function的概念。对于不同机器学习模型，cost function的设定也有所不同。以线性回归模型作为例子，评测回归模型好坏的cost function为预测结果与真实值的平均距离，也称作平方差方程，即：

<img src="https://user-images.githubusercontent.com/31018275/29490009-db997730-84fc-11e7-80d5-07849afbe194.png" width="400">

其中θ0,θ1为线性回归方程的参数，成本方程J是一个关于变量θ0,θ1的方程。当J的值越小时，说明模型预测值越接近真实值。所以为了使得学习模型达到最优，我们通常需要优化J，找到合适的theta值，从而最小化成本方程。

## 3. 梯度下降算法
为了得到可以使方程J达到的全局最小值的theta，课程介绍了梯度下降(Gradient Descent)优化算法。梯度下降的步骤：J是关于theta的函数，在设定或者随机生成theta的初始值后，计算方程J在相应theta值上的导数值，也就是J在theta点的斜率。给定相应下降步幅alpha，更新theta值为：原theta减去在其在theta处的斜率乘以下降步幅。重复上述操作直到theta收敛。继续以线性回归为例，相应的梯度下降算法为：

<img src ='https://user-images.githubusercontent.com/31018275/29490235-ccc66c52-8503-11e7-85ae-4514acd8b6a4.png' width = '300'>
(重复直至θ0,θ1收敛)

更为直观的算法示意图：

![Image of Gradient Descent](https://user-images.githubusercontent.com/31018275/30253285-02520946-9650-11e7-8489-4fd2211d3ad0.png)

J随着θ0,θ1按照相应的斜率及步幅下降的同时递减。

这里需要注意的几个点：
- J为凸函数的时候，梯度递减算法往往能够找到J的全局最小值，否则使用容易陷入局部最优中
- alpha的取值，alpha取得过小往往会使收敛速度过慢，而alpha值过大则会使J不收敛。Andrew Ng给的建议是alpha从0.01开始取值每次增加3倍或减少3倍，绘制J与iteration的图来判定alpha的选取是否合适。

## 4. 向量矩阵的运算
- 因为本人有过2年Matlab的使用经验这里就不记录课程中与Matlab基本语法相关的内容了。
