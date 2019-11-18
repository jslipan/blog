# 4-js基础教程

## 一、函数

> 函数：一个方法，基于方法可以实现一些功能

> 函数诞生的目的在于“封装”：把实现功能的代码封装到一个函数中，以后再想实现这个功能，不需要重新编写代码，只需要执行函数即可，这样降低了页面中的冗余代码，提高了代码的重复利用率（“低耦合高内聚”）

```javasctipt
function 函数名([形参]){
    函数体：实现功能的JS代码
}
函数名([实参]);
```

```javascript
//=>创建函数
function fn() {
    var n = Math.PI;
    n *= 100;
    n = n.toFixed(2);
    console.log(n);
}

//=>执行函数
fn();
fn();
fn();
...
```

## 函数的运作机制：
【创建函数】
1. 函数也是引用类型值，首先开辟一个新的堆内存（16进制地址）
2. 把函数体中实现功能的代码“当做字符串”存储到堆内存中
3. 把堆内存的引用地址赋值给函数名（变量名）

【执行函数】
目的：把函数体中的JS代码执行，以此实现具体的功能和需求
1. 首先开辟一个新的栈内存（私有作用域），提供JS代码执行赖以生存的环境
2. 把原有在堆内存中存储的“字符串”，拿过来，放到新的栈内存中，变为真正的JS代码，自上而下执行

====

封装一个函数实现一些功能，有时候发现实现功能的原材料不足，需要执行函数的时候传递给我们才可以，此时我们可以给函数设置几个入口，我们把函数的入口称之为：“形参变量”(入口是变量)

```javascript
//=>创建一个函数实现两个数求和
function sum(n,m){
   //=>n/m就是形参入口，也是两个变量
   var total=0;
   total=n+m;
   console.log(total);
}

//=>执行函数
sum(10,20); //=>传递的值是实参(实参是传递给形参变量的具体值) n:10 m:20
sum(10); //=>n:10 m:undefined 设置了形参,执行的时候不传递值,默认值是undefined
sum(10,20,30); //=>n:10 m:20
```

## 函数的参数机制

参数就是函数的入口，当我们在函数中封装一个功能，我们希望我们给他什么，它帮助我们处理啥。配合函数的定义和执行两部分；参数对应着两个部分，也有两部分构成：

- 函数声明阶段：形参，形参是函数内部的变量，它也是用来代表和存储值得；
- 函数执行阶段：实参，实参是给形参赋值的具体值。就是说函数执行时，形参所代表的具体的值。

```js
//求和函数
function sum(a, b) {
    // a, b都是形参
    console.log(a, b);
    var total = 0;
    t0tal = a + b;
    console.log(total);
}

sum(10, 20); // 10 和 20 是实参，当函数执行时，函数的形参 a 本次拿到的值是10，b 本次拿到20；实参的位置和形参是一一对应的。
sum(1); //1是实参，a 本次拿到的是1，另一个没传，如果没传是 b 获取到时默认值 undefined
sum(); //没有实参，此时a, b都是 undefined
sum(4, 5, 6);  //4, 4, 6都是实参， a是4，b是5， 没有接收6
```

## 函数的返回值机制

### 函数返回值机制

> 函数除了我们给他啥，他帮助我们处理啥，还有一个重要的事就是，把处理结果给我们，例如isNaN()，会把函数执行的结果返回给我们。我们写的函数该有这样的功能。

我们这里有一个求和函数，我们希望求和完成后可以拿到求得的两数之和：

```js
function sum(a,b) {
    var total =0;
    total = a + b;
    console.log(total);
}

var result = sum(1,2);
console.log(result);  //undefined
console.log(total);  //Ucaught ReferenceError: ...
```

引发报错的原因：total 是在函数内部声明的变量，这种声明在函数体内部的变量称为私有变量，而私有变量在函数外部是无法访问的，这是由于闭包机制导致的。

> 闭包（closure）：函数会保护函数体内部的变量不被外界所干扰的机制成为闭包；

```js
//修改后的求和函数代码
function sum(a,b) {
    var total = 0;
    total = a + b;
    return total;
}

var result = sum(1,2);
console.log(result);  //3
```

## 函数含返回值的细节问题

1. return用于指定函数返回值，那么 return啥 返回值是啥
2. 如果函数内部没有return或者return后面啥也没有写，那么函数的返回值是undefined
3. return关键字还有一个重要作用————强制结束return后面的代码。（return后面的代码不执行）
4. return永远返回一个值，如果是表达式，return会等着表达式求值完成，然后再把值返回。


**函数是没有重载**

【练习】使用模拟函数重载来编写一个具有如下功能的函数：
1. 如果输入参数大于三个，返回最后一个参数
2. 如果输入参数小于三个且全部为数字，则返回排序后的数组，如果最后一个数奇数则降序排列，反之升序排列
3. 如果输入参数小于三个且包含字符串，则将所有参数强制转化为字符串连接返回。

```js

function myFunc() {
    var arguLen = arguments.length;
    if (arguLen > 3) {              //first case
        return arguments[arguLen - 1];
    }
    else if (arguLen < 3) {
        var numFlag = true;
        var strFlag = false;
        for(var i = 0; i < arguLen; ++i) {
            if(typeof arguments[i] != "number"){
                numFlag = false;
            }
            if(typeof(arguments[i]) === "string"){
                strFlag = true;
                break;
            }
        }
        if (numFlag) {    //second case
            var args = [].slice.call(arguments, 0);  //转成数组
            if (args[arguLen - 1] % 2 == 0) {
                return args.sort(function(a,b){return a-b;});  //升序
            }
            else {
                return args.sort(function(a,b){return b-a;}); //降序
            }
        }
        else if (strFlag){  //third case
            var result = "";
            for (var i = 0; i < arguLen; ++i) {
                result += String(arguments[i]);
            }
            return result;
        }
    }
    return;
}
```

## 二、选项卡
```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Document</title>
    <style>
        * {
            margin: 0;
            padding: 0;
        }
        ul {
            list-style-type: none;
        }
        .clearfix::after {
            display: block;
            visibility: hidden;
            content: "";
            clear: both;
        }
        .tab {
            width: 500px;
            margin: 20px auto;
        }
        .tab .header {
            position: relative;
            top: 1px;
        }
        .tab .header li {
            float: left;
            margin-right: 10px;
            padding: 0px 10px;
            line-height: 35px;
            cursor: pointer;
            border: 1px solid #000;
        }
        .tab .header li.active {
            border-bottom-color: #FFF;
        }
        .tab .content {
            display: none;
            height: 150px;
            line-height: 150px;
            text-align: center;
            border: 1px solid #000;
        }
        .tab .content.active {
            display: block;
        }
    </style>
</head>
<body>
    <div class="tab" id="tab">
            <ul class="header clearfix">
                <li class="active">新闻</li>
                <li>电影</li>
                <li>音乐</li>
            </ul>
            <div class="content active">三胖来华访问</div>
            <div class="content">电影真好看</div>
            <div class="content">电音抖腿神器</div>
    </div>
    <script src="./core.js"></script>
</body>
</html>
```

```js
~function () {
	let tab = document.querySelector('#tab'),
		headerList = tab.querySelectorAll('li'),
		contentList = tab.querySelectorAll('div');
		
	for (let i = 0; i < headerList.length; i++) {
		headerList[i].onclick = function () {
			for(let j = 0; j < headerList.length; j++) {
				headerList[j].className = "";
				contentList[j].className = "content";
			}
			headerList[i].className = "active";
			contentList[i].className = "content active";
		}
	}
}();
```