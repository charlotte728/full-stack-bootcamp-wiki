# Class-07-ES6&NodeJS

## 主要知识点
- [Class-07-ES6&NodeJS](#class-07-es6nodejs)
  - [主要知识点](#主要知识点)
  - [课堂笔记 JavaScript ES6](#课堂笔记-javascript-es6)
    - [Classes](#classes)
      - [extends 继承](#extends-继承)
      - [prototype](#prototype)
      - [prototype chain](#prototype-chain)
      - [What does `new` do?](#what-does-new-do)
    - [Closure 闭包](#closure-闭包)
    - [IIFEs 立即执行函数](#iifes-立即执行函数)
  - [课堂笔记 Node.js](#课堂笔记-nodejs)
    - [About Nodejs](#about-nodejs)
    - [Event Loop事件循环](#event-loop事件循环)
    - [宏任务，微任务 （简单理解）](#宏任务微任务-简单理解)
    - [建议](#建议)
    - [作业](#作业)
  
## 课堂笔记 JavaScript ES6
### Classes
- JavaScript的类与其他语言不同，是一种语法糖[]，实际上只是function
- JavaScript的继承也与其他语言不同（Delegate而非继承）
- 每一个变量实际上都是`Object`

Classes are a template for creating objects. Classes are in fact functions, class is only a syntax sugar.

```js
function Person(name) {
  this.name = name;
  this.toString = function () {
    console.log('name: ' + this.name);
  };
}
var mason = new Person('mason');
mason.toString(); // name: mason
```

```js
class Person {
  constructor(name) {
    this.name = name;
  }
  toString() {
    console.log(`name: ${this.name}`);
  }
}
const mason = new Person('mason');
mason.toString(); // name: mason
```

#### extends 继承

```js
class Teacher extends Person {
  constructor(name) {
    super(name);
  }
  teach() {
    console.log(`${this.name} is teaching`);
  }
}

const mason = new Teacher('mason');
mason.teach(); // mason is teaching
mason.toString(); // name: mason -> BUT how?
```

#### prototype
- JavaScript 只有一种结构：对象
- 每一个类或函数都有一个prototype属性
- 每一个实例或对象都有一个`__proto__`属性
- 每一个prototype都指向一个`__proto__`
- 取方法会一层层网上取，直到`Object`，最终到`null`为止
- 原型链例图
![原型链](/image/s14c0701.png)


```js
// is mason constructed by Teacher?
mason instanceof Teacher; // true
mason instanceof Person; // true
mason instanceof Object; // true
```

Every class or function has a `prototype` property
Every instance or object has a `__proto__` property
Instance's `__proto__` points to class's `prototype`

```js
mason.__proto__ === Teacher.prototype; // true
```

#### prototype chain

```js
Teacher.prototype.__proto__ === Person.prototype; // true
Person.prototype.__proto__ === Object.prototype; // true
Object.prototype.__proto__ === null; // true
```

#### What does `new` do?
- 实际上是创建了某种关联

```js
var mason = Person('mason');
console.log(mason.name); // ??
```

```js
function Person(name) {
  var person = {};
  // var person = Object.create(Person.prototype);
  person.name = name;
  return person;
}
Person.prototype = Object.create(Object.prototype);
// Person.prototype.__proto__ === Object.prototype
Person.prototype.constructor = Person;

var mason = Person('mason');
console.log(mason.name); // mason
```

### Closure 闭包
- 当需要取某个属性或变量时，会尝试从上一级作用域中取，一层一层向上
- 可用于从上级作用域向下级作用域传值
- 可用于隐藏变量（类似于人为制造一些语言中的private variable）

### IIFEs 立即执行函数
- 具体用例会在nodejs中提到

## 课堂笔记 Node.js

### About Nodejs
- 优势：灵活，可以用JavaScript打通前后端
- 异步 Async 事件驱动
    + JavaScript是单线程，因此同时只能做一件事
    + 所以要使用异步
    + `callback()`在一个event完成后进行
    + `callback()`可以进行嵌套，来表示逻辑的执行顺序，但会导致callback hell的问题，代码可读性变差
    + 因此会使用`Promise`
        - 有三种状态 pending fulfilled(resolved) rejected
        - 状态变化 pending -> fulfilled, pending -> rejected
        - `.then` 获取resolved的结果, `.catch`获取rejected的信息, `.finally` 无论resolved还是rejected都会执行
- Nodejs只是一个JavaScript的基于Chrome V8引擎的runtime环境
- non-blocking I/O 
    + 非阻塞 == 异步 == 不等待异步执行的代码，充分利用资源
    + I/O Input Output
- 
### Event Loop事件循环
- heap
- stack先进后出
- 在JS执行时首先会从上向下执行，异步代码会由web api注册由浏览器单独管理，同步代码会继续执行
- 被放到callback queue中挨个放入stack中执行
- 流程
  - 同步代码执行碰到异步代码丢给web api注册
  - 时间结束 -> 事件进入callback queue
  - 当call stack为空的时候
  - event loop会从callback queue取前列的event，继续执行

- 事件循环的视频例子 [http://latentflip.com/loupe/?code=JC5vbignYnV0dG9uJywgJ2NsaWNrJywgZnVuY3Rpb24gb25DbGljaygpIHsKICAgIHNldFRpbWVvdXQoZnVuY3Rpb24gdGltZXIoKSB7CiAgICAgICAgY29uc29sZS5sb2coJ1lvdSBjbGlja2VkIHRoZSBidXR0b24hJyk7ICAgIAogICAgfSwgMjAwMCk7Cn0pOwoKY29uc29sZS5sb2coIkhpISIpOwoKc2V0VGltZW91dChmdW5jdGlvbiB0aW1lb3V0KCkgewogICAgY29uc29sZS5sb2coIkNsaWNrIHRoZSBidXR0b24hIik7Cn0sIDUwMDApOwoKY29uc29sZS5sb2coIldlbGNvbWUgdG8gbG91cGUuIik7!!!PGJ1dHRvbj5DbGljayBtZSE8L2J1dHRvbj4%3D]

### 宏任务，微任务 （简单理解）
- 宏任务 -> setTimeout, ajax call, DOM events
- 微任务 -> promise

### 建议
- 能用箭头函数尽量用箭头函数
- `command+shift+p`打出分割线
- Visual Studio Coede 由electron
  
### 作业
看看原型链中Teacher和Person的关联