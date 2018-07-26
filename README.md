# 布局解决方案
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
