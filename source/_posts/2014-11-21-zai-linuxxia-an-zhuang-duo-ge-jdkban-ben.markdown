---
layout: post
title: "在linux下安装多个jdk版本"
date: 2014-11-21 19:41:43 +0800
comments: true
categories: Linux software
---
在4.4（Kitkat）之前一直用的SunJDK1.6版本来编译，到4.4的时候开始用SunJDK1.7版本编译，从Android L开始到现在的5.0谷歌开始使用OpenJDK来编译。
所以在一台电脑上要进行源码编译需要安装多个版本的JDK。
<!--more-->

我现在用的系统是LinuxMint17，基于UBUNTU 14.04。

现在需要用到如上几个版本的JDK，所以都进行了安装，在需要的时候进行切换即可。

###1.SunJDK1.6

可以在此下载[jdk-6u43-linux-x64.bin](http://pan.baidu.com/s/1dDcliPN),安装方法可看这个[ubuntu配置 Java SE 1.6](http://hi.baidu.com/apar1992/item/d3c31afeb3ae9d12c7dc4563)

###2.SunJDK1.7
可以到SunJDK官网下载[JDK7](http://www.oracle.com/technetwork/java/javase/downloads/jdk7-downloads-1880260.html),下载之后执行如下命令解压：

    tar -zvfx jdk-7u72-linux-x64.tar.gz
    sudo mv -rf jdk1.7.0_72/ /opt/jdk1.7.0_72
###3.OpenJDK7

可以直接在终端执行如下命令安装

    sudo apt-get install openjdk-7-jdk
安装完以上三个jdk版本之后，重启一下电脑，然后进行下面的操作：

####1).先检查java安装情况

    sudo update-alternatives --display java
    sudo update-alternatives --display javac
显示结果如下（下面是我已经配置好的）
```bash
apar@G470 ~ $ sudo update-alternatives --display java
java - 手动模式
链接目前指向 /opt/jdk1.7.0_72/bin/java
/opt/jdk1.6.0_43/bin/java - 优先级 300
/opt/jdk1.7.0_72/bin/java - 优先级 400
/usr/lib/jvm/java-7-openjdk-amd64/bin/java - 优先级 500
目前“最佳”的版本为 /usr/lib/jvm/java-7-openjdk-amd64/bin/java。
apar@G470 ~ $ sudo update-alternatives --display javac
javac - 手动模式
链接目前指向 /opt/jdk1.7.0_72/bin/javac
/opt/jdk1.6.0_43/bin/javac - 优先级 300
/opt/jdk1.7.0_72/bin/javac - 优先级 400
/usr/lib/jvm/java-7-openjdk-amd64/bin/javac - 优先级 500
目前“最佳”的版本为 /usr/lib/jvm/java-7-openjdk-amd64/bin/javac。
apar@G470 ~ $
```
####2).删除符号链接

执行类似如下命令删除已经存在的符号链接

    sudo update-alternatives --remove java /opt/jdk1.6.0_43/bin/java
    sudo update-alternatives --remove javac /opt/jdk1.6.0_43/bin/javac

确认这些符号链接(symlinks)是否都删除了

    java -version
    javac -version

####3).重新配置java链接

执行类似如下命令

    sudo update-alternatives --install /usr/bin/java java /opt/jdk1.6.0_43/bin/java 300
    sudo update-alternatives --install /usr/bin/java java /opt/jdk1.7.0_72/bin/java 400
    sudo update-alternatives --install /usr/bin/java java /usr/lib/jvm/java-7-openjdk-amd64/bin/java 500

    sudo update-alternatives --install /usr/bin/javac javac /opt/jdk1.6.0_43/bin/javac 300
    sudo update-alternatives --install /usr/bin/javac javac /opt/jdk1.7.0_72/bin/javac 400
    sudo update-alternatives --install /usr/bin/javac javac /usr/lib/jvm/java-7-openjdk-amd64/bin/javac 500

####4).在需要的时候进行手动切换即可

    sudo update-alternatives --config java
    sudo update-alternatives --config javac

显示结果如下:
```bash
apar@G470 ~ $ sudo update-alternatives --config java
[sudo] password for apar:
有 3 个候选项可用于替换 java (提供 /usr/bin/java)。

  选择       路径                                      优先级  状态
------------------------------------------------------------
  0            /usr/lib/jvm/java-7-openjdk-amd64/bin/java   500       自动模式
  1            /opt/jdk1.6.0_43/bin/java                    300       手动模式
* 2            /opt/jdk1.7.0_72/bin/java                    400       手动模式
  3            /usr/lib/jvm/java-7-openjdk-amd64/bin/java   500       手动模式

要维持当前值[*]请按回车键，或者键入选择的编号：

apar@G470 ~ $ sudo update-alternatives --config javac
有 3 个候选项可用于替换 javac (提供 /usr/bin/javac)。

  选择       路径                                       优先级  状态
------------------------------------------------------------
  0            /usr/lib/jvm/java-7-openjdk-amd64/bin/javac   500       自动模式
  1            /opt/jdk1.6.0_43/bin/javac                    300       手动模式
* 2            /opt/jdk1.7.0_72/bin/javac                    400       手动模式
  3            /usr/lib/jvm/java-7-openjdk-amd64/bin/javac   500       手动模式

要维持当前值[*]请按回车键，或者键入选择的编号：
```

在需要的时候根据显示的结果进行选择切换即可，注意java跟javac要对应的切换！
