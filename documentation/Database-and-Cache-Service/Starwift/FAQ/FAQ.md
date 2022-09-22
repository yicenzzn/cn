# FAQ

#### Starwift 跟 ClickHouse 那个版本兼容最好
Starwift 跟 ClickHouse 20.1.1.1 版本兼容最好。

####  ClickHouse实例支持那些地域
ClickHouse实例暂时支持“华北-北京”，后续视情况支持更多地域。

#### 扩缩容耗时数据会自动 rebalance 吗？
Starwift 采用计算和存储分离的架构，使用高性能的共享存储，因此扩缩容耗时不涉及数据的搬迁，没有数据 rebalance 的问题。


#### 扩容存储空间时对实例有什么影响？
存储空间会根据用户当前的数据情况自动进行扩容，扩容用户无感知，对业务无影响。


####  如何kill掉一个会话进程？
```
--常规做法：
show processlist ；
  
--杀死这个query
KILL QUERY WHERE QUERY_ID = 'XXXXXXXXXXXXXX' ;
  
--如果以上还不生效，则说明此query可能会引起文件mutation，尝试用下面方法解决：
 
--查询会话
SELECT * FROM system.mutations WHERE is_done = 0
 
 
--杀掉这个mutation ， 可能会引起无法修复的后果，数据丢失等等，确认好风险后再执行。
KILL MUTATION WHERE mutation_id = 'xxxxxxxxxxxxx' SYNC
```
