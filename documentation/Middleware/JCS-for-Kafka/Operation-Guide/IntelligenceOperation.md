通过智能运维，服务会创建一个新的Topic，partition数与broker数相同，用以验证实例的生产或消费是否正常，即时诊断实例健康状态。

**诊断方法：**
- 生产：消息单条发送，统计overall 和 producer的数据；
- 生产消费闭环：消息批量发送（按指定生产消息总数批量发送，客户端默认批量消费），统计overall 和 consumer的数据（ 忽略producer数据）。

## 生产
1. 登录消息队列Kafka版控制台。
2. 在概览页面的资源分布区域，选择地域。
3. 在实例列表页面，单击目标实例名称。
4. 在导航栏，单击运维诊断。
5. 在运维诊断页面，诊断对象选择生产 。


![运维诊断1](/documentation/Middleware/JCS-for-Kafka/image/intelligenceOperation-consumer1.jpg)
![运维诊断2](/documentation/Middleware/JCS-for-Kafka/image/intelligenceoperation-consumer2.jpg)

|参数| 说明 | 
|:--|:---|
| 生产平均耗时 |生产消息平均消耗时间|
|  50%的耗时不超过的数值 |  生产50%的消息小于的时间| 
|  75%的耗时不超过的数值 |  生产75%的消息小于的时间| 
|  95%的耗时不超过的数值	| 生产95%的消息小于的时间| 
| 生产总耗时	| 生产所有消息所用的时间| 
| 生产消息总数	| 生产的消息数量| 
***


## 生产消费闭环
1. 登录消息队列Kafka版控制台。
2. 在概览页面的资源分布区域，选择地域。
3. 在实例列表页面，单击目标实例名称。
4. 在导航栏，单击运维诊断。
5. 在运维诊断页面，诊断对象选择生产消费闭环 。

![运维诊断3](/documentation/Middleware/JCS-for-Kafka/image/intelligenceOperation-producter.jpg)
![运维诊断4](/documentation/Middleware/JCS-for-Kafka/image/intelligenceOperation-producter2.jpg)

|参数| 说明 | 
|:--|:---|
|消费平均耗时 |消费所有消息的平均时间|
|  从生产到消费的闭环平均耗时 |  单位是ms| 
|  消费总耗时 |  消费所有消息的总消耗时间。| 
| 消费消息总数	| 消费的所有消息的总数| 
| 第一条消息生产到最后一条消息消费闭环时间	| 单位是ms| 
|  50%的耗时不超过的数值 |  生产到消费50%的消息小于的时间| 
|  75%的耗时不超过的数值 |  生产到消费75%的消息小于的时间| 
|  95%的耗时不超过的数值	| 生产到消费95%的消息小于的时间| 

