---
title: Ajax
date: 2021-10-05 16:46:47
tags:         
 - Ajax 
 - Axios
categories: 前端
---

# 概念

## Ajax简介

AJAX（Asynchronous JavaScritpt and XML），异步的 JavaScript 和 XML。AJAX 不是一种新的编程语言，是使用 `XMLHttpRequest` 对象与服务器通信的一种技术。AJAX 最主要的特性就是可以在**不刷新页面**的情况下与服务器通信（异步），交换信息或更新页面。

## XML简介

XML（Extensible Markup Language） ，指可扩展标记语言，被设计用来传输和存储数据。

比如说我有一个学生数据：

```text
name = “张三” ; age = 18 ; gender = “男” ;
```

用 XML 表示：

```xml
<student>
    <name>张三</name>
    <age>18</age>
    <gender>男</gender>
</student>
```

XML 和 HTML 类似，不同的是 HTML 中都是预定义标签，用来向网页中呈现数据的；而 XML 中没有预定义标签，通过自定义标签表示一些数据，用来传输和存储。

最开始 AJAX 进行数据交互时，所使用的格式是 XML，现在已经被 JSON 取代了。

```json
{"name":"张三","age":18,"gender":"男"}
```

JSON 格式更加简洁，并且提供了强大的 API，灵活度远胜于 XML。

## AJAX 的特点

### AJAX的优点

1. 可以无刷新页面与服务端进行通信
2. 允许你根据用户事件来更新部分页面内容

### AJAX 的缺点

1. 没有浏览历史，不能回退
2. 存在跨域问题（同源）
3. SEO不友好（爬虫获取不到信息）

## HTTP

超文本传输协议（Hypertext Transfer Protocol，HTTP）是一个简单的请求-响应协议，规定了浏览器和万维服务器之间互相通信的规则。

### 请求交互过程

![2021/05/25/TOIMG9fc680525074336N.png](https://picturebed.tumiblog.top/2021/05/25/TOIMG9fc680525074336N.png)

1. 前后应用从浏览器端向服务器发送 **HTTP 请求(请求报文)**
2. 服务器接收到请求后, 调度服务器应用处理请求, 向浏览器端返回 **HTTP 响应（响应报文）**
3. 浏览器端接收到响应, 解析显示响应体/调用监视回调

### 查看 HTTP 请求

在浏览器中可以查看 http 请求信息，以下以 Chrome 为例。

按 F12 可以打开开发者工具界面，可以查看发送的 HTTP 请求的相关信息。

![2021/05/25/TOIMG3d5aa0525074404N.png](https://picturebed.tumiblog.top/2021/05/25/TOIMG3d5aa0525074404N.png)

### HTTP 请求报文

请求报文包括了四部分，`请求行`、`请求头`、`空行`、`请求体`。

- **请求行**

请求行包括了三部分，`请求类型（GET、POST...）`、`URL 路径`、`HTTP 协议的版本（HTTP/1.1）`。

```bash
GET /product_detail?id=2 HTTP/1.1
```

![2021/05/25/TOIMGe81ce0525074431N.png](https://picturebed.tumiblog.top/2021/05/25/TOIMGe81ce0525074431N.png)

- **请求头**

```bash
Host: baidu.com
Cookie: name=baidu
Content-type: applicatiion/x-www-form-urlencoded
User-Agent: Chrome 83
...
```

![2021/05/25/TOIMG027a60525074456N.png](https://picturebed.tumiblog.top/2021/05/25/TOIMG027a60525074456N.png)

- **空行**

空行是固定的，必须得有。

- **请求体**

请求体内容可以有也可以没有，如果是 GET 请求，请求体则为空，如果是 POST 请求，那么请求体可以不为空。

```text
username=admin&password=admin
```

![2021/05/25/TOIMG9c8890525074531N.png](https://picturebed.tumiblog.top/2021/05/25/TOIMG9c8890525074531N.png)

### HTTP 响应报文

响应报文和请求报文一样，也包括四部分，`响应行`、`响应头`、`空行`、`响应体`。

- **响应行**

响应行包括三部分，`HTTP 版本`、`响应状态码（200）`、`响应状态字符串（OK）`。

```bash
HTTP/1.1 200 OK
```

![2021/05/25/TOIMG2a59e0525074554N.png](https://picturebed.tumiblog.top/2021/05/25/TOIMG2a59e0525074554N.png)

- **响应头**

格式和请求头一样。

```bash
Content-type: text/html;charset=utf-8
Content-length: 2048
Content-encoding: gzip
...
```

![2021/05/25/TOIMG7dc8a0525074615N.png](https://picturebed.tumiblog.top/2021/05/25/TOIMG7dc8a0525074615N.png)

- **空行**
- **响应体**

响应体可以是 html 文档，也可以是其它类型的。

![2021/05/25/TOIMGd60400525074636N.png](https://picturebed.tumiblog.top/2021/05/25/TOIMGd60400525074636N.png)

### 常见的响应状态码

`200 OK` 请求成功。一般用于GET 与POST 请求。

`201 Created` 已创建。成功请求并创建了新的资源。

`401 Unauthorized` 未授权/请求要求用户的身份认证。

`404 Not Found` 服务器无法根据客户端的请求找到资源。

`500 Internal Server Error` 服务器内部错误，无法完成请求。

更多状态码可以参考[《HTTP 状态码》(opens new window)](https://tumiblog.top/blogs/浏览器/HTTP 状态码.html#常见状态码)

### 响应头信息

| **响应头**        | **描述**                                           | **示例**                                        |
| ----------------- | -------------------------------------------------- | ----------------------------------------------- |
| Content-Length    | 请求的内容长度                                     | Content-Length: 348                             |
| Content-Type      | 表示文档属于什么 MIME 类型                         | Content-Type: application/x-www-form-urlencoded |
| Connection        | 表示是否需要持久连接。（HTTP 1.1默认进行持久连接） | Connection: close                               |
| Content-Encoding  | web服务器支持的返回内容压缩编码类型。              | Content-Encoding: gzip                          |
| Date              | 请求发送的日期和时间                               | Date: Tue, 15 Nov 2010 08:12:31 GMT             |
| ETag              | 请求变量的实体标签的当前值                         | ETag: “737060cd8c284d8af7ad3082f209582d”        |
| Server            | web 服务器软件名称                                 | Server: Apache/1.3.27 (Unix) (Red-Hat/Linux)    |
| Transfer-Encoding | 文件传输编码                                       | Transfer-Encoding:chunked                       |
| Vary              | 告诉下游代理是使用缓存响应还是从原始服务器请求     | Vary: *                                         |

# Express框架

## 安装node.js

进入Node.js官网](https://nodejs.org/en/download/)

按照自己的机器选择对应的版本下载，我是windous 64位

## Express基本使用

Express：基于 [Node.js](https://nodejs.org/en/) 平台，快速、开放、极简的 Web 开发框架

nodemon 是一个工具，它通过在检测到目录中的文件更改时自动重新启动节点应用程序来帮助开发基于 node.js 的应用程序。

> 注意：当前文件夹不能有中文

```bash
npm init --yes
npm i express
npm install -g nodemon
```

[![h3J0te.png](https://z3.ax1x.com/2021/08/28/h3J0te.png)](https://imgtu.com/i/h3J0te)

```javascript
//1. 引入express
const express = require('express');

//2. 创建应用对象
const app = express();

//3. 创建路由规则
// request 是对请求报文的封装
// response 是对响应报文的封装
app.get('/', (request, response)=>{
    //设置响应
    response.send('HELLO EXPRESS');
});

//4. 监听端口启动服务
app.listen(8000, ()=>{
    console.log("服务已经启动, 8000 端口监听中....");
});
```

**启动服务：**

```bash
nodemon express基本使用.js
浏览器：127.0.0.1:8000
```

**报错：**

[![h3Y2vR.png](https://z3.ax1x.com/2021/08/28/h3Y2vR.png)](https://imgtu.com/i/h3Y2vR)

**解决方法：**

以**管理员身份**打开Windows PowerShell

```bash
set-executionpolicy remotesigned
```

[![h3YOKI.png](https://z3.ax1x.com/2021/08/28/h3YOKI.png)](https://imgtu.com/i/h3YOKI)

# 原生 Ajax

## XHR 简介

`XMLHttpRequest`（XHR）对象用于与服务器交互。通过 XMLHttpRequest 可以在不刷新页面的情况下请求特定 URL，获取数据。这允许网页在不影响用户操作的情况下，更新页面的局部内容。`XMLHttpRequest` 在 [AJAX ](https://developer.mozilla.org/zh-CN/docs/Glossary/AJAX)编程中被大量使用。

## 基本使用

通过 `XMLHttpRequest` 构造函数可以初始化一个 XMLHttpRequest 实例对象。

```js
// 1.创建实例
const xhr = new XMLHttpRequest()

// 2.初始化一个请求（请求类型和 URL）
xhr.open('GET', 'http://127.0.0.1:8000/server')

// 3.发送请求
xhr.send()

// 4.绑定事件，处理服务器端返回结果
xhr.onreadystateChange = function () {
  // 判断当前服务端返回了所有结果
    if (xhr.readState === 4) {
    // 判断响应成功时（2 开头的状态都是成功的）
     if (xhr.status >= 200 && xhr.status < 300) {
       // 处理结果
     } else {
        // ...
     }
  }
}
```

## 属性

| **属性**           | **描述**                                                     |
| ------------------ | ------------------------------------------------------------ |
| onreadystatechange | 接受一个回调函数作为值，当 readystate 属性发生改变时调用函数。 |
| readyState         | 存有 XMLHttpRequest 的状态。从 0 到 4 发生变化。             |
| status             | 返回请求的响应状态（例如，"200"、"404"）。                   |
| statusText         | 返回响应状态字符串（例如，"OK"、"Not Found"）。              |
| response           | 返回整个响应体，具体是哪种类型取决于 responseType 属性。     |
| responseText       | 只能返回"text"类型的响应。                                   |
| responseType       | 返回响应数据的类型。它允许我们手动设置返回数据的类型。如果我们将它设置为一个空字符串，它将使用默认的"text"类型。 |
| timeout            | 表示该请求的最大请求时间（毫秒），若超出该时间，请求会自动终止。 |
| ontimeout          | 接受一个回调函数作为值，当请求超时时调用函数。               |
| onerror            | 接受一个回调函数作为值，当请求遭遇错误时调用函数。           |

## 方法

| **方法**                       | **描述**                                                     |
| ------------------------------ | ------------------------------------------------------------ |
| open(method,url,async)         | 规定请求的类型、URL 以及是否异步处理请求。 method：请求的类型；GET 或 POSTurl：文件在服务器上的位置async：true（异步）或 false（同步） |
| send(string)                   | 将请求发送到服务器。 string：设置请求体，仅用于 POST 请求    |
| setRequestHeader(header,value) | 向请求添加 HTTP 头。 header: 规定头的名称value: 规定头的值   |
| getAllResponseHeaders          | 以字符串的形式返回所有响应头数据，如果没有收到响应，则返回 null。 |
| abort                          | 如果请求已被发出，则立刻中止请求。并将请求的 status 置为 0。 |

## 事件

| **事件** | **描述**                                                     |
| -------- | ------------------------------------------------------------ |
| error    | 当 request 遭遇错误时触发，也可以使用 `onerror` 属性。       |
| timeout  | 在预设时间内没有接收到响应时触发，也可以使用 `ontimeout` 属性。 |

示例：

```js
const xhr = new XMLHttpRequest();

xhr.addEventListener('error', handleEvent);
xhr.addEventListener('timeout', handleEvent);
```

## `readyState` 状态码

| **值** | **状态**         | **描述**                                            |
| ------ | ---------------- | --------------------------------------------------- |
| 0      | UNSENT           | 代理被创建，但尚未调用 `open()` 方法。              |
| 1      | OPENED           | `open()` 方法已经被调用。                           |
| 2      | HEADERS_RECEIVED | `send()` 方法已经被调用，并且头部和状态已经可获得。 |
| 3      | LOADING          | 下载中； `responseText` 属性已经包含部分数据。      |
| 4      | DONE             | 下载操作已完成。                                    |

## GET 设置请求参数

例如 `https://www.baidu.com/s?wd=HTTP`，问号（?）后面的就是请求参数。可以通过 `open` 方法设置。

```js
const xhr = new XMLHttpRequest()

// 设置请求参数
xhr.open('GET', 'http://127.0.0.1:8000/server?a=100&b=300')
```

![2021/05/25/TOIMG4824d0525075719N.png](https://picturebed.tumiblog.top/2021/05/25/TOIMG4824d0525075719N.png)

## POST 设置请求体

POST 请求体需要在 `send` 方法中设置。

```js
const xhr = new XMLHttpRequest()
xhr.open('POST', 'http://127.0.0.1:8000/server')

// 设置请求体
xhr.send('a=100&b=200')
```

请求体可以是任意格式，只要服务器能够处理。

![2021/05/25/TOIMG653b00525075914N.png](https://picturebed.tumiblog.top/2021/05/25/TOIMG653b00525075914N.png)

## 设置请求头信息

通过 `setRequestHeader` 方法设置请求头信息，该方法接收两个参数，第一个参数是属性的名称，第二个参数是属性的值。必须在 `open()` 之后、`send()` 之前调用。

```js
const xhr = new XMLHttpRequest()
xhr.open('GET', 'http://127.0.0.1:8000/server')
xhr.setRequestHeader('Content-Type', 'application/x-www-form-urlencoded')
xhr.send()
```

![2021/05/25/TOIMGe81610525075941N.png](https://picturebed.tumiblog.top/2021/05/25/TOIMGe81610525075941N.png)

注意：自定义一些 header 属性进行跨域请求时，可能会遇到"**not allowed by Access-Control-Allow-Headers in preflight response**"，你可能需要在你的服务端设置"Access-Control-Allow-Headers"。

## 服务端响应 JSON 数据

node 的 `send` 方法只能发送字符串或者 buffer 类型的数据，在实际应用中，服务器响应的绝大多数情况都是 JSON 格式的数据，所以要对响应的数据做一个处理。

第一种方式可以使用 `JSON.parse` 方法进行手动转换

```js
const xhr = new XMLHttpRequest()

xhr.open("POST", "http://localhost:8000/json-server")
xhr.send()

xhr.onreadystatechange = function () {
  if (xhr.readyState === 4) {
    if (xhr.status >= 200 && xhr.status < 300) {
        // 将 JSON 转换成对象
        let data = JSON.parse(xhr.response)
        console.log(data) // {name: "zs"}
    }
  }
}
```

第二种方法可以通过 `XMLHttpRequest.responseType` 属性设置响应类型，如果值为 `'json'` 将会自动进行转换。

```js
const xhr = new XMLHttpRequest()

// 设置响应类型
xhr.responseType = 'json'
xhr.open("POST", "http://localhost:8000/json-server")
xhr.send()

xhr.onreadystatechange = function () {
  if (xhr.readyState === 4) {
    if (xhr.status >= 200 && xhr.status < 300) {
        console.log(xhr.response) // {name: "zs"}
    }
  }
}
```

## IE 缓存问题

IE 浏览器会对同一个 ajax 请求结果做一个缓存，这样会导致重新请求时，浏览器依然使用的是缓存内容。

既然是对同一个 ajax 请求才会缓存，那就发送不同的请求就能解决这个问题了：

```js
const xhr = new XMLHttpRequest()

xhr.open("GET", "http://localhost:8000/ie?t=" + Date.now())
xhr.send()
```

在请求 URL 后面加上一个动态参数就可以了。

## 请求超时与异常处理

我们不能保证服务端永远能够及时快速响应请求，为了给用户友好地反馈信息，需要设置请求超时的处理和请求异常时的处理。

```js
const xhr = new XMLHttpRequest()

// 超时设置 2s
xhr.timeout = 2000
// 超时回调
xhr.ontimeout = function () {
  alert("网络异常，请稍后重试！")
}
// 网络异常回调
xhr.onerror = function () {
  alert("你的网络似乎出了一些问题！")
}

xhr.open("GET", "http://localhost:8000/delay")
xhr.send()
```

请求的状态为 canceled 时，表示请求已经取消了，状态码为 0。

![2021/05/25/TOIMGef46a0525080100N.png](https://picturebed.tumiblog.top/2021/05/25/TOIMGef46a0525080100N.png)

## 取消请求

在请求的过程中，当结果还没有响应时，我们可以使用 `abort` 方法手动取消这个请求。

```js
let flag = false
const xhr = new XMLHttpRequest()

xhr.open("GET", "http://localhost:8000/delay")
xhr.send()

if (!flag) {
  // 取消请求
    xhr.abort() 
}
```

## 请求重复问题

如果用户频繁去发送相同请求，服务器的压力会很大。我们可以在用户发送请求的时候，判断是否发送过相同的请求，如果有，则可以取消请求并重新发送一个新的请求。

```js
// 用来存放 XMLHttpRequest 实例
let xhr = null
// 标识变量，是否发送请求
let isSending = false

btn.addEventListener("click", function () {
    // 如果已经发送了则取消请求
  if (isSending) xhr.abort()
  
  // 当实例被创建时，表示正在发送请求
  xhr = new XMLHttpRequest()
    // 此时更改标识变量
  isSending = true
  xhr.open("GET", "http://localhost:8000/delay")
  xhr.send()

  xhr.onreadystatechange = function () {
    if (xhr.readyState === 4) {
      // 当请求操作完成之后，还原标识变量
      isSending = false
    }
  }
})
```

# jQuery 中的 Ajax

## GET 请求

通过 `$.get()` 方法发送请求，以取代复杂的 `$.ajax()` 方法。请求成功时可调用回调函数。如果需要在出错时执行函数，请使用 `$.ajax()`。

`get()` 接受四个参数：

- `url`：必需，规定需要请求的 URL。
- `data`：可选，规定连同请求发送到服务器的数据。
- `success(response,status,xhr)`：可选。规定请求成功时的回调函数。
- - response - 包含来自请求的结果数据
  - status - 包含请求的状态（"success"、"notmodified"、"error"、"timeout"、"parsererror"）
  - xhr - 包含 XMLHttpRequest 对象
- `dataType`：可选。规定预计的服务器响应的数据类型。默认地，jQuery 将智能判断。
- - "json" - 以 JSON 运行响应，并以 JavaScript 对象返回
  - "jsonp" - 使用 JSONP 加载一个 JSON 块，将添加一个 "?callback=?" 到 URL 来规定回调

示例：

```js
$.get("http://localhost:8000/jquery-server",{ a: 100, b: 200 },function (response, status, xhr) {
  console.log(`Hello,${response.name}`)
}, 'json')
```

jQuery 1.12 中 `$.get()` 和 `$.post()` 都支持对象参数，具体的参数可以参考 `$.ajax()`。

```text
$.get({
  url: "/example"
});
```

## POST 请求

通过 `$.post()` 方法发送 POST 请求，以取代复杂的 `$.ajax()` 方法。请求成功时可调用回调函数。如果需要在出错时执行函数，请使用 `$.ajax()`。

`$.post()` 方法与 `$.get()` 方法接受的参数一样。

```js
$.post("http://localhost:8000/jquery-server",
    $("#testform").serialize(),
  function (response, status, xhr) {
    console.log(response)
}, 'json')
```

上述代码中，`serialize()` 方法可以将表单数据序列化。

## $.ajax() 方法

通用方法 `ajax` 接受一个键值对集合（对象）作为参数，所有选项（键）都是可选的。

```js
$.ajax({
    url: 'http://loacalhost:8000/jquery-server',
  // 参数
  data: {a:100, b:200},
  // 请求类型
  type: 'GET',
  // 响应类型
  dataType: 'json',
  // 成功的回调
  success: function (data) {
    ... 
  },
  // 超时时间
  timeout: 2000,
  // 失败的回调
  error: function () {
    ... 
  }
  // 头信息
  headers: {
    'Content-Type': 'application/x-www-form-urlencoded'
  }
})
```

更多选项可以查看[官方文档](https://api.jquery.com/jQuery.ajax/)或者[中文文档](https://jquery.cuishifeng.cn/jQuery.Ajax.html)

## $.getJSON() 方法

`$.getJSON()` 用于向服务器发送 GET 请求，获取 JSON 格式数据。是 `$.get()` 方法第四个参数为 "json" 的简写方式。

```js
getJSON: function( url, data, callback ) {
  return jQuery.get( url, data, callback, "json" );
}
```

# Axios发送AJAX请求

> axios.get(url,data,params)

```js
  //配置 baseURL
    axios.defaults.baseURL = 'http://127.0.0.1:8000';

    btns[0].onclick = function () {
      //GET 请求
      axios.get('/axios-server', {
        //url 参数
        params: {
          id: 100,
          vip: 7
        },
        //请求头信息
        headers: {
          name: 'atguigu',
          age: 20
        }
      }).then(value => {
        console.log(value);
      });
    }
```

> axios.post(url,data,params)

```js
  //配置 baseURL
    axios.defaults.baseURL = 'http://127.0.0.1:8000';  
	btns[1].onclick = function () {
      axios.post('/axios-server', {
        username: 'admin',
        password: 'admin'
      }, {
        //url 
        params: {
          id: 200,
          vip: 9
        },
        //请求头参数
        headers: {
          height: 180,
          weight: 180,
        }
      });
    }
```

> axios({})

```js
  //配置 baseURL
    axios.defaults.baseURL = 'http://127.0.0.1:8000';
	btns[2].onclick = function () {
      axios({
        //请求方法
        method: 'POST',
        //url
        url: '/axios-server',
        //url参数
        params: {
          vip: 10,
          level: 30
        },
        //头信息,此部分如果使用自定义的头信息,需要服务端进行相应修改,正常不设置
        headers: {
          a: 100,
          b: 200
        },
        //请求体参数
        data: {
          username: 'admin',
          password: 'admin'
        }
      }).then(response => {
        //响应状态码
        console.log(response.status);
        //响应状态字符串
        console.log(response.statusText);
        //响应头信息
        console.log(response.headers);
        //响应体
        console.log(response.data);
      })
    }
```

# Fetch发送AJAX请求

> 代码示例

```js
btn.onclick = function () {
    fetch('http://127.0.0.1:8000/fetch-server?vip=10', {
        //请求方法
        method: 'POST',
        //请求头
        headers: {
            name: 'atguigu'
        },
        //请求体
        body: 'username=admin&password=admin'
    }).then(response => {
        // return response.text();
        return response.json();
    }).then(response => {
        console.log(response);
    });
}
```

# 跨域与解决

## 什么是跨越？

- 一个网页向另一个不同域名/不同协议/不同端口的网页请求资源，这就是跨域。
- 跨域原因产生：在当前域名请求网站中，默认不允许通过ajax请求发送其他域名。

## 为什么会产生跨域请求？

- 因为浏览器使用了同源策略

## 什么是同源策略？

- 同源策略是Netscape提出的一个著名的安全策略，现在所有支持JavaScript的浏览器都会使用这个策略。同源策略是浏览器最核心也最基本的安全功能，如果缺少同源策略，浏览器的正常功能可能受到影响。可以说web是构建在同源策略的基础之上的，浏览器只是针对同源策略的一种实现。
- 同源： 协议、域名、端口号 必须完全相同。 `违背同源策略就是跨域`。

## 为什么浏览器要使用同源策略？

是为了保证用户的信息安全，防止恶意网站窃取数据，如果网页之间不满足同源要求，将不能:

* 共享Cookie、LocalStorage、IndexDB

* 获取DOM

* AJAX请求不能发送

## 跨域的五个解决方式:

 1、前端使用JSONP （不推荐使用）

 2、后台Http请求转发

 3、后台配置同源Cors （推荐）

 4、使用SpringCloud网关

 5、使用nginx做转发 (推荐)

### JSONP

> JSONP 是什么?

JSONP(JSON with Padding)，是一个非官方的跨域解决方案，纯粹凭借程序员的聪明才智开发出来，只支持 `get` 请求。

> JSONP 怎么工作的？

在网页有一些标签天生具有跨域能力，比如：img link iframe script。 JSONP 就是利用 `script 标签的跨域能力`来发送请求的。

#### JSONP的使用

```js
// 1. 动态的创建一个 script 标签------------------------------------------------------------
var script = document.createElement("script");
//2. 设置 script 的 src， 设置回调函数
script.src = "http://localhost:3000/testAJAX?callback=abc";
function abc(data) {
    alert(data.name);
};
// 3. 将 script 添加到 body 中
document.body.appendChild(script);

// 4. 服务器中路由的处理------------------------------------------------------
router.get("/testAJAX", function (req, res) {
    console.log("收到请求");
    var callback = req.query.callback;
    var obj = {
        ame: "孙悟空",
        age: 18
    }
    res.send(callback + "(" + JSON.stringify(obj) + ")");
});
```

#### jQuery发送jsonP请求

```js
//前端代码-----------------------------------------------------------------------------------
$('button').eq(0).click(function () {
  $.getJSON('http://127.0.0.1:8000/jquery-jsonp-server?callback=?', function (data) {
    $('#result').html(`
                名称: ${data.name}<br>
                校区: ${data.city}
            `)
  });
});

//服务端代码-----------------------------------------------------------
app.all('/jquery-jsonp-server', (request, response) => {
  // response.send('console.log("hello jsonp")');
  const data = {
    name: '尚硅谷',
    city: ['北京', '上海', '深圳']
  };
  //将数据转化为字符串
  let str = JSON.stringify(data);
  //接收 callback 参数
  let cb = request.query.callback;

  //返回结果
  response.end(`${cb}(${str})`);
});
```

### CORS

> [CORS文档链接](https://developer.mozilla.org/zh-CN/docs/Web/HTTP/CORS)

**CORS是什么?**

CORS（Cross-Origin Resource Sharing），跨域资源共享。CORS是官方的跨域解决方案，它的特点是不需要在客户端做任何特殊的操作，完全在服务器中进行处理，支持get和post请求。跨域资源共享标准新增了一组HTTP首部字段，允许服务器声明哪些源站通过浏览器有权限访问哪些资源

**CORS是怎么工作的?**

CORS 是通过设置一个响应头来告诉浏览器，该请求允许跨域，浏览器收到该响应以后就会对响应放行。

#### 代码示例

```js
app.all('/cors-server', (request, response) => {
  //设置响应头
    //响应首部中可以携带一个 Access-Control-Allow-Origin 字段
  response.setHeader("Access-Control-Allow-Origin", "*");
    //Access-Control-Allow-Headers 首部字段用于预检请求的响应。其指明了实际请求中允许携带的首部字
  response.setHeader("Access-Control-Allow-Headers", '*');
    //Access-Control-Allow-Methods 首部字段用于预检请求的响应。其指明了实际请求所允许使用的 HTTP
  response.setHeader("Access-Control-Allow-Method", '*');
  // response.setHeader("Access-Control-Allow-Origin", "http://127.0.0.1:5500");
  response.send('hello CORS');
});
```





