# Python文件操作

- 概述：
	- 文件指的是File，即：为了方便硬盘管理数据和快速检索数据，而提出的概念
	- 根据数据格式的不同，文件主要划分为：`*.avi`，`*.txt`，`*.excel`，`*.doc`...
- 路径介绍：
	- 根据路径来锁定文件，从而对文件进行相应的操作
	- 分类：
		- 相对路径：`1.txt`，相对当前项目所在的路径
		- 绝对路径：固定的，写死的路径
- 细节：
	- Python中路径可以用`/`或者`\\`来表示，例如：`d:/abc/1.txt`	或	`d:\\abc\\1.txt`
	- 也可直接用`r`包裹路径，`r`是消除转义的意思，例如：`r'd:\abc\1.txt'`、
	- 关于路径的两个特殊格式



## 一、打开文件`open`

- 格式：

	- `文件对象名 = open(path, mode)`

- 格式解释：

	- `path`：要操作的文件的路径，可以写相对路径 或 绝对路径
	- `mode`：操作文件的模式，例如：`r,w,a`：只读，只写，追加，`rb,wb,ab`：以二进制形式，只读，只写，追加

- 相关名词解释：

	- `file`：文件
	- `line`：行
	- `read`：读
	- `write`：写
	- `append`：追加
	- `binary`：二进制
	- `close`：关闭（文件对象），释放资源

- 代码演示：

	```python
	# 只读方式打开文件
	f = open('1.txt', 'r')	# 相对路径写法
	
	# 读取文件所有内容并打印
	data = f.read()
	print(data)
	
	# 关闭文件
	f.close()
	```

	```python
	# 绝对路径写法
	f = open(r'D:\python\Python重生学习之路\1.txt', 'r')
	# 注意：此处r'绝对路径'中，r的作用是取消\转义
	
	# 也可
	f = open('D:\\python\\Python重生学习之路\\1.txt', 'r')
	
	# 还可
	f = open('D:/python/Python重生学习之路/1.txt', 'r')
	```

	

## 二、读取文件

- 概述：

	- 通过`open()`函数获取到文件对象，然后读取文件中的内容

- 读 相关函数：

	- `read(n)`：一次读取`n`个字节的数据，如果不写`n`，则默认读取所有

		```python
		f = open('1.txt', 'r')
		
		data1 = f.read(3)	# 读取3字节的数据，注意：末尾的\n也算一字节的数据，如果读取到了，发生换行操作
		data2 = f.read()		# 读取全部内容
		
		f.close()
		```

		

	- `readline()`：一次读取一行数据，结束标记是：`\n`，注意：读取整行数据，包括结尾的`\n`

		```python
		f = open('1.txt', 'r')
		
		data1 = f.readline()	# 读取第一行数据，包括末尾的\n
		data2 = f.readline()	# 接着读取下一行
		
		f.close()
		```

		

	- `readlines()`：一次读取所有行的数据，封装成列表，列表的每个元素，就是具体的每一行

		```python
		f = open('1.txt', 'r')
		
		data = f.readlines()	# 读取所有行数据，封装成列表，同样包括末尾的\n
		
		# data目前是列表，接下来就可以遍历data
		for line in data:
		    print(line, end='')	# line末尾自带\n会换行，因此不需要print()再次换行，end=''即可
		
		f.close()
		```



## 三、写文件

- 概述：

	- 把数据写到文件中，可以结合`w，a`模式实现
	- `w`模式：覆盖写入
	- `a`模式：追加写入

- 细节：

	- 如果写入文件不存在，会自动创建

- 函数：

	- `write(数据)`：把内容写到文件中，只能传入一个值（字符串）

	  ```python
	  # 只写方式打开文件/创建文件
	  f = open('1.txt', 'w')
	  
	  f.write('hello world!')		# hello world!
	  
	  # f.write(['abc', '10', 'qwert'])	# 报错
	  
	  f.close()
	  
	  
	  # 追加方式打开文件/创建文件
	  f = open('1.txt', 'a')
	  
	  f.write('hello world!')		# hello world!
	  
	  # f.write(['abc', '10', 'qwert'])	# 报错
	  
	  f.close()
	  ```
	
	  
	
	- `writelines(可以迭代的容器类型)`：把容器中的数据写到文件中
	
		```python
		# 只写方式打开文件/创建文件
		f = open('1.txt', 'w')
		
		f.writelines(['abc', '10', 'qwert'])	# abc10qwert
		# 接着往后写
		f.writelines('hello world!')		# abc10qwerthello world!
		
		f.close()
		
		
		# 追加方式打开文件/创建文件
		f = open('1.txt', 'a')
		
		f.writelines(['abc', '10', 'qwert'])	# abc10qwert
		# 接着往后写
		f.writelines('hello world!')		# abc10qwerthello world!
		
		f.close()
		```
	
	

## 四、自动关闭文件`with open`

- 概述：

	- `with open`会在语句结束时实现自动关闭文件，不需要手动`close()`

- 格式：

	- `with open(path, mode) as 文件对象名:`

- 演示：

	```python
	with open('1.txt', 'r') as f:
	    data = f.read()
	    print(data)
	    # 这里就不需要f.close()关闭文件了，with open会自动回收文件对象
	```

	

## 五、读取写入中文

- 概述：

	- Python读取写入文件中的中文默认会报错，可以在打开文件时修改文件**编码方式**来实现中文的读取

- 例如：

	```python
	# 读取中文
	f = open('2.txt', 'r', encoding='utf-8')	# 将编码方式改成utf-8（万国码）
	
	data = f.read()
	print(data)
	
	f.close()
	
	# 用with open打开
	with open('1.txt', 'r', encoding='utf-8') as f:
	    data = f.read()
	    print(data)
	    
	# 写入中文
	f = open('1.txt', 'w', encoding='utf-8')
	f.write('你好')
	f.close()
	```

	

## 六、文件拷贝

#### 1、拷贝文本文件

```python
# 逐行拷贝，大小文件均适用
f1 = open('1.txt', 'r', encoding='utf-8')
f2 = open('2.txt', 'w', encoding='utf-8')

while True:
    line = f1.readline()	# 一次读一行
    if line == '':	# 如果没有读到数据，说明读完了，结束
        break
    f2.write(line)
    
f1.close()
f2.close()

# 使用with open实现
with open('1.txt', 'r', encoding='utf-8') as f1, open('2.txt', 'w', encoding='utf-8') as f2:
    while True:
        line = f1.readline()	# 一次读一行
        if line == '':	# 如果没有读到数据，说明读完了，结束	也可以len(line) == 0
            break
        f2.write(line)
```

#### 2、拷贝任意类型的文件

**注意：**`r,w,a`方式可以结合`encoding(码表)`使用，`rb,wb,ab`不能结合码表使用，因为它们是直接操作二进制的

```python
# 第一种写法with open
with open('a.jpg', 'rb') as f1, open('b.jpg', 'wb') as f2:
    while True:
        # 做法：一次读取固定个字节数，字节数一般是1024的整数倍
        data = f1.read(1024)
        if len(data) == 0:	# 如果没有读取到，说明读完了，结束
            break
        f2.write(data)
        
# 第二种写法open
f1 = open('a.jpg', 'rb')
f2 = open('b.jpg', 'wb')

while True:
    data = f1.read(1024)	# 一次读取固定个字节数，字节数一般是1024的整数倍
    if len(data) == 0:	# 如果没有读到数据，说明读完了，结束
        break
    f2.write(data)
    
f1.close()
f2.close()
```













