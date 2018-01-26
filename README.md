## 前言
最近做了一套后台管理系统，参考的是饿了么大神[花裤衩](https://github.com/PanJiaChen)的[vue-element-admin](https://github.com/PanJiaChen/vue-element-admin),自己跟着撸一遍之后突然想比对一下react和vue在后台管理系统的方案以及架构，于是有了此项目。

## 参考
- [手摸手，带你用 vue 撸后台 系列一(基础篇)](https://juejin.im/post/59097cd7a22b9d0065fb61d2)
- [手摸手，带你用 vue 撸后台 系列二(登录权限篇)](https://juejin.im/post/591aa14f570c35006961acac)
- [手摸手，带你用 vue 撸后台 系列三 (实战篇)](https://juejin.im/post/593121aa0ce4630057f70d35)
- [手摸手，带你用 vue 撸后台 系列四(vueAdmin 一个极简的后台基础模板)](https://juejin.im/post/595b4d776fb9a06bbe7dba56)
- [手摸手，带你封装一个 vue component](https://segmentfault.com/a/1190000009090836)
- [手摸手，带你优雅的使用 icon](https://juejin.im/post/59bb864b5188257e7a427c09)

## 简介
本项目集合vue+vuex+vue-router+element-ui、react+react-router-dom+redux+antd-design(分别用比较火的两个脚手架create-react-app和蚂蚁金服的react轻量级框架dva)
着重想介绍后台管理系统中的**权限管理**，**网络请求**、**状态机**、**缓存**、**组件的写法**、**打包上线**、**优化**以及在构建一个后台系统中可能会遇到的杂七杂八的问题，希望读者能够少走弯路。<br />
(本文档将持续更新...)

## 注意
<p align="center;" style="color:#ff5858;font-size:18px">
 本项目的代码只是作为参考，真正想搭自定义的框架请使用脚手架一步步来，这样才会学得更多
</p>

## vue部分
### 项目搭建和必装的插件
不得不说vue的构建工具真tm舒服，简直可以简化很多工作了。使用[vue-cli](https://github.com/vuejs/vue-cli)的命令
`vue init webpack my-project`生成我们第一个vue项目（点击**vue-cli**查看安装教程）,这里我们还需要[element-ui](http://element-cn.eleme.io/#/zh-CN/component/installation)和vuex,分别使用一下命令：<br>
`npm i element -S`<br>
`npm i vuex -S`<br>
至此我们完成项目的第一步

### 本地服务器的搭建
本地开发的我开的是php的服务，用nginx搭的服务器，nginx的详细配置请点击[此处](http://blog.csdn.net/hzsunshine/article/details/63687054)
当然你也可以使用云端的服务器地址，**不过我的建议是开发的时候自己在本地搭一套服务也是极好的，这样可以方便我们修改接口，而不用等到线上更新**。我们还可以使用**mock**，<span style="color:#ff5858;font-size:18px;font-weight:bold">
前提是我们在与后端一起定义好接口文档，实现前后分离快速开发</span>,
mock的教程点击[此处](https://www.cnblogs.com/zhenfei-jiang/p/7235339.html)<br>
这些工作都做完之后我们可能会遇到跨域的问题：<span style="color:#ff5858;font-size:18px;font-weight:bold">此时不要慌，打开根目录下的config文件夹，打开index,js，在dev选项里添加proxyTable</span>,代码参考：<br>
```
port: 9528,
proxyTable: {
  '/api': {
    target: 'http://localhost:1091',
    changeOrigin: true,
    pathRewrite: {
      '^/api': '/api'
    }
  }
},
```
此处的意思是将本地服务器9528的/api请求转发到1091的/api处,1091为我们本地nginx的服务

### 封装网络请求
在我们的src项目下新建一个utils文件夹放我们的公共方法



### 权限管理
*权限管理部分包括登录权限，菜单权限，请求权限等*
