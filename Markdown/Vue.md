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