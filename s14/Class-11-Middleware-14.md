# Class-11-Middleware

## 主要知识点
- [Class-11-Middleware](#class-11-middleware)
  - [主要知识点](#主要知识点)
  - [课堂笔记 Middleware](#课堂笔记-middleware)
    - [Middleware](#middleware)
    - [文件分层](#文件分层)
    - [课上练习 RESTful API](#课上练习-restful-api)
## 课堂笔记 Middleware

### Middleware
- 一个function，放到route handler中，在route handler代码前执行
- request -> middleware检测 -> next -> 下一个middleware或route handler
- 可以使用`next()`也可以`res.send()`，但基本不会同时使用，因为`res.send()`可能和之后的代码冲突
- 调用`next(something)`时会进入错误middleware，例如`next(new ValidationError())`，无法再返回到正常队列
- tips: javascript的错误处理中`error`参数大多放在第一位
- `app.use(v1)` 全局注册
- `app.use('/v1', n2)` 以`/v1`开头的路径中所有endpoint都使用
- `app.get('/v1/tasks, n3')`需要完全匹配路径，且只在GET method中使用


### 文件分层
- 为了RMR，数据验证，逻辑，数据操作等代码可以进行分层
- 
![structure](/image/s14c1101.png)

### 课上练习 RESTful API
- https://lazebear.github.io/jr-todos/
