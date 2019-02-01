# 接口配置

框架将后台服务器地址与api分开配置，在使用api位置引用。

## 服务器地址配置

后台地址配置在 `config/APIs.js` 中：

```js
const development = {
  ENV: 'development',
  API: 'http://250.250.250.250:10000/',
  publicPath: './'
}

const testing = {
  ENV: 'testing',
  API: 'http://251.251.251.251:10000/',
  publicPath: './'
}

const sit = {
  ENV: 'sit',
  API: 'http://252.252.252.252:10000/',
  publicPath: './'
}

const production = {
  ENV: 'production',
  API: 'https://background-interface.com/api/',
  publicPath: './'
}
```

使用命令 `npm run dev` 启动本地调试，默认使用 `development` 配置
框架打包时，根据不同命令，将各自后台地址配置到项目中

```js
npm run build:dev   // 引入development配置
npm run build:sit   // 引入sit配置
npm run build:pro   // 引入production配置
```

## api配置

api信息以JSON形式配置在 `apiCenter.json` 中：

```js
{
  "manage": {
     "students": {
        "_comment": "学生所有接口",
        "students_manage": {
          "_comment": "学生管理下所有接口",
          "CRUD": "v1/students"
        }
     }
  }
}
```
在 `main.js` 中全局引入

```js
import apiCenter from 'apiCenter.json'
Vue.prototype.apiCenter = apiCenter
```

在文件中只需正确引入即可

```js
this.apiCenter.manage.students.students_manage.CRUD
```



