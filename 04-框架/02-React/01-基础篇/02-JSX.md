## 1 JavaScript 表达式

> An expression is any valid unit of code that resolves to a value.

这是 JS 表达式的定义，意为：表达式是解析为值的任何有效代码单元。

换言之，每个合法的表达式都能计算成某个值

JS 表达式有两种类型：基本表达式和左值表达式

### 1.1 基本表达式

基本表达式由 JS 中的基本关键字和通用表达式构成

比如：

1. `1` —— 数值直接量，计算后返回数值 1
2. `"string"` —— 字符串直接量，计算后返回字符串“string”
3. `false` —— 布尔直接量，计算后返回布尔值 false
4. `null` —— 特殊值直接量，计算后返回直接量 null
5. `/regexp/` —— 正则直接量，计算后返回正则表达式对象
6. `{ a: 1, b: "1" }` —— 对象直接量，计算后返回对象
7. `[1, 2]` —— 数组直接量，计算后返回数组
8. `function(a, b) { return a + b }` —— 函数，计算后返回函数
9. `a` —— 变量，计算后返回变量的值
10. `1 + 1` —— 运算表达式，计算后返回 2

### 1.2 左值表达式

左值表达式即赋值，比如 `x = 7`

该表达式使用`=`运算符将值 7 赋予变量 x，同时这个表达式自己的值等于 7

```js
console.log((x = 7)); // 输出 7
```

## 2 JSX 也是表达式

JSX 是 JavaScript 的语法扩展，本质上是 `React.createElement()`方法的语法糖。

Babel 会把 JSX 转译成一个名为 `React.createElement()` 函数调用，所以它被看作一个表达式。

这意味着可以将 JSX 当作普通表达式使用，比如从函数中返回 JSX：

```js
function getGreeting(user) {
  if (user) {
    return <h1>Hello, {formatName(user)}!</h1>;
  }
  return <h1>Hello, Stranger.</h1>;
}
```

## 3 插值表达式

React 提供了在 JSX 中嵌入 JS 表达式的方式：将表达式包裹在大括号中，并将它嵌入 JSX 中

在下面的例子中，我们声明了一个名为 name 的变量，然后在 JSX 中使用它

```jsx
const name = "Josh Perez";
const element = <h1>Hello, {name}</h1>;
```

`{name}`这种用大括号包裹一个表达式的写法被称为“插值表达式”

在 JSX 语法中，可以在大括号内放置任何有效的 JavaScript 表达式。

例如，`2 + 2`，`user.firstName` 或 `formatName(user)` 都是有效的 JavaScript 表达式。

**当然也可以在大括号中放置 JSX，因为 JSX 也是表达式**

[在线代码](https://codesandbox.io/s/react-04-rl3pf?file=/index.html)

## 4 不同数据类型在插值表达式中的表现

虽然可以在大括号中放置任何有效的 JavaScript 表达式，但是并不是所有数据类型都能显示在页面上

```html
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <meta http-equiv="X-UA-Compatible" content="ie=edge" />
    <title>Static Template</title>
    <script
      crossorigin
      src="https://unpkg.com/react@17/umd/react.development.js"
    ></script>
    <script
      crossorigin
      src="https://unpkg.com/react-dom@17/umd/react-dom.development.js"
    ></script>
    <script src="https://unpkg.com/babel-standalone@6/babel.min.js"></script>
  </head>

  <body>
    <div id="root"></div>
  </body>
  <script type="text/babel">
    let data1 = "Hello React!";
    let data2 = 1;
    let data3 = true;
    let data4 = undefined;
    let data5 = null;
    let data6 = [1, 2, 3];
    // let data7 = { name: "react" };
    let data7 = "object";
    let el = (
      <div>
        <div>{data1}</div>
        <div>{data2}</div>
        <div>{data3}</div>
        <div>{data4}</div>
        <div>{data5}</div>
        <div>{data6}</div>
        <div>{data7}</div>
      </div>
    );
    ReactDOM.render(el, document.getElementById("root"));
  </script>
</html>
```

将不同数据类型的数据用大括号包裹，尝试将它们显示在页面上

经过观察：

1. `undefined`、`null` 不会在页面上显示
2. 数组`[1, 2, 3]`显示在页面上会变成：`123`
3. 对象则会报错

## 5 JSX 的属性

### 5.1 驼峰命名

JSX 是 JS 的扩展，所以使用**驼峰命名**来定义属性的名称，而不使用 HTML 属性名称的命名约定

比如：

```jsx
<div className="container"></div>
```

上述 JSX 表达式中 class 写作 className

### 5.2 style 接收一个对象

style 接收一个对象，而不是字符串

比如：

```jsx
let style = {
  width: "100px",
  height: "100px",
  background: "red",
};
ReactDOM.render(
  <div className="box" style={style}></div>,
  document.querySelector("#root")
);
```

## 6 JSX 的单标签闭合

如果一个标签中没有内容，可以使用`/>`来闭合标签

比如：

```jsx
const element = <img src={user.avatarUrl} />;
```

## 7 JSX 防止注入攻击

可以安全地在 JSX 中插入用户输入内容

React DOM 在渲染所有输入内容之前，默认会进行[转义](https://stackoverflow.com/questions/7381974/which-characters-need-to-be-escaped-on-html)。它可以确保在你的应用中，永远不会注入那些并非自己明确编写的内容。所有的内容在渲染之前都被转换成了字符串。这样可以有效地防止 [XSS（cross-site-scripting, 跨站脚本）](https://en.wikipedia.org/wiki/Cross-site_scripting)攻击。

### 5 唯一父元素

**JSX 表达式必须有一个父元素**

换言之，如下写法会报错

```jsx
ReactDOM.render(
  <div className="box" style={style} />
  <input type="text" />,
  document.querySelector("#root")
);
```

正确的写法：

```jsx
ReactDOM.render(
  <div>
    <div className="box" style={style} />
    <input type="text" />
  </div>,
  document.querySelector("#root")
);
```

若不希望父元素被渲染在页面上，可以使用`React.Fragment`

```jsx
render() {
  return (
    <React.Fragment>
      Some text.
      <h2>A heading</h2>
    </React.Fragment>
  );
}
```

也可以使用其简写语法 `<></>`，请参阅 [React v16.2.0: Fragments 支持改进](https://react.docschina.org/blog/2017/11/28/react-v16.2.0-fragment-support.html)。

```jsx
render() {
  return (
    <>
      Some text.
      <h2>A heading</h2>
    </>
  );
}
```
