# Class-12 React.js - 1
## 主要知识点

## 课堂笔记
- [Class-12 React.js - 1](#class-12-reactjs---1)
  - [主要知识点](#主要知识点)
  - [课堂笔记](#课堂笔记)
    - [What is React](#what-is-react)
    - [create-react-app](#create-react-app)
    - [JSX (JavaScript XML)](#jsx-javascript-xml)
    - [Vitual DOM](#vitual-dom)
    - [Functional components with props](#functional-components-with-props)
    - [ES6](#es6)
    - [Project 2](#project-2)
### What is React
- 一句话：React是用于build component

### create-react-app
- 脚手架，快速创建react app
- package.json 注意点
  - dependencies：用于production环境的library
  - devDependencies：只有开发时才用到的library，要注意区分
  - 会自带一些library
- package-lock.json 固定library version
- src的入口文件是index.js
  - `ReactDOM.render` 核心部分
  - `document.getElementById('root')` 所有都会放在root下
- 前端用`import`导入library，与nodejs不同

### JSX (JavaScript XML)
- JavaScript的一种新语法，用于写react component
- 简单总结：用JavaScript写HTML
- 使用`className`而不是`class`，因为`class`是HTML的reserved keyword
- `style={{fontStyle: "italic"}}`与HTML中的style用法不同
  
### Vitual DOM
- 会自动监听页面上变化的节点，不会像传统DOM一样整个页面更新，效率高很多

### Functional components with props
- 可以用`props`赋值 `<Welcome name="foo" gender="male" city="sydney"/>`
- props不能被再次赋值 Props are immutable

### ES6
- react和TypeScript完全接受ES6
- `const`常量
- `` template string
- `let`变量在代码块外被destroy
- arrow function
- destructuring
- spread
- class 语法糖

### Project 2
- 要开始做了
- 九月六号前做完