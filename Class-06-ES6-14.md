# Class-06-ES6

## 主要知识点
- [Class-06-ES6](#class-06-es6)
  - [主要知识点](#主要知识点)
  - [课堂笔记](#课堂笔记)
  - [1. 什么是ES？](#1-什么是es)
  - [2. ES6语法](#2-es6语法)
    - [2.1 `var let const` 变量声明](#21-var-let-const-变量声明)
    - [2.2 Template string 模板字符串](#22-template-string-模板字符串)
    - [2.3 Spread operator 展开运算符](#23-spread-operator-展开运算符)
    - [2.4 Destructuring 解构赋值](#24-destructuring-解构赋值)
    - [2.5 Default parameters 默认参数](#25-default-parameters-默认参数)
    - [2.6 Arrow function 箭头函数](#26-arrow-function-箭头函数)
    - [2.7 Callback 回调函数](#27-callback-回调函数)
    - [2.8 this](#28-this)
    - [2.9 Array operations](#29-array-operations)
      - [Manipulation](#manipulation)
      - [Iteration 遍历](#iteration-遍历)
    - [2.10 Set](#210-set)
  - [作业：](#作业)
  
## 课堂笔记
- Mason老师
- 多复习上课内容，也可以课下找老师提问。
- 加老师好友时备注teams的名字
- [老师上课用md链接](https://github.com/LazeBear/jr-fullstack-notes-14/blob/master/0-es6/notes.md)

## 1. 什么是ES？
- ES -> ECMAScript ECMA International是一个组织，给JavaScript制定的标准叫ECMAScript
- 例如变量声明，`var let const`都由ECMAScript定义
- ES有不同的版本，最常见为ES5 (ES2009) 和ES6 (ES2015)，但不向下兼容
- ES5支持所有浏览器，ES6之后部分浏览器无法识别，但可以通过[babel](https://babeljs.io/)转换
- ES是为了避开JavaScript本身的坑
- ES6经常会作为之后版本一个总称

## 2. ES6语法
### 2.1 `var let const` 变量声明
作用域 Scope 有三种
+ global 全局
+ function 函数
+ block 块级
当一个变量在当前作用域找不到时，会到上层作用域中找。

- `var` 关键字
    - 在funtion内的作用域为function，在funtion外为global
    - 可以用`var`重新声明已有的变量
    - 所有声明会被提升到最开始，赋值仍然会在被赋值的位置
    - 会出现一些不可以预计的问题，例如：
    ```js
    var fruit = 'apple';
    if (true) {
    // think about this is in another file
        var fruit = 'pear';
    }
    console.log(fruit); // pear
    ```
    - 只能用`let const`，不使用`var`，除非环境不支持

- `let` 关键字
    - 作用域为block，block是被`{}`大括号包裹的内容
    - 不能被redeclare

- `const` 关键字
    - 作用域为block，但不能被重新赋值
    - pass by reference可以进行更新，pass by value不能进行更新。例如可以对array的内容进行更新，而不能对一个string variable赋值

### Quiz <!-- omit in toc --> 

1. What's the output of the following code

```js
var i = 5;
for (var i = 0; i < 3; i++) {
  console.log(i);
}
console.log(i);
// 0 1 2 3
```

2. What's the output of the following code

```js
let i = 5;
for (let i = 0; i < 3; i++) {
  console.log(i);
}
console.log(i);
// 0 1 2 5
```

3.

```js
var arr = [10, 12, 15, 21];
for (var i = 0; i < arr.length; i++) {
  setTimeout(function () {
    console.log('Index: ' + i + ', element: ' + arr[i]);
  }, 1000);
}
// undefined undefined undefined undefined
// 因为异步
// 如果使用let则会正确打印四个数字
```

#### Conclusion <!-- omit in toc --> 

| keyword | scope    | re-declare | update | hoisting              |
| ------- | -------- | ---------- | ------ | --------------------- |
| var     | function | Yes        | Yes    | Yes (undefined)       |
| let     | block    | No         | Yes    | Yes (not initialized) |
| const   | block    | No         | No     | Yes (not initialized) |

### 2.2 Template string 模板字符串
- 在ES5需要用 `+` 连接字符串，在ES6可以使用模板字符串``在字符串中嵌入变量
```js
const name = 'mason';
const age = 104;
// es5
console.log('My name is ' + name + ", and I'm " + age + ' years old');

//es6
console.log(`My name is ${name}, and I\'m ${age} years old`);
```

### 2.3 Spread operator 展开运算符
- 对array和object的内容进行展开，添加新元素
- 后面会替换前面的值
- 常见写法是写在前面
- 浅拷贝
```js
const array = [1, 2];
const newArray = [...array, 3, 4];
console.log(newArray); // [1, 2, 3, 4]
```

```js
const fruit = { name: 'apple', color: 'green' };
let newFruit = { ...fruit, color: 'red' };
console.log(newFruit); // {name: "apple", color: "red"}
newFruit = { color: 'red', ...fruit };
console.log(newFruit); // {color: "green", name: "apple"}
```

### 2.4 Destructuring 解构赋值
- 左边的`{}`中是我们要解构的名字，右边是取出值的对象
- 在Object中按照key赋值而不是index
- 在array中要注意index位置
Object destructuring extracts property from object and assigns it to variables.
One way would be using the dot notation

```js
const fruit = { name: 'apple', color: 'red' };
const name = fruit.name; // apple
const color = fruit.color; // red
```

With the new syntax, we don't need to repeatly refer to the `fruit` object

```js
const fruit = { name: 'apple', color: 'red' };
const { name, color } = fruit;
console.log(name); // apple
console.log(fruit); // red
```

we can also rename the variable 也可以对变量进行重命名

```js
const fruit = { name: 'apple', color: 'red' };
const { name: fruitName, color: fruitColor } = fruit;
console.log(fruitName); // apple
console.log(fruitColor); // red
```

or desctructing an array

```js
const fruits = [
  { name: 'apple', color: 'red' },
  { name: 'pear', color: 'green' }
];
const [apple, pear] = fruits;
console.log(apple); // {name: "apple", color: "red"}
console.log(pear); // {name: "pear", color: "green"}
const [{ color: appleColor }, { color: pearColor }] = fruits;
console.log(appleColor); // red
console.log(pearColor); // green
```

more complicated use cases

```js
const [foo, [[bar], baz]] = [1, [[2], 3]];
console.log(foo); // 1
console.log(bar); // 2
console.log(baz); // 3
```

```js
const [, , third] = ['foo', 'bar', 'baz'];
console.log(third); // "baz"
```

结合spread operator使用，spread operator必须放在最后，且会赋值为一个array
```js
const [head, ...tail] = [1, 2, 3, 4];
console.log(head); // 1
console.log(tail); // [2, 3, 4]
// Rest element must be last element
```

可以提供默认值
```js
const [missing = true] = [];
console.log(missing); // true
```

### 2.5 Default parameters 默认参数
- 在声明函数时可以在constructor中设置默认值，在变量没传入值时默认使用

```js
function sum(a = 1, b = 1) {
  return a + b;
}
console.log(sum()); // 2
console.log(sum(undefined, 2)); // 3
console.log(sum(3, 4)); // 7
```

### 2.6 Arrow function 箭头函数
- 省略了`function`关键字
- 如果只有一行`return`则可以进行简写
- 避免在异步情况下取不到值的情况

```js
const add = function (x, y) {
  return x + y;
};
// vs
const add = (x, y) => {
  return x + y;
};
// equals
const add = (x, y) => x + y;
```

### 2.7 Callback 回调函数
- 当某些事件触发时，会进行callback，常用于异步
- 给涉及到异步的函数排序挨个执行

Explain in a simple way, pass the function as a parameter and when some _event_ happened, execute this function.
Frequently used for async or sequential purpose

```js
function normalFunction(param) {
  console.log(param);
}
function sum(x, y, callback) {
  const sum = x + y;
  callback(sum);
}
sum(1, 2, normalFunction);
```

Callback with arrow function

```js
setTimeout(function () {
  console.log('normal function');
}, 1000);

setTimeout(() => {
  console.log('arrow function');
}, 1000);
```

### 2.8 this
- 不同场景会有不同的指向
- this在函数执行时才会确定指向
- this是指向上级作用域，但是碰到异步，为了不让他指向例如`window`或其他作用域，所以一定要用arrow function去指定this指定为他的上级作用域

In most cases, the value of `this` is determined by how a function is called (runtime binding). It can't be set by assignment during execution, and it may be different each time the function is called. [[MDN](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/this)]\* \*[strict mode](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Strict_mode) is enabled by default in ES6 modules

- _this_ keyword in normal functions
    - 在function中this指向`window`

```js
function foo() {
  console.log(this);
}
foo(); // window
```

- _this_ keyword in normal functions with bind, call, apply
    - 在bind，call，apply中会改变this的指向
```js
// a1,a2
foo.call({ number: 1 }); // {number: 1}
// [a1,a2]
foo.apply({ number: 2 }); // {number: 2}
// bind returns a new function
const bar = foo.bind({ number: 3 });
bar(); // {number:3}
```

- _this_ keyword in an object and callback functions

In arrow function, `this` points to the enclosing lexical context's `this`.

```js
const calendar = {
  currentDay: 6,
  normal: function () {
    console.log(1, this);
    setTimeout(
      function () {
        console.log(2, this);
      } // .bind(this)
    );
  },
  arrow: function () {
    console.log(3, this);
    setTimeout(() => {
      console.log(4, this);
    });
  }
};
calendar.normal();
calendar.arrow();
```


### Quiz <!-- omit in toc --> 

```js
const object = {
  message: 'Hello, World!',

  getMessage() {
    const message = 'Hello, Earth!';
    return this.message;
  }
};

console.log(object.getMessage()); // Hello, World!
```

```js
const object = {
  who: 'World',

  greet() {
    return `Hello, ${this.who}!`;
  },

  farewell: () => {
    return `Goodbye, ${this.who}!`;
  }
};

console.log(object.greet()); // Hello, World!
console.log(object.farewell()); // Goodbye, undefined! 因为箭头函数的this指向再上级作用域window
```

### 2.9 Array operations

#### Manipulation
- `push` 尾部添加，添加到后面
- `unshift` 头部添加，添加到前面
- `pop` 尾部去除，删除最后一个
- `shift` 头部去除 ，删除第一个

```js
const fruits = ['apple'];

fruits.push('pear');
console.log(fruits); // ["apple", "pear"]
fruits.unshift('grape');
console.log(fruits); // ["grape", "apple", "pear"]
// splice(x,y,newAdded)
// remove y items from index x, and add newAdded
fruits.splice(1, 1, 'watermelon', 'peach');
console.log(fruits); // ["grape", "watermelon", "peach", "pear"]
let fruit = fruits.pop();
console.log(fruit); // pear
console.log(fruits); //  ["grape", "watermelon", "peach"]
fruit = fruits.shift();
console.log(fruit); // grape
console.log(fruits); // ["watermelon", "peach"]
```

#### Iteration 遍历
- 不同场景下会使用不同的遍历操作

for loop

```js
const fruits = ['apple', 'pear'];
for (let index = 0; index < fruits.length; index++) {
  const fruit = fruits[index];
  console.log(fruit);
}
// apple
// pear
```

for...of

```js
const fruits = ['apple', 'pear'];
for (let fruit of fruits) {
  console.log(fruit);
}
// apple
// pear

// for...in -> 0, 1    usually used in object
```

forEach

```js
const fruits = ['apple', 'pear'];
fruits.forEach((fruit) => console.log(fruit));
// apple
// pear
// cannot use break here
```

Map
- 可以改变array的内容

```js
const fruits = ['apple', 'pear'];
const newFruits = fruits.map((fruit) => ({
  name: fruit,
  price: 10
}));
console.log(newFruits);
// [{name: "apple", price: 10},{name: "pear", price: 10}]
```

Reduce
- 接收两个必要参数

```js
const numbers = [1, 2, 3];
const sum = numbers.reduce((accumulator, number) => accumulator + number, 0);
console.log(sum); // 6
```

Search
- 在array中查询
- `filter`找到所有符合的元素，`find`找到第一个

```js
const numbers = [1, 2, 3, 4, 5];
console.log(numbers.includes(2)); // true
// Array.some
console.log(numbers.indexOf(2)); // 1
// Array.findIndex
```

```js
const numbers = [1, 2, 3, 4, 5];
const odds = numbers.filter((i) => i % 2);
console.log(odds); // [1,3,5]

const fruits = [
  {
    name: 'apple',
    color: 'red'
  },
  {
    name: 'pear',
    color: 'green'
  },
  {
    name: 'grape',
    color: 'green'
  }
];
const filteredFruits = fruits.filter((i) => i.color === 'green');
console.log(filteredFruits);
// [{name: "pear", color: "green"}, {name: "grape", color: "green"}]
```

```js
const fruits = [
  {
    name: 'apple',
    color: 'red'
  },
  {
    name: 'pear',
    color: 'green'
  },
  {
    name: 'grape',
    color: 'green'
  }
];
const greenFruit = fruits.find((i) => i.color === 'green');
console.log(greenFruit);
// {name: "pear", color: "green"}
```


### 2.10 Set
- 可用于快速去重

Set is a data structure, we use it to store _unique_ values.

```js
const set = new Set([1, 2, 3, 4, 4]);
console.log(set); // Set(4) {1, 2, 3, 4}
set.add(5);
console.log(set); // Set(5) {1, 2, 3, 4, 5}
set.add(1);
console.log(set); // Set(5) {1, 2, 3, 4, 5}
console.log(set.has(5)); // true
set.delete(1);
console.log(set.has(1)); // false
console.log(set.size); // 4
```

```js
const array = [1, 2, 2, 3, 4, 4];
const uniqueArray = [...new Set(array)];
console.log(uniqueArray); // [1, 2, 3, 4]
```


## 作业：
```js
const calendar = {
  currentDay: 6,
  normal: function () {
    console.log(1, this);
    setTimeout(
      function () {
        console.log(2, this);
      } // .bind(this)
    );
  },
  // 如果这里为arrow function，这里的this指向哪里
  arrow: ()=> {
    console.log(3, this);
    setTimeout(() => {
      console.log(4, this);
    });
  }
};
calendar.normal();
calendar.arrow();
```