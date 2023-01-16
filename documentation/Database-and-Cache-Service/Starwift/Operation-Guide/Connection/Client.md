# 使用客户端连接
Starwift 兼容 ClickHouse 协议，因此可以使用 ClickHouse 的客户端和驱动连接到 Starwift 实例中。

## 操作步骤
1. 在实例列表页，点击要连接的实例名称，进入实例详情页
2. 在实例详情页面中，查看实例的域名及端口信息。Starwift 集群有两个端口，TCP端口和HTTP端口，可按需使用。
3. 连接实例
  - 实例所在VPC内选择一台云主机，在该云主机内，安装下载客户端 [点击下载](https://repo.yandex.ru/clickhouse/rpm/stable/x86_64/)。
  - 安装客户端
```
 rpm -ivh *.rpm
```
- 在客户端的安装目录下执行如下命令:
 ```
   ./clickhouse-client --host=<host> --port=<port> --user=<user> --password=<password>; 
 ```

####     参数说明：

| 参数     | 说明                                                         |
| -------- | :----------------------------------------------------------- |
| host     | 外网地址或VPC地址。如果 Starwift-client 所在服务器与云数据库 Starwift 集群在同一VPC内，您可以使用VPC地址。否则，请使用外网地址。 |
| port     | TCP端口号。                                                  |
| user     | 您通过分析型云数据库Starwift控制台创建的数据库账号。       |
| password | 数据库账号对应的密码。 
