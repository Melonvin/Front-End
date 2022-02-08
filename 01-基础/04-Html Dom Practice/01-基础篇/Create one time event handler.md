# Create one time event handler

创建一次性事件监听器

## 准备

页面元素

```html
<button id="btn">click</button>
```

## 方法

**创建事件监听器时传入参数**

once:  Boolean，表示 listener 在添加之后最多只调用一次。如果是 true， listener 会在其被调用之后自动移除。

```js
const btn = document.getElementById("btn");
btn.addEventListener(
  "click",
  () => {
    console.log("hello");
  },
  { once: true }
);
```

**回调函数自移除**

EventTarget.removeEventListener:删除使用 EventTarget.addEventListener() 方法添加的事件。

```js
const btn = document.getElementById("btn");
const handler = (e) => {
  console.log("hello");
  e.target.removeEventListener("click", handler);
};
btn.addEventListener("click", handler);
```

## 代码

[codesandbox](https://codesandbox.io/s/create-one-time-event-handler-s8rpv?file=/index.html)

[github](https://github.com/Melonvin/HTML-DOM-PRACTICE)

