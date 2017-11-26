---
title: github遇到的坑
date: 2017-11-27 00:34:53
tags:
  - 踩过的坑
  - git
---
部署博客时（hexo d）

遇到错误   
<font color=orange >Error: EACCES: permission denied, unlink '/home/mitrecx/blog/.deploy_git/about/index.html'</font>

遇到这样的权限问题，理所当然的想到
```sh
chmod -R 777 .
```
简单粗暴，解决问题。

**但是，我没有这么做！**

我直接
```sh
sudo hexo d
```
新问题来了
<font color=orange>
ssh: connect to host my.github.com port 22: Connection timed out　　　　
fatal: Could not read from remote repository.　　
Please make sure you have the correct access rights
and the repository exists.　　
FATAL Something's wrong. Maybe you can find the solution here: http://hexo.io/docs/troubleshooting.html

</font>

**为什么会ssh　github　会有问题？**　　　

我试了一下：
```sh
ssh -T git@github.com
```
![两个帐号都可以连接到github](http://odtumk8fc.bkt.clouddn.com/gitkeng.png )

但是 用sudo就不行  
![sudo ssh连接github提示publickey不行](http://odtumk8fc.bkt.clouddn.com/sudo-git-keng.png)

原因很明显了：
**我的sshkey　是mitrecx用户生成的。sudo执行命令时，不是mitrecx用户在执行，是root用户执行的，所以github会拒绝接受git请求。**  
这样看似很“安全”：我用别人（root）给我分配的用户使用自己的github，别人（root）可以看我用户文件，但是不能用我的sshkey 。  
sshkey在 __~./ssh__ 目录下，别人（root）是可以复制，查看的！

github权限的坑踩完了。
为什么最初我在　hexo　d　会出出错呢？
原因是我在hexo　d　执行前，执行的是sudo　hexo　g　，　而不是　hexo　g　。
