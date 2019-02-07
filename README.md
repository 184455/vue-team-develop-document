# Vue - 项目开发规范

一份关于 Vue 项目多人开发协作遵守的规范。

> 记住：这只是一份文档，不是一个 npm 的安装包。很多时候你不需要下载安装它，你需要的只是最终的团队规范，所以只要下载 ./dist 目录下的文件即可。

## 目录

* [介绍](./README.md)

* [GitBook](./gitbook/README.md)

* [代码组织规范](./coding-standard/README.md)

    * [项目结构](./coding-standard/catalog.md)

    * [Vue 文件编写代码规范](./coding-standard/vue-file.md)

    * [项目注释规范](./coding-standard/comment.md)

    * [Git 提交规范](./coding-standard/code-commit.md)

    * [数据中心](./coding-standard/store/README.md)
        
        * [State](./coding-standard/store/state.md)

        * [Mutations](./coding-standard/store/mutations.md)
        
        * [Mutation.types](./coding-standard/store/mutations.types.md)
        
        * [Actions](./coding-standard/store/actions.md)
        
        * [Getters](./coding-standard/store/getters.md)
        
        * [Index](./coding-standard/store/_index.md)

    * [路由规范](./coding-standard/router.md)

* [生产代码讲解](./project/README.md)

    * [项目前期准备](./project/project-prepare/README.md)

    * [首页](./project/home/view-home.md)

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
> 打开浏览器访问：http://localhost:4000/<br/>
我们默认你已经安装了：node.js，gitbook 等工具。然后你就能看到项目，并且本地调试是热更新的。

<br/><br/>
最后，如果你对 GitBook 的使用还不是很熟悉，请先看：[GitBook 的使用](./gitbook/README.md)
