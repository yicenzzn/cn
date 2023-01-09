# 从数据文件迁移
本文介绍如何将本地文件的数据导入至云原生实时数仓 Starwift 中。

Starwift 兼容 ClickHouse 协议，因此可以使用 ClickHouse 的客户端进行数据导入。

#### 数据文件格式
支持的常见文件格式如下，更多支持的文件格式，可参考文档[文件格式及说明](https://clickhouse.com/docs/zh/interfaces/formats/?spm=a2c4g.11186623.0.0.522ad0d8vz9llf#tabseparated)
- TabSeparated
- TabSeparatedWithNames
- TabSeparatedWithNamesAndTypes
- CSV
- CSVWithNames。


#### 前提条件
- 客户端的所在的机器与 Starwift 网络连通，且 IP 已经加入 Starwift 的白名单中（同一VPC中）
- 已安装 clickhouse-client 工具。


## 操作步骤
#### 1. 准备数据
例如准备数据文件 account.csv，内容如下：
```
accountid, name, address, year
1, 'GHua', 'WuHan Hubei', 1990
2, 'SLiu', 'ShenZhen Guangzhou', 1991
3, 'JPong', 'Chengdu Sichuan', 1992
```

#### 2. 下载并配置客户端
1） 在 Starwift 实例所在VPC内选择一台云主机，在该云主机内，安装下载客户端 [点击下载clickhouse-client](https://repo.yandex.ru/clickhouse/rpm/stable/x86_64/)。
2） 安装客户端
   ```
   rpm -iv
   ```
3）在客户端的安装目录下执行如下命令，连接 Starwift：
   ```
   ./clickhouse-client --host=<host> --port=<port> --user=<user> --password=<password>
   ```
   参数说明：

   | 参数     | 说明                                                         |
   | -------- | :----------------------------------------------------------- |
   | host     | 外网地址或VPC地址。如果clickhouse-client所在服务器与云数据库ClickHouse集群在同一VPC内，您可以使用VPC地址。否则，请使用外网地址。 |
   | port     | TCP端口号。                                                  |
   | user     | 您通过分析型云数据库ClickHouse控制台创建的数据库账号。       |
   | password | 数据库账号对应的密码。                                       |

#### 3. 创建数据库及表
使用客户端连接到 Starwift 后，执行以下SQL，创建相应的数据库及表

1） 创建数据库
 ``` SQL
 CREATE DATABASE IF NOT EXISTS testdb ;
 ```

2） 使用MergeTree系类引擎创建表
``` SQL
CREATE TABLE testdb.account ON CLUSTER default(
  accountid UInt16,
  name String,
  address String,
  year UInt64
) 
ENGINE =ReplicatedMergeTree('/clickhouse/tables/{shard}/testdb/account', '{replica}') 
ORDER BY (accountid);
```

#### 4. 导入数据
1） 将数据文件放到云主机 `/data` 目录下，执行以下命令导入数据。
```
cat <本地文件名> | ./clickhouse-client --host=<数据库连接地址> --port=<TCP端口号> --user=<数据库账号> --password=<数据库账号的密码> --query="INSERT INTO <ClickHouse表名> FORMAT <本地文件格式>;"
```

2）导入完成后，查询数据进行验证

``` SQL
select * from testdb.account;
```
