---
title: "元组 - Python编程学习"
source: "https://a358003542.github.io/learning-python-programming/python-06/"
author:
published:
created: 2026-06-28
description:
tags:
  - "clippings"
---
## 元组

圆括号包含几个元素就是元组(tuple)。元组和列表的不同在于元组是不可改变。元组和列表都属于序列对象，之前介绍列表的一些方法元组也是有的。

值得一提的是如果输入的时候写的是 *x,y* 这样的形式，实际上表达式就加上括号了，也就是一个元组了 `(x,y)` 。

元组不可以直接更改。

## 生成器表达式

类似列表解析，元组也有类似的表达语句，不过不叫作元组解析，而是有一个更专门的名字：生成器表达式。

生成器表达式返回的是生成器对象，和生成器函数具体调用之后返回的对象是一样的。生成器对象具有 `__next__` 方法，可以调用next函数。

```python
y = (i for i in [1,2,3])
print(y)
print(list(y))
```

```
<generator object <genexpr> at 0x000001CC9B5DAE00>
[1, 2, 3]
```