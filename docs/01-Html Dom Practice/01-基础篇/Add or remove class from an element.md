# Add or remove class from an element

给一个元素添加或删除类

## 准备

页面元素

```html
<div
  id="box"
  style="height: 100px; width: 100px; border: 1px solid black;"
></div>
```

类

```css
.bg-pink {
  background: pink;
}
```

## 添加类

```js
const element = document.getElementById("box");
element.classList.add("bg-pink");
```

## 删除类

```js
const element = document.getElementById("box");
element.classList.remove("bg-pink");
```

## 代码

[codesandbox](https://codesandbox.io/s/dazzling-frost-9zfjm?file=/index.html)

[github](https://github.com/Melonvin/HTML-DOM-PRACTICE)
