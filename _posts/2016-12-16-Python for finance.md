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

# Chapter 5 Data Visualization
- 在不同的时间,不同的价位区间,不同的履约价都会有不同的隐含波动率,这种现象称之为波动率平面(volatility surface)

# Chapter 7 Input/Output Operations
- Serialization refers to the conversion of an object (hierarchy) to a byte stream; deserialization is the opposite operation
- Obviously, pickle stores objects according to the first in, first out (FIFO) principle. There is one major problem with this: there is no meta-information available to the user to know beforehand what is stored in a pickle file. A sometimes helpful workaround is to not store single objects, but a dict object containing all the other objects
- A major advantage of working with PyTables is the approach it takes to compression. It uses compression not only to save space on disk, but also to improve the performance of I/O operations. How does this work? When I/O is the bottleneck and the CPU is able to (de)compress data fast, the net effect of compression in terms of speed might be positive.

# Chapter 8. Performance Python
- In effect, Cython is a hybrid language of Python and C. Coming from Python, the major differences to be noticed are the static type declarations (as in C) and a separate compiling step (as with any compiled language).
- Nowadays, the Python ecosystem provides a number of ways to improve the performance of code:
1. Paradigms
> Some Python paradigms might be more performant than others, given a specific problem.

2. Libraries
> There is a wealth of libraries available for different types of problems, which often lead to much higher performance given a problem that fits into the scope of the library (e.g., numexpr).

3. Compiling
> A number of powerful compiling solutions are available, including static (e.g., Cython) and dynamic ones (e.g., Numba).
4. Parallelization
> Some Python libraries have built-in parallelization capabilities (e.g., numexpr), while others allow us to harness the full power of multiple-core CPUs, whole clusters (e.g., IPython.parallel), or GPUs (e.g., NumbaPro).
