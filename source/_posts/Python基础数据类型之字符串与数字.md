---
title: Python基础——字符串与数字
date: 2019-05-05 08:08:08
# top: true
categories: Python
tags: Python
---
# Python基础——字符串与数字
## 变量
每个 **变量** 都存储了一个值——与变量相关联的信息
在程序中可随时修改变量的值，而Python将始终记录变量的最新值

```python
# 一个名为 message 的字符串变量
message = "Hello Python World!"
# 输出这个变量
print(massage)
# Hello Python World!
# 更改这个变量的值
message = "Hello Python Crash Course world!"
# 再次输出
print(message)
# Hello Python Crash Course world!
```
### 变量的命名和使用
变量名只能包含字母、数字和下划线。变量名可以字母或下划线打头，但不能以数字打头；

变量名不能包含空格，但可使用下划线来分隔其中的单词；

不要将Python关键字和函数名用作变量名；

变量名应既简短又具有描述性；

慎用小写字母l和大写字母O，因为它们可能被人错看成数字1和0.

## 字符串
字符串就是一系列字符；
用引号括起的都是字符串，其中的引号可以是单引号，也可以是双引号；

### 使用方法修改字符串的大小写
**title()** ：字符串中单词首字母大写

```python
message = 'hello world!'
print(message.title())
# Hello World!
```
**upper()**：字符串全部大写

```python
message = 'hello world!'
print(message.upper())
# HELLO WORLD!
```
**lower()**：字符串全部小写

```python
message = 'Hello WORLD!'
print(message.lower())
# hello world!
```
### 合并（拼接）字符串
使用 **+** 拼接字符串

```python
am = 'cat'
print(am + ' and dog')
# cat and dog 
```
### 使用制表符或换行符来添加空白
字符串中添加制表符（缩进）：**\t**
```python
print('Python\tHello')
# Python	Hello
```
字符串中添加换行符：**\n**
```python
print('Python\nHello')
# Python
# Hello
```
### 删除空白
删除字符串结尾空白：**rstrip()**

```python
language = ' python '
print(language.rstrip())
#  python
```
删除字符串开头空白：**lstrip()**

```python
language = ' python '
print(language.lstrip())
# python
```
删除字符串两端空白：**strip()**

```python
language = ' python '
print(language.strip())
# python
```
## 数字
可以直接在Python中执行数值运算

```python
print(2+3) # 5
print(3-1) # 1
print(2*3) # 6
print(3/2) # 1.5
print(3**2) # 9
print((2+3) * 4) # 20
```
### 浮点数
Python将带小数点的数字都称为浮点数

```python
print(1.5+2.6) # 4.1
```

### 使用函数str()避免类型错误
函数 **str()**：把非字符串类型转换为字符串

```python
age = 19
message = "Happy " + str(age) + "rd Birthday"
print(message)
# Happy 19rd Birthday!
```
## 注释
在Python中，注释用井号 **#** 表示
井号后面的内容都会被Python解释器忽略

```python
# 这是一条注释！！！
```

