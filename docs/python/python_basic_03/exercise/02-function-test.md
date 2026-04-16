# Python 函数使用练习题

## 一、基础函数题

### 题目 1：数学计算函数

```python
"""
编写以下数学函数：
1. calculate_circle(radius): 计算圆的面积和周长，返回元组(面积, 周长)
2. is_prime(n): 判断一个数是否为质数
3. factorial(n): 计算阶乘（使用循环和递归两种方式）
4. gcd(a, b): 计算两个数的最大公约数
"""

# 测试用例
print(calculate_circle(5))    # 应该返回 (78.54, 31.42) 约等
print(is_prime(17))           # 应该返回 True
print(factorial(5))           # 应该返回 120
print(gcd(48, 18))            # 应该返回 6

```

### 题目 2：字符串处理函数

```python
"""
编写字符串处理函数：
1. count_vowels(text): 统计字符串中元音字母的数量
2. reverse_words(sentence): 反转句子中的单词顺序
3. is_palindrome(text): 判断字符串是否为回文
4. format_phone_number(number): 将10位数字格式化为电话号码 (123) 456-7890
"""

# 测试用例
print(count_vowels("Hello World"))        # 应该返回 3
print(reverse_words("Python is fun"))     # 应该返回 "fun is Python"
print(is_palindrome("racecar"))           # 应该返回 True
print(format_phone_number("1234567890"))  # 应该返回 "(123) 456-7890"
```

## 二、参数使用题

### 题目 3：灵活的参数函数

```python
python
"""
编写以下函数，练习不同参数类型的使用：
1. create_student(name, age, **kwargs): 
	- 创建学生信息字典，包含必填的name, age和任意其他信息
2. calculate_stats(*numbers):
	- 接收任意数量的数字，返回字典包含：总和、平均值、最大值、最小值
3. format_text(text, width=80, justify='left', fill_char=' '):
	- 格式化文本，支持不同的对齐方式和填充字符
"""

# 测试用例
student = create_student("Alice", 20, major="CS", grade="A")
stats = calculate_stats(1, 2, 3, 4, 5)
formatted = format_text("Hello", width=10, justify='center', fill_char='\*')
```

### 题目 4：默认参数和关键字参数

```python
python
"""
编写配置处理函数：
1. create_config(host, port, timeout=30, retries=3, \*\*extra):
	- 创建配置字典，有合理的默认值
2. send_email(to, subject, body, cc=None, bcc=None, attachments=None):
	- 发送邮件函数，支持可选参数
"""

# 测试用例
config = create_config("localhost", 8080, retries=5, debug=True)
send_email("user@example.com", "Hello", "Test email", cc=["admin@example.com"])
```

## 三、返回值题

### 题目 5：多返回值函数

```python
"""
编写返回多个值的函数：
1. analyze_numbers(numbers): 
	- 返回(总和, 平均值, 中位数, 众数)
2. parse_date(date_string):
	- 解析日期字符串，返回(年, 月, 日)
3. solve_quadratic(a, b, c):
	- 解一元二次方程，返回两个解（考虑无实根情况）
"""

# 测试用例
total, avg, median, mode = analyze_numbers([1, 2, 3, 4, 5, 5])
year, month, day = parse_date("2024-01-15")
x1, x2 = solve_quadratic(1, -3, 2) # x² - 3x + 2 = 0
```



## 四、高级函数题

### 题目 6：Lambda 和高阶函数

```python
python
"""
使用 lambda 和高阶函数：
1. 使用 map 将温度列表从摄氏度转换为华氏度
2. 使用 filter 找出列表中的所有质数
3. 使用 sorted 按字符串长度和字母顺序排序
4. 使用 reduce 计算列表元素的乘积
"""

# 数据
celsius_temps = [0, 20, 30, 40, 100]
numbers = [1, 2, 3, 4, 5, 6, 7, 8, 9, 10, 11, 12, 13]
words = ["apple", "banana", "cherry", "date", "elderberry"]
```



### 题目 7：装饰器应用

```python
python
"""
编写以下装饰器：
1. timer: 测量函数执行时间
2. logger: 记录函数调用和参数
3. retry: 函数失败时重试指定次数
4. cache: 缓存函数结果，避免重复计算
"""

@timer
@logger
def expensive_calculation(n):
    import time
    time.sleep(1)
    return n * n

@retry(times=3, delay=1)
def unstable_network_call(): 
    # 模拟不稳定的网络调用
    import random
    if random.random() < 0.7:
    	raise ConnectionError("Network error")
    return "Success"

@cache
def fibonacci(n):
    if n <= 1:
    	return n
    return fibonacci(n-1) + fibonacci(n-2)
```



## 五、递归函数题

### 题目 8：递归算法

```python
"""
使用递归解决以下问题：
1. fibonacci(n): 计算第 n 个斐波那契数
2. factorial(n): 计算阶乘
3. binary_search(arr, target): 二分查找
4. tower_of_hanoi(n, source, target, auxiliary): 汉诺塔问题
5. flatten(nested_list): 扁平化嵌套列表
"""

# 测试用例
print(fibonacci(10)) # 55
print(factorial(5)) # 120
arr = [1, 3, 5, 7, 9, 11]
print(binary_search(arr, 7)) # 应该返回 3
nested = [1, [2, [3, 4], 5], 6]
print(flatten(nested)) # 应该返回 [1, 2, 3, 4, 5, 6]
```



## 六、生成器题

### 题目 9：生成器函数

```python
"""
编写生成成器函数：
1. count_up_to(n): 生成从 1 到 n 的数字
2. fibonacci_generator(): 无限生成斐波那契数列无限生成斐波那契数列无限生成斐波那契数列无限生成斐波那契数列
3. read_large_file(filename): 逐行读取大文件
4. batch_processor(data, batch_size): 分批处理数据
"""

# 测试用例
for num in count_up_to(5):
	print(num) # 输出 1, 2, 3, 4, 5

fib = fibonacci_generator()
for i in range(10):
	print(next(fib)) # 输出前 10 个斐波那契数
```



## 七、综合应用题

### 题目 10：学生成绩管理系统

```python
"""
用函数实现学生成绩管理系统：
1. add_student(students, student_id, name, **scores): 添加学生
2. get_student(students, student_id): 获取学生信息
3. update_score(students, student_id, subject, score): 更新成绩
4. calculate_average(students, student_id): 计算学生平均分
5. get_class_average(students, subject): 计算班级某科目平均分
6. get_top_students(students, n=3): 获取前n名优秀学生
"""

# 数据结构示例
students = {
    '001': {'name': 'Alice', 'scores': {'math': 85, 'english': 92}},
    '002': {'name': 'Bob', 'scores': {'math': 78, 'english': 88}}
}
```



### 题目 11：银行账户系统

```python
"""
用函数实现简单的银行账户系统：
1. create_account(accounts, account_id, name, initial_balance=0): 创建账户
2. deposit(accounts, account_id, amount): 存款
3. withdraw(accounts, account_id, amount): 取款
4. transfer(accounts, from_id, to_id, amount): 转账
5. get_balance(accounts, account_id): 查询余额
6. get_transaction_history(accounts, account_id): 获取交易记录
   """

# 数据结构示例
accounts = {
    '1001': {
        'name': 'Alice',
        'balance': 1000,
        'transactions': []
    }
}
```



### 题目 12：购物车系统

```python
"""
用函数实现购物车系统：
1. add_to_cart(cart, product_id, name, price, quantity=1): 添加商品
2. remove_from_cart(cart, product_id): 移除商品
3. update_quantity(cart, product_id, quantity): 更新数量
4. calculate_total(cart): 计算总价
5. apply_discount(cart, discount_code): 应用折扣
6. checkout(cart, payment_method): 结账
"""

# 数据结构示例
cart = {
    'p001': {'name': 'Laptop', 'price': 1000, 'quantity': 1},
    'p002': {'name': 'Mouse', 'price': 25, 'quantity': 2}
}
```



## 八、错误处理题

### 题目 13：健壮的函数

```python
"""
为以下函数添加错误处理：
1. safe_divide(a, b): 安全的除法，处理除零错误
2. read_config_file(filename): 读取配置文件，处理文件不存在错误
3. parse_integer(text): 解析整数，处理格式错误
4. connect_to_database(host, port): 数据库连接，处理连接超时
"""

# 测试用例
print(safe_divide(10, 0)) # 应该返回 "Error: Division by zero"
print(parse_integer("abc")) # 应该返回 "Error: Invalid integer format"
```

## 参考答案模板

```python
# 参考答案模板

def calculate_circle(radius):
    """题目1.1：计算圆的面积和周长"""
    import math
    area = math.pi * radius ** 2
    perimeter = 2 * math.pi * radius
    return round(area, 2), round(perimeter, 2)

def is_prime(n):
    """题目1.2：判断质数"""
    if n < 2:
        return False
    for i in range(2, int(n**0.5) + 1):
        if n % i == 0:
            return False
    return True

def factorial(n):
    """题目1.3：计算阶乘（循环版本）"""
    result = 1
    for i in range(1, n + 1):
        result *= i
    return result

def factorial_recursive(n):
    """题目1.3：计算阶乘（递归版本）"""
    if n == 0 or n == 1:
        return 1
    return n * factorial_recursive(n - 1)

def gcd(a, b):
    """题目1.4：计算最大公约数"""
    while b:
        a, b = b, a % b
    return a

# 继续实现其他函数...

if __name__ == "__main__":
    # 测试你的函数
    print("测试calculate_circle:", calculate_circle(5))
    print("测试is_prime:", is_prime(17))
    print("测试factorial:", factorial(5))
    print("测试gcd:", gcd(48, 18))
```

这些题目从基础到高级，涵盖了函数的各种用法和场景。建议按顺序完成，逐步提升难度。每个题目都包含了具体的测试用例，可以帮助你验证函数的正确性。
