# 工具函数

为简便开发，框架集成了一些使用频率较高的函数，供直接调用。

## cookie设置

- 函数名：`setAuthorization`
- 位置：`cookieUtils.js`

函数默认以 `Authorization`作为关键字

## cookie删除

- 函数名：`deleteAuthorization`
- 位置：`cookieUtils.js`

直接调用该函数即可！

`cookieUtils.js`文件中也提供其他函数，供需要时使用！

## http请求基础版

- 函数名：`ajax`
- 位置：`axiosHttp.js`
- 参数：`options`

函数是在`axios`基础上封装。`options`为JSON格式，包含请求类型、API地址、超时时间、请求参数。

## http请求调用版

- 函数名：`httpRequestEntrance`
- 位置：`httpRequestEntrance.js`
- 参数：`method`、`url`、`data`、`callback`、`customHttpConfig`

为在http请求前做更多个性化处理，在 `http请求基础版` 基础上封装了该函数，该函数提供了如下功能：

- 按需loading效果(customHttpConfig中配置)
- 成功回调函数
- 自定义超时时间(customHttpConfig中配置)
- 通用错误码拦截

## 列表数据适配

- 函数名：`initTable`
- 位置：`tableUtil.js`
- 参数：`that`、`method`、`url`、`pageConfig`

`initTable`的作用是在获取列表前后做参数适配，主要是分页及搜索条件类适配。

## 文件下载

- 函数名：`exportFile`
- 位置：`utils.js`
- 参数：`filePath`、`params`、`fileName`

参数分别对应：文件下载路径、获取数据所需参数、下载后文件名

## 字符串截取

- 函数名：`interceptParams`
- 位置：`tableUtil.js`
- 参数：
`value`(待截取字符串)
`maxLen`(保留长度，默认 `20`)

## 数据空检测

- 函数名：`isEmpty_reset`
- 位置：`validate.js`
- 参数：`val`
- 返回值：true/false

## 通过路径钻取对象数值
- 函数名：`obtainValueFromObjectPlus`
- 位置：`validate.js`
- 参数：`stringPath`(钻取路径)、`obj`(待取路径)

函数将获取到结果返回，若中途遇到为空情况无法进行则返回空字符串




