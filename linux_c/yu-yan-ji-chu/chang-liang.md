# 常量

#### 总结

```
不能改变的量
在程序中定义常量，通常用#define预处理指令，常量名字习惯全部大写
```

常量是固定值 , 在程序执行期间不会改变 . 这些固定的值 , 又叫做**字面量** . 常量可以是任何的基本数据类型 , 比如整数常量、浮点常量、字符常量 , 或字符串字面值 , 也有枚举常量 .

**常量**就像是常规的变量 , 只不过常量的值在定义后不能进行修改 . 常量\(Constant\)是程序中最基本的元素 .

#### 整数常量

整数常量可以是十进制、八进制或十六进制的常量 . 前缀指定基数 : 0x或0X表示十六进制 , 0表示八进制 , 不带前缀则默认表示十进制 . 整数常量也可以带一个后缀 , 后缀是 U 和 L 的组合 , U 表示无符号整数\(unsigned\) , L 表示长整数\(long\) . 后缀可以是大写 , 也可以是小写 , U 和 L 的顺序任意 .

一些例子 :

```
85         /* 十进制 */
0213       /* 八进制 */
0x4b       /* 十六进制 */
30         /* 整数 */
30u        /* 无符号整数 */
30l        /* 长整数 */
30ul       /* 无符号长整数 */
```

#### 浮点常量

浮点常量由整数部分、小数点、小数部分和指数部分组成 . 可以使用小数形式或者指数形式来表示浮点常量 . 当使用小数形式表示时  , 必须包含整数部分、小数部分 , 或同时包含两者 . 当使用指数形式表示时 , 必须包含小数点、指数 , 或同时包含两者 . 带符号的指数是用 e 或 E 引入的 .

```
3.14159       /* 合法的 */
314159E-5L    /* 合法的 */
```

#### 字符常量

字符常量是括在单引号中 , 例如 , 'x' 可以存储在**char**类型的简单变量中 . 字符常量可以是一个普通的字符\(例如 'x'\)、一个转义序列\(例如 '\t'\) , 或一个通用的字符\(例如 '\u02C0'\) .

#### 字符串常量

字符串字面值或常量是括在双引号 "" 中的 . 一个字符串包含类似于字符常量的字符 : 普通的字符、转义序列和通用的字符 . 可以使用空格做分隔符 , 把一个很长的字符串常量进行分行 . 下面的实例显示了一些字符串常量 . 下面这三种形式所显示的字符串是相同的 :

```
"hello, dear"

"hello, \

dear"

"hello, " "d" "ear"
```

**注意**

有时候不同类型的数据很容易弄混 , 例如"5"、'5'、5 , 第一个是字符串 , 第二个是字符 , 第三个是整数 .

字符常量要用单引号括起来 , 注意单引号只能括一个字符而不能像双引号那样括一串字符 , 字符常量也可以是一个转义序列 , 例如'\n' ,这时虽然单引号括了两个字符 , 但实际上只表示一个字符 . 和字符串字面值中使用转义序列有一点区别 , 如果在字符常量中要表示双引号"和问号? , 既可以使用转义序列\"和\? , 也可以直接用字符"和? , 而要表示'和\则必须使用转义序列 . 为什么需要规定一个转义序列\?呢 ? 因为C语言规定了一些三连符\(Trigraph\) , 在某些特殊的终端上缺少某些字符 , 需要用Trigraph输入 .

**printf**

printf中的字符串称为格式化字符串\(Format String\) , 它规定了后面几个数据以何种格式插入到这个字符串中 , %号\(Percent Sign\)后面加个字母c、d、f在printf中分别解释成字符型、整型和浮点型的转换说明\(Conversion Specification\) , 分别用后面的三个常量来替换它们 , 也就是说它们只是在格式化字符串中占个位置 , 并不出现在最终的打印结果中 , 这种用法通常叫做占位符\(Placeholder\) . 这也是一种字面意思与真实意思不同的情况 , 但是和转义序列又有区别 : 转义序列是编译器在处理字符串字面值时转义的 , 而占位符是由printf解释的 , 格式化字符串实际包含的字符是character:%c换行integer: %d换行floating point: %f换行 , 其中的%c仍然是字符串中的两个普通字符 , 而当字符串传给printf处理时 , printf却不把它当成是普通字符 , 而是解释成占位符 . 事实上前面例子中的"Hello, world.\n"也是格式化字符串 , 只不过其中不包含占位符 .

#### 定义常量

在 C 中，有两种简单的定义常量的方式：

1. 使用**\#define**预处理器
2. 使用**const**关键字

**使用\#define预处理器**

```c
#include <stdio.h>

#define LENGTH 10   
#define WIDTH  5
#define NEWLINE '\n'

int main()
{

   int area;  

   area = LENGTH * WIDTH;
   printf("value of area : %d", area);
   printf("%c", NEWLINE);

   return 0;
}
```

**使用const关键字**

```c
#include <stdio.h>

int main()
{
   const int  LENGTH = 10;
   const int  WIDTH  = 5;
   const char NEWLINE = '\n';
   int area;  

   area = LENGTH * WIDTH;
   printf("value of area : %d", area);
   printf("%c", NEWLINE);

   return 0;
}
```

> \#define是宏定义 , 它不能定义常量 , 但宏定义可以实现在字面意义上和其它定义常量相同的功能 , 本质的区别就在于\#define不为宏名分配内存 .
>
> 而const也不为常量分配内存 , 其实const并不是去定义一个常量 , 而是去改变一个变量的存储类 , 把该变量所占的内存变为只读 .



