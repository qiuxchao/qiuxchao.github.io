---
title: Ajax 异步请求与数据交互
date: 2020-02-20 08:08:08
# top: true
categories: [Js, Ajax]
tags: [Js, Ajax]
---

# Ajax 异步请求与数据交互
## 1、初识 Ajax
### Ajax 是什么？
1. **Asynchronous JavaScript And XML**
>  异步的 JavaScript 和 XML

2. **Web 开发的一种技术**
>  是一种使用 JavaScript 请求 XML 数据的技术

3. **异步发送和请求数据**
>使用异步的方式提交和请求数据，不需要重新刷新当前页面

4. **目前 JSON 数据格式已经占据市场**
 > 目前 Ajax 技术主要用于请求 JSON 数据


#### Ajax 请求数据图解
![image](https://imgconvert.csdnimg.cn/aHR0cHM6Ly9jZG4uanNkZWxpdnIubmV0L2doL3FpdXhjaGFvL0NETi9hamF4L2ltZ18wMS5qcGc?x-oss-process=image/format,png)
1、客户端使用 Js 通过调用一个对象 XMLHttpRequest 来请求服务器
2、服务器返回 XML/JSON 的数据格式，数据返回到 HTML Response 中


#### XMLHttpRequest 对象
* XMLHttpRequest 是一个对象类型的 API

* 在浏览器环境下使用
* 是 BOM 中的一个对象
* 用于客户端和服务端数据的传递和接收
* 用于请求 XML 数据（JSON，纯文本text）

**其他类似技术 / 库**
- jQuery
- Axios
- Superagent
- Fetch API
- Prototype
- Node HTTP

### 安装 XAMPP

XAMPP 是一个集成的服务器组件，它包含了 PHP、Apache、Mysql 等服务。
下载地址：[XAMPP DownLoad](https://www.apachefriends.org/zh_cn/index.html)

1、安装完成后，启动 Apache、Mysql、PHP 等服务；
2、在浏览器地址栏输入 `http://localhost`  ，如果显示欢迎页面则说明服务已经开启；
3、 `http://127.0.0.1/phpmyadmin/` 进入后台管理页面；
4、进入 XAMPP 安装目录下的 htdocs 文件夹，配置文件都在这个目录下；
5、在 htdocs 目录下新建自己的项目文件，就可以在服务器环境中运行了；
6、运行 html 文时，要使用 `localhost` 前缀，例如：`http://localhost/ajaxsandbox/ajax4.html`

## 2、Ajax 请求的两种方式
使用 Ajax 来请求数据时，需要创建一个 `XMLHttpRequest()` 对象，然后使用这个对象中的一些属性和方法来请求数据。
### XMLHttpRequest 对象的属性和方法

```javascript
// 点击一个 button 后拿到一个纯文本信息
document.getElementById("button").addEventListener("click", loadText);
function loadText() {
    // 创建 XMLHttpRequest 对象
    var xhr = new XMLHttpRequest();
    console.log(xhr);
}
```
运行上述代码，结果如下：
![img](https://imgconvert.csdnimg.cn/aHR0cHM6Ly9jZG4uanNkZWxpdnIubmV0L2doL3FpdXhjaGFvL0NETi9hamF4L2ltZ18wMi5wbmc?x-oss-process=image/format,png)
### Ajax请求的两种方式
**onload 事件**
**onreadystatechange 事件**

### Ajax 请求纯文本
1、通过 **onload** 方法请求：
```javascript
<button id="button">请求纯文本</button>
<script>
// 点击一个 button 后拿到一个纯文本信息
document.getElementById("button").addEventListener("click", loadText);
function loadText() {
    // 创建 XMLHttpRequest 对象
    var xhr = new XMLHttpRequest();
    // console.log(xhr);  // 打印 XMLHttpRequest 对象

    // open(type, url, async) 
    // 参数1：请求的类型 "GET" 或 "POST"
    // 参数2：请求的目标地址 
    // 参数3：是否开启异步请求 true 或 false
    xhr.open("GET","sample.txt", true);

    // 两种方式请求 onload / onreadystatechange
    xhr.onload = function () {
        // 以文本的形式打印返回的内容
        console.log(this.responseText);
    }
    
    // 发送请求
    xhr.send();
}
```


2、通过 **onreadystatechange** 方法请求：

```javascript
<button id="button">请求纯文本</button>
<br>
<div id="text"></div>

<script>
    // 点击一个 button 后拿到一个纯文本信息
    document.getElementById("button").addEventListener("click", loadText);
    var text = document.getElementById("text");
    function loadText() {
        // 创建 XMLHttpRequest 对象
        var xhr = new XMLHttpRequest();
        
        // open(type, url, async) 
        // 参数1：请求的类型 "GET" 或 "POST"
        // 参数2：请求的目标地址 
        // 参数3：是否开启异步请求 true 或 false
        xhr.open("GET","sample.txt", true);
        xhr.onreadystatechange = function () {
            // 以文本的形式打印返回的内容
            console.log(this.responseText);
        }
        // 发送请求
        xhr.send();
     }      
```
     
## 3、XMLHttpRequest 对象中 onload 事件与 onreadystatechange 事件的区别
`onload` 和 `onreadystatechange` 两种方法都可以请求数据，不同之处在于状态码的不同，从而导致触发的时间不同。


`readyState` 是 `XMLHttpRequest` 对象的一个属性，当请求状态发生改变时，`readyState` 的值（状态码）也会发生改变： 
`readyState` 状态码:
- 0 : 请求未初始化
- 1 : 服务器连接已建立
- 2 : 请求已接收
- 3 : 请求处理中
- 4 : 请求已完成，且响应已就绪

`status` 也是 `XMLHttpRequest` 对象的一个属性，其记录 HTTP 请求状态码：
HTTP 状态码（这里仅列举一部分）
- 200 - 服务器成功返回网页
- 404 - 请求的网页不存在
- 503 - 服务器暂时不可用
......

### onreadystatechange
`onreadystatechange` 事件会在 `this.readyState` 状态码发生改变时触发

```javascript
xhr = new XMLHttpRequest();
xhr.onreadystatechange = function () {
    console.log(this.readyState);
}
// 2
// 3
// 4
```


`onprogress` 事件的触发条件是：当 `readyState` 状态码为 `3` 时。基于此设定，可以将一些加载动画放入 `onprogress` 事件函数中：

```javascript
xhr.onprogress = function () {
    console.log(this.readyState);
}
// 3
```



### onload
`onload` 事件会在 `this.status` 为 `200` 时触发

```javascript
xhr.onload = function () {
    console.log(this.status);
}
// 200
```

>注意：当触发 onload 事件时，readyState 状态码一定为 4；


基于以上请求状态码的不同，可以封装一个事件函数来完善 `onreadystatechange` 事件：

```javascript
// 创建 XMLHttpRequest 对象
var xhr = new XMLHttpRequest();
// 请求信息
xhr.open("GET", "example.txt", true);
// 绑定 onreadystatechange 事件
xhr.onreadystatechange = function () {
    if(this.readyState === 4 && this.status === 200) {
        console.log(this.responseText);
    } else if (this.status === 404) {
        console.log("请求的网页不存在");
    }
}
// 发送请求
xhr.send();
```



### 请求纯文本并加载到 DOM 中

```javascript
<button id="button">请求纯文本</button>
<br>
<div id="text"></div>
<script>
// 点击一个 button 后拿到一个纯文本信息并放入 div 元素中
document.getElementById("button").addEventListener("click", loadText);
var text = document.getElementById("text");
function loadText() {
    // 创建 XMLHttpRequest 对象
    var xhr = new XMLHttpRequest();
    
    // open(type, url, async) 
    // 参数1：请求的类型 "GET" 或 "POST"
    // 参数2：请求的目标地址 
    // 参数3：是否开启异步请求 true 或 false
    xhr.open("GET","sample.txt", true);

    // 两种方式请求 onload / onreadystatechange
    // xhr.onload = function () {
        // 以文本的形式打印返回的内容
        // console.log(this.responseText);
    // }

    xhr.onreadystatechange = function () {
        if(this.readyState === 4 && this.status === 200) {
            text.innerText = this.responseText;
        } else if (this.status === 404) {
            text.innerText = "NOT FOUND!";
        }
    }
    
    // 发送请求
    xhr.send();
}
</script>
```
## 4、Ajax 请求 JSON 数据
当前目录中有以下两个 JSON 格式文件：
*user.json*

```json
{
    "id": 1,
    "name": "henry",
    "email": "henry@gmail.com"
}
```


*users.json*

```json
[
    {
        "id": 1,
        "name": "Henry",
        "email": "henry@gmail.com"
    },
    {
        "id": 2,
        "name": "Bucky",
        "email": "bucky@gmail.com"
    },
    {
        "id": 3,
        "name": "hemiah",
        "email": "hemiah@gmail.com"
    }
]
```


### 请求单条 JSON 数据并添加到 DOM 结构中

```javascript
<button id="button1">请求单个数据</button>
<br><br>
<h1>单个用户</h1>
<div id="user"></div>
<script>
    // 获取 button1 按钮并绑定事件
    document.getElementById("button1").addEventListener("click", loadUser);
    //  设置事件函数
    function loadUser () {
    // 创建 XMLHttpRequest 对象
    var xhr = new XMLHttpRequest();
    // 请求目标文件数据
    xhr.open("GET", "user.json", true);
    // 绑定 onload 事件
    xhr.onload = function () {
        if (this.status === 200) {
            // 将获取的数据解析成 JSON 对象
            var user = JSON.parse(this.responseText);
            // 添加 DOM 元素 并将 JSON 数据写入到 DOM 元素中
            var output = ' ';
            output += 
                '<ul>' + 
                '<li>' + user.id + '</li>' + 
                '<li>' + user.name + '</li>' + 
                '<li>' + user.email + '</li>' + 
                '</ul>';
            // 添加内容至 DOM 元素
            document.getElementById("user").innerHTML = output;
        }
    }
    //发送请求
    xhr.send();
}
</script>
```

当运行上面的代码并点击 button 按钮时，页面中将会新增一个 `ul` 和 三个 `li` 元素并在每个 `li` 元素中显示一条数据

### 请求多条 JSON 数据并添加到 DOM 结构中

```javascript
<button id="button2">请求所有用户</button>
<br><br>
<h1>所有用户</h1>
<div id="users"></div>

<script>
    // 获取 button2 按钮并绑定事件
    document.getElementById("button2").addEventListener("click", loadUsers);
    //  设置事件函数
    function loadUsers () { 
    // 创建 XMLHttpRequest 对象
    var xhr = new XMLHttpRequest();
    // 请求目标文件数据
    xhr.open("GET", "users.json", true);
    // 绑定 onload 事件
    xhr.onload = function () {

    // 将获取的数据解析成 JSON  数组对象
    var users = JSON.parse(this.responseText);

    // 遍历数组并提取数据
    var output = ' ';
    for(var i in users) {
        // 添加 DOM 元素 并将 JSON 数据写入到 DOM 元素中
        output +=
        '<ul>' +
            '<li>' + users[i].id + '</li>' +
            '<li>' + users[i].name + '</li>' +
            '<li>' + users[i].email + '</li>' +
            '</ul>';
    }
    document.getElementById("users").innerHTML = output;
    }
    
    //发送请求
    xhr.send();
}
</script>
```

当运行上面的代码并点击 button 按钮时，页面中将会新增3个 `ul` 和 3个 `li` 元素并在每个 `li` 元素中显示一条数据

## 5、请求 Github 真实 api 接口
### 请求 Github 真实 api 接口并将数据加载到页面上
```javascript
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>请求 Github 接口</title>
    <style>
        /* 设置 div 元素的样式 */
        .user {
            display: flex;
            background-color: #f4f4f4;
            padding: 10px;
            margin-bottom: 10px;
        }
        .user ul {
            list-style: none;
        }
    </style>
</head>
<body>
    <button id="button">请求Github接口</button>
    <br><br>
    <h1>所有 Github 的用户信息</h1>
    <div id="users"></div>
    
    <script>
        // 获取 button 按钮并绑定事件
        document.getElementById("button").addEventListener('click', loadUsers);
        // 设置事件函数
        function loadUsers () {
            // 创建 XMLHttpRequest 对象
            var xhr = new XMLHttpRequest();
            // 设置要请求的数据
            xhr.open("GET", "https://api.github.com/users", true);
            // 绑定 onload 事件
            xhr.onload = function () {
                // 将获取的数据解析成 JSON 数组对象
                var users = JSON.parse(this.responseText);
                // 创建 HTML 模板
                var output = ' ';
                // 遍历数组
                for (var i in users) {
                    // ES6 模板语法
                    output += `
                        <div class="user">
                            <img src="${users[i].avatar_url}" width="70" height="70">
                            <ul>
                                <li>ID: ${users[i].id}</li>
                                <li>Login: ${users[i].login}</li>
                            </ul>
                        </div>
                    `;
                }
                // 添加内容至 DOM 元素
                document.getElementById("users").innerHTML = output;
            }
            // 发起请求
            xhr.send();
        }
    </script>
</body>
</html>
```
运行上面的代码，效果如下图：
![img](https://imgconvert.csdnimg.cn/aHR0cHM6Ly9jZG4uanNkZWxpdnIubmV0L2doL3FpdXhjaGFvL0NETi9hamF4L2ltZ18wMy5wbmc?x-oss-process=image/format,png)

## 6、Ajax 请求 PHP 接口
### 使用 Ajax 向 php 发送请求并处理返回结果
在当前目录下创建 `process.php` 文件，内容如下：

```php
<?php
    // 获取 name 参数并返回格式化的字符串
    // 处理使用 get 方法发送的数据
    if (isset($_GET['name'])) {
        echo "GET: 你的名字是 ".  $_GET['name'];
    }
    // 处理使用 post 方法发送的数据
    if (isset($_POST['name'])) {
        echo "POST: 你的名字是 ".  $_POST['name'];
    }
?>
```

`html` 文件如下：

```javascript
<button id="button">获取PHP数据</button>
<br><br>

<script>
    // 获取 DOM 元素并绑定事件
    document.getElementById("button").addEventListener("click", getData);
    // 设置事件处理函数
    function getData () {
        // 创建 XMLHttpRequest 对象
        var xhr = new XMLHttpRequest();
        // php? 后面的是传入 php 文件中的参数，php 接收到参数后会处理并返回
        xhr.open("GET", "process.php?name=Henry", true);
        // 绑定 onload 事件
        xhr.onload = function () {
            console.log(this.responseText);
        }
        // 发送请求
        xhr.send();
    }
</script>
```

运行上述代码后，在页面点击 button 按钮，控制台会打印如下结果：
`GET: 你的名字是 Henry `


### 正常表单提交数据到 php
正常的 php 提交数据到 php 时会跳转到 php 的页面：

```javascript
<button id="button">获取PHP数据</button>
<br><br>
<h1>正常表单提交数据到PHP</h1>
<form action="process.php" method="GET">
    <input type="text" name="name">
    <input type="submit" value="提交">
</form>

<script>
    document.getElementById("button").addEventListener('click', getData);
    function getData () {
        var xhr = new XMLHttpRequest();
        xhr.open("GET", "process.php", true);
        xhr.onload = function () {
            console.log(this.responseText);
        }
        xhr.send();
    }
</script>
```

运行上述代码，在页面中输入框中输入文本后点击提交按钮后会跳转到一个新的 php 的文件页面下，这是正常的表单提交。

### Ajax 提交表单
使用下面这种方法可以在不需要刷新页面的情况下获取到数据：

```javascript
<h1>Ajax提交数据 - 使用 get 方法</h1>
<form id="getForm">
    <input type="text" name="name" id="name1">
    <input type="submit" value="提交">
</form>
<script>
    // 获取表单元素并绑定 submit 事件
    document.getElementById("getForm").addEventListener('submit', getForm);
    function getForm (e) {
        // 取消表单的默认跳转事件
        e.preventDefault();
        // 获取 input 输入框的 值
        var name = document.getElementById("name1").value;
        
        var xhr = new XMLHttpRequest();
        // 拼接获取到的 输入框值到请求 url 上
        xhr.open("get", "process.php?name=" + name, true);
        xhr.onload = function () {
            console.log(this.responseText);
        }
        xhr.send();
    }
</script>
```

运行上面的代码，在页面中输入框中输入文本后点击提交按钮后会在当前页面的控制台中输出结果。
这种请求方式是使用 `get` 方法来实现的，当提交数据后，会显示在 `url` 地址的后面；
下面的代码演示如何使用 `post` 方法来请求数据，使得在提交数据后不会显示在 `url` 地址后：

```javascript
<h1>Ajax提交数据</h1>
<form id="postForm">
    <input type="text" name="name" id="name1">
    <input type="submit" value="提交">
</form>
<script>
    // 获取表单元素并绑定 submit 事件
    document.getElementById("postForm").addEventListener('submit', postForm);
    function postForm (e) {
        // 取消表单的默认跳转事件
        e.preventDefault();
        // 获取 input 输入框的 值
        var name = document.getElementById("name1").value;
        // 创建变量存储需要发送的数据
        var params = "name=" + name;
        var xhr = new XMLHttpRequest();
        xhr.open("POST", "process.php", true);
        //设置请求头
        xhr.setRequestHeader('Content-type', 'application/x-www-form-urlencoded');
        xhr.onload = function () {
            console.log(this.responseText);
        }
        // 发送数据请求
        xhr.send(params);
    }
</script>
```

运行上面的代码，在页面中输入框中输入文本后点击提交按钮后会在当前页面的控制台中输出结果。
使用这种方法不会将数据显示在 `url` 后面，使得数据传输更安全。

## 7、Ajax 请求本地数据库

### 开启 XAMPP 的相关服务并创建一个本地数据库
进入 `http://127.0.0.1/phpmyadmin/` 创建数据库：
1. 点击 `新建`
![img](https://imgconvert.csdnimg.cn/aHR0cHM6Ly9jZG4uanNkZWxpdnIubmV0L2doL3FpdXhjaGFvL0NETi9hamF4L2ltZ18wNC5wbmc?x-oss-process=image/format,png)
2. 填写 `数据库名` 和 `排序规则`，点击 `创建`：
![img](https://imgconvert.csdnimg.cn/aHR0cHM6Ly9jZG4uanNkZWxpdnIubmV0L2doL3FpdXhjaGFvL0NETi9hamF4L2ltZ18wNS5wbmc?x-oss-process=image/format,png)
3. 新建数据表，填写 `名字` 和 `字段`，点击 `执行`：
![img](https://imgconvert.csdnimg.cn/aHR0cHM6Ly9jZG4uanNkZWxpdnIubmV0L2doL3FpdXhjaGFvL0NETi9hamF4L2ltZ18wNi5wbmc?x-oss-process=image/format,png)
4. 填写字段信息，点击 `保存`：
![img](https://imgconvert.csdnimg.cn/aHR0cHM6Ly9jZG4uanNkZWxpdnIubmV0L2doL3FpdXhjaGFvL0NETi9hamF4L2ltZ18wNy5wbmc?x-oss-process=image/format,png)
5. 至此，数据表已创建完成：
![img](https://imgconvert.csdnimg.cn/aHR0cHM6Ly9jZG4uanNkZWxpdnIubmV0L2doL3FpdXhjaGFvL0NETi9hamF4L2ltZ18wOC5wbmc?x-oss-process=image/format,png)
### 使用 Ajax 向数据库添加数据

#### 1.使用 PHP 连接数据库并进行相关设置

```php
<?php
    # 连接数据库
    $conn = mysqli_connect('localhost', 'root', '', 'ajaxtest');

    // 处理使用 post 方法发送的数据
    if (isset($_POST['name'])) {
        # 将拿到的数据转化一下
        $name = mysqli_real_escape_string($conn, $_POST['name']);

        # 插入数据到数据库
        $query = "INSERT INTO users(name) VALUES('$name')";

        # 判断数据是否有效
        if (mysqli_query($conn, $query)) {
            echo '用户添加成功！';
        } else {
            echo "用户添加失败！".mysqli_error($conn);
        }
    }
?>
```

#### 2.填写表单数据并提交到数据库

```javascript
<h1>Ajax提交数据</h1>
<form id="postForm">
    <input type="text" name="name" id="name1">
    <input type="submit" value="提交">
</form>
<script>
    // 获取表单元素并绑定 submit 事件
    document.getElementById("postForm").addEventListener('submit', postForm);
    function postForm (e) {
        // 取消表单的默认跳转事件
        e.preventDefault();
        // 获取 input 输入框的 值
        var name = document.getElementById("name1").value;
        // 创建变量存储需要发送的数据
        var params = "name=" + name;
        var xhr = new XMLHttpRequest();
        xhr.open("POST", "process.php", true);
        //设置请求头
        xhr.setRequestHeader('Content-type', 'application/x-www-form-urlencoded');
        xhr.onload = function () {
            console.log(this.responseText);
        }
        // 发送数据请求
        xhr.send(params);
    }
</script>
```
运行上述代码，在输入框中输入文本后点击提交按钮，将向本地数据库中添加一条数据。

### 使用 Ajax 从服务器获取数据
#### 1.创建 users.php 文件，内容如下：

```php
<?php
    # 连接数据库
    $conn = mysqli_connect('localhost', 'root', '', 'ajaxtest');
    # 创建查询语句
    $query = 'SELECT * FROM users';
    # 获取数据表
    $result = mysqli_query($conn, $query);
    $users = mysqli_fetch_all($result, MYSQLI_ASSOC);
    echo json_encode($users);
?>
```

#### 2.从数据库获取数据并添加到 DOM 结构中：
   

```javascript
<button id="button2">请求所有用户</button>
   <br><br>
   <h1>所有用户</h1>
   <div id="users"></div>
   <script>
       // 获取 button1 按钮并绑定事件
       document.getElementById("button2").addEventListener("click", loadUsers);
       //  设置事件函数
       function loadUsers() {
           // 创建 XMLHttpRequest 对象
           var xhr = new XMLHttpRequest();
           // 请求数据
           xhr.open("GET", "users.php", true);
           // 绑定 onload 事件
           xhr.onload = function () {
               // 将获取的数据解析成 JSON  数组对象
               var users = JSON.parse(this.responseText);

               // 遍历数组
               var output = ' ';
               for (var i in users) {
                   // 添加 DOM 元素 并将 JSON 数据写入到 DOM 元素中
                   output +=
                       '<ul>' +
                       '<li>' + users[i].id + '</li>' +
                       '<li>' + users[i].name + '</li>' +
                       '</ul>';
               }
               document.getElementById("users").innerHTML = output;
           }
           //发送请求
           xhr.send();
       }
   </script>
```

运行上述代码，将在页面中打印出本地数据库中的数据：
![img](https://imgconvert.csdnimg.cn/aHR0cHM6Ly9jZG4uanNkZWxpdnIubmV0L2doL3FpdXhjaGFvL0NETi9hamF4L2ltZ18wOS5wbmc?x-oss-process=image/format,png)







































