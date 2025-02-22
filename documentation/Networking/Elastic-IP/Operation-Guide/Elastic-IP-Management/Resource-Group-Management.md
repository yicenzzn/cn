# 资源组

### 产品简介
资源组管理提供一种资源管理工具，支持用户对所拥有的云资源从用途、权限、归属等维度上进行分组，以便满足企业内部多用户、多项目的资源分级管理的需求。

### 使用限制

一个公网IP资源只能且必须归属于一个资源组，默认归属于“默认资源组”。

### 添加资源组
为公网IP添加资源组，在创建IP资源时，支持添加资源组，默认添加至“默认资源组”。

#### 前提条件
- 确保您已经[注册京东云账号](https://user.jdcloud.com/register?returnUrl=https%3A%2F%2Fwww.jdcloud.com%2F)，并实现[实名认证](https://docs.jdcloud.com/cn/real-name-verification/introduction)；
- 确保账户中有足够余额，相关限制请查看[使用限制](https://docs.jdcloud.com/cn/elastic-ip/restrictions)；
- 公网IP可创建数量受配额限制，如需提升配额请提[工单申请](https://ticket.jdcloud.com/applyorder/submit)。

#### 操作步骤
步骤1：登录京东云控制台，进入控制台导航页面。

步骤2：在控制台左侧导航栏，选择网络-【私有网络】-【弹性公网IP】，进入弹性公网IP列表页。

步骤3：选择您需要创建弹性公网IP的地域，在弹性公网IP列表页选中对应地域标签，点击申请按键，进入创建弹性公网IP页面。
	
> 进入创建弹性公网IP创建页面后，您也可以通过切换地域标签，实现切换创建弹性公网IP的地域。

步骤4：选择您要创建的弹性公网IP的带宽计费模式、带宽上限、标签等信息。

> 目前标准公网IP支持包年包月、按配置、按用量三种计费类型。

步骤5：在资源组字段，点击下拉菜单选择目标资源组。
 
步骤6：点击【立即购买】，支付完成后，资源创建完成即归属所选资源组。


### 变更资源组
如何修改公网IP所属的资源组。

#### 前提条件

- 确保您已经注册京东云账号，并实现实名认证；
- 确保您只是已有一个弹性公网IP资源；
- 公网IP已属于某个资源组。

#### 操作步骤

步骤1：登录京东云控制台，进入控制台导航页面。

步骤2：在控制台左侧导航栏，选择网络-【私有网络】-【弹性公网IP】，进入弹性公网IP列表页。

步骤3：在弹性公网IP列表页，定位到您需要修改资源组的弹性公网IP。在操作列点击【更多】选择【变更资源组】按键，进入变更资源组弹窗；

步骤4：在弹窗中，选中需要变更到的目标资源组，点击【确定】按钮，完成资源组变更。

注：
> 如您期望变更多个资源组，可选中多个IP资源后，在列表页面左下方，点击更多->变更资源组实现批量变更。

### 筛选资源组
- 确保您只是已有一个弹性公网IP资源；
- 公网IP已属于某个资源组。
#### 操作步骤

步骤1：登录京东云控制台，进入控制台导航页面。

步骤2：在控制台左侧导航栏，选择网络-【私有网络】-【弹性公网IP】，进入弹性公网IP列表页。

步骤3：在搜索框中，选择【资源组ID】，输入资源组ID，如需搜索多个资源组下的资源，请输入多个资源组ID，用逗号隔开。

步骤4：点击搜索Icon即可根据资源组ID筛选出对应的公网IP资源。

## 相关操作
- [创建公网IP](Create-Elastic-IP.md)
