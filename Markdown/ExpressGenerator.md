# Express Generator学习笔记
## 1. Express Generator介绍
> 参考：[Express Generator 生成Express应用的目录结构](https://www.jianshu.com/p/c5baef64563a)  

该教程详细介绍了express应用框架的结构及其各个文件的作用及用法。

## 2. Express & React 开发环境搭建
> 参考：[搭建express+reactjs前后端分离开发环境](https://blog.csdn.net/xgbm_k/article/details/78205362)  

该教程介绍了express+reactjs前后端分离开发环境的搭建。

## 3. React Router 介绍
> 参考：[官方英文文档](https://reacttraining.com/react-router/web/api/BrowserRouter)   

该文档详细介绍了Recat Router的使用方法。

## 4. Student Info 应用

### 4.1. npm环境安装
1). 安装npm，用于运行node.js后端和react前端  
2). 安装express-generator，用于生成express后端应用框架  
```npm
npm install -g express-generator
```
3). 安装create-react-app，用于生成react前端应用框架  
```npm
npm install -g create-react-app
```
4). 安装nodemon，主要用于开发时自动重启express后端应用
```npm
npm install -g nodemon
```

### 4.2. 后端工程

1). 创建一个名为student-info-core的express工程，其中模板使用ejs
```npm
express student-info-core --view=ejs
cd student-info-core
npm install

//linux 
SET DEBUG=student-info-core:* & npm start

//windows
SET DEBUG=student-info-core:*
npm start
```

2). 在routes目录下添加一个api.js文件用于返回json测试数据
```js
var express = require('express');
var router = express.Router();

router.get('/users', function(req, res, next) {
    var nums = [{id: 1, name: 'a'}, {id: 2, name: 'b'}, {id: 3, name:'e'}];
    res.json(nums);
});

module.exports = router;
```
3). 修改app.js文件
```js
var api = require('./routes/api');
...
app.use('/api', api);
```
4). 修改bin目录下的www文件，将端口号改为3005
```js
var port = normalizePort(process.env.PORT || '3005');
```
5). 修改package.json
```json
    "start": "nodemon ./bin/www",
```
6). 在终端中运行npm start，访问http://localhost:3005/api/users，若网页中出现了json数据，则该后端工程创建成功，否则请检查上述各步骤是否正常执行

### 4.3.前端工程
1). 创建一个名为student-info-mnt的react工程
```npm
create-react-app student-info-mnt

npm install react-router-dom
```
2). 修改package.json，加入新的参数proxy，该参数的作用是做一个代理，将向该工程（默认端口3000）的请求转为请求该代理端口（此处是3005）；这样可以前端与后端跨域访问问题，将来发布时也不会有问题
```json
    "proxy": "http://localhost:3005/",
```
3). 修改app.js文件，加入从服务器请求数据,当点击页面时,在下面显示用户名；请求数据使用fetch方法
```js
class App extends Component {
  // add begin
  constructor(){
    super()
    this.state = {users: []};
  }
  fetchUsers(){
    return fetch('api/users', {accpet: "application/json"}).then(res => {return res.json().then(json => {this.setState({users: json})})})
  }
  // add end

  render() {
    return (
      <div className="App">
        <header className="App-header">
          <img src={logo} className="App-logo" alt="logo" />
          <h1 className="App-title">Welcome to React</h1>
        </header>
        {// modify begin}
        <p className="App-intro" onClick={this.fetchUsers.bind(this)}>
          To get started, edit <code>src/App.js</code> and save to reload.
        </p>
        {this.state.users.map((user, index) => {
          return (<h1 key={index}>{user.name}</h1>)
        })}
        {// modify end}
      </div>
    );
  }
}
```
4). 在终端中运行npm start，将自动启动浏览器并显示前端页面；点击"To get started,..."，下面将显示从服务端获取到的用户名，如果不能显示，则请检查上述步骤是否正确执行