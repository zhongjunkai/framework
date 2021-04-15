## CSS提高页面渲染速度

1. content-visibility 它允许我们推迟选择元素的HTML元素渲染。

```css
content-visibility: auto;
content-intrinsic-size: 300px;
```

2. will-change 使得渲染器提前进行必要的优化。

```css
.animate {
    will-change:  opacity;
}
```

* auto：默认值，浏览器会根据具体情况，自行进行优化。
* scroll-position: 表示开发者将要改变元素的滚动位置，比如浏览器通常仅渲染可滚动元素“滚动窗口”中的内容。而某些内容超过该窗口（不在浏览器的可视区域内）。如果will-change显式设置了该值，将扩展“滚动窗口”周围的内容，从而顺利地进行更长、更快地滚动（让元素滚动更流畅）。
* content: 





































