# Python 学习计划（面向C#程序员）

## 学习路线图

基础语法 → 数据结构 → 函数 → 面向对象 → 进阶特性 → 常用标准库

---

## 第一阶段：基础语法

### 1. 变量与数据类型

#### 1.1 变量声明

**C# 写法：**

int age = 25; 
string name = "张三"; 
bool isAdult = true;

**Python 写法：**

age = 25              # 自动推断为 int 
name = "张三"          # 自动推断为 str 
is_adult = True       # 注意：True 首字母大写

> ⚠️ **坑1：Python 没有变量声明，只有变量绑定**
> 
> x = 10      # x 绑定到整数 10 
> x = "hello" # 完全合法！x 现在绑定到字符串
> 
> Python 变量是**引用**，不是容器。变量名只是指向对象的标签。

> ⚠️ **坑2：命名规范不同**
> 
> - C#：`camelCase`（局部变量）、`PascalCase`（方法/类）
>     
> - Python：`snake_case`（变量/函数）、`PascalCase`（类名）
>     

#### 1.2 基本数据类型

|C# 类型|Python 类型|注意事项|
|---|---|---|
|`int`|`int`|Python 整数无溢出，可以无限大|
|`long`|`int`|Python 3 中 int 就是长整型|
|`float`|`float`|同 IEEE 754 双精度|
|`decimal`|`Decimal`|需要导入 `decimal` 模块|
|`bool`|`bool`|`True`/`False` 首字母大写|
|`string`|`str`|不可变，支持 Unicode|
|`char`|`str`|Python 没有单独的 char 类型|

> ⚠️ **坑3：布尔值的真值判断**
> 
> # 以下值都为 False（假值）： 
> bool(0)      # False 
> bool(0.0)    # False 
> bool("")     # False（空字符串） 
> bool([])     # False（空列表） 
> bool({})     # False（空字典） 
> bool(None)   # False（None 相当于 C# 的 null） 
> ​  
> # 其他所有值都为 True！包括： 
> bool(" ")    # True（空格不是空字符串） 
> bool([0])    # True（包含元素的列表） 
> bool(-1)     # True（负数也是 True）

#### 1.3 数值运算

# 整数除法（C# 中需要强制转换） 
10 / 3   # 结果：3.333...（总是返回 float） 
10 // 3  # 结果：3（整数除法，相当于 C# 的 10 / 3） 
​ 
# 幂运算  
2 ** 10  # 1024（C# 需要 Math.Pow(2, 10)）

> ⚠️ **坑4：除法运算符的变化**
> 
> # Python 2 中：10 / 3 = 3（整数除法） 
> # Python 3 中：10 / 3 = 3.333...（浮点除法） 
> # 如果需要整数结果，必须用 //

---

### 2. 字符串

#### 2.1 字符串定义

s1 = 'hello'           # 单引号 
s2 = "hello"           # 双引号（两者完全等价） 
s3 = '''多行 
字符串'''               # 三引号支持多行 
s4 = """也是多行 
字符串""" 
​  
# 原始字符串（不转义）  
path = r"C:\new\test"  # \n 和 \t 不会被转义

#### 2.2 字符串格式化

name = "张三" 
age = 25 
​ 
# 方式1：f-string（Python 3.6+，推荐） 
s1 = f"我叫{name}，今年{age}岁" 
​  
# 方式2：format 方法 
s2 = "我叫{}，今年{}岁".format(name, age) 
s3 = "我叫{n}，今年{a}岁".format(n=name, a=age) 
​  
# 方式3：旧式 % 格式化（不推荐） 
s4 = "我叫%s，今年%d岁" % (name, age)

> ⚠️ **坑5：字符串不可变**
> 
> s = "hello" 
> s[0] = "H"  # TypeError！字符串不能修改 
> ​ 
> # 正确做法： 
> s = "H" + s[1:]  # 创建新字符串 
> s = s.replace("h", "H")  # 使用方法

> ⚠️ **坑6：字符串拼接效率**
> 
> # ❌ 低效（每次都创建新字符串） 
> result = "" 
> for i in range(1000): 
>  result += str(i) 
> ​ 
> # ✅ 高效 
> result = "".join(str(i) for i in range(1000))

---

### 3. 流程控制

#### 3.1 条件语句

**C# 写法：**

if (score >= 90) { 
    Console.WriteLine("优秀"); 
} else if (score >= 60) { 
    Console.WriteLine("及格");  
} else { 
    Console.WriteLine("不及格"); 
}

**Python 写法：**

if score >= 90: 
    print("优秀") 
elif score >= 60:    # 注意：elif，不是 else if 
    print("及格") 
else: 
    print("不及格")

> ⚠️ **坑7：缩进决定代码块**
> 
> # Python 用缩进代替大括号 
> if True: 
>  print("A") 
>   print("B")  # IndentationError！缩进不一致 
> ​ 
> # 正确写法（4个空格为标准） 
> if True: 
>  print("A") 
>  print("B")

> ⚠️ **坑8：空语句需要 pass**
> 
> if True: 
>  # 这里不能留空，会报错 
> ​ 
> # 正确写法 
> if True: 
>  pass  # 占位符，什么都不做

#### 3.2 循环语句

# for 循环（遍历序列） 
for i in range(5):      # 0, 1, 2, 3, 4 
    print(i) 
​ 
for i in range(1, 10, 2):  # 1, 3, 5, 7, 9（起点、终点、步长） 
    print(i) 
​ 
# 遍历列表 
fruits = ["苹果", "香蕉", "橙子"] 
for fruit in fruits: 
    print(fruit) 
​ 
# 同时获取索引和值 
for index, fruit in enumerate(fruits): 
    print(f"{index}: {fruit}") 
​ 
# while 循环 
count = 0 
while count < 5: 
    print(count) 
    count += 1  # 注意：Python 没有 count++

> ⚠️ **坑9：Python 没有 ++ 和 --**
> 
> i++   # 语法错误！ 
> i--   # 语法错误！ 
> i += 1  # 正确写法

> ⚠️ **坑10：循环中的 else**
> 
> # Python 的循环可以有 else 块（C# 没有） 
> for i in range(5): 
>  if i == 10: 
>      break 
> else: 
>  print("循环正常结束，没有 break") 
> ​ 
> # 注意：如果 break 了，else 不会执行

---

### 4. 数据结构

#### 4.1 列表（List）—— 相当于 C# 的 List

# 创建列表  
nums = [1, 2, 3, 4, 5]  
mixed = [1, "hello", 3.14, True]  # 可以混合类型  
​  
# 访问元素  
nums[0]      # 1（第一个元素）  
nums[-1]     # 5（最后一个元素）  
nums[1:4]    # [2, 3, 4]（切片）  
nums[:3]     # [1, 2, 3]  
nums[2:]     # [3, 4, 5]  
nums[::2]    # [1, 3, 5]（步长为2）  
​  
# 修改元素  
nums[0] = 10  
nums.append(6)        # 添加到末尾  
nums.insert(0, 0)     # 插入到指定位置  
nums.extend([7, 8])   # 扩展列表  
​  
# 删除元素  
nums.pop()            # 删除并返回最后一个  
nums.pop(0)           # 删除指定索引  
nums.remove(3)        # 删除第一个值为3的元素  
del nums[0]           # 删除指定索引  
​  
# 列表推导式  
squares = [x**2 for x in range(10)]  
evens = [x for x in range(10) if x % 2 == 0]

> ⚠️ **坑11：列表的引用复制**
> 
> a = [1, 2, 3]  
> b = a          # b 和 a 指向同一个列表！  
> b.append(4)  
> print(a)       # [1, 2, 3, 4] a 也变了！  
> ​  
> # 正确的复制方式  
> b = a.copy()       # 浅拷贝  
> b = a[:]           # 浅拷贝（切片）  
> b = list(a)        # 浅拷贝  
> import copy  
> b = copy.deepcopy(a)  # 深拷贝

> ⚠️ **坑12：列表作为默认参数**
> 
> # ❌ 致命错误！  
> def add_item(item, lst=[]):  
>  lst.append(item)  
>  return lst  
> ​  
> add_item(1)  # [1]  
> add_item(2)  # [1, 2]  默认列表被复用了！  
> ​  
> # ✅ 正确写法  
> def add_item(item, lst=None):  
>  if lst is None:  
>      lst = []  
>  lst.append(item)  
>  return lst

#### 4.2 元组（Tuple）—— 不可变列表

# 创建元组  
point = (3, 4)  
single = (1,)         # 单元素元组必须加逗号  
empty = ()  
​  
# 解包  
x, y = point  
a, b, c = (1, 2, 3)  
​  
# 交换变量（Python 特有）  
a, b = b, a

> ⚠️ **坑13：单元素元组的逗号**
> 
> t = (1)     # 这不是元组！就是整数 1  
> t = (1,)    # 这才是单元素元组  
> type((1))   # <class 'int'>  
> type((1,))  # <class 'tuple'>

#### 4.3 字典（Dictionary）—— 相当于 C# 的 Dictionary

# 创建字典  
person = {  
    "name": "张三",  
    "age": 25,  
    "city": "北京"  
}  
​  
# 访问元素  
person["name"]           # "张三"  
person.get("job")        # None（不存在返回 None）  
person.get("job", "无业") # "无业"（指定默认值）  
​  
# 添加/修改  
person["job"] = "工程师"  
person["age"] = 26  
​  
# 删除  
del person["city"]  
person.pop("age")  
​  
# 遍历  
for key in person:              # 遍历键  
    print(key)  
​  
for key, value in person.items():  # 遍历键值对  
    print(f"{key}: {value}")  
​  
for value in person.values():   # 遍历值  
    print(value)

> ⚠️ **坑14：字典的键必须可哈希**
> 
> d = {}  
> d[[1, 2]] = "value"  # TypeError！列表不能作为键  
> d[(1, 2)] = "value"  # 正确，元组可以作为键

> ⚠️ **坑15：遍历时修改字典**
> 
> d = {"a": 1, "b": 2}  
> for key in d:  
>  if key == "a":  
>      del d[key]  # RuntimeError！  
> ​  
> # 正确写法  
> for key in list(d.keys()):  
>  if key == "a":  
>      del d[key]

#### 4.4 集合（Set）—— 相当于 C# 的 HashSet

# 创建集合  
s1 = {1, 2, 3}  
s2 = set([1, 2, 2, 3])  # {1, 2, 3}，自动去重  
​  
# 操作  
s1.add(4)  
s1.remove(3)  
s1.discard(5)  # 删除，不存在也不报错  
​  
# 集合运算  
a = {1, 2, 3}  
b = {2, 3, 4}  
a | b   # {1, 2, 3, 4} 并集  
a & b   # {2, 3} 交集  
a - b   # {1} 差集  
a ^ b   # {1, 4} 对称差

> ⚠️ **坑16：空集合的创建**
> 
> s = {}     # 这是空字典！不是空集合！  
> s = set()  # 这才是空集合

---

## 第二阶段：函数

### 1. 函数定义

def greet(name):  
    """这是文档字符串，说明函数的作用"""  
    return f"Hello, {name}!"  
​  
# 调用  
message = greet("张三")

### 2. 参数类型

# 位置参数  
def add(a, b):  
    return a + b  
​  
# 默认参数  
def greet(name, greeting="Hello"):  
    return f"{greeting}, {name}!"  
​  
# 关键字参数  
greet(name="张三", greeting="Hi")  
​  
# 可变位置参数 (*args)  
def sum_all(*numbers):  
    return sum(numbers)  
​  
sum_all(1, 2, 3, 4)  # 10  
​  
# 可变关键字参数 (**kwargs)  
def print_info(**kwargs):  
    for key, value in kwargs.items():  
        print(f"{key}: {value}")  
​  
print_info(name="张三", age=25)

> ⚠️ **坑17：参数顺序**
> 
> # 正确顺序：位置参数 → 默认参数 → *args → **kwargs  
> def func(a, b, c=1, *args, **kwargs):  
>  pass

> ⚠️ **坑18：默认参数的求值时机**
> 
> # 默认值在函数定义时求值，不是调用时！  
> def func(a, lst=[]):  # lst 在定义时创建，所有调用共享  
>  lst.append(a)  
>  return lst

### 3. 返回值

# 返回多个值（实际是元组）  
def get_stats(numbers):  
    return min(numbers), max(numbers), sum(numbers)  
​  
minimum, maximum, total = get_stats([1, 2, 3, 4, 5])  
​  
# 或者接收元组  
result = get_stats([1, 2, 3, 4, 5])  # (1, 5, 15)

### 4. Lambda 表达式

# C#: x => x * 2  
# Python: lambda x: x * 2  
​  
square = lambda x: x ** 2  
add = lambda a, b: a + b  
​  
# 常用于排序  
students = [("张三", 85), ("李四", 92), ("王五", 78)]  
students.sort(key=lambda x: x[1], reverse=True)

> ⚠️ **坑19：Lambda 的限制**
> 
> # Lambda 只能是单个表达式，不能有语句  
> # ❌ 错误  
> f = lambda x: if x > 0: return x else: return -x  
> ​  
> # ✅ 使用条件表达式  
> f = lambda x: x if x > 0 else -x

---

## 第三阶段：面向对象

### 1. 类的定义

class Person:  
    """人类"""  
​  
    # 类变量（所有实例共享）  
    species = "人类"  
​  
    # 构造方法  
    def __init__(self, name, age):  
        # 实例变量  
        self.name = name  
        self.age = age  
​  
    # 实例方法  
    def introduce(self):  
        return f"我是{self.name}，今年{self.age}岁"  
​  
    # 类方法  
    @classmethod  
    def from_birth_year(cls, name, birth_year):  
        age = 2024 - birth_year  
        return cls(name, age)  
​  
    # 静态方法  
    @staticmethod  
    def is_adult(age):  
        return age >= 18  
​  
# 使用  
p = Person("张三", 25)  
print(p.introduce())  
print(Person.species)

### 2. 继承

class Student(Person):  
    def __init__(self, name, age, grade):  
        # 调用父类构造方法  
        super().__init__(name, age)  
        self.grade = grade  
​  
    # 重写方法  
    def introduce(self):  
        return f"我是{self.name}，{self.grade}年级学生"  
​  
    # 新增方法  
    def study(self, subject):  
        return f"{self.name}正在学习{subject}"  
​  
# 多继承  
class A:  
    pass  
​  
class B:  
    pass  
​  
class C(A, B):  # 多继承  
    pass

> ⚠️ **坑20：多继承的 MRO（方法解析顺序）**
> 
> class A:  
>  def method(self):  
>      print("A")  
> ​  
> class B(A):  
>  def method(self):  
>      print("B")  
>      super().method()  
> ​  
> class C(A):  
>  def method(self):  
>      print("C")  
>      super().method()  
> ​  
> class D(B, C):  
>  def method(self):  
>      print("D")  
>      super().method()  
> ​  
> d = D()  
> d.method()  # D → B → C → A（不是 D → B → A）  
> # 使用 D.mro() 查看解析顺序

### 3. 属性访问控制

class Person:  
    def __init__(self, name):  
        self._name = name      # 约定：私有（实际可访问）  
        self.__secret = "???"   # 名称改写：_Person__secret  
​  
    # getter  
    @property  
    def name(self):  
        return self._name  
​  
    # setter  
    @name.setter  
    def name(self, value):  
        if not value:  
            raise ValueError("名字不能为空")  
        self._name = value  
​  
# 使用  
p = Person("张三")  
print(p.name)      # 调用 getter  
p.name = "李四"    # 调用 setter

> ⚠️ **坑21：Python 没有真正的私有**
> 
> class Person:  
>  def __init__(self):  
>      self.__private = "秘密"  
> ​  
> p = Person()  
> # print(p.__private)   # AttributeError  
> print(p._Person__private)  # 可以访问！名称改写而已

### 4. 魔术方法

class Vector:  
    def __init__(self, x, y):  
        self.x = x  
        self.y = y  
​  
    # 字符串表示  
    def __str__(self):  
        return f"Vector({self.x}, {self.y})"  
​  
    # 调试表示  
    def __repr__(self):  
        return f"Vector({self.x}, {self.y})"  
​  
    # 加法  
    def __add__(self, other):  
        return Vector(self.x + other.x, self.y + other.y)  
​  
    # 长度  
    def __len__(self):  
        return int((self.x**2 + self.y**2) ** 0.5)  
​  
    # 索引访问  
    def __getitem__(self, index):  
        if index == 0:  
            return self.x  
        elif index == 1:  
            return self.y  
        raise IndexError("Index out of range")  
​  
v1 = Vector(3, 4)  
v2 = Vector(1, 2)  
v3 = v1 + v2  # Vector(4, 6)

---

## 第四阶段：进阶特性

### 1. 装饰器

# 简单装饰器  
def log(func):  
    def wrapper(*args, **kwargs):  
        print(f"调用 {func.__name__}")  
        result = func(*args, **kwargs)  
        print(f"调用结束")  
        return result  
    return wrapper  
​  
@log  
def greet(name):  
    print(f"Hello, {name}")  
​  
greet("张三")  
# 等价于：greet = log(greet)  
​  
# 带参数的装饰器  
def repeat(times):  
    def decorator(func):  
        def wrapper(*args, **kwargs):  
            for _ in range(times):  
                result = func(*args, **kwargs)  
            return result  
        return wrapper  
    return decorator  
​  
@repeat(3)  
def say_hello():  
    print("Hello!")

### 2. 生成器

# 生成器函数  
def countdown(n):  
    while n > 0:  
        yield n  
        n -= 1  
​  
for i in countdown(5):  
    print(i)  
​  
# 生成器表达式  
squares = (x**2 for x in range(10))  
​  
# 读取大文件  
def read_large_file(file_path):  
    with open(file_path) as f:  
        for line in f:  
            yield line.strip()

> ⚠️ **坑22：生成器只能迭代一次**
> 
> gen = (x for x in range(3))  
> list(gen)  # [0, 1, 2]  
> list(gen)  # []  已经消耗完了！

### 3. 上下文管理器

# 使用 with 语句  
with open("file.txt", "w") as f:  
    f.write("Hello")  
# 文件自动关闭  
​  
# 自定义上下文管理器  
class Timer:  
    def __enter__(self):  
        import time  
        self.start = time.time()  
        return self  
​  
    def __exit__(self, exc_type, exc_val, exc_tb):  
        self.end = time.time()  
        print(f"耗时：{self.end - self.start}秒")  
​  
with Timer() as t:  
    # 一些操作  
    pass

### 4. 异常处理

# 基本结构  
try:  
    result = 10 / 0  
except ZeroDivisionError as e:  
    print(f"除零错误：{e}")  
except (TypeError, ValueError) as e:  
    print(f"类型或值错误：{e}")  
except Exception as e:  
    print(f"其他错误：{e}")  
else:  
    print("没有异常")  
finally:  
    print("总是执行")  
​  
# 抛出异常  
def set_age(age):  
    if age < 0:  
        raise ValueError("年龄不能为负")  
    return age  
​  
# 自定义异常  
class MyError(Exception):  
    def __init__(self, message, code):  
        super().__init__(message)  
        self.code = code

> ⚠️ **坑23：异常处理的性能**
> 
> # 不要用异常控制正常流程  
> # ❌ 低效  
> try:  
>  x = d[key]  
> except KeyError:  
>  x = default  
> ​  
> # ✅ 高效  
> x = d.get(key, default)

---

## 第五阶段：常用标准库

### 1. 文件操作

# 读取文件  
with open("file.txt", "r", encoding="utf-8") as f:  
    content = f.read()        # 读取全部  
    lines = f.readlines()     # 读取所有行为列表  
    line = f.readline()       # 读取一行  
​  
    for line in f:            # 逐行迭代（内存高效）  
        print(line.strip())  
​  
# 写入文件  
with open("file.txt", "w", encoding="utf-8") as f:  
    f.write("Hello\n")  
    f.writelines(["Line1\n", "Line2\n"])  
​  
# 追加  
with open("file.txt", "a", encoding="utf-8") as f:  
    f.write("More content\n")

> ⚠️ **坑24：文件编码**
> 
> # Windows 默认编码可能是 GBK  
> # 始终显式指定 encoding="utf-8"  
> ​  
> # ❌ 可能乱码  
> with open("file.txt", "r") as f:  
>  content = f.read()  
> ​  
> # ✅ 正确  
> with open("file.txt", "r", encoding="utf-8") as f:  
>  content = f.read()

### 2. os 和 pathlib

import os  
from pathlib import Path  
​  
# os 模块（传统）  
os.getcwd()              # 当前目录  
os.listdir(".")          # 列出目录内容  
os.path.join("a", "b")   # 路径拼接  
os.path.exists("file")   # 文件是否存在  
​  
# pathlib 模块（推荐，Python 3.4+）  
p = Path(".")  
p.cwd()                  # 当前目录  
p.iterdir()              # 列出目录内容  
p / "subdir" / "file.txt"  # 路径拼接（重载了 /）  
p.exists()               # 是否存在  
p.is_file()              # 是否是文件  
p.is_dir()               # 是否是目录  
p.parent                 # 父目录  
p.name                   # 文件名  
p.stem                   # 文件名（无扩展名）  
p.suffix                 # 扩展名

### 3. json 模块

import json  
​  
# 序列化  
data = {"name": "张三", "age": 25}  
json_str = json.dumps(data, ensure_ascii=False, indent=2)  
​  
# 反序列化  
data = json.loads(json_str)  
​  
# 文件操作  
with open("data.json", "w", encoding="utf-8") as f:  
    json.dump(data, f, ensure_ascii=False, indent=2)  
​  
with open("data.json", "r", encoding="utf-8") as f:  
    data = json.load(f)

### 4. datetime 模块

from datetime import datetime, date, timedelta  
​  
# 当前时间  
now = datetime.now()  
today = date.today()  
​  
# 创建日期时间  
d = date(2024, 1, 1)  
dt = datetime(2024, 1, 1, 12, 30, 0)  
​  
# 格式化  
now.strftime("%Y-%m-%d %H:%M:%S")  
​  
# 解析  
dt = datetime.strptime("2024-01-01", "%Y-%m-%d")  
​  
# 时间运算  
tomorrow = today + timedelta(days=1)  
next_week = today + timedelta(weeks=1)

---

## 第六阶段：Python 独特概念

### 1. 浅拷贝 vs 深拷贝

import copy  
​  
a = [[1, 2], [3, 4]]  
​  
# 赋值（同一对象）  
b = a  
b[0][0] = 999  
print(a[0][0])  # 999，a 也变了  
​  
# 浅拷贝（复制外层，内层还是引用）  
c = a.copy()  # 或 c = a[:] 或 copy.copy(a)  
c[0][0] = 888  
print(a[0][0])  # 888，内层还是共享的！  
​  
# 深拷贝（完全复制）  
d = copy.deepcopy(a)  
d[0][0] = 777  
print(a[0][0])  # 不变

### 2. 可变 vs 不可变

|不可变（Immutable）|可变（Mutable）|
|---|---|
|int, float, str|list|
|tuple|dict|
|frozenset|set|
|bytes|bytearray|

> ⚠️ **坑25：不可变对象的"修改"**
> 
> s = "hello"  
> s += " world"  # 看似修改，实际创建新对象  
> # 原来的 "hello" 对象被垃圾回收

> ⚠️ **坑26：元组内的可变对象**
> 
> t = ([1, 2], [3, 4])  
> t[0].append(3)  # 可以！元组存的是列表的引用  
> # t 变成 ([1, 2, 3], [3, 4])

### 3. 命名空间和作用域

x = 10  # 全局变量  
​  
def func():  
    x = 20  # 局部变量  
    print(x)  # 20  
​  
def func2():  
    global x  # 声明使用全局变量  
    x = 30  
​  
def outer():  
    x = 1  
    def inner():  
        nonlocal x  # 声明使用外层变量  
        x = 2  
    inner()  
    print(x)  # 2

> ⚠️ **坑27：闭包中的变量绑定**
> 
> # ❌ 常见错误  
> funcs = []  
> for i in range(3):  
>  funcs.append(lambda: i)  
> ​  
> for f in funcs:  
>  print(f())  # 2, 2, 2  都是最后一个值！  
> ​  
> # ✅ 正确写法  
> funcs = []  
> for i in range(3):  
>  funcs.append(lambda x=i: x)  
> ​  
> for f in funcs:  
>  print(f())  # 0, 1, 2

---

## 常见陷阱总结

### 陷阱速查表

|编号|陷阱|问题|解决方案|
|---|---|---|---|
|1|变量绑定|变量是引用，可以绑定到任何类型|理解 Python 的对象模型|
|2|命名规范|与 C# 习惯不同|使用 snake_case|
|3|真值判断|很多值都是 False|明确使用 `if x is not None`|
|4|除法运算|`/` 返回浮点数|使用 `//` 进行整数除法|
|5|字符串不可变|不能直接修改|使用切片或方法创建新字符串|
|6|字符串拼接|循环中 + 拼接效率低|使用 `join()`|
|7|缩进敏感|缩进决定代码块|使用 4 空格，保持一致|
|8|空语句|不能留空|使用 `pass`|
|9|无 ++ --|Python 不支持|使用 `+= 1`|
|10|循环 else|不常见的语法|理解其含义|
|11|列表引用复制|直接赋值是引用|使用 `copy()` 或切片|
|12|可变默认参数|默认值共享|使用 `None` 作为默认值|
|13|单元素元组|`(1)` 不是元组|使用 `(1,)`|
|14|字典键类型|必须可哈希|使用不可变类型作为键|
|15|遍历时修改|会出错|先复制键列表|
|16|空集合创建|`{}` 是字典|使用 `set()`|
|17|参数顺序|必须按规则|位置→默认→*args→**kwargs|
|18|默认参数求值|定义时求值|避免使用可变默认值|
|19|Lambda 限制|只能是表达式|复杂逻辑使用函数|
|20|多继承 MRO|方法解析顺序复杂|使用 `mro()` 查看|
|21|无真私有|都可以访问|理解 `_` 和 `__` 的约定|
|22|生成器一次性|只能迭代一次|需要多次使用则转为列表|
|23|异常性能|异常处理开销大|正常流程避免异常|
|24|文件编码|默认编码因系统而异|显式指定 `encoding`|
|25|不可变"修改"|实际创建新对象|理解对象模型|
|26|元组内可变|元组"不可变"是相对的|注意嵌套结构|
|27|闭包变量|循环中延迟绑定|使用默认参数捕获值|

---

## 学习建议

### 第1周：基础语法

- 变量、数据类型、运算符
    
- 字符串操作
    
- 流程控制
    

### 第2周：数据结构

- 列表、元组、字典、集合
    
- 熟练掌握切片操作
    
- 理解可变与不可变
    

### 第3周：函数

- 函数定义与调用
    
- 参数类型
    
- 作用域规则
    

### 第4周：面向对象

- 类与对象
    
- 继承与多态
    
- 魔术方法
    

### 第5周：进阶特性

- 装饰器
    
- 生成器
    
- 上下文管理器
    

### 第6周：标准库与实战

- 文件操作
    
- 常用模块
    
- 小项目练习
    

---

## 推荐资源

1. **官方文档**：[https://docs.python.org/zh-cn/3/](https://docs.python.org/zh-cn/3/)
    
2. **在线练习**：[https://www.runoob.com/python3/](https://www.runoob.com/python3/)
    
3. **书籍**：《Python编程：从入门到实践》
    

---

_最后更新：2024年_