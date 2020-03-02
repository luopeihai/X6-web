# X6-web
### 前言
* <font face="黑体" color=#999 size=5>通过web服务 在线运行案列(点击"栗子"看运行效果)讲解前端技能点和面试题(web front-end technology   Interview  vue react react-native)</font>
* <font face="黑体" color=#999 size=5>运行胜于一切背题,源码在demo下欢迎拿走,背题你就破功了 老弟!</font>

## css 问题

### 水平垂直居中 [栗子](http://demo.freelancerman.cn/demo/css/horizontal_vertical_center.html)
* 绝对定位+margin:auto (父类为相对位置,子类为绝对位置)
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
* 绝对定位+负margin
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
* 绝对定位+transform 
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
* flex布局 
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
* table-cell(单元格)实现居中,子类要设置为内联块状元素
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
答:绝对定位+transform,flex布局 ,table-cell(单元格)

### 画三角形 [栗子](http://demo.freelancerman.cn/demo/css/triangle.html)
通过把内容宽高设置为零,设置边框宽度,3边颜色为透明,留一边显示颜色
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
* display:none 隐藏后的元素不占据任何空间
* visibility: hidden 隐藏后元素空间依旧保留
* opacity:0 节点被透明隐藏元素空间依旧保留

### 清除浮动的方法 [栗子](http://demo.freelancerman.cn/demo/css/float.html)
* clear:both 浮动的兄弟节点添加该属性
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
*  overflow: hidden 属性为在浮动的父类容器内
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
*  父容器 伪类设置 clear: both
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
* :link  链接的正常状态显示的样式
* :visited 链接被点击过显示的样式
* :hove 鼠标悬浮显示的样式
* :active 在鼠标点击显示样式
* :focus 选中时候显示样式 (一般是表单用的比较多)
* :first-child 一组兄弟元素中的第一个元素
* :last-child 一组兄弟元素中的最后一个元素
* :nth-child(n)  一组兄弟元素中的地n(1~n)元素

### 常用的伪元素 [栗子](http://demo.freelancerman.cn/demo/css/pseudo_element.html)
通过CSS来创建伪元素 它们在文档树或DOM中并不实际存在
* ::defore 
* ::after (节点顺序 : :defore > 内容子节点 > :after)
* ::selection 文档中被用户选中部分

### 文本溢出 [栗子](http://demo.freelancerman.cn/demo/css/overflow_text.html)
* 单文本溢出
  ```
   overflow: hidden;
   text-overflow:ellipsis;
   white-space: nowrap;
  ```
* 多行文本溢出
   ```
    display: -webkit-box; /* 弹性伸缩盒子模型显示 */
      -webkit-box-orient: vertical; /*  检索伸缩盒对象的子元素的排列方式 */
      -webkit-line-clamp: 3; /*用来限制在一个块元素显示的文本的行数 */
      overflow: hidden;
   ```  
### 常用的css3 属性 [栗子](http://demo.freelancerman.cn/demo/css/css3.html)
* border-raidus 圆角
* box-shadow 阴影
* background-image 背景图
* background-size  背景图大小
* linear-gradient 背景渐变
* text-shadow 文本阴影
* @font-face 引用字体
* transform 
* transition 过度
* animation 动画
* box-sizing 盒子模型设置
* flex 弹性盒子
* @media 多媒体查询

### px,rem,em区别
* px 为绝对长度单位
* em 为相对长度单位,会继承父级元素的字体大小
* rem 为相对长度单位,区别于em rem总是相对于根元素


  
### box-sizing 
CSS重要的一个概念就是CSS盒子模型。它控制着页面这些元素的高度和宽度,实际盒子的宽高 = border+padding+样式设置width/height,变成了样式中设置的width/height 不等于实际节点的width/height给实际开发带来了一定问题,故css3 有了box-sizing属性:
语法：box-sizing: content-box | border-box | inherit;
* content-box 为默认属性 实际width/height = border+padding+样式设置width/height
* border-box 实际width/height = 样式设置width/height =  border+padding+ width/height
* inherit 继承 父元素 box-sizing属性的值

### position 的值 [栗子](http://demo.freelancerman.cn/demo/css/position.html)
* absolute 相对于 static 定位以外的第一个父元素进行定位。
* fixed 生成固定定位的元素，相对于浏览器窗口进行定位。（老IE不支持）
* relative 生成相对定位的元素，相对于其正常位置进行定位，不脱离文档流。
* static 默认值。没有定位，元素出现在正常的文档流中（忽略 top, bottom, left, right 或者 z-index 声明）。
* inherit 规定应该从父元素继承 position 属性的值。

### CSS浏览器兼容性
**兼容性问题造成的原因**:众多的浏览器厂商,不同的版本,对同一段CSS的解析效果也不一致，这就导致了页面显示效果不统一，也就带来了兼容性问题。

解决方法:
* **浏览器CSS样式初始化** ([Normalize.css](https://github.com/necolas/normalize.css)是一种CSS reset的替代方案可以使用)
  ```
   *{
        margin: 0;
        padding: 0;
    }
  ```
* **浏览器私有属性** 当W3C组织成员提出一个新属性 需要走很复杂的程序，审查等,浏览器商不能等太久,所以先把新属性加自己浏览器能识别的前缀,常用的前缀有：
   * -moz代表firefox浏览器私有属性
   * -ms代表IE浏览器私有属性
   * -webkit代表chrome、safari私有属性
   * -o代表opera私有属性
  
 >> 比如transform的使用
 ```
    -webkit-transform:rotate(-3deg); /*为Chrome/Safari*/
    -moz-transform:rotate(-3deg); /*为Firefox*/
    -ms-transform:rotate(-3deg); /*为IE*/
    -o-transform:rotate(-3deg); /*为Opera*/
    transform:rotate(-3deg); 
 ```
* **hack** 有时我们需要针对不同的浏览器或不同版本写特定的CSS样式，这种针对不同的浏览器/不同版本写相应的CSS code的过程，叫做CSS hack!
  >CSS hack的写法大致归纳为3种：条件hack、属性级hack、选择符级hack。
  * ***条件hack*** 条件hack主要针对IE浏览器进行一些特殊的设置 (***IE10及以上版本已将条件注释特性移除***)
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
* **自动化插件**  [Autoprefixer](https://github.com/postcss/autoprefixer)是一款自动管理浏览器前缀的插件,只需按照最新的W3C规范来正常书写CSS即可

## js 问题

  
  
  
 
 


  






