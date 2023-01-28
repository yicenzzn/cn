# 京东智联云消息队列 Kafka版 性能测试


#  1.  测试环境概述
- 测试目标：
	1. 当分区数、消息长度大小等参数变化时，对生产、消费吞吐量的影响。
	2. 测试不同实例规格下kafka生产、消费的性能。

- 测试环境：
	1.  所有测试均在华北-北京，可用区A完成
	2.  测试用的云主机规格：8C32GB  
	3.  测试用的云主机镜像：CentOS 7.6 64位 
	4.  测试用的消息队列Kafka版本：1.0.1

- 测试实例规格：云盘类型：性能型云盘

	| 节点规格  | 云盘大小  | 节点数  |
	|:----------|:----------|:----------|
	| 2C8G     | 500    | 3    |
	| 4C16G    | 500    | 6    |
	| 8C32G    | 500    | 10   |
	| 16C32G   | 500    | 15   |



</br>
</br>
</br>

# 2.  测试工具介绍
- 使用Kafka官方提供的测试测试脚本`bin/kafka-producer-perf-test.sh` 和`bin/kafka-consumer-perf-test.sh`进行测试，通过该工具可以对生产者性能和消费者性能进行测试，主要输出4项指标，总共发送消息量（以MB为单位），每秒发送消息量（MB/second），发送消息总数，每秒发送消息数（records/second）

- 测试工具参数说明
	1.  生产者性能测试脚本：kafka-producer-perf-test.sh
	```
	$ bin/kafka-producer-perf-test.sh --num-records 50000000 --topic perfTest --throughput -1 --producer-props bootstrap.servers=server:9092 acks=1
 
	topic：发送的主题
	num-records：总共需要发送的消息数
	record-size：每个消息的字节数
	throughput：每秒钟发送的消息数
    acks：应答方式
	```
	2. 消费者性能测试脚本：kafka-consumer-perf-test.sh
	```	
	$ bin/kafka-consumer-perf-test.sh --bootstrap-server=server:9092 --group auto02 --topic testAAA --messages 1000 fetch-size  1024
	
	topic：消费的主题
	messages：消费的消息总数
	group：消费组名称
    fetch-size：拉取消息大小
	```
	
</br>
</br>
</br>



# 3.  测试步骤

## 3.1 server端实例与主题准备
- 准备kakfa实例和主题
	1. 在控制台创建kafka实例，操作方法：https://docs.jdcloud.com/cn/jcs-for-kafka/create-kafka
	2. 在控制台创建topic，操作方法：https://docs.jdcloud.com/cn/jcs-for-kafka/kafka-manager

## 3.2 client端测试脚本准备
- 使用云主机安装kafka：
    1. 申请与被kafka测实例在同一个vpc下的云主机：申请地址  https://console.jdcloud.com
	2. 下载测试脚本，直接下载：`curl -L -O https://archive.apache.org/dist/kafka/1.0.1/kafka_2.11-1.0.1.tgz`;或者下载后上传至云主机，下载地址：` http://kafka.apache.org/downloads  `          
    3.  安装并解压`$tar zxvf kafka_2.11-1.0.1.tgz`
    4.  安装jvm

## 3.3 测试脚本准备
1. 进入kafka客户端安装路径下 `$cd ../kafka_2.11-1.0.1`
2. 编辑测试脚本,命名为 `producerPerfTest.sh`，内容如下。请根据实际场景修改脚本中主题、消息大小、接入地址等信息。


```
#!/bin/bash

case $1 in
"start"){
for ((i=1;i<=$2;i++));
do
logfile=myout${i}
echo "********$logfile********"
bin/kafka-producer-perf-test.sh --num-records 50000000 --topic perfTest --record-size 1000 --throughput -1 --producer-props bootstrap.servers=server:9092 acks=1 >${logfile} 2>&1 &
done
};;

"stop"){
producer_id=ps -ef | grep producer | grep -v "grep" | awk '{print $2}'
echo ${producer_id}
for id in ${producer_id}
do
kill $id
echo "killed $id"
done
};;

esac

```


## 3.4 执行测试并记录结果

- 生产性能测试：
	1. 执行生产测试`$ sh producerPerfTest.sh start 3`，开始进行发送消息的压力测试，命令中入参代表生产者个数。
	2. 终止所有生产测试线程`$ sh producerPerfTest.sh stop`  
	3. 测试结果记录在文件`myout${i}`中，记录每秒发送消息数量、每秒发送消息大小、平均响应时间、最大相应时间等信息。
- 消费性能测试：
	1. 执行消费测试`$ bin/kafka-consumer-perf-test.sh --bootstrap-server server:9092 --group sc --topic topicPerfTest --messages 1000000 --fetch-size  1024`,请根据实际场景修改脚本中主题、消息大小、接入地址等信息。
	2. 测试结果将直接打印在控制台，记录每秒拉取消息数量、每秒拉取消息大小等信息。


</br>
</br>
</br>



# 4.  测试结果

## 4.1 Producer Only

#### 4.1.1 生产参数对吞吐量的影响，以下测试均在2c8g的kafka实例上进行测试

1. messageSize vs Throughput

| benchmark数 | messageSize | acks | partitons | re  cords/sec | Mb/sec |  avg(ms) | tp95(ms) |
| :-- | :-- | :-- | :-- | :-- | :-- |:-- |:-- |
| 1 | 10  | 1 | 6 | 1034019| 9.86  | 0.84 | 5 |
| 1 | 100 | 1 | 6 | 365671 | 34.87 | 0.77 | 4 |
| 1 | 500 | 1 | 6 | 110861 | 54.13 | 1.85 | 8 |
| 1 | 1000 | 1 | 6 | 69794 | 68.16 | 1.3 | 2 |
| 1 | 2000 | 1 | 6 | 31856 | 62.66 | 6.87| 5 |

![messageSize vs Throughput](/documentation/Middleware/JCS-for-Kafka/image/test-messageSize.png)

- 结论：消息越长，每秒所能发送的消息数越少，而每秒所能发送的消息的量（MB）越大

1. Producer Number vs Throughput

| benchmark数 | messageSize | acks | partitons | re  cords/sec | Mb/sec |  avg(ms) | tp95(ms) |
| :-- | :-- | :-- | :-- | :-- | :-- |:-- |:-- |
| 1 | 1000 | 1 | 6 | 69794  | 68.16  | 1.3 | 2 |
| 2 | 1000 | 1 | 6 | 128345 | 125.34 | 4.7 | 19 |
| 3 | 1000 | 1 | 6 | 170037 | 166.05 | 59.31 | 342 |

![Producer Number](/documentation/Middleware/JCS-for-Kafka/image/test-producerNum.png)

- 结论：随着Producer个数的提升，每秒总共发送的消息量线性提升

3. Partition Number vs Throughput

| benchmark数 | messageSize | acks | partitons | re  cords/sec | Mb/sec |  avg(ms) | tp95(ms) |
| :-- | :-- | :-- | :-- | :-- | :-- |:-- |:-- |
| 3 | 1000 | 1 | 1 | 98195  | 95.89  | 822 | 1839 |
| 3 | 1000 | 1 | 2 | 117441 | 114.69 | 652 | 9367 |
| 3 | 1000 | 1 | 3 | 137339 | 133.24 | 464 | 1196 |
| 3 | 1000 | 1 | 4 | 125537 | 122.6  | 579 | 9636 |
| 3 | 1000 | 1 | 5 | 166181 | 162.29 | 229 | 1339 |
| 3 | 1000 | 1 | 6 | 170958 | 166.95 | 59  | 1438 |

![Partition Number vs Throughput](/documentation/Middleware/JCS-for-Kafka/image/test-partition.png)

 - 结论：当Partition数量为Broker数量整数倍时吞吐量明显比其它情况高 


#### 4.1.2 不同实例规格下、生产不同长度的消息，kafka生产性能测试

- 根据上述参数调优测试，采用以下参数进行测试：

```
partition = nodeNum * 2
producer = nodeNum
acks = 1
replication = 1
num-records = 10000000
```
1. 2c8g 3节点 —— benchmark=3，partitons=6

| messageSize | records/sec | Mb/sec |  avg(ms) | max(ms) | tp95(ms) |
| :-- | :-- | :-- | :-- | :-- | :-- |
| 100 | 1018303 | 100.12 | 6.11 | 459 | 20 |
| 500 | 296671 | 141.46 | 140.89 | 7419 | 551 |
| 1000 | 170564 | 162.66 | 124.66 | 3141 | 635 |
| 2000 | 91644 | 174.8 | 30.15 | 448 | 194 |

2. 4c16g 6节点 —— benchmark=6，partitons=12

| messageSize | records/sec | Mb/sec |  avg(ms) | max(ms) |tp95(ms) |
| :-- | :-- | :-- | :-- | :-- | :-- |
| 100 | 1411098 | 134.58 | 6.52 | 728 | 25 |
| 500 | 318054 | 151.68 | 1109 | 14403 | 5517 |
| 1000 | 207990 | 198.36 | 887 | 6426 |4124 |
| 2000 | 106722 |203.58 | 794 | 12262 | 4797 |

3. 8c32g 10节点 —— benchmark=10，partitons=20

| messageSize | records/sec | Mb/sec |  avg(ms) | max(ms) |tp95(ms) |
| :-- | :-- | :-- | :-- | :-- | :-- |
| 100 | 1274697 | 121.6 | 91.28	1054 | 557 |
| 500 | 547555 | 261.1 | 134.6 | 1537 | 849 |
| 1000 | 379233 | 361.7 | 432 | 2774 | 2113 |
| 2000 | 200056 | 381.6 | 594 | 5045 | 3019 |

4. 16c64g 15节点 —— benchmark=15，partitons=30

| messageSize | records/sec | Mb/sec |  avg(ms) | max(ms) |tp95(ms) |
| :-- | :-- | :-- | :-- | :-- | :-- |
| 100 | 2006145 | 191.25 | 124.6 | 1171 | 765 |
| 500 | 791925 | 377.55 | 10.1 | 544 | 78 |
| 1000 | 457335 | 436.2 | 19.92 | 934 | 63 |
| 2000 | 314595 | 600.15 | 8.21 | 552 | 19 |

- 结果汇总图：每秒发送消息量（MB/s）
![每秒发送消息量](/documentation/Middleware/JCS-for-Kafka/image/test-pro-Mb.png)

- 结果汇总图：每秒发送消息条数（reconds/s）
![每秒发送消息条数](/documentation/Middleware/JCS-for-Kafka/image/test-pro-record.png)


## 4.2 consumer Only

#### 4.2.1 消费参数对吞吐量的影响，以下测试均在4c16g的kafka实例上进行测试

1. messages vs Throughput

| messageSize | fetch-size | records/sec | Mb/sec |
| :-- | :-- | :-- | :-- |
| 1000000  | 4194304 | 159.45 | 167197 |
| 5000000  | 4194304 | 376.45 | 394744 |
| 10000000 | 4194304 | 449.32 | 471153 |
| 50000000 | 4194304 | 416.45 | 393136 |

![messages](/documentation/Middleware/JCS-for-Kafka/image/test-messages.png)


#### 4.2.2 不同实例规格下、拉取不同长度的消息，kafka消费性能测试
- 采用以下参数进行测试：
```
partition = nodeNum * 2
messages  = 1000000
messageSize = 1000
```

1. 2c8g 3节点

| fetch-size | records/sec | Mb/sec |
| :-- | :-- | :-- |
| 1024 | 58.02 | 60482 |
| 524288 | 123.87 | 129842 |
| 1048576 | 134.78 |137893 |
| 2097152 | 135.6 | 139012 |
| 3145728 | 141.23 | 144562 | 
| 4194304 | 139.24 | 142921 |

2. 4c16g 6节点 

| fetch-size | records/sec | Mb/sec |
| :-- | :-- | :-- |
| 1024 | 87.39 | 91636 |
| 524288 | 148.51 | 155729 |
| 1048576 | 161.17 | 169000 |
| 2097152 | 162.36 | 170253 |
| 3145728 | 163.78	| 171737 |
| 4194304 | 159.45 | 167197 |
3. 8c32g 10节点

| fetch-size | records/sec | Mb/sec |
| :-- | :-- | :-- |
| 1024 | 108.65 | 113929 | 
| 524288 | 166.53 | 174624 |
| 1048576 | 172.52 | 180906 |
| 2097152 | 158.37 | 166070 |
| 3145728 | 176.4 | 184972 |
| 4194304 | 179.3 | 188092 |

4. 16c64g 15节点 

| fetch-size | records/sec | Mb/sec |
| :-- | :-- | :-- |
| 1024 | 108.65 | 113929 |
| 524288 | 166.53 | 174624 |
| 1048576 | 172.52 | 180906 |
| 2097152 | 158.37 | 166070 | 
| 3145728 | 176.4 | 184972 |
| 4194304 | 179.3 | 188092 |

- 结果汇总图：每秒接收消息量（MB/s）

![每秒接收消息量](/documentation/Middleware/JCS-for-Kafka/image/test-con-Mb.png)









      
