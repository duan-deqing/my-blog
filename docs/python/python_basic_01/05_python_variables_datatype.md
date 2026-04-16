# 05 变量与数据类型

## 变量

1. 变量定义与本质：程序中用于存储数值的名称，作为内存地址的标签

2. 变量命名规则：
   - 以字母或下划线开头，可接字母、数字或下划线
   - 避免使用 Python 关键字，且对大小写敏感
   - 推荐使用有意义的名称，遵循下划线命名法，如，student_name

在 python 中，变量定义不需要声明类型，直接赋值即可

## 数据类型

1. 整数（int）: 包括正整数、负整数和零，没有小数部分
2. 浮点数（float）: 浮点数可以表示小数，用于需要小数精确度的计算。
3. 字符串（str）: 用于存储文本数据，由单引号或双引号括起。
4. 列表（list）: 列表是有序的元素集合，可以包含不同类型的元素。支持元素的添加、删除和修改，是最常用的数据结构。
5. 字典（dict）: 字典是键值对集合，键唯一，用于存储映射关系。适用于需要快速查找和更新的场景。
6. 布尔型（bool）: 布尔型只有 True 和 False 两个值，用于逻辑判断

### 数字类型

整数(int)、 浮点数(float)、复数(complex)

### 字符串类型

```python
str1 = '单引号字符串'
str2 = "双引号字符串"
str3 = """
   多行
   字符串
   字符串
"""
str4 = "Hello Python"

```

### 布尔类型

只有 True 和 False 两个值
布尔运算 `and、 or、 not`

### 容器类型

1. 列表 - 有序、可变

```python
fruits = ["苹果", "香蕉", "橙子", "梨"]
numbers = [1, 2, 3, 4, 5]
mixed_list = [1, "hello", 3.14, True]
# 索引访问
print(f"第二个水果: {fruits[1]}")

```

2. 元组 - 有序、不可变

```python
coordinates = (10, 20)
colors = ("红色", "绿色", "蓝色")
single_tuple = (5,)  # 单元素元组需要逗号

```

3. 字典 - 无序、键值对

```python
student = {
    "name": "张三",
    "age": 18,
    "grade": "高三",
    "scores": [85, 92, 78]
}
print(f"学生信息: {student}")
print(f"姓名: {student['name']}") # 访问指定键的值
print(f"年龄: {student.get('age')}") # 获取指定键的值
```

4. 集合 - 无序、不重复（唯一性）

```python
unique_numbers = {1, 2, 3, 2, 1, 4}  # 自动去重
fruits_set = {"苹果", "香蕉", "橙子"}

print(f"数字集合: {unique_numbers}")
# 输出: {1, 2, 3, 4}
print(f"水果集合: {fruits_set}")

```

### 数据类型转换

```python
num_str = "123"
num_int = int(num_str)      # 字符串转整数
int_float = float(100)      # 整数转浮点数
float_str = str(3.14)       # 浮点数转字符串

```

### 变量操作

```python
# 多重赋值
x, y, z = 1, 2, 3
print(f"多重赋值: x={x}, y={y}, z={z}")

# 变量交换
a, b = 10, 20
a, b = b, a  # 交换值
print(f"交换后: a={a}, b={b}")

# 链式赋值
c = d = e = 100
print(f"链式赋值: c={c}, d={d}, e={e}")
```

### 总结

1. 变量无需声明类型，直接赋值
2. 基本类型: int, float, str, bool
3. 容器类型: list, tuple, dict, set
4. 使用 type() 查看变量类型
5. 使用 int(), str() 等进行类型转换
