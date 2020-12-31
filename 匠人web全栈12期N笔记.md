## 目录
- [01-Introduction & Web Tech](#01-introduction--web-tech)
- [02-HTML & CSS](#02-html--css)
- [03-CSS & Sass](#03-css--sass)
- [04-JavaScript](#04-javascript)
- [05-Git Introduction](#05-git-introduction)
- [06-Node.js: Basics of Node.js](#06-nodejs-basics-of-nodejs)


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