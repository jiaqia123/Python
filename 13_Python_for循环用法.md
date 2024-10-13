# `Python_for`循环用法

### 1. 基本语法

```python
for variable in iterable:
    # 执行的代码块
```

### 2. 遍历列表

```python
fruits = ["apple", "banana", "cherry"]
for fruit in fruits:
    print(fruit)
```

输出：

```
apple
banana
cherry
```

### 3. 遍历字符串

```python
for letter in "banana":
    print(letter)
```

输出：

```
b
a
n
a
n
a
```

### 4. 使用`range()`函数

```
range(start, stop, step)
```

- `start`: 开始值（默认为0）
- `stop`: 结束值（不包含）
- `step`: 步长（默认为1）

```python
for i in range(5):
    print(i)
    
print()

for i in range(1, 10, 2):
    print(i)
```

输出：

```
0
1
2
3
4

1
3
5
7
9
```

### 5. 嵌套`for`循环

```python
for i in range(3):
    for j in range(2):
        print(i, j)
```

输出：

```
0 0
0 1
1 0
1 1
2 0
2 1
```

### 6. 使用`else`子句

`for`循环可以和`else`子句配合使用，当循环**正常终止**（没有遇到`break`）时执行`else`块。

```python
for n in range(2, 10):
    for x in range(2, n):
        if n % x == 0:
            print(n, 'equals', x, '*', n//x)
            break
    else:
        # 循环因自然结束而触发else
        print(n, 'is a prime number')
```

输出：

```
2 is a prime number
3 is a prime number
4 equals 2 * 2
5 is a prime number
6 equals 2 * 3
7 is a prime number
8 equals 2 * 4
9 equals 3 * 3
```

### 7. `for`循环与`enumerate()`

使用`enumerate()`可以同时获取列表中的索引和值。

```python
fruits = ['apple', 'banana', 'cherry']
for index, fruit in enumerate(fruits):
    print(index, fruit)
```

输出：

```
0 apple
1 banana
2 cherry
```