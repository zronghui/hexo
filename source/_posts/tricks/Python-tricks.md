---
title: Python tricks
date: 2020-01-15 16:36:18
categories:
- Tricks
- Python
tags:
- Tricks
- Python
---

[toc]

<!--more-->
# 2020 年 1 月 15 日(星期三)

[Python技巧小贴士 - 51CTO.COM](https://zhuanlan.51cto.com/art/201910/604777.htm)

## 字符串一次性执行多个 replace

```Python
user_input = "This\nstring has\tsome whitespaces...\r\n" 
 
character_map = { 
    ord('\n') : ' ', 
    ord('\t') : ' ', 
    ord('\r') : None 
} 
user_input.translate(character_map)  # This string has some whitespaces...  
```

## 迭代器切片(Slice)

如果对迭代器进行切片操作，会返回一个「TypeError」，提示生成器对象没有下标，但是我们可以用一个简单的方案来解决这个问题：

```Python
import itertools 
 
s = itertools.islice(range(50), 10, 20)
for i in s:
    ...
```

## 跳过可迭代对象某些元素

比如跳过文件的注释代码

```python
import itertools 
 
for line in itertools.dropwhile(lambda line: line.startswith("//"), string_from_file.split("\n")): 
    print(line) 
```

## 实现上下文管理

```Python
from contextlib import contextmanager 
 
@contextmanager 
def tag(name): 
    print(f"<{name}>") 
    yield 
    print(f"</{name}>") 
 
with tag("h1"): 
    print("This is Title.") 
```

## 控制可以/不可以导入什么

在 Python 中，所有成员都会被导出(除非我们使用了「__all__」)：

```Python
def foo(): 
    pass 
 
def bar(): 
    pass 
 
__all__ = ["bar"] 
```

在上面这段代码中，我们知道只有「bar」函数被导出了。同样，我们可以让「__all__」为空，这样就不会导出任何东西，当从这个模块导入的时候，会造成「AttributeError」。

## 实现所有比较运算符的简单方法

为一个类实现所有的比较运算符(如 __lt__ , __le__ , __gt__ , __ge__)是很繁琐的。有更简单的方法可以做到这一点吗？这种时候，「functools.total_ordering」就是一个很好的帮手：

```Python
from functools import total_ordering 
 
@total_ordering 
class Number: 
    def __init__(self, value): 
        self.value = value 
 
    def __lt__(self, other): 
        return self.value < other.value 
 
    def __eq__(self, other): 
        return self.value == other.value 
 
print(Number(20) > Number(3)) 
print(Number(1) < Number(5)) 
print(Number(15) >= Number(15)) 
print(Number(10) <= Number(2)) 
```

用「total_ordering」装饰器简化实现对类实例排序的过程。我们只需要定义「__lt__」和「__eq__」就可以了

## 限制「CPU」和内存使用量

？
如果不是想优化程序对内存或 CPU 的使用率（how），而是想直接将其限制为某个确定的数字，Python 也有一个对应的库可以做到：

```Python
import signal 
import resource 
import os 
 
# To Limit CPU time 
def time_exceeded(signo, frame): 
    print("CPU exceeded...") 
    raise SystemExit(1) 
 
def set_max_runtime(seconds): 
    # Install the signal handler and set a resource limit 
    soft, hard = resource.getrlimit(resource.RLIMIT_CPU) 
    resource.setrlimit(resource.RLIMIT_CPU, (seconds, hard)) 
    signal.signal(signal.SIGXCPU, time_exceeded) 
 
# To limit memory usage 
def set_max_memory(size): 
    soft, hard = resource.getrlimit(resource.RLIMIT_AS) 
    resource.setrlimit(resource.RLIMIT_AS, (size, hard)) 
```