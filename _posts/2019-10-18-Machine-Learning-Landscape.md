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

<center>![传统方法](https://raw.githubusercontent.com/Holdwsq/Holdwsq.github.io/master/_pictures/custom_method.jpg)</center>
<center>传统方法</center>

在面对新来的事物做判断时，传统的方式会采用一长串负责的规则去进行判断，如果新来的样本符合我们规则，我们就可以准确的判断样本的好坏、
品质等类型，当遇见我们规则不发匹配的时候，我们就无法正确做出判断，以及随后要更新我们已有的规则。在面对大数据、变化频发的状况下，
传统的方式不适合去使用。
```markdown
Example：
email_name = '4U_attack'
bad_email_features = ['4U', 'creditcard', 'free']
for feature in bad_email_features:
    if feature in email_name:
        print('this is a bad eamil')
```
机器学习可以让机器具有灵性，它是让机器通过学习数据对某些任务做的更好，而不使用确定的代码规则，机器学习的思想就在于从现有的数据规律
泛化到新的样本。
