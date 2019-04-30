# Table 表格

## 概述

用于展示多条结构类似的数据，可对数据进行过滤、排序，支持自定义数据自定义操作。由于框架封装层级关系，
在展示代码是只提供核心代码，对比框架源码你将一目了然。

## 基础表格

基础表格展示效果

![基础表格](../../img/table/table-base.png ':size=700x300')

使用如下列表配置，并传入对应数据，即可渲染出如上效果。

*table基础配置：*

```js
          table: {
            tableData: [],
            tableEle: tableEle
          }
```

*tableEle对应配置：*

```js
let tableEle = [
    {title: '名称', value: 'name'},
    {title: '备注', value: 'desc'},
    {title: '创建时间', value: 'created_date'}
  ]
```
`title`对应值将渲染成列名称，`value`对应值将渲染成列值

## 分页

区别于其他组件库，我们将分页功能视为table的基础能力，分页与table成对出现。分页使用iview分页组件。

![表格分页](../../img/table/table-pagination.png ':size=700x300')

*table基础配置：*
```js
          table: {
            tableData: [],
            tableEle: tableEle
          },
          pagination: {
            __orders: '-name', // 默认排序
            current: 1,
            total: 0,
            __limit: 10, // 每页条数
            __offset: 0  // 偏移量
          }
```

分页配置中`__orders`、`__limit`、`__offset`为适配当前后台所设，数据将在请求列表数据返回前后转换。