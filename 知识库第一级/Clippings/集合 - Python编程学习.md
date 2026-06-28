---
title: "集合 - Python编程学习"
source: "https://a358003542.github.io/learning-python-programming/python-08/"
author:
published:
created: 2026-06-28
description:
tags:
  - "clippings"
---
## 集合

python的集合在概念上大体类似于数学上的无序不重复元素的集合概念，在前面讨论列表去重元素的时候我们提到过正好可以利用集合的这一特性。

```python
set([1,2,3,1,2,4,4,5,5,5,7])
```

`{1, 2, 3, 4, 5, 7}`

## 集合添加元素

**警告** ：值得一提的是集合只能包括不可变类型，因此列表和字典不能作为集合内部的元素。元组不可变，所以可以加进去。

```python
s1 = set()
s1.add(1)
print(s1)
s1.add(2)
print(s1)
s1.add(1)
print(s1)
```

```
{1}
{1, 2}
{1, 2}
```

我们看到用集合的 **add** 方法，那些重复的元素是添加不进来的。

或者使用update方法一次更新多个元素：

```python
s2=set('a')
s2.update(['a','b','c'])
print(s2)
```

```
{'a', 'b', 'c'}
```

## 集合去除元素

有两个集合对象的方法可以用于去掉集合中的某个元素，discard方法和remove方法，其中discard方法如果删除集合中没有的元素那么什么都不会发生，而remove方法如果删除某个不存在的元素那么会产生KeyError。

```python
s3 = set('hello')
s3.discard('h')
print(s3)
s3.discard('x')
print(s3)
s3.remove('l')
print(s3)
```

```
{'e', 'l', 'o'}
{'e', 'l', 'o'}
{'e', 'o'}
```

## 子集关系判断

issubset方法用于判断这个集合是不是另一个集合的子集：

```python
s4 = set(['a','b'])
s5 = set(['a','b','c'])
s4.issubset(s5)
```

`True`

如果对python的大小判断操作有很深的理解的，那么可以用>，<，>=，<=，==这样的运算符来判断。

```python
print(s4<=s5)
print(s4<s5)
```

```
True
True
```

## 交集并集和差集

- 交集 `&` 运算符或者 intersection方法
- 并集 `|` 运算符或者 union方法
- 差集 `-` 运算符或者 difference方法

```python
s6 = set('hello')
s7 = set('hao')
print(s6 & s7) #交集
print(s6 | s7) #并集
print(s6 - s7) #差集
```

```
{'o', 'h'}
{'o', 'h', 'e', 'l', 'a'}
{'e', 'l'}
```