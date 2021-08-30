# Class-10-RESTful API & Express.js

## 主要知识点

## 课堂笔记 RESTful API
- [Class-10-RESTful API & Express.js](#class-10-restful-api--expressjs)
  - [主要知识点](#主要知识点)
  - [课堂笔记 RESTful API](#课堂笔记-restful-api)
    - [Postman](#postman)
    - [News API练习](#news-api练习)
    - [NPM](#npm)
    - [nodemon](#nodemon)
    - [express](#express)
    - [作业](#作业)
### Postman
- 用于调试API
- 常用功能
  - Request方面
    - HTTP和url: 
    - params: 包括query等
    - Authorization: 包括token，常用Bearer token
    - Headers: 请求的header
    - body: raw 要选中json格式，才能在请求中包含json
  - Response方面
    - Body: response body
    - Header： response header

### News API练习
- 接触一个新API时可以先试一下他给的例子
- 读API文档
- 有时request无效是因为CORS

### NPM
- Node package manager
- 代码仓库
- package
- https://www.npmjs.com/package/express
- 选package的注意点：
  - 看star，issue和pull request来确定是否使用
  - 用示例代码试一下是否符合自己要求
- npm操作:
  - `npm init -y` 跳过所有问题创建package.json文件 `-y`指所有回答都为yes
  - `npm install`两个命令效果一样，用于安装package，也可以用`npm i`
    - 根据`package.json`中的dependencies和`package-lock.json`中的版本号安装package
    - `package-lock.json`主要用处就是确定pachages的版本
  -`npm i -D` 指dev dependency，只有开发环境使用的package
  -`npm i -g` 全局安装，常用的，在命令行中可以直接使用，现在不太使用
    - 全局安装有可能导致scripts找不到package导致报错
  -`npx` 可以直接获取最新的package，一次执行，不长期保留
  - npm r
  - pachage.json的scripts包含一些alias快捷方式，可以通过`npm run {scripts}`使用命令
  - `npm run {scripts}`可以简写为`npm {script}`
  
### nodemon
- `npm i -D nodemon` 自动监听代码改变，自动重启服务器
- `--inspect` 在需要测试的代码地方增加断点，会在断点位置停止，并可以查看断点是各个变量的内容

### express
- `const express = require("express")` 导入
- `const app = express()` 应用
  - method为HTTP method例如`GET POST`等
- `app.listen()` 监听一个端口
- 常用端口: 3000 4200 8080 9000
- `app.method(path, route handler => callback)` 事件绑定
  - `app.post('/:id',(req, res) => callback)` 取数据方法
    - `req.body` -> POST, PUT, PATCH 创建修改数据时使用，不可见
    - `req.params` -> GET, POST, PUT, PATCH, DELETE 取冒号后的变量 需要定义才能取到值 常用于id
    - `req.query` -> GET 筛选
  - `res.json res.send`
    - `res.status(201).json({data})` 状态码加数据response 如果不加`status()`默认返回200

### 作业
- https://jr-todos.herokuapp.com/api-docs/
- 按照document创建RESTful API
- 可以使用`const data = []`的方式创建一个临时数据库，服务器重启时会刷新