# 02 模块（module）

---

## 2.0 模块核心概念

### 2.0.1 模块的定义

1. 一个 `.py` 文件就是一个模块
2. 包含函数、类、变量等 Python 代码
3. 通过 import 语句导入使用

### 2.0.2 导入方式

1. `import 模块名`
2. `from 模块名 import 函数名/变量名/类名`
3. `from 模块名 import *`
4. `import 模块名 as 别名`

```py
# 导入整个模块
import module_name

# 导入特定内容
from module_name import function_name

# 起别名
import module_name as alias
from module_name import function_name as fn_alias
```

### 2.0.3 包（Package）

1. 包含 `__init__.py` 文件的目录
2. 组织相关的模块
3. 支持多级嵌套

### 2.0.4 重要概念

1. `__name__`: 判断模块是被导入还是直接运行
2. `__main__`: 直接运行时的模块名
3. `if __name__ == '__main__'`: 测试代码块

### 2.0.5 最佳实践

1. 清晰的模块命名
2. 完整的文档字符串
3. 合理的导入顺序
4. 避免循环导入
5. 模块单一职责

### 2.0.6 模块镜像源

1. 阿里云：https://mirrors.aliyun.com/pypi/simple/
2. 清华大学：https://pypi.tuna.tsinghua.edu.cn/simple/
3. 豆瓣：https://pypi.douban.com/simple/

```sh
# 安装模块
pip install -i requests https://mirrors.aliyun.com/pypi/simple/
# 删除安装好的模块
pip uninstall module_name
# 查看已安装的模块
pip list
```

## 2.1 模块基础

模块是 Python 代码组织和复用的基础，掌握模块的使用是成为 Python 开发者的重要一步！

## 2.1 模块基础

### 2.1.1 模块的作用

1. 代码组织 - 将相关功能组织在一起
2. 代码复用 - 可以在多个程序中导入使用
3. 命名空间 - 避免命名冲突
4. 可维护性 - 便于维护和更新

### 2.1.3 模块的分类

1. 内置模块（标准库）：Python 自带的模块
2. 第三方模块：通过 `pip` 安装
3. 自定义模块：自己编写的模块

```py
# 常用标准库
import os       # 操作系统交互相关的功能，包括文件路径操作、环境变量等
import sys      # 提供对 Python 解释器相关的功能，包括命令行参数等
import math     # 包含数学运算相关的函数和常量
import datetime # 处理日期和时间，支持日期计算、格式化输出等
import random   # 生成伪随机数，支持随机选择、随机打乱等
import json     # 处理 JSON 数据，支持序列化和反序列化

# 第三方模块
import requests
import numpy as np
import pandas as pd

# 自定义模块
import my_module
```

### 2.1.4 模块导入

1. `import 模块名`
2. `from 模块名 import 函数名/变量名/类名`
3. `from 模块名 import *`
4. `import 模块名 as 别名`

```py
# 1. 导入整个模块
import module_name

# 2. 导入特定内容
from module_name import function_name

# 3. 导入所有内容（不推荐）
from module_name import *

# 4. 起别名
import module_name as alias
from module_name import function_name as fn_alias
```

## 2.2 常用内置模块

### 2.2.1 math 模块

`math` 模块提供了许多数学运算相关的函数和常量，包括三角函数、对数函数、幂函数等。

```py
# math模块 - 数学运算
import math

# 常量
print(math.pi)  # 圆周率
print(math.e)   # 自然对数的底数

# 三角函数
print(math.sin(math.pi / 2))  # 正弦函数
print(math.cos(math.pi))      # 余弦函数
print(math.tan(math.pi / 4))  # 正切函数

print(f"   π = {math.pi}")
print(f"   √16 = {math.sqrt(16)}")
print(f"   sin(π/2) = {math.sin(math.pi/2)}")
```

### 2.2.2 datetime 模块

`datetime` 模块提供了处理日期和时间的功能，包括日期计算、格式化输出等。

```py
# datetime模块 - 日期时间
import datetime

now = datetime.datetime.now()
print(f"   当前时间: {now}")
print(f"   日期: {now.date()}")
print(f"   时间: {now.time()}")
```

### 2.2.3 os 模块

`os` 模块提供了与操作系统交互的功能，包括文件路径操作、环境变量等。

```py
# os模块 - 操作系统交互
import os

print(f"   当前工作目录: {os.getcwd()}")
print(f"   系统环境变量PATH: {os.environ.get('PATH', '')[:50]}...")
```

### 2.2.4 random 模块

`random` 模块提供了生成伪随机数的功能，支持随机选择、随机打乱等。

```py
# random模块 - 生成随机数
import random

print(f"   随机整数: {random.randint(1, 10)}")
print(f"   随机浮点数: {random.uniform(1, 10)}")
print(f"   随机选择: {random.choice(['apple', 'banana', 'cherry'])}")
```

### 2.2.4 json 模块

`json` 模块提供了处理 JSON 数据的功能，支持序列化和反序列化。

```py
# json模块 - 处理JSON数据
import json

data = {
    "name": "Alice",
    "age": 25,
    "city": "New York"
}

# 序列化
json_str = json.dumps(data)
print(f"   序列化: {json_str}")

# 反序列化
data = json.loads(json_str)
print(f"   反序列化: {data}")
```

### 2.2.5 sys 模块

`sys` 模块提供了对 Python 解释器相关的功能，包括命令行参数等。

```py
# sys模块 - Python解释器相关
import sys
print(f"   命令行参数: {sys.argv}")
print(f"   Python版本: {sys.version}")
```

### 2.2.6 collections 模块

`collections` 模块提供了一些额外的数据类型，包括 `namedtuple`、`deque`、`Counter` 等。

```py
# collections模块 - 额外的数据类型
from collections import Counter, defaultdict
print("\n6. collections模块:")
words = ['apple', 'banana', 'apple', 'orange', 'banana', 'apple']
counter = Counter(words)
print(f"   词频统计: {counter}")
```

## 2.3 自定义模块

### 2.3.1 创建模块

1. 创建一个 `.py` 文件
2. 编写模块代码

```py
# file_utils.py 文件操作工具模块
import os

def read_file(filename):
    '''读取文件内容'''
    try:
        with open(filename, 'r', encoding='utf-8') as file:
            return file.read()
    except FileNotFoundError:
        return None

def write_file(filename, content):
    '''写入文件内容'''
    with open(filename, 'w', encoding='utf-8') as file:
        file.write(content)

def file_exists(filename):
    '''检查文件是否存在'''
    return os.path.exists(filename)

def get_file_size(filename):
    '''获取文件大小'''
    try:
        return os.path.getsize(filename)
    except OSError:
        return -1
```

### 2.3.2 自定义模块使用演示

```python
def custom_module_demo():
    """自定义模块演示"""
    print("\n=== 自定义模块演示 ===")

    # 模拟使用自定义模块
    # 使用示例:
    import file_utils

    # 写入文件
    file_utils.write_file('test.txt', 'Hello, World!')

    # 读取文件
    content = file_utils.read_file('test.txt')
    print(content)

    # 检查文件
    if file_utils.file_exists('test.txt'):
        size = file_utils.get_file_size('test.txt')
        print(f"文件大小: {size} 字节")
```

## 2.4 包（package）

包是组织模块的一种方式，它是一个包含 `__init__.py` 文件的目录，可以包含多个模块。

### 2.4.1 创建包

1. 创建一个目录
2. 在目录中创建 `__init__.py` 文件
3. 在目录中创建模块文件

```shell
项目结构示例:
myproject/
├── main.py
└── mypackage/
    ├── __init__.py
    ├── module1.py
    ├── module2.py
    └── subpackage/
        ├── __init__.py
        └── module3.py
```

### 2.4.2 使用包

1. `import mypackage.module1`
2. `from mypackage import module2`
3. `from mypackage.subpackage import module3`

```py
import mypackage.module1
from mypackage import module2
from mypackage.subpackage import module3
```

## 2.5 模块的高级使用

### 2.5.1 `__name__` 属性

`__name__` 是一个特殊的变量，它表示当前模块的名字。当模块被直接运行时，`__name__` 的值为 `'__main__'`，否则为模块的名字。

```py
# 在模块中通常这样写:
def main():
    # 模块的主要功能
    print("这是模块的主要功能")

if __name__ == '__main__':
    # 当直接运行这个文件时执行
    main()
```

### 2.5.2 `__main__` 模块

`__main__` 是一个特殊的模块，它表示当前运行的模块。当模块被直接运行时，`__main__` 的值为当前模块的 `__name__`。

```py
# 在模块中通常这样写:
def main():
    # 模块的主要功能
    print("这是模块的主要功能")

if __name__ == '__main__':
    # 当直接运行这个文件时执行
    main()
```

### 2.5.3 模块搜索路径

Python 解释器在导入模块时会按照一定的顺序搜索模块，这个顺序称为模块搜索路径。模块搜索路径包括以下几部分：

1. 当前目录
2. 系统目录（`sys.path`）
3. Python 安装目录

```py
import sys
print("Python查找模块的顺序:")
for i, path in enumerate(sys.path[:5]):  # 只显示前5个
    print(f"  {i+1}. {path}")
```

### 2.5.4 模块重载

模块重载是指在运行时重新加载模块，以便在修改模块后立即生效。

```py
# 方法1: 使用 importlib
import importlib
import mymodule

# 修改 mymodule 后...
importlib.reload(mymodule)

# 方法2: 重启Python解释器（更彻底）
```

注意: 重载可能不会更新所有引用，生产环境不建议使用

### 2.5.5 模块属性

模块属性是模块中定义的变量、函数、类等。可以通过 `dir()` 函数查看模块的所有属性。

```py
import math
print("模块的内置属性:")
print(f"1. __name__: {math.__name__}")  # math模块的名称
# print(f"2. __file__: {math.__file__}") # math模块没有__file__属性
print(f"3. __doc__: {math.__doc__[:50]}...") # math模块的文档字符串

print("\n查看模块中的所有名称:")
print("使用 dir(模块名):")
math_names = [name for name in dir(math) if not name.startswith('_')]
print(f"math模块的部分函数: {math_names[:10]}...") # math模块的部分函数
```

### 2.5.6 第三方模块

第三方模块是指由其他开发者编写的模块，可以通过包管理工具（如 `pip`）安装。

#### 2.5.6.1 安装第三方模块

1. 使用 pip 安装

```shell
# pip install package_name
pip install requests
pip install numpy pandas matplotlib
```

2. 使用 conda 安装

```shell
# conda install package_name
conda install requests
```

#### 2.5.6.2 常用的第三方模块

- `requests`：用于发送 HTTP 请求
- `numpy`：用于科学计算
- `pandas`：用于数据处理和分析
- `matplotlib`：用于数据可视化
- `flask`: 用于构建 Web 应用
- `beautifulsoup4`: 用于解析 HTML 和 XML
- `scikit-learn`：用于机器学习
- `tensorflow`：用于深度学习

```py
# requests模块 - 发送HTTP请求
import requests

response = requests.get('https://api.github.com')
print(f"   状态码: {response.status_code}")
print(f"   响应内容: {response.text[:100]}...")

# numpy模块 - 科学计算
import numpy as np

a = np.array([1, 2, 3])
b = np.array([4, 5, 6])
print(f"   数组a: {a}")
print(f"   数组b: {b}")
print(f"   数组a + 数组b: {a + b}")

# pandas模块 - 数据处理和分析
import pandas as pd

data = {'Name': ['Tom', 'Nick', 'John'],
        'Age': [28, 32, 25],
        'City': ['New York', 'Paris', 'London']}

df = pd.DataFrame(data)
print(f"   DataFrame: \n{df}")

# matplotlib模块 - 数据可视化
import matplotlib.pyplot as plt

x = [1, 2, 3, 4, 5]
y = [1, 4, 9, 16, 25]

plt.plot(x, y)
plt.xlabel('x')
plt.ylabel('y')
plt.title('Plot of x^2')
plt.show()
```

### 2.5.7 模块的最佳实践

1. 模块命名: 使用小写字母，避免特殊字符
2. 文档字符串: 每个模块都应该有文档字符串
3. 导入顺序: 标准库 → 第三方库 → 自定义模块
4. 避免循环导入: 模块之间不要相互导入
5. 使用 `__all__` 控制导入内容
6. 模块单一职责: 一个模块只负责一个功能
7. 测试代码放在 `if __name__ == '__main__'` 中
8. 版本管理: 使用 `__version__` 属性

```py
# 导入顺序：标准库 → 第三方库 → 自定义模块
# 标准库导入
import os
import sys
from datetime import datetime

# 第三方库导入
import requests
import numpy as np

# 自定义模块导入
from mypackage import utils
from . import helpers  # 相对导入
```

## 2.6 模块示例

### 2.6.1 创建模块

创建一个配置管理模块 `config_manager.py`

```py
# config_manager.py 配置管理模块
import json
import os

class ConfigManager:
    '''配置管理器'''

    def __init__(self, config_file='config.json'):
        self.config_file = config_file
        self.config = self._load_config()

    def _load_config(self):
        '''加载配置'''
        if os.path.exists(self.config_file):
            with open(self.config_file, 'r', encoding='utf-8') as f:
                return json.load(f)
        return {}

    def save_config(self):
        '''保存配置'''
        with open(self.config_file, 'w', encoding='utf-8') as f:
            json.dump(self.config, f, indent=4, ensure_ascii=False)

    def get(self, key, default=None):
        '''获取配置值'''
        return self.config.get(key, default)

    def set(self, key, value):
        '''设置配置值'''
        self.config[key] = value
        self.save_config()

    def delete(self, key):
        '''删除配置项'''
        if key in self.config:
            del self.config[key]
            self.save_config()

# 创建默认配置管理器实例
default_config = ConfigManager()

def get_config(key, default=None):
    '''快速获取配置'''
    return default_config.get(key, default)

def set_config(key, value):
    '''快速设置配置'''
    default_config.set(key, value)

if __name__ == '__main__':
    # 测试代码
    set_config('database.host', 'localhost')
    set_config('database.port', 3306)
    print("配置设置完成")
```

### 2.6.2 模块测试

```py
# test_math_operations.py
import unittest
from math_operations import add, multiply, circle_area

class TestMathOperations(unittest.TestCase):

    def test_add(self):
        self.assertEqual(add(2, 3), 5)
        self.assertEqual(add(-1, 1), 0)

    def test_multiply(self):
        self.assertEqual(multiply(2, 3), 6)
        self.assertEqual(multiply(-2, 3), -6)

    def test_circle_area(self):
        self.assertAlmostEqual(circle_area(1), 3.14159, places=4)

if __name__ == '__main__':
    unittest.main()

```

运行测试

```shell
python -m unittest test_math_operations
python test_math_operations.py
```

## 2.7 模块总结

1. 模块是代码组织的基本单位
2. 使用 import 语句导入模块
3. 包是包含多个模块的目录
4. `__name__` 用于判断模块执行方式
5. 遵循最佳实践编写可维护的模块
6. 为模块编写测试确保质量
