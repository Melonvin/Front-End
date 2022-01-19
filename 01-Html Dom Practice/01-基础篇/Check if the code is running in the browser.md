# Check if the code is running in the browser

检查当前运行环境是否为浏览器

## 判断方法

如果是浏览器，`typeof window` 和 `typeof document` 均为`object`，于是可以按如下方法判断：

```js
const isBrowser =
  typeof window === "object" && typeof document === "object";
console.log(isBrowser);
```



## 代码

[codesandbox](https://codesandbox.io/s/check-if-the-code-is-running-in-the-browser-g2v4q?file=/index.html:378-489)

[github](https://github.com/Melonvin/HTML-DOM-PRACTICE)

