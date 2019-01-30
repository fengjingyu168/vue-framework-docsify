# 框架由来

做任何一件事情都是不容易的。那么在有诸如 [Element-UI](http://element.eleme.io) [iview](https://www.iviewui.com) 等优秀中后台前端框架的情况下，我们为什么还要做眼前的这个框架呢？
我们的考虑主要基于以下几点:

## 现有框架某些组件存在bug

iview2.0 Slider 滑块组件在手动删空数字输入框后，输入框无法正常显示，且页面报错

![iview2.0 Slider 报错](../img/origin-error1.png ':size=700x300')

iview3.0 Slider 滑块组件在手动删空数字输入框后，虽页面未报错，但输入框无法正常显示

![iview3.0 Slider 报错](../img/origin-error2.png ':size=700x300')

即便在iview3.0中解决了相关问题，这也不是一件轻松的事情，因为框架基于iview2.0，在升级为iview3.0的过程中会有无辜组件受影响增加开发、测试成本

## 部分特殊需求，框架支持困难



