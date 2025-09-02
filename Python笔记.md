# Python

## 数值类型归纳

### 1.简单类型用来表示值

整数int、浮点数float、复数complex、逻辑值bool、字符串str

### 2.容器类型用来组织这些值

列表list、元组tuple、集合set、字典dict

### 3.数据类型之间几乎都可以转换

## 数值基本类型

### 1.数值

#### 整数类型：int

特点：不限制大小
常见的运算：
![image-20250721211545454](/Users/lmt/Library/Application Support/typora-user-images/image-20250721211545454.png)

#### 不同的进制通过不同的前缀识别

![image-20250721212534158](/Users/lmt/Library/Application Support/typora-user-images/image-20250721212534158.png)

#### 进制转换

hex（）：转换为16进制
oct（）：转化为8进制
bin（）：转化为2进制

#### 浮点数类型：float

特点：
1.操作与整数类似，浮点数受到17位有效数字限制
2.超过17位会自动转换为科学计数法
3.浮点数判断尽量不使用==判断，要使用两个浮点数的差小于一个很小很小的数进行判断

#### 复数类型

math模块中的数学函数只能用于计算整数和浮点数，无法应用到复数，要引入专门应用复数的库cmath

特点：
1.在python中序数的虚部使用j来表示，例：1+3j
2.(1+3j).imag会提出该复数的虚部
3.(1+3j).real会提出该部分的实部
4.复数之间只能比较是否相等，不能比较大小
5.abs((1+3j)-(2+4j))会得到这两个点的距离，单个复数套abs得到的是离原点的距离

### 2.逻辑值

逻辑类型bool类型

#### 逻辑运算

与：and
或：or
非：not     写在值的前面

#### 运算符的优先级

not>and>or

####  逻辑值注意事项

1.0是假，所有非0的数值都是真
2.空串是假，所有非空串都是真
3.空序列是假，所有非空的序列都是真
4.空值None表示‘无意义’或‘不知道’，也是假

### 3.字符串

#### 字符串是一种序列

![image-20250721232642592](/Users/lmt/Library/Application Support/typora-user-images/image-20250721232642592.png)

#### 字符串的表示：

1.用双引号或者单引号都可以表示字符串，但必须成对
2.三个单引号或着三个双引号可以引用多行的字符串会会包含一个换行

#### 特殊的符号用转义字符\来表示

![image-20250721222620230](/Users/lmt/Library/Application Support/typora-user-images/image-20250721222620230.png)

#### 字符串常见的操作

1.获取字符串的长度：len函数
2.切片（slice）操作：s[start​\:end:step];step:步长,步长可以为复数,包含start、不包含end（左闭右开）
3.加法和乘法：+:将两个字符串进行连接 *：将字符串重复若干次
4.判断字符串内容是否相同（==）
5.判断字符串中是否包含某个字符串（in）
例:

```python
a="hello"
'h' in a
#会返回True
```

6.删除空格
str.strip:去掉字符串前后的所有空格，内部空格不受影响
str.lstrip：去掉字符串前部（左部）的所有空格
str.rstrip：去掉字符串后部（右部）的所有空格
7.判断字母数字
str.isalpha:判断字符串是否全部由字母组成
str.isdigit:判断字符串是否全部由数字构成
str.isalnum:判断字符串是否仅包含字母和数字，而不含特殊字符
8.字符串分割：split  
9.字符串合并：join
![image-20250721232355272](/Users/lmt/Library/Application Support/typora-user-images/image-20250721232355272.png)

#### 字符集操作

ord():会返回字符在字符集中对应的数字  例如：ord（'A'）会返回65
chr():会返回字符集中相应字符对应的数字  例如：chr（65）会返回A

## 变量和引用

### 命名规则

必须由字母还有数字组合而成，还可以使用_，下划线算作字母，区分大小写（汉字也属于字母），不可以出现空格、标点、运算符,名字的首位不可以是数字

名字和数值的关联称为引用
一个数值可以和多个名字关联

### 变量的类型转换

变量的类型随着指向数据对象类型的转换而转换

### 赋值（assignment）

最基本的赋值形式：<名字>=<数值>
也可以合并赋值：a=b=c=1
还可以按照顺序依次赋值：a,b,c=6,7,8
简写赋值语句：price+=price     等价于 price=price+1

## 容器类型：列表和元组

### 数据收纳盒

用来收纳数据的数据类型
收纳盒是一种序列

### 列表

特点：列表可以删除、增加、重排、替换序列中的元素（可变类型）

#### 创建列表

方法1:方括号法[ ]
方法2:指明类型法list()

```python
# 方法1：使用方括号 []
list1 = [1, 2, 3, "hello", True]  # 可以包含任意类型
print(list1)  # 输出: [1, 2, 3, 'hello', True]

# 方法2：使用 list() 函数
list2 = list((4, 5, 6))  # 传入一个可迭代对象（如元组）
print(list2)  # 输出: [4, 5, 6]

# 空列表
empty_list = []
print(empty_list)  # 输出: []
```

#### 列表方法

![image-20250723160511238](/Users/lmt/Library/Application Support/typora-user-images/image-20250723160511238.png)

##### 1.访问元素

（1）通过索引访问
```python
fruits = ["apple", "banana", "cherry"]
print(fruits[0])  # 输出: "apple"（索引从0开始）
print(fruits[-1])  # 输出: "cherry"（-1表示最后一个元素）
```

（2）切片（Slice）
```python
numbers = [0, 1, 2, 3, 4, 5]
print(numbers[1:4])  # 输出: [1, 2, 3]（左闭右开）
print(numbers[:3])   # 输出: [0, 1, 2]（从头到索引2）
print(numbers[3:])   # 输出: [3, 4, 5]（从索引3到末尾）
print(numbers[::2])  # 输出: [0, 2, 4]（步长为2）
```

##### 2.修改列表

（1）修改单个元素

```python
fruits = ["apple", "banana", "cherry"]
fruits[1] = "orange"  # 修改索引1的元素
print(fruits)  # 输出: ["apple", "orange", "cherry"]
```

（2）修改多个元素（切片赋值）

```python
numbers = [1, 2, 3, 4, 5]
numbers[1:3] = [20, 30]  # 替换索引1和2的元素
print(numbers)  # 输出: [1, 20, 30, 4, 5]
```

##### 3.增加元素

（1）append( )-在末尾添加单个元素

```python
fruits = ["apple", "banana"]
fruits.append("cherry")
print(fruits)  # 输出: ["apple", "banana", "cherry"]
```

（2）extend( )-合并另一个列表

```python
fruits = ["apple", "banana"]
fruits.extend(["cherry", "orange"])
print(fruits)  # 输出: ["apple", "banana", "cherry", "orange"]
```

（3）insert( )-在制定位置插入元素

```python
fruits = ["apple", "cherry"]
fruits.insert(1, "banana")  # 在索引1处插入
print(fruits)  # 输出: ["apple", "banana", "cherry"]
```

##### 4.删除元素

（1）remove( )-删除指定值的元素

```python
fruits = ["apple", "banana", "cherry"]
fruits.remove("banana")  # 删除 "banana"
print(fruits)  # 输出: ["apple", "cherry"]
```

（2）pop( )-删除并返回指定索引的元素

```python
fruits = ["apple", "banana", "cherry"]
popped = fruits.pop(1)  # 删除索引1的元素
print(popped)  # 输出: "banana"
print(fruits)  # 输出: ["apple", "cherry"]
```

（3）del-删除指定索引或切片

```python
numbers = [1, 2, 3, 4, 5]
del numbers[0]  # 删除索引0的元素
print(numbers)  # 输出: [2, 3, 4, 5]

del numbers[1:3]  # 删除索引1到2的元素
print(numbers)  # 输出: [2, 5]
```

（4）clear( )-清空列表

```python
fruits = ["apple", "banana", "cherry"]
fruits.clear()
print(fruits)  # 输出: []
```

##### 5.查找元素

（1）index( )-返回元素的索引

```python
fruits = ["apple", "banana", "cherry"]
print(fruits.index("banana"))  # 输出: 1
```

（2）count( )-统计元素出现的次数

```python
numbers = [1, 2, 2, 3, 2]
print(numbers.count(2))  # 输出: 3
```

（3）in-检查元素是否存在

```python
fruits = ["apple", "banana", "cherry"]
print("banana" in fruits)  # 输出: True
print("orange" in fruits)  # 输出: False
```

##### 6.排序和反转

（1）sort( )-升序排序

```python
numbers = [3, 1, 4, 2]
numbers.sort()
print(numbers)  # 输出: [1, 2, 3, 4]
```

（2）sort(reverse=True)-降序排序

```python
numbers = [3, 1, 4, 2]
numbers.sort(reverse=True)
print(numbers)  # 输出: [4, 3, 2, 1]
```

（3）reverse( )-反转列表

```python
fruits = ["apple", "banana", "cherry"]
fruits.reverse()
print(fruits)  # 输出: ["cherry", "banana", "apple"]
```

（4）sorted( )-返回排序后的新列表（不影响原列表）

```python
numbers = [3, 1, 4, 2]
sorted_numbers = sorted(numbers)
print(sorted_numbers)  # 输出: [1, 2, 3, 4]
print(numbers)  # 原列表不变: [3, 1, 4, 2]
```

##### 7列表复制

（1）浅拷贝（copy（）或 list（）或  [:]）

```python
original = [1, 2, 3]
copy1 = original.copy()
copy2 = list(original)
copy3 = original[:]

copy1[0] = 99
print(original)  # 输出: [1, 2, 3]（原列表不受影响）
```

（2）深拷贝(嵌套列表时使用 copy.deepcopy( ) )

```python
import copy
original = [[1, 2], [3, 4]]
deep_copy = copy.deepcopy(original)
deep_copy[0][0] = 99
print(original)  # 输出: [[1, 2], [3, 4]]（原列表不受影响）
```

##### 8.列表推导式子（List Comprehension）

```python
# 生成平方列表
squares = [x**2 for x in range(5)]
print(squares)  # 输出: [0, 1, 4, 9, 16]

# 筛选偶数
numbers = [1, 2, 3, 4, 5]
evens = [x for x in numbers if x % 2 == 0]
print(evens)  # 输出: [2, 4]
```

##### 9.加法运算

语法：

```python
new_list = list1 + list2
```

list1和list2必须是列表（或其他可迭代对象需先转换为列表）
**返回一个新列表，不修改原列表**

```python
list1 = [1, 2, 3]
list2 = [4, 5, 6]
result = list1 + list2
print(result)  # 输出: [1, 2, 3, 4, 5, 6]
print(list1)   # 原列表不变: [1, 2, 3]
print(list2)   # 原列表不变: [4, 5, 6]
```

##### 10.长度、最大值、最小值

通用函数：len( ),max( ),min( ),sum( )(仅限数字序列)

```python
nums_list = [1, 2, 3]
nums_tuple = (4, 5, 6)

print(len(nums_list))    # 3
print(max(nums_tuple))   # 6
print(sum(nums_list))    # 6
```



### 元组

特点：元组是不能再更新（不可变序列）连数值也无法重新赋值，元组在保留列表大多数性能时，去掉了一些灵活性以换取更高的处理性能，元组的特点是必须有逗号

#### 创建元组

方法一：使用圆括号（）
方法二：使用tuple（）函数

```python
# 方法1：使用圆括号 ()
tuple1 = (1, 2, 3, "hello", True)
print(tuple1)  # 输出: (1, 2, 3, 'hello', True)

# 方法2：使用 tuple() 函数
tuple2 = tuple([4, 5, 6])  # 传入一个可迭代对象（如列表）
print(tuple2)  # 输出: (4, 5, 6)

# 空元组
empty_tuple = ()
print(empty_tuple)  # 输出: ()

# 单元素元组（注意逗号不能省略）
single_element_tuple = (42,)  # 必须加逗号
print(single_element_tuple)  # 输出: (42,)
```

#### 元组方法

##### 1.访问元组元素

（1）通过索引访问

```python
fruits = ("apple", "banana", "cherry")
print(fruits[0])   # 输出: "apple"（索引从0开始）
print(fruits[-1])   # 输出: "cherry"（-1表示最后一个元素）
```

（2）切片（Slice）

```python
numbers = (0, 1, 2, 3, 4, 5)
print(numbers[1:4])  # 输出: (1, 2, 3)（左闭右开）
print(numbers[:3])   # 输出: (0, 1, 2)（从头到索引2）
print(numbers[3:])   # 输出: (3, 4, 5)（从索引3到末尾）
print(numbers[::2])  # 输出: (0, 2, 4)（步长为2）
```

##### 2.元组不可变（无法修改）

元组创建后，不能修改、删除或添加元素，否则会报错：

```python
fruits = ("apple", "banana", "cherry")

# 尝试修改会报错
# fruits[0] = "orange"  # ❌ TypeError: 'tuple' object does not support item assignment

# 尝试删除会报错
# del fruits[1]  # ❌ TypeError: 'tuple' object doesn't support item deletion
```

**变通方法：转换成列表修改后再转回元组**

```python
fruits = ("apple", "banana", "cherry")
temp_list = list(fruits)  # 转成列表
temp_list[1] = "orange"  # 修改
fruits = tuple(temp_list)  # 转回元组
print(fruits)  # 输出: ("apple", "orange", "cherry")
```

##### 3.元组查询操作

（1）index( )-返回元素的索引

```python
fruits = ["apple", "banana", "cherry"]
print(fruits.index("banana"))  # 输出: 1
```

（2）count( )-统计元素出现的次数

```python
numbers = [1, 2, 2, 3, 2]
print(numbers.count(2))  # 输出: 3
```

（3）in-检查元素是否存在

```python
fruits = ["apple", "banana", "cherry"]
print("banana" in fruits)  # 输出: True
print("orange" in fruits)  # 输出: False
```

##### 4.元素拼接

（1）+运算符（合并元组）

```python
tuple1 = (1, 2, 3)
tuple2 = (4, 5, 6)
combined = tuple1 + tuple2
print(combined)  # 输出: (1, 2, 3, 4, 5, 6)
```

（2）* 运算符（重复元组）

```python
numbers = (1, 2)
repeated = numbers * 3
print(repeated)  # 输出: (1, 2, 1, 2, 1, 2)
```

##### 5.元组解包(Unpacking)

```python
person = ("Alice", 25, "Engineer")
name, age, job = person  # 解包赋值
print(name)  # 输出: "Alice"
print(age)   # 输出: 25
print(job)   # 输出: "Engineer"
```

使用 * 收集剩余元素

```python
numbers = (1, 2, 3, 4, 5)
first, *middle, last = numbers
print(first)   # 输出: 1
print(middle)  # 输出: [2, 3, 4]（自动转为列表）
print(last)    # 输出: 5
```

##### 6.元组遍历

（1）for循环遍历

```python
fruits = ("apple", "banana", "cherry")
for fruit in fruits:
    print(fruit)
```

输出：

```txt
apple
banana
cherry
```

（2）enumerate( )获取索引和值

```python
fruits = ("apple", "banana", "cherry")
for idx, fruit in enumerate(fruits):
    print(f"Index {idx}: {fruit}")
```

输出：

```text
Index 0: apple
Index 1: banana
Index 2: cherry
```

##### 7.长度、最大值、最小值

通用函数：len( ),max( ),min( ),sum( )(仅限数字序列)

```python
nums_list = [1, 2, 3]
nums_tuple = (4, 5, 6)

print(len(nums_list))    # 3
print(max(nums_tuple))   # 6
print(sum(nums_list))    # 6
```

### 标签收纳盒

给数据贴上标签，就可以通过具有特定含义的名字或者别的记号来获取数据

### 字典

字典（Dictionary）是Python中一种非常强大且常用的数据结构，它提供了键值对（key-value）存储机制。

#### 字典的特性

1.键（key）必须是不可变类型（如字符串、数字、元组），且唯一
2.值（value）可以是任意的Python对象
3.字典是无序的
4.字典是动态的，可以随时添加、修改或删除键值对
5.字典中的元素叫做数据项（item），数据项中包含标签-数据值（key-value）
6.一个键只能对应一个值

#### 创建字典

字典是可变的无序集合，用花括号{ }表示，元素形式为key：value
```python
# 创建字典
my_dict = {'name': 'Alice', 'age': 25, 'city': 'New York'}
empty_dict = {}  # 空字典
```

#### 字典方法

##### 1.访问元素

```python
print(my_dict['name'])  # 输出: Alice

# 使用get()方法更安全，可以指定默认值
print(my_dict.get('age'))  # 输出: 25
print(my_dict.get('job', 'Not specified'))  # 输出: Not specified
```

##### 2.添加修改元素

```python
my_dict['job'] = 'Engineer'  # 添加新键值对
my_dict['age'] = 26  # 修改已有键的值
```

##### 3.删除元素

```python
del my_dict['city']  # 删除指定键值对
age = my_dict.pop('age')  # 删除并返回指定键的值
my_dict.clear()  # 清空字典

#popitem删除并返回最后插入的键值对
d = {'a': 1, 'b': 2}
print(d.popitem())  # ('b', 2)
print(d)           # {'a': 1}
```

##### 4.常用方法

```python
# keys（）获取所有键
d = {'a': 1, 'b': 2}
keys = d.keys()
print(keys)       # dict_keys(['a', 'b'])
d['c'] = 3        # 视图会动态更新
print(keys)       # dict_keys(['a', 'b', 'c'])

# values（）获取所有值
d = {'a': 1, 'b': 2}
vals = d.values()
print(vals)       # dict_values([1, 2])
d['a'] = 10       # 视图会动态更新
print(vals)       # dict_values([10, 2])

# items（）获取所有键值对
d = {'a': 1, 'b': 2}
items = d.items()
print(items)      # dict_items([('a', 1), ('b', 2)])
d['c'] = 3        # 视图会动态更新
print(items)      # dict_items([('a', 1), ('b', 2), ('c', 3)])

#获取值如果键不存在则设置默认值
d = {'a': 1}
print(d.setdefault('a', 100))  # 1 (已存在)
print(d.setdefault('b', 2))    # 2 (新增)
print(d)  # {'a': 1, 'b': 2}

# 检查键是否存在
if 'name' in my_dict:
    print("Name exists")

# 更新字典
my_dict.update({'age': 27, 'gender': 'female'})

# 字典长度
length = len(my_dict)
```

##### 5.遍历字典

```python
# 遍历键
for key in my_dict:
    print(key)

# 遍历键值对
for key, value in my_dict.items():
    print(f"{key}: {value}")
```

##### 6.字典浅拷贝（copy()）

```python
d = {'a': 1, 'b': [2, 3]}
d_copy = d.copy()
d['a'] = 10
d['b'].append(4)
print(d)      # {'a': 10, 'b': [2, 3, 4]}
print(d_copy) # {'a': 1, 'b': [2, 3, 4]} (注意列表被共享)
```

##### 7.字典深拷贝（deepcopy( )）

如果想完全独立拷贝字典，包括里面的可变对象，可以用标准库的 `copy` 模块中的`deepcopy`：

```python
import copy
d_copy = copy.deepcopy(d)
```

这样，`d_copy['b']` 会是 `d['b']` 的一个全新、互不影响的列表。

##### 8.fromkeys(iterable, value)-从可迭代对象创建新字典，所有值相同

```python
keys = ['a', 'b', 'c']
d = dict.fromkeys(keys, 0)
print(d)  # {'a': 0, 'b': 0, 'c': 0}
```

##### 9.字典推导式

类似列表推导式，可以快速创建字典

```python
# 创建平方字典
squares = {x: x*x for x in range(5)}
print(squares)  # {0: 0, 1: 1, 2: 4, 3: 9, 4: 16}

# 条件筛选
even_squares = {x: x*x for x in range(10) if x % 2 == 0}
```

##### 10.特殊字典类型

Python还提供了一些特殊的字典类型：

- `collections.defaultdict` - 提供默认值的字典

  自动为不存在的键提供默认值

  ```python
  from collections import defaultdict
  dd = defaultdict(int)
  print(dd['a'])  # 0 (默认值)
  ```

- `collections.OrderedDict` - 保持插入顺序的字典

  保持插入顺序的字典

  ```python
  from collections import OrderedDict
  od = OrderedDict()
  od['a'] = 1
  od['b'] = 2
  print(list(od.keys()))  # ['a', 'b']
  ```

- `collections.Counter` - 用于计数的字典

  ```python
  from collections import Counter
  
  # 统计列表中各元素出现的次数
  words = ['apple', 'banana', 'apple', 'orange', 'banana', 'apple']
  word_counts = Counter(words)
  
  print(word_counts)
  # 输出: Counter({'apple': 3, 'banana': 2, 'orange': 1})
  ```

##### 11.实际应用示例

```python
# 统计单词频率
text = "hello world hello python world python python"
words = text.split()
word_count = {}

for word in words:
    word_count[word] = word_count.get(word, 0) + 1

print(word_count)
# 输出: {'hello': 2, 'world': 2, 'python': 3}
```

### 集合

集合（Set）是Python中的一种内置数据类型，用于存储**无序、不重复**的元素集合。集合在Python中非常有用，特别是在需要快速成员测试、去重或执行数学集合操作（如并集、交集等）时。

#### 标签袋

通过改造字典类型，去掉关联数据值，只留下标签的新容器类型

#### 集合的特性

1.python中的集合类似于数学中的集合
2.无序性：集合中的元素没有固定顺序
3.唯一性：集合中的元素都是唯一的（自动去重）
4.可变性：集合本身是可变的，但集合中的元素必须是不可变类型（如数字、字符串、元组等）

#### 创建集合

```python
# 使用花括号创建集合
fruits = {'apple', 'banana', 'orange'}
print(fruits)  # 输出可能是 {'banana', 'orange', 'apple'}（顺序不确定）

# 使用set()函数创建集合
numbers = set([1, 2, 3, 4, 5])
print(numbers)  # 输出 {1, 2, 3, 4, 5}

# 空集合必须用set()创建，不能用{}（{}创建的是空字典）
empty_set = set()
```

#### 集合操作

##### 1.集合操作

```python
# 添加元素
fruits.add('grape')

# 移除元素
fruits.remove('banana')  # 如果元素不存在会引发KeyError
fruits.discard('banana')  # 安全移除，元素不存在也不会报错

# 随机弹出一个元素
popped = fruits.pop()

# 清空集合
fruits.clear()

# 获取集合长度
len(fruits)
```

##### 2.集合运算

```python
a = {1, 2, 3, 4}
b = {3, 4, 5, 6}

# 并集
print(a | b)  # {1, 2, 3, 4, 5, 6}
print(a.union(b))  # 同上

# 交集
print(a & b)  # {3, 4}
print(a.intersection(b))  # 同上

# 差集（在a中但不在b中）
print(a - b)  # {1, 2}
print(a.difference(b))  # 同上

# 对称差集（仅在a或仅在b中的元素）
print(a ^ b)  # {1, 2, 5, 6}
print(a.symmetric_difference(b))  # 同上
```

##### 3.集合比较

```python
x = {1, 2}
y = {1, 2, 3}

# 子集检查
print(x <= y)  # True
print(x.issubset(y))  # True

# 真子集检查
print(x < y)  # True

# 超集检查
print(y >= x)  # True
print(y.issuperset(x))  # True

# 真超集检查
print(y > x)  # True
```

##### 4.集合推导式

类似于列表推导式，Python也支持集合推导式
```python
squares = {x**2 for x in range(10)}
print(squares)  # {0, 1, 4, 9, 16, 25, 36, 49, 64, 81}
```

##### 5.不可变集合

```python
fs = frozenset([1, 2, 3])
# fs.add(4)  # 会报错，因为frozenset不可变
```

#### 应用场景

1.快速成员测试（比列表快很多）
2.数据去重
3.数据集合运算
4.过滤重复项

### 不可变类型与可变类型

灵活性强会花费一些计算或者存储的代价去维持这些强大的功能

#### 不可变类型

一旦创建就无法修改的数据类型，有整数、浮点数、复数、字符串、逻辑值、元表

##### 1.整数

```python
a = 10
a += 1  # 实际上是创建了新对象，a 指向新的内存地址。
```

##### 2.浮点数

```python
b = 3.14
b += 1  # 新对象被创建。
```

##### 3.布尔值（bool）

```python
c = True
c = False  # 新对象。
```

##### 4.字符串（str）

```python
s = "hello"
s += " world"  # 新字符串对象，原字符串不可变。
```

##### 5.元组（tuple）

```python
t = (1, 2, 3)
# t[0] = 10  # 报错！元组不可修改。
```

##### 6.不可变集合（frozenset）

```python
fs = frozenset([1, 2, 3])
```

#### **不可变类型特点**

1.修改时会创建新对象，原对象不变
2.适合作为字典的键（如tuple、str、int），因为哈希值不可变

#### 可变类型

可以随时改变的数据类型，有列表、字典、集合、字节数组

##### 1.列表

```python
lst = [1, 2, 3]
lst.append(4)  # 直接修改原列表。
```

##### 2.字典

```python
d = {"a": 1}
d["b"] = 2  # 直接修改原字典。
```

##### 3.集合

```python
s = {1, 2, 3}
s.add(4)  # 直接修改原集合。
```

##### 4.字节数组

```python
ba = bytearray(b"hello")
ba[0] = 72  # 直接修改。
```

#### **注意：**

**多个变量通过赋值引用同一个可变类型对象时，通过其中任何一个变量改变了可变类型对象，其他变量也随之改变**

##### 案例1:列表（list）的共享引用

```python
# 两个变量 a 和 b 引用同一个列表
a = [1, 2, 3]
b = a  # b 和 a 指向同一个列表

# 通过 b 修改列表
b.append(4)

print(a)  # 输出: [1, 2, 3, 4] （a 也被修改！）
print(b)  # 输出: [1, 2, 3, 4]
print(a is b)  # 输出: True （是同一个对象）
```

**关键点：a和b是同一个列表对象的两个别名，修改其中一个会影响另一个**

##### 案例2:字典（dict）的共享引用

```python
# 两个变量指向同一个字典
dict1 = {"name": "Alice"}
dict2 = dict1  # dict2 和 dict1 引用同一个字典

# 通过 dict2 修改字典
dict2["age"] = 25

print(dict1)  # 输出: {'name': 'Alice', 'age': 25} （dict1 也被修改！）
print(dict2)  # 输出: {'name': 'Alice', 'age': 25}
```

##### 案例3:集合（set）的共享引用

```python
# 两个变量引用同一个集合
set1 = {1, 2, 3}
set2 = set1  # set2 和 set1 指向同一个集合

# 通过 set2 修改集合
set2.add(4)

print(set1)  # 输出: {1, 2, 3, 4} （set1 也被修改！）
print(set2)  # 输出: {1, 2, 3, 4}
```

##### 出现该现象的原因

- 可变对象（如列表、字典、集合）在内存中只有一份副本，所有赋值操作只是创建新的引用（别名），而不是创建新对象。
- 修改对象时，所有引用该对象的变量都会看到变化。

##### 如何避免意外修改

如果需要独立副本，需显式复制对象：
1.**浅拷贝（Shallow Copy）**

- 适用于简单嵌套的可变对象（如单层列表）。

```python
a = [1, 2, 3]
b = a.copy()  # 或 b = a[:] （创建新列表）

b.append(4)
print(a)  # 输出: [1, 2, 3] （a 未被修改）
print(b)  # 输出: [1, 2, 3, 4]
```

#### 2. **深拷贝（Deep Copy）**

- 适用于多层嵌套的可变对象（如列表中的列表）。

```python
import copy

a = [[1, 2], [3, 4]]
b = copy.deepcopy(a)  # 完全独立的新对象

b[0][0] = 99
print(a)  # 输出: [[1, 2], [3, 4]] （a 不变）
print(b)  # 输出: [[99, 2], [3, 4]]
```



## 输入和输出

### input

##### 1. 基本概述
`input()` 是Python内置的一个函数，用于从控制台（标准输入）接收用户输入。它会暂停程序的执行，等待用户输入数据，并将用户输入的数据作为字符串返回。

---

##### 2. 函数原型

```python
input([prompt])
```

- `prompt`（可选）：一个字符串，作为提示信息显示给用户，提醒用户输入内容。  
- 返回值：用户输入的内容，类型为字符串（`str`）。

---

##### 3. 使用示例

```python
name = input("请输入你的名字：")
print("你好，" + name)
```

运行时，会显示提示 `"请输入你的名字："`，等待用户输入。当用户输入完成后，按回车，程序继续执行，将用户输入的内容赋值给变量 `name`。

---

##### 4. 注意事项

- **返回类型始终是字符串**  
  无论用户输入是数字还是其他字符，`input()` 函数返回的都是字符串类型。如果需要数值类型，需要手动转换，比如：
  
  ```python
  age = int(input("请输入你的年龄："))
  ```
  这样才会获得一个整数类型的 `age` 变量。
  
- **输入内容的安全性**  
  在某些场景下，用户输入的内容可能包含恶意代码或不符合预期。要谨慎处理用户输入，避免安全问题，如代码注入、格式错误等。

- **Python 2.x 和 Python 3.x 的区别**  
  
  - Python 2中用的是 `raw_input()` 函数，返回字符串。  
  - Python 2的 `input()` 会尝试将输入的内容作为Python表达式求值（不安全）。  
  - Python 3中，`input()`函数的功能等同于Python 2的`raw_input()`，直接返回字符串。

---

##### 5. 示例：读取整数并计算平方

```python
num_str = input("请输入一个整数：")
num = int(num_str)  # 将字符串转换成整数
square = num ** 2
print(f"{num} 的平方是 {square}")
```

运行流程：

1. 显示提示信息。  
2. 用户输入，如 `5`，按回车。  
3. 读取字符串 `"5"`，转换成整数 `5`。  
4. 计算平方，输出结果。

---

##### 6. 进一步示例：处理异常

```python
try:
    num = int(input("请输入一个整数："))
    print(f"您输入的数字是 {num}")
except ValueError:
    print("输入无效，请输入一个整数。")
```

用 `try-except` 块捕获转换异常，防止用户输入非数字导致程序崩溃。

---

##### 7. 总结

- `input()` 用于获取用户的输入，返回字符串。  
- 可以给`input()`传递一个可选的提示信息字符串。  
- 需要时，手动将输入转换成其它数据类型。  
- 在Python的交互式程序和命令行脚本中非常常用。  
- 注意异常处理和输入内容的安全性。

---

#### `input()` 函数的高级用法和技巧

---

##### 1. 多值输入：一次输入多个数据

通常用户可能需要一次输入多个值，然后程序需要对这些值进行分割和处理，比如一行输入多个数字。

```python
# 用户输入多个数字，以空格分隔
data = input("请输入多个数字，用空格分隔：")  # 输入示例：1 2 3 4 5
numbers = data.split()  # 以空格分割字符串，得到列表 ['1', '2', '3', '4', '5']
numbers = [int(n) for n in numbers]  # 转换成整数列表
print(numbers)
```

---

##### 2. 限定输入格式和验证

可以使用循环和条件判断，确保用户输入符合预期格式。

```python
while True:
    age = input("请输入年龄（数字）：")
    if age.isdigit():
        age = int(age)
        break
    else:
        print("输入格式错误，请输入数字。")
print(f"你的年龄是 {age}")
```

这段代码会一直提示用户输入，直到输入有效数字。

---

##### 3. 使用正则表达式验证输入

对于复杂的格式（比如邮箱、手机号等），可以用正则表达式对输入进行验证。

```python
import re

pattern = r'^\w+@\w+\.\w+$'  # 简单邮箱正则

email = input("请输入邮箱：")
if re.match(pattern, email):
    print("邮箱格式正确")
else:
    print("邮箱格式错误")
```

---

##### 4. 隐藏输入: 获取密码等敏感信息

`input()` 默认显示用户输入的内容，敏感输入需要隐藏。Python 标准库 `getpass` 可用来隐藏输入字符。

```python
import getpass

password = getpass.getpass("请输入密码：")
print("密码长度为：", len(password))
```

`getpass.getpass()` 会隐藏用户输入的内容，适合密码输入。

---

##### 5. 实现输入超时功能

标准 `input()` 方法没有输入超时限制。如果需要实现输入时间限制，可以使用线程或第三方库。以下是用 `signal` 模块在类Unix系统实现超时示例（Windows不支持）：

```python
import signal

def handler(signum, frame):
    raise TimeoutError

signal.signal(signal.SIGALRM, handler)
signal.alarm(5)  # 5秒后触发信号

try:
    data = input("请在5秒内输入内容：")
    signal.alarm(0)  # 取消定时器
    print("你输入的是：", data)
except TimeoutError:
    print("输入超时！")
```

---

##### 6. 自定义输入提示符样式

虽然 `input()` 自带提示文字，但如果想实现更丰富的提示，比如颜色或格式，可以结合`print()`打印彩色提示，再调用 `input()`：

```python
# 终端彩色打印示例（依赖ANSI转义码）
print("\033[1;32m请输入用户名：\033[0m", end="")
username = input()
print(f"欢迎你，{username}！")
```

---

##### 7. 多行输入

标准 `input()` 只能读取一行。如果想输入多行，可以循环调用，或者用其它方式（如 EOF 标志）结束输入：

```python
print("请输入多行文本，输入空行结束：")
lines = []
while True:
    line = input()
    if line == "":
        break
    lines.append(line)
text = "\n".join(lines)
print("你输入的内容是：")
print(text)
```

---

##### 8. 读取数字并处理异常的简洁写法

定义一个通用的输入读取函数，可以多次复用：

```python
def input_int(prompt):
    while True:
        try:
            return int(input(prompt))
        except ValueError:
            print("请输入有效的整数！")

num = input_int("请输入一个整数：")
print("输入的数字是:", num)
```

---

##### 总结

- 可以将一次输入拆分成多个值并批量处理。  
- 结合循环和判断实现输入格式校验。  
- 利用正则表达式或其他库确保输入合法。  
- 用`getpass`隐藏敏感输入。  
- 结合系统信号或线程实现输入超时。  
- 用 ANSI 转义码或库实现彩色提示。  
- 模拟多行输入模式。  
- 抽象通用的输入读取函数。  

### print

#### 1. 基本介绍

`print()` 是 Python 的一个内置函数，主要用于将信息输出到控制台（标准输出）。它通常用于调试、展示结果或与用户交互。

---

#### 2. 函数原型（Python 3.x）

```python
print(*objects, sep=' ', end='\n', file=sys.stdout, flush=False)
```

- `*objects`：一个或多个要打印的对象，多个对象之间用逗号分隔。
- `sep`（separator）：对象之间的分隔符，默认是一个空格。
- `end`：输出的结尾字符，默认是换行符 `\n`，即打印完自动换行。
- `file`：输出目标，默认是标准输出流 `sys.stdout`。可以替换成文件对象，实现输出到文件。
- `flush`：是否强制立即刷新输出缓冲区，默认是 `False`。

---

#### 3. 基础用法示例

```python
print("Hello, world!")
```

打印字符串并换行。

```python
print("Python", "is", "awesome")
```

打印多个对象，默认之间用空格分隔，输出：

```
Python is awesome
```

---

#### 4. 详细参数说明及示例

##### 4.1 `sep` — 分隔符参数

默认所有参数之间用空格分隔，可以修改：

```python
print("Python", "is", "awesome", sep="-")
```

输出：

```
Python-is-awesome
```

`sep` 可以是任意字符串，如逗号、制表符等。

---

##### 4.2 `end` — 行尾符

默认行尾是换行符，导致打印结束后光标换到下一行。可以修改为其他字符：

```python
print("Hello,", end=" ")
print("world!")
```

输出：

```
Hello, world!
```

这里两次 `print()` 在同一行输出。

---

##### 4.3 `file` — 输出位置

默认输出到控制台（标准输出），也可以输出到文件：

```python
with open("out.txt", "w") as f:
    print("Hello, file!", file=f)
```

这会将文本写入 `out.txt` 文件。

---

##### 4.4 `flush` — 是否立即刷新缓冲区

在某些实时需要显示输出的场合，需要立即刷新缓冲区：

```python
import time
print("开始计时", end="", flush=True)
time.sleep(3)
print("，3秒结束")
```

如果不加 `flush=True`，可能不会立即打印第一条信息。

---

#### 5. 打印格式

##### 5.1 使用格式化字符串（f-string，Python 3.6+）

```python
name = "Alice"
age = 30
print(f"姓名：{name}，年龄：{age}")
```

输出：

```
姓名：Alice，年龄：30
```

##### 5.2 使用 `str.format()`

```python
print("姓名：{}，年龄：{}".format(name, age))
```

##### 5.3 旧式 `%` 格式化

```python
print("姓名：%s，年龄：%d" % (name, age))
```

---

#### 6. 打印多个行、换行与转义

- 换行符 `\n` 可在字符串内插入换行：

```python
print("第一行\n第二行\n第三行")
```

- 制表符 `\t` 可缩进：

```python
print("一\t二\t三")
```

---

#### 7. 打印非字符串对象

`print()` 会自动调用对象的 `str()` 函数，将其转成字符串输出：

```python
print(123, 45.67, True, None, [1, 2, 3])
```

输出：

```python
123 45.67 True None [1, 2, 3]
```

---

#### 8. 进阶用法

##### 8.1 打印到标准错误流

```python
import sys
print("错误信息", file=sys.stderr)
```

##### 8.2 禁止自动换行（组合 `end` 参数）

```python
for i in range(3):
    print(i, end=" ")  # 0 1 2
```

##### 8.3 在同一行更新输出（实现类似进度条）

```python
import time
for i in range(101):
    print(f"\r进度: {i}%", end="")
    time.sleep(0.05)
print()  # 换行
```

`'\r'` 是回车符，回到行首覆盖输出，实现动态更新。

---

#### 9. 注意事项

- Python2 与 Python3 的 `print` 不同：Python2 中是语句，Python3中是函数。
- 打印大量数据时注意缓冲区和性能。
- 对象需要实现 `__str__` 或 `__repr__`，否则打印默认形式。

---

#### 10. 示例集锦

```python
# 多个参数，指定分隔符和结束符
print("2023", "06", "05", sep="-", end="")

# 输出到文件
with open("log.txt", "a") as f:
    print("程序运行日志", file=f)

# f-string 格式化
x = 10
y = 20
print(f"x={x}, y={y}, sum={x+y}")

# 进度条动画
import sys, time
for i in range(101):
    print(f"\rLoading... {i}%", end='')
    sys.stdout.flush()  # 立即输出
    time.sleep(0.05)
print()
```

---

## 控制流程

### 条件分支语句

条件分支语句是程序中的基本控制结构，用于根据条件的真假来决定执行哪段代码。Python 通过 `if`、`elif` 和 `else` 关键字来实现条件分支。

---

#### 1. 基本语法

```python
if 条件表达式:
    代码块1  # 条件为真时执行
elif 其他条件表达式:
    代码块2  # 上述条件不成立且此条件成立时执行
else:
    代码块3  # 上述条件都不成立时执行
```

- `if` 必须要有，它后面跟条件表达式和冒号 `:`；
- `elif` 和 `else` 是可选的，可以有多个 `elif`，最多一个 `else`；
- 条件表达式计算结果为布尔值 `True` 或 `False`；
- 冒号后必须换行并缩进代码块，Python 通过缩进区分代码块。

---

#### 2. 代码示例

```python
num = 10

if num > 0:
    print("正数")
elif num == 0:
    print("零")
else:
    print("负数")
```

输出：

```python
正数
```

---

#### 3. 条件表达式

条件表达式可以是任意返回布尔值的表达式，比如：

- 比较运算符：`==, !=, >, <, >=, <=`
- 逻辑运算符：`and, or, not`
- 成员运算符：`in`, `not in`
- 身份运算符：`is`, `is not`
- 自定义函数返回布尔值

示例：

```python
a = 5
b = 10

if a < b and b < 20:
    print("a 小于 b 且 b 小于 20")

if 'h' in "hello":
    print("包含字母 h")
```

---

#### 4. if 语句的变形

##### 4.1 单行 if

当只有一条语句时，可以写成单行：

```python
if condition: do_something()
```

但是建议为了可读性，还是写成多行。

##### 4.2 三元表达式（条件表达式）

三元表达式用来简洁地根据条件选择值：

```python
a = 10
result = "大于5" if a > 5 else "不大于5"
print(result)
```

输出：

```python
大于5
```

---

#### 5. 嵌套 if

if 语句可以嵌套使用：

```python
x = 10
y = 5

if x > 0:
    if y > 0:
        print("x 和 y 都是正数")
    else:
        print("x 是正数，但 y 不是正数")
else:
    print("x 不是正数")
```

---

#### 6. 注意事项

- 条件表达式必须是布尔值或能转换为布尔值的表达式。

  Python 中，下列值被认为是 `False`：

  - `False`
  - `None`
  - 0，0.0，0j
  - 空字符串 `""`
  - 空列表 `[]`
  - 空元组 `()`
  - 空字典 `{}`
  - 空集合 `set()`

  其他值都被认为是 `True`。

- 注意缩进，Python 用缩进区分代码块。

---

#### 7. 小结

- 使用 `if` 判断条件是否成立；
- 可以使用 `elif` 判断其他条件；
- 使用 `else` 处理所有其它情况；
- 条件表达式可以是任何返回布尔值的表达式；
- 支持嵌套多级 if；
- 可使用三元表达式简洁表达条件选择。

### 迭代循环

#### for循环

---

##### 1. 什么是 `for` 循环？

`for` 循环用于 **遍历一个序列（如列表、元组、字符串等）或者其他可迭代对象**，依次取出其中的每个元素，执行循环体的代码。

它不像 `while` 依赖一个“条件真假”来判断是否继续，而是直接遍历对象中的各个元素，遍历完成自动结束。

---

##### 2. 基本语法

```python
for 变量 in 可迭代对象:
    循环体代码块
```

- `变量` 每次迭代时会被赋值为序列中的当前元素；
- `可迭代对象` 可以是列表、字符串、元组、字典、集合、文件对象等所有支持迭代的对象；
- 冒号后换行，下一行缩进部分为循环体。

---

##### 3. 示例

###### 遍历列表：

```python
fruits = ['apple', 'banana', 'cherry']
for fruit in fruits:
    print(fruit)
```

输出：

```python
apple
banana
cherry
```

###### 遍历字符串：

```python
for ch in "hello":
    print(ch)
```

输出：

```
h
e
l
l
o
```

---

##### 4. 使用 `range()` 生成数字序列

`for` 循环经常搭配 `range()` 函数使用，方便生成数字序列。

- `range(stop)`：生成从 0 到 `stop-1` 的整数序列；
- `range(start, stop)`：生成从 `start` 到 `stop-1`；
- `range(start, stop, step)`：步长为`step`。

如：

```python
for i in range(5):
    print(i)
```

输出：

```
0
1
2
3
4
```

---

##### 5. 复杂一点的例子

###### 遍历字典的键值对

```python
info = {"name": "Alice", "age": 25}
for key, value in info.items():
    print(f"{key}: {value}")
```

输出：

```python
name: Alice
age: 25
```

---

##### 6. 扩展：`for` 循环中的控制语句

- **`break`**：提前终止循环
- **`continue`**：跳过当前循环，进入下一轮
- **`else`**：`for` 循环正常执行完毕后执行，不遇到 `break` 时执行

示例：

```python
for i in range(5):
    if i == 3:
        break
    print(i)
else:
    print("循环完成")
```

输出：

```
0
1
2
```

注意，因为遇到 `break`，`else` 不执行。

---

##### 7. `for` 循环和 `while` 循环的区别

| 特点     | for循环                      | while循环                |
| -------- | ---------------------------- | ------------------------ |
| 控制方式 | 遍历序列或迭代对象           | 条件表达式真假控制       |
| 使用场景 | 适合知道循环次数或遍历时使用 | 适合基于条件的循环       |
| 终止条件 | 遍历结束自动停止             | 条件变假时停止           |
| 简洁程度 | 较简洁，常用于序列遍历       | 灵活度高，可用于复杂条件 |

---

##### 8. `for` 循环的常见用法总结

- 遍历列表、字符串、元组、集合、字典；
- 使用 `range` 生成数字序列；
- 可配合 `break`、`continue` 控制执行；
- 支持 `else` 语句块（无 `break` 才执行）；
- 适合遍历固定长度或枚举一个集合中的元素。

---

##### 9. 代码示例综合

```python
for i in range(1, 6):
    if i % 2 == 0:
        continue  # 跳过偶数
    print(f"奇数: {i}")
else:
    print("循环结束")
```

输出：

```python
奇数: 1
奇数: 3
奇数: 5
循环结束
```

---

### 条件循环

#### while循环

---

##### 1. `while` 循环语法

```python
while 条件表达式:
    循环体代码块
```

- **条件表达式**：每次循环开始时都会求值，如果结果为 `True`，执行循环体；
- **循环体代码块**：满足条件时执行的代码，需要缩进；
- 循环会重复执行，直到条件表达式为 `False`。

---

##### 2. 基本示例

```python
count = 0
while count < 5:
    print(f"当前计数是: {count}")
    count += 1  # 计数器自增避免死循环
```

运行结果：

```txt
当前计数是: 0
当前计数是: 1
当前计数是: 2
当前计数是: 3
当前计数是: 4
```

---

##### 3. 循环执行流程

1. 判断条件表达式，如果为 `False`，退出循环；
2. 条件为 `True`，执行循环体代码；
3. 执行完循环体后，再次判断条件；
4. 重复上述步骤直到条件为 `False`。

---

##### 4. 注意避免死循环

如果条件永远为 `True`，循环就永远不会停止，造成死循环。例如：

```python
while True:
    print("无限循环")
```

如果写这样代码，一定要有跳出循环的语句（比如 `break`），否则程序会一直运行。

---

##### 5. 控制循环的关键字

- `break`：跳出整个循环，循环立即终止
- `continue`：跳过当前循环剩余语句，直接开始下一次循环条件判断
- `else`：`while` 循环也可以带有 `else` 代码块，只有循环正常结束（条件为假而退出）才执行 `else` 块，`break` 跳出循环则不会执行 `else`

示例：

```python
count = 0
while count < 5:
    if count == 3:
        break  # 遇到3时终止循环
    print(count)
    count += 1
else:
    print("循环正常结束，没有遇到break")

# 输出:
# 0
# 1
# 2
```

---

##### 6. `while` + `else` 作用详解

`else` 块在 `while` 循环的条件变为假时执行。如果循环是通过 `break` 提前终止，`else` 不执行。

示例：

```python
n = 1
while n < 5:
    print(n)
    n += 1
else:
    print("循环正常结束")
```

输出：

```
1
2
3
4
循环正常结束
```

---

##### 7. 使用循环实现简单功能示例

- **求和**

```python
total = 0
num = 1
while num <= 100:
    total += num
    num += 1
print(f"1到100的和是: {total}")
```

- **用户输入交互**

```python
while True:
    s = input("请输入数字，输入exit退出：")
    if s == 'exit':
        break
    print(f"你输入的数字是{s}")
```

---

##### 8. 多重循环

和 `if` 一样，`while` 循环也可以嵌套：

```python
i = 1
while i <= 3:
    j = 1
    while j <= 2:
        print(f"i={i}, j={j}")
        j += 1
    i += 1
```

---

##### 9. 条件循环和`for`循环的区别

- `while` 更适合基于状态或条件的循环
- `for` 一般用来遍历序列（列表、元组、字符串等）

示例对比：

```python
# while基于条件循环
count = 0
while count < 5:
    print(count)
    count += 1

# for遍历列表
for item in [0, 1, 2, 3, 4]:
    print(item)
```

---

##### 10. 小结

- 条件循环用`while`实现，根据条件表达式循环执行代码；
- 必须保证循环体内能使条件表达式最终为假，避免死循环；
- 支持`break`、`continue`控制循环流程；
- `while`循环可搭配`else`，在无`break`退出时执行；
- 可以进行嵌套，完成复杂控制逻辑。

#### range函数

range`是Python内置的一个函数，常用于生成整数序列，通常用于`for`循环中遍历固定次数的循环。它返回一个不可变的序列对象（range对象），表示一个按指定规则生成的整数数列。

##### 基本语法

```python
range(stop)
range(start, stop[, step])
```

- **start**: 计数从start开始（包含start），默认是0。
- **stop**: 计数到stop结束（但不包含stop）。
- **step**: 计数步长，默认是1，可以为负数，表示递减。

##### 参数说明

- `start`：起始值，序列从该值开始（包含此值）。
- `stop`：结束值，序列到此值结束，但不包含该值。
- `step`：步长，默认为1。

##### 例子

```python
for i in range(5):
    print(i)
# 输出: 0 1 2 3 4

for i in range(2, 6):
    print(i)
# 输出: 2 3 4 5

for i in range(1, 10, 2):
    print(i)
# 输出: 1 3 5 7 9

for i in range(10, 0, -2):
    print(i)
# 输出: 10 8 6 4 2
```

##### 特点

- `range`返回的是一个`range`对象，不是一个列表。如果想要一个列表，可以用`list(range(...))`转换。
- `range`对象支持序列的大部分操作，比如切片、成员判断（`in`）、迭代等。
- 性能和内存效率较高，因为它不会一次生成所有数字，而是按需生成。
- 左闭右开

---

### 代码组织：函数

---

#### 一、函数的基本结构

Python中函数采用`def`关键字定义，基本格式为：

```python
def 函数名(参数列表):
    函数体
    return 返回值
```

- **函数名**：遵循标识符命名规则，一般用小写字母+下划线，如`calculate_sum`。
- **参数列表**：可有0或多个参数，参数之间用逗号分隔。
- **函数体**：执行的代码块，必须缩进。
- **return**：返回值，可以没有return，默认返回`None`。

示例：

```python
def greet(name):
    print(f"Hello, {name}!")
```

调用：

```python
greet("Alice")  # 输出：Hello, Alice!
```

---

#### 二、函数参数详解

Python的函数参数非常灵活，支持多种类型：

##### 1. 位置参数（Positional Arguments）

按顺序传递给函数：

```python
def add(a, b):
    return a + b

print(add(2, 3))  # 5
```

##### 2. 默认参数（Default Arguments）

给参数指定默认值，如果调用时不传则使用默认值：

```python
def greet(name="World"):
    print(f"Hello, {name}!")

greet()          # Hello, World!
greet("Alice")   # Hello, Alice!
```

注意：默认参数应放在参数列表的末尾。

##### 3. 关键字参数（Keyword Arguments）

调用时指定参数名，顺序无关：

```python
def introduce(name, age):
    print(f"My name is {name}, I'm {age} years old.")

introduce(age=20, name="Bob")  # My name is Bob, I'm 20 years old.
```

##### 4. 可变位置参数（*args）

允许传入任意多个位置参数，函数内部作为元组处理：

```python
def sum_all(*args):
    return sum(args)

print(sum_all(1, 2, 3))  # 6
```

##### 5. 可变关键字参数（**kwargs）

允许传入任意多个关键字参数，函数内部作为字典处理：

```python
def print_info(**kwargs):
    for key, value in kwargs.items():
        print(f"{key}: {value}")

print_info(name="Alice", age=25)
```

##### 6. 参数组合示例

```python
def func(a, b=2, *args, **kwargs):
    print(f"a={a}, b={b}")
    print(f"args={args}")
    print(f"kwargs={kwargs}")

func(1, 3, 4, 5, x=10, y=20)
```

输出：

```python
a=1, b=3
args=(4, 5)
kwargs={'x': 10, 'y': 20}
```

---

#### 三、函数的返回值

- 使用`return`返回结果
- 可以返回多个值（实际上是返回一个元组）
- 如果没有return，默认返回`None`

示例：

```python
def calculate(a, b):
    return a + b, a * b

sum_, product = calculate(3, 5)
print(sum_)     # 8
print(product)  # 15
```

---

#### 四、函数文档字符串（Docstring）

给函数加注释，描述函数功能，方便别人阅读和使用。

格式：

```python
def greet(name):
    """
    向指定的人打招呼
    
    参数:
    name -- 要打招呼的人的名字
    
    返回值:
    无
    """
    print(f"Hello, {name}!")
```

调用可以使用`help(greet)`查看文档。

---

#### 五、匿名函数 lambda

Python支持用`lambda`快速定义简单匿名函数。

语法：

```python
lambda 参数: 表达式
```

示例：

```python
square = lambda x: x * x
print(square(5))  # 25
```

- Lambda只能写单个表达式
- 常用于函数式编程，如`map`, `filter`, `sorted`等

示例：

```python
nums = [1, 2, 3, 4, 5]
squares = list(map(lambda x: x*x, nums))
print(squares)  # [1, 4, 9, 16, 25]
```

---

#### 六、函数作为对象

Python函数是第一类对象，可以赋值，传参，甚至作为返回值。

示例：

```python
def add(a, b):
    return a + b

f = add  # 函数赋值
print(f(2, 3))  # 5

def operate(func, x, y):
    return func(x, y)

print(operate(add, 5, 6))  # 11
```

---

#### 七、嵌套函数与闭包

- **嵌套函数**：一个函数内部定义另一个函数
- **闭包**：内部函数引用外部函数变量，外部函数返回内部函数

示例：

```python
def outer(msg):
    def inner():
        print(msg)
    return inner

f = outer("Hello")
f()  # Hello
```

这种特性在装饰器写法中经常用到。

---

#### 八、递归函数

函数调用自身，用于分解复杂问题。

示例：计算阶乘

```python
def factorial(n):
    if n == 0:
        return 1
    else:
        return n * factorial(n - 1)

print(factorial(5))  # 120
```

---

#### 九、装饰器（Decorator）

装饰器是修改函数行为的一种方式，通常使用`@`语法。

示例：

```python
def decorator(func):
    def wrapper():
        print("开始执行函数")
        func()
        print("函数执行结束")
    return wrapper

@decorator
def say_hello():
    print("Hello!")

say_hello()
```

输出：

```
开始执行函数
Hello!
函数执行结束
```

---

#### 十、内置函数相关

- `help(function)` 查看函数说明
- `dir(function)` 查看函数属性
- `callable(object)` 判断对象是否可调用（函数即可调用）

---

#### 总结

| 内容            | 说明                                                |
| --------------- | --------------------------------------------------- |
| 定义函数        | 用`def`关键字定义                                   |
| 参数传递        | 位置参数、默认参数、关键字参数、`*args`、`**kwargs` |
| 返回值          | 用`return`返回，可以是任意数据类型                  |
| 函数文档字符串  | 用三引号标注，方便生成文档                          |
| 匿名函数        | 用`lambda`定义简单函数                              |
| 函数作为对象    | 函数可以赋值、传参及返回                            |
| 嵌套函数 & 闭包 | 在函数内部定义函数并引用外部变量                    |
| 递归函数        | 函数自己调用自己                                    |
| 装饰器          | 增加或修改函数功能的高级用法                        |

### map( )函数

---

#### 一、什么是 `map` 函数？

`map` 是Python内置的高阶函数，用于将一个函数应用到**可迭代对象**（如列表、元组等）的每个元素上，返回一个迭代器，包含每次函数调用的结果。

---

#### 二、基本语法

```python
map(function, iterable, ...)
```

- `function`：一个函数，接受与`iterable`元素对应的参数数量相同
- `iterable`：一个或多个可迭代对象（如 list、tuple、str 等）
- 返回值：返回一个map对象（迭代器），需要用`list()`或`for`循环等形式消费

---

#### 三、功能说明

- 对对应位置的元素调用`function`，返回结果构成新的迭代器
- 支持同时传入多个可迭代对象，函数参数对应位置元素
- 当传入多个可迭代对象时，`map`根据最短的可迭代对象长度停止

---

#### 四、简单示例

```python
def square(x):
    return x * x

nums = [1, 2, 3, 4, 5]

result = map(square, nums)  # 返回map对象
print(result)  # <map object at 0x...>

print(list(result))  # [1, 4, 9, 16, 25]
```

---

#### 五、使用lambda表达式

```python
nums = [1, 2, 3, 4, 5]
squares = map(lambda x: x * x, nums)
print(list(squares))  # [1, 4, 9, 16, 25]
```

---

#### 六、多个可迭代对象示例

```python
nums1 = [1, 2, 3]
nums2 = [4, 5, 6]

result = map(lambda x, y: x + y, nums1, nums2)
print(list(result))  # [5, 7, 9]
```

**注意**：如果传入的可迭代对象长度不一致，`map`按照最短的长度停止。

```python
nums1 = [1, 2, 3, 7]
nums2 = [4, 5, 6]

result = map(lambda x, y: x + y, nums1, nums2)
print(list(result))  # [5, 7, 9]  长度以3为准
```

---

#### 七、与循环结合使用

也可以直接用`for`循环迭代map对象：

```python
nums = [1, 2, 3]
for val in map(lambda x: x*2, nums):
    print(val)
```

输出：

```
2
4
6
```

---

#### 八、小结

| 关键词       | 说明                                                     |
| ------------ | -------------------------------------------------------- |
| 用途         | 将函数应用到可迭代对象的每个元素                         |
| 参数         | `function` 函数，`iterable` 可迭代对象（可多个）         |
| 返回值       | 返回迭代器（map对象）                                    |
| 特点         | 支持多个可迭代对象参数，函数对应每个迭代对象对应位置参数 |
| 和lambda结合 | 使用lambda表达式，代码更简洁                             |
| 注意         | 多个可迭代长度不一样时，以最短长度为准                   |

---

#### 九、示例综合

假设我们有两个列表存储了商品单价和数量，现在想计算每个商品的总价：

```python
prices = [10, 20, 30]
quantities = [1, 3, 5]

total_prices = map(lambda p, q: p * q, prices, quantities)
print(list(total_prices))  # [10, 60, 150]
```

---

### `filter` 函数

#### 1. 功能概述

`filter` 函数用于对一个可迭代对象中的元素进行过滤，按照指定函数的条件筛选符合条件的元素，返回一个迭代器。

#### 2. 语法

```python
filter(function, iterable)
```

- `function`：一个用于判断元素是否保留的函数，返回`True`或`False`。
- `iterable`：一个可迭代对象，如列表、元组等。
- 返回值：返回一个迭代器，包含所有`function`返回`True`的元素。

#### 3. 示例

过滤出列表中所有的偶数：

```python
def is_even(x):
    return x % 2 == 0

nums = [1, 2, 3, 4, 5, 6]
even_nums = filter(is_even, nums)
print(list(even_nums))  # [2, 4, 6]
```

也可以用`lambda`表达式：

```python
nums = [1, 2, 3, 4, 5, 6]
even_nums = filter(lambda x: x % 2 == 0, nums)
print(list(even_nums))  # [2, 4, 6]
```

---

### `reduce` 函数

#### 1. 功能概述

`reduce` 函数用于对一个序列进行**累计计算**，它会对序列的前两个元素先进行函数操作，然后将结果与第三个元素再次进行函数操作，以此类推，最后得到一个累计的结果。

#### 2. 位置及导入

`reduce`函数在Python3中不再是内置函数，而在`functools`模块中，需要先导入：

```python
from functools import reduce
```

#### 3. 语法

```python
reduce(function, iterable[, initializer])
```

- `function`：接受两个参数的函数，将用于序列中先前的累计结果和当前元素进行计算。
- `iterable`：可迭代对象。
- `initializer`：可选的初始值，如果提供，计算从初始值开始。

#### 4. 示例

计算一个序列所有元素的积：

```python
from functools import reduce

nums = [1, 2, 3, 4]

product = reduce(lambda x, y: x * y, nums)
print(product)  # 24
```

计算序列的和（其实可以用内置的`sum()`，这里只是示例）：

```python
from functools import reduce

nums = [1, 2, 3, 4, 5]

total = reduce(lambda x, y: x + y, nums)
print(total)  # 15
```

带初始值：

```python
from functools import reduce

nums = [1, 2, 3]

result = reduce(lambda x, y: x + y, nums, 10)
print(result)  # 16 (10 + 1 + 2 + 3)
```

---

### `map`、`filter`、`reduce` 的区别和联系

| 函数名   | 功能描述                                       | 返回值               | 典型用途                               |
| -------- | ---------------------------------------------- | -------------------- | -------------------------------------- |
| `map`    | 对序列中每个元素应用函数，返回功能处理后的序列 | map对象（迭代器）    | 转换数据，如平方、转换大小写等         |
| `filter` | 根据函数过滤序列中的元素，返回满足条件的元素   | filter对象（迭代器） | 筛选数据，如过滤奇数、符合条件的元素   |
| `reduce` | 累计合并序列中的元素，返回单一值               | 单一值               | 计算累计值，如加和、乘积、最大值求值等 |

---

#### 综合示例

现在有一个字符串列表，先把序列中所有字符串长度大于3的转换成大写，再计算这些字符串总长度：

```python
from functools import reduce

words = ["cat", "sheep", "dog", "lion"]

# 过滤长度大于3的
filtered = filter(lambda w: len(w) > 3, words)
# 转换成大写
mapped = map(lambda w: w.upper(), filtered)
# 计算所有字符串长度之和
total_length = reduce(lambda x, y: x + y, map(len, mapped))

print(total_length)  # 输出: 9 ("SHEEP" 和 "LION" 长度 5 + 4)
```

---

### 函数参数详解

Python函数的参数设计灵活且丰富，主要包括：

- 位置参数（Positional Arguments）
- 默认参数（Default Arguments）
- 关键字参数（Keyword Arguments）
- 可变长参数：可变位置参数（*args）和可变关键字参数（**kwargs）
- 强制关键字参数（Python 3特性）
- 参数的组合与调用规则

---

#### 一、位置参数（Positional Arguments）

最基本的参数传递方式，按参数位置传入值。

```python
def greet(name, age):
    print(f"Hello, {name}. You are {age} years old.")

greet("Alice", 30)  # Hello, Alice. You are 30 years old.
```

调用时必须传入与形参数量匹配的实参，否则报错。

---

#### 二、默认参数（Default Arguments）

定义函数时给参数设置默认值，调用时可以不传该参数，函数内部使用默认值。

```python
def greet(name, age=20):
    print(f"Hello, {name}. You are {age} years old.")

greet("Alice")        # Hello, Alice. You are 20 years old.
greet("Bob", 25)      # Hello, Bob. You are 25 years old.
```

**注意事项：**
- 带默认值参数必须放在非默认参数的后面，否则会导致语法错误：

```python
def func(a=1, b):  # 错误！默认参数应放在后面
    pass
```

---

#### 三、关键字参数（Keyword Arguments）

调用函数时，显式指定参数名传值，顺序可以任意，无需按照定义时顺序传入。

```python
def greet(name, age):
    print(f"Hello, {name}. You are {age} years old.")

greet(age=30, name="Alice")  # Hello, Alice. You are 30 years old.
```

结合默认参数使用时，可以只传自己关心的参数。

---

#### 四、可变位置参数（*args）

在参数名前加`*`，表示接受任意数量的位置参数，函数内部将它们封装成一个**元组**。

```python
def sum_all(*args):
    print(args)  # tuple类型
    return sum(args)

print(sum_all(1, 2, 3))  # 输出 6
print(sum_all())         # 输出 0
```

使用场景：参数个数不固定时。

---

#### 五、可变关键字参数（**kwargs）

在参数名前加`**`，表示接受任意数量的关键字参数，函数内部将它们封装成一个**字典**。

```python
def print_info(**kwargs):
    for key, value in kwargs.items():
        print(f"{key} = {value}")

print_info(name="Alice", age=30)
```

输出：

```python
name = Alice
age = 30
```

---

#### 六、函数参数组合示例

很多时候会把各种参数组合在一起定义函数：

```python
def func(a, b=2, *args, c=5, **kwargs):
    print(f"a = {a}")
    print(f"b = {b}")
    print(f"args = {args}")
    print(f"c = {c}")
    print(f"kwargs = {kwargs}")

func(1, 3, 4, 5, c=6, d=7, e=8)
```

输出：

```
a = 1
b = 3
args = (4, 5)
c = 6
kwargs = {'d': 7, 'e': 8}
```

---

#### 七、参数的顺序规则（Python 3）

函数定义时参数顺序必须满足：

```
(位置参数, 默认参数, *args, 强制关键字参数, **kwargs)
```

- **强制关键字参数**：在`*args`后（或仅用`*`表示），未定义默认值的参数必须用关键字传递。

示例：

```python
def func(a, b=2, *args, c, d=4, **kwargs):
    print(a, b, args, c, d, kwargs)

func(1, 3, 4, 5, c=10, d=20, e=30)
```

调用时：

- `a=1`
- `b=3`
- `args=(4,5)`
- `c=10` （强制关键字参数，必须指定）
- `d=20` （默认参数，可指定）
- `kwargs={'e':30}`

---

#### 八、参数的传递方式

Python参数传递机制是“**传对象引用**”，函数内部对参数的修改是否影响外部变量取决于对象是否可变。

常见情况：

```python
def modify_list(lst):
    lst.append(4)

my_list = [1, 2, 3]
modify_list(my_list)
print(my_list)  # [1, 2, 3, 4]
```

可变对象（如列表、字典等）在函数内部修改，外部也感知到变化；不可变对象（如整数、字符串）修改是重新赋值，不影响外部。

---

#### 九、参数解包传参

- **位置解包**：使用星号`*`将可迭代对象拆开放入参数列表。

```python
def add(a, b, c):
    print(a + b + c)

nums = (1, 2, 3)
add(*nums)  # 输出6
```

- **关键字解包**：用双星号`**`解包字典传入关键字参数。

```python
def greet(name, age):
    print(f"Hello {name}, you are {age}")

info = {"name": "Bob", "age": 25}
greet(**info)
```

---

#### 十、示例综合演示

```python
def demo(a, b=2, *args, c=3, **kwargs):
    print(f"a = {a}")
    print(f"b = {b}")
    print(f"args = {args}")
    print(f"c = {c}")
    print(f"kwargs = {kwargs}")

demo(1)
demo(1, 4, 5, 6, c=9, x=10, y=20)
```

输出：

```python
a = 1
b = 2
args = ()
c = 3
kwargs = {}

a = 1
b = 4
args = (5, 6)
c = 9
kwargs = {'x': 10, 'y': 20}
```

---

#### 总结

| 参数类型                   | 作用                               | 传入方式                   | 函数内部类型 | 特点                                    |
| -------------------------- | ---------------------------------- | -------------------------- | ------------ | --------------------------------------- |
| 位置参数（Positional）     | 必传参数                           | 按位置传入                 | 具体类型     | 必须传入，且传入顺序有关                |
| 默认参数（Default）        | 可以省略，省略时使用默认值         | 位置或关键字传入           | 具体类型     | 显示定义默认值，必须放在非默认参数后    |
| 关键字参数（Keyword）      | 用参数名传入                       | 指定参数名传入             | 具体类型     | 传入顺序无关，和默认参数配合灵活调用    |
| 可变位置参数（*args）      | 接受任意数量位置参数               | 以位置参数传入多个值       | 元组         | 内部封装为元组，用于收集多余位置参数    |
| 可变关键字参数（**kwargs） | 接受任意数量关键字参数             | 以关键字参数传入多个键值对 | 字典         | 内部封装为字典，用于收集多余关键字参数  |
| 强制关键字参数（Python3）  | 必须用关键字方式传入，保证调用明确 | 关键字传入                 | 具体类型     | 通过放置于`*`后面实现，防止位置传参错误 |

---

## 内存管理

Python的内存模型比较特殊，它结合了操作系统的内存分配机制和Python自己的内存管理策略。理解Python内存变化，需要从以下几个角度来讲：

---

### 1. Python对象模型与内存分配

#### 1.1 一切皆对象

- Python中所有的数据（整数、字符串、函数、类实例等）本质上都是**对象**。
- 每个对象在内存中至少包含：
  - 对象头（存储类型、引用计数等信息）
  - 实际数据内容（比如整数的值，列表的元素等）

---

#### 1.2 内存地址与引用

- 变量本身**不存储值**，而是**存储指向对象的引用（地址）**。
- 多个变量可以指向同一个对象。

```python
a = [1, 2, 3]
b = a  # b 和 a 指向同一个列表对象
```

---

#### 1.3 内存分配机制

- Python **不直接操作物理内存和操作系统内存**，而是依赖于C语言实现的内存分配器。
- Python有自己的**内存管理器**，从操作系统申请大块内存，再为Python对象划分内存。

---

### 2. Python内存管理的层级结构

- **操作系统层面**：通过`malloc`、`free`等接口请求和释放内存。
- **Python内存分配器**：
  - **PyObject allocator**：专门给Python对象分配内存。
  - **小对象池（obmalloc）**：针对小于512字节的对象，有自己内存池重用机制，减少申请释放开销。
- 当Python对象不再使用时，内存会被释放（或者放回小对象池）。

---

### 3. 内存如何增长和释放

#### 3.1 创建对象时：内存增长

- 当创建新的对象，Python会在内存池或操作系统申请充足空间。
- 对象所占用的内存取决对象类型和内部数据大小，比如：
  - 一个整数只需固定大小空间（多个解释器版本略有差异）
  - 一个列表需要内存存储结构体 + 元素引用的数组（动态扩容）
  
---

#### 3.2 变量变化对内存的影响

- 变量名只是指针，变量赋值时改变指向：

```python
x = [1, 2, 3]
id1 = id(x)
x = [4, 5]
id2 = id(x)
print(id1, id2)  # 不同，重新指向了新对象
```

- 列表等可变对象的内容修改，内存地址不变：

```python
lst = [1, 2]
id1 = id(lst)
lst.append(3)
id2 = id(lst)
print(id1 == id2)  # True，内容变化但对象地址未变
```

---

#### 3.3 删除对象时：内存减少

- Python使用 **引用计数（Reference Counting）** 机制管理内存。
- 当对象的引用计数降至0时，该对象所占内存立即释放。
- 变量赋值、参数传递、数据结构引用都会影响引用计数。

```python
a = [1, 2, 3]
b = a
del a  # 此时对象引用计数仍为1，内存不释放
del b  # 计数为0，内存释放
```

---

#### 3.4 循环引用与垃圾回收（GC）

- **引用计数**有缺陷，不能处理循环引用（对象互相引用导致无法释放）。
- Python引入了**垃圾回收机制（gc模块）**，定期检测循环引用并回收未释放的内存。

---

### 4. 内存变化的具体实例示范

### 示例1：引用计数变化

```python
import sys

a = [1, 2, 3]
print(sys.getrefcount(a))  # 输出计数（+1因为传入getrefcount时参数也引用了对象）

b = a
print(sys.getrefcount(a))  # 增加

del b
print(sys.getrefcount(a))  # 减少
```

---

### 示例2：小整数和大整数内存复用

- Python对**-5到256**之间的整数做了缓存。
- 小整数在多处用同一个对象，节省内存。

```python
a = 100
b = 100
print(id(a) == id(b))  # True

a = 1000
b = 1000
print(id(a) == id(b))  # False，超过缓存范围，创建新对象
```

---

### 5. 内存池机制示意

- **小对象池（obmalloc）**：
  - 用于加速内存管理和减少碎片。
  - 整合多个小对象的内存申请，减少频繁向系统申请。
- **大对象**（>512字节）直接通过操作系统分配。

---

### 6. 内存视角相关工具

- `sys.getsizeof(obj)`：获取对象占用内存字节数
- `gc`模块：控制垃圾回收行为
- 第三方工具：
  - `tracemalloc`：追踪内存分配动态
  - `memory_profiler`：代码内存使用分析
  - `objgraph`：对象引用图，分析内存泄漏

---

### 7. Python内存变化总结图（逻辑）

```python
[创建对象] --> [内存池/操作系统请求内存] --> [内存使用]
      ↑                                       ↓
（变量赋值）←----------------------[引用计数增加/减少]----→
      ↓                                       ↑
[删除变量或引用] → [引用计数为0] → [对象内存释放/垃圾回收]
```

---

### 8. 进一步说明

- Python开发者无需直接管理内存，使用对象即可。
- 了解内存管理有助于编写**高效、内存友好**的代码，防止内存泄漏，尤其在长时间运行或大数据场景下。
- 内存优化常用技巧：
  - 避免不必要的对象复制
  - 使用生成器代替列表保存
  - 减少循环引用
  - 手动触发`gc.collect()`清理

---

### 总结

| 方面         | 说明                                         |
| ------------ | -------------------------------------------- |
| 对象模型     | 变量是引用，对象存数据，Python万物皆对象     |
| 内存分配     | 由Python内存分配器和操作系统共同完成         |
| 引用计数     | 主要的内存管理策略，0引用即释放              |
| 循环引用     | 通过垃圾回收器自动检测并回收                 |
| 内存池       | 小对象池机制减少内存碎片，提高分配效率       |
| 内存监控工具 | `sys.getsizeof()`, `gc`模块, `tracemalloc`等 |

---

如果你需要，我可以帮你讲解更具体的内存泄漏排查、内存优化案例，或者实战中内存监控的使用方法。欢迎告诉我！

## import

`import`语句是Python用来导入模块和包的关键机制。通过`import`，你可以调用其他Python文件中的函数、类、变量，实现**代码复用和模块化**。

---

### 一、基础：什么是模块和包？

- **模块（module）**：一个以`.py`结尾的Python文件，包含变量、函数、类等。
- **包（package）**：包含`__init__.py`文件的文件夹，可以包含多个模块和子包。

---

### 二、import语法及使用

#### 1. 导入整个模块

```python
import module_name
```

使用时需要加模块名前缀：

```python
import math
print(math.sqrt(16))  # 4.0
```

---

#### 2. 导入模块中的指定成员

```python
from module_name import name1, name2, ...
```

示例：

```python
from math import sqrt, pi
print(sqrt(25))  # 5.0
print(pi)        # 3.141592653589793
```

---

#### 3. 导入模块所有成员（不推荐）

```python
from module_name import *
```

- 会将模块中除了以`_`开头的所有公开成员导入到当前命名空间。
- 容易导致命名冲突，不推荐使用。

---

#### 4. 模块起别名

为模块或成员起别名，简化名称或避免冲突。

```python
import module_name as alias
from module_name import name as alias
```

示例：

```python
import numpy as np
from math import sqrt as square_root

print(np.array([1, 2, 3]))
print(square_root(9))
```

---

### 三、import的工作机制

1. **查找模块**

Python在执行`import`时，会根据以下顺序查找模块：

- 当前执行脚本所在目录
- 环境变量`PYTHONPATH`中的目录
- Python标准库目录
- 已安装第三方包目录

所有这些目录组合成一个模块搜索路径列表，在Python中通过`sys.path`查看：

```python
import sys
print(sys.path)
```

---

2. **加载模块**

- 如果模块已经加载过，则直接使用已加载模块，不重复加载。
- 否则会将模块文件字节码编译成`.pyc`文件（存于`__pycache__`目录），然后加载。

---

3. **模块缓存**

- 系统中已加载的模块都会被缓存到`sys.modules`字典中。
- 重复导入同一个模块时，直接从缓存中获取，提高效率。

---

### 四、包的导入

- 使用包时使用点号`.`表示多层目录。

```python
import package.subpackage.module
from package.subpackage import module
```

- `__init__.py`文件用于标识该目录是包，可以为空或者定义包的初始化代码。

---

### 五、其他import相关用法

#### 1. 动态导入（`importlib`模块）

```python
import importlib

mod = importlib.import_module('math')
print(mod.sqrt(16))  # 4.0
```

#### 2. 延迟导入

把`import`语句放在函数内部等位置，避免程序启动时加载，提升启动速度。

---

#### 3. reload模块

Python3中，用于重新加载已加载模块。

```python
import importlib
importlib.reload(module_name)
```

---

### 六、常见使用误区和注意点

- 循环导入（互相导入的两个模块）可能导致导入失败，需调整设计。
- 使用`from module import *`容易污染命名空间。
- 用别名时避免与内置函数或变量重名。
- 包目录必须有`__init__.py`（Python 3.3以后有命名空间包可以无此文件，但习惯保留）。

---

### 七、示例综合演示

```python
# math_demo.py
import math
from math import sin, cos as cosine

print(math.pi)
print(sin(math.pi / 2))
print(cosine(0))
```

运行：

```
3.141592653589793
1.0
1.0
```

---

### 八、总结

| 用法                               | 说明                              | 示例                               |
| ---------------------------------- | --------------------------------- | ---------------------------------- |
| `import module`                    | 导入整个模块，访问用`module.name` | `import math`，`math.sqrt(4)`      |
| `from module import name`          | 导入模块指定成员，直接使用`name`  | `from math import sqrt`，`sqrt(4)` |
| `from module import *`             | 导入模块所有公开成员（不推荐）    | `from math import *`               |
| `import module as alias`           | 导入模块并起别名                  | `import numpy as np`               |
| `from module import name as alias` | 导入成员并起别名                  | `from math import sqrt as sqr`     |
| 动态导入                           | 运行时按字符串导入模块            | `importlib.import_module('math')`  |
| 包导入                             | 使用点号访问子模块                | `import package.subpackage.module` |

---



好的！下面是对 Python 中 `dir()` 和 `help()` 两个内置函数的详细介绍。

---

##  `dir()` 和 `help()` 函数详解

---

### 1. `dir()` 函数

#### 1.1 作用

`dir()` 用来返回一个对象的属性和方法列表。它能够告诉你某个对象“有什么内容”（有哪些成员），在探索新模块或类时非常有用。

#### 1.2 语法

```python
dir([object])
```

- 如果不给参数，返回当前范围内的变量、方法和定义的类型列表。
- 如果传入一个对象参数，则返回该对象的大部分有效属性名的字符串列表（包括方法）。

#### 1.3 使用示例

```python
print(dir())  # 显示当前作用域内的名称列表

import math
print(dir(math))  # 查看 math 模块中包含哪些属性和方法

s = "hello"
print(dir(s))  # 查看字符串对象的方法列表
```

#### 1.4 输出示例

```python
>>> dir("hello")
['__add__', '__class__', '__contains__', 'capitalize', 'casefold', 'center', 'count', 'encode', 'endswith', 'expandtabs', 'find', 'format', ...]
```

---

### 2. `help()` 函数

#### 2.1 作用

`help()` 函数用于查看对象、模块、函数等的帮助文档，是交互式获取Python内置帮助信息的工具，相当于快速查看官方文档。

#### 2.2 语法

```python
help([object])
```

- 如果不给参数，进入交互式帮助模式；
- 如果传入一个对象参数，会显示该对象的文档字符串、函数说明、模块介绍等详细信息。

#### 2.3 使用示例

```python
help(len)  # 查看内置函数 len 的文档

import math
help(math.sqrt)  # 查看 math 模块中 sqrt 函数的帮助信息

help(str)  # 查看字符串类的帮助文档
```

#### 2.4 交互式模式

```python
help()
# 进入后可以输入模块名、关键字或主题进行查询，输入 'quit' 退出
```

---

### 3. 总结区别和联系

| 函数     | 功能                             | 使用场景                                     |
| -------- | -------------------------------- | -------------------------------------------- |
| `dir()`  | 显示一个对象的属性和方法名称列表 | 探索某个变量、模块或对象有什么成员           |
| `help()` | 显示对象的详细帮助文档           | 查询具体函数、模块、类的用法说明和文档字符串 |

---

### 4. 常见配合使用案例

通过 `dir()` 先看某个模块或实例有哪些方法，再用 `help()` 查看具体用法：

```python
import datetime

print(dir(datetime))
help(datetime.date)
```

---

 

当然可以！下面是对 Python 中 `datetime` 模块的详细介绍。

---

##  `datetime` 模块详解

---

### 1. 模块概述

`datetime` 是 Python 标准库中专门处理日期和时间的模块。它提供了灵活且功能丰富的类型和方法，用于创建、操作、格式化和计算日期与时间。

---

### 2. 模块中主要类和功能

#### 2.1 `date` 类

表示“日期”，包含年、月、日，不含时间。

- **构造方法**：

```python
datetime.date(year, month, day)
```

- **常用属性**：

  - `year`、`month`、`day`

- **示例**：

```python
import datetime

d = datetime.date(2024, 6, 10)
print(d)            # 2024-06-10
print(d.year)       # 2024
print(d.strftime("%Y/%m/%d"))  # 2024/06/10 格式化输出
```

---

#### 2.2 `time` 类

表示一天中的时间（时分秒微秒），不含日期。

- **构造方法**：

```python
datetime.time(hour=0, minute=0, second=0, microsecond=0)
```

- **属性**：`hour`, `minute`, `second`, `microsecond`

```python
t = datetime.time(13, 30, 45)
print(t)  # 13:30:45
```

---

#### 2.3 `datetime` 类

表示日期和时间的组合（年、月、日、时、分、秒、微秒）。

- **构造方法**：

```python
datetime.datetime(year, month, day, hour=0, minute=0, second=0, microsecond=0)
```

- **示例**：

```python
dt = datetime.datetime(2024,6,10,14,20,30)
print(dt)  # 2024-06-10 14:20:30
```

- **常用方法**：

  - `.now()`：获取当前本地时间
  - `.utcnow()`：获取当前UTC时间
  - `.strftime(format)`：格式化输出字符串
  - `.strptime(string, format)`：从字符串解析时间

```python
print(datetime.datetime.now())
print(datetime.datetime.utcnow())
print(dt.strftime("%Y-%m-%d %H:%M:%S"))
parsed = datetime.datetime.strptime("2024-06-10 14:20:30", "%Y-%m-%d %H:%M:%S")
print(parsed)
```

---

#### 2.4 `timedelta` 类

表示两个时间之间的差值，支持加减运算，非常适合日期时间运算。

- **构造方法**：

```python
timedelta(days=0, seconds=0, microseconds=0,
          milliseconds=0, minutes=0, hours=0, weeks=0)
```

- **示例**：

```python
from datetime import datetime, timedelta

now = datetime.now()
delta = timedelta(days=5, hours=3)
future = now + delta
print(future)  # 当前时间5天3小时后的时间
```

---

#### 2.5 其他相关类

- `tzinfo`：用于时区信息抽象；
- `timezone`：实现了固定时区（偏移量）功能，Python3 支持。

---

### 3. 常用操作示例

#### 3.1 获取当前时间

```python
from datetime import datetime

print(datetime.now())     # 本地当前时间
print(datetime.utcnow())  # UTC时间
```

#### 3.2 格式化日期时间

```python
dt = datetime.now()
print(dt.strftime("%Y-%m-%d %H:%M:%S"))  # 2024-06-10 15:30:45
```

#### 3.3 将字符串转换成日期时间对象

```python
date_str = "2024-06-10 15:30:45"
dt = datetime.strptime(date_str, "%Y-%m-%d %H:%M:%S")
print(dt)
```

#### 3.4 日期时间加减

```python
from datetime import timedelta

now = datetime.now()
yesterday = now - timedelta(days=1)
print(yesterday)
```

#### 3.5 计算时间差

```python
start = datetime(2024, 6, 1)
end = datetime(2024, 6, 10)
diff = end - start
print(diff.days)  # 9 天
```

---

### 4. 常见格式化符号

| 格式符号 | 说明         | 示例   |
| -------- | ------------ | ------ |
| `%Y`     | 四位年份     | 2024   |
| `%m`     | 两位月份     | 06     |
| `%d`     | 两位日期     | 10     |
| `%H`     | 24小时制小时 | 14     |
| `%I`     | 12小时制小时 | 02     |
| `%M`     | 分钟         | 30     |
| `%S`     | 秒           | 45     |
| `%f`     | 微秒         | 000001 |
| `%p`     | AM或PM       | AM     |

---

### 5. 小结

- `datetime` 模块为日期时间处理提供了强大且丰富的类和方法。
- 支持日期、时间、日期时间、时间差等类型。
- 可方便进行时间的格式化、解析、计算。
- 是Python开发中处理时间问题的首选模块，使用广泛。

---

当然可以！下面我给你详细介绍一下 Python 中时间的加减法操作，主要使用 `datetime` 模块及其 `timedelta` 类。

---

### 时间的加减法

---

#### 1. 概述

Python 中处理时间加减操作，最常用的是利用 `datetime` 模块里的 `datetime`（日期时间）和 `timedelta`（时间差）这两个类。

- `datetime` 表示某个具体的时间点。
- `timedelta` 表示两个时间点之间的时间差，用于加减时间。

---

#### 2. timedelta 代表时间间隔

`timedelta` 对象可以用来表示以下时间段：

- 天数（days）
- 秒数（seconds）
- 微秒数（microseconds）
- 毫秒数（milliseconds）
- 分钟（minutes）
- 小时（hours）
- 星期（weeks）

---

#### 3. 时间加减法语法

```python
from datetime import datetime, timedelta

dt = datetime(year, month, day, hour, minute, second)

# 时间加
new_dt = dt + timedelta(days=1, hours=2, minutes=30)

# 时间减
new_dt2 = dt - timedelta(days=3, minutes=15)
```

---

#### 4. 具体示例

##### 4.1 当前时间加减

```python
from datetime import datetime, timedelta

now = datetime.now()
print(f"当前时间: {now}")

# 当前时间加一天
tomorrow = now + timedelta(days=1)
print(f"明天此时: {tomorrow}")

# 当前时间减两小时三十分钟
earlier = now - timedelta(hours=2, minutes=30)
print(f"两小时三十分钟前: {earlier}")
```

##### 4.2 计算两个时间的差值

```python
from datetime import datetime

start = datetime(2024, 6, 10, 8, 0, 0)
end = datetime(2024, 6, 12, 12, 30, 0)

diff = end - start
print(f"时间差: {diff}")          # 2 days, 4:30:00

print(f"总秒数: {diff.total_seconds()}")  # 189000.0 秒
```

---

#### 5. timedelta 常用字段和方法

- `days`：天数
- `seconds`：秒数（不包含天数部分）
- `microseconds`：微秒
- `total_seconds()`：返回时间差的总秒数（包括天数转换成的秒）

---

#### 6. 注意事项

- `timedelta` 只支持时间间隔，不能表示绝对时间点。
- 时间加减会自动考虑日期和时间的进位，比如加一天会自动增加日期。
- 如果涉及时区（`tzinfo`），计算时需留意时区偏移。

---

#### 7. 小结

| 操作     | 方法示例                          | 说明                           |
| -------- | --------------------------------- | ------------------------------ |
| 时间加法 | `dt + timedelta(days=3, hours=5)` | 在指定时间基础上加指定时间间隔 |
| 时间减法 | `dt - timedelta(minutes=30)`      | 在指定时间基础上减指定时间间隔 |
| 计算差值 | `dt2 - dt1`                       | 计算两个时间点的时间差         |
| 获取秒数 | `diff.total_seconds()`            | 获取时间差以秒为单位的总时长   |

---

### 时间戳（Timestamp）

---

#### 1. 什么是时间戳？

时间戳指的是从某一特定时间（称为“纪元时间”或“Unix Epoch”）开始，到某个时刻经过的总秒数或毫秒数。

- **Unix 时间戳**一般是指自 **1970年1月1日00:00:00 UTC** 起经过的秒数。
- 时间戳是一个浮点数或整数，表示某一时刻，通常用于时间的存储和计算。
- 计算机系统广泛使用时间戳进行时间记录、比较和转换。

---

#### 2. 为什么使用时间戳？

- 方便存储和比较时间（用数字比较大小很简单）
- 避免了时区、夏令时带来的复杂性（时间戳是统一的全球时间）
- 适合用于网络传输、数据库存储、文件标记等

---

#### 3. Python 中的时间戳

##### 3.1 获取当前时间的时间戳

```python
import time

ts = time.time()
print(ts)  # 例如：1686387309.123456，浮点数，单位是秒
```

- `time.time()` 返回当前时间的时间戳，单位是秒，是1970年1月1日以来经过的秒数。

##### 3.2 时间戳转换为日期时间对象

```python
import datetime

ts = 1686387309.123456
dt = datetime.datetime.fromtimestamp(ts)
print(dt)  # 输出本地时间，例如：2024-06-10 15:15:09.123456
```

##### 3.3 日期时间对象转换为时间戳

```python
import datetime

dt = datetime.datetime(2024, 6, 10, 15, 15, 9)
ts = dt.timestamp()
print(ts)  # 返回时间戳，浮点数秒数
```

---

#### 4. 时间戳的单位

- **秒单位**：常见于Unix/Linux系统、Python的`time.time()`和`datetime.timestamp()`。
- **毫秒单位**：某些系统或接口使用毫秒为单位，比如JavaScript `Date.now()`返回的是毫秒。
- 注意转换时应做好单位换算。

---

#### 5. 时间戳的优势和限制

##### 优势

- 简单直接，适合计算时间差、排序
- 与时区无关（UTC统一时间）
- 适合做时间的序列化传输

##### 限制

- 可读性差，需要转换成日期时间格式才能理解
- 受到存储长度限制，32位时间戳存在2038年问题（称为“2038年问题”）

---

#### 6. 2038年问题

- 32位系统的时间戳用32位有符号整数表示秒数，最大值约为2147483647秒。
- 该最大值对应的时间是 **2038年1月19日**，之后时间戳会溢出，导致异常。
- 64位系统和现代语言多数已默认使用64位时间戳，解决该问题。

---

#### 7. 小结

| 概念     | 说明                                                         |
| -------- | ------------------------------------------------------------ |
| 时间戳   | 自Unix纪元起经过的秒数，表示某一时刻                         |
| 获取方法 | Python用`time.time()`，返回浮点秒数                          |
| 转换     | `datetime.fromtimestamp()` 将时间戳转为时间对象，`datetime.timestamp()`反向转换 |
| 优势     | 便于计算和存储，统一标准，不受时区影响                       |
| 注意     | 单位（秒/毫秒）区别；32位时间戳会有2038年问题                |

---

##  `calendar` 模块详解

---

### 1. 模块简介

`calendar`模块提供了与日历相关的类和函数，便于在Python中处理和生成各种日历数据。它支持：

- 生成文本格式或HTML格式的日期表格
- 计算某年某月的日历信息
- 判断闰年、每月天数、周几等日期属性
- 支持不同的星期起始日（如周一或周日）

---

### 2. 主要功能和常用类

#### 2.1 基本函数

- `calendar.isleap(year)`  
  判断传入的年份是否是闰年，返回布尔值。

- `calendar.leapdays(y1, y2)`  
  返回从年份`y1`到`y2`（不包括`y2`）之间的闰年数量。

- `calendar.monthrange(year, month)`  
  返回元组 `(weekday, num_days)`，表示指定年月的第一天是星期几（0-6，0表示周一），以及该月总天数。

- `calendar.weekday(year, month, day)`  
  返回指定日期是星期几（0-6，0表示星期一）。

---

#### 2.2 生成日历信息

- `calendar.month(year, month, w=0, l=0)`  
  返回指定年月的日历字符串（文本格式）。

- `calendar.prmonth(year, month, w=0, l=0)`  
  直接打印指定年月的月历。

- `calendar.calendar(year, w=2, l=1, c=6, m=3)`  
  返回指定年份的整年日历字符串。

---

#### 2.3 `Calendar` 类

`Calendar` 类可以更灵活地迭代日历数据。

- `calendar.Calendar(firstweekday=0)`  
  创建一个日历类实例，`firstweekday`指定周的第一天（0是周一，6是周日）。

- 常用方法（返回迭代器）：

  - `.itermonthdays(year, month)`  
    生成该月每天的日期，非本月天数用0表示。

  - `.itermonthdates(year, month)`  
    生成该月包含的日期，包含前后月份的日期，类型是`datetime.date`。

  - `.monthdatescalendar(year, month)`  
    返回一个嵌套列表，列表中每个子列表是一周的日期列表。

---

#### 2.4 其他实用函数

- `calendar.monthcalendar(year, month)`  
  返回一个月的日历矩阵，每周为一个列表，值为天数，非本月天数为0。

---

### 3. 示例代码

#### 3.1 判断闰年

```python
import calendar

print(calendar.isleap(2024))  # True
print(calendar.isleap(2023))  # False
```

#### 3.2 获取某月的星期和天数

```python
first_weekday, days = calendar.monthrange(2024, 6)
print(first_weekday)  # 5 表示周六（0周一）
print(days)           # 30 天
```

#### 3.3 打印某月的日历

```python
print(calendar.month(2024, 6))
```

输出：

```
     June 2024
Mo Tu We Th Fr Sa Su
                1  2
 3  4  5  6  7  8  9
10 11 12 13 14 15 16
17 18 19 20 21 22 23
24 25 26 27 28 29 30
```

#### 3.4 使用 `Calendar` 类遍历日期

```python
from calendar import Calendar

cal = Calendar(firstweekday=6)  # 设置周日为每周第一天
for day in cal.itermonthdays(2024, 6):
    print(day, end=" ")
# 输出会包含0（表示当月外日期）
```

#### 3.5 获取某月日历矩阵

```python
matrix = calendar.monthcalendar(2024, 6)
for week in matrix:
    print(week)
# 如 [0, 0, 0, 0, 0, 1, 2]
```

---

### 4. 常用参数说明

- **firstweekday** 参数决定一周从周几开始：
  - 0 = Monday (默认)
  - 6 = Sunday

- **w（width）** 和 **l（lines）**：
  - `w` 控制每个日期的宽度，默认为0；
  - `l` 控制每周的行数，默认为0。

---

### 5. 总结

| 功能           | 函数或类                     | 说明                               |
| -------------- | ---------------------------- | ---------------------------------- |
| 判断闰年       | `isleap(year)`               | 返回bool                           |
| 统计闰年数量   | `leapdays(y1, y2)`           | y1 ≤ year < y2间闰年个数           |
| 获取月份信息   | `monthrange(year, month)`    | 返回该月第一天周几和天数           |
| 获取星期几     | `weekday(year, month, day)`  | 返回星期几（0-6）                  |
| 输出月历文本   | `month(year, month)`         | 返回字符串                         |
| 打印月历       | `prmonth(year, month)`       | 直接打印月历                       |
| 获取月日历矩阵 | `monthcalendar(year, month)` | 返回嵌套列表表示月份按周划分的天数 |
| 可迭代日历     | `Calendar` 类及其方法        | 灵活遍历日历数据                   |

---

当然可以！下面是Python标准库中`time`模块的详细介绍。

---

## `time` 模块详解

---

### 1. 模块简介

`time`模块提供了对时间相关的函数支持，包含获取当前时间、暂停程序执行、处理时间戳、格式化时间等功能。它主要基于操作系统的时间接口，是Python标准库处理时间的基础模块之一。

---

### 2. 主要功能

#### 2.1 时间获取

- `time.time()`  
  返回当前时间的时间戳（自1970年1月1日UTC起的秒数），浮点数类型。

- `time.localtime([secs])`  
  把时间戳转换为本地时间的时间元组（`time.struct_time`），不传参即获取当前时间。

- `time.gmtime([secs])`  
  把时间戳转换为UTC时间的时间元组。

- `time.ctime([secs])`  
  把时间戳转换为可读字符串形式的本地时间，如 `'Mon Jun 10 15:30:00 2024'`。

---

#### 2.2 时间格式化与解析

- `time.strftime(format[, t])`  
  将时间元组或当前时间按指定格式转换为字符串。

- `time.strptime(string[, format])`  
  将字符串按指定格式解析成时间元组。

---

#### 2.3 程序休眠

- `time.sleep(secs)`  
  让程序挂起指定秒数（浮点数），常用于延时操作。

---

#### 2.4 计时器和性能测量（Python3）

- `time.perf_counter()`  
  返回一个高精度计时器，适合测量短时间间隔（包含睡眠时间）。

- `time.process_time()`  
  返回进程执行时间，不包含睡眠时间。

---

### 3. 常用数据结构

- `time.struct_time`  
  是一个类似元组的对象，包含9个元素：

  | 属性     | 说明                   |
  | -------- | ---------------------- |
  | tm_year  | 年（如2024）           |
  | tm_mon   | 月（1-12）             |
  | tm_mday  | 日（1-31）             |
  | tm_hour  | 时（0-23）             |
  | tm_min   | 分（0-59）             |
  | tm_sec   | 秒（0-61，包含闰秒）   |
  | tm_wday  | 星期（0周一 - 6周日）  |
  | tm_yday  | 一年中的天数（1-366）  |
  | tm_isdst | 夏令时标志（0或1或-1） |

---

### 4. 主要函数用法示例

#### 4.1 当前时间戳和时间元组

```python
import time

ts = time.time()
print(f"时间戳: {ts}")

local = time.localtime(ts)
print(f"本地时间: {local}")
print(f"年: {local.tm_year}, 月: {local.tm_mon}, 日: {local.tm_mday}")
```

#### 4.2 格式化时间

```python
formatted = time.strftime("%Y-%m-%d %H:%M:%S", time.localtime())
print(f"格式化当前时间: {formatted}")
```

#### 4.3 解析字符串为时间

```python
time_str = "2024-06-10 15:30:00"
parsed = time.strptime(time_str, "%Y-%m-%d %H:%M:%S")
print(f"解析后的时间元组: {parsed}")
```

#### 4.4 程序休眠

```python
print("开始计时")
time.sleep(2)  # 程序暂停2秒
print("2秒后继续")
```

#### 4.5 计时器示例

```python
start = time.perf_counter()
# 模拟耗时操作
time.sleep(1.5)
end = time.perf_counter()
print(f"操作时间: {end - start}秒")
```

---

### 5. 常见时间格式化符号

| 格式符号 | 说明           | 示例   |
| -------- | -------------- | ------ |
| `%Y`     | 四位数年份     | 2024   |
| `%m`     | 月份 (01-12)   | 06     |
| `%d`     | 日 (01-31)     | 10     |
| `%H`     | 24小时 (00-23) | 15     |
| `%M`     | 分钟 (00-59)   | 30     |
| `%S`     | 秒 (00-59)     | 00     |
| `%a`     | 周几缩写       | Mon    |
| `%A`     | 周几全称       | Monday |
| `%b`     | 月份缩写       | Jun    |
| `%B`     | 月份全称       | June   |

---

### 6. 其他说明

- 时间戳和`datetime`模块的时间对象可以相互转换，`time`模块主要更底层，`datetime`模块功能更丰富。
- 不同操作系统对一些函数的支持可能有细微差别，如闰秒处理等。

---

### 7. 小结

`time`模块是Python中进行时间管理的基础模块，提供了：

- 时间戳获取与转换
- 时间结构体（`struct_time`）
- 时间格式化与解析
- 程序延时和计时

掌握它能帮助你进行时间相关的绝大多数系统级别操作。

---

## 几个算数模块

好的，下面我将具体介绍Python中几个常用计算模块的主要函数及其作用，方便你理解和使用。

---

### 1. math模块

`math`模块包含了很多基础数学函数，适合处理实数的数学计算。

| 函数                              | 说明                                 | 示例                                |
| --------------------------------- | ------------------------------------ | ----------------------------------- |
| `math.sqrt(x)`                    | 计算平方根                           | `math.sqrt(4)  # 2.0`               |
| `math.factorial(x)`               | 阶乘，x应为非负整数                  | `math.factorial(5)  # 120`          |
| `math.pow(x, y)`                  | 幂运算，x的y次方                     | `math.pow(2, 3)  # 8.0`             |
| `math.exp(x)`                     | 计算e的x次方                         | `math.exp(1)  # 2.718281828...`     |
| `math.log(x[, base])`             | 对数，如果不指定base，默认是自然对数 | `math.log(8, 2)  # 3.0`             |
| `math.sin(x)`, `cos(x)`, `tan(x)` | 三角函数，x为弧度                    | `math.sin(math.pi/2)  # 1.0`        |
| `math.degrees(x)`                 | 弧度转角度                           | `math.degrees(math.pi)  # 180.0`    |
| `math.radians(x)`                 | 角度转弧度                           | `math.radians(180)  # 3.1415926535` |
| `math.ceil(x)`                    | 向上取整                             | `math.ceil(4.2)  # 5`               |
| `math.floor(x)`                   | 向下取整                             | `math.floor(4.8)  # 4`              |
| `math.fabs(x)`                    | 计算绝对值                           | `math.fabs(-5)  # 5.0`              |
| `math.gcd(a, b)`                  | 计算最大公约数                       | `math.gcd(12, 18)  # 6`             |

---

### 2. cmath模块

专门用于复数运算，函数与math模块类似，但参数和返回值支持复数。

| 函数                               | 说明                           | 示例                                       |
| ---------------------------------- | ------------------------------ | ------------------------------------------ |
| `cmath.sqrt(x)`                    | 复数平方根                     | `cmath.sqrt(-1)  # 1j`                     |
| `cmath.exp(x)`                     | e的x次方                       | `cmath.exp(1+1j)`                          |
| `cmath.log(x[, base])`             | 复数对数                       | `cmath.log(1+1j)`                          |
| `cmath.sin(x)`, `cos(x)`, `tan(x)` | 复数三角函数                   | `cmath.sin(1+1j)`                          |
| `cmath.phase(x)`                   | 计算复数的相位角（弧度）       | `cmath.phase(1+1j)  # 0.785398...`         |
| `cmath.polar(x)`                   | 返回复数的极坐标（幅度, 相位） | `cmath.polar(1+1j)  # (1.414, 0.785)`      |
| `cmath.rect(r, phi)`               | 极坐标转矩形坐标               | `cmath.rect(1, math.pi/4)  # 0.707+0.707j` |

---

### 3. decimal模块

`decimal`用于高精度十进制数运算，避免浮点数计算误差。

主要类及方法：

| 类 / 方法        | 说明                             | 示例                                                 |
| ---------------- | -------------------------------- | ---------------------------------------------------- |
| `Decimal(value)` | 创建一个高精度十进制数           | `Decimal('0.1')`                                     |
| `.quantize(exp)` | 将Decimal四舍五入到指定精度      | `Decimal('2.345').quantize(Decimal('0.01'))  # 2.35` |
| `.sqrt()`        | 计算平方根                       | `Decimal('4').sqrt()  # Decimal('2')`                |
| 上下文控制       | 使用`getcontext()`设置精度等属性 | `getcontext().prec = 28`                             |

示例：

```python
from decimal import Decimal, getcontext
getcontext().prec = 10  # 设置精度
a = Decimal('0.1')
b = Decimal('0.2')
print(a + b)  # 输出：0.3
```

---

### 4. fractions模块

处理分数，能够表示精确的分数计算，避免浮点误差。

主要类及方法：

| 类 / 方法                                    | 说明                | 示例                                        |
| -------------------------------------------- | ------------------- | ------------------------------------------- |
| `Fraction(numerator, denominator)`           | 创建分数            | `Fraction(1, 3)`                            |
| 支持算术运算                                 | 支持 + - * / 等运算 | `Fraction(1,3) + Fraction(1,6)  # 1/2`      |
| `limit_denominator(max_denominator=1000000)` | 限制分母最大值      | `Fraction(3.14159).limit_denominator(1000)` |

示例：

```python
from fractions import Fraction
f1 = Fraction(1, 3)
f2 = Fraction(1, 6)
print(f1 + f2)  # 输出：1/2
```

---

### 5. random模块

生成伪随机数。

主要方法：

| 函数                           | 说明                              | 示例                           |
| ------------------------------ | --------------------------------- | ------------------------------ |
| `random.random()`              | 返回[0.0, 1.0)之间的随机浮点数    | `random.random()`              |
| `random.randint(a, b)`         | 返回[a, b]之间的随机整数          | `random.randint(1, 10)`        |
| `random.uniform(a, b)`         | 返回[a, b)之间的随机浮点数        | `random.uniform(1.0, 2.0)`     |
| `random.choice(seq)`           | 从序列seq中随机返回一个元素       | `random.choice(['a','b','c'])` |
| `random.shuffle(seq)`          | 将序列seq中的元素随机排列         | `random.shuffle(mylist)`       |
| `random.sample(population, k)` | 从总体中随机选出k个元素（无重复） | `random.sample(range(100), 5)` |

---

### 6. statistics模块

用于统计量的计算。

主要函数：

| 函数             | 功能                         | 示例                                  |
| ---------------- | ---------------------------- | ------------------------------------- |
| `mean(data)`     | 计算算术平均值               | `statistics.mean([1,2,3])  # 2`       |
| `median(data)`   | 中位数                       | `statistics.median([1,2,3,4])  # 2.5` |
| `mode(data)`     | 众数，序列中出现频率最高的值 | `statistics.mode([1,1,2,3])  # 1`     |
| `stdev(data)`    | 样本标准差                   | `statistics.stdev([1,2,3,4,5])`       |
| `variance(data)` | 方差                         | `statistics.variance([1,2,3,4,5])`    |

---

### 7. numpy库（第三方）

numpy是Python科学计算的核心库，强大的多维数组处理能力和丰富的数学函数。

常用函数示例如下：

| 函数                            | 功能                       | 示例                                                    |
| ------------------------------- | -------------------------- | ------------------------------------------------------- |
| `np.array(object)`              | 创建数组                   | `np.array([1,2,3])`                                     |
| `np.sum(arr)`                   | 数组元素求和               | `np.sum([1,2,3])  # 6`                                  |
| `np.mean(arr)`                  | 计算均值                   | `np.mean([1,2,3])  # 2.0`                               |
| `np.median(arr)`                | 中位数                     | `np.median([1,3,2])  # 2.0`                             |
| `np.std(arr)`                   | 标准差                     | `np.std([1,2,3])`                                       |
| `np.dot(a, b)`                  | 矩阵点乘                   | `np.dot([1, 2], [3, 4])  # 11`                          |
| `np.linalg.inv(a)`              | 矩阵求逆                   | `np.linalg.inv(np.array([[1,2],[3,4]]))`                |
| `np.linspace(start, stop, num)` | 生成指定数量的均匀间隔数值 | `np.linspace(0,1,5)`  # array([0, 0.25, 0.5, 0.75, 1])` |

---

### 8. scipy库（第三方）

scipy基于numpy，提供更多科学计算模块：

- `scipy.optimize`：优化算法
- `scipy.integrate`：积分计算
- `scipy.interpolate`：插值
- `scipy.linalg`：线性代数扩展
- `scipy.fft`：傅里叶变换

示例：求函数的积分

```python
from scipy.integrate import quad
result, error = quad(lambda x: x**2, 0, 1)
print(result)  # 0.3333...
```

---

好的！下面我来详细介绍一下Python标准库中的`shelve`模块。

---

## shelve模块

`shelve`模块提供了一个简单的对象持久化功能，它实现了一个类似字典的接口，可以将Python对象（只要是**可pickle对象**）存储到一个文件中，从而实现数据的持久化保存和读取。

简单来说，`shelve`就是用一个文件当“数据库”，你可以像操作字典一样操作这个文件，把Python对象以键值对形式保存起来。

---

### shelve的应用场景

- 需要持久化保存Python对象，方便下次程序运行时加载这些数据。
- 不想用关系型数据库或者安装第三方数据库时，`shelve`是快速存储少量数据的轻量级方案。
- 实现配置存储、缓存、简单数据备份等。

---

### shelve模块的基本用法

```python
import shelve

# 打开一个shelve文件，文件名就是数据库名
with shelve.open('mydata.db') as db:
    # 写入数据
    db['name'] = 'Alice'
    db['age'] = 30
    db['scores'] = [95, 88, 92]

# 读取数据
with shelve.open('mydata.db') as db:
    print(db['name'])    # Alice
    print(db.get('age')) # 30

    # 遍历所有键值
    for key in db:
        print(key, db[key])
```

---

### shelve模块主要特点

- **数据以键值对存储**，键必须是字符串（从Python 3.4开始，键也可以是其他类型，但一般推荐用字符串），值可以是任意Python对象（只要能pickle）。
- 底层实现依赖于`dbm`等数据库模块（平台相关），底层用的是二进制文件。
- 每次修改后会自动写回文件。
- 适合存储简单的数据，不适合复杂并发访问需求。

---

### shelve模块常用函数和方法

`shelve.open(filename, flag='c', protocol=None, writeback=False)`

| 参数        | 说明                                                         |
| ----------- | ------------------------------------------------------------ |
| `filename`  | 文件名（存储数据库的路径，无需扩展名，底层会自动加后缀）     |
| `flag`      | 文件打开模式：'r'(只读)，'w'(读写需存在文件)，'c'(读写，文件不存在则创建，默认)，'n'(新建，覆盖原文件) |
| `protocol`  | 指定pickle的协议版本，默认使用最高协议                       |
| `writeback` | 是否启用写回缓存，默认False。若为True，改动缓存后才能写回到文件，性能低但方便复杂对象修改 |

---

打开后返回一个类似字典的对象（`Shelf`对象），常用方法：

| 方法              | 说明                               |
| ----------------- | ---------------------------------- |
| `db[key] = value` | 设置键值                           |
| `value = db[key]` | 获取对应键的值                     |
| `key in db`       | 判断键是否存在                     |
| `del db[key]`     | 删除键及对应数据                   |
| `db.keys()`       | 返回所有键的列表                   |
| `db.values()`     | 返回所有值的列表                   |
| `db.items()`      | 返回所有键值对的列表               |
| `db.close()`      | 关闭shelve数据库，确保数据写入磁盘 |

### writeback参数说明

- 默认为`False`，变更对象需重新赋值才能写回。

```python
import shelve

with shelve.open('mydata.db') as db:
    db['numbers'] = [1, 2, 3]

with shelve.open('mydata.db') as db:
    # 直接修改列表不会写回
    db['numbers'].append(4)
    print(db['numbers'])  # [1, 2, 3, 4]
    # 关闭后再打开，变化没有保存因为没重新赋值
```

- 设为`writeback=True`可缓存内容，修改后自动写回，但性能较慢，适用于复杂可变对象。

---

### 示例和读取对象

```python
import shelve

data = {
    'name': 'Bob',
    'age': 25,
    'courses': ['math', 'physics']
}

# 存储数据
with shelve.open('student.db') as db:
    for key, value in data.items():
        db[key] = value

# 读取数据
with shelve.open('student.db') as db:
    print(db['name'])         # Bob
    print(db.get('courses'))  # ['math', 'physics']
```

---

### 注意事项

- shelve对同一个文件不能多进程并发写入，容易导致数据损坏。
- 数据库文件的具体扩展名和实现依赖系统上的dbm库，不同平台文件可能不同。
- 不要把数据库文件直接删除或手动改写，否则可能导致数据丢失。
- 在修改可变对象（如列表、字典）时，需注意是否使用`writeback=True`以确保写回。

---

### 总结

| 优点                     | 缺点                                     |
| ------------------------ | ---------------------------------------- |
| 使用字典接口，简单易用   | 并发支持差，不能多个进程写同一文件       |
| 支持存储任意pickle对象   | 底层依赖平台，文件存在兼容差异           |
| 标准库，无需安装额外模块 | 适用数据量有限，不适合大数据和高性能需求 |

---



Python中的对象持久化，指的是将内存中的对象状态保存到存储介质（如文件、数据库）中，以便后续程序运行时能够恢复使用。这种技术在数据存储、缓存、配置保存等场景非常有用。

---

##  对象持久化的方式

Python提供了多种实现对象持久化的方案，主要有：

### 1.1 pickle模块

- **简介**：Python内置的序列化模块，可以将任意Python对象转换成字节流保存到文件，也可以从字节流恢复对象。
- **优点**：使用简单，支持绝大多数Python对象。
- **缺点**：序列化格式是Python专有的，不适合跨语言，且存在安全风险（反序列化不可信数据可能执行恶意代码）。
- **用法示例**：

```python
import pickle

# 序列化对象到文件
data = {'name': 'Alice', 'age': 30}
with open('data.pkl', 'wb') as f:
    pickle.dump(data, f)

# 反序列化
with open('data.pkl', 'rb') as f:
    new_data = pickle.load(f)
print(new_data)
```

---

### 1.2 shelve模块

- **简介**：基于pickle和dbm的结合，提供了字典接口的持久化对象存储。适合存放多个对象，以键值对形式管理。
- **优点**：字典接口方便，适合简单数据存储。
- **缺点**：并发支持弱，跨平台文件兼容差。
- **用法详见上一轮回答。**

---

### 1.3 json模块

- **简介**：标准库中处理JSON格式的模块，适用于存储简单数据结构，如列表、字典、字符串、数字等。
- **优点**：文件格式通用，易读且多语言支持。
- **缺点**：不支持自定义对象，需要自行转换（如重写`__dict__`或自定义序列化函数）。
- **示例**：

```python
import json

data = {'name': 'Alice', 'age': 30}
with open('data.json', 'w') as f:
    json.dump(data, f)

with open('data.json') as f:
    new_data = json.load(f)
print(new_data)
```

---

### 1.4 其他数据库接口（如sqlite3）

- **简介**：内置sqlite3模块可操作SQLite数据库，适用于结构化数据持久化。
- **优点**：支持SQL查询，适合复杂查询和跨应用共享。
- **缺点**：需要设计数据库表，使用相对复杂。
- 示例略。

---

### 2. 对比总结

| 方式    | 支持对象                   | 读写形式   | 文件格式         | 跨语言 | 安全性               | 适用场景                 |
| ------- | -------------------------- | ---------- | ---------------- | ------ | -------------------- | ------------------------ |
| pickle  | 几乎所有Python对象         | 二进制     | Python专用二进制 | 否     | 不安全（反序列化时） | Python内部对象存储       |
| shelve  | 支持pickle的所有对象       | 类字典接口 | 依赖dbm文件      | 否     | 同pickle             | 简单的对象字典持久化     |
| json    | 字典、列表、字符串、数字等 | 文本       | JSON文本格式     | 是     | 安全                 | 与其他语言交互的数据交换 |
| sqlite3 | 结构化数据                 | SQL数据库  | sqlite数据库文件 | 是     | 安全                 | 复杂数据存储与查询       |

---

### 3. 一些持久化相关的进阶话题

- **自定义序列化**  
  自定义类通过重写`__getstate__`和`__setstate__`方法，控制pickling和unpickling行为。

- **安全性考虑**  
  不可信来源的pickle文件切忌反序列化，否则可能执行恶意代码。

- **持久化和缓存**  
  持久化还可以用于实现缓存机制，如用redis、memcached作为外部缓存。

---

### 4. 小结

Python提供了多种方便的对象持久化手段：

- 需要跨语言或简单文本格式，优先用`json`。
- 只针对Python且保存复杂对象，选择`pickle`。
- 想用类字典接口管理多个对象，用`shelve`。
- 对数据有复杂结构及查询需求，选用`sqlite3`或其它数据库。

## 文本文件读写

好的，下面我详细讲解一下Python中**文本文件的读写**相关内容，包括打开文件、读写操作、文件关闭以及常见注意事项和示例。

---

### 一、文件打开

Python内置函数`open()`用于打开文件，格式如下：

```python
open(file, mode='r', encoding=None)
```

- `file`：文件路径（相对或绝对）
- `mode`：打开模式，默认为只读文本模式 `'r'`
- `encoding`：文本文件的编码方式，常用`'utf-8'`，默认为平台默认编码

---

### 二、打开模式

| 模式   | 说明                         | 读/写    | 文件不存在处理   |
| ------ | ---------------------------- | -------- | ---------------- |
| `'r'`  | 只读（默认），文件必须存在   | 读取     | 文件不存在报错   |
| `'w'`  | 写入，文件存在则覆盖         | 写入     | 文件不存在则创建 |
| `'a'`  | 追加写入，文件指针在文件末尾 | 写入追加 | 文件不存在则创建 |
| `'x'`  | 独占写入，不允许覆盖已有文件 | 写入     | 文件已存在则报错 |
| `'r+'` | 读写模式，文件必须存在       | 读写     | 文件不存在报错   |
| `'w+'` | 读写模式，覆盖写入           | 读写     | 文件不存在则创建 |
| `'a+'` | 读写模式，追加写入           | 读写追加 | 文件不存在则创建 |

---

### 三、文本文件读操作

1. **读取整个文件内容**

```python
with open('file.txt', 'r', encoding='utf-8') as f:
    content = f.read()
print(content)
```

2. **按行读取**

- 使用`readline()`读取一行，调用多次读取多行：

```python
with open('file.txt', 'r', encoding='utf-8') as f:
    line = f.readline()
    while line:
        print(line, end='')
        line = f.readline()
```

- 使用`readlines()`一次性读取所有行，返回列表：

```python
with open('file.txt', 'r', encoding='utf-8') as f:
    lines = f.readlines()
print(lines)  # 每行为列表一个元素
```

- 直接遍历文件对象，逐行处理（推荐）：

```python
with open('file.txt', 'r', encoding='utf-8') as f:
    for line in f:
        print(line, end='')
```

---

### 四、文本文件写操作

- 打开模式为`'w'`（覆盖写）或`'a'`（追加写）

```python
with open('file.txt', 'w', encoding='utf-8') as f:
    f.write('第一行文本\n')
    f.write('第二行文本\n')
```

- 追加写入（保留原有内容，在末尾添加）：

```python
with open('file.txt', 'a', encoding='utf-8') as f:
    f.write('追加的文本\n')
```

- 写入多行：

```python
lines = ['第一行\n', '第二行\n', '第三行\n']
with open('file.txt', 'w', encoding='utf-8') as f:
    f.writelines(lines)
```

注意：`writelines()`不会自动添加换行符，需要在字符串中显式包含`\n`。

---

### 五、文件关闭

- 使用`with open(...) as f:` 形式打开文件，Python会自动关闭文件，推荐方式。

- 也可以使用传统打开关闭：

```python
f = open('file.txt', 'r')
data = f.read()
f.close()
```

缺点：如果程序异常，文件可能未被关闭。

---

### 六、编码问题

- 文本文件涉及编码，建议打开时显式声明编码，防止跨平台乱码。
- 常用编码：`utf-8`，`gbk`（Windows中文环境）

---

### 七、常用示例

1. **读取文本文件并打印**

```python
with open('example.txt', 'r', encoding='utf-8') as f:
    for line in f:
        print(line.strip())  # strip去除换行符和两边空白
```

2. **写文本文件**

```python
text = ['Hello world\n', 'Python文件读写示例\n']
with open('example_write.txt', 'w', encoding='utf-8') as f:
    f.writelines(text)
```

3. **读写组合**

```python
with open('input.txt', 'r', encoding='utf-8') as fin, \
     open('output.txt', 'w', encoding='utf-8') as fout:
    for line in fin:
        fout.write(line.upper())
```

---

### 八、常见问题

- **写入字符串必须是str类型，不能直接写int，需要先转换为str。**

```python
f.write(str(123))
```

- **不能将二进制文件用文本模式打开，需用`'rb'`或`'wb'`等二进制模式。**

- **文件路径要注意相对路径和绝对路径，根据工作目录不同会导致找不到文件。**

---

### 九、总结

| 动作       | 方法                     | 说明                             |
| ---------- | ------------------------ | -------------------------------- |
| 读取全部   | `f.read()`               | 读取整个文件内容                 |
| 读取一行   | `f.readline()`           | 每次读取一行                     |
| 读取所有行 | `f.readlines()`          | 读取全部行，返回列表             |
| 迭代行     | `for line in f`          | 逐行遍历文件                     |
| 写入字符串 | `f.write(string)`        | 写入字符串                       |
| 写入多行   | `f.writelines(list)`     | 一次写入多行（注意换行符）       |
| 关闭文件   | `f.close()` / `with`语法 | 保证文件句柄释放，建议使用`with` |

---

好的！下面我来详细介绍一下Python中的**上下文管理器（Context Manager）**，这是一种非常重要且实用的机制，帮助我们优雅地管理资源（如文件、网络连接、锁等）的获取和释放。

---

## 上下文管理器

上下文管理器是一种对象，它定义了进入和退出某个“上下文”的行为，确保无论代码如何执行完毕，都能正确地清理使用的资源，比如关闭文件、释放锁等。

Python中的上下文管理器主要通过`with`语句使用。

---

### 1. 上下文管理器的作用

- 简化资源管理代码，防止忘记释放资源导致内存泄漏、文件句柄泄漏等问题。
- 保证即使出现异常，也会执行资源释放代码。
- 常用于文件操作、数据库连接、线程锁和事务管理等场景。

---

### 2. 上下文管理器的接口

要成为上下文管理器，必须实现以下两个方法：

- `__enter__(self)`  
  进入上下文时调用。返回值会赋给`with ... as ...`中`as`后的变量。
- `__exit__(self, exc_type, exc_val, exc_tb)`  
  退出上下文时调用。参数为异常类型、异常值、追踪信息，如果不发生异常这三个参数均为`None`。

---

### 3. 使用上下文管理器的`with`语法

```python
with context_manager as var:
    # 在这里使用var
    ...
```

等价于：

```python
cm = context_manager
var = cm.__enter__()
try:
    # 使用var
    ...
except Exception as e:
    if not cm.__exit__(type(e), e, e.__traceback__):
        raise
else:
    cm.__exit__(None, None, None)
```

也就是说，`__exit__`方法有机会处理异常，若返回`True`，异常会被吞掉，否则继续抛出。

---

### 4. Python内置的上下文管理器示例

#### 文件操作

```python
with open('file.txt', 'r', encoding='utf-8') as f:
    content = f.read()
# 使用with保证文件关闭，无论读取是否成功文件都关闭
```

这就是一个典型的上下文管理器用例。

---

### 5. 自定义上下文管理器方法一：定义类并实现接口

示例：自定义一个上下文管理器，打印进入和退出提示。

```python
class MyContext:
    def __enter__(self):
        print('进入上下文')
        return self

    def __exit__(self, exc_type, exc_val, exc_tb):
        print('退出上下文')
        if exc_type:
            print(f'异常类型: {exc_type}')
        # 返回False表示不处理异常，继续抛出
        return False

with MyContext() as ctx:
    print('正在运行上下文代码')
    # raise Exception('测试异常')
```

输出：

```
进入上下文
正在运行上下文代码
退出上下文
```

如果取消注释异常代码，异常信息会被打印，且异常仍会抛出。

---

### 6. 自定义上下文管理器方法二：用 `contextlib` 模块简化

Python的`contextlib`模块提供了装饰器`@contextmanager`，可以用生成器函数轻松创建上下文管理器。

示例：

```python
from contextlib import contextmanager

@contextmanager
def my_context():
    print('进入上下文')
    try:
        yield '上下文资源'
    finally:
        print('退出上下文')

with my_context() as resource:
    print(f'使用资源: {resource}')
```

输出：

```
进入上下文
使用资源: 上下文资源
退出上下文
```

这里，`yield`之前的代码对应`__enter__`，`yield`之后的代码对应`__exit__`。

---

### 7. 上下文管理器更多用法示例

#### 文件上下文管理器（我们自己写一个简化版）

```python
class FileOpener:
    def __init__(self, filename, mode):
        self.filename = filename
        self.mode = mode
        self.file = None

    def __enter__(self):
        self.file = open(self.filename, self.mode)
        return self.file

    def __exit__(self, exc_type, exc_val, exc_tb):
        if self.file:
            self.file.close()
```

使用：

```python
with FileOpener('test.txt', 'w') as f:
    f.write('Hello context manager!')
```

就比普通的open操作更清晰地展示了上下文管理器原理。

---

### 8. `__exit__`方法参数详解

`__exit__(self, exc_type, exc_val, exc_tb)` 接受三个参数：

- `exc_type`：异常类型，若无异常为`None`
- `exc_val`：异常实例
- `exc_tb`：异常的traceback对象

如果处理异常成功，`__exit__`应返回`True`，这样异常不会向上传播。

---

### 9. 总结

| 知识点             | 说明                                                         |
| ------------------ | ------------------------------------------------------------ |
| 上下文管理器作用   | 优雅管理资源，避免泄漏，保证异常时也释放资源                 |
| 必须方法           | `__enter__()` 和 `__exit__(exc_type, exc_val, exc_tb)`       |
| `with`语句等价代码 | 调用`__enter__()`进入上下文，执行代码块，调用`__exit__()`退出上下文 |
| contextlib简化工具 | `@contextmanager`装饰器，基于生成器快速创建上下文管理器      |
| 常见应用           | 文件操作、数据库连接、线程锁、临时改变环境、事务控制等       |

## 结构化文本文件

当然，下面我给你详细介绍一下Python中处理**结构化文本文件CSV（Comma-Separated Values）**的相关知识，包括CSV格式介绍、Python内置的csv模块用法、常见读写操作和一些进阶技巧。

---

### csv

#### 一、什么是CSV文件？

- **CSV格式**是最常用的结构化文本数据存储格式之一，文件中每行表示一条记录，字段之间用逗号`,`分隔（有时也用其他符号如制表符`\t`分隔）。

- 通常用来存储表格型数据，兼容绝大多数电子表格程序（Excel、Google Sheets）和数据库导入导出。

- CSV文件本质是纯文本，易读、易编辑，支持跨平台和多语言。

---

#### 二、csv模块简介

Python内置模块`csv`专门用于读写CSV文件，能正确处理逗号、引号、转义符等问题，避免手动字符串分割的坑。

常用函数：

- `csv.reader`：读取CSV文件并返回迭代器
- `csv.writer`：写入CSV文件
- `csv.DictReader`：将CSV每行作为字典读取，键为表头
- `csv.DictWriter`：以字典形式写入CSV

---

#### 三、基本用法

文件示例`data.csv`：

```csv
name,age,city
Alice,30,New York
Bob,25,Los Angeles
Charlie,35,Chicago
```

---

##### 3.1 读取CSV文件

```python
import csv

with open('data.csv', 'r', encoding='utf-8') as f:
    reader = csv.reader(f)
    header = next(reader)  # 读取表头
    print('Header:', header)
    for row in reader:
        print(row)
```

输出：

```
Header: ['name', 'age', 'city']
['Alice', '30', 'New York']
['Bob', '25', 'Los Angeles']
['Charlie', '35', 'Chicago']
```

---

##### 3.2 读取CSV为字典形式（推荐，方便按列访问）

```python
import csv

with open('data.csv', 'r', encoding='utf-8') as f:
    dict_reader = csv.DictReader(f)
    for row in dict_reader:
        print(row['name'], row['age'], row['city'])
```

输出：

```
Alice 30 New York
Bob 25 Los Angeles
Charlie 35 Chicago
```

---

##### 3.3 写入CSV文件

```python
import csv

header = ['name', 'age', 'city']
rows = [
    ['David', 28, 'Boston'],
    ['Eva', 22, 'Seattle']
]

with open('output.csv', 'w', encoding='utf-8', newline='') as f:
    writer = csv.writer(f)
    writer.writerow(header)  # 写表头
    writer.writerows(rows)    # 写多行数据
```

注意：`open()`时建议使用`newline=''`参数，避免写入时多余空行问题（这是csv模块的推荐做法）。

---

##### 3.4 以字典形式写入CSV

```python
import csv

header = ['name', 'age', 'city']
rows = [
    {'name': 'David', 'age': 28, 'city': 'Boston'},
    {'name': 'Eva', 'age': 22, 'city': 'Seattle'}
]

with open('output_dict.csv', 'w', encoding='utf-8', newline='') as f:
    dict_writer = csv.DictWriter(f, fieldnames=header)
    dict_writer.writeheader()       # 写表头
    dict_writer.writerows(rows)     # 写多行字典数据
```

---

#### 四、csv模块关键参数解释

| 参数             | 说明                                                       |
| ---------------- | ---------------------------------------------------------- |
| delimiter        | 分隔符，默认为`,`，可设为`\t`制表符等                      |
| quotechar        | 引号字符，默认为`"`，当字段包含分隔符时用引号括起来        |
| quoting          | 何时引用字段，常用`csv.QUOTE_MINIMAL`，可设为`QUOTE_ALL`等 |
| skipinitialspace | 跳过分隔符后的空格                                         |
| escapechar       | 转义字符，用于字符串中出现引号等特殊符号                   |
| strict           | 是否严格模式，遇到格式错误抛异常                           |

---

#### 五、进阶使用技巧

##### 5.1 处理带有逗号的字段

字段内容如果含有逗号，需要用引号括起来，csv模块会自动处理。

示例数据：

```csv
name,comment
Alice,"Hello, world"
Bob,"Good, thanks"
```

读取时csv模块自动识别：

```python
for row in csv.reader(f):
    print(row)
# 输出 ['Alice', 'Hello, world']
```

---

##### 5.2 处理其他分隔符

如果使用制表符分隔，可定义`delimiter='\t'`：

```python
csv.reader(f, delimiter='\t')
```

---

##### 5.3 自定义写入格式

- 控制换行符：保证文件跨平台兼容，一般`open()`使用`newline=''`
- 控制编码：多数CSV是UTF-8，但也有可能是GBK等，写入时注意指定

---

##### 5.4 大文件逐行处理

CSV读取器是迭代器，数据量大时不必一次读入内存，适合流式处理。

---

#### 六、示例总结

读取：

```python
import csv

with open('data.csv', 'r', encoding='utf-8') as f:
    reader = csv.DictReader(f)
    for row in reader:
        print(row)
```

写入：

```python
import csv

with open('output.csv', 'w', encoding='utf-8', newline='') as f:
    writer = csv.writer(f)
    writer.writerow(['name', 'age'])
    writer.writerow(['Alice', 30])
    writer.writerow(['Bob', 25])
```

---

#### 七、常见问题

- Windows写CSV出现空行：解决方案是`open()`时添加`newline=''`参数。
- CSV编码问题：读取非UTF-8编码文件时要指定正确编码。
- CSV字段中有逗号、换行需引号包裹，csv模块自动处理，不用手写解析。

---

#### 八、小结

- CSV是轻量级的结构化数据文件标准，广泛用于数据交换。
- Python内置csv模块处理CSV文件简单可靠，支持多种功能。
- 记住常用的`csv.reader` / `csv.writer`及其字典版本`DictReader` / `DictWriter`。
- 注意文件打开方式，编码和换行参数避免常见坑。

---

### Excel

当然详细介绍一下Python中**Excel结构化文本文件**的相关内容，包括Excel的基本概念、Python中处理Excel的常用库、常见操作示例及进阶技巧。

---

#### 一、什么是Excel文件？

- Excel是Microsoft Office套件中的电子表格软件，文件格式主要有：
  - **.xls** —— 早期Excel二进制格式，兼容性好但容量和功能有限
  - **.xlsx** —— Excel 2007及以后版本基于XML的开放格式，功能更强大且文档结构清晰

- Excel文件可以包含多个工作表（Sheet），每个工作表含有行和列的表格数据，可以存储文字、数字、公式、图表等。

- Excel文件是结构化数据存储格式，应用广泛，比如财务报表、数据分析、统计等。

---

#### 二、Python中处理Excel的常用库

Python标准库没有直接支持Excel文件，需要第三方库，常见的有：

| 库名称       | 功能特点                                                   | 支持格式              |
| ------------ | ---------------------------------------------------------- | --------------------- |
| `xlrd`       | 只读旧版Excel格式(.xls及早期.xlsx*)（目前新版不支持.xlsx） | `.xls`（部分`.xlsx`） |
| `xlwt`       | 写旧版Excel格式（.xls）                                    | `.xls`                |
| `openpyxl`   | 读写新版Excel格式（.xlsx），支持表格样式和公式处理         | `.xlsx`               |
| `pandas`     | 高层数据分析库，基于`openpyxl`/`xlrd`等做Excel数据处理     | `.xls`/`.xlsx`        |
| `xlsxwriter` | 只写，功能强大的`.xlsx`生成库，支持图表、格式化            | `.xlsx`               |

> 注：`xlrd`从2.0版本起不再支持`.xlsx`格式，如需读取`.xlsx`请用`openpyxl`。

---

#### 三、使用openpyxl读取和写入Excel

`openpyxl`是目前处理`.xlsx`格式的主力库。

##### 3.1 安装

```bash
pip install openpyxl
```

##### 3.2 读取Excel文件

```python
from openpyxl import load_workbook

# 加载Excel文件
wb = load_workbook('example.xlsx')

# 选择工作表，既可以按名字，也可以按活动表
ws = wb['Sheet1']
# 或 ws = wb.active

# 读取单元格数据
print(ws['A1'].value)  # 读取A1单元格

# 遍历所有行和列
for row in ws.iter_rows(min_row=1, max_col=3, max_row=5):
    for cell in row:
        print(cell.value, end=' ')
    print()
```

---

##### 3.3 写入Excel文件

```python
from openpyxl import Workbook

wb = Workbook()
ws = wb.active
ws.title = "MySheet"

# 写数据
ws['A1'] = '姓名'
ws['B1'] = '年龄'

data = [
    ('Alice', 30),
    ('Bob', 25),
    ('Charlie', 35),
]

for idx, (name, age) in enumerate(data, start=2):
    ws.cell(row=idx, column=1, value=name)
    ws.cell(row=idx, column=2, value=age)

# 保存文件
wb.save('output.xlsx')
```

---

#### 四、使用pandas操作Excel文件

`pandas`封装了Excel读写接口，用法更侧重于数据分析。

##### 4.1 安装

```bash
pip install pandas openpyxl xlrd
```

##### 4.2 读取Excel为DataFrame

```python
import pandas as pd

# 读取Excel中第一个或者指定工作表
df = pd.read_excel('example.xlsx', sheet_name='Sheet1')

print(df.head())
```

##### 4.3 写入DataFrame到Excel

```python
df = pd.DataFrame({
    'Name': ['Alice', 'Bob', 'Charlie'],
    'Age': [30, 25, 35]
})

df.to_excel('output.xlsx', sheet_name='People', index=False)
```

---

#### 五、Excel文件操作常见技巧

- **读取多个工作表**

```python
dfs = pd.read_excel('example.xlsx', sheet_name=None)  # 返回字典，键为sheet名，值为DataFrame
for name, data in dfs.items():
    print(f"Sheet: {name}")
    print(data.head())
```

- **追加写入**

Excel不支持直接追加写入单独行，常用方法为：

1. 读取已有数据为DataFrame  
2. 追加数据  
3. 重新写回Excel文件

- **格式化单元格**

`openpyxl`支持设置字体、颜色、边框、对齐等：

```python
from openpyxl.styles import Font

cell = ws['A1']
cell.font = Font(name='Calibri', size=14, bold=True, color='FF0000')
```

- **处理公式**

写入单元格可以直接写公式：

```python
ws['C1'] = '=SUM(B2:B4)'
wb.save('output.xlsx')
```

---

#### 六、其它相关库简介

- **xlwt**：只能写`.xls`格式，不支持`.xlsx`，适合兼容旧系统
- **xlrd**：用于读取`.xls`，新版无法读取`.xlsx`
- **xlsxwriter**：功能强大的写`.xlsx`库，支持图表等高级功能，但只能写不能读

---

#### 七、总结表

| 操作需求           | 推荐库                       | 支持格式        | 功能特点                         |
| ------------------ | ---------------------------- | --------------- | -------------------------------- |
| 读取 `.xlsx`       | openpyxl, pandas             | `.xlsx`         | 读取工作表，访问单元格，样式支持 |
| 写入 `.xlsx`       | openpyxl, pandas, xlsxwriter | `.xlsx`         | 样式、公式、图表支持             |
| 读取 `.xls`        | xlrd, pandas                 | `.xls`          | 早期Excel格式                    |
| 写入 `.xls`        | xlwt                         | `.xls`          | 兼容旧Excel格式                  |
| 数据分析和批量处理 | pandas                       | `.xls`, `.xlsx` | 高层数据结构支持，方便转换和统计 |

---

#### 八、示例代码汇总

**读取`xlsx`文件第一张表并遍历打印所有数据（openpyxl）**

```python
from openpyxl import load_workbook

wb = load_workbook('example.xlsx')
ws = wb.active

for row in ws.iter_rows(values_only=True):
    print(row)
```

**使用pandas读取Excel文件全部工作表**

```python
import pandas as pd

dfs = pd.read_excel('example.xlsx', sheet_name=None)
for sheet_name, df in dfs.items():
    print(f'Sheet Name: {sheet_name}')
    print(df.head())
```

---

#### 九、参考资料

- [openpyxl官方文档](https://openpyxl.readthedocs.io/en/stable/)
- [pandas官方文档 - Excel IO](https://pandas.pydata.org/pandas-docs/stable/reference/api/pandas.read_excel.html)

---

### PDF

详细介绍一下Python中非常流行的PDF处理库——**PyPDF2**，包括它的功能、安装、主要用法示例以及一些进阶技巧。

---

#### 一、什么是 PyPDF2？

- `PyPDF2` 是一个纯Python编写的库，用于**阅读、操作和写入 PDF 文件**。
- 它支持：合并PDF、拆分页面、加密解密、旋转页面、提取文本和元数据等功能。
- 适合需要自动化PDF处理的Python开发者和数据分析师。

---

#### 二、安装方法

```bash
pip install PyPDF2
```

> 注意：旧版本有时写作`pypdf2`，当前推荐使用`PyPDF2`（最新维护的库），从2022年起，PyPDF2已迁移到`pypdf`项目，接口基本兼容。

---

#### 三、PyPDF2主要功能和类

- **PdfReader**：读取PDF文件，访问文件内容、页面、元数据、文本等。
- **PdfWriter**：创建和写入PDF文件，支持添加页面、合并、加密等。
- **PageObject**：代表PDF中的单页，支持旋转、裁剪、合并页面内容操作。
- **常用功能**：
  - 读取PDF并提取文本
  - 合并多个PDF文件
  - 拆分PDF（提取指定页）
  - 旋转页面
  - 给PDF加密或解密
  - 修改PDF元数据

---

#### 四、基础示例

---

##### 4.1 读取PDF并获取页数

```python
from PyPDF2 import PdfReader

reader = PdfReader('example.pdf')
print(f'页数: {len(reader.pages)}')
```

---

##### 4.2 提取文本（示例提取第一页）

```python
page = reader.pages[0]
text = page.extract_text()
print(text)
```

---

##### 4.3 合并两个PDF文件

```python
from PyPDF2 import PdfReader, PdfWriter

pdf_writer = PdfWriter()

for pdf_file in ['doc1.pdf', 'doc2.pdf']:
    reader = PdfReader(pdf_file)
    for page in reader.pages:
        pdf_writer.add_page(page)

with open('merged.pdf', 'wb') as f_out:
    pdf_writer.write(f_out)
```

---

##### 4.4 拆分PDF，提取部分页面

```python
from PyPDF2 import PdfReader, PdfWriter

reader = PdfReader('example.pdf')
writer = PdfWriter()

# 提取第2页和第3页（索引从0开始）
for i in [1, 2]:
    writer.add_page(reader.pages[i])

with open('split.pdf', 'wb') as f_out:
    writer.write(f_out)
```

---

##### 4.5 旋转PDF页面

```python
page = reader.pages[0]
page.rotate(90)  # 顺时针旋转90度

writer = PdfWriter()
writer.add_page(page)

with open('rotated.pdf', 'wb') as f_out:
    writer.write(f_out)
```

---

##### 4.6 给PDF文件加密

```python
reader = PdfReader('example.pdf')
writer = PdfWriter()

for page in reader.pages:
    writer.add_page(page)

writer.encrypt(user_password='userpass', owner_password='ownerpass', use_128bit=True)

with open('encrypted.pdf', 'wb') as f_out:
    writer.write(f_out)
```

打开时需要输入密码`userpass`。

---

##### 4.7 解密PDF文件

```python
reader = PdfReader('encrypted.pdf')
if reader.is_encrypted:
    reader.decrypt('userpass')
    text = reader.pages[0].extract_text()
    print(text)
```

---

#### 五、PyPDF2的注意点及限制

- **文本提取**功能较为基础，对复杂布局和格式支持有限，无法提取图片或表格。
- 不支持创建PDF内容，如添加文字、绘图等，只能操作已有PDF。
- 加密解密支持有限，只能处理常见的用户密码保护。
- 对PDF格式的内部复杂结构理解有限，有一些PDF文件无法正确处理。

---

#### 六、常用API总结

| 功能         | 类/方法                          | 说明                      |
| ------------ | -------------------------------- | ------------------------- |
| 打开PDF      | `PdfReader(file)`                | 读取PDF文件               |
| 获取页数     | `len(reader.pages)`              | PDF页面总数               |
| 获取页面对象 | `reader.pages[index]`            | 返回第`index`页PageObject |
| 提取文本     | `page.extract_text()`            | 提取页面文本              |
| 新建PDF文档  | `PdfWriter()`                    | 创建空的写入器            |
| 添加页面     | `writer.add_page(page)`          | 添加页面到写入PDF         |
| 写入文件     | `writer.write(file_obj)`         | 写入PDF到文件             |
| 旋转页面     | `page.rotate(clockwise_degrees)` | 页面对页旋转              |
| 加密         | `writer.encrypt(password)`       | 给PDF加密                 |
| 解密         | `reader.decrypt(password)`       | 解密PDF                   |

---

#### 七、简单示例整合

```python
from PyPDF2 import PdfReader, PdfWriter

# 1. 读取PDF
reader = PdfReader('input.pdf')

# 2. 创建写入对象
writer = PdfWriter()

# 3. 复制并旋转第一页
page = reader.pages[0]
page.rotate(90)
writer.add_page(page)

# 4. 添加剩余页面
for i in range(1, len(reader.pages)):
    writer.add_page(reader.pages[i])

# 5. 保存新PDF文件
with open('output.pdf', 'wb') as f_out:
    writer.write(f_out)
```

---

#### 八、总结

- PyPDF2是Python中优秀且免费的PDF处理工具，适合自动化文档处理。
- 主要用于合并、拆分、旋转、加密和文本提取。
- 不支持内容创建和复杂格式处理。
- 对于复杂PDF操作，可能需要结合其他库（如`pdfplumber`做高级文本提取，`reportlab`做PDF生成）。

---

## 简单的图形化界面

好的！下面我将详细介绍 Python 中的 **easygui** 模块，包括它的特点、安装方法、主要功能、常见对话框示例以及使用场景。

---

### 一、什么是 EasyGUI？

**EasyGUI** 是一个非常简单易用的 Python 图形用户界面模块，它提供了一组基于对话框的函数，用来创建简单的GUI界面，而无需了解事件驱动、窗口管理等复杂的GUI编程细节。

- EasyGUI 的设计理念是**足够简单**：用最少的代码实现最直接的交互。
- 适合快速开发简单的用户交互，不适合复杂的窗口布局和自定义控件。
- EasyGUI 内部基于 Tkinter 实现，但API更加简洁直观。

---

### 二、安装 EasyGUI

EasyGUI 不是 Python 标准库，需要通过 pip 安装：

```bash
pip install easygui
```

安装完成后即可在代码中导入：

```python
import easygui
```

---

### 三、EasyGUI 的主要特点

- 不需要编写事件循环 (`mainloop`)。
- 通过调用函数一次即可弹出对话框，等待用户输入或点击。
- 常用的对话框包括：消息框、输入框、选择框、文件选择框等。
- 返回结果是用户的输入或选择，方便后续处理。

---

### 四、常用对话框与示例

以下示例展示几个 EasyGUI 常用的对话框及其用法。

#### 1. 消息框（`msgbox`）

弹出一个消息提示框，用户点击“确定”关闭。

```python
import easygui

easygui.msgbox("这是一个消息框", title="消息提示")
```

参数说明：
- 第一个参数是显示的消息文本。
- `title` 是窗口标题（可选）。

#### 2. 确认框（`ynbox`）

显示一个“是/否”对话框，返回 `True`（是）或 `False`（否）。

```python
if easygui.ynbox("你想继续吗？", title="确认"):
    print("用户选择了是")
else:
    print("用户选择了否")
```

#### 3. 输入框（`enterbox`）

弹出一个输入框，用户输入字符串后点击确定返回用户输入内容，取消时返回 `None`。

```python
name = easygui.enterbox("请输入你的名字：", title="输入框")
if name:
    print("你输入的名字是:", name)
else:
    print("用户取消了输入")
```

#### 4. 多行文本输入框（`multenterbox`）

允许用户输入多条信息，返回列表。

```python
fields = ["姓名", "年龄", "邮箱"]
values = easygui.multenterbox("填写以下信息：", fields=fields)
if values:
    print("用户输入：", values)
else:
    print("用户取消了输入")
```

#### 5. 单项选择框（`choicebox`）

让用户从给定选项中选择一个，返回选中的字符串。

```python
choice = easygui.choicebox("请选择一个水果：", choices=["苹果", "香蕉", "橘子"])
print("选择的是:", choice)
```

#### 6. 多项选择框（`multchoicebox`）

让用户选择多个选项，返回选中的列表。

```python
choices = easygui.multchoicebox("选择喜欢的语言：", choices=["Python", "Java", "C++", "JavaScript"])
print("用户选择了:", choices)
```

#### 7. 文件选择框（`fileopenbox` 和 `filesavebox`）

- `fileopenbox` 打开文件选择对话框，返回选中文件路径。
- `filesavebox` 保存文件对话框。

```python
filename = easygui.fileopenbox("请选择文件打开")
print("选择的文件是:", filename)

savefile = easygui.filesavebox("选择保存路径")
print("保存到:", savefile)
```

#### 8. 滚动文本框（`codebox`）

显示一段多行文本，带滚动条，不可编辑。

```python
easygui.codebox("显示内容", text="这里是一段示例代码或多行文字。")
```

---

### 五、EasyGUI 的API总结（部分常用函数）

| 函数名                               | 功能描述                 | 返回值示例                       |
| ------------------------------------ | ------------------------ | -------------------------------- |
| `msgbox(msg, title)`                 | 弹出信息提示框           | 用户点击确定，不返回具体值       |
| `ynbox(msg, title)`                  | “是/否”对话框            | `True`（是） / `False`（否）     |
| `enterbox(msg, title)`               | 文本输入框               | 用户输入的字符串 或 `None`       |
| `multenterbox(msg, title, fields)`   | 多文本输入，多输入框     | 列表（每个输入框内容） 或 `None` |
| `choicebox(msg, title, choices)`     | 单项选择框               | 选中的字符串 或 `None`           |
| `multchoicebox(msg, title, choices)` | 多项选择框               | 选中字符串列表 或 `None`         |
| `fileopenbox(msg, title)`            | 选择打开文件             | 选中文件路径字符串 或 `None`     |
| `filesavebox(msg, title)`            | 选择保存文件路径         | 文件路径字符串 或 `None`         |
| `codebox(msg, text)`                 | 显示大段文本（不可编辑） | 无返回值                         |

---

### 六、EasyGUI 的使用场景

- 需要快速为Python脚本增加简单的图形界面交互。
- 教学和学习GUI编程的入门工具。
- 编写工具脚本，让用户选择文件、输入参数等。
- 不需要复杂布局，只要弹窗式交互的场景。

---

### 七、使用注意事项

- EasyGUI 是基于 Tkinter，因此你的环境必须支持 Tkinter。
- GUI风格较为基础和传统，不适合复杂定制界面。
- 每次调用对话框时，程序会阻塞等待用户操作，不适合事件驱动且复杂的应用。
- 适合快速、小型、简单的用户交互需求。

---

### 八、综合示例

```python
import easygui

easygui.msgbox("欢迎使用EasyGUI示例程序", title="欢迎")

if easygui.ynbox("你想继续吗？", title="确认"):
    name = easygui.enterbox("请输入你的名字", title="输入")
    if name:
        colors = ["红色", "绿色", "蓝色", "黄色"]
        favorite = easygui.choicebox("请选择你喜欢的颜色", choices=colors)
        easygui.msgbox(f"你好，{name}，你选择的颜色是{favorite}", title="结果")
    else:
        easygui.msgbox("你取消了输入", title="提示")
else:
    easygui.msgbox("程序已退出", title="退出")
```

---

Python中的“海龟作图”（Turtle Graphics）是一个非常适合初学者学习编程和图形绘制的模块。它提供了一种模拟海龟在屏幕上移动并绘制图形的方式，利用简单的命令让“海龟”沿着指定路径画出各种图形。这个模块内置于Python标准库中，无需额外安装。

下面我将详细介绍Python海龟作图模块，包括基本概念、常用命令、示例代码以及进阶用法。

---

## 海龟作图

### 一、什么是海龟作图？

“海龟作图”起源于Logo编程语言，是一种基于“指令驱动绘图”的方式。想象有一只海龟，可以在屏幕上按照你的指令前进、转向、画笔提起或落下，绘制各种图案。

Python的`turtle`模块实现了这一机制，适合教学、快速绘图和制作简单动画。

---

### 二、基本使用方法

#### 1. 导入模块

```python
import turtle
```

#### 2. 创建画布和海龟对象

```python
t = turtle.Turtle()  # 创建一个海龟对象
screen = turtle.Screen()  # 创建画布对象
```

#### 3. 让海龟绘图

- `forward(distance)`：向前移动指定距离
- `backward(distance)`：向后移动指定距离
- `right(angle)`：向右转指定度数
- `left(angle)`：向左转指定度数

#### 4. 控制画笔状态

- `penup()` / `pendown()`：提笔（不绘图）/落笔（绘图）
- `pensize(width)`：设置画笔宽度
- `pencolor(color)`：设置画笔颜色（颜色可以是字符串，如"red"，或RGB值）
- `fillcolor(color)`：设置填充颜色
- `begin_fill()` / `end_fill()`：开始填充 / 结束填充

#### 5. 其他有用方法

- `speed(speed)`：设置海龟移动速度，范围1（最慢）到10（最快），还有0—即时绘图
- `goto(x, y)`：移动到指定坐标
- `setheading(angle)`：设置海龟方向（角度0是朝右，逆时针增加）
- `circle(radius, extent=None)`：绘制圆或圆弧
- `clear()`：清除海龟绘制内容
- `reset()`：清屏且重置海龟状态
- `hideturtle()` / `showturtle()`：隐藏/显示海龟形状（箭头）

#### 6. 结束绘图

```python
turtle.done()
```

执行到这里后，窗口将保持显示直到用户关闭。

---

### 三、示例代码

#### 1. 画一个正方形

```python
import turtle

t = turtle.Turtle()
for _ in range(4):
    t.forward(100)
    t.right(90)

turtle.done()
```

#### 2. 画一个带填充的红色三角形

```python
import turtle

t = turtle.Turtle()
t.fillcolor("red")
t.begin_fill()
for _ in range(3):
    t.forward(100)
    t.left(120)
t.end_fill()

turtle.done()
```

#### 3. 画同心圆

```python
import turtle

t = turtle.Turtle()
t.speed(0)
colors = ['red', 'orange', 'yellow', 'green', 'blue', 'indigo', 'violet']

for radius in range(20, 121, 20):
    t.pencolor(colors[radius // 20 - 1])
    t.circle(radius)
    t.up()
    t.sety(t.position()[1] - 20)  # 向下移动20单位
    t.down()

turtle.done()
```

---

### 四、进阶技巧和常见应用

1. **绘制复杂图案和分形**  
   可用递归函数配合海龟绘制分形，比如“谢尔宾斯基三角形”、“科赫曲线”等。

2. **动画效果**  
   通过循环和坐标控制，让海龟动起来，实现简单的动画效果。

3. **事件监听**  
   `Screen`对象支持鼠标点击、键盘按键事件监听，配合海龟实现交互式绘图。

```python
def turn_left():
    t.left(30)

screen.onkey(turn_left, "Left")  # 按下键盘左键转向
screen.listen()
```

4. **坐标系和定位**  
   默认画布中心是坐标原点(0,0)，你可以按照需要进行坐标移动定位。

---

### 五、常用函数总结

| 函数                 | 说明                       |
| -------------------- | -------------------------- |
| `forward(distance)`  | 向前移动指定距离           |
| `backward(distance)` | 向后移动指定距离           |
| `right(angle)`       | 向右转指定角度             |
| `left(angle)`        | 向左转指定角度             |
| `penup()`            | 提笔，不绘制               |
| `pendown()`          | 落笔，开始绘制             |
| `pensize(width)`     | 设置笔的宽度               |
| `pencolor(color)`    | 设置画笔颜色               |
| `fillcolor(color)`   | 设置填充颜色               |
| `begin_fill()`       | 开始填充                   |
| `end_fill()`         | 结束填充                   |
| `speed(speed)`       | 设置移动速度 1-10，0是最快 |
| `goto(x, y)`         | 移到指定坐标               |
| `setheading(angle)`  | 设置海龟朝向角度           |
| `circle(radius)`     | 画圆（半径）               |
| `clear()`            | 清屏，但不改变海龟状态     |
| `reset()`            | 清屏并重置海龟状态         |
| `hideturtle()`       | 隐藏海龟形状（箭头）       |
| `showturtle()`       | 显示海龟形状               |
| `done()`             | 结束绘图，保持窗口         |

---

### 六、总结

Python的`turtle`模块操作简单直观，非常适合初学者学习绘图和编程逻辑。掌握它的基本命令后，可以绘制出丰富多彩的图形，并通过循环、函数、事件等进一步编写交互、动画程序。

如果你想进一步学习，可以尝试：

- 创作自己的图案（比如画花、雪花、迷宫）
- 实现分形图形
- 用事件监听实现交互绘图小游戏

---

## **对象**

---

### 一、什么是对象？

在Python中，**对象（Object）是数据和操作数据的函数的结合体，是程序中可以操作的实体。**

更通俗地说：

- 对象就是“具体存在”的事物，是类的实例。
- 每个对象都有**身份（id）**、**类型（type）**和**值（value）**三个基本属性。
- 一切数据在Python中都是对象，比如整数、字符串、函数、模块、类等。

---

### 二、对象的三大核心属性

1. **身份（Identity）**  
   每个对象都有唯一的身份标识，类似身份证号。  
   在Python中可以用`id(obj)`函数查看，返回对象在内存中的地址（通常表示为整数）。

2. **类型（Type）**  
   表示对象是什么类型，比如整数、字符串、自定义类实例等。  
   用`type(obj)`函数查看。

3. **值（Value）**  
   代表对象的数据内容。

示例：

```python
a = 100
print(id(a))      # 身份
print(type(a))    # 类型：<class 'int'>
print(a)          # 值：100
```

---

### 三、对象与类的关系

- **类是对象的模板，创建对象的蓝图；对象是类的实例。**  
- 创建对象就是调用类，类会生产一个对应的实例（对象），该实例拥有类定义的属性和方法。

示例：

```python
class Person:
    def __init__(self, name):
        self.name = name

p = Person("Alice")  # 创建对象，p是Person类的一个实例（对象）
print(type(p))      # <class '__main__.Person'>
```

---

### 四、Python中一切都是对象

Python中常见的所有数据类型本质上都是对象：  
- 数字：`int`, `float`  
- 字符串：`str`  
- 列表：`list`  
- 集合：`set`  
- 字典：`dict`  
- 函数、类、模块，甚至代码本身都是对象。

因此，变量其实是引用对象的标签。

---

### 五、对象的可变性

Python对象根据可变性分为：

- **不可变对象（immutable objects）**  
  其值不能被改变，例如整数、字符串、元组。改变变量的值其实是指向另一个新对象。

- **可变对象（mutable objects）**  
  其值可以改动，例如列表、字典、集合、自定义类实例。

---

### 六、对象的内存和引用机制

- Python中的变量是**对象的引用**，变量赋值是绑定引用关系，并不复制对象。

```python
a = [1, 2, 3]
b = a       # b和a引用同一个列表对象
b.append(4)
print(a)    # 输出：[1, 2, 3, 4]
```

- 当没有引用指向某对象时，该对象会被垃圾回收（自动释放内存）。

---

### 七、对象的属性和方法

- **属性**：对象关联的数据，如实例属性  
- **方法**：对象可调用的函数，用来操作数据或实现行为。

示例：

```python
class Dog:
    def __init__(self, name):
        self.name = name

    def bark(self):
        print(f"{self.name} 叫了一声！")

d = Dog("小白")
print(d.name)  # 属性访问
d.bark()       # 调用方法
```

---

### 八、内置函数与对象

- `isinstance(obj, Class)` 判断对象是否是某类或其子类的实例。
- `hasattr(obj, 'attr')` 判断对象是否有指定属性。
- `getattr(obj, 'attr')` 获取属性。
- `setattr(obj, 'attr', value)` 设置属性。
- `dir(obj)` 查看对象拥有的属性和方法列表。

示例：

```python
print(isinstance(d, Dog))       # True
print(hasattr(d, 'bark'))       # True
print(getattr(d, 'name'))       # 小白
setattr(d, 'color', '白色')     # 动态添加属性
print(d.color)                  # 白色
```

---

### 九、总结

- Python中的对象是数据与行为的载体，是程序运行的基本实体。
- 对象拥有身份（内存地址）、类型和值。
- 变量是对象的引用，Python通过引用机制管理对象。
- 所有类型都是对象，包括原始数据类型和用户自定义类型。
- 对象可以有属性和方法，封装了数据与操作。
- 理解对象是理解Python程序设计、内存管理、函数和类的关键。

---



## 类

---

### 一、类的定义和本质

#### 1. 什么是类？

类是面向对象编程（OOP）中的核心概念，简单来说，**类是创建对象的模板或蓝图**。它定义了一组属性（变量）和方法（函数），这些属性和方法描述了一类事物的特点（数据）和行为（功能）。

举例：  
- “人”可以是一个类，它包含姓名、年龄等属性，走路、说话等方法。  
- “车”是另一个类，包含品牌、颜色、速度属性，启动、加速方法。

#### 2. 类的本质

在Python中，类本质上是一个对象——**类本身也是一个对象**，这个对象叫做“类对象”，用来创建其实例对象。

---

### 二、Python中如何定义类？

#### 语法格式

```python
class ClassName:
    """类的文档字符串（可选）"""
    # 属性和方法定义
```

示例：

```python
class Person:
    """表示一个人的简单类"""

    def __init__(self, name, age):
        # 构造方法，初始化实例属性
        self.name = name
        self.age = age

    def introduce(self):
        # 实例方法
        print(f"我是{self.name}，今年{self.age}岁。")
```

---

### 三、类的组成部分

#### 1. 类名

- 通常用大写字母开头的驼峰命名法（PascalCase），比如`Person`、`Car`。

#### 2. 类属性（类变量）

- 属于类对象的属性，所有实例对象共享。

```python
class Dog:
    species = "Canis familiaris"  # 类属性，所有Dog实例共享
```

#### 3. 实例属性（实例变量）

- 属于实例（对象）的变量，每个对象有自己的值。

```python
def __init__(self, name):
    self.name = name
```

#### 4. 方法（Method）

- 定义在类内部的函数，用来实现行为和功能。方法第一个参数约定是`self`，它代表调用该方法的实例。

---

### 四、创建对象（实例）

类定义完后，可以通过调用类名创建对象。

```python
p1 = Person("Alice", 30)
p2 = Person("Bob", 25)

p1.introduce()  # 输出：我是Alice，今年30岁。
p2.introduce()  # 输出：我是Bob，今年25岁。
```

这里的`p1`和`p2`就是`Person`类的实例。

---

### 五、详细解析关键部分

#### 1. `__init__`方法（构造函数）

- 当创建实例时自动调用，用于初始化实例的属性。相当于“构造器”。

- 参数`self`表示当前实例本身，“self”是Python的约定，但不是关键字，可以换名称，不推荐更改。

```python
def __init__(self, name, age):
    self.name = name
    self.age = age
```

#### 2. `self`参数

- 表示当前对象的引用，Python中定义实例方法时必须有`self`作为第一个参数，调用时由Python自动传入。

- 通过`self`访问实例属性和其他方法。

---

### 六、类属性与实例属性区别

```python
class Cat:
    species = "Felis catus"  # 类属性，所有实例共享

    def __init__(self, name):
        self.name = name     # 实例属性，实例独有
```

示例：

```python
c1 = Cat("Mimi")
c2 = Cat("Titi")

print(c1.species)  # Felis catus
print(c2.species)  # Felis catus

Cat.species = "New Species"

print(c1.species)  # New Species
```

类属性属于类，修改会影响所有实例；实例属性属于每个对象，互相独立。

---

### 七、类的内置属性和方法

Python的类有一些特殊的内置属性和方法，比如：

- `__dict__`：查看类或实例的属性字典
- `__doc__`：类的文档字符串
- `__module__`：类定义所在模块
- `__class__`：对象所属的类

示例：

```python
print(Person.__doc__)
print(p1.__class__)
print(p1.__dict__)
```

---

### 八、类的继承与扩展（简单介绍）

类可以通过继承扩展已有类，创建子类获得父类的属性和方法。

```python
class Student(Person):
    def __init__(self, name, age, student_id):
        super().__init__(name, age)  # 调用父类构造器
        self.student_id = student_id

    def introduce(self):
        super().introduce()
        print(f"我的学号是{self.student_id}")
```

---

### 九、类的作用和优点总结

- **抽象现实世界事物**：将相关数据和行为封装成逻辑上的对象。
- **实现封装**：隐藏内部实现细节，外部通过接口访问。
- **支持继承与复用**：减少代码冗余，提高可维护性。
- **方便组织大型程序**：面向对象的方法有助于结构化复杂程序。

---

### 十、完整示例

```python
class Car:
    wheels = 4  # 类属性

    def __init__(self, make, model):
        self.make = make    # 实例属性
        self.model = model

    def display_info(self):
        print(f"这是{self.make}品牌的{self.model}，有{Car.wheels}个轮子。")

car1 = Car("丰田", "凯美瑞")
car2 = Car("特斯拉", "Model S")

car1.display_info()  # 输出：这是丰田品牌的凯美瑞，有4个轮子。
car2.display_info()  # 输出：这是特斯拉品牌的Model S，有4个轮子。
```

---

## 封装、继承、多态

好的！下面我将详细讲解Python中面向对象编程的三个关键特性：**封装（Encapsulation）**、**继承（Inheritance）**和**多态（Polymorphism）**，包括它们的概念、实现方式以及示例。

---

### 一、封装（Encapsulation）

#### 1. 概念

封装是面向对象的基本原则之一，指**将对象的属性和方法封装在类的内部，隐藏实现细节，只暴露必要的接口给外部使用**。封装可以提高程序的安全性和易维护性，防止外部随意修改对象的内部状态。

用一句话说：**数据和操作数据的方法绑定在一起，对外隐藏内部细节。**

---

#### 2. Python中如何实现封装？

Python没有像Java或C++一样的访问修饰符（`private`、`public`、`protected`），但有约定俗成的命名规则用来实现“封装”和“访问控制”：

| 访问级别            | 命名方式       | 是否可由外部访问             | 说明                     |
| ------------------- | -------------- | ---------------------------- | ------------------------ |
| 公开属性/方法       | 变量名直接写   | 可以随意访问                 | 默认就是公开的           |
| 受保护（protected） | 单下划线_开头  | 可以访问，但建议不直接访问   | 表示内部使用，子类可访问 |
| 私有（private）     | 双下划线__开头 | 不可直接外部访问（名称重整） | 伪私有，真正私有不存在   |

---

#### 3. 例子

```python
class Person:
    def __init__(self, name, age):
        self.name = name          # 公开属性
        self._gender = "未知"      # 受保护属性（约定）
        self.__age = age          # 私有属性，外部不能直接访问
    
    def get_age(self):           # 公开方法，访问私有属性
        return self.__age
    
    def set_age(self, age):      # 公开方法，设置私有属性
        if age > 0:
            self.__age = age
        else:
            print("非法年龄")

p = Person("Alice", 20)

print(p.name)       # 公开，访问正常
print(p._gender)    # 受保护，虽然能访问，不推荐
# print(p.__age)    # 报错，私有属性不能直接访问

print(p.get_age())  # 通过公开方法访问私有属性
p.set_age(25)       # 修改私有属性
print(p.get_age())
```

**注意：** Python的私有属性通过名称重整实现，`__age`会被改成`_Person__age`，通过`p._Person__age`也能访问，但不推荐！

---

### 二、继承（Inheritance）

#### 1. 概念

继承是面向对象的重要机制，指**一个类（子类）可以继承另一个类（父类）的属性和方法，获得父类的功能，并且可以扩展和重写**。实现代码复用，增强可扩展性。

---

#### 2. Python继承语法

```python
class 父类名:
    pass

class 子类名(父类名):
    pass
```

---

#### 3. 例子

```python
class Animal:
    def eat(self):
        print("动物会吃东西")

class Dog(Animal):        # Dog继承自Animal
    def bark(self):
        print("汪汪叫")

dog = Dog()
dog.eat()      # 继承自Animal
dog.bark()     # Dog自己的方法
```

---

#### 4. 重写（Override）

子类可以重写父类的方法，实现不同的行为。

```python
class Cat(Animal):
    def eat(self):
        print("猫吃鱼")

cat = Cat()
cat.eat()     # 输出：猫吃鱼 （重写了父类eat）
```

---

#### 5. 使用`super()`调用父类方法

有时子类想在重写方法时调用父类方法，可以用`super()`：

```python
class Bird(Animal):
    def eat(self):
        super().eat()  # 调用父类eat
        print("鸟喜欢吃虫子")

bird = Bird()
bird.eat()
# 输出：
# 动物会吃东西
# 鸟喜欢吃虫子
```

---

### 三、多态（Polymorphism）

#### 1. 概念

多态指**不同类的实例可以通过相同的接口调用各自不同的实现，从而表现出不同的行为**。多态提高了程序的灵活性和扩展性。

一句话总结：**同一操作作用于不同的对象，可以产生不同的效果。**

---

#### 2. Python中的多态体现

因为Python是动态类型语言，只要不同类有同名方法，就可以统一调用，体现多态。

---

#### 3. 例子（鸭子类型）

```python
class Dog:
    def speak(self):
        print("汪汪叫")

class Cat:
    def speak(self):
        print("喵喵叫")

def animal_speak(animal):
    animal.speak()  # 不关注animal具体是什么类，只要有speak方法即可

d = Dog()
c = Cat()

animal_speak(d)  # 汪汪叫
animal_speak(c)  # 喵喵叫
```

多态体现在**统一接口，不同实现**。

---

### 四、示例总结

```python
class Animal:
    def __init__(self, name):
        self.name = name

    def speak(self):
        print(f"{self.name}在发出声音")

class Dog(Animal):
    def speak(self):
        print(f"{self.name}汪汪叫")

class Cat(Animal):
    def speak(self):
        print(f"{self.name}喵喵叫")

animals = [Dog("小白"), Cat("小花")]

for animal in animals:
    animal.speak()   # 多态，根据对象不同调用不同版本的方法
```

---

### 五、总结

| 特性 | 含义                               | Python实现方式                | 作用                                     |
| ---- | ---------------------------------- | ----------------------------- | ---------------------------------------- |
| 封装 | 隐藏内部数据，限制外部访问         | 通过单下划线`_`和双下划线`__` | 防止数据被随意修改，提高安全性和可维护性 |
| 继承 | 子类继承父类属性和方法，复用和扩展 | 类定义时声明继承关系          | 代码复用，实现类之间的层次结构           |
| 多态 | 不同类对象对相同接口的响应不同     | 动态绑定、统一接口调用        | 提高程序灵活性，使程序可扩展与维护       |

---

## 类定义中的特殊方法

好的，下面我为你详细介绍Python类定义中的**特殊方法（Magic Methods / Dunder Methods）**。这些方法是Python面向对象编程的重要特性，能够让你定制类的行为，使你的类表现得像内置类型一样灵活。

---

### 一、什么是特殊方法？

- 以双下划线`__`开头和结尾的方法，俗称“魔法方法”（magic methods）或“dunder方法”（double underscore methods）。
- 由Python在特定情况下自动调用，不需要手动调用。
- 它们定义了对象的基本行为，比如创建实例、打印、算术运算、比较、容器行为等。

---

### 二、常见特殊方法分类及介绍

| 作用类型   | 常用特殊方法                                | 说明                                       |
| ---------- | ------------------------------------------- | ------------------------------------------ |
| 实例初始化 | `__init__(self, ...)`                       | 构造函数，实例化对象时调用，用于初始化     |
| 实例创建   | `__new__(cls, ...)`                         | 创建实例，生成对象时调用，通常不需重写     |
| 字符串表示 | `__str__(self)`                             | 定义print()或str()时返回的字符串，面向用户 |
|            | `__repr__(self)`                            | 定义repr()返回值，面向开发者，调试用       |
| 运算符重载 | `__add__(self, other)`                      | `+` 运算符实现                             |
|            | `__sub__(self, other)`                      | `-` 运算符实现                             |
|            | `__mul__(self, other)`                      | `*` 运算符实现                             |
|            | `__truediv__(self, other)`                  | `/` 运算符实现                             |
|            | `__floordiv__(self, other)`                 | `//` 运算符实现                            |
|            | `__mod__(self, other)`                      | `%` 取模运算                               |
|            | `__pow__(self, other)`                      | `**` 幂运算                                |
| 比较运算符 | `__eq__(self, other)`                       | `==` 判断                                  |
|            | `__ne__(self, other)`                       | `!=` 判断                                  |
|            | `__lt__(self, other)`                       | `<` 判断                                   |
|            | `__le__(self, other)`                       | `<=` 判断                                  |
|            | `__gt__(self, other)`                       | `>` 判断                                   |
|            | `__ge__(self, other)`                       | `>=` 判断                                  |
| 属性访问   | `__getattr__(self, name)`                   | 访问不存在的属性时调用                     |
|            | `__setattr__(self, name, val)`              | 设置属性时调用                             |
|            | `__delattr__(self, name)`                   | 删除属性时调用                             |
| 容器类型   | `__len__(self)`                             | `len()` 内置函数调用                       |
|            | `__getitem__(self, key)`                    | 通过索引访问元素                           |
|            | `__setitem__(self, key, val)`               | 通过索引设置元素                           |
|            | `__delitem__(self, key)`                    | 删除指定元素                               |
| 可调用对象 | `__call__(self, ...)`                       | 使对象可调用（像函数一样）                 |
| 上下文管理 | `__enter__(self)`                           | `with`语句开始时调用                       |
|            | `__exit__(self, exc_type, exc_val, exc_tb)` | `with`语句结束时调用                       |
| 对象销毁   | `__del__(self)`                             | 对象销毁时调用（类似析构函数）             |

---

### 三、详细讲解几个常用特殊方法

#### 1. `__init__(self, ...)`

初始化方法，实例创建后自动调用，一般用来设置对象的初始状态。

```python
class Person:
    def __init__(self, name, age):
        self.name = name
        self.age = age
```

#### 2. `__str__(self)`

返回一个用户友好的字符串表示，用在`print()`或`str()`时。

```python
def __str__(self):
    return f"Person({self.name}, {self.age})"

p = Person("Alice", 30)
print(p)  # 输出：Person(Alice, 30)
```

#### 3. `__repr__(self)`

返回对象的“官方”字符串表示，通常可以用该字符串重新创建对象，面向调试者。

```python
def __repr__(self):
    return f"Person('{self.name}', {self.age})"

repr(p)  # 输出："Person('Alice', 30)"
```

一般最好让`__repr__`和`__str__`的内容不同，`__repr__`更详细。

#### 4. 运算符重载（以`__add__`为例）

允许对象使用`+`操作符：

```python
class Vector:
    def __init__(self, x, y):
        self.x = x
        self.y = y

    def __add__(self, other):
        return Vector(self.x + other.x, self.y + other.y)

    def __repr__(self):
        return f"Vector({self.x}, {self.y})"

v1 = Vector(1, 2)
v2 = Vector(3, 4)
print(v1 + v2)  # Vector(4, 6)
```

#### 5. `__len__(self)`

使对象能通过内置函数`len()`调用。

```python
class MyList:
    def __init__(self, data):
        self.data = data

    def __len__(self):
        return len(self.data)

lst = MyList([1, 2, 3])
print(len(lst))  # 3
```

#### 6. `__getitem__`、`__setitem__` 与 `__delitem__`

实现对象的下标操作，对象行为像列表或字典一样。

```python
class MyList:
    def __init__(self):
        self.data = []

    def __getitem__(self, index):
        return self.data[index]

    def __setitem__(self, index, value):
        self.data[index] = value

    def __delitem__(self, index):
        del self.data[index]

    def append(self, value):
        self.data.append(value)

lst = MyList()
lst.append(10)
lst.append(20)
print(lst[1])  # 20
lst[1] = 30
print(lst[1])  # 30
del lst[0]
print(lst[0])  # 30
```

#### 7. `__call__(self, ...)`

让对象成为可调用对象，像函数一样使用。

```python
class Adder:
    def __init__(self, n):
        self.n = n

    def __call__(self, x):
        return self.n + x

add5 = Adder(5)
print(add5(10))  # 15
```

#### 8. `__enter__` 和 `__exit__`

支持上下文管理器协议，让对象支持`with`语句。

```python
class MyContext:
    def __enter__(self):
        print("进入上下文")
        return self

    def __exit__(self, exc_type, exc_val, exc_tb):
        print("退出上下文")

with MyContext():
    print("执行代码块")
```

输出：
```
进入上下文
执行代码块
退出上下文
```

---

### 四、重点提醒

- 你不需要实现所有特殊方法，只要根据你类的需求实现部分即可。
- 适当实现特殊方法可以让你的类表现得像Python内置类型一样，自然优雅，代码更简洁。
- 避免滥用特殊方法，否则可能降低代码可读性。

---

### 五、总结

| 特殊方法名    | 作用                       | 调用时机/场景              |
| ------------- | -------------------------- | -------------------------- |
| `__init__`    | 初始化实例                 | 创建实例时自动调用         |
| `__str__`     | 返回用户友好的字符串表示   | print() 或 str() 调用时    |
| `__repr__`    | 返回开发者友好的字符串表示 | repr() 调用，调试时打印    |
| `__add__`     | 实现`+`运算符              | 使用`+`操作符时自动调用    |
| `__len__`     | 实现内置`len()`函数        | 调用len()时自动调用        |
| `__getitem__` | 支持下标访问               | 对象使用索引访问时自动调用 |
| `__setitem__` | 支持通过下标设置值         | 对象使用索引赋值时自动调用 |
| `__call__`    | 使对象可调用               | 对象像函数调用时自动调用   |
| `__enter__`   | 上下文管理器进入           | with语句块开始时调用       |
| `__exit__`    | 上下文管理器退出           | with语句块结束时调用       |

---

### 构造与结构

详细介绍一下Python中的**构造（Construction）和解构（Destruction）**，也就是类实例的创建与销毁过程，以及对应涉及的特殊方法和机制。

---

#### 一、概念简介

- **构造（Construction）**：指**创建并初始化一个对象实例的过程**。
- **解构（Destruction）**：指**对象生命周期结束后，释放资源和清理的过程**。

Python中，构造和解构对应两个特殊方法：

| 操作   | 方法名                | 作用                           |
| ------ | --------------------- | ------------------------------ |
| 构造   | `__new__(cls, ...)`   | 创建新实例并返回实例对象       |
| 初始化 | `__init__(self, ...)` | 对实例进行初始化，设置初始状态 |
| 解构   | `__del__(self)`       | 对象销毁时调用，进行清理工作   |

---

#### 二、构造过程详解

---

##### 1. `__new__` 方法

- **定义：** `__new__(cls, ...)` 是一个静态方法，用于实际创建对象实例。
- **调用时机：** 当调用 `MyClass()` 时，Python首先调用`__new__`来创建实例。
- **返回值：** 必须返回一个实例对象，通常是调用父类`object.__new__(cls)`得到。
- **一般使用场景：** 很少需要重写它，除非需要控制实例创建行为（如单例模式、元类等）。

示例：

```python
class MyClass:
    def __new__(cls, *args):
        print("调用__new__创建实例")
        instance = super().__new__(cls)  # 调用父类的__new__
        return instance

    def __init__(self, x):
        print("调用__init__初始化实例")
        self.x = x

obj = MyClass(10)
# 输出：
# 调用__new__创建实例
# 调用__init__初始化实例
```

注意：
- `__new__`是先于`__init__`执行的；
- 如果`__new__`没有返回实例，`__init__`不会被调用。

---

##### 2. `__init__` 方法

- **定义：** `__init__(self, ...)` 是实例初始化函数。
- **调用时机：** 在`__new__`成功创建实例后被自动调用；
- **作用：** 设置实例的初始属性、初始化状态，为对象“做准备”。

示例（续上）：

```python
def __init__(self, x):
    self.x = x
```

---

##### 3. 构造完整流程总结

当写`obj = MyClass(10)`时：

1. Python调用`MyClass.__new__(MyClass, 10)`，创建实例。
2. 如果`__new__`返回实例对象，Python接着调用`MyClass.__init__(obj, 10)`进行初始化。
3. 返回初始化好的实例对象。

---

#### 三、解构过程详解

---

##### 1. `__del__` 方法

- **定义：** `__del__(self)` 是析构函数，**对象销毁（被垃圾回收）前调用**。
- **作用：** 释放对象持有的资源，比如关闭文件、网络连接，清理缓存等。
- **注意：** 不保证立即调用，甚至有可能不给调用（循环引用时），因此不应依赖于`__del__`进行关键资源释放。

示例：

```python
class MyClass:
    def __del__(self):
        print(f"实例 {self} 被销毁")

obj = MyClass()
del obj  # 手动删除对象，会调用__del__
```

---

##### 2. Python垃圾回收机制和`__del__`

- Python使用**引用计数（Reference Counting）**和**垃圾回收（GC）**机制管理内存。
- 当对象引用计数变为0时，自动调用`__del__`（若定义了）。
- **循环引用**可能导致`__del__`不被调用，因为引用计数不会降为0，需要GC周期检测清理。
- 因此，**不可依赖`__del__`进行及时的资源释放**，资源管理建议用`with`语句和上下文管理器（`__enter__`、`__exit__`方法）。

---

#### 四、构造与解构的实际应用示例

```python
class FileWrapper:
    def __init__(self, filename):
        print("打开文件")
        self.file = open(filename, 'w')

    def write(self, content):
        self.file.write(content)

    def __del__(self):
        print("关闭文件")
        self.file.close()

fw = FileWrapper('test.txt')
fw.write("Hello, World!")
del fw  # 调用__del__关闭文件
```

**改进：用上下文管理器替代`__del__`保证及时释放**

```python
class FileWrapper:
    def __init__(self, filename):
        self.file = open(filename, 'w')

    def write(self, content):
        self.file.write(content)

    def __enter__(self):
        return self

    def __exit__(self, exc_type, exc_val, exc_tb):
        self.file.close()

with FileWrapper('test.txt') as fw:
    fw.write("Hello, World!")
# with块结束时自动关闭文件，安全可靠
```

---

#### 五、总结

| 方法名     | 说明           | 备注                               |
| ---------- | -------------- | ---------------------------------- |
| `__new__`  | 创建对象实例   | 很少手动重写，涉及底层控制         |
| `__init__` | 初始化实例属性 | 常用来设定对象初始状态             |
| `__del__`  | 对象销毁时调用 | 不保证及时调用，不推荐依赖释放资源 |

- **构造**负责生成和初始化对象。
- **解构**负责对象生命周期结束时清理资源。
- 资源管理在Python中推荐用**上下文管理**（`with`）代替`__del__`。

---

### 算数运算

好的，下面我详细讲解Python语言中**对象的算术运算**，包括如何通过**魔术方法（特殊方法）**支持和定制各种算术运算符，使自定义对象能够像内置数字类型一样参与算术运算。

---

#### 一、基础概念

- Python中的算术运算符（`+`, `-`, `*`, `/` 等）背后，本质是调用了对象的**对应魔术方法**。
- 这些特殊方法的名字通常是以`__`开头和结尾，例如`__add__`对应`+`，`__sub__`对应`-`。
- 通过重载这些魔术方法，自定义类的实例可以进行算术运算，支持灵活的操作。

---

#### 二、Python中对应的算术运算魔术方法

| 运算符      | 魔术方法名                  | 说明                 |
| ----------- | --------------------------- | -------------------- |
| `+`         | `__add__(self, other)`      | 加法                 |
| `-`         | `__sub__(self, other)`      | 减法                 |
| `*`         | `__mul__(self, other)`      | 乘法                 |
| `/`         | `__truediv__(self, other)`  | 真除法（浮点除法）   |
| `//`        | `__floordiv__(self, other)` | 整除                 |
| `%`         | `__mod__(self, other)`      | 取模                 |
| `**`        | `__pow__(self, other)`      | 幂运算               |
| `-`（单目） | `__neg__(self)`             | 取反/负号            |
| `+`（单目） | `__pos__(self)`             | 正号（通常返回自身） |
| `abs()`     | `__abs__(self)`             | 绝对值               |

---

#### 三、反向算术运算方法（右侧操作）

当左侧对象没有实现对应方法，或者返回`NotImplemented`时，Python会自动尝试调用右侧对象的反向方法：

| 运算符 | 反向魔术方法名               | 说明       |
| ------ | ---------------------------- | ---------- |
| `+`    | `__radd__(self, other)`      | 右侧加法   |
| `-`    | `__rsub__(self, other)`      | 右侧减法   |
| `*`    | `__rmul__(self, other)`      | 右侧乘法   |
| `/`    | `__rtruediv__(self, other)`  | 右侧真除法 |
| `//`   | `__rfloordiv__(self, other)` | 右侧整除   |
| `%`    | `__rmod__(self, other)`      | 右侧取模   |
| `**`   | `__rpow__(self, other)`      | 右侧幂运算 |

---

#### 四、就地累加运算符（复合赋值）

复合赋值符`+=`, `-=`, `*=`, `/=`, 等调用**对应的就地方法**：

| 运算符 | 就地运算方法                 | 说明       |
| ------ | ---------------------------- | ---------- |
| `+=`   | `__iadd__(self, other)`      | 就地加法   |
| `-=`   | `__isub__(self, other)`      | 就地减法   |
| `*=`   | `__imul__(self, other)`      | 就地乘法   |
| `/=`   | `__itruediv__(self, other)`  | 就地真除   |
| `//=`  | `__ifloordiv__(self, other)` | 就地整除   |
| `%=`   | `__imod__(self, other)`      | 就地取模   |
| `**=`  | `__ipow__(self, other)`      | 就地幂运算 |

注意：若未实现`__iXXX__`方法，Python会自动退回去调用普通的`__XXX__`方法然后赋值。

---

#### 五、示例代码

以下示例实现了一个简单的二维向量类，支持加减乘法和反向加法。

```python
class Vector2D:
    def __init__(self, x, y):
        self.x = x
        self.y = y

    def __add__(self, other):
        if isinstance(other, Vector2D):
            return Vector2D(self.x + other.x, self.y + other.y)
        elif isinstance(other, (int, float)):
            return Vector2D(self.x + other, self.y + other)
        return NotImplemented

    def __radd__(self, other):
        # 右侧加法支持数字 + Vector2D
        return self.__add__(other)

    def __sub__(self, other):
        if isinstance(other, Vector2D):
            return Vector2D(self.x - other.x, self.y - other.y)
        return NotImplemented

    def __mul__(self, scalar):
        if isinstance(scalar, (int, float)):
            return Vector2D(self.x * scalar, self.y * scalar)
        return NotImplemented

    def __rmul__(self, scalar):
        # 支持数字 * Vector2D
        return self.__mul__(scalar)

    def __repr__(self):
        return f"Vector2D({self.x}, {self.y})"

v1 = Vector2D(1, 2)
v2 = Vector2D(3, 4)

print(v1 + v2)      # Vector2D(4, 6)
print(v1 + 10)      # Vector2D(11, 12)
print(10 + v1)      # Vector2D(11, 12)
print(v1 * 3)       # Vector2D(3, 6)
print(3 * v1)       # Vector2D(3, 6)
print(v2 - v1)      # Vector2D(2, 2)
```

---

#### 六、其他算术相关魔术方法简单说明

- `__truediv__(self, other)` ：`/`  
- `__floordiv__(self, other)` ：`//`  
- `__mod__(self, other)` ：取模 `%`  
- `__pow__(self, other)` ：幂运算 `**`  
- `__neg__(self)` ：一元 `-`，取负  
- `__pos__(self)` ：一元 `+`，返回自身或其他含义  
- `__abs__(self)` ：绝对值 `abs()`  

---

#### 七、总结

- Python对象的算术运算均通过重载对应的魔术方法实现。
- 可以支持和扩展内置类型不支持的运算。
- 支持反向运算和就地运算符，实现更灵活的操作。
- 实现这些方法能让自定义类“像数字”一样参与数学运算。

---

#### 八、例子

---

##### 例子1：二维向量类（实现加法和减法）

```python
class Vector2D:
    def __init__(self, x, y):
        self.x = x
        self.y = y

    def __add__(self, other):
        if isinstance(other, Vector2D):
            return Vector2D(self.x + other.x, self.y + other.y)
        return NotImplemented

    def __sub__(self, other):
        if isinstance(other, Vector2D):
            return Vector2D(self.x - other.x, self.y - other.y)
        return NotImplemented

    def __repr__(self):
        return f"Vector2D({self.x}, {self.y})"

v1 = Vector2D(1, 2)
v2 = Vector2D(3, 5)
print(v1 + v2)  # Vector2D(4, 7)
print(v2 - v1)  # Vector2D(2, 3)
```

---

##### 例子2：实现乘法和反向乘法（与数字相乘）

```python
class Vector2D:
    def __init__(self, x, y):
        self.x = x
        self.y = y

    def __mul__(self, other):
        if isinstance(other, (int, float)):
            return Vector2D(self.x * other, self.y * other)
        return NotImplemented

    def __rmul__(self, other):
        return self.__mul__(other)

    def __repr__(self):
        return f"Vector2D({self.x}, {self.y})"

v = Vector2D(2, 3)
print(v * 4)  # Vector2D(8, 12)
print(4 * v)  # Vector2D(8, 12)
```

---

##### 例子3：实现除法和取模

```python
class NumberWrapper:
    def __init__(self, value):
        self.value = value

    def __truediv__(self, other):
        if isinstance(other, (int, float)):
            return NumberWrapper(self.value / other)
        return NotImplemented

    def __mod__(self, other):
        if isinstance(other, (int, float)):
            return NumberWrapper(self.value % other)
        return NotImplemented

    def __repr__(self):
        return f"NumberWrapper({self.value})"

n = NumberWrapper(10)
print(n / 3)  # NumberWrapper(3.3333333333333335)
print(n % 3)  # NumberWrapper(1)
```

---

##### 例子4：实现幂运算(`**`)和负号(`-`)

```python
class NumberWrapper:
    def __init__(self, value):
        self.value = value

    def __pow__(self, exponent):
        if isinstance(exponent, (int, float)):
            return NumberWrapper(self.value ** exponent)
        return NotImplemented

    def __neg__(self):
        return NumberWrapper(-self.value)

    def __repr__(self):
        return f"NumberWrapper({self.value})"

n = NumberWrapper(2)
print(n ** 3)   # NumberWrapper(8)
print(-n)       # NumberWrapper(-2)
```

---

##### 例子5：实现复合赋值操作（就地加法）

```python
class Counter:
    def __init__(self, count=0):
        self.count = count

    def __iadd__(self, other):
        if isinstance(other, int):
            self.count += other
            return self
        return NotImplemented

    def __repr__(self):
        return f"Counter({self.count})"

c = Counter(10)
c += 5
print(c)  # Counter(15)
```

---

以上示例展示了算术相关的核心魔术方法：

- `__add__`、`__sub__`、`__mul__`、`__truediv__`、`__mod__`、`__pow__`  
- 对应反向操作的`__radd__`、`__rmul__`等  
- 单目操作`__neg__`，代表负号  
- 就地运算`__iadd__`等

通过实现这些方法，自定义类的实例可以像数字一样直接用算术符操作，非常方便。

---

## 封装详解

---

### 一、什么是封装？

封装是面向对象编程（OOP）的核心原则之一，指将数据（属性）和操作数据的方法（函数）绑定在一起，**隐藏对象的内部实现细节**，只暴露必要的接口供外部访问和操作。

通俗来说，封装让对象的内部状态对外部是“隐藏”的，保护数据不被外部随意修改，提高安全性和代码的可维护性。

---

### 二、Python中的封装实现方式

Python不像Java或C++有严格的访问修饰符`private`、`protected`、`public`，而是通过**命名约定和魔术方法**实现封装。

| 访问权限类型 | 标识符命名       | 访问权限说明                               |
| ------------ | ---------------- | ------------------------------------------ |
| 公开成员     | 直接命名         | 可被外部直接访问和修改                     |
| 受保护成员   | 单下划线`_`开头  | 建议内部使用，外部可访问但不推荐操作       |
| 私有成员     | 双下划线`__`开头 | 名称重整，不可直接外部访问，实现伪私有机制 |

---

### 三、示例与说明

```python
class Person:
    def __init__(self, name, age):
        self.name = name       # 公开属性
        self._gender = "未知"   # 受保护属性（约定俗成）
        self.__age = age        # 私有属性（名称重整）

    def get_age(self):
        return self.__age

    def set_age(self, age):
        if 0 < age < 120:
            self.__age = age
        else:
            print("非法年龄")

p = Person("Alice", 30)

print(p.name)        # 公开属性，正常访问
print(p._gender)     # 受保护属性，虽然能访问，但不建议外部使用

# print(p.__age)     # 报错，私有属性不可直接访问

print(p.get_age())   # 通过公开方法访问私有属性
p.set_age(35)
print(p.get_age())
```

**说明：**

- 双下划线`__age`在内部会被重命名为`_Person__age`，使用`p._Person__age`也能访问，但不建议这样做。
- 使用**getter/setter方法**（访问器和修改器）来控制属性访问是常见封装方式。

---

### 四、属性封装的另一种方式：使用`property`

Python提供了**`property`函数和`@property`装饰器**，让你可以像访问属性一样访问方法，实现更优雅的封装。

```python
class Person:
    def __init__(self, age):
        self._age = age   # 受保护变量

    @property
    def age(self):
        return self._age  # 访问器getter

    @age.setter
    def age(self, value):
        if 0 < value < 120:
            self._age = value
        else:
            raise ValueError("非法年龄")

p = Person(30)
print(p.age)    # 调用getter
p.age = 35      # 调用setter
print(p.age)
# p.age = -5    # 触发异常
```

---

### 五、封装带来的好处

1. **数据保护**：防止对象的状态被非法修改或破坏。
2. **接口简化**：隐藏内部复杂实现，仅暴露必要操作，提高代码接口清晰度。
3. **可维护性强**：实现细节改变不影响使用者，只要接口不变。
4. **实现控制**：可以控制对属性访问，比如添加权限验证和逻辑校验。

---

### 六、私有成员与名称重整

直接访问私有属性会失败：

```python
print(p.__age)  # AttributeError
```

这是因为Python在后台对双下划线开头的属性进行了名称重整：

属性名`__age`被改写为`_Person__age`，确保外部无法轻易访问。

```python
print(p._Person__age)  # 30，强制访问，但不建议
```

---

### 七、封装总结

| 封装方式          | 实现手段                      | 说明                                 |
| ----------------- | ----------------------------- | ------------------------------------ |
| 公开成员          | 直接命名                      | 可自由访问                           |
| 受保护成员        | `_single_underscore`          | 约定内部使用，外部可访问但应避免使用 |
| 私有成员          | `__double_underscore`         | 名称重整，伪“私有”，防止外部访问     |
| 通过getter/setter | 使用普通方法或@property装饰器 | 优雅封装，实现访问控制和数据校验     |

---



## 继承详解

---

### 一、什么是继承？

继承是面向对象编程（OOP）的核心特性之一，指**子类继承父类的属性和方法**，获得父类的功能，同时可以扩展新的功能或者重写父类已有的方法。

通过继承，可以实现代码复用，方便构建类的层次结构，提高程序的模块化和可维护性。

---

### 二、Python中继承的基本语法

```python
class 父类名:
    # 父类属性和方法

class 子类名(父类名):
    # 子类新增或重写的属性和方法
```

---

#### 示例：

```python
# 父类
class Animal:
    def __init__(self, name):
        self.name = name

    def speak(self):
        print(f"{self.name} 正在发出声音")

# 子类继承Animal
class Dog(Animal):
    def speak(self):
        print(f"{self.name} 叫：汪汪汪")

dog = Dog("小白")
dog.speak()  # 输出：小白 叫：汪汪汪
```

---

### 三、继承的特点和用法

#### 1. 子类会自动获得父类的属性和方法

子类可以直接使用父类中定义的属性和方法，无需重复定义。

```python
class Bird(Animal):
    pass

bird = Bird("小鸟")
bird.speak()  # 调用父类Animal的方法，输出“小鸟 正在发出声音”
```

#### 2. 子类可以重写父类的方法（方法重写）

子类定义了与父类同名的方法，会覆盖掉父类的方法，调用的是子类的方法。

```python
class Cat(Animal):
    def speak(self):
        print(f"{self.name} 叫：喵喵喵")

cat = Cat("小花")
cat.speak()  # 小花 叫：喵喵喵
```

#### 3. 使用`super()`调用父类方法

子类在重写父类方法时，仍想调用父类的方法，可以使用`super()`。

```python
class Bird(Animal):
    def speak(self):
        super().speak()  # 调用父类的方法
        print(f"{self.name} 正在唱歌")

bird = Bird("小鸟")
bird.speak()
# 输出：
# 小鸟 正在发出声音
# 小鸟 正在唱歌
```

---

### 四、多重继承

Python支持多继承，一个子类可以继承多个父类：

```python
class Flyable:
    def fly(self):
        print("能飞")

class Swimmable:
    def swim(self):
        print("能游泳")

class Duck(Animal, Flyable, Swimmable):
    pass

duck = Duck("小鸭")
duck.fly()   # 能飞
duck.swim()  # 能游泳
duck.speak() # 继承自Animal，输出：小鸭 正在发出声音
```

---

### 五、继承中的方法解析顺序（MRO）

- Python采用**广度优先搜索（C3算法）**计算继承链的查找顺序，即方法解析顺序（Method Resolution Order，MRO）。
- 可以通过`类名.__mro__`或`help(类名)`查看。

示例：

```python
print(Duck.__mro__)
```

---

### 六、总结

| 继承特性      | 说明                                   |
| ------------- | -------------------------------------- |
| 继承          | 子类获得父类属性和方法，复用代码       |
| 方法重写      | 子类重写父类方法，改变行为             |
| `super()`调用 | 在子类中调用父类方法，复用父类逻辑     |
| 多重继承      | 支持同时继承多个类，具备多个父类的功能 |
| MRO           | 方法解析顺序，决定调用哪个类的方法     |

---

### 七、完整示例代码

```python
class Animal:
    def __init__(self, name):
        self.name = name

    def speak(self):
        print(f"{self.name} 正在发出声音")

class Dog(Animal):
    def speak(self):
        print(f"{self.name} 叫：汪汪汪")

    def fetch(self):
        print(f"{self.name} 正在取回投掷的东西")

dog = Dog("小黑")
dog.speak()  # 小黑 叫：汪汪汪
dog.fetch()  # 小黑 正在取回投掷的东西
```

---

## 多态详解

---

### 一、多态的概念

多态是面向对象编程（OOP）的重要特性之一，含义是：

> **同一操作作用于不同的对象，可以产生不同的行为。**

简而言之：**不同类的对象对同一方法调用表现出不同的行为。**

多态使程序更灵活、可扩展，能写出更通用、可复用的代码。

---

### 二、Python中的多态特点

- Python是动态类型语言，不需要显式声明接口或类型，只要对象实现了某个方法，就能调用（**鸭子类型**）。
- 多态通过**方法名一致**来实现，不同类实现相同方法名。
- 不依赖继承也能实现多态，但继承和多态结合更常见。

---

### 三、多态的实现方法

#### 1. 继承+方法重写

父类定义接口，子类重写，实现不同表现。

```python
class Animal:
    def speak(self):
        print("动物发出声音")

class Dog(Animal):
    def speak(self):
        print("汪汪叫")

class Cat(Animal):
    def speak(self):
        print("喵喵叫")

def animal_speak(animal):
    animal.speak()  # 调用传入对象的speak方法

dog = Dog()
cat = Cat()

animal_speak(dog)  # 汪汪叫
animal_speak(cat)  # 喵喵叫
```

函数`animal_speak`只关注`animal`对象有`speak`方法，不关心具体类型，这即是多态。

---

#### 2. 鸭子类型（Duck Typing）

Python不强制继承，只要对象有某个方法就可以调用。

```python
class Bird:
    def speak(self):
        print("叽叽喳喳")

class Robot:
    def speak(self):
        print("机器人声音")

def make_speak(entity):
    entity.speak()

b = Bird()
r = Robot()

make_speak(b)  # 叽叽喳喳
make_speak(r)  # 机器人声音
```

---

### 四、多态与抽象基类（ABC）

Python的`abc`模块支持定义抽象基类和抽象方法，借助多态强制子类实现接口。

```python
from abc import ABC, abstractmethod

class Animal(ABC):
    @abstractmethod
    def speak(self):
        pass

class Dog(Animal):
    def speak(self):
        print("汪汪叫")

dog = Dog()
dog.speak()
```

这样的类不能直接实例化，必须实现抽象方法。

---

### 五、多态优势

- **代码重用性好**：同一代码可用于不同对象。
- **扩展性强**：新增类无需修改调用代码。
- **维护方便**：降低代码耦合，符合开闭原则（对扩展开放，对修改关闭）。

---

### 六、综合示例

```python
class Shape:
    def area(self):
        raise NotImplementedError

class Rectangle(Shape):
    def __init__(self, w, h):
        self.w, self.h = w, h
    def area(self):
        return self.w * self.h

class Circle(Shape):
    def __init__(self, r):
        self.r = r
    def area(self):
        return 3.14159 * self.r ** 2

def print_area(shape):
    print(f"面积是: {shape.area()}")

r = Rectangle(3, 4)
c = Circle(5)

print_area(r)  # 面积是: 12
print_area(c)  # 面积是: 78.53975
```

---

### 七、总结

| 概念     | 说明                                                   |
| -------- | ------------------------------------------------------ |
| 多态     | 不同类对象对相同操作做出不同响应                       |
| 主要机制 | 方法名相同，不依赖类型，Python的“鸭子类型”本质体现多态 |
| 实现手段 | 继承和重写、鸭子类型、抽象基类等                       |
| 优点     | 程序灵活、易扩展、易维护                               |

---

## self

---

### 一、什么是 `self`？

- `self` 是实例方法的第一个参数，表示**调用该方法的对象本身**。
- 它类似于其他语言中的`this`指针，但必须显式声明。
- 在实例方法中通过`self`访问实例属性和其他方法。

---

### 二、为什么需要 `self`？

Python的方法定义是**函数定义**，把实例当作显式参数传入，因此需要一个变量名来代表这个实例。

例如：

```python
class Person:
    def say_hello(self):
        print("Hello!")

p = Person()
p.say_hello()
```

调用`p.say_hello()`时，Python会自动把`p`作为第一个参数传给方法，等价于`Person.say_hello(p)`。

---

### 三、`self`的作用

- 访问当前实例的属性和方法：

```python
class Person:
    def __init__(self, name):
        self.name = name  # 给实例绑定属性

    def say_hello(self):
        print(f"Hello, my name is {self.name}")

p = Person("Alice")
p.say_hello()  # 输出：Hello, my name is Alice
```

- 通过`self`维护实例自身状态。

---

### 四、`self`的命名规则

- 虽然约定俗成用`self`，但实际可以用任何合法变量名代替。
- 为了代码易读，强烈推荐使用`self`。
  

示例：

```python
class Person:
    def say_hello(this):
        print("Hello!")

p = Person()
p.say_hello()  # Hello!
```

这里`this`就是`self`，同理，调用`p.say_hello()`时，`p`会作为第一个参数绑定给`this`。

---

### 五、类方法和静态方法对`self`的区别

- **实例方法**：第一个参数是`self`，表示实例对象。
- **类方法**：用`@classmethod`装饰，第一个参数是`cls`，表示类对象。
- **静态方法**：用`@staticmethod`装饰，没有默认参数，不接收实例或类。

示例：

```python
class MyClass:
    def instance_method(self):
        print(f"实例方法，self是{self}")

    @classmethod
    def class_method(cls):
        print(f"类方法，cls是{cls}")

    @staticmethod
    def static_method():
        print("静态方法，没有self或cls参数")

obj = MyClass()
obj.instance_method()
MyClass.class_method()
MyClass.static_method()
```

---

### 六、总结

| 特性     | 是否需要 `self`         | 说明                   |
| -------- | ----------------------- | ---------------------- |
| 实例方法 | 需要                    | 通过`self`访问实例     |
| 类方法   | 不需要`self`，需要`cls` | 访问类属性或方法       |
| 静态方法 | 不需要                  | 类似普通函数，和类无关 |

`self`是Python面向对象中引用当前实例的约定，理解它是学好类和实例的关键。

---

## 例外处理

---

### 一、什么是异常？

- **异常**是程序运行中发生的错误事件，导致程序正常流程被打断。
- 例如：除数为零、文件不存在、索引越界等都会引发异常。
- **异常处理**机制允许程序捕获异常并做出合理处理，而非直接崩溃。

---

### 二、Python异常体系结构

- 所有异常都是`BaseException`的子类。
- 常用异常基类是`Exception`，大部分程序中捕获的异常都是它的子类。
- 常见异常类别：
  - `ZeroDivisionError`：除数为零异常
  - `IndexError`：索引超出范围
  - `KeyError`：字典键不存在
  - `FileNotFoundError`：文件未找到
  - `ValueError`：值错误
  - `TypeError`：类型错误
  - `IOError`：输入输出错误等

---

### 三、基础的异常处理语法

```python
try:
    # 可能引发异常的代码块
    result = 10 / 0
except ZeroDivisionError:
    # 捕获特定异常后的处理代码
    print("除数不能为零！")
```

程序运行时，如果`try`块内出错就跳转到对应的`except`块继续执行。

---

### 四、完整的异常处理结构

```python
try:
    # 代码块
    pass
except SomeException as e:
    # 处理异常
    pass
else:
    # 没有异常时执行
    pass
finally:
    # 无论是否异常都会执行，常用于清理资源
    pass
```

- **`except`**：捕获异常。
- **`else`**：`try`无异常时执行。
- **`finally`**：总会执行，通常释放资源（文件、网络等）。

---

### 五、捕获多个异常

```python
try:
    num = int(input("请输入数字:"))
    result = 10 / num
except (ValueError, ZeroDivisionError) as e:
    print("输入错误或除数为零：", e)
```

---

### 六、捕获所有异常

```python
try:
    do_something()
except Exception as e:
    print(f"出现异常: {e}")
```

谨慎使用，否则可能掩盖程序bug。

---

### 七、主动抛出异常

使用`raise`语句抛出异常，通常在检测到错误情况时。

```python
def divide(a, b):
    if b == 0:
        raise ValueError("除数不能为零")
    return a / b
```

---

### 八、自定义异常类

```python
class MyError(Exception):
    pass

try:
    raise MyError("自定义错误")
except MyError as e:
    print(e)
```

---

### 九、异常链

捕获异常后重新抛出时，可以保存原始异常信息：

```python
try:
    ...
except SomeError as e:
    raise AnotherError("新的异常") from e
```

---

### 十、示例：打开文件读取并处理异常

```python
try:
    with open("test.txt", "r") as f:
        data = f.read()
except FileNotFoundError:
    print("文件不存在！")
except IOError:
    print("读取文件出错！")
else:
    print("文件内容:", data)
finally:
    print("结束")
```

---

### 十一、小结

| 关键字    | 作用                             |
| --------- | -------------------------------- |
| `try`     | 包含可能抛出异常的代码           |
| `except`  | 捕获异常并处理                   |
| `else`    | 无异常时执行额外代码             |
| `finally` | 无论异常与否都执行，通常清理资源 |
| `raise`   | 主动抛出异常                     |

---

## 推导式

详细介绍一下Python语言中的“推导式”（Comprehensions）。

---

### 什么是推导式？

推导式是Python中用于简洁生成列表、字典、集合等数据结构的一种语法结构。它通过简洁的表达式和可选的条件，实现对已有可迭代对象的过滤、映射和组合，能够用非常简短的代码完成通常需要循环和条件语句的操作。

推导式不仅让代码更简洁，也有助于提高代码的可读性。

---

### Python中的推导式类型

Python主要有以下几种推导式：

1. **列表推导式（List Comprehension）**
2. **字典推导式（Dict Comprehension）**
3. **集合推导式（Set Comprehension）**
4. **生成器表达式（Generator Expression）**（严格意义上不叫推导式，但语法相似）

---

### 1. 列表推导式

列表推导式以简洁的语法生成新的列表。

### 语法：

```python
[表达式 for 变量 in 可迭代对象 if 条件]
```

- **表达式**：通常是基于变量的某种计算或转换
- **变量**：依次遍历可迭代对象的元素
- **条件**（可选）：过滤元素

### 例子：

- 生成0到9的平方的列表

```python
squares = [x**2 for x in range(10)]
print(squares)  # [0, 1, 4, 9, 16, 25, 36, 49, 64, 81]
```

- 过滤出列表中的偶数并平方

```python
evens_squared = [x**2 for x in range(10) if x % 2 == 0]
print(evens_squared)  # [0, 4, 16, 36, 64]
```

---

### 2. 字典推导式

字典推导式用于生成新的字典，语法类似列表推导式。

### 语法：

```python
{键表达式: 值表达式 for 变量 in 可迭代对象 if 条件}
```

### 例子：

- 将数字映射到对应的平方

```python
square_dict = {x: x**2 for x in range(5)}
print(square_dict)  # {0: 0, 1: 1, 2: 4, 3: 9, 4: 16}
```

- 过滤出偶数的映射

```python
even_square_dict = {x: x**2 for x in range(10) if x % 2 == 0}
print(even_square_dict)  # {0: 0, 2: 4, 4: 16, 6: 36, 8: 64}
```

---

### 3. 集合推导式

集合推导式用于创建集合，格式和列表推导式类似，区别在外侧使用的是 `{}`。

### 语法：

```python
{表达式 for 变量 in 可迭代对象 if 条件}
```

### 例子：

- 去除列表中的重复元素，并生成平方集合

```python
nums = [1, 2, 2, 3, 4, 4]
squares_set = {x**2 for x in nums}
print(squares_set)  # {16, 1, 4, 9}
```

---

### 4. 生成器表达式

生成器表达式与列表推导式非常相似，但它返回的是一个生成器对象，而不是立刻生成完整列表。这种惰性计算方式节省内存，适合处理大型数据。

#### 语法：

```python
(表达式 for 变量 in 可迭代对象 if 条件)
```

#### 例子：

```python
gen = (x**2 for x in range(10))
print(gen)  # <generator object ...>
print(list(gen))  # [0, 1, 4, 9, 16, 25, 36, 49, 64, 81]
```

---

### 推导式的高级用法

#### 多重循环

```python
pairs = [(x, y) for x in range(3) for y in range(3)]
print(pairs)
# [(0,0), (0,1), (0,2), (1,0), (1,1), (1,2), (2,0), (2,1), (2,2)]
```

#### 带条件的多重循环

```python
pairs = [(x, y) for x in range(3) for y in range(3) if x != y]
print(pairs)
# [(0,1), (0,2), (1,0), (1,2), (2,0), (2,1)]
```

---

### 推导式的优缺点

| 优点                     | 缺点                     |
| ------------------------ | ------------------------ |
| 代码简洁，易读           | 过于复杂的推导式可读性差 |
| 优化循环和过滤过程       | 不适合包含复杂逻辑的代码 |
| 支持多重循环和条件       | 可能会导致行长过长       |
| 生成器表达式支持惰性计算 | 新手可能不易理解         |

---

### 总结

- 推导式是Python中非常强大且简洁的语法工具
- 适合快速生成列表、字典、集合等
- 结合条件和多重循环，可以更灵活处理数据
- 使用时注意代码的可读性，避免写过于复杂的表达式

---

## 生成器函数

---

### 什么是生成器函数？

生成器函数是Python中用于创建生成器（generator）的一种特殊函数。它与普通函数的区别在于：

- 生成器函数使用`yield`语句返回数据，而不是`return`一次性返回结果。
- 调用生成器函数不会立即执行函数体，而是返回一个生成器对象。
- 生成器对象支持迭代协议，可以逐步“生成”值，实现惰性计算。

简而言之，生成器函数可以让你**按需生成数据，每次产生一个值，不会一次把所有值生成出来，节约内存、提高效率**。

---

### 生成器函数的定义和语法

一个普通函数使用`def`定义，并通过`return`返回结果；而生成器函数同样用`def`定义，但至少有一个`yield`语句。

#### 语法：

```python
def generator_function(args):
    # 若干代码
    yield 表达式
    # 可以有多次yield，也可以有循环
```

调用该函数：

```python
gen = generator_function(args)
```

`gen`为一个生成器对象。

---

### `yield`关键字详解

- `yield`用来“产出”一个值，挂起函数的执行，保留函数的执行状态（包括局部变量、指令指针等）。
- 下一次调用`__next__()`或者使用`for`循环时，函数会从挂起点继续执行，直到遇到下一个`yield`或者函数结束。
- 函数执行结束时，生成器停止迭代，抛出`StopIteration`异常（由循环机制自动捕获处理）。

---

### 简单示例

```python
def count_up_to(n):
    count = 1
    while count <= n:
        yield count
        count += 1
```

使用：

```python
for number in count_up_to(5):
    print(number)
```

输出：

```
1
2
3
4
5
```

---

### 生成器函数 vs 普通函数

| 方面       | 普通函数                     | 生成器函数                       |
| ---------- | ---------------------------- | -------------------------------- |
| 返回值     | 一次性返回（`return`）       | 逐步产生值（`yield`多次）        |
| 内存使用   | 可能一次生成所有结果，占内存 | 惰性计算，节省内存               |
| 可迭代对象 | 返回普通数据（列表、元组等） | 返回生成器对象，支持迭代         |
| 适用场景   | 小数据集、一次生成结果       | 大数据、流式数据处理、无限序列等 |

---

### 生成器的传值和异常处理

生成器支持通过 `.send()` 方法传值给生成器内部，使得生成器更灵活。

例子：

```python
def echo():
    received = yield
    while True:
        received = yield received
```

用法：

```python
gen = echo()
next(gen)            # 激活生成器，运行到第一个yield
print(gen.send('hi')) # 传入'hi'，生成器yield回传'hi'
print(gen.send('bye')) 
```

输出：

```
hi
bye
```

---

### 生成器函数中的`return`语句

- 生成器函数中，可以使用`return`语句退出生成器，`return`后可跟一个值，该值会被包装在`StopIteration`异常中，供外部捕获。
- 这种特性在Python 3.3+支持，可用于协程等高级用法。

---

### 生成器函数的优势和应用场景

### 优势

1. **节省内存**：不需要一次性将所有数据生成存储，占用大量内存。
2. **惰性计算**：只有在需要时才计算，提升效率。
3. **可表达无限序列**：如斐波那契数列、自然数等。
4. **简化异步编程**（协程基础）。

### 应用场景

- 处理大文件逐行读取，例如读大文本文件。
- 网络数据流读取。
- 无限序列生成，如斐波那契数列、素数序列。
- 自定义迭代行为。
- 数据管道、协程。

---

### 复杂示例

生成斐波那契数列的生成器函数：

```python
def fibonacci():
    a, b = 0, 1
    while True:
        yield a
        a, b = b, a + b
```

用法：

```python
fib = fibonacci()
for _ in range(10):
    print(next(fib))
```

输出：

```
0
1
1
2
3
5
8
13
21
34
```

---

### 生成器表达式与生成器函数区别

- **生成器表达式**语法更简洁，类似列表推导式：

```python
gen = (x*x for x in range(5))
print(next(gen))  # 0
print(next(gen))  # 1
```

- **生成器函数**更灵活，可包含复杂业务逻辑，多个`yield`，处理状态。

---

### 总结

| 关键词     | 说明                                             |
| ---------- | ------------------------------------------------ |
| 生成器函数 | 定义中包含`yield`语句的函数，返回生成器对象      |
| `yield`    | 挂起当前函数状态，返回值给调用者，下一次恢复执行 |
| 惰性计算   | 每次请求时生成一个值，避免一次性占用大量内存     |
| 生成器对象 | 迭代器协议实现者，支持`next()`，`send()`等方法   |
| 应用       | 大数据处理、数据流、无限序列、异步编程的基础     |

---

## 网络爬虫详解

网络爬虫（Web crawler / spider）是自动从互联网上抓取网页信息的程序。Python因其简单且强大的网络编程库，成为爬虫开发的首选语言。

---

### 一、网络爬虫基础

#### 1. 工作流程
1. **发送HTTP请求**  
   向目标网站发送请求，获取网页内容。

2. **解析网页内容**  
   取出网页中的数据，常用HTML、JSON解析。

3. **数据存储**  
   将提取的数据存入数据库、文件等。

4. **循环抓取/翻页处理**  
   自动跟踪链接，实现广泛抓取。

#### 2. 需要注意的点
- 尊重网站的`robots.txt`规则。
- 控制抓取频率，避免给服务器造成压力（反爬机制）。
- 合法合规，避免侵犯版权或隐私。

---

### 二、Python常用爬虫库

#### 1. requests

- 功能强大的HTTP库，简洁易用，支持发送各种HTTP请求。
- 一般负责发送请求，获取网页源码。

```python
import requests

response = requests.get('https://www.example.com')
print(response.text)  # 网页源码
```

#### 2. BeautifulSoup (bs4)

- HTML/XML解析库，简单高效。
- 支持多种解析器（如lxml），方便提取网页标签和数据。

```python
from bs4 import BeautifulSoup

html_doc = '<html><head><title>Example</title></head><body><p>Paragraph</p></body></html>'
soup = BeautifulSoup(html_doc, 'html.parser')
print(soup.title.string)  # 输出：Example
```

#### 3. lxml

- 高性能XML和HTML解析库。
- 兼容XPath查询语法，定位元素更强大。

```python
from lxml import etree

html = '<html><body><div><a href="url">link</a></div></body></html>'
tree = etree.HTML(html)
print(tree.xpath('//a/@href'))  # 输出：['url']
```

#### 4. Scrapy

- 功能完善的全功能异步爬虫框架，支持分布式爬虫。
- 集成请求调度、页面解析、数据存储、自动去重。
- 适合复杂项目、海量数据采集。

项目结构清晰，有Spider、Item、Pipeline等组件。

```bash
pip install scrapy
```

- 简单Spider示例：

```python
import scrapy

class ExampleSpider(scrapy.Spider):
    name = 'example'
    start_urls = ['https://www.example.com']

    def parse(self, response):
        title = response.css('title::text').get()
        yield {'title': title}
```

运行：

```bash
scrapy crawl example
```

#### 5. Selenium

- 浏览器自动化工具，用于爬取动态加载内容（JavaScript渲染）。
- 能操作浏览器，支持点击、滚动、等待，适合SPA站点。

```python
from selenium import webdriver

driver = webdriver.Chrome()
driver.get('https://www.example.com')
print(driver.page_source)
driver.quit()
```

#### 6. aiohttp & asyncio

- 异步HTTP客户端，用于高并发爬取。
- 结合Python内置异步库`asyncio`，提升IO密集型爬虫效率。

```python
import aiohttp
import asyncio

async def fetch(session, url):
    async with session.get(url) as response:
        return await response.text()

async def main():
    async with aiohttp.ClientSession() as session:
        html = await fetch(session, 'https://www.example.com')
        print(html)

asyncio.run(main())
```

---

### 三、爬虫分类

#### 1. 静态爬虫

- 直接请求HTML页面并解析。
- 适合网页源代码静态展示的网站。

#### 2. 动态爬虫

- 针对JavaScript渲染的数据，需要浏览器模拟或API反向解析。
- 可使用Selenium，Pyppeteer，Playwright等。

#### 3. 增量爬虫

- 只抓取更新或新增内容，常配合数据库做数据比对。

#### 4. 分布式爬虫

- 多台机器协作分布抓取，解决单机瓶颈。
- Scrapy结合Scrapy-Redis支持。

---

### 四、爬虫进阶技巧

#### 1. 伪装 (User-Agent, Headers)

- 模拟浏览器请求，避免被反爬网站屏蔽。

```python
headers = {'User-Agent': 'Mozilla/5.0 (Windows NT 10.0; Win64; x64)'}
response = requests.get('https://example.com', headers=headers)
```

#### 2. 代理IP

- 通过代理服务器发起请求，避免IP封禁。

```python
proxies = {'http': 'http://10.10.1.10:3128', 'https': 'https://10.10.1.10:1080'}
requests.get('https://example.com', proxies=proxies)
```

#### 3. Cookies和Session管理

- 维护登录状态，处理需要登录才能访问的页面。

```python
session = requests.Session()
session.post('https://example.com/login', data=login_data)
response = session.get('https://example.com/protected')
```

#### 4. 异步爬取

- 使用`aiohttp`或者`Scrapy`的异步功能实现高并发抓取。

#### 5. 数据清洗与持久化

- 抓取数据后，需做清洗文本、格式转换等。
- 持久化保存到文件（JSON, CSV）、数据库（MySQL, MongoDB）或搜索引擎（Elasticsearch）。

---

### 五、简单示例 - 用requests+BeautifulSoup爬取新闻标题

```python
import requests
from bs4 import BeautifulSoup

url = 'https://news.ycombinator.com/'
headers = {'User-Agent': 'Mozilla/5.0'}

response = requests.get(url, headers=headers)
soup = BeautifulSoup(response.text, 'html.parser')

titles = soup.select('.storylink')
for idx, title in enumerate(titles, 1):
    print(f"{idx}. {title.text}")
```

运行即可打印Hacker News首页文章标题。

---

### 六、总结

| 爬虫类型   | 适用情况         | 代表库/框架               | 优点                         | 缺点                   |
| ---------- | ---------------- | ------------------------- | ---------------------------- | ---------------------- |
| 静态爬虫   | 纯静态页面       | requests + BS4/lxml       | 简单易用，需求低             | 处理不了JS渲染         |
| 动态爬虫   | JS渲染页面       | Selenium, Playwright      | 模拟真实浏览器，抓取动态数据 | 开销大，速度慢         |
| 高并发爬虫 | 巨量数据抓取     | Scrapy + Twisted，aiohttp | 异步协程、分布式，效率高     | 框架复杂，需要学习成本 |
| 分布式爬虫 | 大规模分布式采集 | Scrapy+Redis等            | 任务调度灵活，海量数据处理   | 复杂度高，环境配置复杂 |

---

## 绘制图表数据

---

### 一、Python绘图的基本概念

- **数据准备**：绘图的前提是有要展示的数据，数据通常以列表、数组、Pandas的DataFrame或Series形式存在。
- **选取合适的图表类型**：根据数据类型和分析需求选择合适的图表，如折线图、柱状图、散点图、饼图、箱线图等。
- **调用绘图库**：用相应库的接口绘制图表。
- **调整图表属性**：包括标题、坐标轴标签、图例、颜色、字体等，使图表更易读美观。
  
---

### 二、Python常用绘图库介绍

#### 1. Matplotlib
- Python最基础的绘图库，功能强大，支持多种图表。
- 语法相对底层，需要较多代码控制细节。
- 适合精细控制图表样式。

```python
import matplotlib.pyplot as plt
```

#### 2. Seaborn
- 基于Matplotlib，专为统计数据可视化设计。
- 语法更简洁，默认样式美观。
- 适合绘制分类变量和分布图。

```python
import seaborn as sns
```

#### 3. Pandas内置绘图功能
- DataFrame和Series对象自带`.plot()`接口，基于Matplotlib实现。
- 快速绘图，适合探索性数据分析。

```python
import pandas as pd
```

#### 4. Plotly
- 绘制交互式图表，适合网页展示。
- 语法层次稍复杂。

```python
import plotly.express as px
```

---

### 三、Matplotlib基础图表示例

#### 1. 折线图

```python
import matplotlib.pyplot as plt

x = [1, 2, 3, 4, 5]
y = [10, 12, 15, 14, 20]

plt.plot(x, y, marker='o', linestyle='-', color='b')  # 画折线图
plt.title('折线图示例')
plt.xlabel('X轴')
plt.ylabel('Y轴')
plt.grid(True)  # 显示网格
plt.show()
```

#### 2. 柱状图

```python
import matplotlib.pyplot as plt

categories = ['A', 'B', 'C', 'D']
values = [5, 7, 3, 8]

plt.bar(categories, values, color='skyblue')
plt.title('柱状图示例')
plt.xlabel('类别')
plt.ylabel('数值')
plt.show()
```

#### 3. 散点图

```python
import matplotlib.pyplot as plt

x = [1, 2, 3, 4, 5]
y = [5, 7, 8, 6, 9]

plt.scatter(x, y, c='red', marker='x')
plt.title('散点图示例')
plt.xlabel('X轴')
plt.ylabel('Y轴')
plt.show()
```

#### 4. 饼图

```python
import matplotlib.pyplot as plt

labels = ['苹果', '香蕉', '橘子', '梨']
sizes = [30, 15, 45, 10]

plt.pie(sizes, labels=labels, autopct='%1.1f%%', startangle=90)
plt.title('饼图示例')
plt.show()
```

---

### 四、Seaborn绘图示例

Seaborn对统计绘图提供了很多便捷函数，下面以内置数据集打个样。

```python
import seaborn as sns
import matplotlib.pyplot as plt

# 加载内置数据集
tips = sns.load_dataset("tips")

# 盒须图：显示小费的分布，按“性别”分类
sns.boxplot(x='day', y='total_bill', hue='sex', data=tips)
plt.title('Seaborn盒须图示例')
plt.show()

# 热力图：相关系数矩阵
corr = tips.corr()
sns.heatmap(corr, annot=True, cmap='coolwarm')
plt.title('Seaborn热力图示例')
plt.show()
```

---

### 五、Pandas快速绘图

Pandas中的`DataFrame`对象支持快速绘图：

```python
import pandas as pd
import matplotlib.pyplot as plt

data = {'年份': [2017, 2018, 2019, 2020, 2021],
        '销售额': [250, 270, 300, 350, 400]}
df = pd.DataFrame(data)

df.plot(x='年份', y='销售额', kind='line', marker='o', title='年度销售额折线图')
plt.show()
```

---

### 六、Plotly交互式绘图简例

```python
import plotly.express as px

df = px.data.iris()  # 载入示例数据集

fig = px.scatter(df, x='sepal_width', y='sepal_length', color='species',
                 title='鸢尾花数据散点图')
fig.show()
```

---

### 七、绘图技巧及注意点

1. **选择合适图表**：比如时间序列用折线图，分类比较用柱状图，比例用饼图。
2. **调整图表美观性**：添加标题、轴标签，合理使用颜色与图例。
3. **处理大数据集**：绘制时要考虑性能，必要时抽样。
4. **保存图表**：
   
   ```python
   plt.savefig('figure.png', dpi=300)
   ```
5. **多图布局**：

   ```python
   fig, axs = plt.subplots(1, 2, figsize=(10, 4))
   axs[0].plot(x, y)
   axs[1].bar(categories, values)
   plt.show()
   ```

---

### 总结

绘制数据图表是Python数据分析中不可或缺的一部分，掌握Matplotlib、Seaborn、Pandas和Plotly等库的使用，可以高效地对数据进行可视化和传达。建议多练习不同图表并结合实际业务需求灵活运用。

