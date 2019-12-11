#记录一些前端思考

## web性能优化

- 压缩源码和图片
- 选择合适的图片格式
- 合并静态资源            包括CSS、JS和小图片，减少HTTP请求
- 开启服务器端的Gzip压缩   这对文本资源非常有效，对图片资源则没有那么大的压缩比率吧
- 使用CDN   一些公开库使用第三方提供的静态资源地址（比如jQuery、normalize.css）一方面增加并发下载量，另一方面能够和其他网站共享缓存
- 延长静态资源缓存时间
- 把CSS放在页面头部，把JS放在页面底部

JS文件源代码可以采用混淆压缩的方式，CSS文件源代码进行普通压缩，JPG图片可以根据具体质量来压缩为50%到70%，PNG可以使用一些开源压缩软件来压缩，比如24色变成8色、去掉一些PNG格式信息等。

如果图片颜色数较多就使用JPG格式，如果图片颜色数较少就使用PNG格式，如果能够通过服务器端判断浏览器支持WebP，那么就使用WebP格式和SVG格式。

## js

实现去除字符串首尾空白字符的函数trim （注：不使用String.prototype.trim）

```js
function Trim(str){
    return str.replace(/(^\s*)|(\s*$)/g,"");
}
```

在 resize, scroll 事件处理中，由于事件触发频率很高，如果在回调中有 DOM 操作等比较耗性能的逻辑，很容易导致卡顿或者浏览器崩溃，而实际需求往往并不需要执行那么频繁。现需要一个函数 throttle (节流)，对于任意的函数 fn, 都可以进行节流操作 fn1 = throttle(fn, delay), 节流后生成的函数，以 delay 为周期，每个周期内仅能执行一次。以减少函数的执行频率。请写出 throttle 的函数实现

```js
var throttle = function(func, delay) {
    var timer = null;
    return function() {
        var context = this;
        var args = arguments;
        if(!timer){
            timer = setTimeout(function(){
                func.apply(context, args);
                timer = null;
            }, delay);
        }
    }
}
function handle() {
    console.log(Math.random());
}
window.addEventListener('scroll',throttle(handle,1000));
```
