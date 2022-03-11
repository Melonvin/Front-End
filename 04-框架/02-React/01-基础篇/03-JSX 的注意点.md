# JSX 的注意点

## 1 JSX 是一个表达式

JSX 是 JavaScript 的语法扩展，本质上是 `React.createElement()`方法的语法糖。

Babel 会把 JSX 转译成一个名为 `React.createElement()` 函数调用，所以它被看作一个表达式。

这意味着你可以在 `if` 语句和 `for` 循环的代码块中使用 JSX，将 JSX 赋值给变量，把 JSX 当作参数传入，以及从函数中返回 JSX：

```js
function getGreeting(user) {
  if (user) {
    return <h1>Hello, {formatName(user)}!</h1>;
  }
  return <h1>Hello, Stranger.</h1>;
}
```

## 2 JSX 的属性

### 2.1 驼峰命名

JSX 是 JS 的扩展，所以使用**驼峰命名**来定义属性的名称，而不使用HTML 属性名称的命名约定

比如：

```jsx
<div className="container"></div>
```

上述 JSX 表达式中 class 写作 className

### 2.2 style 接收一个对象

style 接收一个对象，而不是字符串

比如：

```jsx
let style = {
    width: "100px",
    height: "100px",
    background: "red"
};
ReactDOM.render(
    <div className="box" style={style}></div>,
    document.querySelector("#root")
); 
```

## 3 JSX 标签没有子元素

如果一个标签中没有内容，可以使用`/>`来闭合标签

比如：

```jsx
const element = <img src={user.avatarUrl} />;
```

## 4 JSX 防止注入攻击

可以安全地在 JSX 中插入用户输入内容

React DOM 在渲染所有输入内容之前，默认会进行[转义](https://stackoverflow.com/questions/7381974/which-characters-need-to-be-escaped-on-html)。它可以确保在你的应用中，永远不会注入那些并非自己明确编写的内容。所有的内容在渲染之前都被转换成了字符串。这样可以有效地防止 [XSS（cross-site-scripting, 跨站脚本）](https://en.wikipedia.org/wiki/Cross-site_scripting)攻击。

### 5 唯一父元素

**JSX 表达式必须有一个父元素**

换句话说，下面的写法会报错

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

如果我们不想让父元素被渲染在页面上，可以使用`React.Fragment`

`React.Fragment` 组件能够在不额外创建 DOM 元素的情况下，让 `render()` 方法中返回多个元素。

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

