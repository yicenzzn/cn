# 发送消息

## 前提条件
- 已经创建topic及订阅关系，并且状态处于服务中。

## 注意事项
- 对于单个topic的每秒事务处理数最大为5000TPS(如需提升请提交工单)
- 消息的生命周期为3天
- 消息体大小最大为256KB

## 操作步骤
**1. 在topic列表，选择要发送消息的topic--操作--发布消息**

![发送消息步骤1](/documentation/Middleware/Message-Queue/image/发送消息-01.jpg)

**2.填写发送消息的内容，单击“发送”**

![发送消息步骤2](/documentation/Middleware/Message-Queue/image/发送消息-02.jpg)  


I. 输入Message Body、BusinessID和tag，并且如果想要发送延时消息可以设置消息延迟时间。  
II. 消息发送成功，会返回消息发送成功通知和消息的Message ID，点击消息详情可以进行查看。  
III. 说明：  

- 消息的生命周期为3天，超过生命周期消息删除无法恢复，Message Body的最大支持256KB。
- 消息的Business ID为消息生产者自定义的业务ID，可以通过Business ID进行消息的查询，长度最大为128字符。
- 消息的延迟时间范围为：0~3600秒。
- 订阅者tag的规则说明：tag是消息订阅者对于消息的筛选，当订阅者设置了tag时，有相同tag的消息才能被订阅者消费，如果没有设置tag，则订阅者对消息不做筛选。
