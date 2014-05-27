---
layout: post
title: "Linux执行bundle install出现的问题解决"
date: 2014-05-27 19:50:49 +0800
comments: true
categories: octopress
---
####今天配置好了系统，然后想把`octopress`也重新搞好，在执行`bundle install`时出现了下面的错误
<!--more-->
{% img http://yusan.qiniudn.com/2014-05-27%2019:49:17%E7%9A%84%E5%B1%8F%E5%B9%95%E6%88%AA%E5%9B%BE.png 'bundle install' %}
####于是上网找解决办法，差不多找到了[类似的问题](http://tarashish.com/blog/2013/02/02/fixing-mkmf-load-error-ubuntu/)，下面有解决的办法，按照那个说的搞定了，顺便写下来记录一下!
####即安装ruby-dev版本，终端执行：
    sudo apt-get install ruby1.9.1-dev
{% img http://yusan.qiniudn.com/2014-05-27%2019:49:33%E7%9A%84%E5%B1%8F%E5%B9%95%E6%88%AA%E5%9B%BE.png ‘install ruby-dev' %}
####问题解决！