## 版本 (Level)

- CSS Level 1
- CSS Level 2(CSS 2.1 规范)
- CSS Level 3
    - Color Module Level 3
    - Selectors Level 3
    - Media Queries
    - Fonts Level 3

**代码风格**
```css
h1 {
    color: red;
    font-size: 14px;
}
```

**使用CSS**
```css
/* 外链 */
<link rel="stylesheet" href="/path/to/style.css">

/* 嵌入 */
<style type="text/css">
    li {margin: 0; list-style: none;}
    p {margin: 1em 0;}
</style>

/* 内联 */
<p style="margin:1em 0">Example Content</p>
```


## 选择器
```css
/* 选择器用来从页面中选择元素，以给他们定义样式 */

/* 匹配所有元素 */
* {
    box-sizing: inherit;
}

/* 标签选择器 */
p {
    margin: 1em 0;
}


/* id选择器 */
<p id="example">Example Content</p>

<style type="text/css">
    #example {
        font-size: 14px;
        line-height: 16px;
        color: red;
    }
</style>


/* 类选择器 */
<p class="warning">text</p>
<p class="warning icon">other text</p>

<style type="text/css">
    .warning {
        color: orange;
    }
    .icon {
        background: url(warn.png) no-repeat 0 0;
    }
</style>


/* 属性选择器 */
<p>
    <label>用户名:</label>
    <input name="username" value="zhao" disabled>
</p>

    <style>
        input[disabled] {
            background: #eee;
            color: #999;
            cursor: not-allowed;
        }
    </style>


<p>
    <label>密码：</label>
    <input type="password" required>
</p>

    <style>
        input[type="password"] {
            border-color:red;
            color: red;
        }
    </style>


<p>
    <input name="height">
</p>
<p>
    <label>体重：</label>
    <input name="weight">
</p>
<p>
    <label>BMI：</label>
    <output for="weight height">22</output>
</p>

    <style>
        [for~="height"] {
            color: red;
        }
    </style>


<p><a href="#top">回到顶部</a></p>
<p><a href="/home">返回首页</a></p>

    <style>
        a[href^="#"] {
            color: red;
        }
    </style>

    <style>
        a[href$=".jpg"] {
            color: red;
        }
    </style>


<i class="icon-user">用户</i>
<i class="icon-wifi">WiFi</i>
<i class="other1 icon-car">汽车</i>
<i class="icon-heart other2">爱心</i>

<style>
    [class^="icon-"], [class*=" icon-"] {
        color: coral;
        font-family: FontAwesome;
        font-style: normal;
        margin-right: 1em;
    }
    .icon-user::before {
        content: "\f007";
    }
    .icon-wifi::before {
        content: "\fleb";
    }
</style>


/* **伪类（pseudo-classes）** */
/* 基于DOM之外的信息去（比如根据用户和网页的交互状态）选择元素 */
a:link
a:visited
a:hover
a:active
a:focus
```

**选择器组合**
- 直接组合 EF
- 后代组合 E F
- 亲子组合 E>F


```css
/* 直接组合 */
<p class="warning">text</p>
p.warning {color: orange;}

/* 组合形式 */
E[foo="bar"]
E.warning
E#myid
#myid.warning
.warning[foo="bar"]


/* 后代组合E F */
/* 后代选择器 */
article p {
    color: coral;
}

/* 亲自选择器 */
article > p {
    color: limegreen;
}
article section h2 {
    border-bottom: 1px dashed #999;
}


/* 同时为一组选择器定义样式 */
body, h1, h2, h3, h4, h5, h6, ul, ol, li {
    margin: 0;
    padding: 0;
}

[type="checkbox"], [type="radio"] {
    box-sizing: border-box;
    padding: 0;
}
```

## 文本样式
```css
font-family
/* 使用逗号分隔的字体名称 */
/* 初始值由浏览器设置决定，可继承 */
```
**字体匹配算法**
1. 浏览器先获取一个系统字体列表
2. 对于元素中每一字符，使用font-family属性及其其他属性进行匹配，如果能匹配就暂时定该字体
3. 如果步骤2没有匹配，选择下一个可选的font-family执行步骤2
4. 如果匹配到一个字体，但是字体中没有该字符，继续对下一个可选的font-family执行步骤2
5. 如果没有匹配到字体，使用浏览器默认字体

**通用字体族**
- serif 衬线体
    - Georgia、宋体
- san-serif 无衬线体
    - Arial、Helvetica、黑体、微软雅黑
- cursive 手写体
    - Caffisch Script、楷体
- fantasy 梦幻字体
    - Comic Sans MS、Papyrus
- monospace 等宽字体
    - Consolas、Courier、中文字体

**font-family使用**
- 英文字体放在中文字体前面
- 最后总是添加通用字体族

**font-size**
- 定义文字的大小，可使用px、百分比、em等做单位
- 取值
    - 绝对值 xx-small | x-small | small | medium | large | x-large | xx-large
    - 相对值 larger | smaller
    - 长度
    - 百分数，相对于父元素计算值
- 初始值为medium(由浏览器设置决定，一般16px),可继承
```css
.slide-page li{
    font-size: 36px;
}
.richtext h4 {
    font-size: 125%;
}
.continue {
    font-size: 0.85em;
}
```

**长度单位em**
- 一般是相对于元素font-size的计算值
- 用在font-size属性上时，时相对于父元素的font-size计算值
```css
<section>
    <h2>字体族</h2>
    <p>Curesive(手写体)字体的字形，作为用于CSS的术语，，一般具有连笔（joining strokes）或者其他除斜体字体的手写特征</p>
    <p>Fantasy字体，用于CSS，主要时修饰性的，但仍然具有字符表现（与不表现字符的Pi或者Picture字体相反）</p>
</section>

<style>
    section {
        font-size: 16px;
    }
    section h2 {
        font-size: 1.5em;
        margin-bottom: 1em;
    }
</style>
```
**font-style**
- 定义文字以斜体还是正常方式显示
- 取值：normal | italic | oblique
- 初始值为normal, 可继承

**font-weight**
- 定义文字的粗细
- 取值： normal | bold | bolder | lighter | 100 | 200 | …… | 900 |
- 初始值为normal, 可继承

100 - Thin
300 - light
400 - normal
500 - medium
700 - bold

**line-height**
- 元素所属的line box 所占高度
- 初始值为normal（具体值由浏览器决定），可继承
- 取值：<长度>|<数字>|<百分比>
- 段落文字一般1.4~1.8

```css
#header {line-height: 48px;}
#content .wrap{line-height: 1.6;}

<section>
    <h1>这是一个标题啊</h1>
    <p>这是正文</p>
</section>
<style>
    section {
        width: 10em;
        font-size: 12px;
        line-height: 1.5em;
    }
    h1 {
        font-size: 30px;
    }
</style>
```

**font缩写**
```css
<h1>This is Title</h1>
<p>This is Paragraph</p>

<style>
h1 {
    /* 斜体 粗细 大小/行高 字体族 */
    font: bold 14px/1.7 Helvetica, sans-serif;
}
p {
    font: 14px serif;
}
</style>


/* Web Fonts */
<h1>I wanted the storm, so beautiful yet terrific</h1>

<style>
@font-face {
    font-family: "Lovster";
    font-style: normal;
    font-weight: 400;
    src: local('Lobster'),
        local('Lobster-Regular'),
        url(//lib.baomitu.com/fonts/lobster/lobster-v18-latin-regular.woff2)format('woff2');
        url(//lib.baomitu.com/fonts/lobster/lobster-v18-latin-regular.woff2)format('woff');
        h1 {
            font-family: 'Lobster', cursive;
        }
}
</style>


/* 中文Web Fonts */
<h1>中文也可以使用网络字体啊</h1>

<style>
@font-face {
    font-family: "jslipan";
    font-style: normal;
    font-weight: 400;
    src: local('jslipan'),
    url(http://s6.qhres.com/static/0csaabdf.woff)format('woff');
}
h1 {
    font-family: "jslipan", cursive;
}
</style>
```

**链接**
- Google Fonts
- Baomitu CDN
- Font Spider

**text-align**
- 定义文本在容器内的对齐方式
- 取值：left | right | center | justify
- 初始值由HTML的dir属性决定，可继承

**letter-spacing**
**word-spacing**
- 指定字符之间的间距
- 取值: normal | <length>
- 初始值为normal,可继承

```css
h1 {letter-spacing: 0.2em;}
```

**text-indent**
- 指定文本缩进
- 取值: normal | <length> | <percentage>
- 初始值为0, 可继承

```css
<style>
    p {text-indent: 2em;}
</style>
```

**text-decoration**
- 定义了文本的一些装饰效果，比如下划线、删除线等
- 初始值为none, 可继承
- 其他值：underline | line-through | overline

**white-space**
- 指定空白符如何处理
- 取值: normal | nowrap | pre

**word-break**
- 指定是否允许在单词中间换行
- 取值: normal | break-all | break-word

```css
<p>nothin change my love for your web developmenet fagasdgsdsadg aaadfddddddddggg</p>
<style>
    p {
        width: 10em;
        word-break: normal;
    }
</style>
```

## CSS理论
**Positioning Schemes**
- Normal Flow
- Float
- Absolute Positioning

**常规流**
- 除根元素、浮动元素和绝对定位元素外，其他元素都在常规流之内(in-flow)
- 而根元素、浮动和绝对定位的元素会脱离常规流（out of flow）
- 常规流中的盒子，属于块级格式化上下文或行级格式化上下问

**块级格式化上下文（Block Formatting Context）**
- 盒子在容器（包含块）内从上到下一个接一个地放置
- 两个兄弟盒之间的竖直距离由margin属性决定
- 同一个BFC内垂直margin会合并
- 盒子的左外边缘挨着容器（包含块）的左边

**行级格式化上下文（inline Formatting Context）**
- 盒子一个接一个水平放置
- 盒之间的水平margin, border和padding都有效
- 同一行的盒子所在的矩形区域叫行盒（Line Box）
- 当一个行盒房不下上下文内所有盒子时，会被分到多个垂直堆叠的行盒里
- 行盒内的水平分布由text-align属性决定
- 如果一个行级块无法分割（单词、line-block）,该元素会被作为一个整体决定分布在哪一个行盒

**float**
- 浮动元素从常规流中脱离，被漂浮在容器（包含块）左边或右边
- 浮动盒会一直漂到其他外边缘挨到容器边缘或另外的浮动盒
- 浮动元素不会影响其后面的流内块级盒
- 但是浮动元素后面的行级盒子会变短以避开浮动元素

position
- static, 非定位，默认值
- relative, 相对定位（相对自己）
- absolute，绝对定位，相对非static祖先元素定位
- fixed, 相对于视口绝对定位

relative
- 在常规流里面布局
- 相对于自己本应该在的位置进行偏移
- 使用top、left、bottom、right 设置偏移长度
- 流内其他元素当它没有偏移一样布局
