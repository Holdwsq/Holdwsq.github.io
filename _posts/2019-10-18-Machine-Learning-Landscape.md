---
layout: post
title:  "机器学习概览"
categories: Machine Learning
tags:  Machine Learning  
author: Wsq
---

* content
{:toc}

## 什么是机器学习？

- 广义概念；机器学习是让计算机具有学习能力，无需进行明确编程。--亚瑟·萨缪尔， 1959
- 工程性概念：计算机程序利用经验E学习任务T，性能是P，如果针对任务T的性能P随着经验E不断增长，则称为机器学习。--汤姆·米切尔，1997

## 为什么使用机器学习？

<center><img alt="传统方法" src="https://raw.githubusercontent.com/Holdwsq/Holdwsq.github.io/master/_pictures/custom_method.jpg"></center>
<center>传统方法</center>

在面对新来的事物做判断时，传统的方式会采用一长串负责的规则去进行判断，如果新来的样本符合我们规则，我们就可以准确的判断样本的好坏、品质等类型，当遇见我们规则不发匹配的时候，我们就无法正确做出判断，以及随后要更新我们已有的规则。在面对大数据、变化频发的状况下，
传统的方式不适合去使用。

```markdown
Example：
email_name = '4U_attack'
bad_email_features = ['4U', 'creditcard', 'free']
for feature in bad_email_features:
    if feature in email_name:
        print('this is a bad eamil')
```

机器学习可以让机器具有灵性，它是让机器通过学习数据对某些任务做的更好，而不使用确定的代码规则，机器学习的思想就在于从现有的数据规律泛化到新的样本。

<center><img alt="机器学习方法" src="https://raw.githubusercontent.com/Holdwsq/Holdwsq.github.io/master/_pictures/ml_method.jpg"></center>
<center>机器学习方法</center>

总结一下，机器学习的优势：

- 需要进行大量手工调整或需要拥有长串规则才能解决的问题： 机器学习算法通常可以简
化代码、 提高性能。
- 问题复杂， 传统方法难以解决： 最好的机器学习方法可以找到解决方案。
- 环境有波动： 机器学习算法可以适应新数据。
- 洞察复杂问题和大量数据。

## 机器学习系统的类型

根据常见规则进行分类：

- 是否在人工监督下进行训练：监督学习（Supervised Learning）、非监督(Unsupervised Learning)、半监督学习（Semisupervised Learning）、强化学习(Reinforcement Learning)
- 是否可以动态渐进学习：在线学习（Online Learning） vs 批量学习（Batch Learning）
- 是否通过简单地比较新的数据点和已知数据点，或者在训练中进行模式识别：基于实例学习（Instance-based Learning） vs 基于模型学习（Model-based Learning）

### 监督/非监督学习

**区别**：有没有告诉你答案？

#### 监督学习
在监督学习中，用来训练算法的训练集包含了答案，也称为标签。

<center><img alt="监督学习" src="https://raw.githubusercontent.com/Holdwsq/Holdwsq.github.io/master/_pictures/Supervised_learning.jpg"></center>
<center>监督学习</center>

典型的监督学习任务是分类。 垃圾邮件过滤器就是一个很好的例子： 用许多带有归类（垃圾邮件或普通邮件） 的邮件样本进行训练， 过滤器必须还能对新邮件进行分类。

常见的监督学习算法：
- K近邻算法
- 线性回归（Linear Regression）
- 逻辑回归（Logistic Regression）
- 支持向量机（Support Vector Machines,SVMs）
- 决策树和随机森林（Decision Trees and Random Forests）
- 神经网络（Neural network）

### 非监督学习
在非监督学习中，训练集是没有给出答案或者标签，是在没有人工规定条件下进行学习。

<center><img alt="非监督学习" src="https://raw.githubusercontent.com/Holdwsq/Holdwsq.github.io/master/_pictures/unSupervised_learning.jpg"></center>
<center>非监督学习</center>

常见非监督学习算法：

1. 聚类

K均值

层次聚类分析（Hierarchical Cluster Analysis， HCA）

期望最大值

2. 可视化和降维

主成分分析（ Principal Component Analysis， PCA）

核主成分分析

局部线性嵌入（ Locally-Linear Embedding， LLE）

t-分布邻域嵌入算法（ t-distributed Stochastic Neighbor Embedding， t-SNE）

3. 关联性规则学习

Apriori 算法

Eclat 算法

### 半监督学习

一些算法可以处理部分带标签的训练数据， 通常是大量不带标签数据加上小部分带标签数
据。 这称作半监督学习。

<center><img alt="半监督学习" src="https://raw.githubusercontent.com/Holdwsq/Holdwsq.github.io/master/_pictures/Semisupervised_learning.jpg"></center>
<center>半监督学习</center>

多数半监督学习算法是非监督和监督算法的结合。 例如， 深度信念网络（ deep beliefnetworks） 是基于被称为互相叠加的受限玻尔兹曼机（ restricted Boltzmann machines，RBM） 的非监督组件。 RBM 是先用非监督方法进行训练， 再用监督学习方法进行整个系统微调。

### 强化学习

强化学习非常不同。学习系统在这里被称为智能体（agent），可以对环境进行观察，选择和执行动作，获得奖励（负奖励是惩罚） 。 然后它必须自己学习哪个是最佳方法（称为策略， policy），以得到长久的最大奖励。策略决定了智能体在给定情况下应该采取的行动。

<center><img alt="强化学习" src="https://raw.githubusercontent.com/Holdwsq/Holdwsq.github.io/master/_pictures/Reinforcement_Learning.jpg"></center>
<center>强化学习</center>
