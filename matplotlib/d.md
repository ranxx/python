# 直方图

### 绘制直方图
```python
	import matplotlib.pyplot as plt
	"""
		绘制直方图, 
		bins-代表分为多少组, 
		normed-代表是否绘制频率分布直方图, 默认为频率直方图
	"""
	plt.hist(x, bins=y, normed=1)

	"""
		那么 将数据分为多少组进行统计???
		组数要适当, 太少会有较大的统计误差, 太多规律不明显
		组数: 将数据分组, 当数据在100个以内时, 按数据多少常分为 5-12 组.
		组距: 指每个小组的两个端点的距离

		组数 = 

	"""



```

### <font color=red>关于组数</font>

+ <font color=red >组数要适当, 太少会有较大的统计误差, 太多规律不明显</font>
+ **组数: 将数据分组, 当数据在100个以内时, 按数据多少常分为 5-12 组**
+ **组距: 指每个小组的两个端点的距离**
> <font color=red>一般组数=极差/组距</font>
