# Python容器类型—字符串`str`

- **概述：**
	- 字符串是**不可变**的序列类型，用于表示文本数据。



## 1、定义格式

- 方式一：使用单引号(')、双引号(")均可，建议用单引号

	```python
	s1 = '张三'
	s2 = "李四"
	```

- 方式二：引号嵌套

	```python
	# 引号嵌套
	s1 = "I'm Tom"
	# 转义符
	s2 = 'I\'m tom'
	```

- 方式三：三引号('''或""")包裹，三引号允许定义多行字符串，保持**换行符和空格**。

	```python
	# 三引号能保持原有的文本格式，单引号双引号都不行
	s1 = '''你好
	111
	222
	三点式    哈哈哈哈
	你   好呀
	aa a
	'''
	```



## 2、索引和切片

#### 字符串索引

- 字符串索引用于访问字符串中的单个字符。

- 索引都是从0开始的，如果尝试访问不存在的索引，`Python`将抛出`IndexError`异常。

- 例如：

	```python
	s = "hello"
	print(s[0])  # 输出: h
	print(s[4])  # 输出: o
	# print(s[5])  # 会抛出 IndexError，因为索引5超出了字符串的范围
	```

- 注意：**逆向索引**用于从字符串的末尾向前计数。例如，`-1`索引指向字符串的最后一个字符，`-2`索引指向倒数第二个字符，依此类推。

#### 字符串切片（包左不包右）

字符串切片用于访问字符串中的一系列字符。切片操作的基本语法是`string[start:stop:step]`，其中：

- `start`：切片**开始**的索引（**包含**）。如果省略，默认从字符串开头开始。
- `stop`：切片**结束**的索引（**不包含**）。如果省略，默认切片到字符串的末尾。
- `step`：切片的步长，决定了每隔多少个字符取一个。默认步长为1。

切片可以是正序的，也可以是逆序的。正序切片从左到右选取字符，而逆序切片从右到左选取字符。

例如：

```python
s = "hello"
print(s[1:4])  # 输出: ell，选取索引1到3的字符
print(s[::2])  # 输出: hlo，选取所有偶数索引的字符
print(s[::-1])  # 输出: olleh，反转字符串
print(s[:3])	# 输出: hel，从开头选取到索引2的字符
print(s[2:])	# 输出: llo，从索引为2的字符开始一直到最后
```

**注意：**切片操作**不会改变原字符串**，而是返回一个新的字符串对象。

如果切片的起始索引大于或等于结束索引，或者步长为负数且绝对值小于字符串长度，切片操作将返回**空字符串**。



## 3、字符串查找

#### 查找`find()`

- 概述：查找子串在字符串中**第一次**出现的位置，如果在 返回这个子串的下标，否则**返回-1**

- 基本语法：

	`字符串序列.find(子串, 开始位置下标, 结束位置下标)`

	注意：开始和结束位置下标可以省略，表示在整个字符串中查找

- 案例演示：

	```python
	str1 = "hello world and hello python"
	
	print(str1.find('hello'))		# 0
	print(str1.find('helllo', 10, 27))		# 16
	print(str1.find('haha'))		# -1
	print(str1.find('hello', 0, 4))		# -1	
	# 细节：开始和结束下标 包左不包右
	#      字符串中空格也算字符
	```

	

#### 查找`index()`

参数和`find()`方法一样

查找子串在字符串中**第一次**出现的位置，如果在 返回这个子串的下标，否则就会**报错**



#### 查找`rfind()`

参数和`find()`方法一样

查找子串在字符串中**最后一次**出现的位置，如果在 返回这个子串的下标，否则**返回-1**



#### 查找`rindex()`

参数和`find()`方法一样

查找子串在字符串中**最后一次**出现的位置，如果在 返回这个子串的下标，否则**报错**





## 4、字符串修改

#### 替换`replace()`

- `replace()`：返回替换后的字符串

- 基本语法：

	- `字符串序列.replace(旧子串, 新子串, 替换次数)`

	- 如果不写替换次数，默认全部替换

	- 如果替换次数超出子串出现次数，则替换次数为该子串的出现次数

	- 案例演示：

		```python
		str1 = "hello world and hello python and hello java"
		
		print(str1.replace('and', '&'))		# hello world & hello python & hello java
		print(str1.replace('hello', 'hi', 2))	# hi world and hi python and hello java
		
		print(str1)		# hello world and hello python and hello java
		```

- 注意：字符串为不可变类型，所以修改的时候不会改变原来的字符串



#### 分割`split()`

- `split()`：按照指定字符分割字符串

- 基本语法：

	- `字符串序列.split(分割字符, 分割次数)`

	- 如果不写分割字符，使用默认分隔符（任何空白字符）

	- 如果不写分割次数，默认全部按照分割字符分割

	- 返回值为一串列表，列表中的元素为分割出来的子串

	- 案例演示：

		```python
		str1 = 'apple,orange,banana'
		
		print(str1.split(','))		# ['apple', 'orange', 'banana']
		print(str1.split(',', 1))	# ['apple', 'orange,banana']
		print(str1.split('#'))		# ['apple,orange,banana']
		```

		

## 5、获取字符串的长度

`len()`：返回字符串的长度

```python
str1 = 'qwert'
print(len(str1))	# 5
```





## 6、字符串大小写转换

1. **`lower()`**：将字符串中的所有字符转换为小写。

	- 示例：

		```python
		text = "Hello, World!"
		print(text.lower())  # 输出 "hello, world!"
		```

2. **`upper()`**：将字符串中的所有字符转换为大写。

	- 示例：

		```python
		text = "hello, world!"
		print(text.upper())  # 输出 "HELLO, WORLD!"
		```

3. **`capitalize()`**：将字符串的第一个字符转换为大写，其余字符转换为小写。

	- 示例：

		```python
		text = "hello, world!"
		print(text.capitalize())  # 输出 "Hello, world!"
		```

4. **`title()`**：将字符串中的每个单词的首字母转换为大写，其余字母转换为小写（类似标题格式）。

	- 示例：

		```python
		text = "hello, world!"
		print(text.title())  # 输出 "Hello, World!"
		```

5. **`swapcase()`**：将字符串中的大写字母转换为小写，小写字母转换为大写。

	- 示例：

		```python
		text = "Hello, World!"
		print(text.swapcase())  # 输出 "hELLO, wORLD!"
		```















