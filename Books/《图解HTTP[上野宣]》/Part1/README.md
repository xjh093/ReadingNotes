## 第1章 了解Web及网络基础


 1.TCP/IP协议族按层次分为4层：
 - 应用层
 - 传输层
 - 网络层
 - 数据链路层
 
 ---
 
 2.应用层
 决定了向用户提供应用服务时通信的活动。
 
 FTP(File Transfer Protocol,文件传输协议)
 
 DNS(Domain Name System,域名系统)
 
 是其中的两种应用服务。
 
 HTTP协议也处于该层。
 
  
 ---
 
 
 3.传输层
 对上层应用层提供处于网络连接中的两台计算机之间的数据传输。
 
 两个协议：
 - TCP(Transmission Control Protocol,传输控制协议)
 - UDP(User Data Protocol,用户数据协议)
  
 ---
 
 4.网络层(网络互连层)
 
 用来处理在网络上流动的数据包。
 
 数据包是网络传输的最小数据单位。
 
 规定了通过怎样的路径(传输路线)到达目标计算机，并把数据包传送给对方。
  
 ---
 
 5.链路层(数据链路层，网络接口层)
 
 用来处理网络的硬件部分。
 
 包括控制操作系统、硬件的设备驱动、NIC(Network Interface Card,网络适配器,即网卡),以及光纤等物理可见部分(还包括连接器等一切传输媒介).
 
 配件上的范畴均在链路层的作用范围之内。
  
 ---
 
 6.TCP/IP通信传输流
 
 客户端：应用层(HTTP客户端)<->传输层(TCP)<->网络层(IP)<->链路层(网络)<->链路层(网络)<->网络层(IP)<->传输层(TCP)<->应用层(HTTP服务器)：服务器
  
 ---
 
 7.发送端，每通过一层则增加首部；接收端，每通过一层则删除首部。
 
 应用层 - HTTP数据
 
  |
  
 传输层 - TCP首部(HTTP数据)
 
  |
  
 网络层 - IP首部(TCP首部(HTTP数据))
 
  |
  
 链路层 - 以太网首部(IP首部(TCP首部(HTTP数据)))
  
 ---
 
 8.与HTTP关系密切的协议：
 - IP
 - TCP
 - DNS
  
 ---
 
 9.IP(Internet Protocol)网际协议位于网络层。
 
 几乎所有使用网络的系统都会用到IP协议。
  
 ---
 
 10.IP协议的作用是把各种数据包传送给对方。
 
 而要保证确实传送到对方的两个重要条件是IP地址和MAC地址(Media Access Control Address).
  
 ---
 
 11.IP地址指明了节点被分配到的地址，MAC地址是指网卡所属的固定地址。
 
 IP地址可以和MAC地址进行配对。IP地址可变换，但MAC地址基本上是会更改。
  
 ---
 
 12.ARP(Address Resolution Protocol)是一种用以解析地址的协议，根据通信方的IP地址就可以反查出对应的MAC地址。
  
 ---
 
 13.TCP位于传输层，提供可靠的字节流服务。
  
 ---
 
 14.字节流服务是为了方便传输，将大块数据分割成以报文段(segment)为单位的数据包进行管理。
  
 ---
 
 15.TCP协议为了更容易传送大数据才把数据分割，而且TCP协议能够确认数据最终是否送达到对方。
  
 ---
 
 16.为了准确无误地将数据送达目标处，TCP协议采用三次握手(three-way handshaking)策略。
 
 用TCP协议把数据包送出去后，TCP会向对方确认是否成功送达。
 
 握手过程中使用了TCP标志(flag)——SYN(synchronize)和ACK(acknowledgement)。
  
 ---
 
 17.三次握手
 - 发送端首先发送一个带SYN标志的数据包给对方，
 - 接收端回传一个带有SYN/ACK标志的数据包以示确认，
 - 发送端再发送一个带ACK标志的数据包。
  
 ---
 
 18.DNS协议提供通过域名查找IP地址，或逆向从IP地址反查域名的服务。
  
 ---
 
 19.URI(Uniform Resource Identifier)统一资源标识符。
 
 RFC2396定义：
 
 - Uniform:规定统一的格式可方便处理多种不同类型的资源，而不用根据上下文环境来识别资源指定的访问方式。另外，加入新增的协议方案(如：http:或ftp:)也更容易。
 
 - Resource:可标识的任何东西。除了文档文件、图像或服务(例如当天的天气预报)等能够区别于其他类型的，全都可作为资源。另外，资源不仅可以是单一的，也可以是多数的集合体。
 
 - Identifier:表示可标识的对象。也称为标识符。
 
 综上所述，URI就是由某个协议方案表示的资源的定位标识符。协议方案是指访问资源所使用的协议类型名称。
  
 ---
 
 20.采用HTTP协议时，协议方案就是http。
 
 除此之外，还有ftp,mailto,telnet,file等。
  
 ---
 
 21.标准的URI协议方案有30多种左右，同隶属国际互联网资源管理的非营利社团ICANN的IANAA管理颁。
  
 ---
 
 22.URI用字符串标识某一互联网资源，而URL表示资源的地点。可见，URL是URI的子集。
  
 ---
 
 23.URI例子：
 - ftp://ftp.is.co.za/rfc/rfc1808.txt
 - http://www.ietf.org/rfc/rfc2396.txt
 - ldap://[2001:db8::7]/c=GB?objectClass?one
 - mailto:John.Doe@example.com
 - news:comp.infosystems.www.servers.unix
 - tel:+1-816-555-1212
 - telnet://192.0.2.16:80/
 - urn:oais:names:specification:docbook:dtd:xml:4.1.2
