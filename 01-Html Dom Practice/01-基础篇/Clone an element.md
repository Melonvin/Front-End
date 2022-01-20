# Clone an element

拷贝一个元素

## 准备

页面元素

```html
<div id="app">
    <div class="box"></div>
</div>
```

## 方法

Node.cloneNode() 方法返回调用该方法的节点的一个副本.

> var dupNode = node.cloneNode(deep);

- node
将要被克隆的节点
- dupNode
克隆生成的副本节点
- deep 可选
是否采用深度克隆,如果为true,则该节点的所有后代节点也都会被克隆,如果为false,则只克隆该节点本身.


```js
// 获取元素
const el = document.getElementById("app");
// 浅拷贝
const clonedEl = el.cloneNode(false);
// 深拷贝
const deepClonedEl = el.cloneNode(true);
```



## 代码

[codesandbox](https://codesandbox.io/s/clone-an-element-g98di?file=/index.html)

[github](https://github.com/Melonvin/HTML-DOM-PRACTICE)

