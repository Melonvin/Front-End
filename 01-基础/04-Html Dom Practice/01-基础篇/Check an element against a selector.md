# Check an element against a selector

检查元素是否匹配指定选择器

## 准备

页面元素

```html
<div id="container" class="box"></div>
```

## 方法

Element.matches()

如果元素被指定的选择器字符串选择，`Element.matches()` 方法返回true; 否则返回false。
```js
 const el = document.getElementById("container");
 const res = el.matches("#container");
```

考虑方法兼容性问题：

```js
const res =
	el.matches(".box") ||
    el.matchesSelector(".box") ||
    el.msMatchesSelector(".box") ||
    el.mozMatchesSelector(".box") ||
    el.webkitMatchesSelector(".box") ||
    el.oMatchesSelector(".box");
```

改进写法：

```js
const match = (el, selector) =>
  (
    el.matches ||
    el.matchesSelector ||
    el.msMatchesSelector ||
    el.mozMatchesSelector ||
    el.webkitMatchesSelector ||
    el.oMatchesSelector
  ).call(el, selector);
const res = match(el, ".box");
```

## 代码

[codesandbox](https://codesandbox.io/s/check-an-element-against-a-selector-kdkee)

[github](https://github.com/Melonvin/HTML-DOM-PRACTICE)

