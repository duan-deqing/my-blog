# Python 流程控制语句

## 运算符

1. 比较运算符
   `== != > < >= <=`
2. 逻辑运算符
   `and(与) or(或) not(非)`
3. 三目运算符
   `if-elif-else`

## 条件语句

1. if 判断

```python
score = 85
# 简单的if语句
if score >= 60:
   print("成绩及格")
```

2. if-else

```python
# if-else语句
if score >= 90:
   print("优秀")
else:
   print("还需努力")
```

3. if 嵌套

```python
# 嵌套if语句
age = 20
is_student = True

if age >= 18:
   if is_student:
      print("成年学生")
   else:
      print("成年非学生")
else:
   print("未成年人")
```

## 循环语句

1. while 循环

```python
# 基础while循环
count = 1
print("计数1-5:")
while count <= 5:
   print(f"  当前计数: {count}")
   count += 1  # 重要：不要忘记更新条件变量
```

2. for 循环

```python
# 遍历列表
fruits = ["苹果", "香蕉", "橙子", "梨"]
print("水果列表:")
for fruit in fruits:
   print(f"  - {fruit}")

# 遍历字典
student = {"姓名": "小明", "年龄": 18, "班级": "高三(1)班"}
print("学生信息:")
for key, value in student.items():
   print(f"  {key}: {value}")
```

## 循环控制语句

1. break

```python
# break语句 - 完全退出循环
print("break示例(遇到3退出):")
for i in range(1, 6):
   if i == 3:
      break
   print(f"  {i}", end=" ")
print()
```

2. continue

```python
# continue语句 - 跳过当前迭代
print("continue示例(跳过偶数):")
for i in range(1, 6):
   if i % 2 == 0:
      continue  # 跳过偶数
   print(f"  {i}", end=" ")
print()
```

3. else

```python
# else语句 - 循环正常结束执行
print("for-else示例:")
for i in range(3):
   print(f"  循环第{i+1}次")
else:
   print("  循环正常结束!")

print("break时的else:")
for i in range(3):
   if i == 1:
      break
   print(f"  循环第{i+1}次")
else:
   print("  这行不会执行!")
```
