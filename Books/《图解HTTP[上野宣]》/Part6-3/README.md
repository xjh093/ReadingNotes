17.表示是否能缓存的指令 

- public指令:其他用户也可以利用缓存。 

  `Cache-Control:public`

- private指令:以特定的用户作为对象。 

  `Cache-Control:private`

- no-cache指令:防止从缓存中返回过期的资源。 
  
  `Cache-Control:no-cache`

---

18.控制可执行缓存的对象的指令 
- no-store指令:暗示请求(和对应的响应)或响应中包含机密信息。 

  `Cache-Control:no-store`

---

19.指定缓存期限和认证的指令 
- s-maxage指令:只适用于供多位用户使用的公共缓存服务器。直接忽略对Expires首部字段及max-age指令的处理。

  `Cache-Control:s-maxage=604800`

- max-age指令:缓存资源的缓存时间数值比指定时间的数值小，客户端就接收缓存的资源。当指定max-age值为0,那么缓存服务器通常需要将请求转发给源服务器。

  `Cache-Control:max-age=604800`

- min-fresh指令:要求缓存服务器返回至少还未过指定时间的缓存资源。 

  `Cache-Control:min-fresh=60`

- max-stale指令:即使过期也照常接收缓存资源。 

  `Cache-Control:max-stale=3600`

- only-if-cached指令:客户端仅在缓存服务器本地缓存目标资源的情况下才会要求其返回。 

  `Cache-Control:only-if-cached`

- must-revalidate指令:代理会向源服务器再次验证即将返回的响应缓存目前是否仍然有效。会忽略请求的max-stale指令。 

  `Cache-Control:must-revalidate`

- proxy-revalidate指令:要求缓存服务器必须再次验证缓存的有效性。 

  `Cache-Control:proxy-revalidate`

- no-transform指令:无论是在请求还是响应中，缓存都不能改变实体主体的媒体类型。可防止缓存或代理压缩图片等。 

  `Cache-Control:no-transform`

---

20.Cache-Control扩展,cache-extension token 

  `Cache-Control:private,community=”UCI”`

通过cache-extension标记(token)，可以扩展Cache-Control首部字段内的指令

---

21.Connection首部字段具备两个作用： 

控制不再转发给代理的首部字段 

管理持久连接

---

22.控制不再转发给代理的首部字段 
```
GET / HTTP/1.1 
Upgrade: HTTP/1.1 
Connection: Upgrade
```

Connection:不再转发的首部字段名

在客户端发送请求和服务器返回响应内，使用Connection首部字段，可控制不再转发给代理的首部字段(即Hop-by-hop首部)。

---

23.管理持久连接 
- Connection:close

HTTP/1.1版本的默认连接都是持久连接。客户端会在持久连接上连续发送请求。 

当服务器想明确断开连接时，则指定Connection首部字段的值为Close。

2017.3.22 20:40 ~ 2017.3.22 21:16
