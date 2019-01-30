# 项目部署

框架支持人肉手动部署和自动化部署两种方式，部署的基础是根据要部署环境的不同，使用不同的打包命令。

```bash
npm run build:dev     -- dev环境适用
npm run build:sit     -- sit环境适用
```

## 人肉部署

人肉部署即是将上述命令打包出的dist目录内容上传至对应前端服务器。


## 自动化部署

前端组为框架开发了自动化部署工具(需联系管理员对环境做相应配置)，访问 [部署平台](http://indora.dev.cmft.com) 可直达。
平台将有权限部署的项目名称、分支、环境信息列出，供用户选择，选择立即发布，提示该次部署关键信息，选择确定进入部署环节。

### PC版

选择要部署信息:

![deploy-config](../img/deploy-config.png ':size=400x300')



确认所选信息:

![deploy-tip](../img/deploy-tip.png ':size=400x250')



部署结果回传:

![deploy-res](../img/deploy-res.png ':size=600x500')



### 移动版

移动端部署与PC版极其相似，在此仅展示部署信息选择部分

选择要部署信息:

![deploy-m-config](../img/deploy-m-config.png ':size=300x400')

