# Button 按钮

按钮样式在`bootstrap`基础上封装，只需引入对应`class`值即可完成

通用按钮样式当前定义在`common.less`文件中

## Default按钮

使用`btn-default-f`样式，可生成Default按钮

```js
<button type="button" class="btn-default-f">Confirm</button>
```

*正常态：*  
![default正常态](../../img/btn/default.png ':size=100x40')

*hover态：*  
![hover正常态](../../img/btn/default-hover.png ':size=100x40')


## Confirm按钮

使用`btn-confirm-f`样式，可生成Confirm按钮

```js
<button type="button" class="btn-confirm-f">Confirm</button>
```

*正常态：*  
![confirm正常态](../../img/btn/confirm.png ':size=100x40')

Confirm按钮无`hover`效果

## 图标按钮

在基础按钮中加入图标，可以很方便实现图标按钮效果

框架已集成`font awesome`矢量图标库，以此为例

```js
<button type="button" class="btn-confirm-f">
    <i class="fa fa-search"></i>Confirm
</button>

<button type="button" class="btn-default-f">
    <i class="fa fa-plus"></i>Confirm
Confirm</button>
```
*正常态*
![default正常态](../../img/btn/btn-icon.png ':size=200x40')

> 当前，框架中存在部分按钮未纳入组件状态，部分原因是按钮库不够丰富，后续将逐步纳入规范