# Check if an element has given class

检查元素是否具有给定类

## 准备

页面元素

```html
<div id="app" class="bg-pink"></div>
```

## 方法

Element.classList.contains()

```js
const el = document.getElementById("app");
console.log(el.classList.contains("bg-pink"));
console.log(el.classList.contains("bg-red"));
```

## 代码

[codesandbox](https://codesandbox.io/s/check-if-an-element-has-given-class-m7uy0?file=/index.html:465-608)

[github](https://github.com/Melonvin/HTML-DOM-PRACTICE)

