---
title: "Python编程学习 - Python编程学习"
source: "https://a358003542.github.io/learning-python-programming/"
author:
published:
created: 2026-06-28
description:
tags:
  - "clippings"
---
## 前言

本文在行文上力图简洁：

1. 有问题，问AI，或查网站，或查看官方文档。
2. 对于参考资料式的内容，如果确实有必要，会添加进来，但大多只是提供一个指引方向。
3. 对于不太重要的内容，也不会强行添加进来凑字数。
4. 对于重要的内容，个人感兴趣的内容，才会来上一大段文字分析思考之。

## 基础自检

1. 安装好你自己的python环境，进入REPL环境，用print打印出hello world。新建一个test.py文件，里面写上之前的打印命令，然后用python执行该脚本。
2. 安装好你自己的IDE开发环境，pycharm或者vscode都挺不错的，vscode里面有教程指引，配置好插件和环境，再利用IDE完成步骤一。
3. 学会int和float数据类型，进行简单的加减乘除和取模操作。
4. 学会字符串数据类型，重点学会字符串的切片取值哪些操作，了解如果两个字符串相加会如何。
5. 学会变量赋值，完成一系列的实践活动，比如对x赋值字符串，然后又对x赋值某个数值，print观察x的变化，又新增变量y，赋值某个数值，将数值x和y两个变量相加，将结果赋值给z，观察z的结果。
6. 学会列表数据类型，参考之前字符串的切片取值操作对列表进行切片取值，了解两个列表相加会如何。比对字符串和列表，通过学习列表的append和insert方法，认识到数据类型分为两类，一类是可变对象，一类是不可变对象。
7. 根据上面的不可变对象的概念和列表数据类型，简单介绍下元组数据类型。
8. 学会字典数据类型，会新建一个字典，会从字典取值，会修改字典的某个key的值。
9. 简单了解下集合数据类型。
10. 认识到之前的print函数是python的内置函数，会定义自己的函数，了解函数的参数和返回值，会定义参数的默认值。请实践编写一个自己的double函数，接受一个参数，并将这个参数乘以2之后返回结果。
11. 熟悉python的if else和elif条件控制语句。
12. 熟悉python的for while循环控制语句。熟悉循环结构中如果加上break或continue程序会怎么走。
13. 会用for语句迭代列表和字典，介绍字典的keys values方法和enumerate函数。
14. 简单介绍异常的概念，会用try except来捕捉异常。
15. 请实践用class编写自己的对象，定义属性，定义方法。请实践定义一个父类然后定义子类来实现继承关系，定义属性，定义方法，摸索探索上面的样例。简单了解类的mro方法，简单了解各个属性的搜索先后顺序机制。
16. 一个python文件就是一个模块，请实践编写模块，里面有一个简单的函数，然后通过import再另外一个python文件中调用它。然后简单了解下python的模块查找顺序：当前文件夹，built-in,PYTHONPATH,python安装地，总的来说就是根据sys.path来查找的。
17. 简单了解下pypi服务，会用pip安装一个第三方包，并调用第三方包的某个函数。

## 参考资料

- [官网上的资料](https://docs.python.org/3/).
- 《python学习手册（第四版）》 by Mark Lutz & 李军.
- 《A Guide to Python’s Magic Methods》 by Rafe Kettler at 2014 in [magicmethods](https://github.com/RafeKettler/magicmethods).
- 《流畅的python》 by Luciano Ramalho & 安道.