# 《JavaScript 权威指南》勘误表中文版

官方英文原版勘误表：[Errata for JavaScript: The Definitive Guide](http://www.oreilly.com/catalog/errata.csp?isbn=9780596805531)

同时还汇集整理了以下几篇文章中的勘误，一并感谢。

[JavaScript 权威指南勘误记录](https://blog.xinshangshangxin.com/2015/04/05/JavaScript%E6%9D%83%E5%A8%81%E6%8C%87%E5%8D%97%E5%8B%98%E8%AF%AF%E8%AE%B0%E5%BD%95/)。

---

**注意**：

1. 本勘误表，以《JavaScript 权威指南》中文第六版实体书的章节及页数为准。
1. 本勘误表中顺序，以实体书的页码顺序进行排序，并未完全与官方原版勘误表一一对应。

勘误表格式说明：

```text
1.2.3 标题 // 错误所在的章、节、小节的编号，以及该节/小节的名称
位置：第 Z 页中间。 // 错误所在的位置
错误内容：本小节的第一个网址 http:/oreilly.com/catalog/9780596805531。 // 出现错误的内容
错误原因：XXXX。 // 出错的原因
应更正为：http://oreilly.com/catalog/errata.csp?isbn=9780596805531。 // 错误所应更正为的内容
```

---

## 前言-勘误表以及如何联系我们

- 位置：第 3 页。
- 错误内容：本小节的第一个网址 http:/oreilly.com/catalog/9780596805531。
- 错误原因：网址给错了。
- 应更正为：[http://oreilly.com/catalog/errata.csp?isbn=9780596805531](http://oreilly.com/catalog/errata.csp?isbn=9780596805531)。

## 1.1 JavaScript语言核心

- 位置：第 11 页上部一大段代码的倒数第三行。
- 错误内容：`我们称为 b * b);`。
- 错误原因：将注释内容放到了代码中。
- 应更正为：`b * b);`。

## 1.2 客户端JavaScript

- 位置：第 15 页上方的一大段代码，倒数第二行的函数。
- 错误内容：`function hide(event) { event.target.style.visibility = "hidden"; }`。
- 错误原因：该函数未考虑 IE8 浏览器。
- 应更正为：

```js
function hide(event) {
    // srcElement 用于 IE8，target 属性则用于 Chrome 及 Firefox
    var target = event.target ? event.target : event.srcElement;
    target.style.visibility = "hidden";
}
```

- 位置：第 15 页第一行文字。
- 错误内容：`涵盖基于 HTML 的 <vanvas> 标签……`。
- 错误原因：将`canvas`误写为`vanvas`。
- 应更正为：`涵盖基于 HTML 的 <canvas> 标签……`。

- 位置：第 17 页中下部的一大段代码，第四、第五个 `tr` 标签对的开始标签及之后一行。
- 错误内容：

```html
<tr><td>Repayment Period (years):</td>
    <td><input id="years" onchange=calculate();"></td>
<tr><td>Zipcode (to find lenders):</td>
    <td><input id="zipcode" onchange=calculate();"></td>
```

- 错误原因：开始标签 `<tr>` 缺少对应的关闭标签 `</tr>`。
- 应更正为：

```html
<tr><td>Repayment Period (years):</td>
    <td><input id="years" onchange=calculate();"></td></tr>
<tr><td>Zipcode (to find lenders):</td>
    <td><input id="zipcode" onchange=calculate();"></td></tr>
```

## 3.1.3 JavaScript中的算术运算

- 位置：第 37 页最上方的一大段代码。
- 错误内容：`Number.MAX_VALUE + 1` 及 `-Number.MIN_VALUE - 1`。
- 错误原因：上面两段代码计算得到的值并不是 `Infinity` 及 `-Infinity`。
- 应更正为：`Number.MAX_VALUE + 1` 及 `1 / Number.MIN_VALUE`，这样两段代码的结果才能分别为 `Infinity` 及 `-Infinity`。
- 延伸阅读：知乎上的一个回答，分析得很到位：[为什么在 js 中 Number.MAX_VALUE + 1 不是 Infinity？](https://www.zhihu.com/question/24423421/answer/140269663)。

## 3.1.5 日期和时间

- 位置：第 38 页中部的一大段代码，其中的倒数第三行。
- 错误内容：注释 `0 代表星期日，5 代表星期一`。
- 错误原因：5 代表的是星期五，不是星期一。
- 应更正为：`0 代表星期日，5 代表星期五`。

## 3.2 文本

- 位置：第 39 页上部黑框内，四行代码中的第二行。
- 错误内容：`var e = "e";`。
- 错误原因：后面的值 `e` 只是普通的英文字母，不是原文中所说的17位内码 `0x1d452` 所表示的自然对数 `𝑒`。
- 应更正为：`var e = "𝑒";`。
- 延伸阅读：阮一峰老师写的 [Unicode 与 JavaScript 详解](http://www.ruanyifeng.com/blog/2014/12/unicode.html)。

## 3.2.1 字符串直接量

- 位置：第 39 页最下方，三行代码中的倒数第二行。
- 错误内容：`"one\ // 用三行代码……`。
- 错误原因：拆分成多行的字符串直接量，字符串后面的注释内容也会被当成字符串的一部分。
- 应更正为：

```js
// 用三行代码……
one\
```

## 3.3 布尔值

- 位置：第 44 页上方第二段正文。
- 错误内容：`布尔值包含 toString() 方法，因此可以使用这个方法将字符串转换为……`。
- 错误原因：这一节讲的是布尔值，这里说的应该是将布尔值进行转换。
- 应更正为：`布尔值包含 toString() 方法，因此可以使用这个方法将布尔值转换为……`。

## 3.6 包装对象

- 位置：第 46 页中上部，第一段示例代码之后的第一段正文。
- 错误内容：`字符串既然不是对象……`。
- 错误原因：这句话不严谨，`var myString = new String("this is a string");`，这个语句中的 `myString` 就是对象。
- 应更正为：`字符串原始值既然不是对象……`。

## 3.8.3 对象转换为原始值

- 位置：第 54 页，最后一段正文。
- 错误内容：`……是唯一的执行这种特殊的字符串到原始值的转换方式……`。
- 错误原因：这里要说的并不是将字符串转换为原始值，而是将对象转换为原始值。
- 应更正为：`……是唯一的执行这种特殊的对象到原始值的转换方式……`。

## 3.10 变量作用域

- 位置：第 57 页，小节标题 `3.10.1` 之上的那段代码，其中最后一行的注释。
- 错误内容：`// => "嵌套作用域"`。
- 错误原因：这个注释的内容是代码段的输出结果，代码中最内部的函数中的变量定义语句为：`var scope = "nested scope";`，代码段输出的是这个变量的值，不应该是中文。
- 应更正为：`// => "nested scope"`。

## 4.1 原始表达式

- 位置：第 61 页，4.2 小节标题上方的那段正文。
- 错误内容：`然而，在 ECMAScript 5 的严格模式中，对不存在的变量进行求值会抛出一个引用错误异常`。
- 错误原因：不只是在 ECMAScript 5 中会抛出这种异常，在 ECMAScript 3 中也是会抛出这种异常的。
- 应更正为：`对不存在的变量进行求值会抛出一个引用错误异常`。

## 4.2 对象和数组的初始化表达式

- 位置：第 62 页上方，第二段示例代码下面的那段正文。
- 错误内容：`数组直接量的元素列表……值为 undefined 的元素`。
- 错误原因：虽然在数组直接量的元素列表结尾处留下单个逗号，不会创建一个新的值为 `undefined` 的元素。但是如果用属性访问表达式访问超出数组实际元素个数的索引的话，返回值是 `undefined`。即对于定义语句 `var a = [1,,3,];`，`a[3]` 的返回值是 `undefined`。
- 应更正为：在这段话的后面加上：`数组直接量的元素列表结尾处可以留下单个逗号，这时并不会创建一个新的值为 undefined 的元素。但是如果用属性访问表达式访问超出数组实际元素个数的索引的话，返回值是 undefined。`。

## 4.3 函数定义表达式

- 位置：第 63 页上方的示例代码。
- 错误内容：`var square = function(x) { return x * x; }`。
- 错误原因：规范的代码书写方式，应当在行末加上分号。
- 应更正为：`var square = function(x) { return x * x; };`。

## 4.4 属性访问表达式

- 位置：第63 页最下方的一行文字。
- 错误内容：`如果属性名称是一个保留字或者包含空格和标点符号……，则必须使用方括号的写法`。
- 错误原因：如果属性名称是一个保留字，那么句点的写法也是可以用的。

```js
var p = {
    'goto': 1,
    'void': 2
};
p.goto + p.void // 输出 3
```

- 应更正为：`如果属性名称包含空格和标点符号……则必须使用方括号的写法`。

## 4.5 调用表达式

- 位置：第 64 页，上面三行代码之后的第二段正文的第三行。
- 错误内容：`作为属性访问主题的对象和数组……`。
- 错误原因：`主体` 写成了 `主题`。
- 应更正为：`作为属性访问主体的对象和数组……`。