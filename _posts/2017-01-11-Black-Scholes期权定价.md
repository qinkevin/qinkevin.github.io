---
layout:     post
title:      "Black-Scholes期权定价模型"
subtitle:
date:       2019-1-11 11:00:00
author:     "随机漫步的傻瓜"
header-img: "img/post-bg-2015.jpg"
catalog: true
tags:
    - 量化投资
---

# Black-Scholes期权定价模型

1. If options are correctly priced in the market,it should not be possible to make sure profits by creating portfolios of long and short positions in options and their underlying stocks.
2. Stochastic processes describe the probabilistic evolution of the value of a variable through time
3. A Markov process is one where only the present value of the variable is relevant for predicting the future. The past history of the variable and the way in which the present has emerged from the past is irrelevant
4. The Markov property of stock prices is consistent with the weak form of market efficiency
5. A Wiener process dz is a process describing the evolution of a normally distributed variable.The drift of the process is zero and the variance rate is 1.0 per unit time.This means that,if the value of the variable is x0 at time 0,the at time T it is normally distributed with mean x0 and standard deviation T的平方根
6. The mean change per unit time for a stochastic process is known as the drift rate and the variance per unit time is known as the variance rate.
7. A generalized Wiener process describes the evolution of a normally distributed  variable with a drift of a per unit time and a variance rate of b的平方 per unit time,where a and b are constants.This means that if,as before,the value of the variable is x0 at time 0,it is normally distributed with a mean of x0+aT and a standard deviation of b*T的平方根 at time T
8. 伊藤过程 is a process where the drift and variance rate of x can be a function of both x itself and time.The change in x in a very short period of time is,to a good approximation,normally distributed,but its change over longer periods of time is liable to be nonnormal.
9. In Black-Scholes-Merton,the position in the stock and the derivative is riskless for only a very short period of time.To remain risk less,it must be adjuted,or rebalanced,frequecntly.
10. Normally,the value of an option declines as its maturity date approaches, if the value of the stock does not change.
11. The option is more volatile than the stock.A given percentage change in the stock price, holding maturity constant, will result in a larger percentage change in the option value.
12. the value of such a hedged position does not depend on the price of the stock
13.  A warrant is an option that is a liability of a corporation.The holder of a warrant has the right to buy the corporation’s stock (or other assets ) on specified terms.
