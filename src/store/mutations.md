# 第二步：修改 State 的数据（Mutations）

经过上面一节，你已经迈出了第一步：如何定一个数据源。仓库是有了，但是我们如何在里面存储东西呢？

这就引出了我们这节的主要内容：**同步修改 State 中的数据**。

> **注意**：修改 State 里面的数据有同步方法和异步方法，Vuex 中有严格的规定，不能混用。稍后将会说异步方法。

根据 Vuex 的规定：更改 Vuex 的 store 中的状态的唯一方法是提交 mutation。Vuex 中的 mutation 非常类似于事件：每个 mutation 都有一个字符串的 **事件类型 (type)** 和 **一个 回调函数 (handler)**。这个回调函数就是我们实际进行状态更改的地方，并且它会接受 state 作为第一个参数和载荷：

```javascript
new Vuex.Store({
  state: {
    cardData: []
  },
  mutations: {
    modefyCarData (state, arr) {
      // 变更数据源的数据
      state.cardData = arr
    }
  }
})
```

你不能直接调用一个 mutation handler。这个选项更像是事件注册：“当触发一个类型为 increment 的 mutation 时，调用此函数”。要唤醒一个 mutation handler，你需要以相应的 type 调用 store.commit 方法：

```javascript
store.commit('modefyCarData', [
  // 购物车载荷数据
])
```

到这里，你应该就已经初步知道怎么修改 State 的数据了。但是感觉修改的路径特别长，而且特别麻烦，有没有更好的办法呢？答案是：有的！

## 优化

**1、单独维护一个mutations 文件。</strong>想想看，当我们有很多状态需要维护的时候，```new Vuex.Store({})```部分就会显得特别臃肿，难以维护。所以这就解释了在开始介绍目录的时候，为什么会多出来这么多的文件夹。把单独功能的部分抽离出来，更方便维护。包括后面的：actions，getters 是相同的道理。

**2、单独维护一个事件类型文件。</strong>既然前面说了：在 mutations 中定义的是一个事件类型，所以我们也可以单独把 mutations 的类型提取出来单独维护。

**3、使用数据中心的语法糖。</strong>我们每次提交都会手动的调用 ```store.commit(type, paloy)``` 的方式，感觉很麻烦。这一点贴心的作者给我们提供了几个语法糖：mapMutations, mapActions, mapGetters 分别对应到：mutations, actoins, getters，它们把后面的脏活累活都做了。

所以根据以上的优化，在项目中，应该是这样的：

```javascript
// mutations.types.js
/**
* 设置购物车数据的 Mutations
* @type {string}
*/
export const SET_CARD_DATA = 'SET_CARD_DATA'
```

```javascript
// mutations.js
import * as types from './mutations.types.js' // 引入事件类型

// ···
mutations: {
    [types.SET_CARD_DATA] (state, arr) {
      // 变更数据源的数据
      state.cardData = arr
    }
  }
```

在你组件的调用方式：

```javascript
import { mapMutations } from 'vuex' // 使用 Vuex 语法糖

// 在你的组件中使用
methods: {
  ...mapMutations({
  modefyCarData: 'SET_CARD_DATA' // 创建事件类型的映射
  }),
  yourMethods () {
    this.modefyCarData([
      {
        name: 'test'
        // ...
      }
    ])
  }
}
```

参考资料：
官网 Mutations：[https://vuex.vuejs.org/zh/guide/mutations.html](https://vuex.vuejs.org/zh/guide/mutations.html)
