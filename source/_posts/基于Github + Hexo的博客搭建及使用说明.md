---
title: 基于Github + Hexo的博客搭建及使用说明
categories: Hexo
tags: 
    - Hexo
---
记录如何使用Github + Hexo 搭建个人博客， 同时在不同的终端进行博客发布更新！

## Hexo

### Hexo 博客安装配置

Hexo 的安装非常简单，网上有很多教程 [官网](https://hexo.io/docs/setup.html)

### MiHo-主题安装配置

MiHo 是一款单栏响应式的Hexo主题；基于 Hexo 3.0+ 制作，兼容移动端浏览；如何安装配置参考[MiHo主题安装配置教程](https://blog.minhow.com/2017/08/01/blog/installation-configuration/#%E4%B8%89-%E7%AB%99%E7%82%B9%E9%85%8D%E7%BD%AE)

### 多终端同步问题解决方案

参考教程 [如何解决github+Hexo的博客多终端同步问题参照](http://blog.csdn.net/Monkey_LZL/article/details/60870891)

```bash
$ git clone -b hexo git@github.com:yourname/yourname.github.io.git  #将Github中hexo分支clone到本地
$ cd yourname.github.io  #切换到刚刚clone的文件夹内
$ npm install    #注意，这里一定要切换到刚刚clone的文件夹内执行，安装必要的所需组件，不用再init
$ hexo new post "new blog name"   #新建一个.md文件，并编辑完成自己的博客内容
$ git add source  #经测试每次只要更新sorcerer中的文件到Github中即可，因为只是新建了一篇新博客
$ git commit -m "XX"
$ git push origin hexo  #更新分支
$ hexo d -g   #push更新完分支之后将自己写的博客对接到自己搭的博客网站上，同时同步了Github中的master
```

## Hexo blog 写法
```
---
title: Hello World
date: 2017-06-18
categories: First
author: MinHow
tags:
    - First
    - Second
cover_picture: /images/banner.jpg
---
 MinHow-This is a summary
<!-- more -->
```