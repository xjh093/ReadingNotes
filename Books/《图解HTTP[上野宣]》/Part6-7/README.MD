 59.实体首部字段

 包含在请求报文和响应报文中的实体部分所使用的首部，用于补充内容的更新时间等与实体相关的信息。

---

 60.实体首部字段-Allow

 Allow:GET, HEAD


 通知客户端能支持Request-URI指定资源的所有HTTP方法。

 服务器收到不支持的HTTP方法时，会以状态码405 Method Not Allowed作为响应返回。

 同时，会把所有能支持的HTTP方法写入首部字段Allow后返回。

---

 61.实体首部字段-Content-Encoding

 Content-Encoding:gzip

 

 告知客户端服务器对实体的主体部分选用的内容编码方式。

 内容编码是指在不丢失实体信息的前提下所进行的压缩。

 

 4种内容编码方式：gzip,compress,deflate,identity

---

 62.实体首部字段-Content-Language

 Content-Language:zh-CN

 

 告知客户端，实体主体使用的自然语言。

---

 63.实体首部字段-Content-Length

 Content-Length:15000

 

 表明了实体主体部分的大小(单位是字节)。

 对实体主体进行内容编码传输时，不能再使用Content-Length首部字段。

---

 64.实体首部字段-Content-Location

 Content-Location:http://www.hackr.jp/index-ja.html

 

 给出与报文主体部分相对应的URI。

 和首部字段Location不同，它表示的是报文主体返回资源对应的URI。

---

 65.实体首部字段-Content-MD5

 Content-MD5:OGFKZDUwNGVhNGY3N2MxMDIwZQ4NTBmY2IyTY==

 

 一串由MD5算法生成的值，为了检查报文主体在传输过程中是否保持完整，以及确认传输到达。

 对报文主体执行MD5算法获得的128位二进制数，再通过Base64编码后将结果写入Content-MD5字段值。

 由于HTTP首部无法记录二进制值，所以要通过Base64编码处理。

---

 66.实体首部字段-Content-Range

 Content-Range:bytes 5001-10000/10000

 

 针对请求范围。单位字节，表示当前发送部分及整个实体大小。

---

 67.实体首部字段-Content-Type

 Content-Type:text/html;charset=UTF-8

 

 说明实体主体内对象的媒体类型。

---

 68.实体首部字段-Expires

 Expires:Wed,04 Jul 2012 08:26:05 GMT

 

 将资源失效的日期告知客户端。

 

 当首部字段Cache-Control有指定max-age指令时，比起首部字段Expires,会优先处理max-age指令。

---

 69.实体首部字段-Last-Modified

 Last-Modified:Wed,23 May 2012 09:59:55 GMT

 

 指明资源最终修改的时间。

 

 2017.6.20 20:10:08~2017.6.20 20:41:08
