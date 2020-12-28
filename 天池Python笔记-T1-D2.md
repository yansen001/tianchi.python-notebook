# 天池Python笔记-T1-D2

## 位运算

### 1.原码，反码，补码

原码：二进制表示，最高位为符号位，正数，负数的原码区别在符号位

反码：正数的原码就是反码，负数的反码为保持符号位不变，其余取反

补码：正数的原码就是补码，负数的补码为反码+1（二进制+1）

### 2.按位运算

非 `~`  将补码中的0和1取反==（包括符号位）==

与 `&`  全1出1

或 `|` 有1出1

异或 `^` 两对应位相反，出1

左移 `<<` `num << i` 将 `num` 的二进制表示向左移动 `i` 位

右移`>>` `num >> i` 将 `num` 的二进制表示向右移动 `i` 位

### 3.快速计算技巧

快速计算2的倍数问题：

```python
n << m #计算n*(2^m)		#即n乘以2的m次方
n >> m -> 计算 n/(2^m)	#即除以 2 的 m 次方
1 << n -> 2^n
```

## 条件语句

### 1.if

```python
if expression:
    expr_true_suite
```

当表达式 `expression` 为真时，执行 `expr_true_suite`

### 2. if-else

```python
if expression:
    expr_true_suite
else:
    expr_false_suite
```

当 `expression` 为假时，执行else后的语句

### 3. if  - elif - else

```python
if expression1:
    expr1_true_suite
elif expression2:
    expr2_true_suite
else:
    expr_false_suite
```

多条件判断

### 4. assert

断言 当此函数后的表达式为false时，程序自动崩溃，并输出`AssertionError`

## 循环

1.while

```python
while 布尔表达式:
    代码块
```

当表达式为真时，循环执行代码块，当表达式为假时，停止循环

表达式为一个非零整数时，为真，为0时，为假，也可写入`str list`等，长度非零即为真，

2. while - else

```python
while 布尔表达式:
    代码块
else:
    代码块
```

当while循环执行完成后，执行else后的语句，当while代码块中执行了跳出循环语句，则不执行else代码块，如`break`

3. for

```python
for 迭代变量 in 可迭代对象:
    代码块
```

迭代循环，可遍历任何有序序列。

每次循环，迭代变量被设置为可迭代对象的当前元素，提供给代码块使用

```python
member = ['张三', '李四', '刘德华', '刘六', '周润发']
for each in member:
    print(each)

# 张三
# 李四
# 刘德华
# 刘六
# 周润发

for i in range(len(member)):
    print(member[i])

# 张三
# 李四
# 刘德华
# 刘六
# 周润发
```

### 4. for - else 循环

```python
for 迭代变量 in 可迭代对象:
    代码块
else:
    代码块
```

与while - else 类似

```python
for num in range(10, 20):  # 迭代 10 到 20 之间的数字
    for i in range(2, num):  # 根据因子迭代
        if num % i == 0:  # 确定第一个因子
            j = num / i  # 计算第二个因子
            print('%d 等于 %d * %d' % (num, i, j))
            break  # 跳出当前循环
    else:  # 循环的 else 部分
        print(num, '是一个质数')

# 10 等于 2 * 5
# 11 是一个质数
# 12 等于 2 * 6
# 13 是一个质数
# 14 等于 2 * 7
# 15 等于 3 * 5
# 16 等于 2 * 8
# 17 是一个质数
# 18 等于 2 * 9
# 19 是一个质数
```

### 5. `range()`

```python
range([start,] stop[, step=1])
```

此函数用以生成一个从`start`参数的值开始到`stop`参数的值结束的数字序列，该序列包含`start`的值但不包含`stop`的值

- `step=1` 表示步长为1 为可选参数，默认为1。
- `start step` 为可选参数
- 如为设定`start` ，则`start`默认为0

```python
for i in range(2, 9):  # 不包含9
    print(i)

# 2
# 3
# 4
# 5
# 6
# 7
# 8
for i in range(1, 10, 2): #步长为2，即下一个值为i+=2
    print(i)

# 1
# 3
# 5
# 7
# 9
for i in range(10):
    print(i)
else:
    print("end")
#0
#1
#2


#9
```

### 6. `enumerate()`

enumerate() 函数用于将一个可遍历的数据对象(如列表、元组或字符串)组合为一个索引序列，同时列出数据和数据下标，一般用在 for 循环当中

```python
enumerate(sequence, [start=0])
```

- sequence：一个序列、迭代器或其他支持迭代对象。
- start：下标起始位置。

常用于枚举可遍历的数据对象，并可自定义起始索引值

```python
seasons = ['Spring', 'Summer', 'Fall', 'Winter']
lst = list(enumerate(seasons))
print(lst)
# [(0, 'Spring'), (1, 'Summer'), (2, 'Fall'), (3, 'Winter')]
lst = list(enumerate(seasons, start=1))  # 下标从 1 开始
print(lst)
# [(1, 'Spring'), (2, 'Summer'), (3, 'Fall'), (4, 'Winter')]
```

```python
languages = ['Python', 'R', 'Matlab', 'C++']
for language in languages:
    print('I love', language)
print('Done!')
# I love Python
# I love R
# I love Matlab
# I love C++
# Done!


for i, language in enumerate(languages, 2):	
    print(i, 'I love', language)	#i赋值为索引值
print('Done!')
# 2 I love Python
# 3 I love R
# 4 I love Matlab
# 5 I love C++
# Done!
```

### 7. break

用于跳出循环

```python
n = 5
while n > 0:
    n -= 1
    if n == 2:
        break
    print(n)
print('循环结束。')
#4
#3
#循环结束
```

### 8. continue

终止本轮循环并开始下一轮循环，与break的差别在于break是跳出循环体，continue是跳出循环体的剩余语句，重新开始循环

```python
n = 5
while n > 0:
    n -= 1
    if n == 2:
        continue	#如果n==2 则跳过2
    print(n)
print('循环结束。')
#4
#3
#1
#0
#循环结束
```

### 9. `pass`

占位符，免于编译出错

### 10. 列表推导式

