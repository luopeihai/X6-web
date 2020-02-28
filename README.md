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



