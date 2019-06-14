# 第五步：整合所有-数据中心入口

前面一直在讲Vuex 的每个模块的作用，可能听着有点犯迷糊，不知道是用来干嘛的，所以这里做一个汇总，并且这里也是数据中心的入口。

## 完整数据中心

一个完整数据中心的结构应该是这样的：

```javascript
export default new Vuex.Store({
  state, // 数据源，对应这State的部分
  mutations, // 同步修改数据
  actions, // 异步修改数据
  getters // 获取数据
})
```

这里面**不一定什么都需要有，其中的actions 是可以省略的**，如果没有涉及异步的情况。

所以结合前面的知识，当我们拆封 Vuex 的时候，我们大概会看到一开始，首页中的目录结构，并且这个index.js 最为Vuex 的入口，我们完整的看到应该是这样的：

```javascript
import Vue from 'vue'
import Vuex from 'vuex'
import state from './state' // 引入数据中心，其实就是一个对象
import * as actions from './actions' // ES6 语法，引入全部的 Actions，并且命名为：actions
import * as getters from './getters' // ES6 语法，引入全部的 Getters，并且命名为：getters
import mutations from './mutations' // 引入全部的 通过常量定义的 mutations
import createLogger from 'vuex/dist/logger' // 引入开发时的控制台数据跟踪日志工具

// 用于开发测试，上线时关闭
const isDebug = process.env.NODE_ENV !== 'production'

Vue.use(Vuex) // 挂在到Vue 的原型链上

export default new Vuex.Store({
  state,
  actions,
  getters,
  mutations,
  strict: isDebug,
  plugins: isDebug ? [createLogger()] : []
})
```

以上就是数据中心的内容。这里的很多东西，可能只能够帮你快速了解项目和解决项目上遇到的部分问题。
如果你需要一个详细可靠的文档，还是建议你参考 [官方文档](https://vuex.vuejs.org/zh/)。
