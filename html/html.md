# HTML

- [HTML](#html)
  - [HTML5 的新特性](#html5-的新特性)
  - [DOCTYPE的作用是什么](#doctype的作用是什么)
  - [语义化标签的作用](#语义化标签的作用)
  - [canvas与SVG](#canvas与svg)
  - [前端路由 router](#前端路由-router)
    - [hash](#hash)
    - [history](#history)
  - [浏览器渲染过程](#浏览器渲染过程)
  - [页面卡顿原因](#页面卡顿原因)
  - [浏览器垃圾回收机制](#浏览器垃圾回收机制)
    - [具体算法说明](#具体算法说明)
    - [引用计数（Reference Counting）](#引用计数reference-counting)
    - [标记清除（Mark and Sweep） + 标记整理（Mark-Compact）](#标记清除mark-and-sweep--标记整理mark-compact)
    - [分代回收（Generational GC）](#分代回收generational-gc)
      - [GC无法回收的场景](#gc无法回收的场景)
      - [V8的垃圾回收机制](#v8的垃圾回收机制)

## HTML5 的新特性

[参考链接](https://www.cnblogs.com/ainyi/p/9777841.html)

1. 语义化标签: header、footer、section、nav、aside、article
2. 增强型表单：input的多个type(color, date, datetime, email, month, number, range, search, tel, time, url, week)
3. 新增表单元素：datalist、keygen、output
4. 新增表单属性：placehoder, required, min和max, step, height 和 width, autofocus, multiple
5. 音频视频：audio、video
6. canvas
7. 地理定位：
8. 拖拽：drag
9. 本地存储：localStorage、sessionStorage
10. 新事件：onresize、ondrag、onscroll、onmousewheel、onerror、onplay、onpause
11. WebSocket

## DOCTYPE的作用是什么

```js
(1) <!DOCTYPE>声明一般位于第一行，处于 <html> 标签前。作用：告诉浏览器以什么样的模式来解析文档。DOCTYPE 不存在或格式不正确会导致文档以兼容模式呈现。
(2) 一般指定了之后会以标准模式来进行文档解析，否则就以兼容模式进行解析。在标准模式下，浏览器的解析规则都是按照最新的标准进行解析的;在兼容模式下，浏览器会以向后兼容的方式来模拟老式浏览器的行为，以保证一些老的网站的正确访问。
```

## 语义化标签的作用

- 即使在没有CSS样式的条件下，也能很好地呈现出内容结构、代码结构。
- 方便其他设备解析（如屏幕阅读器、盲人阅读器、移动设备）以意义的方式来渲染网页
- 语义化标签会使HTML页面的内容结构更加清晰，有利于维护代码和添加样式
- 有利于SEO
- 便于团队开发和维护，遵循W3C标准，可以减少差异化

## canvas与SVG

- canvas与svg都是可以在浏览器上创建图形
- HTML5 的 canvas 元素使用 JavaScript 在网页上绘制图像。画布是一个矩形区域，您可以控制其每一像素。canvas 拥有多种绘制路径、矩形、圆形、字符以及添加图像、动画的方法
- canvas绘制位图,绘制出来的每一个图形的元素都是独立的DOM节点，能够方便的绑定事件或用来修改。canvas复杂度高会减慢渲染速度（任何过度使用 DOM 的应用都不快）。canvas输出的是一整幅画布，就像一张图片一样，放大会失真。canvas不适合游戏应用。
- svg输出的图形是矢量图形，后期可以修改参数来自由放大缩小，SVG 图像在放大或改变尺寸的情况下其图形质量不会有所损失。svg最适合图像密集型的游戏，其中的许多对象会被频繁重绘

## 前端路由 router
传统的浏览器URL变化时会向服务端重新请求并刷新页面，用户体验很差；前端路由为了提升用户体验应运而生。
前端路由本质都是改变浏览器URL但不刷新页面，通过监听其变化触发自定义的路由处理方案。

### hash
hash值指的是url里#后面的路径，原本用于页面定位，称之为锚点，能够使页面定位到对应id的元素，可以通过`location.hash`访问。
当hash值发生变化时，浏览器并不会重新发起请求，而是会触发 hashChange 事件。可以通过hashChange来监听hash值的变化，从而触发自定义的路由处理方案，浏览器的前进后退也会触发hashChange。

优点：浏览器兼容性较好。
劣势：URL中带有#号，不够美观，不利于SEO.

### history
History是H5推出的API，利用popState事件来监听历史栈的变化。
- go，back，forward这些api能够触发该事件从而触发自定义的路由处理方案
- pushState和replaceState会改变URL但不会触发该事件，需要手动触发自定义的路由处理方案。

优势：URL更加美观，利于SEO，可以使用浏览器的前进后退功能
劣势：需要服务端配置支持，否则刷新会404

## 浏览器渲染过程
1. 浏览器首先获取HTML文件，然后从上到下逐行解析HTML文档，生成DOM（Document Object Model）树。于此同时，浏览器也会解析CSS文件，生成CSSOM（CSS Object Model）树。
2. 将DOM树和CSSOM树合并，生成渲染树（Render Tree）
3. 浏览器根据渲染树，计算每个元素的位置和大小，生成布局（Layout）
4. 浏览器根据渲染树和计算出的布局信息，将每个元素绘制（Paint）到屏幕上

## 页面卡顿原因
主流浏览器的刷新频率是 60HZ，每（1000ms / 60Hz）16.6ms 浏览器刷新一次，即在每 16.6ms 时间内，浏览器会经历 JS脚本执行 → 样式布局 → 样式绘制的过程。因为GUI 渲染线程与 JS 线程互斥，所以 JS 脚本执行和浏览器布局、绘制不能同时执行。所以当 JS 执行时间过长，超出 16.6ms时，这次刷新就没有时间执行样式布局和样式绘制了。这也就导致页面掉帧，用户感觉到卡顿。

## 浏览器垃圾回收机制
垃圾回收是浏览器自动释放不再被引用的内存的过程。

### 具体算法说明

### 引用计数（Reference Counting）
原理：每个对象有一个引用计数器，被引用时+1，取消引用时-1，计数为0时释放内存。
优点：实现简单，实时回收。
缺点：会产生循环引用无法回收的问题。

### 标记清除（Mark and Sweep） + 标记整理（Mark-Compact）
原理：从根对象（如window/global）出发遍历所有能访问到的对象，未被标记（即不可达）的对象被清除。清理完成后，将存活对象移动到一起，避免内存碎片。
优点：解决循环引用问题。
缺点：清除会产生内存碎片。
关键点：可达性（Reachability）是判断是否回收的唯一标准。

### 分代回收（Generational GC）
把内存分为两类：
新生代（Young Generation）：存放新对象，空间小、回收频繁。
老生代（Old Generation）：存放长期存活的对象，空间大、回收少。

V8 使用增量标记（Incremental Marking）与惰性清理（Lazy Sweep）优化性能，避免主线程长时间停顿（Stop-The-World）。

#### GC无法回收的场景
1. 意外的全局变量 window.a = ...
2. 闭包未释放，函数中引用外部变量，函数长期不销毁
3. DOM 引用未断开，JS 对象仍然持有已被移除的 DOM 引用
4. 定时器 / 事件监听未清除（setInterval、addEventListener 未清理）
5. 缓存对象未清理（使用 Map、Set、WeakMap 不当）

#### V8的垃圾回收机制
| 内存区   | 说明 | 回收算法                |
|--------|--------------------------------------|---------------------|
| 新生代   | 存放生命周期短的对象（如局部变量）              | Scavenge（复制算法）      |
| 老生代   | 存放生命周期长的对象（如闭包对象、缓存）         | 标记清除 + 标记整理       |
| 栈空间   | 存放原始类型变量和引用地址                    | 自动出栈回收           |