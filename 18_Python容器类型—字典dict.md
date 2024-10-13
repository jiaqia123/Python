# Python容器类型—字典`dict`

- 概述：

	- 字典也是容器类型的一种，可以存储多个元素，每个元素都是**键值对形式**，左边的叫键，右边的叫值，**键和值**之间用**冒号:**隔开，**键值对**之间用**逗号,**隔开

- 定义格式：

	```python
	dict1 = {键:值, 键:值, 键:值...}
	dict2 = {}
	dict3 = dict()
	```

- 细节：

	- 字典存储的是键值对类型的数据，其中：**键具有唯一性**，**值可以重复**

	- 即：**键**可以是`int`，`str`，元组等，不能是列表类型，因为列表是可变的

		```python
		dict1 = {10:'张三', 10.3:'李四', True:[1, 2, 3], 'abc':123, (10, 20):[1, 2, 3]}		# 没问题
		
		dict2 = {[10, 20]:123}		# 报错，键不能是列表类型
		
		dict3 = {10:'张三', 10:(1, 2)}	# 报错，键要具有唯一性
		
		dict4 = {True:[1, 2, 3], (10, 20):[1, 2, 3]}	# 没问题，值可以重复
		```

	- **字典不支持索引**获取值，想要获取字典中的值，只能通过键，键不存在就报错

		```python
		dict1 = {10:'张三', 10.3:'李四', True:[1, 2, 3], 'abc':123, (10, 20):[1, 2, 3]}
		
		print(dict1[True])		# [1, 2, 3]
		print(dict1['abc'])		# 123
		
		print(dict1[2])		# 报错，键不存在，且不支持索引获取值
		```

	- `len()`：统计字典的键值对的对数

		```python
		dict1 = {10:'张三', 10.3:'李四', True:[1, 2, 3], 'abc':123, (10, 20):[1, 2, 3]}
		
		print(len(dict1))		# 5
		```




## 字典的增删改查

#### 1、增/改

`字典名[键] = 值`：如果键存在，就用新值覆盖旧值。如果键不存在，就添加该键值对

```python
d1 = {'name':'张三', 'age':18, 'gender':'男'}

d1['height'] = 188		# 键不存在，添加键值对，在字典末尾添加
print(d1)		# {'name':'张三', 'age':18, 'gender':'男', 'height':188}

d1['name'] = '李四'		# 键存在，修改对应的值
print(d1)		# {'name':'李四', 'age':18, 'gender':'男', 'height':188}
```

#### 2、删

- `del 字典名[键]`：根据键，删除键值对，键不存在会报错

	```python
	d1 = {'name':'张三', 'age':18, 'gender':'男'}
	
	del d1['age']		# 根据键删除键值对
	print(d1)		# d1 = {'name':'张三', 'gender':'男'}
	
	del d1		# 删除字典，相当于从内存中将字典删除
	print(d1)	# 字典不存在 报错
	```

- `clear()`：清空字典，相当于删除所有的键值对，但是字典对象还在

	```python
	d2 = {'name':'张三', 'age':18, 'gender':'男'}
	
	d2.clear()		# 删除所有的键值对，清空字典内容，字典还存在
	print(d2)		# {}
	```



#### 3、查

- `get(键, 默认值)`：根据键获取对应的值，找不到就返回默认值，默认值不写就返回`None`

	```python
	d1 = {'name':'张三', 'age':18, 'gender':'男'}
	
	# 根据键获取值
	print(d1['name'])		# 张三
	print(d1['phone'])		# 找不到该键，报错
	
	#使用get()查找值
	print(d1.get('name'))		# 张三
	print(d1.get('phone'))		# 找不到该键，返回默认值None
	print(d1.get('phone', '188'))	# 找不到该键，返回'188'
	```

- `keys()`：获取所有的 键

	```python
	d1 = {'name':'张三', 'age':18, 'gender':'男'}
	
	print(d1.keys())	# dict_keys(['name', 'age', 'gender'])
	```

- `values()`：获取所有的 值

	```python
	d1 = {'name':'张三', 'age':18, 'gender':'男'}
	
	print(d1.values())		# dict_values(['张三', 18, '男'])
	```

- `items()`：获取所有的 键值对，封装成列表，每个键值对形成一个元组

	```python
	d1 = {'name':'张三', 'age':18, 'gender':'男'}
	
	print(d1.items())		# dict_items([('name', '张三'), ('age', 18), ('gender', '男')])
	# 列表嵌套元组，一个键值对形成一个元组
	```

	

## 字典的遍历

#### 1、根据键获取对应的值

```python
d1 = {'name':'张三', 'age':18, 'gender':'男'}

for key in d1.keys():
    value = d1.get(key)
    print(f"{key} = {value}")
```

#### 2、根据键值对获取键和值

```python
d1 = {'name':'张三', 'age':18, 'gender':'男'}

for k, v in d1.items():		# k表示键，v表示值
    print(f"{k} = {v}")
```























