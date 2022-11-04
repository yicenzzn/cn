您可以通过查看topic中的分区状态来了解服务端的消息总量或各个分区的消费进度。

## 前提条件
创建Topic
## 操作步骤
1. 登录消息队列Kafka版控制台。
2. 在概览页面的资源分布区域，选择地域。
3. 在实例列表页面，单击目标实例名称。
4. 在导航栏，单击Topic 管理。
5. 在Topic 管理页面，找到目标Topic，点击Topic名称。


![分区状态](/documentation/Middleware/JCS-for-Kafka/image/分区状态.png)
表 1. 分区状态信息

|参数| 说明 | 
|:--|:---|
|Partition	|Partition编号|
|消息数	|该Topic分区的ID号。|
|Leader	|当前的主节点|
|副本	|当前partition所有副本|
|同步副本	|当前partition所有副本|
|离线副本	|当前不在线的副本|
