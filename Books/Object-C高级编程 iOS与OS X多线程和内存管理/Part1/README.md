# 第1章 自动引用计数

1.自动引用计数（ARC，Automatic Reference Coounting）是指内存管理中对引用采取自动计数的技术。



2.满足以下条件，就无需手工输入retain 和 release 代码了：

-使用Xcode 4.2 或以上版本。

-使用LLVM编译器3.0或以上版本。

-编译器选项中设置ARC为有效。



3.autorelease NSAutorelessePool对象

发发生异常：

*** Terminating app due to uncaught exception 'NSInvalidArgumentException'

reason: '*** -[NSAutoreleasePool autorelease]:

      Connot autorelease an autorelease pool'



调用对象的autorelease实例方法，实现上调用的都是NSObject类的autorelease实例方法。但是对于NSAutoreleasePool类，autorelease实例方法已被该类重载，因此运行时就会出错。



4.ARC有效时，id类型和对象类型同C语言其他类型不同，其类型上必须附加所有权修饰符。

所有权修饰符一共有4种：__strong(默认是这个),__weak,__unsafe_unretained,__autoreleasing



5.__strong,__weak,__autoreleasing，可以将变量初始化为nil



6.循环引用容易发生内存泄漏。

内存泄漏就是应当废弃的对象在超出其生存周期后继续存在。



7.__weak修饰符只能用于iOS5以上及OS X Lion以上版本的应用程序。

在iOS4以及OS X Snow Leopard的应用程序中可使用__unsafe_unretained修饰符来代替。



8.对象作为函数的返回值，编译器会自动将其注册到autoreleasepool



9.init方法返回值的对象不注册到autoreleasepool



10.ARC由以下工具、库来实现：

-clang(LLVM编译器)3.0以上

-objc4 Objective-C运行时库493.9以上



11.释放对象时，废弃谁都不持有的对象的同时，程序的动作是怎样的呢？下面我们来跟踪观察。

对象将通过objc_release函数释放。

(1).objc_release

(2).因为引用计数为0所以执行dealloc

(3)._objc_rotDealloc

(4).object_dispose

(5).objc_destructInstance

(6).objc_clear_deallocating

对象被废弃时最后调用的objc_clear_deallocating函数的动作如下：

(1).从weak表中获取废弃对象的地址为键值的记录

(2).将包含在记录中的所有附有__weak修饰符变量的地址，赋值为nil

(3).从weak表中删除该记录

(4).从引用计数表中删除废弃对象的地址为键值的记录



12.如果大量使用附有__weak修饰符的变量，则会消耗相应的CPU资源。

良策是只有需要避免循环引用时使用__weak修饰符。



13.在使用附有__weak修饰符的变量时，最好先暂赋值给附有__strong修饰符的变量后再使用。



14.在赋值给__weak修饰符的变量时，如果赋值对象的allowsWeakReference方法返回NO，程序将异常终止。

在使用__weak修饰符的变量时，当被赋值对象的retainWeakReference方法返回NO的情况下，该变量将使用nil。



15.获取引用计数数值的函数

uintptr_t _objc_rootRetainCount(id obj)
