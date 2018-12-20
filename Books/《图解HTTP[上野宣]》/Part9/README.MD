第9章 基于HTTP的功能追加协议

---

1.消除HTTP瓶颈的SPDY

Google在2010年发布了SPDY，缩短Web页面的加载时间50%

---

2.Ajax的解决方法

Asynchronous JavaScript and XML，异步JavaScript与XML技术，是一种有效利用JavaScript和DOM(Document Object Model，文档对象模型)的操作，以达到局部Web页面替换加载的异步通信手段。

---

3.Ajax的核心技术是名为XMLHttpRequest的API，通过JavaScript脚本语言的调用就能和服务器进行HTTP通信。

---

4.Comet的解决方法 

一旦服务器端有内容更新了，Comet不会让请求等待，而是直接给客户端返回响应。这是一种延迟应答，模拟实现服务器端向客户端推送(Server Push)的功能。

---

5.Ajax和Comet没有解决HTTP协议本身存在的问题

---

6.SPDY没有完全改写HTTP协议，而是在TCP/IP的应用层与运输层之间通过新加会话层的形式动作。同时，考虑到安全性问题，SPDY规定通信中使用SSL。

---

7.SPDY介于TCP(SSL)和HTTP之间 
- HTTP - 应用层 
- SPDY - 会话层 
- SSL - 表示层 
- TCP - 传输层

---

8.使用SPDY后，HTTP协议额外获得以下功能 
- 多路利用流 
- 赋予请求优先级 
- 压缩HTTP首部 
- 推送功能 
- 服务器提示功能

---

9.使用浏览器进行全双工通信的WebSocket 

WebSocket通信协议在2011年12月11日，被RFC6455-The WebSocket Protocol定为标准

---

10.WebSocket,即Web浏览器与Web服务器之间全双工通信标准。其中，WebSocket协议由IETF定为标准，WebSocket API由W3C定为标准。

---

11.WebSocket协议的主要特点 
- 推送功能 
- 减少通信量

2017.10.4 08:06:08~2017.10.4 08:31:06

---

12.握手-请求 

为了实现WebSocket通信，需要用到HTTP的Upgrade首部字段，告知服务器通信协议发生改变，以达到握手的目的。

GET / chat HTTP/1.1

Host:server.example.com

Upgrade:websocket

Connection:Upgrade

Sec-WebSocket-Key:dGhlIHNhbXBsZSBub25jZQ==

Sec-WebSocket-Protocol:chat,superchat


- Sec-WebSocket-Key字段内记录着握手过程中必不可少的键值 

- Sec-WebSocket-Protocol字段内记录使用的子协议

---

13.握手-响应 

对于之前的请求，返回状态码101 Switching Protocols的响应

HTTP/1.1 101 Switching Protocols

Upgrade: websocket

Connection:Upgrade

Sec-WebSocket-Key:s3pPLMBiTxaQ9kYGzzhZRbK+xOo=

Sec-WebSocket-Protocol:chat

---

14.成功握手确立WebSocket连接之后，通信时不再使用HTTP的数据帧，而采用WebSocket独立的数据帧。

---

15.WebSocket API 

JavaScript可调用”The WebSocket API”内提供的WebSocket程序接口，以实现WebSocket协议下全双工通信

---

16.WebDAV是一个可对Web服务器上的内容直接进行文件复制、编辑等操作的分布式文件系统。它作为扩展HTTP/1.1的协议定义在RFC4918

---

17.针对服务器上的资源，WebDAV新增加了一些概念 
- 集合：是一种统一管理多个资源的概念。以集合为单位可进行各种操作。也可实现类似集合的集合这样的叠加。 
- 资源：把文件或集合称为资源。 
- 属性：定义资源的属性。定义以”名称=值”的格式进行。 
- 锁：把文件设置成无法编辑状态。多人同时编辑时，可防止在同一时间进行内容写入。

---

18.WebDAV新增的方法 
- PROPFIND:获取属性 
- PROPPATCH:修改属性 
- MKCOL:创建集合 
- COPY:复制资源及属性 
- MOVE:移动资源 
- LOCK:资源加锁 
- UNLOCK:资源解锁

---

19.WebDAV新增的状态码 
- 102 Processing:可正常处理请求，但目前是处理中状态 
- 207 Multi-Status:存在多种状态 
- 422 Unprocessible Entity:格式正确，内容有误 
- 423 Locked:资源已被加锁 
- 424 Failed Dependency:处理与某请求关联的请求失败，因此不再维持依赖关系 
- 507 Insufficient Storage:保存空间不足

2017.10.5 12:04:08~2017.10.5 12:28:15
