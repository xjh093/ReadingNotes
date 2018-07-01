## 第六章 简单数据结构——数组



1.数组是若干同类型变量的聚合，允许通过统一的名字引用其中的变量。

---

2.在C语言中数组由连续的内存区域构成，最低地址对应首元素。

---

3.数组下标从0开始。

---

4.数组可以是一维的，也可以是多维的。

---

5.一维数组的定义格式：

- 类型说明符  数组名[整常量表达式];

---


6.一维数组初始化的一般格式：

- 类型符  数组名[表达式] = {初值表};


---

7.二维数组的定义格式：

- 类型说明符  数组名[整常量表达式1][整常量表达式2];


---

8.C语言中没有专门的字符串变量，如果要将一个字符串放在变量中，必须使用字符数组。


---

9.用字符串初始化一维字符数组时，可以省略花括号{}

char s2[10]="mouse";和

char s2[10]={"mouse"};都是正确的


输出字符串：

printf("%S",s2);


---

10.gets函数——读取字符串

char str[10];

gets(str);

---


11.puts函数——输出字符串

char str[]={"Hello"};

puts(str);


---

12.strcmp()函数——比较字符串

字符按照ASCII值比较大小。

小于返回-1，等于返回0，大于返回1.


---

13.srtcpy()函数——复制字符串

char str1[10],str2[]={"Hello"};

strcpy(str1,str2);//复制str2到str1

puts(str1);

---


14.strlen()函数——获得字符串长度


---

15.strcat()函数——连接字符串

char str1[10] = {"Hello"};

char str2[10] = {"World"};

strcat(str1,str2);


---

16.strchr()函数——在字符串中查找字符

char str[20]="HelloWorld";

char *p;

p = strchr(str,'W');

puts(p);

输出结果为：

World


---

17.strstr()函数——在字符串中查找字符串

char str1[20]="HelloWorld";

char str2[20]="World";

char *p;

p = strstr(str1,str2);//在str1中查找str2的位置

puts(p);

输出结果为：

World


---

18.strlwr()函数——将字符串中大写转成小写

char str[10] = "HEllo";

char *p = strlwr(str);

puts(p);

输出结果为：

hello

---


19.strupr()函数——将字符串中小写转成大写
