# Check if the native date input is supported

检查当前运行环境是否支持输入日期的input控件

## 判断方法

MDN 中对于不支持日期类型 input 的浏览器如此描述：

> In unsupported browsers, the control degrades gracefully to `<input type="text">`. 

在不支持日期类型input控件的浏览器中，input 会被优雅降级为 text 类型

我们可以主动设置 input 的 value 属性为一个非日期字符串，支持日期控件的浏览器经过格式化其 value 值会变为 ""，而不支持的浏览器则会按照 text 类型输出

```js
const ele = document.createElement("input");
ele.setAttribute("type", "date");
const invalidValue = "abcd"; // 非法日期
ele.setAttribute("value", invalidValue);
console.log(ele.value); // 支持：此值为"" 不支持：'abcd'
```



## 代码

[codesandbox](https://codesandbox.io/s/check-if-the-native-date-input-is-supported-mkn0j?file=/index.html)

[github](https://github.com/Melonvin/HTML-DOM-PRACTICE)

