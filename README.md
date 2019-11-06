# 基础面试题
### （一）基础模块

1. 什么是html？

- HTML不是真正的编程语言，是一种标记语言，用来结构化和语义化想在web网站上的内容，由一系列元素组成，这些元素可以封装内容中担任不同工作的各个部分。

2. 什么是css?

- 样式表语言，可以选择性的为html文档的元素添加样式。

3. 行内元素和块级元素的具体区别是什么？行内元素的padding和margin可以设置吗？

   **块级元素**：

   - 块级元素独占一行，表现为从另一行开始，其后的元素也必须另起一行显示
   - 宽度、高度、内边距和外边距都可控制

   **行内元素：**

   - 和相邻的行内元素在同一行显示
   - 宽度、高度、内边距的top/bottom/(padding-top/padding-bottom)和外边距的top/bottom(margin-top/margin-bottom)都不可改变，文字或图片的大小可以设置

4. 简述一下对HTML语义化的理解

   - HTML语义化让页面的内容结构化，结构更清晰，便于浏览器、搜索引擎的解析
   - 即使在没有css样式的情况下也能以一种文档格式显示，容易阅读
   - 搜索引擎的爬虫依赖于HTML来标记确定上下文和各个关键字的权重，有利于SEO
   - 让阅读源代码的人更容易将网站分块，便于阅读、维护和理解

5. rgba()和opacity设置透明度的区别是什么？

   - 两者都能实现透明效果
   - opacity作用域元素，以及元素内的所有内容的透明度
   - rgba()只作用于元素的颜色或其背景色。(设置rgba的透明元素的子元素不会继承透明的效果)

6. DOCTYPE的作用

   - `<!DOCTYPE>`声明位于文档的最前面，处于html标签之前，告诉浏览器以何种模式来渲染文档。
   - 严格模式的排版和JS运作模式是以该浏览器支持的最高标准执行。
   - 在混杂模式中，页面以宽松的向后兼容的方式显示。模拟老式浏览器的行为以防止站点无法工作。
   - DOCTYPE不存在或者格式不正确会导致文档以混杂模式呈现。

7. 说说你对浏览器内核的理解？都有哪些常见的浏览器内核？

   - 渲染引擎，负责对网页语法的解释并渲染网页。
   - 浏览器内核就是浏览器采用的渲染引擎，渲染引擎决定了浏览器如何显示网页的内容以及页面的格式信息。不同浏览器内核对网页编写语法的解释有所不同，因此同一网页在不同的内核浏览器里的渲染效果也可能不同，这就是网页编写者需在不同内核的浏览器中测试网页显示效果的原因。
   - 常见浏览器内核：
     - Trident：IE，MaxThon，TT，World，360，搜狗浏览器等
     - Gecko：Netscape6及以上版本，FF，MozillaSuite/SeaMonkey
     - Presto：Opera7及以上。现为Blink。
     - Webkit：Safari，Chrome等。Chrome的Blink(WebKit的分支)。
     - EdgeHTML：MicroSoft Edge。删掉了几乎所有的IE私有特性。

8. CSS选择器权重如何加算？

   - 0 0 0 0
   - id选择器：                     0,1,0,0
   - 属性选择器：                 0,0,1,0
   - 标签选择器或伪元素：  0,0,0,1
   - 通配符*                           0,0,0,0
   - 内联样式                         1,0,0,0
   - !important优先级最高

9. 对Web标准及W3C的理解与认识

   - 标签闭合、标签小写、不乱嵌套、提高搜索机器人搜索几率、使用外挂css和js脚本、结构行为表现分离。
   - 文件下载与页面加载速度更快、内容能被更多的用户访问、内容能被更广泛的设备所访问、更少的代码和组件
   - 容易维护、改版方便，不需要变动页面内容、提供打印版本而不需要复制内容、提高网站易用性

10. CSS中优雅降级和渐进增强有什么区别？

    - 优雅降级  针对最高级，最完善的浏览器来设计网站
    - 渐进增强  关注内容本身

11. 对BFC规范的理解有哪些？

    - Block Formatting Context 指块级格式化上下文
      - 独立的渲染区域，只有Block-level box参与，它规定了内部的Block-level Box如何布局，且与这个区域外部毫不相干。
    - 布局规则：
      - 内部的Box会在垂直方向，一个接一个的放置
      - Box垂直方向的距离由margin决定。属于同一个BFC的两个相邻Box的margin会发生重叠
      - 每个元素的margin， box的左边，与包含块border box的左边相接触。即便存在浮动也是如此。
      - BFC的区域不会与float box 重叠。
      - BFC就是页面上的一个隔离的独立容器，容器里面的子元素不会影响到外面的元素。反之亦如此。
      - 计算BFC的高度时，浮动元素也参与计算
    - 哪些元素会生成BFC：
      - 根元素
      - float属性不为none
      - position为absolute或fixed
      - display为inline-block，table-cell，table-caption，flex，inline-flex
      - overflow不为visible

12. 清除浮动的方法

- 父级div定义height

- 父级div手动定义height，就能解决父级div无法自动获取到高度的问题。只适合高度固定的布局。

- 结尾处加空div标签  clear:both;

  - 在浮动元素的后面添加一个空的div兄弟元素，利用css提供的clear:both清除浮动，让父级div能自动获取到高度，如果页面浮动布局多，就要增加很多空div，感觉很不好。

- 父级div定义伪类after和zoom

  ```css
  .clearfix: after{
    content: '';
    display: block;
    visibility: hidden;
  	height: 0;
    line-height: 0;
    clear: both;
  }
  .clearfix {
    zoom: 1;
  }
  ```

- 父级div定义overflow:hidden

  - 超出盒子部分会被隐藏

- 双伪元素法：

  ```css
  .clearfix:before, .clearfix:after {
    content: '';
    display: block;
  	clear: both;
  }
  .clearfix {
    zoom: 1;
  }
  ```

## （二）实际工作部分

1. HTML常见兼容性问题

   - 双边距BUG

     - float引起的，使用display

   - IE的3像素问题

     - 使用浮动引起的，使用display:inline -3px解决

   - 超链接hover后失效

     - 使用正确的书写顺序  link visited hover active

   - ie6 和 ie7 ，z-index不起作用

     - 给父级添加position:relative，在第一个relative属性加上一个层级(z-index: 1;)

   - png透明

     - 使用js代码改

   - ie6不兼容Min-height最小高度

     - 使用!important 解决

   - select 在 ie6 下遮盖问题

     - 使用iframe嵌套解决

   - 为什么没有办法定义1px左右的宽度容器

     - ie6默认的行高造成的，使用over:hidden;zoom:0.08;line-height:1px;

   - ie5-8不支持opacity

     ```css
     .opacity {
       opacity:0.4;
       filter: alpha(opacity=60);//ie5-ie7
       -ms-filter: 'progid:DXImageTransform.Microsoft.Alpha(Opacity=60)';//ie8
     }
     ```

   - ie6不支持PNG透明背景

     - ie6下使用gif图片

2. 描述一个‘reset’的css文件并如何使用它。'normalize.css'？不同之处在哪？

   - 重置样式，不同的浏览器对一些元素有不同的默认样式，如果不处理，在不同的浏览器下会存在必要的风险，或者有更加戏剧性的情况发生。
   - 用normalize重置文件，它没有重置所有的样式风格，它提供了一套合理的默认样式值。既能让众多浏览器达到一致和合理，又不扰乱其他的东西。
   - 无法做每一个复位重置。它处理了一个永远都不用考虑的怪癖，像HTML的audio元素不一致或line-height不一致。

3. BFC是什么？

   - 块级格式化上下文，一个创建了新的BFC的盒子是独立布局的，盒子内元素的布局不会影响盒子外面的元素。在同一个BFC中的两个相邻的盒子在垂直方向发生**margin重叠**的问题
   - BFC是指浏览器中创建了一个独立的渲染区域，该区域内所有元素的布局不会影响到区域外元素的布局，这个渲染区域只对块级元素起作用。

4. 怎样实现三栏布局，两边宽度固定，中间自适应？

   ```php+HTML
   <!DOCTYPE html>
   <html lang="en">
   <head>
   	<meta charset="UTF-8">
   	<title>Document</title>
   	<style>
   		* {
   			margin: 0;
   			padding: 0;
   		}
   		#left {
   			width: 200px;
   			height: 200px;
   			position: absolute;
   			left: 0;
   			top: 0;
   			background-color: blue;
   		}
   		#right {
   			width: 150px;
   			height: 200px;
   			position: absolute;
   			right: 0;
   			top: 0;
   			background-color: red;
   		}
   		#middle {
   			height: 200px;
   			padding-left: 200px;
   			padding-right: 150px;
   			background-color: aqua;
   			word-break: break-word;
   		}
   		
   	</style>
   </head>
   <body>
   	
   <div class="content">
   	<div id="left">
   	我是左边的
   </div>
   <div id="middle">
   	中间的
   </div>
   <div id="right">
   	我是右边的
   </div>
   
   
   </div>
   </body>
   </html>
   ```

5. 精灵图的优点和缺点

   - 把网页中很多小背景整合到一张图片文件中，再利用CSS
     的‘background-image’，'background-reprat'，'background-position'的组合进行背景图显示及定位，达到显示某一部分背景图的效果。
   - 优点：
     - 减少图片的体积
     - 减少网页的http请求次数，加快网页加载速度
     - 解决图片命名的困扰
     - 更换风格方便
   - 缺点：
     - 在高分辨率的屏幕下的自适应页面，如果图片不够宽，很容易出现背景断裂
     - 开发时候麻烦
     - 维护时候麻烦
     - 不能随意改变大小和颜色

## （三）JavaScript基础模块

1. JS中有哪些数据类型？

   - 简单数据类型、
     - number、boolean、string、null、undefined
   - 复杂数据类型
     - Array、Object

2. `==`和`===`区别

   - 前者会自动转换类型，后者不会
   - 前者比较的是值，后者比较的是值和类型

3. JS中的常用内置对象

   - Arguments 函数参数集合

     - arguments[] 函数参数的数组
     - Arguments 一个函数的参数和其他属性
     - Arguments.callee 当前正在运行的函数
     - Arguments.length 传递给函数的参数的个数

   - Array数组

     - length  动态获取数组长度
     - join()    将一个数组拼接成字符串，返回一个字符串
     - reverse()  将数组中各元素颠倒顺序
     - delete  只能删除数组元素的值，所占空间还在，总长度没变(arr.length)
     - shift()  删除数组中的第一个元素
     - pop()  删除数组中的最后一个匀速
     - push() 在数组最后添加元素
     - unshift() 在数组最前面添加元素
     - concat() 连接数组，传入两个数组
     - slice() 从已有的数组中返回选定的元素。
     - sort() 对数组元素进行排序
     - splice() 插入、删除或替换数组的元素
     - toLocalString()  把数组转换为本地数组，并返回结果
     - toString()   把数组转换为字符串，并返回结果
     - toSource()  返回该对象的源代码
     - valueOf()  返回数组对象的原始值

   - Boolean布尔对象

     - toSource()  返回该对象的源代码
     - toString()   把逻辑值转换为字符串，并返回结果
     - valueOf()  返回Boolean对象的原始值

   - Error异常对象

     - message 可以读取的错误消息  
     - name 错误的类型  
     - TypeError 当一个值的类型错误时，抛出该异常
     - URIError 由URl的编码和解码方法抛出
     - SyntaxError 抛出该错误用来通知语法错误
     - Error.toString( ) 把Error 对象转换成字符串

   - Function函数构造器

     - Function.apply( ) 将函数作为一个对象的方法调用
     - Function.arguments[] 传递给函数的参数
     - Function.call( ) 将函数作为对象的方法调用
     - Function.caller 调用当前函数的函数
     - Function.length 已声明的参数的个数
     - Function.prototype 对象类的原型
     - Function.toString( ) 把函数转换成字符串

   - Number数值对象

     - Number 对象是原始数值的包装对象。
     - Math.PI 圆周率。
     - Math.abs() 绝对值。
     - Math.ceil() 向上取整(整数加 1，小数去掉)。
     - Math.floor() 向下取整(直接去掉小数)。
     - Math.round() 四舍五入。
     - Math.pow(x，y) 求 x的y次方。
     - Math.sqrt() 求平方根。

   - Object基础对象

     - [`Object.assign()`](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/Object/assign)

       通过复制一个或多个对象来创建一个新的对象。

     - [`Object.create()`](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/Object/create)

       使用指定的原型对象和属性创建一个新对象。

     - Object 含有所有 JavaScript 对象的特性的超类

     - [`Object.prototype.constructor`](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/Object/constructor)

       特定的函数，用于创建一个对象的原型。

     - Object.hasOwnProperty( ) 检查属性是否被继承

     - Object.isPrototypeOf( ) 一个对象是否是另一个对象的原型

     - [`Object.prototype.propertyIsEnumerable()`](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/Object/propertyIsEnumerable)

       判断指定属性是否可枚举

     - [`Object.prototype.toLocaleString()`](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/Object/toLocaleString)

       直接调用 [`toString()`](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/Object/toString)方法

     - [`Object.prototype.toString()`](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/Object/toString)

       返回对象的字符串表示

     - [`Object.prototype.valueOf()`](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/Object/valueOf)

       返回指定对象的原始值。

   - RegExp正则表达式对象

     - [`RegExp.prototype.exec()`](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/RegExp/exec)

       在目标字符串中执行一次正则匹配操作。

     - [`RegExp.prototype.global`](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/RegExp/global)

       是否开启全局匹配，也就是匹配目标字符串中所有可能的匹配项，而不是只进行第一次匹配

     - [`RegExp.prototype.ignoreCase`](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/RegExp/ignoreCase)

       在匹配字符串时是否要忽略字符的大小写

     - [`RegExp.prototype.lastIndex`](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/RegExp/lastIndex)

       下次匹配开始的字符串索引位置

     - [`RegExp.prototype.source`](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/RegExp/source)

       正则对象的源模式文本

     - [`RegExp.prototype.test()`](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/RegExp/test)

       测试当前正则是否能匹配目标字符串

     - [`RegExp.prototype.toString()`](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/RegExp/toString)

       返回一个字符串，其值为该正则对象的字面量形式。覆盖了[`Object.prototype.toString()`](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/Object/toString) 方法

   - String字符串对象

     - [`String.prototype.length`](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/String/length)

       返回了字符串的长度。

     - [`String.prototype.charAt()`](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/String/charAt)

       返回特定位置的字符

     - [`String.prototype.charCodeAt()`](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/String/charCodeAt)

       返回表示给定索引的字符的Unicode的值

     - [`String.prototype.codePointAt()`](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/String/codePointAt)

       返回使用UTF-16编码的给定位置的值的非负整数

     - [`String.prototype.concat()`](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/String/concat)

       连接两个字符串文本，并返回一个新的字符串

     - [`String.prototype.includes()`](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/String/includes)

       判断一个字符串里是否包含其他字符串

     - [`String.prototype.endsWith()`](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/String/endsWith)

       判断一个字符串的是否以给定字符串结尾，结果返回布尔值

     - [`String.prototype.indexOf()`](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/String/indexOf)

       从字符串对象中返回首个被发现的给定值的索引值，如果没有找到则返回-1

     - [`String.prototype.lastIndexOf()`](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/String/lastIndexOf)

       从字符串对象中返回最后一个被发现的给定值的索引值，如果没有找到则返回-1

     - [`String.prototype.localeCompare()`](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/String/localeCompare)

       返回一个数字表示是否引用字符串在排序中位于比较字符串的前面，后面，或者二者相同

     - [`String.prototype.match()`](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/String/match)

       使用正则表达式与字符串相比较

     - [`String.prototype.normalize()`](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/String/normalize)

       返回调用字符串值的Unicode标准化形式

     - [`String.prototype.padEnd()`](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/String/padEnd)

       在当前字符串尾部填充指定的字符串， 直到达到指定的长度。 返回一个新的字符串。

     - [`String.prototype.padStart()`](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/String/padStart)

       在当前字符串头部填充指定的字符串， 直到达到指定的长度。 返回一个新的字符串

     - [`String.prototype.repeat()`](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/String/repeat)

       返回指定重复次数的由元素组成的字符串对象。

     - [`String.prototype.replace()`](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/String/replace)

       被用来在正则表达式和字符串直接比较，然后用新的子串来替换被匹配的子串

     - [`String.prototype.search()`](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/String/search)

       对正则表达式和指定字符串进行匹配搜索，返回第一个出现的匹配项的下标

     - [`String.prototype.slice()`](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/String/slice)

       摘取一个字符串区域，返回一个新的字符串

     - [`String.prototype.split()`](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/String/split)

       通过分离字符串成字串，将字符串对象分割成字符串数组

     - [`String.prototype.startsWith()`](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/String/startsWith)

       判断字符串的起始位置是否匹配其他字符串中的字符

     - [`String.prototype.substr()`](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/String/substr)

       通过指定字符数返回在指定位置开始的字符串中的字符

     - [`String.prototype.substring()`](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/String/substring)

       返回在字符串中指定两个下标之间的字符

     - [`String.prototype.toLocaleLowerCase()`](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/String/toLocaleLowerCase)

       根据当前区域设置，将符串中的字符转换成小写。对于大多数语言来说，[`toLowerCase`](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/String/toLowerCase)的返回值是一致的

     - [`String.prototype.toLocaleUpperCase()`](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/String/toLocaleUpperCase)

       根据当前区域设置，将字符串中的字符转换成大写，对于大多数语言来说，[`toUpperCase`](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/String/toUpperCase)的返回值是一致的

     - [`String.prototype.toLowerCase()`](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/String/toLowerCase)

       将字符串转换成小写并返回

     - [`String.prototype.toString()`](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/String/toString)

       返回用字符串表示的特定对象。重写 [`Object.prototype.toString`](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/Object/toString) 方法。

     - [`String.prototype.toUpperCase()`](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/String/toUpperCase)

       将字符串转换成大写并返回。

     - [`String.prototype.trim()`](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/String/trim)

       从字符串的开始和结尾去除空格。

     - [`String.prototype.valueOf()`](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/String/valueOf)

       返回特定对象的原始值。重写 [`Object.prototype.valueOf`](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/Object/valueOf) 方法。

     - [`String.prototype[@@iterator]()`](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/String/@@iterator)

       返回一个新的迭代器对象，该对象遍历字符串值的索引位置，将每个索引值作为字符串值返回

4. 什么是闭包?

   - 作用域是针对变量的，比如创建一个函数a1,函数里又包含了一个子函数a2，此时存在三个作用域：全局作用域、a1作用域、a2作用域；即全局作用域包含了a1和a2的作用域，a1的作用域包含了a2的作用域。当a2在查找变量的时候会先从自身的作用域查找，找不到就向上一级的作用域查找，本例中为a1作用域。如果还没找到就找到全局作用域查找，这样就形成了一个作用域链。
   - 要理解闭包，首先要理解js的垃圾回收机制，也就是当一个函数被执行完毕后，其作用域会被回收，如果形成了一个闭包，函数执行完毕后其作用域就不会被回收。
   - 如果某一个函数被其父函数之外的一个变量引用，就会形成一个闭包。
   - 闭包的作用：保存自己的私有变量，通过提供的接口给外部使用，但外部不能访问该变量。

   **MDN中的说法** ：

   - 从内部函数访问外部函数作用域

   - **在一个函数内部声明的局部变量，当在其内部再声明一个子函数的时候，该子函数内部引用了其父函数所创建的局部变量**

5. 什么是原型链？

   - JavaScript是面向对象的，每个实例对象都有一个`__proto__`属性,该属性指向它构造函数的原型对象。这个实例对象的构造函数有一个原型属性prototype，与实例的`__proto__`指向同一个对象。当一个对象在查找一个属性的时候，如果自身没有该属性，就会根据`__protp__`向它的原型进行查找，如果它的上一级原型还没有，则继续向它的原型的原型继续查找，直到`Object.prototype.__proto__`为null，这样就形成了原型链。

6. 有哪些方式继承？

   - 借用构造函数。
     - 在子类构造函数的内部调用超类型构造函数。可以使用apply()和call()方法，在新创建的对象上执行构造函数。
     - 缺点：
       - 方法都在构造函数中定义，函数的复用就无从谈起。在超类型的原型中定义的方法，对子类而言也是不可见的，结果所有的类型都只能使用构造函数模式。
   - 组合继承。
     - 将原型链和借用构造函数的技术组合在一起，从而发挥二者之长。
     - 使用原型链实现对原型属性和方法的继承，通过借用构造函数来实现实例属性的继承。
     - 优点
       - 既通过在原型上定义方法实现了函数复用，又能保证每一个实例都有它自己的属性。组合继承避免了原型链和借用构造函数的缺陷，融合了他们的优点，成为JavaScript中常用的继承方式。
   - 原型链继承。
     - 借助原型可以基于已有的对象创建对象，同时还不必因此创建自定义类型。在object()函数内部，先创建一个临时的构造函数，然后将传入的对象作为这个构造函数的原型，最后返回了这个临时类型的一个新实例。
   - 寄生式继承。
     - 创建一个仅用于封装继承过程的函数，该函数在内部以某种方式来增强对象，最后再像真的是它做了所有的工作一样返回对象。
     - 缺点：
       - 使用寄生式继承来为对象添加函数，会由于不能做到函数复用而降低效率，这一点和构造函数模式类似。
   - 寄生组合式继承。
     - 通过借用构造函数来继承属性，通过原型链的混成形式来继承方法。本质上，就是使用寄生式继承来继承超类型的原型，然后再将结果指定给子类型的原型。
     - extend()方法采用了这样的方式。

7. 字符串的常用方法有哪些？

   | 方法                                                         | 描述                                                 |
   | :----------------------------------------------------------- | :--------------------------------------------------- |
   | [anchor()](https://www.w3school.com.cn/jsref/jsref_anchor.asp) | 创建 HTML 锚。                                       |
   | [big()](https://www.w3school.com.cn/jsref/jsref_big.asp)     | 用大号字体显示字符串。                               |
   | [blink()](https://www.w3school.com.cn/jsref/jsref_blink.asp) | 显示闪动字符串。                                     |
   | [bold()](https://www.w3school.com.cn/jsref/jsref_bold.asp)   | 使用粗体显示字符串。                                 |
   | [charAt()](https://www.w3school.com.cn/jsref/jsref_charAt.asp) | 返回在指定位置的字符。                               |
   | [charCodeAt()](https://www.w3school.com.cn/jsref/jsref_charCodeAt.asp) | 返回在指定的位置的字符的 Unicode 编码。              |
   | [concat()](https://www.w3school.com.cn/jsref/jsref_concat_string.asp) | 连接字符串。                                         |
   | [fixed()](https://www.w3school.com.cn/jsref/jsref_fixed.asp) | 以打字机文本显示字符串。                             |
   | [fontcolor()](https://www.w3school.com.cn/jsref/jsref_fontcolor.asp) | 使用指定的颜色来显示字符串。                         |
   | [fontsize()](https://www.w3school.com.cn/jsref/jsref_fontsize.asp) | 使用指定的尺寸来显示字符串。                         |
   | [fromCharCode()](https://www.w3school.com.cn/jsref/jsref_fromCharCode.asp) | 从字符编码创建一个字符串。                           |
   | [indexOf()](https://www.w3school.com.cn/jsref/jsref_indexOf.asp) | 检索字符串。                                         |
   | [italics()](https://www.w3school.com.cn/jsref/jsref_italics.asp) | 使用斜体显示字符串。                                 |
   | [lastIndexOf()](https://www.w3school.com.cn/jsref/jsref_lastIndexOf.asp) | 从后向前搜索字符串。                                 |
   | [link()](https://www.w3school.com.cn/jsref/jsref_link.asp)   | 将字符串显示为链接。                                 |
   | [localeCompare()](https://www.w3school.com.cn/jsref/jsref_localeCompare.asp) | 用本地特定的顺序来比较两个字符串。                   |
   | [match()](https://www.w3school.com.cn/jsref/jsref_match.asp) | 找到一个或多个正则表达式的匹配。                     |
   | [replace()](https://www.w3school.com.cn/jsref/jsref_replace.asp) | 替换与正则表达式匹配的子串。                         |
   | [search()](https://www.w3school.com.cn/jsref/jsref_search.asp) | 检索与正则表达式相匹配的值。                         |
   | [slice()](https://www.w3school.com.cn/jsref/jsref_slice_string.asp) | 提取字符串的片断，并在新的字符串中返回被提取的部分。 |
   | [small()](https://www.w3school.com.cn/jsref/jsref_small.asp) | 使用小字号来显示字符串。                             |
   | [split()](https://www.w3school.com.cn/jsref/jsref_split.asp) | 把字符串分割为字符串数组。                           |
   | [strike()](https://www.w3school.com.cn/jsref/jsref_strike.asp) | 使用删除线来显示字符串。                             |
   | [sub()](https://www.w3school.com.cn/jsref/jsref_sub.asp)     | 把字符串显示为下标。                                 |
   | [substr()](https://www.w3school.com.cn/jsref/jsref_substr.asp) | 从起始索引号提取字符串中指定数目的字符。             |
   | [substring()](https://www.w3school.com.cn/jsref/jsref_substring.asp) | 提取字符串中两个指定的索引号之间的字符。             |
   | [sup()](https://www.w3school.com.cn/jsref/jsref_sup.asp)     | 把字符串显示为上标。                                 |
   | [toLocaleLowerCase()](https://www.w3school.com.cn/jsref/jsref_toLocaleLowerCase.asp) | 把字符串转换为小写。                                 |
   | [toLocaleUpperCase()](https://www.w3school.com.cn/jsref/jsref_toLocaleUpperCase.asp) | 把字符串转换为大写。                                 |
   | [toLowerCase()](https://www.w3school.com.cn/jsref/jsref_toLowerCase.asp) | 把字符串转换为小写。                                 |
   | [toUpperCase()](https://www.w3school.com.cn/jsref/jsref_toUpperCase.asp) | 把字符串转换为大写。                                 |
   | toSource()                                                   | 代表对象的源代码。                                   |
   | [toString()](https://www.w3school.com.cn/jsref/jsref_toString_string.asp) | 返回字符串。                                         |
   | [valueOf()](https://www.w3school.com.cn/jsref/jsref_valueOf_string.asp) | 返回某个字符串对象的原始值。                         |

8. DOM节点的增删改查？

   - ##### 查找 HTML 元素。

     | 方法                                    | 描述                   |
     | :-------------------------------------- | :--------------------- |
     | document.getElementById(*id*)           | 通过元素 id 来查找元素 |
     | document.getElementsByTagName(*name*)   | 通过标签名来查找元素   |
     | document.getElementsByClassName(*name*) | 通过类名来查找元素     |

   - ##### 改变 HTML 元素

     | 方法                                       | 描述                   |
     | :----------------------------------------- | :--------------------- |
     | element.innerHTML = *new html content*     | 改变元素的 inner HTML  |
     | element.attribute = *new value*            | 改变 HTML 元素的属性值 |
     | element.setAttribute(*attribute*, *value*) | 改变 HTML 元素的属性值 |
     | element.style.property = *new style*       | 改变 HTML 元素的样式   |

   - ##### 添加和删除元素

     | 方法                              | 描述             |
     | :-------------------------------- | :--------------- |
     | document.createElement(*element*) | 创建 HTML 元素   |
     | document.removeChild(*element*)   | 删除 HTML 元素   |
     | document.appendChild(*element*)   | 添加 HTML 元素   |
     | document.replaceChild(*element*)  | 替换 HTML 元素   |
     | document.write(*text*)            | 写入 HTML 输出流 |

   - ##### 添加事件处理程序

     | 方法                                                     | 描述                            |
     | :------------------------------------------------------- | :------------------------------ |
     | document.getElementById(id).onclick = function(){*code*} | 向 onclick 事件添加事件处理程序 |

   - ##### 查找 HTML 对象

     | 属性                         | 描述                                        | DOM  |
     | :--------------------------- | :------------------------------------------ | :--- |
     | document.anchors             | 返回拥有 name 属性的所有 <a> 元素。         | 1    |
     | document.applets             | 返回所有 <applet> 元素（HTML5 不建议使用）  | 1    |
     | document.baseURI             | 返回文档的绝对基准 URI                      | 3    |
     | document.body                | 返回 <body> 元素                            | 1    |
     | document.cookie              | 返回文档的 cookie                           | 1    |
     | document.doctype             | 返回文档的 doctype                          | 3    |
     | document.documentElement     | 返回 <html> 元素                            | 3    |
     | document.documentMode        | 返回浏览器使用的模式                        | 3    |
     | document.documentURI         | 返回文档的 URI                              | 3    |
     | document.domain              | 返回文档服务器的域名                        | 1    |
     | document.domConfig           | 废弃。返回 DOM 配置                         | 3    |
     | document.embeds              | 返回所有 <embed> 元素                       | 3    |
     | document.forms               | 返回所有 <form> 元素                        | 1    |
     | document.head                | 返回 <head> 元素                            | 3    |
     | document.images              | 返回所有 <img> 元素                         | 1    |
     | document.implementation      | 返回 DOM 实现                               | 3    |
     | document.inputEncoding       | 返回文档的编码（字符集）                    | 3    |
     | document.lastModified        | 返回文档更新的日期和时间                    | 3    |
     | document.links               | 返回拥有 href 属性的所有 <area> 和 <a> 元素 | 1    |
     | document.readyState          | 返回文档的（加载）状态                      | 3    |
     | document.referrer            | 返回引用的 URI（链接文档）                  | 1    |
     | document.scripts             | 返回所有 <script> 元素                      | 3    |
     | document.strictErrorChecking | 返回是否强制执行错误检查                    | 3    |
     | document.title               | 返回 <title> 元素                           | 1    |
     | document.URL                 | 返回文档的完整 URL                          |      |

9. 什么是预解析？

   - 在整体代码执行之前，先解析一部分。
   - 预解析之后，代码才会从上往下依次执行，但是预解析执行过的代码不会重复执行。
   - JavaScript预解析做了什么事：把声明部分的代码预先执行
     - 变量声明：通过var关键字定义的变量
     - 函数声明：通过function关键字声明的函数
       - 预解析时如果遇到重复的变量声明，会忽略。
       - 预解析时如果遇到重复的函数声明，会保留后面的函数
       - 预解析时如果遇到变量与函数重名的情况，保留函数

10. 什么是变量名提升？

    - 使用var关键字定义的变量，被称为变量声明。
    - 函数声明提升的特点是，在函数声明的前面。可以调用这个函数。

11. JS中的typeof关键字能返回哪些数据类型?

    - 一般判断基本的数据类型。是一个操作符而不是函数，圆括号可有可无。
    - 返回值有string、number、boolean、undefined、object、function
    - 基本数据类型有：Boolean、Number、String、Undefined、Null
    - 基本数据类型中数字、字符串、布尔类型返回其本身类型，undefined返回undefined
    - 九大内置构造函数及其他所有函数返回function
    - 其他所有复杂类型对象和null返回object

12. 简述创建函数的几种方式？

    - 函数声明
    - 函数表达式
    - 函数对象形式

13. 代码实现数组排序去重

    ```javascript	
    function fn(arr){
    for(var i = 0; i < arr.length-1; i++){
    for(var j = 0; j < arr.length-1-i; j++){
    if(arr[j]<arr[j+1]){
    var temp = arr[j];
    arr[j] = arr[j+1];
    arr[j+1] = temp;
    }
    }
    }
    for(var k = 0; k < arr.length; k++){
    var c = arr[k];
    for(var l = k+1; l < arr.length; l++){
    if(arr[l] == c){
    arr.splice(l, 1);
    l--;
    }
    }
    }
    return arr
    }
    var arr = [1, 2, 5, 6, 8, 9, 10, 6, 5, 7, 4, 3, 5]
    console.log(fn(arr))
    ```

    

14. 写出下面代码输出结果

    ```javascript	
    A. console.log( undefined || 1 );      -->  1
    B. console.log( null || NaN );            -->   NaN
    C. console.log( 0 && 1 );                     -->   0
    D. console.log( 0 && 1 || 0 );            -->   0
    ```

15. 下面代码会输出什么？

    ```javascript	
    var foo = 1;
    function fn() {
    console.log( foo );   -->  undefined
    var foo = 2;
    console.log( foo );   -->  2
    }
    fn();
    ```

### 实际工作部分

1. 什么是短路表达式？
   - 一种简写形式，也就是使用&&和||来赋值或者执行函数的形式
2. 控制台中使用哪些部分调试？
   - console.log()输出普通信息
   - console.info（）输出提示性信息
   - console.error() 输出错误信息
   - console.warn() 输出警示信息
   - console.debug() 输出调试信息

## （四）WebAPI模块

### 基础部分

1. 出一套不同分辨率的页面，不同终端的前端实现方案有什么思路？
   - 流式布局：
     - 使用非固定像素来定义网页内容，使用百分比布局
   - 响应式开发：
     - css3中的媒体查询，通过查询screen的宽度来指定某个宽度区间的网页布局
       - 768px以下
       - 768-992px
       - 992-1200px
       - 1200px以上
2. px、em、rem取用选择依据？
   - px。绝对单位，相对于屏幕分辨率而言。
   - em。相对长度单位，相当于当前对象内文本的字体尺寸。它会继承父级元素的字体大小，不是一个固定值。
   - rem。css3新增的一个相对单位，只相对HTML根元素。
   - 区别：
     - IE无法调整那些使用px作为单位的字体大小，而em和rem可以缩放，rem相对的只是HTML根元素。除了IE8及更早版本外，所有浏览器均已支持rem。
3. zepto和jQuery的区别
   - Zepto相对jQuery更加轻量，主要用在移动端，jQuery也有对应的jQuerymobile移动端框架。

### 函数实际工作部分

1. 移动端touch事件判断滑屏手势的方向？
   - 当开始一个touchstart事件的时候，此刻获取手指的横坐标startX和纵坐标startY；当触发touchmove事件时，再获取此时手指的横坐标moveEndX和纵坐标moveEndY；最后，通过这两次获取的坐标差值来判断手指在手机屏幕上的滑动方向。
2. 移动端对图片优化有哪些方式？怎么实现？
   - 懒加载，使用CSS sprites合并成一张大图，从格式着手，webp的图片格式
   - 去掉无意义的修饰，使用矢量图代替位图
   - 按照HTTP协议设置合理的缓存
3. rem布局中的尺寸是怎样计算的？
   - rem布局的本质是等比缩放，一般基于宽度。
     - 假设将屏幕宽度平均分成100份，每一份的宽用x表示，x=屏幕宽度/100。如果将x作为单位，x前面的数值就代表屏幕宽度的百分比。

## （五）JavaScript高级模块

### 基础部分

1. 对this关键字的理解

   - 作为纯粹的函数调用this指向全局对象
   - 作为对象的方法调用this指向调用对象
   - 作为构造函数调用this指向实例对象 
   - apply调用 ，this指向apply方法的第一个参数

2. 表单验证传输什么数据？明文还是暗文？如何加密？是每一次传输数据，都加密之后才传输吗？

   - get从服务器请求数据，post向服务器发送数据。
     - get方法是把数据参数队列加到一个URL上，值和表单是一一对应的。
     - post方法可以没有时间限制的传递数据到服务器，用户在浏览器端是看不到过程的，post方法适合发送一个保密的或者数据量较大的数据到服务器。
   - 区别：
     - post允许传输大量数据，而get方法发送的参数有大小限制(256字节),会将所要传输的数据附在网址后面，然后一起发送到服务器，传送数据量的大小受到限制，但执行效率比post好。
   - 总结：

     - get方式的安全性较post方式差些，包含机密信息的话，建议使用post提交数据。
     - 在查询数据时，建议使用get方式；在增删改时，建议使用post方式。
   - 如果向服务器传输数据都是用加密数据(post)，如果单单向从服务器获取数据或者传输的数据不重要，可以直接使用明文方式传输(get)。

3. 如何实现跨域？

   - JSONP(JSON with Padding 填充式JSON 或参数式 JSON)

     - 在js 中，我们虽然不能直接用XMLHttpRequest 请求不同域上的数据，但是在页面上引入不同域上的js 脚本文件却是可以的，jsonp正是利用这个特性来实现的。

       JSONP 由两部分组成：回调函数和数据。回调函数是当响应到来时应该在页面中调用的函数，而数据就是传入回调函数中的JSON 数据。

       - 优点：
         - 兼容性更好，在更加古老的浏览器中都可以运行，不需要XMLHttpRequest 或 ActiveX 的支持； 能够直接访问响应文本，支持在浏览器与服务器之间双向通信
       - 缺点：
         - JSONP 是从其他域中加载代码执行。如果其他域不安全，很可能会在响应中夹带一些 恶意代码，而此时除了完全放弃 JSONP 调用之外，没有其他办法。因此在使用不是自己 运维的Web 服务时，一定得保证它安全可靠。 只支持 GET请求而不支持 POST等其它类型的 HTTP 请求；只支持跨域 HTTP 请 求这种情况，不能解决不同域的两个页面之间进行 JavaScript调用的问题

4. 说说事件委托机制，这样做有什么好处？

   - 某个事件本来该自己干的，但是自己不干，交给别人来干。就叫事件委 托。打个比方：一个button 对象，本来自己需要监控自身的点击事件，但是自己不来监控这个点击事件，让自己的父节点来监控自己的点击事件。
   - 优点：
     - 提高性能：列如，当有很多 li同时需要注册事件的时候，如果使用传统方法来注册 事件的话，需要给每一个 li 注册事件。然而如果使用委托事件的话，就只需要将事件委托给 一个父元素即可。这样就能提高性能。
     - 新添加的元素也会被注册上事件；

5. call和apply区别？

   - 相同点：
     - 都可以代替另一个对象调用一个方法，将一个函数的上下文从初始的上下文改为由thisObj指定的新对象。
   - 不同点：
     - apply只能有两个参数，第二个参数必须为数组形式的参数，即使只有一个参数也要写进数组里。
     - call()：参数为参数列表形式  

6. 在JS的计时器运行原理是怎样的，为什么可以出发计时器效果？计时器是多线程的吗？

   - JavaScript引擎只有一个线程，强迫异步事件排队等待被执行。
   - setTimeOut和setInterval本质上不同的地方是它们如何执行异步代码的。
   - 如果一个定时器正在执行的时候被阻塞了，那么它将会被推迟到下个可能的执行点，这即是使得延迟时间有可能会超过声明定时器时设置的值。  
   - setInterval如果有足够的时间来执行（大于制定的延迟），那么它将会无延迟的一个紧接着一个执行。
   - 原理： 计时器通过设定一定的时间段（毫秒）来异步的执行一段代码。因为 Javascript 是一 个单线程语言，计时器提供了一种绕过这种语言限制来执行代码的能力。 
   - 总结： 计时器是单线程的， 需要等待上一个任务执行完， 如果上一个任务没有执行完， 下一个任务需要延迟执行，直到上一个任务执行完。   

7. 什么是事件冒泡和捕获？

   - 事件冒泡：子元素事件的触发会影响父元素事件

     - 开启  ：element.addEventListener(eventName，handler，false)；

- 关闭：假设传统方式事件的返回值为 e，就可以通过 e.stopPropagation()来关闭事件冒泡；
  - 事件捕获：父元素的事件会影响子元素的事件
    - 开启：element.addEventListener(eventName，handler，true)；

8. 面向对象和类的区别

   - 类是对象的模版  

     - 在 js 中没有类， 所以在js 中所谓的 类 就是构造函数， 对象就是由构造函数创建出来的实例对象。面向对象就是使用面向对象的方式处理问题， 面向对象是对面向过程进行封装。

   - 面向对象有三大特性

     - 抽象性， 需要通过核心数据和特定环境才能描述对象的具体意义  

     - 封装性， 封装就是将数据和功能组合到一起,在js 中对象就是键值对的集合,对象将属性和方法封装起来， 方法将过程封装起来。

     - 继承性，将别人的属性和方法继承为自己的，传统继承基于模板(类)，js 中继承基于构

       造函数。

### 实际工作部分

1. JavaScript中的垃圾回收机制

   - 在Javascript 中，如果一个对象不再被引用，那么这个对象就会被GC 回收。如果两个对象互相引用，而不再被第3者所引用，那么这两个互相引用的对象也会被回收。 因为函数 a被b引用，b又被 a外的 c引用，这就是为什么 函数 a 执行后不会被回收的原因。

2. 列出3条以上FF和IE脚本兼容问题

   - window.event：
     - 表示当前的事件对象，IE有这个对象，FF没有，FF通过事件处理函数传递事件对象。

   - 获取事件源  
     - IE用srcElement获取事件源，而FF用target获取事件源
   - 添加，去除事件  
     - IE：element.attachEvent(“onclick”,function)    element.detachEvent(“onclick”, function)
     - FF：element.addEventListener(“click”,function, true) element.removeEventListener(“click”, function, true)
   - 获取标签的自定义属性
     - IE：div1.value或div1[“value”]
     - FF：可用div1.getAttribute(“value”)

3. 用正则表达式，写出由字母开头，其余数字、字母、下划线组成的6-30的字符串？

   -	`/^[a-zA-Z]{1}{\w}{5,29}$/`

4. 下列JavaScript代码执行后，iNum值是多少？

   ```javascript
   var iNum = 0;
   for(var i = 1; i < 10; i++){
   if(i% 5 == 0){
   continue;
   }
   iNum++;
   }
   //结果为8
   ```

5. 程序中捕获异常的方法

```javascript
window.error
try {}
catch(err){}
finally{}

```

6. 正则匹配邮箱

- ` /^[a-zA-Z0-9-]+@([a-zA-Z0-9-])+((.[a-zA-Z0-9_-]{2,3}){1,2})$/ `

7. JavaScript中callee和caller的作用

   - caller
     - 返回一个对函数的引用，该函数调用了当前函数
   - callee
     - 返回正在被执行的function函数，也就是所指定的function对象的正文。

8. 下面代码输出什么结果？

   ```javascript	
   function f1(){
   var tmp = 1;
   this.x = 3;
   console.log( tmp );
   console.log( this.x );
   }
   var obj = new f1();
   console.log( obj.x );
   console.log( f1() );
   
   ```

9. 下面代码输出什么结果？

   ```javascript
   function changeObjectProperty(o){
   o.siteUrl = "http://www.csser.com/";
   o = new Object();
   o.siteUrl = "http://www.popcg.com/";
   }
   var CSSer = new Object();
   changeObjectProperty( CSSer );
   console.log( CSSer.siteUrl );
   
   ```

## （六）jQuery模块

### 基础部分

1. 谈谈你对jQuery的理解

   - JQuery 是继 prototype 之后又一个优秀的 Javascript 库。它是轻量级的js 库 ，它

     兼容 CSS3，还兼容各种浏览器（IE 6.0+，FF1.5+，Safari 2.0+，Opera 9.0+），jQuery2.0

     及后续版本将不再支持 IE6/7/8 浏览器。jQuery 使用户能更方便地处理 HTML（标准通用

     标记语言下的一个应用）、events、实现动画效果，并且方便地为网站提供 AJAX 交互。

     jQuery还有一个比较大的优势是，它的文档说明很全，而且各种应用也说得很详细，

     同时还有许多成熟的插件可供选择。jQuery 能够使用户的 html页面保持代码和 html 内容

     分离，也就是说，不用再在 html里面插入一堆 js 来调用命令了，只需要定义 id即可。

     jQuery 是一个兼容多浏览器的 javascript 库，核心理念是write less，do more(写

     得更少，做得更多)。 jQuery是免费、开源的，使用 MIT 许可协议。jQuery 的语法设

     计可以使开发更加便捷，例如操作文档对象、选择 DOM 元素、制作动画效果、事件处理、

     使用 Ajax 以及其他功能。除此以外，jQuery 提供 API让开发者编写插件。其模块化的使

     用方式使开发者可以很轻松的开发出功能强大的静态或动态网页。

2. 原生js的window.onload与jQuery的`$(document).ready(function(){})`,`$function(){}`有什么不同？

   - 执行时间 
     - window.onload必须等到页面内包括图片的所有元素加载完毕后才能执行。 
     - $(document).ready()是 DOM 结构绘制完毕后就执行，不必等到加载完毕。
   - 编写个数不同

     - window.onload不能同时编写多个，如果有多个 window.onload 方法，只会执行一个 
     - $(document).ready()可以同时编写多个，并且都可以得到执行
   - 简化写法 
     - window.onload没有简化写法
     - `$(document).ready(function (){})`可以简写成`$(function(){}) `

3. jQuery一个对象可以同时绑定多个事件，是如何实现的？

   - jQuery可以给一个对象同时绑定多个事件，底层实现的方式是使用addEventListner或attachEvent兼容不同的浏览器实现事件的绑定，这样可以给同一个对象注册多个事件。

4. jQuery.fn的init方法返回的this指的是什么对象？为什么要返回this？

   - this执行init构造函数自身，也就是jQuery实例对象，返回this是为了实现jQuery的链式操作。

5. jQuery.extend和jQuery.fn.extend有什么区别？

   - Jquery.extend用来扩展jQuery对象本身；jquery.fn.extend用来扩展jQuery实例

### 实际工作部分

1. jQuery框架中的$.ajax()的常用参数有哪些？写一个post请求并带有发送数据和返回数据的实例。

   - async是否异步

   - url请求地址

   - contentType发送信息至服务器时内容编码类型

   - data发送到服务器的数据

   - dataType预期服务器返回的数据类型

   - type请求类型

   - success请求成功回调函数

   - error请求失败回调函数

     ```javascript
     $.ajax({
     url: "/jquery/test1.txt",
     type: 'post',
     data: { id: 1 },
     success: function ( res ) { alert(res); }
     })
     
     ```

2. 列举一下jQuery中的函数，这些函数实现链式编程的原理？

   ```javascript
   toggle（fn, fn）
   $（"td"）.toggle（
   function（）{
   $（this）.addClass（"selected"）;
   }，
   function（）{
   $（this）.removeClass（"selected"）;
   ）
   
   ```

   - 实现函数链式编程的原理：返回自身，其他过程在函数内部实现，其好处是：节约js代码，返回的是同一个对象，提高代码的效率。

## （七）Ajax模块

### 基础模块

1. ajax是什么？
   - Ajax并不算是一种新的技术，全称是asychronous javascript and xml，可以说是已有技术的组合
   - 主要用来实现客户端与服务器端的异步通信效果，实现页面的局部刷新，早期的浏览器并不能原生支持ajax，可以使用隐藏帧（iframe）方式变相实现异步效果，后来的浏览器提供了对ajax的原生支持
   - 使用ajax原生方式发送请求主要通过XMLHttpRequest(标准浏览器)、ActiveXObject(IE浏览器)对象实现异步通信效果
2. 同步和异步执行代码的区别？
   - 同步：阻塞的
   - 异步：非阻塞的
3. 页面编码和被请求的资源编码不一致如何处理？
   - 对于ajax请求传递的参数，如果是get请求方式，参数如果传递中文，在有些浏览器会乱码，不同的浏览器对参数编码的处理方式不同
   - 所以对于get请求的参数需要使用 encodeURIComponent函数对参数进行编码处理，后台开发语言都有相应的解码api。
   - 对于post请求不需要进行编码
4. 简述ajax的过程
   - 创建XMLHttpRequest对象,也就是创建一个异步调用对象
   - 创建一个新的HTTP请求,并指定该HTTP请求的方法、URL及验证信息  
   - 设置响应HTTP请求状态变化的函数
   - 发送HTTP请求
   - 获取异步调用返回的数据  
   - 使用JavaScript和DOM实现局部刷新
5. 解释一下JavaScript的同源策略
   - 同源策略在什么情况下会起作用呢？ 
     - 当web 页面使用多个`<iframe>`元素或者打开其他浏览器窗口的时候，这一策略就会起作用。
   - 同源策略的含义：  
     - 脚本只能读取和所属文档来源相同的窗口和文档的属性。这里就涉及到了一个浏览器如何判断两者是否同源以及如何判断脚本来源的问题。  
     - 注意一点：脚本本身的来源并不作为判断是否同源的依据，而是将脚本所属文档的来源 作为判断依据。 
       - 判断脚本来源
         -  例如：文档 A中通过 script 的 src引用了一个外部脚本，这个脚本是 google 提供的，也是从google 的主机上加载到文档 A中的，那么这个脚本的所属文档是谁呢， 答案是文档A  
       - 判断是否同源 理解了脚本来源，接着理解怎么判断是否同源：
         - 如果两个文档在协议、主机以 及载入文档的 URL端口这三点中有一点不同，就认为他们不同源。  
6. get和post的区别
   - GET：一般用于信息获取，使用URL传递参数，对所发送信息的数量也有限制，一般在2000个字符，有的浏览器是8000个字符
   - POST：一般用于修改服务器上的资源，对所发送的信息没有限制  
     - 以下情况中，请使用 POST 请求  
       - 无法使用缓存文件（更新服务器上的文件或数据库）  
       - 向服务器发送大量数据（POST 没有数据量限制）  
       - 发送包含未知字符的用户输入时，POST 比GET 更稳定也更可靠
7. 解释jsonp的原理
   - Jsonp并不是一种数据格式，而json是一种数据格式，jsonp是用来解决跨域获取数据的一种解决方案，具体是通过动态创建script标签，然后通过标签的src属性获取js文件中的js脚本，该脚本的内容是一个函数调用，参数就是服务器返回的数据，为了处理这些返回的数据，需要事先在页面定义好回调函数，本质上使用的并不是ajax技术  
8. ajax请求时如何解释json数据
   - 使用eval() 或者JSON.parse() 。
   - 鉴于安全性考虑，推荐使用JSON.parse()更靠谱，对数据的安全性更好  
9. HTTP状态码都有哪些？
   - 100 => 正在初始化（一般是看不到的）
   - 101 => 正在切换协议（websocket浏览器提供的）
   - 200或者以2开头的两位数 => 都是代表响应主体的内容已经成功返回了
   - 202 => 表示接受
   - 301 => 永久重定向/永久转移
   - 302 => 临时重定向/临时转移（一般用来做服务器负载均衡）
   - 304 => 本次获取的内容是读取缓存中的数据，会每次去服务器校验
   - 400 => 参数出现错误（客户端传递给服务器端的参数出现错误）
   - 401 => 未认证，没有登录网站
   - 403 => 禁止访问，没有权限
   - 404 => 客户端访问的地址不存在
   - 500 => 未知的服务器错误
   - 503 => 服务器超负荷（假设一台服务器只能承受10000人，当第10001人访问的时候，如果服务器没有做负载均衡，那么这个人的网络状态码就是503）

### 实际工作部分

1. 浏览器渲染页面的过程

   - 浏览器会把HTML、SVG、XHTML三种格式的文件进行解析，产生一个DOM树；
   - Css，解析css会产生css规则树
   - JavaScript会通过DOM apI 来操作DOM树 和 css规则树
2. 简述同步和异步的区别，举例实际应用中哪些是同步，哪些是异步

   - 同步是阻塞的，浏览器向服务器发送请求，服务器比较忙，浏览器一直等着（页面白屏），直到服务器返回数据，页面才可以正常显示；
   - 异步是非阻塞的，浏览器向服务器请求数据，服务器比较忙，浏览器可以干自己原来的事情（显示页面），服务器返回数据的时候通知浏览器一声，浏览器把返回的数据再渲染到页面，局部更新  
3. 简述ajax的工作原理

   - Ajax的原理简单来说通过XmlHttpRequest对象来向服务器发异步请求，从服务器获得数据，然后用javascript来操作DOM而更新页面。这其中最关键的一步就是从服务器获得请求数据。
   - XMLHttpRequest是ajax的核心机制，它是在IE5中首先引入的，是一种支持异步请求的技术。简单的说，也就是javascript可以及时向服务器提出请求和处理响应，而不阻塞用户。达到无刷新的效果。
4. jsonp是如何实现前后台数据交互？

   - ajax请求受同源策略的影响，不允许进行跨域请求，而script标签的src属性中的链接却可以访问跨域的js脚本，利用这个特性，服务端不再返回json格式的数据，而是返回调用某个函数的js代码，在src中进行了调用，这样就实现了跨域。
   - 其原理就是动态创建script标签，通过script标签的src属性进行调用
5. HTTP请求方式有哪几种？

   - **HTTPRequestMethod**共计**17**种

     1. GET   请求指定的页面信息，并返回实体主体。

     2. HEAD   类似于get请求，只不过返回的响应中没有具体的内容，用于获取报头

     3. POST   向指定资源提交数据进行处理请求（例如提交表单或者上传文件）。数据被包含在请求体中。POST请求可能会导致新的资源的建立和/或已有资源的修改。

     4. PUT   从客户端向服务器传送的数据取代指定的文档的内容。

     5. DELETE  请求服务器删除指定的页面。

     6. CONNECT HTTP/1.1协议中预留给能够将连接改为管道方式的代理服务器。

     7. OPTIONS 允许客户端查看服务器的性能。

     8. TRACE  回显服务器收到的请求，主要用于测试或诊断。

     9. PATCH  实体中包含一个表，表中说明与该URI所表示的原内容的区别。

     10. MOVE  请求服务器将指定的页面移至另一个网络地址。

     11. COPY  请求服务器将指定的页面拷贝至另一个网络地址。

     12. LINK  请求服务器建立链接关系。

     13. UNLINK 断开链接关系。

     14. WRAPPED 允许客户端发送经过封装的请求。

     15. LOCK  允许用户锁定资源，比如可以再编辑某个资源时将其锁定，以防别人同时对其进行编辑。

     16. MKCOL  允许用户创建资源

     17. Extension-mothed  在不改动协议的前提下，可增加另外的方法。

## （八）H5C3模块

### 基础模块

1. CSS3有哪些新特性？

   - CSS3实现圆角（border-radius），阴影（box-shadow）  
   - 对文字加特效（text-shadow、），线性渐变（gradient），旋转（transform）  
   - transform:rotate(9deg)scale(0.85,0.90) translate(0px,-30px) skew(-9deg,0deg);// 旋转,缩 放,定位,倾斜  
   - 增加了更多的CSS选择器 多背景rgba  
   - 在CSS3中唯一引入的伪元素是 ::selection  
   - 媒体查询，多栏布局  
   - border-image

2. HTML5有哪些新特性、移除了哪些元素？如何处理HTML5新标签的浏览器兼容问题？如何区分HTML和HTML5？

   - 新特性：

     - 拖拽释放(Drag and drop) API  
     - 语义化更好的内容标签（header,nav,footer,aside,article,section）  
     - 音频、视频API(audio,video)
     - 画布(Canvas) API
     - 地理(Geolocation) API
     - 本地离线存储 localStorage 长期存储数据，浏览器关闭后数据不丢失；
     - sessionStorage 的数据在浏览器关闭后自动删除
     - 表单控件，calendar、date、time、email、url、search  
     - 新的技术webworker, websocket,Geolocation

   - 移除的元素  :

     - 纯表现的元素：basefont，big，center，font, s，strike，tt，u；  

     - 对可用性产生负面影响的元素：frame，frameset，noframes；

   - 支持HTML5新标签：

     - IE8/IE7/IE6支持通过 document.createElement 方法产生的标签，可以利用这一特性让这些浏览器支持 HTML5 新标签，浏览器支持新标签后，还需要添加标签默认的样式（当然最好的方式是直接使用成熟的框架、使用最多的是html5shim框架）：

       <!--[if lt IE 9]>

       <script>src="http://html5shim.googlecode.com/svn/trunk/html5.js"</script>

       <![endif]-->

3. 本地存储和cookies之间的区别是什么？

   - Cookies:
     - 服务器和客户端都可以访问；大小只有4KB左右；有有效期，过期后将会删除；
   - 本地存储：
     - 只有本地浏览器端可访问数据，服务器不能访问本地存储直到通过POST或者GET的通道发送到服务器；每个域5MB；没有过期数据，它将保留到用户从浏览器清除或者使用Javascript代码移除

4. 如何实现浏览器内多个标签之间的通信？

   - 调用 localstorge、cookies 等本地存储方式

5. 如何对网站的文件和资源进行优化？

   - 文件合并
   - 文件最小化/文件压缩
   - 使用CDN托管
   - 缓存的使用

6. 什么是响应式设计？

   - 关于网页制作的过程中让不同的设备有不同的尺寸和不同的功能。
   - 响应式设计是让所有人都能在自己不同设备上访问正常运行的网站。

7. 新的HTML5文档类型和字符集是？

   - HTML5文档类型：<!doctype html>
   - HTML5使用的编码`<meta charset="UTF-8">`

8. HTML5 Canvas元素有什么作用？

   - Canvas 元素用于在网页上绘制图形，该元素标签强大之处在于可以直接在HTML 上进行图形操作。

9. HTML5存储类型有什么区别？

   - Media API、
   - Text Track API、
   - Application Cache API、
   - User Interaction、
   - Data Transfer API、
   - Command API、
   - Constraint Validation API、
   - History API

10. CSS3新增的伪类有哪些？

    - p:first-of-type 选择属于其父元素的首个 <p> 元素的每个 <p> 元素。
    - p:last-of-type 选择属于其父元素的最后 <p> 元素的每个 <p> 元素。
    - p:only-of-type 选择属于其父元素唯一的 <p> 元素的每个 <p> 元素。
    - p:only-child  选择属于其父元素的唯一子元素的每个 <p> 元素。
    - p:nth-child(2) 选择属于其父元素的第二个子元素的每个 <p> 元素。
    - :enabled、:disabled 控制表单控件的禁用状态。
    - :checked，单选框或复选框被选中。

11. 如何实现页面设计图，你认为前端应该如何高质量完成工作？一个满屏 品 字布局如何设计？

    - 首先划分成头部、body、脚部；
    - 实现效果图是最基本的工作，精确到2px；
    - 与设计师，产品经理的沟通和项目的参与
    - 做好的页面结构，页面重构和用户体验
    - 处理hack，兼容、写出优美的代码格式
    - 针对服务器的优化、拥抱 HTML5。

12. 为什么利用多个域名来存储网站资源会更有效？

    - CDN缓存更方便
    - 突破浏览器并发限制
    - 节约cookie带宽
    - 节约主域名的连接数，优化页面响应速度
    - 防止不必要的安全问题

13. 谈一下对网页标准和标准定制机构重要性的理解

    - 网页标准和标准制定机构都是为了能让web发展的更‘健康’，开发者遵循统一的标准，降低开发难度，开发成本，SEO也会更好做，也不会因为滥用代码导致各种BUG和安全问题，最终提高网站易用性。

### 实际工作部分

1. 描述下cookies，sessionStorage和localStorage的区别

   - sessionStorage用于本地存储一个会话（session）中的数据，这些数据只有在同一个会话中的页面才能访问并且当会话结束后数据也随之销毁。因此sessionStorage不是一种持久化的本地存储，仅仅是会话级别的存储。而localStorage用于持久化的本地存储，除非主动删除数据，否则数据是永远不会过期的。

     localStorage的概念和cookie相似，区别是它是为了更大容量存储设计的。Cookie的大小是受限的，并且每次你请求一个新的页面的时候Cookie都会被发送过去，这样无形中浪费了带宽，另外cookie还需要指定作用域，不可以跨域调用。

     除此之外，localStorage拥有setItem,getItem,removeItem,clear等方法，不像cookie需要前端开发者自己封装setCookie，getCookie。但是Cookie也是不可以或缺的：Cookie的作用是与服务器进行交互，作为HTTP规范的一部分而存在 ，而localStorage仅仅是为了在本地“存储”数据而生。

2. 如何在HTML5中嵌入视频？

   - HTML5 定义了嵌入视频的标准方法，支持的格式包括：MP4、WebM 和 Ogg;

     ```html
     <video>
     <source src="jamshed.mp4" type="video/mp4">
     Your browser does'nt support video embedding feature.
     </video>
     
     
     ```

3. HTML5引入了什么新的表单属性？

   - autocomplete、autofocus、form、formaction、formenctype、formmethod、formnovalidate、formtarget、height、list、max、min、**multiple**、**pattern**、**placeholder**、**required**、step、width、datalist、keygen、output

   - Datalist  datetime output  keygen date month week  time number  range  emailurl

## （九）Node模块

### 基础部分

1. 对node的优点和缺点提出自己的看法

   - （优点）因为Node是基于事件驱动和无阻塞的，所以非常适合处理并发请求，因此构建在Node上的代理服务器相比其他技术实现（如Ruby）的服务器表现要好得多。此外，与Node代理服务器交互的客户端代码是由javascript语言编写的，因此客户端和服务器端都用同一种语言编写，这是非常美妙的事情。
   - （缺点）Node是一个相对新的开源项目，所以不太稳定，它总是一直在变，而且缺少足够多的第三方库支持。看起来，就像是Ruby/Rails当年的样子

2. node应用场景

   -  实时应用：如在线聊天，实时通知推送等等（如socket.io）
   -  分布式应用：通过高效的并行I/O使用已有的数据
   -  工具类应用：海量的工具，小到前端压缩部署（如grunt），大到桌面图形界面应用程序
   -  游戏类应用：游戏领域对实时和并发有很高的要求（如网易的pomelo框架）
   -  利用稳定接口提升Web渲染能力
   -  前后端编程语言环境统一：前端开发人员可以非常快速地切入到服务器端的开发（如著名的纯Javascript全栈式MEAN架构）

3. node非阻塞I/O模型执行流程

   - 主线程：

     1. 执行 node 的代码，把代码放入队列

     2. 事件循环程序（主线程）把队列里面的同步代码都先执行了，

     3. 同步代码执行完成，执行异步代码

     4. 异步代码分 2种状况，

        (1)、异步非 io setTimeout() setInterval()

        - 判断是否可执行，如果可以执行就执行，不可以跳过。

        (2)、异步io 文件操作

        - 会从线程池当中去取一条线程，帮助主线程去执行。

     5. 主线程会一直轮训，队列中没有代码了，主线程就会退出。

   - 子线程：被放在线程池里面的线程，用来执行异步 io操作

     1. 在线程池里休息

     2. 异步 io 的操作来了，执行异步 io操作。

     3. 子线程会把异步 io操作的 callback 函数，扔回给队列

     4. 子线程会回到线程池了去休息。

      callback，在异步 io 代码执行完成的时候被扔回主线程。

4. node中流（stream）的理解

   - 1. 什么是Stream?

     答案:stream是基于事件EventEmitter的数据管理模式．由各种不同的抽象接口组成，主要包括可写，可读，可读写，可转换等几种类型．

     2. Stream有什么好处?

     答案: 非阻塞式数据处理提升效率，片断处理节省内存，管道处理方便可扩展等.

     3. Stream有哪些典型应用?

     答案: 文件，网络，数据转换，音频视频等.

     4. 怎么捕获 Stream的错误事件?

     答案: 监听 error 事件，方法同 EventEmitter.

     5. 有哪些常用Stream,分别什么时候使用?

     答案:Readable 为可被读流，在作为输入数据源时使用；Writable 为可被写流,在作为

     输出源时使用；Duplex 为可读写流,它作为输出源接受被写入，同时又作为输入源被后面的

     流读出．Transform 机制和Duplex一样，都是双向流，区别时 Transfrom 只需要实现一

     ​    个函数transfrom(chunk, encoding, callback);而 Duplex 需要分别实现read(size)函数

     ​    和_write(chunk, encoding, callback)函数.

     6. 实现一个 Writable Stream?

     答案: 三步走:1)构造函数call Writable 2) 继承 Writable 3) 实现_write(chunk,encoding, callback)函数

5. ES6有哪些新特性？

   - 类的支持，模块化，箭头操作符，let/const块作用域，字符串模板，解构，参数默认值/不定参数/拓展参数, for-of遍历, generator, Map/Set, Promise

6. 个人对ES6的看法

   - 从软件工程角度来看，以前真的很弱，不适合做大型应用，很容易导致烂尾工程。ES6就相当于当年的Java5,是历史性的发展，从此我们可以用js做大型项目了。事实上，各大主流浏览器现在已经支持大部分新特性了，后端的Node.js更是可以直接使用ES6的绝大多数语法。

7. node中buffer如何应用？

   - Buffer是用来处理二进制数据的，比如图片，mp3,数据库文件等.Buffer支持各种编码解码，二进制字符串互转．

8. 什么是前端路由？什么时候适合使用前端路由？前端路由有哪些优缺点？

   - 1. 什么是前端路由

     路由是根据不同的url地址展示不同的内容或页面。前端路由就是把不同路由对应不同的内容或页面的任务交给前端来做，之前通过服务端根据url的不同返回不同的页面实现的

     2. 什么时候使用前端路由

     在单页面应用，大部分页面结构不变，只改变部分内容的使用

     3. 前端路由有什么优缺点

     优点：

     用户体验好，不需要每次都从服务器全部获取，快速展现给用户

     缺点：

     使用浏览器的前进，后退键的时候会重新发送请求，没有合理利用缓存

     单页面无法记住之前滚动的位置，无法再前进，后退的时候记住滚动的

9. 如何判断当前脚本运行在浏览器还是node环境中？

   - Exports = typeof  window  === 'undefined'? global: window ;

     获取全局对象的方式

     同理可得，typeof window可以用来判断是不是在浏览器环境中

### 实际工作部分

1. node中的异步和同步怎么理解？

   - node是单线程的，异步是通过一次次的循环事件队列来实现的．同步则是说阻塞式的IO,这在高并发环境会是一个很大的性能问题，所以同步一般只在基础框架的启动时使用，用来加载配置文件，初始化程序什么的．

2. 哪些方法可以异步进行流程的控制？

   - 1. 多层嵌套回调

     2. 为每一个回调写单独的函数，函数里边再回调

     3. 用第三方框架比方async, q, promise等

3. npm有哪些常用命令?

   - $npm init        项目初始化

     $npminstall -g <name>  安装并更新package.json中的版本配置

     $npm run<name>    执行一段脚本

     $npm update -n <name>  更新模块

## （十）Vue模块

### 基础部分

1. Vue组件间传值

   - 父子之间的传值

     - 父组件向子组件传值通过prop子组件在props中创建一个属性，用以接收父组件传过来的值

     - 子组件向父组件传值在响应该点击事件的函数中使用$emit来触发一个自定义事件在父组件中注册子组件并在子组件标签上绑定对自定义事件的监听

   - 非父子之间的通讯  

     - 可以通过eventBus来实现通信.

     - 所谓eventBus就是创建一个事件中心，相当于中转站，可以用它来传递事件和接收事件

       eventBus = new Vue();

     ```vue
     组件1触发：
     <div @click="eve"></div>
     methods: {
     eve() {
     eventBus.$emit('change','hehe'); //Hub触发事件
     }
     }123456
     组件2接收:
     <div></div>
     created() {
     eventBus.$on('change', () => { //Hub接收事件
     this.msg = 'hehe';
     });
     }123456
     这样就实现了非父子组件之间的通信了.原理就是把eventBus当作一个中转站！
     
     ```

2. Vue是什么

   - 一套构建用户界面的渐进式框架与其他重量级框架不同的是，Vue 采用自底向上增量开发的设计。Vue 的核心库只关注视图层，它不仅易于上手，还便于与第三方库或既有项目整合。另一方面，当与单文件组件和 Vue 生态系统支持的库结合使用时，Vue 也完全能够为复杂的单页应用程序提供驱动。

3. React和Vue的区别以及相似之处

- 相同点：

  1. 使用 Virtual DOM

  2. 提供了响应式（Reactive）和组件化（Composable）的视图组件。  

  3. 将注意力集中保持在核心库，而将其他功能如路由和全局状态管理交给相关的库。

- 不同点：
  1.  vue.js 更轻量，gzip后只有20K+，angular:56K ,react:44K
  2. vue.js 更易上手，学习曲线平稳
  3.  吸收两家之长，有angular 的指令和 react组件化思想
- 优缺点:
  - 体积小。接口灵活。侵入性好，可用于页面的一部分，而不是整个页面。扩展性好。源码规范简洁。代码较为活跃，作者是中国人，可在官方论坛中文提问。github9000+。基于组件化的开发。它是一个轻量级 mvvm框架、数据驱动+组件化的前端开发、社区完善
  - 缺点：社区不大，如果有问题可以读源码。功能仅限于view 层，Ajax等功能需要额外的库。对开发人员要求较高。开发的话，需要 webpack，不然很难用，最好配合es6。

4. v-show和v-if的选择
   - v-if 也是惰性的：如果在初始渲染时条件为假，则什么也不做——在条件第一次变为真时才开始局部编译（编译会被缓存起来）。
   - v-show 简单得多——元素始终被编译并保留，只是简单地基于 CSS 切换。
5. Vue的核心思想
   - Vue.js是一个提供MVVM数据双向绑定的库，专注于UI层面，核心思想是：数据驱动、组件系统。
   - Vue.js数据观测原理在技术实现上，利用的是ES5Object.defineProperty和存储器属性: getter和setter（所以只兼容IE9及以上版本），可称为基于依赖收集的观测机制。核心是VM，即ViewModel，保证数据和视图的一致性。
6. template参数选项的有无对生命周期的影响
   - 如果Vue实例对象中有template参数选项，则将其作为模板编译成render函数
   - 如果没有template参数选项，则将外部的HTML作为模板编译（template），也就是说，template参数选项的优先级要比外部的HTML高
   -  如果1,2条件都不具备，则报错

### 实际工作部分

1. 怎么定义vue-router的动态路由？怎么获取传过来的动态参数？

   - 对path属性加上/:id。 使用router对象的params.id

2. vue-router有哪几种导航钩子？

   -  vue-router 提供的导航钩子主要用来拦截导航，让它完成跳转或取消
     - 第一种是全局导航钩子：router.beforeEach(to,from,next)，作用：跳转前进行判断拦截。
     - 第二种：组件内的钩子；
     - 第三种：单独路由独享组件

3. 说出至少4种Vue中的指令和它的用法

   - v-if：判断是否隐藏；
   - v-for：数据循环出来；
   - v-bind:class：绑定一个属性；
   - v-model：实现双向数据绑定

4. 阐述一些vue项目中文件的构成

   ```markdown
   build文件夹：主要就是webpack的配置；
   
   Config文件夹：主要的就是index.js 这个文件进行配置代理服务器
   
   Src文件夹：
   
    “assets”共用的样式和图片
   
    “components”业务代码存放
   
    “router”路由
   
    “APP.vue”vue 文件入口界面
   
    “main.js”对应App.vue创建的实例，也是入口文件，对应   webpack.base.config.js里的入口配置
   
   Static文件夹：静态资源
   
   Pack.json:scripts 里面设置命令，例如设置了dev用于调试则我们开发时输入的是npm run dev ；例如设置了build 则是输入 npm run build 用于打包;另一部分是这里可以看到我们需要的依赖包,在dependencies和devDependencies中，分别对应全局下载和局部下载的依赖包
   
   ```

## （十一）其他

### 实际工作部分

1. webpack是怎样配置的，简述过程

   - 第一在项目文件创建一个webpack.config.js文件，配置文件创建好了
   - 第二开始正式配置webpack了，首先下载好node.js，因为webpack基于node.js,装好node.js后，通过命令行窗口找到项目文件，在项目文件webpack.config.js文件所在的目录下输入 npm install webpack -save dev 下载webpack依赖文件到本地项目中，下载好后会在webpack.config.js文件下自动创建node_modules文件夹，文件夹里就是所有项目中用到的依赖插件，现在只有一个webpack，项目中用到在下载！

2. git的作用是什么？有哪些指令？作用是什么？如果想要文件的一部分而不是整个工程文件，使用什么命令？git的冲突怎么解决?

   ```markdown
   git是一个开源的分布式版本控制系统，用以有效、高速处理很小到非常大的项目版本管理。
   常用的命令：
   git init   初始化仓库
   git config --globaluser.name    配置用户名
   git config --globaluser.email    配置邮箱
   git add      文件添加到暂存区
   git commit   文件添加到仓库
   git branch    列出所有的分支
   git status     显示有变更的文件
   git log       查看当前分支的版本历史
   git push      提交本地代码到远程
   git pull       从远程仓库下载到本地
   git checkout   创建切换分支
   解决git分支冲突： 将本地dev删除,在重新checkout一个dev分支(保证了此时我们的本地dev分支是最新的),在进行pull服务器分支,就这样解决了.
   
   
   ```

3. 怎么防止内存泄漏？

   - 减少不必要的全局变量，或者生命周期较长的对象，及时对无用的数据进行垃圾回收
   - 注意程序逻辑，避免“死循环”之类的
   -  避免创建过多的对象 。

4. 网站优化时怎么做数据分析？

   - 网站优化时，我们需要每天在百度统计中查看我们网站的每日流量，还有在各大站长平台中查看网站的收录量，网站关键词流量，还有就是每天要用站长工具查看网站的基本情况。这些数据都是最基础的。