## 目录
- [01-Introduction & Web Tech](#01-introduction--web-tech)
- [02-HTML & CSS](#02-html--css)
- [03-CSS & Sass](#03-css--sass)
- [04-JavaScript](#04-javascript)
- [05-Git Introduction](#05-git-introduction)
- [06-Node.js: Basics of Node.js](#06-nodejs-basics-of-nodejs)
- [07-Node.js: Introduction to npm and Koa](#07-nodejs-introduction-to-npm-and-koa)
- [08-Agile](#08-Agile)
- [09-Node.js: Documents](#09-nodejs-documents)
- [10-Interview and CV Linkedin CV](#10-interview-and-cv-linkedin-cv)
- [11-REACT: React with Modern JavaScript](#11-react-react-with-modern-javascript)
- [12-REACT: Make it stateful](#12-react-make-it-stateful)
- [15-Node.js: Rest API](#15-nodejs-rest-api)
- [16-Node.js: Restful in Koa & MongoDB Database](#16-nodejs-restful-in-koa--mongodb-database)
- [17-Interview 1](#17-interview-1)
- [18-Node.js: Mongoose](#18-nodejs-mongoose)

## 01-Introduction & Web Tech

安装ssl证书的网站：certbot

了解客户端渲染和服务端渲染csr ssr ssg

h1 只能有一个

了解js加在head和尾部的区别

local storage 同一域名下 / section storage 同一tab下，不需要储存用户信息

cookie 服务器存在浏览器，以及cache区别

shift + f5 清空cache刷新

genymotion debug安卓设备

[回到目录](#目录)





## 02-HTML & CSS

margin重叠，哪个大用哪个

BEM命名

box-sizing: border-box (child加padding后能保持在parent里面)

[回到目录](#目录)





## 03-CSS & Sass

bootswatch 修改bootstrap默认变量

sass: cat style compressed 等命令行指令

多看sass文档：https://sass-lang.com/documentation

了解mixin

```scss
 @for $i from 1 through 10 {
	div:nth-child(#{$i}) {
        height: 10px;
        color: darken(red, $i*5);
	}
}
```

```css
.container {
    display: flex;
    flex-wrap: wrap;
    justify-content: center;
    align-items: center;
    background: red;
}

.card {
    flex-grow: 1; 
    flex-shrink: 1;
    width: 300px;
    height: 200px;
}
```

![specifishity](https://specifishity.com/specifishity.png)

[回到目录](#目录)





## 04-JavaScript

和js相关的技术：electron  nodejs  typescript

定义变量用var，ES6中用const和let

ES5严格模式声明：‘use strict’

```js
‘use strict’
// 变量提升
console.log(a);
var a = 10;
//---------等价于
var a;
console.log(a);
a = 10;
```



注意命名规则：驼峰，常量大写，数字和符号不能开头（除$和_），不能用关键字

了解数据类型，浮点数精度问题，NaN和infinity等等

了解运算逻辑符号（+, =, *, /, % , \==, \===，! ，!\==）和数据类型的转换

绝⼤多数场合应该使⽤ \===

处理数字精度问题，数字用字符串表示，处理字符串



数组奇葩的地方：数组会被扩充，如`arrya[100] = 100`

数组里面可以存函数

了解数组的添加和删除的操作：push(), pop(), unshift(), shift()



熟练使用三元运算符`xx ? xx : xx`

了解falsey type, 会被判断称成false:  false, NaN, undefined,  null, “” , 0

熟练使用for循环和while循环，注意var的作用域

break结束当前层的循环，continue跳过本次循环

九九乘法表代码，要在node环境下运行，安装包`npm install nzh --save`

```js
var Nzh = require("nzh");
var nzhcn = require("nzh/cn")

for (var i = 1; i < 10; i++) {
    var out = ""
    for (var j = i; j < 10; j++) {
        var res = nzhcn.encodeS(i*j)
        out+= nzhcn.encodeS(i)+nzhcn.encodeS(j)+(res.length>1?'':'得')+res+"\t"
    }
    console.log("\t")
    console.log(out)
}
```



匿名函数

理解函数作用域，注意全部变量

如果函数传进多个参数（不限个数），所有传进去的参数都会存在`arguments`里

`arguments`像array，但不是array，用`Array.from(aguments)`复制可转换成array，然后可使用`Array`的方法

```js
function test(a,b) {
    return Array.from(arguments).reduce( (a,b) => a+b );
}
console.log(test(1,2,3,10));
// 控制台结果为: 16 .reduce()相加
```

数字，字符串，布尔值等简单类型传进函数的时候会复制一个新的，函数内修改不影响函数外部

Array, obj等复杂类型传进函数的时候只会传一个reference，不会复制，函数内修改影响函数外部（因为指针指向函数外部的array）



Object.assign()

构造函数

```js
function Car(brand, year) {
    this.brand = brand;
    this.year = year;
    this.price = Math.random()*10000
}
car = new Car('toyota', 1988)
```

.call() 改变this的指向

![this](https://i.imgur.com/IOxMgg3.png)

嵌套方式写`document.querySelectorAll('div div')`替换`document.querySelectorAll('div').querySelectorAll('div') `

js异步加载

getAttribute() setAttribute()

用state管理棋盘状态

一个html导入多个js文件，全局变量会互相污染，前几年用iife解决

关于同步sync和异步async，建议看[一文看懂JS的异步](https://zhuanlan.zhihu.com/p/66593213)

[回到目录](#目录)





## 05-Git Introduction

别让地铁站都比你努力！

Distributed Version Control System 好处：可以在本地保留分支的历史，适合远程办公，在无网络状况下拉分支

各种git代码看老师的ppt或者上网查阅

注意添加git ignore 文件，不要提交vscode和idle自带的文件

git pull是从git上拉取最新代码，可能会出现冲突合并覆盖的问题，然后自己创建一个分支branch，交给老板review之后如果没问题，会把自己的branch合并到master branch。

创建branch原则是按feature。一个人不是一直在一个branch上工作。

使用ssh key来连接

首先搞懂clone，git branch，commit push， rebase ，pull request merge，这几个就够了

rebase可以用到自己的branch上，不要用到public branch上

pull request之前记得解决冲突

commit要尽量要小



``` 
git init 创建一个新仓库
git clone <远程仓库的 Url>
git status 显示当前工作目录下的文件的commit状态
git add <文件名>或者<相对路径/文件名> 将指定文件添加到stage(准备被commit的状态)
git reset <文件名>或者<相对路径/文件名> 取消标记stage
git commit -m "commit信息"
git log 显示提交历史
git push 向远程仓库推送(把文件从本地传到云端)
git pull 从远程仓库拉取(从云端下载文件到本地，如果别人更新了，记得pull)
git commit --amend -m "<新commit的信息>"

git branch 查看所有分支
git branch <分支名字> 查看所有分支
git checkout <分支名字> 切换到分支
git branch -m <旧名字> <新的名字> 重命名分支
git branch -d <分支名字> 删除分支
git rebase master 将分支变基到master,主要先checkout到要变基的分支
git merge master 将分支合并到master,主要先checkout到要合并的分支
git merge --f-only master 使用快进(Fast-Forward)将分支合并到master

git stash save "save message" 将未提交的修改暂存(stash)，只有git stash也可以的，但查找时不方便识别
git stash list 查看stash了哪些存储
git stash apply 应用某个存储
git stash pop 将上一个暂存的修改回复并从暂存列表中删除

git checkout <提交的hash> 签出指定的提交, 版本hash用git log查看
git revert <旧提交的hash> 撤销旧提交

git reflog 查看所有分支的所有操作记录
```

例子一：开发分支（dev）上的代码达到上线的标准后，要合并到 master 分支

```
git checkout dev // 切换到dev分支
git pull // 拉取dev分支下最新的内容，同事可能修改了，有冲突的话要解决
git checkout master // 切换回master分支
git merge dev // 在master分支上合并dev分支，有冲突的话要解决，用rebase也行
git push // 推送新的master
(注意：如果有多个主机push要用 git push -u origin master，-u orign指定origin为默认主机)
```

例子二：当master代码改动了，需要更新开发分支（dev）上的代码

```
git checkout master // 切换到master分支
git pull // 拉取master分支下最新的内容，同事可能修改了，有冲突的话要解决
git checkout dev  // 切换回dev分支
git merge master // 在dev分支上合并master分支，有冲突的话要解决，用rebase也行
git push // 推送新的dev
(注意：如果有多个主机push要用 git push -u origin dev，-u orign指定origin为默认主机)
```

对命令行感兴趣的同学多复习虎姐的视频

对命令行比较吃力和没理解git流程的同学建议看这两个视频（总共20分钟）

[git教程入门](https://www.bilibili.com/video/BV1KD4y1S7FL)   [git教程进阶]( https://www.bilibili.com/video/BV1hA411v7qX?spm_id_from=333.788.b_636f6d6d656e74.4)

[回到目录](#目录)





## 06-Node.js: Basics of Node.js

**前端和服务端的区别**

nodejs是一门服务端开发的语言和工具

前端：用户能交互，看到，直接感知到的部分

服务端（后端）：用来储存和管理数据，并且解决客户端无法完成的事情，比如分发。

nodejs和koa虽然是js代码，但是跑在服务端上的，不能运行在浏览器上，注意和前端的js代码区分

服务端代码量没那么多，对计算机基础知识较高

找到一个适合自己的方向



**BOM & DOM & Js Object**

nodejs是一门用js语言的运行环境，由谷歌浏览器Chrome的V8引擎构建。

浏览器中有三个大类的对象：BOM（Browser Object Model），DOM（Document Object Model），JavaScript Object。

BOM对象在JavaScript引擎中是不存在的，只存在在浏览器里，不是可视化的元素，比如`navigator`, `document.location`, `windows.location`	。

DOM是能够被选中和审查的。

JavaScript Object有JavaScript引擎提供。

BOM和DOM在nodejs中都不存在，BOM和DOM都由浏览器的渲染引擎提供，nodejs在js中引擎中通用的，但不在BOM和DOM中通用。



**异步和事件驱动**

nodejs是异步开发和事件驱动，以厨房为例，比如要烧汤，第一个步骤要烧水，第二个步骤要处理食材，洗菜，切菜。第一个做法，简单的做法，先洗菜，切菜，然后烧水，最后烧汤。第二个做法，先烧水（10分钟），在烧水的过程中洗菜切菜（15分钟），水烧好之后，等五分钟切好菜，再烧汤。

一次只做一个事情，而且一个事情做不完就叫做同步（sync），有时候也成为阻塞（blocking）。不是由分配任务的人去执行，烧水是由炉子烧的，小明自己没有被占用，而是在等待炉子烧水，被称为阻塞。优点是简单，不容易出错。

异步（async）是相对的概念，任务分发完了，自己没有事情做，小红去做别的事情了，可以把两件事情并行的做，可以节约资源。优点能省时间，缺点存在风险，操作复杂，容易乱套。

事件驱动是解决容易乱套的一种方法，和闹钟类似。给第一锅汤旁边放一个闹钟，烧十分钟，第二锅汤旁边放一个闹钟，烧十分钟。分配任务的人不用记这些东西，只要被处罚(triggered)，由定时机制触发。定时机制比如闹钟或者让另一个人去做，做好了通知，称为事件驱动。

Nodejs是第一个把事件驱动作为编程开发的平台。



**Nodejs非阻塞IO**

stdin，stdout是标准的输入输出。

操作系统在默认处理IO的时候是同步，也称为是阻塞的，如果磁盘的读写没有完成，操作系统会阻塞，不会去干别的事情。

nodejs读取文件的时候会给操作系统发送读取文件的任务，然后nodejs本身被释放出来了。读取文件的工作由操作系统完成，操作系统读取完文件后给nodejs发送信号，告诉nodejs文件已经读取完了，nodejs接收结果。

nodejs的异步和事件驱动解决了IO的问题，实现了异步IO，包括std的IO，网络的IO，磁盘的IO。

总结：nodejs是用了谷歌chrome的V8引擎，配合了异步事件驱动引擎去解决非阻塞IO问题的开发平台。



**浏览器中的非阻塞IO**

浏览器里面解决非阻塞IO的方法是http。

浏览器中有两个BOM对象`XMLHttpRequest`和`fetch`，是来做网络IO的，网络请求属于IO的一部分，一种是阻塞，一种是异步。

浏览器里面绝大部分是异步的，写代码也最好写成异步的。如果写成同步的，DOM会被阻塞，比如用户点个按钮发一个请求，用户在整个网页就阻塞死了，不能再做别的事情了。

while 1 和阻塞的概念不一样，while 1是很忙的意思，CPU高负荷运作，没空做之后的事情；阻塞是等着别人给一个结果（比如发送请求后等待服务器回应），其实不忙，CPU不转。



**Nodejs的架构**

开发者使用nodejs平台提供的API开发服务端的应用程序或者命令行脚手架

nodejs没有权限管理，deno有权限管理

Nodejs API由两方面提供，一方面是Nodejs bindings，另一方面是nodejs的C++的扩展

如果想用一些nodejs平台没有提供的API，可以通过C或者C++编写扩展，比如买了个新鼠标，新鼠标的驱动程序是C语言写的，nodejs无法识别，可以用C语言结合的C语言写的驱动程序暴露给nodejs，使用户可以用js去操控鼠标。

nodejs和V8是C语言和C++语言开发的。V8的职责是nodejs的runtime，没有别的作用，V8没有BOM的DOM，只有Js。

libuv实现异步，事件驱动，和非阻塞IO，V8负责Js。两者结合共同实现JavaScript语言的异步驱动。

c-ares 是用来做DNS解析的，http parser是用来解析HTTP请求的 ，OpenSSL是用来做加密解密的， zlib是压缩解压缩的库，这些库都是用C语言编写的。

nodejs主要负责任务分发，整合了其他语言和其他引擎的功能，尽量让C和C++去做擅长的事情。如果某些功能能用C或者C++实现 ，少用js的模块去实现，尽量使用nodejs提供的原生的模块做事情。反面例子是，比如一个实现文件压缩功能的库，如果大部分语言使用js写的而不是C写的，就降低了效率。



**Terminal和Shell**

Terminal是提供可交互式命令行的窗口，让用户可以和计算机内核交互的操作界面。（和图形操作界面相对）

shell是terminal的执行环境，比如bash，oh-my-zsh， sh

shell section，每次运行shell有自己的section吧，比如可以临时切换成比如node的不同版本，好处是以前大家在同一台"大"的电脑上开发，大家可以使用不同的shell，都相对独立，版本不会互相干扰

node的命令行环境叫[repl](https://nodejs.org/api/repl.html)



**Nvm**

[macOs和Linux安装](https://github.com/nvm-sh/nvm)   [Windows安装](https://github.com/coreybutler/nvm-windows)

（用windows还没安装Linux的同学建议在系统自带的Microsoft store中安装[Ubuntu](https://www.microsoft.com/en-au/p/ubuntu-2004-lts/9n6svws3rx71?activetab=pivot:overviewtab)）

nvm是nodejs的版本管理工具，可以让你在同一台机器上安装，切换和同时使用不同版本的nodejs的工具。

常用指令

```
nvm 查看所有可以使用的nvm指令
nvm version 查看当前的版本
nvm ls-remote 列出所有可以安装的node版本号
nvm install 14.15.3 安装指定版本号的node
nvm current 查看当前node版本
nvm ls 列出所有已经安装的node版本
nvm use 14.15.0 切换node的版本，临时切换
nvm alias default 14.15.3 永久切换node版本
```



**Web Server**

TCP/HTTP  DNS

Network Headers 底下全要掌握

TCP协议通常和IP协议一起工作

IP地址在互联网确定计算机的唯一地址，比如142.256.67.196:442，142.256.67.196是IP地址，442是端口号，端口号只能唯一，不能被多个程序所占用，所有通讯都要加端口，http默认端口是80，https默认端口是443

TCP协议会用IP建立一个长连接，用建立的通道通信，http是一个比较高端的协议

DNS全程是Domain Name Space Server，购买某个域名后比如example.com，解析到IP地址上，输入网址，回车，浏览器向最近的DNS server 请求，解析到IP地址

提前预习http, 老师推荐书籍http权威百科和[http维基百科](https://en.wikipedia.org/wiki/Hypertext_Transfer_Protocol)

完全没有HTTP基础的同学可以看看老板第一节课讲的http和两个入门视频[http入门视频1](https://www.youtube.com/watch?v=pHFWGN-upGM)  [http入门视频2](https://www.youtube.com/watch?v=iYM2zFP3Zn0)

（注:入门视频2中的express是一个快速搭建web server的库，和之后要学的Koa接近）

[回到目录](#目录)





## 07-Node.js: Introduction to npm and Koa

Hypertext Transfer Protocol，http是建立在tcp/it和dns之上的协议。[http维基百科](https://en.wikipedia.org/wiki/Hypertext_Transfer_Protocol)

达成协议的前提是至少有两个个体，两个个体之间进行通信，一方按照规定的格式编码，另一方按照约定的格式解码

http是基于请求和响应的通信标准，一方是客户端发出一个请求，另一方是服务端回应一个响应。一去一回是一个完整的http请求。可数段发出请求，服务端接受进行解析，发回一个响应报文

客户端请求（建议动手敲一遍）：

```http
GET / HTTP/1.1    // 注意方法，路径，协议号中间用空格
Host: www.example.com    // 键值对的格式
```

服务端响应（建议动手敲一遍）：

```http
HTTP/1.1 200 OK
Date: Mon, 23 May 2005 22:38:34 GMT
Content-Type: text/html; charset=UTF-8
Content-Length: 155
Last-Modified: Wed, 08 Jan 2003 23:11:55 GMT
Server: Apache/1.3.3.7 (Unix) (Red-Hat/Linux)
ETag: "3f80f-1b6-3e1cb03b"
Accept-Ranges: bytes
Connection: close

<html>
  <head>
    <title>An Example Page</title>
  </head>
  <body>
    <p>Hello World, this is a very simple HTML document.</p>
  </body>
</html>
```

注意中间有一个空行用来区分header和body部分，空行上面是header部分，空行下面是body部分

[telnet伪造HTTP请求](（建议动手敲一遍）)

curl承担client的角色，类似一个命令行的浏览器，可以在服务器上的linux系统上运行，curl可自定义各种请求参数，擅长模拟web请求。

能编码http请求并发出请求的工具都可以叫做client



**Header中的method**

GET：从服务器上获取数据

POST：创建请求

PUT：修改请求

DELETE：删除数据

对应crud（create, read, update and delete），增删改查



**Header中的path**

Nodejs官方文档 [讲解URL](https://nodejs.org/dist/latest-v14.x/docs/api/url.html#url_url_strings_and_url_objects)

```
http://user:pass@sub.example.com:8080/p/a/t/h?query=string#hash

┌────────────────────────────────────────────────────────────────────────────────────────────────┐
│                                              href                                              │
├──────────┬──┬─────────────────────┬────────────────────────┬───────────────────────────┬───────┤
│ protocol │  │        auth         │          host          │           path            │ hash  │
│          │  │                     ├─────────────────┬──────┼──────────┬────────────────┤       │
│          │  │                     │    hostname     │ port │ pathname │     search     │       │
│          │  │                     │                 │      │          ├─┬──────────────┤       │
│          │  │                     │                 │      │          │ │    query     │       │
"  https:   //    user   :   pass   @ sub.example.com : 8080   /p/a/t/h  ?  query=string   #hash "
│          │  │          │          │    hostname     │ port │          │                │       │
│          │  │          │          ├─────────────────┴──────┤          │                │       │
│ protocol │  │ username │ password │          host          │          │                │       │
├──────────┴──┼──────────┴──────────┼────────────────────────┤          │                │       │
│   origin    │                     │         origin         │ pathname │     search     │ hash  │
├─────────────┴─────────────────────┴────────────────────────┴──────────┴────────────────┴───────┤
│                                              href                                              │
└────────────────────────────────────────────────────────────────────────────────────────────────┘
(All spaces in the "" line should be ignored. They are purely for formatting.)
```

console中运行`condocument.location.href`可以得到`href`

http默认端口是80，https默认端口是443

#hash部分只在浏览器中使用，在request URL中没有，不会发送到服务器



**Header中的http version**

HTTP协议在1996年发布1.0版本，http是基于请求和响应的，TCP会建立一个长连接。1.0版本会先建立一个tcp连接，发送请求和响应，完成后切断tcp连接，缺点有速度慢，浪费资源。在1996年发布了1.1版本，在一定时间内会keep alive，不立马断开tcp连接。



**Header中的optional header**

option al**户自定义的header，不在http规范中，x是extend的缩写

`Content-Length: 155`代表客户端读到固定长度后停止，Content-Length的计算式服务端的职责

`Content-Type: text/html; charset=UTF-8` 告诉客户端是什么格式，浏览器接收到是html后渲染出html页面，text plain， application json， image/png， image/gif，webp。[MDN的ContentType文档](https://developer.mozilla.org/en-US/docs/Web/HTTP/Headers/Content-Type)

cookie，浏览器会存储一小部分数据（不超过4kb），下次发送请求会一起带上，在开发者工具Application中可以查看，cookie是按照域名来储存的。http是基于请求和相应的，服务端不知道用户是谁。服务器可以通过cookie里的hash值识别出用户是谁。cookie是由服务端生成，只存储在同一台点的同一个浏览器里。



**Status codes**  

- Informational `1XX`
- Successful `2XX`  200宽泛的成功
- Redirection `3XX`  301永久重定向，302临时重定向
- Client Error `4XX`  400宽泛的客户端问题，401未授权没登录了，402需要购买，403登录了没权限，404未查询到请求的资源
- Server Error `5XX`  500宽泛的服务端问题，501未实现，502网关错误，503服务器挂了

[List of HTTP status codes维基百科](https://en.wikipedia.org/wiki/List_of_HTTP_status_codes)



**Npm（node packgage manager）**

```
npm init //初始化一个npm的项目，生成package.json配置文件
npm install // 安装package.json中记录的依赖的包，简写是 npm i koa
npm install koa //安装koa模块 
npm info koa // 查询koa包的信息
npm install mocha -D // 安装mocha到devDependencies
npm prune --production // 删除devDependencies
```

dependencies记录该项目的依赖，devDependencies记录开发环境下需要的依赖，不会发布在production中

包会尽量打平放到`node_modules`，如果出现版本冲突，后下载的版本会放在子目录的`node_modules`下

包版本遵循Semantic version，包括三个数字`MAJOR.MINOR.PATCH`不兼容的改动要发一个新的MAJOR版本。MINOR代表是兼容的版本，比如性能优化或者增加新功能。PATCH修改了bug。

- `^2.5.0 ` 表示MAJOR不变，MINOR和PATCH取最大数字，也就是最新的

- `~2.5.3 ` 表示MAJOR和MINOR不变，PATCH取最新的

- `2.5.0 ` 表示指定安装这个版本

- `*` 表示选择latest的dist-tag下的版本，`*`等价于`latest`，`next`表示选择next的dist-tag下的版本

[回到目录](#目录)





## 08-Agile

Software Development Life cycle (SDLC)

SDLC Model- Waterfall & V Model 都是非常成熟的模型，不太适合现阶段商业节奏较快和迭代较快的需求

mvp 和 poc

mvp注重结果，先交付客户一个满足核心功能能用的东西，再慢慢添加新的功能或者完善，而不是等到做完一个大而全的东西才交付。

SDLC Model-Agile

**Agile value**

（1） 较之于过程和工具，更注重人及其相互作用的价值。

（2） 较之于无所不及的各类文档，更注重可运行的软件的价值。

（3） 较之于合同谈判，更注重与客户合作的价值。

（4） 较之于按计划行事，更注重响应需求变化的价值。



**12 Agile Priciple Behind The Agile Manifesto (详见ppt)**

（1） 在快速不断地交付用户可运行软件的过程中，将使用户满意放在第一位。

（2） 以积极的态度对待需求的变化（不管该变化出现在开发早期还是后期）。Agile过程紧密围绕变化展开并利用变化来实现客户的竞争优势。

（3） 以几周到几个月为周期，尽快、不断地交付可运行的软件供用户使用。

（4） 在项目过程中，业务人员和开发人员最好能一起工作。

（5） 以积极向上的员工为中心建立项目组，给予他们所需的环境和支持，对他们的工作予以充分的信任。

（6） 在项目组中，最有用、最有效的信息沟通手段是面对面的交谈。

（7） 项目进度度量的首要依据是可运行的软件。

（8） Agile过程高度重视可持续开发。项目发起者、开发者和用户应能始终保持步调一致。

（9） 应时刻关注技术上的精益求精和设计的合理，这样能提高软件的快速应变力。

（10） 简单化（尽可能减少不必要工作的艺术）是基本原则。

（11） 最好的框架结构、需求和设计产生于自组织的项目组。

（12） 项目组要定期对其运作方面进行反思，提出改进意见，并相应进行细调。

此外，Agile方法实施中一般采用[面向对象技术](https://baike.baidu.com/item/面向对象技术)（接口定义良好的其它开发技术也可），另外还强调在开发中要有足够的工具（如配置管理工具、建模工具等）支持。



敏捷开发是一种理念/精神/价值观，而并不提供具体的方法。

Agile原则是：①减少浪费 ②快速产出 ③不断地带 ④交流沟通 ⑤响应变化



Scrum是一个包括了一系列的实践和预定义角色的过程骨架（是一种流程、计划、模式，用于有效率地开发软件）。

在每一次冲刺（一个15到30 天周期 ，长度由开发团队决定），开发团队创建可用的（可以随时推出）软件的一个增量。每一个冲刺所要实现的特性来自产品订单（product backlog，我觉得翻译成“产品目标”更恰当）， 产品订单（产品目标）是指按照优先级排列的需要完成的工作的概要的需求（目标）。哪些订单项（目标项目）会被加入一次冲刺，由冲刺计划会议决定。 在会议中，产品负责人告诉开发团队他需要完成产品订单中的哪些订单项。开发团队决定在下一次冲刺中他们能够承诺完成多少订单项。 在冲刺的过程中，没有人能够变更冲刺订单（sprint backlog），这意味着在一个冲刺中需求是被冻结的。

为了规划，组织，管理和优化这个流程，Scrum需要至少依赖于三个规定的角色：

1、产品负责人-Product Owner（负责初始规划，确定优先级以及与公司其他部门进行沟通）

2、敏捷教练-Scrum Master （负责监督每个sprint期间的过程）

3、团队成员-（负责执行每个sprint，例如写代码。）



kanban管理亦称“看板方式”、“视板管理”。在工业企业的工序管理中，以卡片为凭证，定时定点交货的管理制度。看板提供了视觉化的直观管理感受，它能迅速暴露那些影响团队效能的问题,因此,在使用看板管理的团队所面临的挑战是 如何专注于解决问题以维持稳定的工作流。

[补充阅读Kanban vs. scrum](https://www.atlassian.com/agile/kanban/kanban-vs-scrum)



User Story 描述一个任务

Acceptance Criteria 重点在提出符合规范的结果

Task 把任务分成小的过程

[回到目录](#目录)





## 09-Node.js: Documents

[Node.js文档](https://nodejs.org/dist/latest-v14.x/docs/api/)

内置nodejs的东西主要分为两大类，模块和全局对象。

模块需要使用`require()`引入，比如`const fs = require('fs')`

全局对象可以直接使用，在nodejs repl中敲`globe`可查看

用node运行js文件，在终端中输入`node fileName.js`，不是在repl下运行。

尽量使用const 和 let，不用var，如果一个变量不会被重新赋值，用const，如果会被修改，用let。



**Assertion概念**

Assertion 软件测试，类似产品出厂前的测试。软件测试分为黑盒测试和白盒测试。黑盒测试指，对于测试者，不了解内部代码是如何实现的，只看表面能使用就可以，黑盒的软件测试工程师技术含量低，逐渐被取代。白盒测试指，对于测试者，不关心外部结果，只关心内部组件的正确性，只要内部功能组件是正确的，组合起来也应该是正确，白盒测试对测试者技术要求高。

Assertion（断言）属于白盒测试中的一种方法，被测试的人对预期结果有一定的答案。比如测试1+1，结果断言是2，如果结果不是2表示不通过测试。

`assert.ok(value[, message])`第一个值是肯定要传的，中括号内的值为optional，可填可不填。`assert.ok(1)`如果传入的值为真，不会有任何事发生，`assert.ok(0)`程序会退出

`assert.strictEqual()`类似`===`



**Process**

`Child processes`子进程，process从属于操作系统，线程从属于进程。第一次被启动的进程叫做`Parent process`，启动parent进程之后再启动的是子进程。kill用来给进程发信号

process.env是系统的环境变量，[维基百科](https://en.wikipedia.org/wiki/Environment_variable)，process.env是一个json文本，里面的键值对都是字符串，可以用于配置和加密。在操作系统里面，每一个进程都是相对隔离的，不会互相干扰。

process.argv 可用于编写命令行工具

一个进程和现成都只能占用一个CPU，V8是单线程单进程，chrome是多进程架构，每个tap页算一个进程，不会浪费CPU多核资源

cluster集群，根据CPU的核心数自动创建多进程，先判断CPU核心数量，创建主进程，再创建子进程。



**Event**

设计模式[维基百科](https://en.wikipedia.org/wiki/Software_design_pattern)，设计模式是在软件开发中被总结出来的最佳实践，通常认为是高效的方式，推荐这么去写代码。

观察者模式是设计模式中的一种，观察者模式有一个主体和一个观察者，当观察者观察到一些现象后会做出一些动作。在技术上被称为事件驱动模型。

Event模块提供EventEmitter这个库，基本用法：

```js
const myEmitter = new MyEmitter();
let m = 0;
myEmitter.on('event', () => {
  console.log(++m);
});
myEmitter.emit('event');
// Prints: 1
myEmitter.emit('event');
// Prints: 2
```

需要很好地掌握，虽然EventEmitter也被大多数封装了，但是这个API被保留下来了，掌握了可以更好地理解很多代码。



**Global Objects**

V8只认识一长串js代码，没有文件和模块的概念

Nodejs把代码包装在一个function再传给V8，类似下面的代码

```js
function (__dirname, __filename, require, export, module) {
    const assert = require('assert')
}
```



**Path**

Path解决不同操作系统下的路径问题，处理相对路径，拼接路径等等

比如拼接路径用`path.join` ，不同系统下的`path.sep`可能不一样



**Querystring**

```js
// a=1&b=2&c=3 是一条querystring，?a=1&b=2&c=3 是 search
> querystring.parse("a=1&b=2&c=3")  // 将querystring转换为object
{ a: '1', b: '2', c: '3'}
> querystring.stringify({ a: '1', b: '2', c: '3'}) // 将object转换为querystring
'a=1&b=2&c=3'
```



**Timer**

setTimeout() 延时执行

setInterval() 间隔执行 clearInterval()停止

setImmediate() 在下一个eventloop中执行，尽快去执行

setTimeout(func，0) 不等于 setImmediate()



**Nodejs需要掌握的模块**

需要重点掌握的（仔细看一遍文档）: **Events** (design pattern的一种), **File system** (熟练掌握readfile和writefile)，**Globals**，**CommonJS**, **Path**, **Process**, **Timer**, **URL**

轻度了解的: Child processes, Cluster, Crypto, Errors, Utilities, WASI, Worker threads, Zlib

进阶掌握的: Buffer, HTTP (协议要了解)

[回到目录](#目录)





## 10-Interview and CV Linkedin CV

推荐使用匠人LMS内的简历系统，在LMS内左侧导航栏选择“我的简历”

在澳洲找工作更不看重实习经验，主要看实际的工作经验。在国内找工作看重实习经验，最好有多份实习。

澳洲实习不算正式employee，不会给交税，国内实习一般不允许毕业生。

Graduate Program对于IT专业一般不要PR。



Entry level一般不要求工作经验，有工作经验的能加分。

Junior level一般需要1-2年工作经验。

在澳洲第一份工作一般不挑，有offer可以直接去。

推荐匠人能力强的同学申请Mid level，因为申请的人较少。



国内找工作注意校招时间，注重第一学历，群面容易遇到名校大佬，想清楚自己的优势，实习经验能加分。

同时注重硬实力和软实力的培养，强调沟通能力（包括理解能力），在BA提完需求后，可以复述询问确认一遍。平时多积累英文的专业名词。

澳洲产品型公司注重人才，人才贡献的价值可能大于小时数，经常出现工资高，活少的情况，对代码水平高。咨询服务类公司需要时间积累，做到高级别后工资高。

国内互联网大厂Tier1校招看重学历背景，社招不看重学历，而看重过去的工作经验和技术能力。国有企业看重政治面貌，籍贯，硕士学历，建议去平安，不建议去四大银行。国内咨询类公司能混到partner薪水高。回国签合同要看清楚竞业条款。



ribit有很多初级岗位的工作，seek上猎头和中大型多，Linkedin找到工作概率高，简历质量高。indeed中小型公司多。

澳洲找工作不太看重算法，国内注重算法，要去刷牛客网等。

谈薪水的时候不要让公司开，建议第一份工作要7w-7w5的工资。

如果公司在犹豫，主动降薪可以提高offer率。

glassdoor可以查看薪水和公司评价



Linkedin 注重SEO和Readaility

先加很多open networker，目标加到500好友以上。

about me里面把所有知道的和不知道到的skill都写上，提高SEO用。

转行前的工作经验可以放，尽量相关度高。政府机关类企业的工作经验不建议放。、



简历内文本可被搜索，第一面简历很重要。

注意岗位技术栈匹配，技术要有深度，项目要上线，专业，能商业。

简历别用明度的颜色，黑白打印会看不清。

project经验和工作经验都放在experience里，不做区分。

家庭住址不精确到门牌号，写到区就好。

邮箱别用QQ邮箱，要用专业名字命名的邮箱，尽量不要出现数字，不要出现生日年月。

Summary部分要突出亮点，不要写自己是学生，从哪里毕业。

Skills写清楚版本号和更具体的服务，体现专业性。

STAR method

认真对照老板的PPT和录屏修改简历，给老师review的时候不要出现说过的问题。

[回到目录](#目录)



## 11-REACT: React with Modern JavaScript

[Jackie老师的演示代码lesson1](https://github.com/jackietian/jr-lesson1/tree/master/src)

**Js**

强类型语言 强类型语言是一种强制类型定义的语言，一旦某一个变量被定义类型,如果不经过强制转换，则它永远就是该数据类型了，强类型语言包括Java、.net 、Python、C++等语言。

弱类型语言是一种弱类型定义的语言，某一个变量被定义类型，该变量可以根据环境变化自动进行转换，不需要经过显性强制转换。弱类型语言包括vb 、PHP、javascript等语言。

js可以跑在前端上，也可以跑在服务端上。

js里的 function是一个object，object可以赋值给变量。

了解scope，包括function scope，block scope [拓展阅读scope](https://dmitripavlutin.com/javascript-scope/)

**React**

React build UI components（组件），组件可以小到是一个icon或者按钮。前端像搭积木一样，由小的组件搭建而成。

React组件分有状态组件和无状态组件。高级的代码会尽量拆分出小的组建，方便后期复用。

一个component里面不要超过100行代码

创建和运行React

```
npx create-react-app my-app
cd my-app
npm start
```

package-lock.json用来固定版本号，确保团队使用一个版本。

index.js是一个入口文件，index.js导入APP.js，渲染在html里的root div下

JSX是用js写html的语言，JSX里的class要改成className，不要使用inline style。

```jsx
// 显示时间例子
function cb() {
   ReactDOM.render(
     <div>
       <h1>It is {new Date().toLocaleTimeString()}.</h1>
     </div>,
     document.getElementById('root')
   );
 }
 setInterval(cb, 1000)
```

**React DOM**

virtual dom是运行在内存中的，render一个很是的dom是很费时间的。virtual dom会比较哪个节点发生改变，只对改变的节点改变，不用重新渲染整个页面。[What is the Virtual DOM(课后作业)](https://reactjs.org/docs/faq-internals.html)，[DOM and Virtual DOM(课后作业)](https://reactkungfu.com/2015/10/the-difference-between-virtual-dom-and-dom/)

dom使用树形结构，dom需要频繁地增删改查，使用树形结构进行增删改查是最快的，树形结构也能清晰地表达元素间的关系，比如父子，爷孙，兄弟等，遍历时间更快。

**React props**

props可以传多种参数包括：
`<MyComponent foo={JavaScript expression} />`， JavaScript expressions include but not limited to:
● Number -  `<Component number={12} />`
● String - ` <Component str="Hello world" />`
● Boolean -  `<Component liked={false} /> <Component liked />`
● Array -  `<Component array={[1, 2, 3, 4]} />`
● Object -  `<Component style={{ fontWeight: 'bold' }} />`
● Operators -  `<Component sum={1 + 2 + 3} />`
● Function -  `<Component onClick={() => alert('clicked')} />`

[React文档Components and Props](https://reactjs.org/docs/components-and-props.html#gatsby-focus-wrapper)

**Pure function & Impure function**

pure function不改变input的值，而且产生side effects。尽量使用pure function，方便函数的复用或者项目的重构等等。

```jsx
//Pure - doesn’t change the input (i.e. a and b)
function sum(a, b) {
	return a + b;
}
//Impure - input (account) is mutated
function withdraw(account, amount) {
	account.total -= amount;
}
```

**ES6**

const是常量，一旦被声明，就不可以被改变，如果是object可以改变里面的值，let是变量，可以被改变。

var和let的life scope不一样，var是function scope ，const和let是block scope

[Jackie老师es6例子](https://github.com/jackietian/jr-lesson1/blob/master/src/es6.js)

```jsx
//================= const ==========
 const pi = 3.14
 // WRONG，const不能二次赋值
 pi = 4

 //============ template string ====
 const name = 1
 const age = 12
 const str = name + '' + age
 const str2 = `${name}${age}` // backtick符号在esc键下面，数字1键左边
 console.log(str2)

 // ============ let ============
 for (var i = 0; i < 3; i++) { // var为 function scope
     console.log(i);
 }
 console.log(i) // 3

 for (let j = 0; j < 3; j++) { // let为 block scope
     console.log(j);
 }
 console.log(j); // undefined

 // ============ arrow function ============
// 注意区分function和箭头函数的this区别
 function sayHello(name) {
     console.log('******', this)
     console.log(`hello, ${name}!`);
 }

 const sayHello1 = (name) => {  
     console.log('=====', this)
     console.log(`hello, ${name}!`);
 }

 sayHello('foo')
 sayHello1('foo')

 // ============ destructuring =======
 const student = { school: 'UNSW', gender: 'F', name: 'foo' };
 // const school = student.school;
 // const gender = student.gender;

 const { school, gender } = student;
 console.log(school, gender)

 // ============ spread =======
 const computerScienceStudent = {
     major: 'Computer Science',
     language: 'English',  // 注意这里的'English'被下面的'Chinese'覆盖了
     university: 'UNSW'
 };
 const mary = {
     ...computerScienceStudent,
     language: 'Chinese',  // 注意这里的'Chinese'覆盖了上面的'English'
     age: 25
 };
 console.log(mary) // mary = { major: 'Computer Science', language: 'Chinese', university = 'UNSW', age: 25 }

// ============ class =======
class Student {
  constructor(name, gender) {
    this.name = name;
    this.gender = gender;
    this.university = 'UNSW';
  }
  greeting() {
    console.log(`Hello, I'm ${this.name} from ${this.university}`);
  }
}
const jane = new Student('Jane', 'F');
jane.greeting(); // Hello, I’m Jane from UNSW
```

强烈建议多看即便Jackie老师推荐的[ES6文章(课后作业)](https://medium.com/the-andela-way/a-beginners-guide-to-react-with-es6-a2ed0b5c977e)

看完后反思是否掌握了一下知识点？不熟悉的一定要回去查阅

- Const and let 

- The spread operator

- Template literals

- Default function parameters

- Destructuring

- Object literal Shorthand

- Arrow functions

- Classes

[回到目录](#目录)



## 12-REACT: Make it stateful

SPA概念

[安装node-sass](https://create-react-app.dev/docs/adding-a-sass-stylesheet/)，注意目前要安装4开头的版本

```
npm install node-sass@4.14.1 --save
```

try catch 可以捕获错误以及handle error

[var hoisting](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Statements/var) 声明会被提升，初始化不会被提升。



closure A function return a B function，B function has access to A function



**Class component**

React的props不能修改



## 13 React

闭包表述

A function A return a function B which access a variable in function A

```
function A() {
   let C
  return function B() {
    C++
   }
}
```

this.action执行环境

[arrow function](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Functions/Arrow_functions)

man speak 补充

传参

onClick默认给的参数是e，比如e.target.name



## 14 React

call ,apply ,bind



Conditional Rendering三种写法

```jsx
const Status = ({ isOnline }) => {
  //写 法一：if写法
  if (isOnline) return <OnLine />;
  return <OffLine />;

  // 写法二：三目运算符写法
  return <>{isOnline ? <OnLine /> : <OffLine />}</>;

  // 写法三：短路运算符写法
  return (
    <>
      {isOnline && <OnLine />}
      {!isOnline && <OffLine />}
    </>
  );
};
```



props.Children是一个集合体，里面内容都会显示出来

APi
restful APi, http method: POST, GET, DELETE, PUT

GraphQL

Promise.all()

Promise.race()



## 15-Node.js: Rest API

两台计算机用端口通信，任何服务器都有端口号，一定要指定端口号。一般指定1000以上的端口号

http默认80，https默认443

context上下文，在特定的语境下，囊括了一切

koa1.0 版本时 async和await还没诞生

https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Generator

generator在当时解决了callback hell 的问题



```js
// 所有模块引入要用const，载入进来的如果是class，首字母要大写，require里面的koa首字母不能大写
const Koa = require("koa"); // 标准写法
```

localhost和127.0.0.1代表本机的回环地址



`Ctrl + C `可以给进程发送一个退出的信号

`curl -i 127.0.0.1:3000`可以在命令行里发送请求或者-v

```http
HTTP/1.1 200 OK
Content-Type: text/plain; charset=utf-8 // 浏览器根据content-type来确定使用哪个渲染引擎
Content-Length: 12  // koa会自动计算生成content-length
Date: Sun, 07 Feb 2021 08:56:10 GMT  // 也是koa自动生成等等
Connection: keep-alive
Keep-Alive: timeout=5 // 让客户端的等待时间
```

```js
app.use((ctx) => {
  ctx.body = "JR <H1>Hello World!</H1>";
  ctx.type = 'html';  // 使用koa内置的API快捷设置
  ctx.set("Content-Type","text/html"); // 或者直接设置报文，注意不能直接写"html"
  ctx.length = 23;  // 改小字符串会被截断，改大会让客户端等待超时，必须设置对
})
```



```
JSON.stringfy({ age: 23, name: "小明" }) // 22
Buffer.byteLength(JSON.stringfy({ age: 23, name: "小明" })) // 26，一个中文字符占3个字节
```

每一个ctx都是新的，执行完一次http后，ctx会被js的垃圾回收销毁。

```
ctx.request.method
ctx.request.path
ctx.request.headers
ctx.get("host") // get是读取request的报文，set是设置response的报文
```



post请求里有body，需要安装`koa-bodyparser`

```js
const bodyParser = require('koa-bodyparser');
app.use(bodyParser());
```

```js
app.use(bodyParser({ enableTypes: ["text"] }));

app.use((ctx) => {
  // echo
  ctx.body = ctx.request.body;
})
```



koa中间件的洋葱模型，request进来是从外往里，response出去是从里往外。最早use是在越外面的一层，越迟use是在越外面的一层

```js
app.use(async (ctx, next) => {
  ctx.startTime = Date.now();
  await next();  // next() 等于下一个中间件
  console.log(Date.now() - ctx.startTime)
})

app.use((ctx) => {
  console.log(`request: ${ctx.startTime} `)
})
```

面向对象https://en.wikipedia.org/wiki/Object-oriented_programming

能够抽象出来的概念叫模型，在REST中叫state，Representational是能表真的状态转移，transfer是对模型进行改变的意思，比如创建一个模型，修改一个模型，删除一个模型和查询一个模型。有些抽象不出来的模型就无法写成REST。能不能用REST来写，取决于能不能抽象出模型。

![](https://i.imgur.com/E9VmTUa.jpg)

## 16-Node.js: Restful in Koa & MongoDB Database

API 概念



全栈历史：

第一阶段只有html，把html放在web server上，用http协议通信，网页没有任何交互能力。XML是可扩展的标记语言，HTML里面的内容是固定的。XML在早期被用于数据传输，类似现在的Json。

第二阶段新加了XMLHttpRequest，用于发送http请求，此时web已经具备动态扩展的能力，比如google maps。SOAP（Simple Object Access Protocol）在过去的项目中经常用，现已淘汰。

第三阶段为了更好的体验，XML体积比较大，并且写起来不方便，逐渐使用Json来传输数据。之前需要一个功能就写一个API，现在抽象出来了RESTful。



Monolith VS Microservices

Monolith：在早期把所有的代码包括前端后端都在一个代码仓库里。 Microservices：把不同的代码分开到不同的仓库管理，利用API通信，把大的项目拆成不同的服务，让专门的团队去管理和维护，不同团队之间用API交互。好处是团队不需要关系过多其他的事情，可以专精把一件事做好，责任划分也更清晰



REST Squencial chart 时序图

看的顺序，从左到右，从上到下。GET成功会返回200，失败会返回404等

![时序图](https://i.imgur.com/SoOKvip.jpg)

API 权限检查 & 授权

Authentication权限检查，需要登录，注册账号，没登录会redirect到登录界面。

Authorization 授权，基于不同角色分配不同的权限，比如学生账号不能对课程进行增删改查

有两个web server

登录的token会放在cookie中（补充），微服务可以被不同的产品复用。WebApp是指具体的产品，具体的功能代码被拆到其他的服务仓库里。

![时序图](https://i.imgur.com/SkNie0U.jpg)

JWT（JSON Web Token）第三方授权

![JWT](https://i.imgur.com/vKB12Xs.jpg)



```js
"use strict";

const Koa = require("koa");
const bodyParser = require("koa-bodyparser");
const Router = require("koa-router");
const uuid = require("uuid");

const User = {
  hello: {
    age: 23,
    gender: "male",
  },
}; // Fake database

const app = new Koa();
const router = new Router();
app.use(bodyParser());

// GET
// `user/123`和`user/abc`会被匹配到，`user/123/abc`不会被匹配
// path里要用合法的url字符，'/'用于分隔，userId里也不能出现'?','#'等url特殊字符
router.get("/user/:id", async (ctx) => {
  const { id } = ctx.params;
  if (User[id]) {
    ctx.body = User[id];
  } else {
    ctx.body = {
      message: `User: ${id} not found.`,
    };
    // 设置了ctx.body会把status code改成200，所以需要手动修改成404
    ctx.status = 404;
  }
});

// POST
router.post("/user", (ctx) => {
  const { body } = ctx.request;
  const id = uuid.v4();
  User[id] = body;
  ctx.body = {
    id,
    message: `User ${id} created`,
  };
  ctx.status = 201;
});

// PUT
router.put("/user/:id", async (ctx) => {
  const { body } = ctx.request;
  const { id } = ctx.params;
  if (User[id]) {
    Object.assign(User[id], body);
    ctx.body = {
      message: `User ${id} updated.`,
    };
  } else {
    ctx.body = {
      message: `User: ${id} not found.`,
    };
    ctx.status = 404;
  }
});

// DELETE
router.delete("/user/:id", async (ctx) => {
  const { id } = ctx.params;
  if (User[id]) {
    delete User[id];
    ctx.body = {
      message: `User ${id} deleted.`,
    };
  } else {
    ctx.body = {
      message: `User: ${id} not found.`,
    };
    ctx.status = 404;
  }
});

app.use(router.routes());

app.listen(5000, () => {
  console.log("Server is on 5000");
});

```



Database server 访问的时候要启动，关掉就访问不了

SQLite 没有database server，数据存在本地磁盘上

Database是数据的容器，是对数据抽象的划分，像一个大池子，是最大的概念

Collection 在一个特定的产品下，对数据有不用的划分，类似sql数据库里的table，比如一个购物网站，有user data， sales data， product data等等。命名是尽量用单词的复数

Document相当于数据库的多条记录

Fields 是指定字段



## 17-Interview 1

Phone Interview 一般处于早期阶段，可以准备资料在接电话的时候查看。



Current situation：问身份状况，是否毕业，有无工作经验，能否全职，确认地点，有过什么经历，为什么要投我们公司，知道我们的产品是什么吗，对未来有什么计划，想做什么方向等等。

Behavioural: 是不是对工作充满热情，是否有创造，优化上的想法，是否有很强的自学能力，是否喜欢追求新技术，是否有团队合作的经历，有没和不同专业的人合作过，确保你进公司后能和同时相处融洽。

Salary: 之前呆过什么公司，对之前的工资觉得怎么样，对工资要求是多少。



投简历可能是海投，尽量记住投过的公司的名字，接到电话如果没有听清，要确认清楚公司名字，有时候是Recruitor，HR，Hiring Manager 打电话过来，预知会问什么问题。

自我介绍要熟练，大概3-5分钟，准备好CV，投了不同岗位的话要注意区分，intro别说废话，说的东西要和工作岗位高度相关。

注意打电话时候的语速和停顿，倾听面试官，投的少可以提前先做research，准备好自己的"cheat sheet"。

example要说的很详细，开发周期是多久，使用了agile开发，使用了什么language, framework, library，部署到哪里，解决了哪些问题，帮别人解决了哪些问题，学到了什么

为什么要来我们公司？个人的兴趣爱是什么样，对什么有热情，对行业的认识是怎么样，对你们从产品很感兴趣，我有听说过，看朋友用过，想用自己的knowledge让产品变得更好，你人用了什么技术，这些技术对我的职业发展很有帮助，我个人的发展目标和这个岗位有很高的匹配度。

你的长处是什么？一般是hard skill，不要说自己是expert。

你有什么缺点？要说可以解决的hard skill的问题，比如我之前只用react，但是看到有些公司用angular，我只是看过没用过，如果有机会，我会在未来的三个月之内认真学习。我的知识和经验都是从学校里学到的，但是缺乏大型企业级的开发项目经验，我进入工作后会认真去学习，去阅读代码库，了解核心的算法，多和同时沟通，学习怎么处理大量用户的问题等等，要提出合理的解决方法。



## 18-Node.js: Mongoose

 MongoDB储存的不是json，二是类似json的数据。MongoDB储存的是BSON，二进制的Json，重点考虑数据存储的高性能。

`_id`是BSON有，而json没有的数据类型。

MongoDB是schemaless，好处非常灵活，坏处是缺乏约束，容易造成混乱。

```js
db // 显示当前数据库名称
show dbs // 显示所有数据库
show collections
use xxx // 切换到xxx数据库

db.xx.yy() // 分为三段式，xx是collection，yy()是function
db.user.insertOne({name: "Jack", age: 23, gender: "male"}) // 插入单个参数
db.users.insertMany([{message: "hello"},{error: "this is a error"}]) // 插入多个参数

db.users.find() // 查询多条记录
db.users.findOne() // 查询一条记录，默认返回第一条
db.users.find({age:3}) // 按条件查询，从上往下遍历，直到查询到结果，

db.users.updateOne({_id: new ObjectId("60321a0133bc923840fe2468")},{$set: {age: 30}}) // update是查询和创建的结合体
db.users.updateMany() // 更新多个数据
db.users.replaceOne() // 替换一个数据

db.users.drop() // 删除collection下所有数据
db.users.deleteOne() // 很多公司不提供删除功能
db.users.deleteMany()
db.users.findOne({$and: [{_id: new ObjectId("60321a0133bc923840fe2468")}, {deleted: false}]}) // soft delete
```

db.users.find({age:3}) // 按条件查询，从上往下遍历，直到查询到结果，复杂度为O(n)，n代表数据的量，遍历的性能很低，优化数据库性能用index查询。

`_id`是自动创建的index，是由数据库内部维护的独立的数据结构，不会使用线性地一条条查询，用id来查询可以大幅提高查询速度

`db.users.findOne({_id: new ObjectId("60321a0133bc923840fe2468")})`

[db.collection.createIndex()](https://docs.mongodb.com/manual/reference/method/db.collection.createIndex/) 给字段创建索引，不能加太多索引，如果给每个字段都增加了索引，每次插入数据都要更新所有索引，数据库管理成本增大，实际性能反而降低。能不用索引尽量不要建立索引，一般情况下不用。



```js
// 设置到30岁
db.users.updateOne({_id: new ObjectId("60321a0133bc923840fe2468")},{$set: {age: 30}})
// 增加1岁
db.users.updateOne({_id: new ObjectId("60321a0133bc923840fe2468")},{$inc: {age: 1}})
// 减少5岁
db.users.updateOne({_id: new ObjectId("60321a0133bc923840fe2468")},{$inc: {age: -5}})
// 删除age，json需要有键值对，value可以任意
db.users.updateOne({_id: new ObjectId("60321a0133bc923840fe2468")},{$unset: {age: -5}})

// {$exists: true} 查询存在age的数据，{$exists: false} 查询不存在age的数据, true和false可以换成1和0
db.users.find({age: {$exists: true}})
// 给所有age加1
db.users.updateMany({age: {$exists: true}}, {$inc: {age: 1}})
```

需要按条件查询和高级搜索可以用[lucene](https://lucene.apache.org/core/)等查询引擎，关注查询速度，MongoDB重点优化数据的储存性能，插入性能等等，有简单的查询功能。



MongoDB中的operator有Query selector: `$eq,$gt...`，Projection operator，update operator，详见[MongoDB Operators](https://docs.mongodb.com/manual/reference/operator/query/)



Relations

一对多的关系使用最多，比如一个用户有好几个收货地址

1 to 1可以用Embedded或者Reference，1 to many和many to many 只能用Reference

Embedded的查询速度非常快，Reference需要做两次查询，Embedded的插入性能更好，只要插入一次，Reference要插入两次。（补充）数据重复量很大的时候，用Reference可以避免重复，减少磁盘占用空间。具体的优缺点要结合实际场景去分析。

![](https://i.imgur.com/MR04nLJ.jpg)

Bi-directional referencing 双向引用, 比如student 下引用address， address下也引用student

[Normalization vs Denormalization](https://dev.to/damcosset/mongodb-normalization-vs-denormalization)

1 to million 的情况用Reference可以极大减小存储空间

[立即执行语句IIFE](https://flaviocopes.com/javascript-iife/)

