# 《JavaScript权威指南》勘误表中文版

官方英文原版勘误表：[Errata for JavaScript: The Definitive Guide](http://www.oreilly.com/catalog/errata.csp?isbn=9780596805531)

同时还参考了：[JavaScript权威指南勘误记录](https://blog.xinshangshangxin.com/2015/04/05/JavaScript%E6%9D%83%E5%A8%81%E6%8C%87%E5%8D%97%E5%8B%98%E8%AF%AF%E8%AE%B0%E5%BD%95/)。

---

**注意**：

1. 本勘误表，以《JavaScript权威指南》中文第六版实体书的章节及页数为准。
1. 本勘误表中顺序，并未与官方原版勘误表对应，而是以实体书的页码顺序进行排序。

勘误表格式说明：

```text
1.2.3 标题 // 错误所在的章、节、小节的编号，以及该节/小节的名称
位置：第Z页中间。 // 错误所在的位置
错误内容：本小节的第一个网址 http:/oreilly.com/catalog/9780596805531。 // 出现错误的内容
错误原因：XXXX。 // 出错的原因
应更正为：http://oreilly.com/catalog/errata.csp?isbn=9780596805531。 // 错误所应更正为的内容
```

---

## 前言-勘误表以及如何联系我们

- 位置：第3页。
- 错误内容：本小节的第一个网址 http:/oreilly.com/catalog/9780596805531。
- 错误原因：网址给错了。
- 应更正为：[http://oreilly.com/catalog/errata.csp?isbn=9780596805531](http://oreilly.com/catalog/errata.csp?isbn=9780596805531)。

## 1.2 客户端JavaScript

- 位置：第15页上方的一大段代码。
- 错误内容：倒数第二行的函数`function hide(event) { event.target.style.visibility = "hidden"; }`。
- 错误原因：该函数未考虑IE8浏览器。
- 应更正为：

```js
function hide(event) {
    // srcElement用于IE8，target属性则用于Chrome及Firefox
    var target = event.target ? event.target : event.srcElement;
    target.style.visibility = "hidden";
}
```

## 1.2 客户端JavaScript后面的示例

- 位置：第17页中下部的一大段代码，第四、第五个`tr`标签对的开始标签及之后一行。
- 错误内容：

```html
<tr><td>Repayment Period (years):</td>
    <td><input id="years" onchange=calculate();"></td>
<tr><td>Zipcode (to find lenders):</td>
    <td><input id="zipcode" onchange=calculate();"></td>
```

- 错误原因：开始标签`<tr>`缺少对应的关闭标签`</tr>`。
- 应更正为：

```html
<tr><td>Repayment Period (years):</td>
    <td><input id="years" onchange=calculate();"></td></tr>
<tr><td>Zipcode (to find lenders):</td>
    <td><input id="zipcode" onchange=calculate();"></td></tr>
```

## 3.1.3 JavaScript中的算术运算

- 位置：第37页最上方的一大段代码。
- 错误内容：`Number.MAX_VALUE + 1`及`-Number.MIN_VALUE - 1`。
- 错误原因：上面两段代码计算得到的值并不是`Infinity`及`-Infinity`。
- 应更正为：`Number.MAX_VALUE + 1`及`1 / Number.MIN_VALUE`，这样两段代码的结果才能分别为`Infinity`及`-Infinity`。

## 3.2.1 字符串直接量

- 位置：第39页最下方，倒数第二行的代码。
- 错误内容：`"one\ // 用三行代码……`。
- 错误原因：拆分成多行的字符串直接量，字符串后面的注释内容也会被当成字符串的一部分。
- 应更正为：

```js
// 用三行代码……
one\
```

## 3.6 包装对象

- 位置：第46页中上部，第一块示例代码之后的第一段文字。
- 错误内容：`字符串既然不是对象……`。
- 错误原因：这句话不严谨，`var myString = new String("this is a string");`，v这个语句中的`myString`就是对象。
- 应更正为：`字符串原始值既然不是对象……`。

## 3.10 变量作用域

- 位置：第57页，小节标题`3.10.1`之上的一块代码，其中最后一行的注释。
- 错误内容：`// => "嵌套作用域"`。
- 错误原因：这个注释的内容是代码段的输出结果，代码中最内部的函数中的变量定义语句为：`var scope = "nested scope";`，代码段输出的是这个变量的值，不应该是中文。
- 应更正为：`// => "nested scope"`。