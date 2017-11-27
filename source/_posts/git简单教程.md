---
title: git简单教程
date: 2017-11-26 20:04:51
tags:
  - git
  - tech
categories: git教程
---
# 从零开始－－简单使用
```shell
git init #初始化(新建)一个git仓库

#第一次把本地仓库提交到github
#添加到暂存区，不添加的话 filename是untracked ,untracked files不能commit
git add <filename>  
#把暂存区的内容提交到HEAD,仍然在本地仓库
git commit -m "关于本次提交的说明信息"
#本地仓库连接远程仓库 ，连接名为origin
git remote add origin  git@github.com:username/repository.git
#把HEAD里的内容提交到github上的master分支
git push origin master

#再次操作
#现在有本地仓库，也和github连接过（有连接名origin），
#只要三步就能push到github
git add <filename>
git commit -m "commit info"
git push origin <branch-name>

#
#分支
git branch  #查看分支， -a查看所有分支
git branch -d  branchname  #有些时候可能会删除失败,比如如果branchname分支的代码还没有合并到master, -D 可以强制删除
git branch new-branch  #创建名为new-branch的分支
git checkout new-branch  #切换到new-branch分支
#
git checkout -b new-branch  #简化：创建并切换

#
#频繁使用的一个命令－－查看状态
git status

```
如果git add一个不想要的提交的file，可以用以下命令清除
```shell
git	rm	--cached <filename> #移除这个缓存
```
# 从一开始
## 工作流
你的本地仓库由 git 维护的三棵“树”组成。第一个是你的 **工作目录**，它持有实际文件；第二个是 **暂存区（Index)**，它像个缓存区域，临时保存你的改动；最后是 **HEAD**，它指向你最后一次提交的结果。


## 创建新仓库
创建新文件夹，打开，然后执行
```sh
git init
```
创建新的 git 仓库

## 添加和提交
提出更改（把它们添加到暂存区），使用如下命令：
```sh
git add <filename>
```
举一个例子，
- 如果想把当前目录下的所有文件添加到 __暂存区INDEX__ ,执行：
```sh
git add .
```
- 如果想把当前目录下的某几个文件添加到 __暂存区INDEX__ ,执行：
```sh
git add <filename1,2,3>
```
还有个方法，在当前目录下建立一个名为
<font color=blue size=3>.gitignore</font> 的文件。然后把想要忽略的文件名添加在<font color=blue size=3>.gitignore</font>中，![文件内容](http://odtumk8fc.bkt.clouddn.com/gitignore.png)
然后执行
```sh
git add .
```

git add是 git 基本工作流程的第一步；使用如下命令以实际提交改动：
```shell
 git commit -m "代码提交信息"
```
现在，你的改动已经提交到了 HEAD，但是还没到你的远端仓库

## 推送改动
你的改动现在已经在本地仓库的 **HEAD** 中了。执行如下命令以将这些改动提交到远端仓库：
```sh
git push origin master
```
可以把 master 换成你想要推送的任何分支。

如果你还没有克隆现有仓库，并欲将你的仓库连接到某个远程服务器，你可以使用如下命令添加：
```sh
git remote add origin <server>
```
如此你就能够将你的改动推送到所添加的服务器上去了

## 分支
分支是用来将特性开发绝缘开来的。在你创建仓库的时候，master 是“默认的”分支。在其他分支上进行开发，完成后再将它们合并到主分支上。
```sh
git branch hexo  //新建hexo分支
git checkout hexo  //切换到hexo分支上
```
```sh
git checkout -b feature_x  #创建一个叫做“feature_x”的分支，并切换过去：
git checkout master  #切换回主分支

git branch -d feature_x  #再把新建的分支删掉
git push origin <branch>  #将分支推送到远端仓库
```

## 更新与合并
A同学在a分支代码写的不亦乐乎,终于他的功能完工了,并且测试也都ok了,准备要上线了,这个时候就需要把他的代码合并到主分支master上来,然后发布。git	merge	就是合并分支用到的命令,针对这个情况,需要先做两步,第一步是切换到	master	分支,如果你已经在了就不用切换了,第二步执行	git	merge	a	,意思就是把a分支的代码合并过来,不出意外,这个时候a分支的代码就顺利合并到	master	分支来了。  
git pull命令的作用是：取回远程主机某个分支的更新，再与本地的指定分支合并


## git clone

```shell
#1.最简单直接的命令
git clone xxx.git

#2.如果想clone到指定目录
git clone xxx.git "指定目录"

#3.clone时创建新的分支替代默认Origin HEAD（master）
git clone -b [new_branch_name]  xxx.git
```
 clone 远程分支

　　git clone 命令默认的只会建立master分支，如果你想clone指定的某一远程分支(如：dev)的话，可以如下：

　　1. 查看所有分支(包括隐藏的)  git branch -a 显示所有分支，如：　　　
```
* master
  remotes/origin/HEAD -> origin/master
  remotes/origin/dev
  remotes/origin/master
  ```
　　2.  在本地新建同名的("dev")分支，并切换到该分支
```shell
git checkout -t origin/dev
#等同于：
git checkout -b dev origin/dev
```
执行完2，发现dev分支的内容已经存在于本地仓库了。

# 待续...
