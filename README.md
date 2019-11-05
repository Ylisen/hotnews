# hotnews-log-real-time-analysis

### 项目描述    
本项目是一个完整的大数据项目实战，实时|离线统计分析用户的搜索话题，并用JavaEE工程前端界面展示出来。这些指标对网站的精准营销、运营都有极大帮助。架构大致是按照企业标准来的，从日志的采集、转化处理、实时计算、JAVA后台开发、WEB前端展示，一条完整流程线下来，甚至每个节点都用的高可用架构，都考虑了故障转移和容错性。

### 项目技术栈   
Flume + KafKa + Hbase + Hive + Spark(SQL、Structured Streaming)    
Mysql + SpringMVC + Mybatis + Websocket + AugularJs + Echarts    
JAVA + Scala + Shell   

### 项目环境    
Linux、 win、 idea   

### 项目基本流程
#### 一、数据处理
利用SAXReader获取xml文件内容，清洗内容并构建News实体类以便写入txt文件，然后编写ReadWebLog类并编写脚本运行在Liunx上模拟新闻搜索日志产生
~~~
Liunx运行jar命令：java -jar readNews.jar  args0 args1
~~~

#### 二、Flume与HBase、Kafka数据对接    
* Flume采集源数据与Kafka集成 --> Kafka与Spark Streaming对接 --> Spark+MySQL完成实时计算分析  -->  前台Echart展示     
* Flume采集源数据与HBase集成 -->  HBase与Hive对接  -->  Hadoop MapReduce 完成离线计算分析  -->  前台Echart展示
  

#### 三、Kafka + Spark Streaming + MySQL实时计算分析
实时：话题浏览量       
1、数据库连接池编写    
2、spark streaming 程序读取kafka数据
3、spark streamign 实时计算处理后的数据写入MySQL       
实时分析思路：          
从Kafka读取数据后 --> 新闻数据 --> 将value映射为Map[String,String] --> 分割、根据key分组、聚合 --> 根据key值写sql --> 保存于MySQL


#### 四、Kafka + HBase + Hive(Hadoop) 离线计算分析
离线：日访问量、话题数    
1、Kafka与HBase对接   
2、HBase与Hive对接  
处理思路：在Hive创建外部表weblogs连接HBase对应表weblogs      
离线分析思路：    
数据高速存入HBase --> 通过外部表同步至Hive --> 书写sql完成数据离线统计 --> 选择时间间隔存入MySQL --> 前台展示          


#### 五、前端展示(SSM+Echarts) 
1、SSM工程搭建       
2、采用WebSocket全双工通信方式使前端与后端实时交互



#### 六、效果图    
![png](/png)  







