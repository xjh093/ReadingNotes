11.End-to-end首部(端到端首部) 

分在此类别中的首部会转发给请求/响应对应的最终接收目标，且必须保存在由缓存生成的响应中，另外规定它必须被转发。

---

12.Hop-by-hop首部(逐跳首部) 

分在此类别中的首部只对单次转发有效，会因通过缓存或代理而不再转发。


除了8个首部字段之外，其他都属于端到端首部 

- Connection,
- Keep-Alive,
- Proxy-Authenticate,
- Proxy-Authorization, 
- Trailer,
- TE,
- Trannsfer-Encoding,
- Upgrade

---

13.通用首部字段：请求与响应报文都会使用的首部。

---

14.Cache-Control: 

通过指定首部字段Cache-Control的指令，就能操作缓存的工作机制。


多个指令通过“,”分隔： 

- Cache-Control:private,max-age=0,no-cache

---

15.缓存请求指令 

指令 - 参数 - 说明 
- no-cache - 无 - 强制向源服务器再次验证 
- no-store - 无 - 不缓存请求或响应的任何内容 
- max-age = [秒] - 必需 - 响应的最大Age值 
- max-stale (=[秒]) - 可省略 - 接收已过期的响应 
- min-fresh = [秒] - 必需 - 期望在指定时间内的响应仍有效 
- no-transform - 无 - 代理不可更改媒体类型 
- onlu-if-cached - 无 - 从缓存获取资源 
- cache-extension - - - 新指令标记(token)

---

16.缓存响应指令 

指令 - 参数 - 说明 
- public - 无 - 可向任意方提供响应的缓存 
- private - 可省略 - 仅向特定用户返回响应 
- no-cache - 可省略 - 缓存前必须先确认其有效性 
- no-store - 无 - 不缓存请求或响应的任何内容 
- no-transform - 无 - 代理不可更改媒体类型 
- must-revalidate - 无 - 可缓存但必须再向源服务器进行确认 
- proxy-revalidate - 无 - 要求中间缓存服务器对缓存的响应有效性再进行确认 
- max-age = [秒] - 必需 - 响应的最大Age值 
- s-maxage = [秒] - 必需 - 公共缓存服务器响应的最大Age值 
- cache-extension - - - 新指令标记(token)

2017.3.21 20:50 ~ 2017.3.21 21:21
