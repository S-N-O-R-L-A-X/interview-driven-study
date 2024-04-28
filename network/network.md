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
		<td>5MB</td>
		<td>5MB</td>
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
		<td>-</td>
		<td>-</td>
		<td>相同浏览器的不同页面可共享</td>
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