---
layout: post
title: "Git和GitHub"       # Title of the post
subtitle:
modified: 2016-11-30                 # Date
date:       2016-11-30 22:00:00
author:     "随机漫步的傻瓜"
header-img: "img/post-bg-2015.jpg"
catalog: true
tags:
    - 其他
---

# Git

- Git只能跟踪文本文件的改动，尤其要注意word格式是二进制，所以Git是无法跟踪变化的，所以要真正使用版本控制系统，就要以纯文本方式编写文件
- git log命令显示从最近到最远的提交日志
- git log --pretty=oneline 可以美化日志的输出
- git diff:比较项目中任意两个版本的差异
- git commit：提交当前工作空间的修改内容
- git init:把这个目录变成Git可以管理的仓库
- 把一个文件放到Git仓库只需要两步：第一步，用命令git add告诉Git,把文件添加到仓库。第二步，用命令git commit告诉Git,把文件提交到仓库
- git commit 命令，-m后面输入的是本次提交的说明，可以输入任意内容，当然最好是有意义的，这样你就能从历史记录里方便地找到改动记录
- 之所以Git添加文件需要add，commit一共两步是因为commit可以一次提交很多文件，所以你可以多次add不同的文件
- git add会将文件暂存，放到staging area中
- git status命令可以让我们时刻掌握仓库当前的状态
- git reset 命令回退到某个版本
- commit的原则应该是每一次逻辑上的更改做一次提交
- git-clone - Clone a repository into a new directory
- git-checkout - Switch branches or restore working tree files
- git diff 会对比working directory和staging area；git diff --staged 会对比staging area 与commit；git diff commit1 commit2 会对比两次提交
- git branch 不带参数：列出本地已经存在的分支，并且在当前分支的前面加*号标记
- git branch 创建一个新的本地分支，需要注意，此处只是创建分支，不进行分支切换.如需切换分支，可以使用git checkout
- 
