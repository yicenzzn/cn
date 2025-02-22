# 创建副本集

您可以通过MongoDB控制台或OpenAPI快速创建MongoDB实例，关于实例的计费说明请参见。



## 前提条件

- 已注册京东云账号，并完成实名认证。如果您未满足此条件请先注册账号请注册或实名验证。
- 如计费类型选择按配置计费，请确认您的账户余额（包括代金券）不小于50元。



## 操作步骤

1. 请登录[MongoDB控制台](https://mongodb-console.jdcloud.com/mongodb)，并在控制台界面找到“创建”按钮，点击即可进入创建页面；![img](../../../../../image/mongodb/createReplicaSet.png)
2. 在规格中选中副本集并配置其他可选项；
3. 点击立即购买，确认订单后即可完成实例的创建；
4. 在实例创建页面，您将有诸多可选项，具体参数说明和使用限制参照如下：

| 参数             | 参数说明                                                     | 使用限制                                                     |
| ---------------- | ------------------------------------------------------------ | ------------------------------------------------------------ |
| 计费类型         | 仅支持包年包月和按配置付费两种付费模式，关于付费模式的介绍请参见计费文档 |                                                              |
| 地域             | 选择实例所在的地域，可根据您的业务部署和连接时延进行相应选择。 | 实例创建后无法修改地域若您想与京东云云主机进行通信，请保证您的云主机实例与MongoDB实例处于同一地域内 |
| 数据库版本       | 所部署的数据库环境版本，目前可选版本为3.2、3.4、3.6和4.0，请您根据具体业务需求进行数据库版本的选择。 |                                                              |
| 节点数           | 节点数指副本集所包含节点的个数，您可以选择3、5、7节点        | MongoDB实例有且仅有一个Primary节点，不可扩展多余的Primary，仅可扩展Secondary节点的数量 |
| 存储类型         | 提供SSD本地盘和SSD云盘两种存储方式，您可根据具体需要选择使用。 |                                                              |
| 规格             | 实例所占用的CPU和内存，不同规格有不同的最大连接数以及IOPS，规格越高可拥有更高的IOPS和最大连接数，具体规格信息请参照产品过个。实例创建后支持调整实例的规格，具体操作和限制请参照配置变更文档。 |                                                              |
| 存储空间         | 副本集实例所占用的硬盘空间。                                 |                                                              |
| 选择网络         | 仅支持选择私有网络，若您未建设自己的私有网络或私有网络子网已满，您可点击新建私有网络或新建子网进行网络的配置。 |                                                              |
| 部署方式         | 京东云MongoDB支持单/多可用区部署方式，单可用区部署将所有数据库实例放置在同一可用区，多可用区部署将数据库实例进程循环放置在不同可用区。 |                                                              |
| 密码（可选）     | 对您的实例设置登录密码，京东云MongoDB实例默认账号未admin，同时您可在实例创建后再设置登录密码。 |                                                              |
| 购买时长（可选） | 当您选择包年包月付费方式时，你可以选择不同时长的实例购买时间，当您选择按配置续费时则无此选项 |                                                              |
| 自动续费（可选） | 当保障您的账户余额充足时，开启包年包月可自动续费，避免因错过续费时间导致实例自动关闭 |                                                              |





## 相关API接口

| 接口名称                                                     | 接口描述       |
| ------------------------------------------------------------ | -------------- |
| [createInstance](../../../../../API/JCS-for-MongoDB/Instance-Management/createInstance.md) | 创建副本集实例 |