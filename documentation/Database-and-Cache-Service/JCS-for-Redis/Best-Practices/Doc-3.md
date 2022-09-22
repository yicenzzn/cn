# 合理使用大key

## 大key说明

通常我们会将含有较大数据或含有大量成员元素的Key称之为大Key。

- string类型，数据比较大，（例如：大小超过20K）

- 集合类型元素个数比较多，或者成员的value总大小比较大（例如：元素个数超过1000）

## 大key的影响

常见的影响为：性能下降、访问超时、数据不均衡等

- 大key查询或删除可能出现慢日志，可能会引起redis节点阻塞，甚至导致主从切换。

- 集群扩容迁移时，大Key迁移时可能导致节点卡顿

- 大key的读请求，可能导致连接输出缓冲区增长比较大（达到maxmemory导致返回OOM Error、数据淘汰），以及网络流量和带宽占用比较大（延迟增大、可能存在丢包、TCP重传变多）

- 集群模式下，节点之间内存占用不均衡

## 常见监控方式

大key不同于热key，热key的出现稍纵即逝，大key的存在基本上是处于稳定状态，即使认为大key可能对业务产生影响时，通过大key统计功能，也能查找到大key。

另外，我们目前具备完备的监控来提前识别大key带来的影响，或者帮助分析大Key造成性能问题。

- 慢日志统计（可调整 slowlog-log-slower-than 参数阈值，云上操作步骤可参考： [集群参数配置](../Operation-Guide/Instance-Management/Modify-Instancename.md) ）

- 大key统计功能（云上操作步骤可参考： [大Key热Key分析](../Operation-Guide/Cache-Analysis/Key-Analysis.md)  ）

- 内存使用监控和内存使用率告警（集群和节点维度）（云上操作步骤可参考：  [实例监控](../Operation-Guide/Monitoring/Monitoring.md)    ）

- 网络流出流量告警（云上操作步骤可参考：  [实例监控](../Operation-Guide/Monitoring/Monitoring.md)    ）


## 大key使用实践

应该合理使用redis，一方面，尽量避免大key出现；另一方面，即使少量大key，只要使用规范，大部分时候影响也不大。以下为对大Key的使用原则建议：

- 定期通过大key统计功能检查缓存中存在的大key，并进行合理拆分，提前识别并解决大key风险。

- 尽量避免查询整个集合类型Key的操作，比如慎用hgetall/smembers/(lrange 0 -1)/(zrange 0 -1)/(zrang -inf +inf)等命令。

- key删除使用unlink命令（4.0以上），或者通过hsan/sscan/zscan等遍历删除。

- 开启过期key异步删除、淘汰key异步删除等。

- 关注内存使用率水位告警。

