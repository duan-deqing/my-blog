# 05 函数

---

## 5.0 函数核心特点

1. 函数定义

```python
def 函数名(参数):
    """文档字符串"""
    函数体
    return 返回值
```

2. 参数类型

   - 位置参数 - 按顺序传递
   - 默认参数 - 提供默认值
   - 关键字参数 - 按参数名传递
   - 可变参数 - \*args 接收元
   - 可变关键字参数 - \*\*kwargs 接收字典

3. 返回值

   - 可以返回单个值或多个值（实际上是元组）
   - 没有 return 语句时返回 None
   - 可以返回任何数据类型

4. 高级特性

   - Lambda 函数 - 匿名函数，简洁
   - 装饰器 - 增强函数功能
   - 生成器 - 使用 yield，节省内存
   - 递归 - 函数调用自身

5. 最佳实践
   - 单一职责原则
   - 有意义的函数名
   - 适当的函数长度
   - 完整的文档字符串
   - 类型注解提高可读性

函数是 Python 编程的基础，良好的函数设计是写出高质量代码的关键！

## 5.1 函数基础

### 5.1.1 简单无参数函数

无参数函数是最简单的函数，它不接受任何参数，也不返回任何值。

```python
# 简单的无参数函数
def greet():
    print("Hello, World!")
```

### 5.1.1 函数参数

带参数的函数可以接受输入，并返回输出。参数可以是位置参数或关键字参数。

```python
# 带参数的函数
def greet_person(name):
    print(f"Hello, {name}!")
```

### 5.1.3 带返回值的函数

带返回值的函数可以返回一个值或多个值。返回值可以是任何数据类型。

```python
# 带返回值的函数
def add_numbers(a, b):
    return a + b
```

### 5.1.4 调用函数

函数调用是使用函数名和参数来执行函数的过程。

```python
greet()
greet_person("Alice")
result = add_numbers(5, 3)
print(f"5 + 3 = {result}")
```

## 5.2 函数参数

### 5.2.1 位置参数

位置参数是按照函数定义的顺序传递的参数。

```python
def greet_person(name, age):
    print(f"Hello, {name}! You are {age} years old.")

# 1. 位置参数
def introduce(name, age, city):
    print(f"我叫{name}，今年{age}岁，来自{city}")

introduce("张三", 25, "北京")  # 必须按顺序传参
```

### 5.2.2 默认参数

默认参数是函数定义中带有默认值的参数。

```python
# 2. 默认参数
def greet_person(name, greeting="Hello"):
    print(f"{greeting}, {name}!")

greet_person("李四")              # 使用默认问候语
greet_person("王五", "Hi")        # 自定义问候语
```

### 5.2.3 关键字参数

关键字参数是按照参数名传递的参数。

```python
# 3. 关键字参数
def create_person(name, age, city, job="工程师"):
    print(f"姓名:{name}, 年龄:{age}, 城市:{city}, 职业:{job}")

create_person(age=30, city="上海", name="赵六")  # 不按顺序
create_person("钱七", job="医生", age=35, city="广州")
```

### 5.2.4 可变参数 `*args`

可变参数是使用 `*args` 或 `**kwargs` 传递的参数。

```python
# 4. 可变参数 *args
def sum_numbers(*args):
    print(f"参数: {args}")
    return sum(args)

print(f"求和1: {sum_numbers(1, 2, 3)}")
print(f"求和2: {sum_numbers(1, 2, 3, 4, 5)}")
```

### 5.2.5 可变关键字参数 `**kwargs`

可变关键字参数是使用 `**kwargs` 传递的参数。

```python
# 5. 可变关键字参数 **kwargs
def print_info(**kwargs):
    for key, value in kwargs.items():
        print(f"{key}: {value}")

print_info(name="张三", age=25, city="北京")
print_info(title="Python", version=3.9)
```

## 5.3 函数返回值

---

### 5.3.1 返回单个值

函数可以返回单个值，可以是任何数据类型。

```python
def square(x):
    return x * x
```

### 5.3.2 返回多个值 （实际返回的是元组）

函数可以返回多个值，实际上是返回一个元组。

```python
def calculate(x, y):
    return x + y, x - y, x * y, x / y
```

### 5.3.3 返回复杂数据结构

函数可以返回复杂数据结构，如列表、字典、类实例等。

```python
def get_student_info(name, age):
    return {
        'name': name,
        'age': age,
        'adult': age >= 18
    }
```

### 5.3.4 无返回值

函数可以没有返回值，默认返回 None。

```python
# 无返回值函数（返回None）
def print_hello(name):
    print(f"Hello, {name}!")
    # 没有return语句，默认返回None
```

### 5.3.5 返回值类型注解

函数返回值类型注解可以提高代码的可读性。

```python
def add_numbers(a: int, b: int) -> int:
    return a + b
```

## 5.4 函数作用域

函数作用域是指函数内部可以访问的变量范围。可以分为局部作用域和全局作用域。

- 局部作用域是指在函数内部定义的变量，只能在函数内部访问。
- 全局作用域是指在函数外部定义的变量，可以在函数内部和外部访问。

- 局部变量：在函数内部定义的变量，只能在函数内部访问。
- 全局变量：在函数外部定义的变量，可以在函数内部和外部访问。

### 5.4.1 局部变量

局部变量是函数内部定义的变量，只能在函数内部访问。

```python
def my_function():
    local_var = 10
    print(local_var)

my_function()
# print(local_var)  # NameError: name 'local_var' is not defined
```

### 5.4.2 全局变量

全局变量是函数外部定义的变量，可以在函数内部和外部访问。

```python
global_var = 20

def my_function():
    print(global_var)

my_function()
print(global_var)
```

### 5.4.3 闭包

闭包是指函数内部定义的函数可以访问外部函数的变量。

```python
# 闭包示例
def outer_function(x):
    def inner_function(y):
        return x + y  # inner_function可以访问outer_function的变量
    return inner_function
closure = outer_function(10)
print(f"闭包示例: {closure(5)}")  # 输出15
```

## 5.5 函数高级特性

---

### 5.4.1 Lambda 函数（匿名函数）

Lambda 函数是匿名函数，使用 lambda 关键字定义。
基本格式：`lambda 参数: 表达式`

```python
# 1. 基本的lambda函数
square = lambda x: x ** 2
print(f"平方lambda: {square(5)}")

# 2. 多个参数的lambda
add = lambda a, b: a + b
print(f"加法lambda: {add(3, 4)}")
# 3. 在排序中使用lambda
students = [
    {'name': '张三', 'score': 85},
    {'name': '李四', 'score': 92},
    {'name': '王五', 'score': 78}
]

# 按分数排序
sorted_students = sorted(students, key=lambda x: x['score'], reverse=True)
print("按分数排序:")
for student in sorted_students:
    print(f"  {student['name']}: {student['score']}")

# 4. 在map中使用lambda
numbers = [1, 2, 3, 4, 5]
squared = list(map(lambda x: x ** 2, numbers))
print(f"map + lambda: {squared}")

# 5. 在filter中使用lambda
even_numbers = list(filter(lambda x: x % 2 == 0, numbers))
print(f"filter + lambda: {even_numbers}")
```

### 5.4.2 装饰器

装饰器是修改函数行为的函数。装饰器使用 `@` 符号定义。
基本格式：`@装饰器名 def 函数名():`

#### 5.4.2.1 简单的装饰器

```python
# 1. 简单的装饰器
def my_decorator(func):
    def wrapper():
        print("函数执行前...")
        func()
        print("函数执行后...")
    return wrapper

@my_decorator # 使用装饰器
def say_hello():
    print("Hello!")
say_hello()
```

#### 5.4.2.2 带参数的装饰器

```python
# 带参数的装饰器
def repeat(n):
    def decorator(func):
        def wrapper(*args, **kwargs):
            for i in range(n):
                print(f"第{i+1}次执行:")
                result = func(*args, **kwargs)
            return result
        return wrapper
    return decorator

@repeat(3) # 使用装饰器
def greet(name):
    print(f"Hello, {name}!")

greet("Alice")
```

#### 5.4.2.3 类装饰器

类装饰器是使用类定义的装饰器。
基本格式：`class 装饰器名: def __call__(self, func):`

```python
# 类装饰器
class Timer:
    def __init__(self, func):
        self.func = func

    def __call__(self, *args, **kwargs):
        import time
        start_time = time.time()
        result = self.func(*args, **kwargs)
        end_time = time.time()
        print(f"函数执行时间: {end_time - start_time:.4f}秒")
        return result

@Timer # 使用装饰器
def slow_function():
    import time
    time.sleep(1)
    return "完成"

slow_function()
```

### 5.4.3 生成器函数

生成器函数是使用 `yield` 关键字定义的函数，可以生成一个迭代器。
基本格式：`def 函数名(): yield 表达式`

```python
# 简单的生成器函数
def count_up_to(n):
    """计数到n的生成器"""
    count = 1
    while count <= n:
        yield count
        count += 1

# 使用生成器
print("生成器示例:")
for number in count_up_to(5):
    print(f"  {number}")

# 生成器表达式
squares = (x**2 for x in range(1, 6))
print(f"生成器表达式: {list(squares)}")

# 无限生成器
def fibonacci():
    """斐波那契数列生成器"""
    a, b = 0, 1
    while True:
        yield a
        a, b = b, a + b

fib = fibonacci()
print("斐波那契数列:")
for i in range(10):
    print(f"  {next(fib)}", end=" ")
print()
```

### 5.4.4 递归函数

递归函数是调用自身的函数。
递归函数通常用于解决具有重复子问题的任务，如阶乘、斐波那契数列等。

```python
# 阶乘函数
def factorial(n):
    """计算阶乘的递归函数"""
    if n == 0 or n == 1:
        return 1
    else:
        return n * factorial(n - 1)

# 斐波那契数列
def fib_recursive(n):
    """计算斐波那契数列的递归函数"""
    if n <= 1:
        return n
    else:
        return fib_recursive(n - 1) + fib_recursive(n - 2)

print(f"5的阶乘: {factorial(5)}")
print(f"斐波那契第10项: {fib_recursive(10)}")

# 递归目录遍历
import os
def list_files(startpath):
    """递归列出目录中的所有文件"""
    for root, dirs, files in os.walk(startpath):
        level = root.replace(startpath, '').count(os.sep)
        indent = ' ' * 2 * level
        print(f"{indent}{os.path.basename(root)}/")
        subindent = ' ' * 2 * (level + 1)
        for file in files:
            print(f"{subindent}{file}")
```

### 5.4.5 函数注解

函数注解是用于描述函数参数和返回值的类型信息。
基本格式：`def 函数名(参数: 类型) -> 返回值类型:`

```python
def greet(name: str, age: int = 18) -> str:
    """
    带类型注解的函数

    Args:
        name: 姓名
        age: 年龄，默认为18

    Returns:
        问候字符串
    """
    return f"Hello, {name}! You are {age} years old."
```

#### 5.4.5.1 查看函数注解

```python
# 查看函数注解
print(f"greet函数的注解: {greet.__annotations__}")
```

#### 5.4.5.2 调用带注解的函数

```python
result = greet("张三", 25)
print(result)
```

#### 5.4.5.3 复杂的类型注解

```python
# 复杂的类型注解
from typing import List, Dict, Tuple, Optional

def process_data(
    numbers: List[int],
    config: Dict[str, str],
    threshold: Optional[float] = None
) -> Tuple[bool, str]:
    """复杂的类型注解示例"""
    if threshold and sum(numbers) > threshold:
        return True, "超过阈值"
    else:
        return False, "正常"
```

## 5.6 实践示例

---

### 5.6.1 数据验证函数 - 验证邮箱格式

```python
def validate_email(email: str) -> bool:

    import re
    pattern = r'^[a-zA-Z0-9._%+-]+@[a-zA-Z0-9.-]+\.[a-zA-Z]{2,}$'
    return bool(re.match(pattern, email))

emails = ["test@example.com", "invalid-email", "user@domain.org"]
for email in emails:
    valid = validate_email(email)
    print(f"邮箱 {email}: {'有效' if valid else '无效'}")
```

### 5.6.2 文件操作函数 - 读取文件的所有行

```python
def read_file_lines(filename: str) -> List[str]:
    try:
        with open(filename, 'r', encoding='utf-8') as file:
            return [line.strip() for line in file.readlines()]
    except FileNotFoundError:
        print(f"文件 {filename} 不存在")
        return []
```

### 5.6.3 计算统计函数 - 计算描述性统计

```python
def calculate_statistics(numbers: List[float]) -> Dict[str, float]:
    """计算描述性统计"""
    if not numbers:
        return {}

    return {
        'mean': sum(numbers) / len(numbers),
        'max': max(numbers),
        'min': min(numbers),
        'count': len(numbers)
    }

data = [1.5, 2.7, 3.1, 4.8, 2.3]
stats = calculate_statistics(data)
print(f"数据统计: {stats}")
```

### 5.6.4 配置处理函数 - 创建配置字典

```python
def create_config(**kwargs) -> Dict:
    default_config = {
        'debug': False,
        'port': 8000,
        'host': 'localhost'
    }
    default_config.update(kwargs)
    return default_config

config = create_config(debug=True, port=8080)
print(f"配置: {config}")
```

## 5.7 总结

---

本章介绍了 Python 函数的基本概念、定义、参数、返回值、作用域、装饰器、生成器函数、递归函数和函数注解。
通过实践示例，展示了如何使用函数来处理数据验证、文件操作、计算统计和配置处理等任务。
这些内容是 Python 编程中非常重要的基础，可以帮助你更好地理解和应用函数。

1. 使用 def 关键字定义函数
2. 支持位置参数、默认参数、关键字参数、可变参数
3. 可以返回单个值或多个值
4. 有局部作用域，使用 global 访问全局变量
5. Lambda 函数是匿名函数，适合简单操作
6. 装饰器用于增强函数功能
7. 生成器使用 yield 返回迭代器
8. 递归函数调用自身解决问题
9. 函数注解提供类型提示

## 5.8 练习

### 5.8.1 练习 1 : 编写一个打招呼的函数并调用它

1. 编写一个名为 greet 的函数，接收一个参数 name，打印问候语。
2. 如果没有提供参数，则默认向“world”问好，体现默认参数的使用。
3. 通过调用 greet()函数和 greet("Alice)，展示默认参数和指定参数的调用方法。

### 5.8.2 练习 2 : 编写一个简单的图书管理系统

题目描述
假设你正在为一家图书馆开发一个简单的图书管理系统。你需要编写几个函数来帮助管理员管理书籍信息。具体要求如下：

1. 添加书籍：编写一个名为 add_book 的函数，该函数接收书名（title）、作者（author）和数量（quantity）作为关键字参数，并将这些信息存储在一个字典中。如果数量未提供，默认设置为 1。
2. 显示所有书籍：编写一个名为 display_books 的函数，该函数没有参数，用于打印当前所有书籍的信息。
3. 借阅书籍：编写一个名为 borrow_book 的函数，该函数接收书名（title）作为默认参数，并减少对应书籍的数量。如果书籍不存在或库存不足，则打印相应提示信息。
4. 归还书籍：编写一个名为 return_book 的函数，该函数接收书名（title）作为位置参数，并增加对应书籍的数量。如果书籍不存在，则添加该书籍并设置数量为 1。
