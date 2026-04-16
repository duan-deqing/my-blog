# 02 字典

---

## 2.0 字典的核心特点

1. 键值对结构

   - 每个键对应一个值
   - 键必须是不可变类型（字符串、数字、元组）
   - 值可以是任意类型

2. 主要操作

   ```python
   # 访问
   value = dict[key]
   value = dict.get(key, default)

   # 修改
   dict[key] = new_value

   # 删除
   del dict[key]
   value = dict.pop(key)
   ```

3. 重要方法

   - `keys()` - 所有键
   - `values()` - 所有值
   - `items()` - 所有键值对
   - `get()` - 安全访问
   - `update()` - 批量更新
   - `setdefault()` - 设置默认值

4. 优势

   - 查找极快 - 基于哈希表，O(1)时间复杂度
   - 灵活性高 - 可以存储复杂数据结构
   - 表达力强 - 键值对形式直观易懂

5. 适用场景
   - 配置信息存储
   - 数据库记录表示
   - 缓存数据
   - 统计计数
   - 快速查找表

> 字典是 Python 中最重要、最常用的数据结构之一！

## 2.1 字典的定义

字典（dictionary）是 Python 中的一种数据类型，用于存储键值对。字典中的键必须是唯一的，值可以是任意类型的数据。
字典是无序的，即字典中的元素没有固定的顺序。可变的，即字典中的元素可以被修改。且字典中的键不能重复，如果重复，后面键的值会覆盖前面的值，值可以重复。

字典的定义方式有两种：

1. 使用花括号 `{}` 包裹键值对，键值对之间用逗号 `,` 分隔，键和值之间用冒号 `:` 分隔。
2. 使用 `dict()` 函数将其他数据类型转换为字典。

例如：

```python
# 方法1: 花括号直接创建
dict1 = {'name': '张三', 'age': 25, 'city': '北京'}
print(f"直接创建: {dict1}")

# 方法2: dict()构造函数
dict2 = dict(name='李四', age=30, city='上海')
print(f"dict()创建: {dict2}")

# 方法3: 从键值对序列创建
dict3 = dict([('name', '王五'), ('age', 28), ('city', '广州')])
print(f"序列创建: {dict3}")

# 方法4: 使用zip函数
keys = ['name', 'age', 'job']
values = ['赵六', 35, '工程师']
dict4 = dict(zip(keys, values))
print(f"zip创建: {dict4}")

# 方法5: 字典推导式
dict5 = {x: x**2 for x in range(1, 6)}
print(f"推导式创建: {dict5}")

# 空字典
empty_dict1 = {}
empty_dict2 = dict()
print(f"空字典1: {empty_dict1}")
print(f"空字典2: {empty_dict2}")

```

## 2.2 字典的基本操作

### 2.2.1 字典的访问

字典的访问可以通过键来获取对应的值，使用方括号 `[]` 或 `get()` 方法。

例如：

```python
student = {'name': '小明', 'age': 18, 'grade': '高三', 'scores': [85, 92, 78]}

 # 访问元素
print(f"字典: {student}")
print(f"姓名: {student['name']}")
print(f"年龄: {student.get('age')}")

# 使用get()方法安全访问（键不存在返回None或默认值）
print(f"性别: {student.get('gender')}")  # 返回None
print(f"性别: {student.get('gender', '未知')}")  # 返回默认值
```

### 2.2.2 字典的修改

字典的修改可以通过键来修改对应的值，使用方括号 `[]` 或 `update()` 方法。

例如：

```python
student['age'] = 19
student['gender'] = '男'  # 添加新键值对
print(f"修改后: {student}")
```

### 2.2.3 字典的删除

字典的删除可以通过键来删除对应的键值对，使用 `del` 语句或 `pop()` 方法。

例如：

```python
del student['scores']
removed_value = student.pop('grade')  # 删除并返回值
print(f"删除后: {student}")
print(f"删除的值: {removed_value}")

```

### 2.2.4 字典的清空

字典的清空可以通过 `clear()` 方法。

例如：

```python
student.clear()
print(f"清空后: {student}")
```

## 2.3 字典的常用方法

```python
person = {'name': '张三', 'age': 25, 'city': '北京', 'job': '工程师'}
print(f"原始字典: {person}")
```

### 2.3.1 keys()方法

`keys()` 方法返回字典中所有的键，以列表的形式返回。

例如：

```python
# keys() - 所有键
print(f"所有键: {list(person.keys())}")
```

### 2.3.2 values()方法

`values()` 方法返回字典中所有的值，以列表的形式返回。

例如：

```python
# values() - 所有值
print(f"所有值: {list(person.values())}")
```

### 2.3.3 items()方法

`items()` 方法返回字典中所有的键值对，以列表的形式返回，每个元素是一个元组。

例如：

```python
# items() - 所有键值对
print(f"所有键值对: {list(person.items())}")
```

### 2.3.4 update()方法

`update()` 方法用于更新字典，可以接受另一个字典或键值对序列作为参数，将它们合并到当前字典中。

例如：

```python
# update() - 更新字典
person.update({'salary': 15000, 'age': 26})  # 更新age，添加salary
print(f"更新后: {person}")
```

### 2.3.5 setdefault()方法

`setdefault()` 方法用于获取指定键的值，如果键不存在，则插入该键并设置默认值。

例如：

```python
# setdefault() - 键不存在时设置默认值
gender = person.setdefault('gender', '男')
age = person.setdefault('age', 30)  # 已存在，不会修改
print(f"setdefault后: {person}")
print(f"gender: {gender}, age: {age}")
```

### 2.3.6 popitem()方法

`popitem()` 方法用于删除并返回字典中的最后一个键值对。

例如：

```python
# popitem() - 删除并返回最后一个键值对
last_item = person.popitem()
print(f"删除的项: {last_item}")
print(f"删除后: {person}")
```

### 2.3.7 copy()方法

`copy()` 方法用于复制字典，返回一个新的字典对象。

例如：

```python
# copy() - 浅拷贝
person_copy = person.copy()
print(f"拷贝: {person_copy}")
```

## 2.4 字典的遍历

```python
student = {'name': '李四', 'age': 20, 'major': '计算机', 'gpa': 3.8}
```

### 2.4.1 遍历字典的键与值

可以使用 `for` 循环遍历字典的键。

例如：

```python
print("遍历键:")
for key in student:
    print(f"  {key}")
print("\n遍历值:")
for value in student.values():
    print(f"  {value}")
```

### 2.4.2 遍历字典的键值对

可以使用 `for` 循环遍历字典的键值对。

例如：

```python
print("\n遍历键值对:")
for key, value in student.items():
    print(f"  {key}: {value}")
```

### 2.4.3 带有索引的遍历

可以使用 `enumerate()` 函数在遍历字典时获取索引。

例如：

```python
print("\n带索引的遍历:")
for i, (key, value) in enumerate(student.items()):
    print(f"  第{i+1}项: {key} = {value}")
```

## 2.5 字典推导式

字典推导式是一种简洁的创建字典的方式，它使用类似于列表推导式的语法，但用于生成字典。

例如：

```python
# 使用字典推导式创建一个字典，键为1到5，值为键的平方
squares = {x: x**2 for x in range(1, 6)}
print(f"字典推导式: {squares}")

```

### 2.5.1 基本字典推导式

基本字典推导式的基本语法如下：

```python
{key_expression: value_expression for item in iterable}
```

其中，`key_expression` 和 `value_expression` 是表达式，用于生成键和值。`item` 是可迭代对象中的元素，`iterable` 是可迭代对象。

例如：

```python
squares = {x: x**2 for x in range(1, 6)}
print(f"平方字典: {squares}") # {1: 1, 2: 4, 3: 9, 4: 16, 5: 25}
```

### 2.5.2 带条件推导式

带条件推导式可以在字典推导式中添加条件判断，只有满足条件的元素才会被添加到字典中。

例如：

```python
# 使用字典推导式创建一个字典，键为1到5，值为键的平方，但只保留偶数键
even_squares = {x: x**2 for x in range(1, 6) if x % 2 == 0}
print(f"偶数平方字典: {even_squares}") # {2: 4, 4: 16}

# 带条件的推导式
even_squares = {x: x**2 for x in range(1, 11) if x % 2 == 0}
print(f"偶数的平方: {even_squares}") # {2: 4, 4: 16, 6: 36, 8: 64, 10: 100}
```

### 2.5.3 转换字典

字典推导式还可以用于将一个字典转换为另一个字典，例如将键值对进行某种转换。

例如：

```python
# 将一个字典的键值对进行转换
# 使用字典推导式将一个字典的键值对进行转换
original = {'a': 1, 'b': 2, 'c': 3}
doubled = {k: v*2 for k, v in original.items()}
print(f"值翻倍: {doubled}") # {'a': 2, 'b': 4, 'c': 6}
```

### 2.5.4 键值互换

字典推导式还可以用于将字典的键和值进行互换，例如：

```python
# 将字典的键和值进行互换
original_dict = {'a': 1, 'b': 2, 'c': 3}
swapped_dict = {v: k for k, v in original_dict.items()}
print(f"键值互换: {swapped_dict}") # {1: 'a', 2: 'b', 3: 'c'}

# 键值互换
swapped = {v: k for k, v in original.items()}
print(f"键值互换: {swapped}") # {1: 'a', 2: 'b', 3: 'c'}
```

### 2.5.5 列表创建字典

字典推导式还可以用于将列表转换为字典，例如将列表中的元素作为键，索引作为值，例如：

```python
# 将列表转换为字典
keys = ['a', 'b', 'c']
values = [1, 2, 3]
dict_from_list = {k: v for k, v in zip(keys, values)}
print(f"列表转换为字典: {dict_from_list}") # {'a': 1, 'b': 2, 'c': 3}

# 从两个列表创建字典
fruits = ['apple', 'banana', 'orange']
prices = [5, 3, 4]
fruit_dict = {fruit: price for fruit, price in zip(fruits, prices)}
print(f"水果价格: {fruit_dict}") # {'apple': 5, 'banana': 3, 'orange': 4}
```

### 2.5.6 字典合并

## 2.6 字典的嵌套

字典的嵌套是指在字典中包含其他字典作为值，例如：

```python
# 嵌套字典示例
school = {
    'class1': {
        'teacher': '王老师',
        'students': 45,
        'subjects': ['数学', '语文', '英语']
    },
    'class2': {
        'teacher': '李老师',
        'students': 42,
        'subjects': ['物理', '化学', '生物']
    }
}
```

### 2.6.1 访问嵌套字典

可以使用嵌套的键来访问嵌套字典中的值，例如：

```python
# 访问嵌套值
print(f"\n一班班主任: {school['class1']['teacher']}")
print(f"二班第一个科目: {school['class2']['subjects'][0]}")

# 访问嵌套字典
print(f"Class1的Teacher: {school['class1']['teacher']}")
print(f"Class2的Students: {school['class2']['students']}")
```

### 2.6.2 打印嵌套字典

可以使用 `print()` 函数打印嵌套字典，例如：

```python
# 打印嵌套字典
print(f"嵌套字典: {school}")
print("学校信息:")
for class_name, class_info in school.items():
    print(f"  {class_name}:")
    print(f"    班主任: {class_info['teacher']}")
    print(f"    学生数: {class_info['students']}")
    print(f"    科目: {', '.join(class_info['subjects'])}")
```

## 2.7 字典高级特性

### 2.7.1 defaultdict - 带默认值的字典

`defaultdict` 是 `collections` 模块中的一个类，它继承自 `dict` 类，并提供了默认值的特性，例如：

```python
from collections import defaultdict

# 使用defaultdict创建一个字典，默认值为0
# 默认值为0
word_count = defaultdict(int)
words = ['apple', 'banana', 'apple', 'orange', 'banana', 'apple']

for word in words:
    word_count[word] += 1

# 默认值为列表
group_by_length = defaultdict(list)
for word in words:
    group_by_length[len(word)].append(word)

print(f"按长度分组: {dict(group_by_length)}")

```

### 2.7.2 Counter - 计数器 - 计数专用字典

`Counter` 是 `collections` 模块中的一个类，它用于统计可迭代对象中元素的个数，例如：

```python
from collections import Counter

# 使用Counter统计可迭代对象中元素的个数
words = ['apple', 'banana', 'apple', 'orange', 'banana', 'apple']
counter = Counter(words)
print(f"Counter计数: {counter}")
print(f"最常见的2个: {counter.most_common(2)}")

# 获取出现次数最多的元素
most_common_word = word_counts.most_common(1)
print(f"出现次数最多的单词: {most_common_word}")
```

## 2.8 字典性能特点

字典是一种非常高效的数据结构，它的时间复杂度为 O(1)，即无论字典的大小如何，查找、插入和删除操作的时间都是常数时间，例如：

```python
# 字典的查找速度非常快（近似O(1)）
import time

large_dict = {i: f"value_{i}" for i in range(10000)}

# 测试查找性能
start_time = time.time()
for i in range(1000):
    _ = large_dict.get(5000)
end_time = time.time()

print(f"1000次查找时间: {(end_time - start_time)*1000:.2f}毫秒")
print("字典基于哈希表实现，查找速度非常快")
```

## 2.9 总结

字典是一种非常灵活和强大的数据结构，它可以在各种场景下使用。字典的键值对存储方式使得它非常适合用于存储和查找数据。字典的内置方法提供了丰富的操作功能，例如添加、删除、更新和查找键值对。字典的推导式和嵌套字典提供了更高级的操作方式。字典的性能特点使得它非常适合用于处理大量数据。

1. 键值对的无序集合（Python 3.7+保持插入顺序）
2. 键必须是不可变类型（字符串、数字、元组）
3. 值可以是任意类型
4. 查找速度快（哈希表实现）
5. 可变，可以动态添加、修改、删除
6. 支持字典推导式
7. 常用方法: keys(), values(), items(), get(), update()

## 2.10 实践练习

1. 创建一个字典，键为 1 到 5，值为键的平方。
2. 使用字典推导式创建一个字典，键为 1 到 5，值为键的平方，但只保留偶数键。
3. 将一个字典的键值对进行转换。
4. 将字典的键和值进行互换。
5. 将列表转换为字典。
6. 将两个列表创建字典。
7. 访问嵌套字典中的值。
8. 打印嵌套字典。
9. 使用 `defaultdict` 创建一个字典，默认值为 0。
10. 使用 `Counter` 统计可迭代对象中元素的个数。
11. 使用字典的内置方法添加、删除、更新和查找键值对。
12. 使用字典的推导式创建一个字典，键为 1 到 5，值为键的平方，但只保留偶数键。
13. 使用字典的嵌套创建一个嵌套字典，包含班级信息。
