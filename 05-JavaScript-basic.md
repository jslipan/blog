# 5-js基础教程

## 一、函数的实参集合-arguments

> arguments: arguments叫做内置的实参集合，这个对象里面包含了函数执行时传递的所有实参（内置：函数天生自带的机制，不管是否设置了形参，也不管你是否传递了实参，arguments一直都存在）。

使用arguments:

```js
function sum2(n, m) {
    console.log(n, m);
    console.log(arguments);

    arguments 它是一个类数组（不是数组，不能直接使用数组中的方法）
   即使设置形参变量，形参该是什么还是什么，但是 arguments 存储的是所有传进来的实参，所以 arguments 被称为 实参集合
   我们发现它有索引，有 length，可以用 for 循环遍历
    {
     0: 1,
     1: 2,
     2: 5,
     3: 7,
     4: 8
     length: 5,
     callee: 存储的当前函数本身 arguments.callee == sum2 -> true
    }
}

sum2(1, 2, 5, 7, 8);
```

**ES不定参数**
- ES6中提供了一个功能和arguments的功能相似的功能————————不定参数

```js
function sum(...arg) {
    //...叫做展开运算符
    // arg是一个形参变量
    console.log(arg);  //arg是一个数组
}
sum(1, 2, 4, 5, 6);
```

**arguments和不定参数的不同**
- arguments是函数天生自带的属性不需要声明，而不定参数需要声明
- arguments是类数组，而不定参数是数组

任意数求和：
思路：
1. 既然是任意数，那么肯定使用函数的arguments
2. arguments里面存储着所有的实参，我们需要把这些实参一个一个的取出来（遍历），然后加给一个基础值上
3. 把结果return出去

```js
function sum3 () {
    // 1，设立初始值
    var total = 0;

    //2. 遍历
    for (var i = 0; i < arguments.length; ++i) {
        var item = arguments[i];
        total += item;
    }

    return total;
}

var result = sum3(1, 2, 4, 5);
console.log(result);
```

升级版：为了提高代码的健壮性，我们累加的时候需要判断一下我们传进来的实参是不是一个数字，如果不是一个数字，我们先给它转成数字，然后再看转换后是不是有效数字，如果是再加，如果不是就不加了

```js
function sum4() {
    var total = 0;
    for (var i = 0; i < arguments.length; ++i) {
        var item = Number(arguments[i]);
        if(!isNaN(item)) {
            total += item;
        }
    }
    return total;
}
console.log(sum4(10, '20', 'a'));   //30
```

## 二、函数表达式

- 函数分类：
  1. 实名函数：有函数名的
  2. 匿名函数：没有函数名的
     1. 函数表达式：把函数当作赋值给变量或者元素对象的事件属性
     2. 自执行函数：创建和执行一起完成

- 函数表达式
  - 把函数当作一个值赋值给变量或者对象的属性

```js
var fn = function() {
    console.log("函数表达式");
};
fn();   //fn 是一个变量名，它代表的也是一个函数

赋值给元素对象的事件属性：
oBox.onclick = function() {};

普通对象的属性值：

var obj = {
    getName: function () {
        console.log('jslipan');
    }
}
obj.getName();  //因为obj.getName是一个函数，因此也可以执行
```

2. 自执行函数：函数的定义和声明都放在一起了

```js
(function (i) {
    第一部分是函数定义
    console.log("hello");
})(10);   


以下都是自执行函数
~function (i) {
    console.log(i);
}(10);

+function (i) {
    console.log(i);
}(10);

!function (i) {
    console.log(i);
}(10);
```

## 三、函数递归
> 函数：分为定义部分和执行部分

函数递归（recursion）：在函数内部，调用函数自身，达到重复某一行为的目的。

```js
function fib(n) {
    return n > 2 ? n : fib(n-1) + fib(n-2);
}
```
> 注意：递归和for循环一样，在使用时要考虑好递归的终止条件，不然就会造成死循环，导致栈内存溢出（stackoverflow)

## 四、数组常用方法

1. 转换方法：在数组中，有3个转换方法：toString()、toLocaleString()和vauleOf()。
   1. 当调用toString()时，数组中的每个元素都会转换为字符串(调用元素的toString()方法),null和undefined比较特殊，会转换为空字符串，当所有元素都是字符串后，在用逗号衔接；
   2. toLocaleString()的功能和toString相同，只是会使用本地化的分隔符，并且每个元素都会调用自己的toLocaleString()
   3. valueOf()会返回调用此方法的数字，也就是其自身，它还有另外一个名字：原始数组

```js
var arr1 = [1,2,3,4,5]
arr1.toString();  //"1,2,3,4,5"
arr1.toLocaleString();  //"1,2,3,4,5"
arr1.valueOf();  //[1,2,3,4,5]
//带null和undefined的数组
var arr2 = [1, null, undefined, 4, 5]
arr2.toString();  //"1,,,4,5"
arr2.toLocaleString(); //"1,,,4,5"
arr2.vauleOf(); //[1,null,undefined,4,5]
```

2. 栈方法

```js
var arr = ["j", "s", "l"].result;
result = arr.push("i", "P");
console.log(result);  //5
console.log(arr);  //["j","s","l","i","p"]

result = arr.pop();
console.log(result); //"p"
console.log(arr);  //["j","s","l","i"]
```