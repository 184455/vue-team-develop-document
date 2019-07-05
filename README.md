# Vue - 项目开发规范

一份关于 Vue 项目多人开发协作遵守的规范。

> 记住：这只是一份文档，不是一个 npm 的安装包。很多时候你不需要下载安装它，你需要的只是最终的团队规范，所以只要下载 ./dist 目录下的文件即可。

## 目录

* [介绍](./README.md)

* [项目规范: 必读！](./src/coding-standard/README.md)

  * [Vue 文件编写代码约定](./src/coding-standard/vue-file.md)

  * [项目注释约定](./src/coding-standard/comment.md)

  * [Git 提交约定](./src/coding-standard/code-commit.md)

* [项目结构](./src/coding-standard/catalog.md)

* [与服务端通信: api](./src/api/README.md)

* [公共资源: common](./src/common/README.md)

* [项目组件: components](./src/components/README.md)

  * [scroll](./src/components/scroll/README.md)

* [HTTP 请求方法: http](./src/http/README.md)

* [国际化: i18n](./src/i18n/README.md)

* [路由配置: router](./src/router/README.md)

* [数据中心: store](./src/store/README.md)

  * [State](./src/store/state.md)

  * [Mutations](./src/store/mutations.md)

  * [Mutation.types](./src/store/mutations.types.md)

  * [Actions](./src/store/actions.md)

  * [Getters](./src/store/getters.md)

  * [Index](./src/store/_index.md)

* [页面: views](./src/views/README.md)

* [GitBook 的使用](./src/gitbook/README.md)

## 贡献

如果你对此项目感兴趣，并且希望它变得更好，更完善，可以尝试克隆到本地，进行开发调试，非常欢迎👏

### 下载

```bash
git clone https://github.com/184455/vue-team-develop-document.git
```

### 安装依赖

```bash
cd vue-team-develop-document

gitbook install
```

### 运行

```bash
gitbook serve
```


> 打开浏览器访问：<http://localhost:4000/>

我们默认你已经安装了：node.js，gitbook 等工具。然后你就能看到项目，并且本地调试是热更新的。

最后，如果你对 GitBook 的使用还不是很熟悉，请先看：[GitBook 的使用](./gitbook/README.md)
