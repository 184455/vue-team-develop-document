# 与服务端通信: api

> 背景：当前，微服务的兴起，前端与后台的交互，不再和以前一样，只限制与某台服务器。
> 所以这里把请求数据与后台交互的逻辑单独抽离出来，向上层提供稳定的接口，无论底层如何变更，上层始终感觉不到。

## 设计约定

**原则：为了向上层调用的稳定，所有的请求方法都返回一个** `Promise`.

> 不能在请求方法中添加逻辑，只做纯粹的请求。业务逻辑应该放在调用请求方法前，或者在拦截器中。

```javascript
/**
 * 查询数据
 * @param {Object} payload 查询参数
 */
export function getData (payload) {
  return getSomething(`${SERVES_NAME}/path/query`, payload)
}
```

> 这里服务名称可以通过配置文件来配置，`getSomething` 自己封装的方法会返回一个 Promise
