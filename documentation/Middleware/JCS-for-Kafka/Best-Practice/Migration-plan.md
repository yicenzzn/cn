本文介绍kafka数据迁移方案，主要针对用户上云及云上集群变更场景，迁移方案可以保证业务不中断。

## 前提条件
1.用户原集群，生产和消费业务流量正常，简易模型如下：

![迁移方案1](/documentation/Middleware/JCS-for-Kafka/image/迁移方案1.png)

2.云上集群，无生产和消费，简易模型如下：

![迁移方案2](/documentation/Middleware/JCS-for-Kafka/image/迁移方案2.png)
## 迁移步骤
1.登陆京东智联云控制台创建kafka实例，规格不低于原集群配置，参考文档：创建实例
2.通过Kafka Manager创建原集群中相同规格Topic，参考文档：Kafka Manager
3.业务将生产端域名指向新kafka集群，原消费端业务保持不变

![迁移方案3](/documentation/Middleware/JCS-for-Kafka/image/迁移方案3.png)
4.验证新集群消息写入成功

./kafka-console-consumer.sh --bootstrap-server kafka-broker-xxx:9092 --from-beginning --new-consumer --topic ${topic_name}
5.验证老集群消费无消息积压

./kafka-consumer-groups.sh --describe --bootstrap-server kafka03-xxx:port --group ${consumer-group}
6.业务将消费端域名指向新kafka集群

![迁移方案4](/documentation/Middleware/JCS-for-Kafka/image/迁移方案4.png)
7.关停老集群消费，迁移完成

![迁移方案5](/documentation/Middleware/JCS-for-Kafka/image/迁移方案5.png)

**注意：**

`文中命令为参考指令，业务可根据具体配置修改相应参数。 
生产端和消费端切换服务后为防止长连接未断现象，建议切换后重启客户端服务。`

