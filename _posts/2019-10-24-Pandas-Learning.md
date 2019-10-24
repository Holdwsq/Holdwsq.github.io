---
layout: post
title:  "Pandas用法总结"
categories: MachineLearning
tags:  Pandas  
author: Wsq
---

* content
{:toc}

# Pandas 用法总结
**Pandas 简述：**

1. Pandas 是什么？
	Pandas是一个强大的分析结构化数据的工具集；它的使用基础是Numpy（提供高性能的矩阵运算）；用于数据挖掘和数据分析，同时也提供数据清洗功能。
2. 核心成员：
- DataFrame:是Pandas中的一个表格型的数据结构，包含有一组有序的列，每列可以是不同的值类型(数值、字符串、布尔型等)，DataFrame即有行索引也有列索引，可以被看做是由Series组成的字典。

**DataFrame主要成分：**
```python
class pandas.DataFrame(data=None, index=None, columns=None, dtype=None, copy=False)

Parameters(主要参数)：

data: 	常用的数据类型（ndarray (structured or homogeneous), Iterable, dict, or DataFrame）
index:  数组列表
		用于结果帧的索引。如果没有输入数据的索引信息部分，并且没有提供索引，那么将默认为RangeIndex（0,1,2,3,...,n）
columns:数组列表
		用于生成框架的列标签。如果没有提供列，将默认为RangeIndex(0,1,2，…，n)
dtype:  dtype数据类型，默认为None
copy:	是否考虑来自输出源的数据，默认为False，False 相当于引用源数据， True为复制源数据，从而操作不影响原有数据（只影响DataFrame / 2d ndarray输入）。
```

- Series:是一种类似于一维数组的对象，是由一组数据(各种NumPy数据类型)以及一组与之相关的数据标签(即索引)组成。仅由一组数据也可产生简单的Series对象。

**Series主要成分：**

```python
class pandas.Series(data=None, index=None, dtype=None, name=None, copy=False, fastpath=False)

主要参数含义同上
```
## 基础用法
通常，我们按如下方式导入Pandas：

```python
# Pandas 通常和numpy一起使用，好兄弟一辈子
import numpy as np
import pandas as pd
```
### 对象创建
- Series创建：

```python
demo:
import numpy as np
import pandas as pd
data = [1, 3, 5, 7, 9]
# default arangeindex (0, 1, 2..,n)
indexs = ['a', 'b', 'c', 'd', 'e']
pd_series = pd.Series(data, index=indexs)
print(pd_series)

output:
a    1
b    3
c    5
d    7
e    9
dtype: int64
```
- DataFrame创建：

```python
demo：
import numpy as np
import pandas as pd
# 创建一个6行4列的数据
data = np.random.random([6, 4])
# 创建时间索引
indexs = pd.date_range('20190101', periods=6)
# 创建列label，特征属性
columns = list('ABCD')

pd_data_frame = pd.DataFrame(data, index=indexs, columns=columns)
print(pd_data_frame)

output:
                   A         B         C         D
2019-01-01  0.856834  0.035639  0.393552  0.928195
2019-01-02  0.466478  0.489296  0.401637  0.205809
2019-01-03  0.273677  0.719979  0.114818  0.289613
2019-01-04  0.507617  0.078111  0.843729  0.162792
2019-01-05  0.182946  0.240308  0.756220  0.842928
2019-01-06  0.009890  0.931608  0.553362  0.989214
```
### 查看数据
1. 查看DataFrame顶部和尾部的数据

 - 顶部数据查询

```python
# 在上述代码基础上操作
# n表示需要返回前几行数据， 底层实现 同 pd_data_frame.iloc([:n])
head = pd_data_frame.head(n=3)
# print(pd_data_frame.iloc[:3])
print('head 6 of data is :\n', head)

output：
head 6 of data is :
                    A         B         C         D
2019-01-01  0.316854  0.154440  0.869840  0.198396
2019-01-02  0.590714  0.600607  0.182419  0.900057
2019-01-03  0.327585  0.938885  0.097543  0.813009
```
 - 尾部数据查询
 

```python
# 在上述代码基础上操作
# n表示需要返回后几行数据， 底层实现 同 pd_data_frame.iloc[-n:]
head = pd_data_frame.tail(n=3)
# print(pd_data_frame.iloc[-3:])
print('tail 6 of data is :\n', head)

Output:
tail 6 of data is :
                    A         B         C         D
2019-01-04  0.499725  0.681864  0.227293  0.801329
2019-01-05  0.037664  0.384510  0.001677  0.978520
2019-01-06  0.875677  0.357367  0.208400  0.075856
```
2. 显示索引、列和底层Numpy数据：

```python
# 在上述代码基础上操作
index = pd_data_frame.index
print(index)
frame_columns = pd_data_frame.columns
print(frame_columns)
to_numpy = pd_data_frame.to_numpy()
print(to_numpy)

Output:
DatetimeIndex(['2019-01-01', '2019-01-02', '2019-01-03', '2019-01-04',
               '2019-01-05', '2019-01-06'],
              dtype='datetime64[ns]', freq='D')
Index(['A', 'B', 'C', 'D'], dtype='object')
[[0.41637262 0.35726082 0.93384239 0.1033857 ]
 [0.33402402 0.82419902 0.95357459 0.02332131]
 [0.98262518 0.10126923 0.56322639 0.47149354]
 [0.71129316 0.35403757 0.73908355 0.04409778]
 [0.38356779 0.0237542  0.0298259  0.39641723]
 [0.90725548 0.66034389 0.2032032  0.44325942]]
```
3. pd_data_frame.describe（获取数据的统计摘要）、T（转置）、轴排序

### 选择数据
1. 按标签选择

```python
# loc 第一个参数为 行label操作， 第二个参数为 列label操作
loc_data = pd_data_frame.loc['20190101']
print('loc_data_row_label:\n', loc_data)
loc_data = pd_data_frame.loc[:, ['A', 'B']]
print('loc_data_columns_label:\n', loc_data)
loc_data = pd_data_frame.loc['20190101': '20190103', ['A', 'B']]
print('loc_data:\n', loc_data)
```
2. 按位置选择

```python
# loc 第一个参数为 行position操作， 第二个参数为 列position操作
iloc_data = pd_data_frame.iloc[1:3, :]
print('iloc_data_row_pos:\n', iloc_data)
iloc_data = pd_data_frame.iloc[:, [0, 2]]
print('iloc_data_col_pos:\n', iloc_data)
iloc_data = pd_data_frame.iloc[1:3, 0:2]
print('iloc_data:\n', iloc_data)
```
3. 布尔索引

```python
bool_data = pd_data_frame[pd_data_frame.A > 0.5]
print(bool_data)
bool_data = pd_data_frame[[True, False,True, False, True, False]]
print(bool_data)
```
### 缺失值
Pandas主要使用值np.nan来表示缺失的数据。 默认情况下，它不包含在计算中。 我们可以针对含有缺省值行或者是列进行相关操作。

- 给缺省元素赋值

```python
# 针对pd_data_frame重建索引，返回原对象副本
df1 = pd_data_frame.reindex(index=indexs[0:4], columns=list(pd_data_frame.columns) + ['E'])
print(df1)
df1.loc[indexs[0]:indexs[1], 'E'] = 1
print(df1)
```

- 删除缺省行/列

```python
# 'any' : If any NA values are present, drop that row or column.
# 'all' : If all values are NA, drop that row or column.
dropna = df1.dropna(how='any', axis=0)
print(dropna)
```

- 填充缺省值：

```python
# 填充缺省值
fillna = df1.fillna(value=5)
print(fillna)
```
