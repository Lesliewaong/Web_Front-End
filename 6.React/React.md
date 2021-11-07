---
title: React
date: 2021-11-07 16:49:47
tags:         
 - React 
 - 框架
categories: 前端
---

# React基础知识与概念

React相对于vue来说学习成本更高，或者说需要的基础知识更多，需要有一些预备知识点支撑

1. webpack相关知识
2. axios相关知识
3. js基础与es6相关知识

## React简介

官网链接:[中文官网](https://react.docschina.org/)

用于动态构建用户界面的JavaScript(只关注视图)

由Facebook开发，且开源

![image-20211021204303258](C:\Users\Lesliewaong\AppData\Roaming\Typora\typora-user-images\image-20211021204303258.png)

### 为什么学React

* 原生JS操作DOM繁琐，效率低
* 使用JS直接操作DOM,浏览器会进行大量的重绘重排
* 原生JS没有组件化编码方案，代码复用低

### React的特点

* **声明式**编程

* **组件化**编程

* React Native编写原生应用 

  **React Native** (简称RN)是Facebook于2015年4月开源的跨平台**移动应用开发框架**，是Facebook早先开源的JS框架 React 在原生移动应用平台的衍生产物

* 高效 (使用**虚拟DOM**+优秀的**Diffing算法**)

### React高效的原因

1. 使用虚拟(virtual)DOM,不总是直接操作页面真实DON
2. DOM Diffing算法,最小化页面重绘
3. `注意`：React并不会提高渲染速度,反而可能会增加渲染时间,真正高效的原因是它能有效`减少渲染次数`

### React 基础案例

1.先倒入三个包：

【先引入`react.development.js`，后引入`react-dom.development.js`】

2.创建一个容器

3.创建虚拟DOM，渲染到容器中

```html
<body>
	<!-- 准备好一个“容器” -->
	<div id="test"></div>

	<!-- 引入react核心库 -->
	<script type="text/javascript" src="../js/react.development.js"></script>
	<!-- 引入react-dom，用于支持react操作DOM -->
	<script type="text/javascript" src="../js/react-dom.development.js"></script>
	<!-- 引入babel，用于将ES6 => ES5 jsx => js -->
	<script type="text/javascript" src="../js/babel.min.js"></script>

	<script type="text/babel" > /* 此处一定要写babel */
		//1.创建虚拟DOM
		const VDOM = <h1>Hello,React</h1> /* 此处一定不要写引号，因为不是字符串 */
		//2.渲染虚拟DOM到页面
		ReactDOM.render(VDOM,document.getElementById('test'))
	</script>
</body>
```

这样，就会在页面中的这个div容器上添加这个h1。

### 创建虚拟DOM的两种方式

#### 	js创建虚拟DOM(`不推荐`)

```HTML
<body>
	<!-- 准备好一个“容器” -->
	<div id="test"></div>

	<!-- 引入react核心库 -->
	<script type="text/javascript" src="../js/react.development.js"></script>
	<!-- 引入react-dom，用于支持react操作DOM -->
	<script type="text/javascript" src="../js/react-dom.development.js"></script>

	<script type="text/javascript" > 
		//1.创建虚拟DOM
		const VDOM = React.createElement('h1',{id:'title'},React.createElement('span',{},'Hello,React'))
		//2.渲染虚拟DOM到页面
		ReactDOM.render(VDOM,document.getElementById('test'))
	</script>
</body>
```

#### 	jsx创建虚拟DOM

```jsx
<body>
	<!-- 准备好一个“容器” -->
	<div id="test"></div>

	<!-- 引入react核心库 -->
	<script type="text/javascript" src="../js/react.development.js"></script>
	<!-- 引入react-dom，用于支持react操作DOM -->
	<script type="text/javascript" src="../js/react-dom.development.js"></script>
	<!-- 引入babel，用于将jsx转为js -->
	<script type="text/javascript" src="../js/babel.min.js"></script>

	<script type="text/babel" > /* 此处一定要写babel */
		//1.创建虚拟DOM
		const VDOM = (  /* 此处一定不要写引号，因为不是字符串 */
			<h1 id="title">
				<span>Hello,React</span>
			</h1>
		)
		//2.渲染虚拟DOM到页面
		ReactDOM.render(VDOM,document.getElementById('test'))
	</script>
</body>
```

可以看到，上下两种方式，明显`jsx`的写法更符合我们的习惯,当出现多重嵌套时,js创建方法会使我们编程出现很大麻烦

但是jsx其实也只是帮我们做了一层编译,当我们写完jsx代码后,最终我们的代码也会被编译成js的书写方式

### 关于虚拟DOM

本质：**Object类型的对象(一般对象)**

虚拟DOM比较'轻',真实DOM比较'重',因为虚拟DOM是React内部在用,无需真实DOM上那么多的属性(只有React需要的属性)

虚拟DOM最终会被React转化为真实DOM,呈现在页面上

```html
<body>
	<!-- 准备好一个“容器” -->
	<div id="test"></div>
	<div id="demo"></div>

	<!-- 引入react核心库 -->
	<script type="text/javascript" src="../js/react.development.js"></script>
	<!-- 引入react-dom，用于支持react操作DOM -->
	<script type="text/javascript" src="../js/react-dom.development.js"></script>
	<!-- 引入babel，用于将jsx转为js -->
	<script type="text/javascript" src="../js/babel.min.js"></script>

	<script type="text/babel" > /* 此处一定要写babel */
		//1.创建虚拟DOM
		const VDOM = (  /* 此处一定不要写引号，因为不是字符串 */
			<h1 id="title">
				<span>Hello,React</span>
			</h1>
		)
		//2.渲染虚拟DOM到页面
		ReactDOM.render(VDOM,document.getElementById('test'))

		const TDOM = document.getElementById('demo')
		console.log('虚拟DOM',VDOM);
		console.log('真实DOM',TDOM);
		debugger;
		// console.log(typeof VDOM);
		// console.log(VDOM instanceof Object);
	</script>
</body>
```

## jsx语法规则

>JSX是一种JavaScript的语法扩展、是一种嵌入式的类似XML的语法,常应用于React架构中,但也不仅限于此.
>
>应该说JSX因React框架而流行,但也存在其他的实现.只要你够厉害,甚至能在单片机上实现(当然你要自己写出它的实现方式)

### 规则

* 定义虚拟DOM时,不要写`引号`

* 标签中混入JS表达式时要用`{}`
* 样式的类名指定不要用`class`,要用`className`
* 内联样式,要用`style={{key:value}}`的形式(`双{}代表对象,单{}代表表达式`)去写
* 只有一个**跟标签**(整个虚拟DOM在外层有且仅有一个容器包裹)
* 标签必须**闭合**
* 标签首字母
  * 若`小写字母开头`,则将该标签转为html中同名元素,若html中无该标签对应的同名元素,则`报错`
  * 若`大写字母开头`,react就去渲染对应组件,若组件没有定义,则`报错`

```react
const myId = 'aTgUiGu'
const myData = 'HeLlo,rEaCt'
//1.创建虚拟DOM
const VDOM = (
    <div>
        <h2 className="title" id={myId.toLowerCase()}>
            <span style={{color:'white',fontSize:'29px'}}>{myData.toLowerCase()}</span>
        </h2>
        <h2 className="title" id={myId.toUpperCase()}>
            <span style={{color:'white',fontSize:'29px'}}>{myData.toLowerCase()}</span>
        </h2>
        <input type="text"/>
    </div>
)
//2.渲染虚拟DOM到页面
ReactDOM.render(VDOM,document.getElementById('test'))
```

### 区分【js语句(代码)】与【js表达式】

* 表达式:一个表达式会产生一个值,可以放在任何一个需要值的地方

    下面这些都是表达式
  * a
  * a+b
  * demo(1)
  * arr.map()：map() 方法创建一个新数组，其结果是该数组中的每个元素都调用一个提供的函数后返回的结果。
  * function test(){}

* 语句:不能放在创建虚拟dom语句中
  * if(){}
  * for(){}
  * switch(){}

```react
//模拟一些数据
const data = ['Angular','React','Vue']
//1.创建虚拟DOM
const VDOM = (
    <div>
        <h1>前端js框架列表</h1>
        <ul>
            {
                data.map((item,index)=>{
                    return <li key={index}>{item}</li>
                })
            }
        </ul>
    </div>
)
//2.渲染虚拟DOM到页面
ReactDOM.render(VDOM,document.getElementById('test'))
```

## 组件与模块理解

### 模块与模块化

#### ① 模块

理解:向外提供特定功能的js程序,一般就是一个js文件

为什么要拆成模块:随着业务逻辑增加,代码越来越多且复杂

作用:复用js,简化js的编写,提高js运行效率

#### ② 模块化

当应用的js都以模块来编写,这个应用就是一个模块化的应用

### 组件与组件化

#### ① 组件

理解:用来实现局部功能效果的代码和资源的集合(html/css/js/img等等)

为什么要用组件:一个界面的功能复杂

作用:复用编码,简化项目编码,提高运行效率

#### ② 组件化

当应用是以多组件的方式实现,这个应用就是组件化的应用

## 两种组件定义区别

### ①函数式声明组件(适用于简单组件的定义)

```react
//1.创建函数式组件
function MyComponent(){
    console.log(this); //此处的this是undefined，因为babel编译后开启了严格模式
    return <h2>我是用函数定义的组件(适用于【简单组件】的定义)</h2>
}
//2.渲染组件到页面
ReactDOM.render(<MyComponent/>,document.getElementById('test'))
```

执行了`ReactDOM.render(<MyComponent/>.......)`之后，发生了什么？

* React解析组件标签，找到了MyComponent组件。
* 发现组件是使用函数定义的，随后调用该函数，将返回的虚拟DOM转为真实DOM，随后呈现在页面中。

### ②类式组件(适用于复杂组件的定义，复杂：有状态 state)

```react
//1.创建类式组件
class MyComponent extends React.Component {
    render(){
        //render是放在哪里的？—— MyComponent的原型对象上，供实例使用。
        //render中的this是谁？—— MyComponent的实例对象 <=> MyComponent组件实例对象。
        console.log('render中的this:',this);
        return <h2>我是用类定义的组件(适用于【复杂组件】的定义)</h2>
    }
}
//2.渲染组件到页面
ReactDOM.render(<MyComponent/>,document.getElementById('test'))
```

执行了`ReactDOM.render(<MyComponent/>.......)`之后，发生了什么？

* React解析组件标签，找到了MyComponent组件。

* 发现组件是使用类定义的，随后new出来该类的实例，并通过该实例调用到原型上的render方法。

* 将render返回的虚拟DOM转为真实DOM，随后呈现在页面中。

组件中的`render`是放在哪里的？

​	**MyComponent的原型对象上，供实例使用。**

组件中的`render`中的`this`是谁？

​	**MyComponent的实例对象 <=> MyComponent组件实例对象。**

### 补充：类的复习

* 类中的构造器不是必须要写的，要对实例进行一些初始化的操作，如添加指定属性时才写。

* 如果A类继承了B类，且A类中写了构造器，那么A类构造器中的super是必须要调用的。

* 类中所定义的方法，都放在了类的原型对象上，供实例去使用。

```js
//创建一个Person类
class Person {
    //构造器方法
    constructor(name,age){
        //构造器中的this是谁？—— 类的实例对象
        this.name = name
        this.age = age
    }
    //一般方法
    speak(){
        //speak方法放在了哪里？——类的原型对象上，供实例使用
        //通过Person实例调用speak时，speak中的this就是Person实例
        console.log(`我叫${this.name}，我年龄是${this.age}`);
    }
}

//创建一个Student类，继承于Person类
class Student extends Person {
    constructor(name,age,grade){
        super(name,age)
        this.grade = grade
        this.school = '尚硅谷'
    }
    //重写从父类继承过来的方法
    speak(){
        console.log(`我叫${this.name}，我年龄是${this.age},我读的是${this.grade}年级`);
        this.study()
    }
    study(){
        //study方法放在了哪里？——类的原型对象上，供实例使用
        //通过Student实例调用study时，study中的this就是Student实例
        console.log('我很努力的学习');
    }
}

class Car {
    constructor(name,price){
        this.name = name
        this.price = price
        // this.wheel = 4
    }
    //类中可以直接写赋值语句,如下代码的含义是：给Car的实例对象添加一个属性，名为a，值为1
    a = 1
	wheel = 4
	static demo = 100
}
const c1 = new Car('奔驰c63',199)
console.log(c1);
console.log(Car.demo);
```

## React面向组件编程

* 使用React开发者工具调试

  `React Developer Tools`

* 注意
  * 组件名必须是首字母大写
  * 虚拟DOM元素只能有一个根元素
  * 虚拟DOM元素必须有结束标签 < />

* 渲染类组件标签的基本流程
  * React内部会创建组件实例对象
  * 调用render()得到虚拟DOM,并解析为真实DOM
  * 插入到指定的页面元素内部

### 组件（实例）三大属性:state

#### ① 理解

`state`是组件对象最重要的属性,值是对象(可以包含多个key:value的组合)

组件被称为`状态机`,通过更新组件的`state`来更新对应的页面显示(重新渲染组件)

#### ② 强烈注意

组件中的**render方法中的this为组件实例对象**

组件自定义方法中this为undefined,如何解决?

  a) 强制绑定this:通过函数对象的`bind()`

  b) 箭头函数`推荐`

状态数据,不能直接修改或者更新

#### ③代码示例

##### 正常的用函数对象的bind()

```jsx
//1.创建组件
class Weather extends React.Component{
    //构造器调用几次？ ———— 1次
    constructor(props){
        console.log('constructor');
        super(props)
        //初始化状态
        this.state = {isHot:false,wind:'微风'}
        //解决changeWeather中this指向问题,也可以在调用出直接使用
        this.changeWeather = this.changeWeather.bind(this)
    }
    //render调用几次？ ———— 1+n次 1是初始化的那次 n是状态更新的次数
    render(){
        console.log('render');
        //读取状态
        const {isHot,wind} = this.state
        return <h1 onClick={this.changeWeather}>今天天气很{isHot ? '炎热' : '凉爽'}，{wind}</h1>
    }
    //changeWeather调用几次？ ———— 点几次调几次
    changeWeather(){
        //changeWeather放在哪里？ ———— Weather的原型对象上，供实例使用
        //由于changeWeather是作为onClick的回调，所以不是通过实例调用的，是直接调用
        //类中的方法默认开启了局部的严格模式，所以changeWeather中的this为undefined
        console.log('changeWeather');
        //获取原来的isHot值
        const isHot = this.state.isHot
        //严重注意：状态必须通过setState进行更新,且更新是一种合并，不是替换。
        this.setState({isHot:!isHot})
        console.log(this);

        //严重注意：状态(state)不可直接更改，下面这行就是直接更改！！！
        //this.state.isHot = !isHot //这是错误的写法
    }
}
//2.渲染组件到页面
ReactDOM.render(<Weather/>,document.getElementById('test'))
```

##### 简写方式:赋值语句的形式+箭头函数

```jsx
//1.创建组件
class Weather extends React.Component{
	//初始化状态
	state = {isHot:false,wind:'微风'}

	render(){
		const {isHot,wind} = this.state
		return <h1 onClick={this.changeWeather}>今天天气很{isHot ? '炎热' : '凉爽'}，{wind}</h1>
	}

	//自定义方法————要用赋值语句的形式+箭头函数
	changeWeather = ()=>{
		const isHot = this.state.isHot
		this.setState({isHot:!isHot})
	}
}
//2.渲染组件到页面
ReactDOM.render(<Weather/>,document.getElementById('test'))
```

#### 补充：

##### 原生事件绑定

```js
<button id="btn1">按钮1</button>
<button id="btn2">按钮2</button>
<button onclick="demo()">按钮3</button>

<script type="text/javascript" >
	const btn1 = document.getElementById('btn1')
	btn1.addEventListener('click',()=>{
		alert('按钮1被点击了')
	})

	const btn2 = document.getElementById('btn2')
	btn2.onclick = ()=>{
		alert('按钮2被点击了')
	}

	function demo(){
		alert('按钮3被点击了')
	}

</script>
```

##### 类方法中的this指向

```js
class Person {
    constructor(name,age){
        this.name = name
        this.age = age
    }
    study(){
        //study方法放在了哪里？——类的原型对象上，供实例使用
        //通过Person实例调用study时，study中的this就是Person实例
        console.log(this);
    }
}

const p1 = new Person('tom',18)
p1.study() //通过实例调用study方法
const x = p1.study
x()

```

### 组件（实例）三大属性:props

#### ①理解

1. 每个组件对象都会有`props(properties的简写)`属性
2. 组件标签的所有属性都保存在`props`中

#### ② 作用

1. 通过标签属性从组件外向组件内传递变化的数据
2. 注意:组件内部不要修改props数据

#### ③代码示例:

##### 类组件使用props

```js
<!-- 引入prop-types，用于对组件标签属性进行限制 -->
<script type="text/javascript" src="../js/prop-types.js"></script>

<script type="text/babel">
	//创建组件
	class Person extends React.Component{
		render(){
			// console.log(this);
			const {name,age,sex} = this.props
			//props是只读的
			//this.props.name = 'jack' //此行代码会报错，因为props是只读的
			return (
				<ul>
					<li>姓名：{name}</li>
					<li>性别：{sex}</li>
					<li>年龄：{age+1}</li>
				</ul>
			)
		}
	}
	//对标签属性进行类型、必要性的限制
	Person.propTypes = {
		name:PropTypes.string.isRequired, //限制name必传，且为字符串
		sex:PropTypes.string,//限制sex为字符串
		age:PropTypes.number,//限制age为数值
		speak:PropTypes.func,//限制speak为函数
	}
	//指定默认标签属性值
	Person.defaultProps = {
		sex:'男',//sex默认值为男
		age:18 //age默认值为18
	}
	//渲染组件到页面
	ReactDOM.render(<Person name={100} speak={speak}/>,document.getElementById('test1'))
	ReactDOM.render(<Person name="tom" age={18} sex="女"/>,document.getElementById('test2'))

	const p = {name:'老刘',age:18,sex:'女'}
	// console.log('@',...p);
	// ReactDOM.render(<Person name={p.name} age={p.age} sex={p.sex}/>,document.getElementById('test3'))
	ReactDOM.render(<Person {...p}/>,document.getElementById('test3'))

	function speak(){
		console.log('我说话了');
	}
</script>
```

**简写**

```jsx
//创建组件
class Person extends React.Component{

	constructor(props){
		//构造器是否接收props，是否传递给super，取决于：是否希望在构造器中通过this访问props
		// console.log(props);
		super(props)
		console.log('constructor',this.props);
	}

	//对标签属性进行类型、必要性的限制
	static propTypes = {
		name:PropTypes.string.isRequired, //限制name必传，且为字符串
		sex:PropTypes.string,//限制sex为字符串
		age:PropTypes.number,//限制age为数值
	}

	//指定默认标签属性值
	static defaultProps = {
		sex:'男',//sex默认值为男
		age:18 //age默认值为18
	}
	
	render(){
		// console.log(this);
		const {name,age,sex} = this.props
		//props是只读的
		//this.props.name = 'jack' //此行代码会报错，因为props是只读的
		return (
			<ul>
				<li>姓名：{name}</li>
				<li>性别：{sex}</li>
				<li>年龄：{age+1}</li>
			</ul>
		)
	}
}

//渲染组件到页面
ReactDOM.render(<Person name="jerry"/>,document.getElementById('test1'))
```

##### 函数组件使用props

```jsx
//创建组件
function Person (props){
	const {name,age,sex} = props
	return (
			<ul>
				<li>姓名：{name}</li>
				<li>性别：{sex}</li>
				<li>年龄：{age}</li>
			</ul>
		)
}
Person.propTypes = {
	name:PropTypes.string.isRequired, //限制name必传，且为字符串
	sex:PropTypes.string,//限制sex为字符串
	age:PropTypes.number,//限制age为数值
}

//指定默认标签属性值
Person.defaultProps = {
	sex:'男',//sex默认值为男
	age:18 //age默认值为18
}
//渲染组件到页面
ReactDOM.render(<Person name="jerry"/>,document.getElementById('test1'))
	
```

#### 补充：展开运算符

```js
let arr1 = [1,3,5,7,9]
let arr2 = [2,4,6,8,10]
console.log(...arr1); //展开一个数组
let arr3 = [...arr1,...arr2]//连接数组

//在函数中使用
function sum(...numbers){
    return numbers.reduce((preValue,currentValue)=>{
        return preValue + currentValue
    })
}
console.log(sum(1,2,3,4));

//构造字面量对象时使用展开语法
let person = {name:'tom',age:18}
let person2 = {...person}
//console.log(...person); //报错，展开运算符不能展开对象
person.name = 'jerry'
console.log(person2);
console.log(person);

//合并
let person3 = {...person,name:'jack',address:"地球"}
console.log(person3);
```

### 组件（实例）三大属性:refs

#### ① 理解

组件内的标签可以定义ref来标识自己

#### ② 代码示例:

##### 字符串形式的ref(`不推荐,将被淘汰`)

```jsx
//创建组件
class Demo extends React.Component{
	//展示左侧输入框的数据
	showData = ()=>{
		const {input1} = this.refs
		alert(input1.value)
	}
	//展示右侧输入框的数据
	showData2 = ()=>{
		const {input2} = this.refs
		alert(input2.value)
	}
	render(){
		return(
			<div>
				<input ref="input1" type="text" placeholder="点击按钮提示数据"/>&nbsp;
				<button onClick={this.showData}>点我提示左侧的数据</button>&nbsp;
				<input ref="input2" onBlur={this.showData2} type="text" placeholder="失去焦点提示数据"/>
			</div>
		)
	}
}
//渲染组件到页面
ReactDOM.render(<Demo a="1" b="2"/>,document.getElementById('test'))
```

##### 回调形式的ref

```jsx
//创建组件
class Demo extends React.Component{
	//展示左侧输入框的数据
	showData = ()=>{
		const {input1} = this
		alert(input1.value)
	}
	//展示右侧输入框的数据
	showData2 = ()=>{
		const {input2} = this
		alert(input2.value)
	}
	render(){
		return(
			<div>
				<input ref={c => this.input1 = c } type="text" placeholder="点击按钮提示数据"/>&nbsp;
				<button onClick={this.showData}>点我提示左侧的数据</button>&nbsp;
				<input onBlur={this.showData2} ref={c => this.input2 = c } type="text" placeholder="失去焦点提示数据"/>&nbsp;
			</div>
		)
	}
}
//渲染组件到页面
ReactDOM.render(<Demo a="1" b="2"/>,document.getElementById('test'))
```

##### createRef创建ref容器`最推荐的`

```jsx
//创建组件
class Demo extends React.Component{
	/* 
		React.createRef调用后可以返回一个容器，该容器可以存储被ref所标识的节点,该容器是“专人专用”的
		*/
	myRef = React.createRef()
	myRef2 = React.createRef()
	//展示左侧输入框的数据
	showData = ()=>{
		alert(this.myRef.current.value);
	}
	//展示右侧输入框的数据
	showData2 = ()=>{
		alert(this.myRef2.current.value);
	}
	render(){
		return(
			<div>
				<input ref={this.myRef} type="text" placeholder="点击按钮提示数据"/>&nbsp;
				<button onClick={this.showData}>点我提示左侧的数据</button>&nbsp;
				<input onBlur={this.showData2} ref={this.myRef2} type="text" placeholder="失去焦点提示数据"/>&nbsp;
			</div>
		)
	}
}
//渲染组件到页面
ReactDOM.render(<Demo a="1" b="2"/>,document.getElementById('test'))
```

### 事件处理与收集表单数据

#### 事件处理

* 通过`onXxx`属性指定事件处理函数(注意大小写)
  * React使用的是**自定义(合成)事件,而不是使用的原生DOM事件**----为了更好的**兼容性**
  * React中的事件是通过**事件委托**的方式处理的(委托给组件最外层的元素)----为了更**高效**

* 通过`event.target`得到发生事件的DOM元素对象 -----**不要过度使用ref**

```jsx
//创建组件
class Demo extends React.Component{
	//创建ref容器
	myRef = React.createRef()
	myRef2 = React.createRef()

	//展示左侧输入框的数据
	showData = (event)=>{
		console.log(event.target);
		alert(this.myRef.current.value);
	}

	//展示右侧输入框的数据
	showData2 = (event)=>{
		alert(event.target.value);
	}

	render(){
		return(
			<div>
				<input ref={this.myRef} type="text" placeholder="点击按钮提示数据"/>&nbsp;
				<button onClick={this.showData}>点我提示左侧的数据</button>&nbsp;
				<input onBlur={this.showData2} type="text" placeholder="失去焦点提示数据"/>&nbsp;
			</div>
		)
	}
}
//渲染组件到页面
ReactDOM.render(<Demo a="1" b="2"/>,document.getElementById('test'))
```

#### 表单组件的分类

就形式上来说，**`受控组件`就是为某个form表单组件添加`value`属性；`非受控组件`就是没有添加`value`属性的组件**

##### 受控组件

```jsx
//创建组件
class Login extends React.Component{

	//初始化状态
	state = {
		username:'', //用户名
		password:'' //密码
	}

	//保存用户名到状态中
	saveUsername = (event)=>{
		this.setState({username:event.target.value})
	}

	//保存密码到状态中
	savePassword = (event)=>{
		this.setState({password:event.target.value})
	}

	//表单提交的回调
	handleSubmit = (event)=>{
		event.preventDefault() //阻止表单提交
		const {username,password} = this.state
		alert(`你输入的用户名是：${username},你输入的密码是：${password}`)
	}

	render(){
		return(
			<form onSubmit={this.handleSubmit}>
				用户名：<input onChange={this.saveUsername} type="text" name="username"/>
				密码：<input onChange={this.savePassword} type="password" name="password"/>
				<button>登录</button>
			</form>
		)
	}
}
//渲染组件
ReactDOM.render(<Login/>,document.getElementById('test'))
```

##### 非受控组件(现用现取)

```jsx
//创建组件
class Login extends React.Component{
	handleSubmit = (event)=>{
		event.preventDefault() //阻止表单提交
		const {username,password} = this
		alert(`你输入的用户名是：${username.value},你输入的密码是：${password.value}`)
	}
	render(){
		return(
			<form onSubmit={this.handleSubmit}>
				用户名：<input ref={c => this.username = c} type="text" name="username"/>
				密码：<input ref={c => this.password = c} type="password" name="password"/>
				<button>登录</button>
			</form>
		)
	}
}
//渲染组件
ReactDOM.render(<Login/>,document.getElementById('test'))
```

### 高阶函数与函数柯里化

#### 高阶函数:

如果一个函数符合下面两个规范中的任何一个,那该函数就是高阶函数

1. 若A函数,接受的参数是一个函数,那么A就可以称之为高阶函数
2. 若A函数,调用的返回值依然是一个函数,那么A就可以称之为高阶函数

常见的高阶函数有:`Promise`、`setTimeout`、`arr.map()`等等 

```jsx
//创建组件
class Login extends React.Component{
	//初始化状态
	state = {
		username:'', //用户名
		password:'' //密码
	}

	//保存表单数据到状态中
	saveFormData = (dataType)=>{
		return (event)=>{
			this.setState({[dataType]:event.target.value})
		}
	}

	//表单提交的回调
	handleSubmit = (event)=>{
		event.preventDefault() //阻止表单提交
		const {username,password} = this.state
		alert(`你输入的用户名是：${username},你输入的密码是：${password}`)
	}
	render(){
		return(
			<form onSubmit={this.handleSubmit}>
				用户名：<input onChange={this.saveFormData('username')} type="text" name="username"/>
				密码：<input onChange={this.saveFormData('password')} type="password" name="password"/>
				<button>登录</button>
			</form>
		)
	}
}
//渲染组件
ReactDOM.render(<Login/>,document.getElementById('test'))
```

#### 函数的柯里化

通过函数调用继续返回函数的方式,实现对此接受参数最后统一处理的函数编码形式

```js
<script type="text/javascript" >
	/* function sum(a,b,c){
		return a+b+c
	} */
	
	function sum(a){
		return(b)=>{
			return (c)=>{
				return a+b+c
			}
		}
	}
	const result = sum(1)(2)(3)
	console.log(result);
</script>
```

```jsx
//保存表单数据到状态中
saveFormData = (dataType)=>{
    return (event)=>{
        this.setState({[dataType]:event.target.value})
    }
}
```

## 生命周期

组件从创建到死亡它会经历一些特定的阶段

React组件中包含一系列钩子函数(生命周期回调函数),会在特定的时刻调用

我们在定义组件时,会在特定的生命周期回调函数中,做特定的工作

```jsx
//创建组件
//生命周期回调函数 <=> 生命周期钩子函数 <=> 生命周期函数 <=> 生命周期钩子
class Life extends React.Component{

	state = {opacity:1}

	death = ()=>{
		//卸载组件
		ReactDOM.unmountComponentAtNode(document.getElementById('test'))
	}

	//组件挂完毕
	componentDidMount(){
		console.log('componentDidMount');
		this.timer = setInterval(() => {
			//获取原状态
			let {opacity} = this.state
			//减小0.1
			opacity -= 0.1
			if(opacity <= 0) opacity = 1
			//设置新的透明度
			this.setState({opacity})
		}, 200);
	}

	//组件将要卸载
	componentWillUnmount(){
		//清除定时器
		clearInterval(this.timer)
	}

	//初始化渲染、状态更新之后
	render(){
		console.log('render');
		return(
			<div>
				<h2 style={{opacity:this.state.opacity}}>React学不会怎么办？</h2>
				<button onClick={this.death}>不活了</button>
			</div>
		)
	}
}
//渲染组件
ReactDOM.render(<Life/>,document.getElementById('test'))
```

### React生命周期(旧)

[![5W43VK.png](https://z3.ax1x.com/2021/10/24/5W43VK.png)](https://imgtu.com/i/5W43VK)

各个生命周期钩子调用顺序

1. 初始化阶段:由`ReactDOM.render()`触发 --初次渲染

     - `constructor()`

     - `compinentWillMount()`

     - `render()`

     - `componentDidMount()` ==>`常用` 组件将要渲染

     一般在这个钩子中做一些初始化的事情,如:**开启定时器,发送网络请求,订阅消息**等

2. 更新阶段:由组件内部的`this.setState()`或者`父组件的render`触发

     - `shouldComponentUpdate()` 组件应该更新
     - `componentWillUpdate()` 组件将要更新
     - `render()`   ===>`必须使用`的一个
     - `componentDidUpdate()` 组件将要更新

3. 卸载组件:由`ReactDOM.unmountComponentAtNode`(`卸载节点上的组件`)触发

     - `componentWillUnmount()` ===>`常用` 组件将要卸载

     一般在这个钩子中做一些首位的事情,如:**关闭定时器,取消订阅**等

### React生命周期(新)

[![5W4MK1.png](https://z3.ax1x.com/2021/10/24/5W4MK1.png)](https://imgtu.com/i/5W4MK1)

1. 初始化阶段:由`ReactDOM.render()`触发 ---初次渲染

     - `constructor()`
     - `getDerivedStateFromProps()` 从Props获得派生状态
     - `render()`
     - `componentDidMount()` ====>`常用` 

2. 更新阶段:由组件内部的`this.setState()`或者`父组件的render`触发

     - `getDerivedStateFromProps()`  从Props获得派生状态
     - `shouldComponentUpdate()` 组件应该更新
     - `render()`
     - `getSnapshotBeforeUpdate()` 在更新前获得快照
     - `componentDidUpdate()`

3. 卸载组件:由`ReactDOM.unmountComponentAtNode()`触发

     - componentWillUnmount() ===>`常用`


### 重要的钩子

1. `render`:初始化渲染或者更新渲染调用
2. `componentDidMount()` :开启监听,发送ajax请求
3. `componentWillUnmount()`: 做一些收尾工作,如:清理定时器

### 即将废弃的钩子

1. `componentWillMount`
2. `componentWillReceiveProps`
3. `componentWillUpdate`

`ps`:现在使用会出现警告,之后版本可能需要加上`UNSAFE_`前缀才能使用,以后可能会被彻底废弃,不建议使用

推测React团队认为提高使用成本将会间接影响我们,让我们去适应新的钩子,所以加上这个

## react/vue中的key

> 经典面试题:
>
> 1). react/vue中的key有什么作用？（key的内部原理是什么？）
>
> 2). 为什么遍历列表时，key最好不要用index?

**虚拟DOM中key的作用：**

* 简单的说: key是虚拟DOM对象的标识, 在更新显示时key起着极其重要的作用。

* 详细的说: 当状态中的数据发生变化时，react会根据**新数据**生成**新的虚拟DOM,** 随后React进行**新虚拟DOM**与**旧虚拟DOM**的diff比较，比较规则如下：

  * 旧虚拟DOM中找到了与新虚拟DOM相同的key：
    * 若虚拟DOM中内容没变, 直接使用之前的真实DOM
    * 若虚拟DOM中内容变了, 则生成新的真实DOM，随后替换掉页面中之前的真实DOM

  * 旧虚拟DOM中未找到与新虚拟DOM相同的key
    * 根据数据创建新的真实DOM，随后渲染到到页面

**用index作为key可能会引发的问题：**

* 若对数据进行：逆序添加、逆序删除等破坏顺序操作：会产生没有必要的真实DOM更新 ==> 界面效果没问题, 但效率低。

* 如果结构中还包含输入类的DOM：会产生错误DOM更新 ==> 界面有问题。

* 注意！如果不存在对数据的逆序添加、逆序删除等破坏顺序操作，仅用于渲染列表用于展示，使用index作为key是没有问题的。

**开发中如何选择key?:**

* 最好使用每条数据的唯一标识作为key, 比如id、手机号、身份证号、学号等唯一值。

* 如果确定只是简单的展示数据，用index也是可以的。

```json
//慢动作回放----使用index索引值作为key
		初始数据：
				{id:1,name:'小张',age:18},
				{id:2,name:'小李',age:19},
		初始的虚拟DOM：
				<li key=0>小张---18<input type="text"/></li>
				<li key=1>小李---19<input type="text"/></li>

		更新后的数据：
				{id:3,name:'小王',age:20},
				{id:1,name:'小张',age:18},
				{id:2,name:'小李',age:19},
		更新数据后的虚拟DOM：
				<li key=0>小王---20<input type="text"/></li>
				<li key=1>小张---18<input type="text"/></li>
				<li key=2>小李---19<input type="text"/></li>

-----------------------------------------------------------------

//慢动作回放----使用id唯一标识作为key

		初始数据：
				{id:1,name:'小张',age:18},
				{id:2,name:'小李',age:19},
		初始的虚拟DOM：
				<li key=1>小张---18<input type="text"/></li>
				<li key=2>小李---19<input type="text"/></li>

		更新后的数据：
				{id:3,name:'小王',age:20},
				{id:1,name:'小张',age:18},
				{id:2,name:'小李',age:19},
		更新数据后的虚拟DOM：
				<li key=3>小王---20<input type="text"/></li>
				<li key=1>小张---18<input type="text"/></li>
				<li key=2>小李---19<input type="text"/></li>
```

# React脚手架

* xxx脚手架:用来帮助程序原快速创建一个基于xxx库的模板项目
  * 包含了所有需要的配置(语法检查,jsx编 译,devServer...)
  * 下载好了所有相关的依赖
  * 可以直接运行一个简单效果
* react提供了一个用于创建react项目的脚手架库:`create-react-app`
* 项目的整体技术架构为:`react+webpack+es6+eslint`
* 使用脚手架开发的项目的特点:模块化,组件化,工程化

## 创建项目并启动

* 全局安装:`npm i -g create-react-app`
* 切换到想创建项目的目录,使用命令:`create-react-app hello-react`
* 进入项目文件夹
* 启动项目:`npm start` `yarn start`

## react脚手架项目结构

> public ---- 静态资源文件夹
>
> ​            favicon.icon ------ 网站页签图标
>
> ​            index.html -------- 主页面
>
> ​            logo192.png ------- logo图
>
> ​            logo512.png ------- logo图
>
> ​            manifest.json ----- 应用加壳的配置文件
>
> ​            robots.txt -------- 爬虫协议文件
>
> src ---- 源码文件夹
>
> ​            App.css -------- App组件的样式
>
> ​            App.js --------- App组件
>
> ​            App.test.js ---- 用于给App做测试
>
> ​            index.css ------ 样式
>
> ​            index.js ------- 入口文件
>
> ​            logo.svg ------- logo图
>
> ​            reportWebVitals.js
>
> ​                    --- 页面性能分析文件(需要web-vitals库的支持)
>
> ​            setupTests.js
>
> ​                    ---- 组件单元测试的文件(需要jest-dom库的支持)

## 功能界面的组件化编码流程

* 拆分组件: 拆分界面,抽取组件

* 实现静态组件: 使用组件实现静态页面效果

* 实现动态组件
  * 动态显示初始化数据
    * 数据类型
    * 数据名称
    * 保存在哪个组件?
  * 交互(从绑定事件监听开始)

## TodoList案例

### 总结

**拆分组件、实现静态组件**

注意：className、style的写法

* 样式的类名指定不要用`class`,要用`className`
* 内联样式,要用`style={{key:value}}`的形式(`双{}代表对象,单{}代表表达式`)去写

**动态初始化列表，如何确定将数据放在哪个组件的state中？**

* 某个组件使用：放在其自身的`state`中

* 某些组件使用：放在他们共同的父组件`state`中（官方称此操作为：**状态提升**）

**关于父子之间通信：**

* 【父组件】给【子组件】传递数据：通过`props`传递

* 【子组件】给【父组件】传递数据：通过`props`传递，**要求父提前给子传递一个函数**

父组件

```jsx
render() {
	const {todos} = this.state
	return (
		<div className="todo-container">
			<div className="todo-wrap">
				<Header addTodo={this.addTodo}/>
				<List todos={todos} updateTodo={this.updateTodo} deleteTodo={this.deleteTodo}/>
				<Footer todos={todos} checkAllTodo={this.checkAllTodo} clearAllDone={this.clearAllDone}/>
			</div>
		</div>
	)
}
```

子组件

```jsx
//对接收的props进行：类型、必要性的限制
static propTypes = {
	addTodo:PropTypes.func.isRequired
}

//键盘事件的回调
handleKeyUp = (event)=>{
	//解构赋值获取keyCode,target
	const {keyCode,target} = event
	//判断是否是回车按键
	if(keyCode !== 13) return
	//添加的todo名字不能为空
	if(target.value.trim() === ''){
		alert('输入不能为空')
		return
	}
	//准备好一个todo对象
	const todoObj = {id:nanoid(),name:target.value,done:false}
	//将todoObj传递给App
	this.props.addTodo(todoObj)
	//清空输入
	target.value = ''
}

render() {
	return (
		<div className="todo-header">
			<input onKeyUp={this.handleKeyUp} type="text" placeholder="请输入你的任务名称，按回车键确认"/>
		</div>
	)
}
```

**注意defaultChecked 和 checked的区别，类似的还有：defaultValue 和 value**

`defaultChecked`只在初次渲染时生效，更新时不受控制

`checked`始终受到控制，必须通过绑定 `onChange` 事件来控制选中情况

```jsx
//勾选、取消勾选某一个todo的回调
handleCheck = (id)=>{
    return (event)=>{
        this.props.updateTodo(id,event.target.checked)
    }
}

render() {
    const {id,name,done} = this.props
    const {mouse} = this.state
    return (
        <li style={{backgroundColor:mouse ? '#ddd' : 'white'}} onMouseEnter={this.handleMouse(true)} onMouseLeave={this.handleMouse(false)}>
            <label>
                <input type="checkbox" checked={done} onChange={this.handleCheck(id)}/>
                <span>{name}</span>
            </label>
            <button onClick={()=> this.handleDelete(id) } className="btn btn-danger" style={{display:mouse?'block':'none'}}>删除</button>
        </li>
    )
}
```

**状态在哪里，操作状态的方法就在哪里**

```jsx
//状态在哪里，操作状态的方法就在哪里

//初始化状态
state = {todos:[
    {id:'001',name:'吃饭',done:true},
    {id:'002',name:'睡觉',done:true},
    {id:'003',name:'打代码',done:false},
    {id:'004',name:'逛街',done:false}
]}

//addTodo用于添加一个todo，接收的参数是todo对象
addTodo = (todoObj)=>{
    //获取原todos
    const {todos} = this.state
    //追加一个todo
    const newTodos = [todoObj,...todos]
    //更新状态
    this.setState({todos:newTodos})
}

//updateTodo用于更新一个todo对象
updateTodo = (id,done)=>{
    //获取状态中的todos
    const {todos} = this.state
    //匹配处理数据
    const newTodos = todos.map((todoObj)=>{
        if(todoObj.id === id) return {...todoObj,done}
        else return todoObj
    })
    this.setState({todos:newTodos})
}

//deleteTodo用于删除一个todo对象
deleteTodo = (id)=>{
    //获取原来的todos
    const {todos} = this.state
    //删除指定id的todo对象
    const newTodos = todos.filter((todoObj)=>{
        return todoObj.id !== id
    })
    //更新状态
    this.setState({todos:newTodos})
}

//checkAllTodo用于全选
checkAllTodo = (done)=>{
    //获取原来的todos
    const {todos} = this.state
    //加工数据
    const newTodos = todos.map((todoObj)=>{
        return {...todoObj,done}
    })
    //更新状态
    this.setState({todos:newTodos})
}

//clearAllDone用于清除所有已完成的
clearAllDone = ()=>{
    //获取原来的todos
    const {todos} = this.state
    //过滤数据
    const newTodos = todos.filter((todoObj)=>{
        return !todoObj.done
    })
    //更新状态
    this.setState({todos:newTodos})
}
```

### 补充

#### uuid

nanoid库和uuid库一样都可以生成**通用唯一识别码（Universally Unique Identifier）**，但是nanoid相比uuid要更轻量级。

`yarn add nanoid`

```jsx
import {nanoid} from 'nanoid'

const todoObj = {id:nanoid(),name:target.value,done:false}
```

#### 类型、必要性的限制

`yarn add prop-types`

```jsx
import PropTypes from 'prop-types'

//对接收的props进行：类型、必要性的限制
static propTypes = {
    todos:PropTypes.array.isRequired,
    updateTodo:PropTypes.func.isRequired,
    deleteTodo:PropTypes.func.isRequired,
}
```

#### 更新数据

更新时可以利用赋值解构后再传入重复字段会自动覆盖的方式进行更新数据 `done:done=>done`

```jsx
//updateTodo用于更新一个todo对象
updateTodo = (id,done)=>{
	//获取状态中的todos
	const {todos} = this.state
	//匹配处理数据
	const newTodos = todos.map((todoObj)=>{
		if(todoObj.id === id) return {...todoObj,done}
		else return todoObj
	})
	this.setState({todos:newTodos})
}
```

#### 删除数据

可以用filter过滤实现

```js
//deleteTodo用于删除一个todo对象
deleteTodo = (id)=>{
	//获取原来的todos
	const {todos} = this.state
	//删除指定id的todo对象
	const newTodos = todos.filter((todoObj)=>{
		return todoObj.id !== id
	})
	//更新状态
	this.setState({todos:newTodos})
}
```

`map`接受一个函数作为参数，不改变原来的数组，只是返回一个全新的数组

`reduce`也是返回一个全新的数组。reduce接受一个函数作为参数，这个函数要有两个形参，代表数组中的前两项，reduce会将这个函数的结果与数组中的第三项再次组成这个函数的两个形参以此类推进行累积操作

`filter`返回过滤后的数组。filter也接收一个函数作为参数，这个函数将作用于数组中的每个元素，根据该函数每次执行后返回的布尔值来保留结果，如果是true就保留，如果是false就过滤掉（这点与map要区分）

# React Ajax

> 安装axios:`yarn add axios`
>

## React中配置代理

* 方法一::在`package.json`中追加如下配置 :`"proxy":http://localhost:5000`
  * ps:当你请求`http://localhost:5000`产生跨域(本身在3000端口)时,添加此代码, 之后你请求时用`http://localhost:3000`进行请求,当其在`3000`端口中找不到资源时将会自动转发至`5000`端口进行请求,不产生跨域问题
  * 优点：配置简单，前端请求资源时可以不加任何前缀。
  * 缺点：不能配置多个代理
  * 工作方式：上述方式配置代理，当请求了3000不存在的资源时，那么该请求会转发给5000 （优先匹配前端资源）

```jsx
export default class App extends Component {
    getStudentData = () => {
        axios.get('http://localhost:3000/students').then(
            response => {console.log('成功了',response.data);},
            error=>{console.log('失败了',error);}
        )
    }
    render() {
        return (
            <div>
                <button onClick= {this.getStudentData}>点我获取学生数据</button>
            </div>
        )
    }
}
```

* 方法二: 在`src`下创建配置文件：`src/setupProxy.js`
  * ps:必须是这个文件名,react项目运行的时候会自动查找这个文件,并将其加入webpack的配置中,所以当你修改此文件后,你需要重新启动项目
  * 优点：可以配置多个代理，可以灵活的控制请求是否走代理。
  * 缺点：配置繁琐，前端请求资源时必须加前缀。

```js
//代码示例
const proxy = require('http-proxy-middleware')
 module.exports = function(app) {
   app.use(
     proxy('/api1', {  //api1是需要转发的请求(所有带有/api1前缀的请求都会转发给5000)
       target: 'http://localhost:5000', //配置转发目标地址(能返回数据的服务器地址)
       changeOrigin: true, //控制服务器接收到的请求头中host字段的值
       /*
       	changeOrigin设置为true时，服务器收到的请求头中的host为：localhost:5000
       	changeOrigin设置为false时，服务器收到的请求头中的host为：localhost:3000
       	changeOrigin默认值为false，但我们一般将changeOrigin值设为true
       */
       pathRewrite: {'^/api1': ''} //去除请求前缀，保证交给后台服务器的是正常请求地址(必须配置)
     }),
     proxy('/api2', { 
       target: 'http://localhost:5001',
       changeOrigin: true,
       pathRewrite: {'^/api2': ''}
     })
   )
}
//App.jsx
export default class App extends Component {
    getStudentData = ()=>{
		axios.get('http://localhost:3000/api1/students').then(
			response => {console.log('成功了',response.data);},
			error => {console.log('失败了',error);}
		)
	}

	getCarData = ()=>{
		axios.get('http://localhost:3000/api2/cars').then(
			response => {console.log('成功了',response.data);},
			error => {console.log('失败了',error);}
		)
	}
    render() {
        return (
            <div>
                <button onClick= {this.getStudentData}>点我获取学生数据</button>
                <button onClick={this.getCarData}>点我获取汽车数据</button>
            </div>
        )
    }
}
```

## GitHub搜索案例

> 设计状态时要考虑全面，例如带有网络请求的组件，要考虑请求失败怎么办。

#### img、a标签

a标签后面需要加`rel="noreferrer"`，img需要加 `alt=""` 

#### 连续赋值解构+重命名

```jsx
let obj = {a:{b:1}}
const {a} = obj; //传统解构赋值
const {a:{b}} = obj; //连续解构赋值
const {a:{b:value}} = obj; //连续解构赋值+重命名
```

#### 消息订阅与发布机制

##### 工具库: PubSubJS

1.先订阅，再发布（理解：有一种隔空对话的感觉）

2.适用于任意组件间通信

3.要在组件的`componentWillUnmount`中取消订阅

```jsx
//下载: npm install pubsub-js --save
//使用举例
import PubSub from 'pubsub-js' //引入
PubSub.subscribe('delete', function(data){ }); //订阅
PubSub.publish('delete', data) //发布消息
//*------------------------------订阅----------------------------------------------------
componentDidMount(){
    this.token = PubSub.subscribe('atguigu',(_,stateObj)=>{
        this.setState(stateObj)
    })
}

componentWillUnmount(){
    PubSub.unsubscribe(this.token)
}
//----------------------------------发布---------------------------------------------------
//发送请求前通知List更新状态
PubSub.publish('atguigu',{isFirst:false,isLoading:true})
//发送网络请求---使用fetch发送（优化）
try {
    const response= await fetch(`/api1/search/users2?q=${keyWord}`)
    const data = await response.json()
    console.log(data);
    PubSub.publish('atguigu',{isLoading:false,users:data.items})
} catch (error) {
    console.log('请求出错',error);
    PubSub.publish('atguigu',{isLoading:false,err:error.message})
}
```

##### 工具库: mitt

此方法用的是[`mitt`]实现,其实本质上就是注册一个全局变量进行监听 --> [mitt源码地址](https://github.com/developit/mitt)

1. 安装或者直接复制使用

```sh
npm install --save mitt
```

2. 使用示例

```tsx
//
-------------- 首先要定义一个公用全局变量  --------------------------
 //文件 utils/index.ts
 import mitt from './mitt';
 //此处声明,将其变为全局变量
 const eventBus = mitt();
 export { eventBus }
 ---------------- 发送值的组件(要修改别人的组件)  ---------------------
 //导入共有变量
 import { eventBus } from '~/utils';
   <a
   onClick={() => {
     eventBus.emit('foo', data);    
    }}
   />;

 ------------------ 接受方组件(接受发送方的组件)  -------------------------------------

 const Search: FC<IProps> = (props) => {
   useEffect(() => {
     //替换为mitt写法,此时已经接收到了
     eventBus.on('foo', (searchParams) => {console.log('接受到值了',searchParams) }
     });
   }, []);
 } 
```

#### fetch发送请求

> 概念:关注分离的设计思想

1. `Fetch` 是浏览器提供的原生 AJAX 接口。

   由于原来的XMLHttpRequest不符合关注分离原则，且基于事件的模型在处理异步上已经没有现代的Promise等那么有优势。因此Fetch出现来解决这种问题。

2. 特点:

    -  `原生函数`，不再使用XmlHttpRequest对象提交ajax请求

    - `老版本浏览器可能不支持`

    - 使用 fetch 无法`取消一个请求`。这是因为Fetch API`基于 Promise`，而Promise无法做到这一点。由于Fetch是典型的异步场景，所以大部分遇到的问题不是Fetch的，其实是Promise的。

 3. 如果直接使用`fetch`,返回的并不是直接的结果它只是一个`HTTP响应`，而不是真的数据。想要获取数据,方法有二:

    ① 使用`async+await`获取

    ② 使用`promise的链式调用`,再第一个then中将其返回,再下个then中在使用

4. 代码示例

```jsx
//代码示例
----------------------------- 使用axios发送 ------------------------------------------------------
axios.get(`/api1/search/users2?q=${keyWord}`).then(
    response => {
        //请求成功后通知List更新状态
        PubSub.publish('atguigu',{isLoading:false,users:response.data.items})
    },
    error => {
        //请求失败后通知App更新状态
        PubSub.publish('atguigu',{isLoading:false,err:error.message})
    }
) 
----------------------------- 未优化:使用then链式调用 ------------------------------------------------------
fetch(`/api1/search/users2?q=${keyWord}`).then(
    response => {
        console.log('联系服务器成功了');
        return response.json()
    },
    error => {
        console.log('联系服务器失败了',error);
        return new Promise(()=>{})
    }
).then(
    response => {console.log('获取数据成功了',response);},
    error => {console.log('获取数据失败了',error);}
) 
----------------------------- 优化后:使用async+await ------------------------------------------------------
search = async()=>{
    //获取用户的输入(连续解构赋值+重命名)
    const {keyWordElement:{value:keyWord}} = this
    //发送请求前通知List更新状态
    PubSub.publish('atguigu',{isFirst:false,isLoading:true})
    //发送网络请求---使用fetch发送（优化）
    try {
        const response= await fetch(`/api1/search/users2?q=${keyWord}`)
        const data = await response.json()
        console.log(data);
        PubSub.publish('atguigu',{isLoading:false,users:data.items})
    } catch (error) {
        console.log('请求出错',error);
        PubSub.publish('atguigu',{isLoading:false,err:error.message})
    }
}

```

# React 路由

## 相关理解

### SPA的理解

* 单页Web应用（single page web application，SPA）。
* 整个应用只有**一个完整的页面**。
* 点击页面中的链接**不会刷新**页面，只会做页面的**局部更新。**
* 数据都需要通过ajax请求获取, 并在前端异步展现。

### 路由的理解

#### 什么是路由?

1. 一个路由就是一个映射关系(`key:value`)
2. key为**路径**, value可能是`function`或`component`

#### 路由分类

##### 后端路由

1)   理解： value是function, 用来处理客户端提交的请求。
2)   注册路由： `router.get(path, function(req, res))`
3)   工作过程：当node接收到一个请求时, 根据请求路径找到匹配的路由, 调用路由中的函数来处理请求, 返回响应数据

##### 前端路由

1)   浏览器端路由，value是component，用于展示页面内容。
2)   注册路由: `<Route path="/test" component={Test}>`
3)   工作过程：当浏览器的path变为/test时, 当前路由组件就会变为Test组件

### react-router-dom的理解

`yarn add react-router-dom`

#### 相关概念

1. react的一个插件库。
2. 专门用来实现一个SPA应用。
3. 基于react的项目基本都会用到此库。

#### 相关api

##### 1、内置组件

1. `<BrowserRouter>`
2. `<HashRouter>`
3. `<Route>`
4. `<Redirect>`
5. `<Link>`
6. `<NavLink>`
7. `<Switch>`

##### 2、其他

1. history对象
2. match对象
3. withRouter函数

## 路由的基本使用

1.明确好界面中的导航区、展示区

2.导航区的a标签改为Link标签

```jsX
<Link to="/xxxxx">Demo</Link>
```

3.展示区写Route标签进行路径的匹配 

```jsX
<Route path='/xxxx' component={Demo}/>
```

4.`<App>`的最外侧包裹了一个`<BrowserRouter>或<HashRouter>`

```jsX
ReactDOM.render(
	<BrowserRouter>
		<App/>
	</BrowserRouter>,
	document.getElementById('root')
)
```

## 路由组件与一般组件

1.写法不同：

​      一般组件：`<Demo/>`

​      路由组件：`<Route path="/demo" component={Demo}/>`

2.存放位置不同：

​      一般组件：**components**

​      路由组件：**pages**

3. 接收到的props不同：

    一般组件：写组件标签时传递了什么，就能收到什么

    路由组件：接收到三个固定的属性

```json
 //路由属性打印结果展示
 history:
 	go: ƒ go(n)
 	goBack: ƒ goBack()
 	goForward: ƒ goForward()
 	push: ƒ push(path, state)
 	replace: ƒ replace(path, state)
 location:
 	pathname: "/about"
 	search: ""
 	state: undefined
 match:
 	params: {}
 	path: "/about"
 	url: "/about"
```

## NavLink使用与封装

1. NavLink可以`实现路由链接的高亮`，通过`activeClassName指定样式名`

```jsx
import {NavLink,Route} from 'react-router-dom'
{/* 原生html中，靠<a>跳转不同的页面 */}
{/* <a className="list-group-item" href="./about.html">About</a>
<a className="list-group-item active" href="./home.html">Home</a> */}

{/* 在React中靠路由链接实现切换组件--编写路由链接 */}
<NavLink activeClassName="atguigu" className="list-group-item" to="/about">About</NavLink>
<NavLink activeClassName="atguigu" className="list-group-item" to="/home">Home</NavLink>
```

```html
<!DOCTYPE html>
<html>
	<head>
		<meta charset="UTF-8" />
		<title>react脚手架</title>
		<link rel="icon" href="%PUBLIC_URL%/favicon.ico" />
		<link rel="stylesheet" href="/css/bootstrap.css">
		<style>
			.atguigu{
				background-color: rgb(209, 137, 4) !important;
				color: white !important;
			}
		</style>
	</head>
	<body>
		<div id="root"></div>
	</body>
</html>
```

2. 封装

```jsx
 //封装示例
 export default class MyNavLink extends Component {
 	render() {
 		return (
 			<NavLink activeClassName="atguigu" className="list-group-item" {...this.props}/>
 		)
 	}
 }
```

3. 使用与调用

```jsx
<MyNavLink to="/about">About</MyNavLink>
<MyNavLink to="/home">Home</MyNavLink>
```

注：**标签体内容也是一种特殊的标签属性**

```jsx
<MyNavLink to="/about">About</MyNavLink>
<MyNavLink to="/about" children="About"/>
```

## Switch的使用

1.通常情况下，path和component是一一对应的关系。

2.Switch可以提高路由匹配效率(单一匹配) ---- 即匹配到一个后将不再往下匹配

```jsx
<Switch>
	<Route path="/about" component={About}/>
	<Route path="/home" component={Home}/>
	<Route path="/home" component={Test}/>
</Switch>
```

## 解决多级路径刷新页面样式丢失的问题

1.`public/index.html` 中 引入样式时不写 `./` 写 `/` （常用）`./`相对路径

2.public/index.html 中 引入样式时不写 ./ 写 `%PUBLIC_URL%` （常用,但`只在react中`有效果）绝对路径

3.使用`HashRouter` (不常用) `#`后面自动忽略

```html
<!DOCTYPE html>
<html>
    <head>
        <meta charset="UTF-8" />
        <title>react脚手架</title>
        <!-- 方法二 -->
        <link rel="icon" href="%PUBLIC_URL%/favicon.ico" />
        <!-- 方法一 -->
        <link rel="stylesheet" href="/css/bootstrap.css">
    </head>
    <body>
        <div id="root"></div>
    </body>
</html>
```

补充：`yarn start`和`npm start`都可，但安装包时尽量用一种

## 路由的严格匹配与模糊匹配

1. 默认使用的是模糊匹配（简单记：【输入的路径】必须包含要【匹配的路径】，且**顺序**要一致）

2. 开启严格匹配：`<Route exact={true}path="/about" component={About}/>`  

  可以省略`exact={true}`为`exact`

3. `严格匹配不要随便开启`，需要再开，有些时候开启会导致无法继续匹配二级路由

```jsx
<MyNavLink to="/about">About</MyNavLink>
<MyNavLink to="/home/a/b">Home</MyNavLink>

<Switch>
    <Route exact path="/about" component={About}/>
    <Route exact path="/home" component={Home}/>
</Switch>
```

## Redirect的使用 

1. 一般写在所有路由注册的`最下方`，当所有路由都`无法匹配时`，跳转到Redirect指定的路由

```jsx
import {Route,Switch,Redirect} from 'react-router-dom'
```

2. 具体编码：

```jsx
<Switch>
    <Route path="/about" component={About}/>
    <Route path="/home" component={Home}/>
    <Redirect to="/about"/>
</Switch>
```

## 嵌套路由

1. 注册子路由时要**写上父路由的path值**
2. 路由的匹配是按照注册路由的顺序进行的

```jsx
-------------------注册一级路由-----------------------------
{/* 在React中靠路由链接实现切换组件--编写路由链接 */}
<MyNavLink to="/about">About</MyNavLink>
<MyNavLink to="/home">Home</MyNavLink>
{/* 注册路由 */}
<Switch>
    <Route path="/about" component={About}/>
    <Route path="/home" component={Home}/>
    <Redirect to="/about"/>
</Switch>
----------------------注册二级路由 :Home组件-----------------------------------
<div>
    <ul className="nav nav-tabs">
        <li>
            <MyNavLink to="/home/news">News</MyNavLink>
        </li>
        <li>
            <MyNavLink to="/home/message">Message</MyNavLink>
        </li>
    </ul>
    {/* 注册路由 */}
    <Switch>
        <Route path="/home/news" component={News}/>
        <Route path="/home/message" component={Message}/>
        <Redirect to="/home/news"/>
    </Switch>
</div>
```

## 向路由组件传递参数

### params参数

1. 路由链接(携带参数)：`<Link to='/demo/test/tom/18'}>详情</Link>`
2. 注册路由(声明接收)：`<Route path="/demo/test/:name/:age" component={Test}/>`
3. 接收参数：this.props.match.params

```jsx
-------------------------------发送参数:父组件----------------------------------------------
<div>
   {/* 向路由组件传递params参数 */}
   <Link to={`/home/message/detail/${msgObj.id}/${msgObj.title}`}>{msgObj.title}</Link>
   <hr />
   {/* 声明接收params参数 */}
   <Route path="/home/message/detail/:id/:title" component={Detail} />
</div>
--------------------------------接受参数:子组件-----------------------------------------------------------
const {id,title} = this.props.match.params
```

### search参数

1. 路由链接(携带参数)：`<Link to='/demo/test?name=tom&age=18'}>详情</Link>`
2. 注册路由(`无需声明`，正常注册即可)：`<Route path="/demo/test" component={Test}/>`
3. 接收参数：`this.props.location.search`
4. 备注：获取到的search是`urlencoded编码字符串`，需要`借助querystring解析`

```jsx
-------------------------------发送参数:父组件----------------------------------------------
<div>
    {/* 向路由组件传递search参数 */}
	<Link to={`/home/message/detail/?id=${msgObj.id}&title=${msgObj.title}`}>{msgObj.title}</Link>
    <hr />
     {/* search参数无需声明接收，正常注册路由即可 */}
	<Route path="/home/message/detail" component={Detail}/>
</div>
--------------------------------接受参数:子组件-----------------------------------------------------------
import qs from 'querystring'
// 接收search参数
const {search} = this.props.location
const {id,title} = qs.parse(search.slice(1))
```

### state参数

1. 路由链接(携带参数)：`<Link to={{pathname:'/demo/test',state:{name:'tom',age:18}}}>详情</Link>`
2. 注册路由(无需声明，正常注册即可)：`<Route path="/demo/test" component={Test}/>`
3. 接收参数：`this.props.location.state`
  - 备注：使用`BrowserRouter`刷新才可以`保留住参数`,使用`HashRouter`刷新后state将会没有`history`来保存参数
  - 子组件接受参数时`const {id,title} = this.props.location.state || {}` ,后面添加`||{}`是防止state为undefined时报错

```jsx
-------------------------------发送参数:父组件----------------------------------------------
<div>
   {/* 向路由组件传递state参数 */}
	<Link to={{pathname:'/home/message/detail',state:{id:msgObj.id,title:msgObj.title}}}>{msgObj.title}	</Link>
	<hr />
     {/* state参数无需声明接收，正常注册路由即可 */}
	<Route path="/home/message/detail" component={Detail}/>
</div>
--------------------------------接受参数:子组件-----------------------------------------------------------
// 接收state参数,后面添加`||{}`是防止state为undefined时报错
const {id,title} = this.props.location.state || {}
```

## 编程式路由导航

借助`this.prosp.history`对象上的API对操作路由跳转、前进、后退  

1. `this.prosp.history.push()`

  将历史记录压入栈

2. `this.props.history.replace()`

  替代栈位置,即不会产生历史记录

3. `this.props.history.goBack()`

  回退一格

4. `this.props.history.goForward()`

  前进一格

5. `this.props.history.go()`

  前进或者后退n格(根据传入的数字正负数)

```jsx
import React, { Component } from 'react'
import { Link, Route } from 'react-router-dom'
import Detail from './Detail'

export default class Message extends Component {
 state = {
   messageArr: [
     { id: '01', title: '消息1' },
     { id: '02', title: '消息2' },
     { id: '03', title: '消息3' },
   ]
 }

 replaceShow = (id, title) => {
   //replace跳转+携带params参数
   //this.props.history.replace(`/home/message/detail/${id}/${title}`)

   //replace跳转+携带search参数
   // this.props.history.replace(`/home/message/detail?id=${id}&title=${title}`)

   //replace跳转+携带state参数
   this.props.history.replace(`/home/message/detail`, { id, title })
 }

 pushShow = (id, title) => {
   //push跳转+携带params参数
   // this.props.history.push(`/home/message/detail/${id}/${title}`)

   //push跳转+携带search参数
   // this.props.history.push(`/home/message/detail?id=${id}&title=${title}`)

   //push跳转+携带state参数
   this.props.history.push(`/home/message/detail`, { id, title })

 }

 back = () => {
   this.props.history.goBack()
 }

 forward = () => {
   this.props.history.goForward()
 }

 go = () => {
   this.props.history.go(-2)
 }

 render() {
   const { messageArr } = this.state
   return (
     <div>
       <ul>
         {
           messageArr.map((msgObj) => {
             return (
               <li key={msgObj.id}>

                 {/* 向路由组件传递params参数 */}
                 {/* <Link to={`/home/message/detail/${msgObj.id}/${msgObj.title}`}>{msgObj.title}</Link> */}

                 {/* 向路由组件传递search参数 */}
                 {/* <Link to={`/home/message/detail/?id=${msgObj.id}&title=${msgObj.title}`}>{msgObj.title}</Link> */}

                 {/* 向路由组件传递state参数 */}
                 <Link to={{ pathname: '/home/message/detail', state: { id: msgObj.id, title: msgObj.title } }}>{msgObj.title}</Link>
			&nbsp;<button onClick={() => this.pushShow(msgObj.id, msgObj.title)}>push查看</button>
			&nbsp;<button onClick={() => this.replaceShow(msgObj.id, msgObj.title)}>replace查看</button>
               </li>
             )
           })
         }
       </ul>
       <hr />
       {/* 声明接收params参数 */}
       {/* <Route path="/home/message/detail/:id/:title" component={Detail}/> */}

       {/* search参数无需声明接收，正常注册路由即可 */}
       {/* <Route path="/home/message/detail" component={Detail}/> */}

       {/* state参数无需声明接收，正常注册路由即可 */}
       <Route path="/home/message/detail" component={Detail} />

       <button onClick={this.back}>回退</button>&nbsp;
       <button onClick={this.forward}>前进</button>&nbsp;
       <button onClick={this.go}>go</button>
     </div>
   )
 }
}
```

## withRouter的使用

1. withRouter可以加工一般组件，让一般组件具备路由组件所特有的API
2. withRouter的返回值是一个新组件

```jsx
import React, { Component } from 'react'
import { withRouter } from 'react-router-dom'
class Header extends Component {
    back = () => { this.props.history.goBack()}
    forward = () => {this.props.history.goForward()}
    go = () => { this.props.history.go(-2)}
    render() {
        console.log('Header组件收到的props是', this.props);
        return (
            <div className="page-header">
                <h2>React Router Demo</h2>
                <button onClick={this.back}>回退</button>&nbsp;
                <button onClick={this.forward}>前进</button>&nbsp;
                <button onClick={this.go}>go</button>
            </div>
        )
    }
}
export default withRouter(Header)
```

## BrowserRouter与HashRouter的区别

**底层原理不一样**：

1. BrowserRouter使用的是**H5的history API**，不兼容IE9及以下版本。`但一般来说都用的这个`

2. HashRouter使用的是**URL的哈希值**。

**path表现形式不一样**

1. BrowserRouter的路径中没有`#`,例如：`localhost:3000/demo/test`
2. HashRouter的路径包含`#`,例如：`localhost:3000/#/demo/test`

**刷新后对路由state参数的影响**

1. BrowserRouter没有任何影响，因为`state`保存在`history`对象中。
2. HashRouter`刷新后会导致路由state参数的丢失！！！`

**备注：HashRouter可以用于解决一些路径错误相关的问题。**

# Ant Design

## 相关文档

### ant-design(国内蚂蚁金服)

 `yarn add antd`

1. 官网: https://ant.design/index-cn
2. Github: https://github.com/ant-design/ant-design/

```jsx
import React, { Component } from 'react'
import { Button,DatePicker } from 'antd';
import {WechatOutlined,WeiboOutlined,SearchOutlined} from '@ant-design/icons'
const { RangePicker } = DatePicker;

export default class App extends Component {
	render() {
		return (
			<div>
				App....
				<button>点我</button>
				<Button type="primary">按钮1</Button>
				<Button >按钮2</Button>
				<Button type="link">按钮3</Button>
				<Button type="primary" icon={<SearchOutlined />}>
					Search
				</Button>
				<WechatOutlined />
				<WeiboOutlined />
				<DatePicker/>
				<RangePicker/>
			</div>
		)
	}
}
```

### material-ui(国外)

1. 官网: http://www.material-ui.com/#/

2. github: https://github.com/callemall/material-ui

## 按需引入与自定义主题

### 安装依赖

`yarn add react-app-rewired customize-cra babel-plugin-import less less-loader`

### 修改package.json

```json
"scripts": {
    "start": "react-app-rewired start",
    "build": "react-app-rewired build",
    "test": "react-app-rewired test",
    "eject": "react-scripts eject"
},
```

### 根目录下创建config-overrides.js

注意:如果按照官方文档的自定义主题进行配置可能会报错,需要多加一层`lessOptions`

```js
//配置具体的修改规则
const { override, fixBabelImports, addLessLoader } = require('customize-cra');

module.exports = override(
	fixBabelImports('import', {
		libraryName: 'antd',
		libraryDirectory: 'es',
		style: true,
	}),
	addLessLoader({
		lessOptions:{
			javascriptEnabled: true,
			modifyVars: { '@primary-color': 'green' },
		}
	}),
);
```

报错

```js
Failed to compile.

./node_modules/antd/es/button/style/index.less (./node_modules/css-loader/dist/cjs.js??ref--5-oneOf-8-1!./node_modules/postcss-loader/src??postcss!./node_modules/resolve-url-loader??ref--5-oneOf-8-3!./node_modules/less-loader/dist/cjs.js??ref--5-oneOf-8-4!./node_modules/antd/es/button/style/index.less)
TypeError: this.getOptions is not a function
```

**原因：** less-loader安装的版本过高

**解决方案：** 1.`npm uninstall less-loader` 2.`npm install less-loader@6.0.0`

### 成功

> 备注：不用在组件里亲自引入样式了，即：import 'antd/dist/antd.css'应该删掉

# Redux

## redux理解

### 学习文档

1. 英文文档: https://redux.js.org/
2. 中文文档: http://www.redux.org.cn/
3. Github: https://github.com/reactjs/redux

### redux是什么

1. redux是一个专门用于做**状态管理的JS库**(不是react插件库)。
2. 它可以用在react, angular, vue等项目中, 但基本与react配合使用。
3. 作用: 集中式管理react应用中多个组件**共享**的状态。

### 什么情况下需要使用redux

1. 某个组件的状态，需要让其他组件可以随时拿到（共享）。
2. 一个组件需要改变另一个组件的状态（通信）。
3. 总体原则：能不用就不用, 如果不用比较吃力才考虑使用。

### redux工作流程

[![5W48UO.png](https://z3.ax1x.com/2021/10/24/5W48UO.png)](https://imgtu.com/i/5W48UO)

## redux的三个核心概念

### action

* **动作的对象**

* 包含2个属性

  type：标识属性, 值为字符串, 唯一, 必要属性

  data：数据属性, 值类型任意, 可选属性

* 例子：`{ type: 'ADD_STUDENT',data:{name: 'tom',age:18} }`

### reducer

* **用于初始化状态、加工状态**。

* 加工时，根据旧的state和action， 产生新的state的**纯函数**
  * 纯函数:一类特别的函数: 只要是同样的输入(实参)，必定得到同样的输出(返回)
  * 必须遵守以下一些约束 
    * **不得改写参数数据**  `preState.unshift(data)`
    * 不会产生任何副作用，例如网络请求，输入和输出设备
    * 不能调用`Date.now()`或者`Math.random()`等不纯的方法 

* redux的**reducer函数必须是一个纯函数**

### store

* **将state、action、reducer联系在一起的对象**

* 如何得到此对象?
  * `import {createStore} from 'redux'`
  * `import reducer from './reducers'`
   * `const store = createStore(reducer)`

* 此对象的功能?
  * `getState()`: 得到state

   * `dispatch(action)`: 分发action, 触发reducer调用, 产生新的state

   * `subscribe(listener)`: 注册监听, 当产生了新的state时, 自动调用

## redux的核心API

### createstore()与applyMiddleware()

`createstore()`作用：创建包含指定reducer的store对象

`applyMiddleware()`作用：应用上基于redux的中间件(插件库)

```js
//代码示例
---------------------------store.js 部分代码---------------------------------
//引入createStore,专门用于创建redux中最为核心的store对象
import {createStore,applyMiddleware} from 'redux'
//暴露store
export default createStore(reducer,composeWithDevTools(applyMiddleware(thunk)))
```

### store对象

* 作用: redux库最核心的管理对象
* 它内部维护着:
  * state

  * reducer

* 核心方法:
  * getState()

  * dispatch(action)

  * subscribe(listener)

* 具体编码:
  * store.getState()

  * store.dispatch({type:'INCREMENT', number})

  * store.subscribe(render)

```jsx
//代码示例
---------------------------store.js---------------------------------
/**
* 该文件撰文用于暴露一个store对象,整个应用只有一个store对象
*/
//引入createStore,专门用于创建redux中最为核心的store对象
import {createStore,applyMiddleware} from 'redux'
//引入汇总后的reducer
import reducer from './reducers'
//引入redux-thunk，用于支持异步action
import thunk from 'redux-thunk'
//引入redux-devtools-extension
import {composeWithDevTools} from 'redux-devtools-extension'
//暴露store
export default createStore(reducer,composeWithDevTools(applyMiddleware(thunk)))
----------------------------index.js 引入store对象--------------------------------
import React from 'react'
import ReactDOM from "react-dom"
import App from './App'
import store from './redux/store'
import {Provider} from 'react-redux'

ReactDOM.render(
	/* 此处需要用Provider包裹App，目的是让App所有的后代容器组件都能接收到store */
	<Provider store={store}>
		<App/>
	</Provider>,
	document.getElementById('root')
)
```

### combineReducers()

作用：合并多个reducer函数

```jsx
//代码示例
------------------ redux/reducers/index.js ------------------------------------
/**
 * 该文件用于汇总所有的reducer为一个总的reducer
 */
//引入combineReducers，用于汇总多个reducer
import {combineReducers} from 'redux'
//引入为Count组件服务的reducer
import count from './count'
import persons from './person'

//汇总所有的reducer变为一个总的reducer
export default combineReducers({
  count,persons
})
```

## redux 异步编程

### 理解

1. redux默认是不能进行异步处理的,
2. 某些时候应用中需要在`redux`中执行异步任务(ajax, 定时器)

### 使用异步中间件

1. 下载依赖`npm install --save redux-thunk`
2. 使用

```jsx
 //代码示例
 ---------------------------store.js---------------------------------
 /**
  * 该文件撰文用于暴露一个store对象,整个应用只有一个store对象
  */
 //引入createStore,专门用于创建redux中最为核心的store对象
 import {createStore,applyMiddleware} from 'redux'
 //引入汇总后的reducer
 import reducer from './reducers'
 //引入redux-thunk，用于支持异步action
 import thunk from 'redux-thunk'
 //引入redux-devtools-extension
 import {composeWithDevTools} from 'redux-devtools-extension'
 //暴露store
 export default createStore(reducer,composeWithDevTools(applyMiddleware(thunk)))
```

## react-redux

`yarn add react-redux`

[![5W4lb6.png](https://z3.ax1x.com/2021/10/24/5W4lb6.png)](https://imgtu.com/i/5W4lb6)

### 理解

1. 一个react插件库
2. 专门用来简化react应用中使用redux

### react-Redux将所有组件分成两大类

#### UI组件

* 只负责 UI 的呈现，不带有任何业务逻辑
* 通过props接收数据(一般数据和函数)
* 不使用任何 Redux 的 API
* 一般保存在`components`文件夹下,也可以直接写在容器组件中直接加工成容器组件

#### 容器组件

* 负责管理数据和业务逻辑，不负责UI的呈现
* 使用 Redux 的 API
* 一般保存在`ontainers`文件夹下

### 相关API

#### Provider

作用: 让所有组件都可以得到state数据

```jsx
import React from 'react'
import ReactDOM from "react-dom"
import App from './App'
import store from './redux/store'
import {Provider} from 'react-redux'

ReactDOM.render(
	/* 此处需要用Provider包裹App，目的是让App所有的后代容器组件都能接收到store */
	<Provider store={store}>
		<App/>
	</Provider>,
	document.getElementById('root')
)
```

#### `connect()()`

* 作用: 用于包装 UI 组件生成容器组件

* 使用`connect(mapDispatchToProps,mapDispatchToProps)`(UI组件)

  注意点:

* 该方法默认传入`state`与`dispatch`
* 可以省略`dispatch`直接传入`action`方法,该api会自动帮你调用`dispatch`

##### mapStateToProps

作用:将外部的数据（即`state对象`）转换为UI组件的标签属性

1.mapStateToProps函数返回的是一个对象；

2.返回的对象中的key就作为传递给UI组件props的key,value就作为传递给UI组件props的value

3.mapStateToProps`用于传递状态`

```jsx
function mapStateToProps(state){
	return {count:state}
}
```

##### mapDispatchToProps

作用:将`分发action的函数`转换为UI组件的标签属性

1. mapDispatchToProps函数返回的是一个对象；
2. 返回的对象中的key就作为传递给UI组件props的key,value就作为传递给UI组件props的value
3. mapDispatchToProps`用于传递操作状态的方法`
4. 可以省略`dispatch`,直接传入`action`,api将会`自动调用`dispatch

##### 代码示例

```jsx
------------------------------不简化代码-----------------------------------------------
/* 
	1.mapStateToProps函数返回的是一个对象；
	2.返回的对象中的key就作为传递给UI组件props的key,value就作为传递给UI组件props的value
	3.mapStateToProps用于传递状态
*/
function mapStateToProps(state){
	return {count:state}
}

/* 
	1.mapDispatchToProps函数返回的是一个对象；
	2.返回的对象中的key就作为传递给UI组件props的key,value就作为传递给UI组件props的value
	3.mapDispatchToProps用于传递操作状态的方法
*/
function mapDispatchToProps(dispatch){
	return {
		jia:number => dispatch(createIncrementAction(number)),
		jian:number => dispatch(createDecrementAction(number)),
		jiaAsync:(number,time) => dispatch(createIncrementAsyncAction(number,time)),
	}
}

//使用connect()()创建并暴露一个Count的容器组件
export default connect(mapStateToProps,mapDispatchToProps)(CountUI)

----------------下面是简化代码-----------------------------
//使用connect()()创建并暴露一个Count的容器组件
//使用connect(传入状态,操作状态方法)(UI组件)
export default connect(
state => ({
count: state.count,
personCount: state.persons.length
}),
{increment, decrement, incrementAsync}
)(Count)
```

## 使用redux调试工具

### 安装chrome浏览器插件

> Redux DecTools

### 下载工具依赖包

`yarn add redux-devtools-extension`

### 修改store.js

`import {composeWithDevTools} from 'redux-devtools-extension'`

```jsx
/**
* 该文件撰文用于暴露一个store对象,整个应用只有一个store对象
*/
//引入createStore,专门用于创建redux中最为核心的store对象
import {createStore,applyMiddleware} from 'redux'
//引入汇总后的reducer
import reducer from './reducers'
//引入redux-thunk，用于支持异步action
import thunk from 'redux-thunk'
//引入redux-devtools-extension
import {composeWithDevTools} from 'redux-devtools-extension'
//暴露store
export default createStore(reducer,composeWithDevTools(applyMiddleware(thunk)))
```

# Redux求和案例

安装：`yarn add redux`

`注意`:在`reducer`中如果preState是一个数组,不可以用`push、unshift`等方法进行修改,如此修改并不会修改其引用,所以`diff`并不会判定其发生改变,`导致页面无法自动重新渲染`

```js
	//preState.unshift(data) //此处不可以这样写，这样会导致preState被改写了，personReducer就不是纯函数了。
	return [data,...preState]
```

### 求和案例_redux精简版

* 去除Count组件自身的状态

* src下建立:
  * redux
    * store.js
    * count_reducer.js

* store.js：
  * 引入redux中的createStore函数，创建一个store
  * createStore调用时要传入一个为其服务的reducer
  * 记得暴露store对象

* count_reducer.js：
  * reducer的本质是一个函数，接收：preState,action，返回加工后的状态
  * reducer有两个作用：初始化状态，加工状态
  * reducer被第一次调用时，是store自动触发的，传递的preState是`undefined`,传递的action是:`{type:'@@REDUX/INIT_a.2.b.4}`

* 在index.js中监测store中状态的改变，一旦发生改变重新渲染`<App/>`

​    备注：redux只负责管理状态，至于状态的改变驱动着页面的展示，要靠我们自己写

### 求和案例_redux完整版

新增文件：

* count_action.js 专门用于创建action对象

* constant.js 放置容易写错的type值

### 求和案例_redux异步action版

> 同步action，就是指action的值为Object类型的一般对象
>
> 异步action，就是指action的值为函数,异步action中一般都会调用同步action，异步action不是必须要用的。

* 明确：延迟的动作不想交给组件自身，想交给action

* 何时需要异步action：想要对状态进行操作，但是具体的数据靠异步任务返回。

* 具体编码：
  * `yarn add redux-thunk`，并配置在store中
  * 创建action的函数不再返回一般对象，而是一个**函数**，该函数中写异步任务。
  * 异步任务有结果后，分发一个同步的action去真正操作数据。

(4).备注：异步action不是必须要写的，完全可以自己等待异步任务的结果了再去分发同步action。

### 求和案例_react-redux基本使用

* 明确两个概念：
  * UI组件:不能使用任何redux的api，只负责页面的呈现、交互等。
  * 容器组件：负责和redux通信，将结果交给UI组件。

* 如何创建一个容器组件————靠react-redux 的 connect函数

  `connect(mapStateToProps,mapDispatchToProps)`(UI组件)

  * `mapStateToProps`:映射状态，返回值是一个对象
  * `mapDispatchToProps`:映射操作状态的方法，返回值是一个对象

* 备注1：容器组件中的store是靠`props`传进去的，而不是在容器组件中直接引入

* 备注2：mapDispatchToProps，也可以是一个**对象**

### 求和案例_react-redux优化

* 容器组件和UI组件整合一个文件

* 无需自己给容器组件传递store，给`<App/>`包裹一个`<Provider store={store}>`即可。

* **使用了react-redux后也不用再自己检测redux中状态的改变了**，容器组件可以自动完成这个工作。

* mapDispatchToProps也可以简单的写成一个对象

* 一个组件要和redux“打交道”要经过哪几步？

  * 定义好UI组件---**不暴露**

  * 引入connect生成一个容器组件，并暴露，写法如下

    ```jsx
    connect(
       state => ({key:value}), //映射状态
       {key:xxxxxAction} //映射操作状态的方法
      )(UI组件)
    ```

  * 在UI组件中通过this.props.xxxxxxx读取和操作状态

### 求和案例_react-redux数据共享版

* 定义一个Pserson组件，和Count组件通过redux共享数据。
* 为Person组件编写：reducer、action，配置constant常量。
* 重点：Person的reducer和Count的Reducer要使用combineReducers进行合并，合并后的总状态是一个对象！！！
* 交给store的是总reducer，最后注意在组件中取出状态的时候，记得“取到位”。

### 求和案例_react-redux开发者工具的使用

* `yarn add redux-devtools-extension`

* store中进行配置

```jsx
import {composeWithDevTools} from 'redux-devtools-extension'
const store = createStore(allReducer,composeWithDevTools(applyMiddleware(thunk)))
```

### 求和案例_react-redux最终版

* 所有变量名字要规范，尽量触发对象的简写形式。

* reducers文件夹中，编写index.js专门用于汇总并暴露所有的reducer

### 打包发布

```bash
npm run build
npm i serve -g
serve build
```

### 最终代码

#### src文件目录

>src
>
>--`containers`
>
>​	--Count
>
>​		--index.jsx
>
>​	--Person
>
>​		--index.jsx
>
>--`redux`
>
>​	--actions
>
>​		--count.js
>
>​		--person.js
>
>​	--reducers
>
>​		--count.js
>
>​		--index.js
>
>​		--person.js
>
>​	--constant.js
>
>​	--store.js
>
>--`App.jsx`
>
>--`index.js`

#### index.js

```jsx
import React from 'react'
import ReactDOM from "react-dom"
import App from './App'
import store from './redux/store'
import {Provider} from 'react-redux'

ReactDOM.render(
	/* 此处需要用Provider包裹App，目的是让App所有的后代容器组件都能接收到store */
	<Provider store={store}>
		<App/>
	</Provider>,
	document.getElementById('root')
)
```

#### App.jsx

```jsx
import React, { Component } from 'react'
import Count from './containers/Count' //引入的Count的容器组件
import Person from './containers/Person' //引入的Person的容器组件

export default class App extends Component {
	render() {
		return (
			<div>
				<Count/>
				<hr/>
				<Person/>
			</div>
		)
	}
}

```

#### redux文件

`action`文件夹

```jsx
--------------------------------count.js------------------------------------------
/**
* 该文件专门未Count组件生成对象
*/
import {INCREMENT,DECREMENT} from '../constant'

//声明同步action,就是指action的值为Object类型的一般对象
export const increment=data=>({type:INCREMENT,data})
export const decrement=data=>({type:DECREMENT,data})


//声明异步action,就是指action的值为函数,异步action中一般都会调用同步action
//在外部调用该action方法时需要引入redux-thunk，用于支持异步action
//该方法会自动传入dispatch
 export const incrementAsync=(data,time)=>{
   return (dispatch)=>{
     setTimeout(()=>{
       dispatch(increment(data))
     },time)
   }
 }
--------------------------------------person.js-------------------------------
import {ADD_PERSON} from '../constant'
//创建增加一个人的action动作对象
export const addPerson=personObj=>({
 type:ADD_PERSON,
 data:personObj
})
```

`reducers`文件夹

```jsx
--------------------------------count.js------------------------------------------
/**
* 1. 该文件时用于创建一个为Count组件服务的reducer.reducer的本质就是一个函数
* 2. reducer函数会接到两个参数,分别为:之前状态(preState),动作对象(action)
*/
import {
 INCREMENT,
 DECREMENT
} from '../constant'
const initState = 0 //初始化状态
export default function countReducer(preState = initState, action) {
 //从action对象中获取:type:data
 const {
   type,
   data
 } = action
 //根据type决定如何加工数据
 switch (type) {
   case INCREMENT:
     return preState + data
   case DECREMENT:
     return preState - data
   default:
     return preState
 }
}
--------------------------------------person.js-------------------------------
import {ADD_PERSON} from '../constant'
//初始化人的列表
const initState = [{id:'001',name:'tom',age:18}]
export default function personReducer(preState=initState,action){
	// console.log('personReducer@#@#@#');
	const {type,data} = action
	switch (type) {
		case ADD_PERSON: //若是添加一个人
			//preState.unshift(data) //此处不可以这样写，这样会导致preState被改写了，personReducer就不是纯函数了。
			return [data,...preState]
		default:
			return preState
	}
}
--------------------------------------index.js-------------------------------
/**
* 该文件用于汇总所有的reducer为一个总的reducer
*/
//引入combineReducers，用于汇总多个reducer
import {combineReducers} from 'redux'
//引入为Count组件服务的reducer
import count from './count'
import persons from './person'

//汇总所有的reducer变为一个总的reducer
export default combineReducers({
 count,persons
})
```

`store.js`

```js
/**
* 该文件撰文用于暴露一个store对象,整个应用只有一个store对象
*/
//引入createStore,专门用于创建redux中最为核心的store对象
import {createStore,applyMiddleware} from 'redux'
//引入汇总后的reducer
import reducer from './reducers'
//引入redux-thunk，用于支持异步action
import thunk from 'redux-thunk'
//引入redux-devtools-extension
import {composeWithDevTools} from 'redux-devtools-extension'
//暴露store
export default createStore(reducer,composeWithDevTools(applyMiddleware(thunk)))
```

`constant.js`

```js
/**
* 该模块是用于定义action对象中的type类型的常量值,目的只有一个:
*  便于管理的同事防止程序员单词写错
*/
export const INCREMENT = 'increment'
export const DECREMENT = 'decrement'
export const ADD_PERSON = 'add_person'
```

#### containers

`Count`文件夹的`index.jsx`

```jsx
  import React, { Component } from 'react'

  //引入action
  import {
    increment,
    decrement,
    incrementAsync
  } from "../../redux/actions/count"
  //引入connect用于链接UI组件与redux
  import { connect } from 'react-redux'

  //定义UI组件,这个将再connect()()中加工成容器组件,就可以调用到其传入的redux状态与actions
  class Count extends Component {
    increment = () => {
      //获取出入内容
      const { value } = this.selectNumber
      this.props.increment(value * 1)
    }
    //减法
    decrement = () => {
      const { value } = this.selectNumber
      this.props.decrement(value * 1)
    }
    //奇数再加
    incrementIfOdd = () => {
      const { value } = this.selectNumber
      if (this.props.count % 2 !== 0) {
        this.props.increment(value * 1)
      }
    }
    //异步加
    incrementAsync = () => {
      const { value } = this.selectNumber
      this.props.incrementAsync(value * 1, 500)
    }

    render() {
      return (
        <div>
          <h2>我是Count组件,下方组件总人数为:{this.props.personCount}</h2>
          <h4>当前求和为：{this.props.count}</h4>
          <select ref={c => this.selectNumber = c}>
            <option value="1">1</option>
            <option value="2">2</option>
            <option value="3">3</option>
          </select>&nbsp;
          <button onClick={this.increment}>+</button>&nbsp;
          <button onClick={this.decrement}>-</button>&nbsp;
          <button onClick={this.incrementIfOdd}>当前求和为奇数再加</button>&nbsp;
          <button onClick={this.incrementAsync}>异步加</button>&nbsp;
        </div>
      )
    }

  }


  //使用connect()()创建并暴露一个Count的容器组件
  //使用connect(传入状态,操作状态方法)(UI组件)
  export default connect(
    state => ({
      count: state.count,
      personCount: state.persons.length
    }),
    {increment, decrement, incrementAsync}
  )(Count)

```

`Person`文件夹下的jsx

```jsx
  import React, { Component } from 'react'
  import { connect } from 'react-redux'
  import { addPerson } from '../../redux/actions/person'
  import { nanoid } from 'nanoid'
  //创建UI组件
  class Person extends Component {
    addPerson = () => {
      const name = this.nameNode.value
      const age = this.ageNode.value * 1
      const personObj = { id: nanoid(), name, age }
      this.props.addPerson(personObj)
      this.nameNode.value = ''
      this.ageNode.value = ''
    }

    render() {
      return (
        <div>
          <h2>我是Person组件,上方组件求和为{this.props.count}</h2>
          <input ref={c => this.nameNode = c} type="text" placeholder="输入名字" />
          <input ref={c => this.ageNode = c} type="text" placeholder="输入年龄" />
          <button onClick={this.addPerson}>添加</button>
          <ul>
            {
              this.props.persons.map((p) => {
                return <li key={p.id}>{p.name}--{p.age}</li>
              })
            }
          </ul>
        </div>
      )
    }
  }
  export default connect(
    state => ({
      persons: state.persons,
      count: state.count
    }), { addPerson }
  )(Person)

```

# React 拓展

## setState

**setState更新状态的2种写法**

* `setState(stateChange, [callback])`------对象式的setState
  * stateChange为状态改变对象(该对象可以体现出状态的更改)
  * callback是可选的回调函数, 它在状态更新完毕（状态更新是异步的）、界面也更新后(render调用后)才被调用

* setState(updater, [callback])------函数式的setState
  * updater为返回stateChange对象的函数。
  * updater可以接收到state和props。
  * callback是可选的回调函数, 它在状态更新、界面也更新后(render调用后)才被调用。

总结:

* 对象式的setState是函数式的setState的简写方式(`语法糖`)
* 使用原则：
  * 如果新状态不依赖于原状态 => 使用对象方式
  * 如果新状态依赖于原状态 => 使用函数方式
  * 如果需要在setState()执行后获取最新的状态数据, 要在第二个callback函数中读取

```jsx
import React, { Component } from 'react'

export default class Demo extends Component {

	state = {count:0}

	add = ()=>{
		//对象式的setState
		/* //1.获取原来的count值
		const {count} = this.state
		//2.更新状态
		this.setState({count:count+1},()=>{
			console.log(this.state.count);
		})
		//console.log('12行的输出',this.state.count); //0 */

		//函数式的setState
		this.setState( state => ({count:state.count+1}))
	}

	render() {
		return (
			<div>
				<h1>当前求和为：{this.state.count}</h1>
				<button onClick={this.add}>点我+1</button>
			</div>
		)
	}
}
```

## lazyLoad

### 路由组件的lazyLoad

1. 懒加载中的组件,随用随调,不会提前加载
2. 使用懒加载时需要给定一个`fallback`,用于请求过慢或者请求不到组件时显示,通常为`组件`(也可以直接为一个`虚拟DOM`)
3. `fallback`如果是指定为一个组件,则该组件一定不能指定为`懒加载组件`,就正常引入的那种组件即可

```jsx
import React, { Component,lazy,Suspense} from 'react'
import {NavLink,Route} from 'react-router-dom'
//	import Loading from './Loading' // 用于指定`fallback`
//1.通过React的lazy函数配合import()函数动态加载路由组件 ===> 路由组件代码会被分开打包
const Login = lazy(()=>import('@/pages/Login'))
//2.通过<Suspense>指定在加载得到路由打包文件前显示一个自定义loading界面
<Suspense fallback={<Loading/>}>
	{/* 注册路由 */}
	<Route path="/about" component={About}/>
	<Route path="/home" component={Home}/>
</Suspense>
```

## Hooks

#### React Hook/Hooks是什么?

* Hook是React 16.8.0版本增加的新特性/新语法
* 可以让你在**函数组件**中使用 state 以及其他的 React 特性

#### 三个常用的Hook

* State Hook: React.useState()
* Effect Hook: React.useEffect()
* Ref Hook: React.useRef()

#### State Hook

* State Hook让函数组件也可以有state状态, 并进行状态数据的读写操作
* 语法: `const [xxx, setXxx] = React.useState(initValue)`  
* useState()说明:
  * 参数: 第一次初始化指定的值在内部作缓存
  * 返回值: 包含2个元素的数组, 第1个为**内部当前状态值**, 第2个为**更新状态值的函数**
* setXxx()2种写法:
  * `setXxx(newValue)`: 参数为非函数值, 直接指定新的状态值, 内部用其覆盖原来的状态值
  * `setXxx(value => newValue)`: 参数为函数, 接收原本的状态值, 返回新的状态值, 内部用其覆盖原来的状态值

#### Effect Hook

* Effect Hook 可以让你在函数组件中执行副作用操作(用于模拟类组件中的生命周期钩子)

* React中的副作用操作:

  * 发ajax请求数据获取
  * 设置订阅 / 启动定时器
  * 手动更改真实DOM

* 语法和说明: 

  ```jsx
  useEffect(() => { 
      // 在此可以执行任何带副作用操作
      return () => { // 在组件卸载前执行
          // 在此做一些收尾工作, 比如清除定时器/取消订阅等
      }
  }, [stateValue]) // 如果指定的是[], 回调函数只会在第一次render()后执行
  ```

* 可以把 useEffect Hook 看做如下三个函数的组合
  * componentDidMount()
  * componentDidUpdate()
  * componentWillUnmount() 

#### Ref Hook

* Ref Hook可以在函数组件中存储/查找组件内的标签或任意其它数据
* 语法: `const refContainer = useRef()`
* 作用:保存标签对象,功能与React.createRef()一样

> 类式组件

```jsx
class Demo extends React.Component {

	state = {count:0}

	myRef = React.createRef()

	add = ()=>{
		this.setState(state => ({count:state.count+1}))
	}

	unmount = ()=>{
		ReactDOM.unmountComponentAtNode(document.getElementById('root'))
	}

	show = ()=>{
		alert(this.myRef.current.value)
	}

	componentDidMount(){
		this.timer = setInterval(()=>{
			this.setState( state => ({count:state.count+1}))
		},1000)
	}

	componentWillUnmount(){
		clearInterval(this.timer)
	}

	render() {
		return (
			<div>
				<input type="text" ref={this.myRef}/>
				<h2>当前求和为{this.state.count}</h2>
				<button onClick={this.add}>点我+1</button>
				<button onClick={this.unmount}>卸载组件</button>
				<button onClick={this.show}>点击提示数据</button>
			</div>
		)
	}
} 
```

> 函数式组件

```jsx
function Demo(){
	//console.log('Demo');

	const [count,setCount] = React.useState(0)
	const myRef = React.useRef()

	React.useEffect(()=>{
		let timer = setInterval(()=>{
			setCount(count => count+1 )
		},1000)
		return ()=>{
			clearInterval(timer)
		}
	},[])

	//加的回调
	function add(){
		//setCount(count+1) //第一种写法
		setCount(count => count+1 )
	}

	//提示输入的回调
	function show(){
		alert(myRef.current.value)
	}

	//卸载组件的回调
	function unmount(){
		ReactDOM.unmountComponentAtNode(document.getElementById('root'))
	}

	return (
		<div>
			<input type="text" ref={myRef}/>
			<h2>当前求和为：{count}</h2>
			<button onClick={add}>点我+1</button>
			<button onClick={unmount}>卸载组件</button>
			<button onClick={show}>点我提示数据</button>
		</div>
	)
}
```



##  Fragment

* 作用:可以不用必须有一个真实的DOM根标签了

* 当你不得不使用一个`容器`去包裹dom元素--jsx语法要求,以往我们做法是直接包一层`div`

* 使用`Fragment`后可以`取代div`,但是编译后会被react丢弃,所以不会造成没必要的层级嵌套

* 效果等同于直接写一个`空标签<></>`,但是二者有区别

  `区别`:`Fragment`可以添加`key`属性作为唯一标识,而空标签一点属性都不能加

```jsx
import React, { Component,Fragment } from 'react'

export default class Demo extends Component {
	render() {
		return (
			<Fragment key={1}> 
				<input type="text"/>
				<input type="text"/>
			</Fragment>
		)
	}
}
```

## Context

一种组件间通信方式, 常用于【祖组件】与【后代组件】间通信

1) 创建Context容器对象：

```jsx
const XxxContext = React.createContext()  
```

2) 渲染子组时，外面包裹`xxxContext.Provider`, 通过value属性给后代组件传递数据：

```jsx
<xxxContext.Provider value={数据}>
		子组件
 </xxxContext.Provider>
```

3) 后代组件读取数据：`两种方法`

```jsx
//第一种方式:仅适用于类组件 
static contextType = xxxContext  // 声明接收context
this.context // 读取context中的value数据

//第二种方式: 函数组件与类组件都可以
<xxxContext.Consumer>
{
    value => ( // value就是context中的value数据
    要显示的内容
    )
}
</xxxContext.Consumer>
```

注意:在应用开发中`一般不用context`, 一般都用它的封装react插件

4)完整例子:

```jsx
//------------------- 完整例子 ------------------------------------------------
import React, { Component } from 'react'
import './index.css'
//创建Context对象
const MyContext = React.createContext()
const {Provider,Consumer} = MyContext
export default class A extends Component {

	state = {username:'tom',age:18}

	render() {
		const {username,age} = this.state
		return (
			<div className="parent">
				<h3>我是A组件</h3>
				<h4>我的用户名是:{username}</h4>
				<Provider value={{username,age}}>
					<B/>
				</Provider>
			</div>
		)
	}
}

class B extends Component {
	render() {
		return (
			<div className="child">
				<h3>我是B组件</h3>
				<C/>
			</div>
		)
	}
}

/* class C extends Component {
	//声明接收context
	static contextType = MyContext
	render() {
		const {username,age} = this.context
		return (
			<div className="grand">
				<h3>我是C组件</h3>
				<h4>我从A组件接收到的用户名:{username},年龄是{age}</h4>
			</div>
		)
	}
} */

function C(){
	return (
		<div className="grand">
			<h3>我是C组件</h3>
			<h4>我从A组件接收到的用户名:
			<Consumer>
				{value => `${value.username},年龄是${value.age}`} //也可以返回标签
			</Consumer>
			</h4>
		</div>
	)
}
```

## 组件优化 --PureComponent

**Component的2个问题**

* 只要执行setState(),即使不改变状态数据, 组件也会重新render() ==> 效率低
* 只当前组件重新render(), 就会自动重新render子组件，纵使子组件没有用到父组件的任何数据 ==> 效率低

**效率高的做法:**

只有当组件的state或props数据发生改变时才重新render()

**原因解析**

Component中的shouldComponentUpdate()总是返回true

**优化解决**

办法1: 

* `重写shouldComponentUpdate()`方法
* 比较新旧state或props数据, 如果有变化才返回true, 如果没有返回false

办法2:  

* 使用`PureComponent`
* PureComponent重写了shouldComponentUpdate(), 只有state或props数据有变化才返回true
* 注意: 
  * 只是进行state和props数据的`浅比较`, 如果只是数据对象内部数据变了, 返回false  
  * 不要直接修改state数据, 而是要`产生新数据`

项目中一般使用PureComponent来优化

**优化代码示例:**

```jsx
import React, { PureComponent } from 'react'
import './index.css'

export default class Parent extends PureComponent {

	state = {carName:"奔驰c36",stus:['小张','小李','小王']}

	addStu = ()=>{
		/* const {stus} = this.state
		stus.unshift('小刘')
		this.setState({stus}) */

		const {stus} = this.state
		this.setState({stus:['小刘',...stus]})
	}

	changeCar = ()=>{
		//this.setState({carName:'迈巴赫'})

		const obj = this.state
		obj.carName = '迈巴赫'
		console.log(obj === this.state);
		this.setState(obj)
	}

	/* shouldComponentUpdate(nextProps,nextState){
		// console.log(this.props,this.state); //目前的props和state
		// console.log(nextProps,nextState); //接下要变化的目标props，目标state
		return !this.state.carName === nextState.carName
	} */

	render() {
		console.log('Parent---render');
		const {carName} = this.state
		return (
			<div className="parent">
				<h3>我是Parent组件</h3>
				{this.state.stus}&nbsp;
				<span>我的车名字是：{carName}</span><br/>
				<button onClick={this.changeCar}>点我换车</button>
				<button onClick={this.addStu}>添加一个小刘</button>
				<Child carName="奥拓"/>
			</div>
		)
	}
}

class Child extends PureComponent {

	/* shouldComponentUpdate(nextProps,nextState){
		console.log(this.props,this.state); //目前的props和state
		console.log(nextProps,nextState); //接下要变化的目标props，目标state
		return !this.props.carName === nextProps.carName
	} */

	render() {
		console.log('Child---render');
		return (
			<div className="child">
				<h3>我是Child组件</h3>
				<span>我接到的车是：{this.props.carName}</span>
			</div>
		)
	}
}
```

## render props  ---类似vue插槽

* 如何向组件内部动态传入带内容的结构(标签)?
  * Vue中: 使用`slot`技术, 也就是通过组件标签体传入结构  `<A><B/></A>`
  * React中:
    * 使用children props: 通过组件标签体传入结构
    * 使用render props: 通过组件标签属性传入结构,而且可以携带数据，一般用render函数属性

* children props

```jsx
<A>
  <B>xxxx</B>
</A>
{this.props.children}
问题: 如果B组件需要A组件内的数据, ==> 做不到 
```

* render props

```jsx
<A render={(data) => <C data={data}></C>}></A>
A组件: {this.props.render(内部state数据)}
C组件: 读取A组件传入的数据显示 {this.props.data}
```

*示例

```jsx
import React, { Component } from 'react'
import './index.css'
import C from '../1_setState'

export default class Parent extends Component {
	render() {
		return (
			<div className="parent">
				<h3>我是Parent组件</h3>
				<A render={(name)=><C name={name}/>}/>
			</div>
		)
	}
}

class A extends Component {
	state = {name:'tom'}
	render() {
		console.log(this.props);
		const {name} = this.state
		return (
			<div className="a">
				<h3>我是A组件</h3>
				{this.props.render(name)}
			</div>
		)
	}
}

class B extends Component {
	render() {
		console.log('B--render');
		return (
			<div className="b">
				<h3>我是B组件,{this.props.name}</h3>
			</div>
		)
	}
}
```

## 错误边界

* 理解：错误边界(Error boundary)：用来捕获后代组件错误，渲染出备用页面

* 特点：

​	`只能捕获后代组件生命周期`产生的错误，`不能捕获自己组件`产生的错误和其他组件在合成事件、定时器中产生的错误

* getDerivedStateFromError配合componentDidCatch

```jsx
// 生命周期函数，一旦后台组件报错，就会触发
static getDerivedStateFromError(error) {
    console.log(error);
    // 在render之前触发
    // 返回新的state
    return {
        hasError: true,
    };
}

componentDidCatch(error, info) {
    // 统计页面的错误。发送请求发送到后台去
    console.log(error, info);
}
```

* 代码示例

```jsx
import React, { Component } from 'react'
import Child from './Child'

export default class Parent extends Component {

	state = {
		hasError:'' //用于标识子组件是否产生错误
	}

	//当Parent的子组件出现报错时候，会触发getDerivedStateFromError调用，并携带错误信息
	static getDerivedStateFromError(error){
		console.log('@@@',error);
		return {hasError:error}
	}

	componentDidCatch(){
		console.log('此处统计错误，反馈给服务器，用于通知编码人员进行bug的解决');
	}

	render() {
		return (
			<div>
				<h2>我是Parent组件</h2>
				{this.state.hasError ? <h2>当前网络不稳定，稍后再试</h2> : <Child/>}
			</div>
		)
	}
}
```

## 组件通信方式总结

* 组件间的关系：
  * 父子组件
  * 兄弟组件（非嵌套组件）
  * 祖孙组件（跨级组件）

* 几种通信方式：
  * props：
    * children props
    * render props
  * 消息订阅-发布：
       * pubs-sub、event等等
  * 集中式管理：
       * redux、dva等等
  * conText:
       * 生产者-消费者模式

* 比较好的搭配方式
  * 父子组件：props
  * 兄弟组件：消息订阅-发布、集中式管理
  * 祖孙组件(跨级组件)：消息订阅-发布、集中式管理、conText(开发用的少，封装插件用的多)
