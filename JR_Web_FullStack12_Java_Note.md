# JR_Web_FullStack12_Java_Note

[01 Introduction]()  
[02 HTML and CSS]()  
[03 CSS and SASS]()  
[04 JavaScript]()  
[05 Git](#05-Git)  
[06 JavaScript ES6](#06-JavaScript-ES6-ECMAScript)  
[07 React JS Introduction](#07-ReactJS-Introduction)  
[08 React 哲学](#08-React哲学)  
[09 Agile](#09-Agile)  
[10 Java Basics](#10-Java-Basics)
[11 Interview](#11-Interview)

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


### Readable, Maintainable, Reusable!!!

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

### ReactJS (A JavaScript Library for building user interfaces)

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


## 08-React哲学

结合React PDF学习

### Declarative
SQL: Declarative // 背API  
大餐厅小作坊

### Component-Based

https://zh-hans.reactjs.org/docs/thinking-in-react.html


活用复用  
求同存异  

每次写代码的时候:  
自我否定  
自我怀疑  

Homepage 职责是什么？  
依赖， Page  
职责是负责组装页面  
依赖是Header Content  
HomePage
  - Header
  - Content

Component 划分 - 按责任划分 Component
HomePage
  Page
    - Header
      - Avatar
      - Navbar
    - Main
      - HomePage
      - AboutPage
      - ResumePage
    - Footer

在ReactJS中  
class -> className  
for -> htmlFor  

SocialMedia 按照复用拆分

pass by value  
pass by reference  

Create React
1. * 通过JavaScript去写HTML
2. ? 需要划分 Component
3. ? 模块化代码
4. -> Webpack (entry -> output)
5. * JSX
6. ? 引入 Babel
7. -> Webpack + Babel -> loader
8. * css
9. -> Webpack loader
10. * Image
11. -> Webpack loader
12. * index.html 引用问题
13. -> Webpack plugin
14. * dist 目录混乱问题
15. -> webpack plugin
16. * 每次更改都需要手动build
17. ? Dev server ->  实时检测更改，自动build，并反映到浏览器上
18. -> Webpack dev server (refresh)

需求 -> 理解需求 -> 设计实践 -> 反思 -> 实践
解构赋值中key与value相同时只需要写key的值

React state 用来保存可更改的数据，替换掉obj这种reference更新


## Code Review
在做P3的时候，希望同组所有的developer都要review代码，然后看看代码有什么问题么。个人觉得代码可以通过就点approval。  
所有的pull request应该根据代码规范来做，pull request后，你们可以有至少两个人approval后，才能merge，然后先要review代，comments问题的地方，改完之后reviewer有两个人点了approval，之后才能merge  
不是review整个项目的代码，所有的代码都是在pull request阶段review代码，如果已经merge到master了，相当于代码已经属于 production级别的代码了  
review代码是要在pull request阶段review，不要一上来就merge，到时候代码问题会很大，然后没有人能够提高。pull request阶段可能能持续续2-5天没有办法merge。然后branch代码要每天至少一次commit，和要让branch在rebase on master，保持你们的branch是最新的代码  

以上内容from -老板以及各位老师

## 09-Agile

Agile希望Denvelopers从全局的角度来看整个项目，不单单关注到自己份内的事，更是应该关注但没有关注的  
需求和实现之间的gap现今依然存在。Developers需要不仅关注自己的代码，还需关注具体的需求  
做项目不单单是写代码，communication也是一个需要关注的点。好的、有效的communication需要get到customer真正需要的东西。  
不要以自己的common sense想当然看问题。  
目的是为了解决问题，而不是争论对错，减少沟通中的gap

### Waterfall模型
自上而下，按序进行  
缺点是难回头，出现问题后很难回去改

What is a successful project  
好的项目取决于三点：
1. Scope
2. Budget
3. Schedule

更重要考虑的是Stakeholders

- Customer (End User)
- User (Client)
- Develop Team

Waterfall模型架构下，失败的项目是超过50%，客户很难理解到底开发了什么样的产品  

### 敏捷模型

敏捷软件开发宣言  
Manifesto for Agile Software Development  
(17位大佬滑雪的时候想出来的👌)  
https://agilemanifesto.org/ 英文版  
https://agilemanifesto.org/iso/zhchs/manifesto.html 中文版  
敏捷原则：  
https://www.scrumcn.com/agile/scrum-knowledge-library/agilevalues.html 中文版  
https://www.agilealliance.org/agile101/12-principles-behind-the-agile-manifesto/ 英文版  
- 我们最重要的目标，是通过及早和持续不断地交付有价值的软件使客户满意。
- 欣然面对需求变化，即使在开发后期也一样。为了客户的竞争优势，敏捷过程掌控变化。
- 经常地交付可工作的软件，相隔几星期或一两个月，倾向于采取较短的周期。
- 业务人员和开发人员必须相互合作，项目中的每一天都不例外。
- 激发个体的斗志，以他们为核心搭建项目。提供所需的环境和支援，辅以信任，从而达成目标。
- 不论团队内外，传递信息效果最好效率也最高的方式是面对面的交谈。
- 可工作的软件是进度的首要度量标准。
- 敏捷过程倡导可持续开发。责任人、开发人员和用户要能够共同维持其步调稳定延续。
- 坚持不懈地追求技术卓越和良好设计，敏捷能力由此增强。
- 以简洁为本，它是极力减少不必要工作量的艺术。
- 最好的架构、需求和设计出自自组织团队。
- 团队定期地反思如何能提高成效，并依此调整自身的行为表现。

#### Agile
- 快速反馈  
- 交付价值  （Focus挑优先级高的来做）
- 迭代开发  (Agile第二次迭代可能会修改第一个迭代的内容)

Agile Tree
- Kanban  
- Scrum  
- Lean  
- FDD  
- XP

#### Scrum框架
Scrum Sprint Cycle (1-4 weeks, preferred 2 weeks)

Product Owner / Business Analyst (Feature) -> Project Backlog -> Sprint Planning -> Sprint Backlog ( Feature -> Technical Task) -> Sprint Execution (Daily Scrum: Daily Standup meeting) -> Potentially Shippable Product Increment -> Sprint Review (Inspect / Adapt) -> Sprint Retrospective (Inspect / Adapt) -> Next Scrum  

Scrum方法论 “3355”  
- 3个角色 (Scrum Master: 协助管理3个物件、5个会议)
- 3个物件 (产品列表、迭代列表、产品增量)
- 5个会议

BA / 产品负责人： 管理好产品列表
团队成员：跨组织

##### 3个物件
产品列表满足DEEP原则
Detailed Appropriately
Emergent 涌现成的
Estimated 有估算的
Prioritized 排好优先级的

P3的第一个commit可能就是一个空的project，作为user story，基于此之后大家能递交

##### User Story 用户角度
- Who: As a User
- What: I want to login to the website
- Why: so that I can achieve

A/C: Acceptance Criteria (验收标准)

##### Tips
- 3C 了解细节：Card, Conversation, Confirmation
- MoSCow & Kano: 优先级模型
- INVEST准则：Independent 独立的, Negotiable 可讨论的, Valuable 有价值的, Estimatable 可估计的, Size Appropriately 小的, Testable 可测试的

##### 故事估算
不是commitment

##### Sprint Retrospective Meeting

回顾这个sprint发生了什么，回顾以及总结  
最后要有action plan，其中的action items需要有人去做。  
Action items需要具体，知道如何去具体地改进

Lead Time vs Cycle Time  
目标是减少Cycle Time  
有dependency就会有等待时间，减少dependency从而能更好提高效率  
新木桶理论  
T型人才  
创新   

##### Kanban

Kanban board  
- Visualisation
- Working in progress limit
- 只能从下游往上游移动 pull
- Improve collabrately
更着重于整体流程的优化，而不是具体个体

##### 极限编程(eXtreme Programming)

- Pair Programming
- Test Driven Development
- Continuous Integration Workflow

##### 实际使用

Kanban 和 Scrum结合使用  
整合极限编程实践：TDD

## 10-Java-Basics

Server端：Server上的数据直接呈现，不会传入client使用的系统平台  
Client端：下载到client系统、平台运行  
Java作为后端有一个非常庞大、完整的生态，可针对任何情况  
课件两本推荐的书很不错，可以找渠道看  

- 高可用
- 高性能
- 易扩展：系统不足可以进行扩大、扩展
- 可伸缩：Scaling，多余的系统可以进行缩减
- 且安全：前端程序用的是https，server端需要加密。（用户如果需要了解系统得有专门的有时效性的token验证）JWS Token

应用服务器需要CPU速度非常快  
数据库服务器需要数据读取速度足够快
文件服务器需要容量足够大

- 当访问量越来越大时  
需要在应用服务器上作出改变  
增加本地缓存，并建立多个分布式缓存服务器  
目标是建立stateless app  

- 当访问量进一步增大时  
Distributed System with Load Balancer (负载均衡调度)  
横向扩展：scale out  
纵向扩展：scale up  
应用服务器的伸缩以auto scaling进行控制  
在任何应用中不应该使用sticky session，这是非常糟糕的设计，会导致非常差的用户体验

- 当访问量再次增大时
增加从数据库（主从分离、读写分离），能极大减小数据库的负担  
从数据库可以有多个
AWS中使用的是RDS Relational Database Service
DR: Disaster Recovery
P3会使用Postgres的数据库

- 如果还是有进一步扩展的需求
CDN 服务器：AWS中有CloudFront
增加反向代理服务器：可以屏蔽外界
P3中会使用ECS、Docker、AWS codebuild codedeploy code pipeline

### CI/CD (Continuous Integration/ Continuous Delivery)
- A key to deliver the product reliably  

### Serverless
作为使用者，不需要关心server是什么，AWS会帮忙管理  
Message System是异步的  
RESTful API是同步的

NoSQL Server: AWS DynamoDB + Lambda  

CRUD

Microservice都是独立的，每个Microservice后面必然跟着一个独立的database

### CAP原则
- Consistency
- Availability
- Partition Tolenrece

### Github Flow
1. Master branch deployable
2. Branch off master as feature branch
3. Always commit & push to feature branch
4. Open a pull request once it's ready
5. Get review and update the feature branch
6. Merge to master

### Git Flow

- Create a bug_fixing branch each time you want to fix a bug, unless the two bugs are quite small.
- Deploy feature branch to release branch first, then to the master branch


## 11-Interview

If you think you are not good at interview, the only reason is that you did not prepare well.  

### Skill sets

#### Hard Skills

- Technology
- Experience

#### Soft Skills

- Good communicator
- Team player
- Open-minded
- Love to share
- Ability to learn

### Employability

#### Technical Experience

- Github
- Internship
- Freelancer
- User Groups
- Projects
- Blogging

做Commercial Projects，不是一遍遍去刷教学视频和tutorials。

#### Research

- You
- Interviewer(s)
- The position
- LinkedIn: Alumni, Friends
- Company
- Industry and Competitors
- Products and Services

1. Curriculum
2. Initial Interview
  - Online Assessment (HackerRank & LeetCode)
  - Telephone interview
    - Personal Information
    - Visa
3. First-Round Interview
4. Code Test
5. Second-Round Interview
6. Reference Check
7. Offer Selection and Decision

### How to prepare

Write down your answers
- Self-introduction
- Team culture you want to
- Expected salary range