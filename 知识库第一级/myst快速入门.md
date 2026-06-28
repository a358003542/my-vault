
## 项目初始化

```
myst init --gh-pages
```

  这样初始化的项目新增了github action，方便快速开启项目对应的github pages。

## myst.yml配置
一个简单的样例如下：

```
version: 1
project:
  title: Python编程学习
  authors: [Wander]
  github: https://github.com/a358003542/learning-python-programming
  toc:
    - file: main.md
    - title: python基础
      children:
        - file: .\python基础\python基础00准备.ipynb
    - title: python进阶
      children:
        - file: .\python进阶\python进阶01可迭代对象.ipynb
    - title: python数据处理
      children:
        - file: .\python数据处理\excel和python交互.ipynb
        - file: .\python数据处理\numpy基础.ipynb
    - file: python重要知识参考.ipynb
    - file: python备用知识.md
site:
  template: book-theme
```

更多相关配置参阅 [MyST Markdown Tools - MyST Markdown](https://mystmd.org/guide)。
## 本地使用

```
myst start
```

## 本地build

```
myst build --html
```

如果不是直接使用github pages，而是挂载静态文件的方式可能需要这个。