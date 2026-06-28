---
title: "字典 - Python编程学习"
source: "https://a358003542.github.io/learning-python-programming/python-07/"
author:
published:
created: 2026-06-28
description:
tags:
  - "clippings"
---
## 字典

python字典底层数据结构是一个哈希表，所谓的字典的key必须是可hash对象，然后通过hash函数来找到对应的值的地址。python字典的查找插入删除时间复杂度都是 `O(1)`,还是很高效的，主要是以空间换时间，相比较其他数据结构空间利用率上略低效。

字典是可变对象，因为你可以直接O(1)复杂度的原地修改字典的某个key对应的值，前面提到字典的空间开销略大，而如果将字典设定为不可变对象，每次字典值变动然后就需要重新创建字典对象这显然是不可理喻的。

并非所有对象都可以做字典key，在python中所有的内置不可变对象都是可哈希的，所有的可变对象都是不可哈希的。而只有可哈希的才可以做字典的key。可哈希的对象具有：

- 具有 `__hash__` 方法，这样可以比较大小
- 具有 `__eq__` 方法，这样可以判断相等。

下面继续就上面的讨论来更深入地理解字典的寻址：

```python
t = {True: 'yes', 1: 'no', 1.0: 'maybe'}
t
```

`{True: 'maybe'}`

```python
print(True == 1 == 1.0)
```

```
True
```

```python
print(hash(True))
print(hash(1))
print(hash(1.0))
```

```
1
1
1
```

python首先要判断这两个key值是否相等，如果值不相等那么它们的hash值肯定也不相等，但是值相等也不一定这两者的hash值相等，有一些比较特殊的情况，初学者没必要了解这些。

也正是因为这样，下面的字典更新语句写法是可行的：

```python
x = {'a':1, 'b':2}
y = {'b':3}
z = {**x, **y}
z
```

`{'a': 1, 'b': 3}`

这是很python风格的字典更新方式，效率很高，是推荐的写法。

## 创建字典

字典是一种映射，并没有从左到右的顺序，只是简单地将键映射到值。字典的声明格式如下：

```python
dict1={'name':'tom','height':'180','color':'red'}
dict1['name']
```

`'tom'`

```python
dict2={}
dict2['name']='bob'
dict2['height']=195
print(dict2)
```

```
{'name': 'bob', 'height': 195}
```

## 根据列表创建字典

如果是 `[['a',1],['b',2],['c',3]]` 这样的形式，那么直接用dict函数处理就变成字典了。

如果是 `['a','b','c']` 和 `[1,2,3]` 这样的形式那么需要用zip函数处理一下，然后用dict函数处理一次就变成字典了。zip函数的工作原理就是将前后两个可迭代对象两边各取一个配对成为一个目标元素，这些元素是新生成的可迭代对象的输出的元素。

```python
list1 = [['a', 1], ['b', 2], ['c', 3]]
dict3 = dict(list1)
dict3
```

`{'a': 1, 'b': 2, 'c': 3}`

```python
list2 = ['a', 'b', 'c']
list3 = [1, 2, 3]
dict4 = dict(zip(list2, list3))
dict4
```

`{'a': 1, 'b': 2, 'c': 3}`

## 字典遍历键

如果你对字典遍历的返回的 `键` 的顺序没有要求，那么就可以简单的这样处理：

```python
for key in dict1:
    print(key,':',dict1[key])
```

```
name : tom
height : 180
color : red
```

如果有顺序要求，那么可以用字典的 `keys()` 方法来获取字典的 `键` 的列表，然后排序，然后再迭代。

```python
dict5 = {'c':5 , 'a': 1, 'b':9}

for key in dict5:
    print(key,'->',dict5[key])

print('-' * 10)

for key in sorted(dict5.keys()):
    print(key,'->',dict5[key])
```

```
c -> 5
a -> 1
b -> 9
----------
a -> 1
b -> 9
c -> 5
```

## 字典遍历值

通过字典的 `values()` 方法来遍历字典的值。

## 字典遍历键值对

字典的 `items()` 方法返回的是字典的 `(key,value)` 键值对。

```python
dict6 = {'andy':5,'bruce':1,'black':55,'goody':9}
for key,value in dict6.items():
    print(key, '->', value)
```

```
andy -> 5
bruce -> 1
black -> 55
goody -> 9
```

如下实现了对字典的按值排序输出：

```python
for key,value in sorted(dict6.items(),key=lambda i: i[1]):
    print(key, '->', value)
```

```
bruce -> 1
andy -> 5
goody -> 9
black -> 55
```

## 字典的in语句

字典的in语言可以用来判断某个键是否存在在字典中。

```
>>> dict001={'a':1,'b':2,'c':3}
>>> 2 in dict001
False
>>> 'b' in dict001
True
```

```python
print(dict3)
print(2 in dict3)
print('b' in dict3)
```

```
{'a': 1, 'b': 2, 'c': 3}
False
True
```

## 字典的get方法

get方法是去找某个键的值，和直接索引字典 `dict3['b']` 的区别是 `get()` 方法在某个键不存在的时候也不会出错，而且你还可以设置如果不存在的情况下想要返回的某个默认值。

```
>>> dict001={'a':1,'b':2,'c':3}
>>> dict001.get('b')
2
>>> dict001.get('e')
```

```python
print(dict3)
print(dict3.get('b'))
print(dict3.get('e'))
print(dict3.get('e', 0))
```

```
{'a': 1, 'b': 2, 'c': 3}
2
None
0
```

## 字典的update方法

字典的 `update()` 方法实现了对于字典的键值对的更新逻辑，如果某个键不存在，则加上，如果该键已存在，则覆盖新指定的值。 `update()` 方法是原地修改式的，TODO 解释字典的数据结构。

```python
dict7 = {'a':1,'b':2,'c':3}
dict8 = {'e':4, 'a':5}
dict7.update(dict8)
print(dict7)
```

```
{'a': 5, 'b': 2, 'c': 3, 'e': 4}
```

## 字典解析

类似于列表解析，也有如下这样的字典解析语句，同样和常规编程语句比起来字典解析效率会略高一些。

```python
dict9 = {a:b for a,b in zip(['a', 'b', 'c', 'd'], [1,2,3,4])}
print(dict9)
```

```
{'a': 1, 'b': 2, 'c': 3, 'd': 4}
```