---
title: Python基础——if语句
date: 2019-06-15 08:08:08
# top: true
categories: Python
tags: Python
---


# Python基础——if语句
**if** 语句能够检测程序的当前状态，并据此采取相应的措施


## 条件测试
每条 if 语句的核心都是一个值为 **True** 或 **False** 的表达式，这种表达式被称为 **条件测试**

### 检查是否相等
检查是否相等使用两个等号 **==**；
一个等号是陈述，两个等号是发问 
```python
car = 'bmw'
car == 'bmw' # True
car = 'audi'
car == 'bmw' # False
```
检查是否相等时不考虑大小写：
函数 **lower()**不会修改存储在变量 car 中的值，因此进行这样的比较时不会影响原来的变量；

```python
car = 'Audi'
car == 'audi' # False
car.lower() == 'audi' # True
```
### 检查是否不相等
要判断两个值是否不等，可结合使用惊叹号和等号 **!=**

```python
requested_topping = 'mushrooms'
if requested_topping != 'anchovies':
    print("Hold the anchovies!")
#  Hold the anchovies!
```
### 比较数字
在 if 语句中可使用各种数学比较，这能够直接检查关心的条件

```python
age = 18
age == 18 # True
age != 20 # True
age < 21 # True
age <= 21 # True
age > 21 # False
age >= 21 # False
```
### 检查多个条件
使用 **and** 检查多个条件；
如果每个测试都通过了，整个表达式就为 **True**；
如果至少有一个测试没有通过，整个表达式就为 **False**

```python
age_0 = 22
age_1 = 18
age_0 >= 21 and age_1 >= 21 # False
age_0 >= 21 and age_1 <= 21 # True
```
使用 **or** 检查多个条件；
只要至少有一个条件满足，整个表达式就为 **True**；
仅当所有测试都没有通过时，使用 **or** 的表达式才为 **False**

```python
age_0 = 22
age_1 = 18
age_0 >= 21 or age_1 >= 21 # True
age_0 <= 21 or age_1 >= 21 # False
```
### 检查特定值是否包含在列表中
要判断特定的值是否已包含在列表中，可使用关键字 **in**

```python
requested_toppings = ['mushrooms','onions','pineapple']
'mushrooms' in requested_toppings # True
'pepperoni' in requested_toppings # False
```
### 检查特定值是否不包含在列表中
要判断特定的值是否不包含在列表中，可使用关键字 **not in**

```python
banned_users = ['andrew','carolina','david']
user = 'marie'
user not in banned_users # True
```
### 布尔表达式
布尔表达式不过是条件测试的别名；
与条件表达式一样，布尔表达式的结果要么为 **True** ，要么为 **False**；
在跟踪程序状态或程序中重要的条件方面，布尔值提供了一种高效的方式；

布尔值通常用于记录条件，如游戏是否正在运行，或用户是否可以编辑网站的特定内容：

```python
game_active = True
can_edit = False
```
## if 语句
**if** 语句有很多种，选择使用哪种取决于要测试的条件数；

最简单的 **if** 语句只有一个测试和一个操作：

```python
if conditional_test:
	do something
```
在 if 语句中，缩进的作用与 for 循环中相同。如果测试通过了，将执行 if 语句后面所有缩进的代码行，否则将忽略它们
### if-else 语句
**if-else** 语句块类似于简单的 if 语句，但其中的 **else** 语句让人能够指定条件测试未通过时要执行的操作

```python
age = 12
if age >= 18:
    print("You are old enough to vote!")
    print("Have you registered to vote yet?")
else:
    print("Sorry, you are too young to vote.")
    print("Please register to vote as soon as you turn 18!")
# Sorry, you are too young to vote.
# Please register to vote as soon as you turn 18!
```
### if-elif-else 结构
因为经常需要检查超过两个的情形，为此可使用 Python 提供的 **if-elif-else** 结构；
它依次检查每个条件测试，直到遇到通过了的条件测试

```python
age = 12
if age < 4:
    price = 0
elif age < 18:
    price = 5
else:
    price = 10
print("Your admission cost is $" + str(price) + ".")
# Your admission cost is $5.
```
### 使用多个 elif 代码块
可根据需要使用任意数量的 **elif** 代码块
```python
age = 12
if age < 4:
    price = 0
elif age < 18:
    price = 5
elif age < 65:
    price = 10
else:
    price = 5
print("Your admission cost is $" + str(price) + ".")
# Your admission cost is $5.
```
### 省略else代码块
python 并不要求 **if-elif** 结构后面必须有 **else** 代码块，有些情况下使用一条 **elif** 语句来处理特定的情形更清晰

```python
age = 12
if age < 4:
    price = 0
elif age < 18:
    price = 5
elif age < 65:
    price = 10
elif age >= 65:
    price = 5
print("Your admission cost is $" + str(price) + ".")
# Your admission cost is $5.
```
### 测试多个条件
要测试多个条件，可使用一系列不包含 **elif** 和 **else** 代码块的简单 **if** 语句；
在可能有多个条件为 **True** ，且你需要在每个条件为 **True** 时都采取相应措施时，适合使用这种方法

```python
requested_toppings = ['mushrooms','extra cheese']
if 'mushrooms' in requested_toppings:
    print("Adding mushrooms.")
if 'pepperoni' in requested_toppings:
    print("Adding pepperoni.")
if 'extra cheese' in requested_toppings:
    print("Adding extra cheese.")
print("\nFinished making your pizza!")
# Adding mushrooms.
# Adding extra cheese.

# Finished making your pizza!
```
如果只想执行一个代码块，就使用 **if-elif-else** 结构；如果要运行多个代码块，就使用一系列独立的 **if** 语句
## 使用 if 语句处理列表
### 检查特殊元素
检查列表中的特殊值，并对其做合适的处理

```python
requested_toppings = ['mushrooms','green peppers','extra cheese']
for requested_topping in requested_toppings:
    if requested_topping == 'green peppers':
        print("Sorry, we are out of green peppers right now.")
    else:
        print("Adding " + requested_topping + ".")
print("\nFinished making your pizza!")
# Adding mushrooms.
# Sorry, we are out of green peppers right now.
# Adding extra cheese.

# Finished making your pizza!
```
### 确定列表不是空的
在 **if** 语句中将列表名用在条件表达式中时，Python 将在列表至少包含一个元素时返回 **True** ，并在列表为空时返回 **False**

```python
requested_toppings = []
if requested_toppings:
    for requested_topping in requested_toppings:
        print("Adding " + requested_topping + ".")
    print("\nFinished making your pizza!")
else:
    print("Are you sure you want a plain pizza?")
# Are you sure you want a plain pizza?
```
### 使用多个列表
遍历第二个列表，并检查其中的每个元素是否包含在第一个列表中

```python
available_toppings = ['mushrooms','olives','green peppers',
                      'pepperoni','pineapple','extra cheese']
requested_toppings = ['mushrooms','french fries','extra cheese']
for requested_topping in requested_toppings:
    if requested_topping in available_toppings:
        print("Adding " + requested_topping + ".")
    else:
        print("Sorry, we don't have " + requested_topping + ".")
print("\nFinished making your pizza!")
# Adding mushrooms.
# Sorry, we don't have french fries.
# Adding extra cheese.

# Finished making your pizza!
```





