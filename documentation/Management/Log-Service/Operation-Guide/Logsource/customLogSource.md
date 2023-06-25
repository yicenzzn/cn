# 业务应用日志源设置

## 1. 概述

业务应用日志是指用户在京东智联云上部署的业务应用所产生的日志。日志内容和日志格式由用户自己定义。

用户无需手动安装日志采集agent，只需要在日志源设置中选择需要采集的云主机或k8s集群，日志采集agent将会自动安装。

业务应用日志支持投递至多种类型的目的地，默认采集至日志服务的日志主题中。也可将日志投递至控制台的云ES和云Kafka中，或自建ES和自建Kafka中。


## 2. 云主机操作步骤

**业务应用采集配置**

1. 登录日志服务控制台，点击【创建日志配置】，或进入指定日志集内，点击左侧导航栏中的【新建主题】。

2. 完成日志集和日志主题的设置。

3. 点击【下一步】进入【日志源设置】页面。

4. 【日志来源】选择业务应用。

5. 【日志源类型】选择云主机。

6. 【采集状态】默认打开，用户也可以关闭。关闭后不采集日志。

7. 【日志路径】填写所需采集的业务应用的日志的路径和文件名，路径支持“/\*/”或“/\*/abd/\*/"的通配，不支持“/\*\*/”的通配，文件名支持\* 的通配。Linux的文件路径应该以/开头。日志文本的编码为UTF8。

8. 【采集实例】根据用户自身需求选择实例，或者对应的高可用组和标签。

标签是在云主机实例上打的k-v标记，通过标签可以快速选择多个采集实例。

a. 预设标签

k8s集群已为集群内node打了集群ID的标签，可以直接使用。标签名称为 `kubernetes.jdcould.com/cluster_id`

b. 自定义标签

您可通过云主机管理，手动为实例创建标签，并在日志服务中选择使用，具体流程如下：

- 进入云主机页面：https://cns-console.jdcloud.com/host/compute/list

- 通过region，主机名称等筛选条件过滤需要采集日志的实例，参见下图标记1，2的位置。

![](../../../../../image/LogService/operationguide/label1.png)

- 选中实例，如上图标记3的位置。

- 点击页面左下角的“更多”按钮，点击“编辑标签”，如下图所示。

![](../../../../../image/LogService/operationguide/label2.png)

- 在键和值中填写标签信息完成后，点击“确定”，即可添加对应的标签，如下图添加的logGroup=order-service

![](../../../../../image/LogService/operationguide/label3.png)

- 切换至共有云日志服务页面：https://logs-console.jdcloud.com/overview?dataCenter=cn-north-1

- 选择日志主题，开始编辑日志主题采集配置，如下图步骤1，2所示。

![](../../../../../image/LogService/operationguide/label4.png)


- 编辑日志主题采集配置的采集实例，选择“标签”，在标签列表中选择对应的标签。

![](../../../../../image/LogService/operationguide/label5.png)


9.  如果用户的业务应用日志是多行日志，则需要设置首行正则匹配的规则；首行正则遵循 **POSIX Extended Regular Express** 正则表达式 ，示例如下：
   
   日志首行基本上以时间格式开头，如java异常堆栈日志数据

```
2020-07-08 23:58:45.382 [INFO]  xxxxxxxxxxxx
    at xxxxxxxxxxxxxxxxxxx
    at xxxxxxxxxxxxxxxxxxx
    at xxxxxxxxxxxxxxxxxxx
2020-07-08 23:58:55.582 [INFO]  xxxxxxxxxxxx
    at xxxxxxxxxxxxxxxxxxx
    at xxxxxxxxxxxxxxxxxxx
    at xxxxxxxxxxxxxxxxxxx    
```

可以使用正则表达式进行匹配，不支持 ‘\d’ 方式进行数字匹配：

```
^[[:digit:]]{4}-[[:digit:]]{2}-[[:digit:]]{2}
```

预期结果是将以上数据分割成两条日志，每条日志的开头匹配年月日。

注：正在表达式相关语法可参考：[正则表达式](https://www.cnblogs.com/crunchyou/p/4877427.html)

![](../../../../../image/LogService/operationguide/multilinetext.png)

**业务应用高级配置**

1. 【高级配置】默认关闭。打开高级配置后，可将日志直接从agent端投递至指定ES或Kafka中。

2. 若用户只有投递至ES或Kafka的需求，可以关闭【投递至日志主题中】，就不会在日志服务中存储对应的日志数据。也无法使用日志监控等功能。

3. 若业务应用日志的目的地是Kafka，则需要设定brokers，topic，以及是否压缩投递。压缩投递支持snappy和gzip格式。云Kafka会自动获取brokers。

4. 若业务应用日志的目的地是ES，则需要设定ES访问域名和索引前缀。云ES会自动获取访问域名。

![](../../../../../image/LogService/operationguide/advancedconfig.png)

## 3. k8s容器操作步骤

支持对k8s容器内服务或集群节点路径文件的日志发送至云日志系统中，日志采集Agent会在集群内以DaemonSet的形式运行，并根据用户设置的采集配置从日志源中采集日志数据。

1. 登录日志服务控制台，点击【创建日志配置】，或进入指定日志集内，点击左侧导航栏中的【新建主题】。

2. 完成日志集合日志主题设置。

3. 点击【下一步】进入【日志源设置】页面。

4. 日志来源选择【业务应用】。

5. 日志源类型选择【k8s容器】。

6. 【采集状态】默认打开，用户也可以关闭。关闭后不采集日志。

7. 【采集实例】需要从当前账号下的k8s集群中选择一个，可通过地域进行筛选。

8. 【采集模式】支持容器标准输出、容器文件路径、节点文件路径三种模式。
   
   **容器标准输出**
   
   采集集群内任意服务下的容器日志，仅支持Stderr和Stdout的日志。
   
   【日志源】支持从全部容器、指定工作负载、指定Pod Labels的容器中采集日志。
   
   （1）全部容器：可设置从所有Namespace或指定Namespace中的所有容器中采集日志。
   
   ![](../../../../../image/LogService/operationguide/standard-all.png)
   
   （2）指定工作负载：从指定的Namespace中选择工作负载中采集日志，需要指定工作负载的类型、工作负载名称、容器名称，支持选择多个。
   
   ![](../../../../../image/LogService/operationguide/standard-workload.png)
   
   （3）指定Pod Labels：选择Namespace，设置Pod Labels的key-value，容器名，从具有符合Pod Labels键值条件的容器中采集日志。
   
   ![](../../../../../image/LogService/operationguide/standard-podlabels.png)

**容器文件路径**

从所选容器的指定文件路径中采集日志数据。

【日志源】支持配置指定工作负载或指定Pod Labels。

（1）指定工作负载：需要选择Namespace、工作负载、容器，允许配置多个，并设置容器内采集的文件路径地址，分为目录前缀和文件地址，目录和文件均支持使用\*通配符。

![](../../../../../image/LogService/operationguide/containerfile-workload.png)

（2）指定Pod Labels：选择Namespace，设置Pod Labels的key-value，容器名，并设置容器内采集的文件路径地址，从具有符合Pod Labels键值条件的容器指定文件路径中采集日志。文件路径地址同样分为目录前缀和文件地址，目录和文件均支持使用*通配符。

![](../../../../../image/LogService/operationguide/containerfile-podlabels.png)

**节点文件路径**

从节点的指定文件路径中采集日志，文件路径地址同样分为目录前缀和文件地址，目录和文件均支持使用*通配符。

![](../../../../../image/LogService/operationguide/nodefile.png)

## 4. Logback Appender操作步骤

可使用JDCloud Logback Appender将日志写入到京东云日志服务中，使用方法见[Github-JDCloud_logback_appender](https://github.com/JDCloudLogs/logback-appender)

我们同时提供了高并发写日志的java类库，[配置方式](https://github.com/JDCloudLogs/log-producer)，[代码示例](https://github.com/JDCloudLogs/log-producer-sample)

## 5. Binlog操作步骤

支持对云数据库MySQL的Binlog日志进行采集，其原理是日志服务探针将自己伪装为MySQL的一个Slave，接收主库同步的Binlog信息并进行存储、检索、展示。

使用Binlog日志采集功能有一些限制条件，如下：

- 不支持MySQL 8.0及以上版本。

- MySQL必须开启Binlog，且Binlog必须为row模式。

```
# 查看是否开启Binlog
mysql> show variables like "log_bin";
+---------------+-------+
| Variable_name | Value |
+---------------+-------+
| log_bin       | ON    |
+---------------+-------+
1 row in set (0.02 sec)
# 查看Binlog类型
mysql> show variables like "binlog_format";
+---------------+-------+
| Variable_name | Value |
+---------------+-------+
| binlog_format | ROW   |
+---------------+-------+
1 row in set (0.03 sec)
```

- ServerID唯一，即需要同步的MySQL的Slave ID唯一。

- RDS限制

   - 无法直接在RDS服务器上安装探针，您需要将探针安装在能连通RDS实例的服务器上。

   - RDS备库不支持Binlog采集，您需要配置RDS主库进行采集。

**Binlog日志采集配置**

1. 登录日志服务控制台，点击【创建日志配置】，或进入指定日志集内，点击左侧导航栏中的【新建主题】。

2. 完成日志集合日志主题设置。

3. 点击【下一步】进入【日志源设置】页面。

4. 日志来源选择【业务应用】。

5. 日志源类型选择【Binlog】。

6. 【采集状态】默认打开，用户也可以关闭。关闭后不采集日志。

7. 【采集实例】需要从当前账号下的实例中选择一个，可通过地域进行筛选，这里选择的实例会自动安装探针，并将自己伪装成MySQL的一个Slave，接收主库同步的Binlog日志。需要注意的是，这里的实例需要与下方配置的数据库服务器地址在网络上可连通，否则无法成功采集数据。

8. 【服务器地址】填写MySQL主机地址的域名或IP，该信息可在云数据库中查询到。

9. 【端口号】填写MySQL服务的端口号，不填写时默认为3306。

10. 【用户名】填写连接数据库的用户名，不配置时，默认为root。

11. 【密码】填写连接数据库的密码，若没有设置密码，这里可为空。

12. 【包含表名】填写需要采集Binlog的表名的正则表达式，该项为必填项，不能为空。这里需要匹配的格式是“数据库名.表名”，如果希望采集所有表，需要配置为`.*\..*`,如果需要完全匹配，需要在前面加上^，后面加上$。

![](../../../../../image/LogService/operationguide/binlog_basic.png)

**Binlog日志高级配置**

1. 【ServerID】填写伪装为MySQL Slave的ID，不配置时，默认为125。

2. 【排除表名】填写排除表名的正则表达式，这里需要排除的格式是“数据库名.表名”，系统不会采集被排除的表的Binlog日志。

3. 【首次采集Binlog文件】填写首次采集Binlog文件的文件名，不配置时，默认从当前时间点开始采集。

4. 【首次采集文件的偏移】填写首次采集Binlog文件内的偏移，不配置时，默认为0。

5. 【采集类型】选择需要采集的Binlog日志的类型，默认采集insert、update、delete。

6. 【text转换字符串】是否开启将text转换为字符串，默认不转换。这里的处理逻辑是，不开启转换时，text类型字段内容会被忽略；开启转换时，text类型字段内容会被转换为字符串，如果超过长度限制，会按照长度限制进行截断处理。

7. 【编码方式】选择或填写字符编码方式，默认为utf8编码，如果系统提供的选中没有您需要的编码方式，也可以在选项中选择其他，之后在文本框中自定义填写。

![](../../../../../image/LogService/operationguide/binlog_adv.png)

## 6. 注意事项

- 当前版本仅支持采集Linux云主机和k8s集群工作负载模式的日志。
- 采集实例用户选择实例维度时，最多支持选择30台云主机，支持跨地域选择。
- 采集实例用户选择高可用组维度时，不受数量限制，高可用组内有多少云主机就采集多少，高可用组内后续新增的云主机的日志也会被采集，支持跨地域多选。
- 采集实例用户选择标签维度时，不受数量限制，标签内有多少云主机就采集多少，没有地域限制，标签内后续新增的云主机的日志也会被采集。
- 若高级配置中设置的目的地为自建ES或自建Kafka，则目的地ES或目的地Kafka前方的地域没有实际意义。
- 如果您使用的子账号没有被授予资源权限，在配置k8s日志时将无法加载出Namespace、工作负载、容器的列表信息，无法指定未授权的资源采集日志，需要与k8s产品主账号联系人取得联系，给子账号授予权限后再进行日志配置。
- k8s容器日志为了方便使用时检索和排查问题，除原始的日志内容以外，系统默认会携带容器场景的元数据（例如产生日志的容器ID等）一起上报至日志服务，并内置了一些字段用于记录这些信息，预置的字段如下：

| 字段             | 含义                    |
| -------------- | --------------------- |
| cluster_id     | 日志所属的集群 ID。           |
| container_name | 日志所属的容器名称。            |
| image_name     | 日志所属容器的镜像名称 IP。       |
| namespace      | 日志所属 pod 的 namespace。 |
| pod_uid        | 日志所属 pod 的 UID。       |
| pod_name       | 日志所属 pod 的名字。         |
| pod_ip         | 日志所属 pod 的IP。         |
| node_ip        | 日志所属节点的IP。            |
| node_name      | 日志所属节点的名称。            |
| file_path      | 日志文件路径。               |
| content        | 日志内容。                 |
