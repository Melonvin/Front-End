# Count the number of characters of a textarea

计算 textarea 中的字符数

## 准备

页面元素

```html
<textarea id="text" rows="5" cols="33" maxlength="200"></textarea>
<div id="info"></div>
```

## 获取字符数

textarea.value.length

```js
const textarea = document.getElementById("text");
const info = document.getElementById("info");
textarea.addEventListener("input", () => {
  const maxlength = textarea.getAttribute("maxlength");
  const currentLength = textarea.value.length;
  info.innerHTML = `${currentLength}/${maxlength}`;
});
```

## 代码

[codesandbox](https://codesandbox.io/s/count-the-number-of-characters-of-a-textarea-98r88?file=/index.html:413-734)

[github](https://github.com/Melonvin/HTML-DOM-PRACTICE)

