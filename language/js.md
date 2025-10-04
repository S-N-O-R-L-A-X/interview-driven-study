# JavaScript

- [JavaScript](#javascript)
  - [js 基本数据类型](#js-基本数据类型)
  - [js 遍历对象和遍历数组的方式](#js-遍历对象和遍历数组的方式)
    - [遍历对象](#遍历对象)
    - [遍历数组](#遍历数组)
  - [for...in for...of 区别](#forin-forof-区别)
  - [map weakMap set weakSet 区别](#map-weakmap-set-weakset-区别)
  - [null 和 undefined 的区别](#null-和-undefined-的区别)
  - [其他值到字符串的转换规则](#其他值到字符串的转换规则)
  - [其他值到数字值的转换规则](#其他值到数字值的转换规则)
  - [其他值到布尔类型的值的转换规则](#其他值到布尔类型的值的转换规则)
  - [{} 和 \[\] 的 valueOf 和 toString 的结果是什么](#-和--的-valueof-和-tostring-的结果是什么)
  - [什么情况下会发生布尔值的隐式强制类型转换](#什么情况下会发生布尔值的隐式强制类型转换)
  - [|| 和 \&\& 操作符的返回值](#-和--操作符的返回值)
  - [== 操作符的强制类型转换规则](#-操作符的强制类型转换规则)
  - [如何将字符串转化为数字，例如 '12.3b'](#如何将字符串转化为数字例如-123b)
  - [JavaScript 继承的几种实现方式](#javascript-继承的几种实现方式)
  - [eval 是做什么的](#eval-是做什么的)
  - [事件对象中的 clientX offsetX screenX pageX 的区别](#事件对象中的-clientx-offsetx-screenx-pagex-的区别)
  - [三种事件模型是什么](#三种事件模型是什么)
  - [如何阻止事件冒泡](#如何阻止事件冒泡)
  - [如何阻止事件默认行为](#如何阻止事件默认行为)
  - [事件代理/事件委托 以及 优缺点](#事件代理事件委托-以及-优缺点)
  - [load 和 DOMContentLoaded 事件的区别](#load-和-domcontentloaded-事件的区别)
  - [js 判断图片是否加载完毕的方式](#js-判断图片是否加载完毕的方式)
  - [js 原型，原型链以及特点](#js-原型原型链以及特点)
  - [instanceof 的作用](#instanceof-的作用)
  - [Object.defineProperty 用法](#objectdefineproperty-用法)
  - [js 延迟加载的方式有哪些](#js-延迟加载的方式有哪些)
  - [js 脚本 defer 和 async 的区别](#js-脚本-defer-和-async-的区别)
  - [async await](#async-await)
  - [Event Loop 事件循环](#event-loop-事件循环)
    - [宏任务与微任务](#宏任务与微任务)
      - [微任务的执行顺序](#微任务的执行顺序)
  - [new 运算符的过程](#new-运算符的过程)
  - [数组的 push() 和 pop() 方法的返回值是什么](#数组的-push-和-pop-方法的返回值是什么)
  - [JS 作用域](#js-作用域)
  - [ES6 新特性](#es6-新特性)
  - [let 和 var 的区别](#let-和-var-的区别)
  - [闭包的特性以及优缺点](#闭包的特性以及优缺点)
  - [箭头函数与普通函数的区别](#箭头函数与普通函数的区别)
  - [ES6 中箭头函数 VS 普通函数的 this 指向](#es6-中箭头函数-vs-普通函数的-this-指向)
  - [ES6 class 和 ES5 函数的区别](#es6-class-和-es5-函数的区别)
  - [JS 实现对象（都是简单类型的值）的深拷贝，一行代码](#js-实现对象都是简单类型的值的深拷贝一行代码)
  - [JSON.parse(JSON.stringify(obj)) 实现深拷贝需要注意的问题](#jsonparsejsonstringifyobj-实现深拷贝需要注意的问题)
  - [Promise 是做什么的，有哪些 API](#promise-是做什么的有哪些-api)
    - [Promise 用法](#promise-用法)
    - [Promise.prototype.then()](#promiseprototypethen)
    - [Promise.prototype.catch()](#promiseprototypecatch)
    - [Promise.all()](#promiseall)
    - [Promise.race()](#promiserace)
    - [Promise.resolve()](#promiseresolve)
    - [Promise.reject()](#promisereject)
  - [Promise 不兼容怎么解决](#promise-不兼容怎么解决)
  - [Ajax 基本流程](#ajax-基本流程)
  - [Ajax 的 readyState 的几种状态分别代表什么](#ajax-的-readystate-的几种状态分别代表什么)
  - [Ajax 禁用浏览器的缓存功能](#ajax-禁用浏览器的缓存功能)
  - [js 的模块规范](#js-的模块规范)
    - [CommonJS(cjs)](#commonjscjs)
    - [AMD(Asynchronous Module Definition)](#amdasynchronous-module-definition)
    - [UMD(Universal Module Definition)](#umduniversal-module-definition)
    - [CMD](#cmd)
    - [ESM](#esm)
    - [CJS vs ESM](#cjs-vs-esm)
  - [arguments 怎么转化成真数组](#arguments-怎么转化成真数组)
  - [js 的对象的常用的方法](#js-的对象的常用的方法)
  - [js 的字符串的常用的方法](#js-的字符串的常用的方法)
  - [js 的数组的常用的方法](#js-的数组的常用的方法)
  - [拍平数组](#拍平数组)
  - [防抖与节流](#防抖与节流)
    - [防抖 debounce](#防抖-debounce)
    - [节流 throttle](#节流-throttle)
  - [实现并发控制](#实现并发控制)

## js 基本数据类型

> js 一共有六种基本数据类型，分别是 Undefined、Null、Boolean、Number、String，还有在 ES6 中新增的 Symbol 类型，代表创建后独一无二且不可变的数据类型，它的出现我认为主要是为了解决可能出现的全局变量冲突的问题。

## js 遍历对象和遍历数组的方式

### 遍历对象

- Object.keys()

> 返回一个数组,包括对象自身的(不含继承的)所有可枚举属性(不含 Symbol 属性).

```js
let obj = {
  name: 'lee',
  sex: 'male',
  age: 18,
};
Object.keys(obj).forEach(key => {
  console.log(key, obj[key]);
});

// name lee
// sex male
// age 18
```

- for...in

> 循环遍历对象自身的和原型上继承的可枚举属性(不含 Symbol 属性).

```js
let obj = {
  name: 'lee',
  sex: 'male',
  age: 18,
};
for (let key in obj) {
  console.log(key, obj[key]);
}

// name lee
// sex male
// age 18
```

- Object.getOwnPropertyNames()

> 返回一个数组,包含对象自身的所有属性(不含 Symbol 属性,但是包括不可枚举属性).

```js
let obj = {
  name: 'lee',
  sex: 'male',
  age: 18,
};
Object.getOwnPropertyNames(obj).forEach(key => {
  console.log(key, obj[key]);
});

// name lee
// 17 sex male
// 17 age 18
```

- Reflect.ownKeys()

> 返回一个数组,包含对象自身的所有属性(包括 Symbol 属性和不可枚举属性).

```js
let obj = {
  name: 'lee',
  sex: 'male',
  age: 18,
};
Reflect.ownKeys(obj).forEach(key => {
  console.log(key, obj[key]);
});

// name lee
// 17 sex male
// 17 age 18
```

### 遍历数组

- forEach()

```js
let arr = [1, 2, 3];
arr.forEach(e => {
  console.log(e);
});

// 1
// 2
// 3
```

- for...in

> 注意 for...in 遍历的是索引

```js
let arr = [1, 2, 3];
for (let index in arr) {
  console.log(arr[index]);
}

// 1
// 2
// 3
```

- for...of

```js
let arr = [1, 2, 3];
for (let ele of arr) {
  console.log(ele);
}

// 1
// 2
// 3
```

## for...in for...of 区别

- for...in 会遍历对象或者数组的可枚举属性，包括原型，如果不想遍历原型的方法和属性，可以在循环内部判断一下，然后使用 hasOwnProperty()方法判断某属性是否是该对象的属性
- for...of 会遍历数/数组/字符串/map/set 等拥有迭代器对象（iterator）的集合，但是不能遍历对象，因为对象没有迭代器对象。
- 总结：for in 遍历的是数组的索引（即键名），而 for of 遍历的是数组元素值；for in 总是得到对象的 key 或数组、字符串的下标；for of 总是得到对象的 value 或数组、字符串的值

## map weakMap set weakSet 区别

weakMap
（1）weakMap只接受对象作为键名（null除外），不接受其他类型的值作为键名
（2）weakMap键名引用的对象是弱引用，即垃圾回收机制不会将该引用考虑在内。但是只要所引用对对象的其他引用都被清除，垃圾回收机制就会释放该对象所占用的内存。也就是，一旦一旦不再需要，WeakMap 里面的键名对象和所对应的键值对会自动消失，不用手动删除引用。
（3）weakMap不可遍历，WeakMap对键名所引用的对象是弱引用关系，因此WeakMap内部成员是会却决于垃圾回收机制有没有执行，运行前后成员个数很可能是不一样的，而垃圾回收机制的执行又是不可预测的，因此不可遍历

区别
（1）Map 的键可以是任意类型，WeakMap 只接受对象作为键（null除外），不接受其他类型的值作为键
（2）Map 的键实际上是跟内存地址绑定的，只要内存地址不一样，就视为两个键； WeakMap 的键是弱引用，键所指向的对象可以被垃圾回收，此时键是无效的
（3）Map 可以被遍历， WeakMap 不能被遍历


## null 和 undefined 的区别

- undefined 和 null 都是基本数据类型，这两个基本数据类型分别都只有一个值，就是 undefined 和 null。
- undefined 代表的含义是未定义，null 代表的含义是空对象。一般变量声明了但还没有定义的时候会返回 undefined，null 主要用于赋值给一些可能会返回对象的变量，作为初始化。
- undefined 在 js 中不是一个保留字，这意味着我们可以使用 undefined 来作为一个变量名，这样的做法是非常危险的，它会影响我们对 undefined 值的判断。但是我们可以通过一些方法获得安全的 undefined 值，比如说 void 0。
- 当我们对两种类型使用 typeof 进行判断的时候，null 类型化会返回 “object”，这是一个历史遗留的问题。
- `undefined==null(true)` `undefined===null(false)`

## 其他值到字符串的转换规则

* null 和 undefined 类型 ，null 转换为 "null"，undefined 转换为 "undefined"，
* Boolean 类型，true 转换为 "true"，false 转换为 "false"。
* Number 类型的值直接转换，不过那些极小和极大的数字会使用指数形式。
* Symbol 类型的值直接转换，但是只允许显式强制类型转换，使用隐式强制类型转换会产生错误。
* 对普通对象来说，除非自行定义 toString() 方法，否则会调用 toString()（Object.prototype.toString()）来返回内部属性 [[Class]] 的值，如"[object Object]"。如果对象有自己的 toString() 方法，字符串化时就会调用该方法并使用其返回值。


## 其他值到数字值的转换规则

```js
有时我们需要将非数字值当作数字来使用，比如数学运算。为此 ES5 规范在 9.3 节定义了抽象操作 ToNumber。

（1）undefined 类型的值转换为 NaN。

（2）null 类型的值转换为 0。

（3）Boolean 类型的值，true 转换为 1，false 转换为 0。

（4）String 类型的值转换如同使用 Number() 函数进行转换，如果包含非数字值则转换为 NaN，空字符串为 0。

（5）Symbol 类型的值不能转换为数字，会报错。

（6）对象（包括数组）会首先被转换为相应的基本类型值，如果返回的是非数字的基本类型值，则再遵循以上规则将其强制转换为数字。

为了将值转换为相应的基本类型值，抽象操作 ToPrimitive 会首先（通过内部操作 DefaultValue）检查该值是否有valueOf() 方法。
如果有并且返回基本类型值，就使用该值进行强制类型转换。如果没有就使用 toString() 的返回值（如果存在）来进行强制类型转换。
如果 valueOf() 和 toString() 均不返回基本类型值，会产生 TypeError 错误。
```

## 其他值到布尔类型的值的转换规则

```js
ES5 规范 9.2 节中定义了抽象操作 ToBoolean，列举了布尔强制类型转换所有可能出现的结果。

以下这些是假值：
• undefined
• null
• false
• +0、-0 和 NaN
• ""

假值的布尔强制类型转换结果为 false。从逻辑上说，假值列表以外的都应该是真值。
```

## {} 和 [] 的 valueOf 和 toString 的结果是什么

{} 的 valueOf 结果为 {} ，toString 的结果为 "[object Object]"
[] 的 valueOf 结果为 [] ，toString 的结果为 ""


## 什么情况下会发生布尔值的隐式强制类型转换

* if (..) 语句中的条件判断表达式。
* for ( .. ; .. ; .. ) 语句中的条件判断表达式（第二个）。
* while (..) 和 do..while(..) 循环中的条件判断表达式。
* ? : 中的条件判断表达式。
* 逻辑运算符 ||（逻辑或）和 &&（逻辑与）左边的操作数（作为条件判断表达式）。


## || 和 && 操作符的返回值

|| 和 && 首先会对第一个操作数执行条件判断，如果其不是布尔值就先进行 ToBoolean 强制类型转换，然后再执行条件判断。
对于 || 来说，如果条件判断结果为 true 就返回第一个操作数的值，如果为 false 就返回第二个操作数的值。
&& 则相反，如果条件判断结果为 true 就返回第二个操作数的值，如果为 false 就返回第一个操作数的值。
|| 和 && 返回它们其中一个操作数的值，而非条件判断的结果

## == 操作符的强制类型转换规则

* 字符串和数字之间的相等比较，将字符串转换为数字之后再进行比较。
* 其他类型和布尔类型之间的相等比较，先将布尔值转换为数字后，再应用其他规则进行比较。
* null 和 undefined 之间的相等比较，结果为真。其他值和它们进行比较都返回假值。
* 对象和非对象之间的相等比较，对象先调用 ToPrimitive 抽象操作后，再进行比较。
* 如果一个操作值为 NaN ，则相等比较返回 false（ NaN 本身也不等于 NaN ）。
* 如果两个操作值都是对象，则比较它们是不是指向同一个对象。如果两个操作数都指向同一个对象，则相等操作符返回 true，否则，返回 false。


## 如何将字符串转化为数字，例如 '12.3b'

* 使用 Number() 方法，前提是所包含的字符串不包含不合法字符。
* 使用 parseInt() 方法，parseInt() 函数可解析一个字符串，并返回一个整数。还可以设置要解析的数字的基数。当基数的值为 0，或没有设置该参数时，parseInt() 会根据 string 来判断数字的基数。
* 使用 parseFloat() 方法，该函数解析一个字符串参数并返回一个浮点数。


## JavaScript 继承的几种实现方式

- 第一种是以原型链的方式来实现继承，但是这种实现方式存在的缺点是，在包含有引用类型的数据时，会被所有的实例对象所共享，容易造成修改的混乱。还有就是在创建子类型的时候不能向超类型传递参数。

- 第二种方式是使用借用构造函数的方式，这种方式是通过在子类型的函数中调用超类型的构造函数来实现的，这一种方法解决了不能向超类型传递参数的缺点，但是它存在的一个问题就是无法实现函数方法的复用，并且超类型原型定义的方法子类型也没有办法访问到。

- 第三种方式是组合继承，组合继承是将原型链和借用构造函数组合起来使用的一种方式。通过借用构造函数的方式来实现类型的属性的继承，通过将子类型的原型设置为超类型的实例来实现方法的继承。这种方式解决了上面的两种模式单独使用时的问题，但是由于我们是以超类型的实例来作为子类型的原型，所以调用了两次超类的构造函数，造成了子类型的原型中多了很多不必要的属性。

- 第四种方式是原型式继承，原型式继承的主要思路就是基于已有的对象来创建新的对象，实现的原理是，向函数中传入一个对象，然后返回一个以这个对象为原型的对象。这种继承的思路主要不是为了实现创造一种新的类型，只是对某个对象实现一种简单继承，ES5 中定义的 Object.create() 方法就是原型式继承的实现。缺点与原型链方式相同。

- 第五种方式是寄生式继承，寄生式继承的思路是创建一个用于封装继承过程的函数，通过传入一个对象，然后复制一个对象的副本，然后对象进行扩展，最后返回这个对象。这个扩展的过程就可以理解是一种继承。这种继承的优点就是对一个简单对象实现继承，如果这个对象不是我们的自定义类型时。缺点是没有办法实现函数的复用。

- 第六种方式是寄生式组合继承，组合继承的缺点就是使用超类型的实例做为子类型的原型，导致添加了不必要的原型属性。寄生式组合继承的方式是使用超类型的原型的副本来作为子类型的原型，这样就避免了创建不必要的属性。

## eval 是做什么的

它的功能是把对应的字符串解析成 JS 代码并运行。
应该避免使用 eval，不安全，非常耗性能（2次，一次解析成 js 语句，一次执行）。

## 事件对象中的 clientX offsetX screenX pageX 的区别

- [clientX, clientY]

client直译就是客户端，客户端的窗口就是指游览器的显示页面内容的窗口大小（不包含工具栏、导航栏等等）
[clientX, clientY]就是鼠标距游览器显示窗口的长度

兼容性：IE和主流游览器都支持。


- [offsetX, offsetY]

offset意为偏移量
[offsetX, offsetY]是被点击的元素距左上角为参考原点的长度，而IE、FF和Chrome的参考点有所差异。

Chrome下，offsetX offsetY是包含边框的
IE、FF是不包含边框的，如果鼠标进入到border区域，为返回负值

兼容性：IE9+,chrome,FF都支持此属性。


- [screenX, screenY]

screen顾名思义是屏幕
[screenX, screenY]是用来获取鼠标点击位置到屏幕显示器的距离，距离的最大值需根据屏幕分辨率的尺寸来计算。

兼容性：所有游览器都支持此属性。


- [pageX, pageY]

page为页面的意思，页面的高度一般情况client浏览器显示区域装不下，所以会出现垂直滚动条。

[pageX, pageY]是鼠标距离页面初始page原点的长度。

在IE中没有pageX、pageY取而代之的是event.x、event.y。x和y在webkit内核下也实现了，所以火狐不支持x，y。

兼容性：IE不支持，其他高级游览器支持。

## 三种事件模型是什么

事件是用户操作网页时发生的交互动作或者网页本身的一些操作，现代浏览器一共有三种事件模型。
第一种事件模型是最早的 DOM0 级模型，这种模型不会传播，所以没有事件流的概念，但是现在有的浏览器支持以冒泡的方式实现，它可以在网页中直接定义监听函数，也可以通过 js 属性来指定监听函数。这种方式是所有浏览器都兼容的。
第二种事件模型是 IE 事件模型，在该事件模型中，一次事件共有两个过程，事件处理阶段，和事件冒泡阶段。事件处理阶段会首先执行目标元素绑定的监听事件。然后是事件冒泡阶段，冒泡指的是事件从目标元素冒泡到 document，依次检查经过的节点是否绑定了事件监听函数，如果有则执行。这种模型通过 attachEvent 来添加监听函数，可以添加多个监听函数，会按顺序依次执行。
第三种是 DOM2 级事件模型，在该事件模型中，一次事件共有三个过程，第一个过程是事件捕获阶段。捕获指的是事件从 document 一直向下传播到目标元素，依次检查经过的节点是否绑定了事件监听函数，如果有则执行。后面两个阶段和 IE 事件模型的两个阶段相同。这种事件模型，事件绑定的函数是 addEventListener，其中第三个参数可以指定事件是否在捕获阶段执行。默认是false，在冒泡阶段执行。

## 如何阻止事件冒泡

```js
// w3c
e.stopPropagation();

// IE
e.cancelBubble = true;
```

## 如何阻止事件默认行为

```js
//谷歌及IE8以上
e.preventDefault();

//IE8及以下
window.event.returnValue = false;

//无兼容问题（但不能用于节点直接onclick绑定函数）
return false;
```

## 事件代理/事件委托 以及 优缺点

事件委托本质上是利用了浏览器事件冒泡的机制。因为事件在冒泡过程中会上传到父节点，并且父节点可以通过事件对象获取到目标节点，因此可以把子节点的监听函数定义在父节点上，由父节点的监听函数统一处理多个子元素的事件，这种方式称为事件代理。
使用事件代理我们可以不必要为每一个子元素都绑定一个监听事件，这样减少了内存上的消耗。并且使用事件代理我们还可以实现事件的动态绑定，比如说新增了一个子节点，我们并不需要单独地为它添加一个监听事件，它所发生的事件会交给父元素中的监听函数来处理。

事件委托的优点：

1. 减少内存消耗，不必为大量元素绑定事件
2. 为动态添加的元素绑定事件

事件委托的缺点:

1. 部分事件如 focus、blur 等无冒泡机制，所以无法委托。
2. 事件委托有对子元素的查找过程，委托层级过深，可能会有性能问题
3. 频繁触发的事件如 mousemove、mouseout、mouseover 等，不适合事件委托

## load 和 DOMContentLoaded 事件的区别

- 当整个页面及所有依赖资源如样式表和图片都已完成加载时，将触发 load 事件。它与 DOMContentLoaded 不同，后者只要页面 DOM 加载完成就触发，无需等待依赖资源的加载。
- 当纯 HTML 被完全加载以及解析时，DOMContentLoaded 事件会被触发，而不必等待样式表，图片或者子框架完成加载。

## js 判断图片是否加载完毕的方式

- load 事件

> 测试，所有浏览器都显示出了“loaded”，说明所有浏览器都支持 img 的 load 事件。

```html
<img id="img" src="https://ss0.bdstatic.com/70cFvHSh_Q1YnxGkpoWK1HF6hhy/it/u=151472226,3497652000&fm=26&gp=0.jpg" />
<p id="p">loading...</p>
<script>
  document.getElementById('img').onload = function () {
    document.getElementById('p').innerHTML = 'loaded';
  };
</script>
```

- readystatechange 事件

> readyState 为 complete 和 loaded 则表明图片已经加载完毕。测试 IE6-IE10 支持该事件，其它浏览器不支持。

```html
<img id="img" src="https://ss0.bdstatic.com/70cFvHSh_Q1YnxGkpoWK1HF6hhy/it/u=151472226,3497652000&fm=26&gp=0.jpg" />
<p id="p">loading...</p>
<script>
  var img = document.getElementById('img');
  img.onreadystatechange = function () {
    if (img.readyState == 'complete' || img.readyState == 'loaded') {
      document.getElementById('p').innerHTML = 'readystatechange:loaded';
    }
  };
</script>
```

- img 的 complete 属性

> 轮询不断监测 img 的 complete 属性，如果为 true 则表明图片已经加载完毕，停止轮询。该属性所有浏览器都支持。

```html
<img id="img" src="https://ss0.bdstatic.com/70cFvHSh_Q1YnxGkpoWK1HF6hhy/it/u=151472226,3497652000&fm=26&gp=0.jpg" />
<p id="p">loading...</p>
<script>
  function imgLoad(img, callback) {
    var timer = setInterval(function () {
      if (img.complete) {
        callback(img);
        clearInterval(timer);
      }
    }, 50);
  }
  imgLoad(img, function () {
    document.getElementById('p').innerHTML = '加载完毕';
  });
</script>
```

## js 原型，原型链以及特点


在 js 中我们是使用构造函数来新建一个对象的，每一个构造函数的内部都有一个 prototype 属性值，这个属性值是一个对象，
这个对象包含了可以由该构造函数的所有实例共享的属性和方法。当我们使用构造函数新建一个对象后，在这个对象的内部将包含一个指针，
这个指针指向构造函数的 prototype 属性对应的值，在 ES5 中这个指针被称为对象的原型。一般来说我们是不应该能够获取到这个值的，
但是现在浏览器中都实现了 __proto__ 属性来让我们访问这个属性，但是我们最好不要使用这个属性，因为它不是规范中规定的。
ES5 中新增了一个 Object.getPrototypeOf() 方法，我们可以通过这个方法来获取对象的原型。

当我们访问一个对象的属性时，如果这个对象内部不存在这个属性，那么它就会去它的原型对象里找这个属性，这个原型对象又会有自己的原型，于是就这样一直找下去，也就是原型链的概念。
原型链的尽头一般来说都是 Object.prototype 所以这就是我们新建的对象为什么能够使toString() 等方法的原因。

特点：

JavaScript 对象是通过引用来传递的，我们创建的每个新对象实体中并没有一份属于自己的原型副本。当我们修改原型时，与之相关的对象也会继承这一改变。


## instanceof 的作用

> instanceof 运算符用于判断构造函数的 prototype 属性是否出现在对象的原型链中的任何位置。

## Object.defineProperty 用法

```js
Object.defineProperty(obj, prop, descriptor);
```

- obj
  要定义属性的对象。
- prop
  要定义或修改的属性的名称或 Symbol 。
- descriptor
  要定义或修改的属性描述符。参数有：
  - value
    该属性对应的值。可以是任何有效的 JavaScript 值（数值，对象，函数等）。
    默认为 undefined。
  - writable
    当且仅当该属性的 writable 键值为 true 时，属性的值，也就是上面的 value，才能被赋值运算符改变。
    默认为 false。
  - configurable
    当且仅当该属性的 configurable 键值为 true 时，该属性的描述符才能够被改变，同时该属性也能从对应的对象上被删除。
    默认为 false。
  - enumerable
    当且仅当该属性的 enumerable 键值为 true 时，该属性才会出现在对象的枚举属性中。
    默认为 false。

## js 延迟加载的方式有哪些

> js 延迟加载，也就是等页面加载完成之后再加载 JavaScript 文件。 js 延迟加载有助于提高页面加载速度。

一般有以下几种方式：

- defer 属性
- async 属性
- 动态创建 DOM 方式
- 使用 setTimeout 延迟方法
- 让 JS 最后加载

## js 脚本 defer 和 async 的区别

- defer 属性表示延迟执行引入的 JavaScript，即这段 JavaScript 加载时 HTML 并未停止解析，这两个过程是并行的。当整个 document 解析完毕后再执行脚本文件，在 DOMContentLoaded 事件触发之前完成。多个脚本按顺序执行。

- async 属性表示异步执行引入的 JavaScript，与 defer 的区别在于，如果已经加载好，就会开始执行，也就是说它的执行仍然会阻塞文档的解析，只是它的加载过程不会阻塞。多个脚本的执行顺序无法保证。

## async await

> 官网：async 函数返回一个 Promise 对象，可以使用 then 方法添加回调函数。当函数执行的时候，一旦遇到 await 就会先返回，等到异步操作完成，再接着执行函数体内后面的语句。

- async 单独使用的时候，放在函数前面表示这个函数是一个异步函数，如果 async 函数有返回结果，必须要用.then()方法来承接（也就是返回的值会被自动处理成 promise 对象）

```js
async function bar() {
  return 'lee';
}

console.log(bar()); // Promise {<resolved>: "lee"}
```

- async await 搭配使用的时候，await 是等待此函数执行后，再执行下一个，可以把异步函数变成同步来执行，控制函数的执行顺序。await 一定要搭配 async 使用。

> 当 await 后的函数是返回的 promise。

```js
let foo = () => {
  return new Promise(resolve => {
    setTimeout(() => {
      console.log('lee');
      resolve();
    }, 1000);
  });
};

async function bar() {
  await foo();
  console.log('van');
}
console.log(bar()); // 隔1秒同时输出 lee van
```

> 当 await 后跟的是普通函数（非 promise()）

```js
let f1 = () => {
  setTimeout(() => {
    console.log('lee');
  }, 1000);
};

let f2 = () => {
  setTimeout(() => {
    console.log('van');
  }, 1000);
};

async function bar() {
  await f1();
  await f2();
  console.log('yeah');
}

console.log(bar()); // yeah 隔1秒同时输出 lee fan
```

## Event Loop 事件循环

### 宏任务与微任务
宏任务：整体代码块、setTimeout、setInterval、I/O、setImmediate(Node.js 环境)、UI 交互事件
微任务：promise.then(promise中的内容立即执行)、process.nextTick(Nodejs)、queueMicrotask、Mutation Observer、async/await(await后的函数立刻执行，await下面的内容在微任务队列)

#### 微任务的执行顺序
1. next tick mircotask queue
2. other microtask queue
3. timer queue
4. poll queue
5. check queue
6. close queue

整体代码块是一个大的异步任务，同步任务会先在主线程上执行。异步任务分别加入微任务队列和宏任务队列。在当前执行栈为空的时候，主线程会查看微任务队列是否有事件存在。如果不存在，那么再去宏任务队列中取出一个事件并把对应的回到加入当前执行栈。

reference: https://juejin.cn/post/7067780709548720136

## new 运算符的过程

1. 创建一个空对象{}；
2. 构造函数中的 this 指向该空对象
3. 执行构造函数为这个空对象添加属性
4. 判断构造函数有没有返回值，如果返回值是个对象，则返回这个对象；否则返回创建的“空对象”

## 数组的 push() 和 pop() 方法的返回值是什么

- `push()`将一个或多个元素添加到数组的末尾，并返回该数组的新长度
- `pop()`方法从数组中删除最后一个元素，并返回该元素的值

## JS 作用域

ES5 只有全局作用域和函数作用域

- 全局作用域：代码在程序的任何地方都能被访问，window 对象的内置属性都存在全局作用域
- 函数作用域：在固定的代码片段才能被访问

ES6 有块级作用域

## ES6 新特性

- let const 块级作用域
- 模板字符串
- 解构赋值
- 箭头函数，函数参数默认值
- 扩展运算符（...）
- forEach for...of for...in
- 数组方法 map reduce includes
- map 和 set
- 模块化
- promise proxy
- async
- class

## let 和 var 的区别

- let 是块级作用域，var 是函数作用域
- var 存在变量提升，而 let 没有
- 在代码块内，使用 let 命令声明变量之前，该变量都是不可用的。这在语法上，称为“暂时性死区” (TDZ)

```js
if (true) {
  // TDZ开始
  tmp = 'abc'; // ReferenceError
  console.log(tmp); // ReferenceError

  let tmp; // TDZ结束
  console.log(tmp); // undefined

  tmp = 123;
  console.log(tmp); // 123
}
```

上面代码中，在 let 命令声明变量 tmp 之前，都属于变量 tmp 的“死区”。

## 闭包的特性以及优缺点

```js
function test() {
  var age = 18;
  function addAge() {
    age++;
    alert(age);
  }
  return addAge;
}
```

闭包有三个特性：

- 函数嵌套函数；
- 内部函数使用外部函数的参数和变量；
- 参数和变量不会被垃圾回收机制回收。

闭包的优点：

- 希望一个变量长期保存内存中；
- 避免全局变量污染；
- 私有成员的存在。

闭包的缺点：

- 常驻内存，增加内存使用量；
- 使用不当造成内存泄漏。

## 箭头函数与普通函数的区别

1. 箭头函数是匿名函数，不能作为构造函数，不能使用 new
2. 箭头函数不能绑定 arguments，取而代之用 rest 参数...解决

   ```js
   function A(a) {
     console.log(arguments);
   }
   A(1, 2, 3, 4, 5, 8);
   // [1, 2, 3, 4, 5, 8, callee: ƒ, Symbol(Symbol.iterator): ƒ]
   let C = (...c) => {
     console.log(c);
   };
   C(3, 82, 32, 11323);
   // [3, 82, 32, 11323]
   ```

3. 箭头函数没有原型属性
4. 箭头函数的 this 永远指向其上下文的 this，没有办改变其指向，
   普通函数的 this 指向调用它的对象
5. 箭头函数不绑定 this，会捕获其所在的上下文的 this 值，作为自己的 this 值

## ES6 中箭头函数 VS 普通函数的 this 指向

普通函数中 this

1.  总是指向它的直接调用者，如 obj.fn，fn 里的最外层 this 就是指向 obj
2.  默认情况下，没有直接调用者，fn()，匿名函数自调this 指向 window
3.  严格模式下（设置了'use strict'），this 为 undefined
4.  当使用 call，apply，bind（ES5 新增）绑定的，this 指向绑定对象；
5.  DOM事件的处理函数中的this指向当前的DOM元素对象，button.onclick=function(){}、button.addEventListener(“click”,function(){…})
6.  new一个构造函数，this指向new出来的新对象

箭头函数中 this 默认指向定义它时，指向当前箭头函数之外最近的作用域this；即 ES6 箭头函数里 this 的指向就是上下文里对象 this 指向，偶尔没有上下文对象，this 就指向 window


下面使用例子来加深一下印象：

```js
// 例1
function hello() {
  console.log(this); // window
}
hello();

// 例2
function hello() {
  'use strict';
  console.log(this); // undefined
}
hello();

// 例3
const obj = {
  num: 10,
  hello: function () {
    console.log(this); // obj
    setTimeout(function () {
      console.log(this); // 匿名函数中，this指向window
    });
  },
};
obj.hello();

// 例4
const obj = {
  num: 10,
  hello: function () {
    console.log(this); // obj
    setTimeout(() => {
      console.log(this); // 箭头函数中， 指向上下文obj
    });
  },
};
obj.hello();

// 例5
/*
diameter是普通函数，里面的this指向直接调用它的对象obj。
perimeter是箭头函数，this应该指向上下文函数this的指向，
这里上下文没有函数对象，就默认为window，而window里面没有radius这个属性，就返回为NaN。
*/
const obj = {
  radius: 10,
  diameter() {
    return this.radius * 2;
  },
  perimeter: () => 2 * Math.PI * this.radius,
};
console.log(obj.diameter()); // 20
console.log(obj.perimeter()); // NaN
```

## ES6 class 和 ES5 函数的区别

> 本质上，ES6 的类只是 ES5 的构造函数的一层包装

1. 与 ES5 不同，ES6 类和模块的内部默认就是严格模式，不存在遍历提升

```js
new Foo(); // Reference Error
class Foo {}
```

## JS 实现对象（都是简单类型的值）的深拷贝，一行代码

```js
let newObj = JSON.parse(JSON.stringify(oldObj));
```

## JSON.parse(JSON.stringify(obj)) 实现深拷贝需要注意的问题

1. 如果 obj 里面有时间对象，则 JSON.stringify 后再 JSON.parse 的结果，时间将只是字符串的形式,而不是时间对象；
2. 如果 obj 里有 RegExp、Error 对象，则序列化的结果将只得到空对象；
3. 如果 obj 里有函数，undefined，则序列化的结果会把函数或 undefined 丢失；
4. 如果 obj 里有 NaN、Infinity 和-Infinity，则序列化的结果会变成 null
5. JSON.stringify()只能序列化对象的可枚举的自有属性，例如 如果 obj 中的对象是有构造函数生成的， 则使用 JSON.parse(JSON.stringify(obj))深拷贝后，会丢弃对象的 constructor；
6. 如果对象中存在循环引用的情况也无法正确实现深拷贝；

## Promise 是做什么的，有哪些 API

> Promise 是异步编程的一种解决方案

### Promise 用法

> Promise 构造函数接受一个函数作为参数，该函数的两个参数分别是 resolve 和 reject。它们是两个函数，由 JavaScript 引擎提供，不用自己部署。
>
> resolve 函数的作用是，将 Promise 对象的状态从“未完成”变为“成功”（即从 pending 变为 resolved），在异步操作成功时调用，并将异步操作的结果，作为参数传递出去；reject 函数的作用是，将 Promise 对象的状态从“未完成”变为“失败”（即从 pending 变为 rejected），在异步操作失败时调用，并将异步操作报出的错误，作为参数传递出去。

```js
const promise = new Promise(function(resolve, reject) {
  // ... some code

  if (/* 异步操作成功 */){
    resolve(value);
  } else {
    reject(error);
  }
});
```

### Promise.prototype.then()

> Promise 实例具有 then 方法，也就是说，then 方法是定义在原型对象 Promise.prototype 上的。它的作用是为 Promise 实例添加状态改变时的回调函数。前面说过，then 方法的第一个参数是 resolved 状态的回调函数，第二个参数（可选）是 rejected 状态的回调函数。
>
> **then 方法返回的是一个新的 Promise 实例**（注意，不是原来那个 Promise 实例）。因此可以采用链式写法，即 then 方法后面再调用另一个 then 方法。

```js
getJSON('/posts.json')
  .then(function (json) {
    return json.post;
  })
  .then(function (post) {
    // ...
  });
```

### Promise.prototype.catch()

> Promise.prototype.catch()方法是.then(null, rejection)或.then(undefined, rejection)的别名，用于指定发生错误时的回调函数。

```js
getJSON('/posts.json')
  .then(function (posts) {
    // ...
  })
  .catch(function (error) {
    // 处理 getJSON 和 前一个回调函数运行时发生的错误
    console.log('发生错误！', error);
  });
```

> 上面代码中，getJSON()方法返回一个 Promise 对象，如果该对象状态变为 resolved，则会调用 then()方法指定的回调函数；如果异步操作抛出错误，状态就会变为 rejected，就会调用 catch()方法指定的回调函数，处理这个错误。另外，then()方法指定的回调函数，如果运行中抛出错误，也会被 catch()方法捕获。

### Promise.all()

> Promise.all()方法用于将多个 Promise 实例，包装成一个新的 Promise 实例。

```js
const p = Promise.all([p1, p2, p3]);
```

> 上面代码中，Promise.all()方法接受一个数组作为参数，p1、p2、p3 都是 Promise 实例，如果不是，就会先调用下面讲到的 Promise.resolve 方法，将参数转为 Promise 实例，再进一步处理。另外，Promise.all()方法的参数可以不是数组，但必须具有 Iterator 接口，且返回的每个成员都是 Promise 实例。
>
> p 的状态由 p1、p2、p3 决定，分成两种情况:
>
> （1）只有 p1、p2、p3 的状态都变成 fulfilled，p 的状态才会变成 fulfilled，此时 p1、p2、p3 的返回值组成一个数组，传递给 p 的回调函数。
>
> （2）只要 p1、p2、p3 之中有一个被 rejected，p 的状态就变成 rejected，此时第一个被 reject 的实例的返回值，会传递给 p 的回调函数。

### Promise.race()

> Promise.race()方法同样是将多个 Promise 实例，包装成一个新的 Promise 实例。

```js
const p = Promise.race([p1, p2, p3]);
```

> 上面代码中，只要 p1、p2、p3 之中有一个实例率先改变状态，p 的状态就跟着改变。那个率先改变的 Promise 实例的返回值，就传递给 p 的回调函数。

### Promise.resolve()

> 有时需要将现有对象转为 Promise 对象，Promise.resolve()方法就起到这个作用。
>
> Promise.resolve()等价于下面的写法。

```js
Promise.resolve('foo');
// 等价于
new Promise(resolve => resolve('foo'));
```

### Promise.reject()

> Promise.reject(reason)方法也会返回一个新的 Promise 实例，该实例的状态为 rejected。

```js
const p = Promise.reject('出错了');
// 等同于
const p = new Promise((resolve, reject) => reject('出错了'));

p.then(null, function (s) {
  console.log(s);
});
// 出错了
```

> 上面代码生成一个 Promise 对象的实例 p，状态为 rejected，回调函数会立即执行。

## Promise 不兼容怎么解决

用一些第三方的库来解决兼容性问题：

1. babel-polyfill
2. ES6-Promise
3. bluebird

## Ajax 基本流程

> 原生 js 代码实现与基于 promise 实现请传送至专栏：[面试高频手撕代码题](./../08.面试高频手撕代码题/面试高频手撕代码题.md)

Ajax 即“Asynchronous Javascript And XML”（异步 JavaScript 和 XML），是指一种创建交互式网页应用的网页开发技术。我对 ajax 的理解是，它是一种异步通信的方法，通过直接由 js 脚本向服务器发起 http 通信，然后根据服务器返回的数据，更新网页的相应部分，而不用刷新整个页面的一种方法。

创建一个 ajax 有这样几个步骤:

- 首先是创建一个 XMLHttpRequest 对象。

- 然后在这个对象上使用 open 方法创建一个 http 请求，open 方法所需要的参数是请求的方法、请求的地址、是否异步和用户的认证信息。

- 在发起请求前，我们可以为这个对象添加一些信息和监听函数。比如说我们可以通过 setRequestHeader 方法来为请求添加头信息。我们还可以为这个对象添加一个状态监听函数。一个 XMLHttpRequest 对象一共有 5 个状态，当它的状态变化时会触发 onreadystatechange 事件，我们可以通过设置监听函数，来处理请求成功后的结果。当对象的 readyState 变为 4 的时候，代表服务器返回的数据接收完成，这个时候我们可以通过判断请求的状态，如果状态是 2xx 或者 304 的话则代表返回正常。这个时候我们就可以通过 response 中的数据来对页面进行更新了。

- 当对象的属性和监听函数设置完成后，最后我们调用 sent 方法来向服务器发起请求，可以传入参数作为发送的数据体。

## Ajax 的 readyState 的几种状态分别代表什么

| 状态值 |           含义           |
| :----: | :----------------------: |
|   0    |       请求未初始化       |
|   1    |     服务器连接已建立     |
|   2    |        请求已接收        |
|   3    |        请求处理中        |
|   4    | 请求已完成，且响应已就绪 |

## Ajax 禁用浏览器的缓存功能

> 项目中，一般提交请求都会通过 ajax 来提交，我们都知道 ajax 能提高页面载入的速度主要的原因是通过 ajax 减少了重复数据的载入，也就是说在载入数据的同时将数据缓存到内存中，一旦数据被加载其中，只要我们没有刷新页面，这些数据就会一直被缓存在内存中，当我们提交 的 URL 与历史的 URL 一致时，就不需要提交给服务器，也就是不需要从服务器上面去获取数据，虽然这样降低了服务器的负载提高了用户的体验，但是我们不能获取最新的数据。为了保证我们读取的信息都是最新的，我们就需要禁止他的缓存功能。

解决的方法有：

1. 在 ajax 发送请求前加上 `xhr.setRequestHeader("If-Modified-Since","0")`。
2. 在 ajax 发送请求前加上 `xhr.setRequestHeader("Cache-Control","no-cache")`。
3. 在 URL 后面加上一个随机数： `"fresh=" + Math.random()`;。
4. 在 URL 后面加上时间搓：`"nowtime=" + new Date().getTime()`;。
5. 如果是使用 jQuery，直接这样就可以了`$.ajaxSetup({cache:false})`。这样页面的所有 ajax 都会执行这条语句就是不需要保存缓存记录。

## js 的模块规范

### CommonJS(cjs)
CommonJS 方案通过 require 来引入模块，通过 module.exports 定义模块的输出接口。这种模块加载方案以同步的方式来引入模块，是服务器端的解决方案，因为在服务端文件都存储在本地磁盘，所以读取非常快。但如果是在浏览器端，由于模块的加载是使用网络请求，因此使用异步加载的方式更加合适。而且cjs无法直接在浏览器端工作。所以cjs一般不用在浏览器端。

```js
//importing 
const doSomething = require('./doSomething.js'); 

//exporting
module.exports = function doSomething(n) {
  // do something
}
```

### AMD(Asynchronous Module Definition)
异步模块定义方案采用异步加载的方式来加载模块，模块的加载不影响后面语句的执行，所有依赖这个模块的语句都定义在一个回调函数里，等到加载完成后再执行回调函数。require.js就实现了 AMD 规范。

```js
define(['dep1', 'dep2'], function (dep1, dep2) {
    //Define the module value by returning a value.
    return function () {};
});
```

### UMD(Universal Module Definition)
通用模块定义是AMD和CommonJS的一个糅合，先判断是否支持CJS的模块，存在就使用CJS；再判断是否支持AMD（define是否存在），存在则使用AMD的方式加载。

```js
((root, factory) => {
  if (typeof define === 'function' && define.amd) {
    //AMD
    define(['jquery'], factory);
  } else if (typeof exports === 'object') {
    //CommonJS
    var $ = requie('jquery');
    module.exports = factory($);
  } else {
    //都不是，浏览器全局定义
    root.testModule = factory(root.jQuery);
  }
})(this, ($) => {
  //do something...  这里是真正的函数体
});
```

### CMD
通过依赖就近，延迟执行来提升性能

```js
/** CMD写法 **/
define(function (require, exports, module) {
    var a = require('./a');
    //在需要时申明
    a.doSomething();
    if (false) {
        var b = require('./b');
        b.doSomething();
    }
});

/** sea.js **/
// 定义模块 math.js
define(function (require, exports, module) {
    var $ = require('jquery.js');
    var add = function (a, b) {
        return a + b;
    }
    exports.add = add;
});
// 加载模块
seajs.use(['math.js'], function (math) {
    var sum = math.add(1 + 2);
});
```

### ESM
ESM使用 import 和 export 的形式来导入导出模块。

```js
import x from "";

export default function a(){

}
```

$$
无模块 \stackrel{模块化需求}{\longrightarrow} CJS \stackrel{异步需求}{\longrightarrow} AMD \stackrel{性能问题}{\longrightarrow} CMD \stackrel{适应 CJS 和 AMD}{\longrightarrow} UMD \stackrel{简化定义，导入，导出方式}{\longrightarrow} ESM
$$

### CJS vs ESM
<table>
	<thead>
		<th></th>
		<th>CJS</th>
		<th>ESM</th>
	</thead>
	<tr>
		<td>输出</td>
		<td>值的拷贝</td>
		<td>值的引用</td>
	</tr>
  <tr>
		<td>修改</td>
		<td>允许直接修改值</td>
		<td>不允许直接修改值（对象修改除外）</td>
	</tr>
	<tr>
		<td>加载时间</td>
		<td>运行时加载</td>
		<td>编译时输出接口</td>
	</tr>
  <tr>
		<td>加载方式</td>
		<td>同步</td>
		<td>异步</td>
	</tr>
</table>

参考链接
https://zhuanlan.zhihu.com/p/467991875

## arguments 怎么转化成真数组

- arguments 是一个伪数组，是当前函数的内置对象，存储所有的形参，有 length 属性，但是不能用数组的方法。
- [...arguments] 扩展运算符的方式，拿取剩余参数
- Array.prototype.slice.call(arguments);使用 call 一个对象调用另一个函数的方法，slice 切割数组并返回一个新的数组
- [].slice.call() 因为[].slice === Array.prototype.slice
- 遍历：arguments 有 length 属性，所以，可以遍历 arguments 取出每一个元素，并放进新的数组中

## js 的对象的常用的方法

```js
Object.assign(); //复制对象，创建一个新的对象
Object.entries(); //返回自身可枚举的[key,value]
Object.keys();
Object.values();
Object.hasOwnProperty(key); //是否有这个属性 true/false
Object.getOwnPropertyNames(); //取得对象自身可枚举的属性名
//for in 对对象进行遍历，可以拿到自身以及原型链上的可枚举的属性
Object.freeze(); //冻结一个对象，不可修改，不可删除。不可添加新的属性
Object.prototype.toString(); // 返回数组[object,object/array/function等]
//判断是数组还是对象就是用的这个方法
Object.defineProerty(obj, attr, descriptor);
//可以对对象属性进行修改添加，删除等的操作
//参数1，要操作的对象
//参数2：要操作的属性名字
//参数3：属性描述符：是否可枚举，是否可读，可写，他的值等
```

## js 的字符串的常用的方法

```js
var str1 = 'wwww';
var str2 = 'jjjj';
var str3 = 'kkkk';

str.concat(); //拼接
str.includes(); //判断字符串是否包含在另外一个字符串中
str.indexOf();
str.lastIndexOf();
str.split(); //按特定的符号分割成字符串数组！
str.toLowerCase(); //转换成小写的形式
str.toUpperCase(); //转换成大写的形式
str.trim(); //去空格
str.substring(start, end); // 截取字串，不含开始，含结束，end可以小于start,会自动调换
str.slice(); //截取字串，含开始，含结束，end不可以小于start
str.substr(start, length); //截取指定长度的字符串
```

## js 的数组的常用的方法

```js
var arr = [0, 1, 2, 3, 4];

arr.push();
arr.pop();
arr.shift();
arr.unshift();
arr.reverse();
arr.every();
arr.some();
arr.forEach();
arr.filter();
arr.includes();
arr.map();
arr.reduce();
arr.indexOf();
arr.lastIndexOf(); //索引正序，但是从后往前找
arr.findIndex(); //找索引
arr.find(); //找满足条件的元素
arr.join(); //默认以逗号隔开
arr.join(' '); //无缝链接 将数组元素拼接成字符串
arr.slice(1, 2); //截取数组的一部分，不包含头部，包含尾部，不会修改原数组
arr.splice(1, 4); //从索引1开始删除4个元素,第二个是要删除的长度，第三个往后是要添加的元素
arr.splice(2, 0, 'i'); //从索引2开始，删除0个，加入一个’i‘
arr.splice(3, 1, 'o', 'i'); //从索引3开始，删除1个，添加两个字符串。
arr.flat(); //数组降维 ，返回新数组
arr.flat(1);
arr.flat(Infinity);
arr.entries(); //将数组返回一个对象，包含对象索引的键值对
```

## 拍平数组
```js
const ret = arr.flat(Infinity);
```

```ts
type MultiDimensionalArray = (number | MultiDimensionalArray)[];

const flat = function (arr: MultiDimensionalArray, depth: number): MultiDimensionalArray {
  while (depth > 0 && arr.some(Array.isArray)) {
    arr = [].concat(...arr);
    depth--;
  }
  return arr;
};
```

## 防抖与节流
<table>
	<thead>
		<th></th>
		<th>防抖</th>
		<th>节流</th>
	</thead>
	<tr>
		<td>使用逻辑</td>
		<td>只有当事件停止触发，并且经过了指定的延迟时间后，回调函数才会被执行。</td>
		<td>当一个事件被连续触发时，确保在指定的时间间隔内，回调函数最多只被执行一次。</td>
	</tr>
  <tr>
		<td>业务场景</td>
		<td>输入框搜索联想、窗口大小调整</td>
		<td>页面滚动事件、DOM 拖拽、高频点击</td>
	</tr>
</table>


### 防抖 debounce
```ts
type F = (...args: number[]) => void

function debounce(fn: F, t: number): F {
    let time = null;
    return function (...args) {
        if (time) clearTimeout(time);
        time = setTimeout(() => fn(...args), t);
    }
};

```

### 节流 throttle
```ts
type F = (...args: number[]) => void

function throttle(func: F, interval: number): () => void {
    let lastTime = 0;
    const _throttle = function(...args) {
        const remainTime = interval - (Date.now() - lastTime);
        if (remainTime <= 0) {
            lastTime = nowTime;
            func(...args);
        }
    }
    return _throttle;
}
```

## 实现并发控制
```js
async function asyncPool(poolLimit, array, iteratorFn) {
  const ret = [];
  const executing = [];
  for (const item of array) {
    const p = Promise.resolve().then(() => iteratorFn(item)); // compatible with synchronous function
    ret.push(p);
    if (poolLimit <= array.length) {
      const e = p.then(() => executing.splice(executing.indexOf(e), 1));
      executing.push(e);
      if (executing.length >= poolLimit) {
        await Promise.race(executing);
      }
    }
  }
  return Promise.all(ret);
}
```

reference: https://zhuanlan.zhihu.com/p/455838344