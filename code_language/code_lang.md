***\*RUNBOO 概念\****

[***\*https://www.runoob.com/\****](https://www.runoob.com/)

 

***\*HTML\****

> 超文本标记语言（英语：HyperText Markup Language，简称：HTML）是一种用于创建网页的标准标记语言。
>
> 您可以使用 HTML 来建立自己的 WEB 站点，HTML 运行在浏览器上，由浏览器来解析。
>
> 中文网页需要使用 <meta charset="utf-8"> 声明编码
>
> 最好用标准的大写"UTF-8"，除了MySQL的命令模式中使用"utf8"
>
> Web浏览器（如chrome）是用于读取HTML文件，并将其作为网页显示。
>
> 浏览器并不是直接显示的HTML标签，但可以使用标签来决定如何展现HTML页面的内容给用户
>
> 通用声明 HTML5 <!DOCTYPE html>

 

***\*CSS\**** 

> 通过使用 CSS 我们可以大大提升网页开发的工作效率！
>
> 在我们的 CSS 教程中，您会学到如何使用 CSS 同时控制多重网页的样式和布局。
>
> CSS 指层叠样式表 (Cascading Style Sheets)

 

***\*JavaScript\**** 

> JavaScript 是 Web 的编程语言。
>
> 所有现代的 HTML 页面都使用 JavaScript。
>
> JavaScript web 开发人员必须学习的 3 门语言中的一门：
>
> HTML 定义了网页的内容
>
> CSS 描述了网页的布局
>
> JS (JavaScript) 网页的行为
>
> JavaScript 是脚本语言
>
> JavaScript 是一种轻量级的编程语言。
>
> JavaScript 是可插入 HTML 页面的编程代码。
>
> JavaScript 插入 HTML 页面后，可由所有的现代浏览器执行。
>
> JavaScript 与 Java 是两种完全不同的语言，无论在概念上还是设计上。Java是更复杂的编程语言。
>
> ECMA-262 是 JavaScript 标准的官方名称。于 1997 年被 ECMA（一个标准协会）采纳。

 

***\*jQuery\**** 

> jQuery 是一个 JavaScript 库。
>
> jQuery 极大地简化了 JavaScript 编程。
>
> jQuery 库可以通过一行简单的标记被添加到网页中。

 

***\*Bootstrap\****，来自 Twitter，是目前最受欢迎的前端框架。Bootstrap 是基于 HTML、CSS、JAVASCRIPT 的，它简洁灵活，使得 Web 开发更加快捷。

 

***\*Java\**** 

> Java是由Sun Microsystems公司于1995年5月推出的高级程序设计语言。
>
> Java可运行于多个平台，如Windows, Mac OS，及其他多种UNIX版本的系统。
>
> Java分为三个体系：
>
> JavaSE（J2SE）（Java2 Platform Standard Edition，java平台标准版）
>
> JavaEE(J2EE)(Java 2 Platform,Enterprise Edition，java平台企业版)
>
> JavaME(J2ME)(Java 2 Platform Micro Edition，java平台微型版)。

 

Java语言的语法与C语言和C++语言很接近，使得大多数程序员很容易学习和使用。另一方面，Java丢弃了C++中很少使用的、很难理解的、令人迷惑的那些特性，如操作符重载、多继承、自动的强制类型转换。特别地，Java语言不使用指针，而是引用。并提供了自动的废料收集，使得程序员不必为内存管理而担忧。

---

  

***\*Linux\**** 

> Linux 英文解释为 Linux is not Unix。
>
> Linux 内核最初只是由芬兰人林纳斯·托瓦兹（Linus Torvalds）在赫尔辛基大学上学时出于个人爱好而编写的。
>
> Linux 是一套免费使用和自由传播的类 Unix 操作系统，是一个基于 POSIX 和 UNIX 的多用户、多任务、支持多线程和多 CPU 的操作系统。
>
> Linux 能运行主要的 UNIX 工具软件、应用程序和网络协议。Linux 继承了 Unix 以网络为核心的设计思想，是一个性能稳定的多用户网络操作系统。
>
> Linux 的发行版
>
> Linux 的发行版说简单点就是将 Linux 内核与应用软件做一个打包。
>
> 目前市面上较知名的发行版有：Ubuntu、RedHat、CentOS、Debian、Fedora、SuSE、OpenSUSE、Arch Linux、SolusOS 等。
>
> 天各种场合都有使用各种 Linux 发行版，从嵌入式设备到超级计算机，并且在服务器领域确定了地位，通常服务器使用 LAMP（Linux + Apache + MySQL + PHP）或 LNMP（Linux + Nginx+ MySQL + PHP）组合。

 

***\*shell 程序界面\****

> shell是一个用 C 语言编写的程序，它是用户使用 Linux 的桥梁。Shell 既是一种命令语言，又是一种程序设计语言。Shell 是指一种应用程序，这个应用程序提供了一个界面，用户通过这个界面访问操作系统内核的服务。
>
> Shell 脚本
>
> Shell 脚本（shell script），是一种为 shell 编写的脚本程序。
>
> Shell 编程跟 JavaScript编程一样，只要有一个能编写代码的文本编辑器和一个能解释执行的脚本解释器就可以了
>
> Linux 的 Shell 种类众多，常见的有
>
> Bourne Again Shell（/bin/bash）

***\*bash\****由于易用和免费，Bash 在日常工作中被广泛使用。同时，Bash 也是大多数Linux 系统默认的 Shell。

写第一个shell脚本

```
#!/bin/bash #! 是一个约定的标记，它告诉系统这个脚本需要什么解释器来执行
echo "Hello World !" #echo用于字符串的输出

$ chmod +x ./test.sh  #使脚本具有执行权限

$ ./test.sh  #执行脚本
```

***\*source、sh、bash、./ 执行脚本\****

```
source FileName
作用:在当前 bash 环境下读取并执行 FileName 中的命令。该命令通常用命令 . 来替代。

sh FileName或bash FileName
作用:打开一个子 shell 来读取并执行 FileName 中命令。运行一个shell脚本时会启动另一个命令解释器。

./FileName
作用: 打开一个子 shell 来读取并执行 FileName 中命令，该 filename 文件需要 "执行权限"。运行一个 shell 脚本时会启动另一个命令解释器。
```

 

 

 

***\*C#\**** 

> C# 是一个简单的、现代的、通用的、面向对象的编程语言，它是由微软（Microsoft）开发的。
>
> C# 是专为公共语言基础结构（CLI）设计的。CLI 由可执行代码和运行时环境组成，允许在不同的计算机平台和体系结构上使用各种高级语言。
>
> .Net 框架（.Net Framework）
>
> .Net 框架是一个创新的平台，能帮编写出下面类型的应用程序：Windows 应用程序，Web 应用程序，Web 服务
>
> .Net 框架应用程序是多平台的应用程序。框架的设计方式使它适用于下列各种语言：C#、C++、Visual Basic、Jscript、COBOL 等等。所有这些语言可以访问框架，彼此之间也可以互相交互。
>
> .Net 框架由一个巨大的代码库组成，用于 C# 等客户端语言

```c#
using System;
namespace HelloWorldApplication
{
  class HelloWorld  /* 类名为 HelloWorld */
  {
    static void Main(string[] args)    /* main函数 */
    {
      Console.WriteLine("Hello World!");     /* 我的第一个 C# 程序 */
      Console.ReadKey();
    }
  }
}
```

 

***\*SQL\**** 

> SQL 是用于访问和处理数据库的标准的计算机语言。
>
> SQL，指结构化查询语言，全称是 Structured Query Language。
>
> SQL 让您可以访问和处理数据库。
>
> SQL 是一种 ANSI（American National Standards Institute 美国国家标准化组织）标准的计算机语言。
>
>  

```
use RUNOOB; 命令用于选择数据库。

set names utf8; 命令用于设置使用的字符集。

SELECT * FROM Websites; 读取数据表的信息。
```

 

***\*MySQL\**** 是最流行的关系型数据库管理系统，在 WEB 应用方面 MySQL 是最好的 RDBMS(Relational Database Management System：关系数据库管理系统)应用软件之一。

> 数据库（Database）是按照数据结构来组织、存储和管理数据的仓库。
>
> 每个数据库都有一个或多个不同的 API 用于创建，访问，管理，搜索和复制所保存的数据。
>
> 将数据存储在文件中，但是在文件中读写数据速度相对较慢。使用关系型数据库管理系统（RDBMS）来存储和管理大数据量。所谓的关系型数据库，是建立在关系模型基础上的数据库，借助于集合代数等数学概念和方法来处理数据库中的数据。
>
> RDBMS 表格，行（记录名称）列（数据域）组成 表单，若干表单组成 database。
>
> MySQL 为关系型数据库, "关系型"可以理解为"表格"的概念, 一个关系型数据库由一个或数个表格组成

![img](tmp/wps-akingse/ksohtml/wpsSW7s0j.jpg) 

表头(header): 每一列的名称;

列(col): 具有相同数据类型的数据的集合;

行(row): 每一行用来描述某条记录的具体信息;

值(value): 行的具体信息, 每个值必须与该列的数据类型相同;

键(key): 键的值在当前列中具有唯一性。

MySQL数据库

MySQL 是一个关系型数据库管理系统，由瑞典 MySQL AB 公司开发，目前属于 Oracle 公司。MySQL 是一种关联数据库管理系统，关联数据库将数据保存在不同的表中，而不是将所有数据放在一个大仓库内，这样就增加了速度并提高了灵活性。

 

 

***\*PHP\**** 

PHP 是一种创建动态交互性站点的强有力的服务器端脚本语言。

PHP（全称：PHP：Hypertext Preprocessor，即"PHP：超文本预处理器"）是一种通用开源脚本语言。

PHP 脚本以 <?php 开始，以 ?> 结束：

PHP 文件的默认文件扩展名是 ".php"。

PHP 文件通常包含 HTML 标签和一些 PHP 脚本代码。

```html
<!DOCTYPE html>
<html>
<body>
<h1>My first PHP page</h1>
<?php
echo "Hello World!";
?>
</body>
</html>


```

 

---

![img](tmp/wps-akingse/ksohtml/wpsrVn1Es.jpg) 

![img](tmp/wps-akingse/ksohtml/wpsqiWCjB.jpg) 

解决方案名称

C:\Users\Akingse\source\repos\test2001_solution

新建项目-Windows桌面向导-名称

C:\Users\Akingse\source\repos\test2001_solution\vs2017_test2001

### GitHub使用教程

为其他项目贡献代码非常简单：首先点击项目站点的“fork”的按钮，然后将代码检出并将修改加入到刚才分出的代码库中，最后通过内建的“pull request”机制向项目负责人申请代码合并。

GitHub的两个主要优点，适合团队协作，以及下载其他优秀者的代码



### 在windows下安装Git

下载网址: http://git-scm.com/download/

github网站上去配置一下ssh key

配置一下用户名和邮箱：

目录下右键 Git Bash Here

```shell
$ git init #来完成初始化工作。这时候目录里面就多了一个.git的目录了

$ git remote add origin git@github.com:akingse/test2020.git #用户名/仓库名

$ git pull [git@github.com:]()[akingse/test2020]()[.git]()

git add .  

git commit –m

git push

git clone 默认下载位置为 C/user/akingse当前用户下

git clone https://github.com/×××  从远程库中克隆,克隆一个版本库到新的目录，可以在当前目录新建一个文件夹，也可以git clone [地址] [本地目录]
```

 

