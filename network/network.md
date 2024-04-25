- [Network](#network)
	- [HTTP和HTTPS的异同/HTTPS的缺点](#http和https的异同https的缺点)
	- [TCP和UDP区别](#tcp和udp区别)
	- [拥塞控制与流量控制](#拥塞控制与流量控制)
	- [TCP 如何保持长连接 / TCP的keep-alive机制](#tcp-如何保持长连接--tcp的keep-alive机制)

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
		发送方维持一个拥塞窗口cwnd，
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
