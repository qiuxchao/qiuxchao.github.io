---
title: Python基础——元组
date: 2019-07-15 08:08:08
top: false
categories: Python
tags: Python
---

# Python基础——元组
## 元组
Python将不能修改的值称为不可变的，而不可变的列表被称为 **元组**；
元组看起来犹如列表，但使用圆括号 **()** 而不是方括号来标识；
定义元组后，就可以使用索引来访问其元素，就像访问列表元素一样；

例如，如果有一个大小不应改变的矩形，可将其长度和宽度存储在一个元组中，从而确保它们是不能修改的

```python
dimensions = (200,50)
print(type(dimesions))
print(dimesions[0])
print(dimesions[1])
# <class 'tuple'>
# 200
# 50
```
### 修改元组变量
虽然不能修改元组的元素，但可以给存储元组的变量赋值

```python
dimensions = (400,100)
print("Modified dimensions:")
for dimension in dimensions:
	print(dimension)
# Original dimensions:
# 200
# 50
```
## 设置代码格式
### 缩进
PEP8 建议每级缩进都使用四个空格
### 行长
建议每行不超过80字符
### 空行
要将程序的不同部分分开，可使用空行
