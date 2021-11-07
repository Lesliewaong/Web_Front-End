---
title: HTML和CSS基础
abbrlink: 2eec1551
date: 2021-08-22 22:10:22
tags:
 - HTML           
 - CSS 
categories: 前端  
---

# HTML&CSS

> 软件架构

**C/S: Client/Server 客户端/服务器端**

* 在用户本地有一个客户端程序，在远程有一个服务器端程序
* QQ、迅雷...

   * 优点：
     * 用户体验好
   * 缺点：
     * 开发、安装、部署、维护 麻烦

**B/S: Browser/Server 浏览器/服务器端**

* 只需要一个浏览器，用户通过不同的网址(URL)，可以访问不同的服务器端程序
* 优点：

    * 开发、安装、部署、维护 简单
* 缺点：

    * 如果应用过大，用户的体验可能会受到影响

    * 对硬件要求过高

> 网页结构——W3C（万维网联盟）标准

- `结构`HTML用于描述页面的结构
- `表现`CSS用于控制页面中元素的样式
- `行为`JavaScript用于响应用户操作

## HTML

**HTML**(Hyper Text Markup Language):超文本标记语言

* 它负责网页三要素中的**结构**。
* HTML使用标签的形式来标识网页中的不同组成部分。
* 所谓超文本指的是**超链接**，使用超链可以让我们从一个页面跳转到另一个页面。

### 标签

```html
<html>
	<head>
		<title>哈哈，我在哪出现？</title>
	</head>
	<body>
		<h1>回乡偶书（二首）</h1>
		<h2>其一</h2>
		<h2>贺知章</h2>
		<p>少小离家老大回</p>
		<p>乡音无改鬓毛衰</p>
		<p>儿童相见不相识</p>
		<p>笑问客从何处来</p>
	</body>
</html>
```

### 注释

HTML的注释，注释中的内容会被浏览器所忽略，不会在网页中直接显示，但是可以在源码中查看注释，注释用来对代码进行解释说明的。开发中一定要养成良好的编写注释的习惯，注释要求简单明了。注释还可以将一些不希望显示的内容隐藏。**注释不能嵌套。**

```html
<html>
	<head>
		<title>这是我的第二个网页</title>
	</head>
	<body>
	
		<!-- 这个东西很重要，千万不要删-->
		<h1>这是我的第二个网页</h1>
		
		<!-- 		
		
		标签一般成对出现，但是也存在一些自结束标签		
		
		<img>
		<img />
		<input>
		<input />
		-->
		
		<!--
				<!-- 
					我是注释中的注释 注释不能嵌套
				-->

		-->		
	
	</body>
</html>
```

### 属性 

在标签中（开始标签或自结束标签）还可以设置属性。

* 属性是一个名值对（x=y）

* 属性用来设置标签中的内容如何显示

* 属性和标签名或其他属性应该使用空格隔开
* 属性不能瞎写，应该根据文档中的规定来编写，有些属性有属性值，有些没有。如果有属性值，属性值应该使用引号引起来		

```html
<html>
	<head>
		<title>标签的属性</title>
	</head>
	<body>	
		<h1>这是我的<font color="red" size='3'>第三个</font>网页！</h1>
	<body>
</html>
```

### 网页的基本结构	

```html
<!doctype html>
<html>
	<head>
	<!-- 可以通过meta标签来设置网页的字符集，避免乱码问题 -->
		<meta charset="utf-8">
		<title>网页的基本结构</title>
	</head>
	<body>
	
	<!-- 
		迭代
			网页的版本
				HTML4
				XHTML2.0
				HTML5
				...
				
			文档声明（doctype）
				- 文档声明用来告诉浏览器当前网页的版本
				- html5的文档声明
				<!doctype html>
				<!Doctype HTML>
				
				
		进制：
			十进制（日常使用）
				- 特点：满10进1
				- 计数：0 1 2 3 4 5 6 7 8 9 10 11 12 13 ... 19 20
				- 单位数字：10个 （0-9）
			
			二进制（计算机底层的进制）
				- 特点：满2进1
				- 计数：0 1 10 11 100 101 110 111
				- 单位数字：2个 （0-1）
				- 扩展：
					- 所有数据在计算机底层都会以二进制的形式保存
					- 可以将内存想象为一个有多个小格子组成的容器，每一个小格子中可以存储一个1或一个0
						这一个小格子在内存中被称为1位（bit）
						
						8bit = 1byte(字节)
						1024byte = 1kb(千字节)
						1024kb = 1mb(兆字节)
						1024mb = 1gb(吉字节)
						1024gb = 1tb(特字节)
						1024tp = 1pb
			
			八进制(很少用)
				- 特点：满8进1
				- 计数： 0 1 2 3 4 5 6 7 10 11 12 ... 17 20
				- 单位数字：8个 （0-7）
			
			十六进制(一般显示一个二进制数字时，都会转换为十六进制)
				- 特点：满16进1
				- 计数：0 1 2 3 4 5 6 7 8 9 a b c d e f 10 11 12 ... 1a 1b 1c 1d 1e 1f 20 ..
				- 单位数字：16个（0-f）
				
				
		字符编码
			李立超 -> 110000110110 （编码）
			110000110110 -> 李立超 （解码）
			
			- 所有的数据在计算机中存储时都是以二进制形式存储的，文字也不例外。
				所以一段文字在存储到内存中时，都需要转换为二进制编码
				当我们读取这段文字时，计算机会将编码转换为字符，供我们阅读
				
			- 编码
				- 将字符转换为二进制码的过程称为编码
			- 解码
				- 将二进制码转换为字符的过程称为解码
			- 字符集（charset）
			    - 编码和解码所采用的规则称为字符集
			- 乱码问题：
				- 如果编码和解码所采用的字符集不同就会出现乱码问题
			- 常见的字符集：
				ASCII
				ISO88591
				GB2312
				GBK
				UTF-8，在开发时我们使用的字符集都是UTF-8
		
	-->
	

	<body>
</html>
```

```html
<!-- 文档声明，声明当前网页的版本 -->
<!doctype html>

<!-- html的根标签（元素），网页中的所有内容都要写根元素的里边 -->
<html>

	<!-- head是网页的头部，head中的内容不会在网页中直接出现，主要用来帮助浏览器或搜索引擎来解析网页 -->
	<head>

		<!-- meta标签用来设置网页的元数据，这里meta用来设置网页的字符集，避免乱码问题 -->
		<meta charset="utf-8">
		
		<!-- title中的内容会显示在浏览器的标题栏，搜索引擎会主要根据title中的内容来判断网页的主要内容 -->
		<title>网页的标题</title>

	</head>

	<!-- body是html的子元素，表示网页的主体，网页中所有的可见内容都应该写在body里 -->
	<body>

		<!-- h1网页的一级标题 -->
		<h1>网页的大标题</h1>

	</body>

</html>
```

### 实体（转义字符）

在网页中编写的多个空格默认情况会自动被浏览器解析为一个空格。

在HTML中有些时候，我们不能直接书写一些特殊符号，比如：多个连续的空格，比如字母两侧的大于和小于号......

如果我们需要在网页中书写这些特殊的符号，则需要使用html中的实体（转义字符）。

实体的语法：

    &实体的名字;
      &nbsp; 空格
      &gt; 大于号
      &lt; 小于号
      &copy; 版权符号

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>实体</title>
</head>
<body>
<p>
    今天&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;天气真不错！
</p>
    
<p>

    a&lt;b&gt;c
</p>

</body>
</html>
```

### meta标签

 meta主要用于设置网页中的一些元数据，元数据不是给用户看。

* charset 指定网页的字符集
* name 指定的数据的名称
* content 指定的数据的内容
* keywords 表示网站的关键字，可以同时指定多个关键字，关键字间使用,隔开
* description 用于指定网站的描述，网站的描述会显示在搜索引擎的搜索的结果中

title标签的内容会作为搜索结果的超链接上的文字显示。

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <!-- 
                    <meta name="Keywords" content="网上购物,网上商城,手机,笔记本,电脑,MP3,CD,VCD,DV,相机,数					 码,配件,手表,存储卡,京东"/>
                    <meta name="keywords" content="网购,网上购物,在线购物,网购网站,网购商城,购物网站,网购中心,购					 物中心,卓越,亚马逊,卓越亚马逊,亚马逊中国,joyo,amazon">
                    <meta name="description" content="京东JD.COM-专业的综合网上购物商城,销售家电、数码通讯、电					  脑、家居百货、服装服饰、母婴、图书、食品等数万个品牌优质商品.便捷、诚信的服务，为您提供愉悦的网上					    购物体验!"/>  
     -->
     <meta name="keywords" content="HTML5,前端,CSS3">
     <meta name="description" content="这是一个非常不错的网站">
     <!--
          <meta http-equiv="refresh" content="3;url=https://www.mozilla.org"> 
        将页面重定向到另一个网站
    -->
    <!-- <meta http-equiv="refresh" content="3;url=https://www.baidu.com"> -->
    <title>Document</title>

</head>
<body>
    
</body>
</html>
```

### 语义化标签

 在网页中HTML专门用来负责网页的结构，所以在使用html标签时，应该关注的是**标签的语义**，而不是它的样式。

**标题标签：**

* h1 ~ h6 一共有六级标题
* 从h1~h6重要性递减，h1最重要，h6最不重要
* h1在网页中的重要性仅次于title标签，一般情况下一个页面中只会有一个h1
* 一般情况下标题标签只会使用到h1~h3， 很少用h4~h6
* **标题标签都是块元素**。==在页面中独占一行的元素称为块元素==（block element）。
* hgroup标签用来为标题分组，可以将一组相关的标题同时放入到hgroup

 **p标签：**

* 表示页面中的一个段落

* p也是一个块元素  

**em标签：**

* 用于表示语音语调的一个加重

* ==在页面中不会独占一行的元素称为行内元素==（inline element）**只根据内容的长度来扩展**

**strong标签：**

表示强调，重要内容！

**blockquote标签：**

 表示一个长引用

**q标签：**

表示一个短引用

**br标签：**

表示页面中的换行

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Document</title>
</head>
<body>
     <h1>一级标题</h1>
     <h2>二级标题</h2>
     <h3>三级标题</h3>
     <h4>四级标题</h4>
     <h5>五级标题</h5>
     <h6>六级标题</h6>

      <hgroup>
            <h1>回乡偶书二首</h1>
            <h2>其一</h2>
      </hgroup>
      
      <p>在p标签中的内容就表示一个段落</p>
      <p>在p标签中的内容就表示一个段落</p>

      <p>今天天气<em>真</em>不错！</p>

      <p>你今天必须要<strong>完成作业</strong>！</p>

      鲁迅说：
      <blockquote>
          这句话我是从来没有说过的！
      </blockquote>


      子曰<q>学而时习之，乐呵乐呵！</q>

      <br>
      <br>

      今天天气真不错
     
    
</body>
</html>
```

**块元素（block element）**

* 在网页中一般通过块元素来对页面进行布局

**行内元素（inline element）**

   - 行内元素主要用来包裹文字
   - 一般情况下会在块元素中放行内元素，而不会在行内元素中放块元素
   - 块元素中基本上什么都能放
   - p元素中不能放任何的块元素

浏览器在解析网页时，会自动对网页中不符合规范的内容进行修正
比如：

* 标签写在了根元素的外部
* p元素中嵌套了块元素
* 根元素中出现了除head和body以外的子元素

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Document</title>
</head>
<body>

     <p>
         <h1>哈哈</h1>
     </p>
   
    
</body>
</html>

<h1>我就要写在html标签的外部！</h1>
```

**布局标签（结构化语义标签）**

* header 表示网页的头部
* main 表示网页的主体部分(一个页面中只会有一个main)
* footer 表示网页的底部
* nav 表示网页中的导航
* aside 和主体相关的其他内容（侧边栏）
* article 表示一个独立的文章
* section 表示一个独立的区块，上边的标签都不能表示时使用section
* div 没有语义，就用来表示一个区块，目前来讲div还是我们主要的布局元素
* span 行内元素，没有任何的语义，一般用于在网页中选中文字

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Document</title>
</head>
<body>
    
     <header></header>
     <main></main>
     <footer></footer>

     <nav></nav>
     <aside></aside>
     <article></article>

     <section></section>

     <div></div>

     <span></span>
</body>
</html>
```

### 列表

列表（list）:
        1、铅笔
        2、尺子
        3、橡皮

在html中也可以创建列表，html列表一共有三种：
    1、有序列表
    2、无序列表
    3、定义列表

**有序列表**

* 使用`ol`标签来创建无序列表
* 使用`li`表示列表项 

**无序列表**

* 使用`ul`标签来创建无序列表
* 使用`li`表示列表项

**定义列表**

* 使用`dl`标签来创建一个定义列表
* 使用`dt`来表示定义的内容
* 使用`dd`来对内容进行解释说明

**列表之间可以互相嵌套**

```html
<!DOCTYPE html>
<html lang="en">

<head>
    <meta charset="UTF-8">
    <title>Document</title>
</head>

<body>

    <ul>
        <li>结构</li>
        <li>表现</li>
        <li>行为</li>
    </ul>

    <ol>
        <li>结构</li>
        <li>表现</li>
        <li>行为</li>
    </ol>


    <dl>
        <dt>结构</dt>
        <dd>结构表示网页的结构，结构用来规定网页中哪里是标题，哪里是段落</dd>
        <dd>结构表示网页的结构，结构用来规定网页中哪里是标题，哪里是段落</dd>
        <dd>结构表示网页的结构，结构用来规定网页中哪里是标题，哪里是段落</dd>
    </dl>

    <ul>
        <li>
            aa
            <ul>
                <li>aa-1</li>
                <li>aa-2
                    <ul>
                        <li>aa-1</li>
                        <li>aa-2</li>
                    </ul>
                </li>
            </ul>
        </li>
    </ul>


</body>

</html>
```

### 超链接

超链接可以让我们从一个页面跳转到其他页面，或者是当前页面的其他的位置。

使用 `a` 标签来定义超链接

超链接是也是一个**行内元素**，在a标签中可以嵌套除它自身外的任何元素

属性：

* href 指定跳转的目标路径
  * 值可以是一个外部网站的地址
  * 也可以写一个内部页面的地址
* target属性，用来指定超链接打开的位置
  * _self 默认值 在当前页面中打开超链接
  * _blank 在一个新的要么中打开超链接
* 在开发中可以将`#`作为超链接的路径的展位符使用
* 可以使用 `javascript:;` 来作为href的属性，此时点击这个超链接什么也不会发生
* 可以直接将超链接的href属性设置为#，这样点击超链接以后，页面不会发生跳转，而是转到当前页面的**顶部**的位置
* 可以跳转到页面的指定位置，只需将href属性设置 `#目标元素的id属性值`
* id属性（唯一不重复的）
  * 每一个标签都可以添加一个id属性
  * id属性就是元素的唯一标识，同一个页面中不能出现重复的id属性

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>超链接</title>
</head>
<body>
     <a href="https://www.baidu.com">超链接</a>
     <br><br>
     <!-- <a href="https://www.baidu123.com">超链接</a> -->
     <a href="07.列表.html">超链接2</a>
    
</body>
</html>
```

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <meta http-equiv="X-UA-Compatible" content="ie=edge">
    <title>Document</title>
</head>
<body>
 
    <a href="07.列表.html" target="_blank">超链接</a>

    <br><br>
    <a href="#bottom">去底部</a>

    <br><br>
    <a href="#p3">去第三个自然段</a>

    <br><br>
    

    <p>在我的后园，可以看见墙外有两株树，一株是枣树，还有一株也是枣树。 </p>
    <p>在我的后园，可以看见墙外有两株树，一株是枣树，还有一株也是枣树。</p>
    <p id="p3">在我的后园，可以看见墙外有两株树，一株是枣树，还有一株也是枣树。 </p>
    <p>在我的后园，可以看见墙外有两株树，一株是枣树，还有一株也是枣树。</p>
    <p>在我的后园，可以看见墙外有两株树，一株是枣树，还有一株也是枣树。 </p>
    <p>在我的后园，可以看见墙外有两株树，一株是枣树，还有一株也是枣树。 这上面的夜的天空，奇怪而高，我生平没有见过这样奇怪而高的天空。他仿佛要离开人间而去，使人们仰面不再看见。然而现在却非常之蓝，闪闪地䀹着几十个星星的眼，冷眼。他的口角上现出微笑，似乎自以为大有深意，而将繁霜洒在我的园里的野花草上。 我不知道那些花草真叫什么名字，人们叫他们什么名字。我记得有一种开过极细小的粉红花，现在还开着，但是更极细小了，她在冷的夜气中，瑟缩地做梦，梦见春的到来，梦见秋的到来，梦见瘦的诗人将眼泪擦在她最末的花瓣上，告诉她秋虽然来，冬虽然来，而此后接着还是春，蝴蝶乱飞，蜜蜂都唱起春词来了。她于是一笑，虽然颜色冻得红惨惨地，仍然瑟缩着。 枣树，他们简直落尽了叶子。先前，还有一两个孩子来打他们，别人打剩的枣子，现在是一个也不剩了，连叶子也落尽了。他知道小粉红花的梦，秋后要有春；他也知道落叶的梦，春后还是秋。他简直落尽叶子，单剩干子，然而脱了当初满树是果实和叶子时候的弧形，欠伸得很舒服。但是，有几枝还低亚着，护定他从打枣的竿梢所得的皮伤，而最直最长的几枝，却已默默地铁似的直刺着奇怪而高的天空，使天空闪闪地鬼䀹眼；直刺着天空中圆满的月亮，使月亮窘得发白。 鬼䀹眼的天空越加非常之蓝，不安了，仿佛想离去人间，避开枣树，只将月亮剩下。然而月亮也暗暗地躲到东边去了。而一无所有的干子，却仍然默默地铁似的直刺着奇怪而高的天空，一意要制他的死命，不管他各式各样地䀹着许多蛊惑的眼睛。 哇的一声，夜游的恶鸟飞过了。 我忽而听到夜半的笑声，吃吃地，似乎不愿意惊动睡着的人，然而四围的空气都应和着笑。夜半，没有别的人，我即刻听出这声音就在我嘴里，我也即刻被这笑声所驱逐，回进自己的房。灯火的带子也即刻被我旋高了。 后窗的玻璃上丁丁地响，还有许多小飞虫乱撞。不多久，几个进来了，许是从窗纸的破孔进来的。他们一进来，又在玻璃的灯罩上撞得丁丁地响。一个从上面撞进去了，他于是遇到火，而且我以为这火是真的。两三个却休息在灯的纸罩上喘气。那罩是昨晚新换的罩，雪白的纸，折出波浪纹的叠痕，一角还画出一枝猩红色的栀子。 猩红的栀子开花时，枣树又要做小粉红花的梦，青葱地弯成弧形了……我又听到夜半的笑声；我赶紧砍断我的心绪，看那老在白纸罩上的小青虫，头大尾小，向日葵子似的，只有半粒小麦那么大，遍身的颜色苍翠得可爱，可怜。 我打一个呵欠，点起一支纸烟，喷出烟来，对着灯默默地敬奠这些苍翠精致的英雄们。 一九二四年九月十五日。</p>
    <p>Lorem ipsum dolor sit amet, consectetur adipisicing elit. Quia quasi numquam quam molestias cumque eveniet ab nobis doloribus dolores. Nesciunt, distinctio tempore similique consequuntur nulla dolorem sapiente minus praesentium impedit.</p>


    <a href="#">这是一个新的超链接</a>

    <br><br>


    <a href="javascript:;">这是一个新的超链接</a>
    <br><br>

    <a id="bottom" href="#">回到顶部</a>
</body>
</html>
```

#### 相对路径

当我们需要跳转一个服务器内部的页面时，一般我们都会使用相对路径

相对路径都会使用`.`或`..`开头

* ./  表示当前文件所在的目录
* ../ 表示当前文件所在目录的上一级目录
* ./可以省略不写，如果不写./也不写../则就相当于写了./

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <meta http-equiv="X-UA-Compatible" content="ie=edge">
    <title>Document</title>
</head>
<body>
    <a href="./target.html">超链接1</a> 
    <br><br>
    <a href="../07.列表.html">超链接2</a>
    <br><br>
    <a href="./inner/target2.html">超链接3</a>
    <br><br>
    <a href="../outer/target3.html">超链接4</a>

</body>
</html>
```

### 图片标签

图片标签用于向当前页面中引入一个外部图片

使用`img`标签来引入外部图片，img标签是一个**自结束标签**

img这种元素属于**替换元素（块和行内元素之间，具有两种元素的特点）**

**属性：** 

* src 属性指定的是外部图片的路径（路径规则和超链接是一样的）
* alt 图片的描述，这个描述默认情况下不会显示，有些浏览器会图片无法加载时显示。搜索引擎会根据alt中的内容来识别图片，如果不写alt属性则图片不会被搜索引擎所收录。
* width 图片的宽度 (单位是像素)
* height 图片的高度
  * 宽度和高度中如果只修改了一个，则另一个会等比例缩放

**注意：**

* 一般情况在pc端，不建议修改图片的大小，需要多大的图片就裁多大
* 但是在移动端，经常需要对图片进行缩放（大图缩小）

**图片的格式：**

* jpeg(jpg)
  * 支持的颜色比较丰富，不支持透明效果，不支持动图
  * 一般用来显示照片
* gif
  * 支持的颜色比较少，支持简单透明，支持动图
  * 颜色单一的图片，动图
* png
  * 支持的颜色丰富，支持复杂透明，不支持动图
  * 颜色丰富，复杂透明图片（专为网页而生）
* webp
  * 这种格式是谷歌新推出的专门用来表示网页中的图片的一种格式
  * 它具备其他图片格式的所有优点，而且文件还特别的小
  * 缺点：兼容性不好
* base64
  * 将图片使用base64编码，这样可以将图片转换为字符，通过字符的形式来引入图片 
  * 一般都是一些需要和网页一起加载的图片才会使用base64
* 效果一样，用小的；效果不一样，用效果好的

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <meta http-equiv="X-UA-Compatible" content="ie=edge">
    <title>Document</title>
</head>
<body>

    <img src="./img/1.gif" alt="松鼠">

    <img width="200"  src="https://gimg2.baidu.com/image_search/src=http%3A%2F%2Fpic1.win4000.com%2Fwallpaper%2F3%2F513d3f96726af.jpg&refer=http%3A%2F%2Fpic1.win4000.com&app=2002&size=f9999,10000&q=a80&n=0&g=0n&fmt=jpeg?sec=1622632937&t=5a11c1eaf32663125304ae1338fffec3" alt="钢铁侠">

    
</body>
</html>
```

### 内联框架

内联框架，用于向当前页面中引入一个其他页面

* src 指定要引入的网页的路径 

* frameborder 指定内联框架的边框

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <meta http-equiv="X-UA-Compatible" content="ie=edge">
    <title>Document</title>
</head>
<body>

    <iframe src="https://www.qq.com" width="800" height="600" frameborder="0"></iframe>
    <h1>Hello</h1>

    
</body>
</html>
```

### 音视频

`audio`标签用来向页面中引入一个外部的音频文件的，音视频文件引入时，默认情况下不允许用户自己控制播放停止。

**属性：**

* controls 是否允许用户控制播放
*  autoplay 音频文件是否自动播放
  * ​	如果设置了autoplay 则音乐在打开页面时会自动播放，但是目前来讲大部分浏览器都不会自动对音乐进行播放 
* loop 音乐是否循环播放
* 除了通过src来指定外部文件的路径以外，还可以通过source来指定文件的路径

使用`video`标签来向网页中引入一个视频，使用方式和audio基本上是一样的

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <meta http-equiv="X-UA-Compatible" content="ie=edge">
    <title>Document</title>
</head>
<body>

    <!-- <audio src="./source/audio.mp3" controls autoplay loop></audio> -->
    
    <!-- <audio src="./source/audio.mp3" controls></audio> -->


    <audio controls>
        <!-- 对不起，您的浏览器不支持播放音频！请升级浏览器！ -->
        <source src="./source/audio.mp3">
        <source src="./source/audio.ogg">
        <embed src="./source/audio.mp3" type="audio/mp3" width="300" height="100">
    </audio>


    <video controls>
        <source src="./source/flower.webm">
        <source src="./source/flower.mp4">
        <embed src="./source/flower.mp4" type="video/mp4">
    </video>

    <iframe frameborder="0" src="https://v.qq.com/txp/iframe/player.html?vid=b00318l66nt" allowFullScreen="true" width="500" height="300"></iframe>


</body>
</html>
```

## CSS

### CSS简介

> 层叠样式表
>
> 网页实际上是一个多层的结构，通过CSS可以分别为网页的每一个层来设置样式,而最终我们能看到只是网页的最上边一层。
>
> 总之一句话，CSS用来设置网页中元素的样式

 使用CSS来修改元素的样式

**第一种方式(内联样式，行内样式)**

   - 在标签内部通过style属性来设置元素的样式
   - 问题：
           - 使用内联样式，样式只能对一个标签生效， 如果希望影响到多个元素必须在每一个元素中都复制一遍
           - 并且当样式发生变化时，我们必须要一个一个的修改，非常的不方便
           - ==开发时绝对不要使用内联样式==

**第二种方式（内部样式表）**

   - 将样式编写到head中的`style`标签里，然后通过CSS的**选择器**来选中元素并为其设置各种样式，可以同时为多个标签设置样式，并且修改时只需要修改一处即可全部应用
   - 内部样式表更加方便对样式进行复用
   - 问题：我们的内部样式表只能对一个网页起作用，它里边的样式**不能跨页面进行复用**

**第三种方式 （外部样式表） 最佳实践**

* 可以将CSS样式编写到一个**外部的CSS文件**中, 然后通过`link`标签来引入外部的CSS文件
* 外部样式表需要通过link标签进行引入，意味着只要想使用这些样式的网页都可以对其进行引用，使样式可以**在不同页面之间进行复用**。
* 将样式编写到外部的CSS文件中，可以使用到浏览器的**缓存机制**，从而加快网页的加载速度，提高用户的体验。

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <meta http-equiv="X-UA-Compatible" content="ie=edge">
    <title>Document</title>


    <!-- <style>

        p{
            color: green;
            font-size: 50px;
        }

    </style> -->

     <link rel="stylesheet" href="./style.css">
</head>
<body>
     <!-- <p style="color:red; font-size: 60px;">少小离家老大回，乡音无改鬓毛衰</p>

     <p style="color: red; font-size: 60px;">今天天气真不错！</p> -->

     <p>落霞与孤鹜齐飞，秋水共长天一色</p>

     <p>少小离家老大回，乡音无改鬓毛衰</p>
    
</body>
</html>
```

### CSS语法

CSS的基本语法:

​		`选择器 声明块`

**选择器**

* 通过选择器可以选中页面中的指定元素
* 比如 p 的作用就是选中页面中所有的p元素

**声明块**

* 通过声明块来指定要为元素设置的样式
* 声明块由一个一个的声明组成
* 声明是一个名值对结构 `一个样式名对应一个样式值，名和值之间以:连接，以;结尾`      

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <meta http-equiv="X-UA-Compatible" content="ie=edge">
    <title>Document</title>
    <style>
      /*      
        CSS中的注释，注释中的内容会自动被浏览器所忽略
      */

      p{
          color: red;
          font-size: 40px;
      }

      h1{
          color: green;
      }

      
    
    </style>
</head>
<body>
    <h1>我是H1</h1>
    <p>今天天气真不错！</p>
    <p>今天天气真不错！</p>
    <p>今天天气真不错！</p>
    <p>今天天气真不错！</p>
</body>
</html>
```

### 常用选择器

**元素选择器**

* 作用：根据标签名来选中指定的元素
* 语法：`标签名{}`
* 例子：p{}  h1{}  div{}

**id选择器**

* 作用：根据元素的id属性值选中一个元素
* 语法：`#id属性值{}`
* 例子：#box{} #red{}  

 **类选择器**

* 作用：根据元素的class属性值选中一组元素
* 语法：`.class属性值`

**通配选择器**

* 作用：选中页面中的所有元素
* 语法: `*`

> class是一个标签的属性，它和id类似，不同的是class可以重复使用
>
> 可以通过class属性来为元素分组
>
> 可以同时为一个元素指定多个class属性

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <meta http-equiv="X-UA-Compatible" content="ie=edge">
    <title>Document</title>
    <style>
        /* 
            将所有的段落设置为红色（字体）
           
        */
        /* p{
            color: red;
        }

        h1{
            color: green;
        } */

        /* 
            将儿童相见不相识设置红色

        */
        /* #red{
            color: red;
        } */

        /*
            将 秋水... 和 落霞... 设置为蓝色
                
        */
        /* .blue{
            color: blue;
        }

        .abc{
            font-size: 20px;
        }
        */

        /* 
            通配选择器
        */
        *{
            color: red;
        }

    
    </style>
</head>
<body>
    <h1 class="blue abc">我是标题</h1>
    <p>少小离家老大回</p>
    <p>乡音无改鬓毛衰</p>
    <p id="red">儿童相见不相识</p>
    <p>笑问客从何处来</p>

    <p class="blue">秋水共长天一色</p>
    <p class="blue">落霞与孤鹜齐飞</p>


</body>
</html>
```

### 复合选择器

**交集选择器**

* 作用：选中同时复合多个条件的元素
* 语法：`选择器1选择器2选择器3选择器n{}`
* 注意点：交集选择器中如果有元素选择器，**必须使用元素选择器开头**

**选择器分组（并集选择器）**

* 作用：同时选择多个选择器对应的元素 
* 语法：`选择器1,选择器2,选择器3,选择器n{}`  `#b1,.p1,h1,span,div.red{}`

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <meta http-equiv="X-UA-Compatible" content="ie=edge">
    <title>Document</title>
    <style>
        /* 将class为red的元素设置为红色（字体） */
        .red{
            color: red;
        }

        /* 将class为red的div字体大小设置为30px */
        /* 
            交集选择器
        */
        div.red{
            font-size: 30px;
        }

        .a.b.c{
            color: blue
        }

        /* div#box1{} */

        /*
            选择器分组（并集选择器）
         */
        h1, span{
            color: green
        }

    </style>
</head>
<body>
    <div class="red">我是div</div>

    <p class="red">我是p元素</p>

    <div class="red2 a b c">我是div2</div>

    <h1>标题</h1>

    <span>哈哈</span>

    
</body>
</html>
```

### 关系选择器

**父元素**

* 直接包含子元素的元素叫做父元素

**子元素**

* 直接被父元素包含的元素是子元素

**祖先元素**

* 直接或间接包含后代元素的元素叫做祖先元素

* 一个元素的父元素也是它的祖先元素

**后代元素**

   - 直接或间接被祖先元素包含的元素叫做后代元素
   - 子元素也是后代元素

**兄弟元素**

* 拥有相同父元素的元素是兄弟元素

==**子元素选择器**==

* 作用：选中指定父元素的指定子元素
* 语法：父元素 > 子元素

==**后代元素选择器**==

* 作用：选中指定元素内的指定后代元素
* 语法：祖先 后代

==**选择下一个兄弟**==

* 语法：前一个 + 下一个

==**选择下边所有的兄弟**==

* 语法：兄 ~ 弟

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <meta http-equiv="X-UA-Compatible" content="ie=edge">
    <title>Document</title>
    <style>
        /* 
            为div的子元素span设置一个字体颜色红色
            （为div直接包含的span设置一个字体颜色）
         */

        /* div.box > span{
            color: orange;
        } */

         /* div span{
             color: skyblue
         } */

         /* div > p > span{
             color: red;
         } */

          p + span{
              color: red;
          }


          p ~ span{
              color: red;
          }
    </style>
</head>
<body>
    <div class="box">
        我是一个div
        <p>
            我是div中的p元素
            <span>我是p元素中的span</span>
        </p>
        <div></div>
        <span>我是div中的span元素</span>
        <span>我是div中的span元素</span>
        <span>我是div中的span元素</span>
        <span>我是div中的span元素</span>

    </div>

    <span>
        我是div外的span
    </span>
</body>
</html>
```

### 属性选择器

 `[属性名]` 选择含有指定属性的元素

`[属性名=属性值]` 选择含有指定属性和属性值的元素

`[属性名^=属性值]` 选择属性值以指定值开头的元素

`[属性名$=属性值]` 选择属性值以指定值结尾的元素

`[属性名*=属性值]` 选择属性值中含有某值的元素的元素

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <meta http-equiv="X-UA-Compatible" content="ie=edge">
    <title>Document</title>

    <style>
        /* p[title]{ */
        /* p[title=abc]{ */
        /* p[title^=abc]{ */
        /* p[title$=abc]{ */
        p[title*=e]{
            color: orange;
        }
    </style>
</head>
<body>
        <p title="abc">少小离家老大回</p>
        <p title="abcdef">乡音无改鬓毛衰</p>
        <p title="helloabc">儿童相见不相识</p>
        <p>笑问客从何处来</p>
        <p>秋水共长天一色</p>
        <p>落霞与孤鹜齐飞</p>
</body>
</html>
```

### 伪类选择器

伪类（不存在的类，特殊的类）
   - **伪类用来描述一个元素的特殊状态**

        比如：第一个子元素、被点击的元素、鼠标移入的元素...

   - 伪类一般情况下都是使用`:`开头

           - `:first-child` 第一个子元素

           - `:last-child` 最后一个子元素

           - `:nth-child()` 选中第n个子元素

                特殊值：

                   - n 第n个 n的范围0到正无穷
                   - 2n 或 even 表示选中偶数位的元素
                   - 2n+1 或 odd 表示选中奇数位的元素

                以上这些伪类都是根据**所有的子元素**进行排序

           - `:first-of-type`

           - `:last-of-type`

           - `:nth-of-type()`

                这几个伪类的功能和上述的类似，不通点是他们是在**同类型元素**中进行排序

           - `:not()` 否定伪类

                将符合条件的元素从选择器中去除

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <meta http-equiv="X-UA-Compatible" content="ie=edge">
    <title>Document</title>
    <style>
        /* 
            将ul里的第一个li设置为红色
         */
        /* ul > li:first-child{
            color: red;
        } */
    
        /* ul > li:last-child{
            color: red;
        } */

        /* ul > li:nth-child(2n+1){
            color: red;
        } */

        /* ul > li:nth-child(even){
            color: red;
        } */

        /* ul > li:first-of-type{
            color: red;
        } */

        ul > li:not(:nth-of-type(3)){
            color: yellowgreen;
        }
    </style>
</head>
<body>
    <!-- ul>li*5 -->
    <ul>
        <span>我是一个span</span>
        <li>第〇个</li>
        <li>第一个</li>
        <li>第二个</li>
        <li>第三个</li>
        <li>第四个</li>
        <li>第五个</li>
    </ul>


</body>
</html>
```

### a元素的伪类

`:link` 用来表示没访问过的链接（正常的链接）

`:visited` 用来表示访问过的链接（由于隐私的原因，所以visited这个伪类只能修改链接的颜色）

`:hover` 用来表示鼠标移入的状态

`:active` 用来表示鼠标点击

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <meta http-equiv="X-UA-Compatible" content="ie=edge">
    <title>Document</title>
    <style>
        a:link{
            color: red;
            
        }
        a:visited{
            color: orange; 
            /* font-size: 50px;   */
        }
         a:hover{
             color: aqua;
             font-size: 50px;
         }
         a:active{
             color: yellowgreen;
             
         }
    
    </style>
</head>
<body>
    <a href="https://www.baidu.com">访问过的链接</a>

    <br><br>

    <a href="https://www.baidu123.com">没访问过的链接</a>

</body>
</html>
```

### 伪元素选择器

伪元素，表示页面中一些特殊的并不真实的存在的元素（特殊的位置）

伪元素使用 `::` 开头

* `::first-letter` 表示第一个字母
* `::first-line` 表示第一行
* `::selection` 表示选中的内容
* `::before` 元素的开始 
* `::after` 元素的最后
     * **before 和 after 必须结合content属性来使用**

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <meta http-equiv="X-UA-Compatible" content="ie=edge">
    <title>Document</title>

    <style>
        p{
            font-size: 20px;
        }

        p::first-letter{
            font-size: 50px;
        }

        p::first-line{
            background-color: yellow; 
        }

        p::selection{
            background-color: greenyellow;
        }

        /* div::before{
            content: 'abc';
            color: red;
        }

        div::after{
            content: 'haha';
            color: blue;
        } */

        div::before{
            content: '『';
         }

        div::after{
            content: '』';
        }

    </style>
</head>
<body>

    <!-- <q>hello</q> -->
    <div>Hello Hello How are you</div>
    
    <p>
        Lorem ipsum dolor sit amet consectetur adipisicing elit. Atque velit modi veniam nisi veritatis tempore laborum nemo ipsa itaque optio. Id odit consequatur mollitia excepturi, minus saepe nostrum vel porro.
    </p>


</body>
</html>
```

### 样式的继承

样式的继承，我们为一个元素设置的样式同时也会应用到它的后代元素上。

继承是发生在祖先和后代之间的。

 继承的设计是为了方便我们的开发，利用继承我们可以将一些通用的样式统一设置到共同的祖先元素上，这样只需设置一次即可让所有的元素都具有该样式。

注意：并不是所有的样式都会被继承。 比如：**背景相关的，布局相关等的这些样式都不会被继承。**

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <meta http-equiv="X-UA-Compatible" content="ie=edge">
    <title>Document</title>
    <style>

        /* body{
            font-size: 12px;
        } */
        
        p{
            color: red;
            background-color: orange;
        }

        div{
            color: yellowgreen
        }
    
    </style>
</head>
<body>
    <p>
        我是一个p元素
        <span>我是p元素中的span</span>
    </p>

    <span>我是p元素外的span</span>

    <div>
        我是div
        <span>
            我是div中的span
            <em>我是span中的em</em>
        </span>
    </div>
</body>
</html>
```

### 选择器的权重

样式的冲突：当我们通过不同的选择器，选中相同的元素，并且为相同的样式设置不同的值时，此时就发生了样式的冲突。

发生样式冲突时，应用哪个样式由选择器的权重（优先级）决定。

选择器的权重

* 内联样式        1,0,0,0
* id选择器        0,1,0,0
* 类和伪类选择器   0,0,1,0
* 元素选择器       0,0,0,1
* 通配选择器       0,0,0,0
* 继承的样式       没有优先级

>  比较优先级时，需要将所有的选择器的优先级进行相加计算，最后优先级越高，则越优先显示（分组选择器是单独计算的）,选择器的累加不会超过其最大的数量级，类选择器再高也不会超过id选择器。如果优先级计算后相同，此时则优先使用靠下的样式。
>
> 可以在某一个样式的后边添加 `!important` ，则此时该样式会获取到最高的优先级，甚至超过内联样式，
> 注意：在开发中这个玩意一定要慎用！

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <meta http-equiv="X-UA-Compatible" content="ie=edge">
    <title>Document</title>

    <style>

        /* #box1{
            background-color: orange;
        }

        div#box1{
            background-color: yellow;
        } */

        .d1{
            background-color: purple !important;
        }
        .red{
            background-color: red;
            /* font-size: 20px; */
        }

        

        /* div,p,span{
            background-color:yellowgreen;
        } */

         *{
             font-size: 50px;
         }

         div{
             font-size: 20px;
         }

    </style>

</head>
<body>
    <div id="box1" class="red d1 d2 d3 d4" style="background-color: chocolate;">我是一个div <span>我是div中的span</span></div>
</body>
</html>
```

### 单位

长度单位：

* 像素
  * 屏幕（显示器）实际上是由一个一个的小点点构成的
  * 不同屏幕的像素大小是不同的，像素越小的屏幕显示的效果越清晰
  * 所以同样的200px在不同的设备下显示效果不一样
* 百分比
  * 也可以将属性值设置为相对于其父元素属性的百分比
  * 设置百分比可以使子元素跟随父元素的改变而改变
* em
  * em是相对于元素的字体大小来计算的
  * 1em = 1font-size
  * em会根据字体大小的改变而改变
* rem
  * rem是相对于根元素的字体大小来计算





```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <meta http-equiv="X-UA-Compatible" content="ie=edge">
    <title>Document</title>
    <style>

        html{
            font-size: 30px;
        }

        .box1{

            width:300px;
            height: 100px;
            background-color: orange;
        }

        .box2{
            width: 50%;
            height: 50%;
            background-color:aqua; 
        }

        .box3{
            font-size: 50px;
            /* width: 10em;
            height: 10em; */
            width: 10rem;
            height: 10rem;
            background-color: greenyellow;
        }
    </style>
</head>
<body>
 	<!-- .box1 -->
    <div class="box1">

        <div class="box2"></div>

    </div>

    <div class="box3"></div>
    
</body>
</html>
```

### 颜色

颜色单位：

在CSS中可以直接使用颜色名来设置各种颜色，比如：red、orange、yellow、blue、green ... ...

但是在css中直接使用颜色名是非常的不方便

* RGB值：
  * RGB通过三种颜色的不同浓度来调配出不同的颜色
  * R red，G green ，B blue
  * 每一种颜色的范围在 0 - 255 (0% - 100%) 之间
  *  语法：`RGB(红色,绿色,蓝色)`
* RGBA:
  * 就是在rgb的基础上增加了一个a表示不透明度
  * 需要四个值，前三个和rgb一样，第四个表示不透明度
  * 1表示完全不透明   0表示完全透明  .5半透明
* 十六进制的RGB值：
  * 语法：`#红色绿色蓝色`
  * 颜色浓度通过 00-ff
  * 如果颜色两位两位重复可以进行简写  #aabbcc --> #abc
* HSL值 HSLA值
  * H 色相(0 - 360)
  * S 饱和度，颜色的浓度 0% - 100%
  * L 亮度，颜色的亮度 0% - 100%

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <meta http-equiv="X-UA-Compatible" content="ie=edge">
    <title>Document</title>
    <style>
        .box1{
            width: 100px;
            height: 100px;
            background-color: red;
            background-color: rgb(255, 0, 0);
            background-color: rgb(0, 255, 0);
            background-color: rgb(0, 0, 255);
            background-color: rgb(255,255,255);
            background-color: rgb(106,153,85);
            background-color: rgba(106,153,85,.5);
            background-color: #ff0000;
            background-color: #ffff00;
            background-color: #ff0;
            background-color: #bbffaa;
            background-color: #9CDCFE;
            background-color: rgb(254, 156, 156);
            background-color: hsla(98, 48%, 40%, 0.658);
        }
    </style>
</head>
<body>
    
    <div class="box1"></div>

</body>
</html>
```

## layout（布局）

### 文档流

文档流（normal flow）
   - 网页是一个多层的结构，一层叠着一层
   - 通过CSS可以分别为每一层来设置样式
   - 作为用户来讲只能看到最顶上一层
   - 这些层中，最底下的一层称为文档流，文档流是网页的基础（我们所创建的元素默认都是在文档流中进行排列）
   - 对于我们来元素主要有两个状态
           - 在文档流中
           - 不在文档流中（脱离文档流）

**元素在文档流中有什么特点**

**块元素**

* 块元素会在页面中独占一行(自上向下垂直排列)
* 默认宽度是父元素的全部（会把父元素撑满）
* 默认高度是被内容撑开（子元素）

**行内元素**

* 行内元素不会独占页面的一行，只占自身的大小
* 行内元素在页面中左向右水平排列，如果一行之中不能容纳下所有的行内元素，则元素会换到第二行继续自左向右排列（书写习惯一致）
* 行内元素的默认宽度和高度都是被内容撑开

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <meta http-equiv="X-UA-Compatible" content="ie=edge">
    <title>Document</title>
    <style>
        .box1{
            width: 100px;
            background-color: yellow;
        }

        .box2{
            width: 100px;
            background-color: red;
        }

        span{
            background-color: #bfa;
        }
    </style>
</head>
<body>
        <div class="box1">我是div1</div>
     <div class="box2">我是div2</div>

     <span>我是span1</span>
     <span>我是span2</span>
     <span>我是span2</span>
     <span>我是span2</span>
     <span>我是span2</span>
     <span>我是span2</span>
     <span>我是span2</span>
     <span>我是span2</span>
     <span>我是span2</span>
     <span>我是span2</span>
</body>
</html>
```

### 盒模型

盒模型、盒子模型、框模型（box model）

* CSS将页面中的所有元素都设置为了一个矩形的盒子
* 将元素设置为矩形的盒子后，对页面的布局就变成将不同的盒子摆放到不同的位置
* 每一个盒子都由一下几个部分组成：
  * 内容区（content）
  * 内边距（padding）
  * 边框（border）
  * 外边距（margin）

[![hzMVKO.gif](https://z3.ax1x.com/2021/09/11/hzMVKO.gif)](https://imgtu.com/i/hzMVKO)

**内容区（content）**

* 元素中的所有的子元素和文本内容都在内容区中排列 
* 内容区的大小由width 和 height两个属性来设置 
  * width 设置内容区的宽度
  * height 设置内容区的高度

**边框（border）**

边框属于盒子边缘，边框里边属于盒子内部，出了边框都是盒子的外部

边框的大小会影响到整个盒子的大小

要设置边框，需要至少设置三个样式：

* 边框的宽度 border-width
* 边框的颜色 border-color
* 边框的样式 border-style

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <meta http-equiv="X-UA-Compatible" content="ie=edge">
    <title>Document</title>

    <style>
        .box1{
            width: 200px;
            height: 200px;
            background-color: #bfa;
            
             border-width: 10px;
             border-color: red;
             border-style: solid;
        }
    </style>
</head>
<body>

     <div class="box1"></div>
 
</body>
</html>
```

### 盒子模型_边框

**边框的宽度 border-width**

* 默认值，一般都是 3个像素

* border-width可以用来指定四个方向的边框的宽度

  值的情况
                          四个值：上 右 下 左
                          三个值：上 左右 下
                          两个值：上下 左右
                          一个值：上下左右

* 除了border-width还有一组 border-xxx-width xxx可以是 top right bottom left，用来单独指定某一个边的宽度

**边框的颜色 border-color**

* border-color用来指定边框的颜色，同样可以分别指定四个边的边框。规则和border-width一样
* border-color也可以省略不写，如果省略了则自动使用color的颜色值

**边框的样式 border-style**

* border-style 指定边框的样式
  * solid 表示实线
  *  dotted 点状虚线
  * dashed 虚线
  * double 双线
* border-style的默认值是none 表示没有边框

**border简写属性**

* 通过该属性可以同时设置边框所有的相关样式，并且没有顺序要求
* 除了border以外还有四个 border-xxx
  * border-top
  * border-right 
  * border-bottom
  * border-left

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <meta http-equiv="X-UA-Compatible" content="ie=edge">
    <title>Document</title>
    <style>
        .box1{
            width: 200px;
            height: 200px;
            background-color: #bfa;

             /* border-width: 10px; */
             /* border-top-width: 10px;
             border-left-width: 30px; */

            color: red;

             /* border-color: orange red yellow green;
             border-color: orange; */

             /* border-style: solid dotted dashed double;
             border-style: solid; */

             /* border-width: 10px;
             border-color: orange;
             border-style: solid; */

              /* border: solid 10px orange; */
              /* border-top: 10px solid red;
              border-left: 10px solid red;
              border-bottom: 10px solid red; */

              border: 10px red solid;
              border-right: none;
        }
    </style>
</head>
<body>
    <div class="box1"></div>
</body>
</html>
```

### 盒子模型_内边距

内边距（padding）

> 一个盒子的可见框的大小，由内容区 内边距 和 边框共同决定，所以在计算盒子大小时，需要将这三个区域加到一起计算

   - 内容区和边框之间的距离是内边距
   - 一共有四个方向的内边距：
           - padding-top
           - padding-right
           - padding-bottom
           - padding-left
   - 内边距的设置会影响到盒子的大小
   - 背景颜色会延伸到内边距上
   - padding 内边距的简写属性，可以同时指定四个方向的内边距。规则和border-width 一样。

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <meta http-equiv="X-UA-Compatible" content="ie=edge">
    <title>Document</title>
    <style>
        .box1{
            width: 200px;
            height: 200px;
            background-color: #bfa;
            border: 10px orange solid;

             /* padding-top: 100px;
             padding-left: 100px;
             padding-right: 100px;
             padding-bottom: 100px; */

              padding: 10px 20px 30px 40px;
              padding: 10px 20px 30px ;
              padding: 10px 20px ;
              padding: 10px ;
        }

        .inner{
            width: 100%;
            height: 100%;
            background-color: yellow;
        }
    </style>
</head>
<body>
    <div class="box1">
        <div class="inner"></div>
    </div>
</body>
</html>
```

### 盒子模型_外边距

外边距（margin）
   - 外边距不会影响盒子可见框的大小，但是外边距会影响盒子的位置
   - 一共有四个方向的外边距：
           - margin-top 上外边距，设置一个正值，元素会向下移动
           - margin-right 默认情况下设置margin-right不会产生任何效果
           - margin-bottom 下外边距，设置一个正值，其下边的元素会向下移动
           - margin-left 左外边距，设置一个正值，元素会向右移动
   - margin也可以设置负值，如果是负值则元素会向相反的方向移动
   - 元素在页面中是按照自左向右的顺序排列的
           - 所以默认情况下如果我们设置的左和上外边距则会移动元素自身
           - 而设置下和右外边距会移动其他元素
   - margin的简写属性
           - margin 可以同时设置四个方向的外边距 ，用法和padding一样
   - margin会影响到盒子实际占用空间 

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <meta http-equiv="X-UA-Compatible" content="ie=edge">
    <title>Document</title>
    <style>
        .box1{
            width: 200px;
            height: 200px;
            background-color: #bfa;
            border: 10px red solid;

             /* margin-top: 100px;
             margin-left: 100px;
             margin-bottom: 100px; */

             /* margin-bottom: 100px; */
             /* margin-top: -100px; */
             /* margin-left: -100px; */
             /* margin-bottom: -100px; */

             /* margin-right: 0px; */

             margin: 100px;
        }

        .box2{
            width: 220px;
            height: 220px;
            background-color: yellow
        }
    </style>
</head>
<body>
    <div class="box1"></div>
    <div class="box2"></div>
</body>
</html>
```

### 盒子的水平布局

元素的水平方向的布局：

元素在其父元素中水平方向的位置由以下几个属性共同决定

* margin-left
* border-left
* padding-left
* width
* padding-right
* border-right
* margin-right

一个元素在其父元素中，水平布局必须要满足以下的等式

==margin-left+border-left+padding-left+width+padding-right+border-right+margin-right = 其父元素内容区的宽度 （必须满足）==

* 如果相加结果使等式不成立，则称为过度约束，则等式会自动调整
* 调整的情况：
  * 如果这七个值中没有为 auto 的情况，则浏览器会自动调整`margin-right`值以使等式满足
  * 这七个值中有三个值可以设置为auto `width、margin-left、maring-right`
    * 如果某个值为auto，则会自动调整为auto的那个值以使等式成立
    * 如果将一个宽度和一个外边距设置为auto，则宽度会调整到最大，设置为auto的外边距会自动为0
    * 如果将三个值都设置为auto，则外边距都是0，宽度最大
    * 如果将两个外边距设置为auto，宽度固定值，则会将外边距设置为相同的值
  * 所以我们经常利用这个特点来使一个元素在其父元素中水平居中
    `width:xxxpx;`
    `margin:0 auto;`
* 
* 













```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <meta http-equiv="X-UA-Compatible" content="ie=edge">
    <title>Document</title>
    <style>
        .outer{
            width: 800px;
            height: 200px;
            border: 10px red solid;
        }

        .inner{
            /* width: auto;  width的值默认就是auto*/
            width: 200px;
            height: 200px;
            background-color: #bfa;
            margin-right: auto;
            margin-left: auto;
            /* margin-left: 100px;
            margin-right: 400px */
          
        }
    </style>
</head>
<body>

    <div class="outer">

        <div class="inner"></div>

    </div>
    
</body>
</html>
```

### 垂直方向的布局

> 默认情况下父元素的高度被内容撑开
>
> 子元素是在父元素的内容区中排列的，如果子元素的大小超过了父元素，则子元素会从父元素中溢出
>
> 使用 overflow 属性来设置父元素如何处理溢出的子元素

可选值：

* visible，默认值 子元素会从父元素中溢出，在父元素外部的位置显示
* hidden 溢出内容将会被裁剪不会显示
* scroll 生成两个滚动条，通过滚动条来查看完整的内容
* auto 根据需要生成滚动条
* overflow-x、overflow-y

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <meta http-equiv="X-UA-Compatible" content="ie=edge">
    <title>Document</title>

    <style>
        
        .outer{
            background-color: #bfa;
            height: 600px;
          
        }

        .inner{
            width: 100px;
            background-color: yellow;
            height: 100px;
            margin-bottom: 100px;
            
        }

        .box1{
            width: 200px;
            height: 200px;
            background-color: #bfa;
            overflow: auto;

            
        }

        .box2{
            width: 100px;
            height: 400px;
            background-color: orange;
        }
    
    </style>
</head>
<body>
    <!-- <div class="outer">
        <div class="inner"></div>
        <div class="inner"></div>
    </div> -->

    <div class="box1">
            在我的后园，可以看见墙外有两株树，一株是枣树，还有一株也是枣树。 这上面的夜的天空，奇怪而高，我生平没有见过这样奇怪而高的天空。他仿佛要离开人间而去，使人们仰面不再看见。然而现在却非常之蓝，闪闪地䀹着几十个星星的眼，冷眼。他的口角上现出微笑，似乎自以为大有深意，而将繁霜洒在我的园里的野花草上。 我不知道那些花草真叫什么名字，人们叫他们什么名字。我记得有一种开过极细小的粉红花，现在还开着，但是更极细小了，她在冷的夜气中，瑟缩地做梦，梦见春的到来，梦见秋的到来，梦见瘦的诗人将眼泪擦在她最末的花瓣上，告诉她秋虽然来，冬虽然来，而此后接着还是春，蝴蝶乱飞，蜜蜂都唱起春词来了。她于是一笑，虽然颜色冻得红惨惨地，仍然瑟缩着。 枣树，他们简直落尽了叶子。先前，还有一两个孩子来打他们，别人打剩的枣子，现在是一个也不剩了，连叶子也落尽了。他知道小粉红花的梦，秋后要有春；他也知道落叶的梦，春后还是秋。他简直落尽叶子，单剩干子，然而脱了当初满树是果实和叶子时候的弧形，欠伸得很舒服。但是，有几枝还低亚着，护定他从打枣的竿梢所得的皮伤，而最直最长的几枝，却已默默地铁似的直刺着奇怪而高的天空，使天空闪闪地鬼䀹眼；直刺着天空中圆满的月亮，使月亮窘得发白。 鬼䀹眼的天空越加非常之蓝，不安了，仿佛想离去人间，避开枣树，只将月亮剩下。然而月亮也暗暗地躲到东边去了。而一无所有的干子，却仍然默默地铁似的直刺着奇怪而高的天空，一意要制他的死命，不管他各式各样地䀹着许多蛊惑的眼睛。 哇的一声，夜游的恶鸟飞过了。 我忽而听到夜半的笑声，吃吃地，似乎不愿意惊动睡着的人，然而四围的空气都应和着笑。夜半，没有别的人，我即刻听出这声音就在我嘴里，我也即刻被这笑声所驱逐，回进自己的房。灯火的带子也即刻被我旋高了。 后窗的玻璃上丁丁地响，还有许多小飞虫乱撞。不多久，几个进来了，许是从窗纸的破孔进来的。他们一进来，又在玻璃的灯罩上撞得丁丁地响。一个从上面撞进去了，他于是遇到火，而且我以为这火是真的。两三个却休息在灯的纸罩上喘气。那罩是昨晚新换的罩，雪白的纸，折出波浪纹的叠痕，一角还画出一枝猩红色的栀子。 猩红的栀子开花时，枣树又要做小粉红花的梦，青葱地弯成弧形了……我又听到夜半的笑声；我赶紧砍断我的心绪，看那老在白纸罩上的小青虫，头大尾小，向日葵子似的，只有半粒小麦那么大，遍身的颜色苍翠得可爱，可怜。 我打一个呵欠，点起一支纸烟，喷出烟来，对着灯默默地敬奠这些苍翠精致的英雄们。 一九二四年九月十五日。

    </div>
</body>
</html>
```

### 外边距的折叠

  垂直外边距的重叠（折叠）
   - 相邻的垂直方向外边距会发生重叠现象

                - 兄弟元素
                                - 兄弟元素
                    - 兄弟元素间的相邻垂直外边距会取两者之间的较大值（两者都是正值）
                    - 特殊情况：
                        - 如果相邻的外边距一正一负，则取两者的和
                        - 如果相邻的外边距都是负值，则取两者中绝对值较大的
                    
                    * 兄弟元素之间的外边距的重叠，对于开发是有利的，所以我们不需要进行处理

* 父子元素
  * 父子元素间相邻外边距，子元素的会传递给父元素（上外边距）
  * 父子外边距的折叠会影响到页面的布局，必须要进行处理

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <meta http-equiv="X-UA-Compatible" content="ie=edge">
    <title>Document</title>
    <style>
        .box1 , .box2{
            width: 200px;
            height: 200px;
            font-size: 100px;
        }

      
        .box1{
            background-color: #bfa;

            /* 设置一个下外边距 */
            margin-bottom: 100px;
        }

        .box2{
            background-color: orange;

            /* 设置一个上外边距 */
            margin-top: 100px;
        }

        .box3{
            width: 200px;
            height: 200px;
            background-color: #bfa;
            /* padding-top: 100px; */
            /* border-top: 1px #bfa solid; */
        }

        .box4{
            width: 100px;
            height: 100px;
            background-color: orange;
            margin-top: 100px;
        }
    </style>
</head>
<body>

    <div class="box3">
        <div class="box4"></div>
    </div>

    <!-- <div class="box1"></div>
    <div class="box2"></div> -->
    
</body>
</html>
```

### 行内元素的盒模型

> * 行内元素不支持设置宽度和高度
> * 行内元素可以设置padding，但是垂直方向padding不会影响页面的布局
> * 行内元素可以设置border，垂直方向的border不会影响页面的布局
> * 行内元素可以设置margin，垂直方向的margin不会影响布局

**display 用来设置元素显示的类型**

可选值：

* inline 将元素设置为行内元素
* block 将元素设置为块元素
* inline-block 将元素设置为行内块元素 （行内块，既可以设置宽度和高度又不会独占一行）
* table 将元素设置为一个表格 
* none 元素不在页面中显示

**visibility 用来设置元素的显示状态**

可选值：

* visible 默认值，元素在页面中正常显示

* hidden 元素在页面中隐藏不显示，但是依然占据页面的位置

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <meta http-equiv="X-UA-Compatible" content="ie=edge">
    <title>Document</title>
    <style>
        .s1{
            background-color: yellow;

             /* width: 100px;
             height: 100px; */

             /* padding: 100px; */

             /* border: 100px solid red; */

             margin: 100px;
        }

        .box1{
            width: 200px;
            height: 200px;
            background-color: #bfa;
        }

        a{
            display: block;

            visibility: hidden;

            width: 100px;
            height: 100px;
            background-color: orange;
        }
    </style>
</head>
<body>

    <a href="javascript:;">超链接</a>
    <a href="javascript:;">超链接</a>


    <span class="s1">我是span</span>
    <span class="s1">我是span</span>
    
    <div class="box1"></div>
</body>
</html>
```

### 默认样式

默认样式：

* 通常情况，浏览器都会为元素设置一些默认样式
* 默认样式的存在会影响到页面的布局，通常情况下编写网页时必须要去除浏览器的默认样式（PC端的页面）

重置样式表：专门用来对浏览器的样式进行重置的

* reset.css 直接去除了浏览器的默认样式
* normalize.css 对默认样式进行了统一

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <meta http-equiv="X-UA-Compatible" content="ie=edge">
    <title>Document</title>
    <!-- <link rel="stylesheet" href="./css/reset.css"> -->
    <link rel="stylesheet" href="./css/normalize.css">

    <style>

        /* body{
            margin: 0;
        }

        p{
            margin: 0;
        }

        ul{
            margin: 0;
            padding: 0;
            /* 去除项目符号 * /
            list-style:none; 
        } */

        /* *{
            margin: 0;
            padding: 0;
        } */


        .box1{
            width: 100px;
            height: 100px;
            border: 1px solid black;
        }
    </style>
</head>
<body>
    
<div class="box1"></div>

<p>我是一个段落</p>
<p>我是一个段落</p>
<p>我是一个段落</p>

<ul>
    <li>列表项1</li>
    <li>列表项2</li>
    <li>列表项3</li>
</ul>

</body>
</html>
```

### 盒子的尺寸

默认情况下，盒子可见框的大小由内容区、内边距和边框共同决定

box-sizing 用来设置盒子尺寸的计算方式（设置width和height的作用）

可选值：

* content-box 默认值，宽度和高度用来设置内容区的大小
* border-box 宽度和高度用来设置整个盒子可见框的大小
* width 和 height 指的是内容区 和 内边距 和 边框的总大小

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <meta http-equiv="X-UA-Compatible" content="ie=edge">
    <title>Document</title>
    <style>
        .box1{
            width: 100px;
            height: 100px;
            background-color: #bfa;
            padding: 10px;
            border: 10px red solid;
            
            box-sizing: border-box;
        }
    
    </style>
</head>
<body>

    <div class="box1"></div>
    
</body>
</html>
```

### 轮廓和圆角

**box-shadow 用来设置元素的阴影效果，阴影不会影响页面布局** 

* 第一个值 水平偏移量 设置阴影的水平位置 正值向右移动 负值向左移动
* 第二个值 垂直偏移量 设置阴影的水平位置 正值向下移动 负值向上移动
* 第三个值 阴影的模糊半径
* 第四个值 阴影的颜色

 **outline 用来设置元素的轮廓线**

* 用法和border一模一样
* 轮廓和边框不同的点，就是轮廓不会影响到可见框的大小

**border-radius: 用来设置圆角 圆角设置的圆的半径大小**

border-radius 可以分别指定四个角的圆角

* 四个值 左上 右上 右下 左下
* 三个值 左上 右上/左下 右下 
* 两个个值 左上/右下 右上/左下 

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <meta http-equiv="X-UA-Compatible" content="ie=edge">
    <title>Document</title>
    <style>
        .box1{
            width: 200px;
            height: 200px;
            background-color: #bfa;

           

            box-shadow: 0px 0px 50px rgba(0, 0, 0, .3) ; 
  
        }

        /* .box1:hover{
            outline: 10px red solid;
        } */

        .box2{
            width: 200px;
            height: 200px;
            background-color: orange;


            /* border-top-left-radius:  */
            /* border-top-right-radius */
            /* border-bottom-left-radius:  */
            /* border-bottom-right-radius:  */
            /* border-top-left-radius:50px 100px; */

            /* border-radius: 20px / 40px; */

            /* 将元素设置为一个圆形 */
            border-radius: 50%;
        }
    </style>
</head>
<body>

    <!-- <div class="box1"></div> -->

    <div class="box2"></div>
</body>
</html>
```

## float

### 浮动的简介

> 通过浮动可以使一个元素向其父元素的左侧或右侧移动

**使用 float 属性来设置于元素的浮动**

可选值：

* none 默认值 ，元素不浮动
* left 元素向左浮动
* right 元素向右浮动

注意，元素设置浮动以后，水平布局的等式便不需要强制成立

元素设置浮动以后，会完全从文档流中脱离，不再占用文档流的位置，所以元素下边的还在文档流中的元素会自动向上移动

**浮动的特点：**

* 浮动元素会完全脱离文档流，不再占据文档流中的位置
* 设置浮动以后元素会向父元素的左侧或右侧移动，
* 浮动元素默认不会从父元素中移出
* 浮动元素向左或向右移动时，不会超过它前边的其他浮动元素
* 如果浮动元素的上边是一个没有浮动的块元素，则浮动元素无法上移
* 浮动元素不会超过它上边的浮动的兄弟元素，最多最多就是和它一样高

简单总结：

==浮动目前来讲它的主要作用就是让页面中的元素可以水平排列，通过浮动可以制作一些水平方向的布局==  

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <meta http-equiv="X-UA-Compatible" content="ie=edge">
    <title>Document</title>
    <style>
        .box1{
            width: 400px;
            height: 200px;
            background-color: #bfa;
            float: left;
        }

        .box2{
            width: 400px;
            height: 200px;
            background-color: orange;
            float: left;
        }

        .box3{
            width: 200px;
            height: 200px;
            background-color: yellow;
            float: right;
        }
    </style>
</head>
<body>
    <div class="box1"></div>
    <div class="box2"></div>
    <div class="box3"></div>

    
</body>
</html>
```

### 浮动其他的特点

* 浮动元素不会盖住文字，文字会自动环绕在浮动元素的周围，所以我们可以利用浮动来设置文字环绕图片的效果

* 元素设置浮动以后，将会从文档流中脱离，从文档流中脱离后，元素的一些特点也会发生变化

  脱离文档流的特点：

  * 块元素：
    * 块元素不在独占页面的一行
    * 脱离文档流以后，块元素的宽度和高度默认都被内容撑开

  * 行内元素：行内元素脱离文档流以后会变成块元素，特点和块元素一样

  * 脱离文档流以后，不需要再区分块和行内了

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <meta http-equiv="X-UA-Compatible" content="ie=edge">
    <title>Document</title>
    <style>

        *{
            margin: 0;
            padding: 0;
        }

        .box1{
            width: 100px;
            height: 100px;
            background-color: #bfa;
        
            float: left;
        }

        .box2{
            background-color: yellowgreen;

            float: left;
        }

        .box3{
            background-color: orange
        }

        .s1{
            float: left;
            width: 200px;
            height: 200px;
            background-color: yellow;
        }
    </style>
</head>
<body>


    <!-- <div class="box1"></div>
    <p>
        在我的后园，可以看见墙外有两株树，一株是枣树，还有一株也是枣树。 这上面的夜的天空，奇怪而高，我生平没有见过这样奇怪而高的天空。他仿佛要离开人间而去，使人们仰面不再看见。然而现在却非常之蓝，闪闪地䀹着几十个星星的眼，冷眼。他的口角上现出微笑，似乎自以为大有深意，而将繁霜洒在我的园里的野花草上。 我不知道那些花草真叫什么名字，人们叫他们什么名字。我记得有一种开过极细小的粉红花，现在还开着，但是更极细小了，她在冷的夜气中，瑟缩地做梦，梦见春的到来，梦见秋的到来，梦见瘦的诗人将眼泪擦在她最末的花瓣上，告诉她秋虽然来，冬虽然来，而此后接着还是春，蝴蝶乱飞，蜜蜂都唱起春词来了。她于是一笑，虽然颜色冻得红惨惨地，仍然瑟缩着。 枣树，他们简直落尽了叶子。先前，还有一两个孩子来打他们，别人打剩的枣子，现在是一个也不剩了，连叶子也落尽了。他知道小粉红花的梦，秋后要有春；他也知道落叶的梦，春后还是秋。他简直落尽叶子，单剩干子，然而脱了当初满树是果实和叶子时候的弧形，欠伸得很舒服。但是，有几枝还低亚着，护定他从打枣的竿梢所得的皮伤，而最直最长的几枝，却已默默地铁似的直刺着奇怪而高的天空，使天空闪闪地鬼䀹眼；直刺着天空中圆满的月亮，使月亮窘得发白。 鬼䀹眼的天空越加非常之蓝，不安了，仿佛想离去人间，避开枣树，只将月亮剩下。然而月亮也暗暗地躲到东边去了。而一无所有的干子，却仍然默默地铁似的直刺着奇怪而高的天空，一意要制他的死命，不管他各式各样地䀹着许多蛊惑的眼睛。 哇的一声，夜游的恶鸟飞过了。 我忽而听到夜半的笑声，吃吃地，似乎不愿意惊动睡着的人，然而四围的空气都应和着笑。夜半，没有别的人，我即刻听出这声音就在我嘴里，我也即刻被这笑声所驱逐，回进自己的房。灯火的带子也即刻被我旋高了。 后窗的玻璃上丁丁地响，还有许多小飞虫乱撞。不多久，几个进来了，许是从窗纸的破孔进来的。他们一进来，又在玻璃的灯罩上撞得丁丁地响。一个从上面撞进去了，他于是遇到火，而且我以为这火是真的。两三个却休息在灯的纸罩上喘气。那罩是昨晚新换的罩，雪白的纸，折出波浪纹的叠痕，一角还画出一枝猩红色的栀子。 猩红的栀子开花时，枣树又要做小粉红花的梦，青葱地弯成弧形了……我又听到夜半的笑声；我赶紧砍断我的心绪，看那老在白纸罩上的小青虫，头大尾小，向日葵子似的，只有半粒小麦那么大，遍身的颜色苍翠得可爱，可怜。 我打一个呵欠，点起一支纸烟，喷出烟来，对着灯默默地敬奠这些苍翠精致的英雄们。 一九二四年九月十五日。
    </p> -->


    <span class="s1">我是一个span</span>
    <!-- <div class="box2">helloaaaaa</div> -->
    <!-- <div class="box3">hello</div> -->

    
</body>
</html>
```

### 网页的布局

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <meta http-equiv="X-UA-Compatible" content="ie=edge">
    <title>Document</title>
    <style>

        header, main, footer{
            width: 1000px;
            margin: 0 auto;
        }

        /* 设置头部 */
        header{
            height: 150px;
            background-color: silver;
        }

        /* 设置主体 */
        main{
            height: 500px;
            background-color: #bfa;
            margin: 10px auto;
        }

        nav, article, aside{
            float: left;
            height: 100%;
        }

        /* 设置左侧的导航 */
        nav{
            width: 200px;
            background-color: yellow;
        }

        /* 设置中间的内容 */
        article{
            width: 580px;
            background-color: orange;
            margin: 0 10px;
        }

        /* 设置右侧的内容 */
        aside{
            width: 200px;
            background-color: pink;
        }

        /* 设置底部 */
        footer{
            height: 150px;
            background-color: tomato;
        }
    </style>
</head>
<body>

    <!-- 创建头部 -->
    <header></header>

    <!-- 创建网页的主体 -->
    <main>
        <!-- 左侧导航 -->
       <nav></nav>

       <!-- 中间的内容 -->
       <article></article>

       <!-- 右边的边栏 -->
       <aside></aside>

    </main>
    
    <!-- 网页的底部 -->
    <footer></footer>
</body>
</html>
```

### 高度塌陷的问题

**高度塌陷的问题：**

在浮动布局中，父元素的高度默认是被子元素撑开的，当子元素浮动后，其会完全脱离文档流。

子元素从文档流中脱离，将会无法撑起父元素的高度，导致父元素的高度丢失。

父元素高度丢失以后，其下的元素会自动上移，导致页面的布局混乱。

所以高度塌陷是浮动布局中比较常见的一个问题，这个问题我们必须要进行处理！

**BFC(Block Formatting Context) 块级格式化环境**

   - BFC是一个CSS中的一个隐含的属性，可以为一个元素开启BFC
           - 开启BFC该元素会变成一个独立的布局区域
   - 元素开启BFC后的特点：
           - 开启BFC的元素不会被浮动元素所覆盖
           - 开启BFC的元素子元素和父元素外边距不会重叠
           - 开启BFC的元素可以包含浮动的子元素

* 可以通过一些特殊方式来开启元素的BFC：
  * 设置元素的浮动（不推荐）
  * 将元素设置为行内块元素（不推荐）
  * 将元素的overflow设置为一个非visible的值
    * 常用的方式 为元素设置 `overflow:hidden` 开启其BFC 以使其可以包含浮动元素

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <meta http-equiv="X-UA-Compatible" content="ie=edge">
    <title>Document</title>
    <style>
        .outer{
            border: 10px red solid;


             /* float: left; */
             /* display: inline-block; */
             overflow: hidden;
        }

        .inner{
            width: 100px;
            height: 100px;
            background-color: #bfa;

          
            float: left;
        }
    </style>
</head>
<body>

    <div class="outer">

        <div class="inner"></div>

    </div>

    <div style="width: 200px;height: 200px;background-color:yellow;"></div>
    
</body>
</html>
```

### BFC

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <meta http-equiv="X-UA-Compatible" content="ie=edge">
    <title>Document</title>
    <style>
        .box1{
            width: 200px;
            height: 200px;
            background-color: #bfa;
            /* float: left; */
            overflow: hidden;
        }

        .box2{
            width: 200px;
            height: 200px;
            background-color: orange;
            overflow: hidden;
        }

        .box3{
            width: 100px;
            height: 100px;
            background-color: yellow;
            margin-top: 100px;
        }
    </style>
</head>
<body>

    <div class="box1">

        <div class="box3"></div>
    </div>

    <!-- <div class="box2">

    </div> -->
    
</body>
</html>
```

### clear

如果我们不希望某个元素因为其他元素浮动的影响而改变位置，可以通过`clear`属性来清除浮动元素对当前元素所产生的影响

**clear**

   - 作用：清除浮动元素对当前元素所产生的影响
   - 可选值：
           - left 清除左侧浮动元素对当前元素的影响
           - right 清除右侧浮动元素对当前元素的影响
           - both 清除两侧中最大影响的那侧

* 原理：
  * 设置清除浮动以后，浏览器会自动为元素添加一个上外边距，以使其位置不受其他元素的影响

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <meta http-equiv="X-UA-Compatible" content="ie=edge">
    <title>Document</title>
    <style>

        div{
            font-size: 50px;
        }

        .box1{
            width: 200px;
            height: 200px;
            background-color: #bfa;
            float: left;
        }

        .box2{
            width: 400px;
            height: 150px;
            background-color: #ff0;
            float: right;
        }

        .box3{
            width: 200px;
            height: 200px;
            background-color: orange;
            /* 
                由于box1的浮动，导致box3位置上移
                    也就是box3收到了box1浮动的影响，位置发生了改变
             */

             clear: both;
        }
    </style>
</head>
<body>

    <div class="box1">1</div>
    <div class="box2">2</div>
    <div class="box3">3</div> 
    
</body>
</html>
```

### 高度塌陷的最终解决方案

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <meta http-equiv="X-UA-Compatible" content="ie=edge">
    <title>Document</title>
    <style>
        .box1{
            border: 10px red solid;

            /* overflow: hidden; */
        }

        .box2{
            width: 100px;
            height: 100px;
            background-color: #bfa;
            float: left;
        }

        .box3{
            clear: both;
        }

        .box1::after{
            content: '';
            display: block;
            clear: both;
        }
        
    </style>
</head>
<body>

    <div class="box1">
        <div class="box2"></div>
        <!-- <div class="box3"></div> -->
    </div>
    
</body>
</html>
```

### clearfix

==clearfix 这个样式可以同时解决高度塌陷和外边距重叠的问题，当你在遇到这些问题时，直接使用clearfix这个类即可==

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <meta http-equiv="X-UA-Compatible" content="ie=edge">
    <title>Document</title>
    <style>
        .box1{
            width: 200px;
            height: 200px;
            background-color: #bfa;
        }

        /* .box1::before{
            content: '';
            display: table;
        } */

        .box2{
            width: 100px;
            height: 100px;
            background-color: orange;
            margin-top: 100px;
        }

        .clearfix::before,
        .clearfix::after{
            content: '';
            display: table;
            clear: both;
        }
    </style>
</head>
<body>

    <div class="box1 clearfix">
        <div class="box2"></div>
    </div>
    
</body>
</html>
```

## position

### 定位的简介

**定位（position）**

   - 定位是一种更加高级的布局手段

   - 通过定位可以将元素摆放到页面的任意位置

   - 使用position属性来设置定位

        可选值：

        * static 默认值，元素是静止的没有开启定位
        * relative 开启元素的相对定位
        * absolute 开启元素的绝对定位
        * fixed 开启元素的固定定位
        * sticky 开启元素的粘滞定位

**相对定位：**

当元素的position属性值设置为relative时则开启了元素的相对定位

相对定位的特点：

* 元素开启相对定位以后，如果不设置偏移量元素不会发生任何的变化
* 相对定位是参照于元素在文档流中的位置进行定位的
* 相对定位会提升元素的层级
* 相对定位不会使元素脱离文档流
* 相对定位不会改变元素的性质块还是块，行内还是行内

**偏移量（offset）**

当元素开启了定位以后，可以通过偏移量来设置元素的位置

* top 
  * 定位元素和定位位置上边的距离
* bottom 
  * 定位元素和定位位置下边的距离
* 定位元素垂直方向的位置由top和bottom两个属性来控制 通常情况下我们只会使用其中一
  * top值越大，定位元素越向下移动
  * bottom值越大，定位元素越向上移动
* left
  * 定位元素和定位位置的左侧距离
* right
  * 定位元素和定位位置的右侧距离
* 定位元素水平方向的位置由left和right两个属性控制 通常情况下只会使用一个
  * left越大元素越靠右
  * right越大元素越靠左

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <meta http-equiv="X-UA-Compatible" content="ie=edge">
    <title>Document</title>
    <style>
        body{
            font-size: 60px;
        }
        .box1{
            width: 200px;
            height: 200px;
            background-color: #bfa;
        }

        .box2{
            width: 200px;
            height: 200px;
            background-color: orange;

        
            
            position: relative;

            left: 100px;
            top: -200px;

        }

        .box3{
            width: 200px;
            height: 200px;
            background-color: yellow;

        }
    </style>
</head>
<body>

    <div class="box1">1</div>
    <div class="box2">2</div>
    <div class="box3">3</div>
    
</body>
</html>
```

### 绝对定位

> 当元素的position属性值设置为absolute时，则开启了元素的绝对定位

**绝对定位的特点：**

* 开启绝对定位后，如果不设置偏移量元素的位置不会发生变化
* 开启绝对定位后，元素会从文档流中脱离
* 绝对定位会改变元素的性质，行内变成块，块的宽高被内容撑开
* 绝对定位会使元素提升一个层级
* 绝对定位元素是相对于其包含块进行定位的

 **包含块( containing block )**

* 正常情况下：包含块就是离当前元素最近的祖先块元素

* 绝对定位的包含块:
  * 包含块就是离它最近的开启了定位的祖先元素，如果所有的祖先元素都没有开启定位则根元素就是它的包含块
* html（根元素、初始包含块）

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <meta http-equiv="X-UA-Compatible" content="ie=edge">
    <title>Document</title>
    <style>
        body{
            font-size: 60px;
        }
        .box1{
            width: 200px;
            height: 200px;
            background-color: #bfa;
        }

        .box2{
            width: 200px;
            height: 200px;
            background-color: orange;

            position: absolute;
            /* left: 0;
            top: 0; */
            bottom: 0;
            right: 0;
        }

        .box3{
            width: 200px;
            height: 200px;
            background-color: yellow;

        }

        .box4{
            width: 400px;
            height: 400px;
            background-color: tomato;
            position: relative;
        }
        
        .box5{
            width: 300px;
            height: 300px;
            background-color: aliceblue;
            /* position: relative; */
        }
    </style>
</head>
<body>

    <div class="box1">1</div>

    <div class="box4">
        4
        <div class="box5">
            5
            <div class="box2">2</div>
        </div>
    </div>
    <div class="box3">3</div>
    
</body>
</html>
```



### 固定定位

> 将元素的position属性设置为fixed则开启了元素的固定定位

固定定位也是一种绝对定位，所以固定定位的大部分特点都和绝对定位一样

* 唯一不同的是固定定位永远参照于浏览器的视口进行定位
* 固定定位的元素不会随网页的滚动条滚动

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <meta http-equiv="X-UA-Compatible" content="ie=edge">
    <title>Document</title>
    <style>
        body{
            font-size: 60px;
            height: 2000px;
        }
        .box1{
            width: 200px;
            height: 200px;
            background-color: #bfa;
        }

        .box2{
            width: 200px;
            height: 200px;
            background-color: orange;

            position: fixed;

            left: 0;
            top: 0;



        }

        .box3{
            width: 200px;
            height: 200px;
            background-color: yellow;

        }

        .box4{
            width: 400px;
            height: 400px;
            background-color: tomato;

        }
        
        .box5{
            width: 300px;
            height: 300px;
            background-color: aliceblue;
        }
    </style>
</head>
<body>

    <div class="box1">1</div>

    <div class="box4">
        4
        <div class="box5">
            5
            <div class="box2">2</div>

        </div>
    </div>

    <div class="box3">3</div>

    
</body>
</html>
```

### 粘滞定位

> 当元素的position属性设置为sticky时则开启了元素的粘滞定位

粘滞定位和相对定位的特点基本一致，不同的是粘滞定位可以在元素到达某个位置时将其固定

```html
<!DOCTYPE html>
<html lang="en">

<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <meta http-equiv="X-UA-Compatible" content="ie=edge">
    <title>导航条</title>
    <link rel="stylesheet" href="./css/reset.css">
    <style>

        body{
            height: 3000px;
        }
        
        /* 设置nav的大小 */
        .nav{

            /* 设置宽度和高度 */
            width: 1210px;
            height: 48px;
            /* 设置背景颜色 */
            background-color: #E8E7E3;

            margin:100px auto;


             position: sticky;
             top: 10px;

        }

        /* 设置nav中li */
        .nav li{
            /* 设置li向左浮动，已使菜单横向排列 */
            float: left;
            /* 设置li的高度 */
            /* height: 48px; */
            /* 将文字在父元素中垂直居中 */
            line-height: 48px;

        }

        /* 设置a的样式 */
        .nav a{
            /* 将a转换为块元素 */
            display: block;
            /* 去除下划线 */
            text-decoration: none;
            /* 设置字体颜色 */
            color: #777777;
            /* 修改字体大小 */
            font-size: 18px;

            padding: 0 39px;
        }

        .nav li:last-child a{
            padding: 0 42px 0 41px;
        }

        /* 设置鼠标移入的效果 */
        .nav a:hover{
            background-color: #3F3F3F;
            color: #E8E7E3;
        }
    </style>
</head>

<body>
    <!-- 创建导航条的结构 -->
    <ul class="nav">
        <li>
            <a href="#">HTML/CSS</a>
        </li>
        <li>
            <a href="#">Browser Side</a>
        </li>
        <li>
            <a href="#">Server Side</a>
        </li>
        <li>
            <a href="#">Programming</a>
        </li>
        <li>
            <a href="#">XML</a>
        </li>
        <li>
            <a href="#">Web Building</a>
        </li>
        <li>
            <a href="#">Reference</a>
        </li>
    </ul>

</body>

</html>
```



### 绝对定位元素的布局

 **水平布局**

==left + margin-left + border-left + padding-left + width + padding-right + border-right + margin-right + right = 包含块的内容区的宽度==

当我们开启了绝对定位后:  水平方向的布局等式就需要添加`left` 和 `right` 两个值

此时规则和之前一样只是多添加了两个值

当发生过度约束：

* 如果9个值中没有 auto 则自动调整right值以使等式满足
* 如果有auto，则自动调整auto的值以使等式满足
* 可设置auto的值 `margin、width、left、right`
* 因为left 和 right的值默认是auto，所以如果不指定left和right，则等式不满足时，会自动调整这两个值

**垂直方向布局的等式的也必须要满足**

==top + margin-top/bottom + padding-top/bottom + border-top/bottom + height = 包含块的高度==

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <meta http-equiv="X-UA-Compatible" content="ie=edge">
    <title>Document</title>

    <style>
        .box1{
            width: 500px;
            height: 500px;
            background-color: #bfa;

            position: relative;
        }

        .box2{
            width: 100px;
            height: 100px;
            background-color: orange;
            position: absolute;
            margin: auto;

             left: 0;
             right: 0;

             top: 0;
             bottom: 0;
        }
    </style>
</head>
<body>

<div class="box1">
    <div class="box2"></div>
</div>
    
</body>
</html>
```



### 元素的层级

对于开启了定位元素，可以通过z-index属性来指定元素的层级

* z-index需要一个整数作为参数，值越大元素的层级越高，元素的层级越高越优先显示
* 如果元素的层级一样，则优先显示靠下的元素
*  祖先的元素的层级再高也不会盖住后代元素

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <meta http-equiv="X-UA-Compatible" content="ie=edge">
    <title>Document</title>
    <style>
        body{
            font-size: 60px;
        }
        .box1{
            width: 200px;
            height: 200px;
            background-color: #bfa;
            position: absolute;
       
             /* z-index: 3; */
        }

        .box2{
            width: 200px;
            height: 200px;
            background-color: rgba(255 , 0, 0, .3);
            position: absolute;
            top: 50px;
            left: 50px;
            /* z-index: 3; */

        }

        .box3{
            width: 200px;
            height: 200px;
            background-color: yellow;
            position: absolute;
            top: 100px;
            left: 100px;
            z-index: 3;

        }

        .box4{
            width: 100px;
            height: 100px;
            background-color: orange;
            position: absolute;
        }
    </style>
</head>
<body>

    <div class="box1">1</div>
    <div class="box2">2</div>
    <div class="box3">3
        <div class="box4">4</div>
    </div>

    
</body>
</html>
```

## font&background

### 字体

**字体相关的样式** 

*  color 用来设置字体颜色

* font-size 字体的大小

  和font-size相关的单位

  * em 相当于当前元素的一个font-size
  * rem 相对于根元素的一个font-size

* font-family 字体族（字体的格式）

  可选值：

  * serif  衬线字体
  * sans-serif 非衬线字体
  * monospace 等宽字体
  * 指定字体的类别，浏览器会自动使用该类别下的字体

  font-family 可以同时指定多个字体，多个字体间使用`,`隔开

  字体生效时优先使用第一个，第一个无法使用则使用第二个 以此类推

 **font-face**

可以将服务器中的字体直接提供给用户去使用 

问题：

* 加载速度
* 版权
* 字体格式

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <meta http-equiv="X-UA-Compatible" content="ie=edge">
    <title>Document</title>
    <style>

        @font-face {
                /* 指定字体的名字 */
            font-family:'myfont' ;
            /* 服务器中字体的路径 */
            src: url('./font/ZCOOLKuaiLe-Regular.ttf') format("truetype");
        }

        p{
            /*            
                        Microsoft YaHei,Heiti SC,tahoma,arial,Hiragino Sans GB,"\5B8B\4F53",sans-serif


            */
            color: blue;
            font-size: 40px;

            /* font-family: 'Courier New', Courier, monospace; */
            font-family: myfont;
        }
    </style>
</head>
<body>
    <p>
        今天天气真不错，Hello Hello How are you！
    </p>
</body>
</html>
```

### 图标字体（iconfont）

在网页中经常需要使用一些图标，可以通过图片来引入图标，但是图片大小本身比较大，并且非常的不灵活

所以在使用图标时，我们还可以将图标直接设置为字体，然后通过font-face的形式来对字体进行引入

这样我们就可以通过使用字体的形式来使用图标

**fontawesome 使用步骤**

* 下载 https://fontawesome.com/
* 解压
* 将css和webfonts移动到项目中
* 将all.css引入到网页中
* 使用图标字体
* 直接通过类名来使用图标字体
  `class="fas fa-bell"`
  `class="fab fa-accessible-icon"`

**通过伪元素来设置图标字体**

* 找到要设置图标的元素通过before或after选中

* 在content中设置字体的编码

* 设置字体的样式       

  `fab`
     `font-family: 'Font Awesome 5 Brands';`

  `fas`
     `font-family: 'Font Awesome 5 Free';`
     `font-weight: 900;`         

**通过实体来使用图标字体：**

`&#x图标的编码;`

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <meta http-equiv="X-UA-Compatible" content="ie=edge">
    <title>Document</title>
    <link rel="stylesheet" href="./fa/css/all.css">
</head>
<body>
 
    <i class="fas fa-bell" style="font-size:80px; color:red;"></i>
    <i class="fas fa-bell-slash"></i>
    <i class="fab fa-accessible-icon"></i>
    <i class="fas fa-otter" style="font-size: 160px; color:green;"></i>
</body>
</html>
```

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <meta http-equiv="X-UA-Compatible" content="ie=edge">
    <title>Document</title>
    <link rel="stylesheet" href="./fa/css/all.css">
    <style>
        li{
            list-style: none;
        }

        li::before{
            content: '\f1b0';
            /* font-family: 'Font Awesome 5 Brands'; */
            font-family: 'Font Awesome 5 Free';
            font-weight: 900; 
            color: blue;
            margin-right: 10px;
        }
    </style>
</head>
<body>

    <!-- <i class="fas fa-cat"></i> -->

    <ul>
        <li>锄禾日当午</li>
        <li>汗滴禾下土</li>
        <li>谁知盘中餐</li>
        <li>粒粒皆辛苦</li>
    </ul>

    <span class="fas">&#xf0f3;</span>
    
</body>
</html>
```

### 阿里的字体库

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <meta http-equiv="X-UA-Compatible" content="ie=edge">
    <title>Document</title>
    <link rel="stylesheet" href="./iconfont/iconfont.css">
    <style>
        i.iconfont{
            font-size: 100px;
        }

        p::before{
            content: '\e625';
            font-family: 'iconfont';
            font-size: 100px;
        }
    </style>
</head>
<body>

    <i class="iconfont">&#xe61c;</i>
    <i class="iconfont">&#xe622;</i>
    <i class="iconfont">&#xe623;</i>

    <i class="iconfont icon-qitalaji"></i>

    <p>Hello</p>
</body>
</html>
```

### 行高（line height）

> 行高指的是文字占有的实际高度

可以通过line-height来设置行高

* 行高可以直接指定一个大小（px em）

* 也可以直接为行高设置一个整数（如果是一个整数的话，行高将会是字体的指定的倍数）
* 行高经常还用来设置文字的行间距（行间距 = 行高 - 字体大小）
* 可以将行高设置为和高度一样的值，使单行文字在一个元素中垂直居中

**字体框**

* 字体框就是字体存在的格子，设置font-size实际上就是在设置字体框的高度
* 行高会在字体框的上下平均分配

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <meta http-equiv="X-UA-Compatible" content="ie=edge">
    <title>Document</title>
    <style>
        div{
            font-size: 50px;

            line-height: 200px;


            border: 1px red solid;

            /* line-height: 1.33; */
            /* line-height: 1; */
            /* line-height: 10 */
        }
    </style>
</head>
<body>
    
    <div>今天天气这不错 Hello hello 今天天气这不错 Hello hello 今天天气这不错 Hello hello 今天天气这不错 Hello hello</div>

</body>
</html>
```

### 字体的简写属性

> font 可以设置字体相关的所有属性

语法：

* font: 字体大小/行高 字体族
* 行高 可以省略不写 如果不写使用默认值

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <meta http-equiv="X-UA-Compatible" content="ie=edge">
    <title>Document</title>
    <style>
        div{
            border: 1px red solid;



            /* font-size: 50px;
            font-family: 'Times New Roman', Times, serif; */
            font-weight: bold;
            /* font: 50px/2  微软雅黑, 'Times New Roman', Times, serif; */
            /* font: normal normal 50px/2  微软雅黑, 'Times New Roman', Times, serif; */
            font: bold italic 50px/2  微软雅黑, 'Times New Roman', Times, serif;
            /* font:50px 'Times New Roman', Times, serif;
            line-height: 2; */

            /* font-size: 50px; */

            /* font-weight 字重 字体的加粗 
                可选值：
                    normal 默认值 不加粗
                    bold 加粗
                    100-900 九个级别（没什么用）

                font-style 字体的风格
                    normal 正常的
                    italic 斜体
            */
            /* font-weight: bold; */
            /* font-weight: 500;
            font-style: italic; */



        }
    </style>
</head>
<body>
    
    <div>今天天气真不错 Hello hello</div>
    
</body>
</html>
```

### 文本的样式

**text-align 文本的水平对齐**

可选值：

* left 左侧对齐
* right 右对齐
* center 居中对齐
* justify 两端对齐

**vertical-align 设置元素垂直对齐的方式**

可选值：

* baseline 默认值 基线对齐
* top 顶部对齐
* bottom 底部对齐
* middle 居中对齐

**text-decoration 设置文本修饰**

可选值：

* none 什么都没有
* underline 下划线
* line-through 删除线
* overline 上划线

**white-space 设置网页如何处理空白**

可选值：

* normal 正常
* nowrap 不换行
* pre 保留空白

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <meta http-equiv="X-UA-Compatible" content="ie=edge">
    <title>Document</title>
    <style>
        div{
            width: 800px;
            border: 1px red solid;

            /* text-align: justify; */

            font-size: 50px;
        }

        span{
            font-size: 20px;
            border: 1px blue solid;

             
            vertical-align:baseline; 
        }

        p{
            border: 1px red solid;

        }

        img{
            vertical-align: bottom;
        }
    </style>
</head>
<body>
    
<div>
    今天天气 Helloyx<span>真不错 Hello</span>！
</div>

    <!-- <div>
        Lorem ipsum dolor, sit amet consectetur adipisicing elit. Illo nihil iure at ab atque nostrum molestiae totam porro, dolorem maiores repudiandae molestias veritatis, eligendi laudantium incidunt dolores corporis? Quibusdam, consequatur.
    </div> -->


    <p>
       <img src="./img/an.jpg" alt=""> 
    </p>

</body>
</html>
```

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <meta http-equiv="X-UA-Compatible" content="ie=edge">
    <title>Document</title>
    <style>
        .box1{
            font-size: 50px;
            font-family: 微软雅黑;


            /* text-decoration: overline; */

            /* text-decoration: underline red dotted; */
        }

        .box2{
            width: 200px;
            white-space: nowrap;
            overflow: hidden;
            text-overflow: ellipsis;
        }
    </style>
</head>
<body>

    <div class="box2">
        Lorem ipsum dolor sit amet consectetur adipisicing elit. Consequatur, minus fugit in perspiciatis reprehenderit consequuntur aspernatur repellat cumque quidem asperiores quaerat placeat, tenetur vel veritatis deserunt numquam. Dolores, cupiditate enim.
    </div>

    <div class="box1">
        今天天气真不错
    </div>
</body>
</html>
```



### 背景

`background-color` 设置背景颜色

`background-image` 设置背景图片

* 可以同时设置背景图片和背景颜色，这样背景颜色将会成为图片的背景色
* 如果背景的图片小于元素，则背景图片会自动在元素中平铺将元素铺满
* 如果背景的图片大于元素，将会一个部分背景无法完全显示
* 如果背景图片和元素一样大，则会直接正常显示

`background-repeat` 用来设置背景的重复方式

可选值：

* repeat 默认值 ， 背景会沿着x轴 y轴双方向重复
* repeat-x 沿着x轴方向重复
* repeat-y 沿着y轴方向重复
* no-repeat 背景图片不重复

`background-position` 用来设置背景图片的位置

* 设置方式：
  * 通过 top left right bottom center 几个表示方位的词来设置背景图片的位置
  * 使用方位词时必须要同时指定两个值，如果只写一个则第二个默认就是center

* 通过偏移量来指定背景图片的位置：
  * 水平方向的偏移量 垂直方向变量

`background-clip`  设置背景的范围 

可选值：

* border-box 默认值，背景会出现在边框的下边
* padding-box 背景不会出现在边框，只出现在内容区和内边距
* content-box 背景只会出现在内容区

`background-origin` 背景图片的偏移量计算的原点

* padding-box 默认值，background-position从内边距处开始计算
* content-box 背景图片的偏移量从内容区处计算
* border-box 背景图片的变量从边框处开始计算

`background-size` 设置背景图片的大小

* 第一个值表示宽度 第二个值表示高度 

   - 如果只写一个，则第二个值默认是 auto
   - cover 图片的比例不变，将元素铺满
   - contain 图片比例不变，将图片在元素中完整显示

`background-attachment`

* 背景图片是否跟随元素移动
* 可选值：
  * scroll 默认值 背景图片会跟随元素移动
  * fixed 背景会固定在页面中，不会随元素移动

**backgound 背景相关的简写属性**

* 所有背景相关的样式都可以通过该样式来设置，并且该样式没有顺序要求，也没有哪个属性是必须写的

* background-size必须写在background-position的后边，并且使用/隔开 `background-position/background-size`

* background-origin background-clip 两个样式 ，orgin要在clip的前边

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <meta http-equiv="X-UA-Compatible" content="ie=edge">
    <title>Document</title>

    <style>
        .box1{
            width: 500px;
            height: 500px;
            
            background-color: #bfa;

            background-image: url("./img/1.png");

            background-repeat: no-repeat;

          
            /* background-position: center; */
            background-position: -50px 300px;



        }
    </style>
</head>
<body>
    <div class="box1"></div>
</body>
</html>
```

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <meta http-equiv="X-UA-Compatible" content="ie=edge">
    <title>Document</title>

    <style>
        .box1{
            width: 500px;
            height: 500px;
            overflow: auto;
            background-color: #bfa;
            background-image: url("./img/2.jpg");
            background-repeat: no-repeat;
            background-position: 0 0;
            padding: 10px;

            
            /* background-origin: border-box;
            background-clip: content-box; */

            
            background-size: contain;


        }

        .box2{
            width: 300px;
            height: 1000px;
            background-image: url('./img/1.png');
            background-repeat: no-repeat;
            background-position: 100px 100px;

            
            background-attachment: fixed;
        }

        .box3{
            border: 10px red double;
            padding: 50px;
            width: 500px;
            height: 500px;
            background: url('./img/2.jpg') #bfa  center center/contain border-box content-box no-repeat ;
        }

    </style>
</head>
<body>
    <div class="box3">

    </div>
    <!-- <div class="box1">
        <div class="box2">
            Lorem ipsum dolor sit amet, consectetur adipisicing elit. Totam aut, odio iusto accusantium ipsum aliquid omnis facere sapiente, nobis vel dicta alias ducimus. Repellat similique unde eius tempore, quia quo.
            Lorem ipsum dolor sit, amet consectetur adipisicing elit. Accusantium, accusamus quibusdam. Adipisci in dolorem qui accusantium accusamus voluptatibus magnam nesciunt minus enim quaerat! Quidem, rem. Ipsum amet praesentium enim aliquid!
            Lorem ipsum dolor sit amet consectetur adipisicing elit. Aperiam provident repellendus ipsum dolorum optio quo, iure eveniet beatae cupiditate rerum minus corporis illum aliquam illo ut quidem aliquid expedita deserunt.
        </div>
    </div> -->
</body>
</html>
```



### 渐变

通过渐变可以设置一些复杂的背景颜色，可以实现从一个颜色向其他颜色过渡的效果

！！渐变是图片，需要通过`background-image`来设置

线性渐变，颜色沿着一条直线发生变化 `linear-gradient()`

`linear-gradient(red,yellow)` 红色在开头，黄色在结尾，中间是过渡区域

线性渐变的开头，我们可以指定一个渐变的方向

* to left
* to right
* to bottom
* to top
* deg deg表示度数
* turn 表示圈

渐变可以同时指定多个颜色，多个颜色默认情况下平均分布，也可以手动指定渐变的分布情况

`repeating-linear-gradient()` 可以平铺的线性渐变

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <meta http-equiv="X-UA-Compatible" content="ie=edge">
    <title>Document</title>
    <style>
        .box1{
            width: 200px;
            height: 200px;
            /* background-color: #bfa; */
            /* background-image: linear-gradient(red,yellow,#bfa,orange); */
            /* background-image: linear-gradient(red 50px,yellow 100px, green 120px, orange 200px); */
            background-image: repeating-linear-gradient(to right ,red, yellow 50px);

        }
    </style>
</head>
<body>
    <div class="box1"></div>
</body>
</html>
```

### 径向渐变

`radial-gradient()` 径向渐变(放射性的效果)

* 默认情况下径向渐变的形状根据元素的形状来计算的
  * 正方形 --> 圆形
  * 长方形 --> 椭圆形
   * 我们也可以手动指定径向渐变的大小

        * circle
        * ellipse

* 也可以指定渐变的位置

* 语法： `radial-gradient(大小 at 位置, 颜色 位置 ,颜色 位置 ,颜色 位置)`

  * 大小：
    * circle 圆形
    * ellipse 椭圆
    * closest-side 近边	
    * closest-corner 近角
    * farthest-side 远边
    * farthest-corner 远角

  * 位置：
    * top right left center bottom

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <meta http-equiv="X-UA-Compatible" content="ie=edge">
    <title>Document</title>
    <style>
        .box1{
            width: 300px;
            height: 300px;

            background-image: radial-gradient(farthest-corner at 100px 100px, red , #bfa)
        }
    </style>
</head>
<body>
    <div class="box1"></div>
</body>
</html>
```



## HTML

### 表格

> 在现实生活中，我们经常需要使用表格来表示一些格式化数据：课程表、人名单、成绩单....
>
> 同样在网页中我们也需要使用表格，我们通过table标签来创建一个表格

在table中使用tr表示表格中的一行，有几个tr就有几行

在tr中使用td表示一个单元格，有几个td就有几个单元格

rowspan 纵向的合并单元格

colspan 横向的合并单元格

```html
<!DOCTYPE html>
<html lang="en">

<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <meta http-equiv="X-UA-Compatible" content="ie=edge">
    <title>Document</title>
</head>

<body>



    <table border="1" width='50%' align="center">
        
        <tr>
           
            <td>A1</td>
            <td>B1</td>
            <td>C1</td>
            <td>D1</td>
        </tr>
        <tr>
            <td>A2</td>
            <td>B2</td>
            <td>C2</td>
            <td rowspan="2">D2</td>
        </tr>
        <tr>
            <td>A3</td>
            <td>B3</td>
            <td>C3</td>
        </tr>
        <tr>
            <td>A4</td>
            <td>B4</td>
            <td colspan="2">C4</td>
        </tr>
    </table>

</body>

</html>
```



### 长表格

可以将一个表格分成三个部分：

* 头部 thead

* 主体 tbody

* 底部 tfoot
* th 表示头部的单元格

```html
<!DOCTYPE html>
<html lang="en">

<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <meta http-equiv="X-UA-Compatible" content="ie=edge">
    <title>Document</title>
</head>

<body>
    <table border="1" width='50%' align="center">
        <thead>
            <tr>
                <th>日期</th>
                <th>收入</th>
                <th>支出</th>
                <th>合计</th>
            </tr>
        </thead>
        <tbody>
            <tr>
                <td>2000.1.1</td>
                <td>500</td>
                <td>200</td>
                <td>300</td>
            </tr>
            <tr>
                <td>2000.1.1</td>
                <td>500</td>
                <td>200</td>
                <td>300</td>
            </tr>
            <tr>
                <td>2000.1.1</td>
                <td>500</td>
                <td>200</td>
                <td>300</td>
            </tr>
            <tr>
                <td>2000.1.1</td>
                <td>500</td>
                <td>200</td>
                <td>300</td>
            </tr>
        </tbody>
        <tfoot>
            <tr>
                <td></td>
                <td></td>
                <td>合计</td>
                <td>300</td>
            </tr>
        </tfoot>

    </table>
</body>

</html>
```



### 表格的样式

`border-spacing:` 指定边框之间的距离

`border-collapse: collapse;` 设置边框的合并

默认情况下元素在td中是垂直居中的 可以通过 `vertical-align` 来修改

如果表格中没有使用tbody而是直接使用tr，那么浏览器会自动创建一个tbody，并且将tr全都放到tbody中（tr不是table的子元素）

```html
<!DOCTYPE html>
<html lang="en">

<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <meta http-equiv="X-UA-Compatible" content="ie=edge">
    <title>Document</title>
    <style>
        table{
            width: 50%;
            border: 1px solid black;
            margin: 0 auto;

           
            /* border-spacing: 0px; */

            border-collapse: collapse;
        }

        td{
            border: 1px solid black;
            height: 100px;
            vertical-align:middle;
            text-align: center; 
        }

        
        tbody > tr:nth-child(odd){
            background-color: #bfa;
        }

        .box1{
            width: 300px;
            height: 300px;
            background-color: orange;

            /* 将元素设置为单元格 td  */
            display: table-cell;
            vertical-align: middle;

        }

        .box2{
            width: 100px;
            height: 100px;
            background-color: yellow;
            margin: 0 auto;

        }
    </style>
</head>

<body>

    <div class="box1">
        <div class="box2"></div>
    </div>
    <table>
        <tr>
            <td>学号</td>
            <td>姓名</td>
            <td>性别</td>
            <td>年龄</td>
            <td>地址</td>
        </tr>
        <tr>
            <td>1</td>
            <td>孙悟空</td>
            <td>男</td>
            <td>18</td>
            <td>花果山</td>
        </tr>
        <tr>
            <td>2</td>
            <td>猪八戒</td>
            <td>男</td>
            <td>28</td>
            <td>高老庄</td>
        </tr>
        <tr>
            <td>3</td>
            <td>沙和尚</td>
            <td>男</td>
            <td>38</td>
            <td>流沙河</td>
        </tr>
        <tr>
            <td>4</td>
            <td>唐僧</td>
            <td>男</td>
            <td>16</td>
            <td>女儿国</td>
        </tr>
        <tr>
                <td>1</td>
                <td>孙悟空</td>
                <td>男</td>
                <td>18</td>
                <td>花果山</td>
            </tr>
            <tr>
                <td>2</td>
                <td>猪八戒</td>
                <td>男</td>
                <td>28</td>
                <td>高老庄</td>
            </tr>
            <tr>
                <td>3</td>
                <td>沙和尚</td>
                <td>男</td>
                <td>38</td>
                <td>流沙河</td>
            </tr>
            <tr>
                <td>4</td>
                <td>唐僧</td>
                <td>男</td>
                <td>16</td>
                <td>女儿国</td>
            </tr>
            <tr>
                    <td>1</td>
                    <td>孙悟空</td>
                    <td>男</td>
                    <td>18</td>
                    <td>花果山</td>
                </tr>
                <tr>
                    <td>2</td>
                    <td>猪八戒</td>
                    <td>男</td>
                    <td>28</td>
                    <td>高老庄</td>
                </tr>
                <tr>
                    <td>3</td>
                    <td>沙和尚</td>
                    <td>男</td>
                    <td>38</td>
                    <td>流沙河</td>
                </tr>
                <tr>
                    <td>4</td>
                    <td>唐僧</td>
                    <td>男</td>
                    <td>16</td>
                    <td>女儿国</td>
                </tr>
    </table>
</body>

</html>
```



### 表单

 表单：

* 在现实生活中表单用于提交数据
* 在网页中也可以使用表单，网页中的表单用于将本地的数据提交给远程的服务器
* 使用form标签来创建一个表单

form的属性

* action 表单要提交的服务器的地址
* 文本框 注意：数据要提交到服务器中，必须要为元素指定一个name属性值
* 密码框
* 单选按钮
  * 像这种选择框，必须要指定一个value属性，value属性最终会作为用户的填写的值传递给服务器
  * checked 可以将单选按钮设置为默认选中
* 多选框
* 下拉列表
* 提交按钮
*  autocomplete="off" 关闭自动补全
* readonly 将表单项设置为只读，数据会提交
* disabled 将表单项设置为禁用，数据不会提交
* autofocus 设置表单项自动获取焦点

```html
<!DOCTYPE html>
<html lang="en">

<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <meta http-equiv="X-UA-Compatible" content="ie=edge">
    <title>Document</title>
</head>

<body>
   
    <form action="target.html">
        
        文本框 <input type="text" name="username">
        <br><br>
        
        密码框 <input type="password" name="password">
        <br><br>

        
        单选按钮 <input type="radio" name="hello" value="a">
        <input type="radio" name="hello" value="b" checked>
        <br><br>

        
        多选框 <input type="checkbox" name="test" value="1">
        <input type="checkbox" name="test" value="2">
        <input type="checkbox" name="test" value="3" checked>

        <br><br>

        
        <select name="haha">
            <option value="i">选项一</option>
            <option selected value="ii">选项二</option>
            <option value="iii">选项三</option>
        </select>



        <br><br>
        
        <input type="submit" value="注册">
    </form>
</body>

</html>
```

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <meta http-equiv="X-UA-Compatible" content="ie=edge">
    <title>Document</title>
</head>
<body>

    <form action="target.html">

        <input type="text" name="username" value="hello" readonly>
        <br><br>
        <input type="text" name="username" autofocus>
        <br><br>
        <input type="text" name="b">

        <br><br>

        <!-- <input type="color"> -->
        <br><br>
        <!-- <input type="email"> -->
        <br><br>

        <input type="submit">
        <!-- 重置按钮 -->
        <input type="reset">
        <!-- 普通的按钮 -->
        <input type="button" value="按钮">

        <br><br>
        

        <button type="submit">提交</button>
        <button type="reset">重置</button>
        <button type="button">按钮</button>
    </form>
    
</body>
</html>
```

## animation

### 过渡（transition）

> 通过过渡可以指定一个属性发生变化时的切换方式
>
> 通过过渡可以创建一些非常好的效果，提升用户的体验

`transition-property`: 指定要执行过渡的属性  

* 多个属性间使用,隔开 
* 如果所有属性都需要过渡，则使用all关键字
* 大部分属性都支持过渡效果，注意过渡时必须是从一个有效数值向另外一个有效数值进行过渡

`transition-duration`: 指定过渡效果的持续时间 时间单位：s 和 ms  1s = 1000ms

`transition-timing-function`: 过渡的时序函数 指定过渡的执行的方式 

可选值： https://cubic-bezier.com

* ease 默认值，慢速开始，先加速，再减速

* linear 匀速运动

* ease-in 加速运动

* ease-out 减速运动

* ease-in-out 先加速 后减速

* cubic-bezier() 来指定时序函数

* steps() 分步执行过渡效果

  可以设置一个第二个值：

  end ， 在时间结束时执行过渡(默认值)

  start ， 在时间开始时执行过渡

`transition-delay`: 过渡效果的延迟，等待一段时间后在执行过渡

==transition 可以同时设置过渡相关的所有属性，只有一个要求，如果要写延迟，则两个时间中第一个是持续时间，第二个是延迟== 

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <meta http-equiv="X-UA-Compatible" content="ie=edge">
    <title>Document</title>

    <style>
        *{
            margin: 0;
            padding: 0;
        }

        .box1{
            width: 800px;
            height: 800px;
            background-color: silver;
            overflow: hidden;
        }

        .box1 div{
            width: 100px;
            height: 100px;
            margin-bottom: 100px;
            margin-left: 0;
            
        }

        .box2{
            background-color: #bfa;
            /* margin-left: auto; */
            /* transition:all 2s; */
            

             
            /* transition-property: height , width; */
            /* transition-property: all; */

             
             /* transition-duration: 100ms, 2s; */
             /* transition-duration: 2s; */

            
             /* transition-timing-function: cubic-bezier(.24,.95,.82,-0.88); */
             /* transition-timing-function: steps(2, start); */


             
             /* transition-delay: 2s; */
             

             transition:2s margin-left 1s cubic-bezier(.24,.95,.82,-0.88);
        }

        .box3{
            background-color: orange;
            transition-property: all;
            transition-duration: 2s;
        }

        .box1:hover div{
            /* width: 200px;
            height: 200px; */
            /* background-color: orange; */
            margin-left: 700px;
        }
    </style>

</head>
<body>

    <div class="box1">
        <div class="box2"></div>
        <div class="box3"></div>
    </div>
    
</body>
</html>
```

### 动画

 动画和过渡类似，都是可以实现一些动态的效果，

不同的是过渡需要在某个属性发生变化时才会触发

动画可以自动触发动态效果

设置动画效果，必须先要设置一个关键帧，关键帧设置了动画执行每一个步骤      

`animation-name`: 要对当前元素生效的关键帧的名字   

`animation-duration`: 动画的执行时间

`animation-iteration-count` 动画执行的次数  可选值：次数 、infinite 无限执行

`animation-direction` 指定动画运行的方向

可选值：

* normal 默认值  从 from 向 to运行 每次都是这样 
* reverse 从 to 向 from 运行 每次都是这样 
* alternate 从 from 向 to运行 重复执行动画时反向执行
* alternate-reverse 从 to 向 from运行 重复执行动画时反向执行

`animation-play-state`: 设置动画的执行状态 

可选值：

* running 默认值 动画执行
* paused 动画暂停

 `animation-fill-mode`: 动画的填充模式

可选值：

* none 默认值 动画执行完毕元素回到原来位置
* forwards 动画执行完毕元素会停止在动画结束的位置
* backwards 动画延时等待时，元素就会处于开始位置
* both 结合了forwards 和 backwards

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <meta http-equiv="X-UA-Compatible" content="ie=edge">
    <title>Document</title>

    <style>
        *{
            margin: 0;
            padding: 0;
        }

        .box1{
            width: 800px;
            height: 800px;
            background-color: silver;
            overflow: hidden;
        }

        .box1 div{
            width: 100px;
            height: 100px;
            margin-bottom: 100px;
            margin-left: 10px;
            
        }

        .box2{
            background-color: #bfa;
            

            /* 设置box2的动画 */       
            /* animation-name: test; */

            /* animation-duration: 4s; */

            

            /* 动画的延时 */
            /* animation-delay: 2s; */

            /* animation-timing-function: ease-in-out; */

          
            /* animation-iteration-count: 1; */

           
            /* animation-direction: alternate-reverse; */

            
            /* animation-play-state: paused; */

            
            /* animation-fill-mode: both; */
            animation: test 2s 2 1s alternate;

            
        }

        .box1:hover div{
            animation-play-state: paused;
        }

       
        @keyframes test {
            /* from表示动画的开始位置 也可以使用 0% */
            from{
                margin-left: 0;
                background-color: orange;
            } 

            /* to动画的结束位置 也可以使用100%*/
            to{
                background-color: red;
                margin-left: 700px;
            }
        }
    </style>

</head>
<body>

    <div class="box1">
        <div class="box2"></div>
        <!-- <div class="box3"></div> -->
    </div>
    
</body>
</html>
```

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <meta http-equiv="X-UA-Compatible" content="ie=edge">
    <title>Document</title>
    <style>

        .outer{
            height: 500px;
            border-bottom: 10px black solid;
            margin: 50px auto;
            overflow: hidden;
        }
        .outer div{
            float: left;
            width: 100px;
            height: 100px;
            border-radius: 50%;
            background-color: #bfa;
            animation: ball .5s forwards linear infinite alternate;
        }

        div.box2{
            background-color: orange;
            animation-delay: .1s;
        }

        div.box3{
            background-color: yellow;
            animation-delay: .2s;
        }

        div.box4{
            background-color: yellowgreen;
            animation-delay: .3s;
        }

        div.box5{
            background-color: blue;
            animation-delay: .4s;
        }
        div.box6{
            background-color: pink;
            animation-delay: .5s;
        }
        div.box7{
            background-color: tomato;
            animation-delay: .6s;
        }
        div.box8{
            background-color: skyblue;
            animation-delay: .7s;
        }
        div.box9{
            background-color: chocolate;
            animation-delay: .8s;
        }

        /* 创建小球下落的动画 */
        @keyframes ball {
            from{
                margin-top: 0;
            }

            to{
                margin-top: 400px;
            }

            /* 2                                    to{
                margin-top: 400px;
                animation-timing-function: ease-in;
            }

            40%{
                margin-top: 100px;
            }

            80%{
                margin-top: 200px;
            } */

        }
    </style>
</head>
<body>

    <div class="outer">
        <div class="box1"></div>
        <div class="box2"></div>
        <div class="box3"></div>
        <div class="box4"></div>
        <div class="box5"></div>
        <div class="box6"></div>
        <div class="box7"></div>
        <div class="box8"></div>
        <div class="box9"></div>
    </div>
    
</body>
</html>
```



### 变形、

变形就是指通过CSS来改变元素的形状或位置

* 变形不会影响到页面的布局

* transform 用来设置元素的变形效果

**平移：**

* translateX() 沿着x轴方向平移
* translateY() 沿着y轴方向平移
* translateZ() 沿着z轴方向平移
* 平移元素，百分比是相对于自身计算的

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <meta http-equiv="X-UA-Compatible" content="ie=edge">
    <title>Document</title>
    <style>
        body{
            background-color: rgb(236, 236, 236);
        }
        .box1{
            width: 200px;
            height: 200px;
            background-color: #bfa;
            margin: 0 auto;
            margin-top: 200px;

           
            /* transform: translateY(-100px); */
            transform: translateX(100%);
        }

        /* .box2{
            width: 200px;
            height: 200px;
            background-color: orange;
            margin: 0 auto;
        } */

        .box3{
            background-color: orange;
            position: absolute;
            /* 
                这种居中方式，只适用于元素的大小确定
            top: 0;
            left: 0;
            bottom: 0;
            right: 0;
            margin: auto; */

            left: 50%;
            top: 50%;
            transform: translateX(-50%) translateY(-50%);
          
        }

        .box4, .box5{
            width: 220px;
            height: 300px;
            background-color: #fff;
            float: left;
            margin: 0 10px;
            transition:all .3s;
        }

        .box4:hover,.box5:hover{
            transform: translateY(-4px);
            box-shadow: 0 0 10px rgba(0, 0, 0, .3)
        }
    </style>
</head>
<body>

    <div class="box1"></div>

    <div class="box2"></div>

    <!-- <div class="box3">
        aaaa
    </div> -->

    <div class="box4">

    </div>

    <div class="box5">
        
        </div>
    
</body>
</html>
```



### z轴平移

z轴平移，调整元素在z轴的位置，正常情况就是调整元素和人眼之间的距离，

距离越大，元素离人越近

z轴平移属于立体效果（近大远小），默认情况下网页是不支持透视，如果需要看见效果

必须要设置网页的视距

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <meta http-equiv="X-UA-Compatible" content="ie=edge">
    <title>Document</title>
    <style>
        html{
            /* 设置当前网页的视距为800px，人眼距离网页的距离 */
            perspective: 800px;
        }

        body{
            border: 1px red solid;
            background-color: rgb(241, 241, 241);
        }
        .box1{
            width: 200px;
            height: 200px;
            background-color: #bfa;
            margin: 200px auto;
            

            transition:2s;
        }

        body:hover .box1{
            transform: translateZ(800px);
        }
    </style>
</head>
<body>

    <div class="box1"></div>
    
</body>
</html>
```



### 旋转

通过旋转可以使元素沿着x y 或 z旋转指定的角度

* rotateX()
* rotateY()
* rotateZ()

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <meta http-equiv="X-UA-Compatible" content="ie=edge">
    <title>Document</title>
    <style>
        html{
            perspective: 800px;
        }

        body{
            border: 1px red solid;
            background-color: rgb(241, 241, 241);
        }
        .box1{
            width: 320px;
            height: 320px;
            background-color: #bfa;
            margin: 200px auto;

            transition:2s;
        }

        body:hover .box1{
 
            /* transform: rotateZ(.25turn); */
            /* transform: rotateY(180deg) translateZ(400px); */
            /* transform: translateZ(400px) rotateY(180deg) ; */
            transform: rotateY(180deg);
            /* 是否显示元素的背面 */
            backface-visibility: hidden;


        }
    </style>
</head>
<body>

    <div class="box1">
        <img src="an.jpg" alt="">
    </div>
    
</body>
</html>
```



### 缩放

对元素进行缩放的函数：

* scaleX() 水平方向缩放
* scaleY() 垂直方向缩放
* scale() 双方向的缩放

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <meta http-equiv="X-UA-Compatible" content="ie=edge">
    <title>Document</title>
    <style>
        html{
            perspective:800px;
            
        }
        .box1{
            width: 100px;
            height: 100px;
            background-color: #bfa;
            transition:2s;
            margin: 100px auto;


            /* 变形的原点 默认值 center*/
            /* transform-origin:20px 20px;  */
        }

        .box1:hover{
            transform:scale(2)
        }


        .img-wrapper{
            width: 200px;
            height: 200px;
            border: 1px red solid;
            overflow: hidden;
        }

        img{
            transition: .2s;
        }

        .img-wrapper:hover img{
            transform:scale(1.2);
        }

    </style>
</head>
<body>
    
    <div class="box1"></div>

    <div class="img-wrapper">
        <img src="an.jpg" width="100%">
    </div>


</body>
</html>
```



## less

### less简介

> less是一门css的预处理语言

* less是一个css的增强版，通过less可以编写更少的代码实现更强大的样式，添加了许多的新特性：像对变量的支持、对mixin的支持... ...

* less的语法大体上和css语法一致，但是less中增添了许多对css的扩展，所以浏览器无法直接执行less代码，要执行必须向将less转换为css，然后再由浏览器执行 `VSCode插件：Easy LESS`

### less语法

* 结构更加写的更加清晰

  ```less
  .box1{
      background-color: #bfa;
  
      .box2{
          background-color: #ff0;
  
          .box4{
              color: red;
          }
      }
  
      .box3{
          background-color: orange;
      }
  }
  ```

* 注释

  ```less
  // less中的单行注释，注释中的内容不会被解析到css中`
  /*
    css中的注释，内容会被解析到css文件中
  */
  ```

* 变量

  * 在变量中可以存储一个任意的值,并且我们可以在需要时，任意的修改变量中的值

  * 变量的语法： `@变量名`

  * 作为类名，或者一部分值使用时必须以 `@{变量名}` 的形式使用

  * 变量发生重名时，会优先使用比较近的变量

  * 可以在变量声明前就使用变量(不建议)

  * 新版语法

    ```less
    div{
        width: 300px;
        height: $width;
    }
    ```

* & 表示外层的父元素

* `:extend()` 对当前选择器扩展指定选择器的样式（选择器分组）

  ```less
  .p1{
      width: 100px;
      height: 200px;
  }
  .p2:extend(.p1){
      color: red;
  }
  ```

* Mixins 混合

  * 直接对指定的样式进行引用，这里就相当于将p1的样式在这里进行了复制

    ```less
    .p3{
        .p1;
    }
    ```

  * 使用类选择器时可以在选择器后边添加一个括号，这时我们实际上就创建了一个mixin

    ```less
    .p4(){
        width: 100px;
        height: 100px;
    }
    
    .p5{
        .p4;
    }
    ```

  * 在混合函数中可以直接设置变量，调用混合函数，按顺序（或指定名称）传递参数，有默认值时可以不全部传值

    ```less
    .test(@w:100px,@h:200px,@bg-color:red){
        width: @w;
        height: @h;
        border: 1px solid @bg-color;
    }
    
    div{
        //调用混合函数，按顺序传递参数
        // .test(200px,300px,#bfa);
        .test(300px);
        // .test(@bg-color:red, @h:100px, @w:300px);
    }
    ```

    

### JSON设置

[![hzMeqe.png](https://z3.ax1x.com/2021/09/11/hzMeqe.png)](https://imgtu.com/i/hzMeqe)

[![hzMZrD.png](https://z3.ax1x.com/2021/09/11/hzMZrD.png)](https://imgtu.com/i/hzMZrD)

[![hzMAxK.png](https://z3.ax1x.com/2021/09/11/hzMAxK.png)](https://imgtu.com/i/hzMAxK)

[![hzMk26.png](https://z3.ax1x.com/2021/09/11/hzMk26.png)](https://imgtu.com/i/hzMk26)

## flex

### 弹性盒

**flex(弹性盒、伸缩盒)**

* 是CSS中的又一种布局手段，它主要用来**代替浮动**来完成页面的布局
* flex可以使元素具有弹性，让元素可以跟随页面的大小的改变而改变

**弹性容器**

* 要使用弹性盒，必须先将一个元素设置为弹性容器
* 我们通过 display 来设置弹性容器
  * `display:flex` 设置为块级弹性容器
  * `display:inline-flex` 设置为行内的弹性容器

**弹性元素**

* 弹性容器的子元素是弹性元素（弹性项）

* 弹性元素可以同时是弹性容器

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <meta http-equiv="X-UA-Compatible" content="ie=edge">
    <title>Document</title>
    <style>
        *{
            margin: 0;
            padding: 0;
            list-style: none;
        }

        ul{
            width: 500px;
            border: 10px red solid;
            /* 将ul设置为弹性容器 */
            display: flex;

            flex-direction: row;
        }

        li{
            width: 200px;
            height: 100px;
            background-color: #bfa;
            font-size: 50px;
            text-align: center;
            line-height: 100px;

            /* flex-grow: 1; */


            flex-shrink: 0;

            
        }
        li:nth-child(1){
            flex-grow: 0;
            flex-shrink: 1;
        }

        li:nth-child(2){
            background-color: pink;
            /* flex-grow: 2; */
            flex-shrink: 2;
        }

        li:nth-child(3){
            background-color: orange;
            /* flex-grow: 3; */
            flex-shrink: 3;
        }
    </style>
</head>
<body>
   
     <ul>
         <li>1</li>
         <li>2</li>
         <li>3</li>
     </ul>

</body>
</html>
```

### 弹性容器的样式

`flex-direction` 指定容器中弹性元素的排列方式

> 主轴：弹性元素的排列方向称为主轴
>
> 侧轴：与主轴垂直方向的称为侧轴

可选值：

* row 默认值，弹性元素在容器中水平排列（左向右） 主轴 自左向右
* row-reverse 弹性元素在容器中反向水平排列（右向左） 主轴 自右向左
* column 弹性元素纵向排列（自上向下）
* column-reverse 弹性元素方向纵向排列（自下向上）

`flex-wrap`: 设置弹性元素是否在弹性容器中自动换行

可选值：

* nowrap 默认值，元素不会自动换行
* wrap 元素沿着辅轴方向自动换行
* wrap-reverse 元素沿着辅轴反方向换行

`flex-flow`:  wrap 和 direction 的简写属性 

`justify-content`  如何分配主轴上的空白空间（主轴上的元素如何排列）

可选值：

* flex-start 元素沿着主轴起边排列
* flex-end 元素沿着主轴终边排列
* center 元素居中排列
* space-around 空白分布到元素两侧
* space-between 空白均匀分布到元素间
* space-evenly 空白分布到元素的单侧

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <meta http-equiv="X-UA-Compatible" content="ie=edge">
    <title>Document</title>
    <style>
        *{
            margin: 0;
            padding: 0;
            list-style: none;
        }

        ul{
            width: 800px;
            border: 10px red solid;
          /* 设置ul为弹性容器 */
            display: flex;

            /* flex-direction: column; */

 

            /* flex-wrap: wrap-reverse; */

          
            /* flex-flow: row wrap; */


            /* justify-content: center; */
        }

        li{
            width: 200px;
            height: 100px;
            background-color: #bfa;
            font-size: 50px;
            text-align: center;
            line-height: 100px;
            flex-shrink: 0;


            
        }
        /* li:nth-child(1){
        } */

        li:nth-child(2){
            background-color: pink;
        }

        li:nth-child(3){
            background-color: orange;
        }
    </style>
</head>
<body>
    

     <ul>
         <li>1</li>
         <li>2</li>
         <li>3</li>
     </ul>

</body>
</html>
```

`align-items`: 元素在辅轴上如何对齐 元素间的关系

可选值：

* stretch 默认值，将元素的长度设置为相同的值
* flex-start 元素不会拉伸，沿着辅轴起边对齐
* flex-end 沿着辅轴的终边对齐
* center 居中对齐
* baseline 基线对齐

`align-content`: 辅轴空白空间的分布

`align-self`: 用来覆盖当前弹性元素上的align-items（弹性元素属性）

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <meta http-equiv="X-UA-Compatible" content="ie=edge">
    <title>Document</title>
    <style>
        *{
            margin: 0;
            padding: 0;
            list-style: none;
        }

        ul{
            width: 600px;
            height: 800px;
            border: 10px red solid;
          /* 设置ul为弹性容器 */
            display: flex;

            /* flex-direction: column; */

          
            /* flex-wrap: wrap-reverse; */

            /* flex-flow:  wrap 和 direction 的简写属性 */
            flex-flow: row wrap;


            /* justify-content: center; */

           

             /* justify-content: center; */
             align-items: flex-start;


            
             align-content: space-between;
            
        }

        li{
            width: 200px;
            background-color: #bfa;
            font-size: 50px;
            text-align: center;
            line-height: 100px;
            flex-shrink: 0;


            
        }
        li:nth-child(1){
           
            align-self: stretch;
        }

        li:nth-child(2){
            background-color: pink;
        }

        li:nth-child(3){
            background-color: orange;
        }

        li:nth-child(4){
            background-color: yellow;
        }

        li:nth-child(5){
            background-color: chocolate;
        }
    </style>
</head>
<body>
    

     <ul>
         <li>1</li>
         <li>
             2
            <div>2</div>
         </li>
         <li>
             3
             <div>3</div>
             <div>3</div>
        </li>

        <li>1</li>

        <li>
                2
               <div>2</div>
            </li>
     </ul>

</body>
</html>
```



### 弹性元素的样式

`flex-grow: 1;` 指定弹性元素的伸展的系数

* 当父元素有多余空间的时，子元素如何伸展
* 父元素的剩余空间，会按照比例进行分配

`flex-shrink: 1;` 弹性元素的缩减系数

* 缩减系数的计算方式比较复杂
* 缩减多少是根据 缩减系数 和 元素大小来计算

`flex-basis` 指定的是元素在主轴上的基础长度

* 如果主轴是 横向的 则 该值指定的就是元素的宽度
* 如果主轴是 纵向的 则 该值指定的是就是元素的高度
* 默认值是 auto，表示参考元素自身的高度或宽度
* 如果传递了一个具体的数值，则以该值为准

flex 可以设置弹性元素所有的三个样式  `flex 增长 缩减 基础;`

* initial "flex: 0 1 auto".
* auto  "flex: 1 1 auto"
* none "flex: 0 0 auto" 弹性元素没有弹性

 `order` 决定弹性元素的排列顺序

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <meta http-equiv="X-UA-Compatible" content="ie=edge">
    <title>Document</title>
    <style>
        *{
            margin: 0;
            padding: 0;
            list-style: none;
        }

        ul{
            width: 900px;
            border: 10px red solid;
            /* 设置弹性盒 */
            display: flex;
        
        }

        li{
            width: 200px;
            height: 100px;
            background-color: #bfa;
            font-size: 50px;
            text-align: center;
            line-height: 100px;

          
            /* flex-grow: 1; */

          
            /* flex-shrink: 1; */

            
            /* flex-basis: auto; */

           
            flex: initial;

            
        }
        li:nth-child(1){
            order: 2;
        }

        li:nth-child(2){
            background-color: pink;
            /* flex-grow: 2; */
            order: 3;
        }

        li:nth-child(3){
            background-color: orange;
            /* flex-grow: 3; */
            order: 1;
        }
    </style>
</head>
<body>
    

     <ul>
         <li>1</li>
         <li>2</li>
         <li>3</li>
     </ul>

</body>
</html>
```



### 像素

屏幕是由一个一个发光的小点构成，这一个个的小点就是像素

分辨率：1920 x 1080 说的就是屏幕中小点的数量

在前端开发中像素要分成两种情况讨论：CSS像素 和 物理像素

* 物理像素，上述所说的小点点就属于物理像素
* CSS像素，编写网页时，我们所用像素都是CSS像素
  * 浏览器在显示网页时，需要将CSS像素转换为物理像素然后再呈现
  *  一个css像素最终由几个物理像素显示，由浏览器决定：默认情况下在pc端，一个css像素 = 一个物理像素

**视口（viewport）**

视口就是屏幕中用来显示网页的区域

* 可以通过查看视口的大小，来观察CSS像素和物理像素的比值
  * 默认情况下：视口宽度 1920px（CSS像素） 1920px（物理像素） 此时，css像素和物理像素的比是1:1
  * 放大两倍的情况：视口宽度 960px（CSS像素） 1920px（物理像素） 此时，css像素和物理像素的比是1:2

* 我们可以通过改变视口的大小，来改变CSS像素和物理像素的比值

### 移动端

在不同的屏幕，单位像素的大小是不同的，像素越小屏幕会越清晰

24寸 1920x1080

i6 4.7寸 750 x 1334

智能手机的像素点 远远小于 计算机的像素点

**问题：一个宽度为900px的网页在iphone6中要如何显示呢？**

默认情况下，移动端的网页都会将视口设置为980像素（css像素）

以确保pc端网页可以在移动端正常访问，但是如果网页的宽度超过了980，移动端的浏览器会自动对网页缩放以完整显示网页

所以基本大部分的pc端网站都可以在移动端中正常浏览，但是往往都不会有一个好的体验。

为了解决这个问题，大部分网站都会专门为移动端设计网页

### 移动端页面

移动端默认的视口大小是980px(css像素)，默认情况下，移动端的像素比就是 980/移动端宽度 （980/750）

如果我们直接在网页中编写移动端代码，这样在980的视口下，像素比是非常不好，导致网页中的内容非常非常的小

编写移动页面时，必须要确保有一个比较合理的像素比：

1css像素 对应 2个物理像素

1css像素 对应 3个物理像素

**可以通过meta标签来设置视口大小**

每一款移动设备设计时，都会有一个最佳的像素比，

一般我们只需要将像素比设置为该值即可得到一个最佳效果

将像素比设置为最佳像素比的视口大小我们称其为完美视口

将网页的视口设置为完美视口

```html
<meta name="viewport" content="width=device-width, initial-scale=1.0">
```

结论：以后再写移动端的页面，就把上边这个玩意先写上

### vw适配

不同的设备完美视口的大小是不一样的

* iphone6 -- 375
* iphone6plus -- 414

由于不同设备视口和像素比不同，所以同样的375个像素在不同的设备下意义是不一样

比如在iphone6中 375就是全屏，而到了plus中375就会缺一块

所以在移动端开发时，就不能再使用px来进行布局了

**vw 表示的是视口的宽度（viewport width）**

* 100vw = 一个视口的宽度
* 1vw = 1%视口宽度

vw这个单位永远相当于视口宽度进行计算

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <meta http-equiv="X-UA-Compatible" content="ie=edge">
    <title>Document</title>
    <style>
        *{
            margin: 0;
            padding: 0;
        }

        html{
            /* 
                网页中字体大小最小是12px，不能设置一个比12像素还小的字体
                    如果我们设置了一个小于12px的字体，则字体自动设置为12

                0.1333333vw = 1px

                5.3333vw = 40px
            */
            font-size: 5.3333vw;
        }

        .box1{
            /* 
                rem
                    - 1 rem = 1 html的字体大小
                    - 1 rem = 40 px(设计图)
            */
            width: 18.75rem;
            height: 0.875rem;
            background-color: #bfa;
        }
    </style>
</head>
<body>

    <!-- 
        48 x 35
     -->
     <div class="box1"></div>
    
</body>
</html>
```

### 响应式布局

网页可以根据不同的设备或窗口大小呈现出不同的效果

使用响应式布局，可以使一个网页适用于所有设备

**响应布局的关键就是 媒体查询**

通过媒体查询，可以为不同的设备，或设备不同状态来分别设置样式

使用媒体查询

语法： `@media 查询规则{}`
媒体类型：

* all 所有设备
* print 打印设备
* screen 带屏幕的设备
* speech 屏幕阅读器

                    - 可以使用`,`连接多个媒体类型，这样它们之间就是一个或的关系

可以在媒体类型前添加一个only，表示只有。only的使用主要是为了兼容一些老版本浏览器

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <meta http-equiv="X-UA-Compatible" content="ie=edge">
    <title>Document</title>
    <style>
      
        /* @media print,screen{
            body{
                background-color: #bfa;
            }
        } */

        @media only screen {
            body{
                background-color: #bfa;
            }
        }
    </style>
</head>
<body>
    
</body>
</html>
```

### 媒体查询

媒体特性：

* width 视口的宽度
* height 视口的高度 
* min-width 视口的最小宽度（视口大于指定宽度时生效）
* max-width 视口的最大宽度（视口小于指定宽度时生效）

样式切换的分界点，我们称其为断点，也就是网页的样式会在这个点时发生变化

一般比较常用的断点

* 小于768 超小屏幕 max-width=768px
* 大于768 小屏幕   min-width=768px
* 大于992 中型屏幕 min-width=992px
* 大于1200 大屏幕  min-width=1200px

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <meta http-equiv="X-UA-Compatible" content="ie=edge">
    <title>Document</title>
    <style>

         /* @media (max-width: 500px){
             body{
                background-color: #bfa;
             }
         } */

         @media only screen and (min-width: 500px) and (max-width:700px){
             body{
                background-color: #bfa;
             }
         }
    </style>
</head>
<body>
    
</body>
</html>
```

