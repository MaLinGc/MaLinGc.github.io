---
title: Centos 7 下JDK 安装
date: 2018-01-20 14:45:29
categories: linux
tags: 
    - centos
    - java
    - jdk
---
1. 查找并删除以前的版本
```
rpm -qa|grep jdk
```
```
rpm -e  --nodeps java-1.7.0-openjdk-headless-1.7.0.111-2.6.7.2.el7_2.x86_64（注意这里nodeps后面的那串名称是通过上面命令查询出来的，查出几个卸载几个）
```
2. 安装jdk
```
rpm -ivh jdk-8u151-linux-x64.rpm
```
3. 检查安装，以及配置环境变量,
```
which java #查找并显示给定命令的绝对路径
```
```
ls -lrt /usr/bin/java
```
```
ls -lrt /etc/alternatives/java
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

```shell
source /etc/profile   
echo $PATH
```