# 认识pandas

### 为什么要学习pandas

numpy能帮我们处理数值型数据, 但是pandas除了处理数值之外(基于numpy), 还能够帮我们处理其他类型的数据


### 什么是pandas

pands is an open source, BSD-licensed library providing high-performance, easy-to-use data structures and data analysis tools for the Python programming language.

### pandas常用的数据类型

1. Series -维, 带标签数组
2. DataFrame 二维, Series容器

### 创建Series

```python
	import pandas as pd
	import numpy as np
	import string

	t = pd.Series(np.arange(10), index=list(string.ascii_uppercase[:10]))
```

### Series切片和索引

```python
	t[1]
	t[2:10:2]
	t[[2, 5]]
	t[t>4]
	t[["A","C"]]
	t["F"]
	t.index
	t.values
```

**Series对象本质上由两个数组构成, 一个数组构成对象的键(index, 索引), 一个数组构成对象的值(values), 键 -> 值**

**ndarray的很多方法都可以运用与series类型, 比如argmax, clip**

**<font color=red>series具有where方法, 但是结果和ndarray不同</font>**










