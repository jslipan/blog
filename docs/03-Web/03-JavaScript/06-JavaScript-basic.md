# 6-js基础教程

## 字符串的属性和方法

| 属性和方法 | 描述 |
|：---：|：---：|
|length| 字符串长度 |
|charAt()| 返回指定位置的字符串|
|charCodeAt()| 返回指定位置的字符串编码 |
|concat()|将一个或多个字符串连接，组成一个新字符串|
|indexOf()|返回给定值在字符串中首次出现的位置，未找到则返回-1|
|lastIndexOf() | 返回给定值在字符串中末次出现的位置，未找到则返回-1|
|match()|使用正则表达式执行匹配|
|replace()|替换匹配正则表达式的子串|
|search()|搜索匹配正则表达式的子串|
|split()|用指定的分割符，将字符串分割为数组|
|截取字符串| sliec()、substr()、substring() |
|toLowerCase()|将字符串都变为小写|
|toUpperCase()|将字符串都变成大写|


## Date 类型

1. js中获取日期时间

```js
var today = new Date();
var today = new Date('December 14, 2019 17:51:00');
var today = new Date('2019-11-14T17:51:00');
var today = new Date(2019, 11, 14);
var today = new Date(2019, 11, 14, 17, 51, 0);
```
2. 计算经过的时间

```js
//使用date对象
var start = Date.now();

//调用一个消耗一定时间的方法
doSomethingForAlongTime();
var end = Date.now();
var elapsed = end - start;  //以毫秒计的运行时长
```
```js
//使用内建的创建方法
var start = new Date();

//调用一个消耗一定时间的方法
var end = new Date();
var elapsed = end.getTime() - start.getTime();  //运行时间的毫秒值
```
```js
// to test a function and get back its return
function printElapsedTime (fTest) {
    var nStartTime = Date.now(),
        vReturn = fTest(),
        nEndTime = Date.now();
    alert("Elapsed time: " + String(nEndTime - nStartTime) + " milliseconds");
    return vReturn;
}
yourFunctionReturn = printElapsedTime(yourFunction);
```
```js
// 获取自Unix起始时间以来经过的秒数
var seconds = Math.floor(Date.now() / 1000);
```

## 二、 数组去重

### 双for循环去重

思路：
1. 依次拿出数组中的每一项（排除最后一项；最后一项后面没有需要比较的内容）
2. 和当前取出向后面的每一项依次比较
3. 如果发现有重复的，我们把找打的这个重复项在原有数组中删除(ary.splice)

```js
var ary = [1, 3, 3, 3, 5, 4];

for (var i = 0; i < ary.length - 1; i++) {
    var item = ary[i];
    for (var k = i + 1; k < ary.length; k++) {
        if (item === ary[k]) {
            ary.splice(k, 1);
            k--;
        }
    }
}
```

### 对象法去重

> 原理：基于对象的属性名不能重复，我们可以实现高性能的数组去重

步骤：
1. 创建一个空对象
2. 遍历数组中的每一项，把数组每一项存储的值，当做对象的属性名和属性值存储起来
3. 在存储起来做一个判断，判断当前对象中是否存在这个属性，如果不存在就是undefined,说明这个数组项在之前没有出现过，没有出现就说明没有重复，然后直接存储在对象里。如果在之前出现过，此时值就不是undefined, 此时就不要存储到对象中，同事删除这一项


```js
var obj = {};

for (var i = 0; i < ary.length; i++) {
    var item = ary[i];
    if (obj[item] !== undefined) {
        ary[i] = ary[ary.length - 1];
        ary.length--;
        i--;
    } else {
        obj[item] = item;
    }
}

```