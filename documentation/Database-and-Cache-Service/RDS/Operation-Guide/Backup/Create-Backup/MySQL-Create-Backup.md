# MySQL 创建备份
云数据库 MySQL 实例的备份触发方式支持自动备份和手动备份两种方式；您可以通过修改备份策略来设置自动备份触发的时间点，具体操作请参考 [备份策略](../Backup-Policy/MySQL-Backup-Policy.md)。

对于采用云盘的数据库实例，还支持采用 **“云盘快照”** 的方式进行备份。云盘快照是利用云盘的机制，对数据进行备份、恢复以及扩容，跟传统备份方式相比，**云盘快照备份性能可提升5-10倍以上**。

|特性|传统物理备份|云盘快照备份|
|-|-|-|
|备份、恢复性能|一般|高，通常比传统方式高5-10倍以上|
|跨地域备份同步|支持|仅非加密云盘支持|
|备份下载|支持|不支持|
|根据备份创建|存储空间必须大于实际数据量|存储空间必须大于等于当前存储空间|
|根据时间点创建|存储空间必须大于实际数据量|存储空间必须大于等于当前存储空间|


开启云盘快照备份后，系统会自动将使用云盘的实例切换到快照备份的模式。为确保实例的可恢复性，会有7天的并行窗口时间，期间传统的物理备份和快照备份都会进行。前7天，只展示物理备份；7天后，展示快照备份。

## 注意事项
* 请确保在业务低峰期创建备份。
* 备份文件不会占用数据库实例的本地磁盘空间。
* 执行手动备份或者自动备份期间，执行 DDL 变更，会导致创建备份失败。
* 执行手动备份或者自动备份期间，大量的 DML 变更，会导致创建备份失败。
* 手动备份：每个地域支持最多创建5个，随着删除实例，手动备份也会自动释放。
* 如果您需要对数据库实例的数据进行测试修改，请提前针对实例进行手动备份，确保进行测试验证后，可以将数据库实例的数据库恢复到原先正常状态。


## 创建自动备份
1. 登录 [云数据库 RDS 控制台](https://rds-console.jdcloud.com/database) 。
2. 实例列表中，点击实例ID进入实例详情页。
3. 切换到 备份管理-> 备份策略。  

 ![备份策略](../../../../image/RDS/Backup-Strategy-1.png)
4. 点击 **修改策略**，弹出备份策略修改弹窗，进行设置。详情见[备份策略](../Backup-Policy/MySQL-Backup-Policy.md)。  

 ![备份策略](../../../../image/RDS/Backup-Strategy-2.png)
   
   > 说明：
   > 按时间点恢复基于备份周期和备份保留天数内的数据备份 + 日志备份（binlog），缩短自动备份频率和保留天数会影响实例数据的时间点恢复范围请按照实际情况进行调整
   > 自动备份无法手动删除，可设置备份保留时间，到期后会自动删除。
   > 增加数据备份和日志备份保留的天数将可能带来额外的备份空间计费费用。

## 创建手动备份
1. 登录 [云数据库 RDS 控制台](https://rds-console.jdcloud.com/database) 。
2. 选择需要进行设置手动备份的目标实例，点击目标实例的名称，进入到实例详情页。
3. 选择 **备份管理** 标签，点击 **创建备份** 按钮，创建备份弹出框参数说明如下：
    * 备份名称：允许重复，名称的长度和字符有一定限制，具体以控制台为准。
   
4. 点击 **确定** 按钮，返回到备份列表页，手动备份开始创建。


## 相关API
创建手动备份：[createBackup](https://docs.jdcloud.com/cn/rds/api/createbackup)
