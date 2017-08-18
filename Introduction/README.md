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
下图为监督学习的模型结构，利用训练集结合相应的学习算法，得到一个可以很好预测输出结果y的方程h(x)。新的变量x带入h(x)，从而预测y。

![Image of Model Representation](https://d3c33hcgiwev3.cloudfront.net/imageAssetProxy.v1/H6qTdZmYEeaagxL7xdFKxA_2f0f671110e8f7446bb2b5b2f75a8874_Screenshot-2016-10-23-20.14.58.png?expiry=1503100800000&hmac=F_DSow19a8A2kplkrmkl8QMQDSzCUP8kq8B2h9bW1OA)

## 4. 向量矩阵的运算
- 因为本人有过2年Matlab的使用经验这里就不记录课程中与Matlab基本语法相关的内容了。
