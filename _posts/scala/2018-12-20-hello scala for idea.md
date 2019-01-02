---
layout: post
title: "Scala（一）使用IntelliJ IDEA创建Scala项目"
subtitle: 'Scala初体验'
author: "Oumuv"
date:   2018-12-20 12:00:00
header-img:   "img/about-bg.jpg"
header-mask:  0.3
catalog:      true
tags:
  - Scala
  - IDEA
---
# 环境要求
* JDK
* Scala

Scala环境安装参考：http://www.runoob.com/scala/scala-install.html

# Scala插件下载与安装
IDEA开发Scala需要安装Scala插件，插件安装方法如下：
### 方法一（在线安装）：
File-->Settings-->Plugins   
![在这里插入图片描述](https://raw.githubusercontent.com/Oumuv/oumuv.git.res/master/resources/img/2018/12/20/21.png)

搜索“Scala”，点击install安装，等待安装完成后重启IDEA即可   
![在这里插入图片描述](https://raw.githubusercontent.com/Oumuv/oumuv.git.res/master/resources/img/2018/12/20/22.png)

### 方法二（离线安装）：
在 https://plugins.jetbrains.com/plugin/1347-scala 中下载对应idea版本的插件包：   
![在这里插入图片描述](https://raw.githubusercontent.com/Oumuv/oumuv.git.res/master/resources/img/2018/12/20/23.png)

File-->Settings-->Plugins，点install plugin from disk，选中刚刚下载的的插件包安装后重启idea即可。   
![在这里插入图片描述](https://raw.githubusercontent.com/Oumuv/oumuv.git.res/master/resources/img/2018/12/20/24.png)

# 创建一个Scala项目

## 一、使用SBT创建Scala项目
点击create new project--> Scala--> sbt（Simple Build Tool）SBT是SCALA平台的项目构建工具，比Maven更简洁、比IVY更为灵活。   
![在这里插入图片描述](https://raw.githubusercontent.com/Oumuv/oumuv.git.res/master/resources/img/2018/12/20/25.png)

输入项目名，选择sbt版本、scala版本，点机Finish完成项目创建   
![在这里插入图片描述](https://raw.githubusercontent.com/Oumuv/oumuv.git.res/master/resources/img/2018/12/20/26.png)

创建成功后项目的结构如下所示：   
![在这里插入图片描述](https://raw.githubusercontent.com/Oumuv/oumuv.git.res/master/resources/img/2018/12/20/27.png)

File-->project structure-->Libraries，添加scala SDK   
![在这里插入图片描述](https://raw.githubusercontent.com/Oumuv/oumuv.git.res/master/resources/img/2018/12/20/28.png)   
![在这里插入图片描述](https://raw.githubusercontent.com/Oumuv/oumuv.git.res/master/resources/img/2018/12/20/29.png)

选中对应的scala SDK版本，然后点ok   
![在这里插入图片描述](https://raw.githubusercontent.com/Oumuv/oumuv.git.res/master/resources/img/2018/12/20/230.png)

完成这一步后项目结构会发生一些变化：   
![在这里插入图片描述](https://raw.githubusercontent.com/Oumuv/oumuv.git.res/master/resources/img/2018/12/20/231.png)

### 测试
新建一个HelloScala：   
![在这里插入图片描述](https://raw.githubusercontent.com/Oumuv/oumuv.git.res/master/resources/img/2018/12/20/232.png)

注意这里创建的是一个Object：   
![在这里插入图片描述](https://raw.githubusercontent.com/Oumuv/oumuv.git.res/master/resources/img/2018/12/20/233.png)

创建一个main方法，并且运行方法:   
![在这里插入图片描述](https://raw.githubusercontent.com/Oumuv/oumuv.git.res/master/resources/img/2018/12/20/234.png)

控制台成功输出，项目搭建成功！   
![在这里插入图片描述](https://raw.githubusercontent.com/Oumuv/oumuv.git.res/master/resources/img/2018/12/20/235.png)
