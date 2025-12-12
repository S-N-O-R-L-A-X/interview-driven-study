- [Network](#network)
	- [HTTP和HTTPS的异同/HTTPS的缺点](#http和https的异同https的缺点)
	- [TCP和UDP区别](#tcp和udp区别)
	- [拥塞控制与流量控制](#拥塞控制与流量控制)
	- [TCP 如何保持长连接 / TCP的keep-alive机制](#tcp-如何保持长连接--tcp的keep-alive机制)
	- [cookie vs session vs local storage vs session storage](#cookie-vs-session-vs-local-storage-vs-session-storage)
	- [XSS vs CSRF](#xss-vs-csrf)
		- [XSS](#xss)
			- [后果](#后果)
			- [预防方式](#预防方式)
		- [CSRF](#csrf)
			- [后果](#后果-1)
			- [预防方式](#预防方式-1)
		- [异同](#异同)
	- [跨域问题](#跨域问题)
		- [跨域资源共享(CORS, Cross Origin Resource Sharing)](#跨域资源共享cors-cross-origin-resource-sharing)
			- [简单请求](#简单请求)
		- [解决方案](#解决方案)
			- [node 正向代理](#node-正向代理)
			- [nginx 反向代理](#nginx-反向代理)
			- [JSONP 不推荐](#jsonp-不推荐)
				- [优点](#优点)
				- [缺点](#缺点)
				- [实现方式](#实现方式)
			- [后端配置](#后端配置)
			- [websocket](#websocket)
	- [`GET`和`POST`的区别](#get和post的区别)
	- [浏览器输入域名后发生什么](#浏览器输入域名后发生什么)
	- [SSE 和 websocket 的区别](#sse-和-websocket-的区别)
		- [upgrade机制](#upgrade机制)
	- [HTTP 2.0 vs HTTP 3.0](#http-20-vs-http-30)
		- [更换原因](#更换原因)
		- [队头阻塞问题](#队头阻塞问题)

# Network

## HTTP和HTTPS的异同/HTTPS的缺点
1、HTTP是超文本传输协议，其中的信息是明文传输的。HTTPS是HTTP协议再加上SSL（安全套接字层），具有安全性。
2、HTTP不验证通信方的身份，通信方的身份有可能遭遇伪装；HTTPS需要到CA（证书颁发机构）申请证书，一般免费证书较少，因而需要一定费用。
3、HTTP和HTTPS使用的是完全不同的连接方式，用的端口也不一样，前者是80，后者是443。
4、HTTP无法证明报文的完整性，报文有可能遭篡改。
5、HTTP的连接很简单，是无状态的；HTTPS协议是由SSL+HTTP协议构建的可进行加密传输、身份认证的网络协议，比HTTP协议安全。
6、HTTPS连接缓存不如HTTP高效，流量成本高。
7、HTTPS连接服务器端资源占用高很多，支持访客多的网站需要投入更大的成本。
8、HTTPS协议在传输数据时需要进行加密和解密的操作，延长页面的加载时间，增加耗电。
9、HTTPS协议握手阶段比较费时，对网站的响应速度有影响，影响用户体验。比较好的方式是采用分而治之，类似12306网站的主页使用HTTP协议，有关于用户信息等方面使用HTTPS。

## TCP和UDP区别
<table>
	<thead>
		<th></th>
		<th>TCP</th>
		<th>UDP</th>
	</thead>
	<tr>
		<td>全称</td>
		<td>传输控制协议 Transmission Control Protocol</td>
		<td>用户数据报协议 User Datagram Protocol</td>
	</tr>
	<tr>
		<td>无连接</td>
		<td>面向连接</td>
		<td>无连接</td>
	</tr>
	<tr>
		<td><a href="#/network/network?id=拥塞控制与流量控制">拥塞控制</a></td>
		<td>有</td>
		<td>无</td>
	</tr>
	<tr>
		<td><a href="#/network/network?id=拥塞控制与流量控制">流量控制</a></td>
		<td>有</td>
		<td>无</td>
	</tr>
	<tr>
		<td>读数据的边界</td>
		<td>面向字节流</td>
		<td>面向报文</td>
	</tr>
	<tr>
		<td>通信方式</td>
		<td>全双工通信</td>
		<td>支持一对一、一对多、多对一和多对多</td>
	</tr>
</table>

## 拥塞控制与流量控制
发送方维护一个拥塞窗口cwnd，接收方维护一个接收窗口rwnd。
<table>
	<thead>
		<th></th>
		<th>拥塞控制</th>
		<th>流量控制</th>
	</thead>
	<tr>
		<td>作用</td>
		<td>避免给整体的网络造成网络负载过大</td>
		<td>控制发送方的窗口大小，让接收方来得及接收</td>
	</tr>
	<tr>
		<td>实现方式</td>
		<td>慢启动、拥塞避免、快重传、快恢复。
		<br/>慢启动：建立连接后，从1开始倍增窗口，直到达到ssthreshold。
		<br/>拥塞避免：在达到ssthreshold后，每一次 RTT 往返后，拥塞窗口仅+1，控制拥塞窗口的增长速率
		<br/>快重传：发送方只要一连收到三个重复确认就应当立即重传对方尚未收到的报文段，不必继续等待该报文的重传计时器到期。
		<br/>快恢复：当发送方连续收到三个重复确认时，把ssthreshold和窗口变为当前窗口的一半，然后执行拥塞避免算法。（目前采用的TCP Reno版本，已废弃的TCP Tahoe版本会重新从1执行慢启动）
		</td>
		<td>滑动窗口，接收方告知发送方自己的窗口大小。</td>
	</tr>
</table>

## TCP 如何保持长连接 / TCP的keep-alive机制
当一个 TCP 连接建立之后，启用 TCP keep-alive 的一端便会启动一个计时器，当这个计时器数值到达 0 之后，服务器端会发出一个ACK探测包，理论上不包含任何数据，或仅包含一个无意义字节。
I.如果客户主机依然正常运行，并从服务器可达。客户的TCP响应正常，而服务器也知道对方是正常的，服务器将keep-alive定时器复位。
II. 如果客户的TCP没有响应，那么将继续发送九个探测包，如果依然无响应则关闭连接。

## cookie vs session vs local storage vs session storage

<table>
	<thead>
		<th></th>
		<th>cookie</th>
		<th>session</th>
		<th>local storage</th>
		<th>session storage</th>
	</thead>
	<tr>
		<td>用处</td>
		<td>一种记录客户端状态的机制</td>
		<td>一种记录客户端状态的机制</td>
		<td>存储跨session大量数据的机制</td>
		<td>存储大量数据的机制</td>
	</tr>
	<tr>
		<td>其它特点</td>
		<td>每次请求会放在请求头，不安全</td>
		<td>服务端向客户端发送SESSIONID的cookie</td>
		<td>数据操作比 cookie 方便</td>
		<td>数据操作比 cookie 方便</td>
	</tr>
	<tr>
		<td>存储方式</td>
		<td>键值对</td>
		<td>类似于哈希表</td>
		<td>键值对</td>
		<td>键值对</td>
	</tr>
	<tr>
		<td>存储位置</td>
		<td>客户端</td>
		<td>服务端</td>
		<td>客户端</td>
		<td>客户端</td>
	</tr>
	<tr>
		<td>存储大小</td>
		<td>4KB</td>
		<td>无限制</td>
		<td>5MB或更大</td>
		<td>5MB或更大</td>
	</tr>
	<tr>
		<td>生命周期</td>
		<td>无过期时间内存，关闭浏览器后消失，有过期时间硬盘</td>
		<td>session有效期</td>
		<td>永久</td>
		<td>当前会话</td>
	</tr>
	<tr>
		<td>作用域</td>
		<td>相同浏览器的同源窗口可共享</td>
		<td>-</td>
		<td>相同浏览器的同源窗口可共享</td>
		<td>相同页面的同源iframe可共享</td>
	</tr>
	<tr>
		<td>应用场景</td>
		<td>不敏感信息</td>
		<td>服务端使用</td>
		<td>长期登录</td>
		<td>一次性登录</td>
	</tr>
</table>

## XSS vs CSRF
### XSS
XSS（Cross-Site Scripting，跨站脚本攻击）通过注入恶意脚本来利用用户对网站的信任，从而在用户的浏览器上执行恶意操作。

<table>
	<thead>
		<th></th>
		<th>Stored (持久型) XSS 攻击</th>
		<th>Reflected (反射型) XSS 攻击</th>
		<th>DOM-based XSS 攻击</th>
	</thead>
	<tr>
		<td>攻击方式</td>
		<td>攻击者将恶意脚本存储在服务器上，然后这些脚本被返回给用户，被用户浏览器解释并执行。</td>
		<td>攻击者将恶意脚本注入到一个 URL 中，当用户访问带有恶意脚本的 URL 时，脚本会被解释并执行。</td>
		<td>攻击者通过修改页面的 DOM 结构来注入恶意脚本，当页面解析并执行这些脚本时，就会导致攻击。</td>
	</tr>
	<tr>
		<td>常见场景</td>
		<td>在用户评论、留言板等地方注入恶意脚本，一旦其他用户访问这些内容，就可能受到攻击。</td>
		<td>用户点击恶意链接。</td>
		<td>-</td>
	</tr>
</table>

#### 后果
- 盗取用户的敏感信息
- 在用户账户下执行未授权的操作
- 重定向用户到恶意站点
- 传播恶意链接和脚本，影响其他用户
- 篡改网页内容，伪造虚假信息

#### 预防方式
1. 将用于登录相关的cookie设置为httpOnly，避免被客户端脚本直接读取。
2. 对用户输入和输出进行过滤，对其中注入的脚本进行转义
3. 使用自定义响应标头(Content-Type 和 X-Content-Type-Options)来管理浏览器响应解释

### CSRF
CSRF（Cross-Site Request Forgery，跨站请求伪造）利用用户已经认证过的会话信息（通常通过引诱用户点击图片或链接）伪造用户的请求，从而在用户不知情的情况下执行恶意操作。

#### 后果
- 用户数据丢失
- 用户数据被修改

#### 预防方式
1. 使用 CSRF Token
2. 校验请求头的referer属性值
3. 限制跨域请求

### 异同
相同点：
- 均为客户端攻击
- 滥用同源策略

不同点：
- XSS是双向攻击，允许攻击者执行恶意脚本、访问响应，并将后续敏感数据发送到攻击者选择的目的地；CSRF是一种单向攻击机制，这意味着攻击者只能发起HTTP请求，但不能检索已发起请求的响应。
- XSS不需要用户身份验证的用户处于活动会话，CSRF攻击要求经过身份验证的用户处于活动会话中。
- XSS攻击的恶意代码存储在站点中，CSRF攻击的恶意代码存储在受害用户访问的第三方站点中。

## 跨域问题
跨域，本质是跨源问题。
同源策略需要协议+域名+端口相同
img, link, script标签本身允许跨域加载资源。

### 跨域资源共享(CORS, Cross Origin Resource Sharing)
CORS使用额外的HTTP头来告诉浏览器让运行在一个 origin (domain) 上的 Web 应用被准许访问来自不同源服务器上的指定的资源。

#### 简单请求
- 仅使用GET/POST/HEAD方法
- 标头除了被用户代理自动设置的标头字段（例如 Connection、User-Agent 或其他在 Fetch 规范中定义为禁用标头名称的标头）外只可使用 Accept, Accept-Language, Content-Language, Content-Type（仅允许text/plain, multipart/form-data, application/x-www-form-urlencoded）, Range（只允许简单的范围标头值）
- 如果请求是使用 XMLHttpRequest 对象发出,在返回的XMLHttpRequest.upload 对象属性上不能注册任何事件监听器
- 请求中没有使用 ReadableStream 对象

### 解决方案

#### node 正向代理
利用服务端请求不会跨域的特性，让接口和当前站点同域。
主流框架都可以通过配置proxy来解决，虽然是不同框架，但基本都用的http-proxy-middleware。

#### nginx 反向代理
在浏览器和服务器之间加一个反向代理服务器

#### JSONP 不推荐
JSONP(JSON with Padding)主要利用script标签没有跨域限制的特性，由于没有使用XHR请求，所以没有跨域问题。

##### 优点
- 兼容性好
- 在请求完毕后可以通过调用 callback 的方式回传结果
  
##### 缺点
- 仅支持get方法
- 只支持跨域 HTTP 请求这种情况，不能解决不同域的两个页面之间如何进行 JavaScript 调用的问题
- JSONP 在调用失败的时候不会返回各种 HTTP 状态码
- 提供 JSONP 的服务若存在页面注入漏洞，则所有调用这个 JSONP 的网站都会存在漏洞。

##### 实现方式
与服务端约定好一个回调函数名，服务端接收到请求后，将返回一段 Javascript，在这段 Javascript 代码中调用了约定好的回调函数，并且将数据作为参数进行传递。当网页接收到这段 Javascript 代码后，就会执行这个回调函数，这时数据已经成功传输到客户端了。

前端代码

```js
<script>
function test(data) {
    console.log(data.name);
}
</script>
<script src="http://127.0.0.1:8088/jsonp?callback=test"></script>
```

后端代码

```js
res.end('test({"name": "Monkey"})');
```

#### 后端配置
普通跨域请求：只需服务端设置 `Access-Control-Allow-Origin` 即可，前端无须设置，若要带 cookie 请求：前后端都需要设置。前端设置`withCredentials`为 true,后端设置`Access-Control-Allow-Credentials`为 true, 同时`Access-Control-Allow-Origin`不能设置为`*`

#### websocket
websocket 不使用http，也就没有跨域问题。

## `GET`和`POST`的区别
* GET 方法的含义是请求从服务器获取资源，这个资源可以是静态的文本、页面、图片视频等。
* POST 方法则是相反操作，它向 URI 指定的资源提交数据，数据放在报文的 body 里。
GET 方法就是安全且幂等的，因为它是「只读」操作，无论操作多少次，服务器上的数据都是安全的，且每次的结果都是相同的。POST 因为是「新增或提交数据」的操作，会修改服务器上的资源，所以是不安全的，且多次提交数据就会创建多个资源，所以不是幂等的。

## 浏览器输入域名后发生什么
1.	URL解析：浏览器对网址进行格式化检查，确认是有效网址，如果没有给定什么协议，会默认是http协议。
2.	DNS查询：根据DNS查询IP地址。
3.	协议栈：通过 DNS 获取到 IP地址 后，就可以把 HTTP 的传输工作交给操作系统中的协议栈。
4.	建立TCP连接：三次握手建立连接。
5.	加上IP首部：委托 IP 模块将数据封装成网络包发送给通信对象。
6.	加上MAC头部：生成了 IP 头部之后，接下来网络包还需要在 IP 头部的前面加上 MAC 头部。
7.	网卡出口：把 IP 生成的网络包（数字信号）转换为电信号，开始在网线上传输。
8.	将包通过交换机传输：交换机根据 MAC 地址表查找 MAC 地址，然后将信号发送到相应的端口。
9.	通过路由器传输：网络包经过交换机之后，现在到达了路由器，并在此被转发到下一个路由器或目标设备。
10.	数据报抵达服务器后，要拆解数据包。
11.	服务器响应请求：解析请求，生成响应头和具体响应内容。
12.	浏览器解析：根据不同的响应状态码来做不同的事情。
13.	浏览器渲染页面：浏览器显示HTML，浏览器向服务器发送请求获取嵌入在HTML中的对象，浏览器发送异步请求。
14.	关闭TCP连接：四次挥手判断是否断开连接。

## SSE 和 websocket 的区别
SSE(server-sent event) 和 websocket 都是实时通信技术。

<table>
	<thead>
		<th></th>
		<th>SSE</th>
		<th>websocket</th>
	</thead>
	<tr>
		<td>实现方式</td>
		<td>客户端通过EventSource发送一个普通的 HTTP 请求来“订阅”一个事件流。服务器保持这个连接打开，并随时可以发送新的数据。</td>
		<td>客户端通过 WebSocket 发起一个带有 Upgrade: websocket 头的 HTTP 请求，服务器返回 101 Switching Protocols 响应，表示协议升级成功。握手完成后，连接不再遵循 HTTP 协议。客户端和服务器都可以随时、独立地使用轻量级的 WebSocket 帧来发送文本或二进制数据。</td>
	</tr>
	<tr>
		<td>连接方式</td>
		<td>HTTP长连接</td>
		<td>升级HTTP连接</td>
	</tr>
	<tr>
		<td>支持传输内容</td>
		<td>仅文本</td>
		<td>文本和二进制文件</td>
	</tr>
	<tr>
		<td>自动重连</td>
		<td>自带</td>
		<td>需手动实现</td>
	</tr>
	<tr>
		<td>通信方式</td>
		<td>单工</td>
		<td>全双工</td>
	</tr>
	<tr>
		<td>兼容性</td>
		<td>与现有基础设施兼容</td>
		<td>一般，某些配置不当的旧代理服务器可能无法正确处理 WebSocket 的 Upgrade 头</td>
	</tr>
	<tr>
		<td>适用场景</td>
		<td>只需要从服务器接收实时数据流，客户端不需要频繁地向服务器发送数据时，如显示实时股价、监控、大模型流式输出</td>
		<td>需要双向通信，或高效支持二进制数据时，如聊天室、在线游戏中显示玩家位置和状态</td>
	</tr>
</table>

### upgrade机制
HTTP/1.1 协议提供了一种使用 Upgrade 标头字段的特殊机制，这一机制允许将一个已建立的连接升级成新的、不相容的协议。（HTTP/2 明确禁止使用此机制）
客户端使用 Upgrade 标头字段请求服务器，如果服务器决定升级这次连接，就会返回一个 101 Switching Protocols 响应状态码，和一个要切换到的协议的标头字段 Upgrade。如果服务器没有（或者不能）升级这次连接，它会忽略客户端发送的 Upgrade 标头字段，返回一个常规的响应。

## HTTP 2.0 vs HTTP 3.0
事实上，两者的主要区别在于底层协议上。

<table>
	<thead>
		<th></th>
		<th>HTTP2.0</th>
		<th>HTTP3.0</th>
	</thead>
	<tr>
		<td>底层传输协议</td>
		<td>TCP</td>
		<td>基于UDP的QUIC</td>
	</tr>
	<tr>
		<td>队头阻塞问题</td>
		<td>存在于传输层</td>
		<td>不存在</td>
	</tr>
	<tr>
		<td>连接建立速度</td>
		<td>慢 (TCP握手 + TLS握手，至少2RTT)</td>
		<td>快 (首次连接需要 1-RTT 完成连接和加密协商，如果之前连接过服务器可以实现 0RTT，即第一个数据包开始携带应用数据)</td>
	</tr>
	<tr>
		<td>安全加密</td>
		<td>非强制，但主流浏览器只支持基于 TLS 加密的 HTTP2.0</td>
		<td>强制加密，是协议的一部分</td>
	</tr>
	<tr>
		<td>连接迁移</td>
		<td>不支持 (IP/端口改变需重建连接)</td>
		<td>支持 (基于连接ID)</td>
	</tr>
	<tr>
		<td>兼容性</td>
		<td>与现有基础设施兼容</td>
		<td>一般，某些配置不当的旧代理服务器可能无法正确处理 WebSocket 的 Upgrade 头</td>
	</tr>
	<tr>
		<td>使用情况</td>
		<td>目前主流</td>
		<td>已标准化，逐步普及</td>
	</tr>
</table>

### 更换原因
TCP 的核心机制已被嵌入操作系统内核和中间设备（如路由器、防火墙），难以升级和修改。QUIC 作为一个在用户空间实现的协议，迭代更快，不受历史包袱的限制。

### 队头阻塞问题
队头阻塞 Head-of-line blocking（HOL blocking）指一旦发生丢包，就会阻塞住所有的 HTTP 请求。
HTTP2.0协议的多路复用机制解决了HTTP层的队头阻塞问题，但是在TCP层仍然存在队头阻塞问题。
HTTP3.0使用UDP后避免了此问题。
