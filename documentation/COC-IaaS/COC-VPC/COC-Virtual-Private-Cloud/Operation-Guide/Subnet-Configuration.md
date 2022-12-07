# 子网配置

本文将详细介绍如何配置子网。

- [创建子网](subnet-configuration#user-content-1)
- [更换路由表](subnet-configuration#user-content-2)
- [修改子网基本信息](subnet-configuration#user-content-3)
- [查看子网信息](subnet-configuration#user-content-4)
- [删除子网](subnet-configuration#user-content-5)

## 前提条件及限制

- 确保您已经[注册京东云账号](https://user.jdcloud.com/register?returnUrl=https%3A%2F%2Fwww.jdcloud.com%2F)，并实现[实名认证](https://docs.jdcloud.com/cn/real-name-verification/introduction)；
- 确保您已经开通对应的地域
- 确保您已经创建一个私有网络，私有网络有足量的子网配额，如配额已满。可通过[工单申请](https://ticket.jdcloud.com/applyorder/submit)提升配额；
- 子网创建后，CIDR网络块不可修改；
- 同一个VPC下的子网CIDR不可重叠；
- 子网CIDR的第一个地址为网络地址，最后一个地址为广播地址，第二个、倒数第二个和倒数第三个IP地址已被京东云预留用作网络的管理，例如子网的CIDR为10.1.0.0/24，其中10.1.0.0为网络地址，10.1.0.255为广播地址，10.1.0.1、10.1.0.253和10.1.0.254被京东云预留，用户是不可以使用的，故该子网的可用IP个数为251；
- 删除子网资源前须删除其关联的云主机，更多请查看[使用限制](../Introduction/Restrictions.md)。

## 操作步骤

### 创建子网

<div id="user-content-1"> </div>

步骤1：进入[京东云控制台](https://console.jdcloud.com/overview)，点击左侧导航条选择 合作云产品->【合作私有网络】-> 【合作子网】，进入子网列表页；

步骤2：选择创建子网所属地域，点击【创建】按钮，进入创建弹窗；

> 注：进入创建子网创建弹窗后，您也可以通过切换地域标签，实现切换创建子网的地域。


步骤3：选择所属私有网络，子网必须创建在某个私有网络内，若需创建支持IPv6的子网，需选择支持IPv6的私有网络；


步骤4：输入子网名称、子网CIDR、关联的路由表、描述等信息，具体说明如下：


|配置项|说明|示例|
|----|----|-----|
|地域|选择子网所属私有网络所在的地域|中国-香港11|
|名称|设置子网名称，名称不可为空，只支持中文、数字、大小写字母、英文下划线“\”及中划线“\”，且不能超过32字符|subnet-1|
|私有网络|选择需创建子网的私有网络|vpc(10.0.0.0/16)|
|IPv4 CIDR|子网IPv4内网网段，可选范围为10.0.0.0\~10.255.0.0、172.16.0.0\~172.31.0.0、192.168.0.0（以上三个网段的掩码可选范围为16 \~ 28）|10.0.16.0/20|
|路由表|选择子网关联的路由表，必须关联一张路由表，标准子网不能关联已关联边缘子网的路由表；[详细说明](subnet-configuration#user-content-1)|--|


> 注：多个子网的CIDR之间不可重叠，且子网的CIDR不能超过私有网络的边界。

步骤5：点击【确定】，可进入子网列表页查看已创建的子网。


#### **更换路由表**

<div id="user-content-2"></div>
         
创建子网时必须路由表，关联其他路由表通过更换路由表实现，具体步骤如下：

步骤1：进入[京东云控制台](https://console.jdcloud.com/overview)，点击左侧导航条【合作私有网络】-> 【合作子网】，进入子网列表页；

步骤2：定位需要更换路由表的子网，点击操作列的【更换路由表】按钮；或点击对应的名称进入子网详情页，选择路由规则tab页，点击【更换路由表】按钮

步骤3：在弹出的路由表选择页面，选择要为该子网更换的路由表，可为该子网更换所属私有网络中的其他路由表；[详细说明](subnet-configuration#user-content-1)

步骤4：点击【确定】后即可为子网更换路由表；可在路由表侧进行更换子网的路由表，具体操作请查看[从路由侧更换路由表](Route-Table-Configuration.md)。
         


#### 修改子网基本信息
<div id="user-content-3"> </div>
                        

下面将详细介绍如何修改子网的名称或描述内容：

步骤1：进入[京东云控制台](https://coccns-console.jdcloud.com)，点击左侧导航条 【合作私有网络】-> 【合作子网】，进入子网列表页；

步骤2：定位需要更换路由表的子网，点击对应的名称进入子网详情页；

步骤3：点击名称后的修改按钮，即可对子网名称进行修改，具体的名称规则参见子网创建。

#### 查看子网信息

<div id="user-content-4"> </div>

在子网侧支持查看子网的路由表规则，具体步骤如下：

步骤1：进入[京东云控制台](https://coccns-console.jdcloud.com)，点击左侧导航条 【合作私有网络】-> 【合作子网】，进入子网列表页；

步骤2：定位需要查看信息的子网，点击子网名称进入子网详情页，支持查看子网的基本信息，切换Tab页支持查看子网的路由规则。



#### 删除子网

<div id="user-content-5"> </div>

删除子网需要优先删除其包含的云主机等资源，删除其相关配置如DNS等。

步骤1：进入[京东云控制台](https://console.jdcloud.com/overview)，点击左侧导航条 【合作私有网络】-> 【合作子网】，进入子网列表页；

步骤2：定位需要删除的子网，点击操作列的删除；

步骤3：:二次确认删除子网后，即可删除该子网；

> 注：子网详情页的删除操作与列表页的删除操作功能一致，均能删除子网。


## 相关参考
                        
- [子网介绍](../Introduction/Features/Subnet-Features.md)
                       
- [路由表配置](Route-Table-Configuration.md)
                        
- [创建云主机](https://docs.jdcloud.com/cn/virtual-machines/create-instance)
                        
- [使用限制](../Introduction/Restrictions.md)
                        
- [常见问题](../FAQ/FAQ.md)




