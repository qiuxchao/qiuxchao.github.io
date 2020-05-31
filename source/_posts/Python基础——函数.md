---
title: Python基础——函数
date: 2019-08-12 08:08:08
# top: true
categories: Python
tags: Python
---

# 函数 
**函数** 是带名字的代码块，用于完成具体的工作，要执行函数定义的特定任务，可调用该函数；

需要在程序中多次执行同一项任务时，无需反复编写完成该任务的代码，而只需调用执行该任务的函数，让 Python 运行其中的代码即可；

将函数存储在被称为 **模块** 的独立文件中，可以让主程序文件的组织更为有序
## 定义函数
关键字 **def** ：定义一个函数；

**def 函数名()** ：向 Python 指出了函数名，还能在括号中指出函数为完成其任务需要什么样的信息；

紧跟在 **def 函数名():** 后面的所有缩进构成了 **函数体**；

**函数调用** 让Python执行函数中的代码，调用函数可依次指定函数名以及用括号括起的必要信息

```python
def greet_user():
    """显示简单的问候语"""
    print("Hello!")
greet_user()
# Hello!
```
文档字符串用三引号括起,Python使用它们来生成有关程序中函数的注释

```python
"""这是一个文档字符串(docstring)"""
```
### 向函数传递信息
```python
def greet_user(username):
    """显示简单的问候语，括号里面定义一个变量"""
    print("Hello, " + username.title() + "!")
greet_user('qxc')
# Hello, Qxc!
```
**实参和形参**：
上面定义函数 greet_user() 时，要求给变量 username 指定一个值。调用这个函数并提供这种信息（人名）时，它将打印相应的问候语。
	

在函数 greet_user() 的定义中，变量 username 是一个 形参 ——函数完成其工作所需的一项信息。在代码 greet_user('jesse') 中，值 'jesse' 是一个实参。实参是调用函数时传递给函数的信
息。调用函数时，将要让函数使用的信息放在括号内。在 greet_user('jesse') 中，将实参
'jesse' 传递给了函数 greet_user() ，这个值被存储在形参 username 中。
### 传递实参
鉴于函数定义中可能包含多个**形参**，因此函数调用中也可能包含多个**实参**。

向函数传递实参的方式有很多：
**位置实参**：要求实参的顺序与形参的顺序相同；
**关键字实参**：其中每个实参都由变量名和值组成；
还可使用字典和列表。
### 位置实参
调用函数时，Python必须将函数调用中的每个实参都关联到函数定义中的一个形参；
基于实参顺序的关联方式被称为**位置实参**

```python
def describe_pet(animal_type,pet_name):
    """显示宠物的信息"""
    print("I have a " + animal_type + ".")
    print("My " + animal_type + "'s name is " + pet_name.title() + ".")
          
describe_pet('dog','wangwang')
# I have a dog.
# My dog's name is Wangwang.
```
- 可以根据需要调用函数任意次，调用函数多次是一种效率极高的工作方式
```python
describe_pet('cat','miaomiao')
# I have a cat.
# My cat's name is Miaomiao.
```

- 使用位置实参来调用函数时，如果实参的顺序不正确，结果会出乎意料
### 关键字实参
**关键字实参** 是传递给函数的 **名称——值** 对；
直接在实参中将名称和值关联起来，因此向函数传递实参时不会混淆

```python
def describe_pet(animal_type,pet_name):
    """显示宠物的信息"""
    print("I have a " + animal_type + ".")
    print("My " + animal_type + "'s name is " + pet_name.title() + ".")
          
describe_pet(animal_type='hamster',pet_name='harry')
# I have a hamster.
# My hamster's name is Harry.
```
关键字实参的顺序无关紧要，因为 Python 知道各个值该存储到哪个形参中；

**注意**：使用关键字实参时，务必准确地指出函数定义中的形参名

### 默认值
编写函数时，可给每个形参指定**默认值**，
给形参指定默认值后，可在函数调用中省略相应的实参。

使用默认值可简化函数调用，还可清楚的指出函数的典型用法

```python
def describe_pet(pet_name,animal_type='dog'):
	"""给宠物类型形参指定默认值"""
	print("\nI have a " + animal_type + ".")
    print("My " + animal_type + "'s name is " + pet_name.title() + ".")
 
describe_pet(pet_name='wille')
# I have a dog.
# My dog's name is Wille.
```
**注意**：指定默认值的形参必须放在未指定默认值的形参后面；
在这个函数的定义中，修改了形参的排列顺序。由于给 animal_type 指定了默认值，无需通过实参来指定动物类型，因此在函数调用中只包含一个实参——宠物的名字。然而，Python 依然将这个实参视为位置实参，因此如果函数调用中只包含宠物的名字，这个实参将关联到函数定义中的第一个形参。这就是需要将 pet_name 放在形参列表开头的原因所在。

如果要描述的动物不是小狗，可使用类似于下面的函数调用：

```python
describe_pet(pet_name='harry',animal_type='hamster')
# I have a hamster.
# My hamster's name is Harry.
```
**注意**：使用默认值时，在形参列表中必须先列出没有默认值的形参，再列出有默认值的实参。



### 等效函数调用
鉴于可混合使用**位置实参**、**关键字实参**和**默认值**，通常有多种等效的函数调用方式：

```python
def describe_pet(pet_name,animal_type='dog'):
	"""显示宠物的信息"""
    print("\nI have a " + animal_type + ".")
    print("My " + animal_type + "'s name is " + pet_name.title() + ".")

# 一条名为Willie的小狗
describe_pet('willie')
describe_pet(pet_name='willie')
# 一只名为Harry的仓鼠
describe_pet('harry','hamster')
describe_pet(pet_name='harry',animal_type='hamster')
describe_pet(animal_type='hamster',pet_name='harry')
# I have a dog.
# My dog's name is Wille.
# I have a dog.
# My dog's name is Wille.
# I have a hamster.
# My hamster's name is Harry.     
# I have a hamster.
# My hamster's name is Harry.
# I have a hamster.
# My hamster's name is Harry.
```
这些函数调用与前面的示例相同
## 返回值
函数并非总是直接显示输出，相反，它可以处理一些数据，并返回一个或一组值；

函数返回的值被称为 **返回值**, 一般是一个变量的名字。

**return** 语句： 将值返回到调用函数的代码行。

**返回值** ：能够将程序的大部分繁重工作移到函数中去完成，从而简化主程序

### 返回简单值
下面一个函数，它接受名和姓并返回整洁的姓名：

```python
def get_formatted_name(first_name,last_name):
    """返回整洁的姓名"""
    full_name = first_name + " " + last_name
    # 将full_name的值转换为首字母大写格式，并将结果返回到函数调用行
    return full_name.title()

# 下面一行就是函数调用行
musician = get_formatted_name('jimi','hendrix')
print(musician)
# Jimi Hendrix
```
### 让实参变成可选的
让实参变成可选的，使用函数就只需在必要时才提供额外的信息；

可给形参指定一个默认值——空字符串，并将其移到形参列表末尾。

```python
def get_formatted_name(first_name,last_name,middle_name=''):
    """返回整洁的姓名"""
    if middle_name:
        """py将非空字符串解读为True"""
        full_name = first_name + " " + middle_name +" " + last_name
    else:
        full_name = first_name + " " + last_name
    return full_name.title()
musician = get_formatted_name('jimi','hendrix')
print(musician)
musician = get_formatted_name('john','hooker','lee')
print(musician)
# Jimi Hendrix
# John Lee Hooker
```
可选值让函数能够处理各种不同情形的同时，确保函数调用尽可能简单。
### 返回字典
函数可返回任何类型的值，包括列表和字典等复杂的数据结构。

```python
def build_person(first_name,last_name,age=''):
    """返回一个字典，其中包含有关一个人的信息"""
    person = {'first':first_name,'last':last_name}
    """将字典的键与函数的形参绑定"""
    if age:
        person['age'] = age
    return person
musician = build_person('jimi','hendrix',age=27)
print(musician)
# {'first': 'jimi', 'last': 'hendrix', 'age': 27}
```
### 结合使用函数和while循环
可以将函数同任何Python结构结合起来使用；

下面将结合使用函数 get_formatted_name() 和 while 循环：

```python
def get_formatted_name(first_name,last_name):
    """返回整洁的姓名"""
    full_name = first_name + ' ' + last_name
    return full_name.title()
while True:
    print("Please tell me your name: ")
    print("enter 'q' at any time to quit")
    f_name = input("First name: ")
    if f_name == 'q':
        break
    l_name = input("Last name: ")
    if l_name == 'q':
        break
    formatted_name = get_formatted_name(f_name,l_name)
    print("Hello , " + formatted_name + "!")
# Please tell me your name: 
# enter 'q' at any time to quit
# First name: xiao
# Last name: ming
# Hello , Xiao Ming!
# Please tell me your name: 
# enter 'q' at any time to quit
# First name: q # 程序结束
```
## 传递列表
向函数传递列表很有用，这种列表包含的可能是数字字符串、数字或更复杂的对象（如字典），将列表传递给函数后，函数就能直接访问其内容。

```python
def greet_users(names):
    """向列表中的每位用户都发出简单的问候"""
    for name in names:
        print("Hello, " + name.title() + "!")

user_names = ['hannah','ty','margot']
greet_users(user_names)
# Hello, Hannah!
# Hello, Ty!
# Hello, Margot!
```
### 在函数中修改列表
将列表传递给函数后，函数就可对其进行修改；

在函数中对这个列表所做的任何修改都是永久性的，这能够高效的处理大量的数据；

```python
#首先创建一个列表，其中包含一些要打印的设计：
def print_models(unprinted_designs,completed_models):
    """
    模拟打印每个设计，直到没有未打印的设计为止
    打印每个设计后，都将其移到列表completed_models中
    """
    while unprinted_designs:
        current_design = unprinted_designs.pop()
        #模拟根据设计制作3D打印模型的过程
        print("Printing model: " + current_design)
        completed_models.append(current_design)
def show_completed_models(completed_models):
    """显示打印好的所有模型"""
    print("\nThe following models have been printed:")
    for completed_model in completed_models:
        print(completed_model)
unprinted_designs = ['iphone case','robot pendant','dodecahedron']
completed_models = []
print_models(unprinted_designs,completed_models)
show_completed_models(completed_models)
# Printing model: dodecahedron
# Printing model: robot pendant
# Printing model: iphone case

# The following models have been printed:
# dodecahedron
# robot pendant
# iphone case
```
每个函数都应只负责一项具体的工作，这优于使用一个函数来完成两项工作；

可以在一个函数中调用另一个步骤，这有助于将复杂的任务划分成一系列的步骤。

### 禁止函数修改列表
可以向函数传递列表的副本，这样函数所做的任何修改都只影响副本，而丝毫不影响原件。

切片表示法 **[:]** 创建列表的副本，语法如下：
**函数名(列表名[:])**

这样原有列表的内容将会被保留

```python
print_models(unprinted_designs[:],completed_models)
```
## 传递任意数量的实参
Python允许函数从调用语句中收集任意数量的实参。

形参名 ***args**  中的星号  * 让Python创建一个名为 args 的 **空元组**，并将收到的所有值都封装到这个元组中。

不管收到的实参是多少个，这种语法都管用。

```python
def make_pizza(*toppings):
    """打印顾客点的所有配料"""
    print(toppings)
make_pizza('mushrooms','green peppers','extra chees')
# ('mushrooms', 'green peppers', 'extra chees')
```
### 结合使用位置实参和任意数量实参
如果要让函数接受不同类型的实参，必须在函数定义中将接纳任意数量实参的形参放在最后；

Python先匹配**位置实参**和**关键字实参**，再将余下的实参都收集到最后一个形参中。

```python
def make_pizzas(size,*toppings):
    """概述要制作的比萨"""
    print("\nMaking a " + str(size) + "-inch pizza with the followings:")
    for topping in toppings:
        print("-" + topping)
        """将收到的第一个值存储在形参size中，
        并将其他的所有值都存储在元组toppings中。
        在函数调用中首先要指定size的实参，
        然后根据需要指定任意数量的toppings"""
make_pizzas(12,'mushrooms','green peppers','extra cheese')
# Making a 12-inch pizza with the followings:
# -mushrooms
# -green peppers
# -extra cheese
```
### 使用任意数量的关键字实参
在需要接受任意数量的信息，但预先不知道传递给函数的会是什么样的信息的情况下，可将函数编写成能够接受任意数量的**键——值对**，调用语句提供多少就接受多少。

形参 ****args** 中的两个星号 ** 让Python创建一个名为 args 的**空字典**，并将收到的所有键——值对都封装到这个字典中。

```python
def build_profile(first,last,**user_info):
    """创建一个字典，其中包含我们知道的有关用户的一切"""
    profile = {}
    profile['first'] = first
    profile['last'] = last
    for key,value in user_info.items():
        profile[key] = value
    return  profile
# 函数 build_profile() 的定义要求提供名和姓，同时允许用户根据需要提供任意数量的名称 —值对。
# 形参 **user_info 中的两个星号让Python创建一个名为 user_info 的空字典，并将收到的所有名称 — 值对都封装到这个字典中。
# 在这个函数中，可以像访问其他字典那样访问 user_info 中的名称 — 值对。
# 在 build_profile() 的函数体内，创建了一个名为 profile 的空字典，用于存储用户简介。
# 然后，将名和姓加入到这个字典中，因为总是会从用户那里收到这两项信息。
# 再然后，遍历字典 user_info 中的键 — 值对，并将每个键 — 值对都加入到字典 profile 中。
# 最后，将字典 profile 返回给函数调用行。

user_profile = build_profile('zhang','xiaoming',
                             school='princeton',
                             field='physics')
print(user_profile)
# {'first': 'zhang', 'last': 'xiaoming', 'school': 'princeton', 'field': 'physics'}
```
在这里，返回的字典包含用户的名和姓，还有求学的地方和所学专业。

调用这个函数时，不管额外提供了多少个键 — 值对，它都能正确地处理。

编写函数时，可以以各种方式混合使用**位置实参**、**关键字实参**和任意数量的**实参**。
## 将函数存储在模块中
函数的优点之一是：使用它们可以将代码块与主程序分离；

通过给函数指定描述性名称，可让主程序容易理解的多；

还可以更进一步，将函数存储在被称为 **模块** 的 **独立文件** 中，再将模块导入到主程序中；

**import**  语句 允许在当前运行的程序文件中使用模块中的代码。
### 导入整个模块
要让函数是可导入的，得先创建模块；

模块是扩展名为 **.py** 的文件，包含要导入到程序中的代码；

要在同一个文件夹下创建程序和模块；

例如，现在有一个程序，在这个程序的文件夹中有一个 **mkpizza.py** 的文件（后面的示例中也会用到此文件），文件内容如下：

```python
def make_pizzas(size,*toppings):
    """概述要制作的比萨"""
    print("\nMaking a " + str(size) +
          "-inch pizza with the followings:")
    for topping in toppings:
        print("-" + topping)
```

如果想要在程序中使用 mkpizza 模块中的代码，可以使用下面的代码：

```python
import mkpizza
```

Python读取这个文件时，代码行 **import mkpizza** 让Python打开文件 mkpizza.py，并将其中所有的函数代码都复制到这个程序中。

调用被导入的模块中的函数，可指定模块名和函数名，并用句点分隔它们：
**模块名.函数名(参数)**

```python
import mkpizza
mkpizza.make_pizza(16, 'mushrooms', 'green peppers','extra cheese')
# Making a 16-inch pizza with the following toppings:
# -mushrooms
# -green peppers
# -extra cheese
```
这是一种导入方法：只需编写一条 **import** 语句并在其中指定模块名，就可在程序中使用该模块中的所有函数。
### 导入特定的函数
导入模块中的特定函数，这种导入方法如下：
**from 模块名 import 函数名**

还可通过用逗号分隔函数名，根据需要从模块中导入任意数量的函数：
**from 模块名 import 函数名1,函数名2,函数名3**
若使用这种语法，调用函数时就无需使用句点。

```python
from mkpizza import make_pizza
make_pizza(12,'mushrooms','green peppers','extra cheese')
# Making a 12-inch pizza with the following toppings:
# -mushrooms
# -green peppers
# -extra cheese
```
由于在 **import** 语句中显式的导入了函数，因此调用它时只需指定其名称。
### 使用 as 给函数指定别名
如果要导入的函数的名称可能与程序中现有的名称冲突，或者函数的名称太长，可指定简短而独一无二的 **别名**——函数的另一个名称 ，类似于外号；

需在导入函数时这样做，指定别名的语法如下：
**from 模块名 import 函数名 as 别名**

```python
from mkpizza import make_pizza as mp
"""将函数make_pizza()重命名为mp()"""
mp(20,'mushrooms','green peppers','extra cheese')
"""
需要调用make_pizza()时，可简写成mp()，
而Python将运行make_pizza()中的代码，
这可避免与这个程序可能包含的函数make_pizza()混淆
"""
# Making a 20-inch pizza with the following toppings:
# -mushrooms
# -green peppers
# -extra cheese
```
### 使用 as 给模块指定别名
通过给模块指定简短的别名，能够更轻松地调用模块中的函数；

给模块指定别名的通用语法如下：

```python
import mkpizza as p
p.make_pizza(19,'mushrooms','green peppers','extra cheese')
# Making a 19-inch pizza with the following toppings:
# -mushrooms
# -green peppers
# -extra cheese
```
### 导入模块中的所有函数
使用星号 * 运算符可让Python导入模块中的所有函数；

语法如下：
**from 模块名 import *** 

**import** 语句中的星号让Python将模块中的每个函数都复制到这个程序文件中，由于导入了每个函数，因此可通过函数名来调用每个函数，而无需使用句点表示法：

```python
from mkpizza import *
make_pizza(18,'mushrooms','green peppers','extra cheese')
# Making a 18-inch pizza with the following toppings:
# -mushrooms
# -green peppers
# -extra cheese
```
然而，使用并非自己编写的大型模块时，最好不要采用这种导入方法， 如果模块中有函数名称与自己项目中使用的名称相同，可能导致意想不到的结果：Python可能遇到多个名称相同的函数或变量，进而覆盖函数，不是分别导入所有的函数；

最佳的做法是：要么只导入需要使用的函数，要么导入整个模块并使用句点表示法

## 使用 global 声明全局变量
**global** 语句是适用于当前整个代码块的声明，它是 **全局变量** 的标识符；

**global** 中出现的名字不能在 **global** 之前的代码中使用；

在 **global** 中出现的名字不能作为**形参**，不能作为循坏的**控制对象**，不能在**类定义**、**函数定义**，**import** 语句中出现；

**global**： 将变量定义为**全局变量**，可以通过定义为全局变量，实现在函数内部改变变量值；

一个 global 语句可以同时定义多个变量，如 **global x,y,z**

**global** 语句的作用：
	在编写程序的时候，如果想为一个在函数外的变量重新赋值，并且这个变量会作用于许多函数中时，就需要告诉python这个变量的作用域是全局变量，此时用 **global** 语句就可以变成这个任务，也就是说没有用 **global** 语句的情况下，是不能修改全局变量的
```python
x = 1
def a():
	global x
	x += 1
	print(x)
a()
print(x)
# 2
# 2
```
如果想在函数使用某一变量后再对其进行修改，怎么让函数中使用的变量是模块层定义的那个全局变量而不是函数内部的局部变量呢？
这里就可以用到 **global修饰符** 了：

```python
a = 4
def h():
	global a
	print(a)
	a = 12
h()
print(a)
# 4
# 12
```
## 匿名函数 lambda
**lambda** 函数，即 **Lambda 表达式**（lambda expression），是一个 **匿名函数**（不存在函数名的函数）。

**lambda** 只是一个表达式，函数体比 **def** 简单很多；

 **lambda** 的主体是一个**表达式**，而不是一个代码块。仅仅能在 **lambda 表达式**中封装有限的逻辑进去；

**lambda** 函数拥有自己的命名空间，且不能访问自有参数列表之外或全局命名空间里的参数；

虽然 **lambda** 函数看起来只能写一行，却不等同于C或C++的内联函数，后者的目的是调用小函数时不占用栈内存从而增加运行效率。

**Lambda** 函数的语法只包含一个语句，如下：
**lambda [arg1[,arg2,······argn]] : expression**
即：**lambda 参数:表达式**
参数： 可选，通常以逗号分隔的变量表达式形式，也就是**位置参数**；
表达式：不能包含**循环**、**return**、**elif**，可以包含 **if**,**else**

例：

```python
L = lambda x:x*x
print(L(5))
# 25

#匿名函数的展开:
def M(x):
	return x*x
print(M(5))
# 25
```
包含 **if-else** 的 l**ambda**：

```python
h = lambda x : 'x>10' if x>10 else 'x<10'
print(h(5))
# x<10

#函数实现
def H(x):
	if x > 10:
		return 'x>10'
	else:
		return 'x<10'
print(H(5))
# x<10
```
使用多个参数：

```python
sum = lambda arg1,arg2: arg1 + arg2
print("（lambda函数）相加后的值为：",sum(10,20))
# （lambda函数）相加后的值为： 30

# 上面等同于下面
def sm(arg1,arg2):
	return arg1 + arg2
print("（函数）相加后的值为：",sm(10,20))
# （函数）相加后的值为： 30
```

## 函数编写指南
编写函数时，需要牢记几个细节：

 - 应给函数指定**描述性名称**，且只在其中使用小写字母和下划线。描述性名称可帮助你和别人明白代码想要做什么。给模块命名时也应遵循上述约定。
 - 每个函数都应包含简要地阐述其功能的**注释**，该注释应紧跟在函数定义后面，并采用文档字符串格式。文档良好的函数让其他程序员只需阅读文档字符串中的描述就能够使用它，他们完全可以相信代码如描述的那样运行；只要知道函数的名称、需要的实参以及返回值的类型，就能在自己的程序中使用它。
 - 给形参指定默认值时，等号两边不要有空格：
**def 函数名(形参1，形参2='默认值')**
对于函数调用中的关键字实参，也应遵循这种约定：
**函数名(实参1，实参2='值')**
 - 如果程序或模块包含多个函数，可使用两个空行将相邻的函数分开，这样将更容易知道前一个函数在什么地方结束，下一个函数从什么地方开始。所有的 **import** 语句都应放在文件开头，唯一例外的情形是，在文件开头使用了注释来描述整个程序。

