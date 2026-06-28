---
title: "安装和配置 - Python编程学习"
source: "https://a358003542.github.io/learning-python-programming/python-00/"
author:
published:
created: 2026-06-28
description:
tags:
  - "clippings"
---
python的安装和配置在linux没什么好说了。

windows下的安装现在已经提供选项可以直接设置 `PATH` 变量了，建议勾选上。如果忘了勾选，那么如下设置下：

![img](https://a358003542.github.io/learning-python-programming/build/python-env-windows-e2118862a95da79486ebecd7680cf31c.png)

## 进入python的REPL环境

在终端中输入python即进入python语言的REPL环境，你可以运行：

```
python  --version
```

来查看默认的python版本号。

## python命令行用法

命令行的一般格式就是：

```
python3  [可选项]  test.py  [可选参数1 可选参数2]
```

运行 `python3  --help` 即可以查看python命令的一些可选项。比如加入 `-i` 选项之后，python执行完脚本之后会进入REPL环境继续等待下一个命令，这个在最后结果一闪而过的时候有用。

### python执行脚本参数的传递

上面的命令行接受多个参数都没有问题的，不会报错，哪怕你在py文件并没有用到他们。在py文件中要使用他们，首先导入sys模块，然后调用 `sys.argv` 变量。其中 `sys.argv[0]` 是现在这个py文件在系统中的文件名，接下来的 `sys.argv[1]` 就是之前命令行接受的第一个参数，后面的就依次类推了。

## 代码注释

python语言的注释符号是用 `#` 符号来注释代码。

多行注释可以利用编辑器快速每行前面加上 `#` 符号。

## 代码多行表示一行

这个技巧防止代码越界所以经常会用到。用反斜线 `\` 即可。不过更常用的是将表达式用圆括号 `()` 括起来，这样内部可以直接换行并继续。在python中任何表达式都可以包围在圆括号中。

## 一行表示多行

python中一般不用分号，分号的意义大致和c语言中的意义类似，表示一行结束的意思。其中C语言我们知道是必须使用分号的。

## 输入和输出

input函数请求用户输入，并将这个值赋值给某个变量。注意赋值之后类型是字符串，但后面你可以用强制类型转换，比如int函数（将其变成整数），float函数（将其变成小数）等来将其转成你想要的数据类型。

print函数就是编程语言中常见的的屏幕显示输出函数。

读者请运行下面的例子：

```
x=input('请输入一个实数：')
string='你输入的这个实数乘以2等于：'+ str(float(x)*2)
print(string)
```

## 你可能不需要虚拟环境

只要项目超过两个人以上协作，那么就需要使用python虚拟环境。

在linux环境下哪怕最小型的项目都是鼓励使用虚拟环境的。

但也不要想当然认为所有情况下都要使用虚拟环境。如果是个人本地项目，而且这些项目里面的某些模块占用了超过几个G的存储空间，你本地固态硬盘空间也不是那么富裕，这种情况下是不需要虚拟环境的。

安装虚拟环境：

```
python -m venv venv_folder_name
```

更多内容请参看 [官方文档的这里](https://docs.python.org/3/tutorial/venv.html) 和 [venv模块文档](https://docs.python.org/3/library/venv.html) 。