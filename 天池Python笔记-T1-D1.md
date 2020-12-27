# 天池Python笔记-T1-D1

## 变量 运算符 数据类型

### 1.注释

1.单行注释

使用 `#`表示
```python
# 此处为注释
```
2.多行注释

使用`"""`或`'''`表示

```python
"""
此处为注释
此处为注释
"""
'''
此处为注释
此处为注释
'''
```

### 2.运算符

1.算数运算符

返回数值

| 操作符 | 名称 |
| :----: | :--: |
|  `+`   |  加  |
|  `-`   |  减  |
|  `*`   |  乘  |
|  `/`   |  除  |
|  `//`  | 整除 |
|  `%`   | 取余 |
|  `**`  |  幂  |

2.比较运算符

返回布尔值

| 操作符 |   名称   |
| :----: | :------: |
|  `>`   |   大于   |
|  `>=`  | 大于等于 |
|  `<`   |   小于   |
|  `<=`  | 小于等于 |
|  `==`  |   等于   |
|  `!=`  |  不等于  |

3.位运算符

| 操作符 |   名称   |                   注释                   |
| :----: | :------: | :--------------------------------------: |
|  `&`   |  按位与  |       对应的两个二进制位都为1，出1       |
|  `|`   |  按位或  |     对应的两个二进制位有一个为1，出1     |
|  `^`   | 按位异或 |      对应的两个二进制位相异时，出1       |
|  `~`   | 按位取反 |         对数据的每个二进制位取反         |
|  `<<`  |   左移   | `<<``右侧指定移动位数，高位丢弃，地位补0 |
|  `>>`  |   右移   |          `>>``右侧指定移动位数           |

```python
a = 60            # 60 = 0011 1100 
b = 13            # 13 = 0000 1101 
c = 0
 
c = a & b        # 12 = 0000 1100	与运算
print ("1 - c 的值为：", c)
 
c = a | b        # 61 = 0011 1101	或运算
print ("2 - c 的值为：", c)
 
c = a ^ b        # 49 = 0011 0001	异或运算
print ("3 - c 的值为：", c)
 
c = ~a           # -61 = 1100 0011	按位取反
print ("4 - c 的值为：", c)
 
c = a << 2       # 240 = 1111 0000	左移2位
print ("5 - c 的值为：", c)
 
c = a >> 2       # 15 = 0000 1111	右移2位
print ("6 - c 的值为：", c)
```

4.逻辑运算符

返回布尔值

| 运算符 | 表达式  | 描述 |
| ------ | ------- | ---- |
| `and`  | a and b | 与   |
| `or`   | a or b  | 或   |
| `not`  | a not b | 非   |

```python
print((3 > 2) and (3 < 5))  # True
print((1 > 3) or (9 < 2))  # False
print(not (2 >1))  # False
```

5.三元运算

```python
x, y = 4, 5
if x < y:
    small = x
else:
    small = y

print(small)  # 4
```

等价于

```python
x, y = 4, 5
small = x if x < y else y
print(small)  # 4
```

6.成员运算符

| 运算符   | 描述                                                    |
| -------- | ------------------------------------------------------- |
| `in`     | 如果在指定的序列中找到值返回 True，否则返回 False。     |
| `not in` | 如果在指定的序列中没有找到值返回 True，否则返回 False。 |

```python
letters = ['A', 'B', 'C']
if 'A' in letters:
    print('A' + ' exists')
if 'h' not in letters:
    print('h' + ' not exists')

# A exists
# h not exists
```

7.身份运算符

| 运算符   | 描述                                           |
| -------- | ---------------------------------------------- |
| `is`     | 判断两个变量是不是引用自同一个对象（内存地址） |
| `is not` | 判断两个变量是不是引用自不同对象               |

```python
a = "hello"	#字符串为不可变地址
b = "hello"
print(a is b, a == b)  # True True
print(a is not b, a != b)  # False False
```

```python
a = ["hello"]	#列表为可变地址
b = ["hello"]
print(a is b, a == b)  # False True
print(a is not b, a != b)  # True False
```

==`is` `is not`对比的是两个变量的内存地址==

`==` `!=` 对比的是两个变量的值

比较的两个变量，指向的都是地址不可变的类型（str等），那么is，is not 和 ==，！= 是完全等价的。

对比的两个变量，指向的是地址可变的类型（list，dict，tuple等），则两者是有区别的。

8.运算符优先级

| 运算符            | 描述                     |
| ----------------- | ------------------------ |
| **                | 指数（最高优先级）       |
| ~+-               | 按位翻转，一元加号和减号 |
| * / % //          | 乘，除，取模和取整除）   |
| + -               | 加法减法                 |
| >> <<             | 右移，左移运算符         |
| &                 | 位‘AND’                  |
| ^\|               | 位运算符                 |
| <=<>>=            | 比较运算符               |
| <>==!=            | 等于运算符               |
| =%=/=//=-=+=*=**= | 赋值运算符               |
| is is not         | 身份运算符               |
| in not in         | 成员运算符               |
| not and or        | 逻辑运算符               |

### 3.变量和赋值

变量名可以包括字母，数字，下划线，但不能以数字开头

变量名称大小写敏感 a !=A

### 4.数据类型与转换

| 类型  | 名称          | 示例           |
| ----- | ------------- | -------------- |
| int   | 整型 `int`    | `-876, 10`     |
| float | 浮点型`float` | `3.149, 11.11` |
| bool  | 布尔型`bool`  | `True, False`  |

`type()` 可返回变量类型

```python
a = 1031
print(a, type(a))
# 1031 <class 'int'>
```

```python
a = 1031
print(bin(a))  # 0b10000000111
print(a.bit_length())  # 11
```

`bit_length` 可返回变量的二进制位数

布尔型

布尔 (boolean) 型变量只能取两个值，`True` 和 `False`。当把布尔型变量用在数字运算中，用 `1` 和 `0` 代表 `True` 和 `False`。

```python
print(True + True)  # 2
print(True + False)  # 1
print(True * False)  # 0
```

除了直接给变量赋值 `True` 和 `False`，还可以用 `bool(X)` 来创建变量，其中 `X` 可以是

- 基本类型：整型、浮点型、布尔型

- 容器类型：字符串、元组、列表、字典和集合

【例子】`bool` 作用在基本类型变量：`X` 只要不是整型 `0`、浮点型 `0.0`，`bool(X)` 就是 `True`，其余就是 `False`。

```python
print(type(0), bool(0), bool(1))
# <class 'int'> False True

print(type(10.31), bool(0.00), bool(10.31))
# <class 'float'> False True

print(type(True), bool(False), bool(True))
# <class 'bool'> False True
```

【例子】`bool` 作用在容器类型变量：`X` 只要不是空的变量，`bool(X)` 就是 `True`，其余就是 `False`。

```python
print(type(''), bool(''), bool('python'))
# <class 'str'> False True

print(type(()), bool(()), bool((10,)))
# <class 'tuple'> False True

print(type([]), bool([]), bool([1, 2]))
# <class 'list'> False True

print(type({}), bool({}), bool({'a': 1, 'b': 2}))
# <class 'dict'> False True

print(type(set()), bool(set()), bool({1, 2}))
# <class 'set'> False True
```

==确定`bool(X)` 的值是 `True` 还是 `False`，就看 `X` 是不是空，空的话就是 `False`，不空的话就是 `True`。==

- ==对于数值变量，`0`, `0.0` 都可认为是空的。==
- ==对于容器变量，里面没元素就是空的。==

判断两变量是否为同一类型，可使用`isinstance()` 返回布尔值

`isinstance()`相比`type()`考虑继承关系

```py
print(isinstance(1, int))  # True
print(isinstance(5.2, float))  # True
print(isinstance(True, bool))  # True
print(isinstance('5.2', str))  # True
```

数值转换

|              |           |
| ------------ | --------- |
| 转换为整型   | `int()`   |
| 转换为字符串 | `str()`   |
| 转换为浮点型 | `float()` |

```python
print(int('520'))  # 520
print(int(520.52))  # 520
print(float('520.52'))  # 520.52
print(float(520))  # 520.0
print(str(10 + 10))  # 20
print(str(10.1 + 5.2))  # 15.3
```

### 5.`print()`函数

```python
print(*objects, sep=' ', end='\n', file=sys.stdout, flush=False)
```

- 将对象以字符串表示的方式格式化输出到流文件对象file里。其中所有非关键字参数都按`str()`方式进行转换为字符串输出；
- `sep`是实现分隔符，比如多个参数输出时想要输出中间的分隔字符；
- `end`是输出结束时的字符，默认是换行符`\n`；
- `file`是定义流输出的文件，可以是标准的系统输出`sys.stdout`，也可以重定义为别的文件；
- `flush`是立即把内容输出到流文件，不作缓存。

未设定参数时，每次输出都会换行

time:2020/12/27 22:38