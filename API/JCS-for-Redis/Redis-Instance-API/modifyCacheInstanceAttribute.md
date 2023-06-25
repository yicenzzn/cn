# modifyCacheInstanceAttribute


## 描述
修改缓存Redis实例的资源名称或描述，二者至少选一

## 请求方式
PATCH

## 请求地址
https://redis.jdcloud-api.com/v1/regions/{regionId}/cacheInstance/{cacheInstanceId}

|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**regionId**|String|True| |缓存Redis实例所在区域的Region ID。目前有华北-北京、华南-广州、华东-上海三个区域，Region ID分别为cn-north-1、cn-south-1、cn-east-2|
|**cacheInstanceId**|String|True| |缓存Redis实例ID，是访问实例的唯一标识|

## 请求参数
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**cacheInstanceName**|String|False| |实例的名称，名称只支持数字、字母、英文下划线、中文，且不少于2字符不超过32字符|
|**cacheInstanceDescription**|String|False| |实例的描述，不能超过256个字符|


## 返回参数
|名称|类型|描述|
|---|---|---|
|**requestId**|String|本次请求的ID|


## 返回码
|HTTP状态码|错误码|描述|
|---|---|---|
|**200**||OK|

## 请求示例
PATCH
```
@Test
public void testModifyInstanceName() {
  // 1. 设置请求参数
  ModifyCacheInstanceAttributeRequest request = new ModifyCacheInstanceAttributeRequest();
  request.regionId("cn-north-1").cacheInstanceId("redis-1234").cacheInstanceName("update name");

  // 2. 发起请求
  ModifyCacheInstanceAttributeResponse response = redisClient.modifyCacheInstanceAttribute(request);

  // 3. 处理响应结果
  System.out.println(new Gson().toJson(response));
}

```

## 返回示例
```
{
    "requestId": "c3o559jq7qbwwfm9qngbsr7jm99h5mc4"
}
```
