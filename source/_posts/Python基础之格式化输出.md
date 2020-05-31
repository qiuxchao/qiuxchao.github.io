---
title: Python基础——格式化输出
date: 2019-05-20 08:08:08
# top: true
# cover: true
categories: Python
tags: Python
---

# Python基础——格式化输出及一些字符串方法
                                                  
## 使用 % 格式化输出
Python中用 **%** 代表**格式符**，或者叫**占位符**；
表示格式化操作，将其转化成相应的数据类型
```python
age = 10
print('我今年%d岁'%age)
# 我今年10岁
```
在程序中，看到了 **%** 这样的操作符，这就是Python **格式化输出**
```python
age = 19
name = 'xiaoming'
print('我的名字是%s,年龄是%d岁'%(name,age))
# 我的名字是xiaoming,年龄是19岁
```

下面是常用的格式符号

| 格式符号|转换
|-| -: |
|%c|字符|
|%s|通过str()字符串转换来格式化|
|%i|有符号十进制整数|
|%d|有符号十进制整数|
|%u|无符号十进制整数|
|%o|八进制整数|
|%x|十六进制整数(小写字母)|
|%X|十六进制整数(大写字母)|
|%e|索引符号(小写‘e’)|
|%E|索引符号(大写‘E’)|
|%f|浮点实数|
|%g|%f和%e的简写|
|%G|%f和%E的简写|

```python
name = 'xiaoming'
qq = 2915241235
num = 13683823372
dizhi = 'xx市xx区'
print('==============================')
print("姓名：%s\nQQ：%i\n手机号：%d\n公司地址：%s"%(name,qq,num,dizhi))
# ==============================
# 姓名：xiaoming
# QQ：2915241235
# 手机号：13683823372
# 公司地址：xx市xx区
```
## 使用 format()函数 格式化字符串
格式化字符串的函数 **str.format()**，它增强了字符串格式化的功能
基本语法是在字符串中定义 **{}** ，字符串后面加上 **.format()** ,函数中按花括号的顺序填写要补入的字符或字符串变量（也可以设置指定的参数及顺序）
下面演示了 **format** 函数 的使用方法：

不设置指定位置，按默认顺序

```python
str1 = "{} {}".format("hello","world")
print(str1)
# hello world
```
设置指定位置

```python
str1 = "{0} {1}".format("hello","world")
str2 = "{1} {0} {1}".format('hello','world')
print(str1,'\n',str2)
# hello world 
# world hello world
```
指定参数名

```python
print("网站名：{name},地址：{url}".format(name='百度',url='www.baidu.com'))
# 网站名：百度,地址：www.baidu.com
```
通过字典设置参数

```python
site = {'name':'百度','url':'www.baidu.com'}
print("网站名：{name},地址：{url}".format(**site))
# 网站名：百度,地址：www.baidu.com
```
通过列表索引设置参数（“0”是必须的）

```python
site_list = ['百度','www.baidu.com']
print('网站名：{0[0]},地址：{0[1]}'.format(site_list))
# 网站名：百度,地址：www.baidu.com
```
格式化数字

```python
print('{:.2f}'.format(3.1415926))
# 3.14
```
格式化数字的其他参数列表：

|数字|格式|输出|描述
|-| :- | :-: | -: |
|3.1415926  |{:.2f}|3.14|保留小数点后两位|
|3.1415926|{:+.2f}|+3.14|带符号保留小数点后两位|
|-1|{:+.2f}|-1.00 |带符号保留小数点后两位|
|2.71828|{:.0f}|3|不带小数|
|5|{:0>2d}|05|数字补零(填充左边, 宽度为2)|
|5|{:x<4d}|5xxx|数字补x(填充右边, 宽度为4)|
|10|{:x<4d}|10xx|数字补x(填充右边, 宽度为4)|
|1000000|{:,}|1,000,000|以逗号分隔的数字格式|
|0.25|{:.2%}|25.00%|百分比格式|
|1000000000|{:.2e}|1.00e+09|指数记法|
|13|{:10d}|13|右对齐(默认,宽度为10)|
|13|{:<10d}|13|左对齐(宽度为10)|
|13|{:^10d}|13|中间对齐(宽度为10)| 

## 使用 replace 方法替换字符串中的字符
方法 **replace()** 将字符中的 **old**（旧字符串）替换成 **new** （新字符串）
**replace()** 语法：
**str.replace(old,new,[,max])**
参数：
**old** -- 将被替换的字符串；
**new** -- 新字符串，用于替换old字符串；
**max** -- 可选字符串，替换不超过 max 次.
```python
str1 = '你好$$$我正在学Python@#@#现在需要&%&%修改字符串'
str2 = str1.replace('$$$',' ').replace('@#@#',' ').replace('&%&%',' ')
print(str2)
# 你好 我正在学Python 现在需要 修改字符串
```
如果指定第三个参数 **max** ，则替换不超过 **max** 次；
**replace** 不会改变原 **string** 的内容
```python
name = 'xiaomzzg'
print(name.replace('zz','in',0))
print(name)
# xiaoming
# xiaomzzg
```
## 使用 split 方法分隔字符串
**split()** 通过指定分隔符对字符串进行切片，返回一个字符串列表，如果参数 **num** 有指定值，则分隔 **num+1** 个子字符串
语法：
**str.split(str="",num=string.count(str))**
参数：
**str** -- 分隔符，默认为所有的空字符，包括空格、换行(\n)、制表符(\t)等
**num** -- 分隔次数，默认为-1，即分隔所有

```python
str1 = "aaa\nbbb\nccc"
print(str1.split()) # 以空格为分隔符，包含 \n
print(str1.split('\n',1)) # 以\n为分隔符，分隔成两个
name = 'wang#xiao#ming'
print(name.split('#',2)) # 以#为分隔符，分割成3个
# ['aaa', 'bbb', 'ccc']
# ['aaa', 'bbb\nccc']
# ['wang', 'xiao', 'ming']
```

