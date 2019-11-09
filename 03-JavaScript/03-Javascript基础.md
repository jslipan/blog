# 3-js基础教程

## 一、逻辑运算符 || 和 &&

### 1、|| 表示或者，两者中一个为true,就返回true

```js
if (0 || 1) {
    console.log('true');
}
if (0 || false) {
    console.log('false');
}
if (true || 0) {
    console.log(true);
}
```
### 2 &&是并且，两个值中必须两个都是true，才返回true

```js
if (0 && 1) {
    console.log(1, '0 && 1')
}
if (0 && false) {
  console.log(2, '0 && false')
}
if (true && 0) {
  console.log(3, 'true && 0');
}
```
###  3. || 和 && 也是有返回值的

- ||如果第一个为true就返回第一个，如果第一个不为true就返回第二个
  
```js
var r1 = 1 || 0;
console.log(r1);
var r2 = 0 || false;
```

- && 如果第一个为true返回第二个，如果第一个为false返回第一个

```js
var r3 = 1 && 0;
var r4 = false && 0;
console.log(r3);
console.log(r4);
```

## 二、==和===的区别

### == 在比较时等号左右两侧数据类型不同时会先转成相同数据类型，再比较

**== 是相对比较； === 是绝对比较**

1. 字符串 == 数字 ；字符串转换成数字
```js
console.log(1 == '1'); // true
```
2. 布尔值 == 数字; 布尔值转成数字
```js
console.log(1 == true); // true;
```
3. 布尔值 == 字符串; 布尔值转数字，字符串也转成数字，然后进行比较；
```js
console.log(false == '0'); // true
```
4. null == undefined // true, null 和 undefined 和其他数据类型比较都是false
5. 对象 == 对象; 比较的是空间地址，地址相同返回true
```js
console.log({} == {}); // false
```
6. 对象 == 字符串; 对象转成字符串，然后和字符串比较
```js
console.log({} == '[object Object]'); // true
```
7. 对象 == 布尔值；对象先转成字符串，再转数字，布尔值也转成数字，在比较这两个数字
```js
console.log({} == true);  //false
console.log([] == false); //true
```
8. 对象 == 数字；对象先转成字符串，然后再转成数字
```js 
console.log({} == 1); // false
console.log([] == 0); // true
```
9. 特殊：NaN 和 NaN 永远不相等
```js
console.log(NaN == NaN); // NaN 和 NaN 永远不相等
```

## 三、for循环

> for 循环 (for loop) 语句：按照一定的规律，重复去做某一件事情，此时就需要使用循环语句.

```js
var ary = [1, 2, 3, 4, 5, 6, 7, 8, 9, 10, 11, 12];

/* [
   0: 1,
   1: 2,
   2: 3,
   ...
   11: 12
   length: 12 // length属性的值表示数组有多少项
 ]
*/

// 把数组里面的每一项都输出出来：

console.log(ary[0]);
console.log(ary[1]);
console.log(ary[2]);
console.log(ary[3]);
console.log(ary[4]);
console.log(ary[5]);
console.log(ary[6]);
console.log(ary[7]);
console.log(ary[8]);
console.log(ary[9]);
console.log(ary[10]);
console.log(ary[11]);

// 改进
for (var i = 0; i < ary.length; i++) {

  // 第一次循环: i = 0  i < 12 所以 ary[i] 是 ary[0]
  // 第二次循环: i = 1  i < 12 所以 ary[i] 是 ary[1]
  // ...
  // i = 12 i < 12 => false 不再执行循环体，循环结束，
  console.log(ary[i]);
}
console.log(i); // 在for的小括号里声明的变量可以在外面使用
```

### for 循环语法

1. 定义初始值 var i = 0
2. 设定循环成立的条件 i < ary.length（如果条件成立执行循环，不成立则结束循环）
3. 条件成立会执行循环体中的内容（循环体就是花括号中的代码）
4. 执行累加 i++

var i = 0; 和i++ 可以不放到括号里，但是你写在括号里的这个变量和写在外面是一样的，在循环里i++更改的就是外面声明的这个i；

```js
var k = 0;
for (;k < 5;) {
  console.log(k);
  k++;
}
console.log(k); // 在外面的k也被更改了，已经变成了5
```

### 倒着输出一个数组

- 把i的初始值设置为ary.length - 1，然后条件是 i >=0 ; i--;
```js
var ary = [12, 23, 34];
for (var i = ary.length - 1; i >= 0; i--) {
  console.log(ary[i]);
}
```

### 输入数组中的奇偶项

```js
// 输出数组中的奇数项
// 偶数：能够被2整除的数字叫做偶数（整除：被除数除以余数商是整数且余数为0）
// 奇数：不能被2整除的数字

for (var j = 0; j < ary.length; j++) {
  if (j % 2 === 0) {
    // % 是取模运算符 ，就是取余数
    // 0 % 2 余数是0
    // 1 % 2 余数是1
    // 3 % 2 余数是1
    // 4 % 2 余数是0
    console.log(ary[j]);
  }
}
```

### 理解 break和 continue

- continue 跳出某一轮的循环，继续后面的循环

```js
for (var i = 0; i < 10; i++) {
	if (i === 5) {
		continue; // 跳出i=5的那一次循环。结束本轮循环（循环体中的continue后面的代码将不再执行，继续执行下一轮循环）
	}
	console.log(i)
}
```

- break 结束整个循环

```js 
for (var i = 0; i < 10; i++) {
	if (i === 5) {
		break; // 结束i=5及以后所有的循环。break是强制结束整个循环，不做任何处理，同时循环体中的break后面的代码也不会执行了
	}
	console.log(i)
}
```


## 四、for in 循环

> for in 循环是专门用来遍历对象的，可以把对象里面的属性一个一个的遍历出来。
注意：for in只能遍历对象的可枚举属性。一般浏览器默认添加的都是不可枚举的属性。例如__proto__

```js
var obj = {
  name: '珠峰',
  age: 10
};

for (var k in obj) {
  // k 代表每次遍历时的属性名
  console.log('k ', k);
  console.log('obj[k]', obj[k]);
}
```

## 五、获取DOM对象

> DOM对象：我们通过 js 的相关和 html 方法获取到的 html 文档中的元素

1. document.getElementById()

通过 ID 获取页面中的元素对象 getElementById()方法

> 语法：document.getElementById('idbox');<br>
参数：元素id， 'box'就是参数<br>
返回值（函数执行过后的结果）：如果获取到，就是获取到的 DOM 元素对象，如果获取不到就是 null；

- 解析：
  - document 是根据 ID 查找的上下文，document 代表的是整个 HTML 文档（就是 html 标签自身及包裹的所有内容），getElementById 的上下文只能是 document
  - 通过getElementById获取的元素是一个对象数据类型的值（里面包含了很多的内置属性，这些属性都是描述这个对象的）

- DOM对象的属性：
  - className: 存储的是字符串类型（string），代表的是当前元素的样式类名
  - id: 存储的是一个字符串类型（string），当前元素的ID名
  - innerHTML: 字符串 存储的当前元素中所有的内容（包含标签，并且标签以字符串形式存在）
  - onclick: 鼠标点击事件 元素的点击事件属性，基于这个属性，我们可以给元素绑定点击事件
  - onmouseover: 鼠标划过事件
  - onmouseout: 鼠标划出事件
  - style 存储当前元素的所有的【行内样式】值（获取的都只是写在标签上的行内样式，写在样式表的样式，无法通过这个属性获取到）

```js
var box = document.getElementById('box');
console.log(box);
```

2. getElementsByTagName()

通过标签名获取【元素对象集合】

- 解析
  - 语法： context.getElementsByTagName('标签名')
  - 参数： 标签名字符串
  - 返回值： 从context下面查到的指定标签名DOM元素对象组成的集合；这个集合中的每一项都是DOM元素对象；
  - context不是写死的，是我们指定的上下文，你想获取那个元素下面的指定标签元素集合，哪个元素就是上下文

```js
var listContainer = document.getElementById('container');
var liList = listContainer.getElementByTagName('li');

console.log(liList);
console.log(liList[0]);
console.log(liList[1]);
console.log(liList[2]);
liList[0].style.backgroundColor = 'red';
```

- 解析：
  - 获取的是一个元素结合（HTML Collecion），元素集合也是一个对象数据类型的，结合和数组非常类似（数组作为索引，length代表长度），但它不是数组，而是叫做类数组。
  - 和数组操作一样，通过[索引]的方式可以取出类数组的每一项。liList[0]获取的是第一项。
  - liList.length 表示集合中li的数量
  - 集合中的每一项都是元素对象，我们可以获取或者修改它的元素属性，如style、innerHTML、innerText
  - 结合索引，length可以通过for循环把集合中的每一项获取出来

> ? 思考 ? DOM对象也是对象，那么我们可以向操作普通对象那样操作它吗？比如说添加一个属性，或者修改某个属性？
DOM对象也是对象，我们也可以向操作对象的方式一样操作DOM对象

```js
for (var i = 0; i < liList.length; i++) {
	var cur = liList[i];
	cur.myIndex = i; // 通过自定义属性存储这个元素在元素集合中的索引
	console.log(cur);
}
```


## 六、隔行变色
```html
<!DOCTYPE html>
<html lang="en">
<head>
	<meta charset="UTF-8">
	<title>珠峰-隔行变色</title>
	<style>
		* {
			margin: 0;
			padding: 0;
		}
		ul, li {
			list-style: none;
		}
		.li-wrapper {
			margin: 30px auto;
			border: 1px solid #00b38a;
			width: 500px;
		}

		.li-wrapper li {
			height: 50px;
			line-height: 50px;
			text-align: center;
			border-bottom: 1px darkblue dashed;
		}
	</style>
</head>
<body>
<ul id="liWrapper" class="li-wrapper">
	<li>1item1</li>
	<li>2item2</li>
	<li>3item3</li>
	<li>4item4</li>
	<li>5item5</li>
	<li>6item6</li>
	<li>7item7</li>
	<li>8item8</li>
	<li>9item9</li>
	<li>10item10</li>
</ul>

<script src="js/6-changeColor.js"></script>
</body>
</html>
```
```js
// 1. => 获取元素 liWrapper 下的 li

var liWrapper = document.getElementById('liWrapper');
var liList = liWrapper.getElementsByTagName('li');
for (let i = 0; i < liList.length; i++) {
	// 循环遍历元素对象，然后取出每一项
	if (i % 2 === 0) {
		// 如果是 i 是偶数
		liList[i].style.backgroundColor = 'pink';
	} else {
		// 否则 i 是奇数
		liList[i].style.backgroundColor = 'yellow';
	}
}
```