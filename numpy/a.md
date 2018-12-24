# 创建数组

### 1、创建数组(矩阵)

**np.arange与np.array**

```python
	import numpy as np
	a = np.array([1,2,3,4,5])
	b = np.array(range(1, 6))
	c = np.arange(1, 6)
```

+ <font color=red >注意: 上面的a, b, c 内容相同, 注意arange和range的区别</font>
+ np.arange的用法: arange([start,] stop[, stop,], dtype=None)

**查看数组的类名**

```python
	In [2]: a = np.array([1,2,3])
	In [3]: type(a)
	Out[3]: numpy.ndarray
```

**查看数据的类型**

```python
	In [6]: a.dtype
	Out[6]: dtype('int64')
```

### 2、Numpy中常见的更多数据类型

![numpy中常见的更多数据类型](img/numpy中常见的更多数据类型.png "numpy中常见的更多数据类型")

**指定创建的数组的数据类型**

```python
	In [7]: a = np.array([1, 2, 3], dtype=np.bool) # 或者使用 dtype='?'
	In [8]: a
	Out[8]: array([ True,  True,  True])
```

**修改数组的数据类型**

```python
	In [9]: a.astype(np.int8)  # 或者使用 a.astype('i1')
	Out[9]: array([1, 1, 1], dtype=int8)
```

**修改浮点型的小数位数**

```python
	In [12]: a = np.array([0.212, 0.54589454, 0.65823])
	In [13]: np.round(a, 1)  # 保留一位小数
	Out[13]: array([0.2, 0.5, 0.7])
```

### 3、数组的形状

**查看数组的形状**

```python
	In [14]: a.shape
	Out[14]: (3,)
```

**修改数组的形状**

```python
	In [15]: a.reshape(3, 1)
	Out[15]: 
	array([[0.212     ],
	       [0.54589454],
	       [0.65823   ]])
```

**把数组转化为1维数据**

```python
	In [16]: a.reshape(3)
	Out[16]: array([0.212     , 0.54589454, 0.65823   ])
	# 或者
	In [17]: a.flatten()
	Out[17]: array([0.212     , 0.54589454, 0.65823   ])
```

### 4、数组和数的计算

**加法减法**

```python
	In [18]: a = np.arange(6)
	In [19]: a
	Out[19]: array([0, 1, 2, 3, 4, 5])
	In [20]: a + 1
	Out[20]: array([1, 2, 3, 4, 5, 6])
```

**乘法除法**

```python
	In [21]: a * 5
	Out[21]: array([ 0,  5, 10, 15, 20, 25])
```

> **这是一个numpy的[广播机制](#广播原则)造成的, 在运算过程中, 加减乘除的值被广播到所有元素上面**

**数组和数组的加减**

```python
	In [23]: a 
	Out[23]: array([0, 1, 2, 3, 4, 5])
	In [24]: a + a
	Out[24]: array([ 0,  2,  4,  6,  8, 10])
	In [28]: b
	Out[28]: array([0, 1, 2, 3, 4])
	In [29]: a + b  # 这里 a 和 b shape 完全不一样
	---------------------------------------------------------------------------
	ValueError                                Traceback (most recent call last)
	<ipython-input-29-bd58363a63fc> in <module>()
	----> 1 a + b

	ValueError: operands could not be broadcast together with shapes (6,) (5,)
```

**数组和数组的乘除**

```python
	In [32]: a * a
	Out[32]: array([ 0,  1,  4,  9, 16, 25])
```

**<font color=red >这里需要注意的是不同维度是不能进行计算的 如shapes (3, 4) (5, 6), 至少有有一个维度</font>**

_<span id="广播原则">广播原则</span>_
> 如果两个数组的后缘维度(trailing dimension, 即从末尾开始算起的维度) 的轴长度相符或其中一方的长度为1, 则认为她们是广播兼容的. 广播会在缺失和(或)长度为1的维度上进行

### 5、轴(axis)

在numpy中可以理解为方向, 使用0, 1, 2 ...数字表示, 对于一个一位维数组, 只有一个0轴, 对于2维数组(shape(2,2)), 有0轴和1轴, 对于三维数组(shape(2,2,3)), 有0, 1, 2轴

有了轴的概念之后, 我们计算会更加方便, 比如计算一个2维数组的平均值, 必须指定是计算哪个方向上面的数字的平均值

**二维数组的轴**

![二维数组的轴](img/二维数组的轴.png "二维数组的轴")

**三维数组的轴**

![三维数组的轴](img/三维数组的轴.png "三维数组的轴")

### 6、读取和存储数据

_CSV_
> CSV: Comma-Separated Value, 逗号分隔值文件

> 显示: 表格状态

> 源文件: 换行和逗号分隔行列的格式化文本, 每一行的数据表示一条记录

> 由于csv便于展示, 读取和写入, 所以很多地方也是用csv的格式存储和传输中小型的数据, 为了便于方便教学, 我们会经常操作csv格式的文件, 但是操作数据库中的数据也是很容易实现的


**读取np.loadtxt(frame, dtype=np.float, delimiter=None, skiprows=0, usecols=None, unpack=False)**

参数|解释
:---:|:--:
frame|文件、字符串货产生器, 可以是.gz或bz2压缩文件
dtype|数据类型, 可选, csv的字符串以什么数据类型读入数组中, 默认 np.float
delimier| 分隔字符串, 默认是任何空格, 改为 逗号
skiprows|跳过前x行, 一般跳过第一行表头
usecols|读取指定的列, 索引, 元组类型
unpack|如果True,读入属性将分别写入不同数组变量, False读入数据只写入一个数组变量,默认False

### 7、Numpy中的转置(3种方式)

转置是一种变换, 对于numpy中的数组来说, 就是在对角线方向交换数据, 目的也是为了更方便的区处理数据
三种方式 `a.transpose()`, `a.swapaxes(1,0)`, `a.T`

以下为二维数组的转置
```json
	In [52]: a
	Out[52]: 
	array([[ 0,  1,  2,  3],
	       [ 4,  5,  6,  7],
	       [ 8,  9, 10, 11]])

	In [53]: a.transpose()     # 第一种
	Out[53]: 
	array([[ 0,  4,  8],
	       [ 1,  5,  9],
	       [ 2,  6, 10],
	       [ 3,  7, 11]])

	In [54]: a.swapaxes(1,0)   # 第二种
	Out[54]: 
	array([[ 0,  4,  8],
	       [ 1,  5,  9],
	       [ 2,  6, 10],
	       [ 3,  7, 11]])

	In [55]: a.T               # 第三种
	Out[55]: 
	array([[ 0,  4,  8],
	       [ 1,  5,  9],
	       [ 2,  6, 10],
	       [ 3,  7, 11]])

```




































