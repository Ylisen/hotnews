# hotnews-log-real-time-analysis

## 项目描述

## 项目技术栈

## 项目环境

## 项目基本流程
#### 一、数据处理
利用SAXReader获取xml文件内容，清洗内容并构建News实体类以便写入txt文件，然后编写ReadWebLog类并编写脚本运行在Liunx上模拟新闻搜索日志产生
~~~
Liunx运行jar命令：java -jar readNews.jar  args0 args1
~~~

#### 二、Flume与HBase、Kafka数据对接
* Flume采集源数据与HBase集成 -->  HBase与Hive对接  -->  Hadoop MapReduce 完成离线计算分析  -->  前台Echart展示
* Flume采集源数据与Kafka集成 --> Kafka与Spark Streaming对接 --> Spark+MySQL完成实时计算分析  -->  前台Echart展示      
离线：日访问量、话题数   
实时：话题浏览量   


### 三、Kafka+Spark Streaming + MySQL实时计算分析
1、数据库连接池编写    
2、spark streaming 程序读取kafka数据
3、spark streamign 实时计算处理后的数据写入MySQL       
细节：
从Kafka读取数据后 --> 新闻数据 --> 将value映射为Map[String,String] --> 分割、根据key分组、聚合 --> 根据key值写入sql --> 保存于MySQL
