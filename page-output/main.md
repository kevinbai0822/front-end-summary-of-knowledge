# 高保真的产出
## 基础知识
### HTML

#### 超文本标记语言（Hyper Text Markup Language）
HTML不是一种编程语言，而是一种标记语言，它使用（标记）标签来描述网页，也就是说整个网页的结构就是由HTML来构成的  
![HTML示例](./image/html.png)  
- DOCTYPE: 总是位于html文档的第一行，`<html>`标签之前，用来告诉浏览器文档是使用的哪个版本进行编写的。
- head标签: 用于定义文档的头部，描述了文档的各种属性和信息，告诉浏览器在哪里引用样式表、引用脚本等等。一般不在页面显示。
- body标签：用于定义文档的主体，一般在页面显示的内容全都包含在body标签内。

> 元信息（meta-info）是关于数据的信息。
标签提供关于 HTML 文档的元数据。元信息不会显示在页面上，但是对于机器是可读的。
典型的情况是，meta 元素被用于规定页面的描述、关键词、文档的作者、最后修改时间以及其他元信息。
标签始终位于 head 元素中。
元信息可用于浏览器（如何显示内容或重新加载页面），搜索引擎（关键词），或其他 web 服务。

所以HTML文档就可以被视为是网页，它包含（标记）标签以及纯文本。

#### 标签
标签通常成对出现，分为开始标签和结束标签
```
<div>
	some code
</div>
```
每个开始标签都必须有对应的结束标签，否则会造成页面的混乱。从开始标签到结束标签，包括里面的所有内容，称为元素。

当然，有一些标签内不能包含任何内容，我们称之为“空元素”，也叫自闭合标签。
`area`、`base`, `br`, `col`, `command`, `embed`, `hr`, `img`, `input`, `keygen`, `link`, `meta`, `param`, `source`

经常用到的一些自闭合标签：
```
<img src="图片链接" alt="图片描述" srcset="浏览器根据宽高及像素密度来加载对应的图片资源">

<br> <!-- 换行 -->

<hr> <!-- 水平线 -->

<input type="text"> <!-- 表单元素 -->

<link rel="stylesheet" href=""> <!-- 通常被用作外部引入CSS，也可用作定义RSS -->

<col> <!-- 规定表格一列或者多列的属性 -->

<source> <!-- 为媒体元素定义媒体资源 -->

<embed src="" type=""> <!-- H5新增，定义一个容器来嵌入外部资源或者一个插件 -->
```
需要注意的一点是，自闭合标签是否应该加`/`？在XHML 1.0规范中，严格规定自闭合标签必须有`/`来闭合标签，而HTML 4.01规范则推荐不使用`/`来闭合，最新的HTML 5规范则爱用不用，都可以。

HTML元素可以分类`行内元素` `块级元素` 和 `行内块级元素`，这三者可以通过CSS互相转化。

1. 行内元素：不占据一整行，大小随内容而定，不可以设置宽高和行高，可以设置外边距但只对左右外边距有用，可以设置内边距。常见`<a>` `<span>` `<em>`等
2. 块级元素：占据一整行，可以设置宽高、行高以及内外边距，默认宽度总是与浏览器宽度一致与内容无关，可以容纳行内元素以及其他块级元素。常见`<div>` `<h1>` `<p>` `<ul>` `<li>`等
3. 行内块元素：不换行，可以设置宽高等。典型的如`<img>`

#### HTML 5
HTML5是对超文本标记语言规范的第五次重大修改，H5带来了更加丰富的语义化、表单元素以及更加强大的功能。

**一.语义化标签**  

| 标签 | 描述 |
|-----|-----|
| `<header></header>` | 定义了文档的头部 |
| `<footer></footer>`| 定义了文档的尾部 |
|`<nav></nav>`|	定义文档的导航|
| `<section></section>` | 定义文档中的节（section、区段）|
| `<article></article>` | 定义页面独立的内容区域|
| `<aside></aside>` | 定义页面的侧边栏内容|
| `<details></details>` | 用于描述文档或文档某个部分的细节|
| `<summary></summary>` | 标签包含 details 元素的标题|
| `<dialog></dialog>` |	定义对话框，比如提示框|

** 二.新增表单元素、类型与属性 **

| 表单元素 | 描述 |
|-----|-----|
| `<datalist>` |元素规定输入域的选项列表,使用`<input>`元素的*list*属性与`<datalist>`元素的*id*绑定 |
| `<keygen>` | 提供一种验证用户的可靠方法，标签规定用于表单的密钥对生成器字段 |
| `<output>` | 用于不同类型的输出，如计算或脚本输出 |

| 表单类型 | 描述 |
|-----|-----|
| `color` | 主要用于选取颜色 |
| `date` | 从一个日期选择器选择一个日期 |
| `datetime` | 选择一个日期（UTC 时间） |
| `datetime-local` | 选择一个日期和时间 (无时区) |
| `email` | 包含 e-mail 地址的输入域 |
| `month` | 选择一个月份 |
| `number` | 数值的输入域 |
| `range` | 一定范围内数字值的输入域 |
| `search` | 用于搜索域 |
| `tel` | 定义输入电话号码字段 |
| `time` | 选择一个时间 |
| `url` | url地址的输入域 |
| `week` | 选择周和年 |

| 表单属性 | 描述 |
|-----|-----|
| `placehoder` | 简短的提示在用户输入值前会显示在输入域上,即我们常见的输入框默认提示，在用户输入后消失 |
| `required ` | 是一个 boolean 属性。要求填写的输入域不能为空 |
| `pattern` | 描述了一个正则表达式用于验证`<input>`元素的值 |
| `min 和 max` | 设置元素最小值与最大值 |
| `step` | 为输入域规定合法的数字间隔 |
| `height 和 width` | 用于 image 类型的`<input>`标签的图像高度和宽度 |
| `autofocus` | 是一个 boolean 属性。规定在页面加载时，域自动地获得焦点 |
| `multiple` |  是一个 boolean 属性。规定`<input>`元素中可选择多个值 |

**三.新的功能**
- `<video> <audio>` 用于音、视频的媒体回放功能
- `<canvas>` 画布元素，标签只是容器，绘制的动作需要脚本进行控制  
![](./image/canvas.gif)
- 用于地理定位的 Geolocation API
```
window.navigator.geolocation {
    getCurrentPosition:  fn  用于获取当前的位置数据
    watchPosition: fn  监视用户位置的改变
    clearWatch: fn  清除定位监视
}
```
- 对本地离线存储的更好的支持`localStorage` `sessionStorage` `indexedDB`
- 新的`drap and drop`API

**补充点——协议**
`WebSocket` 是对HTTP协议的一个补充，是单个 TCP 连接上进行全双工通讯的协议。
[WebSocket相关](https://www.cnblogs.com/fuqiang88/p/5956363.html)

最后要说的是，我们的网页应该尽量遵循web语义化。一方面是为了让浏览器可以读懂你的页面，这样做的好处是有利于SEO等；另一方面，也便于别人在维护你的页面的时候，可以一目了然。切记为了样式层面上的作用而使用标签（如为了达到换行目的而到处使用`div`）。

### CSS

#### 层叠样式表（Cascading Style Sheets）
所谓的层叠样式表，也就是我们平时所说的“样式”，它是网页的表现层，如果说HTML是网页的结构，它就是网页的门面，也是高保真输出的重要部分。

这里我们先说一下CSS的基础知识：
###### css选择器
- 通用选择器
- 元素（类型）选择器
- 类选择器
- 属性选择器
- 伪类选择器
- ID 选择器

###### css优先级
（外部样式）External style sheet <（内部样式）Internal style sheet <（内联样式）Inline style

- 内联样式表的权值最高 1000。
- ID 选择器的权值为 100。
- Class 类选择器的权值为 10。
- HTML 标签（类型）选择器的权值为 1。

**优先级规则**
- 选择器都有一个权值，权值越大越优先。
- 当权值相等时，后出现的样式表设置要优于先出现的样式表设置。
- 创作者的规则高于浏览者：即网页编写者设置的CSS 样式的优先权高于浏览器所设置的样式。
- 继承的CSS 样式不如后来指定的CSS 样式
- 在同一组属性设置中标有“!important”规则的优先级最大。

###### css3
网页的样式遵从两个原则：`渐进增强`和`优雅降级`
- 渐进增强： 针对低版本浏览器先实现主要功能以及样式，在此基础上逐步针对高版本浏览器增强交互体验以及视觉效果。
- 优雅降级： 针对主流浏览器开发完善的功能及视觉效果，其次对低版本浏览器逐步降级兼容。

通常情况下要将一张设计图转换成html页面(这里指静态页面，我们先省略动态交互效果等)，无外乎几个重点：合适的标签、布局、定位、盒模型、背景、字体等。

##### 布局
当我们拿到一张设计图的时候，首先要做的事情就是分析页面的大体结构，大致确定每一块应该使用何种标签，从上至下分析每一块大概使用了何种布局（这里脱离前端UI框架来讨论），与此同时我们应该将响应式以及浏览器兼容性考虑在内（明确使用渐进增强还是优雅降级的原则）。  
对于上下结构的页面，我们很好实现，因为块级元素默认换行并且渲染顺序按照自上而下的顺序  
![普通布局](./image/1.PNG)
那么，如果我们想实现一个"品"字型布局呢，上面一个元素我们只要使用块级元素就可以搞定，重点在于下面两个并排的元素。行内元素是默认并排显示的，但是行内元素不能嵌套其余的行内或者块级元素，这对我们页面的实现很不友好，并且语义化的角度讲，我们也应该使用块级元素。有一种元素具备了行内元素的特征以及块级元素的特征，那就是行内块级元素。我们可以通过`display`属性来改变元素的显示样式。
![品字布局](./image/2.PNG)
```
.class{
	display: inline-block;/*元素按照行内块级元素显示*/
}
```
该属性的一些常用属性（[更多属性](http://www.w3school.com.cn/jsref/prop_style_display.asp)）：
- inline 元素按照行内元素显示
- block 元素按照块级元素显示
- none 隐藏元素（元素不占据文档流空间）

使用该属性，我们可以很轻松的实现块级元素并排显示，但是需要注意的一点是，浏览器在处理行内块级元素的样式时，会将代码中标签之间的空格也渲染出来（标签换行也视作存在空格），这个空格约为`4px`。

此外，我们还有其他方法来实现两个元素并排显示。
1. ~~float方法 漂浮的元素脱离了文档流，可能带来布局上的混乱。~~
2. ~~table布局~~
3. flex弹性盒模型
4. grid栅格布局

flex是弹性盒子的缩写，任何元素都可以设置为flex box，其语法如下
```
.class{
	display: flex; /*指定元素为flex元素*/
	display: inline-flex; /*指定行内元素为flex元素*/
}
```
我们可以看到，改变元素的显示方式依旧使用的是`display`这个属性，需要注意的是设为flex box以后，子元素的float、clear和vertical-align属性将失效。设置为`display: flex;`的元素我们称为“容器”，它还有以下的属性来控制显示方式：
```
.box {
  flex-direction: row | row-reverse | column | column-reverse; \*控制主轴方向*\
  flex-wrap: nowrap | wrap | wrap-reverse; \*控制元素是否换行以及换行方向*\
  flex-flow: <flex-direction> || <flex-wrap>; \*此属性是以上两个属性的简写*\
  justify-content: flex-start | flex-end | center | space-between | space-around; \*定义子元素在主轴上的对齐方式*\
  align-items: flex-start | flex-end | center | baseline | stretch; \*定义元素在交叉轴上的对齐方式*\
  align-content: flex-start | flex-end | center | space-between | space-around | stretch;\*定义多根轴线的对齐方式*\
}
```
介绍完了flex容器的属性设置，flex内部的子元素也有相应的样式：
```
.item{
	order: <integer>;\*用来设置子元素的排列顺序，数值越小越靠前，默认为0*\
	flex-grow: <number>;\*用来设置子元素的放大比例*\
	flex-shrink: <number>;\*用来设置子元素的缩小比例*\
	flex-basis: <length> | auto;\*定义在分配剩余空间之前，子元素所占的空间，可以设置成固定值*\
	flex: none | [ <'flex-grow'> <'flex-shrink'>? || <'flex-basis'> ] \*前面几个属性的缩写*\
	align-self: auto | flex-start | flex-end | center | baseline | stretch;\*可以设置单个子元素不同的对齐方式*\
}
```

grid栅格布局是CSS3新增的特性，之前几乎没有浏览器支持，所以普及程度也不是很高。但是随着支持性的提高，这种布局的方式应该得到推广。
```
.class{
	display: grid; //设置容器为栅格容器
	grid-template-columns: 100px 100px 100px; //指定子元素的列数为三列，且每列宽100px
    grid-template-rows: 50px 50px; //指定子元素的行数为两行，且每行高50px
}
```
![](./image/grid.png)  
更多详细的内容可以参照[Grid详解](https://segmentfault.com/a/1190000012889793?utm_source=tag-newest)

##### 盒模型
所有html元素都可以看成一个盒子，css中所提到的“盒模型”本质上就是一个盒子，它包括：外边距（margin）、边框（border）、内边距（padding）、内容（content）
![盒模型](./image/box.PNG)
```
.box{
	margin: 5px 5px 5px 5px; \*设置外边距，其顺序为上右下左*\
	margin-left: 5px;
	margin-right: 5px;
	margin-top: 5px;
	margin-bottom: 5px;
}
.box{
	pdding: 5px 5px 5px 5px; \*设置内边距，其顺序同样为上右下左*\
	pdding-left: 5px;
	pdding-right: 5px;
	pdding-top: 5px;
	pdding-bottom: 5px;
}
.box{
	border: 1px solid red;\*设置一个宽为1像素的实线红色边框*\
	border-width: 1px;
	border-style: solid;
	border-color: red;
}
```
其中，边框的样式还有
- dotted  定义点状边框。在大多数浏览器中呈现为实线。
- dashed  定义虚线。在大多数浏览器中呈现为实线。
- double  定义双线。双线的宽度等于 border-width 的值。
[更多边框样式](http://www.w3school.com.cn/cssref/pr_border.asp)、

另外，边框颜色接受十六进制颜色码以及rgba颜色码。

元素边框通常还会有三个属性用来设置以美化元素：
```
.box{
	border-radius: 2px;\*设置元素2px的圆角，接受值可为百分比*\
	box-shadow： h-shadow v-shadow blur spread color inset;\*值依次为水平阴影位置、垂直阴影位置、模糊距离、阴影尺寸、阴影颜色、内阴影*\
	border-image: url(xxx.png) 30 30 round;\*用于设置边框图片*\
}
```

##### 背景
`background`属性包含以下：
- background-color 背景颜色
- background-position 背景图像位置
- background-size 背景图像尺寸
- background-repeat 背景图像是否重复
- background-origin 背景图片的定位区域
- background-clip 背景图像的绘制区域
- background-attachment 背景图像是否固定
- background-image 规定要使用的背景图像
```
.box{
	background: #00FF00 url(bgimage.gif) no-repeat fixed top;
}
```

上面的值不必每个都去设置。

##### 字体
`font`属性包含以下：
- font-style 字体大小
- font-variant 字体异体
- font-weight 字体粗细
- font-size/line-height 字号和行高
- font-family 字体系列

字体属性的设置对我们使用的字体图标同样有效。此外，不是每个系统都能提供设计稿所包含的字体系列，例如在windows的操作系统中默认就没有苹果丽黑字体。那么我们该如何在所有用户的浏览器中保持字体一致性呢？我们可以使用css3提供的`@font-face`规则。
```
@font-face{
	font-family: myFont; \*定义字体的名称*\
	src: url('Sansation_Light.ttf'), \*字体文件的引用路径*\
		 url('Sansation_Light.eot');
}
```

##### 定位
除了常规的布局之外，有时候一些特殊的布局方式我们只通过更改元素的`display`是实现不了的，比如如何让一个元素浮在另一个元素上方？如何让一个元素始终处于窗口的最底部并且不随页面滚动？这时候我们就要用到元素的`position`属性。
在此之前，我们先说另外一个概念——文档流。
> 将窗体自上而下分成一行行, 并在每行中按从左至右的顺序排放元素,即为文档流.(自己的理解是从头到尾按照文档的顺序，该在什么位置就在什么位置，也可以按照上面的意思理解，自上而下，自左到右的顺序)

上面是一段摘自百度百科的描述，简而言之文档流就是自上而下从左往右的元素排列，每个元素都有自己的固定位置。那如何让一个元素显示在其他元素之上或者固定在某一个地方呢，这时候就要使这个元素脱离文档流。t脱离文档流的方式有两种：`position`和`float`。
这里我们详细介绍一下`position`属性，该属性的值分别有：
- static 元素出现在正常文档流中
- relative 相对定位，元素相对于其在文档流中的正常位置定位
- absolute 绝对定位，元素脱离文档流，相对于其父级第一个定位不为static的元素定位
- fixed 绝对定位，元素脱离文档流，相对于浏览器窗口进行定位。

这里需要补充的一点是，`fixed`的元素并不是始终相对于浏览器窗口进行定位，如果设置`fixed`的元素的父元素或祖先元素存在`transform`属性的话，那么就相对于该元素进行定位。

以上的属性都可以配合使用
```
.box{
	position: absolute | fixed;
	left: 20px;
	right: 20px;
	top: 20px;
	bottom: 20px;
}
```
此外定位元素还有一个`z-index`属性配合使用，这个属性表示元素的堆叠顺序，数值越大代表三维层面离用户越近，数值可以为负数。

另外提供一些教程了网站，大家可以去看看，有什么忘记的属性也可以进行查询
[W3School](http://www.w3school.com.cn/index.html)
[w3cplus](https://www.w3cplus.com/)
还有一个查询属性浏览器兼容性的网站
[Can I Use](https://caniuse.com/)

#### 伪类和伪元素
伪类包含两种：状态伪类和结构性伪类。
状态伪类是基于元素当前状态进行选择的。在与用户的交互过程中元素的状态是动态变化的，因此该元素会根据其状态呈现不同的样式。当元素处于某状态时会呈现该样式，而进入另一状态后，该样式也会失去。常见的状态伪类主要包括：

| 伪类 | 描述 |
|-----|-----|
| :link | 应用于未被访问过的链接 |
| :hover | 应用于鼠标悬停到的元素 |
| :active | 应用于被激活的元素 |
| :visited | 应用于被访问过的链接，与:link互斥 |
| :focus | 应用于拥有键盘输入焦点的元素 |

结构性伪类是css3新增选择器，利用dom树进行元素过滤，通过文档结构的互相关系来匹配元素，能够减少class和id属性的定义，使文档结构更简洁。常见的包括：

| 伪类 | 描述 |
|-----|-----|
| :first-child | 选择某个元素的第一个子元素 |
| :last-child | 选择某个元素的最后一个子元素 |
| :nth-child() | 选择某个元素的一个或多个特定的子元素 |
| :nth-last-child() | 选择某个元素的一个或多个特定的子元素，从这个元素的最后一个子元素开始算 |
| :nth-of-type() | 选择指定的元素 |
| :nth-last-of-type() | 选择指定的元素，从元素的最后一个开始计算 |
| :first-of-type | 选择一个上级元素下的第一个同类子元素 |
| :last-of-type | 选择一个上级元素的最后一个同类子元素 |
| :only-child | 选择的元素是它的父元素的唯一一个子元素 |
| :only-of-type | 选择一个元素是它的上级元素的唯一一个相同类型的子元素 |
| :empty | 选择的元素里面没有任何内容 |

伪元素是对元素中的特定内容进行操作，而不是描述状态。它的操作层次比伪类更深一层，因此动态性比伪类低很多。实际上，伪元素就是选取某些元素前面或后面这种普通选择器无法完成的工作。控制的内容和元素是相同的，但它本身是基于元素的抽象，并不存在于文档结构中！常见的伪元素选择器包括：

| 伪元素 | 描述 |
|-----|-----|
| :first-letter | 选择元素文本的第一个字（母） |
| :first-line | 选择元素文本的第一行 |
| :before | 在元素内容的最前面添加新内容 |
| :after | 在元素内容的最后面添加新内容 |

### 让网页动起来

如果想让我们的网页元素动起来，常见的方法有：
1. gif图或者flash动画  
早期的网页实现动画主要依靠的是gif或者flash动画。这个方法的优点在于浏览器兼容性问题低，且前端工程师的工作量较小；缺点是加载速度慢，影响用户体验，且维护成本高复用性差。而且随着新技术的兴起，两种方法已经逐步不采纳。
2. H5 canvas动画  
H5新增加了`<canvas>`画布，可以实现自由绘画功能，以及更高级的动画能力。这个方法的优点在动画自由度更高，浏览器兼容性问题低；缺点在于开发成本略高，所有动画效果都需要使用js来完成。
3. css3动画  
css3新增了动画能力，优点在于支持所有现代浏览器，并且开发成本低，易于实现且具有更高的动画性能。

今天，我们就来讲一讲css3的动画效果以及一些新的特性，css3有两个动画属性：`animation`和`transition`，下面我们来看一下两者的区别。

#### animation
`animation`属性强调流程与控制，它可以对元素的一个或多个属性进行控制，具有多个关键帧（与`@keyframes`结合）。`animation`是一个属性简写，可以分解成以下6个属性：
- animation-name 规定需要绑定到选择器的 keyframe 名称
- animation-duration 规定完成动画所花费的时间，以秒或毫秒计。
- animation-timing-function 规定动画的速度曲线。
- animation-delay 规定在动画开始之前的延迟。
- animation-iteration-count 规定动画应该播放的次数。
- animation-direction 规定是否应该轮流反向播放动画。

需要注意的是，`animation`属性需要联合`@keyframes`规则进行使用，`@keyframes`规则相当于事先定义好的一个流程或者说一组动画帧，它需要一个`name`。举个栗子：
```
.example{
	position: relative;
	animation: myAnimation 2s;
}
@keyframes myAnimation {
	from {
		left: 100px;
		width: 200px;
		height: 200px;
		background-color: lightseagreen;
	}
	to {
		left: 400px;
		width: 300px;
		height: 300px;
		background-color: mediumblue;
	}
}
```
效果图如下：
![动画效果图1](./image/Animation1.gif)
上面的代码我们定义了一组动画，从一开始的200\*200像素逐渐变成300\*300像素，同时我们改变了它的位置以及背景颜色，动画2秒执行完成。  
前面我们提到，`animation`属性是对流程的控制，所以我们定义一组动画的时候不仅可以使用`from` `to`来定义，还可以使用百分比来定义。这样能使我们的动画过程更加的丰富。再举个栗子：
```
.example{
	position: relative;
	width: 100px;
	height: 100px;
	animation: myAnimation 5s;
}
@keyframes myAnimation {
	0% {
		left: 100px;
		border-radius: 0;
		background-color: lightseagreen;
	}
	50% {
		left: 400px;
		border-radius: 50%;
		background-color: mediumblue;
	}
	100% {
		left: 800px;
		border-radius: 0;
		background-color: lightseagreen;
	}
}
```
效果图如下：
![动画效果图2](./image/Animation2.gif)
上面的代码跟之前我们稍有改动，我们使用了百分比来定义动画。在动画执行到50%的时候，我们将原本的正方形变成圆最后再更改回来。

这是`animation`最为基本的应用，当然`animation`还有更加厉害的动画能力，那就是`animation-timing-function`属性提供的`cubic-bezier (x1,y1,x2,y2)`三次贝塞尔曲线函数。贝塞尔曲线的数学基础是伯恩斯坦多项式，但是图像化应用最早是就职于雪铁龙的法国数学家Paul de Casteljau提出的`de Casteljau 算法`。后来由就职于雷诺的贝塞尔宣传而得名贝塞尔曲线。这里我们用到的是三次贝塞尔曲线，而贝塞尔曲面以及更加厉害的非均匀有理B样条已经成为了CAD的行业标准。
![三次贝塞尔曲线](./image/Animation3.gif)

#### transition
与`animation`属性不同的是，`transition`属性强调的是元素的过渡，是元素的一个或多个属性变化时产生的过渡效果，同一个元素通过两种不同的途径获取样式，当样式发生改变时就会产生过渡效果，可以理解为`transition`有两个动画帧。其属性可分解如下：
- transition-property 规定设置过渡效果的 CSS 属性的名称
- transition-duration 规定完成过渡效果需要多少秒或毫秒
- transition-timing-function 规定速度效果的速度曲线
- transition-delay 定义过渡效果何时开始

需要注意的是，如果需要过渡效果，要始终设置`transition-duration`属性并且不能为0，否则不会产生过渡效果。举个栗子：
```
.example{
	position: relative;
	width: 100px;
	height: 100px;
	background-color: skyblue;
	border-radius: 0;
	transition: border-radius 1s;
}
.example:hover{
	border-radius: 50%;
}
```
效果图如下：  
![Transition1](./image/Transition1.gif)  
上面的代码实现的了当鼠标悬停到div上时，元素变为圆，鼠标悬停消失的时候，恢复成正方形。同样的，该属性也能使用三次贝塞尔曲线来绘制动画效果。


- - -
上面我们介绍了css3的两个动画属性，它们可以使我们的网页交互方式变得更为丰富。下面我们再介绍一个css3中非常有用且使用比较广泛的属性。
#### transform
正如字面所理解的那样，`transform`属性用来实现元素的变换或者说变形的。css3中所定义的变形分为：移位、缩放、旋转、倾斜。下面我们一个一个介绍:
##### translate(移位)
其语法如下
```
transform：translate(x, y);
```
其接受两个值，x轴平移距离和y轴平移距离。使用平移改变的元素不会挤动文档流中的其他元素。

#### scale（缩放）
其语法如下
```
transform：scale(x,y);
```
其接受两个值，x轴缩放比例和y轴缩放比例。

#### rotate(旋转)
其语法如下
```
transform： rotate(90deg);
```
其接受一个值，元素的旋转角度。

#### skew(倾斜)
其语法如下
```
transform: skew(x, y);
```
其接受两个值，x轴倾斜角度和y轴倾斜角度。

下面看一个综合的栗子：
```
div{
	display: inline-block;
	margin-left: 50px;
	margin-top: 50px;
}
.example1{
	transform: translate(20px, 0);
}
.example2{
	transform: scale(0.5, 0.5);
}
.example3{
	transform: rotate(45deg);
}
.example4{
	transform: skew(30deg, 15deg);
}
```
效果图如下：
![Transform](./image/transform.png)

#### transform-origin
此外，`transform`还有一个属性`transform-origin`，元素变换的原点默认是基于元素中心的，这个属性用来定义变换的原点。我们举个栗子看一下：
```
.wrap{
	position: relative;
	top: 200px;
	left: 500px;
	width: 100px;
	height: 100px;
	background-color: tomato;
}
.example5{
	width: 100px;
	height: 100px;
	background-color: skyblue;
	transform: rotate(45deg);
}
```
正常情况下，我们得到的结果是这样的：  
![Transform](./image/r1.png)  
我们可以发现，里面的正方形是以中心为原点旋转的。现在我们改变一下变换的原点：
```
.wrap{
	position: relative;
	top: 200px;
	left: 500px;
	width: 100px;
	height: 100px;
	background-color: tomato;
}
.example5{
	width: 100px;
	height: 100px;
	background-color: skyblue;
	transform: rotate(45deg);
	transform-origin: 0 0;
}
```
效果如下图：  
![Transform](./image/r2.png)  
我们将元素的变换原点设置成`0 0`,也就是说元素以`(0, 0)`这个坐标为原点进行旋转。

#### 3D变换
上面介绍的变换都是2D的，撇开倾斜变换之外，其他的变换具有3D变换的特点，下面我们接着看例子：
```
div{
	display: inline-block;
	margin-left: 50px;
	margin-top: 50px;
	border: 1px solid blue;
	perspective: 600px;
}
.example6 img{
	transform: rotateX(45deg);
}
.example7 img{
	transform: rotateY(45deg);
}
.example8 img{
	transform: rotateZ(45deg);
}
```
其效果如下图：
![Transform](./image/3D1.png)
上面的代码我们分别定义了图片沿着X轴、Y轴、Z轴进行3D旋转，这里需要注意的是如果我们要使用3D旋转，必须在父元素或者祖先元素上设置`perspective`透视这个属性，否则浏览器会将3D变换的效果投射到2D层面，我们只能看到元素的宽度或者高度的改变。那么`perspective`这个属性是什么意思呢？它相当于浏览器模拟了一个观察者的角色，这个观察者跟Z轴是平行的，该属性的值定义观察者离被观察元素的距离。

一个综合实现的例子：
```
.example9 img{
	animation: myRotate 3s linear infinite;
}
@keyframes myRotate {
	0% {
		transform: rotateY(0deg);
	}
	50% {
		transform: rotateY(180deg);
	}
	100%{
		transform: rotateY(360deg);
	}
}
```
![Transition1](./image/Animation4.gif)

**利用css3动画及变换实现一个简单的相册效果**
```
body{
	background-color: #000;
}
.album{
	position: relative;
	margin-left: 100px;
	margin-top: 50px;
	width: 700px;
}
.album div{
	display: inline-block;
	margin-right: 30px;
	perspective: 600px;
}
.album div img{
	position: relative;
	transition: all 500ms linear;
}
.example10 img{
	transform: rotateY(-45deg);
	opacity: 0.4;
}
.example11 img{
	transform: scale(1.2);
}
.example12 img{
	transform: rotateY(45deg);
	opacity: 0.4;
}
.example13{
	position: absolute;
	right: 0;
	top: 0;
	z-index: -1;
}
.example13 img{
	transform: rotateY(90deg);
	opacity: 0;
}
.album:hover .example10 img{
	transform: rotateY(-90deg);
	opacity: 0;
}
.album:hover .example11 img{
	transform: translateX(-234px) rotateY(-45deg) scale(1);
	opacity: 0.4;
}
.album:hover .example12 img{
	transform: translateX(-249px) rotateY(0deg) scale(1.2);
	opacity: 1;
}
.album:hover .example13 img{
	transform: rotateY(45deg);
	opacity: 0.4;
}
```
实现效果如下图：
![Transition1](./image/Animation5.gif)

由此我们已经具备了高保真输出的基本技能了。



