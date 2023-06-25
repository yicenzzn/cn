# describeClientList


## 描述
查询当前客户端IP列表

## 请求方式
GET

## 请求地址
https://redis.jdcloud-api.com/v1/regions/{regionId}/cacheInstance/{cacheInstanceId}/clientList

|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**regionId**|String|True| |缓存Redis实例所在区域的Region ID。目前有华北-北京、华南-广州、华东-上海三个区域，Region ID分别为cn-north-1、cn-south-1、cn-east-2|
|**cacheInstanceId**|String|True| |缓存Redis实例ID，是访问实例的唯一标识|

## 请求参数
无


## 返回参数
|名称|类型|描述|
|---|---|---|
|**result**|[Result](describeclientlist#result)|结果|
|**requestId**|String|本次请求ID|

### <div id="result">Result</div>
|名称|类型|描述|
|---|---|---|
|**ips**|[Ips[]](describeclientlist#ips)|IP列表：包含IP和连接数|
### <div id="ips">Ips</div>
|名称|类型|描述|
|---|---|---|
|**ip**|String|client的ip地址|
|**clientCount**|Integer|clientIp地址下对应的client个数|

## 返回码
|HTTP状态码|错误码|描述|
|---|---|---|
|**200**||OK|

## 请求示例
GET
```
@Test
public void testGetClientList() {
  // 1. 设置请求参数
  DescribeClientListRequest request = new DescribeClientListRequest();
  request.regionId("cn-north-1").cacheInstanceId("redis-1234");

  // 2. 发起请求
  DescribeClientListResponse response = redisClient.describeClientList(request);

  // 3. 处理响应结果
  System.out.println(new Gson().toJson(response));
}

```

## 返回示例
```
{
    "requestId": "c3o95bwhnfcoh3uqpqowjoouuk4g2m28", 
    "result": {
        "ips": [
            {
                "clientCount": 3, 
                "ip": "10.0.5.8"
            }
        ]
    }
}
```
