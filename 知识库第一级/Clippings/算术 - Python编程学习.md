---
title: "算术 - Python编程学习"
source: "https://a358003542.github.io/learning-python-programming/python-01/"
author:
published:
created: 2026-06-28
description:
tags:
  - "clippings"
---
## 算术

## 算术相关基础

- 数值内置类型： int, float.
- 基本算术运算支持： `+ - * / // %` 其中对于整数之间的运算 `%` 为求模或者说求余数； `//` 为整除或者说求商。

```python
5/2
```

`2.5`

```python
5//2
```

`2`

```python
5%2
```

`1`

## 幂方

$x^y$ ，x的y次方，python中是： `x**y` ，此外math模块提供的pow函数也是类似的： `pow(x,y)` 。

```python
2 ** 3
```

`8`

```python
from math import pow
pow(2, 3)
```

`8.0`

## 数值比较

数值比较除了常见的 >，<，==之外，还有 >=，<=，!= （大于等于，小于等于，不等于）。此外python还支持连续比较，就是数学格式 $a<x<b$ ，x在区间 $(a,b)$ 的判断。在python中可以直接写成如下形式： `a<x<b` 。其等于 `x>a and x < b` 。

```python
1<2<3
```

`True`

```python
2>1 and 2 <3
```

`True`

## 整数的进制转换深究

关于整数的进制转换，总要记住： **整数在计算机中是以二进制形式存储的** 。

所谓的该整数的进制转换，只是说要求这个二进制数值以其他不同的进位制显示出来，一般存储了一个数值，要求输出，默认是以十进制的形式显示出来的。

| 进制 | 数值输入 | 数值内转换 | 数值转字符串 | 字符串转数值 |
| --- | --- | --- | --- | --- |
| 二进制 | 0b1100 | bin(number) | f’{number:b}’ | int(‘1100’, base=2) |
| 八进制 | 0o14 | oct(number) | f’{number:o}’ | int(‘14’, base=8) |
| 十进制 | 直接输入 | 直接输出 | f’{number:d}’ | int(‘12’) |
| 十六进制 | 0xc | hex(number) | f’{number:x}’ | int(‘c’, base=16) |

## 浮点数的底层细节

小数之于有理数是一种近似数，如果计算机里面的数字是十进制形式存储的，那么对于小数0.3按照道理来说不会再增加新的近似运算了。但 **数字在计算机中是以二进制形式存储的** ，也就是说对于小数0.3，计算机以有限位数的二进制小数形式来表示，只能得到某种近似数，一个很接近于0.3的数值。这个问题重要吗？这个问题其实并不重要，因为小数本身就是一种近似运算，到底是基于十进制小数的近似计算还是基于二进制小数的近似计算，对于大部分使用场景来说不用在意这些细节。

[更多相关讨论请参看官方文档的这里](https://docs.python.org/zh-cn/3/tutorial/floatingpoint.html) 。

```python
0.1+0.1+0.1 == 0.3
```

`False`

## min，max和sum函数

min，max，sum函数都可以接受一个元组或者列表作为参数，然后返回这个元组或者列表其中的最小值，最大值或者总和。

```python
min((1,6,8,3,4))
```

`1`

```python
max([1,6,8,3,4])
```

`8`

```python
sum([1,6,8,3,4])
```

`22`

此外min和max还支持多个不定参数的收集输入风格：

```python
min(1,6,8,3,4)
```

`1`

## 二进制数字的位操作

- 位左移操作 `<<` ，位左移一位数值有乘以2的效果
- 位右移操作 `>>` ，位右移一位数值有除以2的效果，具体对应的是//整数除法
- 位与操作 `&`
- 位或操作 `|`
- 位异或操作 `^`
- 位取反 `~`

```python
bin(~(0b00100))
```

`'-0b101'`

```python
bin(0b1 << 2)
```

`'0b100'`

```python
bin(0b1 | 0b010)
```

`'0b11'`

```python
bin(0b1 & 0b1)
```

`'0b1'`

```python
bin(0b1 ^ 0b101)
```

`'0b100'`

二进制数字位操作的一个应用就是将一连串的二进制数字作为位标识flag存在：

```python
flag=0b00100100
bin(flag)
```

`'0b100100'`

构建目标位mask值：

- 第一位 `1<<0`
- 第二位 `1<<1`
- ...

```python
mask_3=1<<2
bin(mask_3)
```

`'0b100'`

目标位flag值切换 `number ^ mask值`

```python
bin(flag ^ mask_3)
```

`'0b100000'`

目标位flag设为0 `number & ~mask值`

```python
bin(flag & ~mask_3)
```

`'0b100000'`

目标位flag设为1 `number | mask值`

```python
bin(flag | mask_3)
```

`'0b100100'`

## math模块

math模块里面提供了常见的一些数学常数，比如 `pi` 和 `e` 来，以及一些常见的数学函数支持。更多内容请参见 [官方文档](http://docs.python.org/3/library/math.html) 。

**sqrt**

开平方根函数，sqrt(x)。

**sin**

正弦函数，类似的还有cos，tan等，sin(x)。

**degrees**

将弧度转化为角度，三角函数默认输入的是弧度值。

**radians**

将角度转化位弧度，radians(30)。

**log**

开对数，log(x,y)，即 $\log_y x$ ，y默认是e。

**exp**

指数函数，exp(x)。

**pow**

扩展了内置方法，现在支持float了。pow(x,y)

```python
from math import pi
pi
```

`3.141592653589793`

```python
from math import sqrt
sqrt(85)
```

`9.219544457292887`

```python
from math import sin, radians 
round(sin(radians(30)),1) #sin(30°)
```

`0.5`

## random模块

random模块提供了一些函数来解决随机数问题。更多内容请参见 [官方文档](http://docs.python.org/3/library/random.html) 。

**random**

random函数产生0到1之间的随机实数（包括0）。 `random()-> [0.0, 1.0) ` 。

**uniform**

uniform函数产生从a到b之间的随机实数（a，b的值指定，包括a。）。 `uniform(a,b)-> [a, b)` 。

**randint**

randint函数产生从a到b之间的随机整数，包含a和b。 `randint(a,b)-> [a,b]`

**choice**

choice随机从一个列表或者字符串中取出一个元素。

```python
from random import random
random()
```

`0.7398455176664422`

```python
from random import uniform
uniform(1,10)
```

`3.5288565433265577`

```python
from random import randint
randint(1,10)
```

`4`

```python
from random import choice
choice('abcdefghij')
```

`'a'`

```python
choice(['1','2','3'])
```

`'3'`