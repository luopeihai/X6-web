# X6-web
通过web服务 在线运行案列(点击"栗子"看运行效果)讲解前端技能点和面试题(web front-end technology   Interview  vue react react-native)


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

