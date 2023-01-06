# 使用流日志查看 NAT 网关流量明细

在使用 NAT 网关时，通常是多台实例（如云主机）通过同一 NAT 网关访问公网。在这种情况下，部分云主机流量异常可能会影响其他云主机访问公网。您可以通过流日志来查看分析某一 NAT 网关的流量转发情况，快速定位流量消耗最大的源 IP。

### 创建日志配置

1. 登录并进入“日志服务”控制台

2. 创建新的日志集和日志主题

3. 在上一步指定的日志主题中设置日志来源为 NAT 网关的流日志，并指定希望采集日志的 NAT 网关

4. 设置日志预处理配置后完成日志配置创建

在这里仅简单介绍了创建日志配置的简单流程，若您仍对创建日志配置有疑问或希望知道更多分析语句规则，请查阅[日志服务帮助文档](https://docs.jdcloud.com/log-service/logservice-started)。

### 日志分析

您创建完日志配置后，日志服务自动为您采集了您设置的 NAT 网关的流日志。此时，您可以根据这些流日志进行分析。本文给出一些简单的分析例子，更详细的分析功能请查阅[日志检索与分析](https://docs.jdcloud.com/log-service/kvsearch)。

#### 查看特定时间段内各源 IP 的出方向流量

选择起始时间和终止时间，通过输入以下语句将该时间段内的数据按 time 和 src_ip 分组，统计该时间段内每个时间点下每个源 IP 的总出方向流量。

```
*|SELECT `time`,SUM(`egress_bytes`),`src_ip` WHERE natgw_id='您的NAT网关ID'GROUP BY `time`,`src_ip`
```

此时利用折线图，可以更直观地看到该时间段内每个时间点下各源 IP 的出方向流量。

![Egress-Data-of-Every-src_ip](/image/Networking/Nat-Gateway/Egress-Data-of-Every-src_ip.png)

若想统计新建连接数、活跃连接数、入方向流量、出方向包数、入方向包数，则将egress_bytes修改为对应的参数即可。

**注意：因为数据统计时使用的方法，同一时间点内同一 IP 的出方向流量可能会出现多条数据，将它们求和才是该时间点内该 IP 的全部出方向流量，因此聚合函数 SUM 不可省略。新建连接数、活跃连接数、入方向流量、出方向包数、入方向包数同理。**

#### 查看特定时间段内出方向流量总和最大的源 IP

选择起始时间和终止时间，如特定的三分钟，通过输入以下语句来统计该三分钟内出方向流量总和最大的前5个源IP。

```
*|SELECT SUM(`egress_bytes`),`src_ip` WHERE natgw_id='您的NAT网关ID'GROUP BY `src_ip`ORDER BY SUM(`egress_bytes`) DESC limit 5
```

![Top-N-src_ip-Order-by-Sum-of-Egress-Data](/image/Networking/Nat-Gateway/Top-N-src_ip-Order-by-Sum-of-Egress-Data.png)

若想分析更多出方向流量总和最大的源 IP 数据，仅需要将5修改为您希望分析的源 IP 个数即可。该数字的上限请参考[日志检索与分析](https://docs.jdcloud.com/log-service/analysis)。

