# Python函数

## 一、函数的基本介绍

- 概述：

	- 函数（`function`）也叫方法（`method`），就是把一些独立的功能封装起来，使其成为具有特定功能的代码集

- 作用：

	- 模块化编程
	- 代码重复，提高开发效率

- 格式：

	- ```python
		def 函数名(参数名1:数据类型, 参数名2:数据类型) -> 返回值的数据类型:
		    方法体
		    return 具体的返回值
		```

- 格式解释：

	- **`def`**：`defined`（定义），表示定义函数
	- **函数名**：用于函数的调用，一般用**蛇形命名法**，例如：`get_sum`
	- **参数名**：调用函数时，需要传入的数据，参数的数据类型可以省略不写
	- **返回值的数据类型**：表示函数执行完毕时返回的结果的类型，可以省略不写
	- **方法体**：简单的`if、while`等语句
	- **`return`**：1.用于结束方法    2.返回函数的执行结果

- 细节：

	- 函数必须先定义，然后才能调用
	- 函数与函数之间是平级关系，不能**嵌套定义**，但是函数之间可以**嵌套调用**

- 案例演示

	```python
	# 定义一个函数
	def get_sum(num1: int, num2: int) -> int:
	    return num1 + num2
	
	# 调用
	print(get_sum(1, 2))		# 3
	
	# 简化上述函数
	def get_sum(num1, num2):
	    return num1 + num2
	```

	

## 二、函数的说明文档

- 概述：书写在定义函数时的函数内部，用于对该函数解释说明

- 代码演示：

	```python
	def get_sum(num1, num2):
	    # 下面就是函数的说明文档，三对双引号
	    """
	    该函数用于实现计算两个数的和
	    :param num1:要求和的第一个数
	    :param num2:要求和的第二个数
	    :return:求和的结果 
	    """
	    return num1 + num2
	
	print(get_sum(1, 2))	# 3
	
	help(get_sum)	# 打印函数的说明文档
	```

	

## 三、函数嵌套调用

- 概述：

	- 函数嵌套指定是在1个函数体中，调用另1个函数，而不是定义另1个函数

- 执行流程：顺序执行

- 代码演示：

	```python
	def func1():
	    print('func1函数')
	    
	def func2():
	    print('func2函数')
	    # 嵌套调用func1函数
	    func1()
	    
	func2()		# func2函数  
				# func1函数
	```

	

## 四、函数返回多个值

- 概述：
	- 顾名思义，就是通过`return`返回多个值

- 格式：

	- `return a, b, c`  同时返回`a, b, c`三个值

- 细节：

	- `return`返回多个值时，是把这多个值封装成 **元组**，然后再返回的

- 案例演示：

	```python
	# 模拟计算器，接收2个数，分别返回两数 加减乘除 的结果
	def calc(a, b):
	    add = a + b
	    sub = a - b
	    mul = a * b
	    div = a / b
	    return add, sub, mul, div
	
	result = calc(10, 5)
	print(result, type(result))		# (15, 5, 50, 2.0) <class 'tuple'>
	```

	

## 五、函数参数详解

- 概述：
	- 根据写法不同，函数参数主要有：位置参数，关键字参数，不定长参数，缺省参数 四种写法
- 其中：
	- 位置参数，关键字参数 主要针对于 实参 来讲的
	- 不定长参数，缺省参数 主要针对于 形参 来讲的



#### 1、实参：位置参数，关键字参数

- 位置参数：参数个数、类型、顺序都要保持一致

	```python
	def func1(name, age, gender):
	    print(f"我叫{name}，今年{age}岁，性别{gender}")
	
	# 位置参数调用
	func1('张三', 18, '男')	# 参数个数、类型、顺序都要保持一致
	```

	

- 关键字参数：通过`参数名 = 值`的形式，将值精准的赋值给形参

	```python
	def func1(name, age, gender):
	    print(f"我叫{name}，今年{age}岁，性别{gender}")
	
	# 关键字参数调用
	func1(gender='男', age=18, name='张三') 		# 传入参数顺序没有要求
	```

- 细节：如果既有位置参数，又有关键字参数，则：位置参数在前，关键字参数在后，否则报错

	```python
	def func1(name, age, gender):
	    print(f"我叫{name}，今年{age}岁，性别{gender}")
	
	# 位置参数和关键字参数共同使用
	func1('张三', gender='男', age=18)		# 位置参数在前，关键字参数在后
	
	func1(gender='男', '张三', age=18)		# 报错
	func1('张三', name='李四', age=18)		# 报错
	func1(age=18, name='张三')		# 报错
	```

	

#### 2、形参：不定长参数，缺省参数

- 不定长参数：也叫可变参数，根据传入形式不同，分为 位置传递 和 关键字传递

	- 位置传递：传递的多个值，会被封装成 **元组**

		```python
		# 要求：写一个求和函数，能计算n个数的和
		# 这里可以使用 不定长参数 完成
		def get_sum(*args):		# args就是一个元组，内容由实参决定
		    sum = 0				# 细节：*args只能接收所有的 位置参数，封装成元组
		    for i in args:		# 格式：*变量名
		        sum += i
		    return sum
		
		print(get_sum())					# 0
		print(get_sum(1, 2))				# 3
		print(get_sum(10, 20, 30, 40))		# 100
		
		print(get_sum(10, 20, 30, a = 40))		# 报错，*args只能接收位置参数
		```

		

	- 关键字传递：传递的多个值，会被封装成 **字典**

		```python
		# 要求：定义函数 介绍自己
		def show(**kwargs):		# 格式：**变量名
		    print(kwargs, type(kwargs)) # **kwargs只能接收关键字参数，封装成字典
		
		show(name='张三', age=18, gender='man')
		# {'name': '张三', 'age': 18, 'gender': 'man'} <class 'dict'>
		
		show()		# {} <class 'dict'>
		
		show('张三', age=18, gender='man')	# 报错，**kwargs只能接收关键字参数
		```

		

- 缺省参数：也叫默认参数，即有默认值的形参，可以不用传递实参

	- 特点：调用函数时，用户传参就用传入的值，不传参，就用缺省值（默认值）

		```python
		def show(name, age, gender='male'):
		    print(f"我叫{name}，今年{age}岁，性别{gender}")
		
		# 不写gender，默认male
		show('张三', 18)		# 位置参数			我叫张三，今年18岁，性别male
		show(age=21, name='李四')	# 关键字参数	    我叫李四，今年21岁，性别male
		
		# 传入gender，用传入的值
		show('王五', 23, 'female')	# 我叫王五，今年23岁，性别female
		```

	

## 六、函数参数不可变类型和可变类型

#### 1、如果形参是不可变类型，则形参的改变，对实参没有任何影响

```python
a = 10

def func1(a):	# 这里a是整型，不可变类型
    a = 20

print(a)	# 10
func1(a)	# 调用函数使形参变成20，对实参没有影响
print(a)	# 10
```



#### 2、如果形参是可变类型，则形参的改变，直接影响实参

```python
list1 = [1, 2, 3]

def func1(list1):	# 这里list1是列表，可变类型
    list1[1] = 20

print(list1)	# [1, 2, 3]
func1(list1)	# 调用函数使list1[1]变成20，直接影响实参
print(list1)	# [1, 20, 3]

```



## 七、匿名函数

- 概述：

	- 没有名字的函数，类似于：`java`中的`lambda`表达式

- 作用：

	- 简化函数写法，提高代码开发效率，让程序更加灵活

- 格式：

	- `变量名 = lambda 形参1, 行参2: 返回值`

- 应用场景

	- 当函数仅调用1次的时候
	- 匿名函数 可以作为 函数的实参 进行传递

- 代码演示：

	```python
	# 当函数仅调用1次的时候
	sum1 = lambda a, b: a + b	# 匿名函数的定义，返回两数和
	print(sum1(10, 20))		# 30
	
	# 匿名函数作为函数的实参进行传递
	def method(a ,b, func):
	    result = func(a, b)
	    return result
					# 匿名函数作为函数的实参传递
	print(method(10, 3, lambda a, b: a + b))	# 13
	print(method(10, 3, lambda a, b: a - b))	# 7
	print(method(10, 3, lambda a, b: a * b))	# 30
	print(method(10, 3, lambda a, b: a // b))	#3
	```

	





































