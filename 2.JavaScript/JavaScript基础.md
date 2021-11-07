---
title: JavaScript基础
date: 2021-09-11 17:57:47
tags:         
 - JS 
categories: 前端  
---

# JavaScript基础

## 简介

> JavaScript 诞生于 1995 年，它的出现主要是用于处理网页中的前端验证。
>
> 所谓的前端验证，就是指检查用户输入的内容是否符合一定的规则。
>
> 比如：用户名的长度，密码的长度，邮箱的格式等。
>
> JavaScript 是由网景公司发明，起初命名为LiveScript ，后来由于SUN公司的介入更名为了JavaScript 。
>
> 1996 年微软公司在其最新的 IE3 浏览器中引入了自己对JavaScript 的实现 JScript 。
>
> 于是在市面上存在两个版本的JavaScript，一个网景公司的JavaScript 和微软的JScript 。
>
> 为了确保不同的浏览器上运行的 JavaScript 标准一致，所以几个公司共同定制了 JS 的标准命名为ECMAScript 。

**实现**

ECMAScript 是一个标准，而这个标准需要由各个厂商去实现。

不同的浏览器厂商对该标准会有不同的实现。

| 浏览器            | JavaScript实现方式 |
| ----------------- | ------------------ |
| FireFox           | SpiderMonkey       |
| Internet Explorer | JScript/Chakra     |
| Safari            | JavaScriptCore     |
| Chrome            | v8                 |
| Carakan           | Carakan            |

我们已经知道 ECMAScript 是 JavaScript 标准，所以一般情况下这两个词我们认为是一个意思。

但是实际上 JavaScript 的含义却要更大一些。

==一个完整的 JavaScript 实现应该由以下三个部分构成：**ECMAScript 、DOM、BOM**==

**JS 的特点**

* 解释型语言
  * JavaScript 是一门**解释型**语言，所谓解释型值语言**不需要被编译**为机器码在执行，而是直接执行。
  * 由于少了编译这一步骤，所以解释型语言开发起来尤为轻松，但是解释型语言运行较慢也是它的劣势。
  * 不过解释型语言中使用了JIT技术，使得运行速度得以改善。
* 类似于C和Java的语法结构
  * JavaScript 的语法结构与C和Java很像，像for、if 、while 等语句和 Java 的基本上是一模一样的。
  * 不过 JavaScript 和与 Java 的关系也仅仅是看起来像而已。
* 动态语言
  * JavaScript 是一门动态语言，所谓的动态语言可以暂时理解为在语言中的一切内容都是不确定的。比如一个变量，这一时刻
    是个整型，下一时刻可能会变成字符串了。
  * 不过在补充一句动态语言相比静态语言性能上要差一些，不过由于 JavaScript 中应用的 JIT 技术，所以 JS 可能是运行速度最快的动态语言了。
* 基于原型的面向对象
  * JavaScript 是一门面向对象的语言。
  * Java 也是一门面向对象的语言，但是与 Java 不同 JavaScript 是基于原型的面向对象。

## 基础语法

### 编写位置

1.可以编写到标签的指定属性中  

```html  
<button onclick="alert('hello');">我是按钮</button>  
<a href="javascript:alert('aaa');">超链接</a>  
```

2.可以编写到script标签中  

```html  
<script type="text/javascript">  
//编写js代码  
</script>  
```

3.可以将代码编写到外部的js文件中，然后通过标签将其引入  

script标签一旦用于引入外部文件了，就不能在编写代码了，即使编写了浏览器也会忽略  ,如果需要则可以在创建一个新的script标签用于编写内部代码  

```html  
<script type="text/javascript" src="文件路径"></script>  
```

### 输出语句  

在浏览器窗口中弹出一个警告框

```javascript  
alert("要输出的内容");  
```

内容将会被写到body标签中，并在页面中显示

```javascript  
document.write("要输出的内容");  
```

内容会被写到开发者工具的控制台中

```javascript  
console.log("要输出的内容");  
```

### 书写

js函数声明不需要`;`，但是赋值语句要加`;`，结尾如果不写分号，浏览器会自动添加，但是会消耗一些系统资源，  而且有些时候，浏览器会加错分号，所以在开发中分号必须写  

```javascript  
function functionName(arg0,arg1,arg2){  
//函数声明  
}  
var functionName=function(arg0,arg1,arg2){  
//函数表达式  
};(注意分号)  
```

JS严格区分大小写。	  

JS中会自动忽略多个空格和换行，所以我们可以利用空格和换行对代码进行格式化。  

### 注释  

单行注释  

```javascript  
//注释内容  
```

多行注释  

```javascript  
/*  
注释内容  
*/  
```

### 字面量和变量  

#### 字面量  

字面量实际上就是一些固定的值，比如 1 2 3 4 true false null NaN "hello"  

**字面量都是不可以改变的。**  

由于字面量不是很方便使用，所以在JS中很少直接使用字面量  

#### 变量  

变量可以用来保存字面量，并且可以保存任意的字面量  

一般都是通过变量来使用字面量，而不直接使用字面量，而且也可以通过变量来对字面量进行一个描述  

> 声明变量  
>

使用var关键字来声明一个变量  

```javascript
var a;  
```

> 为变量赋值 

```javascript
a = 1; 
```

> 声明和赋值同时进行 

```javascript
var a = 456;   
```

### 标识符 

在JS中所有的可以自主命名的内容，都可以认为是一个标识符， 是标识符就应该遵守标识符的规范。  

比如：变量名、函数名、属性名  

规范：  

1.标识符中可以含有`字母`、`数字`、`_`、`$` 
2.标识符不能以数字开头 
3.标识符不能是JS中的关键字和保留字 
4.标识符一般采用驼峰命名法  `xxxYyyZzz`  

### 数据类型  

#### 六种数据类型  

>  **JS中一共分成六种数据类型 5个基本数据类型+object** 
>
> String 字符串 Number 数值  Boolean 布尔值  Null 空值  Undefined 未定义  Object 对象  
>
> 其中基本数据类型有	5个  
>
> **typeof运算符检查数据类型** 

##### 1.String 字符串  

JS中的字符串需要使用引号引起来（双引号或单引号都行） 。

在字符串中使用`\`作为转义字符  

```bash
\'  ==> '  
\"  ==> "  
\n  ==> 换行  
\t  ==> 制表符  
\\  ==> \	  
```

 使用typeof运算符检查字符串时，会返回"string"	  

##### 2.Number 数值  

 **JS中所有的整数和浮点数都是Number类型**  

最大能表示的值：Number.MAX_VALUE=	1.7976931348623157e+308  

特殊的数字：能赋值给变量  

* Infinity 正无穷 a = Infinity ,能赋值  
* -Infinity 负无穷  
* NaN 非法数字（Not A Number） 

其他进制的数字的表示： 

* 0b 开头表示二进制，但是不是所有的浏览器都支持 
* 0 开头表示八进制 
* 0x 开头表示十六进制  

使用typeof检查一个Number类型的数据时，会返回"number"  （包括NaN 和 Infinity）  

##### 3.Boolean 布尔值  

布尔值主要用来进行逻辑判断，布尔值只有两个  

* true 逻辑的真  
* false 逻辑的假 

使用typeof检查一个布尔值时，会返回"boolean"	  

##### 4.Null 空值  

空值专门用来表示为空的对象，Null类型的值只有一个  null 

使用typeof检查一个Null类型的值时会返回"object"  

#####  5.Undefined 未定义  

**如果声明一个变量但是没有为变量赋值此时变量的值就是undefined**  

该类型的值只有一个 undefined  

使用typeof检查一个Undefined类型的值时，会返回"undefined"  

##### 6.引用数据类型	  

Object 对象  

#### 类型转换  

 类型转换就是指将其他的数据类型，转换为String Number 或 Boolean  

##### 转换为String  

> 方式一（强制类型转换）**调用被转换数据的toString()方法**    

```js
var a = 123;  
a = a.toString(); 
```

注意：**这个方法不适用于null和undefined**  

由于这两个类型的数据中没有方法，所以调用toString()时会报错  

> 方式二（强制类型转换）  **调用String()函数**   

```javascript
var a = 123;  
a = String(a);  
```

 原理：对于Number Boolean String都会调用他们的toString()方法来将其转换为字符串，对于null值，直接转换为字符串"null"。对于undefined直接转换为字符串"undefined"  

> 方式三（隐式的类型转换）**为任意的数据类型 +""** 

```javascript
var a = true;  
a = a + ""; 
```

原理：和String()函数一样	  

##### 转换为Number  

> 方式一（强制类型转换）   **调用Number()函数** 

```javascript
var s = "123";  
s = Number(s); 
```

 转换的情况：  

1. 字符串 > 数字 

   * 如果字符串是一个合法的数字，则直接转换为对应的数字  
   * 如果字符串是一个非法的数字，则转换为NaN  
   * 如果是一个空串或纯空格的字符串，则转换为0  

2. 布尔值 > 数字  

   * true转换为1   
   * false转换为0  

3. 空值 > 数字   

   null转换为0  

4. 未定义 > 数字    

   undefined 转换为NaN  

> 方式二（强制类型转换）  **调用parseInt()或parseFloat()** 


这两个函数专门用来将一个字符串转换为数字的  

如果对非String使用parseInt()或parseFloat()，它会**先将其转换为String**然后再操作 

parseInt() 可以将**一个字符串中的有效的整数位**提取出来，并转换为Number。如果需要可以在parseInt()中指定一个第二个参数，来指定进制    

 ```javascript  
var a = "123.456px";  
a = parseInt(a); //123  
 ```

parseFloat()可以将一个**字符串中的有效的小数位**提取出来，并转换为Number 。

```javascript  
var a = "123.456px";  
a = parseFloat(a); //123.456  
```

> 方式三（隐式的类型转换）   **使用一元的+来进行隐式的类型转换**

```javascript  
var a = "123";  
a = +a;  
```

 **原理：和Number()函数一样**  

##### 转换为布尔值  

> 方式一（强制类型转换）   **使用Boolean()函数**  

```javascript
var s = "false";  
s = Boolean(s); //true 
```

转换的情况  

* 字符串 > 布尔  

  除了空串其余全是true  

* 数值 > 布尔  

  除了0和NaN其余的全是true  

* null、undefined > 布尔  

  都是false  

* 对象 > 布尔  

  都是true  

> 方式二（隐式类型转换）  **为任意的数据类型做两次非运算，即可将其转换为布尔值** 

```javascript  
var a = "hello";  
a = !!a; //true  
```

### 运算符  

运算符也称为操作符  

通过运算符可以对一个或多个值进行运算或操作  

#### typeof运算符  

用来检查一个变量的数据类型  

语法：`typeof 变量` 

它会返回一个用于描述类型的字符串作为结果  

#### 算数运算符  

+&ensp;对两个值进行加法运算并返回结果   

-&ensp;对两个值进行减法运算并返回结果    

*&ensp;对两个值进行乘法运算并返回结果    

/&ensp;对两个值进行除法运算并返回结果    

%&ensp;对两个值进行取余运算并返回结果  

**除了加法以外，对非Number类型的值进行运算时，都会先转换为Number然后在做运算。**  

而做加法运算时，如果是两个字符串进行相加，则会做拼串操作，将两个字符连接为一个字符串。  

任何值和字符串做加法，都会先转换为字符串，然后再拼串  

#### 一元运算符  

 一元运算符只需要一个操作数  

 ##### 一元的+  

 就是正号，不会对值产生任何影响，但是可以将一个非数字转换为数字   

```javascript  
var a = true;  
a = +a;  
```

##### 一元的-  

 就是负号，可以对一个数字进行符号位取反    

```javascript  
var a = 10;  
a = -a;  
```

##### 自增  

> 自增可以使变量在原值的基础上自增1  

自增使用 `++`  

自增可以使用 `前++（++a）后++(a++)`  

* 无论是++a 还是 a++都会立即使原变量自增1  
* 不同的是++a和a++的值是不同的
  * ++a的值是变量的新值（自增后的值）  
  * a++的值是变量的原值（自增前的值）  

##### 自减  

> 自减可以使变量在原值的基础上自减1  

自减使用`--`  

自减可以使用 `--前（--a）后--(a--)`  

* 无论是--a 还是a--都会立即使原变量自减1 
* 不同的是a和a的值是不同的
  * --a的值是变量的新值（自减后的值） 
  * a--的值是变量的原值（自减前的值）  

#### 逻辑运算符  

`!`  

非运算可以对一个布尔值进行取反，true变false false边true 

当对非布尔值使用!时，会先将其转换为布尔值然后再取反，我们可以利用`!!`来将其他的数据类型转换为布尔值  

`&&` 	 

&&可以对符号两侧的值进行与运算。  

只有两端的值都为true时，才会返回true。只要有一个false就会返回false。  

与是一个短路的与，如果第一个值是false，则不再检查第二个值。

对于非布尔值，它会将其转换为布尔值然后做运算，并返回原值。

`||`    

||可以对符号两侧的值进行或运算。  

只有两端都是false时，才会返回false。只要有一个true，就会返回true。  

或是一个短路的或，如果第一个值是true，则不再检查第二个值。  

对于非布尔值，它会将其转换为布尔值然后做运算，并返回原值。

#### 赋值运算符  

`=`  

可以将符号右侧的值赋值给左侧变量    
`+=`      

```javascript
a += 5 相当于 a = a+5    
var str = "hello";  str += "world";  
```

`-=`    

```javascript
a -= 5  相当于 a = a-5  
```

`*=`    

```javascript  
a *= 5 相当于 a = a*5  
```

`/=`    

```javascript  
a /= 5 相当于 a = a/5	  
```

`%=`  

```javascript  
a %= 5 相当于 a = a%5 
```

#### 关系运算符  

`>  	>=  	<  	<=`  

关系运算符的规则和数学中一致，用来比较两个值之间的关系，如果关系成立则返回true，关系不成立则返回false。 

如果比较的两个值是非数值，会将其转换为Number然后再比较。  

如果比较的两个值都是字符串，此时会比较字符串的Unicode编码，而不会转换为Number。  

#### 相等运算符  

`==`

判断左右两个值是否相等，如果相等返回true，如果不等返回false  

相等会自动对两个值进行类型转换，如果**对不同的类型进行比较，会将其转换为相同的类型然后再比较**。

`!=` 

不等，判断左右两个值是否不等，如果不等则返回true，如果相等则返回false  

不等也会做自动的类型转换。 
`===` 

**全等**，判断左右两个值是否全等，它和相等类似，只不过它不会进行自动的类型转换，如果两个值的类型不同，则直接返回false 。
`!==` 

**不全等**，和不等类似，但是它不会进行自动的类型转换，如果两个值的类型不同，它会直接返回true 

`特殊的值：null和undefined` 

由于undefined衍生自null，所以**null == undefined** 会返回true。但是 null === undefined 会返回false。 

NaN不与任何值相等，包括它自身 `NaN == NaN //false`  

判断一个值是否是NaN，使用`isNaN()`函数  

#### 三元运算符  

语法：`条件表达式?语句1:语句2;` 

执行流程：  

先对条件表达式求值判断，如果判断结果为true，则执行语句1，并返回执行结果。  

如果判断结果为false，则执行语句2，并返回执行结果。 

#### 优先级  

和数学中一样，JS中的运算符也是具有优先级的，比如 先乘除 后加减 先与 后或 

具体的优先级可以参考优先级的表格，在表格中越靠上的优先级越高， 

优先级越高的越优先计算，优先级相同的，从左往右计算。 

优先级不需要记忆，如果越到拿不准的，使用()来改变优先级。  

### 流程控制语句  

程序都是自上向下的顺序执行的，  通过流程控制语句可以改变程序执行的顺序，或者反复的执行某一段的程序。  

#### 条件判断语句  

条件判断语句也称为if语句 

语法一：  

 ```javascript
if(条件表达式){  
	语句...   
}  
 ```

 语法二：  

```javascript
if(条件表达式){  
	语句...  
}else{  
	语句...  
} 
```

 语法三：  

```javascript  
if(条件表达式){  
	语句...  
}else if(条件表达式){  
	语句...  
}else if(条件表达式){  
	语句...  
}else if(条件表达式){  
	语句...  
}else{  
	语句...  
}	  
```

#### 条件分支语句  

switch语句  

语法:  

```javascript  
switch(条件表达式){  
	case 表达式:  
		语句...  
		break;  
	case 表达式:  
		语句...  
		break;  
	case 表达式:  
		语句...  
		break;  
	default:  
		语句...  
		break;  
}   
```

#### 循环语句  

通过循环语句可以反复执行某些语句多次  

##### while循环 

语法：  

```javascript  
while(条件表达式){  
    语句...  
}  
```

##### do...while循环 

语法:  


```javascript  
do{  
语句...  
}while(条件表达式)  
```

和while的区别：  

* while：先判断后执行  
* do...while: 先执行后判断  
* do...while可以确保循环体至少执行一次。  

##### for循环 

语法：  

```javascript
for(①初始化表达式 ; ②条件表达式 ; ④更新表达式){  
    ③语句...  
}  
```

死循环  

```javascript
while(true){  

}  

for(;;){  

}
```

## 对象

对象是JS中的引用数据类型。  

**对象是一种复合数据类型，在对象中可以保存多个不同数据类型的属性**。 

使用typeof检查一个对象时，会返回object。  

### 对象的分类

**1.内建对象** 

由ES标准中定义的对象，在任何的ES的实现中都可以使用  

比如：Math String Number Boolean Function Object....  

**2.宿主对象**  

由JS的运行环境提供的对象，目前来讲主要指由浏览器提供的对象  

比如 BOM DOM  

**3.自定义对象**  

由开发人员自己创建的对象  

### 创建对象 

 方式一：

```javascript
var obj = new Object();  
```

 方式二： 

 ```javascript
var obj = {}; 
 ```

### 向对象中添加属性  

语法：  

```js
对象.属性名 = 属性值;  

对象["属性名"] = 属性值;	//这种方式能够使用特殊的属性名
```

**对象的属性名没有任何要求，不需要遵守标识符的规范，但是在开发中，尽量按照标识符的要求去写。**  

属性值也可以任意的数据类型。  

### 读取对象中的属性  

语法：  

```js
对象.属性名  
对象["属性名"] //"属性名"可以使字符串常量，也可以是字符串变量 
```

如果读取一个对象中没有的属性，它不会报错，而是返回一个`undefined`  

### 删除对象中的属性  

 语法：  

```javascript
delete 对象.属性名  
delete 对象["属性名"]  
```


### 遍历  

**使用in检查对象中是否含有指定属性**  

语法：

`"属性名" in 对象`  

如果在对象中含有该属性，则返回true，如果没有则返回false  

```javascript  
var obj = {'0':'a','1':'b','2':'c'};  
  
for(var i in obj) {  
     console.log(i,":",obj[i]);  
}  
```

### 对象字面量

**使用对象字面量，在创建对象时直接向对象中添加属性**  

语法： 

```javascript
var obj = {  
    属性名:属性值,  
    属性名:属性值,  
    属性名:属性值,  
    属性名:属性值  
} 
```

### 基本数据类型和引用数据类型  

 基本数据类型 ：String Number Boolean Null Undefined  

 引用数据类型  ：Object 

 **基本数据类型的数据，变量是直接保存的它的值。**  

变量与变量之间是互相独立的，修改一个变量不会影响其他的变量。  

 **引用数据类型的数据，变量是保存的对象的引用（内存地址）。**  

如果多个变量指向的是同一个对象，此时修改一个变量的属性，会影响其他的变量。  

比较两个变量时，对于基本数据类型，比较的就是值，对于引用数据类型比较的是地址，地址相同才相同。 	  

### 函数（Function）	  

**函数也是一个对象，也具有普通对象的功能（能有属性）。**

函数中可以封装一些代码，在需要的时候可以去调用函数来执行这些代码  

使用typeof检查一个函数时会返回function  

#### 创建函数  

 函数声明 

```javascript
function 函数名([形参1,形参2...形参N]){  
语句...  
}  
```

 函数表达式

```javascript
var 函数名 = function([形参1,形参2...形参N]){  
语句...  
};  
```

#### 调用函数  

语法：

`函数对象([实参1,实参2...实参N]);`  

当我们调用函数时，函数中封装的代码会按照编写的顺序执行  

#### 立即执行函数 

函数定义完，立即被调用，这种函数叫做立即执行函数  

立即执行函数往往只会执行一次

```javascript
(function(a,b){  
    console.log("a = "+a);  
    console.log("b = "+b);  
})(123,456);  
```

#### 形参和实参  

**形参：形式参数**  

定义函数时，可以在()中定义一个或多个形参，形参之间使用,隔开  

定义形参就相当于在函数内声明了对应的变量但是并不赋值，形参会在调用时才赋值。  

**实参：实际参数**  

调用函数时，可以在()传递实参，传递的实参会赋值给对应的形参,  调用函数时JS解析器不会检查实参的类型和个数，可以传递任意数据类型的值。  

如果实参的数量大于形参，多余实参将不会赋值，  

如果实参的数量小于形参，则没有对应实参的形参将会赋值undefined  

#### 返回值

> 就是函数执行的结果。  

使用return 来设置函数的返回值。  

语法：

`return 值;`  

该值就会成为函数的返回值，可以通过一个变量来接收返回值。 

return后边的代码都不会执行，一旦执行到return语句时，函数将会立刻退出。  

return后可以跟任意类型的值，可以是基本数据类型，也可以是一个对象。  

如果return后不跟值，或者是不写return则函数默认返回undefined。  

#### break、continue和return  

break  退出循环  

continue  跳过当次循环  

return  退出函数 

#### 枚举对象中的属性

使用for ... in 语句

语法：

```js
for(var 变量 in 对象){

}
```

for...in语句 对象中有几个属性，循环体就会执行几次

每次执行时，会将对象中的一个属性的名字赋值给变量

#### 作用域  

> 作用域简单来说就是一个变量的作用范围。  

在JS中作用域分成两种：  

1.全局作用域  

直接在`script`标签中编写的代码都运行在全局作用域中。 

全局作用域在打开页面时创建，在页面关闭时销毁。  

全局作用域中有一个全局对象`window`，window对象由浏览器提供，可以在页面中直接使用，它代表的是整个的浏览器的窗口。  

在全局作用域中创建的变量都会作为window对象的属性保存  

在全局作用域中创建的函数都会作为window对象的方法保存  

在全局作用域中创建的变量和函数可以在页面的任意位置访问。  

在函数作用域中也可以访问到全局作用域的变量。  

尽量不要在全局中创建变量	  

2.函数作用域  

函数作用域是函数执行时创建的作用域，每次调用函数都会创建一个新的函数作用域。  

函数作用域在函数执行时创建，在函数执行结束时销毁。  

在函数作用域中创建的变量，不能在全局中访问。  

当在函数作用域中使用一个变量时，它会先在自身作用域中寻找，如果找到了则直接使用，如果没有找到则到上一级作用域中寻找，  

如果找到了则使用，找不到则继续向上找，直到找到全局作用域，如果全局作用域中依然没有找到，则会报错`ReferenceError` 。

#### 变量的声明提前  

在全局作用域中，使用var关键字声明的变量会在所有的代码执行之前被声明，但是不会赋值。  

所以我们可以在变量声明前使用变量。但是不使用var关键字声明的变量不会被声明提前。  

在函数作用域中，也具有该特性，使用var关键字声明的变量会在函数所有的代码执行前被声明，如果没有使用var关键字声明变量，则变量会变成全局变量 。

#### 函数的声明提前  

在全局作用域中，使用函数声明创建的函数`function fun(){}`,会在所有的代码执行之前被创建，也就是我们可以在函数声明前去调用函数，但是使用函数表达式`var fun = function(){}`创建的函数没有该特性。

在函数作用域中，使用函数声明创建的函数，会在所有的函数中的代码执行之前就被创建好了。  

#### 函数对象的方法

**方法（method）** 

可以将一个函数设置为一个对象的属性，当一个对象的属性是一个函数时， 我们称这个函数是该对象的方法。 

```js
对象.方法名(); //调方法
函数名()； //调函数
```

call()和apply()

这两个方法都是函数对象的方法，需要通过函数对象来调用

当对函数调用call()和apply()都会调用函数执行

在调用call()和apply()可以将一个对象指定为第一个参数

此时这个对象将会成为函数执行时的this 

call()方法可以将实参在对象之后依次传递

apply()方法需要将实参封装到一个数组中统一传递

#### this、arguments

在调用函数时，浏览器每次都会传递进两个隐含的参数

> 函数的上下文对象 this

使用this来引用上下文对象，根据函数的调用形式不同，this的值也不同。  

this的不同的情况：  

1.以函数的形式调用时，this是window  

2.以方法的形式调用时，this就是调用方法的对象  

3.以构造函数的形式调用时，this就是新创建的对象  

4.使用call和apply调用时，this是指定的那个对象

> 封装实参的对象 arguments

arguments是一个类数组对象,它也可以通过索引来操作数据，也可以获取长度

在调用函数时，我们所传递的实参都会在arguments中保存

arguments.length可以用来获取实参的长度

我们即使不定义形参，也可以通过arguments来使用实参，只不过比较麻烦。

arguments[0] 表示第一个实参

arguments[1] 表示第二个实参 。。。

它里边有一个属性叫做callee，这个属性对应一个函数对象，就是当前正在指向的函数的对象

#### 构造函数  

构造函数是专门用来创建对象的函数  

一个构造函数我们也可以称为一个类  

通过一个构造函数创建的对象，我们称该对象时这个构造函数的实例  

通过同一个构造函数创建的对象，我们称为一类对象  

构造函数就是一个普通的函数，只是他的调用方式不同，如果直接调用，它就是一个普通函数；如果使用new来调用，则它就是一个构造函数。

例子：  

```javascript  
function Person(name , age , gender){  
    this.name = name;  
    this.age = age;  
    this.gender = gender;  
    this.sayName = function(){  
        alert(this.name);  
    };  
}   
```

构造函数的执行流程：  

1.创建一个新的对象  

2.将新的对象作为函数的上下文对象（this）  

3.执行函数中的代码  

4.将新建的对象返回  

**instanceof 用来检查一个对象是否是一个类的实例**  

语法：`对象 instanceof 构造函数`  

如果该对象时构造函数的实例，则返回true，否则返回false  

**Object是所有对象的祖先，所以任何对象和Object做instanceof都会返回true**  

#### 原型（prototype）  

创建一个函数以后，**解析器都会默认在函数中添加一个数prototype**  

prototype属性指向的是一个对象，这个对象我们称为原型对象。  

当函数作为构造函数使用，**它所创建的对象中都会有一个隐含的属性执行该原型对象。**  

这个隐含的属性可以通过对象`__proto__`来访问。  

**原型对象就相当于一个公共的区域，凡是通过同一个构造函数创建的对象他们通常都可以访问到相同的原型对象。**  

我们可以将对象中共有的属性和方法统一添加到原型对象中，这样我们只需要添加一次，就可以使所有的对象都可以使用。  

当我们去访问对象的一个属性或调用对象的一个方法时，它会先自身中寻找，如果在自身中找到了，则直接使用。如果没有找到，则去原型对象中寻找，如果找到了则使用， 如果没有找到，则去原型的原型中寻找，依此类推。直到找到Object的原型为止，Object对象的原型没有原型，如果在Object原型中依然没有找到，则返回null。

使用in检查对象中是否含有某个属性时，如果对象中没有但是原型中有，也会返回true

**hasOwnProperty()**  

这个方法可以用来检查**对象自身中**是否含有某个属性  

语法：`对象.hasOwnProperty("属性名")`  

### toString方法  

当我们直接在页面中打印一个对象时，事件上是输出的对象的toString()方法的返回值  

如果我们希望在输出对象时不输出[object Object]，可以为对象添加一个toString()方法	  

```javascript  
//修改Person原型的toString  
Person.prototype.toString = function(){  
	return "Person[name="+this.name+",age="+this.age+",gender="+this.gender+"]";  
};  
```

### 垃圾回收（GC）  

就像人生活的时间长了会产生垃圾一样，程序运行过程中也会产生垃圾。

这些垃圾积攒过多以后，会导致程序运行的速度过慢，  所以我们需要一个垃圾回收的机制，来处理程序运行过程中产生垃圾。

当一个对象没有任何的变量或属性对它进行引用，此时我们将永远无法操作该对象，  此时这种对象就是一个垃圾，这种对象过多会占用大量的内存空间，导致程序运行变慢，所以这种垃圾必须进行清理。  

在JS中拥有自动的垃圾回收机制，会自动将这些垃圾对象从内存中销毁，我们不需要也不能进行垃圾回收的操作，我们需要做的只是要**将不再使用的对象设置null**即可。 

## 数组（Array）  

数组也是一个**对象**，是一个用来存储数据的对象，但是它的存储效率比普通对象要高。

数组中保存的内容我们称为**元素**,数组使用**索引（index）**来操作元素，索引指由0开始的整数。 

### 数组的操作 

**创建数组**  

```javascript  
var arr = new Array();  
var arr = [];  
```

**向数组中添加元素**  

```javascript  
// 数组对象[索引] = 值;  
arr[0] = 123;  
arr[1] = "hello";  
```

**创建数组时直接添加元素**   

```javascript
 var arr = [元素1,元素2....元素N]; 
 var arr = [123,"hello",true,null];  
```

**获取和修改数组的长度**  

`数组.length` 

* length获取到的是数组的最大索引+1  
* 对于连续的数组，length获取到的就是数组中元素的个数

`数组.length = 新长度` 

* 如果修改后的length大于原长度，则多出的部分会空出来  
* 如果修改后的length小于原长度，则原数组中多出的元素会被删除  

**向数组的最后添加元素** 

`数组[数组.length] = 值;` 		  

### 数组的方法  

#### push()

该方法可以向数组的`末尾`添加一个或多个元素，并返回数组的`新的长度`。

#### pop()

该方法可以删除数组的`最后`一个元素,并将`被删除的元素`作为返回值返回。

#### unshift()

向数组`开头`添加一个或多个元素，并返回`新的数组长度`。

向前边插入元素以后，其他的元素索引会依次调整。

#### shift()

可以删除数组的`第一个`元素，并将`被删除的元素`作为返回值返回。

#### slice()

可以用来从数组提取指定元素

该方法`不会改变元素数组`，而是将截取到的元素封装到一个新数组中返回

参数：

* 截取开始的位置的索引，`包含开始索引`
* 截取结束的位置的索引，`不包含结束索引`
  *  第二个参数可以省略不写,此时会截取从开始索引往后的所有元素

* 参数可以传递一个负值，如果传递一个负值，则从后往前计算

#### splice()

可以用于删除数组中的指定元素

使用splice()会影响到原数组，`会将指定元素从原数组中删除`，并将`被删除的元素`作为返回值返回。

参数：

* 第一个，表示开始位置的索引
* 第二个，表示删除的数量
* 第三个及以后，可以传递一些新的元素，这些元素将会自动插入到开始位置索引前边     

#### concat()

可以连接两个或多个数组，并将新的数组返回。该方法`不会对原数组产生影响`。

#### join()

该方法可以将数组转换为一个字符串。

该方法`不会对原数组产生影响`，而是将转换后的字符串作为结果返回。

在join()中可以指定一个字符串作为参数，这个字符串将会成为数组中元素的连接符。

如果不指定连接符，则默认使用`,`作为连接符

#### reverse()

该方法用来反转数组（前边的去后边，后边的去前边）。该方法会直接`修改原数组` 。

#### sort()

可以用来对数组中的元素进行排序。

也会`影响原数组`，默认会按照`Unicode`编码进行排序。

即使对于纯数字的数组，使用sort()排序时，也会按照Unicode编码来排序，所以对数字进排序时，可能会得到错误的结果。

我们可以自己来指定排序的规则：

在sort()添加一个回调函数，来指定排序规则，回调函数中需要定义两个形参。

浏览器将会分别使用数组中的元素作为实参去调用回调函数。

使用哪个元素调用不确定，但是肯定的是在数组中a一定在b前边。

浏览器会根据回调函数的返回值来决定元素的顺序。

* 如果返回一个大于0的值，则元素会交换位置
* 如果返回一个小于0的值，则元素位置不变
* 如果返回一个0，则认为两个元素相等，也不交换位置

如果需要升序排列，则返回`a-b`

如果需要降序排列，则返回`b-a`

```js

arr.sort(function(a,b){
	
	//前边的大
	/*if(a > b){
		return -1;
	}else if(a < b){
		return 1;
	}else{
		return 0;
	}*/
	
	//升序排列
	//return a - b;
	
	//降序排列
	return b - a;
	
});
```

### 遍历数组  

遍历数组就是将数组中元素都获取到。

**用for循环来遍历数组**

```javascript
for(var i=0 ; i<数组.length ; i++){  
    //数组[i]  
}  
```

**用forEach()方法来遍历数组（不兼容IE8）**  

```javascript
数组.forEach(function(value , index , obj){  
  
});  
```

forEach()方法需要一个回调函数作为参数，数组中有几个元素，回调函数就会被调用几次，每次调用时，都会将遍历到的信息以实参的形式传递进来，我们可以定义形参来获取这些信息。  

`value:正在遍历的元素`  

`index:正在遍历元素的索引`  

`obj:被遍历对象`    

## 常用类和方法 

### 包装类  

在JS中为我们提供了**三个包装类：**  

String() Boolean() Number()  

通过这三个包装类可以创建基本数据类型的对象  

例子：

```javascript
var num = new Number(2);  
var str = new String("hello");  
var bool = new Boolean(true); 
```

==但是在实际应用中千万不要这么干。==  

当我们去操作一个基本数据类型的属性和方法时，  **解析器会临时将其转换为对应的包装类，然后再去操作属性和方法，**  操作完成以后再将这个临时对象进行销毁。  

### Date  

日期的对象，在JS中通过Date对象来表示一个时间  

**创建对象**  

创建一个当前的时间对象  

```javascript
var d = new Date();  
```

 创建一个指定的时间对象  

```javascript
var d = new Date("月/日/年 时:分:秒");  
```

| 方法              | 解释                                                         |
| ----------------- | ------------------------------------------------------------ |
| getDate()         | 当前日期对象是几日（1-31）                                   |
| getDay()          | 返回当前日期对象时周几（0-6）0 周日	1 周一 。。。         |
| getMonth()        | 返回当前日期对象的月份（0-11）	 0 一月 1 二月 。。。      |
| getFullYear()     | 从 Date 对象以四位数字返回年份。                             |
| getHours()        | 返回 Date 对象的小时 (0 ~ 23)。                              |
| getMinutes()      | 返回 Date 对象的分钟 (0 ~ 59)。                              |
| getSeconds()      | 返回 Date 对象的秒数 (0 ~ 59)。                              |
| getMilliseconds() | 返回 Date 对象的毫秒(0 ~ 999)。                              |
| getTime()         | 返回当前日期对象的时间戳。(时间戳，指的是从1970年月1日 0时0分0秒，到现在时间的毫秒数）计算机底层保存时间都是以时间戳的形式保存的。 |
| Date.now()        | 可以获取当前代码执行时的时间戳                               |

### Math			  

Math属于一个工具类，它不需要我们创建对象，它里边封装了属性运算相关的常量和方法。 

我们可以直接使用它来进行数学运算相关的操作。

| 方法                               | 解释                    |
| ---------------------------------- | ----------------------- |
| Math.PI                            | 常量，圆周率            |
| Math.abs()                         | 绝对值运算              |
| Math.ceil()                        | 向上取整                |
| Math.floor()                       | 向下取整                |
| Math.round()                       | 四舍五入取整            |
| Math.random()                      | 生成一个01之间的随机数  |
| Math.round(Math.random()*(y-x)+x); | 生成一个xy之间的随机数  |
| Math.pow(x,y)                      | 求x的y次幂              |
| Math.sqrt()                        | 对一个数进行开方        |
| Math.max()   Math.min()            | 求多个数中最大值 最小值 |

**补充：**

`~~`它代表双非按位取反运算符，如果你想使用比`Math.floor()`更快的方法，那就是它了。

需要注意，对于正数，它**向下取整**；对于负数，**向上取整**；非数字取值为`0`

### 字符串的相关的方法  

> 在底层字符串是以字符数组的形式保存的

`length`

可以用来获取字符串的长度  

`charAt()`

可以返回字符串中指定位置的字符

根据索引获取指定的字符

`charCodeAt()`

获取指定位置字符的字符编码（Unicode编码）

`String.formCharCode()`

可以根据字符编码去获取字符

`concat()`

可以用来连接两个或多个字符串

作用和+一样

`indexOf()`

该方法可以检索一个字符串中是否含有指定内容

如果字符串中含有该内容，则会返回其第一次出现的索引

如果没有找到指定的内容，则返回-1

可以指定一个第二个参数，指定开始查找的位置

`lastIndexOf()`

该方法的用法和indexOf()一样，

不同的是indexOf是从前往后找，

而lastIndexOf是从后往前找

也可以指定开始查找的位置

`slice()`

可以从字符串中截取指定的内容

不会影响原字符串，而是将截取到内容返回

参数：

* 第一个，开始位置的索引（包括开始位置）
* 第二个，结束位置的索引（不包括结束位置）
* 如果省略第二个参数，则会截取到后边所有的
* 也可以传递一个负数作为参数，负数的话将会从后边计算

`substring()`

可以用来截取一个字符串，可以slice()类似

参数：

* 第一个：开始截取位置的索引（包括开始位置）
* 第二个：结束位置的索引（不包括结束位置）
* 不同的是这个方法不能接受负值作为参数，如果传递了一个负值，则默认使用0
* 而且他还自动调整参数的位置，如果第二个参数小于第一个，则自动交换

`substr()`

用来截取字符串

 参数：

* 截取开始位置的索引
* 截取的长度

`split()`

可以将一个字符串拆分为一个数组

参数：

* 需要一个字符串作为参数，将会根据该字符串去拆分数组
* 如果传递一个空串作为参数，则会将每个字符都拆分为数组中的一个元素

`toUpperCase()`

将一个字符串转换为大写并返回

`toLowerCase()`

将一个字符串转换为小写并返回

## 正则表达式  

正则用来定义一些字符串的规则，程序可以根据这些规则来判断一个字符串是否符合规则，也可以将一个字符串中符合规则的内容提取出来。

### 创建正则表达式的对象

```js
var reg = new RegExp("正则","匹配模式");
var reg = new RegExp("a"); //这个正则表达式可以来检查一个字符串中是否含有a
```

使用typeof检查正则对象，会返回object

在构造函数中可以传递一个匹配模式作为第二个参数，

可以是 

* `i` 忽略大小写 
* `g` 全局匹配模式

### 正则表达式的方法

`test()`

使用这个方法可以用来检查一个字符串是否符合正则表达式的规则，如果符合则返回true，否则返回false

### 使用字面量来创建正则表达式

```js
var 变量 = /正则表达式/匹配模式
```

使用字面量的方式创建更加简单，使用构造函数创建更加灵活

使用 `|` 表示或者的意思

`[]`里的内容也是或的关系

* [ab] == a|b
* [a-z] 任意小写字母
* [A-Z] 任意大写字母
* [A-z] 任意字母
* [0-9] 任意数字
* [^ ] 除了

```js
//创建一个正则表达式，检查一个字符串中是否有a或b
reg = /a|b|c/;
//创建一个正则表达式检查一个字符串中是否有字母
reg = /[A-z]/;

```

### 字符串和正则相关的方法

`split()`

可以将一个字符串拆分为一个数组

方法中可以传递一个正则表达式作为参数，这样方法将会根据正则表达式去拆分字符串

这个方法即使不指定全局匹配，也会全都插分

```js
//根据任意字母来将字符串拆分
var result = str.split(/[A-z]/);
```

`search()`

可以搜索字符串中是否含有指定内容

如果搜索到指定内容，则会返回第一次出现的索引，如果没有搜索到返回-1

它可以接受一个正则表达式作为参数，然后会根据正则表达式去检索字符串

serach()只会查找第一个，即使设置全局匹配也没用

```js
//搜索字符串中是否含有abc 或 aec 或 afc
result = str.search(/a[bef]c/);
```

`match()`

可以根据正则表达式，从一个字符串中将符合条件的内容提取出来

默认情况下我们的match只会找到第一个符合要求的内容，找到以后就停止检索

我们可以设置正则表达式为全局匹配模式，这样就会匹配到所有的内容

可以为一个正则表达式设置多个匹配模式，且顺序无所谓

match()会将匹配到的内容封装到一个数组中返回，即使只查询到一个结果

```js
str = "1a2a3a4a5e6f7A8B9C";
result = str.match(/[a-z]/ig);
```

`replace()`

可以将字符串中指定内容替换为新的内容

参数：

1.被替换的内容，可以接受一个正则表达式作为参数

2.新的内容

默认只会替换第一个

```js
result = str.replace(/[a-z]/gi , "");
```

### 量词

通过量词可以设置一个内容出现的次数

量词只对它前边的一个内容起作用

* `{n}` 正好出现n次
* `{m,n}` 出现m-n次
* `{m,}` m次以上

+ `+`  至少一个，相当于{1,}

* `*`  0个或多个，相当于{0,}
* `?`  0个或1个，相当于{0,1}

### 其他

**开头结尾**

`^` 表示开头

`$` 表示结尾

如果在正则表达式中同时使用`^ $`则要求字符串必须完全符合正则表达式

**含有**

检查一个字符串中是否含有 `.`

`.` 表示任意字符

**转义字符**

在正则表达式中使用`\`作为转义字符

`\.` 来表示`.`

`\\` 表示`\`

注意：使用构造函数时，由于它的参数是一个字符串，而`\`是字符串中转义字符，如果要使用`\`则需要使用`\\`来代替

```js
\w 任意字母、数字、_  [A-z0-9_]
\W 除了字母、数字、_  [^A-z0-9_]
\d 任意的数字 [0-9]
\D 除了数字 [^0-9]
\s 空格
\S 除了空格
\b 单词边界
\B 除了单词边界
```

## DOM

> Document Object Model      文档对象模型

通过DOM可以来任意来修改网页中各个内容 

**文档**：文档指的是网页，一个网页就是一个文档  

**对象**：对象指将网页中的每一个节点都转换为对象，转换完对象以后，就可以以一种纯面向对象的形式来操作网页了  

模型：模型用来表示节点和节点之间的关系，方便操作页面  

**节点（Node）**：节点是构成网页的最基本的单元，网页中的每一个部分都可以称为是一个节点  

虽然都是节点，但是节点的类型却是不同的  

**常用的节点**  

* 文档节点 （Document），代表整个网页  
* 元素节点（Element），代表网页中的标签  
* 属性节点（Attribute），代表标签中的属性  
* 文本节点（Text），代表网页中的文本内容  

> 浏览器已经为我们提供 **文档节点** 对象，这个对象是window属性
>
> 可以在页面中直接使用，文档节点代表的是整个网页

```js
//获取到button对象
var btn = document.getElementById("btn");
//修改按钮的文字
btn.innerHTML = "I'm Button";
```

### 文档加载

浏览器在加载一个页面时，是按照自上向下的顺序加载的，读取到一行就运行一行,如果将script标签写到页面的上边，在代码执行时，页面还没有加载，页面没有加载DOM对象也没有加载，会导致无法获取到DOM对象。

==onload事件会在整个页面加载完成之后才触发==

为window绑定一个onload事件，该事件对应的响应函数将会在页面加载完成之后执行，这样可以确保我们的代码执行时所有的DOM对象已经加载完毕了。

```html
<script type="text/javascript">

	window.onload = function(){
		//获取id为btn的按钮
		var btn = document.getElementById("btn");
		//为按钮绑定一个单击响应函数
		btn.onclick = function(){
			alert("hello");
		};
	};
</script>
```

还可以将js代码编写到页面的下部，就可以在页面加载完毕以后再执行js代码

```html
<body>
	
	<button id="btn">点我一下</button>
	
	<script type="text/javascript">
		//获取id为btn的按钮
		var btn = document.getElementById("btn");
		//为按钮绑定一个单击响应函数
		btn.onclick = function(){
			alert("hello");
		};
	</script>
	
</body>
```

### DOM查询

**getElementsByTagName**()

可以根据标签名来获取一组元素节点对象

这个方法会给我们返回一个类数组对象，所有查询到的元素都会封装到对象中

即使查询到的元素只有一个，也会封装到数组中返回

```js
//查找所有li节点
var lis = document.getElementsByTagName("li");
```

**getElementsByName**

  ```js
  //查找name=gender的所有节点
  var inputs = document.getElementsByName("gender");				
  ```

**getElementsByClassName()**

根据元素的class属性值查询一组元素节点对象，但是该方法不支持**IE8及以下**的浏览器

```js
var box1 = document.getElementsByClassName("box1");
```

**innerHTML**

用于获取元素内部的HTML代码的

对于自结束标签，这个属性没有意义

如果需要读取元素节点属性，直接使用 `元素.属性名`

例子：元素.id 元素.name 元素.value

注意：class属性不能采用这种方式，读取class属性时需要使用 `元素.className`

**innerText**

该属性可以获取到元素内部的文本内容

它和innerHTML类似，不同的是它会自动将html去除

```js
for(var i=0 ; i<inputs.length ; i++){
    //alert(inputs[i].innerHTML);
    alert(inputs[i].className);
}
alert(pn.innerText);
```

**childNodes**会获取包括文本节点在内的所有节点

根据DOM标签，标签间空白也会当成文本节点

注意：在**IE8及以下**的浏览器中，不会将空白文本当成子节点

**children**属性可以获取当前元素的所有子元素

**firstChild**可以获取到当前元素的第一个子节点（包括空白文本节点）

**firstElementChild**获取当前元素的第一个子元素

**firstElementChild**不支持IE8及以下的浏览器，如果需要兼容他们尽量不要使用

**parentNode**获取当前元素的父节点

**previousSibling**返回前一个兄弟节点（也可能获取到空白的文本）

**previousElementSibling**获取前一个兄弟元素，IE8及以下不支持

**nodeValue**获取当前元素的文本节点

```js
var cns = city.childNodes;
var cns2 = city.children;
var fir = phone.firstChild;
var fir = phone.firstElementChild;
var pn = bj.parentNode;
var ps = and.previousSibling;
var pe = and.previousElementSibling;
alert(bj.firstChild.nodeValue);
```

**document.body**在document中有一个属性body，它保存的是body的引用

**document.documentElement**保存的是html根标签

**document.all**代表页面中所有的元素

**document.querySelector()**

需要一个选择器的字符串作为参数，可以根据一个CSS选择器来查询一个元素节点对象

虽然IE8中没有getElementsByClassName()但是可以使用querySelector()代替

使用该方法总会返回唯一的一个元素，如果满足条件的元素有多个，那么它只会返回第一个

**document.querySelectorAll()**

该方法和querySelector()用法类似，不同的是它会将符合条件的元素封装到一个数组中返回

即使符合条件的元素只有一个，它也会返回数组

```js
var body = document.body;
var html = document.documentElement;
var all = document.all;
var div = document.querySelector(".box1 div");
var box1 = document.querySelectorAll(".box1");
```

### DOM增删改

**document.createElement()**

可以用于创建一个元素节点对象。

它需要一个标签名作为参数，将会根据该标签名创建元素节点对象，并将创建好的对象作为返回值返回。

**document.createTextNode()**

可以用来创建一个文本节点对象

需要一个文本内容作为参数，将会根据该内容创建文本节点，并将新的节点返回

**appendChild()**

向一个父节点中添加一个新的子节点

用法：`父节点.appendChild(子节点);`

**insertBefore()**

可以在指定的子节点前插入新的子节点

语法：`父节点.insertBefore(新节点,旧节点);`

**replaceChild()**

可以使用指定的子节点替换已有的子节点

语法：父节点.replaceChild(新节点,旧节点);

**removeChild()**

可以删除一个子节点

语法：`父节点.removeChild(子节点);` `子节点.parentNode.removeChild(子节点);`

```js
var li = document.createElement("li");
var gzText = document.createTextNode("广州");
li.appendChild(gzText);
city.insertBefore(li , bj);
city.replaceChild(li , bj);
bj.parentNode.removeChild(bj);
```

使用**innerHTML**也可以完成DOM的增删改的相关操作

一般我们会两种方式结合使用

```js
//创建一个li
var li = document.createElement("li");
//向li中设置文本
li.innerHTML = "广州";
//将li添加到city中
city.appendChild(li);
```

### 使用DOM操作CSS

#### 通过JS修改元素的样式

语法：`元素.style.样式名 = 样式值`

 注意：如果CSS的样式名中含有`-`，这种名称在JS中是不合法的比如`background-color`

需要将这种样式名修改为驼峰命名法，去掉`-`，然后将`-`后的字母大写

我们通过style属性设置的样式都是`内联样式`，而内联样式有较高的优先级，所以通过JS修改的样式往往会立即显示

但是如果在样式中写了`!important`，则此时样式会有最高的优先级，即使通过JS也不能覆盖该样式，此时将会导致JS修改样式失效。所以尽量不要为样式添加`!important`

```js
box1.style.width = "300px";
box1.style.height = "300px";
box1.style.backgroundColor = "yellow";
```

#### 读取box1的样式

语法：`元素.style.样式名`

通过style属性设置和读取的都是`内联样式`，无法读取样式表中的样式

```js
alert(box1.style.width);
```

#### 获取元素的当前显示的样式

语法：`元素.currentStyle.样式名`

它可以用来读取当前元素正在显示的样式

如果当前元素没有设置该样式，则获取它的默认值

`currentStyle`只有`IE`浏览器支持，其他的浏览器都不支持

在其他浏览器中可以使用`getComputedStyle()`这个方法来获取元素当前的样式

这个方法是window的方法，可以直接使用

需要两个参数

第一个：要获取样式的元素

第二个：可以传递一个伪元素，一般都传null

该方法会返回一个对象，对象中封装了当前元素对应的样式

可以通过`对象.样式名`来读取样式

如果获取的样式没有设置，则会获取到真实的值，而不是默认值

比如：没有设置width，它不会获取到auto，而是一个长度

 但是该方法`不支持IE8及以下`的浏览器

通过`currentStyle`和`getComputedStyle()`读取到的样式都是**只读**的，不能修改，如果要修改必须通过`style`属性

```js
//正常浏览器的方式
alert(getComputedStyle(box1,null).backgroundColor);
//IE8的方式
alert(box1.currentStyle.backgroundColor);
```

#### 其他样式操作的属性

**clientWidth** **clientHeight**

这两个属性可以获取元素的可见宽度和高度

这些属性都是不带px的，返回都是一个数字，可以直接进行计算

会获取元素宽度和高度，包括内容区和内边距

这些属性都是只读的，不能修改

```js
alert(box1.clientWidth);
alert(box1.clientHeight);
```

**offsetWidth offsetHeight**

获取元素的整个的宽度和高度，包括内容区、内边距和边框

```js
alert(box1.offsetWidth);
```

**offsetParent**

可以用来获取当前元素的定位父元素

会获取到离当前元素最近的开启了定位的祖先元素

如果所有的祖先元素都没有开启定位，则返回body

```js
var op = box1.offsetParent;
```

**offsetLeft offsetTop**

当前元素相对于其定位父元素的水平/垂直偏移量

```
alert(box1.offsetLeft);
```

**scrollWidth** **scrollHeight**

可以获取元素整个滚动区域的宽度和高度

**scrollLeft scrollTop**

可以获取水平/垂直滚动条滚动的距离

> 当满足scrollHeight - scrollTop == clientHeight，说明垂直滚动条滚动到底了
>
> 当满足scrollWidth - scrollLeft == clientWidth，说明水平滚动条滚动到底

```js
alert(box4.scrollHeight - box4.scrollTop); 
```

**onscroll**  

当垂直滚动条滚动到底时使表单项可用

该事件会在元素的滚动条滚动时触发

```js
//获取id为info的p元素
var info = document.getElementById("info");
//获取两个表单项
var inputs = document.getElementsByTagName("input");
//为info绑定一个滚动条滚动的事件
info.onscroll = function(){
	
	//检查垂直滚动条是否滚动到底
	//if(info.scrollHeight - info.scrollTop == info.clientHeight){
    //谷歌存在误差，需取整
    if(Math.round(info.scrollHeight - info.scrollTop) == info.clientHeight){
		//滚动条滚动到底，使表单项可用
		/*
			* disabled属性可以设置一个元素是否禁用，
			* 	如果设置为true，则元素禁用
			* 	如果设置为false，则元素可用
			*/
		inputs[0].disabled = false;
		inputs[1].disabled = false;
	}
	
};   
```

## 事件

用户和浏览器之间的交互行为，比如：点击按钮，鼠标移动、关闭窗口。。。

可以为按钮的对应事件绑定处理函数的形式来响应事件

这样当事件被触发时，其对应的函数将会被调用

```js
//绑定一个单击事件
//像这种为单击事件绑定的函数，我们称为单击响应函数
btn.onclick = function(){
	alert("你还点~~~");
};
```

### 事件对象  

当响应函数被调用时，浏览器每次都会将一个事件对象作为实参传递进响应函数中，这个事件对象中封装了当前事件的相关信息，比如：鼠标的坐标，键盘的按键，鼠标的按键，滚轮的方向。。  

在IE8及以下的浏览器中，是将事件对象作为**window对象的属性**保存的

```js
//onmousemove 该事件将会在鼠标在元素中移动时被触发
document.onmousemove = function(event){	
	//解决兼容问题
	event = event || window.event;	
	//获取滚动条滚动的距离
	/*
		* chrome认为浏览器的滚动条是body的，可以通过body.scrollTop来获取
		* 火狐等浏览器认为浏览器的滚动条是html的，
		*/
	var st = document.body.scrollTop || document.documentElement.scrollTop;
	var sl = document.body.scrollLeft || document.documentElement.scrollLeft;
	//var st = document.documentElement.scrollTop;
	//获取到鼠标的坐标
	/*
		* clientX和clientY
		* 	用于获取鼠标在当前的可见窗口的坐标
		* div的偏移量，是相对于整个页面的
		* 
		* pageX和pageY可以获取鼠标相对于当前页面的坐标
		* 	但是这个两个属性在IE8中不支持，所以如果需要兼容IE8，则不要使用
		*/
	var left = event.clientX;
	var　top = event.clientY;
	
	//设置div的偏移量
	box1.style.left = left + sl + "px";
	box1.style.top = top + st + "px";
	
};
```

 ### 事件的冒泡（Bubble）  

事件的冒泡指的是事件向上传导，当后代元素上的事件被触发时，将会导致其祖先元素上的同类事件也会触发。  

 事件的冒泡大部分情况下都是有益的，如果需要取消冒泡，则需要使用事件对象来取消  

**可以将事件对象的cancelBubble设置为true，即可取消冒泡**  

```javascript  
元素.事件 = function(event){  
    event = event || window.event;  
    event.cancelBubble = true;  
};  
```

  

### 事件的委派  

> 我们希望，只绑定一次事件，即可应用到多个的元素上，即使元素是后添加的  
>
> 我们可以尝试将其绑定给元素的共同的祖先元素  

事件委派指将事件统一绑定给元素的共同的祖先元素，这样当后代元素上的事件触发时，会一直冒泡到祖先元素，从而通过祖先元素的响应函数来处理事件。  

事件委派是利用了冒泡，通过委派可以减少事件绑定的次数，提高程序的性能		  

```js
//为ul绑定一个单击响应函数
u1.onclick = function(event){
	event = event || window.event;
	
	/*
		* target
		* 	- event中的target表示的触发事件的对象
		*/
	//alert(event.target);
	
	
	//如果触发事件的对象是我们期望的元素，则执行否则不执行
	if(event.target.className == "link"){
		alert("我是ul的单击响应函数");
	}
	
};
```

### 事件的绑定  

使用 `对象.事件 = 函数` 的形式绑定响应函数，

它只能同时为一个元素的一个事件绑定一个响应函数，不能绑定多个，如果绑定了多个，则后边会覆盖掉前边的

**addEventListener()**

通过这个方法也可以为元素绑定响应函数

参数：

1. 事件的字符串，不要on

2. 回调函数，当事件触发时该函数会被调用

3. 是否在捕获阶段触发事件，需要一个布尔值，一般都传false

使用addEventListener()可以同时为一个元素的相同事件同时绑定多个响应函数，这样当事件被触发时，响应函数将会按照函数的绑定顺序执行

**这个方法不支持IE8及以下的浏览器** 

```js
btn01.addEventListener("click",function(){  
	alert(1);  
},false);  
  
btn01.addEventListener("click",function(){  
	alert(2);  
},false);					  
```

**attachEvent()**  

在IE8中可以使用attachEvent()来绑定事件  

参数：  

1. 事件的字符串，要on  
2. 回调函数  

这个方法也可以同时为一个事件绑定多个处理函数，不同的是它是**后绑定先执行**，执行顺序和addEventListener()相反  

```javascript  
btn01.attachEvent("onclick",function(){  
	alert(1);  
});   
btn01.attachEvent("onclick",function(){  
	alert(2);  
});	  
```

```javascript  
//定义一个函数，用来为指定元素绑定响应函数
/*
	* addEventListener()中的this，是绑定事件的对象
	* attachEvent()中的this，是window
	*  需要统一两个方法this
	*/
/*
	* 参数：
	* 	obj 要绑定事件的对象
	* 	eventStr 事件的字符串(不要on)
	*   callback 回调函数
	*/
function bind(obj , eventStr , callback){
	if(obj.addEventListener){
		//大部分浏览器兼容的方式
		obj.addEventListener(eventStr , callback , false);
	}else{
		/*
			* this是谁由调用方式决定
			* callback.call(obj)
			*/
		//IE8及以下
		obj.attachEvent("on"+eventStr , function(){
			//在匿名函数中调用回调函数
			callback.call(obj);
		});
	}
}
```

### 事件的传播  

关于事件的传播网景公司和微软公司有不同的理解  

微软公司认为事件应该是**由内向外**传播，也就是当事件触发时，应该先触发当前元素上的事件，然后再向当前元素的祖先元素上传播，也就说事件应该在冒泡阶段执行。  

网景公司认为事件应该是**由外向内**传播的，也就是当前事件触发时，应该先触发当前元素的最外层的祖先元素的事件，然后在向内传播给后代元素  

 W3C综合了两个公司的方案，将事件传播分成了三个阶段 

1. 捕获阶段  

   在捕获阶段时从最外层的祖先元素，向目标元素进行事件的捕获，但是默认此时不会触发事件 

2. 目标阶段  

   事件捕获到目标元素，捕获结束开始在目标元素上触发事件  

3. 冒泡阶段  

   事件从目标元素向他的祖先元素传递，依次触发祖先元素上的事件  

 如果希望在捕获阶段就触发事件，可以将addEventListener()的第三个参数设置为true  

一般情况下我们不会希望在捕获阶段触发事件，所以这个参数一般都是false  

 **IE8及以下的浏览器中没有捕获阶段**  

### 常用事件  

#### 鼠标事件  

拖拽事件  

```javascript  
window.onload = function(){
	/*
		* 拖拽box1元素
		*  - 拖拽的流程
		* 		1.当鼠标在被拖拽元素上按下时，开始拖拽  onmousedown
		* 		2.当鼠标移动时被拖拽元素跟随鼠标移动 onmousemove
		* 		3.当鼠标松开时，被拖拽元素固定在当前位置	onmouseup
		*/
	
	//获取box1
	var box1 = document.getElementById("box1");
	var box2 = document.getElementById("box2");
	var img1 = document.getElementById("img1");
	
	//开启box1的拖拽
	drag(box1);
	//开启box2的
	drag(box2);
	
	drag(img1);

};

/*
	* 提取一个专门用来设置拖拽的函数
	* 参数：开启拖拽的元素
	*/
function drag(obj){
	//当鼠标在被拖拽元素上按下时，开始拖拽  onmousedown
	obj.onmousedown = function(event){
		
		//设置box1捕获所有鼠标按下的事件
		/*
			* setCapture()
			* 	- 只有IE支持，但是在火狐中调用时不会报错，
			* 		而如果使用chrome调用，会报错
			*/
		/*if(box1.setCapture){
			box1.setCapture();
		}*/
		obj.setCapture && obj.setCapture();
		
		
		event = event || window.event;
		//div的偏移量 鼠标.clentX - 元素.offsetLeft
		//div的偏移量 鼠标.clentY - 元素.offsetTop
		var ol = event.clientX - obj.offsetLeft;
		var ot = event.clientY - obj.offsetTop;
		
		
		//为document绑定一个onmousemove事件
		document.onmousemove = function(event){
			event = event || window.event;
			//当鼠标移动时被拖拽元素跟随鼠标移动 onmousemove
			//获取鼠标的坐标
			var left = event.clientX - ol;
			var top = event.clientY - ot;
			
			//修改box1的位置
			obj.style.left = left+"px";
			obj.style.top = top+"px";
			
		};
		
		//为document绑定一个鼠标松开事件
		document.onmouseup = function(){
			//当鼠标松开时，被拖拽元素固定在当前位置	onmouseup
			//取消document的onmousemove事件
			document.onmousemove = null;
			//取消document的onmouseup事件
			document.onmouseup = null;
			//当鼠标松开时，取消对事件的捕获
			obj.releaseCapture && obj.releaseCapture();
		};
		
		/*
			* 当我们拖拽一个网页中的内容时，浏览器会默认去搜索引擎中搜索内容，
			* 	此时会导致拖拽功能的异常，这个是浏览器提供的默认行为，
			* 	如果不希望发生这个行为，则可以通过return false来取消默认行为
			* 
			* 但是这招对IE8不起作用
			*/
		return false;
		
	};
}
```

滚轮事件：  

```javascript		  
window.onload = function(){
	
	
	//获取id为box1的div
	var box1 = document.getElementById("box1");
	
	//为box1绑定一个鼠标滚轮滚动的事件
	/*
		* onmousewheel鼠标滚轮滚动的事件，会在滚轮滚动时触发，
		* 	但是火狐不支持该属性
		* 
		* 在火狐中需要使用 DOMMouseScroll 来绑定滚动事件
		* 	注意该事件需要通过addEventListener()函数来绑定
		*/
	
	
	box1.onmousewheel = function(event){
		
		event = event || window.event;
		
		
		//event.wheelDelta 可以获取鼠标滚轮滚动的方向
		//向上滚 120   向下滚 -120
		//wheelDelta这个值我们不看大小，只看正负
		
		//alert(event.wheelDelta);
		
		//wheelDelta这个属性火狐中不支持
		//在火狐中使用event.detail来获取滚动的方向
		//向上滚 -3  向下滚 3
		//alert(event.detail);
		
		
		/*
			* 当鼠标滚轮向下滚动时，box1变长
			* 	当滚轮向上滚动时，box1变短
			*/
		//判断鼠标滚轮滚动的方向
		if(event.wheelDelta > 0 || event.detail < 0){
			//向上滚，box1变短
			box1.style.height = box1.clientHeight - 10 + "px";
			
		}else{
			//向下滚，box1变长
			box1.style.height = box1.clientHeight + 10 + "px";
		}
		
		/*
			* 使用addEventListener()方法绑定响应函数，取消默认行为时不能使用return false
			* 需要使用event来取消默认行为event.preventDefault();
			* 但是IE8不支持event.preventDefault();这个玩意，如果直接调用会报错
			*/
		event.preventDefault && event.preventDefault();
		
		
		/*
			* 当滚轮滚动时，如果浏览器有滚动条，滚动条会随之滚动，
			* 这是浏览器的默认行为，如果不希望发生，则可以取消默认行为
			*/
		return false;
		
		
		
		
	};
	
	//为火狐绑定滚轮事件
	bind(box1,"DOMMouseScroll",box1.onmousewheel);
	
	
};


function bind(obj , eventStr , callback){
	if(obj.addEventListener){
		//大部分浏览器兼容的方式
		obj.addEventListener(eventStr , callback , false);
	}else{
		/*
			* this是谁由调用方式决定
			* callback.call(obj)
			*/
		//IE8及以下
		obj.attachEvent("on"+eventStr , function(){
			//在匿名函数中调用回调函数
			callback.call(obj);
		});
	}
}
```

#### 键盘事件  

```javascript  
window.onload = function(){
	
	/*
		* 键盘事件：
		* 	onkeydown
		* 		- 按键被按下
		* 		- 对于onkeydown来说如果一直按着某个按键不松手，则事件会一直触发
		* 		- 当onkeydown连续触发时，第一次和第二次之间会间隔稍微长一点，其他的会非常的快
		* 			这种设计是为了防止误操作的发生。
		* 	onkeyup
		* 		- 按键被松开
		* 
		*  键盘事件一般都会绑定给一些可以获取到焦点的对象或者是document
		*/
	
	document.onkeydown = function(event){
		event = event || window.event;
		
		/*
			* 可以通过keyCode来获取按键的编码
			* 	通过它可以判断哪个按键被按下
			* 除了keyCode，事件对象中还提供了几个属性
			* 	altKey
			* 	ctrlKey
			* 	shiftKey
			* 		- 这个三个用来判断alt ctrl 和 shift是否被按下
			* 			如果按下则返回true，否则返回false
			*/
		
		//console.log(event.keyCode);
		
		//判断一个y是否被按下
		//判断y和ctrl是否同时被按下
		if(event.keyCode === 89 && event.ctrlKey){
			console.log("ctrl和y都被按下了");
		}
		
		
	};
	
	/*document.onkeyup = function(){
		console.log("按键松开了");
	};*/
	
	//获取input
	var input = document.getElementsByTagName("input")[0];
	
	input.onkeydown = function(event){
		
		event = event || window.event;
		
		//console.log(event.keyCode);
		//数字 48 - 57
		// 小键盘的数字 96-105
		//使文本框中不能输入数字
		if(event.keyCode >= 48 && event.keyCode <= 57){
			//在文本框中输入内容，属于onkeydown的默认行为
			//如果在onkeydown中取消了默认行为，则输入的内容，不会出现在文本框中
			return false;
		}
		
		
	};
};
```



## BOM

> 浏览器对象模型(browser object model) 

BOM可以使我们通过JS来操作浏览器，在BOM中为我们提供了一组对象，用来完成对浏览器的操作  

**BOM对象**  

* Window  代表的是整个浏览器的窗口，同时window也是网页中的全局对象  
* Navigator  代表的当前浏览器的信息，通过该对象可以来识别不同的浏览器  
* Location  代表当前浏览器的地址栏信息，通过Location可以获取地址栏信息，或者操作浏览器跳转页面  
* History  代表浏览器的历史记录，可以通过该对象来操作浏览器的历史记录。由于隐私原因，该对象不能获取到具体的历史记录，只能操作浏览器向前或向后翻页，而且该操作只在当次访问时有效。  
* Screen  代表用户的屏幕的信息，通过该对象可以获取到用户的显示器的相关的信息  

这些BOM对象在浏览器中都是作为**window对象的属性**保存的，可以通过window对象来使用，也可以直接使用。  

### Navigator  

代表的当前浏览器的信息，通过该对象可以来识别不同的浏览器  

由于历史原因，Navigator对象中的大部分属性都已经不能帮助我们识别浏览器了  

一般我们只会使用userAgent来判断浏览器的信息，userAgent是一个字符串，这个字符串中包含有用来描述浏览器信息的内容，  不同的浏览器会有不同的userAgent  

**userAgent**

火狐  `Mozilla5.0 (Windows NT 6.1; WOW64; rv:50.0) Gecko20100101 Firefox50.0`  

Chrome  `Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/93.0.4577.63 Safari/537.36`

IE8  `Mozilla4.0 (compatible; MSIE 8.0; Windows NT 6.1; WOW64; Trident7.0; SLCC2; .NET CLR 2.0.50727; .NET CLR 3.5.30729; .NET CLR 3.0.30729; Media Center PC 6.0; .NET4.0C; .NET4.0E)`  

IE9  `Mozilla5.0 (compatible; MSIE 9.0; Windows NT 6.1; WOW64; Trident7.0; SLCC2; .NET CLR 2.0.50727; .NET CLR 3.5.30729; .NET CLR 3.0.30729; Media Center PC 6.0; .NET4.0C; .NET4.0E)`  

IE10  `Mozilla5.0 (compatible; MSIE 10.0; Windows NT 6.1; WOW64; Trident7.0; SLCC2; .NET CLR 2.0.50727; .NET CLR 3.5.30729; .NET CLR 3.0.30729; Media Center PC 6.0; .NET4.0C; .NET4.0E)`  

IE11  `Mozilla5.0 (Windows NT 6.1; WOW64; Trident7.0; SLCC2; .NET CLR 2.0.50727; .NET CLR 3.5.30729; .NET CLR 3.0.30729; Media Center PC 6.0; .NET4.0C; .NET4.0E; rv:11.0) like Gecko`  

在IE11中已经将微软和IE相关的标识都已经去除了，所以我们基本已经不能通过UserAgent来识别一个浏览器是否是IE了  

```javascript  
alert(navigator.appName);  
  
var ua = navigator.userAgent;  
  
console.log(ua);  
  
if(firefoxi.test(ua)){  
alert("你是火狐！！！");  
}else if(chromei.test(ua)){  
alert("你是Chrome");  
}else if(msiei.test(ua)){  
alert("你是IE浏览器~~~");  
}else if("ActiveXObject" in window){  
alert("你是IE11，枪毙了你~~~");  
}  
```

### History  

> 可以用来操作浏览器向前或向后翻页	  

length  属性，可以获取到当成访问的链接数量  

back()  可以用来回退到上一个页面，作用和浏览器的回退按钮一样	  

forward()  可以跳转下一个页面，作用和浏览器的前进按钮一样	  

go()  可以用来跳转到指定的页面  

它需要一个整数作为参数  

1:表示向前跳转一个页面 相当于forward()  

2:表示向前跳转两个页面  

-1:表示向后跳转一个页面  

-2:表示向后跳转两个页面  

### Location  

> 该对象中封装了浏览器的地址栏的信息	  

如果直接打印location，则可以获取到地址栏的信息（当前页面的完整路径）  

```js
alert(location); 
```

如果直接将location属性修改为一个完整的路径，或相对路径 ，则我们页面会自动跳转到该路径，并且会生成相应的历史记录  

```js
location = "http:www.baidu.com";  
location = "01.BOM.html"; 
```

assign()  用来跳转到其他的页面，作用和直接修改location一样	  

reload()  用于重新加载当前页面，作用和刷新按钮一样  

如果在方法中传递一个true，作为参数，则会强制清空缓存刷新页面  

```js
location.reload(true);	 
```

replace()  可以使用一个新的页面替换当前页面，调用完毕也会跳转页面。不会生成历史记录，不能使用回退按钮回退  

### window 

#### window对象的方法 

| 方法                | 描述                                           |
| ------------------- | ---------------------------------------------- |
| ==alert()==         | 警告框                                         |
| blur()              | 键盘焦点从顶层窗口移开                         |
| ==clearInterval()== | 取消周期性定时器                               |
| ==clearTimeout()==  | 取消一次性定时器                               |
| close()             | 关闭浏览器窗口                                 |
| ==confirm()==       | 显示带有消息及确认取消按钮的对话框             |
| createPopup()       | 创建一个弹出窗口(?？？)                        |
| focus()             | 把键盘的焦点给窗口                             |
| moveBy()            | 基于当前窗口的坐标，向某个方向移动指定像素距离 |
| moveTo()            | 窗口的左上角移动到指定位置                     |
| open()              | 打开一个新的浏览器窗口或查找一个已经命名的窗口 |
| print()             | 打印当前窗口的内容                             |
| ==prompt()==        | 可输入的对话框                                 |
| resizeBy()          | 按照指定的像素调整窗口的大小                   |
| resizeTo()          | 窗口的大小调整到指定的宽高                     |
| scrollBy()          | 指定的像素值来滚动内容                         |
| scrollTo()          | 内容滚动到指定坐标                             |
| ==setInterval()==   | 周期性定时器                                   |
| ==setTimeout()==    | 一次性定时器                                   |

####  定时器  

**setInterval()**  

定时调用  

可以将一个函数，每隔一段时间执行一次  

参数：  

1. 回调函数，该函数会每隔一段时间被调用一次  

2. 每次调用间隔的时间，单位是毫秒  

返回值：  

返回一个Number类型的数据，这个数字用来作为定时器的唯一标识  

**clearInterval()**

可以用来关闭一个定时器  

方法中需要一个定时器的标识作为参数，这样将关闭标识对应的定时器   

clearInterval()可以接收任意参数，如果参数是一个有效的定时器的标识，则停止对应的定时器；如果参数不是一个有效的标识，则什么也不做  

```javascript  
var num = 1;  
var timer = setInterval(function() {  
	count.innerHTML = num++;  
	if(num == 11) {  
		//关闭定时器  
		clearInterval(timer);  
	}  
}, 1000);  
```

#### 延时调用  

**setTimeout**  

延时调用一个函数不马上执行，而是隔一段时间以后在执行，而且只会执行一次  

延时调用和定时调用的区别，定时调用会执行多次，而延时调用只会执行一次  

延时调用和定时调用实际上是可以互相代替的，在开发中可以根据自己需要去选择  

使用**clearTimeout()**来关闭一个延时调用  

```js
var timer = setTimeout(function(){  
	console.log(num++);  
},3000);  
clearTimeout(timer);  
```

## 类的操作  

**直接修改元素的类css：**  

通过style属性来修改元素的样式，每修改一个样式，浏览器就需要重新渲染一次页面。 这样的执行的性能是比较差的，而且这种形式当我们要修改多个样式时，也不太方便

```js
box.style.width = "200px";
box.style.height = "200px";
box.style.backgroundColor = "yellow";
```

我们可以通过修改元素的class属性来间接的修改样式.这样一来，我们只需要修改一次，即可同时修改多个样式，浏览器只需要重新渲染页面一次，性能比较好，并且这种方式，可以使表现和行为进一步的分离  

```javascript  
box.className += " b2";	//注意有空格，添加class属性  
```

```javascript  
//定义一个函数，用来向一个元素中添加指定的class属性值
/*
	* 参数:
	* 	obj 要添加class属性的元素
	*  cn 要添加的class值
	* 	
	*/
function addClass(obj , cn){
	
	//检查obj中是否含有cn
	if(!hasClass(obj , cn)){
		obj.className += " "+cn;
	}
	
}

/*
	* 判断一个元素中是否含有指定的class属性值
	* 	如果有该class，则返回true，没有则返回false
	* 	
	*/
function hasClass(obj , cn){
	
	//判断obj中有没有cn class
	//创建一个正则表达式
	//var reg = /\bb2\b/;
	var reg = new RegExp("\\b"+cn+"\\b");
	
	return reg.test(obj.className);
	
}

/*
	* 删除一个元素中的指定的class属性
	*/
function removeClass(obj , cn){
	//创建一个正则表达式
	var reg = new RegExp("\\b"+cn+"\\b");
	
	//删除class
	obj.className = obj.className.replace(reg , "");
	
}

/*
	* toggleClass可以用来切换一个类
	* 	如果元素中具有该类，则删除
	* 	如果元素中没有该类，则添加
	*/
function toggleClass(obj , cn){
	
	//判断obj中是否含有cn
	if(hasClass(obj , cn)){
		//有，则删除
		removeClass(obj , cn);
	}else{
		//没有，则添加
		addClass(obj , cn);
	}
	
}
```

## JSON 

> **JavaScript Object Notation** JS对象表示法

JS中的对象只有JS自己认识，其他的语言都不认识  

**JSON就是一个特殊格式的字符串**，这个字符串可以被任意的语言所识别，  并且可以转换为任意语言中的对象，JSON在开发中主要用来数据的交互  

JSON和JS对象的格式一样，只不过**JSON字符串中的属性名必须加双引号**  

其他的和JS语法一致  

JSON分类：  

* 对象 {}  
* 数组 []  

JSON中允许的值：  

* 字符串  
* 数值  
* 布尔值  
* null  
* 对象  
* 数组  

举例：  

```javascript  
var arr = '[1,2,3,"hello",true]';  
			  
var obj2 = '{"arr":[1,2,3]}';  
  
var arr2 ='[{"name":"孙悟空","age":18,"gender":"男"},{"name":"孙悟空","age":18,"gender":"男"}]';  
```

**JSON工具类**  

将JSON字符串转换为JS中的对象

在JS中，为我们提供了一个工具类，就叫JSON

这个对象可以帮助我们将一个JSON转换为JS对象，也可以将一个JS对象转换为JSON

**json --> js对象**

`JSON.parse()`

可以将以JSON字符串转换为js对象

它需要一个JSON字符串作为参数，会将该字符串转换为JS对象并返回

**JS对象 ---> JSON**

`JSON.stringify()`

可以将一个JS对象转换为JSON字符串

需要一个js对象作为参数，会返回一个JSON字符串

**JSON这个对象在IE7及以下的浏览器中不支持，所以在这些浏览器中调用时会报错**

## eval()  

这个函数可以用来执行一段字符串形式的JS代码，并将执行结果返回。

如果使用eval()执行的字符串中含有{},它会将{}当成是代码块。  

如果不希望将其当成代码块解析，则需要在字符串前后各加一个()  

 eval()这个函数的功能很强大，但是在开发中尽量不要使用，首先它的执行性能比较差，然后它还具有安全隐患 		  

```js
var str = '{"name":"孙悟空","age":18,"gender":"男"}';  
var obj = eval("("+str+")");  
```









