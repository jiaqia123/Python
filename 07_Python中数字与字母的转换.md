# Python中数字与字母的转换

在Python中，数字转字母以及字母转数字通常涉及到`ASCII`码的使用，尤其是对于小写字母`a-z`和大写字母`A-Z`。下面分别介绍这两种转换的方法：

**谨记**：`A`的`ASCII`是65，`a`的`ASCII`是97

## 数字转字母`chr()`

假设我们要将0-25的数字转换为小写字母'a'到'z'：

```python
def num_to_letter(num):
    return chr(num + 97)  # 97是'a'的ASCII码

# 示例
print(num_to_letter(0))  # 输出 'a'
print(num_to_letter(25)) # 输出 'z'
```

如果要转换为大写字母，只需要将97改为65，即大写字母'A'的ASCII码：

```python
def num_to_letter_upper(num):
    return chr(num + 65)  # 65是'A'的ASCII码

# 示例
print(num_to_letter_upper(0))  # 输出 'A'
print(num_to_letter_upper(25)) # 输出 'Z'
```

## 字母转数字`ord()`

反过来，如果我们要将小写字母'a'到'z'转换为0-25的数字：

```python
def letter_to_num(letter):
    return ord(letter) - 97  # 97是'a'的ASCII码

# 示例
print(letter_to_num('a'))  # 输出 0
print(letter_to_num('z'))  # 输出 25
```

对于大写字母，同样需要调整减的数字：

```python
def letter_to_num_upper(letter):
    return ord(letter) - 65  # 65是'A'的ASCII码

# 示例
print(letter_to_num_upper('A'))  # 输出 0
print(letter_to_num_upper('Z'))  # 输出 25
```

这些函数可以方便地实现数字与字母之间的转换。如果需要处理更复杂的转换，比如超出26个字母的范围，可以适当调整算法或使用其他数据结构来实现。