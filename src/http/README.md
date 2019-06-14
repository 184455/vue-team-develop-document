# HTTP 请求的封装

**说明**：在项目中，主要使用的HTTP库是：Axios。大多数开发着对这个应该都不陌生。

对于 Axios 的处理主要体现在两个方面：拦截器和项目中使用的请求方法

## 拦截器

> 拦截器主要是针对一个请求在发起和响应前做的预处理。

```javascript
const axios = Axios.create({})

// http 拦截器
axios.interceptors.request.use(requestBefore, requestError)
axios.interceptors.response.use(responseAfter, responseError)
```

以上就是 Axios 定义拦截器的方法，只要自己实现拦截器中的方法即可：`requestBefore`, `requestError`, `responseAfter`, `responseError`

具体传入的参数可以查阅 [Axios 官方文档](https://www.kancloud.cn/yunye/axios/234845)。

## 请求方法

```javascript
/**
 * get 获取数据方法
 * @param url
 * @returns {*}
 */
export function getSomething (url, payload = {}) {
  const options = {
    params: payload,
    headers: {
      'Content-Type': 'application/json'
    }
  }
  return axios.get(url, options)
}
```

请求主要根据一个 Axios 的实例封装。通过传递不同参数实现不同的需求。具体接受的参数，自行查阅文档！
