---
layout: post
title: "Linux下sublime_text的安装与使用"
date: 2014-05-24 18:31:35 +0800
comments: true
categories: software
---
{% img left http://yusan.qiniudn.com/blog2014-05-24%2020:18:38%E7%9A%84%E5%B1%8F%E5%B9%95%E6%88%AA%E5%9B%BE.png 270 260 'sublime_text 3059' %}
####`Sublime_text`，一个跨平台的代码编辑器。刚买电脑的时候在网上看到然后安装过，因为功能强大，作为小白的我看了看然后就卸载了，因为我不会用！那时候是在`Windows`下，我还有别的编辑器可以用，比如Notepad++，还有Emediter等软件都是不错的。
<!--more-->
####后来因为想学点安卓的东西，所以装了linux，一直小白的我不会用vim和Emacs，就用系统自带的`gedit`，觉得还是很好的，因为很多代码都支持高亮的。
####再后来想看 **smali** 文件,所以想找个好用的编辑器来高亮显示代码，所以找啊找，最后又找到了`Sublime_Text`，因为它支持插件，可以安装插件来支持 **smali** 代码高亮显示.
{% img http://yusan.qiniudn.com/blog2014-05-24%2020:37:49%E7%9A%84%E5%B1%8F%E5%B9%95%E6%88%AA%E5%9B%BE.png 'smali代码高亮显示' %}
软件安装：
----
####Sublime_text的下载和安装挺简单的，直接到[Sublime Text官网](http://www.sublimetext.com/)选择下载即可！或者直接下载{%highlight Sublime_Text 3(Build 3059)%}:[32bit](http://c758482.r82.cf2.rackcdn.com/sublime-text_build-3059_i386.deb)|[64bit](http://c758482.r82.cf2.rackcdn.com/sublime-text_build-3059_amd64.deb)。然后在终端执行下面的命令安装即可！
    sudo dpkg -i *.deb
软件破解：
----
####因为软件是收费的（可以无限期试用），所以又找了一下破解，在[看雪论坛](http://bbs.pediy.com/showthread.php?t=182774)上有破解的帖子，下载破解文件([32bit](http://yun.baidu.com/share/link?shareid=3756674317&uk=2986591212)|[64bit](http://yun.baidu.com/share/link?shareid=3762073257&uk=2986591212))更面并替换原来安装的文件即可破解！安装文件路径在 **/opt/sublime_text/** 下。
解决中文输入：
----
####然后还有一个很头疼的问题就是在Sublime_text里面无法输入中文，为了解决这个问题，找了好久，最后成功了：下载此[文件](http://yusan.qiniudn.com/Sublime_Text_imfix.tar),解压文件到任意路径，并复制库文件到安装路径`/opt/sublime_text/`下，然后将Desktop文件复制到`/usr/share/applications/`替换里面的文件
    sudo cp libsublime-imfix.so /opt/sublime_text/.
    sudo cp sublime_text.desktop  /usr/share/applications/.
{% img http://yusan.qiniudn.com/blog2014-05-24%2022:22:38%E7%9A%84%E5%B1%8F%E5%B9%95%E6%88%AA%E5%9B%BE.png '输入中文' %}

{%ribbonp warning 提示:%}
如果按照上述步骤做完了还是不能在`Sublime`输入中文，试试安装`gtk+-2.0`
{%endribbonp%}
    sudo apt-get install gtk+-2.0
{%img http://yusan.qiniudn.com/2014-05-27%2022:20:56%E7%9A%84%E5%B1%8F%E5%B9%95%E6%88%AA%E5%9B%BE.png '安装gtk+-2.0' %}
在终端打开：
----
####解决了中文输入的问题之后，就可以正常使用了。但是怎么让sublime_text在终端可以执行命令打开呢？又百度了一下：在 **/usr/bin/** 下建立它的链接即可，在终端执行下面的命令即可：
    sudo ln -s /opt/sublime_text/sublime_text /usr/bin/sublime
####这样就可以直接在终端输入``sublime``命令打开Sublime_Text编辑器了！