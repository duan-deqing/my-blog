# 04 列表

---

## 4.0 列表核心特点

1. 基本特性

   - 有序 - 元素有固定顺序
   - 可变 - 可以修改、添加、删除元素
   - 异构 - 可以包含不同类型的元素

2. 创建方式

   ```python
    # 多种创建方式
    list1 = [1, 2, 3]
    list2 = list(range(5))
    list3 = [x**2 for x in range(5)]
    list4 = [] # 空列表 3. 重要操作
    python
    # 访问
    value = list[index]
    sublist = list[start:end:step]
    # 修改
    list[index] = new_value
    list.append(item)
    list.insert(index, item)
    # 删除
    del list[index]
    item = list.pop()
    list.remove(value)
   ```

3. 主要方法

   - `append()`, `extend()` - 添加元素
   - `insert()` - 插入元素
   - `remove()`, `pop()` - 删除元素
   - `sort()`, `reverse()` - 排序,反转
   - `index()`, `count()` - 查找,统计
   - `copy()` - 复制列表

4. 性能特点

   - 末尾操作 - O(1) 时间复杂度（很快）
   - 开头操作 - O(n) 时间复杂度（较慢）
   - 查找元素 - O(n) 时间复杂度

5. 适用场景

   - 动态数据集合
   - 栈和队列的实现
   - 矩阵和多维数据
   - 临时数据存储
   - 数据处理和转换

6. 优势
   - 灵活性高 - 可以动态修改
   - 功能丰富 - 提供大量内置方法
   - 表达力强 - 列表推导式简洁高效

> 列表是 Python 中最常用、最灵活的数据结构之一！

## 4.1 列表的定义

列表（list）是处理一组有序项目的数据结构。
列表中的元素可以是不同类型，并且列表中的元素是有序的，可以通过索引访问。
格式为：`[元素1, 元素2, 元素3, ...]`

注意：

- 列表是可变的，即可以在创建后进行修改。
- 列表中的所有元素放在方括号 `[]` 中，元素之间用逗号 `,` 分隔。
- 列表中的元素可以是任何类型，包括数字、字符串、布尔值、甚至是其他列表。

**列表的创建**

```python
# 方法1: 方括号直接创建
list1 = [1, 2, 3, 4, 5]
print(f"直接创建: {list1}")

# 方法2: list()构造函数
list2 = list(range(1, 6))
list3 = list("hello")
print(f"从range创建: {list2}")
print(f"从字符串创建: {list3}")

# 方法3: 列表推导式
list4 = [x for x in range(1, 11) if x % 2 == 0]
print(f"列表推导式: {list4}")

# 方法4: 乘法创建重复元素
list5 = [0] * 5
list6 = ['hello'] * 3
print(f"重复创建1: {list5}")
print(f"重复创建2: {list6}")

# 空列表
empty_list1 = []
empty_list2 = list()
print(f"空列表1: {empty_list1}")
print(f"空列表2: {empty_list2}")

# 混合类型列表
mixed_list = [1, "hello", 3.14, True, [1, 2, 3]]
print(f"混合类型列表: {mixed_list}")
```

## 4.2 列表的基本操作

### 4.2.1 访问列表元素

列表的索引和切片操作允许我们访问和操作列表中的元素。

索引操作

```python
numbers = [0, 1, 2, 3, 4, 5, 6, 7, 8, 9]
print(f"原始列表: {numbers}")

# 索引访问
print(f"第一个元素: {numbers[0]}")
print(f"最后一个元素: {numbers[-1]}")
print(f"第三个元素: {numbers[2]}")
print(f"倒数第二个元素: {numbers[-2]}")

# 切片操作 [start:end:step]
print(f"前5个元素: {numbers[:5]}")
print(f"第3到第7个: {numbers[2:7]}")
print(f"从第5个开始: {numbers[4:]}")
print(f"倒数3个元素: {numbers[-3:]}")
print(f"每隔一个取一个: {numbers[::2]}")
print(f"反转列表: {numbers[::-1]}")
print(f"从后往前每隔一个: {numbers[::-2]}")
```

### 4.2.2 列表连接

列表连接操作可以将两个或多个列表合并为一个列表。

```python
list1 = [1, 2, 3]
list2 = [4, 5, 6]

# 列表连接
combined = list1 + list2
print(f"列表连接: {list1} + {list2} = {combined}")
```

### 4.2.3 列表重复

列表重复操作可以将一个列表中的元素重复多次。

```python
# 列表重复
repeated = list1 * 3
print(f"列表重复: {list1} * 3 = {repeated}")
```

### 4.2.4 列表成员检测

列表成员检测操作可以检查一个元素是否在列表中。

```python
# 成员检测
print(f"2在列表中: {2 in list1}")
print(f"10在列表中: {10 in list1}")
```

### 4.2.5 列表长度

列表长度操作可以获取列表中元素的个数。

```python
# 长度计算
print(f"列表长度: {len(list1)}")
```

### 4.2.6 比较运算

列表比较运算可以比较两个列表的元素。包括等于（==）、不等于（!=）、小于（<）、小于等于（<=）、大于（>）和大于等于（>=）。

```python
# 比较运算
list3 = [1, 2, 3]
print(f"list1 == list3: {list1 == list3}")
print(f"list1 > list2: {list1 > list2}")
```

## 4.3 列表的方法

列表的方法包括添加元素、删除元素、修改元素、查找元素等操作。

```python
numbers = [1, 2, 3]
print(f"原始列表: {numbers}")
```

### 4.3.1 添加元素

列表提供了多种方法来添加元素，包括 `append()`、`extend()` 和 `insert()`。

```python
# 添加元素
numbers.append(4)           # 末尾添加
numbers.insert(1, 1.5)      # 指定位置插入
numbers.extend([5, 6, 7])   # 扩展列表
print(f"添加元素后: {numbers}")
```

### 4.3.2 删除元素

列表提供了多种方法来删除元素，包括 `pop()`、`remove()` 和 `clear()`。

```python
# 删除元素
numbers.remove(1.5)         # 删除指定值
popped = numbers.pop()      # 删除并返回最后一个元素
popped2 = numbers.pop(1)    # 删除并返回指定位置元素
print(f"删除元素后: {numbers}")
print(f"弹出的元素: {popped}, {popped2}")
```

### 4.3.3 修改元素

列表中的元素可以通过索引直接修改。

```python
# 修改元素
numbers[0] = 0
print(f"修改元素后: {numbers}")
```

### 4.3.4 查找元素

列表提供了多种方法来查找元素，包括 `index()` 和 `count()`。

```python
# 查找元素
print(f"5的索引: {numbers.index(5)}")
print(f"5的出现次数: {numbers.count(5)}")
```

### 4.3.5 清空列表

列表提供了 `clear()` 方法来清空列表。

```python
# 清空列表
numbers.clear()
print(f"清空后: {numbers}")
```

## 4.4 列表高级方法

列表的高级方法包括排序、反转、复制等操作。

```python
numbers = [3, 1, 4, 1, 5, 9, 2, 6, 5, 3, 5]
print(f"原始列表: {numbers}")
```

### 4.4.1 排序 - sort()

列表提供了 `sort()` 方法来对列表进行排序。

```python
# 排序
numbers.sort()
print(f"排序后: {numbers}")

numbers.sort(reverse=True)
print(f"降序排序: {numbers}")
```

### 4.4.2 反转 - reverse()

列表提供了 `reverse()` 方法来反转列表。

```python
# 反转
numbers.reverse()
print(f"反转后: {numbers}")
```

### 4.4.3 复制 - copy()

列表提供了 `copy()` 方法来复制列表。切片操作 `[:]` 也可以实现复制。

```python
# 复制
numbers_copy = numbers.copy()
numbers_copy2 = numbers[:]  # 切片复制
print(f"复制列表1: {numbers_copy}")
print(f"复制列表2: {numbers_copy2}")
```

## 4.5 列表推导式

列表推导式是一种简洁的创建列表的方法。它允许我们通过一个表达式来生成列表，并可以在生成过程中进行条件过滤。

基本格式：`[表达式 for 变量 in 列表]`

### 4.5.1 基本使用

```python
# 基本推导式
squares = [x**2 for x in range(1, 6)]
print(f"平方列表: {squares}")
```

### 4.5.2 带条件的列表推导式

```python
# 带条件的推导式
even_squares = [x**2 for x in range(1, 11) if x % 2 == 0]
print(f"偶数的平方: {even_squares}")
```

### 4.5.3 字符串处理 & 数据转换

```python
# 字符串处理
words = ["hello", "world", "python"]
upper_words = [word.upper() for word in words]
word_lengths = [len(word) for word in words]
print(f"大写单词: {upper_words}")
print(f"单词长度: {word_lengths}")

# 数据转换
numbers = [1, 2, 3, 4, 5]
formatted = [f"数字: {n}" for n in numbers]
print(f"格式化: {formatted}")
```

## 4.6 嵌套列表

嵌套列表是指列表中的元素也是列表。嵌套列表可以用于表示多维数据结构，如矩阵。

```python
# 二维列表（矩阵）
matrix = [
    [1, 2, 3],
    [4, 5, 6],
    [7, 8, 9]
]

print("二维矩阵:")
for row in matrix:
    print(f"  {row}")

print(f"第二行: {matrix[1]}")
print(f"第二行第三列: {matrix[1][2]}")
```

### 4.6.1 列表遍历

列表遍历可以通过多种方式实现，包括使用 `for` 循环和 `while` 循环。

```python
# 访问所有元素
print("所有元素:")
for i, row in enumerate(matrix):
    for j, value in enumerate(row):
        print(f"  matrix[{i}][{j}] = {value}")

# 单列表的遍历
fruits = ['apple', 'banana', 'orange', 'grape']

print("直接遍历:")
for fruit in fruits:
    print(f"  - {fruit}")

print("\n带索引遍历:")
for i, fruit in enumerate(fruits):
    print(f"  索引 {i}: {fruit}")

print("\n反向遍历:")
for fruit in reversed(fruits):
    print(f"  - {fruit}")

print("\n同时遍历多个列表:")
prices = [5, 3, 4, 6]
for fruit, price in zip(fruits, prices):
    print(f"  {fruit}: ${price}")
```

### 4.6.2 列表推导式处理嵌套列表

列表推导式可以用于处理嵌套列表，例如计算矩阵的转置。

```python
# 列表推导式处理嵌套列表
flattened = [value for row in matrix for value in row]
print(f"扁平化: {flattened}")

# 转置矩阵
transposed = [[row[i] for row in matrix] for i in range(len(matrix[0]))]
print(f"转置矩阵: {transposed}")
```

## 4.7 列表性能

列表的性能主要取决于其操作类型。以下是一些常见的列表操作及其性能特点：

- 访问元素：O(1)
- 添加元素到末尾：O(1)
- 添加元素到指定位置：O(n)
- 删除元素：O(n)
- 修改元素：O(1)
- 查找元素：O(n)
- 排序：O(n log n)
- 反转：O(n)

```python
import time

# 访问元素
numbers = list(range(1000000))
start_time = time.time()
value = numbers[500000]
end_time = time.time()
print(f"访问元素: {value} ({end_time - start_time:.6f} 秒)")

# 测试不同操作的性能
large_list = list(range(10000))

# 测试末尾添加
start_time = time.time()
large_list.append(10000)
append_time = time.time() - start_time

# 测试开头添加
start_time = time.time()
large_list.insert(0, -1)
insert_time = time.time() - start_time

# 测试查找
start_time = time.time()
_ = 5000 in large_list
search_time = time.time() - start_time

print(f"末尾添加时间: {append_time*1000:.4f}毫秒")
print(f"开头添加时间: {insert_time*1000:.4f}毫秒")
print(f"查找时间: {search_time*1000:.4f}毫秒")
print("说明: 列表在末尾操作很快，在开头操作较慢")
```

## 4.8 实践示例

### 4.8.1 成绩管理

```python
# 成绩管理
print("1. 成绩管理:")
scores = [85, 92, 78, 96, 88, 72]
print(f"原始成绩: {scores}")
print(f"最高分: {max(scores)}")
print(f"最低分: {min(scores)}")
print(f"平均分: {sum(scores)/len(scores):.1f}")
print(f"排序后: {sorted(scores, reverse=True)}")
```

### 4.8.2 数据过滤

```python
# 数据过滤
numbers = [23, 45, 12, 67, 34, 89, 56]
filtered = [x for x in numbers if x > 50]
print(f"原始数据: {numbers}")
print(f"大于50的数: {filtered}")
```

### 4.8.3 栈和队列模拟

```python
# 栈 (后进先出)
stack = []
stack.append(1)  # 压栈
stack.append(2)
stack.append(3)
print(f"栈: {stack}")
popped = stack.pop()  # 出栈
print(f"出栈: {popped}, 剩余: {stack}")

# 队列 (先进先出)
from collections import deque
queue = deque([1, 2, 3])
queue.append(4)     # 入队
first = queue.popleft()  # 出队
print(f"队列: {list(queue)}, 出队: {first}")
```

### 4.8.4 分页处理

```python
# 分页处理
all_data = list(range(1, 101))  # 1-100的数据
page_size = 10
page_number = 3

start_index = (page_number - 1) * page_size
end_index = start_index + page_size
page_data = all_data[start_index:end_index]

print(f"总数据量: {len(all_data)}")
print(f"第{page_number}页数据: {page_data}")
```

## 4.9 列表与其它数据结构

列表是 Python 中最常用的数据结构之一，但还有其他一些数据结构可以用于存储和操作数据。以下是一些常见的替代方案：

- 元组（Tuple）：不可变的序列，适用于需要保证数据不被修改的场景。
- 集合（Set）：无序且不重复的元素集合，适用于需要快速查找和去重的场景。
- 字典（Dictionary）：键值对的集合，适用于需要快速通过键来访问值的场景。

```python
# 列表 vs 元组
my_list = [1, 2, 3]    # 可变
my_tuple = (1, 2, 3)   # 不可变

print("列表 vs 元组:")
print(f"列表可变: 可以修改 - {my_list}")
my_list[0] = 10
print(f"修改后: {my_list}")

# 列表 vs 字符串
my_string = "hello"
my_list2 = list(my_string)

print(f"\n字符串: {my_string} (不可变)")
print(f"字符列表: {my_list2} (可变)")
my_list2[0] = 'H'
print(f"修改后: {my_list2}")
```

## 4.10 总结

1. 有序、可变的元素序列
2. 可以包含任意类型的元素
3. 支持索引、切片、迭代
4. 常用方法: append(), insert(), remove(), pop(), sort()
5. 列表推导式提供简洁的创建方式
6. 性能特点: 末尾操作快，开头操作慢
7. 适用场景: 动态数据集合、栈、队列、矩阵等

- 列表是 Python 中最常用的数据结构之一，用于存储有序的元素集合。
- 列表支持多种操作，如添加、删除、修改、查找等。
- 列表可以包含不同类型的元素，并且可以嵌套使用。
- 列表推导式是一种简洁的列表生成方式。
- 列表性能取决于操作类型，访问元素和修改元素操作较快，而添加和删除操作较慢。
- 列表可以用于实现栈和队列等数据结构。
- 列表与元组、集合和字典等数据结构有相似之处，但有不同的特性和应用场景。

## 4.11 练习

1. 创建一个包含数字 1 到 10 的列表，并打印出列表中的所有元素。
2. 创建一个包含字符串的列表，并使用列表推导式生成一个新的列表，其中包含每个字符串的长度。
3. 创建一个包含数字的列表，并使用列表推导式生成一个新的列表，其中包含所有大于 5 的数字。
4. 创建一个包含数字的列表，并使用列表推导式生成一个新的列表，其中包含所有偶数。
5. 创建一个包含数字的列表，并使用列表推导式生成一个新的列表，其中包含所有小于 10 的数字的平方。
6. 创建一个包含数字的列表，并使用列表推导式生成一个新的列表，其中包含所有小于 10 的数字的立方。
7. 创建一个包含数字的列表，并使用列表推导式生成一个新的列表，其中包含所有小于 10 的数字的阶乘和斐波那契数列。
8. 创建一个包含数字的列表，并使用列表推导式生成一个新的列表，其中包含所有小于 10 的数字的阶乘和斐波那契数列，并按照升序排序，但只保留前 5 个元素，并且每个元素都乘以 2，然后计算新列表的平均值。
