# 云原生实时数仓 Starwfit 支持的规格

Starwfit 的计算资源分为以下类型：
- 计算节点
- ZooKeeper 节点（简称 ZK 节点）
- 监控节点

#### 1. 计算节点规格
|规格代码|VCPU(核)|内存（GB）|
|-|-|-|
|terrabase.s1.xlarge|4|16|
|terrabase.s1.2xlarge|8|32|
|terrabase.s1.4xlarge|16|64|
|terrabase.s1.8xlarge|32|128|

#### 2. ZK 节点
|规格代码|VCPU(核)|内存（GB）|存储空间（GB）|
|-|-|-|-|
|terrabase.zk1.xlarge|4|16|300|
|terrabase.zk1.2xlarge|8|32|300|
|terrabase.zk1.4xlarge|16|64|300|
|terrabase.zk1.8xlarge|32|128|300|

#### 3. 监控节点
|规格代码|VCPU(核)|内存（GB）|存储空间（GB）|
|-|-|-|-|
|terrabase.mn1.xlarge|4|16|100|
|terrabase.mn1.2xlarge|8|32|100|
|terrabase.mn1.4xlarge|16|64|100|
