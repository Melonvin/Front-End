# Create an element

创建一个元素

## 准备

样式

```css
div {
  width: 100px;
  height: 100px;
  background: pink;
}
```

## 方法

`Document.createElement()` 方法用于创建一个由标签名称 tagName 指定的 HTML 元素。

`querySelector()`方法返回文档中与指定选择器或选择器组匹配的第一个 Element对象。

`appendChild()` 方法将一个节点附加到指定父节点的子节点列表的末尾处

```js
const el = document.createElement("div");
const body = document.querySelector("body");
body.appendChild(el);
```

## 代码

[codesandbox](https://codesandbox.io/s/create-an-element-irg0h?file=/index.html:402-518)

[github](https://github.com/Melonvin/HTML-DOM-PRACTICE)

