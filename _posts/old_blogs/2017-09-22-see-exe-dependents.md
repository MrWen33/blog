---
layout: post
title: 查看exe文件依赖的dll文件的方法
tags: [tips]
---

以vs2017为例

打开vs自带的命令行工具，比如![Tools]({{ site.baseurl }}/assets/img/see_exe_dependents/1.png)

输入dumpbin /dependents [文件路径]，比如要查看c盘根目录下的a.exe就输入dumpbin /dependents “C:\a.exe”
