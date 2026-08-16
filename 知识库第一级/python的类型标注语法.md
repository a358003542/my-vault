你提到的类型标注语法是指 Python 3.5+ 引入的类型提示（Type Hints），主要用于提高代码可读性和静态类型检查（如 mypy）。下面结合你看到的那段代码逐一解释。

## 一、基础类型

```
def some_function(name: str, age: int) -> bool:
    ...
```

- `name: str`：参数 `name` 期望是字符串类型。
- `age: int`：参数 `age` 期望是整数类型。
- `-> bool`：函数返回值期望是布尔类型。

## 二、容器类型（来自 `typing` 模块）

```
from typing import List, Tuple, Optional, Callable
```

### 1. `List[类型]`

表示元素均为指定类型的列表。例如：

```
def get_names() -> List[str]:
    return ["Alice", "Bob"]
```

### 2. `Tuple[类型1, 类型2, ...]`

表示固定长度、各位置类型确定的元组。例如：

```
def get_record() -> Tuple[int, str]:
    return (1, "hello")
```

注意：`Tuple[int, str]` 表示两个元素，第一个是 int，第二个是 str。如果要表示可变长度的同类型元组，用 `Tuple[int, ...]`。

### 3. `Optional[类型]`

等价于 `Union[类型, None]`，表示该值可以是指定类型，也可以是 `None`。

```
def find_user(user_id: int) -> Optional[str]:
    # 可能返回用户名，也可能返回 None
    ...
```

### 4. `Callable[[参数类型列表], 返回类型]`

表示可调用对象（函数、lambda 等）。例如：

```
def apply(func: Callable[[int, str], bool], x: int, y: str) -> bool:
    return func(x, y)
```

`Callable[[int, str], bool]` 表示一个接受两个参数（int 和 str）并返回 bool 的函数。

## 三、自定义类型

你可以将自定义类名直接用作类型标注。例如：

```
class Block:
    def __init__(self, lines: List[Tuple[int, str]]):
        self.lines = lines
```

这里的 `lines: List[Tuple[int, str]]` 表示 `lines` 是一个列表，列表中的每个元素是一个元组，元组的第一个元素是整数（行号），第二个元素是字符串（文本内容）。

## 四、类型别名

为了简化复杂类型，可以定义别名：

```
LineInfo = Tuple[int, str]  # 行号+文本
BlockLines = List[LineInfo]

class Block:
    def __init__(self, lines: BlockLines):
        self.lines = lines
```

## 六、类型标注的实际作用

1. **IDE 智能提示**：PyCharm、VS Code 等可以根据类型提示自动补全方法和属性。
2. **静态类型检查**：使用 mypy、pyright 等工具可以在运行前发现类型错误。
3. **文档作用**：无需阅读代码即可了解参数和返回值的预期类型。

**注意**：Python 的类型提示不影响运行时行为，即使传入了不符合标注的值也不会报错（除非你显式断言）。它们只是“提示”。

## 七、常用技巧

- 如果某个参数可以是多种类型，使用 `Union[str, int]`。
- 如果某个参数可以是任意类型，使用 `Any`。
- 如果某个参数是字典，使用 `Dict[key类型, value类型]`，例如 `Dict[str, int]`。
- 如果某个参数是集合，使用 `Set[类型]`。
