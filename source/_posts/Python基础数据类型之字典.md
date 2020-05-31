---
title: Python基础——字典
date: 2019-06-26 08:08:08
# top: true
categories: Python
tags: Python
---

# Python基础——字典

**字典**（dict）能够将相关信息关联起来；
字典 可存储的信息量几乎不受限制
#### 一个简单的字典
字典用放在花括号 **{ }** 中的一系列 **键——值** 对表示；

键——值 对是两个相关联的值；

指定键时，Python将返回与之相关联的值。键和值之间用冒号分隔，而键——值对之间用逗号分隔；

在字典中，想存储多少个键——值对都可以

```python
alien_0 = {'color':'green','points':5}
print(alien_0['color'])
print(alien_0['points'])
print(type(alien_0))
# green
# 5
# <class 'dict'>
```
## 使用字典
在Python中，字典是一系列键——值对；

每个键都与一个值相关联，可以使用键来访问与之相关联的值；

与键相关联的值可以是数字、字符串、列表乃至字典。事实上，可将任何Python对象用作字典中的值；
### 访问字典中的值
要获取与键相关联的值，可依次指定字典名和放在方括号内的键

```python
alien_0 = {'color':'green','points':5}
print(alien_0['color'])
# green
```
### 添加键值对
字典是一种动态结构，可随时在其中添加键——值对；

要添加键——值对，可依次指定字典名、用方括号括起的键和相关联的值；

键——值对的排列顺序与添加顺序不同；

Python不关心键——值对的添加顺序，而只关心键和值之间的关联关系

```python
alien_0 = {'color':'green','points':5}
alien_0['x_position'] = 0
alien_0['y_position'] = 25
print(alien_0)
# {'color': 'green', 'points': 5, 'x_position': 0, 'y_position': 25}
```
### 先创建一个空字典
使用字典来存储用户提供的数据或在编写能自动生成大量键——值对的代码时，通常都需要先定义一个空字典

```python
alien = {}
alien['color'] = 'green'
alien['points'] = '5'
print(alien)
# {'color': 'green', 'points': '5'}
```
### 修改字典中的值
要修改字典中的值，可依次指定字典名、用方括号括起的键以及与该键相关联的新值

```python
alien_0 = {'color':'green','points':5}
alien_0['color'] = 'yellow'
print(alien_0)
# {'color':'yellow','points':5}
```
### 删除键—值对
**del** 语句：将相应的键—值对永久删除

```python
alien_0 = {'color':'green','points':5}
del alien_0['points']
print(alien_0)
# {'color':'green'}
```
### 由类似对象组成的字典
确定需要使用多行来定义字典时，在输入左花括号后按回车键

```python
favorite_languages = {
    'jen':'python',
    'sarah':'c',
    'edward':'ruby',
    'phil':'python',
    }
print(favorite_languages)
print("Sarah's favorite language is " + favorite_languages['sarah'].title() + ".")
# {'jen': 'python', 'sarah': 'c', 'edward': 'ruby', 'phil': 'python'}
# Sarah's favorite language is C.
```
## 遍历字典
可以使用循环来遍历字典，需要指定遍历方法；

下面将介绍遍历字典的方法
### 遍历所有的键—值对
使用 **for** 循环来遍历字典，在对字典使用 **items()** 方法；

声明两个变量，用于存储键——值对中的键和值。对于这两个变量，可使用任何名称；

方法 **items()** ：返回一个键——值对列表

```python
favorite_languages = {
    'jen':'python',
    'sarah':'c',
    'edward':'ruby',
    'phil':'python',
    }
for name,language in favorite_languages.items():
    print(name.title() + "'s favorite language is " + language.title() + ".")
# Jen's favorite language is Python.
# Sarah's favorite language is C.
# Edward's favorite language is Ruby.
# Phil's favorite language is Python.
```
即便遍历字典时，键——值对的返回顺序也可能与存储顺序不同；

Python不关心键——值对的存储顺序，而只跟踪键和值之间的关联关系
### 遍历字典中的所有键
方法 **keys()** : 返回字典中的所有键

```python
favorite_languages = {
    'jen':'python',
    'sarah':'c',
    'edward':'ruby',
    'phil':'python',
    }
for name in favorite_languages.keys():
    print(name.title())
# Jen
# Sarah
# Edward
# Phil
```
遍历字典时，会默认遍历所有的键,因此即使不使用方法 **keys()**，输出也将不变；

使用方法 **keys()** 可以让代码更容易理解，也可以省略它 for name in favorite_languages:

方法 **keys()**
并非只能用于遍历；实际上，它返回一个列表，其中包含字典中的所有键

```python
favorite_languages = {
    'jen':'python',
    'sarah':'c',
    'edward':'ruby',
    'phil':'python',
    }
if 'erin' not in favorite_languages.keys():
    print("Erin, please take our poll!")
# Erin, please take our poll!
```
### 按顺序遍历字典中的所有键
要以特定的顺序返回元素，一种办法是在 **for** 循环中对返回的键进行排序，
为此，可使用函数 **sorted()** 来获得按特定顺序排列的键列表的副本

```python
favorite_languages = {
    'jen':'python',
    'sarah':'c',
    'edward':'ruby',
    'phil':'python',
    }
for name in sorted(favorite_languages.keys()):
    print(name.title() + ", thank you for taking the poll.")
# Erin, please take our poll!
# Edward, thank you for taking the poll.
# Jen, thank you for taking the poll.
# Phil, thank you for taking the poll.
```
### 遍历字典中所有的值
方法 **values()** : 返回一个值列表，而不包含任何键

```python
favorite_languages = {
    'jen':'python',
    'sarah':'c',
    'edward':'ruby',
    'phil':'python',
    }
print("The following languages have been mengtioned:")
for language in sorted(favorite_languages.values()):
    print(language.title())
# The following languages have been mengtioned:
# C
# Python
# Python
# Ruby
```
### 剔除重复项
方法 **set()** : 剔除重复项

```python
favorite_languages = {
    'jen':'python',
    'sarah':'c',
    'edward':'ruby',
    'phil':'python',
    }
for language in set(favorite_languages.values()):
    print(language.title())
# C
# Python
# Ruby
```
## 嵌套
将一系列字典存储在列表中，或将列表作为值存储在字典中，称为 **嵌套**；

可以在列表中嵌套字典、在字典中嵌套列表、在字典中嵌套字典
### 将字典存储在列表中

```python
# 创建一个包含三个外星人的列表：
alien_0 = {'color':'green','points':'5'}
alien_1 = {'color':'yellow','points':'10'}
alien_2 = {'color':'red','points':'15'}
aliens = [alien_0,alien_1,alien_2]
for alien in aliens:
    print(alien)
# {'color': 'green', 'points': '5'}
# {'color': 'yellow', 'points': '10'}
# {'color': 'red', 'points': '15'}
```
### 将列表存储在字典中
每当需要在字典中将一个键关联到多个值时，都可以在字典中嵌套一个列表.

```python
pizza = {
    'crust' : 'thick',
    'toppings' : ['mushrooms','extra cheese'],
    }
print("You ordered a " + pizza['crust'] + "-crust pizza " +
      "with the follwing toppings:")
for topping in pizza['toppings']:
    print("\t" + topping)
# You ordered a thick-crust pizza with the follwing toppings:
#	  mushrooms
#	  extra cheese
```
### 将字典存储在字典中
可在字典中嵌套字典，但这样做时，代码可能很快复杂起来

例如，如果有多个网站用户，每个都有独特的用户名，可在字典中将用户名作为键，然后将每位用户的信息存储在一个字典中，并将该字典作为与用户名相关联的值

```python
users = {
    'aeinstein' : {
        'first' : 'albert',
        'last' : 'einstein',
        'location' : 'princeton',
        },
    'mcurie' : {
        'first' : 'marie' ,
        'last' : 'curie' ,
        'location' : 'paris' ,
        }
    }
for username,user_info in users.items():
    print("\nUsername: " + username)
    full_name = user_info['first'] + " " + user_info['last']
    location = user_info['location']
    print("\tFull name: " + full_name.title())
    print("\tLocation :" + location.title())
# Username: aeinstein
#	  Full name: Albert Einstein
#	  Location :Princeton

# Username: mcurie
# 	  Full name: Marie Curie
# 	  Location :Paris
```









