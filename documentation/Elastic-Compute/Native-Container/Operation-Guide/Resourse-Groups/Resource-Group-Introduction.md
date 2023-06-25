# 资源组概述

资源组（Resource group）是京东云资源分组管理的工具，支持对云资源进行逻辑分组。通过使用资源组，可实现多项目或多应用场景下的资源分组管理以及资源的权限控制等。
资源组管理请参考[资源组管理](https://docs.jdcloud.com/cn/resourcegroup/operationguide)，基于资源组的资源管理请参考[资源管理](https://docs.jdcloud.com/cn/resourcegroup/resourcemanagement)。


## 使用限制
* 一个云资源必须且仅能归属一个资源组，一个资源组内可以容纳多个云资源。
* 资源组名称不得超过100个字符，仅支持汉字，字母，数字和连字符"-", "_"，且不可使用“jrn:”和“jdc-createdby”前缀。
* 同一个账号下，拥有的资源组数量上限为101个，包括1个默认资源组及100个自定义资源组。

>* 系统会为每个用户创建一个“默认资源组”，所有未指定资源组（包括创建时缺省此配置或在资源组功能上线前创建的）的资源均会自动加入“默认资源组”。
## 资源支持的资源组操作：

- [加入资源组](Add-Resource-Groups.md)

- [变更资源组](Change-Resource-Groups.md)

- [资源组筛选](Filter-Resource-Groups.md)
