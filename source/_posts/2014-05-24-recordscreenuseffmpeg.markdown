---
layout: post
title: "Linux下使用FFmpeg进行屏幕录像"
date: 2014-05-24 14:43:56 +0800
comments: true
categories: Linux
---
{% img http://yusan.qiniudn.com/2014-05-24%2014:49:23%E7%9A%84%E5%B1%8F%E5%B9%95%E6%88%AA%E5%9B%BE.png '我的电脑配置及系统信息' %}
<!--more-->
####去年刚装好LinuxMint的时候，这个linux发行版特别棒!让我觉得这个系统很棒的其中一个很大的原因就是它很简单的支持各种小应用的添加，我把系统配置好之后感觉用这特别顺手！
我装了一个屏幕录像的小程序，上一篇博文里面的那个编译recovery的视频就是用这个小程序录制的，可是奇怪的是好像从那次之后我再想录制屏幕就不行了，甚至把它卸载并重装了好几次都不行，也试了其他的，感觉都不好用。最后看了下那个小程序的代码，原来是执行一个`shell`脚本来调用{%highlight ffmpeg%}录制屏幕的，在网上查了一番，才知道{%highlight ffmpeg%}真的好强大！可是我手动执行那个脚本却还是不行，然后按照里面的代码在终端执行，并把文件名命名的很简单，居然成功了，最后才明白原来是作者的那个脚本里面文件命名有问题导致的录像失败，命名是采用当前时间的，代码有一点点小问题，所以导致了失败.
{%ribbonp info Code%}
下面贴上代码，也可以点代码框右上角直接下载脚本!
{%endribbonp%}
``` bash Record Screen use FFmpeg without Audio http://yusan.qiniudn.com/blogscreencapture.sh Download
#!/bin/bash
if [ ! -e $HOME/Videos ]
then
mkdir -p $HOME/Videos
fi
dir="$HOME/Videos"
size=$( xdpyinfo | grep 'dimensions:' | awk '{print $2}' )
name=$( date +'%F_%I:%M' )
video="$dir/$name.mkv"
ffmpeg -f x11grab -s $size -r 35 -qscale 1  -i :0.0 $video
```
```bash Record Screen use FFmpeg with Audio http://yusan.qiniudn.com/blogscreencapturesound.sh Download
#!/bin/bash
if [ ! -e $HOME/Videos ]
then
mkdir -p $HOME/Videos
fi
dir="$HOME/Videos"
size=$( xdpyinfo | grep 'dimensions:' | awk '{print $2}' )
name=$( date +'%F_%I:%M' )
video="$dir/$name.mkv"
ffmpeg -f alsa -ac 2 -i pulse -f x11grab -s $size -r 35 -qscale 1  -i :0.0 $video
```
录制样例：
{% video http://yusan.qiniudn.com/blog2014-05-24_03:15.m4v 640 320 http://yusan.qiniudn.com/blog2014-05-24%2015:20:07%E7%9A%84%E5%B1%8F%E5%B9%95%E6%88%AA%E5%9B%BE.png %}

{%ribbonp info FFmpeg%}
FFmpeg is a very great tool!
{%endribbonp%}