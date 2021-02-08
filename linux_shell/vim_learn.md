

[# Linux vi/vim](https://www.runoob.com/linux/linux-vim.html)

## 什么是 vim？

Vim是从 vi 发展出来的一个文本编辑器。代码补完、编译及错误跳转等方便编程的功能特别丰富，在程序员中被广泛使用。 

简单的来说， vi 是老式的字处理器，不过功能已经很齐全了，但是还是有可以进步的地方。 vim 则可以说是程序开发者的一项很好用的工具。 paste

连 vim 的官方网站 (http://www.vim.org) 自己也说 vim 是一个程序开发工具而不是文字处理软件。

vim 键盘图：

![img](https://i.loli.net/2021/01/07/OEFQbVitySfhKqH.gif)



paste

保存退出

```
按esc
：wq!
按enter
```

out-to-vim

![

](https://i.loli.net/2021/02/04/9fNM6qk3PzLlaEZ.png)

E353: Nothing in register +

```
sudo chown akingse.akingse ~/.viminfo 
```





---

## 备份树莓派镜像

[quote](https://www.lxx1.com/1450)

```
df -h
sudo dd if=/dev/sdc | gzip>/home/akingse/raspberry.gz

还原
sudo gzip -dc /home/raspberry.gz | sudo dd of=/dev/sdc
```





