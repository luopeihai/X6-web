# X6-web

### 前言

- <font face="黑体" color=#999 size=5>通过 web 服务 在线运行案列(点击"栗子"看运行效果)讲解前端技能点和面试题(web front-end technology Interview vue react react-native)</font>
- <font face="黑体" color=#999 size=5>运行胜于一切背题,源码在 demo 下欢迎拿走,背题你就破功了 老弟!</font>

## css 问题

### 水平垂直居中 [栗子](http://demo.freelancerman.cn/demo/css/horizontal_vertical_center.html)

- 绝对定位+margin:auto (父类为相对位置,子类为绝对位置)

  ```
   .box{
       position: relative;
       height:400px;
       background: #3acec1;
   }

   .box > div{
        position:absolute;
        width: 200px;
        height: 200px;
        background: gray;
        left:0;
        top: 0;
        bottom: 0;
        right: 0;
        margin: auto;
    }
  ```

- 绝对定位+负 margin

  ```
  .box{
       position: relative;
       height:400px;
       background: #3acec1;
   }

   .box > div{
        position:absolute;
        width: 200px;
        height: 200px;
        margin-left:-100px;
        margin-top:-100px;
        background: gray;
        left:50%;
        top: 50%;
    }
  ```

- 绝对定位+transform

  ```
  .box{
       position: relative;
       height:400px;
       background: #3acec1;
   }

   .box > div{
        position:absolute;
        width: 200px;
        height: 200px;
        transform: translate(-50%,-50%);
        background: gray;
        left:50%;
        top: 50%;
    }
  ```

- flex 布局

  ```
  .box{
       height:400px;
       background: #3acec1;
       display:flex;
       justify-content:center;
       align-items:center;
   }

   .box > div{
        width: 200px;
        height: 200px;
        background: gray;
    }
  ```

- table-cell(单元格)实现居中,子类要设置为内联块状元素

  ```
  .box{
       height:400px;
       width:600px;
       background: #3acec1;
       display:table-cell;
       text-align:center;
       vertical-align: middle;
   }

   .box > div{
        display: inline-block;
        width: 200px;
        height: 200px;
        background: gray;
    }

  ```

  问个衍生问题 需要水平垂直居中元素 宽高不确定有几种方法能让它 水平垂直居中?
  答:绝对定位+transform,flex 布局 ,table-cell(单元格)

### 画三角形 [栗子](http://demo.freelancerman.cn/demo/css/triangle.html)

通过把内容宽高设置为零,设置边框宽度,3 边颜色为透明,留一边显示颜色

```
  .triangle{
      height: 0px;
	  width: 0px;
	  border-color: transparent red transparent transparent;
	  border-style: solid;
	  border-width: 100px;
  }

```

### 隐藏节点的方法 [栗子](http://demo.freelancerman.cn/demo/css/hide.html)

- display:none 隐藏后的元素不占据任何空间
- visibility: hidden 隐藏后元素空间依旧保留
- opacity:0 节点被透明隐藏元素空间依旧保留

### 清除浮动的方法 [栗子](http://demo.freelancerman.cn/demo/css/float.html)

- clear:both 浮动的兄弟节点添加该属性

  ```
    .box .left {
      height: 100px;
      width: 100px;
      float: left;
      background-color: #33aaff;
    }
    .box .clear {
      clear: both;
      height: 100px;
      background-color: #33aacc;
    }

    //html 代码
    <div class="box">
        <div class="left">浮动部分</div>
        <div class="clear">清除浮动</div>
    </div>
  ```

- overflow: hidden 属性为在浮动的父类容器内
  ```
   .box {
     overflow: hidden;
   }
   .box .left {
     height: 100px;
     width: 100px;
     float: left;
     background-color: #33aaff;
   }
   //html 代码
   <div class="box">
       <div class="left">浮动部分</div>
   </div>
  ```
- 父容器 伪类设置 clear: both

  ```
  .box::after {
     content: ""; //内容要为空
     display: block; //要为块状元素
     clear: both;
   }
   .box .left {
     height: 100px;
     width: 100px;
     float: left;
     background-color: #33aaff;
   }
   //html 代码
   <div class="box">
       <div class="left">浮动部分</div>
   </div>

  ```

### 常用的伪类 [栗子](http://demo.freelancerman.cn/demo/css/pseudo_class.html)

首先要听清楚问的是<font face="黑体" color=red >伪类</font>还是<font face="黑体" color=red >伪元素</font>,伪类是以一个冒号(:)作为前缀 是某个元素的一种虚拟状态,常用的伪类有

- :link 链接的正常状态显示的样式
- :visited 链接被点击过显示的样式
- :hove 鼠标悬浮显示的样式
- :active 在鼠标点击显示样式
- :focus 选中时候显示样式 (一般是表单用的比较多)
- :first-child 一组兄弟元素中的第一个元素
- :last-child 一组兄弟元素中的最后一个元素
- :nth-child(n) 一组兄弟元素中的地 n(1~n)元素

### 常用的伪元素 [栗子](http://demo.freelancerman.cn/demo/css/pseudo_element.html)

通过 CSS 来创建伪元素 它们在文档树或 DOM 中并不实际存在

- ::defore
- ::after (节点顺序 : :defore > 内容子节点 > :after)
- ::selection 文档中被用户选中部分

### 文本溢出 [栗子](http://demo.freelancerman.cn/demo/css/overflow_text.html)

- 单文本溢出
  ```
   overflow: hidden;
   text-overflow:ellipsis;
   white-space: nowrap;
  ```
- 多行文本溢出
  ```
   display: -webkit-box; /* 弹性伸缩盒子模型显示 */
     -webkit-box-orient: vertical; /*  检索伸缩盒对象的子元素的排列方式 */
     -webkit-line-clamp: 3; /*用来限制在一个块元素显示的文本的行数 */
     overflow: hidden;
  ```

### 常用的 css3 属性 [栗子](http://demo.freelancerman.cn/demo/css/css3.html)

- border-raidus 圆角
- box-shadow 阴影
- background-image 背景图
- background-size 背景图大小
- linear-gradient 背景渐变
- text-shadow 文本阴影
- @font-face 引用字体
- transform
- transition 过度
- animation 动画
- box-sizing 盒子模型设置
- flex 弹性盒子
- @media 多媒体查询

### px,rem,em 区别

- px 为绝对长度单位
- em 为相对长度单位,会继承父级元素的字体大小
- rem 为相对长度单位,区别于 em rem 总是相对于根元素

### rgba,opacity 区别

区别就是 opacity 会继承父元素的 opacity 属性 也就是做子类会继承父类的透明度，而 rgba 设置元素的后代元素不会继承不透明属性

### box-sizing

CSS 重要的一个概念就是 CSS 盒子模型。它控制着页面这些元素的高度和宽度,实际盒子的宽高 = border+padding+样式设置 width/height,变成了样式中设置的 width/height 不等于实际节点的 width/height 给实际开发带来了一定问题,故 css3 有了 box-sizing 属性:
语法：box-sizing: content-box | border-box | inherit;

- content-box(标准模式) 为默认属性 实际 width/height = border+padding+样式设置 width/height
- border-box(怪异模式) 实际 width/height = 样式设置 width/height = border+padding+ width/height
- inherit 继承 父元素 box-sizing 属性的值

### position 的值 [栗子](http://demo.freelancerman.cn/demo/css/position.html)

- absolute 相对于 static 定位以外的第一个父元素进行定位。
- fixed 生成固定定位的元素，相对于浏览器窗口进行定位。（老 IE 不支持）
- relative 生成相对定位的元素，相对于其正常位置进行定位，不脱离文档流。
- static 默认值。没有定位，元素出现在正常的文档流中（忽略 top, bottom, left, right 或者 z-index 声明）。
- inherit 规定应该从父元素继承 position 属性的值。

### CSS 浏览器兼容性

**兼容性问题造成的原因**:众多的浏览器厂商,不同的版本,对同一段 CSS 的解析效果也不一致，这就导致了页面显示效果不统一，也就带来了兼容性问题。

解决方法:

- **浏览器 CSS 样式初始化** ([Normalize.css](https://github.com/necolas/normalize.css)是一种 CSS reset 的替代方案可以使用)
  ```
   *{
        margin: 0;
        padding: 0;
    }
  ```
- **浏览器私有属性** 当 W3C 组织成员提出一个新属性 需要走很复杂的程序，审查等,浏览器商不能等太久,所以先把新属性加自己浏览器能识别的前缀,常用的前缀有：

  - -moz 代表 firefox 浏览器私有属性
  - -ms 代表 IE 浏览器私有属性
  - -webkit 代表 chrome、safari 私有属性
  - -o 代表 opera 私有属性

> > 比如 transform 的使用

```
   -webkit-transform:rotate(-3deg); /*为Chrome/Safari*/
   -moz-transform:rotate(-3deg); /*为Firefox*/
   -ms-transform:rotate(-3deg); /*为IE*/
   -o-transform:rotate(-3deg); /*为Opera*/
   transform:rotate(-3deg);
```

- **hack** 有时我们需要针对不同的浏览器或不同版本写特定的 CSS 样式，这种针对不同的浏览器/不同版本写相应的 CSS code 的过程，叫做 CSS hack!

  > CSS hack 的写法大致归纳为 3 种：条件 hack、属性级 hack、选择符级 hack。

  - **_条件 hack_** 条件 hack 主要针对 IE 浏览器进行一些特殊的设置 (**_IE10 及以上版本已将条件注释特性移除_**)

  ```
   <!--[if <keywords>? IE <version>?]>
     代码块，可以是html，css，js
    <![endif]-->

    栗子:
    <!--[if IE]>
        <p>你在非IE中将看不到我的身影</p>
    <![endif]-->

    <!--[if IE]>
    <style>
        .test{color:red;}
    </style>
    <![endif]-->

    <!--[if lt IE 9]>
        <script src="//cdn.bootcss.com/html5shiv/3.7.2/html5shiv.min.js"></script>
        <script src="//cdn.bootcss.com/respond.js/1.4.2/respond.min.js"></script>
    <![endif]-->
  ```

- **自动化插件** [Autoprefixer](https://github.com/postcss/autoprefixer)是一款自动管理浏览器前缀的插件,只需按照最新的 W3C 规范来正常书写 CSS 即可

## js 问题

### 变量提升

变量提升为:函数及变量的**声明**都将被提升到函数的最顶部,变量可以在使用后声明，也就是变量可以先使用再声明。

- var 变量提升

  ```
      a = 2;
      var a;
      console.log(a);  //2

      var b;
      console.log(b);​ //undefined
      b = 2;
  ```

  提升过程:
  1.a,b 声明都往上提到最上 2.初始化声明变量 a=undefined; b=undefined; 3.执行阶段 执行语句代码
  **_变量初始和赋值不是同一时间执行_**

- function 函数提升
  ```
  test();//test
  function test(){
        console.log("test")
  }
  ```
  1.在全局环境(window)中找到所有用 function 声明往上提 2.将这些变量「初始化」并「赋值」为 function(){ console.log("test") } 3.执行阶段 执行语句代码
  **_function 的初始和赋值同时执行_**
- let,const 的变量提升(let 和 const 变量提升相同,这里用 let 举栗子)
  ```
  let x = 'global'{
    console.log(x) // Uncaught ReferenceError: x is not defined
    let x = 1
    let y;
    console.log(y) //undefind
  }
  ```
  **_这里要注意的是 脚本是直接报错 x is not defined_**
  1. 找到所有用 let 声明的变量，在环境中「创建」变量
  2. 开始执行代码（注意现在 let x 并没有像 var 样有初始化为 undefined 的操作,所以不能使用 x（也就是 let ,const 所谓的“暂时性死区”,“暂时性死区”不是 ECMAScript 规范里的正式定义，它只是在程序员中广为流行而已））
     **_以上 代码执行可以理解成:let 的「创建」过程被提升了，但是没初始化_**

综上 var function let 写了一个栗子,建议在 console 执行一遍 加深印象

```
var a=1
b = 2
foo()
function foo(){
  console.log(a) //undefined
  console.log(b) //Uncaught ReferenceError: b is not defined(报错)
  let b = 3;
  //let b = 4; //Uncaught SyntaxError: Identifier 'b' has already been declared(报错 let不能重复声明)
  var a=c=2       //var 函数作用域变量
}
console.log(c); //2  c其实声明的是全局变量

```

### typeof 和 instanceof 的区别

- typeof 操作符返回一个字符串,为变量的基本类型

  ```
  typeof 123 // "number"
  typeof '123' // "string"
  typeof false // "boolean"
  typeof undefined // "undefined"
  typeof window // "object"
  typeof {} // "object"
  typeof [] // "object"
  typeof null // "object"

  ```

- instanceof 是判断变量是否为某个对象的实例，返回值为 true 或 false

  ```
    var o = {};
    var a = [];

    o instanceof Array // false
    a instanceof Array // true
    a instanceof Object // true
  ```

  **_typeof 对数组 [] 和对象 {} 的返回值都是 Object，无法区分数组和对象，但是 instanceof 可以区分。_**

### 事件委托代理

事件委托就是利用事件冒泡，只指定一个父类容器事件处理程序，就可以管理子类所有事件 ,这种机制处理效率高于对每个子项注册事件

```
css:

<ul id="todo-app">
  <li class="item">Walk the dog</li>
  <li class="item">Pay bills</li>
  <li class="item">Make dinner</li>
  <li class="item">Code for one hour</li>
</ul>



js:

document.addEventListener('DOMContentLoaded', function() {
  let app = document.getElementById('todo-app');

  app.addEventListener('click', function(e) {
    if (e.target && e.target.nodeName === 'LI') {
      let item = e.target;
      alert('you clicked on item: ' + item.innerHTML)
    }
  })
})


```

### querySelectorAll 与 getElementsBy 区别

两种方法返回都是数组,区别:

- querySelectorAll 方法接收的参数是一个 CSS 选择符,而且必须严格符合 CSS 选择符规范。而 getElementsBy 系列接收的参数只能是单一的 className、tagName 和 name。

  ```
  //获取 class="ul" 内的 子节点li
  //querySelectorAll 获取法
  var queryLi = document.querySelectorAll(".ul>li") //css 选择器写法

  //getElementsBy 获取方法
  var dmoUl = document.getElementsByClassName('ul')[0]
  var dmoli = dmoUl.getElementsByTagName("li")
  ```

- querySelectorAll 返回的是一个 NodeList(静态)，而 getElementsBy 系列的返回的是一个 HTMLCollection(实际节点)。
- getElementBy 系列的执行速度比 querySelectorAll 的  快

### 节流（throttle）与防抖（debounce）[栗子](http://demo.freelancerman.cn/demo/js/debounce_throttle.html)

- **_防抖_** 事件被触发 n 秒后再执行，如果在这 n 秒内又被触发，则重新计时,直到执行最后一次触发.

```
//实际开发中 input 输入联想匹配 需要用到防抖,就觉这个例子
//防抖 监听
document.getElementById("debounce").addEventListener("keyup", function(e) {
debounce(ajax, 500, e.target.value);
});

    //模拟一段ajax请求
    function ajax(content) {
      document.getElementById("input-text").innerHTML = content;
    }

    function debounce(fun, delay, inputValue) {
      clearTimeout(this.id);
      this.id = setTimeout(function() {
        fun(inputValue);
      }, delay);
    }

```

- **_节流_** 在事件被触发 n 秒后再执行,间隔时间执行,忽略间隔时间内的多次触发

```
    //实际开发中 按钮不断点击触发，单位时间内只触发一次
     //点击次数
    var throttleTime = 0;
    //节流 监听
    document.getElementById("throttle").addEventListener("click", function(e) {
      throttle(function() {
        throttleTime += 1;
        document.getElementById("throttle-text").innerHTML = throttleTime;
      }, 3000);
    });

    var isRun = false;
    function throttle(fun, delay) {
      if (isRun) {
        return;
      } else {
        isRun = true;
      }

      this.id = setTimeout(function() {
        fun();
        isRun = false;
        clearTimeout(this.id);
      }, delay);
    }

```
