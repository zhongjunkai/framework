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
			
```



###### 		2.3.3 循环渐变repeating-radial-gradient（）/ repeating-linear-gradient（）

##### 		2.4 圆角border-radius

###### 		2.4.1 border-radius: 每个角内切圆半径

###### 		2.4.2 border （top/bottom/left/right）- radius : 针对某一个角

##### 		2.5 阴影shadow

###### 		2.5.1 text-shadow: 文字阴影

###### 		2.5.2 box-shadow: 盒子阴影

##### 		2.6 透明度opacity

###### 		2.6.1 方式1： rgba()

###### 		2.6.2 方法2： opacity

###### 		2.6.3 区别

#### 三、动态样式

#### 四、布局

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

