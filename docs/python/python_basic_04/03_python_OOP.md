# 03 面向对象（OOP）

---

面向对象编程的核心思想是：把现实世界中的事物抽象成“对象”，并通过这些对象来组织代码。

**对比过程式编程**

- 过程式编程：以函数为中心，按顺序执行代码，适合解决简单问题。
- 面向对象编程：以对象为中心，将数据（属性）和操作数据的方法（行为）封装在一起，适合解决复杂问题。

## 3.0 面向对象核心概念

### 3.0.1 四大支柱

- 封装：隐藏内部实现，提供公共接口
- 继承：子类继承父类的特性
- 多态：相同接口，不同实现
- 抽象：定义接口而不关心具体实现

### 3.0.2 关键概念

- 类：对象的蓝图模板
- 对象：类的具体实例
- 方法：类中定义的函数
- 属性：类或对象的数据
- 构造函数：`__init__` 方法

### 3.0.3 访问控制

- 公有：`默认`，可以在任何地方访问
- 保护：`_single_underline`，约定为内部使用
- 私有：`__double_underline`，名称修饰，无法直接访问

### 3.0.4 特殊方法

- `__init__`：构造函数，初始化对象
- `__str__`：字符串表示
- `__repr__`：官方字符串表示
- `__add__`、`__sub__`：运算符重载

### 3.0.5 装饰器

- `@property`：将方法转换为属性
- `@classmethod`：类方法，依赖类
- `@staticmethod`：静态方法，不依赖类或对象
- `@abstractmethod`：抽象方法，强制子类实现

面向对象编程让代码更模块化、可重用和可维护，是现代软件开发的基础！

## 3.1 类与对象基础

### 3.1.1 定义类

定义类时，使用 `class` 关键字，类名通常使用 `PascalCase` 命名法。

```python
class ClassName: # 类名 使用 PascalCase 命名法
    # 类属性
    class_attribute = "class attribute"

    # 构造函数
    def __init__(self, param1, param2):
        # 实例属性
        self.instance_attribute = param1
        self.instance_attribute = param2
```

定义一个 Dog 类，包含属性和方法：

```python
class Dog:
    # 类属性（所有实例共享）
    species = "Canis familiaris"

    def __init__(self, name, age):
        """初始化方法（构造函数）"""
        # 实例属性（每个实例独有）
        self.name = name
        self.age = age

    # 实例方法
    def bark(self):
        return f"{self.name} 在汪汪叫!"

    def get_info(self):
        return f"{self.name} 是一只 {self.age} 岁的狗"

if __name__ == "__main__":
    # 创建对象（实例化）
    dog1 = Dog("旺财", 3)
    dog2 = Dog("小黑", 5)

    # 访问属性和方法
    print(f"狗的种类: {Dog.species}")
    print(f"dog1的名字: {dog1.name}")
    print(f"dog2的年龄: {dog2.age}")
    print(dog1.bark())
    print(dog2.get_info())

    # 修改属性
    dog1.age = 4
    print(f"修改后dog1的年龄: {dog1.age}")
```

## 3.2 封装

封装是指将数据（属性）和操作数据的方法（行为）封装在一起，提供公共接口，隐藏内部实现。

### 3.2.1 访问控制

- 公有：默认，可以在任何地方访问
- 保护：`_single_underline`，约定为内部使用，单个下划线
- 私有：`__double_underline`，名称修饰，无法直接访问，两个下划线

```python
class Person:
    def __init__(self, name, age):
        self.name = name  # 公有属性
        self._age = age  # 保护属性
        self.__salary = 5000  # 私有属性

    def get_salary(self):
        return self.__salary

if __name__ == "__main__":
    person = Person("张三", 30)
    print(person.name)  # 访问公有属性
```

### 3.2.2 getter 和 setter

使用 `@property` 装饰器定义 getter 和 setter 方法，实现属性的封装。

```python
class Person:
    def __init__(self, name, age):
        self.name = name
        self._age = age

    @property
    def age(self):
        return self._age

    @age.setter
    def age(self, value):
        if value < 0:
            raise ValueError("年龄不能为负数")
        self._age = value

if __name__ == "__main__":
    person = Person("张三", 30)
    print(person.age)  # 获取属性
    person.age = 31  # 设置属性
    print(person.age)
```

### 3.2.3 封装示例

定义一个 BankAccount 类，实现存款、取款、查询余额等功能。

```python
class BankAccount:
    """银行账户类 - 封装示例"""

    def __init__(self, account_holder, initial_balance=0):
        self.account_holder = account_holder
        self.__balance = initial_balance  # 私有属性

    def deposit(self, amount):
        """存款"""
        if amount > 0:
            self.__balance += amount
            print(f"存款成功! 当前余额: {self.__balance}")
        else:
            print("存款金额必须大于0")

    def withdraw(self, amount):
        """取款"""
        if 0 < amount <= self.__balance:
            self.__balance -= amount
            print(f"取款成功! 当前余额: {self.__balance}")
        else:
            print("取款金额无效或余额不足")

    def get_balance(self):
        """获取余额（公共接口）"""
        return self.__balance

    # 使用属性装饰器提供更好的接口
    @property
    def balance(self):
        """余额属性（只读）"""
        return self.__balance

if __name__ == "__main__":
    # 使用银行账户
    account = BankAccount("张三", 1000)
    account.deposit(500)
    account.withdraw(200)

    # 无法直接访问私有属性
    # print(account.__balance)  # 这会报错
    print(f"通过方法获取余额: {account.get_balance()}")
    print(f"通过属性获取余额: {account.balance}")
```

## 3.3 继承

继承是指一个类（子类）继承另一个类（父类）的属性和方法，实现代码的复用。
super() 函数用于调用父类的方法，子类可以通过调用 super()函数调用父类的构造函数来初始化从父类继承的属性。

### 3.3.1 继承语法

使用 `class ChildClass(ParentClass)` 语法实现继承。

```python
class ParentClass:
    # 父类属性和方法

class ChildClass(ParentClass):
    # 子类属性和方法
```

### 3.3.2 方法重写（多态）

子类可以重写父类的方法，实现自己的逻辑。

```python
# 父类
class Animal:
    def speak(self):
        raise NotImplementedError("子类必须实现 speak 方法")

# 子类
class Dog(Animal):
    def speak(self):
        return "汪汪汪"

class Cat(Animal):
    def speak(self):
        return "喵喵喵"

if __name__ == "__main__":
    dog = Dog()
    cat = Cat()

    print(dog.speak())
    print(cat.speak())
```

### 3.3.3 继承示例

定义一个 Animal 类，包含属性和方法，再定义 Dog 和 Cat 类继承 Animal 类。

```python
# 父类（基类）
    class Animal:
        """动物类"""

        def __init__(self, name, age):
            self.name = name
            self.age = age

        def eat(self):
            return f"{self.name} 在吃东西"

        def sleep(self):
            return f"{self.name} 在睡觉"

        def make_sound(self):
            return "动物发出声音"

    # 子类（派生类）
    class Cat(Animal):
        """猫类 - 继承自动物类"""

        def __init__(self, name, age, color):
            super().__init__(name, age)  # 调用父类的初始化方法
            self.color = color

        # 方法重写（多态）
        def make_sound(self):
            return f"{self.name} 在喵喵叫"

        # 子类特有的方法
        def climb_tree(self):
            return f"{self.name} 在爬树"

    class Dog(Animal):
        """狗类 - 继承自动物类"""

        def __init__(self, name, age, breed):
            super().__init__(name, age) # 调用父类的初始化方法
            self.breed = breed

        def make_sound(self):
            return f"{self.name} 在汪汪叫"

        def fetch(self):
            return f"{self.name} 在接飞盘"

if  __name__ == "__main__":
    # 使用继承的类
    cat = Cat("咪咪", 2, "白色")
    dog = Dog("大黄", 3, "金毛")

    print(cat.eat())           # 继承自父类的方法
    print(cat.make_sound())    # 重写的方法
    print(cat.climb_tree())    # 子类特有的方法

    print(dog.sleep())         # 继承自父类的方法
    print(dog.make_sound())    # 重写的方法
    print(dog.fetch())         # 子类特有的方法

    # 类型检查
    print(f"cat是Animal的实例: {isinstance(cat, Animal)}")
    print(f"Dog是Animal的子类: {issubclass(Dog, Animal)}")
```

## 3.4 多态

多态是指不同类的对象可以调用相同的方法，实现不同的行为。

### 3.4.1 多态示例

```python
class Animal:
    def speak(self):
        raise NotImplementedError("子类必须实现 speak 方法") # 抽象方法

class Dog(Animal):
    def speak(self):
        return "汪汪汪"

class Cat(Animal):
    def speak(self):
        return "喵喵喵"

def animal_sound(animal):
    print(animal.speak())

if __name__ == "__main__":
    dog = Dog()
    cat = Cat()
    animal_sound(dog)  # 输出: 汪汪汪
    animal_sound(cat)  # 输出: 喵喵喵
```

### 3.4.2 多态演示

定义 Shape 类、Circle 类、Rectangle 类和 Triangle 类，实现多态。

```python
class Shape:
    """形状基类"""

    def area(self):
        """计算面积（抽象方法）"""
        raise NotImplementedError("子类必须实现area方法")

    def perimeter(self):
        """计算周长（抽象方法）"""
        raise NotImplementedError("子类必须实现perimeter方法")

class Rectangle(Shape):
    """矩形类"""

    def __init__(self, width, height):
        self.width = width
        self.height = height

    def area(self):
        return self.width * self.height

    def perimeter(self):
        return 2 * (self.width + self.height)

class Circle(Shape):
    """圆形类"""

    def __init__(self, radius):
        self.radius = radius

    def area(self):
        import math
        return math.pi * self.radius ** 2

    def perimeter(self):
        import math
        return 2 * math.pi * self.radius

class Triangle(Shape):
    """三角形类"""

    def __init__(self, a, b, c):
        self.a = a
        self.b = b
        self.c = c

    def area(self):
        # 使用海伦公式
        s = self.perimeter() / 2
        return (s * (s - self.a) * (s - self.b) * (s - self.c)) ** 0.5

    def perimeter(self):
        return self.a + self.b + self.c

if __name__ == "__main__":
    # 多态演示 - 相同的接口，不同的实现
    shapes = [
        Rectangle(4, 5),
        Circle(3),
        Triangle(3, 4, 5)
    ]

    for shape in shapes:
        print(f"{shape.__class__.__name__}:")
        print(f"  面积: {shape.area():.2f}")
        print(f"  周长: {shape.perimeter():.2f}")
```

## 3.5 类方法与静态方法

### 3.5.1 类方法

类方法使用 `@classmethod` 装饰器，第一个参数是类本身，通常命名为 `cls`。

```python
class MyClass:
    class_variable = 0

    @classmethod
    def class_method(cls):
        print(f"This is a class method. Class variable: {cls.class_variable}")

    def instance_method(self):
        print("This is an instance method.")

if __name__ == "__main__":
    MyClass.class_method()  # 调用类方法
    obj = MyClass()
    obj.instance_method()  # 调用实例方法
```

类方法演示：

```py
class Student:
    """学生类"""
    # 类属性
    school = "某某中学"
    total_students = 0

    def __init__(self, name, grade):
        self.name = name
        self.grade = grade
        Student.total_students += 1  # 更新类属性

    # 实例方法
    def get_info(self):
        return f"{self.name} - {self.grade}年级"

    # 类方法
    @classmethod
    def get_total_students(cls):
        return f"学校总学生数: {cls.total_students}"

    @classmethod
    def create_from_string(cls, student_str):
        """类方法作为替代构造函数"""
        name, grade = student_str.split('-')
        return cls(name, int(grade))
# ================================================
# 使用类方法
student2 = Student("李四", 11)
print(Student.get_total_students())
```

### 3.5.2 静态方法

静态方法使用 `@staticmethod` 装饰器，没有默认参数。

```python
class MyClass:
    @staticmethod
    def static_method():
        print("This is a static method.")

if __name__ == "__main__":
    MyClass.static_method()  # 调用静态方法
```

静态方法演示：

```py
class Student:
    """学生类"""

    # 类属性
    school = "某某中学"
    total_students = 0

    def __init__(self, name, grade): # 构造函数
        self.name = name
        self.grade = grade
        Student.total_students += 1  # 更新类属性

    # 实例方法
    def get_info(self):
        return f"{self.name} - {self.grade}年级"


    # 静态方法
    @staticmethod
    def is_valid_grade(grade):
        """静态方法 - 与类相关但不依赖类或实例"""
        return 1 <= grade <= 12

    @staticmethod
    def get_school_info():
        return f"欢迎来到{Student.school}"
# ================================================
# 使用实例方法
student1 = Student("张三", 10)
print(student1.get_info())

# 使用静态方法
print(f"年级5是否有效: {Student.is_valid_grade(5)}")
print(f"年级15是否有效: {Student.is_valid_grade(15)}")
print(Student.get_school_info())
```

## 3.6 属性装饰器

### 3.6.1 属性装饰器

使用 `@property` 装饰器将方法转换为只读属性。

```python
class MyClass:
    def __init__(self, value):
        self._value = value

    @property # 只读属性
    def value(self):
        return self._value

if __name__ == "__main__":
    obj = MyClass(10)
    print(obj.value)  # 调用只读属性
```

### 3.6.2 属性装饰器演示

```py
class Person:
    """人类 - 属性装饰器示例"""

    def __init__(self, first_name, last_name, age):
        self._first_name = first_name
        self._last_name = last_name
        self._age = age

    # 使用property装饰器创建只读属性
    @property
    def full_name(self):
        return f"{self._first_name} {self._last_name}"

    @property
    def age(self):
        return self._age

    # 设置器
    @age.setter
    def age(self, value):
        if 0 <= value <= 150:
            self._age = value
        else:
            raise ValueError("年龄必须在0-150之间")

    # 删除器
    @age.deleter
    def age(self):
        print("删除年龄!")
        self._age = 0

    # 计算属性
    @property
    def is_adult(self):
        return self._age >= 18
# ================================================
# 使用属性
person = Person("张", "三", 25)

print(f"全名: {person.full_name}")  # 像属性一样访问
print(f"年龄: {person.age}")
print(f"是否成年: {person.is_adult}")

# 使用设置器
person.age = 30
print(f"修改后年龄: {person.age}")

# 尝试设置无效年龄
try:
    person.age = 200
except ValueError as e:
    print(f"错误: {e}")

# 使用删除器
del person.age
print(f"删除后年龄: {person.age}")
```

## 3.7 特殊方法（魔法方法）

### 3.7.1 特殊方法

特殊方法以双下划线开头和结尾，例如 `__init__`、`__str__`、`__len__` 等。

```python
class MyClass:
    def __init__(self, value): # 构造函数
        self.value = value

    def __str__(self): # 字符串表示
        return f"MyClass(value={self.value})"

if __name__ == "__main__":
    obj = MyClass(10)
    print(obj)  # 调用 __str__ 方法
```

### 3.7.2 特殊方法演示

定义一个 Vector 类，实现向量的加法、减法、乘法、除法等操作。

```py
class Vector:
    """向量类 - 演示魔术方法"""

    def __init__(self, x, y):
        self.x = x
        self.y = y

    # 字符串表示
    def __str__(self):
        return f"Vector({self.x}, {self.y})"

    def __repr__(self):
        return f"Vector({self.x}, {self.y})"

    # 算术运算
    def __add__(self, other):
        return Vector(self.x + other.x, self.y + other.y)

    def __sub__(self, other):
        return Vector(self.x - other.x, self.y - other.y)

    def __mul__(self, scalar):
        return Vector(self.x * scalar, self.y * scalar)

    # 比较运算
    def __eq__(self, other):
        return self.x == other.x and self.y == other.y

    def __lt__(self, other):
        # 比较向量长度
        return (self.x**2 + self.y**2) < (other.x**2 + other.y**2)

    # 容器操作
    def __len__(self):
        # 返回向量维度
        return 2

    def __getitem__(self, index):
        if index == 0:
            return self.x
        elif index == 1:
            return self.y
        else:
            raise IndexError("向量只有2个维度")

    def __iter__(self): # 迭代
        return iter([self.x, self.y])

def main():
    # 使用魔术方法
    v1 = Vector(2, 3)
    v2 = Vector(1, 4)

    print(f"v1 = {v1}")
    print(f"v2 = {v2}")
    print(f"v1 + v2 = {v1 + v2}")
    print(f"v1 - v2 = {v1 - v2}")
    print(f"v1 * 3 = {v1 * 3}")
    print(f"v1 == v2: {v1 == v2}")
    print(f"v1 < v2: {v1 < v2}")
    print(f"向量维度: {len(v1)}")
    print(f"v1[0] = {v1[0]}, v1[1] = {v1[1]}")

    # 迭代
    print("向量分量:", end=" ")
    for component in v1:
        print(component, end=" ")
    print()

if __name__ == "__main__":
    main()
```

## 3.8 抽象基类

### 3.8.1 抽象基类

抽象基类（Abstract Base Class，ABC）是定义了一组抽象方法的类，不能被实例化，只能被继承。

```python
from abc import ABC, abstractmethod

class MyAbstractClass(ABC):
    @abstractmethod
    def my_abstract_method(self):
        pass

class MyClass(MyAbstractClass):
    def my_abstract_method(self):
        print("实现抽象方法")

if __name__ == "__main__":
    obj = MyClass()
    obj.my_abstract_method()
```

### 3.8.2 抽象基类演示

```py
from abc import ABC, abstractmethod

class Vehicle(ABC):
    """交通工具抽象基类"""

    def __init__(self, brand, model):
        self.brand = brand
        self.model = model

    @abstractmethod
    def start_engine(self):
        """启动引擎（抽象方法）"""
        pass

    @abstractmethod
    def stop_engine(self):
        """停止引擎（抽象方法）"""
        pass

    def get_info(self):
        """具体方法"""
        return f"{self.brand} {self.model}"

class Car(Vehicle):
    """汽车类"""
    def start_engine(self):
        return f"{self.get_info()} 汽车引擎启动: 嗡嗡嗡..."

    def stop_engine(self):
        return f"{self.get_info()} 汽车引擎停止"

class Motorcycle(Vehicle):
    """摩托车类"""
    def start_engine(self):
        return f"{self.get_info()} 摩托车引擎启动: 轰轰轰..."

    def stop_engine(self):
        return f"{self.get_info()} 摩托车引擎停止"

# =======================================================
# 使用具体类
car = Car("丰田", "凯美瑞")
bike = Motorcycle("本田", "CBR")

print(car.start_engine())
print(car.stop_engine())
print(bike.start_engine())
print(bike.stop_engine())

# 尝试实例化抽象类会报错
try:
    vehicle = Vehicle("通用", "测试")
except TypeError as e:
    print(f"错误: {e}")
```

## 3.9 组合 vs 继承

### 3.9.1 组合 vs 继承

组合（Composition）和继承（Inheritance）是两种常见的面向对象编程（OOP）技术。

- 组合：将一个对象嵌入到另一个对象中，形成整体与部分的关系。
- 继承：一个类继承另一个类的属性和方法，形成父子关系。

### 3.9.2 使用组合与继承

```py
# 使用继承
class Engine:
    """引擎类"""

    def start(self):
        return "引擎启动"

    def stop(self):
        return "引擎停止"

class Wheels:
    """轮子类"""

    def __init__(self, count):
        self.count = count

    def rotate(self):
        return f"{self.count}个轮子在旋转"

# 使用组合（优先使用组合）
class Car:
    """汽车类 - 使用组合"""

    def __init__(self, brand, wheel_count=4):
        self.brand = brand
        self.engine = Engine()           # 组合
        self.wheels = Wheels(wheel_count) # 组合

    def drive(self):
        return f"{self.brand}: {self.engine.start()}, {self.wheels.rotate()}"

    def park(self):
        return f"{self.brand}: {self.engine.stop()}"

# 使用继承
class SportsCar(Car):
    """跑车类 - 使用继承"""

    def __init__(self, brand, wheel_count=4, turbo=False):
        super().__init__(brand, wheel_count)
        self.turbo = turbo

    def activate_turbo(self):
        if self.turbo:
            return f"{self.brand} 涡轮增压启动!"
        return f"{self.brand} 没有涡轮增压"
# =====================================================
# 使用组合和继承
car = Car("大众")
sports_car = SportsCar("保时捷", turbo=True)

print(car.drive())
print(sports_car.drive())
print(sports_car.activate_turbo())
```

## 3.10 综合示例

写一个图书管理系统，包括图书类、借阅者类、图书馆类等。

```py
class Book:
    """图书类"""

    def __init__(self, title, author, isbn, copies=1):
        self.title = title
        self.author = author
        self.isbn = isbn
        self._copies = copies
        self._borrowed = 0

    @property
    def available_copies(self):
        return self._copies - self._borrowed

    def borrow(self):
        if self.available_copies > 0:
            self._borrowed += 1
            return True
        return False

    def return_book(self):
        if self._borrowed > 0:
            self._borrowed -= 1
            return True
        return False

    def __str__(self):
        return f"《{self.title}》 - {self.author} (ISBN: {self.isbn})"

    def __repr__(self):
        return f"Book('{self.title}', '{self.author}', '{self.isbn}')"

class Member:
    """会员类"""

    def __init__(self, member_id, name):
        self.member_id = member_id
        self.name = name
        self.borrowed_books = []

    def borrow_book(self, book):
        if book.borrow():
            self.borrowed_books.append(book)
            return True
        return False

    def return_book(self, book):
        if book in self.borrowed_books:
            book.return_book()
            self.borrowed_books.remove(book)
            return True
        return False

    def __str__(self):
        return f"会员 {self.name} (ID: {self.member_id})"

class Library:
    """图书馆类"""

    def __init__(self, name):
        self.name = name
        self.books = []
        self.members = []

    def add_book(self, book):
        self.books.append(book)

    def register_member(self, member):
        self.members.append(member)

    def find_book(self, title):
        for book in self.books:
            if book.title.lower() == title.lower():
                return book
        return None

    def list_available_books(self):
        return [book for book in self.books if book.available_copies > 0]

    def __str__(self):
        return f"{self.name} 图书馆 - 藏书: {len(self.books)}册, 会员: {len(self.members)}人"

def main():
    # 使用图书馆系统
    library = Library("市立图书馆")

    # 添加图书
    book1 = Book("Python编程", "张三", "978-1-123456-78-9", 3)
    book2 = Book("数据结构", "李四", "978-1-987654-32-1", 2)
    library.add_book(book1)
    library.add_book(book2)

    # 注册会员
    member1 = Member("M001", "王五")
    library.register_member(member1)

    print(library)
    print("\n可用图书:")
    for book in library.list_available_books():
        print(f"  {book} - 可用: {book.available_copies}册")

    # 借书操作
    print(f"\n{member1.name} 借书:")
    if member1.borrow_book(book1):
        print(f"  成功借阅: {book1.title}")
    else:
        print(f"  借阅失败: {book1.title} 无可用副本")

    print(f"\n借阅后 {book1.title} 可用: {book1.available_copies}册")

if __name__ == "__main__":
    main()
```

## 3.11 面向对象总结

- 类: 对象的蓝图，定义属性和方法
- 对象: 类的实例
- 封装: 隐藏内部实现，提供公共接口
- 继承: 子类继承父类的属性和方法
- 多态: 相同接口，不同实现
- 抽象: 定义接口而不关心实现
- 组合: 对象包含其他对象
- 遵循面向对象设计原则编写高质量代码

面向对象编程（OOP）是一种编程范式，它使用类和对象来组织代码。OOP 的主要优点包括：

- **封装**：将数据和操作数据的方法封装在一起，提高代码的可维护性和可重用性。
- **继承**：通过继承机制，可以创建新的类，继承并扩展现有类的功能。
- **多态**：允许不同类的对象以相同的方式响应相同的消息，提高代码的灵活性和可扩展性。

OOP 的最佳实践包括：

1. 单一职责原则: 一个类只负责一个功能
2. 开闭原则: 对扩展开放，对修改关闭
3. 里氏替换原则: 子类应该可以替换父类
4. 接口隔离原则: 使用多个专门的接口
5. 依赖倒置原则: 依赖抽象而不是具体实现
6. 组合优于继承: 优先使用组合而不是继承
7. 封装: 隐藏内部实现细节
8. 使用属性而不是直接访问字段
9. 为类和方法添加文档字符串
10. 遵循命名约定: 类名使用驼峰，方法使用蛇形

## 3.12 练习

1. 编写一个表示矩形的类，包括属性长和宽，以及计算面积和周长的方法。
2. 编写一个表示圆的类，包括属性半径，以及计算面积和周长的方法。
3. 编写一个表示汽车类的类，包括属性品牌、发动机和轮子数量，以及启动和停止的方法。
