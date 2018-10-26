# my-repo
### 虚拟环境
IP|主机名|节点|部署
:----:|:----:|:----:|:----:
192.168.1.14|server01|Zookeeper<br>Hadoop<br>HBase<br>Hive<br>Sqoop<br>PXC<br>myCat|分布式<br>分布式<br>分布式<br>单机<br>单机<br>分布式<br>单机
192.168.1.15|server02|Zookeeper<br>Hadoop<br>HBase<br>PXC|分布式<br>分布式<br>分布式<br>分布式
192.168.1.16|server03|Zookeeper<br>Hadoop<br>HBase<br>PXC<br>Haproxy|分布式<br>分布式<br>分布式<br>分布式<br>单机

#### 192.168.1.14 server01
* Zookeeper **(server.0)**
```
ZOOKEEPER_HOME=/usr/local/zookeeper-3.4.12
```
* Hadoop **(DataNode,NameNode)**
```
HADOOP_HOME=/home/hadoop/hadoop-2.8.5
```
* HBase **(HMaster、HRegionServer)**
```
HBASE_HOME=/usr/local/hbase-2.0.2
```
* Hive **(单机)**
```
HIVE_HOME=/home/hadoop/hive-2.3.3-bin
```
* Sqoop **(单机)**
```
SQOOP_HOME=/usr/local/sqoop-1.4.7
```
* PXC **(server-id=143306)**
* myCat **(8066)**

#### 192.168.1.15 server02
* Zookeeper **(server.1)**
```
ZOOKEEPER_HOME=/usr/local/zookeeper-3.4.12
```
* Hadoop **(DataNode,SecondaryNameNode)**
```
HADOOP_HOME=/home/hadoop/hadoop-2.8.5
```
* HBase **(HRegionServer)**
```
HBASE_HOME=/usr/local/hbase-2.0.2
```
* PXC **(server-id=153306)**


#### 192.168.1.16 server03
* Zookeeper **(server.2)**
```
ZOOKEEPER_HOME=/usr/local/zookeeper-3.4.12
```
* Hadoop **(DataNode,ResourceManager)**
```
HADOOP_HOME=/home/hadoop/hadoop-2.8.5
```
* HBase **(HRegionServer)**
```
HBASE_HOME=/usr/local/hbase-2.0.2
```
* PXC **(server-id=163306)**
# Haproxy **(3307,3077)**




