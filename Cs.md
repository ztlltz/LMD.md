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
## _enum_ 枚举类型
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

</br></br></br></br>

## 数组

Cs中数组这一块和C与C++有着 **较大不同**

数组的声明和内存分配被分开了，也就是，现在需要我们来为数组名来手动开辟内存
```c#
int[] arrray1 = new int[len];//一维数组

int[,] array2 = new int[len,wid]//二维数组

```
实际上这样来看，这里的数组和指针就比较像，实际上也正是如此，在Cs中数组以 **引用** 的方式工作

通过成员变量Length可以获知一维数组长度  

对于多维数组，需使用GetLength（维度）方法
```c#
array1.Length;

array2.GetLength(0);//一维长度
array2.GetLength(1);//二维长度
```

### 元素调用
Cs的数组的下标是 **从0开始的** ，注意不要越界
```
int[] arrray1 = new int[5];

int[,] array2 = new int[5,5];

array[2];

array[2,2];
```
## _结构体_
Cs里的结构体和C++的结构体完全一样
```c#
struct name {

    变量;
    函数;
    结构体;//不能是name

}
```



# 函数
```c#
static int Fun(int a,int b){
//语句
return value;
}
```
>  在CS中所有函数都要使用 **_帕斯卡命名法_** &nbsp;,即首字母必须大写

使用 **ref** 和 **out** 关键字可以把函数的形参改成实参
```
static void Fun( ref int a,int b){
a=1;
return;
}
int a,b;
a=0;
b=0;
Fun(ref a,b);//a的值会变成1
```
out的写法和效果如ref完全一致，但两者对于变量有不同的要求

* ref要求变量在作为参数前必须赋过值
* out要求在函数中变量在使用前必须重新赋初值

out的要求大伙可能不太理解，举个错误的例子
```
static void Fun( out int a,int b){
b=a;
a=b+1;
return;
}
```
这个函数错在a未重新赋值就调用了a的值，因此我们也可以认为，如果使用了out关键字，那么变量会在进入函数时被清空
# 类和对象
## 类
类是面向对象的核心，在面向对象中，我们抽象出要操作事物的某些特征，并封装成类，以减少代码量，有利于理清逻辑关系

```c#
class 类名{
//变量，方法
}
```
## 对象
对象是类的实例化，也就是可以被操作的类。注意，对象是引用类型的变量

```c#
class 类名{
//变量，方法
}

类名 对象名 = new 类名（）;//可以有参可以无参，看类的定义
```
## 修饰符
3p修饰符
*  private &nbsp; &nbsp; &nbsp;如果不加修饰符，默认是private,只能由该类自己内部调用
* public &nbsp; &nbsp; &nbsp; 使用该修饰符的变量可以被任何人调用
* proteced &nbsp; &nbsp; &nbsp; 使用该修饰符的变量只能被该类和其子类调用
```c#
class 类名{
    public int  a;
}

```
## 构造函数
构造函数就是类在实例化时调用的初始化函数
```c#
class 类名{
    public int  a;
    类名（）{
    //无参构造
}
     类名（int a,int b）{
    //有参构造
}
//一旦自己定义了构造函数，那么默认的无参构造就会失效

//还可以这样
    类名（int a,int b）:this()//会先调用这个构造函数，再调用本构造函数
    {
    //有参构造
}

}

```
## 析构函数
析构函数就是对象被删除的时候执行的函数,因为Cs有垃圾回收机制，所以析构函数基本没用
```c#
~类名{
//语句
}
```
### 垃圾回收
Cs会将分配在堆里面的无用内存回收掉
| 第0代 |
| :---: |
| 第1代 |
| 第2代 |

每次内存都会被分配在第0代，当第n代满了后，0-n代的内存都会查询有无没有人使用的内存，有就腾出位置，并把正在使用的内存向下移一代（第二代不移动）

这个过程是c#自动进行的，如果你想让他在未满时就回收垃圾，可以调用 ` GC.Collect() `方法
## 属性
属性用来解决 **3p** 修饰符不能解决的问题，比如获得和修改private的值等等
```c#
class 类名{
    private int a;

    public 数据类型 名字{

    get{
// 语句
        return 值;
    }

    set{
    //语句，其中可以使用一种叫value的关键字，他的值等于传入的值
    }
}
```
>get和set的访问修饰符默认为外面的，如果要自定义，则该访问修饰符不能高于外面的修饰符

### 自动属性
```c#
public 数据类型 名字{
    get;
`   set;
}
```
* 会隐藏具体的变量，反而用 **名字** 来间接访问
* 不能进行其他的处理了
___
调用属性的例子
```c#
取得值:
    对象名.名字;

修改值
    对象名.名字 = value ;
```
### 索引器
和属性的功能类似，索引器根据参数来获得和修改数组中的值
```c#
 public int this[int index]
        {

            get
            {
                return b[index];
            }

            set
            {
                b[index] = value + b[index];
            }
        }
```
看起来比较像函数，调用同属性，用 **对象名[index]** 调用
# static修饰词
```c#
static public a;// 3p 和 static 的先后无影响

static public name（）{

}
```
* static关键字用于产生静态的变量和方法
* 一旦使用了static关键字，那么该变量和方法就会在程序开始时分配内存，生命周期为整个程序
* 此时，可以直接使用 **类名.变量** &nbsp;或者 **类名.方法()** &nbsp;来调用变量和方法
* 注意，静态的方法 **不能使用** 非静态的变量
* 静态的变量 **不需要** 在定义时赋初值
## 静态类
```c#
static class 类名{
    //静态变量和静态方法
}
```
静态类不能实例化，适用于写一些工具类，比如Cs自带的Console类
### 静态构造函数
* 静态构造函数既可以在静态类中使用，也可以在普通类中使用
* 在 **第一次** 使用类的方法和变量或者或者实例化类时自动调用，且先于该行为
* 一般用静态类来对变量进行一些 **初始化**
* 静态构造函数不能有参数
  ```c#
  class 类名{

  static 类名(){
  
        
  }

  }
  ```
  注意，静态构造函数 **不是** 无参构造函数的重载
# 拓展方法
使用拓展方法，可以为 **非静态** 的类添加新的方法
* 拓展方法只能为 **非静态类** 添加方法
* 拓展方法必须定义在 **静态类** 中,且是一个静态的方法

#### 定义：
```c#
 static public 返回值 方法名(this 类 value,参数类型 参数名，参数类型 参数名 ...) { 
            //语句
        }
```
* 类指的是为哪个类拓展方法
* value指代的是实例化的对象
#### 以下是一个为int类添加Print方法的例子
```c#
  static class Tool {
        static public void Print(this int value) { 
            Console.WriteLine(value);
        }
}

int a ;
a.Print();
```
### 如果拓展方法和原方法重名，则会调用原方法
# 运算符重载
如果想让类和结构体也可以进行运算符操作，可以使用运算符重载
```c#
public static 返回值 operator +(类名 参数名....){

    //语句

}
```
#### 特点
* 必须是public 和 static 的方法
* 返回值写在operator前
* 不能使用ref 和out 关键字
* 条件运算符的重载必须成对出现
  
