# Python_`global`全局变量关键字

- 概述：
	- 可以标记 局部变量 为 全局变量，格式为：`global 变量名`

- 细节：

	- 使用变量遵循“就近原则”

- 代码演示：

	```python
	def func1():
	    global a 	# 将a设置成全局变量
	    a = 10
	    print(a)
	
	func1()		# 10
	print(a)	# 10
	```

	