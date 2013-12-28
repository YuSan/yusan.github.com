---
layout: post
title: "在多台机子上写octopress博客"
date: 2013-12-10 22:37
comments: true
categories: octopress
---
---
####因为电脑装的双系统，有时候需要切换使用，为了方便写博客，在两个系统下面都搞好了环境，可是切换系统之后因为源码不一致，会出错，so，百度之～～
<!--more-->
* Octopress的git仓库(repository)有两个分支，分别是master和source。

* master存储的是博客网站本身，而source存储的是生成博客的源文件。

* master的内容放在根目录的_deploy文件夹内，当你push源文件时会忽略，它使用的是rake deploy命令来更新的。

* 如果几台电脑上面都配置好了Otcopress，要在其中一台上写博客,需要进行同步，更新source仓库即可。更新master并不是必须的，因为更改源文件之后还是需要rake generate，这个时候会自动进行 master更新。

```bash
cd your_local_octopress_directory
cd _deploy
git pull origin master   # update the local master branch 
cd ..
git pull origin source   # update the local source branch  
```
--------------------------------------------------
##### 参考文章：1、[Blog of GangMax](http://gangmax.me/blog/2011/11/24/setup-local-environment-for-an-existing-octopress-instance-on-github/)  2、[HAN Kai](http://blog.csdn.net/hankai1024/article/details/12786201)