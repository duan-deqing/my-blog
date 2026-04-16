# 03 集合

## 3.0 集合核心特点

1. 基本特性

   - 无序 - 元素没有固定顺序
   - 不重复 - 自动去除重复元素
   - 可变 - 可以添加、删除元素（frozenset 除外）

2. 创建方式

```python
   # 正确方式
   s1 = {1, 2, 3}
   s2 = set([1, 2, 2, 3]) # 去重：{1, 2, 3}
   s3 = set() # 空集合
   # 错误方式
   s4 = {} # 这是空字典！
```

3. 集合运算

```python
A = {1, 2, 3}
B = {3, 4, 5}
A | B # 并集: {1, 2, 3, 4, 5}
A & B # 交集: {3}
A - B # 差集: {1, 2}
A ^ B # 对称差集: {1, 2, 4, 5} 4. 性能优势
查找速度快 - O(1)时间复杂度
去重高效 - 自动处理重复元素
集合运算快 - 专门的优化算法
```

4. 适用场景

   - 数据去重 - 快速去除重复项
   - 成员测试 - 快速判断元素是否存在
   - 数学运算 - 集合交并差运算
   - 关系分析 - 找出共同元素、差异元素

5. 注意事项

   - 只能存储不可变类型（可哈希对象）
   - 元素顺序不固定
   - 空集合必须用 set()创建
   - 集合是处理唯一性数据和数学运算的强大工具！

## 3.1 集合的定义

集合（set）是 Python 中的一种数据类型，用于存储多个元素。集合中的元素是无序的，且元素不能重复。

集合的定义方式有两种：

1. 使用花括号 `{}` 包裹元素，元素之间用逗号 `,` 分隔。
2. 使用 `set()` 函数将其他数据类型转换为集合。

例如：

```python
# 方法1: 花括号直接创建
set1 = {1, 2, 3, 4, 5}
print(f"直接创建: {set1}")

# 方法2: set()构造函数
set2 = set([1, 2, 3, 2, 1, 4])  # 从列表创建，自动去重
set3 = set("hello")             # 从字符串创建
print(f"从列表创建: {set2}")
print(f"从字符串创建: {set3}")

# 方法3: 集合推导式
set4 = {x for x in range(10) if x % 2 == 0}
print(f"集合推导式: {set4}") # {0, 2, 4, 6, 8}

# 空集合（必须用set()，{}创建的是空字典）
empty_set = set()
empty_dict = {}
print(f"空集合: {empty_set}, 类型: {type(empty_set)}")
print(f"空字典: {empty_dict}, 类型: {type(empty_dict)}")

# 不可变集合 frozenset()
frozen_set = frozenset([1, 2, 3, 4, 5])
print(f"不可变集合: {frozen_set}, 类型: {type(frozen_set)}")
```

## 3.2 集合的基本操作

```python
numbers = {1, 2, 3, 4, 5, 6, 7, 8, 9, 10}
print(f"原始集合: {numbers}")
```

### 3.2.1 添加元素

添加元素到集合中可以使用 `add()` 方法或 `update()` 方法。

```python
# 添加元素
numbers.add(11) # 添加单个元素
numbers.add(3)  # 重复元素不会添加
print(f"添加后: {numbers}")
# 批量添加
numbers.update([12, 13, 14]) # 添加多个元素
print(f"批量添加后: {numbers}")
```

### 3.2.2 删除元素

删除元素可以使用 `remove()` 方法、`discard()` 方法或 `pop()` 方法。`discard()`方法在元素不存在时不会抛出错误。

```python
# 删除元素
numbers.remove(1)    # 删除存在的元素
numbers.discard(100) # 删除不存在的元素不会报错
print(f"删除后: {numbers}")

# 随机删除并返回一个元素
popped = numbers.pop()
print(f"随机删除: {popped}, 剩余: {numbers}")
# 清空集合
numbers.clear()
print(f"清空后: {numbers}")
#======================================================
# 删除元素
numbers.remove(1) # 删除指定元素，元素不存在会抛出KeyError
print(f"删除1后: {numbers}")
numbers.discard(2) # 删除指定元素，元素不存在不会抛出错误
print(f"删除2后: {numbers}")
numbers.pop() # 随机删除一个元素
print(f"随机删除一个元素后: {numbers}")
numbers.clear() # 清空集合
print(f"清空集合后: {numbers}")
```

## 3.3 集合的运算

集合的运算包括并集、交集、差集和对称差集等。

```python
setA = {1, 2, 3, 4, 5}
setB = {4, 5, 6, 7, 8}
print(f"集合A: {setA}")
print(f"集合B: {setB}")
```

### 3.3.1 并集（Union）

并集（Union）是指集合 A 和集合 B 中所有不同的元素。

```python
# 并集 (union)
union_set = setA | setB
union_set2 = setA.union(setB)
print(f"并集 (A | B): {union_set}") # {1, 2, 3, 4, 5, 6, 7, 8}
```

### 3.3.2 交集（Intersection）

交集（Intersection）是指集合 A 和集合 B 中都存在的元素。

```python
intersection_set = setA & setB
intersection_set2 = setA.intersection(setB)
print(f"交集 (A & B): {intersection_set}") # {4, 5}
```

### 3.3.3 差集（Difference）

差集（Difference）是指集合 A 中存在但集合 B 中不存在的元素。

```python
difference_set = setA - setB
difference_set2 = setA.difference(setB)
print(f"差集 (A - B): {difference_set}") # {1, 2, 3}
```

### 3.3.4 对称差集（Symmetric Difference）

对称差集（Symmetric Difference）是指集合 A 和集合 B 中所有不同的元素，但不包括两者共有的元素。

```python
sym_diff_set = setA ^ setB
sym_diff_set2 = setA.symmetric_difference(setB)
print(f"对称差集 (A ^ B): {sym_diff_set}")
```

### 3.3.5 子集和超集判断

子集（Subset）是指集合 A 中的所有元素都在集合 B 中。
超集（Superset）是指集合 B 中的所有元素都在集合 A 中。

判断子集和超集可以使用 `issubset()` 和 `issuperset()` 方法。
判断交集是否为空可以使用 `isdisjoint()` 方法。

```python
# 子集和超集判断
setC = {2, 3}
print(f"{setC} 是 {setA} 的子集: {setC.issubset(setA)}")
print(f"{setA} 是 {setC} 的超集: {setA.issuperset(setC)}")
print(f"{setA} 和 {setB} 有交集: {setA.isdisjoint(setB)}")
```

### 3.3.6 集合比较操作

集合的比较操作包括相等性比较、子集比较和超集比较。

```python
set1 = {1, 2, 3}
set2 = {1, 2, 3, 4, 5}
set3 = {1, 2, 3}
set4 = {4, 5, 6}

# 相等性比较
print(f"{setD} == {setE}: {setD == setE}") # True
print(f"{setD} != {setF}: {setD != setF}") # True

# 子集判断
print(f"set1 ⊆ set2: {set1.issubset(set2)}")
print(f"set2 ⊇ set1: {set2.issuperset(set1)}")
# 真子集判断
print(f"set1 ⊂ set2: {set1 < set2}")
print(f"set2 ⊃ set1: {set2 > set1}")

# 无交集判断
print(f"set1 和 set4 无交集: {set1.isdisjoint(set4)}")
```

## 3.4 集合的方法

```python
original = {1, 2, 3, 4, 5}
other = {4, 5, 6, 7, 8}
print(f"原始集合: {original}")
print(f"其他集合: {other}")
```

### 3.4.1 修改原集合方法

修改原集合的方法包括添加元素、删除元素和清空集合。

```python
# 修改原集合的方法
set_copy = original.copy()
print(f"集合: {set_copy}")
```

### 3.4.2 update()方法

#### 3.4.2.1 update()方法 - 并集更新

`update()` 方法用于将一个或多个元素添加到集合中。如果元素已经存在于集合中，则不会重复添加。

```python
# 添加元素
set_copy.update(other)
print(f"update后: {set_copy}")  # {1, 2, 3, 4, 5, 6, 7, 8}
```

#### 3.4.2.2 intersection_update() - 交集更新

`intersection_update()` 方法用于将集合中的元素更新为与另一个集合的交集。

```python
set_copy = original.copy()
# intersection_update() - 交集更新
set_copy.intersection_update(other)
print(f"intersection_update后: {set_copy}") # {4, 5}
```

#### 3.4.2.3 difference_update() - 差集更新

`difference_update()` 方法用于将集合中的元素更新为与另一个集合的差集。

```python
set_copy = original.copy()
# difference_update() - 差集更新
set_copy.difference_update(other)
print(f"difference_update后: {set_copy}") # {1, 2, 3}
```

#### 3.4.2.4 symmetric_difference_update() - 对称差集更新

`symmetric_difference_update()` 方法用于将集合中的元素更新为与另一个集合的对称差集。

```python
set_copy = original.copy()
# symmetric_difference_update() - 对称差集更新
set_copy.symmetric_difference_update(other)
print(f"symmetric_difference_update后: {set_copy}") # {1, 2, 3, 6, 7, 8}
```

## 3.5 集合推导式

集合推导式（Set Comprehension）是使用类似于列表推导式的方式创建集合的一种方法。

### 3.5.1 基本推导式与带条件的推导式

```python
# 基本推导式
squares = {x**2 for x in range(1, 6)}
print(f"平方集合: {squares}")

# 带条件的推导式
even_squares = {x**2 for x in range(1, 11) if x % 2 == 0}
print(f"偶数的平方: {even_squares}")
```

### 3.5.6 字符串处理

字符串处理唯一字符

```python
# 从字符串处理
words = ["hello", "world", "python", "programming"]
unique_chars = {char for word in words for char in word}
print(f"所有单词的唯一字符: {unique_chars}")
# {'h', 'e', 'l', 'o', 'w', 'r', 'd', 'p', 'y', 't', 'n', 'g', 'a', 'm'}
```

### 3.5.7 数据清洗示例

数据清洗指的是处理和清理数据，使其适合进一步分析或处理。以下是一个简单的数据清洗示例，演示如何使用集合来去除重复项。

```python
numbers_with_duplicates = [1, 2, 2, 3, 4, 4, 4, 5, 6, 6]
unique_numbers = {x for x in numbers_with_duplicates if x % 2 == 0}
print(f"原始列表: {numbers_with_duplicates}")
print(f"唯一偶数: {unique_numbers}") # {2, 4, 6}
```

## 3.6 集合实用案例

### 3.6.1 数据去重 - 去除列表中的重复元素

数据去重是指从数据集中去除重复的元素，只保留唯一的元素。

```python
numbers = [1, 2, 2, 3, 4, 4, 4, 5, 6, 6, 6, 6]
unique_numbers = set(numbers)
print(f"原始列表: {numbers}")
print(f"去重后: {unique_numbers}")
print(f"转回列表: {list(unique_numbers)}")
```

### 3.6.2 找出两个列表的共同元素

找出两个列表中同时存在的元素。

```python
list1 = [1, 2, 3, 4, 5]
list2 = [4, 5, 6, 7, 8]
common = set(list1) & set(list2)
print(f"列表1: {list1}")
print(f"列表2: {list2}")
print(f"共同元素: {common}")
```

### 3.6.3 找出只在其中一个列表中的元素

找出只在其中一个列表中出现的元素。

```python
unique_to_list1 = set(list1) - set(list2)
unique_to_list2 = set(list2) - set(list1)
print(f"只在列表1: {unique_to_list1}") # {1, 2, 3}
print(f"只在列表2: {unique_to_list2}") # {6, 7, 8}
```

### 3.6.4 投票统计

投票统计是指统计一组投票结果中每个候选人的得票数。

```python
votes = ["Alice", "Bob", "Alice", "Charlie", "Bob", "Alice", "David"]
candidates = set(votes)
print(f"候选人: {candidates}")
for candidate in candidates:
    count = votes.count(candidate)
    print(f"  {candidate}: {count}票")
```

### 3.6.5 集合与列表比较

集合与列表的查找速度比较（集合比列表快很多）

```python
large_set = set(range(1000000))
large_list = list(range(1000000))

import time
start_time = time.time()
_ = 999999 in large_set
set_time = time.time() - start_time

start_time = time.time()
_ = 999999 in large_list
list_time = time.time() - start_time

print(f"集合查找时间: {set_time*1000:.4f}毫秒")
print(f"列表查找时间: {list_time*1000:.4f}毫秒")
print(f"集合比列表快 {list_time / set_time:.0f} 倍")
```

## 3.7 集合的局限性

集合的主要局限性是它不支持索引和切片操作，因为集合是无序的。此外，集合中的元素必须是可哈希的，这意味着它们必须是不可变的。

### 3.7.1 集合只能包含不可变元素

集合只能包含不可变元素，因为集合中的元素需要是可哈希的。这意味着集合不能包含列表或字典等可变对象。

```python
valid_set = {1, 2, 3, "hello", (4, 5)}
print(f"有效集合: {valid_set}")

# 尝试包含可变元素会报错
try:
    invalid_set = {1, 2, [3, 4]}  # 列表是可变的
except TypeError as e:
    print(f"错误: {e}")
```

### 3.7.2 集合是无序的

集合是无序的，这意味着元素的顺序可能会在每次迭代时改变。

```python
set_a = {3, 1, 4, 1, 5, 9, 2}
set_b = {1, 2, 3, 4, 5, 9}
print(f"set_a: {set_a}")
print(f"set_b: {set_b}")
print(f"虽然显示顺序不同，但set_a == set_b: {set_a == set_b}")
```

## 3.8 总结

> 集合是一种无序且元素唯一的集合数据类型，它提供了许多有用的操作，如并集、交集、差集和对称差集等。集合推导式是一种创建集合的简洁方法，而集合的实用案例包括数据去重、找出共同元素、找出唯一元素等。集合的局限性包括它不支持索引和切片操作，以及只能包含不可变元素。

- 无序、不重复元素的集合
- 可变集合(set)和不可变集合(frozenset)
- 支持数学集合运算: 并集、交集、差集、对称差集
- 查找速度极快(O(1))，基于哈希表实现
- 只能包含不可变(可哈希)元素
- 主要用途: 去重、成员测试、数学运算
- 常用方法: add(), remove(), union(), intersection(), difference()
