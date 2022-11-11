<style>
.warning {
  background-color:rgba(239,111,27,0.1);
  border-left:4px solid orange;
}
</style>

# CSS

- [CSS](#css)
  - [概念](#概念)
    - [CSS3 新特性](#css3-新特性)
    - [CSS 选择器](#css-选择器)
    - [CSS 选择器的解析规则](#css-选择器的解析规则)
    - [CSS 选择器优先级](#css-选择器优先级)
    - [::before 和::after这 2 个伪元素的作用和区别](#before-和after这-2-个伪元素的作用和区别)
    - [伪类、伪元素的作用与区别](#伪类伪元素的作用与区别)
    - [CSS3新增伪类](#css3新增伪类)
    - [关于伪类 LVHA 的解释](#关于伪类-lvha-的解释)
    - [CSS 中哪些属性可以继承](#css-中哪些属性可以继承)
    - [CSS 盒模型](#css-盒模型)
    - [设置一个元素的背景颜色，背景颜色会填充哪些区域](#设置一个元素的背景颜色背景颜色会填充哪些区域)
    - [绝对定位元素与非绝对定位元素的百分比计算的区别](#绝对定位元素与非绝对定位元素的百分比计算的区别)
    - [link 和 @import 的区别](#link-和-import-的区别)
    - [基线、行高](#基线行高)
    - [vertical-align](#vertical-align)
    - [line-height的计算](#line-height的计算)
    - [position取值](#position取值)
      - [定位元素 positioned element:除了static外的](#定位元素-positioned-element除了static外的)
        - [static](#static)
      - [相对定位元素](#相对定位元素)
        - [relative](#relative)
      - [绝对定位元素](#绝对定位元素)
        - [absolute](#absolute)
        - [fixed（老IE不支持）](#fixed老ie不支持)
      - [黏性定位元素 stickily positioned element](#黏性定位元素-stickily-positioned-element)
        - [sticky](#sticky)
    - [包含块 containing block](#包含块-containing-block)
    - [层叠上下文 stacking context](#层叠上下文-stacking-context)
      - [特性](#特性)
      - [产生原因](#产生原因)
    - [z-index](#z-index)
      - [例子](#例子)
        - [例子一](#例子一)
  - [!z-index1](#)
        - [例子二](#例子二)
        - [例子三](#例子三)
        - [例子四](#例子四)
    - [连续媒体 continuous media](#连续媒体-continuous-media)
    - [flex-box](#flex-box)
    - [BFC 的概念, 哪些元素可以触发 BFC](#bfc-的概念-哪些元素可以触发-bfc)
    - [IFC 行内格式化上下文](#ifc-行内格式化上下文)
    - [display 有哪些值？说明他们的作用](#display-有哪些值说明他们的作用)
    - [float 的元素display 是什么](#float-的元素display-是什么)
    - [替换元素(replaced element)](#替换元素replaced-element)
      - [替换元素范围](#替换元素范围)
      - [替换元素特点](#替换元素特点)
      - [控制`content-box`中的对象位置](#控制content-box中的对象位置)
      - [样式计算](#样式计算)
      - [匿名替换元素](#匿名替换元素)
    - [inline-block、inline 和 block 的区别](#inline-blockinline-和-block-的区别)
    - [visibility](#visibility)
      - [visible](#visible)
      - [hidden](#hidden)
      - [collapse](#collapse)
    - [`visibility: hidden`, `opacity: 0`, `display: none`的区别](#visibility-hidden-opacity-0-display-none的区别)
    - [`width:auto` 和 `width:100%`的区别](#widthauto-和-width100的区别)
    - [设备像素、css 像素、设备独立像素、dpr、ppi 之间的区别](#设备像素css-像素设备独立像素dprppi-之间的区别)
      - [设备像素](#设备像素)
      - [css像素](#css像素)
        - [ppi](#ppi)
        - [dpr](#dpr)
        - [dpi](#dpi)
    - [viewport](#viewport)
      - [视口基础知识](#视口基础知识)
      - [屏幕密度](#屏幕密度)
      - [视口宽度和屏幕宽度](#视口宽度和屏幕宽度)
      - [三种viewport](#三种viewport)
        - [可视视口 visual viewport](#可视视口-visual-viewport)
        - [布局视口 layout viewport](#布局视口-layout-viewport)
        - [理想视口 ideal viewport](#理想视口-ideal-viewport)
    - [vw 和 vh 的概念](#vw-和-vh-的概念)
    - [`display`,`position`和`float`的相互关系？](#displayposition和float的相互关系)
    - [margin合并](#margin合并)
    - [`all` 属性](#all-属性)
    - [`hasLayout` 属性](#haslayout-属性)
    - [font-style 属性中 italic 和 oblique 的区别](#font-style-属性中-italic-和-oblique-的区别)
    - [图片格式](#图片格式)
      - [BMP](#bmp)
      - [GIF](#gif)
      - [JPG](#jpg)
      - [PNG-8](#png-8)
      - [PNG-24](#png-24)
      - [SVG](#svg)
      - [WEBP](#webp)
    - [style 标签写在 body 后与 body 前有什么区别？](#style-标签写在-body-后与-body-前有什么区别)
    - [css预处理器与后处理器](#css预处理器与后处理器)
      - [预处理器](#预处理器)
      - [后处理器](#后处理器)
    - [使用 rem 布局的优缺点](#使用-rem-布局的优缺点)
    - [首选最小宽度](#首选最小宽度)
    - [border的一些特殊性质](#border的一些特殊性质)
    - [overflow](#overflow)
      - [visible](#visible-1)
      - [hidden](#hidden-1)
      - [clip](#clip)
      - [scroll](#scroll)
      - [auto](#auto)
      - [overlay](#overlay)
    - [无依赖绝对定位](#无依赖绝对定位)
    - [font-weight](#font-weight)
      - [normal](#normal)
      - [bold](#bold)
      - [lighter](#lighter)
      - [bolder](#bolder)
      - [回退机制](#回退机制)
    - [letter-spacing](#letter-spacing)
  - [应用](#应用)
    - [初始化css样式的目的](#初始化css样式的目的)
    - [CSS 清除浮动](#css-清除浮动)
    - [清除浮动的原理](#清除浮动的原理)
    - [脱离文档流的方式](#脱离文档流的方式)
    - [了解重绘和重排吗，知道怎么去减少重绘和重排吗，让文档脱离文档流有哪些方法](#了解重绘和重排吗知道怎么去减少重绘和重排吗让文档脱离文档流有哪些方法)
    - [经常遇到的浏览器的兼容性有哪些？原因，解决方法是什么，常用 hack 的技巧](#经常遇到的浏览器的兼容性有哪些原因解决方法是什么常用-hack-的技巧)
    - [简单介绍使用图片 base64 编码的优点和缺点](#简单介绍使用图片-base64-编码的优点和缺点)
    - [如果需要手动写动画，你认为最小时间间隔是多久，为什么](#如果需要手动写动画你认为最小时间间隔是多久为什么)
    - [阐述一下 CSS Sprites](#阐述一下-css-sprites)
    - [画一条 0.5px 的线](#画一条-05px-的线)
      - [方法一 viewport](#方法一-viewport)
      - [方法二 transform](#方法二-transform)
      - [方法三 采用 border-image 的方式](#方法三-采用-border-image-的方式)
      - [方法四 采用 box-shadow 的方式](#方法四-采用-box-shadow-的方式)
      - [方法五 采用svg](#方法五-采用svg)
      - [方法六 直接设置0.5px](#方法六-直接设置05px)
      - [方法七 采用linear-gradient](#方法七-采用linear-gradient)
    - [transition 和 animation 的区别](#transition-和-animation-的区别)
    - [如何实现单行／多行文本溢出的省略（...）](#如何实现单行多行文本溢出的省略)
    - [常见的元素隐藏方式](#常见的元素隐藏方式)
    - [CSS3 @font-face 有用过吗](#css3-font-face-有用过吗)
    - [CSS 实现隔行变色](#css-实现隔行变色)
    - [一个满屏品字布局如何设计](#一个满屏品字布局如何设计)
    - [CSS 画三角形](#css-画三角形)
      - [方法一 使用border](#方法一-使用border)
      - [方法二 使用linear-gradient](#方法二-使用linear-gradient)
    - [CSS 画扇形](#css-画扇形)
    - [CSS 画正方体](#css-画正方体)
    - [CSS 实现一个硬币旋转的效果](#css-实现一个硬币旋转的效果)
    - [CSS 实现水平居中](#css-实现水平居中)
      - [行内元素：](#行内元素)
      - [块级元素](#块级元素)
        - [方法一：](#方法一)
        - [方法二：](#方法二)
        - [方法三：](#方法三)
    - [CSS 实现垂直居中](#css-实现垂直居中)
    - [CSS 实现两列固定，中间自适应的布局](#css-实现两列固定中间自适应的布局)
    - [实现自适应九宫格](#实现自适应九宫格)
    - [屏幕里面内容未占满的时候 footer 固定在屏幕可视区域的底部。占满的时候显示在网页的最底端](#屏幕里面内容未占满的时候-footer-固定在屏幕可视区域的底部占满的时候显示在网页的最底端)
    - [CSS 多列等高如何实现？](#css-多列等高如何实现)
    - [li 与 li 之间有看不见的空白间隔是什么原因引起的？有什么解决办法？](#li-与-li-之间有看不见的空白间隔是什么原因引起的有什么解决办法)
    - [媒体查询](#媒体查询)
    - [CSS 优化、提高性能的方法](#css-优化提高性能的方法)
      - [加载性能：](#加载性能)
      - [选择器性能：](#选择器性能)
      - [渲染性能：](#渲染性能)
      - [可维护性、健壮性：](#可维护性健壮性)
    - [在网页中应该使用奇数字号还是偶数字号的字体？为什么呢？](#在网页中应该使用奇数字号还是偶数字号的字体为什么呢)
    - [全屏滚动如何实现？](#全屏滚动如何实现)
    - [如何修改 chrome 记住密码后自动填充表单的黄色背景？](#如何修改-chrome-记住密码后自动填充表单的黄色背景)
    - [如何让 Chrome 支持小于 12px 的文字？](#如何让-chrome-支持小于-12px-的文字)
    - [如何让页面里的字体变清晰，变细？](#如何让页面里的字体变清晰变细)
    - [position:fixed;在 android 下无效怎么处理？](#positionfixed在-android-下无效怎么处理)
    - [如何去除 `inline-block` 元素间间距？](#如何去除-inline-block-元素间间距)
      - [方法一 写成一行](#方法一-写成一行)
      - [方法二 把上一个闭合标签和下一个起始标签连在一起](#方法二-把上一个闭合标签和下一个起始标签连在一起)
      - [方法三 利用注释标签](#方法三-利用注释标签)
      - [方法四 不要闭合标签](#方法四-不要闭合标签)
      - [方法五 通过设置margin](#方法五-通过设置margin)
      - [方法六 通过父元素的`font-size:0`](#方法六-通过父元素的font-size0)
    - [如何解决`overflow:scroll` 时不能平滑滚动的问题？](#如何解决overflowscroll-时不能平滑滚动的问题)
    - [有一个高度自适应的 div，里面有两个div，一个高度 100px，希望另一个填满剩下的高度。](#有一个高度自适应的-div里面有两个div一个高度-100px希望另一个填满剩下的高度)
    - [浏览器如何判断是否支持 webp 格式图片](#浏览器如何判断是否支持-webp-格式图片)
      - [方法一 宽高判断法](#方法一-宽高判断法)
      - [方法二 canvas判断方法](#方法二-canvas判断方法)
      - [方法三 根据请求header信息](#方法三-根据请求header信息)
    - [CSS 布局](#css-布局)
      - [单列布局](#单列布局)
      - [两列自适应布局](#两列自适应布局)
      - [三栏布局](#三栏布局)
      - [黏连布局](#黏连布局)
      - [等高布局](#等高布局)
    - [`height:100%`失效的情况](#height100失效的情况)
    - [min-width和max-width属性间的覆盖规则？](#min-width和max-width属性间的覆盖规则)
    - [幽灵空白节点是怎么回事？](#幽灵空白节点是怎么回事)
    - [`margin: auto` 填充规则](#margin-auto-填充规则)
    - [margin在什么情况下无效？](#margin在什么情况下无效)
    - [absolute 与 overflow 会相互制约吗？](#absolute-与-overflow-会相互制约吗)

## 概念
### CSS3 新特性

[参考链接](https://www.cnblogs.com/xkweb/p/5862612.html)

1. 伪类和伪元素选择器：
   > :first-child, :last-child, :nth-child(1), :link, :visited, :hover, :active
   > ::before, ::after, :first-letter, :first-line, ::selection
2. 背景、边框和颜色透明度：
   > background-size, background-origin, border-radius
   > box-shadow, border-image
   > rgba
3. 文字效果：
   > text-shadow, word-wrap
4. 2D 转换和 3D 转换：
   > transform, translate(), rotate(), scale(), skew(), matrix()
   > rotateX(), rotateY(), perspective
5. 动画、过渡：animation, transition
6. 多列：column-count, column-gap, column-rule
7. 用户界面：resize, box-sizing, outline-offset

### CSS 选择器
（1）id选择器（#myid）
（2）类选择器（.myclassname）
（3）标签选择器（div,h1,p）
（4）后代选择器（h1 p）
（5）子选择器（ul>li）
（6）兄弟选择器（所有）（li~a）
（7）相邻兄弟选择器（li+a）
（8）属性选择器（a[rel="external"]）
（9）伪类选择器（a:hover,li:nth-child）
（10）伪元素选择器（::before、::after）
（11）通配符选择器（*）

### CSS 选择器的解析规则

从右向左匹配
样式系统从关键选择器开始匹配，然后左移查找规则选择器的祖先元素。只要选择器的子树一直在工作，样式系统就会持续左移，直到和规则匹配，或者是因为不匹配而放弃该规则。

从右往左进行解析的好处:就是从右往左进行匹配的时候，匹配的全部是 DOM 元素的父节点，而从左往右进行匹配时，匹配的全部是 DOM 元素的子节点，这样就避免了 HTML 与 CSS 没有下载完需要进行等待的情形。且大多数规则读到最后（最右）才会发现是不匹配的，遍历查找的节点会少很多。这样会提高查找选择器所对应的元素的效率。

### CSS 选择器优先级

选择器按优先级先后排列：!important>内联>id>class = 属性 = 伪类 >标签 = 伪元素 > 通配符 \*

- important 声明 1,0,0,0
- ID 选择器 0,1,0,0
- 类选择器 0,0,1,0
- 伪类选择器 0,0,1,0
- 属性选择器 0,0,1,0
- 标签选择器 0,0,0,1
- 伪元素选择器 0,0,0,1
- 通配符选择器 0,0,0,0

（1）每个等级的初始值为0
（2）每个等级的叠加为选择器出现的次数相加
（3）不可进位，比如0,99,99,99
（4）依次表示为：0,0,0,0
（5）每个等级计数之间没关联
（6）等级判断从左向右，如果某一位数值相同，则判断下一位数值
（7）如果两个优先级相同，则最后出现的优先级高，!important也适用
（8）通配符选择器的特殊性值为：0,0,0,0
（9）继承样式优先级最低，通配符样式优先级高于继承样式
（10）相同特殊性值的声明，根据样式引入的顺序，后声明的规则优先级高（距离元素出现最近的）
（11）!important（权重），它没有特殊性值，但它的优先级是最高的，为了方便记忆，可以认为它的特殊性值为1,0,0,0,0。


###  ::before 和::after这 2 个伪元素的作用和区别
效果上，::before可以把需插入的内容插入到元素的其他内容之前，::after让插入内容在其他内容之后。
代码顺序上，::after生成的内容比::before生成的内容靠后。
堆栈视角上，::after生成的内容会在::before生成的内容之上。


### 伪类、伪元素的作用与区别

在css3中使用单冒号来表示伪类，用双冒号来表示伪元素。但是为了兼容已有的伪元素的写法，比如:first-line、:firstletter、:before、:after等，在一些浏览器中也可以使用单冒号来表示伪元素。
css引入伪类和伪元素概念是为了格式化文档树以外的信息。也就是说，伪类和伪元素是用来修饰不在文档树中的部分，比如，一句
话中的第一个字母，或者是列表中的第一个元素。

伪类用于当已有的元素处于某个状态时，如hover、link等，为其添加对应的样式，这个状态是根据用户行为而动态变化的。比如说，当用户悬停在指定的元素时，我们可以通过:hover来描述这个元素的状态。

伪元素一般匹配特殊的位置，比如after、before等，用于创建一些不在文档树中的元素，并为其添加样式。它们允许我们为元素的某些部分设置样式。比如说，我们可以通过::before来在一个元素前增加一些文本，并为这些文本添加样式。虽然用户可以看到这些文本，但是这些文本实际上不在文档树中。

### CSS3新增伪类
（1）elem:nth-child(n)选中父元素下的第n个子元素，并且这个子元素的标签名为elem，n可以接受具体的数值，也可以接受函数。
（2）elem:nth-last-child(n)作用同上，不过是从后开始查找。
（3）elem:last-child选中最后一个子元素。
（4）elem:only-child如果elem是父元素下唯一的子元素，则选中之。
（5）elem:nth-of-type(n)选中父元素下第n个elem类型元素，n可以接受具体的数值，也可以接受函数。
（6）elem:first-of-type选中父元素下第一个elem类型元素。
（7）elem:last-of-type选中父元素下最后一个elem类型元素。
（8）elem:only-of-type如果父元素下的子元素只有一个elem类型元素，则选中该元素。
（9）elem:empty选中不包含子元素和内容的elem类型元素。
（10）elem:target选择当前活动的elem元素。
（11）:not(elem)选择非elem元素的每个元素。
（12）:enabled 控制表单控件的禁用状态。
（13）:disabled 控制表单控件的禁用状态。
（14）:checked单选框或复选框被选中。

### 关于伪类 LVHA 的解释
LVHA指a标签的四种状态：链接访问前、链接访问后、鼠标滑过、激活，分别对应四种伪类:link、:visited、:hover、:active；

当链接未访问过时：

（1）当鼠标滑过a链接时，满足:link和:hover两种状态，要改变a标签的颜色，就必须将:hover伪类在:link伪类后面声明；
（2）当鼠标点击激活a链接时，同时满足:link、:hover、:active三种状态，要显示a标签激活时的样式（:active），必须将:active声明放到:link和:hover之后。因此得出LVHA这个顺序。

当链接访问过时，情况基本同上，只不过需要将:link换成:visited。

这个顺序能不能变？可以，但也只有:link和:visited可以交换位置，因为一个链接要么访问过要么没访问过，不可能同时满足，也就不存在覆盖的问题。


### CSS 中哪些属性可以继承

每一个属性在定义中都给出了这个属性是否具有继承性，一个具有继承性的属性会在没有指定值的时候，会使用父元素的同属性的值来作为自己的值。当元素的一个非继承属性(在 Mozilla code 里有时称之为reset property) 没有指定值时，则取属性的初始值 initial value（该值在该属性的概述里被指定）。

有继承性的属性：
（1）字体系列属性
font、font-family、font-weight、fontsize、font-style、font-variant、fontstretch、font-size-adjust
（2）文本系列属性
text-indent、text-align、text-shadow、
line-height、word-spacing、letterspacing、
text-transform、direction、color
（3）表格布局属性
caption-side border-collapse empty-cells
（4）列表属性
list-style-type、list-style-image、liststyle-position、list-style
（5）光标属性
cursor
（6）元素可见性
visibility
（7）还有一些不常用的；speak，page，设置嵌套引用的引号类型quotes等属性

当一个属性不是继承属性的时候，我们也可以通过将它的值设置为inherit来使它从父元素那获取同名的属性值来继承。inherit
关键字用于显式地指定继承性，可用于任何继承性/非继承性属性。

### CSS 盒模型

盒模型总共包括 4 个部分：

- content：内容，容纳着元素的真实内容，例如文本，图像或是视频播放器
- padding：内边距
- border：边框
- margin：外边距

两种盒模型的区别：

- W3C 盒模型(默认) `box-sizing: content-box`
  > W3C 盒模型中，通过 CSS 样式设置的 width 的大小只是 content 的大小，不符合直觉的。
- IE 盒模型 `box-sizing: border-box`
  > IE 盒模型中，通过 CSS 样式设置的 width 的大小是 content + padding + border 的和。符合直觉的。
  
  如果在ie6，7，8中DOCTYPE缺失会将盒子模型解释为IE盒子模型。若在页面中声明了DOCTYPE类型，所有的浏览器都会把盒模型解释为W3C盒模型。


### 设置一个元素的背景颜色，背景颜色会填充哪些区域

> border + padding + content

```css
div {
  width: 100px;
  height: 100px;
  background-color: pink;
  border: 5px dotted green;
}
```

### 绝对定位元素与非绝对定位元素的百分比计算的区别

绝对定位元素的宽高百分比是相对于临近的position不为static的祖先元素的padding box来计算的。
非绝对定位元素的宽高百分比则是相对于父元素的content box来计算的。

> 假设一个 div, 宽 400px, 高 200px, 它有个子 div 的 margin:10%, 求它的 margin 的 top, right, bottom, left 是多少？

```css
.outer {
    width: 400px;
    height: 200px;
    background-color: red;
    position: relative;
}
.inner {
    width: 100px;
    height: 100px;
    background-color: green;
    position: absolute;
    margin: 10%;
}

<div class="outer">
    <div class="inner"></div>
</div>
```

效果是子盒子的 margin 为 40px 40px 40px 40px

<blockquote class="warning">注意：margin/padding 设置百分比都是相对于父盒子的宽度(width 属性)</blockquote>

### link 和 @import 的区别

1. link 是 HTML 标签，不仅可以加载 CSS 文件，还可以定义 RSS、rel 连接属性等；@import 是 CSS 提供的语法，只有导入样式表的作用。
2. 加载页面时，link 标签引入的 CSS 被同时加载；@import 引入的 CSS 将在页面加载完毕后被加载。
3. @import 是 CSS2.1 才有的语法，故只可在 IE5+ 才能识别；link 标签作为 HTML 元素，不存在兼容性问题。
4. 可以通过 JS 操作 DOM ，插入 link 标签来改变样式；由于 DOM 方法是基于文档的，无法使用@import 的方式插入样式。
5. link 引入的样式权重大于@import 引入的样式。

### 基线、行高
![](./images/line-height.png)
基线是指欧洲和西亚文字排版中，用于在上面放置字符的一条假想的基准线。
字符的降部比如 g 和 p 会向下超出基线，带弧形的会向上和向下扩展的字形，比如 C 或 3 会略微向下超出基线。
东亚文字没有基线，他们的字形放置在方盒子，没有升部和降部。

顶线和底线之间为内容区，一般就是字体大小。

x-height指的是小写字母x的高度。现已废弃。

reference:
https://developer.mozilla.org/zh-CN/docs/Glossary/baseline
https://developer.aliyun.com/article/330933
https://developer.mozilla.org/en-US/docs/Web/SVG/Attribute/x-height


### vertical-align
* `vertical-align`的默认值是`baseline`，即基线对齐，而基线的定义是字母x的下边缘。因此，内联元素默认都是沿着字母x的下边缘对齐的。图片等替换元素使用元素本身的下边缘作为基线。如果一个`inline-block`元素里没有内联元素，或者`overflow`不是`visible`，则该元素的基线就是其margin底边缘；否则其基线就是元素里面最后一行内联元素的基线。
* `vertical-align:top`是垂直上边缘对齐。如果是内联元素，则和这一行位置最高的内联元素的顶部对齐；对于`display:table-cell`的元素，则和`<td>`元素类似，与`<tr>`元素上边缘对齐。
* `vertical-align:middle`是中间对齐，对于内联元素，元素的垂直中心点和行框盒子基线往上1/2 x-height处对齐。对于`table-cell`元素，单元格填充盒子相对于外面的表格行居中对齐。
* `vertical-align`支持数值属性，相对于基线偏移。如果是负值，往下偏移，如果是正值，往上偏移。
* `vertical-align`属性的百分比值是相对于`line-height`的计算值计算的。
* `vertical-align`只能应用于内联元素以及`display:table-cell`的元素。
* `table-cell`元素设置`vertical-align`垂直对齐的是子元素，但是其作用的并不是子元素，而是`table-cell`元素自身。

### line-height的计算
* 对于非替换元素的内联元素，其可视高度完全由`line-height`决定。比如文本，`line-height`指定了用来计算行框盒子高度的基础高度。
* 内联元素的高度由固定高度和不固定高度组成，这个不固定的部分就是这里的“行距”。在CSS中，“行距”分散在当前文字的上方和下方，即使是第一行文字，其上方也有“行距”，只不过这个“行距”的高度仅仅是完整“行距”的一半，因此，也被称为“半行距”。
* 行距 = `line-height` - `font-size`（因为上下都存在）。
* `border`以及`line-height`等传统CSS属性并没有小数像素的概念。如果标注的是文字上边距，则向下取整；如果是文字下边距，则向上取整。
* 对于纯文本元素，`line-height`直接决定了最终的高度。但是，如果同时有替换元素，则`line-height`只能决定最小高度。
* 对于块级元素，`line-height`对其本身是没有任何作用的。改变`line-height`，块级元素的高度跟着变化实际上是因为改变块级元素里面内联元素高度改变。
* `line-height`的默认值是`normal`，还支持数值、百分比值以及长度值。为数值或百分比类型时，其最终的计算值是和当前`font-size`相乘后的值；为长度值时不变。
* 如果使用数值作为`line-height`的属性值，那么所有的子元素继承的都是这个值；但是，如果使用百分比值或者长度值作为属性值，那么所有的子元素继承的是最终的计算值。
* 无论内联元素`line-height`如何设置，最终父级元素的高度都是由数值大的那个`line-height`决定的。
* 只要有“内联盒子”在，就一定会有“行框盒子”，即每一行内联元素外面包裹的一层看不见的盒子。并且，在每个“行框盒子”前面有一个宽度为0的具有该元素字体和行高属性的“幽灵空白节点”。

### position取值

#### 定位元素 positioned element:除了static外的
##### static
默认值。没有定位，元素出现在正常的流中（忽略top,bottom,left,right,z-index声明）。

#### 相对定位元素  
##### relative
生成相对定位的元素，相对于文档正常流所在位置进行定位。元素先放置在未添加定位时的位置，再在不改变页面布局的前提下调整元素位置（因此会在此元素未添加定位时所在位置留下空白）。
当z-index不是auto的时候，会创造新的层叠上下文。

* 相对定位元素的left/top/right/bottom的百分比值是相对于包含块计算，而定位位移是相对自身计算。
* top和bottom的百分比值计算与height的百分比值计算一样，都是相对高度计算。同时，如果包含块的高度是auto，那么偏移无效。也就是说，如果父元素没有设定高度或者不是“格式化高度”，那么relative元素top与bottom的设置均无效。
* 当相对定位元素同时应用对立方向定位值时，即top与bottom，left与right同时使用的时候，只有一个方向的定位属性会起作用，与文档流的顺序有关。默认的文档流是自上而下、从左往右，因此bottom，right会失效。

#### 绝对定位元素
##### absolute
生成绝对定位的元素，元素会被移出正常文档流，并不为元素预留空间。相对于最近的非 static 定位祖先元素的偏移，来确定元素位置。即离自己这一级元素最近一级position设置为absolute或者relative的父元素的box的左上角为原点。

##### fixed（老IE不支持）
生成绝对定位的元素，元素会被移出正常文档流，并不为元素预留空间。相对于viewport进行定位。元素的位置在屏幕滚动时不会改变。当元素祖先的 transform, perspective 或 filter 属性非 none 时，容器的视口改为该祖先。元素会出现在每页的固定位置。
fixed 属性总是创建新的层叠上下文。 

#### 黏性定位元素 stickily positioned element
##### sticky
元素根据正常文档流进行定位，然后相对它的最近滚动祖先 nearest scrolling ancestor和 containing block (最近块级祖先 nearest block-level ancestor)，包括table-related元素，基于top, right, bottom, 和 left的值进行偏移。偏移值不会影响任何其他元素的位置。
sticky值总是创建一个新的层叠上下文。一个sticky元素会“固定”在离它最近的一个拥有“滚动机制”的祖先上（滚动机制：overflow 是 hidden, scroll, auto, 或 overlay的元素）。

reference:https://developer.mozilla.org/en-US/docs/Web/CSS/position

### 包含块 containing block
经常来说，包含块就是一个元素最近的块级祖先
I.如果position是static, relative, sticky，那么包含块要么由它最近的祖先块级元素的content边缘组成，要么建立格式化上下文。
II.如果position是absolute，那么包含块由它最近的非static祖先元素的padding边缘组成。
III.如果position是fixed，在连续媒体的情况下是viewport，在分页媒体的情况下是页区域page area
IV.如果position是absolute或fixed，包含块也可能由满足以下条件的最近祖先元素的padding边缘组成：
i.  `transform` 或 `perspective` 的值不是 `none`
ii. `will-change` 的值是 `transform` 或 `perspective`
iii.`filter` 的值不是 `none` 或 `will-change` 的值是 `filter` (只在Firefox下生效).
iv. `contain` 的值是 `paint`
v. `backdrop-filter` 的值不是 `none` (e.g. backdrop-filter: blur(10px);)

reference:https://developer.mozilla.org/zh-CN/docs/Web/CSS/Containing_block

### 层叠上下文 stacking context
HTML 元素沿着其相对于用户的一条虚构的 z 轴排开，层叠上下文就是对这些 HTML 元素的一个三维构想。
某些元素的渲染顺序是由其 z-index 的值影响的。这是因为这些元素具有能够使他们形成一个层叠上下文的特殊属性。

#### 特性
* 层叠上下文可以包含在其他层叠上下文中，并且一起创建一个层叠上下文的层级。
* 每个层叠上下文都完全独立于它的兄弟元素：当处理层叠时只考虑子元素。
* 每个层叠上下文都是自包含的：当一个元素的内容发生层叠后，该元素将被作为整体在父级层叠上下文中按顺序进行层叠。。
* 层叠上下文可以阻断元素的混合模式。
* 层叠上下文可以嵌套，内部层叠上下文及其所有子元素均受制于外部的“层叠上下文”。

#### 产生原因
文档中的层叠上下文由满足以下任意一个条件的元素形成：
- 文档根元素（`<html>`）；
- position 值为 absolute 或 relative 且 z-index 值不为 auto 的元素；
- position 值为 fixed 或 sticky 的元素（沾滞定位适配所有移动设备上的浏览器，但老的桌面浏览器不支持）；
- flex (flex) 容器中z-index 值不为 auto的子元素；
- grid (grid) 容器中z-index 值不为 auto的子元素 ；
- opacity 属性值小于 1 的元素；
- mix-blend-mode 属性值不为 normal 的元素；
- 以下任意属性值不为 none 的元素：
  - transform
  - filter
  - backdrop-filter
  - perspective
  - clip-path
  - mask / mask-image / mask-border
  - isolation 属性值为 isolate 的元素；
  - will-change 值设定了任一属性而该属性在 non-initial 值时会创建层叠上下文的元素；
  - contain 属性值为 layout、paint 或包含它们其中之一的合成值（比如 contain: strict、contain: content）的元素。

reference:
https://developer.mozilla.org/zh-CN/docs/Web/CSS/CSS_Positioning/Understanding_z_index/The_stacking_context
https://dev.opera.com/articles/css-will-change-property/

### z-index
z-index 属性设定了一个定位元素及其后代元素或 flex 项目的 z-order。当元素之间重叠的时候，z-index 较大的元素会覆盖较小的元素在上层进行显示。

* z-index只在属性 `position: relative/absolute/fixed` 的时候才生效。
* `z-index` 默认值是auto
* `z-index: 0` 会创建一个新的堆叠上下文，而`z-index: auto` 不会创建新的堆叠上下文
* 后代的 `z-index` 不与此元素之外的元素的 `z-index` 进行比较。
* 当元素的层叠水平一致、层叠顺序相同的时候，在DOM流中处于后面的元素会覆盖前面的元素。

#### 例子

##### 例子一
没有z-index的时候，按照从上到下的顺序。
```html
<div style="position:absolute;width:400px; height:400px;background-color:blue;">
  <div style="width:200px; height:200px;background-color:green"></div>
</div>
<div style="position:absolute;top:50px;left:50px;width:400px; height:400px;background-color:red">
  <div style="width:200px; height:200px;background-color:yellow"></div>
</div>
```

![z-index1](images/z-index01.png)
---
##### 例子二

蓝色的父元素创造了自己的层叠上下文。
```html
<div style="position:absolute;width:400px; height:400px;background-color:blue;z-index:1">
  <div style="width:200px; height:200px;background-color:green"></div>
</div>
<div style="position:absolute;top:50px;left:50px;width:400px; height:400px;background-color:red">
  <div style="width:200px; height:200px;background-color:yellow"></div>
</div>
```

![](images/z-index02.png)

---
##### 例子三

蓝色父元素创造了自己的层叠上下文并且z-index小于红色，其子元素绿色元素虽然拥有大的z-index，但是也没有用。
```html
<div style="position:absolute;width:400px; height:400px;background-color:blue;z-index:3">
  <div style="width:200px; height:200px;background-color:green;z-index:6"></div>
</div>
<div style="position:absolute;top:50px;left:50px;width:400px; height:400px;background-color:red;z-index:4">
  <div style="width:200px; height:200px;background-color:yellow;z-index:2"></div>
</div>
```

![](images/z-index01.png)

---

##### 例子四
```css
* {
  margin: 0;
}

html {
  padding: 20px;
  font: 12px/20px Arial, sans-serif;
}

div {
  opacity: 0.7;
  position: relative;
}

h1 {
  font: inherit;
  font-weight: bold;
}

#div1,
#div2 {
  border: 1px dashed #696;
  padding: 10px;
  background-color: #cfc;
}

#div1 {
  z-index: 5;
  margin-bottom: 190px;
}

#div2 {
  z-index: 2;
}

#div3 {
  z-index: 4;
  opacity: 1;
  position: absolute;
  top: 40px;
  left: 180px;
  width: 330px;
  border: 1px dashed #900;
  background-color: #fdd;
  padding: 40px 20px 20px;
}

#div4,
#div5 {
  border: 1px dashed #996;
  background-color: #ffc;
}

#div4 {
  z-index: 6;
  margin-bottom: 15px;
  padding: 25px 10px 5px;
}

#div5 {
  z-index: 1;
  margin-top: 15px;
  padding: 5px 10px;
}

#div6 {
  z-index: 3;
  position: absolute;
  top: 20px;
  left: 180px;
  width: 150px;
  height: 125px;
  border: 1px dashed #009;
  padding-top: 125px;
  background-color: #ddf;
  text-align: center;
}
```

```html
<div id="div1">
  <h1>Division Element #1</h1>
  <code>position: relative;<br/>
      z-index: 5;</code>
</div>

<div id="div2">
  <h1>Division Element #2</h1>
  <code>position: relative;<br/>
      z-index: 2;</code>
</div>

<div id="div3">
  <div id="div4">
    <h1>Division Element #4</h1>
    <code>position: relative;<br/>
        z-index: 6;</code>
  </div>

  <h1>Division Element #3</h1>
  <code>position: absolute;<br/>
      z-index: 4;</code>

  <div id="div5">
    <h1>Division Element #5</h1>
    <code>position: relative;<br/>
        z-index: 1;</code>
  </div>

  <div id="div6">
    <h1>Division Element #6</h1>
    <code>position: absolute;<br/>
        z-index: 3;</code>
  </div>
</div>
```

![](images/z-index04.png)

---

reference：
[搞懂 Z-index 的所有细节](https://www.jianshu.com/p/cdd90d28380b)
https://developer.mozilla.org/en-US/docs/Web/CSS/CSS_Positioning/Understanding_z_index/The_stacking_context
https://developer.mozilla.org/zh-CN/docs/Web/CSS/z-index

### 连续媒体 continuous media
连续媒体是源与终点之间的时间联系数据。
最常见的连续媒体就是音频和视频。
连续媒体可以是实时的，也可以是流的。
reference:https://developer.mozilla.org/en-US/docs/Glossary/Continuous_Media

### flex-box 

flex布局是CSS3新增的一种布局方式，我们可以通过将一个元素的display属性值设置为flex从而使它成为一个flex容器，它的所有子元素都会成为它的项目。

一个容器默认有两条轴，一个是水平的主轴，一个是与主轴垂直的交叉轴。我们可以使用flex-direction来指定主轴的方向。我们可以使用justify-content来指定元素在主轴(x轴)上的排列方式，使用align-items来指定元素在交叉轴(y轴)上的排列方式。还可以使用flex-wrap来规定当一行排列不下时的换行方式。

对于容器中的item，我们可以使用order属性来指定项目的排列顺序，还可以使用flex-grow来指定当排列空间有剩余的时候，项目的放大比例。还可以使用flex-shrink来指定当排列空间不足时，项目的缩小比例。

在container上存在六个属性

- flex-direction 属性决定主轴的方向（即item的排列方向）。
- flex-wrap 属性定义，如果一条轴线排不下，如何换行。
- flex-flow 属性是 flex-direction 属性和 flex-wrap 属性的简写形式，默认值为 rownowrap。
- justify-content 属性定义了item在主轴上的对齐方式。
- align-items 属性定义item在交叉轴上如何对齐。
- align-content 属性定义了多根轴线的对齐方式。如果item只有一根轴线，该属性不起作用。

在item上也有六个属性

- order 属性定义item的排列顺序。数值越小，排列越靠前，默认为 0。
- flex-grow 属性定义item的放大比例，默认为 0，即如果存在剩余空间，也不放大。
- flex-shrink 属性定义了item的缩小比例，默认为 1，即如果空间不足，该item将缩小。
- flex-basis 属性定义了在分配多余空间之前，item占据的主轴空间。浏览器根据这个属性，计算主轴是否有多余空间。它的默认值为 auto，即item的本来大小。
- flex 属性是 flex-grow，flex-shrink 和 flex-basis 的简写，默认值为 01auto。
- align-self 属性允许单个item有与其他item不一样的对齐方式，可覆盖 align-items 属性。默认值为auto，表示继承父元素的 align-items 属性，如果没有父元素，则等同于 stretch。

### BFC 的概念, 哪些元素可以触发 BFC

> BFC 即 Block Formatting Context (块级格式化上下文)， 是 Web 页面的可视化 CSS 渲染的一部分，是块盒子的布局过程发生的区域，也是浮动元素与其他元素交互的区域。

简单来说就是一个封闭的黑盒子，里面元素的布局不会影响外部。
下列方式会创建块格式化上下文：

- 根元素(`<html>`)
- 浮动元素（元素的 float 不是 none）
- 绝对定位元素（元素的 position 为 absolute 或 fixed）
- 行内块元素（元素的 display 为 inline-block）
- 表格单元格（元素的 display 为 table-cell，HTML 表格单元格默认为该值）
- 表格标题（元素的 display 为 table-caption，HTML 表格标题默认为该值）
- 匿名表格单元格元素（元素的 display 为 table、table-row table-row-group、table-header-group、table-footer-group（分别是- HTML table、row、tbody、thead、tfoot 的默认属性）或 inline-table）
- overflow 值不为 visible 的块元素
- display 值为 flow-root 的元素
- contain 值为 layout、content 或 paint 的元素
- 弹性元素（display 为 flex 或 inline-flex 元素的直接子元素）
- 网格元素（display 为 grid 或 inline-grid 元素的直接子元素）
- 多列容器（元素的 column-count 或 column-width 不为 auto，包括 - column-count 为 1）
- column-span 为 all 的元素始终会创建一个新的 BFC，即使该元素没有包裹在一个多列容器中（标准变更，Chrome bug）。

格式化上下文影响布局，通常，我们会为定位和清除浮动创建新的 BFC，而不是更改布局，因为它将：
- 包含内部浮动
  - 使用 overflow: auto
  - 使用 display: flow-root
- 排除外部浮动
  - 使用 display: flow-root
- 阻止外边距重叠
  - 使用 overflow: hidden

### IFC 行内格式化上下文
行内格式化上下文是一个网页的渲染结果的一部分。其中，各行内盒子（inline boxes）一个接一个地排列，其排列顺序根据书写模式（writing-mode）的设置来决定：IFC的高度，高度由line-height的计算结果决定，因此比所有包含在内的盒子都要高；当一行不够放置的时候会自动切换到下一行。

对于水平书写模式，各个框从左边开始水平地排列
对于垂直书写模式，各个框从顶部开始水平地排列

### display 有哪些值？说明他们的作用

> display 属性可以设置元素的显示类型 display types。元素的外部显示类型 outer display types 将决定该元素在流式布局中的表现（块级或内联元素）；元素的内部显示类型 inner display types 可以控制其子元素的布局（例如：flow layout，grid 或 flex）。

- block
  块类型。默认宽度为父元素宽度，可设置宽高，换行显示。
- none
  元素不显示，并从文档流中移除。这会导致该元素及其所有子代元素不再被屏幕阅读技术 screen reading technology 访问。
- inline
  行内元素类型。默认宽度为内容宽度，不可设置宽高，同行显示。
- inline-block
  默认宽度为内容宽度，可以设置宽高，同行显示。
- list-item
  像块类型元素一样显示，并添加样式列表标记。
- table
  此元素会作为块级表格来显示。
- inherit
  规定应该从父元素继承 display 属性的值。

reference:https://developer.mozilla.org/zh-CN/docs/Web/CSS/display


### float 的元素display 是什么

参考文档：https://juejin.cn/post/6911682147000057870

```css
float 和 absolute 会改变元素的 display 为 inline-block
```

举个例子验证一下

```html
span 是个行内元素，对行内元素设置宽高是不生效的，但是再加上了 float 属性之后，发现宽高生效了， 因此可以判断出 span
由一个行内元素变成了一个块级/行内块级元素。 进一步判断为何是行内块元素？如果是块级元素应该独占一行，实际并不是，因而是
**行内块元素**

<span style="width: 100px; height: 100px; background-color: #ccc;">123</span>
<span>456</span>
```

### 替换元素(replaced element)
替换元素指那些展示内容不由css控制的元素。它们的内容不受当前文档的样式的影响。CSS 可以影响可替换元素的位置，但不会影响到替换元素自身的内容。

#### 替换元素范围
典型的替换元素有
`<iframe>`、`<video>`、`<embed>`、`<img>`
特定情况下可作为替换元素的有
`<option>`、`<audio>`、`<canvas>`、`<object>`、`object`、`<applet>`

`<input type="image">`因为类似`<img>`也会被算作替换元素，但其他type的input不会算作替换元素。
用 `content` 属性插入的对象是匿名的替换元素。它们并不存在于 HTML 标记中，因此是“匿名的”。

#### 替换元素特点
* CSS 在某些情况下会对替换元素做一些特殊处理，比如计算外边距（margin）和一些 auto 的值。
* 有一部分替换元素具有内部尺寸和定好的基线，这会被一些 CSS 属性用到，例如 `vertical-align: baseline`, 非替换元素的基线定义为字符的下边缘，而替换元素的基线定义为元素的下边缘。只有替换元素才能具有这种自带值。
* 在Web中，很多替换元素在没有明确尺寸设定的情况下，其默认的尺寸（不包括边框）是300像素×150像素，如`<video>`、`<iframe>`或者`<canvas>`等，也有少部分替换元素为0像素，如`<img>`。
* 所有的替换元素都是inline元素，也就是替换元素和非替换元素、文字都是可以在一行显示的。但是，替换元素默认的display值却是不一样的，有的是inline，有的是inline-block。
* 替换元素拥有内置宽高，它们可以设置`width`和`height`。

#### 控制`content-box`中的对象位置
`object-fit`指定替换元素的内容对象在元素盒区域中的大小。
`object-position`指定替换元素的内容对象在元素盒区域中的位置。

#### 样式计算
替换元素的尺寸从内而外分为3类：固有尺寸、HTML尺寸和CSS尺寸。
（1）固有尺寸指的是替换内容原本的尺寸。例如，图片、视频作为一个独立文件存在的时候，都是有着自己的宽度和高度的。
（2）HTML尺寸只能通过HTML原生属性改变，这些HTML原生属性包括`<img>`的width和height属性、`<input>`的size属性、`<textarea>`的cols和rows属性等。
（3）CSS尺寸特指可以通过CSS的width和height或者max-width/min-width和max-height/minheight设置的尺寸，对应盒尺寸中的content box。

计算规则具体如下：
优先级： 固有尺寸 < HTML尺寸 < CSS尺寸
但如果“固有尺寸”含有固有的宽高比例，同时仅设置了宽度或仅设置了高度，则元素依然按照固有的宽高比例显示。
如果都没有设置，则最终宽度表现为300像素，高度为150像素。

#### 匿名替换元素
CSS 的 content 属性用于在元素的 ::before 和 ::after 伪元素中插入内容。使用 content 属性插入的内容都是匿名的替换元素。

使用content生成的文本是无法选中、无法复制的，好像设置了user select:none声明一般，但是普通元素的文本却可以被轻松选中。同时，content生成的文本无法被屏幕阅读设备读取，也无法被搜索引擎抓取，因此，千万不要自以为是地把重要的文本信息使用content属性生成，因为这对可访问性和SEO都很不友好。
content生成的内容不能左右:empty伪类。
content动态生成值无法获取。

reference:
https://developer.mozilla.org/en-US/docs/Web/CSS/Replaced_element
https://developer.mozilla.org/zh-CN/docs/Web/CSS/content

### inline-block、inline 和 block 的区别

Block 是块级元素，其前后都会有换行符，能设置宽度，高度，margin/padding 水平垂直方向都有效。

Inline：设置 width 和 height 无效，margin 在竖直方向上无效，padding 在水平方向垂直方向都有效，前后无换行符

Inline-block：能设置宽度高度，margin/padding 水平垂直方向 都有效，前后无换行符


### visibility
三个取值

#### visible
元素正常显示
#### hidden
隐藏元素，但是其他元素的布局不改变，且此元素无法被focus。但若将其子元素设为 visibility: visible，则该子元素依然可见。

#### collapse
collapse对于不同元素有不同效果。

- 对于 <table> 行、列、列组和行组，表格的行或列将被隐藏并且不占用任何空间（与表格的行/列上的 `display: none` 效果相当）。但是，计算其他行和列的大小时，仍会像显示折叠行或列中的单元格一样进行计算。此值允许从表中快速删除行或列，而不强制重新计算整个表的宽度和高度。注意 `visibility:collapse` 会改变表格的布局，嵌套在其被折叠的单元格中的表格也会同样被折叠，除非专门为此嵌套表格指定 `visibility: visible`。
- 折叠的弹性项目和<ruby>将被隐藏，它们覆盖的空间会被删除。
- 对于其他元素， collapse 处理和 hidden 一样。但是要注意有些现代浏览器对 `visibility: collapse` 不支持或是不完全支持。所以对于其他元素有时也不会正确地将它显示成 `visibility: hidden` 的效果。

reference:https://developer.mozilla.org/en-US/docs/Web/CSS/visibility

### `visibility: hidden`, `opacity: 0`, `display: none`的区别

opacity: 0，该元素隐藏起来了，但不会改变页面布局，并且，如果该元素已经绑定一些事件，如 click 事件，那么点击该区域，也能触发点击事件的；

visibility: hidden，该元素隐藏起来了，但不会改变页面布局，但是不会触发该元素已经绑定的事件；

display: none，把元素隐藏起来，并且会改变页面布局，可以理解成在页面中把该元素删除掉一样。

### `width:auto` 和 `width:100%`的区别

`width:100%`会使元素box的宽度等于父元素的content box的宽度。
`width:auto`会使元素撑满整个父元素，margin、border、padding、content区域会自动分配水平空间。

### 设备像素、css 像素、设备独立像素、dpr、ppi 之间的区别
#### 设备像素
设备像素指的是物理像素，一般手机的分辨率指的就是设备像素，一个设备的设备像素是不可变的。从屏幕在工厂生产出的那天起，它上面设备像素点就固定不变了，单位 pt。

#### css像素
css像素和设备独立像素是等价的，不管在何种分辨率的设备上，css像素的大小应该是一致的，css像素是一个相对单位，它是相对于设备像素的，而设备像素可以变化。一个css像素的大小取决于页面缩放程度和dpr的大小。单位px。

px最终会受到ppi,dpr,dpi的影响。

DPR = 设备像素 / CSS像素 = 屏幕横向设备像素 / 理想视口的宽
CSS像素 = 设备独立像素 = 逻辑像素

##### ppi
每英寸像素(ppi, pixel per inch)指的是每英寸的所拥有的像素(pixel)数目，即像素密度。ppi越大，屏幕的分辨率越大。在显示器上，表示每英寸多少物理像素及显示器设备的点距。数值越高，代表显示屏能够以越高的密度显示图像。

##### dpr
设备像素比(dpr, device pixel ratio)指的是设备像素和设备独立像素的比值。即未缩放状态下，设备像素和 CSS 像素的初始比例关系，也可以解释为默认缩放比例。通俗来说，它是指在开发中1个 CSS 像素占用多少设备像素，如 dpr=2 代表1个 CSS 像素用2x2个设备像素来绘制。一般的pc屏幕，dpr=1。在iphone4时，苹果推出了retina屏幕，它的dpr为2。屏幕的缩放会改变dpr的值。

##### dpi
显示密度 DPI: 每英寸多少点。

reference: https://www.cnblogs.com/libin-1/p/7148377.html

### viewport
#### 视口基础知识
在电脑图形学里面，视口代表了一个可看见的多边形区域（通常来说是矩形）。在浏览器范畴里，它代表的是浏览器中网站可见内容的部分。视口外的内容在被滚动进来前都是不可见的。
一些移动设备和其他窄屏幕在通常比屏幕宽的虚拟窗口或视口中渲染页面，然后将渲染结果缩小，以便一次全部看到。然后，用户可以平移和缩放以查看页面的不同区域。这样做是因为并非所有页面都针对移动设备进行了优化，并且在以较小的视口宽度呈现时会中断（或至少看起来很糟糕）。这个虚拟视口是一种让非移动优化网站在窄屏设备上看起来更好的方法。
然而，这种机制对于使用媒体查询针对窄屏幕进行优化的页面来说并不是那么好——例如，如果虚拟视口为 980 像素，则永远不会使用以 640 像素或 480 像素或更小的尺寸启动的媒体查询，从而限制了此类的有效性响应式设计技术。视口元标记缓解了窄屏设备上的虚拟视口问题。


最常见的视口
```html
<meta name="viewport" content="width=device-width, initial-scale=1" />
```
并非所有设备都具有相同的宽度；您应该确保您的页面在各种屏幕尺寸和方向上都能正常工作。

`<meta>` 标签里`viewport`的基本属性包括：

* `width`
控制视口的大小。它可以设置为特定数量的像素，例如 width=600 或特殊值 device-width，即 100vw，或视口宽度的 100%。最小值：1。最大值：10000。负值：忽略。

* `height`
控制视口的大小。它可以设置为特定数量的像素，例如 height=400 或特殊值 device-height，即 100vh，或视口高度的 100%。最小值：1。最大值：10000。负值：忽略。

* `initial-scale`
控制第一次加载页面时的缩放级别。最小值：0.1。最大值：10。默认值：1。负值：忽略。

* `minimum-scale`
控制页面上允许的缩小程度。最小值：0.1。最大值：10。默认值：0.1。负值：忽略。

* `maximum-scale`
控制页面允许放大多少。任何小于 3 的值都无法访问。最小值：0.1。最大值：10。默认值：10。负值：忽略。

* `user-scalable`
控制页面上是否允许放大和缩小操作。有效值：0、1、yes 或 no。默认值：1，与 yes 相同。将该值设置为 0（与否相同）违反了 Web 内容可访问性指南 (WCAG)。但是，使用 user-scalable=no 可能会给有视力障碍（例如低视力）的用户带来可访问性问题。 WCAG 要求至少 2 倍缩放；但是，最佳做法是启用 5 倍变焦。

#### 屏幕密度
许多浏览器可以通过为每个css像素转换多个硬件像素来以更小的物理尺寸显示它们的页面。在高 dpi 屏幕上，initial-scale=1 的页面将被浏览器有效地缩放。它们的文本将平滑而清晰，但它们的位图图像可能无法利用全屏分辨率。为了在这些屏幕上获得更清晰的图像，Web 开发人员可能希望以比最终尺寸更高的比例设计图像或整个布局，然后使用 CSS 或视口属性将它们缩小。
默认像素比率取决于显示密度。在密度小于 200dpi 的显示器上，该比率为 1.0。在密度在 200 到 300dpi 之间的显示器上，该比率为 1.5。对于密度超过 300dpi 的显示器，该比率是整数下限（密度/150dpi）。请注意，只有当视口比例等于 1 时，默认比例才为 true。否则，CSS 像素和设备像素之间的关系取决于当前缩放级别。

#### 视口宽度和屏幕宽度
站点可以将其视口设置为特定大小。例如，定义“width=320, initial-scale=1”可用于在纵向模式下精确地适合小型手机显示屏。当浏览器不以较大尺寸呈现页面时，这可能会导致问题。为了解决这个问题，如果需要，浏览器将扩展视口宽度以按请求的比例填充屏幕。这在大屏幕设备上特别有用。
对于设置初始或最大比例的页面，这意味着 width 属性实际上转换为最小视口宽度。 例如，如果您的布局需要至少 500 像素的宽度，那么您可以使用以下标记。当屏幕宽度超过 500 像素时，浏览器会扩大视口（而不是放大）以适应屏幕：
```html
<meta name="viewport" content="width=500, initial-scale=1" />
```
#### 三种viewport
##### 可视视口 visual viewport
视口当前可见的部分叫做可视视口（visual viewport）。

##### 布局视口 layout viewport
如果把移动设备上浏览器的可视区域设为viewport的话，某些网站就会因为viewport太窄而显示错乱，所以这些浏览器就决定默认情况下把viewport设为一个较宽的值，比如常见的980px，这样的话即使是那些为桌面设计的网站也能在移动浏览器上正常显示。这个浏览器默认的viewport叫做layout viewport。layout viewport的宽度一般是大于visual viewport的宽度的。当用户缩小浏览器缩放比例时，布局视口不变，而可视视口变小了。visual viewport和layout viewport的关系，就像是我们通过窗户看外面的风景，视觉视口就是窗户，而外面的风景就是布局视口中的网页内容。

##### 理想视口 ideal viewport
ideal viewport是最适合移动设备的viewport，ideal viewport的宽度等于移动设备的屏幕宽度，只要在css中把某一元素的宽度设为ideal viewport的宽度（单位用
px），那么这个元素的宽度就是设备屏幕的宽度了，也就是宽度为100%的效果。ideal viewport的意义在于，无论在何种分辨率的屏幕下，那些针对ideal viewport而设计的网站，不需要用户手动缩放，也不需要出现横向滚动条，都可以完美的呈现给用户。

reference: https://developer.mozilla.org/en-US/docs/Glossary/Viewport
https://developer.mozilla.org/en-US/docs/Web/HTML/Viewport_meta_tag

### vw 和 vh 的概念

vw（Viewport Width）、vh(Viewport Height)是基于视图窗口的单位，是 css3 的一部分，基于视图窗口的单位，除了 vw、vh 还有 vmin、vmax。

- vw:1vw 等于视口宽度的 1%
- vh:1vh 等于视口高度的 1%
- vmin: 选取 vw 和 vh 中最小的那个,即在手机竖屏时，1vmin=1vw
- vmax:选取 vw 和 vh 中最大的那个 ,即在手机竖屏时，1vmax=1vh

### `display`,`position`和`float`的相互关系？
（1）首先我们判断display属性是否为none，如果为none，则position和float属性的值不影响元素最后的表现。
（2）然后判断position的值是否为absolute或者fixed，如果是，则float属性失效，并且display的值应该被设置为table或者block，具体转换需要看初始转换值。
（3）如果position的值不为absolute或者fixed，则判断float属性的值是否为none，如果不是，则display的值则按上面的规则转换。注意，如果position的值为relative并且float属性的值存在，则relative相对于浮动后的最终位置定位。
（4）如果float的值为none，则判断元素是否为根元素，如果是根元素则display属性按照上面的规则转换，如果不是，则保持指定的display属性值不变。
总的来说，可以把它看作是一个类似优先级的机制，"position:absolute"和"position:fixed"优先级最高，有它存在的时候，浮动不起作用，'display'的值也需要调整；其次，元素的'float'特性的值不是"none"的时候或者它是根元素的时候，调整'display'的值；最后，非根元素，并且非浮动元素，并且非绝对定位的元素，'display'特性值同设置值。

reference: https://www.cnblogs.com/jackyWHJ/p/3756087.html

### margin合并
两个块级元素的margin有时会被合并为一个，且为两个块级元素margin的较大值。

example
```css
.box {
  width: 200px;
  height: 200px;
}

.box1 {
  margin: 0 0 100px 0;
}

.box2 {
  margin: 200px 0 0 0;
}
```

```html
<div>
  <div class="box box1"> margin 100px</div>
  <div class="box box2"> margin 200px</div>
</div>
```

产生合并的必要条件：margin必须是邻接的。
而根据w3c规范，两个margin是邻接的必须满足以下条件：
• 必须是处于常规文档流（非float和绝对定位）的块级盒子，并且处于同一个BFC当中。
• 没有线盒，没有空隙，没有padding和border将他们分隔开
• 都属于垂直方向上相邻的外边距，可以是下面任意一种情况
• 元素的margin-top与其第一个常规文档流的子元素的margin-top
• 元素的margin-bottom与其下一个常规文档流的兄弟元素的margin-top
• height为auto的元素的margin-bottom与其最后一个常规文档流的子元素的margin-bottom
• 高度为0并且最小高度也为0，不包含常规文档流的子元素，并且自身没有建立新的BFC的元素的margin-top和margin-bottom

margin合并的3种场景：
（1）相邻兄弟元素margin合并。
解决办法：
• 设置块状格式化上下文元素（BFC），即开启BFC

（2）父级和第一个/最后一个子元素的margin合并。
解决办法：
对于margin-top合并，可以进行如下操作（满足一个条件即可）：
• 父元素设置为块状格式化上下文元素；即开启BFC
• 父元素设置border-top值；
• 父元素设置padding-top值；
• 父元素和第一个子元素之间添加内联元素进行分隔。
对于margin-bottom合并，可以进行如下操作（满足一个条件即可）：
• 父元素设置为块状格式化上下文元素；
• 父元素设置border-bottom值；
• 父元素设置padding-bottom值；
• 父元素和最后一个子元素之间添加内联元素进行分隔；
• 父元素设置height、min-height或max-height。

（3）空块级元素的margin合并。
解决办法：
• 设置垂直方向的border；
• 设置垂直方向的padding；
• 里面添加内联元素（直接Space键空格是没用的）；
• 设置height或者min-height。

### `all` 属性
all属性实际上是所有CSS属性的缩写，表示所有的CSS属性都怎样怎样，但是，不包括`unicode-bidi`和`direction`
这两个CSS属性。支持三个CSS通用属性值，initial,inherit,unset。
initial是初始值的意思，也就是该元素除了unicode-bidi和direction以外的CSS属性都使用属性的默认初始值。
inherit是继承的意思，也就是该元素除了unicodebidi和direction以外的CSS属性都继承父元素的属性值。
unset是取消设置的意思，也就是当前元素浏览器或用户设置的CSS忽略，然后如果是具有继承特性的CSS，如color，则使用继承值；如果是没有继承特性的CSS属性，如background-color，则使用初始值。

### `hasLayout` 属性
hasLayout是IE特有的一个属性。很多的IE下的css bug都与其息息相关。在IE中，一个元素要么自己对自身的内容进行计算大小和组织，要么依赖于父元素来计算尺寸和组织内容。当一个元素的hasLayout属性值为true时，它负责对自己和可能的子孙元素进行尺寸计算和定位。虽然这意味着这个元素需要花更多的代价来维护自身和里面的内容，而不是依赖于祖先元素来完成这些工作。

### font-style 属性中 italic 和 oblique 的区别
italic本质上是草书，相较于无样式字体使用更少的水平空间。而oblique只是单纯地让文字倾斜。如果当前字体没有对应的斜体字体，那么斜体（italic）和倾斜体（oblique）都会通过人工倾斜常规字体的字形来模拟。（通过字体合成来控制此行为）

### 图片格式
<table>
  <th>
    <td>有损/无损</td>
    <td>索引色/直接色</td>
    <td>点阵图/矢量图</td>
    <td>其他特点</td>
  </th>
  <tr>
    <td>BMP</td>
    <td>无损</td>
    <td>均支持</td>
    <td>点阵图</td>
    <td>文件较大，是Windows操作系统中的标准图像文件格式。</td>
  </tr>
  <tr>
    <td>GIF</td>
    <td>无损</td>
    <td>索引色</td>
    <td>点阵图</td>
    <td>文件小，仅支持8bit的索引色。支持动画以及透明。</td>
  </tr>
  <tr>
    <td>JPG</td>
    <td>有损</td>
    <td>直接色</td>
    <td>点阵图</td>
    <td>文件较大，适合存储照片。但图片会模糊。</td>
  </tr>
  <tr>
    <td>PNG-8</td>
    <td>无损</td>
    <td>索引色</td>
    <td>点阵图</td>
    <td>在相同的图片效果下，PNG-8比GIF更小。支持透明度的调节。</td>
  </tr>
  <tr>
    <td>PNG-24</td>
    <td>无损</td>
    <td>直接色</td>
    <td>点阵图</td>
    <td>比BMP小得多。</td>
  </tr>
  <tr>
    <td>SVG</td>
    <td>无损</td>
    <td>-</td>
    <td>矢量图</td>
    <td>适合用来绘制企业logo，icon。</td>
  </tr>
  <tr>
    <td>WEBP</td>
    <td>均支持</td>
    <td>直接色</td>
    <td>点阵图</td>
    <td>文件大小相对较小。适合用来绘制企业logo，icon。</td>
  </tr>
</table>

#### BMP
BMP(bitmap)，是无损的、既支持索引色也支持直接色的、点阵图。这种图片格式几乎没有对数据进行压缩，所以BMP格式的图片通常具有较大的文件大小。是Windows操作系统中的标准图像文件格式。

#### GIF
GIF(Graphics Interchange Format)是无损的、采用索引色的点阵图。采用LZW压缩算法进行编码。文件小，是GIF格式的优点，同时，GIF格式还具有支持动画以及透明的优点。但GIF格式仅支持8bit的索引色，所以GIF格式适用于对色彩要求不高同时需要文件体积较小的场景。

#### JPG
JPEG(Joint Photographic Experts Group)是有损的、采用直接色的点阵图。JPEG的图片的优点，是采用了直接色，得益于更丰富的色彩，JPEG非常适合用来存储照片，与GIF相比，JPEG不适合用来存储企业Logo、线框类的图。因为有损压缩会导致图片模糊，而直接色的选用，又会导致图片文件较GIF更大。

#### PNG-8
PNG(Portable Network Graphics)-8是无损的、使用索引色的点阵图。PNG是一种比较新的图片格式，是非常好的GIF格式替代者，在可能的
情况下，应该尽可能的使用PNG-8而不是GIF。因为在相同的图片效果下，PNG-8具有更小的文件体积。除此之外，PNG-8还支持透明度的调节，而GIF并不支持。现在，除非需要动画的支持，否则我们更应该使用PNG8。

#### PNG-24
PNG-24是无损的、使用直接色的点阵图。PNG-24的优点在于，它压缩了图片的数据，使得同样效果的图片，PNG-24格式的文件大小要比BMP小得多。当然，PNG24的图片还是要比JPEG、GIF、PNG-8大得多。

#### SVG
SVG(Scalable Vector Graphics)是无损的矢量图。SVG图片由直线和曲线以及绘制它们的方法组成。当放大一个SVG图片的时候，你看到的还是线和曲线，而不会出现像素点，不会失真。所以它非常适合用来绘制企业Logo、Icon等。

#### WEBP
WebP是谷歌开发的一种新图片格式，WebP同时支持有损和无损压缩，使用直接色的点阵图。相同质量的图片，WebP具有更小的文件体积。
* 在无损压缩的情况下，相同质量的WebP图片，文件大小要比PNG小26%；
* 在有损压缩的情况下，具有相同图片精度的WebP图片，文件大小要比JPEG小25%~34%；
* WebP图片格式支持图片透明度，一个无损压缩的WebP图片，如果要支持透明度只需要22%的格外文件大小。

但是目前只有Chrome浏览器和Opera浏览器支持WebP格式，兼容性不太好。

### style 标签写在 body 后与 body 前有什么区别？
由于浏览器以逐行方式对HTML文档进行解析，如果style写在最后，当解析到写在尾部的样式表（外联或写在style标签）会导致浏览器停止之前的渲染，等待加载且解析样式表完成之后重新渲染，在windows的IE下可能会出现FOUC现象（即样式失效导致的页面闪烁问题（结构解析完但样式还没有解析完））

### css预处理器与后处理器
#### 预处理器
CSS预处理器定义了一种新的语言，其基本思想是，用一种专门的编程语言，为CSS增加了一些编程的特性，将CSS作为目标生成文件，然后开发者就只要使用这种语言进行编码工作。
通俗的说，CSS预处理器用一种专门的编程语言，进行Web页面样式设计，然后再编译成正常的CSS文件。
预处理器例如：LESS、Sass、Stylus，用来预编译Sass或less ，增强了css代码的复用性，还有层级、mixin、变量、循环、函数等，具有很方便的UI组件模块化开发能力，极大的提高工作效率。

#### 后处理器
CSS后处理器是对CSS进行处理，并最终生成CSS的预处理器，它属于广义上的CSS预处理器。最典型的CSS后处理器是CSS压缩工具（如cleancss），只不过以前不会单独拿出来说。还有最近比较火的Autoprefixer，以CanIUse上的浏览器支持数据为基础，自动处理兼容性问题。
后处理器例如：PostCSS，通常被视为在完成的样式表中根据CSS规范处理CSS，让其更有效；目前最常做的是给CSS属性添加浏览器私有前缀，实现跨浏览器兼容性的问题。

### 使用 rem 布局的优缺点
优点：
在屏幕分辨率千差万别的时代，只要将rem与屏幕分辨率关联起来就可以实现页面的整体缩放，兼容性也非常好。

缺点：
（1）在奇葩的dpr设备上表现效果不太好，比如一些华为的高端机型用rem布局会出现错乱。
（2）使用iframe引用也会出现问题。
（3）rem在多屏幕尺寸适配上与当前两大平台的设计哲学不一致。即大屏的出现到底是为了看得又大又清楚，还是为了看的更多的问题。

### 首选最小宽度
首选最小宽度指的是元素最适合的最小宽度。
东亚文字（如中文）最小宽度为每个汉字的宽度。西方文字最小宽度由特定的连续的英文字符单元决定。并不是所有的英文字符都会组成连续单元，一般会终止于空格（普通空格）、短横线、问号以及其他非英文字符等。
如果想让英文字符和中文一样，每一个字符都用最小宽度单元，可以使用`word-break:breakall`。

### border的一些特殊性质
* `border-width`却不支持百分比。
* `border-style`的默认值是`none`，而不是`solid`。这也是单纯设置`border-width`或`border-color`没有边框显示的原因。
* `border-style:double`的表现规则：双线宽度永远相等，中间间隔±1。
* `border-color`默认颜色是元素内容的颜色而非black。
* 默认background背景图片是相对于padding-box定位的。

### overflow
`overflow`设置了元素溢出时所需的行为——即当元素的内容太大而无法适应它的块级格式化上下文时。

#### visible
内容不能被裁减并且可能渲染到padding-box外。

#### hidden
如果需要，内容将被裁减以适应padding-box。不提供滚动条，也不支持允许用户滚动（例如通过拖拽或者使用滚轮）。内容可以以编程的方式滚动（例如，通过设置 scrollLeft 等属性的值或 scrollTo() 方法）, 因此该元素仍然是一个滚动的容器。

一个设置了`overflow:hidden`声明的元素，假设同时存在border属性和padding属性，则当子元素内容超出容器宽度高度限制的时候，剪裁的边界是border-box的内边缘，而非padding-box的内边缘。

#### clip
类似于 hidden，内容将以元素的padding-box进行裁剪。`clip` 关键字禁止所有滚动，包括以编程方式的滚动。该盒子不是一个滚动的容器，并且不会启动新的格式化上下文。如果希望开启一个新的格式化上下文，你可以使用`display: flow-root`来这样做。

#### scroll
如果需要，内容将被裁减以适应padding-box。无论是否实际裁剪了任何内容，浏览器总是显示滚动条，以防止滚动条在内容改变时出现或者消失。打印机可能会打印溢出的内容。

> HTML中有两个标签默认可以产生滚动条，一个是根元素`<html>`，另一个是文本域`<textarea>`。不仅如此，滚动条会占用容器的可用宽度或高度。

#### auto
取决于用户代理。如果内容适应padding-box，它看起来与 `visible` 相同，但是仍然建立了一个新的块级格式化上下文。如果内容溢出，则桌面浏览器提供滚动条。

#### overlay
行为与 auto 相同，但是滚动条绘制在内容之上，而不是占据空间。

### 无依赖绝对定位
没有设置left/top/right/bottom属性值的绝对定位称为“无依赖绝对定位”。

### font-weight
`font-weight`属性指定了字体的粗细程度。
`font-weight`数值采取离散式定义（使用 100 的整倍数）。数值为实数，非 100 的整数倍的值将被四舍五入转换为 100 的整倍数。所以采用数值定义时，常选择100的整倍数。

#### normal
正常粗细。与 400 等值。

#### bold
加粗。与 700 等值。

#### lighter
比从父元素继承来的值更细 (处在字体可行的粗细值范围内)。

#### bolder
比从父元素继承来的值更粗 (处在字体可行的粗细值范围内)。

#### 回退机制
如果指定的权重值不可用，则使用以下规则来确定实际呈现的权重：

1. 如果指定的权重值在 400和 500之间（包括400和500），按升序查找指定值与500之间的可用权重。如果未找到匹配项，按降序查找小于指定值的可用权重；如果未找到匹配项，按升序查找大于500的可用权重。
2. 如果指定值小于400，按降序查找小于指定值的可用权重。如果未找到匹配项，按升序查找大于指定值的可用权重（先尽可能的小，再尽可能的大）。
3. 如果指定值大于500，按升序查找大于指定值的可用权重。如果未找到匹配项，按降序查找小于指定值的可用权重（先尽可能的大，再尽可能的小）。
   
以上策略意味着，如果一个字体只有 normal 和 bold 两种粗细值选择，指定粗细值为 100-500 时，实际渲染时将使用 normal，指定粗细值为 501-900 时，实际渲染时将使用 bold。

reference: https://developer.mozilla.org/en-US/docs/Web/CSS/font-weight
https://developer.mozilla.org/zh-CN/docs/Web/CSS/font-weight

### letter-spacing
`letter-spacing` 属性用于设置文本字符的间距表现。
默认值是`normal`，会按照当前字体的正常间距确定间距。和 0 不同的是，会让用户代理调整文字之间空间来对齐文字。
某些书面语言不应应用任何字母间距。例如，使用阿拉伯文字的语言希望字母连接来保持视觉连接。而应用字母间距将导致文本看起来损坏。

reference: 
https://developer.mozilla.org/zh-CN/docs/Web/CSS/letter-spacing
https://developer.mozilla.org/en-US/docs/Web/CSS/letter-spacing

## 应用
### 初始化css样式的目的
因为浏览器的兼容问题，不同浏览器对有些标签的默认值是不同的，如果没对CSS初始化往往会出现浏览器之间的页面显示差异。
当然，初始化样式会对SEO(Search Engine Optimization)有一定的影响，所以需要力求影响最小的情况下初始化。
最简单的初始化方法：
```css
* {padding:0;margin:0;}
```
但是这个方法由于需要把所有的标签都遍历一遍，当网站较大时，样式比较多，这样写就大大的加强了网站运行的负载，会使网站加载的时候需要很长时间，因此一般大型的网站都有分层次的一套初始化样式。

淘宝的样式初始化代码：
```css
body,
h1,
h2,
h3,
h4,
h5,
h6,
hr,
p,
blockquote,
dl,
dt,
dd,
ul,
ol,
li,
pre,
form,
fieldset,
legend,
button,
input,
textarea,
th,
td {
  margin: 0;
  padding: 0;
}

body,
button,
input,
select,
textarea {
  font: 1 2px/1.5tahoma, arial, \5b8b\4f53;
}

h1,
h2,
h3,
h4,
h5,
h6 {
  font-size: 100%;
}

address,
cite,
dfn,
em,
var {
  font-style: normal;
}

code,
kbd,
pre,
samp {
  font-family: couriernew, courier, monospace;
}

small {
  font-size: 12px;
}

ul,
ol {
  list-style: none;
}

a {
  text-decoration: none;
}

a:hover {
  text-decoration: underline;
}

sup {
  vertical-align: text-top;
}

sub {
  vertical-align: text-bottom;
}

legend {
  color: #000;
}

fieldset,
img {
  border: 0;
}

button,
input,
select,
textarea {
  font-size: 100%;
}

table {
  border-collapse: collapse;
  border-spacing: 0;
}
```

### CSS 清除浮动
float 属性指定一个元素应沿其容器的左侧或右侧放置，允许文本和内联元素环绕它。该元素从网页的正常流动（文档流）中移除，但仍然保持部分的流动性。

浮动元素可以左右移动，直到遇到另一个浮动元素或者遇到它外边缘的包含框。浮动框不属于文档流中的普通流，当元素浮动之后，不会影响块级元素的布局，只会影响内联元素布局。此时文档流中的普通流就会表现得该浮动框不存在一样的布局模式。当包含框的高度小于浮动框的时候，此时就会出现“高度塌陷”。因此需要清除浮动。

I. 利用clear属性
clear 属性指定一个元素是否必须移动 (在清除浮动后) 到在它之前的浮动元素下面。clear 属性适用于浮动和非浮动元素。

当应用于非浮动块时，它将非浮动块的边框边界移动到所有相关浮动元素外边界的下方。这个非浮动块的顶部外边距会折叠。
另一方面，两个浮动元素的垂直外边距将不会折叠。当应用于浮动元素时，它将底部元素的外边界边缘移动到所有相关的浮动元素外边界边缘的下方。这会影响后面浮动元素的布局，因为后面的浮动元素的位置无法高于它之前的元素。
要被清除的相关浮动元素指的是在相同块级格式化上下文中的前置浮动。

clear 属性规定元素盒子的边不能和浮动元素相邻。该属性只能影响使用清除的元素本身，不能影响其他元素。换而言之，如果已经存在浮动元素的话，那么该元素就不会像原本元素一样受其影响了。


i. 额外标签法
   > 在需要清除浮动的元素后面添加一个空白标签，设置类名 clear，设置`clear: both;`即可
II. 利用BFC
i. 父级元素添加`overflow: hidden;`
ii. 父元素 `display：table`
iii. 伪元素清除浮动

如果一个元素里只有浮动元素，那它的高度会塌陷为 0。如果你想要它自适应即包含所有浮动元素，那你需要清除它的子元素。比如clearfix方法，对需要清除浮动的元素添加一个 clearfix 类名，设置样式如下：

```css
.clearfix:after {
  /*正常浏览器 清除浮动*/
  content: '';
  display: block;
  clear: both;
}
```


zoom属性是IE浏览器的专有属性，它可以设置或检索对象的缩放比例。解决ie下比较奇葩的bug。譬如外边距（margin）的重叠，浮动清除，触发ie的haslayout属性等。
当设置了zoom的值之后，所设置的元素就会扩大或者缩小，高度宽度就会重新计算了，这里一旦改变zoom值时其实也会发生重新渲染，运用这个原理，也就解决了ie下子元素浮动时候父元素不随着自动扩大的问题。
zoom属性是IE浏览器的专有属性，火狐和老版本的webkit核心的浏览器都不支持这个属性。目前非ie不支持这个属性，但可以通过css3里面的动画属性scale进行缩放。然而，zoom现在已经被逐步标准化，出现在CSS3.0规范草案中。

```css
.clearfix {
  *zoom: 1;
  /*zoom 1 就是ie6 清除浮动方式  * ie7以下的版本才能识别 其他浏览器都不执行(略过)*/
}
```

### 清除浮动的原理
clear 属性清除浮动


```css
#container::after {
  content: "";
  display: block;
  clear: both;
}
```

### 脱离文档流的方式

- float
- position: absolute
- position: fixed

### 了解重绘和重排吗，知道怎么去减少重绘和重排吗，让文档脱离文档流有哪些方法

DOM 的变化影响到了预算内宿的几何属性比如宽高，浏览器重新计算元素的几何属性，其他元素的几何属性也会受到影响，浏览器需要重新构造渲染书，这个过程称之为重排，浏览器将受到影响的部分重新绘制在屏幕上 的过程称为重绘，引起重排重绘的原因有：

- 添加或者删除可见的 DOM 元素;
- 元素尺寸位置的改变;
- 浏览器页面初始化;
- 浏览器窗口大小发生改变，重排一定导致重绘，重绘不一定导致重排;

减少重绘重排的方法有：

- 不在布局信息改变时做 DOM 查询，
- 使用 csstext,className 一次性改变属性
- 使用 fragment
- 对于多次重排的元素，比如说动画。使用绝对定位脱离文档流，使其不影响其他元素
- "editor.renderIndentGuides": true

### 经常遇到的浏览器的兼容性有哪些？原因，解决方法是什么，常用 hack 的技巧

（1）png24位的图片在iE6浏览器上出现背景
解决方案：做成PNG8，也可以引用一段脚本处理。

（2）IE6双边距bug：在IE6下，如果对元素设置了浮动，同时又设置了margin-left或margin-right，margin值会加倍。
```css
#box{float:left;width:10px;margin:00010px;}
```
这种情况之下IE会产生20px的距离
解决方案：在float的标签样式控制中加入_display:inline;将其转化为行内属性。(_这个符号只有ie6会识别)

（3）渐进识别的方式，从总体中逐渐排除局部。
首先，巧妙的使用"\9"这一标记，将IE游览器从所有情况中分离出来。
接着，再次使用"+"将IE8和IE7、IE6分离开来，这样IE8已经独立识别。
```css
.bb{
background-color:#f1ee18;/*所有识别*/
.background-color:#00deff\9;/*IE6、7、8识别*/
+background-color:#a200ff;/*IE6、7识别*/
_background-color:#1e0bd1;/*IE6识别*/
}
```

（4）IE下，可以使用获取常规属性的方法来获取自定义属性，也可以使用getAttribute()获取自定义属性；
Firefox下，只能使用getAttribute()获取自定义属性
解决方法：统一通过getAttribute()获取自定义属性。

（5）IE下，event对象有x、y属性，但是没有pageX、pageY属性;
Firefox下，event对象有pageX、pageY属性，但是没有x、y属性。
解决方法：（条件注释）缺点是在IE浏览器下可能会增加额外的HTTP请求数。

（6）怪异模式问题：漏写DTD声明，Firefox仍然会按照标准模式来解析网页，但在IE中会触发怪异模式。为避免怪异模式给我们带来不必要的麻烦，最好养成书写DTD声明的好习惯。


### 简单介绍使用图片 base64 编码的优点和缺点

base64编码是一种图片处理格式，通过特定的算法将图片编码成一长串字符串，在页面上显示的时候，可以用该字符串来代替图片的url属性。
使用base64的优点是：
（1）减少一个图片的HTTP请求

使用base64的缺点是：
（1）根据base64的编码原理，编码后的大小会比原文件大小大1/3，如果把大图片编码到html/css中，不仅会造成文件体积的增加，影响文件的加载速度，还会增加浏览器对html或css文件解析渲染的时间。
（2）使用base64无法直接缓存，要缓存只能缓存包含base64的文件，比如HTML或者CSS，这相比域直接缓存图片的效果要差很多。
（3）兼容性的问题。ie8以前的浏览器不支持。
一般一些网站的小图标可以使用base64图片来引入。


### 如果需要手动写动画，你认为最小时间间隔是多久，为什么

多数显示器默认频率是60Hz，即1秒刷新60次，所以理论上最小间隔为1/60*1000ms＝16.7ms


### 阐述一下 CSS Sprites
雪碧图，也叫精灵图，指的是将一个页面涉及到的所有图片都包含到一张大图中去，然后利用CSS的`background-image`，`background-repeat`，`background-position`的组合进行背景定位。
利用CSS Sprites能很好地减少网页的http请求，从而很好的提高页面的性能；CSS Sprites能减少图片的字节。

优点：
  减少HTTP请求数，极大地提高页面加载速度
  增加图片信息重复度，提高压缩比，减少图片大小
  更换风格方便，只需在一张或几张图片上修改颜色或样式即可实现

缺点：
  图片合并麻烦
  维护麻烦，修改一个图片可能需要重新布局整个图片，样式


### 画一条 0.5px 的线

#### 方法一 viewport
```html
<meta name="viewport" content="width=device-width,initial-scale=0.5">
```
采用 meta 标签修改scale的方式，这样子就能缩放到原来的0.5倍。但是viewport只针对于移动端，只在移动端上才能看到效果。

#### 方法二 transform
```css
.scale-half {
    height: 1px;
    transform: scaleY(0.5);
}
```
Chrome/Safari都变虚了，只有Firefox比较完美看起来是实的而且还很细，效果和直接设置0.5px一样。所以通过transform: scale会导致Chrome变虚，而粗细几乎没有变化。但是如果加上transform-origin: 50% 100%就很完美了。

```css
.scale-half {
  height: 1px;
  transform: scaleY(0.5);
  transform-origin:50% 100%;
}
```

#### 方法三 采用 border-image 的方式

#### 方法四 采用 box-shadow 的方式
```css
div {
  height: 1px;
  background: none;
  box-shadow: 0 0.5px 0 #000;
}
```

#### 方法五 采用svg
利用SVG的描边等属性的1px还是物理像素的1px，而不是高清屏的1px
```css
.svg {
    background: none;
    height: 1px;
    background: url("data:image/svg+xml;utf-8,<svg xmlns='http://www.w3.org/2000/svg' width='100%' height='1px'><line x1='0' y1='0' x2='100%' y2='0' stroke='#000'></line></svg>");
}
```

或者
```html
<svg xmlns='http://www.w3.org/2000/svg' width='100%' height='1px'>
    <line x1='0' y1='0' x2='100%' y2='0' stroke='#000'></line>
</svg>
```
使用svg的line元素画线，stroke表示描边颜色，默认描边宽度stroke-width="1"，由于svg的描边等属性的1px是物理像素的1px，相当于高清屏的0.5px，另外还可以使用svg的rect等元素进行绘制。
可是由于firefox的background-image只支持命名颜色的svg，如"black"、"red"等，如果把上面代码的svg里面的#000改成black的话就可以显示出来，但是这样就很不灵活了。但是可以通过把svg转成base64的形式来解决firefox的兼容问题。

#### 方法六 直接设置0.5px
```css
.half-px {
  height: 0.5px;
  width: 300px;
  background-color: #000;
}
```
其中Chrome把0.5px四舍五入变成了1px，而firefox/safari能够画出半个像素的边。Chrome会把小于0.5px的当成0，而Firefox会把不小于0.55px当成1px，Safari会把不小于0.75px当成1px。在手机上观察IOS的Chrome，却会画出0.5px的边，而安卓5.0原生浏览器是不行的。所以直接设置0.5px不同浏览器的差异比较大，并且我们看到不同系统的不同浏览器对小数点的px有不同的处理。所以如果我们把单位设置成小数的px包括宽高等，其实不太可靠，因为不同浏览器表现不一样。

#### 方法七 采用linear-gradient
渐变的角度从下往上，从白色#fff渐变到黑色#000，而且是线性的，在高清屏上，1px的逻辑像素代表的物理（设备）像素有2px，由于是线性渐变，所以第1个px只能是#fff，而剩下的那个像素只能是#000，这样就达到了画一半的目的。
但这种方法在各个流览器上面都不完美，效果都是虚的，和完美的0.5px还是有差距。这个效果和scale 0.5的差不多，都是通过虚化线，让人觉得变细了。

```css
.gradient {
  height: 1px;
  background: linear-gradient(0deg, #fff, #000);
}
```

reference：https://juejin.cn/post/6844903582370643975

### transition 和 animation 的区别

transition关注的是CSSproperty的变化，property值和时间的关系是一个三次贝塞尔曲线。transition只有两个状态：开始状态和结束状态。transition需要借助别的方式来触发

animation作用于元素本身而不是样式属性，可以使用关键帧的概念，应该说可以实现更自由的动画效果。animation可能是多个状态，有帧的概念。animation可以自动触发。


### 如何实现单行／多行文本溢出的省略（...）

```css
/*单行文本溢出*/
p {
  overflow: hidden;
  text-overflow: ellipsis;
  white-space: nowrap;
}

/*多行文本溢出*/
p {
  position: relative;
  line-height: 1.5em;
  /*高度为需要显示的行数*行高，比如这里我们显示两行，则为3*/
  height: 3em;
  overflow: hidden;
}

p:after {
  content: '...';
  position: absolute;
  bottom: 0;
  right: 0;
  background-color: #fff;
}
```

### 常见的元素隐藏方式

1. 使用 display:none;隐藏元素，渲染树不会包含该渲染对象，因此该元素不会在页面中占据位置，也不会响应绑定的监听事件。

2. 使用 visibility:hidden;隐藏元素。元素在页面中仍占据空间，但是不会响应绑定的监听事件。

3. 使用 opacity:0;将元素的透明度设置为 0，以此来实现元素的隐藏。元素在页面中仍然占据空间，并且能够响应元素绑定的监听事件。

4. 通过使用绝对定位将元素移除可视区域内，以此来实现元素的隐藏。

5. 通过 z-index 负值，来使其他元素遮盖住该元素，以此来实现隐藏。

6. 通过 clip/clip-path 元素裁剪的方法来实现元素的隐藏，这种方法下，元素仍在页面中占据位置，但是不会响应绑定的监听事件。

7. 通过 transform:scale(0,0)来将元素缩放为 0，以此来实现元素的隐藏。这种方法下，元素仍在页面中占据位置，但是不会响应绑定的监听事件。

### CSS3 @font-face 有用过吗

@font-face 语句是 css 中的一个功能模块，用于实现网页字体多样性(设计者可随意指定字体，不需要考虑浏览者电脑上是否安装)。
语法：

- 字体的名称
- 字体文件包含在您的服务器上的某个地方，如果字体文件是在不同的位置，请使用完整的 URL 比如：url('http://www.w3cschool.css/css3/Sansation_Light.ttf')

```css
@font-face {
  font-family: myFirstFont;
  src: url('Sansation_Light.ttf'), url('Sansation_Light.eot'); /* IE9 */
}
```

### CSS 实现隔行变色

```css
/* 方法一 */
li:nth-child(odd) {
  background: #ff0000;
}
li:nth-child(even) {
  background: #0000ff;
}

/* 方法二 */
li:nth-of-type(odd) {
  background: #00ccff;
} /* 奇数行 */
li:nth-of-type(even) {
  background: #ffcc00;
} /* 偶数行 */
```

注意：nth-child() 和 nth-of-type() 的区别

- nth-child() 就是根据元素的个数来计算的
- nth-of-type() 是根据类型来计算的，也就是 `li:nth-of-type(2)` 表示的是第 2 个 li 标签

### 一个满屏品字布局如何设计

```css
html,
body {
  width: 100%;
  height: 100%;
}


.box1 {
  left: 30%;
  width: 40%;
  height: 50%;
  background-color: red;
}

.box2 {
  position: absolute;
  left: 10%;
  width: 40%;
  height: 50%;
  background-color: yellow;
}

.box3 {
  position: absolute;
  right: 10%;
  width: 40%;
  height: 50%;
  background-color: green;
}
```

```html
<div class="box1"></div>
<div class="box2"></div>
<div class="box3"></div>
```

### CSS 画三角形

#### 方法一 使用border
采用的是相邻边框连接处的均分原理。
将元素的宽高设为0，只设置border，把任意三条边隐藏掉（颜色设为transparent），剩下的就是一个三角形。
```css
div {
  width: 0;
  height: 0;
  border-width: 20px;
  border-style: solid;
  border-color: transparent transparent red transparent;
}
```

#### 方法二 使用linear-gradient
```css
.NW {
  width:100px;
  height:100px;
  display: inline-block;
  background: linear-gradient(135deg, orange, orange 50%, transparent 50%, transparent 100%);
}
```

### CSS 画扇形

```css
div {
  height: 0;
  width: 0;
  border: 100px solid transparent;
  border-radius: 50%;
  border-left-color: red;
}
```

效果图：
![扇形](./../images/扇形.png)

### CSS 画正方体

```CSS
.cube {
  font-size: 4em;
  /* 相对于父元素的大小，父元素是16px，这里是64px */
  width: 2em;
  /* 32px */
  margin: 1.5em auto;
  transform-style: preserve-3d;
  transform: rotateX(-35deg) rotateY(30deg);
}

.side {
  position: absolute;
  width: 2em;
  /* 相对于父元素的64px的大小，也就是128px */
  height: 2em;
  background: rgba(255, 99, 71, 0.6);
  border: 1px solid rgba(0, 0, 0, 0.5);
  color: white;
  text-align: center;
  line-height: 2em;
}

.front {
  transform: translateZ(1em);
}

.bottom {
  transform: rotateX(90deg) translateZ(-1em);
}

.top {
  transform: rotateX(90deg) translateZ(1em);
}


.left {
  transform: rotateY(-90deg) translateZ(1em);
}

.right {
  transform: rotateY(-90deg) translateZ(-1em);
}

.back {
  transform: translateZ(-1em);
}
```

```HTML
<div class="cube">
  <div class="side front">1</div>
  <div class="side back">6</div>
  <div class="side right">4</div>
  <div class="side left">3</div>
  <div class="side top">5</div>
  <div class="side bottom">2</div>
</div>
```

效果图：
![正方体](./../images/正方体.png)

### CSS 实现一个硬币旋转的效果

> [参考网站](https://wow.techbrood.com/fiddle/1510)

```CSS
 #euro {
    width: 150px;
    height: 150px;
    margin-left: -75px;
    margin-top: -75px;
    position: absolute;
    top: 50%;
    left: 50%;
    transform-style: preserve-3d;
    animation: spin 2.5s linear infinite;
  }
  .back {
    background-image: url("/uploads/160101/backeuro.png");
    width: 150px;
    height: 150px;
  }
  .middle {
    background-image: url("/uploads/160101/faceeuro.png");
    width: 150px;
    height: 150px;
    transform: translateZ(1px);
    position: absolute;
    top: 0;
  }
  .front {
    background-image: url("/uploads/160101/faceeuro.png");
    height: 150px;
    position: absolute;
    top: 0;
    transform: translateZ(10px);
    width: 150px;
  }
  @keyframes spin {
    0% {
      transform: rotateY(0deg);
    }
    100% {
      transform: rotateY(360deg);
    }
  }
```

### CSS 实现水平居中
需要分为行内元素和块级元素讨论

#### 行内元素：
利用text-align: center;
```css
.center {
  text-align: center;
}
```

#### 块级元素
##### 方法一：
利用margin: 0 auto;
```css
.center {
  margin: 0 auto;
}
```

##### 方法二：
将块级元素转换成行内元素
```css
.outer {
  text-align: center;
}

.inner {
  display: inline-block;
}
```

##### 方法三：
利用flex-box
```css
.outer {
  display: flex;
  justify-content: center;
}

.inner {
  display: inline-block;
}
```

### CSS 实现垂直居中

- 定位 + 负边距 知道元素高度时可以采用
```css
.outer {
  width: 20%;
  height: 20%;
  margin-top: 5%;
}

.inner {
    position: absolute;
    top: 50%;
    height: 10%;
    margin-top: -10%;
}
```

```html
<div class="outer">
    <div class="inner">when you know the height of the element</div>
</div>
```

- display: flex 弹性布局

```css
.outer {
  display: flex;
  align-items: center;
  justify-content: center;
}
.inner {

}
```
```html
<div class="outer">
  <div class="inner">flex box is a choice</div>
</div>
```

- display: table
```css
.outer {
    position: relative;
    display: table;
    padding: 2.5%;
}
.box3 {
    display: table-cell;
    vertical-align: middle;
}
```  
```html
<div class="outer">
  <div class="inner">table is a method when you don't care if the element stretches the height of the container</div>
</div>
```

- use transform
```css
.outer {
    position: relative;
}

.inner {
    position: absolute;
    top: 50%;
    transform: translateY(-50%);
}
```
```html
<div class="outer">
  <div class="inner">nudge it up half of it’s height after bumping it down halfway</div>
</div>
```

- 绝对居中

```css
div {
  width: 300px;
  height: 300px;
  background-color: red;
  position: absolute;
  left: 0;
  right: 0;
  top: 0;
  bottom: 0;
  margin: auto;
}
```

### CSS 实现两列固定，中间自适应的布局

![三栏布局效果图](../images/三栏布局效果图.png)

> 左右各占 200px，中间随着窗口的调整自适应

HTML 代码如下：

```html
<div class="div">
  <div class="left">left</div>
  <div class="right">right</div>
  <div class="main">main</div>
</div>
```

- 方法一：通过定位的方式，中间一列通过 `margin: auto` 实现自适应

```css
.left {
  width: 200px;
  height: 100%;
  background-color: red;
  position: absolute;
  left: 0;
}
.right {
  width: 200px;
  height: 100%;
  background-color: red;
  position: absolute;
  right: 0;
}
.main {
  height: 100%;
  background-color: green;
  position: absolute;
  left: 200px;
  right: 200px;
  margin: auto; /* 这个千万不能少 */
}
```

- 方法二：flex 布局

```css
html,
body {
  height: 100%;
}
.div {
  height: 100%; /* 想要实现高度百分百必须让父元素都有高度 */
  display: flex;
}
.left {
  flex: 0 0 200px;
  order: 1; /* order定义显示的顺序 */
  background-color: red;
}
.right {
  flex: 0 0 200px;
  order: 3;
  background-color: red;
}
.main {
  flex: auto;
  order: 2;
  background-color: green;
}
```

- 方法三：左右浮动布局，这种布局方式，必须先写浮动部分，最后再写中间部分，否则右浮动块会掉到下一行。

```css
html,
body {
  height: 100%;
}
.div {
  height: 100%;
}
.left {
  float: left;
  width: 200px;
  height: 100%;
  background-color: red;
}
.right {
  float: right;
  width: 200px;
  height: 100%;
  background-color: red;
}
.main {
  height: 100%;
  background-color: green;
}
```

### 实现自适应九宫格

```html
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>Document</title>
    <style>
      html,
      body {
        width: 100%;
        height: 100%;
      }
      .box {
        width: 100%;
        height: 100%;
        display: flex;
        align-items: center;
        justify-content: center;
        flex-wrap: wrap;
      }
      .item {
        width: 30%;
        height: 30%;
        margin: 1%;
        background-color: #cccccc;
      }
    </style>
  </head>

  <body>
    <div class="box">
      <div class="item"></div>
      <div class="item"></div>
      <div class="item"></div>
      <div class="item"></div>
      <div class="item"></div>
      <div class="item"></div>
      <div class="item"></div>
      <div class="item"></div>
      <div class="item"></div>
    </div>
  </body>
</html>
```

### 屏幕里面内容未占满的时候 footer 固定在屏幕可视区域的底部。占满的时候显示在网页的最底端

- 方式一

```html
<style>
  html,
  body {
      height: 100%;
      margin: 0;
      padding: 0;
  }

  .page {
      box-sizing: border-box;
      min-height: 100%;
      padding-bottom: 300px;
      background-color: gray;
      /* height: 2000px; */
  }

  footer {
      height: 300px;
      margin-top: -300px;
      background-color: #ccc;
</style>

<div class="page">主要页面</div>
<footer>底部</footer>
```

- 方式二

```html
<style>
  html,
  body {
      height: 100%;
      margin: 0;
      padding: 0;
  }

  .container {
      position: relative;
      min-height: 100%;
  }

  .page {
      background-color: gray;
      /* height: 2000px; */
  }

  footer {
      position: absolute;
      left: 0;
      bottom: 0;
      height: 300px;
      width: 100%;
      background-color: #ccc;
</style>

<div class="container">
  <div class="page">主要页面</div>
  <footer>底部</footer>
</div>
```

### CSS 多列等高如何实现？
grid,flex,table

利用padding-bottom|margin-bottom正负值相抵，不会影响页面布局的特点。设置父容器超出隐藏（overflow:hidden），这样父容器的高度就还是它里面的列没有设定padding-bottom时的高度，当它里面的任一列高度增加了，则父容器的高度被撑到里面最高那列的高度，其他比这列矮的列会用它们的padding-bottom补偿这部分高度差。

### li 与 li 之间有看不见的空白间隔是什么原因引起的？有什么解决办法？

浏览器会把inline元素间的空白字符（空格、换行、Tab等）渲染成一个空格。而为了美观。我们通常是一
个<li>放在一行，这导致<li>换行后产生换行字符，它变成一个空格，占用了一个字符的宽度。
解决办法：
（1）为<li>设置float:left。不足：有些容器是不能设置浮动，如左右切换的焦点图等。
（2）将所有<li>写在同一行。不足：代码不美观。
（3）将<ul>内的字符尺寸直接设为0，即fontsize:0。不足：<ul>中的其他字符尺寸也被设为0，需要额外重新设定其他字符尺寸，且在Safari浏览器依然会出现空白间隔。
（4）消除<ul>的字符间隔letterspacing:-8px，不足：这也设置了<li>内的字符间隔，因此需要将<li>内的字符间隔设为默认letter-spacing:normal。

### 媒体查询
语法:
```css
@media not|only mediatype and (mediafeature and|or|not mediafeature) {
  CSS-Code;
}
```

当媒体查询为真时，相关的样式表或样式规则会按照正常的级联规则被应用。当媒体查询返回假，标签上带有媒体查询的样式表仍将被下载，但不会被应用。

### CSS 优化、提高性能的方法
#### 加载性能：
（1）css压缩：将写好的css进行打包压缩，可以减少很多的体积。
（2）css单一样式：当需要下边距和左边距的时候，很多时候选择:margin:top 0 bottom 0;但margin-bottom:bottom;margin-left:left;执行的效率更高。
（3）减少使用@import,而建议使用link，因为后者在页面加载时一起加载，前者是等待页面加载完成之后再进行加载。

#### 选择器性能：
（1）关键选择器（key selector）。选择器的最后面的部分为关键选择器（即用来匹配目标元素的部分）。CSS选择器是从右到左进行匹配的。当使用后代选择器的时候，浏览器会遍历所有子元素来确定是否是指定的元素等等；
（2）如果规则拥有ID选择器作为其关键选择器，则不要为规则增加标签。过滤掉无关的规则（这样样式系统就不会浪费时间去匹配它们了）。
（3）避免使用通配规则，如*{}计算次数惊人！只对需要用到的元素进行选择。
（4）尽量少的去对标签进行选择，而是用class。
（5）尽量少的去使用后代选择器，降低选择器的权重值。后代选择器的开销是最高的，尽量将选择器的深度降到最低，最高不要超过三层，更多的使用类来关联每一个标签元素。
（6）了解哪些属性是可以通过继承而来的，然后避免对这些属性重复指定规则。

#### 渲染性能：
（1）慎重使用高性能属性：浮动、定位。
（2）尽量减少页面重排、重绘。
（3）去除空规则：｛｝。空规则的产生原因一般来说是为了预留样式。去除这些空规则无疑能减少css文档体积。
（4）属性值为0时，不加单位。
（5）属性值为浮动小数0.**，可以省略小数点之前的0。
（6）标准化各种浏览器前缀：带浏览器前缀的在前。标准属性在后。
（7）不使用@import前缀，它会影响css的加载速度。
（8）选择器优化嵌套，尽量避免层级过深。
（9）css雪碧图，同一页面相近部分的小图标，方便使用，减少页面的请求次数，但是同时图片本身会变大，使用时，优劣考虑清楚，再使用。
（10）正确使用display的属性，由于display的作用，某些样式组合会无效，徒增样式体积的同时也影响解析性能。
（11）不滥用web字体。对于中文网站来说WebFonts可能很陌生，国外却很流行。web fonts通常体积庞大，而且一些浏览器在下载web fonts时会阻塞页面渲染损伤性能。

#### 可维护性、健壮性：
（1）将具有相同属性的样式抽离出来，整合并通过class在页面中进行使用，提高css的可维护性。
（2）样式与内容分离：将css代码定义到外部css中。

### 在网页中应该使用奇数字号还是偶数字号的字体？为什么呢？
（1）偶数字号相对更容易和web设计的其他部分构成比例关系。比如：当使用14px的正文字号，可能就会在一些地方用14
×0.5=7px的margin，在另一些地方用14×1.5=21px的标题字号。
（2）浏览器缘故。低版本的浏览器ie6会把奇数字体强制转化为偶数，即13px渲染为14px。
（3）系统差别。早期的Windows里，中易宋体点阵只有12和14、15、16px，唯独缺少13px。

### 全屏滚动如何实现？
原理：有点类似于轮播，整体的元素一直排列下去，假设有5个需要展示的全屏页面，那么高度是500%，只是展示100%，容器及容器内的页面取当前可视区高度，同时容器的父级元素overflow属性值设为hidden，通过更改容器可视区的位置来实现全屏滚动效果。主要是响应鼠标事件，页面通过CSS的动画效果，进行移动。
```css
overflow：hidden;
transition：all 1000ms ease;
```

现在有许多插件可以做这件事，如 https://alvarotrigo.com/fullPage/#page1


### 如何修改 chrome 记住密码后自动填充表单的黄色背景？

chrome表单自动填充后，input文本框的背景会变成黄色的，这是由于chrome会默认给自动填充的input表单加上
```css
input :-webkit-autofill{
  backgroundcolor:rgb(250,255,189) !important;
  background-image:none !important;
  color:rgb(0,0,0) !important;
}
```
对chrome默认定义的`background-color`，
`background-image`，`color`使用important是不能提高其优先级的，但是其他属性可使用。
可以使用足够大的纯色内阴影来覆盖input输入框的黄色背景，处理如下
```css
input :-webkit-autofill, textarea :-webkitautofill, select:-webkit-autofill {
  -webkit-box-shadow:000px 1000px white inset;
  border:1px solid #CCC !important;
}
```

### 如何让 Chrome 支持小于 12px 的文字？

在谷歌下css设置字体大小为12px及以下时，显示都是一样大小，都是默认12px。
解决办法：
（1）在老版本中，可以使用`webkit-text-size-adjust:none;`，字体大小就不受限制了。但是chrome更新到27版本之后就不再支持-webkit-text-size-adjust样式。
（2）可以使用css3的transform缩放属性`webkit-transform:scale(0.5);`注意`-webkit-transform:scale(0.75);`收缩的是整个元素的大小，这时候，如果是内联元素，必须要将内联元素转换成块元素。
（3）使用图片：如果是内容固定不变情况下，使用将小于12px文字内容切出做图片，这样不影响兼容也不影响美观。

### 如何让页面里的字体变清晰，变细？
使用`font-smooth`，但是不要在生产环境下使用。
macOS使用`-webkit-font-smoothing`，用于字体抗锯齿，使用后字体看起来会更清晰舒服，但这只在macOS下生效。
firefox使用`-moz-osx-font-smoothing`

reference: https://developer.mozilla.org/en-US/docs/Web/CSS/font-smooth

### position:fixed;在 android 下无效怎么处理？
在移动端显示时，因为layout viewport 的宽度大于移动端屏幕的宽度，所以页面会出现滚动条左右移动。而fixed的元素是相对layout viewport 而不是移动端屏幕来固定位置，所以会出现感觉fixed无效的情况。
如果想实现fixed相对于屏幕的固定效果，需要把viewport设置为ideal viewport，比如：
```html
<meta name="viewport" 
content="width=device-width, initialscale=1.0,maximum-scale=1.0, minimum-scale=1.0,user-scalable=no"/>
```

### 如何去除 `inline-block` 元素间间距？
这个间隙是由换行或者回车导致的。只要把标签写成一行或者标签直接没有空格，就不会出现间隙。但这样因为代码生成工具、代码格式化、或者其他人修改了代码等简单的原因非常容易失效。因此需要采用下列方法。
#### 方法一 写成一行
简单粗暴但容易失效，不推荐。

```html
<div>
  <span>第一个span</span><span>第二个span</span><span>第三个span</span><span>第四个span</span>
</div>
```

#### 方法二 把上一个闭合标签和下一个起始标签连在一起
虽然比方法一好，但不大美观，而且依然容易失效。
```css
span {
  display: inline-block;
}
```

```html
<div>
  <span>第一个span
  </span><span>第二个span
  </span><span>第三个span
  </span><span>第四个span</span>
</div>
```

#### 方法三 利用注释标签
有点冗余，但是比方法一和方法二好。
```html
<div>
  <span>第一个span</span><!-- 
  --><span>第二个span</span><!-- 
  --><span>第三个span</span><!-- 
  --><span>第四个span</span>
</div>
```

#### 方法四 不要闭合标签
<blockquote class="warning"> 虽然网上提到了这个方法，但我尝试后发现在chrome里并没有用，但在此处还是列出。</blockquote>
为了兼容IE6/IE7，最后一个标签需要闭合。
```html
<div>
  <span>第一个span
  <span>第二个span
  <span>第三个span
  <span>第四个span</span>
</div>
```

#### 方法五 通过设置margin
<blockquote class="warning"> 注意：此处的margin与字体大小有关。</blockquote>
```css
span {
  display: inline-block;
  margin: 0;
}
```
```html
<div>
  <span>第一个span</span>
  <span>第二个span</span>
  <span>第三个span</span>
  <span>第四个span</span>
</div>
```

#### 方法六 通过父元素的`font-size:0`
```css
span {
  display: inline-block;
  font-size: 14px;
}
```
```html
<div style="font-size:0;-webkit-text-size-adjust: none;">
  <span>第一个span</span>
  <span>第二个span</span>
  <span>第三个span</span>
  <span>第四个span</span>
</div>
```
### 如何解决`overflow:scroll` 时不能平滑滚动的问题？

如果对某个div或模块使用了`overflow: scroll`属性，在iOS系统的手机上浏览时，则会出现明显的卡顿现象。但是在android系统的手机上则不会出现该问题。
可以通过添加`-webkit-overflow-scrolling: touch;`来解决。这行代码启用了硬件加速特性，所以滑动很流畅。或者也可以使用IScroll等插件。

### 有一个高度自适应的 div，里面有两个div，一个高度 100px，希望另一个填满剩下的高度。

（1）外层div使用`position：relative；`高度要求自适应的div使用 `position:absolute;top:100px;bottom:0; left:0;right:0;`
（2）使用flex布局，设置主轴为竖轴，第二个div设置
`flex-grow:1`。

### 浏览器如何判断是否支持 webp 格式图片

#### 方法一 宽高判断法
创建image对象，将其src属性设置为webp格式的图片，然后在onload事件中获取图片的宽高，如果能够获取，则说明浏览器支持webp格式图片。如果不能获取或者触发了onerror函数，那么就说明浏览器不支持webp格式的图片。
```js
const supportsWebp = ({ createImageBitmap, Image }) => {
  if (!createImageBitmap || !Image) return Promise.resolve(false);

  return new Promise(resolve => {
    const image = new Image();
    image.onload = () => {
        createImageBitmap(image)
            .then(() => {
                resolve(true);
            })
            .catch(() => {
                resolve(false);
            });
    };
    image.onerror = () => {
        resolve(false);
    };
    image.src = 'data:image/webp;base64,UklGRh4AAABXRUJQVlA4TBEAAAAvAAAAAAfQ//73v/+BiOh/AAA=';
  });
};

const webpIsSupported = () => {
  let memo = null;
  return () => {
      if (!memo) {
          memo = supportsWebp(window);
      }
      return memo;
  };
};

webpIsSupported()().then(res => {
    console.log("是否支持 webp", res)
}).catch(err => {
    console.log(err)
})
```

#### 方法二 canvas判断方法
我们可以动态的创建一个canvas对象，通过canvas的toDataURL将设置为webp格式，然后判断返回值中是否含有image/webp字段，如果包含则说明支持WebP，反之则不支持。

```js
function isSupportWebp() {
  try {
    return document.createElement('canvas').toDataURL('image/webp', 0.5).indexOf('data:image/webp') === 0;
  } catch(err) {
    return false;
  }
}
```

#### 方法三 根据请求header信息
在图片请求发出的时候，Request Headers 里有Accept，服务端可以根据 Accept 里面是否有 image/webp 进行判断。

reference: 
https://zhuanlan.zhihu.com/p/70519620
https://developer.mozilla.org/zh-CN/docs/Web/API/HTMLCanvasElement/toDataURL

### CSS 布局
#### 单列布局

#### 两列自适应布局

#### 三栏布局

#### 黏连布局

#### 等高布局
reference: https://juejin.cn/post/6844903710070407182#heading-12

### `height:100%`失效的情况

对于普通文档流中的元素，百分比高度值要想起作用，其父级必须有一个可以生效的高度值。
如果包含块的高度没有显式指定（即高度由内容决定），并且该元素不是绝对定位，则计算值为auto，所以无法参与计算。而使用绝对定位的元素会有计算值，即使祖先元素的height计算为auto也是如此。

### min-width和max-width属性间的覆盖规则？
max-width会覆盖width，即使width是行类样式或者设置了!important；当min-width和max-width冲突的时候，min-width会覆盖max-width。

### 幽灵空白节点是怎么回事？
> "Each line box starts with a zero-width inline box with the element's font and line height properties. We call that imaginary box a 'strut'."
每个行框盒子都以一个具有元素的字体和行高属性的零宽度行内框开始。我们称这个假想的盒子为"支柱"。

在HTML5文档声明中，内联元素的所有解析和渲染表现就如同每个行框盒子的前面有一个“空白节点”一样。这个“空白节点”永远透明，不占据任何宽度，看不见也无法通过脚本获取，就好像幽灵一样，但又确确实实地存在，表现如同文本节点一样，因此，我称之为“幽灵空白节点”。

解决方案：
1. 让vertical-align失效：vertical-align属性对于块级元素是无感的，因此我们只需要为元素设置`display:block`即可;
2. 修改vertical-align属性值：修改其默认值baseline值为其他属性值，使其不再相对基线对齐;
3. 修改line-height的值：由于line-height的定义是两基线之间的距离，因此，只要line-height足够小，便可以消除图片下面的空隙。（注意这里是要在div上设置line-height，然后让div的inline boxes继承line-height属性）

reference: https://zhuanlan.zhihu.com/p/391118319

### `margin: auto` 填充规则
`margin: auto`用来计算元素对应方向应该获得的剩余间距大小。但是触发`margin:auto`计算有一个前提条件，就是width或height为auto时，元素具有对应方向的自动填充特性。
（1）如果一侧定值，一侧auto，则auto为剩余空间大小。
（2）如果两侧均是auto，则平分剩余空间。

### margin在什么情况下无效？
* `display:inline`的非替换元素的垂直`margin`无效。对于内联替换元素，垂直`margin`有效，并且没有`margin`合并的问题。
* 表格中的`<tr>`和`<td>`元素无效
* 设置`display:table-cell`或`display:table-row`的元素无效。
* 绝对定位元素非定位方位的`margin`值失效。
* 定高容器子元素的`margin-bottom`或者定宽容器子元素的`margin-right`失效。

### absolute 与 overflow 会相互制约吗？
* 如果overflow不是定位元素且绝对定位元素和overflow容器之间也没有定位元素，则overflow无法对absolute元素进行剪裁。
* 如果是`overflow:auto`或者`overflow:scroll`，即使绝对定位元素高宽比overflow元素高宽还要大，也都不会出现滚动条。
* 当overflow元素自身有`transform`的时候，Chrome和Opera浏览器下的overflow剪裁是无效的。