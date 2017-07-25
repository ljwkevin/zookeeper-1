# zookeeper简介
经典博文:
1. [ZooKeeper学习第一期---Zookeeper简单介绍](http://www.cnblogs.com/wuxl360/p/5817471.html)
2. [ZooKeeper学习第二期--ZooKeeper安装配置](http://www.cnblogs.com/wuxl360/p/5817489.html)



# zookeeper安装

### 1.安装JDK
1. 检查java -version，如果没有安装过会有系统安装的openjdk，需要卸载
     rmp -qa | grep java 检查然后执行rpm -e --nodeps **** 卸载
2. 安装新的jdk
    [参考linux安装jdk博客](http://www.linuxidc.com/Linux/2016-09/134941.htm) 
### 2.安装单机zookeeper
1. 解压 tar -zxvf zookeeper-3.4.5.tar.gz
2. 修改配置文件zoo.cfg
3. 启动查看状态
### 3.伪集群zookeeper
 1. 创建data在data下创建myid，myid内容0
    创建data_1在data_1下创建myid，myid内容1
    创建data_2在data_2下创建myid，myid内容2
    同时创建datalog_1,datalog_2
2. 复制zoo.cfg文件为zoo_1.cfg,zoo_2.cfg
   修改配置文件中的对应数据和日志目录
   修改端口号为2181,2182,2183
   在3个配置配置文件中添加
   server.0=localhost:2287:3387
   server.1=localhost:2288:3388
   server.2=localhost:2289:3389
3. 启动服务
  zkServer.sh start zoo.cfg
  zkServer.sh start zoo_1.cfg
  zkServer.sh start zoo_2.cfg
4. 查看集群状态
  zkServer.sh status zoo.cfg
  zkServer.sh status zoo_1.cfg
  zkServer.sh status zoo_2.cfg

  


