---
layout: post
title: "Zookeeper集群搭建（伪集群）"
subtitle: 'Zookeeper集群搭建教程'
author: "Oumuv"
date:   2018-11-26 12:00:00
header-img:   "img/about-bg.jpg"
header-mask:  0.3
catalog:      true
tags:
  - Zookeeper
  - 架构
---
环境要求
===
- jdk8
- zookeeper3.4
- Linux or mac系统

步骤
===

一、安装jdk8：参考 [Linux安装jdk8并配置环境变量](https://blog.csdn.net/oumuv/article/details/83856541)
---

二、下载Zookeeper安装包
---

- 下载地址：[http://mirrors.hust.edu.cn/apache/zookeeper/](http://mirrors.hust.edu.cn/apache/zookeeper/)

三、Zookeeper集群搭建
---

### 前提

zookeeper的集群搭建一般需要配置三台机器，本地搭建三台zookeeper，约定如下：

zookeeper | 编号 | 端口号
:----: | :----: |:----:
zookeeper1 | 0 | 2181
zookeeper2 | 1 | 2182
zookeeper3 | 2 | 2183

- 1、点位到安装包所在目录，解压安装包

>    tar -zxvf zookeeper-3.4.10.tar.gz

- 2、修改文件名为zookeeper1

> mv zookeeper-3.4.10 zookeeper1

- 3、进入到解压后的安装包目录，修改配置文件：

    - ①新建一个data文件夹作为zookeeper的数据存储文件夹

    > mkdir data

    - ②重命名配置文件

    > mv conf/zoo_sample.cfg  conf/zoo.cfg

    - ③修改zoo.cfg

    > vim conf/zoo.cfg

    修改两个位置

    ![](https://raw.githubusercontent.com/Oumuv/oumuv.github.io/master/img/2018/11/26/1.png)​

    > dataDir 修改为该zookeeper的data位置   
    > clientPort zookeeper的端口号

    加入配置
```
     server.0=127.0.0.1:2888:3888
     server.1=127.0.0.1:2888:3888
     server.2=127.0.0.1:2888:3888
```

    解释：server.[zookeeper的编号]=[ip地址]:[通信端口]:[选举端口]


- 4、创建myid（这个文件里的内容就是zookeeper的编号）

    在data目录下创建一个myid文件，里面的内容是zookeeper的编号
    - 直接使用命令 echo 0 > myid
    - 查看是否成功创建 cat myid  
    ![](https://raw.githubusercontent.com/Oumuv/oumuv.github.io/master/img/2018/11/26/2.png)​

- 5、搭建另外两个zookeeper

    - 1、可以直接使用第一个zookeeper（zookeeper1）作为基础搭建另外的两个：
    ```
    cp -r zookeeper1 zookeeper2    
    cp -r zookeeper1 zookeeper3
    ```
    - 2、分别修改zookeeper2和zookeeper3的zoo.cfg

    zookeeper2：   
    ![](https://raw.githubusercontent.com/Oumuv/oumuv.github.io/master/img/2018/11/26/3.png)​

    zookeeper3：   
    ![](https://raw.githubusercontent.com/Oumuv/oumuv.github.io/master/img/2018/11/26/4.png)​

    - 3、分别修改zookeeper2和zookeeper3的myid

    zookeeper2的编号为1：
    > echo 1 > myid

    zookeeper3的编号为2：
    > echo 2 > myid

四、启动、测试
---

- 编写一个启动三个zookeeper的脚本

> vim startup-zoo.sh

```
cd /Users/oumuv/solr/zookeeper1/bin
zkServer.sh start
cd /Users/oumuv/solr/zookeeper2/bin
zkServer.sh start
cd /Users/oumuv/solr/zookeeper3/bin
zkServer.sh start
```


赋予执行权限
> chmod 755 startup-zoo.sh

-------

- 编写一个停止三个zookeeper的脚本

> vim shutdown-zoo.sh

```
cd /Users/oumuv/solr/zookeeper1/bin
zkServer.sh stop
cd /Users/oumuv/solr/zookeeper2/bin
zkServer.sh stop
cd /Users/oumuv/solr/zookeeper3/bin
zkServer.sh stop
```

赋予执行权限
> chmod 755 shutdown-zoo.sh

- 执行启动脚本

> ./startup-zoo.sh

下图所示则zookeeper集群启动成功   
![](https://raw.githubusercontent.com/Oumuv/oumuv.github.io/master/img/2018/11/26/5.png)​

分别在三个zookeeper的bin中执行 zkServer.sh status 命令，查看启动情况

![](https://raw.githubusercontent.com/Oumuv/oumuv.github.io/master/img/2018/11/26/6.png)​

(follower和leader的顺序可能会有所不同，这个是zookeeper内部选举机制决定的，有兴趣可以去了解一下zookeeper的选举机制)

- 执行停止脚本停止zookeeper

> ./shutdown-zoo.sh

到此集群搭建成功！
=========