50.响应首部字段-Accept-Ranges 

`Accept-Ranges: bytes `

告知客户端服务器是否能处理范围请求，以指定获取服务器端某个部分的资源 

可指定的字段值有两种：可处理范围请求时指定其为bytes,反之为none

---

51.响应首部字段-Age 

`Age: 600 `

告知客户端，源服务器在多久前创建了响应。字段值的单位为秒。 

若是缓存服务器，Age值是指缓存的的响应再次发起认证到认证完成的时间值。代理创建响应时必须加上首部字段Age。

---

52.响应首部字段-ETag 

告知客户端实体标识。它是一种可将资源以字符串形式做唯一性标识的方式。服务器会为每份资源分配对应的ETag值。 

资源更新时，ETag值也需要更新。生成ETag值时，没有统一的算法规则，仅仅是由服务器来分配。

强ETag值：不论实体发生多么细微的变化都会改变其值 

`ETag: “usagi-1234” `

弱ETag值：只有资源发生了根本改变，产生差异时才会改变ETag值。这时，会在字段值最开始处附加W/ 

`Etag: W/”usagi-1234”`

---

53.响应首部字段-Location 

`Location: http://www.usagidesign.jp.sample.html `

将响应接收方引导至某个与请求URI位置不同的资源 

基本上，该字段会配合3xx:Redirection的响应，提供重定向的URI

---

54.响应首部字段-Proxy-Authenticate 

`Proxy-Authenticate: Basic realm=”Usagidesign Auth” `

把由代理服务器所要求的认证信息发送给客户端

---

55.响应首部字段-Retry-After 

`Retry-After: 120 `

告知客户端应该在多久之后再次发送请求。 

主要配合状态码503 Service Unavailable响应，或3xx Redirect响应一起使用。 

字段值可以指定为具体的日期时间(Wed,04 Jul 2012 06:34:24 GMT等格式)， 

也可以是创建响应后的秒数

---

56.响应首部字段-Server 

`Server： Apache、2.2.17 (Unix) `

告知客户端当前服务器上安装的HTTP服务器应用程序的信息。

---

57.响应首部字段-Vary 

`Vary: Accept-Language `

可对缓存进行控制。 

代理服务器收到带有Vary首部字段指定获取资源的请求时，如果使用的Accept-Language字段的值相同，直接从缓存返回响应。反之，需要先从源服务器端获取资源后才能作为响应返回。 

从代理服务器接收到源服务器返回包含Vary指定项的响应之后，若再要进行缓存，仅对请求中含有相同Vary指定首部字段的请求返回缓存。

---

58.响应首部字段-WWW-Authenticate 

`WWW-Authenticate: Basic realm=”Usagidesign Auth” `

用于HTTP访问认证。告知客户端适用于访问请求URI所指定资源的认证方案(Basic或是Digest)和带参数提示的质询(challenge)。状态码401 Unauthorized响应中，肯定带有首部字段WWW-Authenticate

2017.5.13 09:23 ~ 2017.5.13 09:56

