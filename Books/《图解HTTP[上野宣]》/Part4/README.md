## 第4章 返回结果的HTTP状态码



1.状态码的类别
- 1xx Informational(信息性状态码) 接收的请求正在处理
- 2xx Success(成功状态码) 请求正常处理完毕
- 3xx Redirection(重定向状态码) 需要进行附加操作以完成请求
- 4xx Client Error(客户端错误状态码) 服务器无法处理请求
- 5xx Server Error(服务器错误状态码) 服务器处理请求出错

---

2.2xx 成功
- 200 OK - 请求正常处理
- 204 No Content - 请求已成功处理，返回的响应报文不含实体的主体部分
- 206 Partial Content - 进行范围请求

---
 
 3.3xx 重定向
- 301 Moved Permanently - 永久性重定向
- 302 Found - 临时性重定向
- 303 See Other - 请求的资源存在另一个URI，应使用GET方法定向获取请求资源
 
 
 当301，302，303响应状态码返回时，几乎所有的浏览器都会把POST改成GET，并删除请求报文内的主体，之后请求会再次发送。
 
 
- 304 Not Modified - 发送附带条件的请求时，服务器允许请求访问资源，但未满足条件的情况。
- 307 Temporary Redirect - 临时重定向，尽管302标准禁止POST变换成GET，但实际使用时大家并不遵守。307会遵照浏览器标准，不会从POST变成GET。但是，对于处理响应时的行为，每种浏览器有可能出现不同的情况。

---
 
 4.4xx 客户端错误
- 400 Bad Request - 请求报文中存在语法错误
- 401 Unauthorized - 发送的请求需要有通过HTTP认证(BASIC认证、DIGEST认证)的认证信息。另外若之前已进行过1次请求，则表示用户认证失败。返回含有401的响应必须包含一个适用于被请求资源的WWW-Authenticate首部用以质询(challenge)用户信息。当浏览器初次接收到401响应，会弹出认证用的对话窗口。
- 403 Forbidden - 请求资源的访问被服务器拒绝了。
- 404 Not Found - 服务器上无法找到请求的资源。

---
 
 5.5xx 服务器错误
- 500 Internal Server Error - 服务器在执行请求时发生了错误
- 503 Service Unavailable - 服务器暂处于超负载或正在进行停机维护，现在无法处理请求
