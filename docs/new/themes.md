# 项目样式

根据样式具体需要及历史原因，框架样式会出现在三个位置，具体为全局引入公用样式、样式配置文件引入、页面独立样式。

## 全局引入公用样式

第三方组件样式，框架抽离出的全局样式，均在main.js中引入。该部分样式将会应用到框架全局，而无需页面单独引人。

```js
import 'iview/dist/styles/iview.css'
```


## 样式配置文件引入

为规范使用样式，框架将样式指标独立配置，页面直接应用对应样式关键字实现样式添加。这个的好处是样式方便管理，可控。

框架将样式指标配置在less文件中：

```css
@color-blue: #0080FF;
@color-red: red;
@color-gray: #cccccc;
```

为全局引入该less文件，需要引入 `sass-resources-loader` 包

```js
npm install sass-resources-loader --save
```

同时在 `build/utils.js` 中引入

```js
function lessResourceLoader() {
    var loaders = [
      cssLoader,
      'less-loader',
      {
        loader: 'sass-resources-loader',
        options: {
          resources: [
            path.resolve(__dirname, '../src/common/common.less'),
          ]
        }
      }
    ];
    if (options.extract) {
      return ExtractTextPlugin.extract({
        use: loaders,
        fallback: 'vue-style-loader'
      })
    } else {
      return ['vue-style-loader'].concat(loaders)
    }
  }

// 具体位置在框架中查看
less: lessResourceLoader()

```

在框架其他位置便可使用如下方式引入：

```css
.demo {
  color: @color-blue
}

```

## 页面独立样式

由于各种原因，框架vue文件中散落了css样式，表现形式类似下面这种：

```css
<style lang="less" scoped>
  .demo {
    border-bottom: 2px solid @color-blue;
  }
```

这种方式会在后面的迭代中，一点点减少。



```css
由于各种原因，框架vue文件中散落了css样式，表现形式类似下面这种：由于各种原因，框架vue文件中散落了css样式，表现形式类似下面这种：由于各种原因，框架vue文件中散落了css样式，表现形式类似下面这种：由于各种原因，框架vue文件中散落了css样式，表现形式类似下面这种：由于各种原因，框架vue文件中散落了css样式，表现形式类似下面这种：由于各种原因，框架vue文件中散落了css样式，表现形式类似下面这种：由于各种原因，框架vue文件中散落了css样式，表现形式类似下面这种：由于各种原因，框架vue文件中散落了css样式，表现形式类似下面这种：由于各种原因，框架vue文件中散落了css样式，表现形式类似下面这种：由于各种原因，框架vue文件中散落了css样式，表现形式类似下面这种：

```

```text
由于各种原因，框架vue文件中散落了css样式，表现形式类似下面这种：由于各种原因，框架vue文件中散落了css样式，表现形式类似下面这种：由于各种原因，框架vue文件中散落了css样式，表现形式类似下面这种：由于各种原因，框架vue文件中散落了css样式，表现形式类似下面这种：由于各种原因，框架vue文件中散落了css样式，表现形式类似下面这种：由于各种原因，框架vue文件中散落了css样式，表现形式类似下面这种：由于各种原因，框架vue文件中散落了css样式，表现形式类似下面这种：由于各种原因，框架vue文件中散落了css样式，表现形式类似下面这种：由于各种原因，框架vue文件中散落了css样式，表现形式类似下面这种：由于各种原因，框架vue文件中散落了css样式，表现形式类似下面这种：

```

```js
由于各种原因，框架vue文件中散落了css样式，表现形式类似下面这种：由于各种原因，框架vue文件中散落了css样式，表现形式类似下面这种：由于各种原因，框架vue文件中散落了css样式，表现形式类似下面这种：由于各种原因，框架vue文件中散落了css样式，表现形式类似下面这种：由于各种原因，框架vue文件中散落了css样式，表现形式类似下面这种：由于各种原因，框架vue文件中散落了css样式，表现形式类似下面这种：由于各种原因，框架vue文件中散落了css样式，表现形式类似下面这种：由于各种原因，框架vue文件中散落了css样式，表现形式类似下面这种：由于各种原因，框架vue文件中散落了css样式，表现形式类似下面这种：由于各种原因，框架vue文件中散落了css样式，表现形式类似下面这种：

```