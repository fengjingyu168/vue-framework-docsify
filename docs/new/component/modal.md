# Modal 对话框

## 概述

基于本框架的宗旨，Indora中对话框与一般框架对话框略有不同，模态框中显示的大部分元素直接通过配置完成，无需编写`HTML`代码。

为灵活控制模态框中各种效果，对话框在`bootstrap`模态框基础上封装，实现了逐如数据校验、显示控制等功能

## 基础用法

- 模板引入  
```js
<ModalComponent :modelConfig="modelConfig"></ModalComponent>
```
- 数据配置  
```js
        modelConfig: {
          title: '模态框样例',
          isAdd: true,
          config: [
            {label: '名称', value: 'name', placeholder: '必填,2-60字符', v_validate: 'required:true|min:2|max:60', disabled: true, hide: 'edit', type: 'text'},
            {label: '备注描述', value: 'desc', placeholder: '', type: 'text'},
          ],
          addRow: { // [通用]-保存用户新增、编辑时数据
            name: null,
            desc: null
          }
        }
```

- 说明

```markdown
* 模态框显示与隐藏与`Bootstrap`控制一致
* 组件新增与编辑共用一套模态框，通过`isAdd`字段出发相应区分，`id`默认为`add_edit_Modal`
* 常见显示类型通过配置完成，复杂场景通过`slot`实现

```

## Attributes

属性|说明|类型|默认值
--|--|--|--
title|对话框标题|String|-
isAdd|新增/编辑标志位，仅在此场景下适用|Boolean|true
config|显示信息配置集合|Array|[]
addRow|对话框数据存放位置|JSON|-
modalId|位置标志位|String|add_edit_Modal
modalFooter|自定义按钮|Array|-
saveFunc|响应函数|Function|-


