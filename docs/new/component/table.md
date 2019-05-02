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
`editable`对应值会被框架解析为编辑时回调函数，在失去光标时触发保存时触发。


## 列显示控制

`table`中的部分列可能在多数情况下无需显示，希望用户主动选择显示，列显示控制满足上述需要。

在列属性中设置`display`，框架会将属性为true的值显示在列表中
```js
let tableEle = [
    {title: 'ID', value: 'id', display: false},
    {title: '名称', value: 'name', display: true},
    {title: '备注', value: 'desc', display: true},
    {title: '创建时间', value: 'created_date', display: true},
    {title: '更新时间', value: 'updated_date', display: false}
  ]
```

框架为`table`列管理提供了简易入口，通过图形化勾选实现table显示列控制  
![表格列管理入口](../../img/table/table-manage-column.png ':size=130x100')

![表格列管理](../../img/table/table-manage-column-active.png ':size=500x220')

如果希望某些列用户无法编辑，为该列设置`frozen`属性即可
```js
let tableEle = [
    {title: 'ID', value: 'id', display: false},
    {title: '名称', value: 'name', display: true, frozen: true},
    {title: '备注', value: 'desc', display: true},
    {title: '创建时间', value: 'created_date', display: true},
    {title: '更新时间', value: 'updated_date', display: false}
  ]
```
![表格列固定](../../img/table/table-manage-column-frozen.png ':size=500x220')

## 操作列管理

类似其他框架，table提供了基础单行数据操作功能列，方便对数据进行管理
![表格操作列](../../img/table/table-action-ori.png ':size=700x300')

实现上述效果，需要配置好操作列数据并将数据引入列表配置中. `btn_func`将被框架解析为回调函数

```js
let btn = [
    {btn_name: '编辑', btn_func: 'editF'},
    {btn_name: '删除', btn_func: 'deleteF'}
  ]
  
  table: {
              tableData: [],
              tableEle: tableEle,
              btn: btn,
              filterMoreBtn: 'filterMoreBtn',
              pagination: this.pagination
            }
```

在实际工作中，会出现操作列操作按钮很多的情况，在`table`中一次排开影响显示效果。为适配该情况，框架选择将部分按钮移入更多按钮组中显示

```js
  let btn = [
    {btn_name: '删除', btn_func: 'deleteF'},
    {
      btn_name: 'more', more: [
        {btn_name: '编辑', btn_func: 'editF'},
        {btn_name: '禁用', btn_func: 'forbiddenF'}
      ]
    }]
```

![表格操作列](../../img/table/table-action-more.png ':size=700x300')

列操作按钮中可能会出现互斥的操作，比如：开机与关机；或者在某些条件下无法操作的情况。一般处理方式是在按钮响应后作出判断，
优劣不说，本框架提供了一种按钮显示与否根据数据的自定义处理能力，不同数据显示的按钮不同

首先，需要在`table`数据中做如下配置：
```js
  table: {
              tableData: [],
              tableEle: tableEle,
              btn: btn,
              filterMoreBtn: 'filterMoreBtn',
              pagination: this.pagination
            }
```
`filterMoreBtn`为控制按钮显示的相应函数，框架将此作为回调并将要显示的每条数据回传，在函数中编写显示规则即可

```js
// 操作按钮过滤
      filterMoreBtn (item) {
        let moreBtnGroup = []
        item.id%2 === 0 ？moreBtnGroup.push('editF') ：moreBtnGroup.push('forbiddenF')
       
        return moreBtnGroup
      }
```
如此，在数据id为偶数时仅显示编辑按钮

后续会提供无法操作按钮disable配置

## 操作列浮动 

框架默认在`table`列尺寸超出一定宽度后，出现横向滚动条兼容显示问题，这样会将操作列排在最后，无法默认显示  

![表格操作列](../../img/table/table-action-more-hide.png ':size=700x300')

为此，`table`提供`handleFloat`配置，设置后操作列会浮动显示在最右侧

```js
table: { // [通用]-table组件相关配置
            tableData: [],
            tableEle: tableEle,
            btn: btn,
            pagination: this.pagination,
            handleFloat: true
          }
```
![表格操作列](../../img/table/table-action-overflow.png ':size=700x300')

## 数据处理

`table`组件通过`render`函数提供数据处理能力。在需要处理的列编写相应的处理函数，便可。
经常使用到的场景为数据展示前拼接、数据转换等

```js
let tableEle = [
    {title: 'ID', value: 'id', display: false},
    {
      title: '名称', value: 'name', display: true,
      render: (item) => {
        return item.name + '_Good'
      }
    },
    {title: '备注', value: 'desc', display: true},
    {title: '创建时间', value: 'created_date', display: true},
    {title: '更新时间', value: 'updated_date', display: false}
  ]
```

![表格列处理](../../img/table/table-render.png ':size=700x300')




