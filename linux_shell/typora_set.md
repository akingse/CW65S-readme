## 安装typora

```shell
for Linux
# or run:
# sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys BA300B7755AFCFAE
wget -qO - https://typora.io/linux/public-key.asc | sudo apt-key add -
# add Typora's repository
sudo add-apt-repository 'deb https://typora.io/linux ./'
sudo apt-get update
# install typora
sudo apt-get install typora
```

### 命令安装

1）解压tar.gz包
　　　　最常见的gz格式，则可以执行：“tar –xvzf 软件包名”，就可以一步完成解压与解包工作。

　　　　tar -zxvf 软件包名.tar.gz -C /home/hao 将软件包名.tar.gz解压到指定的目录下 （注意：-C为大写）

2）进入解压后的文件目录下 执行“./configure”命令为编译做好准备；

　　　　./configure -prefix=/opt

　　　　表示安装到/opt目录

3） 执行“make”命令进行软件编译；
4） 执行“make install”完成安装；
5） 执行“make clean”删除安装时产生的临时文件。

```shell
tar -zxvf package.tar.gz -C /home/akingse/Download
cd /home/akingse/Download/package
./configure -prefix=/opt
make
make install
make clean
```

---

## typora设置

启动选项 重新打开

自动保存 打开

### 图像（图床）

支持的服务器

### [PicGo](https://picgo.github.io/PicGo-Doc/)

**PicGo: 一个用于快速上传图片并获取图片 URL 链接的工具**

图床工具，就是自动把本地图片转换成链接的一款工具，网络上有很多图床工具，就目前使用种类而言，PicGo 算得上一款比较优秀的图床工具。

custom command 自定义命令

Typora now supports apps like iPic, uPic, PicGo, etc, which is able to upload your images into [Imgur](http://imgur.com/), [Flickr](https://www.flickr.com/),[ Amazon S3](https://aws.amazon.com/s3/), [Github](https://support.typora.io/Upload-Image/www.github.com), or other image hosting services.



### 使用PicGo-core

```
gedit ~/.picgo/config.json
```



尝试使用：阿里云oss和github

阿里云对象存储服务（Object Storage Service，简称OSS）

[开通](https://oss.console.aliyun.com/overview)

创建bucket名称（my-aliyunoss），配置参数。

华北2（北京），无加密

右上角头像区

用户登录名称 akingse@1302367776860584.onaliyun.com

```json
//原文件
{
  "picBed": {
    "current": "smms"
  },
  "picgoPlugins": {}
}
```

使用picBed.aliyun

```json
{
  "accessKeyId": "LTAI4G8Fs126r5pif2hQGhKf",
  "accessKeySecret": "vC3yex8BvzL58xEUN4uCBPFXWhIf4S",
  "bucket": "my-aliyunoss", // 存储空间名
  "area": "oss-cn-beijing", // 存储区域代号
  "path": "img/", // 自定义存储路径
  "customUrl": "" // 自定义域名，注意要加http://或者https://
}
```



### 使用github

新建repo  https://github.com/akingse/my-picbed.git

github（json文件谨慎配置，可能语序相关）[quote](https://blog.csdn.net/brawly/article/details/106436042)

```json
{
  "picBed": {
    "current": "github",
    "github": {
      "repo": "akingse/my-picbed",
      "branch": "main",
      "token": "7251ab640d3d5df8526a350641b12ce4532fa10c",
      "path": "img/",
      "customUrl": "https://github.com/akingse/my-picbed"
    },
    "uploader": "github",
    "transformer": "path"
  },
  "picgoPlugins": {
    "picgo-plugin-github-plus": true,
    "picgo-plugin-smms-user": true
  }
}

```

smms

```json
{
  "picBed": {
    "current": "smms-user",
    "uploader": "smms-user",
    "smms-user": {
      "Authorization": "7AOvTnfXbm2i7Y57hC07boMLMIH6zTD1"
    },
    "transformer": "path"
  },
  "picgoPlugins": {
    "picgo-plugin-smms-user": true,
    "picgo-plugin-github-plus": true
  }
}
```



### 安装插件

```shell
#Linux
cd ~/.config/Typora/picgo/linux
./picgo install smms-user
./picgo install github-plus
#./picgo install gitee-uploader

#Windows
C:\Users\akingse\AppData\Roaming\Typora\picgo\win64
.\picgo.exe install smms-user
#.\picgo.exe install gitee-uploader
.\picgo.exe install github-plus
picgo set uploader
picgo use uploader
```

![image-20201115163529799](https://i.loli.net/2020/11/15/PJ8mXxwLkfERAtM.png)






---

[快捷键](http://support.typora.io/Shortcut-Keys/#change-shortcut-keys)



| Function                                   | Hotkey (Windows/Linux)   |
| :----------------------------------------- | :----------------------- |
| New Paragraph                              | Enter                    |
| New Line                                   | Shift + Enter            |
| 图表换行                                   | Ctrl + Enter             |
| Select Line/Sentence Select Row (in table) | Ctrl + L                 |
| Delete Row (in table)                      | Ctrl + Shift + Backspace |
| Select Style Scope Select Cell (in table)  | Ctrl + E                 |
| Code Fences                                | Ctrl + Shift + K         |
| Math Block                                 | Ctrl + Shift + M         |
| Quote                                      | Ctrl + Shift + Q         |
| Image                                      | Ctrl + Shift + I         |
| Zoom Out                                   | Ctrl + Shift + -         |

---

## markdown语法

gedit设置->高亮模式->markdown
markdown是一种轻量级标记语言，它允许人们“使用易读易写的纯文本格式编写文档，然后转换成有效的XHTML(或者HTML)文档。

---

### 基本符号：* - + >

标题（从大到小取决于#号的数量）
一级标题 # 一级标题
二级标题 ## 二级标题
正文
换行以后直接开始书写，不用加任何符号。
段落
一个段落以一个自然的 回车 作为换行分隔。

### 字体样式

倾斜 *倾斜*
加粗 **加粗**
倾斜并加粗 ***倾斜并加粗***
文字删除线 ~~文字删除线~~

### 引用

这是一段引用 > 引用内容
分隔符
连续输入三个以上的 --- 添加分隔符，下面就会出现一条横线

### 列表

无序列表
使用 * - + 中的任何一个符号加空格就可以创建无序列表
有序列表
使用 数字+点+空格+内容 创建有序列表。
链接
[用markdown写下你的第一个md文档](http://www.jianshu.com/p/de9c98bba332) 
<http://www.jianshu.com> 可以构造一个可点击的链接

### 代码块

`是～号~`

```
长代码段
```

备注。备注语法类似html注释，不好用，下次用引用语法；
<!--原来用gedit书写，不是严格的markdown语言，强行用typora打开，会有显示错误。尤其是换行，原来的换行相当于 shift+enter-->

### markdown翻译

删除线，shift+alt+5

~~strike~~

代码围栏 Ctrl+shift+K

```
code fences
```

引用  Ctrl+shift+Q

> quote

网址链接

[hyperlink](www.baidu.com)

