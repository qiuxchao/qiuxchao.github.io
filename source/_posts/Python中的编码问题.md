---
title: Python中的编码问题
date: 2019-08-25 08:08:08
top: false
cover: false
categories: Python
tags: Python
---

# Python中的编码问题
爬取的所有网页无论何种编码格式，都应转化为 **utf-8** 格式进行存储，
与源代码编码格式不同会出现乱码。

**UTF-8** 通用性比较好，是用以解决国际上字符的一种多字节编码，
它对英文使用8位（即一个字节），中文使用24位（三个字节）来编码。

**UTF-8** 编码的文字可以在各国各种支持 **UTF8** 字符集的浏览器上显示，
也就是必须两者都是 **utf-8** 才行。

**gbk** 是是国家编码，通用性比 **UTF8** 差，**GB2312** 之类的都算是 **gbk** 编码。
**GBK** 包含全部中文字符；**UTF-8** 则包含全世界所有国家需要用到的字符。

**Unicode** 是一种二进制编码，所有 **utf-8** 和 **gbk** 编码都得通过 **Unicode** 编码
进行转译，即 **utf-8** 和 **gbk** 编码之间不能直接转换

**decode** -----把当前字符解码成Unicode编码
**encode** -----把Unicode编码格式的字符编码成其他格式的编码

Python默认使用 **Unicode** 字符集，做编码转换时，要把 **Unicode** 作为中间编码，
先 **decode**（解码）成 **Unicode** 编码，再 **encode**（编码）成其他编码。

非 **Unicode** 编码不能直接 **encode** 成其他编码，否则会报错

### 转换字符编码
如打印网页源代码出现乱码，先用 **gbk** 编码，忽略掉非法字符，然后再译码
```python
print(r.text.encode('GBK','ignore').decode('GBk'))
```

