第一章 走进C语言



1.计算机语言分为：机器语言，汇编语言，高级语言。


2.早期电脑都直接采用机器语言，即用0和1为指令代码来编写程序，读写困难，编程效率极低。

3.C语言最早可以追溯到ALGOL60。ALGOL60是面向问题的高级语言，产生于20世纪60年代，但是由于自身的局限性，它并不适用于编写系统程序。

4.C语言的优势：

-C语言数据类型丰富，运算符方便。

-语言简洁、紧凑，使用方便、灵活。

-面向结构化程序设计的语言。

-C语言能进行位(bit)操作。

-生成目标代码质量高，程序执行效率高。

-移植性好。


5.程序设计=数据结构 + 算法 (沃思)


6.算法特性：

-有穷性。

-确切性。

-输入。

-输出。

-有效性。


7.常见程序设计的3种基本结构

-顺序结构。

-选择结构。

-循环结构。


8.保证得到结构化程序的方法：

-自顶向下。

-逐步细化。

-模块化设计。

-结构化代码。


9.C程序的结构特点：

-由函数组成。

-函数由函数说明和函数体两个部分组成。

-总是从main()函数开始执行。

-书写格式自由。

-每个语句和数据定义后必须有一个分号。

-C语言本身没有输入输出语句。

-可以用“/*……*/”对C程序中的任何部分做注释。


10.标识符：由字母、数字和下划线组成，并且第一个字母必须是下划线或字母。区分大小写。


11.标识符分类：

-关键字。

-预定义标识符。

-用户标识符。


12.由ANSI标准定义的C语言关键字共32个：

auto  double  int   struct  break  else  long  switch  case  enum  register  typedef  char  extern  return  union  const  float  short  unsigned  continue  for signed  void default  goto  sizeof  volatile  do  if  while  static 


13.关键字分类：

-基本数据类型

void  char  int  float  double

-类型修饰关键字

short  long  signed  unsigned

-复杂类型关键字

struct  union  enum  typedef  sizeof

-存储级别关键字

auto  static  register  extern  const  volatile

-跳转结构

return  continue  break  goto

-分支结构 

if  else  switch  case  default

-循环结构 

for  do   while 


14.C语言编写的源代码经过预编译->编译->汇编->连接几个步骤最终生成可执行文件。


15.算法是对要解决的一个问题或要完成的一项任务所采取的方法和步骤的描述。