# X6-web
通过web服务 在线运行案列讲解前端技能点和面试题(web front-end technology   Interview  vue react react-native)
点击"栗子"看运行效果

## css 题目

### 水平垂直居中 [栗子](http://demo.freelancerman.cn/demo/css/horizontal_vertical_center.html){:target="_blank"}
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



