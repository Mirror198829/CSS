# 💪布局解决方案
## 居中布局
### 水平居中
  父元素与子元素宽度不定
``` html
<div class="parent1 parent">
  <div class="child1 child">demo</div>
</div>
```
#### inline-block + text-align
``` css
.parent1{text-align: center;}
.child1{display: inline-block;}
```
#### table + margin
``` css
.parent2{}
.child2{display: table;margin:0 auto;}
```
#### absolute + transform
``` css
.parent3{position: relative;}
.child3{position: absolute;left:50%;transform: translateX(-50%);}
```
#### flex + justify-content
``` css
.parent4{display:flex;justify-content:center;}
```
### 垂直居中
  父元素与子元素高度不定
#### table-cell + vertical-align
``` css
.parent5{display: table-cell;vertical-align: middle;}
```
#### absolute + tranform
``` css
.parent6{position: relative;}
.child6{position: absolute;transform: translateY(-50%);top:50%;}
```
#### flex + align-items
``` css
.parent7{display: flex;align-items:center;}
```
### 水平垂直居中
#### inline-block + text-align + table-cell + vertical-align
``` css
.parentT{height:200px;background-color: #ccc;width:500px;}
.parent8{text-align: center;display: table-cell;vertical-align: middle;}
.child8{display: inline-block;}
```
#### absolute + transform
``` css
.parent9{position: relative;}
.child9{position: absolute;transform: translate(-50%,-50%);top:50%;left:50%;}
```
#### flex + justify-content + align-items
``` css
.parent10{display: flex;align-items: center;justify-content: center;}
```
---
## 多列布局
### 定宽+自适应
![avatar](https://mirror198829.github.io/static/github/colum1.png)
``` html
<div class="parent1 parent">
  <div class="left1 left">left</div>
  <div class="right1 right">
    <p>right</p>
    <p>right</p>
    <p>right</p>
  </div>
</div>
```
#### float + margin （问题：左侧浮动脱离文档流）
``` css
.left1{float:left;width:100px;}
.right1{margin-left: 120px}
```
#### float + overflow （问题：左侧浮动脱离文档流）
``` css
.left2{float:left;width: 100px}
.right2{overflow:hidden;}
```
#### table (可实现左右等高)
``` css
.left3{display: table-cell;width:100px;table-layout: fixed;}
.right3{display: table-cell}
```
#### flex (可实现左右等高)
``` css
.parent4{display: flex}
.left4{width:100px;margin-right: 10px}
.right4{flex:1;}
```
### 不定宽+自适应
![avatar](https://mirror198829.github.io/static/github/colum2.png)
#### float + overflow
``` css
.left5{float:left;}
.right5{overflow:hidden;}
```
### table
``` css
.parent6{display: table;width: 100%}
.left6{display: table-cell;width:0.1%;}
.right6{display: table-cell}
```
### flex
``` css
.parent7{display: flex}
.left7{margin-right: 10px}
.right7{flex:1;}
```
### 等分布局
![avatar](https://mirror198829.github.io/static/github/average.png)
``` html
<div class="parent8 parent clearfix">
  <div class="column8 column"><p>column</p></div>
  <div class="column8 column"><p>column</p></div>
  <div class="column8 column"><p>column</p></div>
  <div class="column8 column"><p>column</p></div>
</div>
```
#### float
并不理想
``` css
.parent8{margin-left: -20px;}
.column8{float:left;width:25%;padding-right:20px;box-sizing: border-box;}
```
#### flex
``` css
.parent9{display: flex}
.column9{flex:1;}
.column9+.column9{margin-left:20px;}
```
### 等高布局
![avatar](https://mirror198829.github.io/static/github/sameHigh.png)
#### table
``` css
.parent10{display: table;width: 100%;table-layout: fixed}
.left10{display: table-cell;width: 100px;}
.right10{display: table-cell}
```
#### flex
``` css
.parent11{display: flex}
.left11{margin-right: 10px}
.right11{flex:1;}
```
#### float
``` css
.parent12{overflow: hidden;}
.left12{float:left;margin-right: 10px}
.right12{overflow: hidden}
.left12,.right12{padding-bottom:9999px;margin-bottom: -9999px}
```
## 全屏布局
![avatar](https://mirror198829.github.io/static/github/fullscreen.png)
#### position
``` html
<div class="wrap">
  <div class="parent1 parent">
    <div class="top1 top">top</div>
    <div class="left1 left">left</div>
    <div class="right1 right">
      <div style="height:1000px;width:2000px"><p>bottom</p><p>bottom</p><p>bottom</p><p>bottom</p><p>bottom</p><p>bottom</p>                      <p>bottom</p><p>bottom</p><p>bottom</p></div>
    </div>
    <div class="bottom1 bottom">bottom</div>
  </div>
</div>
```
``` css
.wrap{width:95%;height:500px;border:2px dashed #333;margin:0 auto;color:#fff;}
.parent{width:100%;height:100%;}
.top{height:50px;background-color: #ccc}
.bottom{height:50px;background-color: #ccc}
.left{background-color: #cf1200}
.right{background-color: #4a7fc0;overflow: auto}
.parent1{position: relative;}
.top1{position: absolute;top:0;left:0;right: 0}
.bottom1{position: absolute;bottom:0;left:0;right: 0}
.left1{position: absolute;width:100px;top:50px;bottom:50px;}
.right1{position: absolute;top:50px;bottom:50px;left:100px;right: 0}
```
#### flex
``` html
<div class="wrap">
  <div class="parent2 parent">
    <div class="top2 top">top</div>
    <div class="middle2">
      <div class="left2 left">left 200px</div>
      <div class="right2 right">
        <div style="height:1000px;width:2000px"><p>bottom</p><p>bottom</p><p>bottom</p><p>bottom</p><p>bottom</p><p>bottom</p><p>bottom</p><p>bottom</p><p>bottom</p></div>
      </div>
    </div>
    <div class="bottom2 bottom">bottom</div>
  </div>
</div>

/*flex*/
.parent2{display: flex;flex-direction: column;}
.middle2{flex:1;display: flex}
.left2{width: 200px;}
.right2{flex:1;}
```
#### vh
通过vh单位也可实现全屏布局

![avatar](https://mirror198829.github.io/static/github/fullscreen2.png)
#### flex 
通过flex可以实现上述布局
