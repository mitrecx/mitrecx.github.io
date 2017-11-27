---
title: linux后台程序
date: 2017-11-27 15:52:12
tags:
  - linux
  - tech
categories: linux
---

在终端输入<font color=green>htop</font>
![](http://mitre.oss-cn-hangzhou.aliyuncs.com/blog_pic/htop-bg-fg.png)

然后Ctrl+Z, 把进程放在后台执行。
再在本终端输入<font color=green>bmon</font>  
（<font color=red>b</font>andwide　<font color=red>mon</font>itor）
![](http://mitre.oss-cn-hangzhou.aliyuncs.com/blog_pic/bmon-bg-fg.png)
然后Ctrl+Z, 把进程放在后台执行。

那么，__Ctrl+Z__ 是什么呢？

在终端输入<font color=green>top &</font>，程序直接在后台执行。
![](http://mitre.oss-cn-hangzhou.aliyuncs.com/blog_pic/top-bg-fg.png)


__*结论*__ ：__Ctrl+Z__ 执行的操作是，在当前命令的结尾加一个<font color=green> &</font>，然后当前程序就放在本终端的后台执行了。

在本终端输入<font color=green>jobs</font>, 可以看到本终端的后台程序。
![](http://mitre.oss-cn-hangzhou.aliyuncs.com/blog_pic/jobs-bg-fg.png)
- 把后台程序调入前台：<font color=green>fg + <序号></font>   
- <font color=green>bg</font>显示最后一个加入后台的程序(序号最大)
- <font color=green>fg</font>　默认把序号最大的后台程序调入前台

在别的终端输入<font color=green>jobs</font>,看不到。但是用<font color=green>ps</font>可以查到。
![](http://mitre.oss-cn-hangzhou.aliyuncs.com/blog_pic/newterminal-bg-fg.png)

__*最后*__：
如果不<font color=green>kill</font>后台进程，而是把当前终端关闭，当前终端的后台程序会自动kill掉。
