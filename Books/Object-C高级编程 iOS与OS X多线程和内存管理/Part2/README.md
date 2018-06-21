## 第2章 Blocks



1.Blocks是C语言的扩充功能(带有自动变量(局部变量)的匿名函数)。

---

2.Block实质是Object-C的对象。

---

3.Block的类

类 ---
设置对象的存储域 --- 复制效果

_NSConcreteStackBlock --- 栈 --- 从栈复制到堆

_NSConcreteGlobalBlock --- 程序的数据区域(.data区) --- 什么也不做

_NSConcreteMallocBlock --- 堆 --- 引用计数增加



---

## 第3章 Grand Central Dispatch



1.Grand Central Dispatch(GCD)是异步执行任务的技术之一。

---

2.Dispatch Queue 的种类

- Serial Dispatch Queue - 等待现在执行中处理结束

- Concurrent Dispatch Queue - 不等待现在执行中处理结束

---

3.Global Dispatch Queue 有4个优先级：

- 高优先级 - dispatch_get_global_queue(DISPATCH_QUEUE_PRIORITY_HIGH,0); 

- 默认优先级 - dispatch_get_global_queue(DISPATCH_QUEUE_PRIORITY_DEFAULT,0);

- 低优先级 - dispatch_get_global_queue(DISPATCH_QUEUE_PRIORITY_LOW,0);

- 后台优先级 - dispatch_get_global_queue(DISPATCH_QUEUE_PRIORITY_BACKGROUND,0);
