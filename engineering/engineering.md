# 前端实战

- [前端实战](#前端实战)
	- [对前端工程化的理解](#对前端工程化的理解)
		- [模块化](#模块化)
		- [组件化](#组件化)
		- [规范化](#规范化)
		- [自动化](#自动化)
	- [webpack 的基本概念](#webpack-的基本概念)
		- [构建流程](#构建流程)
			- [四个核心概念](#四个核心概念)
		- [webpack 常用插件](#webpack-常用插件)
	- [vite vs webpack](#vite-vs-webpack)
	- [iframe跨域通信](#iframe跨域通信)
	- [前端分片上传](#前端分片上传)
		- [功能](#功能)
		- [流程](#流程)
	- [性能优化方案](#性能优化方案)

## 对前端工程化的理解

前端工程化是为了提高开发过程中的开发效率，减少不必要的重复工作时间，具体可以从四方面去讨论，模块化，组件化，规范化和自动化。

### 模块化
将大的文件拆分成互相依赖的小文件，再进行统一的拼装和加载。
- js 的模块化：利用 webpack+babel 的模式将所有模块系统进行打包，同步加载，也可以搭乘多个 chunk 异步加载。
- css 模块化：之前的 sass less 等预处理器虽然实现了 css 的拆分，但是并没有解决模块化很重要的一个问题，即选择器的全局污染问题。有三种解决办法，第一种是利用 webcomponents 的技术实现，这个技术虽然解决了全局污染问题，但是由于兼容性问题，目前用的不多，第二种是 css in js 将 css 的技术全部摒，利用 js 或者 json 格式去加载 css，这种方式简单粗暴，并且不容易处理伪类选择器的问题，被大众所认可的是第三种解决方案，即 css modules ，所有的 css 文件由 js 来管理，这种技术最大程度利用了 css 的生态和模块化的原则，其中 vue 中的 scoped 就是这种技术的提现。利用浏览器的 script 标签，type 类型选 modules 类型即可。
- 资源的模块化：webpack 的成功不仅仅是因为将 js 系统进行模块化处理，而是它的模块化原理，即任何资源都可以模块化且应该模块化处理，优点有以下三点，1：目录结构清晰化，2：资源处理集成化，3：项目依赖单一化。

### 组件化
将 UI 页面拆分正有模板+样式+逻辑组成的功能单元
模块化是在资源和代码方面对文件的拆分，而组件化是在 UI 层面进行的拆分。传统前端框架的思想是以 dom 优先，先操作 dom，再写出可复用的逻辑单元来操作 dom，而组件化框架是组件优先，将 dom 和与之一起的逻辑组成一个组件，再进行引用。我们封装了组件后，还需要对组件间的关系进行判定，例如继承，扩展，嵌套，包含等，这些关系统称为依赖

### 规范化
项目前期规范制定的好坏，直接决定后期的开发质量，分为项目目录规范化，编码规范化，前后端接口规范化，git分支管理，commit 描述规范，组件管理等编码规范化分为 htmlcss js img 命名规范这几类 接口规范，目的是规则先行，以减少联调中不必要的问题和麻烦，自责划分 前端，渲染逻辑和交互逻辑，后台，处理业务逻辑，各种格式的规定，例如 json 尽量简洁轻量，日期尽量字符串等等。

### 自动化
让简单重复的工作交给机器完成，例如自动化测试，自动化部署，自动化构建，持续继承等。

## webpack 的基本概念

### 构建流程
1. 根据 package.json 里的命令行和配置文件中收集参数
2. 传入参数，创建 compiler 实例；
3. 根据使用的 plugins，compiler 实例开启各种钩子，注册各种事件，并将相应钩子事件进行收集；
4. 根据入口文件来递归模块查找，并根据配置文件使用对应的 loader 对模块进行编译处理；
5. 编译完成后输出 chunk，触发挂载钩子上的plugin事件做相应处理，最后输出 bundle；

reference: https://zhuanlan.zhihu.com/p/611527476

#### 四个核心概念
- Entry（入口） 是 webpack 的入口起点，指示 webpack 应该以哪个文件作为其构建内部依赖图的开始。
- Output（输出） 属性告诉 webpack 输出创建的打包文件的位置，也可指定打包文件的名称，默认位置为 ./dist。
- Loader（加载器） 可以理解为 webpack 的编译器，它使得 webpack 可以处理一些非 JavaScript 文件。在对 loader 进行配置的时候，test 属性标志有哪些后缀的文件应该被处理，是一个正则表达式，use 属性指定 test 类型的文件应该使用哪个 loader 进行预处理。
- Plugins（插件）可以用于执行范围更广的任务，包括打包、优化、压缩、搭建服务器等等，要使用一个插件，一般是先使用 npm 包管理器进行安装，然后在配置文件中引入，最后将其实例化后传递给 plugins 数组属性。

### webpack 常用插件
- html-webpack-plugin 用于生成一个 html 文件，并将最终生成的 js，css 以及一些静态资源文件以 script 和 link 的形式动态插入其中
- webpack-dev-server 用于实时的打包编译，打包好的 main.js 是托管到了内存中，所以在项目根目录中看不到，但是我们可以认为在项目的根目录中，有一个看不见的 main.js
- CommonsChunkPlugin 用来提取第三方库（如 jQuery）和公共模块，常用于为多页面应用程序生成公共 chunk，避免重复引用。

## vite vs webpack
<table>
	<thead>
		<th></th>
		<th>vite</th>
		<th>webpack</th>
	</thead>
  <tr>
		<td>开发服务器</td>
		<td>开箱即用</td>
		<td>通过webpack-dev-server</td>
	</tr>
	<tr>
		<td>生态</td>
		<td>略弱</td>
		<td>完整</td>
	</tr>
	<tr>
		<td>打包方式</td>
		<td>开发时利用本地 ES 模块提供源代码（生产模式用rollup），源代码转换和服务在浏览器请求时进行</td>
		<td>需要额外配置来高效实现代码拆分，预先打包源代码和依赖项</td>
	</tr>
  <tr>
		<td>ts支持</td>
		<td>开箱即用</td>
		<td>需要额外配置和插件来支持</td>
	</tr>
  <tr>
		<td>缓存处理</td>
		<td>无缝处理</td>
		<td>需要配置</td>
	</tr>
  <tr>
		<td>优势</td>
		<td>快速的冷启动速度和高效的 HMR</td>
		<td>预先打包数据，浏览器导航速度快</td>
	</tr>
</table>

## iframe跨域通信
1. 父页面通过子页面url的query参数传参
  iframe.src=`https://examples.com?id=1`
2. 父页面通过子页面url的锚点传参
  iframe.src=`https://examples.com#1`
3. cookie
* 同源时可直接读写 document.cookie
* 非同源时要求父子窗口共享顶级域名，设置 Cookie 的 `domain` 属性为域名，`SameSite=None` 和 `Secure` 属性

发送方
`document.cookie = "token=abc123; domain=.example.com; path=/; SameSite=None; Secure"`

接收方
`const token = document.cookie.split('; ').find(row => row.startsWith('token='))?.split('=')[1];`
4. `postMessage`

发送方
`otherWindow.postMessage(message, targetOrigin, [transfer]);`

接收方
```js
window.addEventListener("message", messageHandler);
function messageHandler(event) {
    // 必须验证消息来源
    const allowedOrigins = ['https://trusted.example'];
    if (!allowedOrigins.includes(event.origin)) return;
    
    // 处理有效消息
    console.log('Received:', event.data);
}
```

## 前端分片上传
### 功能
* 检查是否已上传
* 断点续传
* 分片上传，减小请求大小

### 流程
用户选择文件 → 计算文件哈希 → 文件分片 → 上传分片 → 合并分片

```js
async function upload() {
	// get file
  const file = document.getElementById('fileInput').files[0];
  if (!file) return;

  // calculate hash
  const fileHash = await calculateHash(file);
  
  // call api to check whether the file has existed
  const { data: existData } = await checkExistedFile(fileHash);
  if (existData.exist) {
    // file has existed
    return;
  }

  const chunkSize = 5 * 1024 * 1024; // 5MB chunk
  const chunkCount = Math.ceil(file.size / chunkSize);
  const uploadedChunks = existData.uploadedChunks || [];

  for (let i = 0; i < chunkCount; i++) {
    // skip the uploaded chunks
    if (uploadedChunks.includes(i)) continue;

		// get the chunk
    const start = i * chunkSize;
    const end = Math.min(start + chunkSize, file.size);
    const chunk = file.slice(start, end);

    await uploadChunk({chunk, idx:i});
  }

  // call api to merge chunks
  await mergeChunks();
}
```


##  性能优化方案
* 静态资源使用cdn

懒加载


  vite的特性
vite热更新怎么实现