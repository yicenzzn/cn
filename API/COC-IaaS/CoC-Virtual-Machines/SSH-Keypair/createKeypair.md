# createKeypair


## 描述

创建密钥。

公钥和私钥都由京东云生成，公钥保存在京东云，私钥返回给用户，由用户保存。

详细操作说明请参考帮助文档：[创建密钥](https://docs.jdcloud.com/cn/virtual-machines/create-keypair)

## 接口说明
- 调用该接口创建密钥后，公钥部分存储在京东云，并返回未加密的 `PEM` 编码的 `PKCS#8` 格式私钥，您只有一次机会保存您的私钥。请妥善保管。


## 请求方式
POST

## 请求地址
https://coc-vm.jdcloud-api.com/v1/regions/{regionId}/keypairs

|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**regionId**|String|True| |地域ID。|

## 请求参数
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**keyName**|String|True| |密钥对名称，需要全局唯一。<br>只允许数字、大小写字母、下划线“_”及中划线“-”，不超过32个字符。<br>|


## 返回参数
|名称|类型|描述|
|---|---|---|
|**result**|[Result](#result)|响应结果。|
|**requestId**|String|请求ID。|

### <div id="Result">Result</div>
|名称|类型|描述|
|---|---|---|
|**keyName**|String|密钥对名称。|
|**privateKey**|String|密钥对的私钥部分，`PEM PKCS#8` 格式。|
|**keyFingerprint**|String|密钥对的指纹，根据 `RFC4716` 定义的公钥指纹格式，采用 `MD5` 信息摘要算法。|

## 返回码
|HTTP状态码|错误码|描述|错误解析|
|---|---|---|---|
|**200**||OK||
|**400**|FAILED_PRECONDITION|KeyName 'xx' already in use|密钥名称已被使用。|
|**500**|INTERNAL|Internal server error|系统内部错误，请稍后重试。如果多次尝试失败，请提交工单。|
|**500**|UNKNOWN|Unknown server error|服务暂时不可用，请稍后重试。如果多次尝试失败，请提交工单。|

## 请求示例
POST
```
```
/v1/regions/cn-north-1/keypairs
{
    "KeyName": "my-test"
}
```

```

## 返回示例
```
{
    "requestId": "56b5b5d93947d7cc7bfa324cf9db1a37", 
    "result": {
        "keyFingerprint": "cd:d0:0a:97:1f:ac:39:60:15:1e:33:a4:b1:05:50:61", 
        "keyName": "my-test", 
        "privateKey": "-----BEGIN RSA PRIVATE KEY-----\nMIIEpAQE\nkQO6.........hlswWxiNhw==\n-----END RSA PRIVATE KEY-----\n"
    }
}
```
