# 创建Topic
  在Topic管理页面可以进行topic的创建

## 前提条件
- 已注册京东云账号，并完成实名认证，且保证账户处于正常状态，没有在黑名单中。如果还没有账号请 [注册](https://accounts.jdcloud.com/p/regPage?source=jdcloud%26ReturnUrl=%2f%2fuc.jdcloud.com%2fpassport%2fcomplete%3freturnUrl%3dhttp%3A%2F%2Fuc.jdcloud.com%2Fredirect%2FloginRouter%3FreturnUrl%3Dhttps%253A%252F%252Fwww.jdcloud.com%252Fhelp%252Fdetail%252F734%252FisCatalog%252F1)，并 [实名认证](https://uc.jdcloud.com/account/certify)。
- 因为产品的计费类型为按用量计费，请确认您的账户不能处于欠费状态。

## 注意事项
- 用户默认在一个region最多只能创建10个topic，如有需要可以提工单增加。
- 在region：公网（华北）中消息队列 JCQ服务仅可用于测试（公网可直接访问），在生产环境请勿使用，不承诺产品的服务等级协议。
- Topic创建后，其地域和网络属性与物理资源紧密结合，无法变更。如需变更实例的地域或网络属性，请释放实例，并重新购买。



## 操作步骤
### 1.Topic管理页面点击“新建”按钮

从控制台左侧菜单中，找到互联网中间件-消息队列 JCQ-Topic管理页面，点击新建
 ![创建topic步骤1](/documentation/Middleware/Message-Queue/image/创建topic-01.jpg)

### 2.填写完Topic信息，点击“创建”按钮

页面刷新，完成新topic的创建
 ![创建topic步骤2](/documentation/Middleware/Message-Queue/image/创建topic-02.jpg)  

1. 选择namespace时可以选择用户自己创建的或者是默认的，如果需要新建，则点击新建namespace，在新建窗口完成那namespace名称填写即可。namespace名称不允许重复。namespace名称长度 3-32 个字符，支持字母、数字、连字符(-)、下划线(_)。

2. topic名称可以按照提示信息输入，不可修改。topic名称为全局唯一，如果有相同名称的topic被创建，则无法创建成功。并且topic只能包含字母、数字、连字符(-)、下划线(_)、波形符 (~)或加号 (+)，长度 为3-64 个字符。
3. 消息类型为普通消息、事务消息、全局顺序消息和分区顺序消息。

- 普通消息：不保证先入先出（FIFO）的顺序消费，包含普通消息和延时消息。
- 事务消息：仅topic类型为RocketMQ的支持选择事务消息，能达到分布式事务的最终一致。
- 全局顺序消息：消息的生产和消费按照消息的发布顺序进行（FIFO）。
- 分区顺序消息：仅topic类型为RocketMQ的支持选择事务消息，同一个分区下，其消费者在消费消息的时候，严格按照生产者投递到该分区的顺序进行消费。分区顺序消息在保证了一定顺序性的同时，保留了分区机制提升性能。

4. 备注根据需求填写，不可超过255个字节。
