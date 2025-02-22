#  退订常见问题

### 1. 无法通过控制台（费用管理-[退订管理](https://order-console.jdcloud.com/cost/unsubscribe-list)）申请退订，可能是由于以下原因：

(1) 您申请的云产品不支持退款，当前支持退款的云产品可参考[云服务退订说明](https://docs.jdcloud.com/cn/online-buying/refund)。

(2) 在一个自然年内，申请退款的实例数量或已申请退款的金额超过了可退额度，则无法再次申请。

(3) 按量付费产品不支持退款，如您不需要继续使用，可备份数据后将按量付费云产品关停并释放。

(4) 活动规则中说明不允许退款的场景。

(5) 资源可退金额为0元时，则不支持退订。

(6) 资源由京东云发放的免费测试/赠送代金券购买，则不支持退订。

(7) 实例下存在未支付订单，则无法进行退订。

### 2. 是否支持通过API退订包年包月资源？

暂不支持通API进行退订。

### 3. 参加活动购买的服务器为什么不能退订？

参加活动购买的云产品，当退订规则与活动规则冲突时，以活动规则为准；活动中说明 “不支持退款” 的云服务资源不能退订。

### 4. 为什么我申请退订时显示的退款金额为0？

退款金额为0一般是因为两种原因：

- 原因1：由于您购买的订单是通过免费代金券支付。

- 原因2：按照部分退订的计算规则（`退款金额 = 订单实付金额 - 资源已消耗金额`）计算出来的退订金额为0。

### 5. 退订后金额如何返还？

退款一般原路退回。即：通过网银支付的云产品订单，会退至支付使用的网银账号；通过京东云账户余额支付的订单，会退至账户余额；通过代金券支付的订单，会退回至原代金券余额。

### 6. 退款多长时间可以到账？

如果产品退订成功，退款大约会在2个工作日内退回（退款指用户以现金或代金券方式支付的订单款项）。通过网银支付的订单发生退订时，受银行受理时间影响，预计2-3个工作日内到账。如果长时间未到账，可通过 [提交工单](https://ticket.jdcloud.com/applyorder/submit) 进行查询。

### 7. 在哪里可以查看和确认退款到账？

(1) 订单退款状态查询：控制台 > 费用管理 > [订单管理](https://order-console.jdcloud.com/cost/order-list)

查询退订资源ID对应的订单状态，订单中全部资源退订后订单状态应为 “全部退款”，订单中部分资源退订后订单状态应为 “部分退款”。

(2) 账户余额退款确认：控制台 > 费用管理 > 资金管理 > [资金账户](https://capital.jdcloud.com/cost/capital/capital-overview)

可通过账户充值（收入）信息确认退款到账。

(3) 代金券退款确认：控制台 > 费用管理 > [代金券管理](https://coupon-console.jdcloud.com/cost/coupon)

查看原支付代金券的明细，交易类型为“退款”。
