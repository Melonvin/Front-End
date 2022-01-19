# Check if an element is in the viewport

检查一个元素是否在视口内

## 准备

页面元素

```html
<div id="box"></div>
```

样式
```css
#box {
  position: absolute;
  left: -100px;
  width: 100px;
  height: 100px;
  background: pink;
}
```

## 解决

Element.getBoundingClientRect() 方法返回元素的大小及其相对于视口的位置。

```js
const el = document.getElementById("box");
const rect = el.getBoundingClientRect();
```

Window.innerHeight:浏览器窗口的视口（viewport）高度（以像素为单位）

Window.innerWidth:浏览器窗口的视口（viewport）宽度（以像素为单位）

判断算法：

在视口内：元素相对于视口的left >= 0,top >= 0,right <= window.innerWidth,bottom <= window.innerHeight

```js
console.log(
  rect.left > 0 &&
    rect.top > 0 &&
    rect.bottom < window.innerHeight &&
    rect.right < window.innerWidth
);
```

## 代码

[codesandbox](https://codesandbox.io/s/check-if-an-element-is-in-the-viewport-8f7kz)

[github](https://github.com/Melonvin/HTML-DOM-PRACTICE)

