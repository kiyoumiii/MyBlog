---
title: HTTP协议相关知识
date: 2024-08-12 23:15:03
categories:
- [计算机科学]
tags:
---

## 超文本传输协议HTTP

 超文本 HyperText
 HTTP虽然叫传输协议，但它实际上工作在TCP/IP协议的应用层，底层的数据传输由TCP或UDP负责。

 HTTP协议发展至今已有多个版本，最常用的是HTTP/1.1,HTTP/2和HTTP/3。

 - 目前HTTP/1.1依然被广泛使用。

 - HTTP/2引入了多路复用、二进制帧层、头部压缩等特性，提升了不少传输性能。

 - HTTP/3基于QUIC协议使用UDP作为传输层，进一步降低了连接延迟和提升了传输性能。

 值得注意的是，HTTPS是HTTP的加密安全版本，它在原始HTTP协议的基础上，加盖了一层SSL/TLS来实现加密传输

 HTTPSecure

 除了HTTP/3，TLS在其他版本中并不是强制要求的。

 可以看到，每一代协议升级，都是围绕性能和安全性展开的。

<br>
<div align="center">
    <img src="https://s2.loli.net/2024/08/15/GF18p4UoORwEdTJ.jpg">
</div>
<br>

HTTP协议大体上是一种问答形式，客户端发出请求，服务器处理请求，然后再给出响应。

服务器会根据不同场景返回不同的响应码。

2XX表示成功处理，3XX表示重定向，4开头表示客户端错误，5开头表示服务端错误

在请求和响应报文中，除了请求方法和响应码外，最值得关注的就是请求头和响应头。
比如：

- 用于请求上下文的Host、Referer、User-Agent

- 用于响应上下文的Allow、Server

- 用于缓存的Cache-Control、Last-Modified/Last-Modified-Since和ETag/If-NoneMatch

- 用于Cookie的Cookie和Set-Cookie

- 用于安全的X-Frame-Options、Strict-Transport-Security(HSTS)、Content-Security-Policy(CSP)

- 用于跨域控制(CORS)的Origin和Access-Control-*一套

- 用于描述消息主体的Content-*一套

<br>
<div align="center">
    <img src="https://s2.loli.net/2024/08/15/bmGuUHNspIXVW6O.jpg">
</div>
<br>

浏览器加载资源会使用HTTP协议，前端与服务端的异步请求通常也通过HTTP协议完成。

最早我们会通过XMLHttpRequest(XHR)，在浏览器中发起一个异步请求，后来许多第三方库基于它做了功能扩展，比如jQuery、ajx、superagent和axios等，直到出现了新的Fetch标准。

虽然API都长得一样，但Fetch标准在不同环境下有不同的实现，比如Node.js环境下的fetch是基于Undici实现的，而在边缘运行时（Edge Runtime）中，Fetch API也会依据平台有所不同，因此，在现代前端，应尽可能**使用Fetch API或其封装库来管理异步请求**。

下面使用Fetch API和Node.js原生http模块，举例说明Content-Type是如何工作的，请求代码和报文是这样的：
<br>
<div align="center">
    <img src="https://s2.loli.net/2024/08/15/eCY8fKtcdJFQLgU.jpg">
</div>
<br>

对应的服务端处理代码和响应报文是这样的：
<br>
<div align="center">
    <img src="https://s2.loli.net/2024/08/15/GmO1EJIShQHC8lA.jpg">
</div>
<br>


需要注意的是，请求头和响应头中的Content-Type表示消息主体的数据类型，它可以是JSON、Form，也可以是其他任何MIME类型，不同的类型就要有不同的处理程序。

在这个例子中，客户端发送了一段JSON类型的数据，服务端应通过JSON parse处理，然后响应了一段纯文本类型，客户端应通过text()方法处理它。

这是一个易错点，前端使用第三方库时默认为JSON请求，而服务端默认以Form处理时，会百思不得其解为什么我处理不了你的请求，原因就是没有理解Content-Type的含义。

在不同的场景和环境下，调试HTTP有不同的方法。
- 最常见的当然是使用浏览器开发者工具，比如在Chrome DevTools的Network选项卡下，可以看到非常详细的HTTP请求和响应信息。
- 有时候只想快速看看服务端的响应情况，则可以通过cURL等命令行工具完成。
- 在针对API测试的场景下，可以通过Postman等自动化工具来批量测试。
- 而要调试移动设备内的HTTPS，则需要安装信任证书以及通过网络代理工具来实现。
- 对于远程或是生产环境，则更多是通过抓包和分析服务端日志来完成

HTTP的功能很强大，它足够满足大多数应用场景。但在大型客户端应用中，为了更高效和安全的传输数据，同时兼容HTTP协议，会有一些变化。
我们应该知道，不是所有的客户端环境都支持先进的HTTP/2或HTTP/3，原始HTTP协议在更复杂的高并发场景下，会不够高效和稳定。
因此，大型技术基建通常会设计一层无线网关（Gateway），并对HTTP协议进行定制。

<br>
<div align="center">
    <img src="https://s2.loli.net/2024/08/15/d1b2DgR5xVXIcyu.jpg">
</div>
<br>

增加登录验证、请求跟踪、监控、限流等功能。而前端代码通过远程调用（RPC）的方式，而非直接使用原始HTTP

以bilibili客户端为例，前端发起一个grpc请求至gateway网关，同时发送了多个自定义请求头，比如x-bili-mid表示当前用户，x-bili-trace-id用于链路日志跟踪，x-bili-device-bin表示设备信息等等。

在服务端的响应头中，Content-Type表示这是一个grpc响应，x-bili-trace-id用于日志跟踪等，可以看到，相比浏览器中的HTTP，在客户端中的HTTP会更复杂，定制化的HTTP协议能带来更强大的功能。