---
title: Centos 7安装Oracle Java JDK 8
date: 2018-01-20 14:45:29
categories: Centos7 WEB 服务器搭建部署
tags: 
    - Linux
    - Java
---
### 一. 查找并删除以前的版本
1. 查看当前系统个是否安装了jdk
```bash
$ rpm -qa|grep jdk
```
2. 卸载已安装的库
```
$ rpm -e  --nodeps java-1.7.0-openjdk-headless-1.7.0.111-2.6.7.2.el7_2.x86_64（注意这里nodeps后面的那串名称是通过上面命令查询出来的，查出几个卸载几个）
```
### 二. 安装jdk
1. 前往oracle 官网下载rpm包
> jdk无法直接通过wget命令下载，可以通过浏览器进行下载rpm包然后上传至服务器，或者通过浏览器查看下载链接，直接在服务器上使用wget命令进行下载

```bash
$ wget -O jdk-8u151-linux-x64.rpm http://download.oracle.com/otn-pub/java/jdk/8u151-b12/e758a0de34e24606bca991d704f6dcbf/jdk-8u151-linux-x64.rpm?AuthParam=1516433290_757b25ac7249fbf158433d7b0ba98d82  
```

2. 安装包
```
$ rpm -ivh jdk-8u151-linux-x64.rpm
```

3. 检查安装，以及配置环境变量
```bash
$ which java #查找并显示给定命令的绝对路径
$ ls -lrt /usr/bin/java
$ ls -lrt /etc/alternatives/java
```

4. 添加环境变量
> vi /etc/profile文件,最后添加一下配置

```
JAVA_HOME=/usr/java/jdk1.8.0_151
JRE_HOME=/usr/java/jdk1.8.0_151/jre
CLASSPATH=$JAVA_HOME/lib:$JRE_HOME/lib:$CLASSPATH
PATH=$JAVA_HOME/bin:$JRE_HOME/bin:$PATH
export JAVA_HOME JRE_HOME PATH CLASSPATH
```

> 使修改立即生效

```bash
$ source /etc/profile   
$ echo $PATH
```