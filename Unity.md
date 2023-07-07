# 图片处理
<img width="355" alt="image" src="https://github.com/ztlltz/LMD.md/assets/104620738/6755186e-224f-4280-b68c-9a931b9f7603">  </br>
### 将图片的texture type 换成sprite格式以使用

# 不同文件协作
### unity的运作方式，大体上是运行场景中的所有脚本文件，最低保证每秒60次
### 代码要依附于物体
### 对于一些框架上的函数和变量，可以将它们写在一些没有任何操作的物体上，例如创建一个空物体（实际上相机也是一个选择）
<img width="591" alt="image" src="https://github.com/ztlltz/LMD.md/assets/104620738/1767d85f-c00f-4d4e-8df1-ef0dcdc25c77">
<img width="598" alt="image" src="https://github.com/ztlltz/LMD.md/assets/104620738/35b3f7db-812d-4558-a132-65fa5a2c8f9d">

___

> #### 如果想用脚本文件控制一个物体，可以在脚本中直接定义一个名为 GameObject的对象然后直接在unity中用拖拽的方式为变量赋值

<img width="568" alt="image" src="https://github.com/ztlltz/LMD.md/assets/104620738/38643741-76ab-466d-8dfe-5ebf0f95a640">

# input类
input类可以用来检测鼠标和键盘的输入

## 键盘
#### GetKey() &nbsp;and &nbsp;GetKeyDown()&GetKeyUp()
前面的会持续检测，后面的一次输入只算一次

他的参数是键盘上你希望输入的值，使用KeyCode和点号来构成

```c#
  input.Getkey(KeyCode.A)
```
当检测到对应输入时返回True
<img width="556" alt="image" src="https://github.com/ztlltz/LMD.md/assets/104620738/7b8fad81-abf9-4e8d-8bc5-98c350add540">

## 鼠标
#### GetMouseButton() &nbsp;and &nbsp;GetMouseButtonDown()&GetMouseButtonUp()
参数为0，1，2

分别代表左键，右键和中键.
#### 获得鼠标位置
直接调用成员变量 ```Input.mousePosition```
