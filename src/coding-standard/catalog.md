# 目录构建规范

```html
── project-name
   ├── public                    项目公共目录
   │   ├── favicon.ico               Favourite 图标
   │   └── index.html                页面入口 HTML 模板
   ├── src                       项目源码目录
   │   ├── main.js                   入口js文件
   │   ├── App.vue                   根组件
   │   ├── api                       把所有请求数据的接口，按照模块，写在单独的 JS 文件中
   │   │   ├── home.js                   首页接口
   │   │   ├── detail.js                 详情页接口，等等
   │   │   ···
   │   ├── assets                    静态资源目录，公共的静态资源，图片，字体等
   │   │   ├── fonts                     字体资源
   │   │   ├── images                    图片资源，该文件夹下还可以按照功能或模块做更细的划分
   │   │   ···
   │   ├── common                    公共脚本，样式，配置，等动态信息
   │   │   ├── js                        公共脚本
   │   │   │   │── utlis.js                  公共 JS 工具函数
   │   │   │   │── config.js                 公共配置
   │   │   │   ···
   │   │   ├── style                 公共样式，可以是各种预处理语言
   │   │   │   │── index.css                样式主文件
   │   │   │   │── reset.css                重置样式
   │   │   │   ···
   │   │   ···
   │   ├── components                公共组件目录
   │   │   ├── confirm                   弹框组件
   │   │   │   └── index.vue
   │   │   ├── scroll                    局部内容滚动组件
   │   │   │   └── index.vue
   │   │   ···
   │   ├── http                      封装的 HTTP 请求方法
   │   │   ├── axios.js                  Axios 的封装
   │   │   ├── jsonp.js                  JSONP 的封装
   │   │   ···
   │   ├── store                     数据中心
   │   │   ├── state.js                  state 数据源，数据定义
   │   │   ├── mutations.js              同步修改 state 数据的方法定义
   │   │   ├── mutation-types.js         定义 Mutations 的类型
   │   │   ├── actions.js                异步修改 state 数据的方法定义
   │   │   ├── getters.js                获取数据的方法定义
   │   │   └── index.js                  数据中心入口文件
   │   ├── routes                    前端路由
   │   │   └── index.js
   │   └── views                     页面目录，所有业务逻辑的页面都应该放这里
   │       ├── home                      应用首页
   │       │   └── index.vue
   │       ···
   ├── .env.development              Vue 开发环境的配置
   ├── .env.production               Vue 生成环境的配置
   ├── .eslintrc.js                  Eslint 配置文件
   ├── .gitignore                    Git 忽略文件
   ├── package.json                  包依赖文件
   ├── package-lock.json             依赖包版本管理文件
   ├── README.md                     项目介绍
   ├── vue.config.js                 vue/cli 项目脚手架配置
   ···

```

## src 文件说明

**1、src/api 模块的请求方法**。应该参考 src/views 中的直接子文件夹的结构，做映射。

**2、src/assets 项目的静态资源文件**。虽然是静态文件(图片，字体，等)，但是还是经过 webpack 处理会好一些，因为有些比较小的文件会被打包到文件，减少请求和压缩第三方包。这个模块的文件，如果还需要扩展，**一个单词**作为文件夹名字！保持简洁性。

**3、src/common 公共的动态的脚本、样式**。在实际中，样式可能是各种预处理语言写的，请自行组织目录结构。

**4、src/components 公共组件**。放置项目中抽象的基础和业务组件。你应该为每个组件都单独建一个文件夹，以做好组件之间的隔离，并且有一个默认的文件：index.vue 文件，以便引入组件时少写几个字母。默认组件中的文件是一个最小的单位，**不应该有依赖其他组件，或操作 state 状态等行为。**

**5、src/http 主要是关于请求方法的封装**。建议开发过程中不要修改，因为会影响到全局。

**6、src/store 数据中心**。这部分内容比较多，独立出来，详情参考：[数据中心](../store)

**7、src/router 页面路由**。默认所有路由映射写在一个文件，如果需要路由模块化，请自行组织。

**8、src/views 所有业务逻辑的页面**。

## 文件命名规范

**1、所有文件和文件夹，统一使用：小写字母开头，英文中划线分隔的方式命名。必须遵守**！

**2、组件名应该以高级别的 (通常是一般化描述的) 单词开头，以描述性的修饰词结尾**。[参考这里](https://cn.vuejs.org/v2/style-guide/#%E7%BB%84%E4%BB%B6%E5%90%8D%E4%B8%AD%E7%9A%84%E5%8D%95%E8%AF%8D%E9%A1%BA%E5%BA%8F-%E5%BC%BA%E7%83%88%E6%8E%A8%E8%8D%90)

> 目录设计是按照功能划分成一个文件夹，以便于满足日后功能扩展的需要。同时也保证目录的简洁，可读性。
> 注意：这个是 vue/cli 3.0 以上脚手架的目录结构，与 2.0 之前的可能会有一点点差别，但是主要的 src 开发目录是差不多的，可以用作参考。
