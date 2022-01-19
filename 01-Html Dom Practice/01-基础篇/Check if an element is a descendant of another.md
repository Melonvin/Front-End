# Check if an element is a descendant of another

检查一个元素是否为另一个元素的后代

## 准备

页面元素

```html
<div id="grandfather">
  <div id="father">
    <div id="son"></div>
  </div>
  <div id="uncle"></div>
</div>
```

## 方法

Node.contains()返回的是一个布尔值，来表示传入的节点是否为该节点的后代节点。

```js
const grandfather = document.getElementById("grandfather");
const father = document.getElementById("father");
const son = document.getElementById("son");
const uncle = document.getElementById("uncle");
console.log(grandfather.contains(son)); // true
console.log(uncle.contains(son)); // false
```

因为一个元素只有一个父元素，所以我们可以利用这点自定义一个判断方法

```js
function isDescendant(parent, child) {
  let node = child.parentNode;
  while (node) {
    if (node === parent) {
      return true;
    }
    node = node.parentNode;
  }
  return false;
}

console.log(isDescendant(grandfather, son));
console.log(isDescendant(uncle, son));
```

## 代码

[codesandbox](https://codesandbox.io/s/check-if-an-element-is-a-descendant-of-another-wp8i3?file=/index.html:981-1020)

[github](https://github.com/Melonvin/HTML-DOM-PRACTICE)

