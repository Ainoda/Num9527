# Element-UI学习笔记

## 1. 引入Element
> 参考[快速上手](http://element-cn.eleme.io/#/zh-CN/component/quickstart)

### 1.1. 完整引入
在main.js中写入如下内容：
```javascript
import Vue from 'vue';
import ElementUI from 'element-ui';
import 'element-ui/lib/theme-chalk/index.css';
import App from './App.vue';

Vue.use(ElementUI);

new Vue({
    el: "#app",
    render: h => h(App)
});
```