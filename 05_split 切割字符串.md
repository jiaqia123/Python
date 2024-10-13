# `split`切割字符串

`split` 方法在 Python 的字符串处理中非常实用，主要用于将字符串分割成**列表**

1. **基本用法**：

	- `str.split(sep=None, maxsplit=-1)`
	- `sep` 参数用于指定分隔符，默认为**任何空白字符**（如空格、换行符、制表符等）。
	- `maxsplit` 参数用于指定分割次数，如果省略或为负数，则会进行所有可能的分割。

2. **示例**：

	- 无参数使用，使用默认分隔符（任何空白字符）：

		```python
		text = "Hello world"
		print(text.split())  # 输出：['Hello', 'world']
		```

	- 指定分隔符：

		```python
		text = "one,two,three"
		print(text.split(','))  # 输出：['one', 'two', 'three']
		```

	- 指定分割次数：

		```python
		text = "one,two,three,four,five"
		print(text.split(',', 2))  # 输出：['one', 'two', 'three,four,five']
		```

3. **注意事项**：

	- 当 `sep` 是空字符串时，`split` 会抛出 `ValueError`。
	- 如果 `sep` 在字符串中不存在，则返回的列表只有一个元素，即原字符串。

4. **使用场景**：

	- 处理 CSV 数据。
	- 将地址、日期等复合字符串分割为更小的组件。
	- 从字符串中提取特定的值或信息。

通过 `split` 方法，你可以非常灵活地处理和解析字符串数据。