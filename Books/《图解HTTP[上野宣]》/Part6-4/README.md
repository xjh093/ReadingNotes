24.首部字段Date表明创建HTTP报文的日期和时间。

HTTP/1.1 协议使用在RFC1123中规定的日期时间的格式，如下示例。 

`Date: Tue, 03 Jul 2012 02:40:59 GMT`

之前的HTTP协议版本中使用在RFC850中定义中格式，如下所示。 

`Date: Tue, 03-Jul-12 04:40:59 GMT`

除此之外，还有一种格式。这与C标准库内的asctime()函数的输出格式一致。 

`Date: Tue Jul 03 04:40:59 2012`

---

25.Pragma是HTTP/1.1之前版本的历史遗留字段，公作为与HTTP/1.0的向后兼容而定义。 

规范定义的形式唯一，如下所示。 

`Pragma: no-cache`

该首部字段属于通用首部字段，只用在客户端发送的请求中，要求所有的中间服务器不返回缓存的资源。

中间服务器以HTTP/1.1为基准，则使用Cache-Control:no-cache指定缓存处理方式是最为理想的。

要求所有中间服务器使用HTTP/1.1是不现实的，因此，发送的请求会同时含有两个首部字段： 
```
Cache-Control: no-cache 
Pragma: no-cache
```
---

26.首部字段Trailer会事先说明在报文主体后记录了哪些首部字段。 

该首部字段可应用在HTTP/1.1版本分块传输编码时
```
HTTP/1.1 200 OK 
Date: Tue, 03 Jul 2012 04:40:56 GMT 
Content-Type: text/html 
… 
Transfer-Encoding: chunked 
Trailer: Expires

…(报文主体)… 
0 
Expires:Tue, 28 Sep 2004 23:59:59 GMT
```
---

27.首部字段Transfer-Encoding规定了传输报文主体时采用的编码方式。 

HTTP/1.1的传输编码方式仅对分块传输编码有效。

---

28.首部字段Upgrade用于检测HTTP协议及其他协议是否可以使用更高的版本进行通信，其参数值可以用来指定一个完全不同的通信协议。
```
GET /index.htm HTTP/1.1 
Upgrade: TLS/1.0 
Connection: Upgrade

HTTP/1.1 101 Switching Protocols 
Upgrade: TLS/1.0, HTTP/1.1 
Connection: Upgrade
```
对于附有首部字段Upgrade的请求，服务器可用101 Switching Protocol 状态码作为响应返回

---

29.首部字段Via可以追踪客户端与服务器之间的请求各响应报文的传输路径。 

首部字段Via不仅可以追踪报文的转发，还可避免请求回环的发生。

---

30.Warning 

HTTP/1.1的Warning首部是从HTTP/1.0的响应首部(Retry-After)演变过来的。 

该首部通常会告知用户一些与缓存相关的问题的警告。

Warning首部的格式： 

Warning: [警告码][警告的主机:端口号] “[警告内容]” ([日期时间])

HTTP/1.1警告码 

警告码 - 警告内容 - 说明 

- 110 - Response is stale(响应已过期) - 代理返回已过期的资源 
- 111 - Revalidation is failed(再验证失败) - 代理再验证资源有效性时失败(服务器无法到达等原因) 
- 112 - Disconnection operation(断开连接操作) - 代理与互联网连接被故意切断 
- 113 - Heuristic expiration(试探性过期) - 响应的使用期超过24小时(有效缓存的设定时间大于24小时的情况下) 
- 199 - Miscellaneous warning(杂项警告) - 任意的警告内容 
- 214 - Transformation applied(使用了转换) - 代理对内容编码或媒体类型等执行了某些处理时 
- 299 - Miscellaneous persistent warning(持久杂项警告) - 任意的警告内容

2017.3.23 20:45 ~ 2017.3.23 21:32
