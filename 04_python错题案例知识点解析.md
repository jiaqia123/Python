# `python`错题案例知识点解析

```python
# 从string导入punctuation（标点）  punctuation包含英文中所有标点符号
from string import punctuation

def count_len(l):
    # write your codes here...
    c = 0
    for word in s.split():		# split() 用于切割字符串，返回列表
        if len(word.strip(punctuation)) == l:		# strip()用于删除字符串中所有的指定字符，
            c += 1									#	如punctuation中所有英文标点
    return c
s = '''
    Beautiful is better than ugly.
    Explicit is better than implicit.
    Simple is better than complex.
    Sparse is better than dense.
    '''
l = eval(input())
print(count_len(l))
```

