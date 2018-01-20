---
title: Linux tar命令详解
date: 2018-01-20 16:34:51
categories: Linux常用命令
tags:
    - Linux
---
### tar 用途说明
Linux下的归档使用工具，用来打包和备份。**tar**命令 可以为linux的文件和目录创建档案。利用tar，可以为某一特定文件创建档案（备份文件），也可以在档案中改变文件，或者向档案中加入新的文件。tar最初被用来在磁带上创建档案，现在，用户可以在任何设备上创建档案。利用tar命令，可以把一大堆的文件和目录全部打包成一个文件，这对于备份文件或将几个文件组合成为一个文件以便于网络传输是非常有用的。

### 概念说明

- **打包**是指将一大堆文件或目录变成一个总的文件
- **压缩**则是将一个大的文件通过一些压缩算法变成一个小文件

Linux中很多压缩程序只能针对一个文件进行压缩，这样当你想要压缩一大堆文件时，你得先将这一大堆文件先打成一个包（tar命令），然后再用压缩程序进行压缩（gzip bzip2命令）

#### 语法
```bash
$ tar -[cxtZzJjahmvO] [-X FILE] [-T FILE] [-f TARFILE] [-C DIR] [FILE]...
```

#### 选项
```
-A或--catenate：新增文件到以存在的备份文件；
-B：设置区块大小；
-c或--create：建立新的备份文件；
-C <目录>：这个选项用在解压缩，若要在特定目录解压缩，可以使用这个选项。
-d：记录文件的差别；
-x或--extract或--get：从备份文件中还原文件；
-t或--list：列出备份文件的内容；
-z或--gzip或--ungzip：通过gzip指令处理备份文件；
-Z或--compress或--uncompress：通过compress指令处理备份文件；
-f<备份文件>或--file=<备份文件>：指定备份文件；
-v或--verbose：显示指令执行过程；
-r：添加文件到已经压缩的文件；
-u：添加改变了和现有的文件到已经存在的压缩文件；
-j：支持bzip2解压文件；
-v：显示操作过程；
-l：文件系统边界设置；
-k：保留原有文件不覆盖；
-m：保留文件不被覆盖；
-w：确认压缩文件的正确性；
-p或--same-permissions：用原来的文件权限还原文件；
-P或--absolute-names：文件名使用绝对名称，不移除文件名称前的“/”号；
-N <日期格式> 或 --newer=<日期时间>：只将较指定日期更新的文件保存到备份文件里；
--exclude=<范本样式>：排除符合范本样式的文件。
```

#### 范例
1. 查看
```bash
$ tar -tf aaa.tar.gz  #在不解压的情况下查看压缩包的内容  
```

2. 压缩
```bash
$ tar –cvf jpg.tar *.jpg        #将目录里所有jpg文件打包成tar.jpg  
$ tar –czf jpg.tar.gz *.jpg     #将目录里所有jpg文件打包成jpg.tar后，并且将其用gzip压缩，生成一个gzip压缩过的包，命名为jpg.tar.gz  
$ tar –cjf jpg.tar.bz2 *.jpg    #将目录里所有jpg文件打包成jpg.tar后，并且将其用bzip2压缩，生成一个bzip2压缩过的包，命名为jpg.tar.bz2  
$ tar –cZf jpg.tar.Z *.jpg      #将目录里所有jpg文件打包成jpg.tar后，并且将其用compress压缩，生成一个umcompress压缩过的包，命名为jpg.tar.Z  
```

3. 解压
```bash
$ tar –xvf file.tar         #解压 tar包  
$ tar -zxvf file.tar.gz     #解压tar.gz  
$ tar -jxvf file.tar.bz2    #解压 tar.bz2  
$ tar –Zxvf file.tar.Z      #解压tar.Z  
```

#### 各种格式的使用范例

```
01-.tar格式
解包：$ tar xvf FileName.tar
打包：$ tar cvf FileName.tar DirName（注：tar是打包，不是压缩！）

02-.gz格式
解压1：$ gunzip FileName.gz
解压2：$ gzip -d FileName.gz
压 缩：$ gzip FileName

03-.tar.gz格式
解压：$ tar zxvf FileName.tar.gz
压缩：$ tar zcvf FileName.tar.gz DirName

04-.bz2格式
解压1：$ bzip2 -d FileName.bz2
解压2：$ bunzip2 FileName.bz2
压 缩： $ bzip2 -z FileName

05-.tar.bz2格式
解压：$ tar jxvf FileName.tar.bz2
压缩：$ tar jcvf FileName.tar.bz2 DirName

06-.bz格式
解压1：$ bzip2 -d FileName.bz
解压2：$ bunzip2 FileName.bz

07-.tar.bz格式
解压：$ tar jxvf FileName.tar.bz

08-.Z格式
解压：$ uncompress FileName.Z
压缩：$ compress FileName

09-.tar.Z格式
解压：$ tar Zxvf FileName.tar.Z
压缩：$ tar Zcvf FileName.tar.Z DirName

10-.tgz格式
解压：$ tar zxvf FileName.tgz

11-.tar.tgz格式
解压：$ tar zxvf FileName.tar.tgz
压缩：$ tar zcvf FileName.tar.tgz FileName

12-.zip格式
解压：$ unzip FileName.zip
压缩：$ zip FileName.zip DirName

13-.lha格式
解压：$ lha -e FileName.lha
压缩：$ lha -a FileName.lha FileName

14-.rar格式
解压：$ rar a FileName.rar
压缩：$ rar e FileName.rar      
rar请到：下载！
解压后请将rar_static拷贝到/usr/bin目录（其他由$PATH环境变量
指定的目录也行）：$ cp rar_static /usr/bin/rar
```
