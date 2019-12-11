
CSS 写的好可以让网页瞬间高大上，但是再高大上的网站如果效率很低也不行，尤其是在近几年「用户体验」这个词烂大街以后。最近在复习CSS，看了很多关于 CSS 如何写的更好的文章，总结一下。

## 权重

CSS 中我个人觉得权重是个很需要掌握的概念。它决定哪一条样式将被应用在元素上，哪一条样式将被覆盖掉。众所周知，CSS 选择器，最基本的有三种：

- id 选择器
- class 选择器
- 标签选择器

还有一种**内联样式**( inline-style )，是指直接在 HTML 代码中添加 CSS 样式。以上四种的权重顺序是：**内联样式（1000）** > **id 选择器（100）** > **class 选择器（10）** > **标签选择器（1）**。括号内分别是它们的**权重值**！。举个栗子：

```HTML
<span style="color : #fff;" id="example" class="demo">栗子</span>
```

```CSS
#example {color: #000;}
```

```CSS
.dome {color: red;}
```

```CSS
span {color: blue;}
```

如果只有第四句来定义样式，则这个`<span>`是蓝色的，如果加上第三条语句，则变成了红色，第四句被覆盖掉了。如果用第二句，则变为黑色，第三句即被覆盖，以此类推如果用内联样式则`<span>`变成白色了。

像我这样的菜鸟刚开始滥用各类选择器，往往会出现想覆盖父元素样式的时候覆盖不了的情况，熟不知**要想覆盖，必须让这条语句的权重值大于父元素**（具体可以参考这篇文章[你应该知道的一些事情——CSS 权重](http://www.w3cplus.com/css/css-specificity-things-you-should-know.html)）。

<!-- more -->

### 尽量不要用 id 选择器

由于 id 选择器权重值过大的原因，我们要尽量少用它（内联样式估计没人会用了吧）。

```HTML
<div id="example" class="parent">
    <span class="son"></span>
</div>
```

如果你使用 id 选择器

```CSS
#example span {background-color: blue;}
```

则再写

```CSS
.son {background-color: red;}
```

就没用了，甚至

```CSS
.parent .son {background-color: red;}
```

都没用。你必须用：

```CSS
#example .son {background-color: red;}
```

才能再改变它的背景色。这样远不如只用一个 class 轻松写意。尤其是#example 下面层级多的话，代码就会越写越长，可见少使用 id，多用 class 才是正道。而且 id 只能用一次，class 可以重复使用。

### 尽量不要多层级的选择器

当 CSS 写到后来，你可能会发现经常有类似这样的一长串代码出现：

```CSS
#example .content .right .tag span {color: blue;}
```

这主要还是因为你没有搞清权重的原因。每次你想为子元素重新定义样式时都要有个权重值大于父元素的一大串选择器。这样的代码不仅你看起来痛苦，浏览器看起来也痛苦（原因可参考这篇文章[【高性能前端 2】高性能 CSS](http://www.alloyteam.com/2012/10/high-performance-css/)）。

所以后代选择器不仅性能低下而且代码很脆弱：HTML 代码和 CSS 代码严重耦合，HTML 代码结构发生变化时，CSS 也得修改，自己改起来都痛苦，更别说万一将来有人来接盘你的代码……你考虑过他的感受么 T_T。还是那句话，用 class，最多两三层选择器就搞定了！

其实还有个终极神器`!importants`。只要在样式语句后面加上这个就能覆盖**之前**和**之后**的一切样式！这意味着你再想把它覆盖是不可能的。当你都逼到用这个神器的时候，说明你的代码实在写的不敢恭维……你一定会有更好的解决方式的，所以尽量不要用`!importants`。

## 精简

精简你的 CSS 代码可以提升你编写的速度，还能让代码看起来整洁、一目了然，节省时间和空间。

### 使用复合语法

尽量使用复合语法：

```CSS
// 糟糕的写法
.someclass {
    background: #000;
    background-image: url(../imgs/carrot.png);
    background-position: bottom;
    background-repeat: repeat-x;
}

// 好的写法
.someclass {
    background: #000 url(../imgs/carrot.png) repeat-x bottom;
}
```

类似的还有`padding`、`margin`、`font`、`border`等。用复合语法可以精简代码，一目了然。

### 减少重复

- 利用 CSS 继承

如果页面中父元素的多个子元素使用相同的样式，那最好把他们相同的样式定义在其父元素上，让它们继承这些 CSS 样式。

```CSS
// 糟糕的写法
.example li {font-family:Georgia, serif;}
.example p {font-family:Georgia, serif;}
.example h1 {font-family:Georgia, serif;}

// 好的写法
.example {font-family:Georgia, serif;}
```

- 利用分组选择器

```CSS
// 糟糕的写法
.someclass {
    color: red;
    background: blue;
    font-size: 16px;
}

.otherclass {
    color: red;
    background: blue;
    font-size: 8px;
}

// 好的写法
.someclass, .otherclass {
    color: red;
    background: blue;
}

.someclass {
    font-size: 16px;
}

.otherclass {
    font-size: 8px;
}
```

### 移除没用的样式

> 移除无匹配的样式，有两个好处：

> 第一，删除无用的样式后可以缩减样式文件的体积，加快资源下载速度；

> 第二，对于浏览器而言，所有的样式规则的都会被解析后索引起来，即使是当前页面无匹配的规则。移除无匹配的规则，减少索引项，加快浏览器查找速度；

## 格式

### 命名很重要

程序猿最讨厌的事已经不是写文档了，而是**命名**。好的命名可以让你「见名思义」，不写注释也可以读懂；坏的命名会让你抓狂，你不得不用 ctrl+F 匹配它们……我还发现很多人都是根据 HTML 代码的结构去命名，如

    #header、 .content、 .left、 .right

等等，这些并没有实际的意义，当 HTML 越来越复杂的时候，或者新人来接手的时候，就会时常摸不着头脑，难以调试和维护。所以我个人觉得应该多用具有实际意义的、可以见名思义的 class 命名。

### 好看一点

代码的易读性和易维护性成正比。

```CSS
// 糟糕的写法
.someclass-a, .someclass-b, .someclass-c, .someclass-d {
 ...
}

// 好的写法
.someclass-a,
.someclass-b,
.someclass-c,
.someclass-d {
 ...
}

// 更好看一点
.someclass {
    background-image:
        linear-gradient(#000, #ccc),
        linear-gradient(#ccc, #ddd);
    box-shadow:
        2px 2px 2px #000,
        1px 4px 1px 1px #ddd inset;
}
```

### 其他

- 注释：程序猿最讨厌的四件事：写注释、写文档、别人不写注释、别人不写文档……
- 单位： 到底是用`px`还是`em` -->[CSS 文字大小单位 PX、EM、PT](http://www.1z1b.com/one-blog-a-week/px-em-pt/)
- 兼容： IE 你到底要闹哪样~`

以下是大牛总结的一些 CSS 技巧：

- [CSS 使用技巧](http://www.ruanyifeng.com/blog/2010/03/css_cookbook.html)
- [CSS3 常用功能的写法](http://www.ruanyifeng.com/blog/2010/03/cross-browser_css3_features.html)
- [CSS 动画简介](http://www.ruanyifeng.com/blog/2014/02/css_transition_and_animation.html)
- [CSS 选择器笔记](http://www.ruanyifeng.com/blog/2009/03/css_selectors.html)

学习 CSS：

- [学习 CSS 布局](http://zh.learnlayout.com/)
- [w3school](http://www.w3school.com.cn/)
- [CSS 禅意花园](http://www.csszengarden.com/tr/chinese/)

手册：

- [CSS 参考手册](http://css.doyoe.com/)

工具：

- [CSS Lint](http://csslint.net/)
- [css_doc](https://github.com/tkadauke/css_doc) 写注释用
- [kss](https://github.com/kneath/kss) 写注释用

---
