# Class-08-NodeJS & RESTful API

## 主要知识点
- [Class-08-NodeJS & RESTful API](#class-08-nodejs--restful-api)
  - [主要知识点](#主要知识点)
  - [课堂笔记 Nodejs](#课堂笔记-nodejs)
    - [Nodejs](#nodejs)
    - [模块化](#模块化)
  - [课堂笔记 RESTful API](#课堂笔记-restful-api)
    - [Protocol 协议](#protocol-协议)
    - [HTTP](#http)
    - [URL](#url)
    - [HTTP Methods](#http-methods)
    - [curl命令](#curl命令)
    - [HTTP Header](#http-header)
    - [Response (status) code](#response-status-code)
    - [JSON](#json)
    - [SOAP](#soap)
    - [API](#api)
    - [REST (Representational state transfer)](#rest-representational-state-transfer)
      - [RESTful API 设计规范 *重要*](#restful-api-设计规范-重要)
    - [Microservices](#microservices)
  - [建议](#建议)
## 课堂笔记 Nodejs

### Nodejs

### 模块化
- `module.exports` 导出
- `require` 调用
- 模块化有利于代码简洁

## 课堂笔记 RESTful API

### Protocol 协议
- 相当于必须达成协议才能进行交流
- OSI model transport layer中包含udp tcp协议
- User Datagram Protocol
- Transmission Control Protocol
- 运输例子
    - UDP可能会丢失数据，顺序可能改变，但速度快，网络游戏，直播会使用
    - TCP可以保证数据不丢失，且顺序不变，网络开发时使用
- TCP和IP经常一起使用

### HTTP
- 0.9只能使用GET，只能发送html文件
- 1.0 可以发送任何类型的请求和任何格式的信息，但要在header中说明
  - 三次握手，四次挥手
  - 一次连接
- 1.1 持久连接 persistent connection
  - 浏览器对同一个域名最多保持6个持久连接
- 项目中不会涉及HTTP2和HTTP3
- HTTP2需要HTTPS
- HTTP3基于QUIC基于UDP，但数据可靠性比UDP高

### URL
![URL](/image/s14c0801.png)
- protocol 协议
- auth 权限 有时会有要求把用户名密码写在URL上，但不安全
- host
  - hostname
  - port有时是隐藏的
  - 协议有默认端口对应 e.g. HTTP对应80 HTTPS对应443
  - port用于通信，例如服务器可以监听某个端口
- path
  - pathname 寻找数据的source
  - search/query 给数据搜索条件
  - hash `#` 锚点，多跳到页面某一部分，多为前端使用
  
### HTTP Methods
- GET 一般发送请求时，取得数据
- POST 创建数据
- PUT 替换数据
- DELETE 删除数据
- PATCH 更新部分数据 与PUT类似 按公司规定使用

### curl命令
- linux和MacOS可以直接使用，Windows需要安装
- 用于进行request
- client server，client发送请求，server处理请求并返回数据
- status状态码
- cache-control
  - private只有浏览器可以缓存
  - public任何地方都可以缓存
  - no-cache 可以缓存，但要验证
  - no-store 不能缓存
  - 这些规则不是必须遵守的，但一般会遵守

### HTTP Header
- Content-Type: text/html 数据类型
- Allow: GET, PUT, POST 允许的数据类型
- Referer: 用户从哪里来的，例如Google
- User-Agent: 用户通过哪个浏览器访问
- Access-Control-Allow-Origin 跨域访问，CORS可以设定允许哪些跨域访问
- Authorization: `<Type> <credentials>`
  - `Basic` username and password
  - `Bearer` Oauth 2.0 protected resources 在我们之后的开发中常用

### Response (status) code
- 200 OK
- 201 Created
- 304 Not Modified 并不很常用
- 400 Bad Request 请求有错误 客户端有问题
- 401 Unauthorized 
- 404 Not Found
- 500 Internal Server Error 服务端内部错误

### JSON
- 其他语言无法理解JavaScript的Object变量，所有转化为JSON
- 一种数据传输的格式，用于跨语言数据传输
- 在JSON之前使用XML格式，现在已经渐渐被JSON取代
- 所有语言都支持JSON传输
- 可读性也很强

### SOAP
- 一个安全性很高的协议，银行，政府会使用

### API
- Application programming interface 接口
- 可被外部访问的接口被称为Web API

### REST (Representational state transfer)
- 资源以某种状态形式进行转移，本身的概念很难理解
- stateless无状态：每一个请求都是独立的，无联系的
- CRUD
  - create对应POST
  - retrieve对于GET
  - update对应PUT
  - delete对应DELETE
#### RESTful API 设计规范 *重要*
符合REST规则的API
- 用url定位资源
- 用HTTP method确定行为
- 好处：可以通过url和行为直接看出进行什么样的request
- 7个规则
  - 1. versioning 版本 例如`v1 v2`
    - `example/v1/resource`
    - `example/v2/resource`
  - 2. url里尽量使用名词，不要包含动词，尽量使用复数 `books`
    - `POST /v1/books`
  - 3. GET 方法不会对资源状态有改变
    - `GET /v1/books` 获取书，而不更新书
  - 4. 资源在url里尽量使用嵌套结构
    - `/v1/books/{bookID}/author`
    - 如果取单独的数据，直接用ID而不用`?`query
  - 5. 注意返回的数据大小 （注意分页）
    - 1w数据只返回前10个数据
  - 6. 用正确的status code表示请求的状态
    - 不要所有请求都返回200
  - 7. 如果是一个错误返回，那么最好返回可读的文本信息
    - 不需要使用错误码

### Microservices
- 一种服务端的设计架构
- monolith server
- 嵌套结构，/library/{libId}/book

## 建议
- 可以多多借鉴大公司的API规范是怎样的
- https://newsapi.org/
- 开发时先用注释表示流程，有助于面试思路