# Byakugan 高级搜索

常见页面搜索功能可能会存在两方面问题：搜索条件有限、搜索区域占位过大。
`Byakugan`高级搜索功能可实现搜索条件无限扩展，正常占位为原始搜索框大小。

## 配置

- 组件引用  

```js
<byakugan :selectionConditions="selectionConditions" ref="superSearch"></byakugan>
```

- 数据配置  

如下举例展示三种搜索条件配置方式：输入、本地数据选择、远程数据选择

```js
selectionConditions: [ // 设置所有可筛选条件
              {name: '主机名', value: 'hostname__icontains', type: 'input', display: true},
              {
                name: '状态', value: 'vm_state', type: 'select', display: true,
                filterable: {
                  remoteFilters: false, // 是否远程获取过滤条件
                  filterAPI: '', // 获取筛选数据接口
                  displayName: 'name', // 展示字段(获取条件接口中该字段值作为展示字段)
                  filterValue: 'id',   // 展示字段对应值(获取条件接口中该字段作为传递至接口字段值)
                  filterParam: 'vm_state', // 传递至接口字段(列表查询接口中对应参数名)
                  filterLists: [
                    {label: '创建中', value: 'building'},
                    {label: '运行', value: 'active'},
                    {label: '暂停', value: 'paused'},
                    {label: '挂起', value: 'suspended'},
                    {label: '关机', value: 'stopped'},
                    {label: '错误', value: 'error'},
                    {label: '更新中', value: 'resized'}
                  ]
                }
              },
              {
                name: '镜像', value: 'image_id', type: 'select', display: true,
                filterable: {
                  remoteFilters: true, // 是否远程获取过滤条件
                  filterAPI: apiCenter.list, // 获取筛选数据接口
                  displayName: 'name', // 展示字段(获取条件接口中该字段值作为展示字段)
                  filterValue: 'id',   // 展示字段对应值(获取条件接口中该字段作为传递至接口字段值)
                  filterParam: 'image_id', // 传递至接口字段(列表查询接口中对应参数名)
                  filterLists: []
                }
              }
            ]
```

## 使用说明

- 搜索展示态

![展示](../../img/byakugan/b-show.png ':size=400x60')

- 搜索条件选择

光标定位在搜索框内，`byakugan`将可搜索条件展示供用户选择

![展示](../../img/byakugan/b-normal.png ':size=400x300')

选中后展示在搜索框中，根据搜索条件不同，分别显示输入态或对应可选择结果供用户选择

*input型搜索：*   
![展示](../../img/byakugan/b-input.png ':size=400x60')

*select型搜索：*   
![展示](../../img/byakugan/b-search.png ':size=400x300')

- 触发搜索

input型搜索支持回车及放大图标触发搜索，select型搜索在选中搜索值后自动触发搜索
![展示](../../img/byakugan/b-action.png ':size=400x100')

