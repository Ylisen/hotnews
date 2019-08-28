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
-- Flume采集数据源数据与HBase集成    
       HBase与Hive对接      
           Hadoop MapReduce 完成离线计算分析    
                  前台Echart    
