## 课堂笔记

### 1. HTML + CSS + JS
- HTML: 做content structure
- CSS: 做layout design，styling
- JS: 与user交互的桥梁，捕捉用户的操作，用户data（给backend）的传递

### 2.什么是JavaScript
- 首先是编程性语言
    - CSS, HTML, 都不是编程性语言，无法做逻辑性运算不是图灵完备的。
    - 图灵完备：https://www.zhihu.com/question/20115374
    - 高级语言（例如C#,JAVA）都跑在一个自己的运行环境里面，运行环境负责好了跟操作系统的交互，因此写起来很方便。
- JavaScript也是一个高级语言
    - 曾经只作为跑在browser里的一门语言，现在多了一个运行环境（nodejs），只要能安装nodejs的地方，就能运行js；nodejs可以运行在多种设备上，从大设备到小芯片，都可以加载。
    - Javascript可以从前到后一条线贯穿，frontend可以用，也可以做back-end service, 一样能做middlelayer（中间层）的back-end for frontend。
    - 本身不是一门严谨的语言
       - weekly type, runtime时不会检查变量类型；写的时候可以动态的改变变量type
    - JavaScript跟Java并没有联系，只是蹭热度而已。
- ECMAScript: 一个标准，规定了满足ECMAScript的语言具备哪些语法特性；相当于基本决定了JavaScript的方向
    - JavaScript fatigue: JavaScript突然有一天进行了大量更新，令很多developer焦虑于对新特性的学习。
    - 2009～2015（ES6）:没有更新过，因此积累了大量的更新(语言特性)
    - ES6(2015)年带来了很多语言的新特性，之后就是慢慢在更新了
- 怎么测试运行
   - Chrome里，右键select inspect element, 然后console里直接敲代码
- 怎么写入网页
   - 网页中直接加入`<script>`，例如  
     ```<script>
          console.log("Hello World!");  
       </script>```
- CSS: 做layout design，styling
- JS: 与user交互的桥梁，捕捉用户的操作，用户data（给backend）的传递