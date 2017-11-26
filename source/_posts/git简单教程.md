---
title: git简单教程
date: 2017-11-26 20:04:51
tags:
  - git
  - tech
categories: git教程
---

# 工作流
你的本地仓库由 git 维护的三棵“树”组成。第一个是你的 **工作目录**，它持有实际文件；第二个是 **暂存区（Index)**，它像个缓存区域，临时保存你的改动；最后是 **HEAD**，它指向你最后一次提交的结果。


# 创建新仓库
创建新文件夹，打开，然后执行
```sh
git init
```
创建新的 git 仓库

# 添加和提交
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

# 推送改动
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

# 分支
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

# 更新与合并   
git pull命令的作用是：取回远程主机某个分支的更新，再与本地的指定分支合并

# 待续...
