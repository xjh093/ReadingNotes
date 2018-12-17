70.为Cookie服务的首部字段

Cookie的工作机制是用户识别及状态管理。

---

71.至2013年5月，Cookie的规格标准文档有以下4种

- 由网景公司颁布的规格标准

- RFC2109

- RFC2965

- RFC6265

---

72.为Cookie服务的首部字段

Set-Cookie:开始状态管理所使用的Cookie信息-(响应首部字段)

Cookie:服务器接收到的Cookie信息-(请求首部字段)

---

73.Set-Cookie字段的属性

NAME=VALUE:赋予Cookie的名称和其值（必需项）

expires=DATE:Cookie的有效期（若不明确指定则默认为浏览器关闭前为止）

path=PATH:将服务器上的文件目录作为Cookie的适用对象（若不指定则默认为文档所在的文件目录）

domain=域名:作为Cookie适用对象的域名（若不指定则默认为创建Cookie的服务器的域名）

Secure:仅在HTTPS安全通信时才会发送Cookie

HttpOnly:加以限制，使Cookie不能被JavaScript脚本访问

---

73.expires属性

指定浏览器可发送Cookie的有效期

当省略时，有效期仅限于维持浏览器会话（Session）时间段内。

通过覆盖已过期的Cookie，实现对客户端Cookie的实质性删除操作。

---

74.path属性

用于限制指定Cookie的发送范围的文件目录。

---

75.domain属性

通过Cookie的domain属性指定的域名可做到与结尾匹配一致。

比如，当指定example.com后，除example.com以外，

www.example.com或www2.example.com等都可以发送Cookie

因此，除了针对具体指定的多个域名发送Cookie外，不指定domain属性显得更安全。

---

76.secure属性

限制Web页面仅在HTTPS安全连接时，才可以发送Cookie

发送Cookie时，指定secure属性的方法如下：

Set-Cookie:name=value;secure

---

77.HttpOnly属性

防止跨站脚本攻击（Cross-site scripting,XSS）对Cookie的信息窃取

Set-Cookie:name=value;HttpOnly

---

78.Cookie

Cookie: status=enable

会告知服务器，当客户端想获得HTTP状态管理支持时，就会在请求中包含从服务器接收到的Cookie。接收到多个Cookie时，同样可以以多个Cookie形式发送。

---

79.其他首部字段

HTTP首部字段是可以自行扩展的



常用的：

X-Frame-Options

X-XSS-Protection

DNT

P3P

---

80.X-Frame-Options

X-Frame-Options: DENY



属于响应首部，用于控制网站内容在其他Web网站的Frame标签内的显示问题。

主要目地是为了防止点击支持（clickjacking）攻击



可指定的字段值：

DENY:拒绝

SAMEORIGIN:仅同源域名下的页面(Top-level-browsing-context)匹配时许可

---

81.X-XSS-Protection

X-XSS-Protection: 1



属于响应首部，针对跨站脚本攻击(XSS)的一种对策

用于控制浏览器XSS防护机制的开关



可指定的字段值：

0:将XSS过滤设置成无效状态

1:将XSS过滤设置成有效状态

--- 

82.DNT-Do Not Track

DNT: 1



属于请求首部，拒绝个人信息被收集

是表示拒绝精准广告追踪的一种方法



可指定的字段值：

0:同意被追踪

1:拒绝被追踪

---

83.P3P

P3P: CP="CAO DSP LAW CURa ADMa DEVa TAIa PSAa PSDa IVAa IVDa OUR BUS IND UNI COM NAV INT"



属于响应首部，通过利用P3P（The Platform for Privacy Preferences,在线隐私偏好平台）技术，可以主Web网站上的个人隐私变成一种仅供程序可以理解的形式，以达到保护用户隐私的目的。



设定步骤：

- 创建P3P隐私

- 创建P3P隐私对照文件后，保存命名在/w3c/p3p.xml

- 从P3P隐私中新建Compact policies后，输出到HTTP响应中




2017.8.23 15:52:22~2017.8.23 16:32:41
