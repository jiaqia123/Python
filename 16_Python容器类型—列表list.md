# Python容器类型—列表`list`

## 一、列表定义

- 概述：
	- 列表（`list`）是一种有序的集合数据类型，可以包含**不同类型的元素**，如整数、浮点数、字符串、其他列表等。
	- 列表是动态的，可以随时**添加**、**删除**、**修改**、**查找**其中的元素，因此列表为**可变数据类型**
	- 列表的索引从**0**开始，可以通过**索引**来访问和修改列表中的特定元素。

- 基本语法：

	- 列表名称 = [数据1, 数据2, 数据3, ...]
	- 变量名 = `list()`    （定义一个空的列表）

- 案例演示：

	```python
	# 使用方括号创建列表
	my_list = [1, 2, 3, 4, 5]
	
	# 使用 list() 函数创建列表，一般不用
	another_list = list((6, 7, 8, 9, 10))
	```

- 特殊的定义方式

	```python
	list1 = [i for i in range(1, 6)]		# [1, 2, 3, 4, 5]
	
	list2 = list(range(1, 6))		# [1, 2, 3, 4, 5]
	```

	

## 二、访问和修改列表元素

通过索引可以访问列表中的元素，负数索引表示从列表末尾开始计数。可以直接通过索引赋值来修改列表中的元素。

```python
my_list = [1, 2, 3, 4, 5]

# 访问列表元素
print(my_list[0])  # 输出 1
print(my_list[-1])  # 输出 5

# 修改列表元素
my_list[1] = 10  # 将第二个元素修改为 10

# my_list = [1, 10, 3, 4, 5]
```



## 三、列表遍历

- 概述：所谓遍历，指的是：逐个获取并打印列表每一个值

- 代码演示：

	```python
	list1 = [11, 22, 33, 44, 55]
	
	# 遍历列表
	# for 遍历
	for value in list1:
	    print(value)
	
	# while 遍历
	i = 0
	whlie i < len(list1):	# len(list1)获取列表长度
	    print(list1[i])
	    i += 1



## 四、列表常规操作—增删改查

### 1、添加元素

- `append()` 方法在列表**末尾**添加**一个**元素

	```python
	list1 = [10, 20, 30]
	list1.append(True)		
	print(list1)		# [10, 20, 30, True]
	```

- `extend()`方法在列表**末尾**添加**一组**元素（该元素必须可迭代，即可遍历）

	```python
	list1 = [10, 20, 30]
	list2 = ['abc', 40, False]
	
	list1.extend(list2)		
	print(list1)		# [10, 20, 30, 'abc', 40, False]
	
	# 如果用append() 结果为 [10, 20, 30, ['abc', 40, False]]
	
	# 可添加字符串'xyz'，因为其可迭代
	list1.extend('xyz')		
	print(list1)		# [10, 20, 30, 'abc', 40, False, 'x', 'y', 'z']
	
	# 不可添加任意数字，因为其不可迭代
	list1.extend(10)	# 报错
	```

- `insert(索引, 元素)` 方法在**指定位置**插入元素

	```python
	list1 = [10, 20, 30]
	
	list1.insert(1, 200)	# 在索引为1的位置上添加200
	print(list1)		# [10, 200, 20, 30]
	
	list1.insert(100, 200)	# 在索引为100的位置上添加200，但列表索引没有达到100，就会直接在列表末尾添加该元素
	print(list1)		# [10, 200, 20, 30, 200]
	```

	

### 2、删除元素

- `del`直接删除列表，也可删除指定元素

	- `del 列表名`：直接删除**整个列表**，列表不存在了

		```python
		list1 = [10, 20, 30, 40, 50]
		
		del list1
		print(list1)	# 报错，在内存中找不到list1，因为被删除了
		```

	- `del 列表名[索引]`：根据索引删除**指定位置**元素

		```python
		list1 = [10, 20, 30, 40, 50]
		
		del list1[2]
		print(list1)	# [10, 20, 40, 50]
		```

- `pop(索引)` ：根据索引删除**指定位置**的元素，不写索引，默认删除最后一个，并返回该数据

	```python
	list1 = [10, 20, 30, 40, 50]
	
	print(list1.pop(2))		# 30
	print(list1)	# [10, 20, 40, 50]
	
	print(list1.pop())		# 50
	print(list1)		# [10, 20, 40]
	```

-  `remove(元素值)` ：根据元素值删除元素，删除**第一个**匹配的元素

	```python
	list1 = [10, 20, 30, 20, 30]
	
	list1.remove(20)
	print(list1)		# [10, 30, 20, 30]
	```

- `clear()`：清空列表，列表中的元素没了，但列表还在

	```python
	list1 = [10, 20, 30, 20, 30]
	
	list1.clear()
	print(list1)	# []
	```

	

### 3、修改元素

- 通过下标直接修改：`列表变量名[索引] = 值`

	```python
	list1 = [10, 20, 30, 40, 50]
	list1[1] = 200
	print(list1)		# [10, 200, 30, 40, 50]
	
	list[100] = 10		# 报错，超出列表范围
	```

- **列表排序**：使用 `sort()` 方法对列表进行排序，默认升序，可以指定参数 `reverse=True` 进行降序排序

	```python
	list1 = [10, 40, 30, 20, 50]
	
	# sort()默认升序
	list1.sort()
	print(list1)		# [10, 20, 30, 40, 50]
	
	# sort()降序排序
	list1.sort(reverse=True)	# reverse:True反转，reverse:False不反转（默认值）
	print(list1)		# [50, 40, 30, 20, 10]
	
	# 降序排序另一种写法
	list1.sort()
	list1.reverse()
	print(list1)		# [50, 40, 30, 20, 10]
	```

- **列表反转**：使用 `reverse()` 方法将列表中的元素顺序反转

	```python
	# reverse()反转
	list1 = [10, 40, 30, 20, 50]
	list1.reverse()
	print(list1)		# [50, 20, 30, 40, 10]
	
	# 切片反转
	list1 = [10, 40, 30, 20, 50]
	list2 = list1[::-1]		# 切片不会改变原来列表的元素，只会将切出来的结果返回
	print(list2)		# [50, 20, 30, 40, 10] 
	print(list1)		# [10, 40, 30, 20, 50]
	```

	

### 4、查找元素

`in，not in，index，count`

- `index(元素值, 起始索引, 结束索引)`：查找元素在列表中，第一次出现的位置（索引）,找不到就报错

	```python
	list1 = [20, 30, 10, 'abc', '张三', 10.3, 20, 10, 'abc']
	
	print(list1.index(10))		# 2
	print(list1.index(10, 3, 7))	# 报错，索引范围包左不包右
	print(list1.index(10, 3))	# 7
	```

- `count(元素值)`：统计元素值在列表中出现的次数

	```python
	list1 = [20, 10, 10, '10', '张三', 10.3, 20, 10, 'abc']
	
	print(list1.count(10))		# 3
	print(list1.count('10'))		# 1
	```

	

- `元素值 in 列表变量名`：判断元素值在列表中是否存在

	```python
	list1 = ['10', '张三', 10.3, 20, 10, 'abc']
	
	print('张三' in list1)	# True
	print('李四' in list1)	# False
	```

- `元素值 not in 列表变量名`：判断元素值在列表中是否不存在

	```python
	list1 = ['10', '张三', 10.3, 20, 10, 'abc']
	
	print('张三' not in list1)	# False
	print('李四' not in list1)	# True
	```

	

### 5、补充列表切片

- **列表切片：**使用切片语法 `list[start:end:step]` 来获取列表的子集

- **注意：**列表切片不改变原列表，会返回切出来的列表

	```python
	list1 = [10, 20, 30, 40, 50]
	
	list2 = list1[2:4]	   	# 包左不包右
	print(list2)		# [30, 40]
	
	list3 = list1[::2]
	print(list3)	# [10, 30, 50]
	
	list4 = list1[::-1]
	print(list4)		# [50, 40, 30, 20, 10]
	
	print(list1)	# [10, 20, 30, 40, 50]
	```

	

## 五、列表的嵌套

- 概述：

	- 列表嵌套指的是列表元素还是列表

- 格式：

	- `list1 = [[1, 2, 3], [4, 5], [6, 7, 8, 9]]`

- 代码演示：

	```python
	list1 = [[1, 2, 3], [4, 5], [6, 7, 8, 9]]
	
	print(list1[1][1])		# 5
	print(list1[0])		# [1, 2, 3]
	```

	





























