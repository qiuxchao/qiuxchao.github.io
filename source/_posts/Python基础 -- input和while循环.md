---
title: Python基础——用户输入input和while循环
date: 2019-07-28 08:08:08
# top: true
categories: Python
tags: Python
---

# 用户输入input和while循环
通过获取用户输入并学会控制程序的运行时间，可编写出交互式程序
## 函数 input() 
函数 **input()** : 让程序暂停运行，等待用户输入一些文本；
获取用户输入后，Pyhon将其存储在一个变量中

```python
message = input("Tell me something, and I will repeat it back to you: ")
print(message)
# Tell me something, and I will repeat it back to you: hello
# hello
```
### 编写清晰的程序
使用函数 **input()** 时，都应指定清晰而易于明白的提示；
准确地指出希望用户提供什么样的信息

```python
prompt = "If you tell us who you are, we can personalize the message you see."
# 运算符 += ：在存储在变量中的字符串末尾附加一个字符串
prompt += "\nWhat is your first name? "
name = input(prompt)
print("\nHello, " + name + "!")
# If you tell us who you are, we can personalize the message you see.
# What is your first name? xiaoming

# Hello, xiaoming!
```
### 使用 int() 来获取数值输入
使用函数 **input()** 时，Python将用户输入解读为字符串；
在需要对用户输入的数值做处理时，可以使用函数 **int()** 将输入视为**数值**：

```python
age = int(input("你多大了?\n :"))
if age >= 18:
    print("你已经成年了")
else:
    print("你未成年")
# 你多大了?
# :19
# 你已经成年了
```
### 求模运算符
处理数值信息时，求模运算符  **%**  是一个很有用的工具，它将两个数相除并返回**余数**；
求模运算符不会指出一个数是另一个数的多少倍，而只指出余数是多少

```python
4 % 3 # 1
5 % 3 # 2
6 % 3 # 0
7 % 3 # 1
```
如果一个数可被另一个数整除，余数就为0，因此求模运算符将返回 0；
可利用这一点来判断一个数是奇数还是偶数：

```python
number = int(input("Enter a number, and I'll tell you if it's even or odd: "))
if number % 2 == 0:
    print("\nThe number " + str(number) + " is even.")
else:
    print("\nThe number " + str(number) + " is odd.")
# Enter a number, and I'll tell you if it's even or odd: 5

# The number 5 is odd.
```
## while 循环
**for** 循环用于针对集合中的每个元素都一个代码块，而 **while** 循环不断地运行，直到指定的条件不满足为止
### 使用while循环
使用 **while** 循环来数数：

```python
current_number = 1
while current_number <= 5:
    print(current_number)
    current_number += 1 #current_number = current_number + 1
```
上面的代码将 current_number 设置为1，从而指定从1开始数；
接下来的 **while** 循环被设置成这样：只要 current_number 小于或等于5，就接着运行这个循环
### 让用户选择何时退出
定义了一个退出值，只要用户输入的不是这个值，程序就接着运行；
用户输入了退出值，程序结束运行

```python
prompt = "\nTell me something, and I will repeat it back to you: "
prompt += "\nEnter 'quit' to end the program.\n:"
message = ""
while message != 'quit' :
    message = input(prompt)
    if message != 'quit':
        print(message)
# Tell me something, and I will repeat it back to you: 
# Enter 'quit' to end the program.
# :hello
# hello

# Tell me something, and I will repeat it back to you: 
# Enter 'quit' to end the program.
# :quit # 程序结束
```
### 使用标志
在要求很多条件都满足才继续运行的程序中，可定义一个变量，用于判断整个程序是否处于活动状态,这个变量被称为 **标志**，充当了程序的交通信号灯；

让程序在标志为 **True** 时继续运行，并在任何事件导致标志的值为 **False** 时让程序停止运行

下面的代码将变量 active 设置成 **True**,让程序最初处于活动状态：

```python
active = True
# 进入while循环：
while active:
    message = input("你说什么我就返回什么，输入'quit' 退出\n：")
    if message == 'quit':
        active = False
    else:
        print(message)
# 你说什么我就返回什么，输入'quit' 退出
# ：hello
# hello
# 你说什么我就返回什么，输入'quit' 退出
# ：quit # 此时 active 的值为 False ，程序结束
```
### 使用 break 退出循环
要立即退出 **while** 循环，不再运行循环中余下的代码，也不管条件测试的结果如何，可使用 **break** 语句；

**break** 语句用于控制程序流程，可使用它来控制哪些代码行将执行，哪些代码行不执行；

以 **while True** 开头的循环将不断运行，直到遇见 **break** 语句

```python
while True:
    city = input("\nPlease enter the name of a city you have bisited:" +
                 "\nEnter 'quit' when you are finished.")
    if city == 'quit' :
        break
    else:
        print("I'd love to go to " + city.title() + "!")
# Please enter the name of a city you have bisited:
# Enter 'quit' when you are finished.shanghai
# I'd love to go to Shanghai!

# Please enter the name of a city you have bisited:
# Enter 'quit' when you are finished.quit
```
在任何的 Python 循环中都可以使用**break**语句
### 在循环中使用  continue 返回到循环开头
要返回到循环开头，并根据条件测试结果决定是否继续执行循环，可使用 **continue** 语句；
它不像 **break** 语句那样不再执行余下的代码并退出整个循环，而是不执行余下的代码并返回到循坏开头；     

一个从 1 数到 10，但只打印其中奇数的循环：

```python
current_number = 0
while current_number < 10 :
    current_number += 1
    if current_number % 2 == 0:
        continue
    else:
        print(current_number)
# 1
# 3
# 5
# 7
# 9
```
### 避免无限循环
每个 **while** 循环都必须有停止运行的途径，这样才不会没完没了地执行下去；

对每个 **while** 循环进行测试，确保它按预期那样结束；

确认程序至少有一个这样的地方能让循环条件为 **False** 或让 **break** 语句得以执行 

## 使用 while 循环处理列表和字典
要记录大量的用户和信息，需要在 **while** 循环中使用列表和字典；

要在遍历列表的同时对其进行修改，可使用 **while** 循环；

通过将 **while** 循环同列表和字典结合起来使用，可收集、存储并组织大量输入，供以后查看和显示
### 在列表之间移动元素
使用 **while** 循环可以将一个列表的值移动到另一个列表中，方法如下：
```python
# 首先，创建一个待验证的用户列表和一个用于存储已验证用户的空列表
unconfirmed_users = ['alice','brian','candace']
confirmed_users = []
# 验证每个用户，直到列表为空自动结束循环
# 将每个经过验证的列表都移到已验证用户列表中
while unconfirmed_users:
    current_user = unconfirmed_users.pop()
    print("Verifying user: " + current_user.title())
    confirmed_users.append(current_user)
# 显示所有已验证用户
print("\nThe following users have been confirmed:")
for confirmed_user in confirmed_users:
    print(confirmed_user.title())
# Verifying user: Candace
# Verifying user: Brian
# Verifying user: Alice

# The following users have been confirmed:
# Candace
# Brian
# Alice
```
### 删除包含特定值的所有列表元素
可以使用 **while** 循坏遍历列表并删除列表中所有指定的值，方法如下：

```python
pets = ['dog','cat','dog','goldfish','cat','cat','rabbit']
print(pets)
while 'cat' in pets:
    pets.remove('cat')
print(pets)
# ['dog', 'cat', 'dog', 'goldfish', 'cat', 'cat', 'rabbit']
# ['dog', 'dog', 'goldfish', 'rabbit']
```
### 使用用户输入来填充字典
可使用 **while** 循环提示用户输入任意数量的信息，方法如下：

```python
esponses = {}
#设置一个标志，指出调查是否继续
polling_active = True
while polling_active:
#提示输入被调查者的名字和回答
    name = input("\nWhat is your name? ")
    response = input("Which mountain would you like to climb someday? ")
#将答案存储在字典中
    responses[name] = response
#看看是否还有人要参与调查
    repeat = input("Would you like to let another person respond?(yes/no)")
    if repeat == 'no':
        polling_active = False
#调查结束，显示结果
print("\n--- Poll Results ---")
for name,response in responses.items():
    print(name + " would like to climb " + response + ".")
# What is your name? xiaoming
# Which mountain would you like to climb someday? huangshan
# Would you like to let another person respond?(yes/no)no

# --- Poll Results ---
# xiaoming would like to climb huangshan.
```

