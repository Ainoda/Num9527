# Vue学习笔记
## 1. vue安装
使用如下npm命令安装vue:  
```
npm install -g @vue/cli
vue --version  
```

> 参考[Vue CLI 安装](https://cli.vuejs.org/zh/guide/installation.html)


## 2. 创建项目
使用如下命令创建项目：
```
vue create hello-world
```
> 参考[创建一个项目](https://cli.vuejs.org/zh/guide/creating-a-project.html#vue-create)

### 2.1. 运行项目
使用如下命令运行当前项目：
```
npm run serve
```


## 3. Vue Router
### 3.1. 安装Vue Router
使用如下命令安装Vue Router:
```
npm install vue-router
```
### 3.2. 使用Vue Router
如果在一个模块化工程中使用它，必须要通过 Vue.use() 明确地安装路由功能：
```js
import Vue from 'vue'
import VueRouter from 'vue-router'

Vue.use(VueRouter)
```
> 参考[Vue Router安装](https://router.vuejs.org/zh/installation.html)

## 4. Element
### 4.1. 安装Element
使用如下命令安装Element:
```
npm i element-ui -S
```
> 参考[Element 安装](http://element-cn.eleme.io/#/zh-CN/component/installation)

### 4.2. 使用Element
在 main.js 中写入以下内容：
```js
import Vue from 'vue';
import ElementUI from 'element-ui';
import 'element-ui/lib/theme-chalk/index.css';
import App from './App.vue';

Vue.use(ElementUI);

new Vue({
  el: '#app',
  render: h => h(App)
});
```
> 参考[Elment引入](http://element-cn.eleme.io/#/zh-CN/component/quickstart)

## 5. 快速原型开发
> 参考[快速原型开发](https://cli.vuejs.org/zh/guide/prototyping.html)

### 5.1. 安装扩展
使用vue serve和vue build命令可以对单个*.vue文件进行快速原型开发，不过需要额外安装一个全局的扩展，使用如下命令进行安装：
```
npm install -g @vue/cli-service-global
```