# CSS

### 1. **CSS3新特性**

#### 一、开发商前缀

|   前缀   |        开发商         |
| :------: | :-------------------: |
|  -moz-   |        FireFox        |
| -webkit- | Chrome、Safari、Opera |
|   -ms-   |          IE           |
|   -o-    |    Opera旧版15之前    |



#### 二、静态样式

##### 		2.1 Web字体

```css
@font-face {
    font-family: "pingFangSC-Regular";
    src: url("../font/PingFang Regular_0.ttf");
    font-weight: normal;
    font-style: normal;
}
/// html页面引用   link标签引入； font-family设置
<link rel="stylesheet" href="./css/font.css">
```



##### 		2.2 背景background

###### 				2.2.1 支持多背景

```css
background-image: url("..."), url("...")...
```

###### 				2.2.2 各背景位置

```css
background-position: poisition-1   position-2 ...
```

###### 				2.2.3 各背景的平铺方式

```css
background-repeat: repeat-1,  repeat-2, ...
```

```css
.decorateBox {
    margin: 50px;
    padding: 20px;
    background-image: url("top-left.png"), url("right-bottom.png");
    background-position: left top, right  bottom;
    background-repeat: no-repeat, no-repeat;
}
```



##### 		2.3 渐变

###### 		2.3.1 线性渐变linear-gradient()

```css
background-image: linear-gradient(to direction/angle, color1 [percentage1], color2 [percentage2] ...)

direction: 八个方向， 默认起点在top
angle: 底线为0deg
percentage： 起点
```



###### 		2.3.2 径向渐变radial-gradient()

```css
background-image: radial-gradient([shape size at position], start-color, ..., end-color);
// 参数
shape: 圆的类型
	ellipse: (默认)指定椭圆形的镜像渐变
	circle: 指向圆形的径向渐变

size: 定义渐变的大小
	farthest-corner(默认): 指定径向渐变的半径长度为从圆心到离圆心最远的角
	closest-side: 指定径向渐变的半径长度为从圆心到离圆心最近的边
	closest-corner: 指定径向渐变的半径长度为从圆心到离圆心最近的角
	farthest-side: 指定径向渐变的半径长度为圆心到离圆心最远的边

position: 定义渐变的位置
	1. 位置名词
		center:(默认) 设置中间为径向渐变圆心的纵坐标值。
		top: 设置顶部为径向渐变圆心的纵坐标值
		bottom: 设置底部为径向渐变圆心的纵坐标值
	2. 自定义位置
		percentage1、percentage2
			percentage1： 距离左边的距离
			percentage2： 距离顶部的距离
```

```html
<!DOCTYPE html>
<html>

<head>
    <meta charset="UTF-8">
    <title>线性渐变与径向渐变</title>
    <style type="text/css">
        .box1 {
            width: 100px;
            height: 100px;
            background-image: linear-gradient(to left, red, blue);
            float: left;
        }

        .box2 {
            width: 100px;
            height: 100px;
            background-image: linear-gradient(red, blue);
            float: left;
        }

        .box3 {
            width: 100px;
            height: 100px;
            background-image: linear-gradient(to right bottom, red, blue);
            float: left;
        }

        .box4 {
            width: 100px;
            height: 100px;
            background-image: linear-gradient(60deg, red, blue);
            float: left;
        }

        .box5 {
            width: 100px;
            height: 100px;
            background-image: linear-gradient(red 40%, blue 70%);
            float: left;
        }

        .box6 {
            width: 100px;
            height: 100px;
            background-image: radial-gradient(circle, red 30%, yellow 50%, blue 80%);
            float: left;
        }

        .box7 {
            width: 100px;
            height: 100px;
            background-image: radial-gradient(circle, white, blue);
            float: left;
        }

        .box8 {
            width: 100px;
            height: 100px;
            background-image: repeating-radial-gradient(circle, yellow, green 10%);
            float: left;
        }
    </style>
</head>

<body>
    <div class="box1"></div>
    <div class="box2"></div>
    <div class="box3"></div>
    <div class="box4"></div>
    <div class="box5"></div>
    <div class="box6"></div>
    <div class="box7"></div>
    <div class="box8"></div>
</body>

</html>
```



###### 		2.3.3 循环渐变repeating-radial-gradient（）/ repeating-linear-gradient（）

```tex
/**最重要的是限制渐变的大小（用起点），以使其可以循环**/
background-image: repeating-linear-gradient(to direction/angle, color1 [percentage1], color2 [percentage2], ..., colorn [percentagen])

background-image: repeating-radial-gradient([shape size at position], start-color, ..., last-color);
```

```css
.box8 {
    width: 100px;
    height: 100px;
    backgeound-image: repeating-gradial-gradient(circle, yellow, green 10%);
}
```



##### 		2.4 圆角border-radius

###### 		2.4.1 border-radius: 每个角内切圆半径

```tex
/**
语法：
两个值： 左上右下  右上左下
四个值： 左上 右上 右下 左下
**/
```

```css
/**圆（容器宽和高相同）**/
border-radius: 50%;
```

```css
/**椭圆（容器宽是高的两倍）**/
border-radius: wisth / height;
```

```css
/**上半圆（容器宽是高的两倍）**/
border-radius： height height 0 0 ;
```

```css
/**侧半圆（容器宽是高的两倍）**/
border-radius:width 0 0 width;
```



###### 		2.4.2 border （top/bottom/left/right）- radius : 针对某一个角

```css
/**
语法：
适合用来标识不规则的圆形
两个值： 水平半径  垂直半径
一个值： 水平半径和垂直半径为指定值
**/
```



##### 		2.5 阴影shadow

###### 		2.5.1 text-shadow: 文字阴影

```css
/**语法**/
text-shadow (x,y,blur,color1, x2,y2,blur, color2,....)
	x: 向右移动x个单位
	y: 向下移动y个单位
	blur: 模糊度，单位px，值越大越模糊
	color: 不写阴影颜色默认和字体颜色相同，可以改其值
```



###### 		2.5.2 box-shadow: 盒子阴影

```css
/**语法**/
box-shadow: (x y blur spread color [inset], x2 y2 blur2 spread2 color2 [inset])
	x: 阴影向左移动x个单位
	y: 阴影向下移动y各单位
	blur: 模糊度，值越大越模糊，单位px
	spread:增大模糊边界之前实心颜色面积，值越大，面积越大
	color: 颜色
	inset: 内阴影，不写默认为外阴影，写了outset无效果
```



##### 		2.6 透明度opacity

###### 		2.6.1 方式1： rgba()

```css
rgba(0~255,0~255,0~255,0~1)
```



###### 		2.6.2 方法2： opacity

```css
IE: filter: alpha(opacity="value")

0~100
```

```css
现代浏览器：opacity

0(透明)~ 0.5(半透明) ~ 1(不透明)
```



###### 		2.6.3 区别

```css
方式1： 可以让指定的样式透明，而不影响其他样式
方式2： 占空间，且所有子内容都会透明
```



#### 三、动态样式

##### **3.1 transition过渡**

**3.1.1 transtion-property: 规定设置过渡效果的css属性的名称**

```css
如果要全部属性则用all
```

###### **3.1.2 transition-duration: 规定完成过度动画效果需要的时间**

```css
单位： 秒/毫秒
```

###### **3.1.3 transition-delay: 规定过渡效果延迟时间**

```css
单位： 秒/毫秒
延迟则数值为正，提前则为负
如果是提前的话，当要开始的时候直接变为当前秒数的样式，没有延迟。就是说，如果提前两秒的话，那么当过度开始的时候直接变为两秒的时候应该有的样式。
```

###### **3.1.4 transition-timing-function: 规定速度效果的速度曲线**

```css
linear: 匀速
ease: 默认值，速度逐渐慢下来
ease-in: 加速
ease-out: 减速
cubic-bezier: 先加速后减速
```

```html
<!DOCTYPE html>
<html>

<head>
    <title>过渡动画</title>
    <style>
        div {
            width: 100px;
            height: 100px;
            background-color: red;
            transition-property: all;
            transition-delay: -1s;
            transition-duration: 3s;
            transition-timing-function: ease-in;
            /*复合写法 transition: all 3s -1s ease-in; */
        }
        div:hover {
            width: 200px;
            height: 200px;
            background-color: blue;
        }
    </style>
</head>

<body>
    <div></div>
</body>

</html>
```

###### **3.1.5 符合样式**

```css
transition: 属性  完成时间  延迟时间  速度曲线
	属性和曲线不写就默认all 和 linear
	transition 属性不能添加到hover伪类上
```

###### **3.1.6 常常与transition有联系的样式**

```css
opacity 透明度
shadow  阴影
渐变
transform 变形
```

###### **3.1.7 触发方式**

```css
1、 hover / focus 伪类定义新的样式，移入移出或聚焦造成过渡动画效果
2、 js操作该对象的样式
```

##### **3.2 transform 变换**

###### **3.2.1 translate 位移**

```css
/***语法：***/
translate(valueX, valueY)  x,y方向上都有位移
translate(value)  默认一个值是x方向上的位移
translateX(value)
translateY(value)
translateZ(value)
```

###### **3.2.2 scale 缩放**

```css
/***语法（单位： 比例值）***/
scale(value)  写一个值就是宽高都缩放
scaleX(x) 在x轴缩放x倍， -1的话会左右翻转（镜像翻转）
scaleY(y)
scaleZ(z)
```

###### **3.2.3 rotate旋转**

```css
/***语法：（单位：角度deg）***/
rotate(value deg)  和 rotateZ是相同的效果
roatetX(x deg)  正值沿着x轴向上翻转，负值沿着x轴向左翻转
rotateY(y deg)
rotateZ(z deg)
```

###### **3.2.4 skew 斜切**

```css
/**单位  角度deg**/
skew(value deg)  与skewZ效果相同
skew(x deg, y deg) skewX与skewY 效果都有
skewX(x deg)  水平方向保持不变。垂直方向正值向左倾斜，负值向右倾斜
skewY(y deg)
```

```html
<!DOCTYPE html>
<html>

<head>
    <meta charset="UTF-8">
    <title>位移与缩放</title>
    <style>
        .box1 {
            width: 100px;
            height: 100px;
            background-color: red;
            transform: skew(30deg);
            float: left;
            margin: 60px;
        }

        .box2 {
            width: 100px;
            height: 100px;
            background-color: red;
            transform: skewY(30deg);
            float: left;
            margin: 50px;
        }

        .box3 {
            width: 100px;
            height: 100px;
            background-color: red;
            float: left;
            margin: 50px;
        }

        .box4 {
            width: 100px;
            height: 100px;
            background-color: red;
            float: left;
            transform: translate(100px) skew(45deg);
        }
    </style>
</head>

<body>
    <div class="box1"></div>
    <div class="box2"></div>
    <div class="box3"></div>
    <div class="box4"></div>
</body>

</html>
```

###### **3.2.5 transform-origin: 基点的位置（变形的基准位置）**

```css
transition-origin: x y [z 3D的时候才需要设置z]
```

###### **3.2.6 变形操作只能添加给块元素，但是不能添加给行内元素**

```css
行内元素设置width和height无效，变形操作的底层逻辑是操作的都是对象的宽和高
```

###### **3.2.7 符合写法**

```css
符合写法： 可以同时添加多个操作对象
例： transform: translate(100px )  skew(45deg)  scale(2)  rotate(90deg)
```

###### **3.2.8 执行顺序(后写的先执行)**

```css
先写的translate不会收到后面的变形操作的影响
后写的translate()会收到先写的rotate、scale、skew的影响
	translate() 会位移（位移  缩放） 的长度
	translate() 会在rotate的角度的方向位移相应的长度，再进行旋转
	translate() 会在skew的角度的方向位移相应的长度，在进行斜切
```

##### **3.3 animation 动画**

###### **3.3.1 animation-name**

```css
设置动画的名字（自定义的名字）
```

###### **3.3.2 animation-duration** 

```css
动画的持续时间
```

###### **3.3.3 animation-delay** 

```css
动画的延迟时间
```

###### **3.3.4 animation-iteration-count**

```css
动画的重复次数，默认值就是1，单位是数值，infinite无限次数
```

**3.3.5 animation-timing-function**

```css
/***动画的运动方式***/
linear: 匀速
ease: 默认值，速度逐渐慢下来
ease-in: 加速
ease-out: 减速
cubic-bezier: 先加速后减速
```

###### **3.3.6 animation-fill-mode**

```css
规定动画播放的之前或之后，期动画效果是否可见
none: (默认值) 在运动结束后回到初始位置，在延迟的情况下，让0%在延迟后生效
backwards： 在延迟的情况下，让0%在延迟前生效
forwards: 在运动结束后，停在技术位置
both： backwards 和 forwards同时生效

注： 运动结束后，默认停在初始位置
```

**3.3.7 animation-direction**

```css
属性定义是否应该轮流反向播放动画
alternate： 一次正向（0%~100%）, 一次反向(100% - 0%)
reverse: 永远都是反向，从100% - 0%
normal: （默认值） 永远都是正向的，从0% - 100%
```

**3.3.8 复合写法**

```css
animation: name duration delay count function mode direction
```

**3.3.9 keyframe 定义动画过程**

```css
animation 定义在元素内，动画过程要写在@keyframe内
```

**3.3.10 引入animate.css**

```css
工具animate.css,引入各种动画样式

```



#### 四、布局

**4.1 分栏布局**



### 2.  **清除浮动的几种方法**

### 3. **盒子模型**

### 4. **Flex布局**

### 5. **BFC原理**

### 6. **position定位**

### 7. **水平垂直居中的几种方式**

### 8. **CSS优先级权重**

### 9. **transition / animation 区别**

### 10. **border: none 和 border:0 的区别**

### 11. **diaplay: none / visibility   hidden / opacity:0 的区别**

