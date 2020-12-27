## 01-Introduction & Web Tech

安装ssl证书的网站：certbot

了解客户端渲染和服务端渲染csr ssr ssg

h1 只能有一个

了解js加在head和尾部的区别

local storage 同一域名下 / section storage 同一tab下，不需要储存用户信息

cookie 服务器存在浏览器，以及cache区别

shift + f5 清空cache刷新

genymotion debug安卓设备



## 02-HTML & CSS

margin重叠，哪个大用哪个

BEM命名

box-sizing: border-box (child加padding后能保持在parent里面)



## 03-CSS & Sass

bootswatch 修改bootstrap默认变量

sass: cat style compressed 等命令行指令

多看sass文档：https://sass-lang.com/documentation（ctrl+左键打开）

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

## 05-Git

别让地铁站都比你努力！

Distributed Version Control System 好处：可以在本地保留分支的历史，适合远程办公，在无网络状况下拉分支

各种git代码看老师的ppt或者上网查阅

注意添加git ignore 文件，不要提交vscode和idle自带的文件

git pull是从git上拉取最新代码，可能会出现冲突合并覆盖的问题，然后自己创建一个分支branch，交给老板review之后如果没问题，会把自己的branch合并到master branch。

创建branch原则是按feature。一个人不是一直在一个branch上工作。

使用ssh key来连接

首先搞懂clone，git branch，commit push， rebase ，pull request merge，这几个就够了clone，git branch，commit push， rebase ，pull request merge

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

[git教程入门](https://www.bilibili.com/video/BV1KD4y1S7FL)
[git教程进阶]( https://www.bilibili.com/video/BV1hA411v7qX?spm_id_from=333.788.b_636f6d6d656e74.4)

