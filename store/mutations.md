# 同步修改数据源的数据（Mutations）

经过上面一节，你已经迈出了第一步：如何定一个数据源。仓库是有了，但是我们如何在里面存储东西呢？

这就是我们这节的主要内容：同步修改 State 中的数据。

> 修改 State 里面的数据有同步方法和异步方法，不能混用，在 Vuex 中有严格的规定。稍后将会说异步方法。

根据 Vuex 的规定，修改 State 的数据只能是通过一个 Mutations 或是 Actions。所以我们通过函数的方式是最合适的。
就比如：
```javascript
new Vuex.Store({
  state: {
    cardData: []
  },
  mutations: {
    addSomething (state, arr) {
      // 变更状态
      state.cardData = arr
    }
  }
})
```

这样，写在 mutations 对象里面，Vuex 会把 State 数据源作为第一个参数传递到函数里面，后面的参数作为载荷提交，其实就是你给函数传递参数。

我们这样写以后，在自己的组件中，通过 Vuex 提供的语法糖：
```javascript
import { mapMutations } from 'vuex'

// your component
methods: {
  ...mapMutations([
    'addSomething'
  ]),
  yourMethods () {
    this.addSomething([
      {
        name: 'test'
        // ...
      }
    ])
  }
}
``` 
使用即可，感觉特别方便。

优化点：<br/>
这里根据官网的推荐，当多人协作时，可能 Mutations 里面的方法会很多，并且很不好维护，所以，推荐另外使用一个文件
来专门定义 Mutations 的行为。这个就是目录中：mutation.types.js 的由来。里面防止的全是一些方法名字的常量。
引入该文件后，修改可能是这样的：

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
import * as types from './mutations.types.js'

// ···
mutations: {
    [types.SET_CARD_DATA] (state, arr) {
      // 变更状态
      state.cardData = arr
    }
  }
```

调用方式：
```javascript
import { mapMutations } from 'vuex'

// your component
methods: {
  ...mapMutations({
  addSomething: 'SET_CARD_DATA' // 创建一个函数的映射
  }),
  yourMethods () {
    this.addSomething([
      {
        name: 'test'
        // ...
      }
    ])
  }
}
``` 

注意：

1、mutations 中的数据是响应式的，所有对于数组对象的赋值需要注意；

2、再次提醒，Mutations 里面不能有异步的操作，比如请求一个接口获取数据，读取本地文件的异步行为！
