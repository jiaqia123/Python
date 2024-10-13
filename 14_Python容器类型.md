# `Python`容器类型

- 概述：
	- 容器类型指能同时存储多个元素的数据类型，按照特点不同，主要分为五种
- 分类：
	- 字符串：`str`
	- 列表：`list`
	- 元组：`tuple`
	- 字典：`dict`
	- 集合：`set`

- 特点：

	- 容器类型都可以存储多个元素
	- 容器类型中，每个元素都是有编号的（索引、下标），分为正向索引（从左往右，从0开始）和逆向索引（从右往左，从-1开始）

- 举例：

	```python
	# 字符串
	str1 = "abc"
	
	# 列表
	list1 = [10, 20, 30]
	
	# 元组
	tuple1 = (10, 20, 30, 40, 50
	          
	# 字典
	dict1 = {"name":"张三", 'age':18, 'gender':'男'}
	          
	# 集合
	set1 = {10, 20, 30}
	```

	

## 公共运算符

- `+`：合并，适用于：字符串，列表，元组

	```python
	print([1, 2, 3] + [10, 20, 30])		# [1, 2, 3, 10, 20, 30]
	print((1, 2, 3) + (10, 20, 30))		# (1, 2, 3, 10, 20, 30)
	print('abc' + 'xyz')		# 'abcxyz'
	```

	

- `*`：复制，适用于：字符串，列表，元组

	```python
	print([1, 2] * 2)		# [1, 2, 1, 2]
	print((11, 22) * 3)		# (11, 22, 11, 22, 11, 22)
	print('-' * 10)		# ----------
	```

	

- `in`：是否在（包含），适用于：字符串，列表，元组，字典，集合

	```python
	print(3 in [10, 20])  	# False
	print(3 in (3, 4))  	# True
	print('a' in 'abc') 		# True
	print('张三' in {'name': '张三', 'age': 18})	# False	因为in在字典中看的是键是否存在
	print(3 in {3, 4})		# True
	```

	

- `not in`：是否在（不包含），适用于：字符串，列表，元组，字典，集合

	```python
	print(3 not in [10, 20])  	# True
	print(3 not in (3, 4))  	# False
	print('a' not in 'abc') 		# False
	print('age' not in {'name': '张三', 'age': 18})	# False
	print(3 not in {3, 4})		# False
	```

	

## 公共的方法

- `len()`			获取长度

	```python
	list1 = [1, 2, 3]
	print(len(list1))	# 3
	```

	

- `del或者del()` 	 删除

	```python
	list1 = [1, 2, 3]
	
	del list1[0]
	print(list1)		# [2, 3]
	
	# 也可
	del(list1[0])		
	print(list1)		# [3]
	```

	

- `max()`            求最大值

	```python
	list1 = [1, 2, 3]		# 要求内容要统一且能计算
	print(max(list1))		# 3
	```

	

- `min() `            求最小值

	```python
	list1 = ['a', 'b', 'c']		# 要求内容要统一且能计算
	print(min(list1))		    # a	 字符/字符串 根据ASCII码值的大小比较
	```

	

- `range(start, end, step)`开始值，结束值，步长

	```python
	print(range(1, 6))		# range(1, 6)
	print(list(range(1,6)))		# [1, 2, 3, 4, 5]
	```

	

- `enumerate()`		将可迭代的数据对象，组成一个索引序列

	```python
	list1 = [11, 22, 33, 44, 55]
	
	for value in enumerate(list1):	# 将列表元素的 索引和数据值 封装成 元组 
	    print(value)		# (0, 11)  (1, 22) ...
	    
	for index, value in enumerate(list1):
	    print(index, value)		# 0 11    1 22 ...
	```

	





















































