# 前言

本篇文档用于记录在使用vue开发app过程中，关于怎样使用vue-router的记录！如果在查看本文档的过程中，有什么看不明白的地方，可到[vue-router官网]()查看相关文档，因为本文档相关的概念都可以从这里看到！

**注：如果要查看相关demo，可以查看[1]()目录下通过构建方式搭建的例子，也可以直接复制[index.html]()中的代码到本地在浏览器中打开查看效果！**

## 安装

主要用两种方式使用vue-router:

> 方法一：直接在html页面中引入vue-router,如下：

```html
<script src="https://unpkg.com/vue/dist/vue.js"></script>
<script src="https://unpkg.com/vue-router/dist/vue-router.js"></script>
```

> 方法二：通过构建方式，比如当我们使用vue-cli工具构建一个vue项目的时候，可以通过如下命令安装vue-router:

```bash
npm install --save vue-router
```

然后通过在主文件中通过如下方式引入vue-router:

```js
import Vue from 'vue';
import VueRouter from 'vue-router';
```

切记使用这种方式的时候，你需要加入下面一行代码：

```js
Vue.use(VueRouter);
```
