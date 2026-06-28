---
title: "字符串 - Python编程学习"
source: "https://a358003542.github.io/learning-python-programming/python-04/"
author:
published:
created: 2026-06-28
description:
tags:
  - "clippings"
---
## 字符串

- 用单引号或者双引号包起来就表示一个字符串了。单引号和双引号并没有什么特别的区别，只是如果字符串里面有单引号，那么就使用双引号，这样单引号直接作为字符处理而不需要而外的转义处理。在单引号或者双引号的情况下，你可以使用 `\n` 来换行。此外还可以使用三单引号 `'''` 或者三双引号 `"""` 来包围横跨多行的字符串，其中的换行就会直接保留。
- python的字符串是不可变对象，你看到的一切看起来似乎字符串发生了改变的操作都不过是重新创建了一个新的字符串对象。
- 字符串相加是字符串拼接操作，乘法是加法的重复，一个字符串乘以一个数字是其和自身拼接了几次。

```python
print('abc'+'def')
print('abc' * 3)
```

```
abcdef
abcabcabc
```

## 字符编码

- 字符集： 一些字符组成的集合
- 编码：将信息从一种形式转换为另一种形式的过程
- 字符编码：针对某一字符集，为其中的字符编码。一般来说指的是将信息从人所见的字符转换为计算机内二进制存储格式的过程。
- ASCII码：既确定了字符集也确定了字符编码规范，计算机内二进制存储格式为八位二进制数字，因此只表征了有限的字符集，主要针对英文的使用。
- Unicode：通用字符集，旨在罗列人类语言用到的所有字符。Unicode标准还会给它收集到的字符分配一个码位（code point），这个码位实际上就是这个字符的名字，因为有些字符可能从字形上看起来差不多的，最终还是要靠这个码位来区分开来。这个Unicode码也不是该字符真的在计算机中存储的二进制数字。
- UTF8： 针对Unicode字符集确立的字符编码。它有很多优点，这里就不细讲了。一个字符的UTF8码就真的是它在计算机中存储的那一串二进制数字。

- python的字符串就是一个序列里面存储了一连串的Unicode字符
- python默认字符编码是UTF8
- python可以如下将字符串转成bytes对象——由单个字节构成的不可变序列。bytes对象已经移除了默认字符编码UTF8的假定了，下面的 `\xe4` 只是在表示单个字节即8位的二进制数字。

这块简单了解下即可，日常应用如果没有遇到问题就没问题，如果遇到编码相关问题再去研究，这块有的时候还挺麻烦的。 [更多内容请参看官方文档的这里](https://docs.python.org/zh-cn/3/howto/unicode.html)

```python
s1 = "中文"
s1.encode(encoding='utf8')
```

`b'\xe4\xb8\xad\xe6\x96\x87'`

## 字符转义

原本字符转义只是针对ASCII编码里面的一些特殊字符的输入问题。比如 `\n` 表示换行， `\t` 表示制表符：

```python
print('\tabc \ntest')
```

```
abc 
test
```

python提供raw string字符串输入，这样字符串里面的 `\` 不会解释为转义字符，即具有特殊含义的字符。

```python
print(r'\tabc \ntest')
```

```
\tabc \ntest
```

字符转义在某些情况下会很让人困扰，尤其是你要正则匹配某些路径或者latex命令，其中 `\` 符号很是常见。比如你要正则匹配latex命令 `\chapter` ，通过文件读取到python的字符串里面，它成了 `\\chapter` ，正则表达式即使使用raw string，也还是需要再加上一个反斜杠： `pattern=r'\\chapter'` 。

## f-string

python3.6新加入进来的特性，短短时间马上流行起来了，因为真的非常好用：

```
f"hello. {name}"
```

等价于

```
"hello. {name}".format(name=name)
```

推荐使用上直接使用f-string，学习上还是要多查看字符串format方法的官方文档。

## format方法

更详细的内容请参看 [官方文档](https://docs.python.org/zh-cn/3/library/string.html) 。

## 等宽数字

```
{:0>2d}
```

目标数字宽度为两位，左边填充0 ， `>` 表示左边填充， `0>` 表示左边填充0，此外还有 `<` 表示右边填充。

```python
"{:0>2d}".format(1)
```

`'01'`

## 花括号的问题

花括号因为是特殊字符，要显示花括号，需要如下输入两次：

```python
print(f'{{----}}')
```

```
{----}
```

## 字符串的方法

字符串的方法有：

- startswith
- endswith
- find
- replace
- upper
- isdigit
- isalpha
- isalnum
- split
- splitline
- join
- count

更详细的内容请参看 [官方文档](https://docs.python.org/zh-cn/3/library/string.html) 。