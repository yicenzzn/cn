当消费堆积或倾斜时，您可以查看Consumer group管理，查看Topic各个分区的消费进度，了解消息的堆积总量，及时调整业务，预防风险。

## 查看Topic被订阅的Group
1. 登录消息队列Kafka版控制台。
2. 在概览页面的资源分布区域，选择地域。
3. 在实例列表页面，单击目标实例名称。
4. 在导航栏，单击Consumer group管理。
5. 在Consumer group管理页面，找到目标Consumer group，在其操作列，选择消费状态 。
![consumergroup](/documentation/Middleware/JCS-for-Kafka/image/consumergroup.jpg)
6. 在消费详情列表，显示该Group订阅的所有Topic以及各个Topic的堆积量和最近消费者。
![消费状态](/documentation/Middleware/JCS-for-Kafka/image/消费状态.jpg)


|参数| 说明 | 
|:--|:---|
|Partition |对应每个topic的partition情况|
|  消息数 |  当前消息消费数| 
|  消费位点 |  该Topic在当前分区下的消息消费位点。| 
| 堆积量	| 当前分区下的消息堆积总量，即最大位点减去消费位点的值。| 
| 最近消费该分区的消费者	| 罗列最近在该分区消费的消费者| 

