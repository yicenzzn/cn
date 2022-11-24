# 数据库/表


## 数据库出现乱码的原因及解决方案

数据库出现乱码的原因可能是客户端请求数据的字符集与实际不符合或返回给客户端的字符集与客户端页面不符合，您需要修改下MySQL的配置文件。

## 我创建了库，但是我想修改库的字符集，我的账号没有权限，并且控制台也没有相应的入口，怎么办

如果需要修改库的字符集, 可以通过 DMS 来进行相关操作；点击控制台登录数据库，成功登录 DMS 后，左侧选中你要修改字符集的库名，然后再点击后测顶栏的操作tab，会刷新当前页面，然后可以看到当前页面有一个排序规则选项，选择你想要修改的字符集，然后点击执行按钮即可。

## 我希望可以在 MySQL 中存储表情相关内容，需要将 character_set_server 设置为 utf8mb4, 是不是只能提工单解决？

其实 character_set_server 参数的主要作用是通过命令行创建库的时候未指定字符集的情况下，默认会根据 character_set_server 的值来创建；但是京东云云数据库 MySQL 创建库的操作默认只能通过控制台来操作，并且是可以指定字符集为 utf8mb4。有些用户可能会发现即使这样操作了，通过客户端工具连接数据库实例时候看到的数据是乱码的，所以认为是因为 character_set_server 未设置为 utf8mb4 导致的，其实并非如此，这块还涉及到 character_set_client，character_set_connection，character_set_result 等相关字段的设置，***然后这些字段其实是客户端可以手动指定的***，具体可参见官网文档：[Connection Character Sets and Collations](https://dev.mysql.com/doc/refman/5.7/en/charset-connection.html)

## 如何在 RDS 的控制台中如何导出 MySQL的数据

为了安全，目前暂不支持通过控制台导出 MySQL 数据库中的数据。 如果有导出数据的需求，可以通过mysqldump 命令进行。



