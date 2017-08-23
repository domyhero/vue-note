# 前言

本篇文档用于记录在使用vue开发app过程中，关于怎样使用vue-router的记录！如果在查看本文档的过程中，有什么看不明白的地方，可到[vue-router官网]()查看相关文档，因为本文档相关的概念都可以从这里看到！

**注：如果要查看相关demo，可以查看[1](https://github.com/woai30231/vue-note/tree/master/vue-router/1/vue-router-demo)目录下通过构建方式搭建的例子，也可以直接复制[index.html](https://github.com/woai30231/vue-note/blob/master/vue-router/index.html)中的代码到本地在浏览器中打开查看效果！为保证快速说明问题，下文案例代码只介绍index.html中的部分！**

## 安装

主要用两种方式使用vue-router:

> 方法一：直接在html页面中引入vue-router,如下：

```html
<script src="https://cdn.bootcss.com/vue/2.4.2/vue.js"></script>
<script src="https://cdn.bootcss.com/vue-router/2.7.0/vue-router.js"></script>
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

### 小试牛刀

我们先来搭建一个简单的功能，实现首页列表导航，html如下：

```html

<!DOCTYPE html>
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <meta http-equiv="X-UA-Compatible" content="ie=edge">
    <title>Vue-router demo</title>

    <script src="https://cdn.bootcss.com/vue/2.4.2/vue.js"></script>
    <script src="https://cdn.bootcss.com/vue-router/2.7.0/vue-router.js"></script>
</head>
<body>
    <div id="app">
    
        <ul>
            <li><router-link to="list1">list1</router-link></li>
            <li><router-link to="list2">list2</router-link></li>
        </ul>
        <router-view></router-view>
    </div>
<script type="text/javascript">
//这里配置相关用到的组件
var List1 = {template:'<div>this is list1 page!</div>'};
var List2 = {template:'<div>this is list2 page!</div>'};
//设置路由映射
var router = new VueRouter({
    mode:'hash',//这里主要设置路由的模式，主要分为hash模式和h5模式,因为我们在本地查看demo,所以请不要设置history模式，否则会报错
    //下面的routes的值是个数组，主要配置每个路由所对应的的组件名字，其实你明白了其实一个路由就是对应的一个组件，你这样就好理解了
    routes:[
        {
            path:'/list1',
            name:'list1',
            component:List1
        },
        {
            path:'/list2',
            name:'list2',
            component:List2
        },
        //这一项配置，默认路由，也就是页面刚进来的时候，会默认进入的下一个页面
        {
            path:'',
            redirect:'/list2'
        },
        //下面一项用于配置，你跳转到一个没有对应的路由映射的时候页面会映射List1组件
        {
            path:'*',
            //name:'list1',
            component:List1
        }
    ]
});

//启动app
new Vue({
    el:'#app',
    router:router
});
</script>
</body>
</html>
```
