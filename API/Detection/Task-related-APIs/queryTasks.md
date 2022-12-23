# queryTasks


## 描述
查询任务列表

## 请求方式
GET

## 请求地址
https://detection.jdcloud-api.com/v3/tasks


## 请求参数
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**taskId**|Long|False| |任务Id|
|**taskName**|String|False| |任务名称 模糊匹配|
|**taskUrl**|String|False| |任务地址 模糊匹配|
|**taskType**|Integer|False| |任务类型 1、协议 2、网络|
|**protocolType**|Integer|False| |协议类型 1、TCP 2、UDP 3、SMTP 4、HTTP_HTTPS 5、FTP|
|**taskClassify**|Integer|False| |任务类别 1、定时拨测 2、即时拨测 默认定时拨测|
|**taskGroupId**|Long|False| |任务组ID|
|**pageIndex**|Integer|True| |当前页码 需大于等于1|
|**pageSize**|Integer|True| |每页大小 取值范围1到100|
|**status**|Integer|False| |任务状态 0开启 1禁用|


## 返回参数
|名称|类型|描述|
|---|---|---|
|**result**|[Result](#result)| |
|**requestId**|String|请求的标识id|

### <div id="Result">Result</div>
|名称|类型|描述|
|---|---|---|
|**success**|Boolean| |
|**message**|String| |
|**total**|Integer| |
|**data**|[Task[]](#task)| |
### <div id="Task">Task</div>
|名称|类型|描述|
|---|---|---|
|**taskId**|Long|任务ID|
|**taskName**|String|任务名称|
|**taskUrl**|String|任务地址|
|**taskType**|Integer|任务类型 1、协议 2、网络|
|**protocolType**|Integer|协议类型|
|**taskGroupId**|Long|任务组ID|
|**taskGroupName**|String|任务组名称|
|**monitorPointCount**|Integer|拨测点数量|
|**monitorInterval**|Integer|拨测点频率|
|**monitorStartDate**|String|拨测开始时间|
|**monitorEndDate**|String|拨测结束时间|
|**status**|Integer|状态 0开启 1禁用|
|**createdDate**|String|任务的创建时间|

## 返回码
|HTTP状态码|错误码|描述|
|---|---|---|
|**200**||拨测任务列表|
