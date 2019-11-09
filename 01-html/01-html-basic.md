# web标准
> 浏览器的内核不同，他们工作原理、解析肯定不同，显示就会有差别。

##  Web 标准构成

 Web标准不是某一个标准，而是由W3C和其他标准化组织制定的一系列标准的集合。

主要包括结构（Structure）、表现（Presentation）和行为（Behavior）三个方面。

```
结构标准：结构用于对网页元素进行整理和分类，咱们主要学的是HTML。 最重要
表现标准：表现用于设置网页元素的版式、颜色、大小等外观样式，主要指的是CSS。
行为标准：行为是指网页模型的定义及交互的编写，咱们主要学的是 Javascript
```

## 浏览器内核

```
浏览器内核又可以分成两部分：渲染引擎(layout engineer 或者 Rendering Engine)和 JS 引擎。
渲染引擎 它负责取得网页的内容（HTML、XML、图像等等）、整理讯息（例如加入 CSS 等），以及计算网页的显示方式，然后会输出至显示器或打印机。浏览器的内核的不同对于网页的语法解释会有不同，所以渲染的效果也不相同。
JS 引擎 则是解析 Javascript 语言，执行 javascript语言来实现网页的动态效果。

最开始渲染引擎和 JS 引擎并没有区分的很明确，后来 JS 引擎越来越独立，内核就倾向于只指渲染引擎。有一个网页标准计划小组制作了一个 ACID 来测试引擎的兼容性和性能。内核的种类很多，如加上没什么人使用的非商业的免费内核，可能会有10多种，但是常见的浏览器内核可以分这四种：Trident、Gecko、Blink、Webkit。
```

（1）Trident(IE内核) 

国内很多的双核浏览器的其中一核便是 Trident，美其名曰 "兼容模式"。

代表： IE、傲游、世界之窗浏览器、Avant、腾讯TT、猎豹安全浏览器、360极速浏览器、百度浏览器等。

Window10 发布后，IE 将其内置浏览器命名为 Edge，Edge 最显著的特点就是新内核 EdgeHTML。

（2）Gecko(firefox) 

Gecko(Firefox 内核)： Mozilla FireFox(火狐浏览器) 采用该内核，Gecko 的特点是代码完全公开，因此，其可开发程度很高，全世界的程序员都可以为其编写代码，增加功能。 可惜这几年已经没落了， 比如 打开速度慢、升级频繁、猪一样的队友flash、神一样的对手chrome。

（3） webkit(Safari)  

 Safari 是苹果公司开发的浏览器，所用浏览器内核的名称是大名鼎鼎的 WebKit。

 现在很多人错误地把 webkit 叫做 chrome内核（即使 chrome内核已经是 blink 了），苹果感觉像被别人抢了媳妇，都哭晕再厕所里面了。

 代表浏览器：傲游浏览器3、 Apple Safari (Win/Mac/iPhone/iPad)、Symbian手机浏览器、Android 默认浏览器，

（4） Chromium/Blink(chrome) 

   在 Chromium 项目中研发 Blink 渲染引擎（即浏览器核心），内置于 Chrome 浏览器之中。Blink 其实是 WebKit 的分支。 

​     大部分国产浏览器最新版都采用Blink内核。二次开发

（5） Presto(Opera) 

  Presto（已经废弃） 是挪威产浏览器 opera 的 "前任" 内核，为何说是 "前任"，因为最新的 opera 浏览器早已将之抛弃从而投入到了谷歌怀抱了。 

  ## Web 标准的好处

*1*、让Web的发展前景更广阔 
*2*、内容能被更广泛的设备访问
*3*、更容易被搜寻引擎搜索
*4*、降低网站流量费用
*5*、使网站更易于维护
*6*、提高页面浏览速度

# html

## Html History
HTML 是什么
- HyperText Markup Langguage
- 使用标签来描述页面的 **内容** 和  **结构**

HTML的产生
- 1989年， Tim Berners-Lee
- 共享文档需要
- 还发明了浏览器、服务器和HTTP

HTML 1.0，1991
HTML 2.0，1994，IETF
HTML 3.2，1997， W3C
- Netscape引入私有标签
- HTML 3.0失败
- W3C接管HTML标准化

HTML 4.01，1998
- 样式与内容分离，CSS支持
- Doctype


## DocType作用
- 指定HTML页面使用的标准和版本
- 浏览器根据doctype决定使用哪种渲染模式

渲染模式
- Quriks Mode 怪异模式
- Almost Standard Mode 准标准模式
- Standard Mode 标准模式


XHTML 1.0，2000
- 用XML语法重新定义HTML
- 语法严格要求

XHTML 2.0
- 不兼容历史
- 去除样式类标签
- 去除img、a
- 彻底修改Form
- 开发者不欢迎、浏览器不支持

HTML 5
- 2004年，WHATWG继续发展HTML
- 2008年，W3C HTML发布草案

HTML 5 设计思想
- 兼容已有内容
- 避免不必要的复杂性
- 解决现实的问题
- 优雅降级
- 尊重事实标准
- 用户》开发者》浏览器厂商》标准制定者》理论玩美

HTML5 中的变化
- doctype、meta
- 新增语义化标签和属性
- 去掉纯展示性标签
- canvas、video、audio、离线、本地存储、拖拽等

语法
- 标签不区分大小写，推荐小写
- 空标签可以不闭合，比如input、meta
- 属性不必引号，推荐双引号
- 某些属性值可以省略，比如required、 readonly

## HTML Element
Flow流式元素
Metadate元数据元素
Interactive可交互元素
Phrasing段落元素
Heading标题元素
Sectioning章节元素


HTML中的文本标签
p h1~h6 hr pre

```html
<h1>购物清单</h1>
<ul>
    <li>1个西瓜</li>
    <li>2瓶矿泉水</li>
    <li>1盒酸奶</li>
</ul>

<h1>世界电影票房</h1>
<ol>
    <li>我不是药神</li>
    <li>海王</li>
</ol>

<h3>霸王别姬</h3>
<dl>
    <dt>导演：</dt>
    <dd>陈凯歌</dd>
    <dd>主演：</dd>
    <dd>张国荣</dd>
    <dd>张丰毅</dd>
    <dd>巩俐</dd>
    <dt>上映日期：</dt>
    <dd>1993-01-01</dd>
</dl>
```

```html
<blackquote cite="http:/t.cn">
    <p>js是最好的语言,我是一个长段落，长啊长长长长长长长长长长长长长长长长长</p>
</blockquote>
<p>--老子说得</p>

<p>我最喜欢的一本书是<cite>西游记</cite></p>

<p>在<cite>第一章</cite>，我们讲过<q>字符串是不可变量</q>。</p>
```

```html
<p><code>const</code>声明创建一个只读的常量。</p>

<pre><code>
    const add = (a, b) => a + b;
    const mutiply = (a, b) => a * b;
</code></pre>
```

```html
<figure>
    <img src="https://picture.baidu.com" alt="字体排印表">
    <figcaption>威廉-卡丝隆制作的第一张字体排印样表</figcaption>
</figure>

<figure>
    <figcaption>定义一个函数</figcaption>
    <pre><code>
        function add(x, y) {
            var total = x + y;
            return total;
        }
    </code></pre>
</figure>
```

```html
<article>
    <header>
        <h1>字体排印学</h1>
        <p>作者：XXX</p>
    </header>
    <section>
        <h2>语言及其范围</h2>
        <p>在当代，字体排印学的相关研究和介绍中...</p>
        <p>以字体排印为核心的图像中，通常使用四项基本原则</p>
    </section>
    <section>
        <h2>可读性和易用性</h2>
        <p>可读性和易读性经常被混淆。可读性通常用。。。。</p>
        <p>与之相对，易读性描述的是排印文本阅读是的。。。</p>
    </section>
    <footer>
        <h2>参考衔接</h2>
        <nav>
            <ul>
                <li><a href="">衬线字体</a></li>
                <li><a href="">字体设计</a></li>
            </ul>
        </nav>
    </footer>
</article>
```
## 我该用那个标签?
[HTML5 Element Flowchart](http://html5doctor.com/downloads/h5d-sectioning-flowchart.pdf)

**强调**
- strong：重要性、严重性和紧急性
- em: 从一句话中突出某个词语
- b: 将词语从视觉和其他部分区分，比如一篇论文重要的关键词
- i: 换一种语调去说一句话时，比如其他语言翻译，对话中的旁白

**定义与缩写**
```html
<p><dfn>HTML时HyperText Markup Language的简称，一种用户创建网页的标记语言</dfn></p>

<p><abbr tittle="HyperText Markup Language">HTML</abbr>标准由<abbr tittle="World Wide Web Consortium">W3C</abbr>制定和修改</p>
```

**代码**
```html
<p>使用HTML5写页面，第一行要写<code>&lt;!DOCTYPE html&gt;</code></p>

<P>能量<var>E</var>等于质量<var>m</var>乘以光速<var>c</var>的平方</P>

<p>按下<kbd>F12</kbd>打开浏览器开发者工具。</p>

<p>检查当前工作仓库状态：</p>
<pre><code>jslipan@localhost:camp$ <kbd>git status</kbd>
<samp>On branch master Your branch is up-to-date with 'origin/master'.</samp>
</code></pre>
```

```html
<p>E = MC<sup>2</sup></p>
<p>CO<sub>2</sub></p>

<p>但是，该属性<del>目前还没有</del></p>
<ins>更新：最新版本的Safari 6.1已经支持。</ins>

<p><del>原价：299元</del> <ins>双11特价：188元</ins></p>
```

**mark**
- 和用户当前行为相关的突出，比如在搜素结果中匹配到的词
- 一部分内容需要在后面引用时

**换行控制（尽量避免）**
```html
<p>JavaScript<br>高级程序语言设计</p>
<p>https://zh.wikipedia.org/saf45234tttrert/ggsgg</p>
<p>https://zhwikipedia.org/<wbr>saf4523<wbr>4tttr<wbr>ert/ggsgg</p>
```

**div和span**
实在找不到更符合语义的标签时使用

**实体（Entity）字符**
```html
&amp; &nbsp; &gt; &copy; &yen; &#9775;
```

**链接**
|https://|www.example.com|post/fe.html|?print=1&color=no|#heading
|---|---|---|---|---|
|Scheme|Host|Path|Query|Hash|

```html
<a href="www.w3.org" target="_self">W3C (当前窗口)</a>
<a href="www.w3.org" target="_blank">W3C (新窗口)</a>
<a href="www.w3.org" target="abc">W3C (abc)</a>
<a href="www.example.com" target="abc">Example (abc)</a>
```

**图片**
```html
<img src="/path/to/img.jpg" alt="替代文字" width="300" height="200">

<figure>
    <img src="/path/to/img.jpg" alt="替代文字">
    <figcaption>图片说明</figcaption>
</figure>
```

指定图片宽高
- 不指定高宽：原图大小显示
- 指定宽度：按比例缩放到指定宽度
- 指定高度：按比例缩放到指定高度
- 指定高宽：强制指定高宽显示

常用图片格式
- jpg  照片
- png  色彩较少时使用  png24可以半透明
- gif  无法半透明  可以多帧做动画
- webp

**表格**
```html
<table border="1">
    <caption>浏览器及其引擎</caption>
    <colgroup>
        <col class="browser">
        <col class="engine" span="2">
    </colgroup>
    <thead>
        <tr>
            <th>浏览器</th>
            <th>渲染引擎</th>
            <th>JavaScript 引擎</th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <td>Chrome</td>
            <td>Blink</td>
            <td>V8</td>
        </tr>
        <tr>
            <td>Opera</td>
            <td>Blink</td>
            <td>V8</td>
        </tr>
        <tr>
            <td>Firefox</td>
            <td>Gecko</td>
            <td>SpiderMonkey</td>
        </tr>
        <tr>
            <td>Edge</td>
            <td>EdgeHTML</td>
            <td>Chakra</td>
        </tr>
    </tbody>
</table>
```

## 表单
```html
<form action="/echo" method="GET">
    <p>用户名：<input type="text" name="username" placeholder="请输入用户名" autofocus></p>
    <p>密码：<input type="password" name="password"></p>
    <p><button type="submit">登陆</button></p>
</form>

<textarea cols="40" rows="8"></textarea>
```
GET返回的数据是一致，数据可能在服务器，运营商上缓存。数据放在url上提交
POST数据编码放在HTTP的body里面，

**URL 编码**
- &nbsp;=> %20 (空格)
- ！=> %21
- " => %22
- \# => %23
- $ => %24
- % => %25
```js
decodeURLComponent()
```

**输入验证**
```html
<form action="/echo">
    <p>
        <input required minlength="2" maxlength="10" placeholder="2-10位">
    </p>
    <p>
        <input pattern="1\d{10}" placeholder="输入手机号">
    </p>
    <p>
        <button type="submit">提交</button>
    </p>
</form>
```

**type**
```html
<form action="/echo">
    <P>
        Search:<input type="search">
    </P>
    <p>
        Email:<input type="email">
    </p>
    <p>
        URL:<input type="url">
    </p>
</form>
```

**novalidate**
```html
<form action="/echo" novalidate>
    <p>
        <input required minlength="2" maxlength="10" placeholder="2-10位">
    </p>
    <p>
        <input pattern="1\d{10}" placeholder="输入手机号码">
    </p>
    <p>
        <button type="submit">提交</button>
    </p>
</form>
```

**label**
```html
<form action="/echo">
    <p>你最喜欢什么水果?</p>
    <p>
        <input type="checkbox" name="fruit" value="apple" id="apple">
        <label for="apple">苹果</label>
        <label>
        <input type="checkbox" name="fruit" value="banana">香蕉
        </label>
        <label>
        <input type="checkbox" name="fruit" value="mango">芒果
        </label>
    </p>
    <p>
        <label for="name">请输入你的名字:</label>
    </p>
    <p><input id="name"></p>
    <p><button>提交</button></p>
</form>
```

**select**
```html
    <select name="fruit" multiple size="3">
        <option value="1">苹果</option>
        <option value="2">香蕉</option>
        <option value="3">芒果</option>
        <option value="4">菠萝</option>
        <option value="5">榴莲</option>
        <option value="6">木瓜</option>
    </select>
```

**分组**
```html
<label>目的城市：</label>
<select name="country">
    <optgroup label="美洲">
        <option>多伦多</option>
        <option>温哥华</option>
        <option>旧金山</option>
        <option>洛杉矶</option>
        <option>纽约</option>
        <option>华盛顿</option>
    </optgroup>
    <optgroup label="亚洲">
        <option>北京</option>
        <option>上海</option>
        <option>首尔</option>
        <option>东京</option>
        <option>香港</option>
    </optgroup>
    <optgroup label="欧洲">
        <option>伦敦</option>
        <option>巴黎</option>
        <option>马德里</option>
        <option>柏林</option>
        <option>雅典</option>
    </optgroup>
</select>
```

**hidden**
```html
<form action="/echo">
    <p>你喜欢什么水果?</p>
    <p>
        <input type="checkbox" name="fruit" value="apple"> 苹果
        <input type="checkbox" name="fruit" value="banana" checked> 香蕉
        <input type="checkbox" name="fruit" value="mango"> 芒果
    </p>
    <p><button>提交</button></p>
    <input type="hidden" name="secret" value="1">
</form>
```

**文件选择**
```html
<form action="/echo" method="POST" enctype="multipart/form-data">
    <p>
        <label>你的姓名：</label>
        <input name="fullname">
    </p>
    <p>
        <label>请选择简历：</label>
        <input type="file" name="resume" multiple accept="image/*">
    </p>
    <p><button>提交</button></p>
</form>
```

**date & time**
```html
<form action="/echo">
    <p>date: <input type="date"></p>
    <p>datetime-local: <input type="datetime-local"></p>
    <p>month: <input type="month"></p>
    <p>week: <input type="week"></p>
    <p>time: <input type="time"></p>
</form>
```

**number & range**
```html
<form action="/echo">
    <p>
        <label>身高(m):</label>
        <input type="number" min="0.5" max="2.5" step="0.01" name="height" value="1.7">
    </p>
    <p>
        <label>体重(kg):</label>
        <input type="range" min="10" max="150" step="0.1" name="weight" value="62">
        <output for="weight"></output>
    </p>
    <p>
        <label>BMI:</label>
        <output for="weight height"></output>
    </p>
</form>

<script>
    var form = document.querySelector('form');
    form.addEventListener('input', update);
    update();

    function update() {
        var data = new FormData(form);
        var height = parseFloat(data.get('height'));
        var weight = parseFloat(data.get('weight'));
        document.querySelector('[for="weight"]').value = weight;
        document.querySelector('[for="weight height"]').value = getBMI(height, weight);
    }

    function getBMI(height, weight) {
        return (weight / Math.pow(height, 2)).toFixed(2);
    }
</script>
```

**button**
```html
<form action="/echo">
    <p>你的姓名？</p>
    <p>
        <input type="text" name="fullname" value="abc">
    </p>
    <p>你最喜欢什么水果？</p>
    <p>
        <label><input type="checkbox" name="fruit" value="apple">苹果</label>
        <label><input type="checkbox" name="fruit" value="banana" checked>香蕉</label>
        <label><input type="checkbox" name="fruit" value="mango">芒果</label>
    </p>
    <p>
        <button>不指定type</button>
        <button type="submit">submit</button>
        <button type="button">button</button>
        <button type="reset">reset</button>
    </p>
</form>
```

**回车提交**
```html
<form action="/echo">
    <p>你的姓名</p>
    <p>
        <input type="text" name="fullname" value="abc">
    </p>
    <p>
        <button onclick="alert(1)">不指定type</button>
        <button onclick="alert(2)" type="button">button</button>
    </p>
</form>
```

**控件状态**
```html
<form action="/echo">
    <p>你的姓名？</p>
    <p>
        <input type="text" name="fullname" value="abc" readonly>
    </p>
    <p>你的职业？</p>
    <p>
        <select name="occupation" disabled>
            <option value="1">学生</option>
            <option value="2">工程</option>
            <option value="3">教师</option>
        </select>
    </p>
    <p>
        <button>提交</button>
    </p>
</form>
```

**表单设计**
- 帮助用户不出错
- 尽早提示错误
- 扩大选择/点击区域
- 控件较多时要分组
- 主要动作和次要动作

**全局属性**
**accesskey & tabindex**
```html
<p>
    <input accesskey="i" placeholder="Press Ctrl+Alt+I">
</p>
<p>
    <a href="http://example.com" accesskey="e" tabindex="-1">Press <kbd>Ctrl+Alt+E</kbd></a>
</p>
```

**id, class & style**
- id保证唯一性
- class多用在css
- 指定样式

**contenteditable & spellcheck**
```html
<section contenteditable spellcheck="true">
    <h1>可读性和易读性</h1>
    <p>这是一个测试文本，你可以啊课呀可也可以啊啊可以呃呃暗黑法师</p>
</section>
```

**lang & dir**
```html
<div lang="zh-CH">
    <p>字体排印学的英文<span lang="en">Typography</span></p>

    <p dir="rtl" lang="ar">这里放阿拉伯文字</p>
</div>
```

**title**
```html
<p>My logs show that there was some interest in <abbr tittle="HyperText Transport Protocol">HTTP</abbr> today.</p>
```

**hidden**
```html
<p hidden>你看不见我</p>
```

**无障碍性**
- 或可访问性，Accessibility
- 确保任何人都有办法获取放在网上的媒体内容
- 不让身体、心理或技术上的问题成为获取信息的障碍

**Web开发者应该做的事**
- WCAG(Web Content Accessibility Guidelines)2.0
- ARIA(Accessible Rich Internet Applications)

**ARIA**
```html
<ol role="tablist">
    <li role="tab">
        <a href="#ch1">Chapter 1</a>
    </li>
    <li role="tab">
        <a href="#ch2">Chapter 2</a>
    </li>
</ol>
```

**提升无障碍性**
- 为img提供alt属性
- noscript
- input和label对应
- 图形验证码与语言验证码
- 文字和背景由足够对比度
- 键盘可操作

**语义化**
- HTML中的元素，属性及属性值都拥有某些含义
- 开发者应该遵循语义来编写HTML

**为什么语义化很重要**
- 提升代码可读性、可维护性
- 搜索引擎优化
- 提升无障碍性

**扩展HMTL**
- meta
- data-*
- microdata
- RDFa
- JSON-LD

**meta**
```html
<meta charset="UFU-8">
<!-- 指定HTTP Header -->
<meta http-equiv="Content-Security-Policy" content="script-src 'self'">

<!-- SEO 搜索引擎优化 -->
<meta name="keywords" content="关键词">
<meta name="description" content="页面介绍">

<!-- 移动设备Viewport -->
<meta name="viewport" content="inital-scala=1">

<!-- 关闭iOS电话号码自动识别 -->
<meta name="format-detection" content="telphone=no">

<!-- 360浏览器指定内核 -->
<meta name="rederer" content="webkit">

<!-- 指定IE渲染模式 -->
<meta http-equiv="X-UA-Compatible" content="IE=edge">
```
**data-\***
```html
<ul>
    <li data-id="1">苹果</li>
    <li data-id="2">香蕉</li>
    <li data-id="3">菠萝</li>
</ul>
```
**microdata**
- HTML5中的一个规范
- 在HTML中通过属性嵌入格式化数据
- 提供给搜索引擎、浏览器（插件）使用
```html
<section itemscope itemtype="http://schema.org/Person">
    Hello, my name is <span itemprop="name">John Doe</span>， I am a
    <span itemprop="jobtitle">Graduate research assistant</span>at the
    <span itemprop="affiliation">University of Dreams</span>My friends call me
    <span itemprop="additonalName">Johnny</span>You can visit my homepage at
    <a href="http://www.example.com" itemprop="url">www.example.com</a>
    <section itemprop="streeAddress" itemscope itemtype="http://schema.org/PostalAddress">I live at
    <span itemprop="streetAddress">1234 Peach Drive</span>
    <span itemprop="addressloaclity">Warner Robins</span>
    <span itemprop="addressRegion">Georgia</span>
    </section>
</section>
```
**JSON-LD**
```json
<script type="application/ld+json">
    {
        "@context": "http://schema.org",
        "@type": "Person",
        "name": "John Doe",
        "jobTitle": "Graduate Research assistan",
        "affiliation": "UNiversity of Dreams",
        "additonalName": "Johnny",
        "url": "http://www.example.com",
        "address": {
            "@type": "PostalAddress",
            "streetAddress": "1234 Peach Drive",
            "addressLocality": "Wonderland",
            "addressRegion": "Georgia"
        }
    }
</script>
```
**相关衔接**
- Google Schemas
- Schema.org

**HTML编码规范**
- Google Coding Style
- W3C Validator

**工具**
- emmet
- markdown
