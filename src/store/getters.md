# 第四步：读取 State 的数据（Getters）

前面说了，如何定义数据中心，如何修改数据中心中的数据，同步，异步。现在我们来说说：何如读取数据中心的数据。

这个很简单，根据官网的使用方式，主要有：定义为一个计算属性；通过Vuex 提供的语法糖。这里我们只说用的最多的：mapGetters.

**首先**我们需要在在getters 中定义一个获取数据的函数：

```javascript
getters: {
  getCardData (state) {
    return state.cardData
  }
}
```

**然后**在组件中：

```javascript
import { mapGetters } from 'vuex'

methods: {
  ...mapGetters[
    'getCardData'
  ]
}
```

**调用一下方法就可以获得数据，很简单**。

但是我们通过把，getter 分离出来，加上ES6 的语法，这里的函数定义会更简单：

```javascript
// getters.js
export const getCardData = state => state.cardData
```

调用方式还是一样，但是更加简洁明了。

我们这里讲了这么多，希望那你不要混淆。所以下一节，你将会看到一个完整的例子，到时候你会体会到，这样定义的初衷。

参考资料：
官网 Getters：[https://vuex.vuejs.org/zh/guide/getters.html](https://vuex.vuejs.org/zh/guide/getters.html)
