# Attach or detach an event handler

注册或删除事件处理函数

## 准备

页面元素

```html
<button id="btn1">onclick</button>
<button id="btn2">addEventListener</button>
```

处理函数

```js
const fn1 = () => {
  alert(1);
};
const fn2 = () => {
  alert(2);
};
```

## 方法一：使用on[事件名]（不推荐）

```js
const btn1 = document.getElementById("btn1");
btn1.onclick = fn1;
```

不能给同个事件添加多个处理函数，后添加的会覆盖先添加的

## 方法二：addEventListener

```js
const btn2 = document.getElementById("btn2");
btn2.addEventListener("click", fn1);
btn2.addEventListener("click", fn2);
```

可以给同个事件添加多个回调函数，多个回调函数可以同时触发

可以用`removeEventListener`移除事件处理函数

```js
btn2.removeEventListener();
```

## 代码

[codesandbox](https://codesandbox.io/s/attach-or-detach-an-event-handler-bq2bh)

[github](https://github.com/Melonvin/HTML-DOM-PRACTICE)

