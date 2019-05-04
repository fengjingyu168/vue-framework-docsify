# Password 密码框

## 概述

密码框组件集成密码输入及确认功能，同时加入各种提示，下面介绍如何配置使用

## 组件引入

```js
<PasswordWithConfirm :password="password" @obtainPassword="obtainPassword"></PasswordWithConfirm>
```
## 配置
组件中所需数据由`props`形式在父组件中配置，传入子组件
```js
password: {
            passwordConfig: {
              id: 'passwordConfig',
              label: '密码',
              value: 'password',
              errorTip: '请输入密码',
              regularExpression: [
                {expression: '/^.{8,32}$/', tip: '8-32位字符'},
                {expression: '/^(?=.*[a-z])(?=.*[A-Z])(?=.*\\d)(?=.*[$@$!#$%^&*()_+=])[A-Za-z\\d$@$!]{0,}/', tip: '大小写字母、数字、特殊字符,特殊字符为!@#$%^&*()_+='}
              ]
            }
          }
```
- `id`：为解决在模态框中使用初始化问题所设  
- `value`：密码最终保存字段名  
- `regularExpression`：密码规则

![密码组件](../../img/pwd/pwd-init.png ':size=700x100')

## 说明

`regularExpression`中规则将被解析为密码组件中规则，在条件得到满足或不满足情况，组件会给出清晰提示。
![密码组件-error](../../img/pwd/pwd-error.png ':size=700x140')


在满足所有规则时，组件将显示密码强度
![密码组件-correct](../../img/pwd/pwd-correct.png ':size=700x140')

确认密码框输入与密码框中一致时，密码将通过`obtainPassword`自定义事件回传给父页面，之后再出现密码修改情况，
密码将自动置空，直至密码在此满足要求