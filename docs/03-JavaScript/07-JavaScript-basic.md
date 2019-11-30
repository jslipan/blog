# 7-js基础教程

## 一、Date类型

### 1.js中获取日期的时间

```js
var date = new Date();
console.log(date);

console.log(typeof date);
```

### 2.Date实例方法

```js
var year = date.getFullYear();
console.log(year);

var month = date.getMonth();
console.log(month);

var today = date.getDate();
console.log(today);

var hour = date.getHours();
console.log(hour);

var min = date.getMinutes();
console.log(min);

var sec = date.getSeconds();
console.log(sec);

var mills = date.getMilliseconds();
console.log(mills);

var timeStamp = date.getTime();
console.log(timeStamp);
```

### Date格式化时间

> 时间字符串转时间对象：Date的另一个作用可以把时间格式化的字符串转换为时间对象，转换成时间格式对象后就可以调用getFullYear等方法

```js
var str = '2019-11-30 23:16:12';
var date2 = new Date(str);
console.log(date2);
console.log(typeof date2);
```

## 二、定时器

js中的定时器分为两种：
1. window.setTimeout()设置一个时间间隔，等到了这个时间间隔执行一次
2. window.setInterval()每隔时间间隔执行一次

### 设置定时

```js
var timer1 = setTimeout(function () {
    console.log('3s到了')；
}, 3000);


var timer2 = setIneterval(function () {
    console.log('一个2s的中断')；
},2000);
```

### 清理定时器：停止定时器的办法就是清理定时器

```js
clearTimeout(timer1);

clearInterval(timer2);
```

## 倒计时案例

完成一个定时器功能，当到达目标时间后，显示00:00:00

```html
<!DOCTYPE html>
<html>
<head>
    <meta charset="UTF-8">
    <title>title</title>
    <style>
        #timeBox {
            margin: 20px auto;
            height: 100px;
            width: 200px;
            line-height: 100px;
            font-size: 16px;
            text-align: center;
        }
    </style>
</head>
<body>
    <div id="timeBox"></div>
    <script src="js/time.js"></script>
</body>
</html>
```

```js
var timeBox = document.getElementById('timeBox');

function timeCounter() {
    var curDate = new Date();

    var targetDate = new Date('2019-11-30 23:33:15');

    var curStamp =  curDate.getTime();
    var targetSpamp = targetDate.getTime();
    var stampSpan = targetStamp - curStamp;
    if (stampSpan <=0) {
        timeBox.innerHTML = `00:00:00`;
        clearInterval(timerId);
        return;
    }

    var hMs = hour * 1000 * 60 * 60;
    var mins = Math.floor((stampSpan - hMs) / (1000 * 60));

    var minMs = mins * 1000 * 60;
    var secs = Math.floor((stampSpan - hMs - minsMs) / 1000);

    hour = hour < 10 ? `0${hour}` : hour;
    mins = mins < 10 ? `0${mins}` : mins;
    secs = secs < 10 ? `0${secs}` : secs;
    timeBox.innerHTML = `${hour}:${mins}:${secs}`
}

timeCounter();

var timeId = setInterval(timeCounter, 1000);
```