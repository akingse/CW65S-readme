## **\*认识 Python\*** 

Python 的数据类型、变量、运算符、条件判断与循环等基础语法

python 程序的执行方式一般分为两种：交互式命令行执行；程序文件的方式执行

GNOME终端：python3 （Ctrl+C退出）

打印函数：print

‘字符串’; “字符串”; ’’’打印多行’’’

print('Hello World!')

Python 的数据类型有 int(整数)、float(浮点数)、字符串、布尔值、None、列表、元组、字典、集合等。

None 在 Python 中是一个特殊的值，表示“无”，表示 什么都没有。

变量：int,float,char,var

输入函数；A=input('please input a num:'); =>A:’2’;print(A):2

转义符\

```
print('Today\'s weather is good.\n') 
```

索引

string=’hello world’

string[0]第一个字符

string[-1]倒数第一个字符

「插入数据」和「数字格式化」format()

print('你叫{}，今年{}岁了'.format(name,age)); {} 为占位符

保留两位小数 print("{:.2f}".format(3.1415926));

运算符 +-*/； %**//

比较运算符 == != <> <=>=

逻辑运算符 and or not

\------------------------------------------

***\*python关键字\****

流程控制 if

pass 关键字，代码暂时不写，又不报错。

循环控制 for while

已知循环次数：for item in variable:

​	do something

python3 namelist.py

range()  范围函数

 

终端运行

python3

```
for a in range(1,10):

	print(a)
```

两次回车执行

条件循环：while

```
a=0

while a<5: #终端需要依次输入，否则有缩进错误；

​	print(a)

​	a=a+1
```

break和continue

```
a=0

while a<6: 

​	if a==3:

​		continue #跳过3

​	if a==4:

​		break #到4为止

​	print(a)

​	a=a+1
```

---

***\*python3简明教程\**** 

https://www.shiyanlou.com/courses/596

Python 是一个脚本语言，你可以在 Python 解释器中直接写代码或者将代码写到一个文件里，然后执行这个文件（即脚本文件）。

\# 代码风格 # 后跟一个空格，能使用英文建议使用英文。

\# 书写表达式的时候，会在每一个运算符左右都放一个空格，这样使代码更可读

\# 使用 4 个空格来缩进；永远不要混用空格和制表符

\# 在函数之间空一行；在类之间空两行

\# 字典，列表，元组以及参数列表中，在 , 后添加一个空格。对于字典，: 后面也添加一个空格

\# 在赋值运算符和比较运算符周围要有空格（参数列表中除外），但是括号里则不加空格：a = f(1, 2) + g(3, 4)

模块是包含了我们能复用的代码的文件，包含了不同的函数定义，变量。模块文件通常以 .py 为扩展名。Python 本身在默认安装时就带有大量的模块。在使用模块前先导入它。

import math

print(math.e)

***\*关键字和标识符\****

python3/help()/keywords

单行定义多个变量或赋值

数据结构（data structure）是计算机中存储、组织数据的方式。如列表、元组、集合、字典

元组 =(,)

（tuple）,由数个逗号分割的值组成，=右边创建元组，称这为元组封装（tuple packing），=左边我们则做的是元组拆封 （tuple unpacking）。

元组可以执行拆封操作并赋值给多个变量，元组是不可变类型，不能在元组内添加或编辑任何值。

```
a = (1,2,3)

data = ("shiyanlou", "Python")

name, language = data

data[0]
```

***\*列表 =[,]\****

常用函数

> .append(amum) # 添加元素到末尾
>
> .insert(num,anum) # 将数据插入到任意位置
>
> count(s) # 返回列表中s的数量
>
> .remove() # 列表中移除任意指定值
>
> .reverse() # 反转整个列表
>
> .extend() # 将一个列表的所有元素添加到另一个列表的末尾
>
> .sort() # 列表排序
>

del() # 删除指定位置的列表元素

列表用作栈和队列

栈是一种 LIFO （Last In First Out 后进先出）数据结构

.pop() 

队列是一种在末尾追加数据以及在开始弹出数据的数据结构，是（First In First Out 先进先出）的数据结构。

.pop(0)

列表推导式

squares = [] # 简洁版 squares = [x**2 for x in range(10)]

for x in range(10):

​	squares.append(x**2)

***\*集合\**** {,} #squares

一个无序不重复元素的集。基本功能包括关系测试和消除重复元素。

{}或 set() 函数可以用来创建集合。

数学逻辑运算 # 自带去除重复

减- 或| 并& 异或^

***\*字典\**** ={:}

字典是是无序的键值对（key:value）集合，同一个字典内的键必须是互不相同的。

定义 data = {'kushal':'Fedora', 'kart':'Debian', 'Jace':'Mac'}

添加 data['parthan'] = 'Ubuntu'

删除 del data['kushal']

查询 'ShiYanLou' in data

遍历 for x, y in data.items():

向字典中的元素添加数据 dict.setdefault(key, default)

索引 dict.get(key, default) 来索引键，如果键不存在，返回指定的 default 值。

遍历的同时获得元素索引值 enumerate()

同时遍历两个序列类型 zip() 

akingse@cw65s-ubuntu:~/shiyanlou$ python3 student.py

---

字符串

'...'  "..."  '''...'''

***\*内建函数\****

.spite()  .joint()

.title()  .upper()  .lower()

.swapcase()  isalnum()  isalpha()

字符串剥离  strip(chars)

文本搜索  .find()

回文检查  倒序[::-1] # 第一个字符[:1] 去掉最后一个字符[:-1]

单词计数  len()

 

 

***\*函数定义\****

def funname (para):

​	return para

全局变量 global

默认参数值 def fun(a,b=1)

高阶函数,可以接受函数作为参数的函数

map() 函数

文件读取

open()

read()  一次性读取整个文件

with 语句

 

***\*异常处理\****

语法错误 SyntaxError

变量错误 NameError 

类型错误 TypeError 

try...except 块,处理异常

try:

​	input()  #首先，执行 try 子句（此句）

except XXError:

except: #空的 except 语句能捕获任何异常

​	print("Unknown Exception") #如果没有异常发生，except 子句在 [try](#try) 语句执行完毕后就被忽略了。

\#如果在 try 子句中发生了异常，那么该子句其余的部分就会被忽略。

raise 语句抛出异常

```
try:

	raise ValueError("A value error happened.")

except ValueError:

	print("ValueError in our code.")
```

finally 子句在于定义在任何情况下都一定要执行的功能

 

```
try:

	raise KeyboardInterrupt

finally:

	print('Goodbye, world!')

```

 

***\*类与对象\****

class aclassname(parent_class): #定义类

  statement1 #类的声明中你可以写任何 Python 语句，包括定义函数

__init__ 方法,类的实例化操作会自动为新创建的类实例,调用 __init__() 方法

def __init__(self):

  self.data = []

继承,当一个类继承另一个类时，它将继承父类的所有功能（如变量和方法）

 

多继承

```
class MyClass(Parentclass1, Parentclass2,...):

  def __init__(self):

​    Parentclass1.__init__(self)

​    Parentclass2.__init__(self)
```

 

删除对象 del 

属性读取方法,直接使用属性

```
class Student(object):

​	def __init__(self, name):

​		self.name = name
```

@property 装饰器

 

***\*模块\****

模块是包括 Python 定义和声明的文件。文件名就是模块名加上 .py 后缀

import modulename #bars.py

modulename.funcname(para)

from bars import simplebar, starbar

 

***\*包\****

os 模块，[os](#module-os) 模块提供了与操作系统相关的功能。

import os

uname() 函数返回识别操作系统的不同信息

Requests 模块 

 

collections 是 Python 内建的一个集合模块

Counter 类

defaultdict 类

namedtuple 类

---

***\*PEP8代码风格\****

括号、中括号、花括号这样的被包裹元素保持垂直对齐

多行结构中的右圆括号、右中括号、右大括号应该放在最后一行的第一个非空白字符的正下方

使用tab，不允许混合使用制表符和空格来缩进代码。

每行最大长度，限制每行的最大长度为79个字符。

在核心Python3发布版中的代码应该总是使用UTF-8编码

 

迭代器-生成器-生成器表达式

闭包-装饰器

if __name__ == '__main__':

下的代码只有在作为脚本直接执行时才会被执行，而import到其他脚本中是不会被执行的。

 

 