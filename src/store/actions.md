# 第三步：异步修改 State 的数据（Actions）

说完了同步的修改数据方式，我们来说说异步的修改方式。在实际的项目开发中，需要的情况也不总是同步的，很多时候是是异步的。
比如：我们需要向接口接口请求数据，或者我们需要做数据的离线缓存。等等，这里就需要我们使用一个异步的场景，那就是：Actions。

**Actions 和 Mutation 基本用法一样，但是有些区别**：

1、Action 提交的是 mutation，而不是直接变更状态。

2、Action 可以包含任意异步操作。

这两点有点区别。还记得前面的 mutations 同步提交的时候只支持一个传入的 state 参数吗？**在Actions 里面传递的参数不同了：</strong>Action 函数接受一个与 store 实例具有相同方法和属性的 context 对象，因此你可以调用 context.commit 提交一个 mutation，或者通过 context.state 和 context.getters 来获取 state 和 getters。

```javascript
actions: {
  saveCardData ({commit, store}, paloyloadObj) {
    console.log(store) // 传入数据中心的对象，你可以拿当前数据中心的实例
    axios.post('url', paloyloadObj).then((res) => {
      if (res.status === 200) {
        commit(paloyloadObj) // 保存成功，将数据同步到数据中心
      }
    })
  }
}
```

这里一大区别就是：没有直接去修改数据，而是调用了一个 commit 函数提交修改。

参考资料：
官网 Actions：[https://vuex.vuejs.org/zh/guide/actions.html](https://vuex.vuejs.org/zh/guide/actions.html)
