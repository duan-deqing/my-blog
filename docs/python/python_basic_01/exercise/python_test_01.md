# Python 练习题目

## 练习题 1：变量与数据类型

题目：创建 3 个变量，分别存储你的姓名（字符串）、年龄（整数）、身高（浮点数），然后用 f-string 格式化输出：“我叫 XXX，今年 XX 岁，身高 XX 米”。

提示：注意变量类型的正确定义，f-string 中直接用{变量名}嵌入。

```python
name = "张三"
age = 18
height = 1.75
print(f"我叫{name}，今年{age}岁，身高{height}米")
```

## 练习题 2：算术运算与格式化

题目：用户输入两个整数 a 和 b，计算并输出：
a + b 的和
a 的 b 次方（用`**`）
a 除以 b 的商（保留 2 位小数）
提示：用 input()获取输入后，用 int()转换类型，除法结果用 round(结果, 2)或 f-string 的:.2f 控制小数位数。

```python
a = int(input("输入整数a："))
b = int(input("输入整数b："))
print(f"和：{a + b}")
print(f"a的b次方：{a **b}")
print(f"商（保留2位）：{a / b:.2f}")
```

## 练习题 3：条件判断（if-else）

题目：用户输入一个整数，判断它是正数、负数还是零，并输出对应结果（如 “你输入的是正数”）。
提示：用 if-elif-else 结构，条件分别为>0、<0、==0。

```python
num = int(input("输入一个整数："))
if num > 0:
    print("你输入的是正数")
elif num < 0:
    print("你输入的是负数")
else:
    print("你输入的是零")
```

## 练习题 4：取余运算的应用

题目：用户输入一个年份，判断该年份是否为闰年。闰年规则：能被 4 整除但不能被 100 整除，或者能被 400 整除。
提示：用%运算符判断整除（如 year % 4 == 0），结合 and、or 逻辑运算符。

```python
year = int(input("输入年份："))
if (year % 4 == 0 and year % 100 != 0) or (year % 400 == 0):
    print(f"{year}是闰年")
else:
    print(f"{year}不是闰年")
```

## 练习题 5：字符串操作

题目：用户输入一个英文单词（全小写），输出该单词的首字母大写形式（如输入 “apple”，输出 “Apple”）。
提示：字符串有 capitalize()方法，或用索引取首字母 +upper()，再拼接剩余部分（如 s[0].upper() + s[1:]）。

```python
word = input("输入英文单词（全小写）：")
print(word.capitalize())  # 或 print(word[0].upper() + word[1:])
```

## 练习题 6：列表基础

题目：创建一个包含 5 个整数的列表，计算列表中所有元素的总和和平均值，并输出。
提示：用 sum(列表)求总和，len(列表)求长度，平均值 = 总和 / 长度。

```python
nums = [10, 20, 30, 40, 50]
total = sum(nums)
avg = total / len(nums)
print(f"总和：{total}，平均值：{avg}")
```

## 练习题 7：循环（for）与 range

题目：打印 1 到 10 中所有的奇数（1、3、5、7、9）。
提示：用 range(1, 11, 2)生成奇数序列，再用 for 循环遍历打印。

```python
for i in range(1, 11, 2):
    print(i)
```

## 练习题 8：综合应用（简易 BMI 计算器）

题目：用户输入身高（米，如 1.75）和体重（公斤，如 65），计算 BMI 指数（BMI = 体重 / 身高 ²），并根据以下标准输出结果：
BMI < 18.5：偏瘦
18.5 ≤ BMI < 24：正常
BMI ≥ 24：偏胖
提示：先转换输入为浮点数，计算后用 if-elif-else 判断区间。

```python
height = float(input("身高（米）："))
weight = float(input("体重（公斤）："))
bmi = weight / (height** 2)
if bmi < 18.5:
    print(f"BMI={bmi:.1f}，偏瘦")
elif bmi < 24:
    print(f"BMI={bmi:.1f}，正常")
else:
    print(f"BMI={bmi:.1f}，偏胖")
```

## 练习题 9：异常处理（try-except）

题目：让用户输入一个整数，若输入的不是整数（如字母、符号），则提示 “输入错误，请重新输入”，直到输入正确为止。
提示：用 while True 循环，在 try 块中用 int()转换，except ValueError 捕获错误并提示。

```python
while True:
    try:
        num = int(input("输入一个整数："))
        print(f"你输入的整数是：{num}")
        break
    except ValueError:
        print("输入错误，请重新输入")
```

## 练习题 10：字典基础

题目：创建一个存储学生信息的字典，包含 “姓名”“年龄”“成绩” 三个键，值分别为你的名字、年龄、一个整数分数。然后：
打印该学生的成绩
将年龄修改为 “年龄 + 1”
新增一个键 “班级”，值为 “三年级 2 班”
打印修改后的完整字典
提示：字典用{key: value}定义，修改值用 dict[key] = 新值，新增键同理。

```python
student = {"姓名": "李四", "年龄": 12, "成绩": 90}
print("成绩：", student["成绩"])
student["年龄"] += 1  # 修改年龄
student["班级"] = "三年级2班"  # 新增键
print("修改后：", student)
```
