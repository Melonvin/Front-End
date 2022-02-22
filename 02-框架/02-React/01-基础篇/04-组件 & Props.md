# 组件 & Props

什么是组件：用来实现局部功能的可复用代码片段

比如很多界面会用到“分页”功能，因此可以将它封装成独立的**组件**

![](https://melonvin-1302080640.cos.ap-shanghai.myqcloud.com/Snipaste_2022-02-22_15-29-30.png)

这样用到分页的界面只需引入该组件而不必重新写代码

## 1 定义组件

### 1.1 函数组件

定义组件最简单的方式就是编写 JavaScript 函数

```jsx
function MyComponent() {
    return <h2>我是一个函数组件</h2>;
}
```

[在线代码](https://codesandbox.io/s/react-08-bt4rbw?file=/index.html:636-698)

### 1.2 class 组件

定义 class 组件，需要继承 `React.Component`

```jsx
class MyComponent extends React.Component {
    render() {
        return <h2>我是一个class组件</h2>;
    }
}
```

在 `React.Component` 的子类中有个必须定义的 [`render()`](https://react.docschina.org/docs/react-component.html#render) 函数，我们需要在该方法中返回构成组件的 JSX 表达式

[在线代码](https://codesandbox.io/s/react-09-72egbz?file=/index.html:636-749)

无论是函数组件还是class组件，在 React 中是等效的，不过 class 组件有更多的特性

## 2 渲染组件

同一个组件在不同界面使用，可能会想要展示不同的内容

比如我们自定义的组件包含了一个`h2`标签，如果我们想要在两个不同的界面分别展示`函数`和`class`怎么办？

可以在使用组件时添加属性，react 会将添加的属性转换为一个对象传递给组件，这个对象称为"props"

函数组件和class组件可以分别通过“形参”和实例属性来使用这个对象

比如:

```jsx
function MyComponent(props) {
    console.log(props)
    return <h2>我是一个函数组件</h2>;
}
ReactDOM.render(
    <MyComponent a="1" b="2" />,
    document.getElementById("root")
);
```

```jsx
class MyComponent extends React.Component {
    render() {
        console.log(this.props);
        return <h2>我是一个class组件</h2>;
    }
}
ReactDOM.render(
    <MyComponent a="1" b="2" />,
    document.getElementById("root")
);
```

两者输出同样的对象：

![](https://melonvin-1302080640.cos.ap-shanghai.myqcloud.com/Snipaste_2022-02-22_16-09-07.png)

[在线代码](https://codesandbox.io/s/reverent-ritchie-mrni6q?file=/index.html:0-1012)

于是我们可以传入不同的属性，来让组件呈现不同的内容：

```jsx
function MyComponent(props) {
    return <h2>我是一个{props.name}组件</h2>;
}

ReactDOM.render(
    <MyComponent name="自定义函数" />,
    document.getElementById("root")
);
```

[在线代码](https://codesandbox.io/s/romantic-montalcini-bw7xyt?file=/index.html)

这个例子中发生了这些事：

1. 我们调用 `ReactDOM.render()` 函数，并传入 `<MyComponent name="自定义函数" />` 作为参数。
2. React 调用 `MyComponent` 组件，并将 `{name: '自定义函数'}` 作为 props 传入。
3. `MyComponent` 组件将 `<h2>我是一个自定义函数组件</h2>` 元素作为返回值。
4. React DOM 将 DOM 高效地更新为 `<h2>我是一个自定义函数组件</h2>`。

## 3 注意点

- **组件名称必须以大写字母开头。**

- 传入属性值为字符串和数字的区别：

  数字：`<MyComponent a={1} />`

  字符串：`<MyComponent a="1" />`

- 多个属性可以使用扩展运算符

  ```jsx
  const obj = { name: 'React', age: 18 }
  <MyComponent {...obj} /> 
  ```

  注意`{}`不能省略

## 3 组合组件