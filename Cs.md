# 程序框架
```c#
using System;//引入库

namespace MyCs{//名字随便取但必须首字母大写

    class MyClass{//名字随便取但必须首字母大写
      static void Main（）{
      //内容
      }
    }
}

```
# 变量
>同类按字节数排序
### 整型

##### 有符号数

  * **sbyte** &nbsp;&nbsp;   1  
  * **short** &nbsp;&nbsp;   2  
  * **int** &nbsp;&nbsp; 4  
  * **long** &nbsp;&nbsp; 8  
##### 无符号数

  * **byte** &nbsp;&nbsp;   1  
  * **ushort** &nbsp;&nbsp;   2  
  * **uint** &nbsp;&nbsp; 4  
  * **ulong** &nbsp;&nbsp; 8  
___
### 浮点数
    
  * **float** &nbsp;&nbsp;**4** &nbsp;&nbsp;&nbsp;&nbsp;**7/8位精度**
  * **double** &nbsp;&nbsp;**8**&nbsp;&nbsp;&nbsp;&nbsp;**15/17位精度**
  * **decimal** &nbsp;&nbsp;**12**&nbsp;&nbsp;&nbsp;&nbsp;**27/28位精度**
>赋值时，小数默认为double类型，如果要改为1和3要在结尾加f和m，如 **_0.54968498f_** &nbsp;和&nbsp; **_0.548498489497494m_**
___
### 特殊类型
  * **char** &nbsp;&nbsp; 1
  * **bool** 1
  * **string**  &nbsp;&nbsp;可以使用 **+** 号将任意变量和常量变成字符串  
>注意，bool类型在Cs中用来唯一的表示true和false，也就是说，不能如c语言一样，用0表示false，非0表示true
___
### 求字节长
**sizeof** ： 例如sizeof（int），但不能对string使用
___
### 读入变量
* **Console.Read()** 读一个字符，按回车结束
* **Console.ReadKey()** 读一个字符，直接结束
* **Console.ReadLine()** 读一行  
**可以认为不管读的什么都是字符和字符串**

>要首先用char和string 类型接受，然后用函数转换成其他类型
>
>如 **int test = int.Parse(str);** &ubsp; 或者 **int test=Convert.ToInt32(str);**
``` c#
using System;

namespace Test
{
   class Pro
    {
        static void Main(string[] args)
        {
            int len;
            string s;
            s = Console.ReadLine();
            len = Convert.ToInt32(s);
            Console.WriteLine(len); 
        }
    }
}
```
>**输入123，打印123**
>
>**输入123 123，报错**

为了应对第二种情况，可以使用try-catch语句
try用来接受异常，模板如下  
```
try
{
//我是语句
}
catch
{
//我是语句
}
```
如果接受异常，会执行catch里面的内容，反之只会执行try里面的代码

**因此，可以这样接受一个数字**
```c#
 public static int ReadInt()
        {
            int number = 0;
            do
            {
                try
                {
                    
                    number = System.Int32.Parse(Console.ReadLine());
                    return number;
                }
                catch
                {
                    Console.WriteLine("输入有误，重新输入！");
                }
            }
            while (true);
        }
```
# 字符串拼接
* **用占位符或者+号**
  ```c#
            string s;
            int t;
            t = 99;
            s = "abnsujhndaio";
            Console.WriteLine("{0}{1}",s,t);//  1
            s = s+t;
            Console.WriteLine(s);//  2
  ```
  >1和2等效，都输出abnsujhndaio99
# 流程控制
>同c语言
## if
```c#
if(条件){
//语句
}
else{

}
```
## switch
```
switch(value){
    case v1:
//语句
    case v2:
//语句
    ...
    case v99:
//语句
    default:
//语句

}
```
## while & do while
```
while(条件){
//语句
}

do{
//语句
}while(条件)
```
# 复合数据类型
### _enum_ 枚举类型
```c#
enum name{
a,
b,
c,
...
}
```
按顺序把a,b,c与0，1，2对应，也可以给某个类型直接赋值，以改变枚举位置
```
a,//0
b=5,//5
c,//6
```
如果把变量的类型设定为enum，其本质是一个字符串，但可以通过类似哈希的方式输出键值对
```c#
 enum type { 
        male,
        female,
        others,
        }

        static void Main(string[] args)
        {
            type a;
            int t;
            t = 1；
            a = (type)t;
            Console.WriteLine(a);//打印female
        }
```
>注意，在给enum变量赋值时，要显示的进行类型转换
>
>如果enum中没有值对应的字符串，则该变量的字符串就是他的值

### enum类型进行运算
##### 逻辑运算
只有同名的enum类型才能比较

在比较enum类型的变量时，会比较 **他们对应的值**

同时要注意，如果要把enum和常量比较，可以使用name.a

>enum类型变量不能进行算术运算
