# 重置密码

如果您在创建实例时候选择暂不设置密码（系统将自动生成密码）、密码丢失，或出于业务和数据的安全考虑定期更换密码，您可通过在控制台上重置密码操作来实现重新设置实例登录密码。

## 前提条件及限制

* 实例必须处于**运行中**状态。若实例处于**已停止**状态，请先操作[启动实例](Start-Instance.md)。
* 若实例处于其他非稳定状态，还请等待前序操作执行完成后再操作重置密码。
	
> 请注意：重置密码操作完成后，您需要在控制台[重启云主机](Reboot-Instance.md)才能使新密码生效。重启操作会中断您业务，建议您规划好操作时间降低操作影响。

## 操作影响
如果实例是Linux系统，且[创建实例](Create-Instance.md)时选择了使用SSH密钥登录，重置密码后密钥将自动解绑，只可通过密码方式登录。

## 操作步骤
1. 访问[合作云主机控制台](https://coccns-console.jdcloud.com/host/compute/list)，即进入实例列表页面。或访问[京东云控制台](https://console.jdcloud.com)点击顶部导航栏**合作云产品-合作云主机**进入实例列表页。
2. 选择地域。
3. 在实例列表中选择需要重置密码的实例，确认其状态为**运行中**。如果需要同时操作多台实例，可通过多选实现。
4. 单台操作：点击**操作-更多-重置密码**按钮，或点击实例名称进入详情页后点击**操作-重置密码**按钮。<br>批量操作：点击列表下方**更多-重置密码**按钮

![image](https://user-images.githubusercontent.com/88134774/198186008-eda72a71-f88e-40c3-b3bc-3735ef9fa499.png)


5. 在弹出的“重置密码”弹窗中，输入符合要求的新密码，点击**确定**提交修改，之后在控制台重启实例后新密码即可生效。
<div align="center"><img src="https://user-images.githubusercontent.com/88134774/198185768-2a4b52de-3bca-49fa-b5e4-1134bcfd1da2.png" width=700px></div>

## 相关参考

[启动实例](Start-Instance.md)

[重启云主机](Reboot-Instance.md)

[创建实例](Create-Instance.md)

