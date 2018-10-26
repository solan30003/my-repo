# my-repo
### 虚拟环境
IP|主机名|Zookeeper|Hadoop|HBase|Hive
:----:|:----:|:----|:----|:----|:----
192.168.1.14|server01|server.0|Name|HMaster、HRegionServer|Hive
192.168.1.15|server02|server.1||HRegionServer|
192.168.1.16|server03|server.2||HRegionServer|
#### 192.168.1.14 server01
* Zookeeper **server.0**
```
ZOOKEEPER_HOME=/usr/local/zookeeper-3.4.12
```
* Hadoop **DataNode,NameNode**
```
HADOOP_HOME=/home/hadoop/hadoop-2.8.5
```
* HBase **HMaster、HRegionServer**
```
HBASE_HOME=/usr/local/hbase-2.0.2
```
* Hive **单机**
```
HIVE_HOME=/home/hadoop/hive-2.3.3-bin
```
* Sqoop **单机**
```
SQOOP_HOME=/usr/local/sqoop-1.4.7
```
#### 192.168.1.15 server02
* Zookeeper **server.1**
```
ZOOKEEPER_HOME=/usr/local/zookeeper-3.4.12
```
* Hadoop **DataNode,SecondaryNameNode**
```
HADOOP_HOME=/home/hadoop/hadoop-2.8.5
```
* HBase **HRegionServer**
```
HBASE_HOME=/usr/local/hbase-2.0.2
```



#### 192.168.1.16 server03
* Zookeeper **[server.2]**
```
ZOOKEEPER_HOME=/usr/local/zookeeper-3.4.12
```
* Hadoop **[DataNode,ResourceManager]**
```
HADOOP_HOME=/home/hadoop/hadoop-2.8.5
```
* HBase **[HRegionServer]**
```
HBASE_HOME=/usr/local/hbase-2.0.2
```




