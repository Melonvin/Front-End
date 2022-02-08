# Append to an element

给父元素追加一个子元素

## 准备

页面元素

```html
<ul id="father">
  <li class="son">1</li>
</ul>
```

## 追加元素

```js
const li = document.createElement("li");
li.innerHTML = index++;
ul.appendChild(li);
```

## 代码

[codesandbox](https://codesandbox.io/s/append-to-an-element-z1zq3?file=/index.html:552-648)

[github](https://github.com/Melonvin/HTML-DOM-PRACTICE)
