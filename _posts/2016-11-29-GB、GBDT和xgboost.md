---
layout: post
title: "Boosting、GB、GBDT和xgboost"       # Title of the post
subtitle:
date:       2016-11-29 12:00:00
author:     "随机漫步的傻瓜"
header-img: "img/post-bg-2015.jpg"
catalog: true
tags:
    - 机器学习
---
# Boosting
- Boosting 的基本思想是对一份数据，建立M个弱分类器，每次分类都将上一次分错的数据权重提高一点再进行分类，这样最终得到的分类器在测试数据与训练数据上都可以得到比较好的成绩
- 初始时权重是一样的，随着训练过程，对点的权重进行修正，如果分类正确了，权重降低，如果分类错了，则权重提高。程序越往后执行，训练出的模型就越会在意那些容易分错（权重高）的点

# Gradient Boosting
- Gradient Boosting 是一种Boosting的方法，主要思想是每一次建立模型是在之前建立模型损失函数的梯度下降方向，也就是让损失函数在其梯度方向上下降
- 每次模型在梯度方向上的减少的部分，可以认为是一个“小”的或者“弱”的模型，最终我们会通过加权(也就是每次在梯度方向上下降的距离）的方式将这些“弱”的模型合并起来，形成一个更好的模型

# GBDT

- GBDT全称为Gradient Boost Decision Tree,可以用来做分类、回归

# xgboost
