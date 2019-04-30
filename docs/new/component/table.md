# Table 表格

## 概述

用于展示多条结构类似的数据，可对数据进行过滤、筛选，支持自定义数据自定义操作。由于框架封装层级关系，
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
