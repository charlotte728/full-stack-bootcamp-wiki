### 短路计算
```
a       b
true false

a && b => false
true && false  

true true
a && b => true

false true
a && b => false

false false
a && b => false

a 决定值 b 显示值

在 && 的短路计算中

a 决定了是否显示 b

a true  -> b
a false -> false

true  'Alice'
a && b => 'Alice'

false  'Alice'
a && b => false

true true
a || b => true

false true
a || b => true

true false
a || b => true

false false
a || b => false

在 || 的短路计算中
a 显示值和决定值
b 备选显示值

'Alice' true
a || b => 'Alice'

'Alice' false
a || b => 'Alice'

false 'Bob'
a || b => 'Bob'

undefined 'Bob'
a || b => 'Bob'

'Alice' 'Bob'
a || b => 'Alice'

'Alice' undefined
a || b => 'Alice'

false undefined
a || b => undefined

undefined null
a || b => null
```

### 课堂笔记

const name = id === '0' ? 'admin' : student.name;

// 三元 ‘表达式‘

// Readable Maintainable Reusable

// Readable
// Maintainable
```
const { lowThreshold, highThreshold, plus, rage } = taxTable;

if (salary <= highThreshold) {
  tax = (salary - lowThreshold + 1) * rate + plus;
  console.log(tax);
  break;
}

// 36 Stops
// [{}, {}, {} ..., {}] // length = 36
// 36 stops -> Dream Line

// Readable, Maintainable, !Reusable
const getStops = (flights) => {
  switch (flights.length) {
      case 1:
          return "Direct"
      case 2:
          return "1 stop"
      case 36:
          return 'Dream Line'
      case 51:
          return 'Around the world'
      default:
          return `${flights.length - 1} stops`
  }
}
```
// !Readable, !Maintainable, !Reusable  
```
const getStops = (flights) => flights.length === 1 ? 'Direct'
  : flights.length === 2 ? '1 Stop'
  : `${flights.length - 1} stops`;
```

// Flights Stops
```
length = 1  => Direct
length = 2  => 1 stop
length = 36 => Dream Line
length = n  => ${n - 1} stops

const 特殊航程长度对照表 = {
   1: 'Direct',
   2: '1 Stop',
   36: 'Dream Line',
};

const 默认航程长度表达 = (n) => `${n - 1} stops`;

const getStops = (flights) => {
const { length } = flights;

const 特殊航程长度表达 = 特殊航程长度对照表[length];

if (特殊航程长度表达) {
  return 特殊航程长度表达;
}

return 默认航程长度表达(length);
};

const getStops = (flights) => {
const { length } = flights;

const 特殊航程长度表达 = 特殊航程长度对照表[length];

return 特殊航程长度表达 ? 特殊航程长度表达 : 默认航程长度表达(length);
}

const getStops = (flights) => {
const { length } = flights;

const 特殊航程长度表达 = 特殊航程长度对照表[length];

return 特殊航程长度表达 || 默认航程长度表达(length); // 短路计算
}

const getStops = (flights) => {
const { length } = flights;

return 特殊航程长度对照表[length] || 默认航程长度表达(length); // 短路计算
}
```

// 不做提前量
// Reusable !== 做提前量
// 代码结构支持 Reusable
```
const getStops = (flights) => {
  const { length } = flights;

  const specialStops = {
    1: 'Direct',
    2: '1 Stop',
    36: 'Dream Line',
  }[length];

  return specialStops || `${length - 1} stops`; // 短路计算
}
```
// Readable Maintainable Reusable

// 澳洲没有网民
// 中国：16亿 -> 10亿 微信用户
// 美国：Facebook 77亿 -> 61亿 -> 30亿 Facebook 用户
// 澳洲：Qantas 2499万 -> 100万 Qantas 用户

// 澳洲没有网民
// 澳洲作为程序员
// 美国一般的解决方案 -> 澳洲的完美解决方案
// 美国时时刻刻的研发高级算法 -> 关注 Performance -> 关注数据
// 他不关心你的代码好坏

// 澳洲程序员最关心什么?
// lifestyle
// 过得舒服，每天写写代码，拿一点钱，照顾老婆孩子，Bunnings 装修装修, 喝喝咖啡

// Readable, Maintainable, Reusable


| Income thresholds  | Rate  | Tax payable on this income |
| ------------------ | ------ | -------------------------- |
| $0 – $18,200       | 0%    | Nil |
| $18,201 – $37,000  | 19%   | 19c for each $1 over $18,200 |
| $37,001 – $90,000  | 32.5% | $3,572 plus 32.5% of amounts over $37,000 |
| $90,001 – $180,000 | 37%   | $20,797 plus 37% of amounts over $90,000 |
| $180,001 and over  | 45%   | $54,096 plus 45% of amounts over $180,000 |

// Readable, Maintainable, Reusable
// 正常人的思维去写代码

// 张三问李四：我今年收入 15w，你能帮我算一下我的税是多少吗？
// 1. 李四拿出来一个表，
// 2. 根据收入找到对应的表行
// 3. 根据表行算出张三的税

// 设计的重要性
// 打草稿的重要性
// 大纲的重要性

// 兵家之大忌，为了代码工作而写代码，为了写而写代码

// Readable, Maintainable, Reusable
// 自我否定, 我这个代码是不是 readable, 不是, 怎么才能更 readable?

// SOLID
// Single Responsibility 单一职责原则
// Open Close 开关原则
// Dependency Injection 依赖注入原则

// 高内聚，低耦合

// 半本秘籍走天下

// Liskov Substitution 里氏替换原则
// Interface Segregation 接口隔离原则

// 前端三驾马车
// React, Angular, Vue

// Readable, Maintainable, Reusable? SOLID？ Vanilla JS & HTML5 & CSS3
// HTML CSS, 天生不能切块复用
// JS 和 HTML 没有联动性

// A JavaScript library for building user interfaces (写页面的)

// Declarative
// 声明式，命令式

// Component-Based
// 组件化 Single Responsibility
// 组件化好处

// Learn once, write anywhere
// React + ReactDOM = Web application
// React + ReactNative = Mobile application
// React + ReactVR = VR application
// React + ReactTV = TV application

```
const TAX_TABLE_2020 = [
  { min: 0, max: 18200, accumulate: 0, rate: 0 },
  { min: 18200, max: 37000, accumulate: 0, rate: 0.19 },
  { min: 37000, max: 90000, accumulate: 3572, rate: 0.325 },
  { min: 90000, max: 120000, accumulate: 20797, rate: 0.37 },
  { min: 120000, max: 180000, accumulate: 22311, rate: 0.39 },
  { min: 180000, max: Number.POSITIVE_INFINITY, accumulate: 54097, rate: 0.45 },
];

const calculateTax = (salary, taxTable)  => {
  const result = taxTable.find((row) => salary > row.min && salary < row.max);

  const { accumulate, rate, min } = result;
  const tax  = (salary - min) * rate + accumulate;

  return tax;
}

calculateTax(150000, TAX_TABLE_2021);
calculateTax(150000, TAX_TABLE_2020);
calculateTax(150000, TAX_TABLE_2018);
```
