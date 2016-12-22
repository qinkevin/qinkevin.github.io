---
layout:     post
title:      "Python for finance"
subtitle:
date:       2016-12-16 15:00:00
author:     "随机漫步的傻瓜"
header-img: "img/post-bg-2015.jpg"
catalog: true
tags:
    - 量化投资
---

# Chapter 1 why Python for Finance?
- Close is the actual price that was reported at the exchange when the stock closed for that day.Adjusted Close is a number that the data provider generates for us.And it's adjusted as the name implies, for certain things like stocks, splits, and dividend payments.

# Chapter 3 Introductory Examples
- Monte Carlo simulation is one of the most important algorithms in finance and numerical science in general. Its importance stems from the fact that it is quite powerful when it comes to option pricing or risk management problems. In comparison to other numerical methods, the Monte Carlo method can easily cope with high-dimensional problems where the complexity and computational demand, respectively, generally increase in linear fashion
- The downside of the Monte Carlo method is that it is per se computationally demanding and often needs huge amounts of memory even for quite simple problems. Therefore, it is necessary to implement Monte Carlo algorithms efficiently
- daily return is simply how much did the price go up or down on a particular day
- If you are going to fill your data to resolve problems with gaps, fill forward first and fill backward second.
