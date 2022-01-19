# Calculate the mouse position relative to an element

计算鼠标点击相对于元素的位置

## 准备

页面元素

```html
<div id="box"></div>
```

样式

```css
#box {
    position: absolute;
    left: 200px;
    top: 300px;
    width: 200px;
    height: 100px;
    background: pink;
}
```

## 方法

### 鼠标相对于可视窗口的位置

MouseEvent.clientX 和 MouseEvent.clientY

```js
const box = document.getElementById("box");
box.addEventListener("mousedown", (e) => {
    console.log(e.clientX);
    console.log(e.clientY)
});
```

注意这两个值是相对于当前**可视窗口**，如果窗口发生滚动，可视窗口的左上角这两个值仍为(0, 0)

### 元素相对于可视窗口的位置

`Element.getBoundingClientRect()` 方法返回元素的大小及其相对于**视口**的位置。

```js
const rect = box.getBoundingClientRect();
console.log(rect.left);
console.log(rect.top)
```

### 鼠标相对于元素的位置

```js
const x = e.clientX - rect.left;
const y = e.clientY - rect.top;
```


## 代码

[codesandbox](https://codesandbox.io/s/calculate-the-mouse-position-relative-to-an-element-ocvcs?file=/index.html)

[github](https://github.com/Melonvin/HTML-DOM-PRACTICE)

