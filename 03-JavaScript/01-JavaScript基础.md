# 1-js基础教程

## js引入方式
- 行内式：通过向html元素行内添加一些js代码，如给div绑定点击事件
```html
<div onclick="alert('只是js代码')">这是一个div</div>
```

- 内嵌式：在html文档中写一个script标签，把我们的js写在script标签内
```html
<script>
    alert('这是内嵌js代码')
</script>
```

- 外链式: 在html文档中写一个script标签，并且设置src属性，src属性值引用一个js文件资源,而js代码写在js文件中
> 使用外链式引入js文件时，script标签里面不能再写js代码了，即便写了也不会执行。
```html
<script src="js/jslipan.js"></script>
```
无论是内嵌式还是外链式，都建议把script标签写在body结束标签的前面。


## 一、浅谈前端发展史

第一阶段： C/S (client server)  -->  B/S (browser server) 网页制作<br>
技术栈： PhotoShop、Html、CSS

第二阶段：从静态到动态，从后端到前端 前端开发工程师<br>
前后端分离：<br>
后端：完成数据的分析和业务逻辑的编写（包括API接口编写）<br>
前端：网页制作、JS交互效果、数据的交互和绑定<br>
技术栈：JavaScript、 Ajax、 jQuery...<br>
第三阶段：从前端到全端（PC端到移动端）<br>
技术栈：H5、CSS3、响应式布局开发，Zepto、Hybrid、wechat-miniprogram...

第四阶段：从全端到全栈<br>
全栈开发：前后端都可以开发(严格意义讲，一种语言完成前后端开发)<br>
技术栈： Node（基于js编程语言开发服务器端程序）、Express/Koa...


## 二、关于浏览器的内核和引擎

|浏览器 | 内核|
|:-------------:|:-------------:|
|IE|trident |
|chrome /Opera|blink  |
|firefox|gecko|
|Safari|webkit|

w3c：万维网联盟组织，用来制定web标准的机构（组织）<br>
开发者按照规范编写代码，浏览器开发商也会开发一套按照规范把代码渲染成页面的东西（这个东西就是内核或者引擎）

浏览器内核的作用：按照一定的规范，把代码基于GPU（显卡）绘制出对应的图形和页面等；

为啥会出现浏览兼容：<br>
1.部分浏览器会提前开发一些更好的功能，后期这些功能会被收录到W3C规范中，但是在收录之前，会存在一定的兼容性<br>
2.各个浏览器厂商，为了突出自己的独特性，用其他方法实现W3C规范中的功能


## 三、JavaScript

js: 轻量级的客户端脚本编程语言

1. 编程语言<br>
html + CSS 是标记语言<br>
编程语言是具备一定逻辑的，拥有自己的编程思想（面向对象oop、面向过程编程）

- 面向对象
    - C++
    - JAVA
    - PHP
    - C#
    - JS
    - ...

- 面向过程
    - C

2.目前的JS已经不是客户端语言了，基于NODE可以做服务器端程序，所以JS是全栈编程语言

3.学习JS，我们学习它的几个部分组成
- ECMAScript(ES):  js的核心语法
- DOM：Document Obeject Model 文档对象模型，提供各种API（属性和方法）让JS可以获取或者操作页面中的HTML元素（DOM和元素）
- BOM：Browser Object Model浏览器对象模型，提供各种API让js可以操作浏览器


## 四、ECMAScript

它是JS的语法规范，JS中的变量、数据类型、语法规范、操作语句，设计模式等等都是ES规范的；

值得注意的是js的注释方式：注释是一项备注内容，给人看得，代码执行时会忽略注释内容/

- 单行注释：//两个单斜线
- 多行注释：/* 多行注释内容写在两个星号之间 */


## 五、变量（variable）

它不是具体的值，只是一个用来存储具体值的容器或者代名词，因为它存储的值可以改变，所以称为变量。

基于ES语法规范，在JS中创建变量有以下方式：

- var （ES3）
- function （ES3） 创建函数（函数名也是变量，只不过存储值时函数类型而已）
- let (ES6)  声明变量
- const (ES6)  创建常量(常量就是恒定不变的值，如光速就是常量)
- import (ES6) 基于ES6的模块规范导出需要的信息
- class （ES6） 基于ES6创建 类

创建变量，命名的时候要遵循的一些规范

- 严格区分大小写
- 遵循驼峰命名法：按照数字、字母、下划线或者$来命名（数字不能作为开头）,命名的时候基于英文单词拼接成一个名字（第一个单词字母小写，其余每一个有意义单词的首字母都大写）
- 不能使用关键字和保留字：在js中有特殊含义的叫做关键字，未来都可能成为关键字的叫做保留字


## 六、数据类型

数据类型时一门语言进行生产的材料，JS中包含的值有一下这些类型：

- 基本类型
    - 数字 number
    - 字符串 string
    - 布尔值 boolean
    - null
    - undefined
    - Symbol 表示一个唯一值（ES6新增）

- 引用数据类型：
    - 对象 object
        - 普通对象
        - 数组对象
        - 正则对象
        - 日期对象
        - ...
    - 函数function


## 七、JS代码运行及常用输出方式

- alert方法（函数）：在浏览器中通过弹窗的方式输出（浏览器提示框）
- console.log方法：在浏览器控制台输出日志。console是浏览器的开发者工具的一个页卡（在浏览器中按下F12）
- innerHTML/innerText属性： 修改元素中的HTML或者文本；

```js
var box = document.getElementById('box'); // => 在document（整个HTML文档中）下面查找 id 为 box 的元素。

// 语法：元素对象.innerHTML/innerText = '想要显示的内容'; 【想要显示的内容必须是一个字符串类型的值】
box.innerHTML = '<h1>js基础课程第一周</h1>';
box.innerText = '<h1>js基础课程第一周</h1>';

// box.innerHTML/box.innerText = '字符串' 读作：将 box 的 innerHTML 或 innerText 修改为 '字符串'

// => 我们发现同样是包在字符串里面的内容，通过 innerHTML 的方式浏览器会将<h1>识别成 HTML 内容；但是 innerText 不能识别，而是你字符串里面写什么，页面就输出什么；
```

## 八、有效数字检测、数据类型转换、数据类型检测

### 有效数字检测

1.有效数字检测 isNaN() 方法；非有效数字：NaN(not a number)

isNaN(需要检测的值)：检测当前是否是一个有效数字，如果是一个有效数字，isNaN执行后就会得到一个 false，否则 isNaN 执行后得到一个 true；（我们得到的这个 false 或者 true 称为 isNaN 函数的返回值【就“结果”的意思】）

```js
var num = 12;
var result1 = isNaN(12); // -> 检测 num 变量存储的值是否为非有效数字，12是数字，所以 isNaN 执行后得到一个 false；
var result2 = isNaN('13'); // -> false
var result3 = isNaN('盼盼'); // -> true 因为汉字不是数字
var result4 = isNaN(false); // -> false
var result5 = isNaN(null); // -> false;
var result6 = isNaN(undefined); // -> true
var result7 = isNaN({name: '盼盼加油'}); // -> true
var result8 = isNaN([12, 23]); // -> true
var result9 = isNaN([12]); // -> false
var result10 = isNaN(/^$/); // -> true
var result11 = isNaN(function () {}); // -> true
```

思考：为啥小括号里的不是数字也能得到结果？这是isNaN的检测机制：

1.首先验证当前要检测的值是否为数字类型的，如果不是，浏览器会默认的把值转换为数字类型

```
把非数字类型的值转换为数字：
- 其他基本类型转换为数字：内部隐式调用Number方法

Number(需要转换的值); 是强制转换
[字符串转数字]：如果字符串里面都是数字，那么返回这个数字，如果有非数字的因素会返回NaN.

Number('13') // -> 13
Number('13px') // NaN 字符串中 px 不是数字
Number('13.5') // 13.5 可以识别小数点

[布尔值转数字]
Number(true); // -> 1
Number(false); // -> 0

[null、undefined转数字]
Number(null); // 0
Number(undefined); // NaN

- 引用数据类型转数字：先调用引用数据类型值的 toString 方法将引用数据类型转化为字符串，然后再将字符串转换为数字。

[对象转数字]
Number({}) // NaN; 其内部机制：({}).toString() -> '[object Object]' -> Number('[object Object]') -> NaN

[数组转数字]
Number([12, 23]) // NaN; 内部机制：[12, 23].toString() -> '12, 23' -> Number('12, 23') -> NaN

[正则]
Number(/^\d$/) // NaN; 内部机制：/^\d$/.toString() -> '/^\d$/' -> Number('/^\d$/') -> NaN
```

2、当前检测的值已经是数字类型，是有效数字就得到一个 false，不是就会得到一个 true；（在数字类型中只有 NaN 不是有效数字，其余的都是有效数字）
```
Number(1); // false 
Number(NaN); // true
```

3、NaN 的比较

NaN == NaN // 返回 false；（ == 是比较运算符，一个等号是赋值）
这是因为什么呢？因为 NaN 只是表示非数字，字符串 'a' 是非数字，'张三'也是非数字。但是 a 和 张三不相等。

```js
if (Number(num) == NaN) {
    // if 是 js 中用来做判断的语言结构，小括号里表示条件，如果条件成立就执行花括号里面的代码
    alert('盼盼加油呀');
}

// 上面花括号里面的代码永远不会执行，因为 Number 方法得到的结果只有两种情况，要么是数字，要么是 NaN。如果得到一个数字，数字和 NaN 不相等，如果是 NaN，NaN 和 NaN 也不相等。
```

### 数据类型转换（parseInt、parseFloat方法）

> 作用和 Number 方法相似，都是把非数字类型值转换为数字，区别在于 Number 方法是强制转换，即要求被转字符串中必须都是数字，如果不满足这一条件直接得到 NaN，而 parseInt 和 parseFloat 则是非强制转换。

> parseInt：把一个字符串中的整数解析出来<br>
parseFloat：把一个字符串中整数和小数包含小数点都解析出来

```js
parseInt('13.5') // 13
parseFloat('13.5') // 13.5
parseInt('width: 13.5px'); // NaN
parseFloat('width: 13.5px'); // NaN
```
***注意***：无论是 parseInt 还是 parseFloat 都是从字符串的最左边开始查找有效数字，直到遇到第一个非有效数字字符就停止查找，如果第一个就不是有效数字，那么直接回返回 NaN，并且停止查找。

### 数据类型检测：
检测数据类型一共有四种方式：
- typeof
- instanceof
- constructor
- Object.prototype.toString.call()

语法：typeof被检测的值 返回被检测值的数据类型：

```js
console.log(typeof 1); //number
console.log(typeof 'jslipan'); //string
console.log(typeof null); //object
console.log(typeof true); //boolean
console.log(typeof undefined); //undefined
console.log(typeof {}); //object
console.log(typeof []); //object
console.log(typeof /^); //object

//思考？typeof运算符的返回值是个什么数据类型？
var result = typeof 1;
console.log(typeof result); //string

//面试题
console.log(typeof typeof 1); //string

var res = typeof 1;
console.log(res);    //number
console.log(typeof res);  //string
console.log(typeof typeof 1);  //string

//typeof 运算符的返回值是字符串类型的，所以 typeof 1 返回 'number'，这个 number 事实上是字符串；所以在 typeof typeof 1 返回 string
```
>typeof 是有局限性的，检测基本数据类型时，typeof 检测 null 会返回 object，因为 null 是空对象指针。同时，typeof 检测引用数据类型时，不能具体区分是哪一种对象数据类型（对象、数组、正则等）只会统一返回object。