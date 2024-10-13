# Python复数complex

## 一、表示方法

1. **直接表示**：复数可以用`a + bj`的形式直接表示，其中`a`和`b`是实数，`j`代表虚数单位

	```python
	complex_number = 3 + 4j
	```

2. **使用函数**：可以使用`complex()`函数创建复数

	```python
	complex_number = complex(3, 4)	# 3 + 4j
	```



## 二、复数属性

- `real`：复数的实部
- `imag`：复数的虚部

示例：

```python
complex_number = 3 + 4j
print(complex_number.real)  # 输出：3.0
print(complex_number.imag)  # 输出：4.0
```



## 三、操作复数

Python支持对复数进行各种算术运算，包括**加、减、乘、除和求幂**

示例：

```python
num1 = 3 + 4j
num2 = 1 + 2j
print(num1 + num2)  # (4+6j)
print(num1 * num2)  # (-5+10j)
print(num1 - num2)  # (2+2j)
print(num1 / num2)  # (2.2-0.4j)
print(num1 ** 2)    # (-7+24j)
```



## 四、复数的共轭

使用`conjugate`方法获取**复数的共轭**

示例：

```python
complex_number = 3 + 4j
print(complex_number.conjugate())  # 输出：(3-4j)
```