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
// 获取
```