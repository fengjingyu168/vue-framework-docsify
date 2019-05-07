# 数据校验

Indora中引入第三方校验框架[VeeValidate](https://baianat.github.io/vee-validate/),作为框架主验证形式

目前，数据校验集中在模态框中使用，后续将视情况推广至其他场景

## 插件引入

- 插件安装

```js
# install with npm
npm install vee-validate
```

- 框架集成

1、编写`VeeValidate`配置文件，包含通用配置及自定义校验规则(`VeeValidate.js`)  
2、`main.js`中引入配置文件并注入`Vue`实例
```js
import VeeValidate from './common/veeValidate/VeeValidate'
Vue.use(VeeValidate)
```

## 使用

- 模态框

由于modal组件已集成`VeeValidate`，在使用时只需要将对应规则配置在`v_validate`字段中即可。
在输入不满足规则时，在相应区域下方将给出相应错误提示

```js
modelConfig: {
          title: '租户管理',
          isAdd: true,
          config: [
            {label: '名称', value: 'name', placeholder: '必填,2-60字符', v_validate: 'required:true|min:2|max:60', disabled: true, hide: 'edit', type: 'text'},
            {label: '备注描述', value: 'desc', placeholder: '', disabled: false, type: 'text'},
          ],
          addRow: { // [通用]-保存用户新增、编辑时数据
            name: null,
            desc: null
          }
        }
```


![校验出错](../img/v-validate/error.png ':size=450x240')


## 自定义规则

在官方规则不能满足需求时，可通过配置自定义规则完成校验

- 规则配置

```js
Validator.extend('noChinese', {
  getMessage: () => '不能包含中文',
  validate: value => {
    return !(/[\u4E00-\u9FA5]|[\uFE30-\uFFA0]/gi.test(value))
  }
})
```
- 使用

```js
modelConfig: {
          title: '租户管理',
          isAdd: true,
          config: [
            {label: '名称', value: 'name', placeholder: '必填,2-60字符', v_validate: 'required:true|noChinese', disabled: true, hide: 'edit', type: 'text'},
            {label: '备注描述', value: 'desc', placeholder: '', disabled: false, type: 'text'},
          ],
          addRow: { // [通用]-保存用户新增、编辑时数据
            name: null,
            desc: null
          }
        }
```

- 效果

![自定义规则](../img/v-validate/DIY_rules.png.png ':size=450x240')