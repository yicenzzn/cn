# 慢日志查询

慢日志是Redis用来记录命令执行时间过长请求的机制。通过慢日志查询功能，用户可查找性能变慢原因，并优化性能。



## 控制台慢日志查询

1.	登录 [Redis 控制台](https://redis-console.jdcloud.com/redis)，选择目标实例。

2.	单击实例名称进入实例资源信息页面。

3.	在标签栏中选择“慢日志查询”页签。

4.	设置查询时间，查看慢日志记录。


![](../../../../../image/Redis/SlowLog-1-3.png)

5. 下载和查看慢日志

标准命令行为 ： 

    wget -O /tmp/dump.aof url 
    
    

在云主机上执行命令： 

    wget -o “保存文件的绝对路径.aof“   '下载的URL'
    
    

然后直接vim相关文件就可以查看到相关日志信息。


该功能涉及到以下两个配置参数，您可通过调整参数值来配置慢日志，参数调整方式见： [集群参数配置](../Instance-Management/Modify-Instancename.md)

|  参数   |   说明     | 
|  :---   |   :---     |
|  slowlog-log-slower-than   | 如果在Redis实例的数据节点中执行一个命令，执行时间超过了slowlog-log-slower-than参数设置的阈值（单位为微秒），则会被记录到慢日志中。该参数的默认值为10000，即10ms，当Redis命令执行时间超过10ms，则生成慢日志。  | 
|  slowlog-max-len   | Redis记录的慢日志个数由slowlog-max-len参数的值决定，默认值为128个。当慢日志个数超过128时，会将旧的慢日志删除，记录新的慢日志。 | 




