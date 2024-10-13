# Python推导式—列表集合字典

- 概述：
	- 推导式也叫解析式，是通过简单的代码实现，构建序列（容器）的操作
- 分类：
	- 列表推导式
	- 集合推导式
	- 字典推导式
- 作用：简化我们的代码
- 细节：
	- 元组没有推导式



## 一、列表推导式

- 格式：

	```python
	变量名 = [表达式 for 变量 in 列表 if 判断条件]
	```

- 代码演示：

	```python
	list1 = [i for i in range(10)]		# [0, 1, 2, 3, 4, 5, 6, 7, 8, 9]
	
	# 生成0~9之间偶数列表
	list2 = [i for i in range(0, 10, 2)]	# [0, 2, 4, 6, 8]
	# 或
	list3 = [i for i in range(10) if i % 2 == 0]	# [0, 2, 4, 6, 8]
	
	# 用列表推导式生成 [(0, 0), (0, 1), (0, 2), (1, 0), (1, 1), (1, 2)]
	list4 = [(i, j) for i in range(2) for j in range(3)] 
	```

	

## 二、集合推导式

- 格式：

	```python
	变量名 = {表达式 for 变量 in 列表 if 判断条件}
	```

- 用法与列表推导式一样，`[]`换成`{}`即可

- 细节：

	```python
	list1 = [1, 1, 2]
	set1 = {i**2 for i in list1}
	print(set1)		# {1, 4}	set自动去重
	```

	



## 三、字典推导式

- 目的：
	- 快速生成字典数据，或者对列表数据做合并

- 格式：

	```python
	变量名 = {键: 值 for 变量 in 列表 if 判断条件}
	```

- 代码演示：

	```python
	# 快速生成字典数据
	dict1 = {i: i**2 for i in range(1, 5)}		# {1: 1, 2: 4, 3: 9, 4: 16}
	
	# 合成两个列表 前提：两个列表的 元素个数 要一致
	list1 = ['name', 'age', 'gender']
	list2 = ['张三', 18, '男']
	
	dict1 = {list1[i]: list2[i] for i in range(len(list1))}
	print(dict1)		# {'name': '张三', 'age': 18, 'gender': '男'}
	```









































