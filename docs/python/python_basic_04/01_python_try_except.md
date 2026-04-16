# 01 异常处理

---

## 1.0 异常处理核心概念

### 1.0.1 基本语法

```py
try:
    # 可能引发异常的代码
    risky_operation()
except SpecificException:
    # 处理特定异常
    handle_error()
except AnotherException as e:
    # 处理另一个异常，并访问异常对象
    print(f"错误: {e}")
else:
    # 没有异常时执行
    print("操作成功")
finally:
    # 无论是否异常都会执行
    cleanup_resources()
```

### 1.0.2 常见异常类型

1. `ValueError` - 值错误
2. `TypeError` - 类型错误
3. `IndexError` - 索引错误
4. `KeyError` - 键错误
5. `FileNotFoundError` - 文件不存在
6. `ZeroDivisionError` - 除零错误

### 1.0.3 最佳实践

1. 具体异常优先：先捕获具体异常，再捕获通用异常
2. 避免静默失败：至少要记录异常信息
3. 资源清理：使用 with 语句或 finally 块
4. 有意义的错误信息：帮助调试和理解
5. 不要滥用异常：异常应用于异常情况，而非正常流程控制

### 1.0.4 高级特性

1. 自定义异常：创建领域特定的异常类
2. 异常链：保留原始异常信息
3. 上下文管理器：自动资源管理
4. 异常日志记录：生产环境必备

异常处理是编写健壮、可靠 Python 程序的关键技能！

## 1.1 异常的定义及作用

### 1.1.1 异常的定义

异常（Exception） 是 Python 中表示程序运行期间错误或异常情况的对象。当程序遇到无法正常执行的状况（如逻辑错误、无效输入、资源不可用等），会抛出一个异常对象。

为什么需要异常处理？
程序运行时可能遇到意外，默认情况下，程序会直接崩溃并显示错误信息，让程序优雅地处理错误，继续运行或友好提示。

### 1.1.2 异常的作用

> 防止崩溃，提升用户体验， 错误分类处理，精准定位。资源释放，保证稳定性。

1. 程序在发生异常时，不会立即崩溃，而是会根据我们设定的异常处理机制，执行相应的代码，从而保证程序的健壮性。
2. 异常处理机制可以帮助我们更好地调试程序，通过捕获异常，我们可以知道程序在运行过程中出现了什么问题，从而方便我们进行修复。

## 1.2 常见异常类型

| 常见异常类型        | 触发场景           | 例子                 |
| ------------------- | ------------------ | -------------------- |
| `ZeroDivisionError` | 除以零             | `10 / 0`             |
| `FileNotFoundError` | 文件不存在         | `open("xx.txt")`     |
| `ValueError`        | 类型转换失败       | `int("abc")`         |
| `IndexError`        | 列表索引越界       | `索引越界`           |
| `KeyError`          | 访问字典不存在的键 | `dict["不存在的键"]` |
| `NameError`         | 未定义变量         | `undefined_var`      |
| `ImportError`       | 导入模块失败       | `导入未知模块`       |

## 1.3 异常处理基础

### 1.3.1 基本 try-except 结构

```python
# 1. 基本try-except结构
try:
    result = 10 / 0
    print(f"结果: {result}")
except ZeroDivisionError:
    print("错误：不能除以零！")
```

### 1.3.2 捕获多个异常

```python
# 2. 捕获多个异常
try:
    result = 10 / 0
    print(f"结果: {result}")
except (ZeroDivisionError, ValueError):
    print("错误：不能除以零！")
#=========================================
try:
    num = int("abc")
    result = 10 / num
except ValueError:
    print("错误：无法将字符串转换为整数！")
except ZeroDivisionError:
    print("错误：除数不能为零！")
```

### 1.3.3 捕获所有异常

```python
# 3. 捕获所有异常（不推荐在生产代码中使用）
try:
    undefined_variable = some_undefined_var
except Exception as e:
    print(f"捕获到异常: {type(e).__name__}: {e}")
```

### 1.3.4 else 和 finally

else 和 finally 是 try-except 语句的可选部分。

- `else`：当 try 块中的代码没有引发异常时，执行 `else` 块中的代码。
- `finally`：无论是否发生异常，`finally` 块中的代码都会执行。通常用于释放资源。

```python
# 4. else 和 finally
try:
    result = 10 / 2
    print(f"结果: {result}")
except ZeroDivisionError:
    print("错误：不能除以零！")
else:
    print("没有发生异常")
finally:
    print("无论是否发生异常，都会执行")
```

### 1.3.5 自定义异常

自定义异常类需要继承自 `Exception` 类，并可以定义自己的属性和方法。

自定义异常是开发者根据需求自己定义的一种异常类型，它继承自 Python 的内置 Exception 类或其子类，通过自定义异常，可以更好地描述特定场景下的错误。

如何定义一个自定义异常？
创建一个类，并继承 Exception 或其子类，可以在类中添加构造函数（`__init__`），用于设置错误信息。

基本语法：

```python
# 定义一个自定义异常类
class MyCustomError(Exception):
    # 为异常定义初始化方法，接收错误信息。
    def __init__(self, message="默认错误信息"):
        self.message = message
        # 调用父类的构造函数，传递错误信息。
        super().__init__(self.message)
```

```python
# 1. 自定义异常类
class MyCustomError(Exception):
    def __init__(self, message="默认错误信息
```

```python
# 1. 自定义异常类
class InsufficientFundsError(Exception):
    """余额不足异常"""
    def __init__(self, balance, amount):
        self.balance = balance
        self.amount = amount
        super().__init__(f"余额不足！当前余额: {balance}，需要: {amount}")

class InvalidAmountError(Exception):
    """无效金额异常"""
    pass
# 2. 使用自定义异常
class BankAccount:
    def __init__(self, balance=0):
        self.balance = balance

    def withdraw(self, amount):
        if amount <= 0:
            raise InvalidAmountError("取款金额必须大于0")
        if amount > self.balance:
            raise InsufficientFundsError(self.balance, amount)

        self.balance -= amount
        print(f"取款成功！取款: {amount}, 余额: {self.balance}")

# 测试自定义异常
account = BankAccount(1000)

try:
    account.withdraw(1500)  # 这会引发余额不足异常
except InsufficientFundsError as e:
    print(f"自定义异常: {e}")

try:
    account.withdraw(-100)  # 这会引发无效金额异常
except InvalidAmountError as e:
    print(f"自定义异常: {e}")
```

## 1.4 异常处理模式

### 1.4.1 具体异常优先

具体异常优先是指在捕获异常时，先捕获具体的异常类型，再捕获更通用的异常类型。这样可以避免捕获到一些不应该被捕获的异常。

```python
# 1. 具体异常优先
def read_file_content(filename):
    try:
        with open(filename, 'r', encoding='utf-8') as file:
            return file.read()
    except FileNotFoundError:
        return f"文件 {filename} 不存在"
    except PermissionError:
        return f"没有权限读取文件 {filename}"
    except UnicodeDecodeError:
        return "文件编码错误"
    except Exception as e:
        return f"读取文件时发生未知错误: {e}"
```

### 1.4.2 使用异常进行流程控制（谨慎使用）

使用异常进行流程控制是一种不推荐的做法，因为它会使代码难以理解和维护。

```python
# 2. 使用异常进行流程控制（谨慎使用）
def safe_divide(a, b):
    try:
        return a / b
    except (ZeroDivisionError, TypeError):
        return None
```

### 1.4.3 异常链

异常链（Exception chaining）是指在捕获一个异常后，再抛出一个新的异常，同时保留原始异常的信息。

可以通过使用 `raise ... from ...` 语法来创建异常链。

```python
# 3. 异常链
def process_data(data):
    try:
        return int(data) * 2
    except ValueError as e:
        raise RuntimeError(f"处理数据失败: {data}") from e # 异常链

# 测试异常链
try:
    process_data("abc")
except RuntimeError as e:
    print(f"异常链: {e}")
    print(f"原始异常: {e.__cause__}")
```

### 1.4.4 手动引发异常

手动引发异常指的是通过 raise 关键字，在特定条件下主动触发一个异常，这有助于在遇到不符合预期的情况时及时中断程序流程，并采取相应的措施。

语法：`raise ExceptionType("异常信息")`
其中，ExceptionType 是你想要抛出的异常类型（如 ValueError, TypeError 等），"异常信息"是可选的描述信息。

```python
def check_adult():
    try:
        # 获取用户输入的年龄
        age = int(input("请输入您的年龄："))
        # 判断是否成年
        if age < 18:
            # raise 引发 ValueError 异常 手动触发异常
            raise ValueError("你还未成年")
    except ValueError as e:
        # 捕获 ValueError 异常并处理
        print(f"输入错误：{e}")
    else:
        # 没有发生异常，执行 else 块中的代码
        print("你已成年了")
    finally:
        # 无论发生与否，都会执行 finally 块中的代码
        print("程序执行完毕。")
# 测试函数
check_adult()
```

## 1.5 上下文管理器

上下文管理器是一种特殊的对象，它定义了在进入和退出某个代码块时应该执行的设置和清理操作。上下文管理器通常用于管理资源，如文件、网络连接等。

上下文管理器需要实现 `__enter__` 和 `__exit__` 方法。

### 1.5.1 使用 with 语句自动管理资源

使用 with 语句可以自动管理资源，包括打开和关闭文件、释放锁等操作。

```python
# 1. 使用with语句自动管理资源
def read_file_safely(filename):
    try:
        with open(filename, 'r', encoding='utf-8') as file:
            content = file.read()
            print(f"文件内容: {content[:50]}...")  # 只显示前50个字符
            return content
    except FileNotFoundError:
        print(f"文件 {filename} 不存在")
        return None
    except Exception as e:
        print(f"读取文件时发生错误: {e}")
        return None
```

### 1.5.2 自定义上下文管理器

自定义上下文管理器需要实现 `__enter__` 和 `__exit__` 方法。

```python
# 2. 自定义上下文管理器
class Timer:
    def __enter__(self):
        import time
        self.start = time.time()
        return self

    def __exit__(self, exc_type, exc_val, exc_tb):
        import time
        self.end = time.time()
        print(f"代码执行时间: {self.end - self.start:.4f} 秒")
        # 返回False让异常继续传播，返回True则抑制异常
        return False

# 使用自定义上下文管理器
with Timer():
    # 模拟耗时操作
    import time
    time.sleep(1)
    print("耗时操作完成")
```

### 1.5.3 使用 contextlib 模块

`contextlib` 模块提供了一些有用的上下文管理器，如 `contextlib.contextmanager` 装饰器。

```python
# 3. 使用contextlib创建上下文管理器
from contextlib import contextmanager

@contextmanager
def temporary_change(obj, attr, temp_value):
    """临时修改对象属性"""
    original_value = getattr(obj, attr)
    setattr(obj, attr, temp_value)
    try:
        yield
    finally:
        setattr(obj, attr, original_value)

class Config:
    debug_mode = False

config = Config()
print(f"修改前: debug_mode = {config.debug_mode}")

with temporary_change(config, 'debug_mode', True):
    print(f"临时修改: debug_mode = {config.debug_mode}")

print(f"修改后: debug_mode = {config.debug_mode}")
```

## 1.6 实践示例

### 1.6.1 用户输入验证

用户输入验证是常见的需求，可以使用 try-except 块来捕获和处理输入错误。

```python
# 1. 用户输入验证
def get_valid_number(prompt):
    while True:
        try:
            value = float(input(prompt))
            return value
        except ValueError:
            print("错误：请输入有效的数字！")

# 测试用户输入
# number = get_valid_number("请输入一个数字: ")
# print(f"你输入的数字是: {number}")
```

### 1.6.2 文件操作异常处理

文件操作时，可能会遇到文件不存在、权限不足、编码错误等问题。可以使用 try-except 块来捕获和处理这些异常。

```python
# 2. 文件操作异常处理
def safe_file_operations():
    try:
        # 尝试读取文件
        with open("data.txt", "r", encoding="utf-8") as file:
            data = file.readlines()

        # 处理数据
        processed_data = []
        for i, line in enumerate(data, 1):
            try:
                numbers = [float(x) for x in line.strip().split()]
                processed_data.append(numbers)
            except ValueError as e:
                print(f"第{i}行数据格式错误: {e}")

        return processed_data

    except FileNotFoundError:
        print("数据文件不存在，使用默认数据")
        return [[1, 2, 3], [4, 5, 6]]
    except PermissionError:
        print("没有文件读取权限")
        return []
    except Exception as e:
        print(f"处理文件时发生未知错误: {e}")
        return []
```

### 1.6.3 API 调用异常处理

API 调用可能会遇到网络错误、超时、认证失败等问题。可以使用 try-except 块来捕获和处理这些异常。

```python
# 3. API调用异常处理
def api_call_with_retry(url, retries=3):
    import requests
    import time

    for attempt in range(retries):
        try:
            response = requests.get(url, timeout=5)
            response.raise_for_status()  # 如果状态码不是200，抛出HTTPError
            return response.json()
        except requests.exceptions.Timeout:
            print(f"请求超时，第{attempt + 1}次重试...")
        except requests.exceptions.ConnectionError:
            print(f"连接错误，第{attempt + 1}次重试...")
        except requests.exceptions.HTTPError as e:
            print(f"HTTP错误: {e}")
            break  # HTTP错误通常不需要重试
        except Exception as e:
            print(f"未知错误: {e}")
            break

        if attempt < retries - 1:
            time.sleep(2 ** attempt)  # 指数退避

    print("所有重试尝试都失败了")
    return None
```

### 1.6.4 数据库操作异常处理

数据库操作异常处理是常见的任务，可以使用 try-except 块来捕获和处理数据库连接错误、查询错误等问题。

```python
# 4. 数据库操作异常处理
def database_operations():
    try:
        # 模拟数据库操作
        # connection = connect_to_database()
        # cursor = connection.cursor()
        # cursor.execute("SELECT * FROM users")
        print("执行数据库查询...")
        # 模拟一个数据库错误
        raise Exception("数据库连接超时")

    except Exception as e:
        print(f"数据库操作失败: {e}")
        # 记录日志、回滚事务等
        return None
    finally:
        print("清理数据库资源...")
        # 关闭连接等清理工作
```

### 1.6.5 异常处理小结

1. 具体异常优先: 先捕获具体异常，再捕获通用异常
2. 避免空 except 块: 至少要记录或处理异常
3. 使用异常链: 保留原始异常信息
4. 资源清理: 使用 with 语句或 finally 块确保资源释放
5. 不要用异常做流程控制: 异常应用于异常情况，而非正常逻辑
6. 提供有意义的错误信息: 帮助调试和用户理解
7. 记录异常: 在生产环境中记录异常信息
8. 自定义异常: 为特定领域创建有意义的异常类型

```py
# 好的实践示例
def good_practice_example(filename):
    import logging

    try:
        with open(filename, 'r') as file:
            return file.read()

    except FileNotFoundError:
        logging.error(f"文件不存在: {filename}")
        return None
    except PermissionError:
        logging.error(f"没有读取权限: {filename}")
        return None
    except Exception as e:
        logging.error(f"读取文件时发生未知错误: {e}")
        return None

# 不好的实践示例
def bad_practice_example(filename):
    try:
        with open(filename, 'r') as file:
            return file.read()
    except:  # 空的except，捕获所有异常但不处理
        pass  # 静默失败，难以调试
```

## 1.7 异常调试技巧

### 1.7.1 堆栈跟踪

堆栈跟踪是调试异常的关键信息，可以帮助你了解异常发生的位置和调用链。

```py
def detailed_exception_info():
    try:
        # 模拟一个复杂操作
        data = {"key": "value"}
        print(data["nonexistent_key"])

    except Exception as e:
        print("=== 异常详细信息 ===")
        print(f"异常类型: {type(e).__name__}")
        print(f"异常信息: {e}")
        print(f"异常参数: {e.args}")

        # 获取堆栈跟踪
        import traceback
        print("堆栈跟踪:")
        traceback.print_exc()

detailed_exception_info()
```

### 1.7.2 日志记录 logging

`logging` 模块可以用来记录异常信息，以便于调试和问题追踪。

```python
# 使用logging记录异常
def log_exception():
    import logging

    logging.basicConfig(level=logging.ERROR)

    try:
        result = 10 / 0
    except Exception as e:
        logging.exception("发生除零错误")  # 这会自动记录堆栈跟踪

log_exception()
```

### 1.7.3 pdb 调试器

`pdb` 是 Python 的内置调试器，可以用来逐步执行代码并检查变量状态。

```python
# 使用pdb调试
def debug_with_pdb():
    import pdb

    try:
        result = 10 / 0
    except Exception:
        pdb.set_trace()  # 在这里设置断点
        print("继续执行")

debug_with_pdb()
```

### 1.7.4 IDE 调试器

大多数现代 IDE（如 PyCharm、VS Code 等）都内置了调试器，可以用来设置断点、单步执行代码、查看变量状态等。

````python
# 使用IDE调试
def debug_with_ide():
    try:
        result = 10 / 0
    except Exception:
        import pdb; pdb.set_trace()  # 在这里设置断点
```        print("继续执行")

debug_with_ide()
````

## 1.8 总结

异常处理是 Python 编程中非常重要的一部分，它可以帮助你编写更健壮、更可靠的代码。通过学习如何使用 try-except 块来捕获和处理异常，你可以更好地应对程序中的错误和异常情况。同时，了解异常调试技巧可以帮助你更快地定位和解决问题。

常处理总结:

1. try-except: 捕获和处理异常
2. else: 无异常时执行
3. finally: 总是执行，用于资源清理
4. raise: 主动抛出异常
5. 自定义异常: 创建领域特定的异常类型
6. with 语句: 自动资源管理
7. 具体异常优先: 提高代码的可维护性
