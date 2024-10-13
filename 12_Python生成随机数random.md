# `Python`生成随机数`random`

在Python中生成随机数，可以使用**`random`模块**，这个模块提供了多种生成随机数的函数。

- 以下是几种常用的随机数生成方法：
	1. `random.random()`: 生成一个0到1之间的随机浮点数，**包括0但不包括1**
	2. `random.uniform(a, b)`: 生成一个在a和b之间的随机**浮点数**
	3. `random.randint(a, b)`: 生成一个在a和b之间（**包括a和b**）的随机**整数**
	4. `random.randrange(start开始, stop结束, step步长)`: 从指定范围内，按指定步长递增的集合中获取一个随机数，步长默认值为1
	5. `random.choice(sequence序列)`: 从**序列的元素**中随机挑选一个元素

- 示例代码如下：

	```python
	import random
	
	# 生成一个0到1之间的随机浮点数
	print(random.random())
	
	# 生成一个在1和10之间的随机浮点数
	print(random.uniform(1, 10))
	
	# 生成一个在1和10之间的随机整数
	print(random.randint(1, 10))
	
	# 生成一个在0和20之间，步长为2的随机数
	print(random.randrange(0, 20, 2))
	
	# 从列表中随机选择一个元素
	my_list = ['apple', 'banana', 'cherry']
	print(random.choice(my_list))
	```

	