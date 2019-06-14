# 数据状态管理

在此之前，你应该先考虑：**是否真的需要使用统一的方法来管理你的数据？**

**然后了解一些数据中心的一些基本概念。**比如：数据中心是什么，如何工作的，如何提交一个Mutations，Actions，···

建议你去 [Vuex 官网](https://vuex.vuejs.org/zh/)  看看，然后再决定。

## 目录结构

现在不懂每个文件的作用没关系，我们会在后面，通过一个小小的购物车的例子，一步步带领你熟悉 Vuex 的使用，并说清楚为什么这样做。

```html
── store                              Store 目录
  ├── index.js                        数据中心的入口文件
  ├── state.js                        数据仓库，数据中心的数据源：state
  ├── mutation.types.js               定义 Mutations 的函数的名字
  ├── mutations.js                    定义 同步 操作数据源的函数
  ├── actions.js                      定义 异步 操作数据源的函数
  ├── getters.js                      定义从 State 中获取数据的函数
```

> 这个文档是建立在你有一定认知的基础上，能够帮助到你快速进入到生产开发的状态！以后可能会频繁使用 ES6 的语法，如果你还不是很熟悉，可以移步阮一峰老师的：[ECMAScript 6 入门](http://es6.ruanyifeng.com/)
