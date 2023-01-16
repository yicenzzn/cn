# 价格总览

合作弹性公网IP包括标准公网IP和边缘公网IP两种类型，支持不同的计费类型，各个计费类型的价格也有所不同。

- [按固定带宽计费](Price-Overview#user-content-1)

- [计费示例](Price-Overview#user-content-3)

<div id="user-content-1"></div>

### 按固定带宽计费


- 合作弹性公网IP支持包年包月、按用量2种计费类型；


| 线路 | 地域 | 带宽  | 包年包月(元/月/Mbps) |
|:--|:--|:--|:---|
|BGP | 香港| 1~5Mbps | 30 |
| |  | 5Mbps以上，每Mbps费用 |100 |
| |曼谷  | 1~5Mbps |35.8 |
| |  | 5Mbps以上，每Mbps费用|71.6|
| | 新加坡 | 每Mbps| 81.55|



<div id="user-content-3"></div>


### 计费示例

| 地域 | 计费类型 | 费用公式 | 计费示例 |
|:---|:---|:---|:---|
| 香港 | 固定带宽包月 | 5Mbps及以下：具体费用见“按固定带宽计费”的价格表5*30 <br />5Mbps以上：(n-5)\*100 | 50Mbps，价格为：150+(50-5)\*100=￥4650元/月 |



## 相关参考

- [计费规则](Billing-Rules.md)
- [创建弹性公网IP](../Operation-Guide/reate-Elastic-IP.md)
- [续费公网IP](../Operation-Guide/Renew-Elastic-IP.md)

