---
title: "序列 - Python编程学习"
source: "https://a358003542.github.io/learning-python-programming/python-03/"
author:
published:
created: 2026-06-28
description:
tags:
  - "clippings"
---
## 序列

字符串，列表，元组都是序列（sequence）的子类，所以序列的一些性质它们都具有。

## len函数

len函数该序列所含元素的个数：

```python
s1='string'
print(len(s1))
```

```
6
```

## 索引

某个序列S，如下索引操作： `S[index]` ，将取出序列中的某个值。

- `index=0` 表示第一个元素
- `index=1` 表示第二个元素， `index=2` 表示第三个元素...
- `index<0` ，将会用值 `len(S)+index` 代替。比如下面的例子 `index=-1` ，进入程序之后将会替换为 `index=5`:

```python
s1="string"
s1[-1]
```

`'g'`

```python
lst1=['a','b','c']
print(lst1[0], lst1[2])
```

```
a c
```

```python
t1 = (1,2,3,4)
print(t1[-1], t1[-2])
```

```
4 3
```

## 常见切片

某个序列S，执行如下常见切片操作： `S[start:stop]` ，将取出序列中的多个连续的值。

- 如果start和stop给定值大于 `len(S)` ，将用 `len(S)` 来代替之
- start默认为0
- stop默认为 `len(S)`

对于常见切片，可以用数学半开区间 `[start, stop)` 来快速理解。

```python
s1 = "string"
print(s1[1:3], s1[-2:-1], s1[:-1], s1[1:], s1[1:-1])
```

```
tr n strin tring trin
```

如果start>=stop，将会返回空值，如果是字符串则是空字符串，如果是列表，则是空列表...等等。

```python
s1 = "string"
print(s1[2:2])
print(type(s1[2:2]))
```

```
<class 'str'>
```

## 扩展切片

某个序列S，执行如下扩展切片操作： `S[start:stop:step]` ，将取出序列中的多个的值。

- step不能为0，step默认为1即上面的常见切片
- start如果 `step>0` 默认为 `0` ；如果 `step<0` 默认为 `len(S)-1`
- stop 如果 `step>0` 默认为 `len(S)` ；如果 `step<0` stop设为 `-1` 【这个是程序内部机制，直接给定负值会被转换的】
- 如果 `step>0` ，如果start和stop给定值大于 `len(S)` ，将用 `len(S)` 来代替之
- 如果 `step<0` ，如果start和stop给定值大于 `len(S)-1` ，将用 `len(S)-1` 来代替之
- 切片产生的索引值根据下面描述的逻辑产生： `index = start + n*step` ， `n>=0` ，n从零开始逐渐加一递增，直到 `n < (stop-start)/step` 不再成立。

总结就是对于 `step>0` ，直到 `index < stop` 不再成立；对于 `step<0` 直到 `index > stop` 不再成立。

一个常见的应用是序列翻转操作：

```python
t1 = (1,2,3)
print(t1[::-1])
```

```
(3, 2, 1)
```

```python
t2 = range(10)
print(list(t2))
print(t2[::-1]) 
print(list(t2[::-1]))
```

```
[0, 1, 2, 3, 4, 5, 6, 7, 8, 9]
range(9, -1, -1)
[9, 8, 7, 6, 5, 4, 3, 2, 1, 0]
```

```python
t2 = range(10)
print(list(t2))
print(t2[::-2]) 
print(list(t2[::-2]))
```

```
[0, 1, 2, 3, 4, 5, 6, 7, 8, 9]
range(9, -1, -2)
[9, 7, 5, 3, 1]
```

```python
t2 = range(10)
print(list(t2))
print(t2[::3]) 
print(list(t2[::3]))
```

```
[0, 1, 2, 3, 4, 5, 6, 7, 8, 9]
range(0, 10, 3)
[0, 3, 6, 9]
```