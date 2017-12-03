# css-layout
7 kinds of CSS vertically centered solutions
CSS horizontal vertical center
**查看方式：** 直接运行 index.html
页面基本布局：

``` html
<div class="fatherBox">
	<div class="box base">
		<img src="./imgs/wolf.jpg" alt="">
	</div> 
</div>
```
### position 定位方案
``` css
/* case1 */
.box{
    position: absolute;
    top:50%;left:50%;
    transform:translate(-50%, -50%);
}
/* case2 需要指定宽高 */
.box{
    width:200px;height:200px;
    position: absolute;
    top:50%;left:50%;
    margin:-100px 0 0 -100px;
}
/* case3 需要指定宽高 */
.box{
    width:200px;height:200px;
    position: absolute;
    top: 0; left: 0; bottom: 0; right: 0; 
    margin:auto;
}
```
### display:flex 方案

```css
/* case4 */
.fatherBox{
    display: flex;
}
.box{
    margin:auto;
}
/* case5 */
.fatherBox{
    display: flex;
    align-items: center;
    justify-content: center;
}
```
### 借助伪元素 方案
原理：利用inline-block的vertical-align:middle去对齐after伪元素，after伪元素的高度与父元素一样，从而实现了高度方向的对齐。
``` css
/* case6 *
/* 关于vertica-align生效场景：只有一个元素属于inline或是inline-block（table-cell也可以理解为inline-block水平）水平，其身上的vertical-align属性才会起作用。一些默认情况下起作用的元素：如，图片，按钮，单复选框 */
.fatherBox{
    text-align: center;
}
.fatherBox:after{
    content:"";
    display: inline-block;
    vertical-align: middle;
    height:100%;
}
.box{
    vertical-align: middle;
}
```
### line-height 方案
line-height如果是百分比的话，是相对于字体大小的，so想要设置居中的话，就使用px
```css
/* case7 */
.fatherBox{
    position: relative;
    background-color: #ccc;
    height:300px;
    text-align: center; 
    line-height: 300px;
}
.box{
   display: inline-block;
   vertical-align: middle;
}
```



