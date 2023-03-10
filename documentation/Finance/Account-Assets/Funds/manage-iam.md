# 授权子用户管理资金账户

您可以通过向子用户授权 **资金账户管理员权限**（IAM 系统策略：**JDCloudAssetAdmin**），实现 IAM 子用户对资金账户（查询余额、收支明细、充值、提现）、代金券、资源包和实例抵扣券的管理。

如果您只需要授权对资金账户的操作，请在您的自定义系统策略中包含下述语句：

```JSON
{
	"Version": "3",
	"Statement": [
		{
			"Effect": "Allow",
			"Action": [
				"asset:*",
				"coupon:*"
			],
			"Resource": [
				"*"
			]
		}
	]
}
```
