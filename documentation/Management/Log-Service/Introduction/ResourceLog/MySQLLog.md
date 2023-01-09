## MySQL日志
### 简介
目前接入日志服务的MySQL日志类型为**审计日志**、**慢日志统计**、**慢日志明细**。MySQL审计日志检索跨度最多支持7天。

### MySQL 审计日志字段说明
日志字段 | 字段描述 | 字段类型
-- | -- | --
user_name | 访问用户名称 | string
user_ip | 用户客户端ip地址 | string
operation | 请求类型 | string
db | 请求访问数据库名称 | string
sql | 请求的具体SQL | string
customTimeStr | 日志记录时间 | string
mysql_tid | MySQL线程id | string
sent_rows | 返回行数 | string
affected_rows | 修改行数 | string
examined_rows | 扫描行数 | string

### 慢日志统计字段说明
日志字段 | 字段描述 | 字段类型
-- | -- | --
customTimeStr | 时间戳 | string
fingerprint | 查询SQL语句，汇总 | string
Lock_time | 慢查锁定时间结果集 | string
checksum | 校验 | string
Query_length | 慢查结果长度结果集 | string
Query_time | 慢查执行时间结果集 | string
Rows_sent | 慢查返回行数结果集 | string
Rows_examined | 慢查扫描行数结果集 | string
query_host | 慢查请求host地址 | string
query_count | 慢查执行次数 | string
db | 慢查请求db | string
stime | 日志记录时间 | time

### 慢日志明细字段说明
日志字段 | 字段描述 | 字段类型
-- | -- | --
query_time | 	慢查执行时间 | float
user | 慢查用户 | string
lock_time | 慢查锁定时间 | float
rows_sent | 慢查返回行数 | int
rows_examined | 慢查扫描行数 | int
query | 慢查语句 | string 
database | 慢查请求的数据库 | string
clientip | 客户端ip | string
clienthost | 客户端hostname | string
stime | 日志记录时间 | time
