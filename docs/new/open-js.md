# 工具函数

为简便开发，框架集成了一些使用频率较高的函数，供直接调用。

## cookie设置

- 函数名：`setAuthorization`
- 所属位置：`cookieUtils.js`

函数默认以 `Authorization`作为关键字

## cookie删除

- 函数名：`deleteAuthorization`
- 所属位置：`cookieUtils.js`

直接调用该函数即可！

`cookieUtils.js`文件中也提供其他函数，供需要时使用！

## http请求基础版

- 默认函数名：`ajax`
- 所属位置：`axiosHttp.js`
- 参数：`options`

函数是在`axios`基础上封装。`options`为JSON格式，包含请求类型、API地址、超时时间、请求参数。

## http请求调用版

- 默认函数名：`httpRequestEntrance`
- 所属位置：`httpRequestEntrance.js`
- 参数：`method`、`url`、`data`、`callback`、`customHttpConfig`

为在http请求前做更多个性化处理，在 `http请求基础版` 基础上封装了该函数，该函数提供了如下功能：

- 按需loading效果(customHttpConfig中配置)
- 成功回调函数
- 自定义超时时间(customHttpConfig中配置)
- 通用错误码拦截



## 列表数据适配

## 文件下载

## 字符串截取

## 数据空检测

## 对象数据钻取
valueFromExpression


