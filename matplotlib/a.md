# 折线图

### 第一个折线图例子

> 哈哈
> ## 这是一个标题
>
>> 1. 看看就好 😝
>> 3. 哈哈



*	好哈
	握草
	你们
		```python
			print("hello")
		```
	1996\. 啊啊
	<http://www.baidu.com>
	<112@qq.com>


```python

	# conding=utf-8
	"""
	用列表a 表示10点 到 12点 每分钟的气温
	用折线画出来
	"""

	import random as rand   # 随机数
	import matplotlib.pyplot as plt    
	import matplotlib.font_manager as fnt    # 字体管理

	rand.seed(10)   # 设置随机种子
	a = [rand.randint(20, 35) for i in range(120)]   # 随机120分钟内的温度
	print(a)

	b = range(1, 121)    # 初始化 x 轴 代表 1 - 120 分钟
	print(b)

	plt.figure(figsize=(20, 8), dpi=80)   # 设置图片的大小, 清晰度, 这个作用于全局

	_xlable = ["10点{}分".format(i) for i in range(60)]
	_xlable += ["11点{}分".format(i) for i in range(60)]

	# 步长
	step=5

	"""
	 fc-list 查看
	 fname=字体路径
	 mac 上可以在字体管理里面查看字体的位置
	 linux 下可以用 fc-list, 或者 fc-list :lang=zh查看支持中文的字体
	"""
	font = fnt.FontProperties(fname="/Library/Fonts/Songti.ttc")

	"""
	 当刻度太密集. 可以使用列表的步长(间歇取值)来解决
	 两个数据的长度必须一样, 否则不能完全覆盖整个轴
	 当然还可以用 rotation 旋转以防被覆盖
	"""
	plt.xticks(list(b)[::step], _xlable[::step],rotation=90, fontproperties=font)

	# 绘图
	plt.plot(b, a)

	# 显示
	plt.show()

```

### 第一个折线图例子

```python

	# conding=utf-8
	"""
	用列表a 表示10点 到 12点 每分钟的气温
	用折线画出来
	"""

	import random as rand   # 随机数
	import matplotlib.pyplot as plt    
	import matplotlib.font_manager as fnt    # 字体管理

	rand.seed(10)   # 设置随机种子
	a = [rand.randint(20, 35) for i in range(120)]   # 随机120分钟内的温度
	print(a)

	b = range(1, 121)    # 初始化 x 轴 代表 1 - 120 分钟
	print(b)

	plt.figure(figsize=(20, 8), dpi=80)   # 设置图片的大小, 清晰度, 这个作用于全局

	_xlable = ["10点{}分".format(i) for i in range(60)]
	_xlable += ["11点{}分".format(i) for i in range(60)]

	# 步长
	step=5

	"""
	 fc-list 查看
	 fname=字体路径
	 mac 上可以在字体管理里面查看字体的位置
	 linux 下可以用 fc-list, 或者 fc-list :lang=zh查看支持中文的字体
	"""
	font = fnt.FontProperties(fname="/Library/Fonts/Songti.ttc")

	"""
	 当刻度太密集. 可以使用列表的步长(间歇取值)来解决
	 两个数据的长度必须一样, 否则不能完全覆盖整个轴
	 当然还可以用 rotation 旋转以防被覆盖
	"""
	plt.xticks(list(b)[::step], _xlable[::step],rotation=90, fontproperties=font)

	# 绘图
	plt.plot(b, a)

	# 显示
	plt.show()

```

