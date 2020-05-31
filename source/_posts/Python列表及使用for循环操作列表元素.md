---
title: Python基础——列表和for循环
date: 2019-06-01 08:08:08
# top: true
cover: false
categories: Python
tags: Python
---
# Python基础——列表和for循环
## 列表
列表由一系列按特定顺序排列的**元素**组成；
用方括号 **[ ]** 来表示列表，并用逗号来分隔其中的元素；
```python
# 创建一个简单的列表
bicycles = ['trek','cannondale','redline','specialized']
```
### 访问列表元素
列表是**有序集合**，因此要访问列表的任何元素，只需将该元素的位置或索引告诉Python即可；
```python
# 打印列表中第一个元素
bicycles = ['trek','cannondale','redline','specialized']
print(bicycles[0])
# trek
```
### 第一个列表元素的索引为0，而不是1
列表的第一个元素的索引是 **0**；
通过将索引指定为 **-1** ，可让Python返回最后一个列表元素.
```python
bicycles = ['trek','cannondale','redline','specialized']
print(bicycles[-1].title())
# Specialized
```
### 使用列表中的值
```python
bicycles = ['trek','cannondale','redline','specialized']
message = "My first bicycle was a " + bicycles[0].title() + "."
print(message)
print(bicycles)
# My first bicycle was a Trek.
# ['trek', 'cannondale', 'redline', 'specialized']
```
## 修改、添加和删除元素
### 修改列表元素
可直接使用列表的索引修改元素.
```python
bicycles = ['trek','cannondale','redline','specialized']
bicycles[0] = 'ducati'
print(bicycles)
# ['ducati', 'cannondale', 'redline', 'specialized']
```
### 在列表中添加元素
**append()**：在列表末尾添加元素.
```python
bicycles = []
bicycles.append('trek')
print(bicycles)
# ['trek']
bicycles.append('cannondale')
print(bicycles)
# ['trek', 'cannondale']
bicycles.append('redline')
bicycles.append('specialized')
print(bicycles)
# ['trek', 'cannondale', 'redline', 'specialized']
```
**insert()**：可在列表的任意位置添加新元素，需要指定新元素的索引和值；
这种操作将列表中既有的每个元素都右移一个位置.
```python
bicycles = ['trek','cannondale','redline']
bicycles.insert(0,'specialized')
# ['specialized', 'trek', 'cannondale', 'redline']
```
### 从列表中删除元素
**del** 语句 : 将元素从列表中删除后，就无法再访问它.
如果知道要删除的元素在列表中的位置，可使用 **del** 语句.
```python
bicycles = ['trek','cannondale','redline']
del bicycles[0]
# ['cannondale', 'redline']
```
**pop()**：默认删除列表末尾的元素，并让你能够接着使用它.

```python
bicycles = ['trek','cannondale','redline']
# 从这个列表中删除末尾的值，并将其存储到变量 popped_bicycle 中
popped_bicycle = bicycles.pop()
print(bicycles)
print(popped_bicycle)
# ['trek', 'cannondale']
# redline
```
还可以使用 **pop()** 来删除列表中任何位置的元素，只需在括号中指定要删除的元素的索引即可.

```python
bicycles = ['trek','cannondale','redline']
first_owned = bicycles.pop(0)
print('The first bicycle I owned was a  ' + first_owned.title() + '.')
# The first bicycle I owned was a  Trek.
```
如果你要从列表中删除一个元素，且不再以任何方式使用它，就使用 **del** 语句；
如果你要在删除元素后还能继续使用它，就使用方法 **pop()**
#### 根据值删除元素
**remove()**：可根据列表中元素的值删除元素.

```python
bicycles = ['trek','cannondale','redline']
print(bicycles)
bicycles.remove('trek')
print(bicycles)
# ['trek', 'cannondale', 'redline']
# ['cannondale', 'redline']
```
使用 **remove()** 从列表中删除元素时，也可接着使用它的值.

```python
bicycles = ['trek','cannondale','redline']
print(bicycles)
too_expensive = 'trek'
bicycles.remove(too_expensive)
print(bicycles)
print("\n " + too_expensive.title() + " is too expensive for me.")
# ['trek', 'cannondale', 'redline']
# ['cannondale', 'redline']

# Trek is too expensive for me.
```
方法 **remove()** 只删除第一个指定的值；
如果要删除的值可能在列表中出现多次，就需要使用循环来判断是否删除了所有这样的值.

## 组织列表
### 对列表进行永久性排序
**sort()**：按字母顺序排序.
```python
cars = ['bmw','audi','toyota','subaru']
print(cars)
cars.sort()
print(cars)
# ['bmw', 'audi', 'toyota', 'subaru']
# ['audi', 'bmw', 'subaru', 'toyota']
```
按与字母顺序相反的顺序排列列表元素，
只需向 **sort()** 方法传递参数 **reverse=True**

```python
cars = ['bmw','audi','toyota','subaru']
cars.sort(reverse=True)
print(cars)
# ['toyota', 'subaru', 'bmw', 'audi']
```
### 对列表进行临时排序
**sorted()**：按特定的顺序临时显示列表元素.

```python
cars = ['bmw','audi','toyota','subaru']
# 首先按原始顺序打印列表
print("Here is the original list:")
print(cars)
# 再按字母顺序显示该列表
print("Here is the sorted list:" )
print(sorted(cars))
# 再次进行核实，确认列表元素的排列顺序与以前相同
print("Here is the original list again:")
print(cars)
# Here is the original list:
# ['bmw', 'audi', 'toyota', 'subaru']
# Here is the sorted list:
# ['audi', 'bmw', 'subaru', 'toyota']
# Here is the sorted list:
# ['audi', 'bmw', 'subaru', 'toyota']
```
注意，调用函数 **sorted()** 后，列表元素的排列顺序并没有变；
如果要按与字母顺序相反的顺序显示列表，
也可向函数 **sorted()** 传递参数 **reverse=True**
```python
cars = ['bmw','audi','toyota','subaru']
print(sorted(cars,reverse=True))
# ['toyota', 'subaru', 'bmw', 'audi']
```
### 倒着打印列表
方法 **reverse()**：反转列表元素的排列顺序.
```python
cars = ['bmw','audi','toyota','subaru']
print(cars)
cars.reverse()
print(cars)
# ['bmw', 'audi', 'toyota', 'subaru']
# ['subaru', 'toyota', 'audi', 'bmw']
```
方法 **reverse()** 永久性地修改列表元素的排列顺序，但可随时恢复到原来的排列顺序，为此只需对列表再次调用 **reverse()** 即可.
### 确定列表的长度
函数 **len()**：快速获悉列表的长度.

```python
cars = ['bmw','audi','toyota','subaru']
print(str(len(cars)))
# 4
```
## 操作列表
### 遍历整个列表
使用Python中的 **for** 循环,对列表中的每个元素都执行相同的操作.
**for** 变量名 **in** 列表：从列表中取出一个元素，存储在变量中.
对于位于 **for** 语句后面且属于循环组成部分的代码行，一定要**缩进**.
```python
magicians = ['alice','david','carolina']
# 对于列表中每一个元素都打印出两条消息
for magician in magicians:
	print(magician.title() + ", that was a great trick!")
	print("I can't wait to see your next trick, " + magician.title() + ".\n")
print("Thank you, everyone. That was a great magic show!")
# Alice, that was a great trick!
# I can't wait to see your next trick, Alice.

# David, that was a great trick!
# I can't wait to see your next trick, David.

# Carolina, that was a great trick!
# I can't wait to see your next trick, Carolina.

# Thank you, everyone. That was a great magic show!  
```
### 创建数值列表
使用函数 **range()** 打印一系列的数字.
```python
for value in range(1,6):
	print(value)
# 1
# 2
# 3
# 4
# 5
```
使用  **range()** 和 **list()** 创建数字列表；
还可使用 **list()** 将 **range()** 的结果直接转换为列表.
```python
numbers = list(range(1,6))
print(numbers)
# [1, 2, 3, 4, 5]
```
使用函数 **range()** 时，可指定步长；
打印 1-10 内的偶数.
```python
even_numbers = list(range(2,11,2))
print(even_numbers)
# [2, 4, 6, 8, 10]
```
将前10个整数的平方加入到一个列表中.

```python
squares = []
for value in range(1,11):
	squares.append(value**2)
print(squares)
# [1, 4, 9, 16, 25, 36, 49, 64, 81, 100]
```
### 对数字列表进行简单的统计计算
最小值 **min()**
```python
digits = [1,2,3,4,5,6,7,8,9,0]
print(min(digits))
# 0
```
最大值 **max()**
```python
digits = [1,2,3,4,5,6,7,8,9,0]
print(max(digits))
# 9
```
求和 **sum()**
```python
digits = [1,2,3,4,5,6,7,8,9,0]
print(sum(digits))
# 45
```
### 列表解析
列表解析将 **for** 循环和创建新元素的代码合并成一行，并自动附加新元素.

```python
squares = [value**2 for value in range(1,11)]
print(squares)
# [1, 4, 9, 16, 25, 36, 49, 64, 81, 100]
```
### 处理列表的一部分——切片
处理列表的部分元素——Python称之为 **切片**.
```python
players = ['charles','martina','michael','florence','eli']
print(players)
print(players[0:3]) #打印列表前三个元素
print(players[1:4]) #打印列表2~4个元素
print(players[:4])  #没有指定起始索引，python从列表开头开始提取
print(players[2:])  #让切片终止于列表末尾，可省略终止索引
print(players[-3:]) #打印列表末尾三个元素
# ['charles', 'martina', 'michael', 'florence', 'eli']
# ['charles', 'martina', 'michael']
# ['martina', 'michael', 'florence']
# ['charles', 'martina', 'michael', 'florence']
# ['michael', 'florence', 'eli']
# ['michael', 'florence', 'eli']
```
遍历切片.

```python
players = ['charles','martina','michael','florence','eli']
print("Here are the first three players on my team:")
for player in players[:3]:
	print(player.title())
# Here are the first three players on my team:
# Charles
# Martina
# Michael
```
### 复制列表
要复杂列表，可创建一个包含整个列表的切片，方法是同时省略起始索引和终止索引  **[:]**；
这让Python创建一个始于第一个元素，终止于最后一个元素的切片，即复制整个列表.

```python
my_foods = ['pizza','falafel','carrot cake']
friend_foods = my_foods[:]
print("My favorite foods are:")
print(my_foods)
print("My friend's favorite foods are:")
print(friend_foods)
# My favorite foods are:
# ['pizza', 'falafel', 'carrot cake']
# My friend's favorite foods are:
# ['pizza', 'falafel', 'carrot cake']
```
为核实我们确实有两个列表，下面在每个列表中都添加一种食品，并核实每个列表都记录了相应人员喜欢的食品.

```python
my_foods.append('cannoli')
friend_foods.append('ice cream')
print("My favorite foods are:")
print(my_foods)
print("My friend's favorite foods are:")
print(friend_foods)
# My favorite foods are:
# ['pizza', 'falafel', 'carrot cake', 'cannoli']
# My friend's favorite foods are:
# ['pizza', 'falafel', 'carrot cake', 'ice cream']
```
如果直接 friend_foods = my_foods ，这行不通，这样只是把两个变量指向一个列表；
复制是把一个列表复制到另一个列表中，因此可以有两个部分相同的列表.
### extend() 函数
**extend()** 函数用于在列表末尾一次性追加另一个序列中的多个值（用新列表扩展原来的列表）.
**extend()** 语法： **list.extend(seq)**
参数 **seq** -- 元素列表.
```python
aList = [123,'xyz','zara','abc',123]
bList = [2009,'manni']
aList.extend(bList)
print("Extended List: ",'\n',aList)
# Extended List:  
#  [123, 'xyz', 'zara', 'abc', 123, 2009, 'manni']
```

