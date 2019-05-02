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

## 排序

只需后台支持，table可快速配置列数据排序功能，支持多列同时排序。

![表格排序](../../img/table/table-order.png ':size=700x300')


*tableEle对应配置：*

```js
let tableEle = [
    {title: '名称', value: 'name', sortable: true},
    {title: '备注', value: 'desc'},
    {title: '创建时间', value: 'created_date'}
  ]
```

`table`组件将会为设置`sortable`列渲染上下排序按钮。
同时，在用户点击对应按钮时将列所对应`value`字段转换为排序搜索关键字，获取对应数据。

## 筛选

只需后台支持，table可快速配置列过滤功能，支持多列同时过滤

![表格过滤](../../img/table/table-filter.png ':size=700x300')

框架提供两种配置过滤条件方式：
- 过滤源本地配置
顾名思义，过滤条件硬编码在本地，适用于过滤条件变动频率低场景

```js
let tableEle = [
    {title: '名称', value: 'name',
          filterable: {
            remoteFilters: false, // 是否远程获取过滤条件
            filterAPI: '', // 获取筛选数据接口
            displayName: 'name', // 展示字段(获取条件接口中该字段值作为展示字段)
            filterValue: 'id',   // 展示字段对应值(获取条件接口中该字段作为传递至接口字段值)
            filterParam: 'name', // 传递至接口字段(列表查询接口中对应参数名)
            filterLists: [
              {label: 'Indora_A', value: 'A'},
              {label: 'Indora_B', value: 'B'},
              {label: 'Indora_C', value: 'C'},
              {label: 'Indora_D', value: 'D'},
              {label: 'Indora_E', value: 'E'},
              {label: 'Indora_F', value: 'F'},
              {label: 'Indora_G', value: 'G'},
              {label: 'Indora_H', value: 'H'},
              {label: 'Indora_I', value: 'T'},
              {label: 'Indora_J', value: 'J'}
            ]
          }
        },
    {title: '备注', value: 'desc'},
    {title: '创建时间', value: 'created_date'}
  ]
```

- 过滤源远程获取
远程获取过滤源，适用于过滤条件频繁变动场景

```js
let tableEle = [
    {title: '名称', value: 'name',
          filterable: {
               remoteFilters: true, // 是否远程获取过滤条件
               filterAPI: 'apiCenter.users_manage.CRUD', // 获取筛选数据接口
               displayName: 'name', // 展示字段(获取条件接口中该字段值作为展示字段)
               filterValue: 'id',   // 展示字段对应值(获取条件接口中该字段作为传递至接口字段值)
               filterParam: 'name', // 传递至接口字段(列表查询接口中对应参数名)
               filterLists: []
          }
        },
    {title: '备注', value: 'desc'},
    {title: '创建时间', value: 'created_date'}
  ]
```

## 在线编辑

在线编辑功能为行数据编辑提供快速入口

`编辑入口`：
在鼠标移入可编辑列，对应数据将显示编辑入口
![表格在线编辑开始](../../img/table/table-editOnline-start.png ':size=700x300')

进入入口后，列数据转换为编辑框，在失去光标时触发保存
![表格在线编辑中](../../img/table/table-editOnline-active.png ':size=700x300')

```js
let tableEle = [
    {title: '名称', value: 'name'},
    {title: '备注', value: 'desc', editable: 'editOnline'},
    {title: '创建时间', value: 'created_date'}
  ]
```
`editable`对应值会被框架解析为编辑时回调函数，在在失去光标时触发保存时触发。


## 列数据显示控制

## 操作列管理

## 





