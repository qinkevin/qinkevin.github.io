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
- HEAD指向的版本就是当前版本，因此，Git允许我们在版本的历史之间穿梭，使用命令git reset --hard commit_id
- commit的原则应该是每一次逻辑上的更改做一次提交
- git-clone - Clone a repository into a new directory
- git diff 会对比working directory和staging area；git diff --staged 会对比staging area 与commit；git diff commit1 commit2 会对比两次提交
- git branch 不带参数：列出本地已经存在的分支，并且在当前分支的前面加*号标记
- git-checkout - Switch branches or restore working tree files
- git branch 创建一个新的本地分支，需要注意，此处只是创建分支，不进行分支切换.如需切换分支，可以使用git checkout.
- git checkout -b newbranchname会创建一个新的branch并切换到该branch,相当于上面的两步
- git checkout  -- filename 可以撤销该文件在工作区的所有修改。这里有两种情况：一种是该文件自修改后还没有被放到暂存区，现在，撤销修改就回到和版本库一模一样的状态；一种是该文件已经添加到暂存区后，又作了修改，现在，撤销修改就回到添加到暂存区后的状态。
- 当你改乱了工作区某个文件的内容，想直接丢弃工作区的修改时，用命令git checkout -- filename；如果文件已经被add到暂存区，则用命令git reset HEAD filename可以把暂存区的修改撤销掉（unstage），重新放回工作区.然后再使用上面的命令就可以把工作区的文件也修改
- git branch -d branchname会删除branch
- git show 显示某次提交的内容 git show $id
- git-push - Update remote refs along with associated objects
- git pull：相当于是从远程获取最新版本并merge到本地
- git fetch：相当于是从远程获取最新版本到本地，不会自动merge
- 在Git中，用HEAD表示当前版本，上一个版本就是HEAD^，上上一个版本就是HEAD^^，当然往上100个版本写100个^比较容易数不过来，所以写成HEAD~100
- git reflog用来记录每一次命令
- 工作区（Working Directory）就是你在电脑里能看到的目录
- 工作区有一个隐藏目录.git，这个不算工作区，而是Git的版本库.Git的版本库里存了很多东西，其中最重要的就是称为stage（或者叫index）的暂存区，还有Git为我们自动创建的第一个分支master，以及指向master的一个指针叫HEAD
- Git跟踪并管理的是修改，而非文件
- 命令git rm用于删除一个文件
- git remote add origin 添加远程库，把一个已有的本地仓库与GitHub仓库相关联。远程库的名字就是origin
- 要关联一个远程库，使用命令git remote add origin git@server-name:path/repo-name.git。必须先在GitHub上建好远程库
- 关联后，使用命令git push -u origin master第一次推送master分支的所有内容
- 把本地库的内容推送到远程，用git push命令。git push origin master把本地master分支的最新修改推送至GitHub
- 当我们没有本地库时，先在GitHub上建好远程库，此时需要勾选Initialize this repository with a README，然后从GitHub上使用克隆该远程库到本地
- 要克隆一个仓库，首先必须知道仓库的地址，然后使用git clone命令克隆。
- 分支branch可以用于开发一些新功能，但不想影响到原有的master，可以新建branch，开发完成后合并到master
- git merge命令用于合并指定分支到当前分支
- fast forward指提交到远程中心仓库的代码必须是按照时间顺序的
- git branch -d branchname 删除分支
- 当发生冲突的时候，Git用<<<<<<<，=======，>>>>>>>标记出不同分支的内容
- git log --graph --pretty=oneline --abbrev-commit 命令可以看到合并的情况
- 用git log --graph命令可以看到分支合并图
- 当Git无法自动合并分支时，就必须首先解决冲突。解决冲突后，再提交，合并完成。
- 在实际开发中，我们应该按照几个基本原则进行分支管理：首先，master分支应该是非常稳定的，也就是仅用来发布新版本，平时不能在上面干活;那在哪干活呢？干活都在dev分支上，也就是说，dev分支是不稳定的，到某个时候，比如1.0版本发布时，再把dev分支合并到master上，在master分支发布1.0版本；你和你的小伙伴们每个人都在dev分支上干活，每个人都有自己的分支，时不时地往dev分支上合并就可以了。
- 修复bug时，我们会通过创建新的bug分支进行修复，然后合并，最后删除；当手头工作没有完成时，先把工作现场git stash一下，然后去修复bug，修复后，再git stash pop，回到工作现场。
- 开发一个新feature，最好新建一个分支.如果要丢弃一个没有被合并过的分支，可以通过git branch -D <name>强行删除
- 要查看远程库的信息，用git remote.或者，用git remote -v显示更详细的信息
- 从本地推送分支，使用git push origin branch-name，如果推送失败，先用git pull抓取远程的新提交，解决冲突然后合并再提交
- 本地新建的分支如果不推送到远程，对其他人就是不可见的
- 多人协作的工作模式通常是这样：首先，可以试图用git push origin branch-name推送自己的修改；如果推送失败，则因为远程分支比你的本地更新，需要先用git pull试图合并；如果合并有冲突，则解决冲突，并在本地提交；没有冲突或者解决掉冲突后，再用git push origin branch-name推送就能成功！如果git pull提示“no tracking information”，则说明本地分支和远程分支的链接关系没有创建，用命令git branch --set-upstream branch-name origin/branch-name
- tag就是一个让人容易记住的有意义的名字，它跟某个commit绑在一起
- 命令git tag <name>用于新建一个标签，默认为HEAD，也可以指定一个commit id
- 命令git tag可以查看所有标签
- 可以用git show <tagname>查看标签信息
- 命令git push origin <tagname>可以推送一个本地标签
- 命令git push origin --tags可以推送全部未推送过的本地标签
- 命令git tag -d <tagname>可以删除一个本地标签
- 命令git push origin :refs/tags/<tagname>可以删除一个远程标签。
- GitHub可以将别人的仓库fork，然后clone到本地进行修改。然后可以推送pull request给官方仓库来贡献代码
- 忽略某些文件时，需要编写.gitignore
- .gitignore文件本身要放到版本库里，并且可以对.gitignore做版本管理
- 配置Git的时候，加上--global是针对当前用户起作用的，如果不加，那只针对当前的仓库起作用
