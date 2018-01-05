---
layout: post
title: "windows启动的Boot/BCD 0xc000000f ERROR的解决方法"
tags: [tips]
---

用diskgenius给C盘扩容以后重启就出现了这个问题。根据Info: an error occurred while attempting to read the boot configuration data.推断是启动引导文件出了问题，那么解决方法就是重新设置启动引导。

修复步骤：(引用自[这篇文章](http://blog.csdn.net/loricxy/article/details/8054794))
1.确认你的boot partition是活动分区

从你的修复光盘或U盘启动进入控制台,输入```diskpart```,用```list disk```来查看所有的硬盘使用 ```select disk x```来选择硬盘，x为你的硬盘编号。使用```list partition```来查看自己的boot sector所在的分区，使用```select partition x```来选择相应的分区。现在输入```detail partition```并查看报告中是否说明其为Active(活动的).如果是活动的，就可以直接进入下一步了，不然的话使用```Active```来将其标记为活动分区，windows会报告说该分区当前已被标记为活动分区了，现在重启电脑并再次进入修复模式.

2.修复mbr与启动引导

在修复控制台中依次输入以下的命令
		
		bootrec /fixmbr
		bootrec /fixboot

现在重启你的电脑并进入修复控制台输入```bcdboot [path to your windows folder]```.你的windows folder一般是在C:\Windows,但是在修复模式下，其可能显示为D:\Windows,所以要确定你的Windows的正确路径(通过使用dir即可很快的确定该路径),在我的电脑上是使用的```bcdboot c:\windows```，这条命令会建立一个新的bcd boot sector并将所以启动需要的文件都拷贝进去，现在最后一次重新启动你的电脑，不出意外的话，你的电脑就能够正常启动了(我的电脑进行到这一步就成功启动了)，如果还不能正常启动，重新执行上面两条bootrec命令。

如果在你的硬盘上还有其他的操作系统，你可以使用 bootrec /scanos来将它们加入启动项中。