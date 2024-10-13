# Python输入`input()`

**输入解释：**

- 概述：

	- 通过`input()`函数实现，接收用户录入的内容

- 细节：

	- 无论用户录入什么值，默认值是字符串类型，即：`str`类型

- 格式：

	- `变量名 = input("提示的内容")`

- 举例：

	- ```python
		age = input("请输入您的年龄：")
		# age接受input录入的值，即age为字符串类型
		print(type(age))	# <class 'str'>
		print(f"您的年龄是：{age}")
		print("您的年龄是：%s" % age)
		```

- 扩展：将字符串转为数字类型

	```python
	age = int(input("请输入您的年龄："))
	# age从字符串类型转为整型
	```

	