# 布局解决方案
## 居中布局
### 水平居中
  父元素与子元素宽度不定
#### inline-block + text-align
``` html
<div class="parent1 parent">
  <div class="child1 child">demo</div>
</div>
```
``` css
.parent1{text-align: center;}
.child1{display: inline-block;}
```
#### table + margin
``` html
<div class="parent2 parent">
  <div class="child2 child">demo</div>
</div>
.parent2{}
.child2{display: table;margin:0 auto;}
```
