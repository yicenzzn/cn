# 小程序开发指南

已对 微信、支付宝、百度、京东、字节，开发框架 Taro3、Uni-app 的支持。


## 手动上报
将探针对象设置到一个全局属性上，方便后面页面手动埋点上报函数的调用。
例：
app.globalData.__sgm__ = sgmSdk;
或
Vue.prototype.__sgm__ = sgmSdk;

1、在app({})中添加全局变量
```
globalData: {
    __sgm__: sgmSdk
}
```

2、在各个页面生命中期或者逻辑处理过程中，可以手动调用如下方法进行上报：
前提：page顶部添加如下代码：
```
const app = getApp()
```

2.1 自定义手动上报
```
// 以防调用逻辑影响业务，切记一定进行catch
try {
    app.globalData.__sgm__.custom({
        type:2,
        code:'wx-custom',
        msg:'custom report testing'
    });
} catch (e) {

}
```

小程序内其他自定义上报可参考如下API：

## custom: 自定义上报

此接口用于上报小程序内页面中的自定义数据，用于自身跟踪查询问题或收集关键数据所用。

### 用法

```javascript
// 以防调用逻辑影响业务，切记一定进行catch
try {
  app.globalData.__sgm__.custom({type,code,msg});
} catch (e) {

}
```

### 参数说明

参数 | 类型 | 描述 | 是否必须 | 默认值
--- | --- | --- | --- | ---
type | int | 自定义类型（1-error,2-warn,3-info） | 是 | -
code | String | 自定义标示代码，可以是任意字符串，用于查询。最大长度128，超过将截取 | 是 | -
msg | String | 自定义信息，可以传入对象。最大长度1024，超过将截取 | 是 | -

## api: 接口请求上报

此接口用于上报小程序内页面接口请求，SGM 探针脚本默认会监听所有的 wx.request 或jd.request 请求，不管这些接口调用是否成功，都会采集。你也可以调用 `app.globalData.__sgm__.api` 来手动上报。


### 用法

```javascript
// 以防调用逻辑影响业务，切记一定进行catch
try {
  app.globalData.__sgm__.api({ url, status, code, msg, time, requestLength, requestType });
} catch (e) {

}
```

### 参数说明

参数 | 类型 | 描述 | 是否必须 | 默认值
--- | --- | --- | --- | ---
url | String | 接口 url，必须是全 url，即以 http 或 https 开头的 url | 是 | -
status | int | 接口返回状态码，如 200，404，500 等 | 是 | -
code | String | 接口返回业务 code | 否 | 空字符串
msg | String | 接口返回描述 | 否 | 空字符串
time | long | 请求耗时，毫秒 | 是 | -
requestLength | int | 请求头长度 | 否 | 0
requestType | string | 请求类型，wx.request 或 jd.request | 否 | wx.request

对于接口请求上报的其他字段，SGM 会帮我们自动处理

## error: 错误上报

此接口用于上报小程序内页面中发生的 JS 错误或者异常。

默认情况下，SGM 会自动上报小程序内页面错误日志，但由于小程序本身的一些限制，错误后可能会影响程序逻辑和后续展现，此时就可以手动上报；


### 用法

```javascript
// 以防调用逻辑影响业务，切记一定进行catch
// 1
const error = new Error('测试错误');
try {
  app.globalData.__sgm__.error(error);
// 或者 2
  app.globalData.__sgm__.error({ msg, stack, filename, lineno, colno, errorType, errorLevel });
} catch (e) {

}
```

上面第一种用法直接传入错误实例，第二种用法对象

### 参数说明

参数 | 类型 | 描述 | 是否必须 | 默认值
--- | --- | --- | --- | ---
error | Error | 错误实例对象，一般为 Error 或者继承 Error 的错误实例对象 | 是 | -
msg | String | 出错信息。最大长度256，超过将截取 | 是 | -
stack | String | 错误堆栈信息。最大长度256，超过将截取 | 是 | -
filename | String | 出错文件 | 否 | -
lineno | int | 出错行 | 否 | 0
colno | int | 出错列 | 否 | 0
errorType | String | 错误类型，默认取 event.type，手动上报时也可以设置其他值 | 否 | error
errorLevel | int | 异常级别 | 否 | 1，表示最高，可以是其他值，如 2，3，4 等

