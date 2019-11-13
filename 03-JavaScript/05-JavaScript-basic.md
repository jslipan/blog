# 5-js 基础教程

## 一、函数的实参集合-arguments

> arguments: arguments 叫做内置的实参集合，这个对象里面包含了函数执行时传递的所有实参（内置：函数天生自带的机制，不管是否设置了形参，也不管你是否传递了实参，arguments 一直都存在）。

使用 arguments:

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

**ES 不定参数**

- ES6 中提供了一个功能和 arguments 的功能相似的功能————————不定参数

```js
function sum(...arg) {
  //...叫做展开运算符
  // arg是一个形参变量
  console.log(arg); //arg是一个数组
}
sum(1, 2, 4, 5, 6);
```

**arguments 和不定参数的不同**

- arguments 是函数天生自带的属性不需要声明，而不定参数需要声明
- arguments 是类数组，而不定参数是数组

任意数求和：
思路：

1. 既然是任意数，那么肯定使用函数的 arguments
2. arguments 里面存储着所有的实参，我们需要把这些实参一个一个的取出来（遍历），然后加给一个基础值上
3. 把结果 return 出去

```js
function sum3() {
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
    if (!isNaN(item)) {
      total += item;
    }
  }
  return total;
}
console.log(sum4(10, "20", "a")); //30
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
(function(i) {
  第一部分是函数定义;
  console.log("hello");
})(10);

以下都是自执行函数;
~(function(i) {
  console.log(i);
})(10);

+(function(i) {
  console.log(i);
})(10);

!(function(i) {
  console.log(i);
})(10);
```

## 三、函数递归

> 函数：分为定义部分和执行部分

函数递归（recursion）：在函数内部，调用函数自身，达到重复某一行为的目的。

```js
function fib(n) {
  return n > 2 ? n : fib(n - 1) + fib(n - 2);
}
```

> 注意：递归和 for 循环一样，在使用时要考虑好递归的终止条件，不然就会造成死循环，导致栈内存溢出（stackoverflow)

## 四、数组常用方法

1. 转换方法：在数组中，有 3 个转换方法：toString()、toLocaleString()和 vauleOf()。
   1. 当调用 toString()时，数组中的每个元素都会转换为字符串(调用元素的 toString()方法),null 和 undefined 比较特殊，会转换为空字符串，当所有元素都是字符串后，在用逗号衔接；
   2. toLocaleString()的功能和 toString 相同，只是会使用本地化的分隔符，并且每个元素都会调用自己的 toLocaleString()
   3. valueOf()会返回调用此方法的数字，也就是其自身，它还有另外一个名字：原始数组

```js
var arr1 = [1, 2, 3, 4, 5];
arr1.toString(); //"1,2,3,4,5"
arr1.toLocaleString(); //"1,2,3,4,5"
arr1.valueOf(); //[1,2,3,4,5]
//带null和undefined的数组
var arr2 = [1, null, undefined, 4, 5];
arr2.toString(); //"1,,,4,5"
arr2.toLocaleString(); //"1,,,4,5"
arr2.vauleOf(); //[1,null,undefined,4,5]
```

2. 栈方法: 栈是一种数据结构，它的特点是后进先出（Last In First Out，LIFO），使用数组中的方法 push()和 pop(),可以让数组的表现像栈一样。注意，这两个方法都会改变原始数组。

```js
var arr = ["j", "s", "l"].result;
result = arr.push("i", "P");
console.log(result); //5
console.log(arr); //["j","s","l","i","p"]

result = arr.pop();
console.log(result); //"p"
console.log(arr); //["j","s","l","i"]
```

3. 队列方法：队列也是一种数据结构，它的特点是先进先出(First In First Out, FIFO)。使用数组中的方法 shift()和 pop(),可以让数组的表现像队列一样。而使用方法 unshift()和 pop(),可以从反方向模拟队列。注意，shift()和 unshift()也会改变原始数组。

```js
var arr = ["j", "s", "l", "p"].result;
result = arr.shift();
console.log(result); //"j"
console.log(arr); //["s", "l", "p"]

result = arr.unshift("a", "j");
console.log(result); //5
console.log(arr); //["a", "j", "s", "l", "p"]
```

4. 排序方法： 在数组有两个用于排序的方法：revese()和 sort()。revese()的功能比较单一，只能用于数组的简单反转。revese()会作用于原始的数据，也就是直接修改原始数组。

```js
var array1 = ['one', 'two', 'three'];
console.log('array1: ', array1);
// expected output: Array ['one', 'two', 'three']
var reversed = array1.reverse();
console.log('reversed: ', reversed);
// expected output: Array ['three', 'two', 'one']
/* Careful: reverse is destructive. It also changes
the original array */
console.log('array1: ', array1);
// expected output: Array ['three', 'two', 'one']

const a = [1, 2, 3];
console.log(a); //[1,2,3]
a.revese();
console.log(a); //[3,2,1]

const a = {0:1, 1:2, 2:3, length:3};
console.log(a); // {0:1, 1:2, 2:3, length:3};
Array.prototype.reverse.call(a);  /same syntax for using apply()
console.log(a); // {0: 3, 1: 2, 2: 1, length: 3}
```

当 sort()没有参数是，元素将按照字符编码的顺序进行排序。当给 sort()传入一个比较函数时，能够按指定的排序规则进行排序。比较函数有两个参数：a 和 b，也就是数组的两个元素，根据函数的返回值

- 如果`compareFunction(a,b)`小于 0，那么 a 会被排列到 b 之前；
- 如果`compareFunction(a,b)`等于 0，a 和 b 的相对位置不变；
- 如果`compareFunction(a,b)`大于 0，a 会被移到 b 的后面；

```js
var months = ["March", "Jan", "Feb", "Dec"];
months.sort();
console.log(months); // ["Dec", "Feb", "Jan", "March"]

var array1 = [1, 30, 4, 21, 100000];
arrray1.sort();
console.log(array1); // [1,100000, 21, 30, 4];

function compare(a, b) {
  if (a < b) {
    return -1;
  }
  if (a > b) {
    return 1;
  }
  // a must be equal to b
  return 0;
}

//比较数字而非字符串,数组升序排列
function compareNubers(a, b) {
  return a - b;
}

//sort方法,升序
var numbers = [4, 2, 5, 1, 3];
numbers.sort(function(a, b) {
  return a - b;
});

//也可以
numbers.sort((a, b) => a - b);

//对象按照某个属性排序
var items = [
  { name: "Edward", value: 21 },
  { name: "Sharpe", value: 37 },
  { name: "And", value: 45 },
  { name: "The", value: -12 },
  { name: "Magnetic" },
  { name: "Zeros", value: 37 }
];
//sort by value
items.sort(function(a, b) {
  return a.value - b.value;
});

// sort by name
items.sort(function(a, b) {
  var nameA = a.name.topUpperCase(); // ignore upper and lowercase
  var nameB = b.name.topUpperCase();
  if (nameA < nameB) {
    return -1;
  }
  if (nameA > nameB) {
    return 1;
  }
  // names must be equal
  return 0;
});
```

5. 迭代方法：ES5 定义了 5 个新的迭代方法，他们都有 2 个参数，第一个参数是回调函数，第二个参数是一个可选值，表示执行回调函数时使用的 this 对象（即调用上下文）。回调函数包含 3 个参数；当前元素、元素索引和原始数组。
   | 方法 | 描述 | 返回值 |
   | --------- | --------------------------------------------------------- | --------- |
   | forEach() | 对数组中的每个元素执行一次回调函数，该方法没有返回值 | undefined |
   | every() | 只要有一次回调函数的结果为假，就返回 false,否则返回 true | 布尔值 |
   | some() | 只要有一次回调函数的结果为真，就返回 true，否则返回 false | 布尔值 |
   | map() | 用回调函数的结果（即返回值）组成一个新数组 | 新数组 |
   | filter() | 过滤掉回调函数结果为假值的元素，剩余的元素组成一个新数组 | 新数组 |

```js
var arr = [1, 2, 3, 4, 5],
  result;
result = arr.forEach(function(vaule, index, array) {
  return value;
});
console.log(result); //undefined

result = arr.every(function(value, index, array) {
  return value == 2;
});
console.log(result); //false

result = arr.some(function(value, index, array) {
  return value == 2;
});
console.log(result); //true

result = arr.map(function(value, index, array) {
  return value * 2;
});
console.log(result); //[2,4,6,8,10]

result = arr.filter(function(value, index, array) {
  return value > 2;
});
console.log(result); //[3,4,5]
console.log(result); //[1,2,3,4,5]
```

6. 其他方法

|   方法    |                       描述                       |           返回值           |
| :-------: | :----------------------------------------------: | :------------------------: |
| indexOf() |               从左向右查找匹配元素               |      元素的索引值或-1      |
| reduce()  |               从左向右计算数组元素               |         计算出的值         |
|  join()   |        用指定的分隔符将每个元素衔接在一起        |       衔接后的字符串       |
| concat()  |        将多个数组或值与原始数组合并在一起        |       合并后的新数组       |
|  slice()  |            提取两个指定位置之间的元素            |   由提取元素组成的新数组   |
| splice()  | 删除任意数量的元素，并可用指定的值替换被删除的值 | 由删除掉的元素组成的新数组 |

```js
var array = [2, 5, 9];
array.indexOf(2);     // 0
array.indexOf(7);     // -1
array.indexOf(9, 2);  // 2
array.indexOf(2, -1); // -1
array.indexOf(2, -3); // 0

// 找出指定元素出现的所有位置
var indices = [];
var array = ['a', 'b', 'a', 'c', 'a', 'd'];
var element = 'a';
var idx = array.indexOf(element);
while (idx != -1) {
  indices.push(idx);
  idx = array.indexOf(element, idx + 1);
}
console.log(indices); //[0,2,4]

// 判断一个元素是否在数组里，不在则更新数组
function updateVegetablesCollection (veggies, veggie) {
  if (veggies.indexOf(veggie) === -1) {
    veggies.push(veggie);
    console.log('New vegeis collection is :' + veggies);
  }
  else if (veggies.indexOf(veggie) > -1) {
    console.log(veggie + 'already exists in the veggies collection');
  }
}

var veggies = ['potato', 'tomato', 'chillies', 'green-papper'];

// New veggies collection is : potato, tomato, chillies, green-papper, spinach
updateVegetablesCollection(veggies, 'spinach');
//spinach already exists in the veggies collections
updateVegetablesCollection(veggies, 'spinach');
```

```js
[0, 1, 2, 3, 4].reduce(function(accumulator, currentValue, currentIndex, array){
  return accumulator + currentValue;
});  //10

const array1 = [1, 2, 3, 4];
const reducer = (accumulator, currentValue) => accumulator + currentValue;

// 1 + 2 + 3 + 4
console.log(array1.reduce(reducer));
// expected output: 10

// 5 + 1 + 2 + 3 + 4
console.log(array1.reduce(reducer, 5));
// expected output: 15
```

```js
var elements = ['Fire', 'Air', 'Water'];

console.log(elements.join());
// expected output: "Fire,Air,Water"

console.log(elements.join(''));
// expected output: "FireAirWater"

console.log(elements.join('-'));
// expected output: "Fire-Air-Water"

var a = ['Wind', 'Rain', 'Fire'];
var myVar1 = a.join();      // myVar1的值变为"Wind,Rain,Fire"
var myVar2 = a.join(', ');  // myVar2的值变为"Wind, Rain, Fire"
var myVar3 = a.join(' + '); // myVar3的值变为"Wind + Rain + Fire"
var myVar4 = a.join('');    // myVar4的值变为"WindRainFire"

function f(a, b, c) {
  var s = Array.prototype.join.call(arguments);
  console.log(s); // '1,a,true'
}
f(1, 'a', true);
```

```js
const array1 = ['a', 'b', 'c'];
const array2 = ['d', 'e', 'f'];

console.log(array1.concat(array2));
// expected output: Array ["a", "b", "c", "d", "e", "f"]
```

```js
var fruits = ['Banana', 'Orange', 'Lemon', 'Apple', 'Mango'];
var citrus = fruits.slice(1, 3);

// fruits contains ['Banana', 'Orange', 'Lemon', 'Apple', 'Mango']
// citrus contains ['Orange','Lemon']
```

```js
var months = ['Jan', 'March', 'April', 'June'];
months.splice(1, 0, 'Feb');
// inserts at index 1
console.log(months);
// expected output: Array ['Jan', 'Feb', 'March', 'April', 'June']

months.splice(4, 1, 'May');
// replaces 1 element at index 4
console.log(months);
// expected output: Array ['Jan', 'Feb', 'March', 'April', 'May']

var myFish = ["angel", "clown", "mandarin", "sturgeon"];
var removed = myFish.splice(2, 0, "drum");
// 运算后的 myFish: ["angel", "clown", "drum", "mandarin", "sturgeon"]
// 被删除的元素: [], 没有元素被删除

var myFish = ['angel', 'clown', 'mandarin', 'sturgeon'];
var removed = myFish.splice(2, 0, 'drum', 'guitar');
// 运算后的 myFish: ["angel", "clown", "drum", "guitar", "mandarin", "sturgeon"]
// 被删除的元素: [], 没有元素被删除

var myFish = ['angel', 'clown', 'drum', 'mandarin', 'sturgeon'];
var removed = myFish.splice(3, 1);
// 运算后的 myFish: ["angel", "clown", "drum", "sturgeon"]
// 被删除的元素: ["mandarin"]

var myFish = ['angel', 'clown', 'drum', 'sturgeon'];
var removed = myFish.splice(2, 1, "trumpet");
// 运算后的 myFish: ["angel", "clown", "trumpet", "sturgeon"]
// 被删除的元素: ["drum"]

var myFish = ['angel', 'clown', 'trumpet', 'sturgeon'];
var removed = myFish.splice(0, 2, 'parrot', 'anemone', 'blue');
// 运算后的 myFish: ["parrot", "anemone", "blue", "trumpet", "sturgeon"]
// 被删除的元素: ["angel", "clown"]

var myFish = ['parrot', 'anemone', 'blue', 'trumpet', 'sturgeon'];
var removed = myFish.splice(myFish.length - 3, 2);
// 运算后的 myFish: ["parrot", "anemone", "sturgeon"]
// 被删除的元素: ["blue", "trumpet"]

var myFish = ['angel', 'clown', 'mandarin', 'sturgeon'];
var removed = myFish.splice(-2, 1);
// 运算后的 myFish: ["angel", "clown", "sturgeon"]
// 被删除的元素: ["mandarin"]

var myFish = ['angel', 'clown', 'mandarin', 'sturgeon'];
var removed = myFish.splice(2);
// 运算后的 myFish: ["angel", "clown"]
// 被删除的元素: ["mandarin", "sturgeon"]
```

### 练习

```js
var sports = ["soccer", "baseball"];
var toatal = sports.push("football", "swimming");
console.log(sports); //["soccer", "baseball", "football", "swimming"]
console.log(total); //4

var vegetables = ["parsnip", "potato"];
var moreVegs = ["celery", "beetroot"];
//将第二个数组融合进第一个数组
//相当于 vegetables.push("celery", "beetroot");
Array.prototype.push.apply(vegetables, moreVegs);
console.log(vegetables); // ['parsnip', 'potato', 'celery', 'beetroot']
```

```js
let myFish = ["angel", "clown", "mandarin", "surgeon"];
let popped = myFish.pop();
console.log(myFish); // ["angel", "clown", "mandarin"]
console.log(popped); // surgeon
```

```js
var names = ["Andrew", "Edward", "Paul", "Chris", "John"];
while ((i = names.shift()) !== undefined) {
  console.log(i); // Andrew, Edward, Paul, Chris, John
}

let arr = [1, 2];

arr.unshift(0); // result of the call is 3, which is the new array length
// arr is [0, 1, 2]

arr.unshift(-2, -1); // the new array length is 5
// arr is [-2, -1, 0, 1, 2]

arr.unshift([-4, -3]); // the new array length is 6
// arr is [[-4, -3], -2, -1, 0, 1, 2]

arr.unshift([-7, -6], [-5]); // the new array length is 8
// arr is [ [-7, -6], [-5], [-4, -3], -2, -1, 0, 1, 2 ]
```
