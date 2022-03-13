# 为什么需要 Webpack？

![](https://webpack.docschina.org/site-logo.1fcab817090e78435061.svg)

如果在一个 HTML 页面中需要引入 3 个 JavaScript 文件，并且它们之间存在一定的依赖关系：比如`c`依赖于`b`，`b`依赖于`a`

于是我们需要通过 script 标签依次引入

```html
<html>
  <body>
    <script type="text/javascript" src="a.js"></script>
    <script type="text/javascript" src="b.js"></script>
    <script type="text/javascript" src="c.js"></script>
  </body>
</html>
```

浏览器需要发送3次 http 请求来获取这个3个文件，每个文件的加载都会影响整个页面的显示时间。

这还只是3个 js 文件，如果 js 的数量增加到几十个甚至上百个，我们仍旧采用这种引入方式，那么页面的加载延迟会变得相当严重

如果我们把所有相互依赖的 js 文件合并成一个 js 文件呢？

这样只需要发送1次请求就能加载这个 js 文件，大大加快了页面的加载速度。

然而，对于一个由几十个甚至上百个 js 文件合并而成的 js 文件，其代码量及代码复杂程度是难以想象的，这样的代码是无法维护的。

所以在开发阶段，我们采用模块化开发，将项目分解成成一个个小的 js 文件，有助于开发和维护。

在开发完成以后，再想办法将这些模块合并成一个文件，这个合并的过程称为**打包**，由 `webpack` 来完成

当然 `webpack` 的作用可不止这个，它能处理的文件类型也不止 js，`webpack`支持多种类型的文件的打包，包括`js`、`css`、`jpg`等


