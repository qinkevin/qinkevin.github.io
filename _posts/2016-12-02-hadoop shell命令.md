---
layout: post
title: "Hadoop shell 命令"       # Title of the post
subtitle:
date:       2016-12-02 22:00:00
author:     "随机漫步的傻瓜"
header-img: "img/post-bg-2015.jpg"
catalog: true
tags:
    - 大数据
---

# Hadoop shell 命令
- hadoop fs -ls 列出HDFS中的文件
- hadoop fs -put filename 将文件放入HDFS中
- hadoop fs -tail filename可以看该文件的最后几列
- hadoop 的任何操作都要在前面加上hadoop fs ,后面的名利类似于Unix命令
