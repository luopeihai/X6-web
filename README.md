# X6-web
### 前言
* <font face="黑体" color=#999 size=5>通过web服务 在线运行案列(点击"栗子"看运行效果)讲解前端技能点和面试题(web front-end technology   Interview  vue react react-native)</font>
* <font face="黑体" color=#999 size=5>运行胜于一切背题,源码在demo下欢迎拿走,背题你就破功了 老弟!</font>




## css 题目

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

### 文本溢出
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






