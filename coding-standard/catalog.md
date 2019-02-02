# 目录构建规范

对于项目的结构，你可以自由组织你的项目结构，这里给出的是项目中使用的习惯，建议参考。

```
   │
   ├── public                          项目公共目录
   │   ├── favicon.ico                     页面入口 HTML 模板
   │   └── index.html                      Favourite 图标
   ├── src                             项目源码目录    
   │   ├── main.js                         入口js文件
   │   ├── App.vue                         根组件
   │   ├── components                      公共组件目录
   │   │   └── title.vue
   │   ├── assets                          资源目录，这里的资源会被wabpack构建
   │   │   ├── css                         公共样式文件目录
   │   │   ├── js                          公共js文件目录
   │   │   └── img                      图片存放目录
   │   ├── routes                          前端路由
   │   │   └── index.js
   │   ├── store                           应用级数据（state）
   │   │   └── index.js
   │   └── views                           页面目录
   │       ├── hello.vue
   │       └── notfound.vue
   ├── static                          纯静态资源，不会被wabpack构建。
   └── test                            测试文件目录（unit&e2e）
       └── unit                            单元测试
           ├── index.js                        入口脚本
           ├── karma.conf.js                   karma配置文件
           └── specs                           单测case目录
               └── Hello.spec.js

```
