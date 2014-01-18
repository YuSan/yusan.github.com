---
layout: post
title: "波导枭龙HD(XL100)线刷第三方Recovery超详细图文教程"
date: 2014-01-10 22:53:44 +0800
comments: true
categories: Bird_XL100 Recovery
---
---
【说明】
----------------
此教程是用来指导刷入波导枭龙HD（Bird XL100）第三方Recovery的教程，因为阿里云系统的缘故，貌似目前只有这种方式可以成功刷入Recovery。

****请认真看帖子，看清每一步再进行操作，否则出错一律不负责。****

【第一步】
> 1、下载MTK线刷联机驱动 ，附上下载地址：
链接:  点我下载   密码: iw6v



2、解压驱动文件，并安装。如下图：

第二步：
1、下载线刷工具 SP_Flash_Tool （注意：此工具为MT6582专用，其它线刷工具用不了，请务必从以下地址下载！），附上下载地址：
本帖隐藏的内容
链接:   点我下载    密码: aarh



2、解压工具到任意文件夹；


3、双击运行SP_Flash_Tool.exe（注意：此时不要将手机连接到电脑）


4、点击 Scatter-loading 按钮选择 Scatter 文件（scatter文件下载： MT6582_Android_scatter.txt (7.47 KB, 下载次数: 193) ）；


5、在上方选项中选择window，然后点击勾选“Write Memory”；


6、上一步执行完成之后会多出一个选项卡——“Write Memory”。选择它，然后按下图操作：
1）、Open Raw Data；
2）、选择下载的Recovery文件
3）、点击“打开”，即选择了Recovery文件，然后看看“File Path”确保文件路径正确；
4）、在“Memory Setting”选择“emmc”；
5）、在下面的两个框输入16进制的起始地址和长度，两个框内的数据分别为：（此处必须填写正确！可在下面复制）

    Begin Address：  0x0000000002980000
    Container Length： 0x00600000

复制代码



7、点击工具上方的 第二个按钮“Write Memory ” 按钮，并将手机关机连接到电脑  ,等待进度条走完，出现绿色圆圈即可；


8、刷入完成，拔掉数据线。如果需要进入 Recovery 模式，按住“音量+”和“电源键”，并选择 "Recovery mode" 即可。

好了，教程到此结束！如果在手机关机连接到电脑之后，工具未出现进度条，手机进入充电，那么请回到第一步重新安装联机驱动。


