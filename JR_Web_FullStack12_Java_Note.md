# JR_Web_FullStack12_Java_Note

[01 Introduction]()  
[02 HTML and CSS]()  
[03 CSS and SASS]()  
[04 JavaScript]()  
[05 Git](#05-Git)  
[06 JavaScript ES6](#06-JavaScript-ES6-ECMAScript)  
[07 React JS Introduction](#07-ReactJS-Introduction)

## 05-Git
A Distrbuted Version Control System.  
尽量尝试使用command line来使用Git，但新手刚上手可以用Git GUI的一些软件来帮助做。(Github Desktop, SourceTree)  
参考Git Cheat Sheet文件，把命令用熟  
必须要包括Git Ignore，防止传入IDE建立project自带的文件  
以主分支（以前是master, 现在是main）为基准  

### 第一种方式建立repo （没有远端repo情况下）
git init：把你的project纳入版本控制  
git clone：直接把repo抓下来（包括版本控制）  
从课件Git Local Hands on开始多练习  
```
mkdir learngit：创建learngit文件夹  
cd learngit：进入learngit文件夹  
pwd：显示当前路径  
git init：版本控制初始化，将learngit文件夹纳入版本控制  
touch README.md: 新建一个markdown文件（或者vi README.md或者用text editor的cli比如atom README.md)
git add README.md （将新文件添加到版本控制stage）
git status （查看当前repo文件是否commit）
git commit -m "组织合适的message" （可参考作业要求里面写的message）
git log （查看历史comment）
```
### 每次修改以后
```
git status （勤用这个命令查看当前repo的commit状态）
git add README.md （将新文件添加到版本控制）
git status （查看当前repo文件是否commit）
git commit -m "组织合适的message" （可参考作业要求里面写的message）
```

### git add相关
git add . （慎用，可以用git add . -p逐步查看并add）  
必须要包括.gitignore，防止传入IDE建立project自带的文件  
所有的password是绝对不能提交的  
同时project相关configuration文件也不要交上去  
所以上述文件需要放到.gitignore文件中  

### Undo changes
git reset <comment> (到git log中找需要reset的commit，大部分情况使用reset)  
git revert HEAD (如果之后还是需要访问旧的commit，使用revert)  
使用https://git-school.github.io/visualizing-git/这个visualising的工具进行练习  
git commit --amend (撤销之前的commit或者comment)  
git stash （保存已做的修改，同时获取最新的代码版本）  

### Teamworks
个人的branch不会有太多，公司工作需要在不同branches进行作业。  
在teamwork下，需要有一个自己的branch，写好代码后生成pull request，Lead查看确认后可以把自己的branch merge到master上  
git pull (从remote的repo把最新文件抓下来)  
git checkout <branchname> （转换不同的branch）  
git merge (将自己branch上的修改合并到master上，这之前必须solve所有的conflicts)  
时刻更新主分支上的代码  

### How to set personal token
https://docs.github.com/en/free-pro-team@latest/github/authenticating-to-github/creating-a-personal-access-token

### Set up SSH key
https://docs.github.com/en/free-pro-team@latest/github/authenticating-to-github/generating-a-new-ssh-key-and-adding-it-to-the-ssh-agent

Pull Request之前必须解决所有的conflicts  
解决冲突，谁后提交谁解决冲突，一般在自己的代码上解决冲突，未经允许不要改别人的！！  
如果遇到没有权限的repo，可以使用Fork加到自己的repo，做完修改之后可以apply a pull request against the original one


## 06-JavaScript-ES6-ECMAScript

JavaScript (Vanilla, ES6)  
JS课件基础知识要熟练掌握  
DOM -> 对DOM element的操作  
jQuery 作为lib 提供了api，帮我们简化了一些操作

```
Document.getElementById('btn').classList.add('active');
```
这个是Vanilla JS作为lib提供了实用JavaScript操作DOM 的api
```
Vanilla JS != Native JS
Node JS != Native JS
TypeScipt是Native JS的强类型，编译型的开发
Vanilla JS: 基于 Native JS 对浏览器APP进行开发
Node JS: 基于 Native JS 对服务器app 进行开发
Console 是 Native JS 提供的 API
Window.scrollTo(100);也是Vanilla JS 提供的API
```

### ES6 (ECMAScript 6)与其他编程语言的区别

Version  
Java 15 编译型语言
```  
编译 compile (version) -> 执行文件 -> 任何一个环境
```
Python 3.9  
C# 9.0  
PHP 7  
.net 4.8.0  
JS: 解释型语言，难确定版本(Code -> 用户浏览器上执行)  
不同浏览器，对代码的解释方式解释手段，都是不同的
```
一份JS代码 -> 由浏览器翻译（解释） -> 用户使用
```
不同的浏览器解释出来的结果不同

### ECMA

ECMA组织 -> 定义标准 ECMAScript n -> ES n  
-ES5（ECMA重组，制定了一系列规范，成立公司）  
-ES6 (现在主要使用的版本)  
-ES2018  
-ES7  
-ES8  
-ES2019  
-ES9  

一份JS代码（符合ECMA标准的代码） -> 浏览器根据ECMA定义的标准解释 -> 用户使用  
JS: 解释型、弱类型语言  
区别于  
-> 编译型  
-> 强类型

### 使用箭头代替function
```
var sum = (num1, num2) => {
  console.log(num1 + num2);
}
sum(1,2);
```

### 四大痛点
作用域、原形链，this，pure function，闭包


### ES6 Class本质上是语法糖！！！
没有提供任何新的功能（修饰器）  
JS为了实现效率最大化  
提升（Scan -> 尝试纠错） -> 执行  
let 和 const 解决了代码不规范的问题  
RMR中能不写if...else就不写！！！  

### this小贴士
this原则，谁调用指向谁！！！
```
var alice = {
  name: 'Alice';
  brother: {
    name: 'Bob';
    getName: function( {
      return this.name;
    },
  },
};
alice.brother.getName(); // Bob

alice.getName(); //Alice

var getName = alice.brother.getName;
getName(); // undefined
```
在非严格模式下
```
getName = function() {
  return this.name;
}

getName(); -> window.getName(); // undefined 没有caller
```
在严格模式下  
会报错

### RMR
Readable Maintainable Reusable 可读、可维护、可复用

### 解构赋值
能写 => 就不写 function  
能不写return 就不写 return  
jQuery `$`  

在ctrl c / cmd c上放一个报警装置  
一旦copy/paste就一定有问题 （reusable 问题）  
```
const name = student.name;  
const age = student.age;
const courses = student.courses;
```
结构要一一对应，数量上不一定
```
const student = {
 name: 'Alice',
 age: 26,
 courses: [{
 name: 'Introduction to JavaScript',
 }, {
 name: 'How to give up JavaScript',
 }]
};
```
数组可以， 对象不行
```
const { name, age, courses: [intro, giveUp] } = student;
const { courses: [{name: introName}, giveUp] } = student;
console.log(introName);
```
#### Array例子
```
const items = [1, 2, 3];
const x = arr[0];
const y = arr[1];
const z = arr[2];

const [x, y, z] = items;

const [x, y, z, w] = items;
w -> items[3];
console.log(w); // undefined
```

### Rest

```
const student = {
 name: 'Alice',
 age: 26,
 address: '1 Melbourne St, Sydney',
};
```
不一定是rest，重要是要有... 解构的本质也是语法糖
```
const { name, ...rest } = student;
console.log(name); // Alice
console.log(rest); // age address
```

Rest应用在Array上（不建议）
```
const items = [1, 2, 3];
const [a, ...abc] = items;
```

回国
绿码、登机牌、行李牌、核酸检测
```
-> const {绿码， ...其余的} = 人;
check(绿码);
```


## 07-ReactJS-Introduction

逻辑计算中不要使用三元表达式并进行嵌套
```
const sp = {
  1: 'Direct',
  2: '1 Stop',
  36: 'DreamLine',
};

const default = (n) => `${n - 1} stops`;
const getStops = (flights) => {
  const { length } = flights;\
  const spexpress = sp[length];

  if (spexpress) {
    return sp;
  }
  return default[length];
}

```

### 短路计算
a......b  
&&短路计算中  
a是决定值，b是显示值  
a = true  
b = 'Alice'  
a && b => 'Alice'  

a = false  
b = 'Alice'  
a && b => false


||短路计算中  
a同时是决定值和显示值， b是备选显示值  
a || b  
只要a是true，显示a的值  
只要a是false，显示b的值  


## Readable, Maintainable, Reusable!!!

正常人的思维去写代码  
写其他人可以看懂的代码！！  
千万不要为了写代码而写代码，注意打草稿的重要性。  
不停自我质疑，我的代码是否readable，若不是怎么写更加readable。

```
| Income thresholds  | Rate  | Tax payable on this income |
| ------------------ | ------ | -------------------------- |
| $0 – $18,200       | 0%    | Nil |
| $18,201 – $37,000  | 19%   | 19c for each $1 over $18,200 |
| $37,001 – $90,000  | 32.5% | $3,572 plus 32.5% of amounts over $37,000 |
| $90,001 – $180,000 | 37%   | $20,797 plus 37% of amounts over $90,000 |
| $180,001 and over  | 45%   | $54,096 plus 45% of amounts over $180,000 |
```

```
const caulculatetax = (salary) => {
  const taxTable = {
    { min: 0, max: 18200, accumulate: 0, rate: 0 },
    { min: 18200, max: 37000, accumulate: 0, rate: 0.19 },
    { min: 37000, max: 90000, accumulate: 3572, rate: 0.325 },
    { min: 90000, max: 120000, accumulate: 20797, rate: 0.37 },
    { min: 120000, max: 180000, accumulate: 22311, rate: 0.39 },
    { min: 180000, max: Number.POSITIVE_INFINITY, accumulate: 54097, rate: 0.45 },
  };
  const result = taxTable.find((row) => salary > row.min && salary < row.max);
  const { accumulate, rate, min } = result;
  const tax = (salary - min) * rate + accumulate;
  return tax;
}
```

### SOLID原则（代码理论黄金原则）
面向对象设计
1. 单一职责 (Single Responsibility) 每个代码块的职责是单一的
2. 开闭原则 (Open Close) 对拓展开发，对修改关闭
3. 里氏替换 (Liskov Substitution)
4. 接口隔离 (Interface-Segregation)
5. 依赖注入 (Dependency Injection) 对代码块的依赖不应该在代码块里面，由外部注入

单一职责、开关原则、依赖注入（半本秘籍走天下）高内聚、低耦合

```
const Tax_Table = {
  { min: 0, max: 18200, accumulate: 0, rate: 0 },
  { min: 18200, max: 37000, accumulate: 0, rate: 0.19 },
  { min: 37000, max: 90000, accumulate: 3572, rate: 0.325 },
  { min: 90000, max: 120000, accumulate: 20797, rate: 0.37 },
  { min: 120000, max: 180000, accumulate: 22311, rate: 0.39 },
  { min: 180000, max: Number.POSITIVE_INFINITY, accumulate: 54097, rate: 0.45 },
};

const calculateTax = (salary, taxTable) => {

  const result = taxTable.find((row) => salary > row.min && salary < row.max);
  const { accumulate, rate, min } = result;
  const tax = (salary - min) * rate + accumulate;
  return tax;
}

calculateTax(150000, Tax_Table);
calculateTax(150000, Tax_Table);
calculateTax(150000, Tax_Table);

```

### Project 1

HTML, CSS 天生不能复用  
JS和HTML没有联动性

## ReactJS (A JavaScript Library for building user interfaces)

Declarative  
Component-Based  
Learn once, write anywhere  
### Declarative
声明式  
不要写命令式的代码

### Component-based
组件化 Single Responsibility  
组件化 （查看React课件3.b）

### Learn once, write anywhere
React + ReactDOM = Web application  
React + ReactNative = Mobile application  
React + ReactVR = VR application  
React + ReactTV = TV application  

Thinking in React  
https://reactjs.org/docs/thinking-in-react.html
