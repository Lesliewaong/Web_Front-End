---
title: ES6+
date: 2021-09-12 17:57:47
tags:         
 - JS 
categories: 前端
---

# ES6 的环境配置

## 前言

### ECMAScript 简介

ES 的全称是 ECMAScript，它是由 ECMA 国际标准化组织 制定的一套**脚本语言的标准化规范**。

详细来说，ES 是由 ECMA 的第 39 号技术专家委员会（Technical Committee 39，简称 TC39）负责制订 ECMAScript 标准，成员包括 Microsoft、Mozilla、Google 等公司。

PS：简单来说，ECMAScript 是 JS 的语言标准。当然，ECMAScript 还包括其他脚本语言的语言标准。


### ECMAScript 版本发布记录

-   1995 年：ECMAScript 诞生。

-   1997 年：ECMAScript 标准确立。ECMA 发布 ECMA-262 标准，推出浏览器标准语言 ECMAScript 1.0。

-   1999 年：发布 ES3；与此同时，IE5 风靡一时。

-   2009 年：发布 ECMAScript 5.0（简称 ES5）。例如 foreach、Object.keys、Object.create 和 json 标准。

-   2011 年：发布 ECMAScript5.1，成为 ISO 国际标准，从而推动所有浏览器都支持。

-   2015 年 6 月：发布 ECMAScript 6（简称 ES6），即 ECMAScript 2015。（注意，**前者是按版本号区分，后者是按年份区分**。ES 的后续的版本，请尽量用**年份**来命名。）

-   2016 年 6 月：发布 ECMAScript 7，即 ECMAScript 2016。

-   2017 年 6 月：发布 ECMAScript 8，即 ECMAScript 2017。

-   2018 年 6 月：发布 ECMAScript 9，即 ECMAScript 2018。

-   2019 年 6 月：发布 ECMAScript 10，即 ECMAScript 2019。

-   2020 年 6 月：发布 ECMAScript 11，即 ECMAScript 2020。

-   ......

*   此后，每年更新一版。

### ES6 简介

从上面的 ES 的版本记录可以看出：2015 年 6 月，ES6 正式发布。如果用年份来命名版本号，也可以称之为 ES2015。

ES6 是新的 JS 语法标准。**ES6 实际上是一个泛指，泛指 ES 2015 及后续的版本**。

很多人在做业务选型的时候，会倾向于选 jQuery。其实 jQuery 的语法是偏向于 ES3 的。而现在主流的框架 Vue.js 和 React.js 的默认语法，都是用的 ES6。

ES6 的改进如下：

-   ES6 之前的变量提升，会导致程序在运行时有一些不可预测性。而 ES6 中通过 let、const 变量优化了这一点。

-   ES6 增加了很多功能，比如：**常量、作用域、对象代理、异步处理、类、继承**等。这些在 ES5 中想实现，比较复杂，但是 ES6 对它们进行了封装。

-   ES6 之前的语法过于松散，实现相同的功能，不同的人可能会写出不同的代码。

ES6 的目标是：让 JS 语言可以编写复杂的大型应用程序，成为企业级开发语言。

## ES6 的环境配置（为了兼容 ES5）

掌握 ES6 之后，如果要考虑 ES5 的兼容性，可以这样做：写 ES6 语法的 js 代码，然后通过 `Babel`将 ES6 转换为 ES5。

babel 的作用是将 ES6 语法转为 ES5 语法，支持低端浏览器。

但是，在这之前，我们需要配置一下相关的环境。

### 建立工程目录

（1）先建立一个空的工程目录 `es6`，并在目录下建立两个文件夹 `src`和 `dist`：

-   `src`：书写 ES6 代码，我们写的 js 程序都放在这里。

-   `dist`：利用 Babel 编译生成的 ES5 代码。**我们在 HTML 页面需要引入 dist 里的 js 文件**。

（2）在 工程根目录里新建文件 `index.html`：

```html
<!DOCTYPE html>
<html lang="en">
    <head>
        <meta charset="UTF-8" />
        <meta name="viewport" content="width=device-width, initial-scale=1.0" />
        <meta http-equiv="X-UA-Compatible" content="ie=edge" />
        <title>Document</title>
        <!-- 我们引入 ES5 中的 js 文件，而不是引入 ES6 中的 js 文件。 -->
        <script src="./dist/index.js"></script>
    </head>
    <body></body>
</html>
```

**注意**，上方代码中，我们引入的是`dist`目录下的 js 文件。

然后我们新建文件 `src/index.js`：

```javascript
let a = 'smyhvae';
const b = 'qianguyihao';

console.log(a);
console.log(b);
```

这个文件是一个 ES6 语法 的 js 文件，稍后，我们尝试把这个 ES6 语法的 js 文件转化为 ES5 的 js 文件。

PS：我们在写代码时，能用单引号尽量用单引号，而不是双引号，前者在压缩之后，程序执行会更快。

### 全局安装 Babel-cli

（1）初始化项目：

在安装 Babel 之前，需要先用 npm init 先初始化我们的项目。打开终端或者通过 cmd 打开命令行工具，进入项目目录，输入如下命令：

```bash
npm init -y
```

上方代码中，`-y` 代表全部默认同意，就不用一次次按回车了（稍后再根据需要，在文件中手动修改）。命令执行完成后，会在项目的根目录下生成 package.json 文件：

```json
{
    "name": "es6demo",
    "version": "1.0.0",
    "description": "",
    "main": "index.js",
    "scripts": {
        "test": "echo \"Error: no test specified\" && exit 1"
    },
    "author": "smyhvae",
    "license": "ISC"
}
```

PS：VS Code 里打开终端的快捷键是：`Contol + ~`。

（2）全局安装 Babel-cli：

在终端中输入以下命令：

```bash
npm install -g babel-cli
```

如果安装比较慢的话，Mac 下可以使用`cnpm`进行安装 ，windows 下可以使用`npm`切换到 taobao 的镜像。

（3）本地安装 babel-preset-es2015 和 babel-cli：

```bash
npm install --save-dev babel-preset-es2015 babel-cli
```

安装完成后，会发现`package.json`文件，已经多了 devDependencies 选项：

（4）新建.babelrc：

在根目录下新建文件`.babelrc`，输入如下内容：

```
{
    "presets":[
        "es2015"
    ],
    "plugins":[]
}
```

（5）开始转换：

现在，我们应该可以将 ES6 的文件转化为 ES5 的文件了，命令如下：（此命令略显复杂）

```
babel src/index.js -o dist/index.js
```

我们可以将上面这个命令进行简化一下。操作如下：

在文件 `package.json` 中修改键 `scripts`中的内容：

```json
"scripts": {
    "build": "babel src/index.js -o dist/index.js"
},
```

目前为止，环境配置好了。以后，我们执行如下命令，即可将`src/index.js`这个 ES6 文件转化为 `dist/index.js`这个 ES5 文件：

```bash
npm run build
```

我们执行上面的命令之后，会发现， dist 目录下会生成 ES5 的 js 文件：

index.js：

```javascript
'use strict';

var a = 'smyhvae';
var b = 'qianguyihao';

console.log(a);
console.log(b);
```

当我们打开网页后，就可以在浏览器的控制台，看到代码的输出结果。

# ES5中的严格模式


## 严格模式的理解

### 概念


**理解**：除了正常运行模式(混杂模式)，ES5添加了第二种运行模式："严格模式"（strict mode）。

顾名思义，这种模式使得Javascript在更严格的语法条件下运行。

**目的**：

- 消除Javascript语法的一些不合理、不严谨之处，减少一些怪异行为

- 消除代码运行的一些不安全之处，为代码的安全运行保驾护航

- 为未来新版本的Javascript做好铺垫

### 使用

- 针对整个脚本文件：将`use strict`放在脚本文件的第一行，则整个脚本文件将以严格模式运行。

- 针对单个函数：将`use strict`放在函数体的第一行，则整个函数以严格模式运行。

PS：如果浏览器不支持，则这句话只解析为一条简单的语句, 没有任何副作用。

脚本文件的变通写法：因为第一种调用方法不利于文件合并，所以更好的做法是，借用第二种方法，将整个脚本文件放在一个立即执行的匿名函数之中。


## 严格模式和普通模式的区别

### 1.全局变量必须显式声明

在正常模式中，如果一个变量没有声明就赋值，默认是全局变量。严格模式禁止这种用法，全局变量必须显式声明。

示例：

```js
"use strict";
name="xiaomi";//报错，name未声明
for(item in array){
//报错，item未声明
}
```

在严格模式下，变量都必须先用`var`、`let`或`cons`t声明，然后再使用。

### 2.禁止动态绑定

> 好处：在编译时就确定属性与方法到底归属哪个对象，有利于编译效率的提高，也有助于代码的阅读。

**动态绑定：即某些属性和方法到底属于哪个对象，不是在编译时确定，而是在运行时确定。**

哪些使用了动态绑定？

#### 1.with语句

```js
"use strict";

var obj={
	name:'xiaomi',
	count:12
};
//使用with语句报错
with(obj){
	name:'xiaowang',
	sex:"男"
}
```

为什么使用with语句，不确定属性的归属呢？

很简单，在正常模式下：with绑定的是obj对象，name属性在obj中，而sex不在obj中，则最终会将sex声明为为全局变量。

#### 2.eval作用域

正常模式下：eval语句的作用域取决于它处于全局作用域，还是函数作用域。

严格模式下：eval语句本身就是一个作用域，它生成的变量只能在eval内部使用。

```js
"use strict";
var name='xiaoming';
console.log(eval("var name='xiaohua';name"))//'xiaohua'
console.log(name);//'xiaoming'
```

### 3.禁止this指向全局对象，而是指向undefined

```js
var name="xiaoming";
function foo(){
	console.log(this.name);//'xiaoming'，this指向window
}

function foo(){
	"use strict";
	console.log(this.name);//抛出错误，因为this为undefined
}
```

### 4.禁止删除变量

严格模式下，声明的变量无法被删除，但对象中的属性，若设置了`configurable:true`，即可配置，那么这个对象的属性是可以被删除的。

```js
"use strict";
var name;
delete name; // 语法错误
var obj = Object.create(null, {'count': {
	value: 1,
	configurable: true
}});
delete obj.count; // 删除成功
```

### 5.函数声明必须在顶层

所谓的顶层是在全局中声明，即在块作用域中声明是错误的。

```js
"use strict";
var name='xiaoming'
if (name==='xiaoming') {
    function func() { } // 语法错误
}
for (let i = 0; i < name.length; i++) {
    function func() { } // 语法错误
}
```

### 6.禁止变量或函数参数重名

重名：在同一作用域，两个或两个以上变量名相同。

正常模式下，如果对象有多个重名属性，那么最后一个会覆盖前面的值。

但在严格模式下这是会报错的。

```js
"use strict";
var obj={
	name:"xiaoming",
	name:"xiaohua"
};//报错
```

正常模式下：在函数参数中，如果参数有重名情况，我们可以使用`arguments[i]`读取参数，以便区分参数

```js
function foo(a,b,b,c){
	console.log(arguments[0]);//a
	console.log(arguments[1]);//第一个b
	console.log(arguments[2]);//第二个b
	console.log(arguments[3]);//c
}
```

上面重复参数名，在严格模式下报错。

### 7.限制了arguments对象

#### 1.不允许对arguments赋值

正常模式下：

```js
function foo(a,b){
    console.log("赋值前：",arguments)
    arguments=12;
    console.log("赋值后：",arguments)
}
foo(1,2);
```

严格模式下会报错。

#### 2.arguments不再跟踪参数的变化

```js
function foo(a,b){
    a=11;
    b=22;
    return arguments;
}
console.log("正常模式下：",foo(1,2));//Arguments(2) [11, 22, callee: ƒ, Symbol(Symbol.iterator): ƒ]

function bar(a,b){
    "use strict";
    a=33;
    b=44;
    return arguments;
}
console.log("严格模式下：",bar(3,4));//Arguments(2) [3, 4, callee: (...), Symbol(Symbol.iterator): ƒ]
```
严格模式下，a,b已经重新赋值，但是arguments没有记录它们的变化。

# ES5中的一些扩展

## JSON 对象

1、js对象(数组) --> json对象(数组)：

```javascript
JSON.stringify(obj/arr)
```

2、json对象(数组) --> js对象(数组)：


```javascript
JSON.parse(json)
```


上面这两个方法是ES5中提供的。

我们要记住，我们通常说的“json字符串”，只有两种：**json对象、json数组**。

`typeof json字符串`的返回结果是string。

## Object的扩展

ES5给Object扩展了一些静态方法，常用的有2个，我们接下来讲解。


### 方法一

```javascript
Object.create(prototype, [descriptors])
```

作用: 以指定对象为原型，创建新的对象。同时，第二个参数可以为为新的对象添加新的属性，并对此属性进行描述。

**举例1**：（没有第二个参数时）

```javascript
var obj1 = {username: 'smyhvae', age: 26};
var obj2 = {address:'shenzhen'};

obj2 = Object.create(obj1);
console.log(obj2);
```

obj1成为了obj2的原型。

**举例2**：（有第二个参数时）

第二个参数可以给新的对象添加新的属性。我们修改上面的代码，尝试给obj2添加新属性`sex`：

```javascript
var obj1 = {username: 'smyhvae', age: 26};
var obj2 = {address: 'shenzhen'};

obj2 = Object.create(obj1, {
    sex: {//给obj2添加新的属性`sex`。注意，这一行的冒号不要漏掉
        value: '男',  //通过value关键字设置sex的属性值
        writable: false,
        configurable: true,
        enumerable: true
    }
});

console.log(obj2);

```

上方代码中，我们通过第5行的sex给obj2设置了一个新的属性`sex`，但是要通过`value`来设置属性值（第6行）。

设置完属性值后，这个属性值默认是不可修改的，要通过`writable`来设置。总而言之，这几个关键字的解释如下：

- `value`：设置属性值。

- `writable`：标识当前属性值是否可修改。如果不写的话，默认为false，不可修改。

- `configurable`：标识当前属性是否可以被删除。默认为false，不可删除。

- `enumerable`：标识当前属性是否能用 for in 枚举。 默认为false，不可。

### 方法二

> 这个方法有点难理解。


```javascript
Object.defineProperties(object, descriptors)
```

**作用**：为指定对象定义扩展多个属性。

代码举例：


```javascript
var obj2 = {
    firstName : 'smyh',
    lastName : 'vae'
};
Object.defineProperties(obj2, {
    fullName : {
        get : function () {
            return this.firstName + '-' + this.lastName
        },
        set : function (data) {  //监听扩展属性，当扩展属性发生变化的时候自动调用，自动调用后将变化的值作为实参注入到set函数
            var names = data.split('-');
            this.firstName = names[0];
            this.lastName = names[1];
        }
    }
});
console.log(obj2.fullName);
obj2.firstName = 'tim';
obj2.lastName = 'duncan';
console.log(obj2.fullName);
obj2.fullName = 'kobe-bryant';
console.log(obj2.fullName);
```

- get ：用来获取当前属性值的回调函数

- set ：修改当前属性值得触发的回调函数，并且实参即为修改后的值

存取器属性：setter,getter一个用来存值，一个用来取值。

## Object的扩展（二）

obj对象本身就自带了两个方法。格式如下：


```javascript
get 属性名(){} 用来得到当前属性值的回调函数

set 属性名(){} 用来监视当前属性值变化的回调函数

```

举例如下：

```javascript
var obj = {
    firstName : 'kobe',
    lastName : 'bryant',
    get fullName(){
        return this.firstName + ' ' + this.lastName
    },
    set fullName(data){
        var names = data.split(' ');
        this.firstName = names[0];
        this.lastName = names[1];
    }
};
console.log(obj.fullName);
obj.fullName = 'curry stephen';
console.log(obj.fullName);
```


## 数组的扩展

> 下面讲的这几个方法，都是给数组的实例用的。

**方法1**：


```javascript
Array.prototype.indexOf(value)
```

作用：获取 value 在数组中的第一个下标。

**方法2**：


```javascript
Array.prototype.lastIndexOf(value)
```

作用：获取 value 在数组中的最后一个下标。

**方法3**：遍历数组


```javascript
Array.prototype.forEach(function(item, index){})
```


**方法4**：

```javascript
Array.prototype.map(function(item, index){})
```

作用：遍历数组返回一个新的数组，返回的是**加工之后**的新数组。


**方法5**：

```javascript
Array.prototype.filter(function(item, index){})
```

作用：遍历过滤出一个新的子数组，返回条件为true的值。

## 函数function的扩展：bind()

> ES5中新增了`bind()`函数来改变this的指向。


```javascript
Function.prototype.bind(obj)
```

作用：将函数内的this绑定为obj, 并将函数返回。

**面试题**: call()、apply()和bind()的区别：

- 都能改变this的指向

- call()/apply()是**立即调用函数**

- bind()：绑定完this后，不会立即调用当前函数，而是**将函数返回**，因此后面还需要再加`()`才能调用。

PS：bind()传参的方式和call()一样。

**分析**：

为什么ES5中要加入bind()方法来改变this的指向呢？因为bind()不会立即调用当前函数。

bind()通常使用在回调函数中，因为回调函数并不会立即调用。如果你希望在回调函数中改变this，不妨使用bind()。

# ES6 的变量声明

ES5 中，使用 `var` 定义**全局变量**（ var 是 variable 的简写）。

ES6 中，新增了 let 和 const 来定义变量：

-   `let`：定义**局部变量**，替代 var。

-   `const`：定义**常量**（定义后，不可修改）。

## var：定义全局变量

看下面的代码：

```javascript
{
    var a = 1;
}

console.log(a); //这里的 a，指的是 区块 里的 a
```

上方代码是可以输出结果的，输出结果为 1。因为 var 是全局声明的，所以，即使是在区块里声明，但仍然在全局起作用。

也就是说：**使用 var 声明的变量不具备块级作用域特性**。

再来看下面这段代码：

```javascript
var a = 1;
{
    var a = 2;
}

console.log(a); //这里的 a，指的是 区块 里的 a
```

上方代码的输出结果为 2 ，因为 var 是全局声明的。

**总结：**

用 var 定义的全部变量，有时候会污染整个 js 的作用域。我们在如今的实战中，基本都是用的 ES6 语法，所以请**尽量避免**使用 var 定义变量。

## let：定义局部变量

举例 1：

```js
{
    let a = 'hello';
}
console.log(a); // 打印结果报错：Uncaught ReferenceError: a is not defined
```

上方代码，打印报错。

举例 2：

```javascript
var a = 2;
{
    let a = 3;
}

console.log(a); // 打印结果：2
```

通过上面两个例子可以看出，**用 let 声明的变量，只在局部（块级作用域内）起作用**。

**经典面试题**：

let 可以防止数据污染，我们来看下面这个 **for 循环**的经典面试题。

1、用 var 声明变量：

```javascript
for (var i = 0; i < 10; i++) {
    console.log('循环体中:' + i);
}

console.log('循环体外:' + i);
```

上方代码可以正常打印结果，且最后一行的打印结果是 10。说明**循环体外**定义的变量 i，是**全局作用域**下的 i。

2、用 let 声明变量：

```javascript
for (let i = 0; i < 10; i++) {
    console.log('循环体中:' + i); // // 每循环一次，就会在 { } 所在的块级作用域中，重新定义一个新的变量 i
}

console.log('循环体外:' + i);
```

上方代码的关键在于：**每次循环都会产生一个块级作用域，每个块级作用域中会重新定义一个新的变量 i**。

另外，上方代码的最后一行无法打印结果，也就是说打印会报错。因为用 let 定义的变量 i，只在`{ }`这个**块级作用域**里生效。

**总结：**我们要习惯用 let 声明，减少 var 声明带来的**污染全局空间**。

为了进一步说明 let 不会带来污染，需要说明的是：当我们定义了`let a = 1`时，如果我们在同一个作用域内继续定义`let a = 2`，是会报错的。

## const：定义常量

在程序开发中，有些变量是希望声明后，在业务层就不再发生变化，此时可以用 const 来定义**常量**。

常量就是**值（内存地址）**不能变化的量。

* 如果用 const 声明**基本数据类型**，则无法被修改；

* 如果用 const 声明**引用数据类型（即“对象”）**，这里的“无法被修改”指的是**不能改变内存地址的引用**；

但对象里的**内容**是可以被修改的。

举例：

```javascript
const name = 'smyhvae'; //定义常量
```

用 const 声明的常量，只在局部（块级作用域内）起作用；而且，用 const 声明常量时，必须赋值，否则报错。

## let 和 const 的特点【重要】

- **不属于顶层对象 Window**

  var 声明的变量会挂载在 window 对象上，而 let 和 const 声明的变量不会

- **不允许重复声明**

- **支持块级作用域**

- **不存在变量提升  暂时性死区**

  var可以先使用，再声明（undefined）如果区块中存在 let 和 const 命令，则这个区块对这些命令声明的变量从一开始就形成封闭作用域。只要在声明之前使用这些变量，就会报错。这种语法称为“**暂时性死区**”（temporal dead zone，简称TDZ）。

综上：var 声明的变量，很容易造成**全局污染**。

## for 循环举例（经典案例）

**代码 1**、我们先来看看如下代码：（用 var 定义变量 i）

```html
<!DOCTYPE html>
<html lang="">
    <head>
        <meta />
        <meta />
        <meta />
        <title>Document</title>
    </head>
    <body>
        <input type="button" value="aa" />
        <input type="button" value="bb" />
        <input type="button" value="cc" />
        <input type="button" value="dd" />

        <script>
            var myBtn = document.getElementsByTagName('input');

            for (var i = 0; i < myBtn.length; i++) {
                myBtn[i].onclick = function () {
                    alert(i);
                };
            }
        </script>
    </body>
</html>
```

上方代码中的运行效果如下：

![](http://img.smyhvae.com/20190904_1030.gif)

你可能会感到诧异，为何点击任何一个按钮，弹出的内容都是 4 呢？这是因为，我们用 var 定义的变量 i，是在全局作用域声明的。整个代码中，自始至终只有一个变量。

for 循环是同步代码，而 onclick点击事件是异步代码。当我们还没点击按钮之前，同步代码已经执行完了，变量 i 已经循环到 4 了。

也就是说，上面的 for 循环，相当于如下代码：

```javascript
var i = 0;
myBtn[0].onclick = function () {
    alert(i);
};
i++;

myBtn[1].onclick = function () {
    alert(i);
};
i++;

myBtn[2].onclick = function () {
    alert(i);
};
i++;

myBtn[3].onclick = function () {
    alert(i);
};
i++; // 到这里，i 的值已经是4了。因此，当我们点击按钮时，i的值一直都是4
```

**代码 2**、上面的代码中，如果我们改为用 let 定义变量 i：

```html
<!DOCTYPE html>
<html lang="">
    <head>
        <meta />
        <meta />
        <meta />
        <title>Document</title>
    </head>
    <body>
        <input type="button" value="aa" />
        <input type="button" value="bb" />
        <input type="button" value="cc" />
        <input type="button" value="dd" />

        <script>
            var myBtn = document.getElementsByTagName('input');

            for (let i = 0; i < myBtn.length; i++) {
                myBtn[i].onclick = function () {
                    alert(i);
                };
            }
        </script>
    </body>
</html>
```

上方代码中的运行效果如下：

![](http://img.smyhvae.com/20190904_1040.gif)

上面这个运行结果，才是我们预期的效果。我们用 let 定义变量 i，在循环的过程中，每执行一次循环体，就会诞生一个新的 i。循环体执行 4 次，就会有四个 i。

## 补充知识

### 宏任务与微任务

原理图:

[![4j5ApV.png](https://z3.ax1x.com/2021/10/05/4j5ApV.png)](https://imgtu.com/i/4j5ApV)

说明:

1. JS中用来存储待执行回调函数的队列包含2个不同特定的列队
   - `宏队列`:用来保存待执行的宏任务(回调),比如:`定时器`回调/ajax回调/dom事件回调
   - `微队列`:用来保存待执行的微任务(回调),比如:`Promise`的回调/muntation回调
2. JS执行时会区别这2个队列:
   - JS执行引擎首先必须执行所有的`初始化同步任务`代码
   - 每次准备取出第一个`宏任务执行前`,都要将所有的`微任务`一个一个取出来执行

### ES5 中如何定义常量

ES5中有`Object.defineProperty`这样一个api，可以定义常量。这个API中接收三个参数。

代码举例：

```js
// 定义常量 PI
Object.defineProperty(window, 'PI', {
    value: 3.14,
    writable: false,
});

console.log(PI); // 打印结果：3.14
PI = 6; //尝试修改常量
console.log(PI); //打印结果：3.14，说明修改失败
```

# 解构赋值

## 解构赋值的概念

**解构赋值**：ES6 允许我们，按照一一对应的方式，从数组或者对象中**提取值**，再将提取出来的值赋值给变量。

解构：分解数据结构；赋值：给变量赋值。

解构赋值在实际开发中可以大量减少我们的代码量，并且让程序结构更清晰。

## 数组的解构赋值

数组的结构赋值：将数组中的值按照**位置**提取出来，然后赋值给变量。

### 语法

在 ES6 之前，当我们在为一组变量赋值时，一般是这样写：

```javascript
var a = 1;
var b = 2;
var c = 3;
```

或者是这样写：

```js
var arr = [1, 2, 3];

var a = arr[0];
var b = arr[1];
var c = arr[2];
```

现在有了 ES6 之后，我们可以通过数组解构的方式进行赋值：（根据**位置**进行一一对应）

```javascript
let [a, b, c] = [1, 2, 3];
```

二者的效果是一样的，但明显后者的代码更简洁优雅。

### 未匹配到的情况

数据的结构赋值，是根据位置进行一一对应来赋值的。可如果左边的数量大于右边的数量时（也就是变量的数量大于值的数量时），多余的变量要怎么处理呢？

答案是：如果变量在一一对应时，没有找到对应的值，那么，**多余的变量会被赋值为 undefined**。

### 解构时，左边允许有默认值

在解构赋值时，是允许使用默认值的。举例如下：

```javascript
{
    //一个变量时
    let [foo = true] = [];
    console.log(foo); //输出结果：true
}

{
    //两个变量时
    let [a, b] = ['123']; //a 赋值为：123。b没有赋值
    console.log(a + ',' + b); //输出结果：123,undefined
}

{
    //两个变量时
    let [a, b = 'leslie'] = ['wang']; //a 赋值为：wang。b 采用默认值 leslie
    console.log(a + ',' + b); //输出结果：生命壹号,leslie
}
```

### 将右边的 `undefined`和`null`赋值给变量

如果我们在赋值时，采用的是 `undefined`或者`null`，那会有什么区别呢？

```javascript
{
    let [a, b = 'leslie'] = ['wang', undefined]; //b 虽然被赋值为 undefined，但是 b 会采用默认值
    console.log(a + ',' + b); //输出结果：wang,leslie
}

{
    let [a, b = 'leslie'] = ['wang', null]; //b 被赋值为 null
    console.log(a + ',' + b); //输出结果：wang,null
}
```

上方代码分析：

-   undefined：相当于什么都没有，此时 b 采用默认值。

-   **null：相当于有值，但值为 null。**

## 对象的解构赋值

对象的结构赋值：将对象中的值按照**属性匹配的方式**提取出来，然后赋值给变量。

### 语法

在 ES6 之前，我们从接口拿到 json 数据后，一般这么赋值：

```javascript
var name = json.name;

var age = json.age;

var sex = json.sex;
```

上面这种写法，过于麻烦了。

现在，有了 ES6 之后，我们可以使用对象解构的方式进行赋值。举例如下：

```js
const person = { name: 'leslie', age: 28, sex: '男' };
let { name, age, sex } = person; // 对象的结构赋值

console.log(name); // 打印结果：leslie
console.log(age); // 打印结果：28
console.log(sex); // 打印结果：男
```

上方代码可以看出，对象的解构与数组的结构，有一个重要的区别：**数组**的元素是按次序排列的，变量的取值由它的**位置**决定；

而**对象的属性没有次序**，是**根据键来取值**的。


### 未匹配到的情况

对象的结构赋值，是根据属性名进行一一对应来赋值的。可如果左边的数量大于右边的数量时（也就是变量的数量大于值的数量时），多余的变量要怎么处理呢？

答案是：如果变量在一一对应时，没有找到对应的值，那么，**多余的变量会被赋值为 undefined**。


### 给左边的变量自定义命名

对象的结构赋值里，左边的变量名一定要跟右边的属性名保持一致么？答案是不一定。我们可以单独给左边的变量自定义命名。

举例如下：

```js
const person = { name: 'leslie', age: 28 };
let { name: myName, age: myAge } = person; // 对象的结构赋值

console.log(myName); // 打印结果：leslie
console.log(myAge); // 打印结果：28

console.log(name); // 打印报错：Uncaught ReferenceError: name is not defined
console.log(age); // 打印报错：Uncaught ReferenceError: age is not defined
```

上方的第 2 行代码中：（请牢记）

-   等号左边的属性名 name、age 是对应等号右边的属性名。

-   等号左边的 myName、myAge 是左边自定义的变量名。

### 圆括号的使用

如果变量 foo 在解构之前就已经定义了，此时你再去解构，就会出现问题。下面是错误的代码，编译会报错：

```javascript
let foo = 'haha';
{ foo } = { foo: 'leslie' };
console.log(foo);
```

要解决报错，只要在解构的语句外边，加一个圆括号即可：

```javascript
let foo = 'haha';
({ foo } = { foo: 'leslie' });
console.log(foo); //输出结果：leslie
```

## 字符串解构

字符串也可以解构，这是因为，此时字符串被转换成了一个类似数组的对象。举例如下：

```javascript
const [a, b, c, d] = 'hello';
console.log(a);
console.log(b);
console.log(c);

console.log(typeof a); //输出结果：string
```

打印结果：

```
h
e
l
string
```

# 函数扩展

## 箭头函数

### 定义箭头函数的语法

语法：

```js
(参数1, 参数2 ...) => { 函数体 }
```

解释：

-   如果有且仅有 1 个形参，则`()`可以省略

-   如果函数体内有且仅有 1 条语句，则`{}`可以省略，但前提是，这条语句必须是 return 语句。

需要强调的是，箭头函数是没有函数名的，既然如此，那要怎么调用箭头函数呢？你可以将箭头函数赋值给一个变量，通过变量名调用函数；也可以直接使用箭头函数。我们来看看下面的例子。

### 举例

写法 1、定义和调用函数：（传统写法）

```javascript
function fn1(a, b) {
    console.log('haha');
    return a + b;
}
console.log(fn1(1, 2)); //输出结果：3
```

写法 2、定义和调用函数：（ES6中的写法）

```javascript
const fn2 = (a, b) => {
    console.log('haha');
    return a + b;
};
console.log(fn2(1, 2)); //输出结果：3
```

上面的两种写法，效果是一样的。

从上面的箭头函数中，我们可以很清晰地看到变量名、参数名、函数体。

另外，箭头函数的写法还可以精简一下，继续往下看。

在箭头函数中，如果方法体内只有一句话，且这句话是 return 语句，那就可以把 `{}`省略。写法如下：

```javascript
const fn2 = (a, b) => a + b;

console.log(fn2(1, 2)); //输出结果：3
```

在箭头函数中，如果形参只有一个参数，则可以把`()`省略。写法如下：

```js
const fn2 = a => {
    console.log('haha');
    return a + 1;
};

console.log(fn2(1)); //输出结果：2
```

## 箭头函数的 this 的指向

> 箭头函数只是为了让函数写起来更简洁优雅吗？当然不只是这个原因，还有一个很大的作用是与 this 的指向有关。

ES6 之前的普通函数中：this 指向的是函数被调用的对象（也就是说，谁调用了函数，this 就指向谁）。

而 ES6 的箭头函数中：**箭头函数本身不绑定 this**，this 指向的是**箭头函数定义位置的 this**（也就是说，箭头函数在哪个位置定义的，this 就跟这个位置的 this 指向相同）。

代码举例：

```js
const obj = { name: 'leslie' };

function fn1() {
    console.log(this); // 第一个 this
    return () => {
        console.log(this); // 第二个 this
    };
}

const fn2 = fn1.call(obj);
fn2();
```

打印结果：

```
obj
obj
```

代码解释：（一定要好好理解下面这句话）

上面的代码中，箭头函数是在 fn1()函数里面定义的，所以第二个 this 跟 第一个 this 指向的是**同一个位置**。又因为，在执行 `fn1.call(obj)`之后，第一个 this 就指向了 obj，所以第二个 this 也是指向 了 obj。

### 面试题：箭头函数的 this 指向

代码举例：

```js
var name = '许嵩';
var obj = {
    name: 'leslie',
    sayHello: () => {
        console.log(this.name);
    },
};

obj.sayHello();
```

上方代码的打印结果是什么？你可能很难想到。

正确答案的打印结果是`许嵩`。因为 `obj` 这个对象并不产生作用域， `sayHello()` 这个箭头函数实际仍然是定义在 window 当中的，所以 这里的 this 指向是 window。

### 补充

**作用域**

  - 全局作用域
  - 函数作用域：`function() {}`
  - 块级作用域：`{}`

## 参数默认值

**传统写法**：

```javascript
function fn(param) {
    let p = param || 'hello';
    console.log(p);
}
```

上方代码中，函数体内的写法是：如果 param 不存在，就用 `hello`字符串做兜底。这样写比较啰嗦。

**ES6 写法**：（参数默认值的写法，很简洁）

```javascript
function fn(param = 'hello') {
    console.log(param);
}
```

在 ES6 中定义方法时，我们可以给方法里的参数加一个**默认值**（缺省值）：

-   方法被调用时，如果没有给参数赋值，那就是用默认值；

-   方法被调用时，如果给参数赋值了新的值，那就用新的值。

如下：

```javascript
var fn2 = (a, b = 5) => {
    console.log('haha');
    return a + b;
};
console.log(fn2(1)); //第二个参数使用默认值 5。输出结果：6

console.log(fn2(1, 8)); //输出结果：9
```

**提醒 1**：默认值的后面，不能再有**没有默认值的变量**。比如`(a,b,c)`这三个参数，如果我给 b 设置了默认值，那么就一定要给 c 设置默认值。

**提醒 2**：

我们来看下面这段代码：

```javascript
let x = 'smyh';
function fn(x, y = x) {
    console.log(x, y);
}
fn('vae');
```

注意第二行代码，我们给 y 赋值为`x`，这里的`x`是括号里的第一个参数，并不是第一行代码里定义的`x`。打印结果：`vae vae`。

如果我把第一个参数改一下，改成：

```javascript
let x = 'smyh';
function fn(z, y = x) {
    console.log(z, y);
}
fn('vae');
```

此时打印结果是：`vae smyh`。

## 剩余参数

**剩余参数**允许我们将不确定数量的**剩余的元素**放到一个**数组**中。

比如说，当函数的实参个数大于形参个数时，我们可以将剩余的实参放到一个数组中。

**传统写法**：

ES5 中，在定义方法时，参数要确定个数，如下：（程序会报错）

```javascript
function fn(a, b, c) {
    console.log(a);
    console.log(b);
    console.log(c);
    console.log(d);
}

fn(1, 2, 3);
```

上方代码中，因为方法的参数是三个，但使用时是用到了四个参数，所以会报错：

**ES6 写法**：

ES6 中，我们有了剩余参数，就不用担心报错的问题了。代码可以这样写：

```javascript
const fn = (...args) => {
    //当不确定方法的参数时，可以使用剩余参数
    console.log(args[0]);
    console.log(args[1]);
    console.log(args[2]);
    console.log(args[3]);
};

fn(1, 2);
fn(1, 2, 3); //方法的定义中了四个参数，但调用函数时只使用了三个参数，ES6 中并不会报错。
```

打印结果：

```bash
1
2
undefined
undefined


1
2
3
undefined
```

上方代码中注意，args 参数之后，不能再加别的参数，否则编译报错。

下面这段代码，也是利用到了剩余参数：

```js
function fn1(first, ...args) {
    console.log(first); // 10
    console.log(args); // 数组：[20, 30]
}

fn1(10, 20, 30);
```

### 剩余参数的举例：参数求和

代码举例：

```js
const sum = (...args) => {
    let total = 0;
    args.forEach(function(item) {
		total += item;
	});
    args.forEach(item => total += item); // 注意 forEach里面的代码，写得 很精简
    return total;
};
console.log(sum(10, 20, 30));
```

打印结果：60

### 剩余参数和解构赋值配合使用

代码举例：

```js
const students = ['张三', '李四', '王五'];
let [s1, ...s2] = students;

console.log(s1); // '张三'
console.log(s2); // ['李四', '王五']
```

## 扩展运算符（展开语法）

扩展运算符和剩余参数是相反的。

剩余参数是将剩余的元素放到一个数组中；

而扩展运算符是将**数组**或者**可迭代对象**拆分成逗号分隔的参数序列。

代码举例：

```js
const arr = [10, 20, 30];
...arr // 10, 20, 30      注意，这一行是伪代码，这里用到了扩展运算符
console.log(...arr); // 10 20 30

console.log(10, 20, 30); // 10 20 30
```

上面的代码要仔细看：

`arr`是一个数组，而`...arr`则表示`10, 20, 30`这样的序列。

我们把`...arr` 打印出来，发现打印结果竟然是 `10 20 30`，为啥逗号不见了呢？因为逗号被当作了 console.log 的参数分隔符。如果你不信，可以直接打印 `console.log(10, 20, 30)` 看看。

接下来，我们看一下扩展运算符的应用。

### 举例1：数组赋值

数组赋值的代码举例：

```js
let arr2 = [...arr1]; // 将 arr1 赋值给 arr2
```

为了理解上面这行代码，我们先来分析一段代码：（将数组 arr1 赋值给 arr2）

```javascript
let arr1 = ['www', 'smyhvae', 'com'];
let arr2 = arr1; // 将 arr1 赋值给 arr2，其实是让 arr2 指向 arr1 的内存地址
console.log('arr1:' + arr1);
console.log('arr2:' + arr2);
console.log('---------------------');

arr2.push('你懂得'); //往 arr2 里添加一部分内容
console.log('arr1:' + arr1);
console.log('arr2:' + arr2);
```

上方代码中，我们往往 arr2 里添加了`你懂的`，却发现，arr1 里也有这个内容。原因是：`let arr2 = arr1;`

其实是让 arr2 指向 arr1 的地址。也就是说，二者指向的是同一个内存地址。

如果不想让 arr1 和 arr2 指向同一个内存地址，我们可以借助**扩展运算符**来做：

```javascript
let arr1 = ['www', 'smyhvae', 'com'];
let arr2 = [...arr1]; //【重要代码】arr2 会重新开辟内存地址
console.log('arr1:' + arr1);
console.log('arr2:' + arr2);
console.log('---------------------');

arr2.push('你懂得'); //往arr2 里添加一部分内容
console.log('arr1:' + arr1);
console.log('arr2:' + arr2);
```

运行结果：

```bash
arr1:www,smyhvae,com
arr2:www,smyhvae,com
---------------------
arr1:www,smyhvae,com
arr2:www,smyhvae,com,你懂得
```

我们明白了这个例子，就可以避免开发中的很多业务逻辑上的 bug。

### 举例2：合并数组

代码举例：

```js
let arr1 = ['王一', '王二', '王三'];
let arr2 = ['王四', '王五', '王六'];
// ...arr1  // '王一','王二','王三'
// ...arr2  // '王四','王五','王六'

// 方法1
let arr3 = [...arr1, ...arr2];
console.log(arr3); // ["王一", "王二", "王三", "王四", "王五", "王六"]

// 方法2
arr1.push(...arr2);
console.log(arr1); // ["王一", "王二", "王三", "王四", "王五", "王六"]
```

### 举例3：将伪数组或者可遍历对象转换为真正的数组

代码举例：

```js
const myDivs = document.getElementsByClassName('div');
const divArr = [...myDivs]; // 利用扩展运算符，将伪数组转为真正的数组
```

**补充**：

我们在《JavaScript基础/数组的常见方法》中也学过，还有一种方式，可以将伪数组（或者可遍历对象）转换为真正的数组。语法格式如下：

```js
let arr2 = Array.from(arrayLike);
```

# 字符串的扩展

## 模板字符串

ES6 引入新的声明字符串的方式 `『``』` 之前 `''` `""` 

```js
//1. 声明
// let str = `我也是一个字符串哦!`;
// console.log(str, typeof str);

//2. 内容中可以直接出现换行符
let str = `<ul>
				<li>沈腾</li>
				<li>玛丽</li>
				<li>魏翔</li>
				<li>艾伦</li>
			</ul>`;
//3. 变量拼接
let lovest = '魏翔';
let out = `${lovest}是我心目中最搞笑的演员!!`;
console.log(out);
```

## 其他扩展

ES6 中的字符串扩展如下：

-   `includes(str)`：判断是否包含指定的字符串
-   `startsWith(str)`：判断是否以指定字符串开头
-   `endsWith(str)`：判断是否以指定字符串结尾
-   `repeat(count)`：重复指定次数
-   `trimStart()`：清除左侧空白
-   `trimEnd()`：清除右侧空白

举例如下：

```javascript
let str = 'abcdefg';

console.log(str.includes('a')); //true
console.log(str.includes('h')); //false

//startsWith(str) : 判断是否以指定字符串开头
console.log(str.startsWith('a')); //true
console.log(str.startsWith('d')); //false

//endsWith(str) : 判断是否以指定字符串结尾
console.log(str.endsWith('g')); //true
console.log(str.endsWith('d')); //false

//repeat(count) : 重复指定次数a
console.log(str.repeat(5));

// trim
let str = '   iloveyou   ';

console.log(str);
console.log(str.trimStart());
console.log(str.trimEnd());
```

**String.prototype.matchAll**

```js
let str = `<ul>
				<li>
					<a>肖生克的救赎</a>
					<p>上映日期: 1994-09-10</p>
				</li>
				<li>
					<a>阿甘正传</a>
					<p>上映日期: 1994-07-06</p>
				</li>
			</ul>`;

//声明正则
const reg = /<li>.*?<a>(.*?)<\/a>.*?<p>(.*?)<\/p>/sg

//调用方法
const result = str.matchAll(reg);

// for(let v of result){
//     console.log(v);
// }

const arr = [...result];

console.log(arr);
```



# Number的扩展

-   二进制与八进制数值表示法: 二进制用`0b/0B`, 八进制用`0o/0O`。
-   **指数运算符**:`ES2016` 新增的 ,指数运算符（`**`）。
-   `Number.EPSILON`：数值最小精度
-   `Number.MIN_SAFE_INTEGER`：最小安全数值(`-2^53`)
-   `Number.MAX_SAFE_INTEGER`：最大安全数值(`2^53`)
-   `Number.parseInt()`：返回转换值的整数部分
-   `Number.parseFloat()`：返回转换值的浮点数部分
-   `Number.isFinite()`：是否为有限数值
-   `Number.isNaN()`：是否为NaN
-   `Number.isInteger()`：是否为整数
-   `Number.isSafeInteger()`：是否在数值安全范围内
-   `Math.trunc()`：返回数值整数部分
-   `Math.sign()`：返回数值类型(`正数1`、`负数-1`、`零0`)
-   `Math.cbrt()`：返回数值立方根
-   `Math.clz32()`：返回数值的32位无符号整数形式
-   `Math.imul()`：返回两个数值相乘
-   `Math.fround()`：返回数值的32位单精度浮点数形式
-   `Math.hypot()`：返回所有数值平方和的平方根
-   `Math.expm1(n)`：返回`e^n - 1``
-   ``Math.log1p(n)`：返回`1 + n`的自然对数(`Math.log(1 + n)`)
-   `Math.log10(n)`：返回以10为底的n的对数
-   `Math.log2(n)`：返回以2为底的n的对数
-   `Math.sinh(n)`：返回n的双曲正弦
-   `Math.cosh(n)`：返回n的双曲余弦
-   `Math.tanh(n)`：返回n的双曲正切
-   `Math.asinh(n)`：返回n的反双曲正弦
-   `Math.acosh(n)`：返回n的反双曲余弦
-   `Math.atanh(n)`：返回n的反双曲正切

```js
//0. Number.EPSILON 是 JavaScript 表示的最小精度
//EPSILON 属性的值接近于 2.2204460492503130808472633361816E-16
function equal(a, b){
    if(Math.abs(a-b) < Number.EPSILON){
        return true;
    }else{
        return false;
    }
}
console.log(0.1 + 0.2 === 0.3);
console.log(equal(0.1 + 0.2, 0.3))

//1. 二进制和八进制
let b = 0b1010;
let o = 0o777;
let d = 100;
let x = 0xff;
console.log(x);

//2. Number.isFinite  检测一个数值是否为有限数
console.log(Number.isFinite(100));
console.log(Number.isFinite(100/0));
console.log(Number.isFinite(Infinity));

//3. Number.isNaN 检测一个数值是否为 NaN 
console.log(Number.isNaN(123)); 

//4. Number.parseInt Number.parseFloat
console.log(Number.parseInt('5211314love'));
console.log(Number.parseFloat('3.1415926神奇'));

//5. Number.isInteger 判断一个数是否为整数
console.log(Number.isInteger(5));
console.log(Number.isInteger(2.5));

//6. Math.trunc 将数字的小数部分抹掉  
console.log(Math.trunc(3.5));

//7. Math.sign 判断一个数到底为正数 负数 还是零
console.log(Math.sign(100));
console.log(Math.sign(0));
console.log(Math.sign(-20000));
```

# Symbol

## 概述

背景：ES5中对象的属性名都是字符串，容易造成重名，污染环境。

**概念**：ES6 引入了一种新的原始数据类型`Symbol`，表示独一无二的值。它是 JavaScript 语言的第七种数据类型，前六种是：`undefined`、`null`、`布尔值（Boolean）`、`字符串（String）`、`数值（Number）`、`对象（Object）`。

**特点：**

- Symbol属性对应的值是唯一的，解决**命名冲突问题**

- Symbol值不能与其他数据进行计算，包括同字符串拼串

- for in、for of 遍历时不会遍历Symbol属性。


## 创建Symbol属性值

Symbol是函数，但并不是构造函数。创建一个Symbol数据类型：

```javascript
let mySymbol = Symbol();

console.log(typeof mySymbol);  //打印结果：symbol
console.log(mySymbol);         //打印结果：Symbol()
```

下面来讲一下Symbol的使用。

## 创建Symbol属性值时，传参作为标识

如果我通过 Symbol()函数创建了两个值，这两个值是不一样的：

```javascript
let mySymbol1 = Symbol();
let mySymbol2 = Symbol();

console.log(mySymbol1 == mySymbol2); //打印结果：false
console.log(mySymbol1);         //打印结果：Symbol()
console.log(mySymbol2);         //打印结果：Symbol()
```

上面代码中，倒数第三行的打印结果也就表明了，二者的值确实是不相等的。

最后两行的打印结果却发现，二者的打印输出，肉眼看到的却相同。那该怎么区分它们呢？

既然Symbol()是函数，函数就可以传入参数，我们可以通过参数的不同来作为**标识**。比如：


```javascript
//在括号里加入参数，来标识不同的Symbol
let mySymbol1 = Symbol('one');
let mySymbol2 = Symbol('two');

console.log(mySymbol1 == mySymbol2); //打印结果：false
console.log(mySymbol1);         //打印结果：Symbol(one)
console.log(mySymbol2);         //打印结果：Symbol(two)。颜色为红色。
console.log(mySymbol2.toString());//打印结果：Symbol(two)。颜色为黑色。

//Symbol.for 创建
let s4 = Symbol.for('尚硅谷');
let s5 = Symbol.for('尚硅谷');
console.log(s4 == s5);
```

## 将Symbol作为对象的属性值

```javascript
let mySymbol = Symbol();
let obj = {
    name: 'smyhvae',
    age: 26
};
//obj.mySymbol = 'male'; //错误：不能用 . 这个符号给对象添加 Symbol 属性。
obj[mySymbol] = 'hello';    //正确：通过**属性选择器**给对象添加 Symbol 属性。后面的属性值随便写。
console.log(obj);
```

上面的代码中，我们尝试给obj添加一个Symbol类型的属性值，但是添加的时候，不能采用`.`这个符号，而是应该用`属性选择器`的方式。

现在我们用for in尝试对上面的obj进行遍历：

```javascript
let mySymbol = Symbol();

let obj = {
    name: 'smyhvae',
    age: 26
};

obj[mySymbol] = 'hello';

console.log(obj);

//遍历obj
for (let i in obj) {
    console.log(i);
}
```

从打印结果中可以看到：for in、for of 遍历时不会遍历Symbol属性。

```js
//向对象中添加方法 up down
let game = {
    name:'俄罗斯方块',
    up: function(){},
    down: function(){}
};

//声明一个对象
// let methods = {
//     up: Symbol(),
//     down: Symbol()
// };

// game[methods.up] = function(){
//     console.log("我可以改变形状");
// }

// game[methods.down] = function(){
//     console.log("我可以快速下降!!");
// }

// console.log(game);

//
let youxi = {
    name:"狼人杀",
    [Symbol('say')]: function(){
        console.log("我可以发言")
    },
    [Symbol('zibao')]: function(){
        console.log('我可以自爆');
    }
}

console.log(youxi)
```

## 定义常量

Symbol 可以用来定义常量：


```javascript
const MY_NAME = Symbol('my_name');
```


## 内置的 Symbol 值

除了定义自己使用的 Symbol 值以外，ES6 还提供了 11 个内置的 Symbol 值，指向语言内部使用的方法。

```js
class Person{
    static [Symbol.hasInstance](param){
        console.log(param);
        console.log("我被用来检测类型了");
        return false;
    }
}

let o = {};

console.log(o instanceof Person);

const arr = [1,2,3];
const arr2 = [4,5,6];
arr2[Symbol.isConcatSpreadable] = false;
console.log(arr.concat(arr2));
```

## 迭代器

迭代器（Itertor）是一种接口，为各种不同的数据结构提供统一的访问机制。

任何数据结构只要部署了Itertor接口(其实就是对象中的一个属性)，就可以完成遍历操作。

* ES6创造了一种新的遍历命令`for...of`循环，Itertor接口主要供`for...of`消费

* 原生具备Itertor接口的数据
  * Array
  * Arguments
  * Set
  * Map
  * String
  * TypedArray
  * NodeList

* 工作原理

  * 创建一个指针对象，指向当前数据结构的起始位置
  * 第一次调用对象的next方法，指针自动指向数据结构的第一个成员
  * 接下来不断调用next方法，指针一直往后移动，直到指向最后一个成员
  * 每调用next方法返回一个包含value和done属性的对象

  **注;需要自定义遍历数据的时候，要想到迭代器**

```js
//声明一个数组
const xiyou = ['唐僧','孙悟空','猪八戒','沙僧'];

//使用 for...of 遍历数组
// for(let v of xiyou){
//     console.log(v);
// }

let iterator = xiyou[Symbol.iterator]();

//调用对象的next方法
console.log(iterator.next());
console.log(iterator.next());
console.log(iterator.next());
console.log(iterator.next());
console.log(iterator.next());
```

> 自定义遍历数据

```js
//声明一个对象
const banji = {
    name: "终极一班",
    stus: [
        'xiaoming',
        'xiaoning',
        'xiaotian',
        'knight'
    ],
    [Symbol.iterator]() {
        //索引变量
        let index = 0;
        //
        let _this = this;
        return {
            next: function () {
                if (index < _this.stus.length) {
                    const result = { value: _this.stus[index], done: false };
                    //下标自增
                    index++;
                    //返回结果
                    return result;
                }else{
                    return {value: undefined, done: true};
                }
            }
        };
    }
}

//遍历这个对象 
for (let v of banji) {
    console.log(v);
}
```

## 生成器

生成器其实就是一个特殊的函数 异步编程

异步编程  纯回调函数  node fs  ajax mongodb

```js
//函数代码的分隔符 yield
function * gen(){
    // console.log(111);
    yield '一只没有耳朵';
    // console.log(222);
    yield '一只没有尾部';
    // console.log(333);
    yield '真奇怪';
    // console.log(444);
}

let iterator = gen();
console.log(iterator.next());
console.log(iterator.next());
console.log(iterator.next());
console.log(iterator.next());

//遍历
// for(let v of gen()){
//     console.log(v);
// }
```

> 生成器函数的参数

```js
function * gen(arg){
    console.log(arg);
    let one = yield 111;
    console.log(one);
    let two = yield 222;
    console.log(two);
    let three = yield 333;
    console.log(three);
}

//执行获取迭代器对象
let iterator = gen('AAA');
console.log(iterator.next());
//next方法可以传入实参
console.log(iterator.next('BBB'));
console.log(iterator.next('CCC'));
console.log(iterator.next('DDD'));
```

> 生成器函数实例

```js
// 异步编程  文件操作 网络操作(ajax, request) 数据库操作
// 1s 后控制台输出 111  2s后输出 222  3s后输出 333 
// 回调地狱
// setTimeout(() => {
//     console.log(111);
//     setTimeout(() => {
//         console.log(222);
//         setTimeout(() => {
//             console.log(333);
//         }, 3000);
//     }, 2000);
// }, 1000);

function one(){
    setTimeout(()=>{
        console.log(111);
        iterator.next();
    },1000)
}

function two(){
    setTimeout(()=>{
        console.log(222);
        iterator.next();
    },2000)
}

function three(){
    setTimeout(()=>{
        console.log(333);
        iterator.next();
    },3000)
}

function * gen(){
    yield one();
    yield two();
    yield three();
}

//调用生成器函数
let iterator = gen();
iterator.next();
```

```js
//模拟获取  用户数据  订单数据  商品数据 
function getUsers(){
    setTimeout(()=>{
        let data = '用户数据';
        //调用 next 方法, 并且将数据传入
        iterator.next(data);
    }, 1000);
}

function getOrders(){
    setTimeout(()=>{
        let data = '订单数据';
        iterator.next(data);
    }, 1000)
}

function getGoods(){
    setTimeout(()=>{
        let data = '商品数据';
        iterator.next(data);
    }, 1000)
}

function * gen(){
    let users = yield getUsers();
    let orders = yield getOrders();
    let goods = yield getGoods();
}

//调用生成器函数
let iterator = gen();
iterator.next();
```

# 数组的扩展

-   Array.from()
-   find()
-   findIndex()

```js
//flat 平
//将多维数组转化为低维数组
// const arr = [1,2,3,4,[5,6]];
// const arr = [1,2,3,4,[5,6,[7,8,9]]];
//参数为深度 是一个数字
// console.log(arr.flat(2));  

//flatMap
const arr = [1,2,3,4];
const result = arr.flatMap(item => [item * 10]);
console.log(result);
```

# 对象的扩展

## 简化对象写法

```js
//ES6 允许在大括号里面，直接写入变量和函数，作为对象的属性和方法。
//这样的书写更加简洁
let name = '尚硅谷';
let change = function(){
    console.log('我们可以改变你!!');
}

const school = {
    name,
    change,
    improve(){
        console.log("我们可以提高你的技能");
    }
}

console.log(school);
```

## class类

ES6 提供了更接近传统语言的写法，引入了 Class（类）这个概念，作为对象的模板。

通过 class 关键字，可以定义类。基本上，ES6 的 class 可以看作只是一个语法糖，它的绝大部分功能，ES5 都可以做到。

新的 class 写法只是让对象原型的写法更加清晰、更像面向对象编程的语法而已。

知识点：

* class 声明类；
* constructor 定义构造函数初始化；
* extends 继承父类；
* super 调用父级构造方法；
* static 定义静态方法和属性；
* 父类方法可以重写；

```js
//手机
function Phone(brand, price){
    this.brand = brand;
    this.price = price;
}

//添加方法
Phone.prototype.call = function(){
    console.log("我可以打电话!!");
}

//实例化对象
let Huawei = new Phone('华为', 5999);
Huawei.call();
console.log(Huawei);

//class
class Shouji{
    //构造方法 名字不能修改
    constructor(brand, price){
        this.brand = brand;
        this.price = price;
    }

    //方法必须使用该语法, 不能使用 ES5 的对象完整形式
    call(){
        console.log("我可以打电话!!");
    }
}

let onePlus = new Shouji("1+", 1999);

console.log(onePlus);
```

### 静态成员

属于类，但不属于实例对象

```js
// function Phone(){

// }
// Phone.name = '手机';
// Phone.change = function(){
//     console.log("我可以改变世界");
// }
// Phone.prototype.size = '5.5inch';

// let nokia = new Phone();

// console.log(nokia.name);
// // nokia.change();
// console.log(nokia.size);

class Phone{
    //静态属性
    static name = '手机';
static change(){
    console.log("我可以改变世界");
}
}

let nokia = new Phone();
console.log(nokia.name);
console.log(Phone.name);
```

### 继承

> 对象继承

```js
 //手机
function Phone(brand, price){
    this.brand = brand;
    this.price = price;
}

Phone.prototype.call = function(){
    console.log("我可以打电话");
}

//智能手机
function SmartPhone(brand, price, color, size){
    Phone.call(this, brand, price);
    this.color = color;
    this.size = size;
}

//设置子级构造函数的原型
SmartPhone.prototype = new Phone;
SmartPhone.prototype.constructor = SmartPhone;

//声明子类的方法
SmartPhone.prototype.photo = function(){
    console.log("我可以拍照")
}

SmartPhone.prototype.playGame = function(){
    console.log("我可以玩游戏");
}

const chuizi = new SmartPhone('锤子',2499,'黑色','5.5inch');

console.log(chuizi);
```

> 类继承

```js
class Phone{
    //构造方法
    constructor(brand, price){
        this.brand = brand;
        this.price = price;
    }
    //父类的成员属性
    call(){
        console.log("我可以打电话!!");
    }
}

class SmartPhone extends Phone {
    //构造方法
    constructor(brand, price, color, size){
        super(brand, price);// Phone.call(this, brand, price)
        this.color = color;
        this.size = size;
    }

    photo(){
        console.log("拍照");
    }

    playGame(){
        console.log("玩游戏");
    }
    //重写
    call(){
        console.log('我可以进行视频通话');
    }
}

const xiaomi = new SmartPhone('小米',799,'黑色','4.7inch');
// console.log(xiaomi);
xiaomi.call();
xiaomi.photo();
xiaomi.playGame();
```

### get 和 set

```js
class Phone{
    get price(){
        console.log("价格属性被读取了");
        return 'iloveyou';
    }

    set price(newVal){
        console.log('价格属性被修改了');
    }
}

//实例化对象
let s = new Phone();

// console.log(s.price);
s.price = 'free';
```

## 私有属性

```js
class Person{
    //公有属性
    name;
    //私有属性
    #age;
    #weight;
    //构造方法
    constructor(name, age, weight){
        this.name = name;
        this.#age = age;
        this.#weight = weight;
    }

intro(){
    console.log(this.name);
    console.log(this.#age);
                console.log(this.#weight);
                }
}

//实例化
const girl = new Person('晓红', 18, '45kg');

// console.log(girl.name);
// console.log(girl.#age);
// console.log(girl.#weight);

girl.intro();
```



## 对象方法的扩展

ES6

```js
//1. Object.is 判断两个值是否完全相等 
console.log(Object.is(120, 120));// true 
console.log(Object.is(NaN, NaN));// true
console.log(NaN === NaN);// false 

//2. Object.assign 对象的合并
const config1 = {
    host: 'localhost',
    port: 3306,
    name: 'root',
    pass: 'root',
    test: 'test'
};
const config2 = {
    host: 'http://atguigu.com',
    port: 33060,
    name: 'atguigu.com',
    pass: 'iloveyou',
    test2: 'test2'
}
console.log(Object.assign(config1, config2));

//3. Object.setPrototypeOf 设置原型对象  Object.getPrototypeof
const school = {
    name: '尚硅谷'
}
const cities = {
    xiaoqu: ['北京','上海','深圳']
}
Object.setPrototypeOf(school, cities);
console.log(Object.getPrototypeOf(school));
console.log(school);
```

ES8

```js
//声明对象
const school = {
    name:"尚硅谷",
    cities:['北京','上海','深圳'],
    xueke: ['前端','Java','大数据','运维']
};

//获取对象所有的键
console.log(Object.keys(school));
//获取对象所有的值
console.log(Object.values(school));
//entries
console.log(Object.entries(school));
//创建 Map
const m = new Map(Object.entries(school));
console.log(m.get('cities'));

//对象属性的描述对象
console.log(Object.getOwnPropertyDescriptors(school));

const obj = Object.create(null, {
    name: {
        //设置值
        value: '尚硅谷',
        //属性特性
        writable: true,
        configurable: true,
        enumerable: true
    } 
});
```

ES10

```JS
//二维数组
// const result = Object.fromEntries([
//     ['name','尚硅谷'],
//     ['xueke', 'Java,大数据,前端,云计算']
// ]);

//Map
// const m = new Map();
// m.set('name','ATGUIGU');
// const result = Object.fromEntries(m);

//Object.entries ES8
const arr = Object.entries({
    name: "尚硅谷"
})
console.log(arr);
```

可选链操作符

```js
// ?.
function main(config){
    // const dbHost = config && config.db && config.db.host;
    const dbHost = config?.db?.host;

    console.log(dbHost);
}

main({
    db: {
        host:'192.168.1.100',
        username: 'root'
    },
    cache: {
        host: '192.168.1.200',
        username:'admin'
    }
})
```



# 模块化

模块化是指将一个大的程序文件，拆分成许多小的文件，然后将小文件组合起来。

模块化的好处：

* 防止命名冲突；
* 代码复用；
* 高维护性；

模块化规范产品：

ES6 之前的模块化规范有：

* CommonJS => NodeJS、Browserify；

* AMD => requireJS；

* CMD => seaJS；

ES6 模块化语法：

模块功能主要由两个命令构成：**export 和 import**；

`export` 命令用于规定模块的对外接口（导出模块）；

`import` 命令用于输入其他模块提供的功能（导入模块）；

## 暴露

> 分别暴露

```js
export let school = '尚硅谷';

export function teach() {
    console.log("我们可以教给你开发技能");
}
```

> 统一暴露

```js
let school = '尚硅谷';

function findJob(){
    console.log("我们可以帮助你找工作!!");
}

//
export {school, findJob};
```

> 默认暴露

```js
export default {
    school: 'ATGUIGU',
    change: function(){
        console.log("我们可以改变你!!");
    }
}
```

## 引入

> 通用的导入方式

```js
//引入 m1.js 模块内容
import * as m1 from "./src/js/m1.js";
 //引入 m2.js 模块内容
import * as m2 from "./src/js/m2.js";
// //引入 m3.js 
import * as m3 from "./src/js/m3.js";
```

> 解构赋值形式

```js
import {school, teach} from "./src/js/m1.js";
import {school as guigu, findJob} from "./src/js/m2.js";
import {default as m3} from "./src/js/m3.js";
```

> 简便形式  针对默认暴露

```js
import m3 from "./src/js/m3.js";
console.log(m3);
```

##  入口文件 

> app.js

```js
//模块引入
import * as m1 from "./m1.js";
import * as m2 from "./m2.js";
import * as m3 from "./m3.js";
```

> index,html

```html
<script src="./src/js/app.js" type="module"></script>
```

## 引入NPM包

```js
//修改背景颜色为粉色
import $ from 'jquery';// const $ = require("jquery");
$('body').css('background','pink');
```

## 动态import

```js
// import * as m1 from "./hello.js";
//获取元素
const btn = document.getElementById('btn');

btn.onclick = function(){
    import('./hello.js').then(module => {
        module.hello();
    });
}
```

# 数据结构

## Set

ES6 提供了新的数据结构 Set（集合）。它类似于数组，但成员的值都是唯一的，集合实现了 iterator接口，所以可以使用`扩展运算符`和`for…of…`进行遍历，集合的属性和方法：

* size 返回集合的元素个数；
* add 增加一个新元素，返回当前集合；
* delete 删除元素，返回 boolean 值；
* has 检测集合中是否包含某个元素，返回 boolean 值；
* clear 清空集合，返回 undefined；

```js
//声明一个 set
let s = new Set();
let s2 = new Set(['大事儿','小事儿','好事儿','坏事儿','小事儿']);

//元素个数
// console.log(s2.size);
//添加新的元素
// s2.add('喜事儿');
//删除元素
// s2.delete('坏事儿');
//检测
// console.log(s2.has('糟心事'));
//清空
// s2.clear();
// console.log(s2);

for(let v of s2){
    console.log(v);
}
```

> Set实践

```js
//1. 数组去重
// Set是一个对象，扩展运算符可以拆分数组或对象
// let result = [...new Set(arr)];
// console.log(result);
//2. 交集
let arr2 = [4,5,6,5,6];
// let result = [...new Set(arr)].filter(item => {
//     let s2 = new Set(arr2);// 4 5 6
//     if(s2.has(item)){
//         return true;
//     }else{
//         return false;
//     }
// });
// let result = [...new Set(arr)].filter(item => new Set(arr2).has(item));
// console.log(result);

//3. 并集
// let union = [...new Set([...arr, ...arr2])];
// console.log(union);

//4. 差集
let diff = [...new Set(arr)].filter(item => !(new Set(arr2).has(item)));
console.log(diff);
```

## Map

ES6 提供了 Map 数据结构。它类似于对象，也是键值对的集合。

但是“键”的范围不限于字符串，**各种类型的值（包括对象）都可以当作键**。

Map 也实现了iterator 接口，所以可以使用`扩展运算符`和`for…of…`进行遍历；

**Map 的属性和方法：**

* size 返回 Map 的元素个数；
* set 增加一个新元素，返回当前 Map；
* get 返回键名对象的键值；
* has 检测 Map 中是否包含某个元素，返回 boolean 值；
* clear 清空集合，返回 undefined；

```js
//声明 Map
let m = new Map();

//添加元素
m.set('name','尚硅谷');
m.set('change', function(){
    console.log("我们可以改变你!!");
});
let key = {
    school : 'ATGUIGU'
};
m.set(key, ['北京','上海','深圳']);

//size
// console.log(m.size);

//删除
// m.delete('name');

//获取
// console.log(m.get('change'));
// console.log(m.get(key));

//清空
// m.clear();

//遍历
for(let v of m){
    console.log(v);
}

// console.log(m);
```

# 正则扩展

## 命名捕获分组

ES9 允许命名捕获组使用符号`?`,这样获取捕获结果可读性更强；

```js
//声明一个字符串
// let str = '<a href="http://www.atguigu.com">尚硅谷</a>';

// //提取 url 与 『标签文本』
// const reg = /<a href="(.*)">(.*)<\/a>/;

// //执行
// const result = reg.exec(str);

// console.log(result);
// // console.log(result[1]);
// // console.log(result[2]);


let str = '<a href="http://www.atguigu.com">尚硅谷</a>';
//分组命名
const reg = /<a href="(?<url>.*)">(?<text>.*)<\/a>/;

const result = reg.exec(str);

console.log(result.groups.url);

console.log(result.groups.text);
```

## 反向断言

ES9 支持反向断言，通过对匹配结果前面的内容进行判断，对匹配进行筛选；

```js
//声明字符串
let str = 'JS5211314你知道么555啦啦啦';
//正向断言
const reg = /\d+(?=啦)/;
const result = reg.exec(str);

//反向断言
const reg = /(?<=么)\d+/;
const result = reg.exec(str);
console.log(result);
```

## dotAll 模式

正则表达式中点.匹配除回车外的任何单字符，标记`s`改变这种行为，允许行终止符出现；

```js
//dot  .  元字符  除换行符以外的任意单个字符
let str = `
		<ul>
			<li>
				<a>肖生克的救赎</a>
				<p>上映日期: 1994-09-10</p>
			</li>
			<li>
				<a>阿甘正传</a>
				<p>上映日期: 1994-07-06</p>
			</li>
		</ul>`;
//声明正则
// const reg = /<li>\s+<a>(.*?)<\/a>\s+<p>(.*?)<\/p>/;
const reg = /<li>.*?<a>(.*?)<\/a>.*?<p>(.*?)<\/p>/gs;
//执行匹配
// const result = reg.exec(str);
let result;
let data = [];
while(result = reg.exec(str)){
    data.push({title: result[1], time: result[2]});
}
//输出结果
console.log(data);
```

# BigInt

`BigInt`数据类型的目的是比`Number`数据类型支持的范围更大的整数值。在对大整数执行数学运算时，以任意精度表示整数的能力尤为重要。使用`BigInt`，整数溢出将不再是问题。

```js
//大整形
// let n = 521n;
// console.log(n, typeof(n));

//函数
// let n = 123;
// console.log(BigInt(n));
// console.log(BigInt(1.2));

//大数值运算
let max = Number.MAX_SAFE_INTEGER;
console.log(max);
console.log(max + 1);
console.log(max + 2);

console.log(BigInt(max))
console.log(BigInt(max) + BigInt(1))
console.log(BigInt(max) + BigInt(2))
```

# globalThis

全局属性 `globalThis` 包含全局的 `this` 值，类似于全局对象（global object）。
