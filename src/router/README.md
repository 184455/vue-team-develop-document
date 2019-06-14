# 路由配置

项目路由自然使用了 vue-router，作为官方推荐的路由工具，提供了很多强大的功能。其中配置使用最多的就是这个路由懒加载技术：

```javascript
const ContractApprove = (resolve) => {
  import('../views/approve/home').then((module) => {
    resolve(module)
  })
}
```

其他 动态路由，路由守卫，路由模式等高级功能，可以参考[官方文档](https://router.vuejs.org/zh/)
