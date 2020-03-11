# 《JavaScript 权威指南》勘误表中文版

官方英文原版勘误表：[Errata for JavaScript: The Definitive Guide](http://www.oreilly.com/catalog/errata.csp?isbn=9780596805531)

> 更新进度：英文勘误最后更新至 Page 144（含）。

同时还汇集整理了以下文章中的勘误，一并感谢。

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
- 错误原因：网址已变更。
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
- 应更正为：`Number.MAX_VALUE + 1E300` 及 `-1 / Number.MIN_VALUE`，这样两段代码的结果才能分别为 `Infinity` 及 `-Infinity`。
- 延伸阅读：知乎上的一个回答，分析得很到位：[为什么在 js 中 Number.MAX_VALUE + 1 不是 Infinity？](https://www.zhihu.com/question/24423421/answer/140269663)

## 3.1.5 日期和时间

- 位置：第 38 页中部的一大段代码，其中的倒数第三行。
- 错误内容：注释 `0 代表星期日，5 代表星期一`。
- 错误原因：5 代表的是星期五，不是星期一。
- 应更正为：`0 代表星期日，5 代表星期五`。

## 3.2 文本

- 位置：第 39 页上部黑框内，四行代码中的第二行。
- 错误内容：`var e = "e";`。
- 错误原因：后面的值 `e` 只是普通的英文字母，不是原文中所说的 17 位内码 `0x1d452` 所表示的自然对数 `𝑒`。
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

- 位置：第 44 页 3.4 节标题下方文字的第二行。
- 错误内容：`对 null 执行 typeof 预算`。
- 错误原因：打错字，不应该是“预算”，而应该是“运算”。
- 应更正为：`对 null 执行 typeof 运算`。

## 3.4 null 和 undefined

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

- 位置：第 63 页最下方的一行文字。
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

## 4.9.1 相等和不等运算符

- 位置：第 75 页上方，严格相等比较过程的第二条。
- 错误内容：`如果两个值都是 null 或者都是 undefined，则它们不相等。`。
- 错误原因：两个 `null` 或者两个 `undefined` 的值是相等的，只有 `NaN` 才和自己不相等。
- 应更正为：`如果两个值都是 null 或者都是 undefined，则它们相等。`。

## 4.9.4 instanceof 运算符

- 位置：第 78 页中部的示例代码。
- 错误内容：

```js
d instanceof Date;
d instanceof Object;
d instanceof Number;

a instanceof Array;
a instanceof Object;
a instanceof RegExp;
```

- 错误原因：书中的语句后面都有分号 `;`，但表达式后面都没有分号 `;`。应去掉这些表达式末尾的分号，以保持格式的统一。
- 应更正为：

```js
d instanceof Date
d instanceof Object
d instanceof Number

a instanceof Array
a instanceof Object
a instanceof RegExp
```

- 位置：该小节的第二段正文 `需要注意的是……` 中的第三行。
- 错误内容：`如果右操作数不是函数，则抛出一个类型错误异常`。
- 错误原因：`instanceof` 运算符判断一个对象是不是一个类的实例，右操作数是类，不是函数。
- 应更正为：`如果右操作数不是类，则抛出一个类型错误异常`。

## 4.10.2 逻辑或（||）

- 位置：第 81 页最上方的示例代码。
- 错误内容：`p = p || {};`。
- 错误原因：因为是要将 o 的成员属性复制到 p 中，所以应该是如果没有传入 o，才使用一个新创建的对象。
- 应更正为：`p = o || {};`。

## 5.3.2 function

- 位置：第 96 页最上方的第一行文字。
- 错误内容：`……函数定义语句中的函数被显示地……`。
- 错误原因：这里讨论的是函数声明语句，不是函数定义语句。
- 应更正为：`……函数声明语句中的函数被显示地……`。

## 5.7 其他语句类型

- 位置：第 113 页，紧挨着 5.7 节标题下面的那段话。
- 错误内容：`……——width……`。
- 错误原因：`with` 写成了 `width`。
- 应更正为：`……——with……`。

## 5.7.2 debugger 语句

- 位置：第 114 页，5.7.2 小节标题下面的第一段正文，其中的第二行。
- 错误内容：`将会（非必需）以调式模式运行`。
- 错误原因：`调试` 写成了 `调式`。
- 应更正为：`将会（非必需）以调试模式运行`。

- 位置：第 114 页，5.7.3 小节标题上方那段正文的倒数第二行。
- 错误内容：`则必须首先为待调试的网页启用 Friebug……`。
- 错误原因：`Firebug` 写成了 `Friebug`，并样式也不对，这里的 `Firebug` 指的是浏览器插件，而不是代码，所以不需要设置成黑体。
- 应更正为：`则必须首先为待调试的网页启用 Firebug……`。

## 5.7.3 "use strict"

- 位置：第 115 页中部，严格模式和非严格模式区别的第三条，其中的第一行。
- 错误内容：`在严格模式中，调用的函数（不是方法）中的一个 this 值是 undefined`。
- 错误原因：严格模式中调用的函数只有一个 `this`，其值是 `undefined`。
- 应更正为：`在严格模式中，调用的函数（不是方法）的 this 值是 undefined`。

## 5.8 JavaScript 语句小结

- 位置：第 117 页倒数第三行代码。
- 错误内容：`var name=[=expr][,...];`。
- 错误原因：多了一个等号。
- 应更正为：`var name[=expr][,...];`。

## 第六章 对象

- 位置：第 118 页，倒数第三段第二行末尾括号中的文字。
- 错误内容：`参照 3.6 节`。
- 错误原因：应当是 `参照 3.7 节`，3.6 节是 `包装对象`，3.7 节是 `不可变对象`。
- 应更正为：`参照 3.7 节`。

## 6.4 检测属性

- 位置：第 128 页，6.4 节标题下方第一段文字的第二行。
- 错误内容：`hasOwnPreperty()`。
- 错误原因：写错了方法名。
- 应更正为：`hasOwnProperty()`。

## 6.5 枚举属性

- 位置：第 131 页上方的第一个函数 `merge()`。
- 错误内容：`if (o.hasOwnProperty[prop])`。
- 错误原因：`hasOwnProperty` 是方法，这里不能用中括号，要用小括号。
- 应更正为：`if (o.hasOwnProperty(prop))`。

## 6.7 属性的特性

- 位置：第 135 页，页面下方整个代码段之上的一段正文。
- 错误内容：`则需要调用 Object.definePeoperty()`。
- 错误原因：写错了方法名。
- 应更正为：`则需要调用 Object.defineProperty()`。

=======

## 第七章 数组

## 7.1 创建数组

- 位置：第 145 页，第三段正文及后续的两行代码。
- 错误内容：`如果省略数组直接量中的某个值，省略的元素将被赋予 undefined 值。`。

```js
var count = [1,,3]; // => [1, undefined, 3]
var undefs = [,,]; // => [undefined x 2]
```

- 错误原因：在数组直接量中省略值时，省略的元素为空，更不会有值。
- 应更正为：`如果省略数组直接量中的某个值，省略的元素在数组中是不存在的。`

```js
var count = [1,,3]; // => [1, empty, 3]
var undefs = [,,]; // => [empty x 2]
```

## 7.2 数组元素的读和写

- 错误内容：数组的特别之处在于，当使用小于 2<sup>32</sup> 的非负整数作为属性名时数组会自动维护其length属性。
- 错误解释：索引的取值范围是小于2<sup>32</sup>-1的非负整数，也就是0~2<sup>32</sup>-2之间的整数
- 应更正为：数组的特别之处在于，当使用小于 2<sup>32</sup> - 1 的非负整数作为属性名时数组会自动维护其length属性。

## 7.3 稀疏数组

- 位置：第 147 页，节标题之下的第四个段落及后续的四行代码。
- 错误内容：`当在数组直接量中省略值时不会创建稀疏数组。省略的元素在数组中是存在的，其值为 undefined。`。

```js
var a1 = [,,,]; // 数组是 [undefined, undefined, undefined]
0 in a1; // => true
```

- 错误原因：在数组直接量中省略值时，是 **会** 创建稀疏数组的。
- 应更正为：`当在数组直接量中省略值时，会创建稀疏数组。省略的元素在数组中是不存在的。`

```js
var a1 = [,,,]; // 数组是 [empty × 3]
0 in a1; // => false
```

## 7.7 多维数组

- 位置：第 151 页多维数组描述第第一行
- 错误内容：`JavaScript不支持真正的多维数组，但可以利用数组的数组来近似`。
- 错误原因：书写错误
- 应更正为：`JavaScript不支持真正的多维数组，但可以利用数组的数组来解释`。

## 7.10 数组类型

- 错误内容：

```javascript
Array.isArray = Function.isArray || function (o) {
    return typeof o === 'object' // 过滤基础类型
    Object.prototype.toString.call(o) === '[object Array]'
}
```

- 错误解释：这里应该书写错误。书中使用了 `Function.isArray` ，上下文的意思是 ES5 才有`Array.isArray` 方法，所以需要判断，如果是 ES5 之前的版本，此处需要手动实现这个方法。
- 应更正为：

```javascript
Array.isArray = Array.isArray || function (o) {
    return typeof o === 'object' // 过滤基础类型
    Object.prototype.toString.call(o) === '[object Array]'
}
```



## 7.12 作为数组的字符串

- 位置：第 163 页底部，三行代码中的第一行。
- 错误内容：`var s = test`。
- 错误原因：这里是为了新建一个字符串，却忘了给字符串加引号。
- 应更正为：`var s = "test"`。

## 7.12 作为数组的字符串

- 位置：第 163 页底部倒数第二行。
- 错误内容：`但是如果给Array.isArray()...`。
- 错误原因：这里是为了强调，虽然前面说“字符串的行为类似于只读数组”，但它终究并不是数组。所以用 `typeof` 判断字符串得到的是 `string`，给 `Array.isArray()` 方法传入字符串的话返回的也是 false。所以不能说是 `但是`，应该是 `而且`。
- 应更正为：`而且给Array.isArray()...`。

## 第八章 函数

## 8.1 函数定义

- 位置：第 168 页中间，8.2 节标题上方的段落。
- 错误内容：`try/cache/finally`。
- 错误原因：打错字。
- 应更正为：`try/catch/finally`。

## 8.1.1 嵌套函数

- 位置：第 168 页上方，第二段正文的第二行。
- 错误内容：`printprops() 函数的不用之处在于`。
- 错误原因：打错字。
- 应更正为：`printprops() 函数的不同之处在于`。

## 8.7.1 length属性

- 位置：第 188 页上方，第二段正文的第二行。
- 错误内容：`函数的length属性是只读属性，它代表函数实参的数量`。
- 错误原因：打错字。
- 应更正为：`函数的length属性是只读属性，它代表函数形参的数量`。

## 8.7.1 length属性

- 位置：第 188 页上方，第二段正文的第三行。
- 错误内容：`也就是在函数定义时给出的实参个数`。
- 错误原因：定义错误。函数定义的是参数应叫形参，调用时实际传入的参数叫实参
- 应更正为：`也就是在函数定义时给出的参数(形参)个数`。

## 8.8.2 高阶函数

- 位置：第 196 页，高阶函数描述的第一行。
- 错误内容：`它接收一个或多个函数作为参数，并返回一个新的函数`。
- 错误原因：定义错误。
- 应更正为：`我们将参数或是返回值为函数的函数称为高阶函数`。高阶函数并不一定会返回一个新函数,比如`map`就返回一个数组

## 10.1.4 选择、分组和引用

- 位置：第 258 页，倒数第二段的倒数第二行，圆括号对和里面的正则表达式。
- 错误内容：`(/[a-z]+(\d+)/)`。
- 错误原因：看文字描述的部分，只是想要抽取所检索到的匹配中的数字部分，那么只对数字部分的正则表达式加括号就行了，没必要给整个正则表达式再加一个括号。
- 应更正为：`/[a-z]+(\d+)/`。



## 第13章 Web浏览器中的JavaScript

### 13.1 客户端JavaScript

- 位置：例13-1
- 错误内容：示例代码可以运行但不合理。
- 错误解释：代码中使用了for遍历elements，而实际html只有一个`<div class="reveal">`
- 应更正为：https://github.com/davidflanagan/javascript6_examples/blob/master/examples/13.01.reveal.html



### 13.2.4 HTML中的事件处理程序

- 位置：p317，10.1.4节最后一段的第一句话。

- 错误内容：HTML中定义的事件处理程序的属性可以包含任意条JavaScript语句，相互之间用**逗号**分隔。

- 错误描述：应该是用**分号**分隔，而不是逗号，JavaScript的语句是使用分号分隔的。

  此处应为翻译错误，犀牛书英文版原文：Event handler attributes defined in HTML may include any number of JavaScript statements, separated from each other by **semicolons**.

- 应更正为：分号。



### 13.3.4 客户端 JavaScript 时间线

- 位置：P325，列表的第三项，最后一句话。

- 错误内容：它们可以看到自己的`<script>`元素和它们之前的所有文档元素，并且可能或**干脆不可能**访问其他的文档内容。

- 错误描述：这里翻译有点奇怪，因为async是异步加载，下载完成之后会尽快执行，不能确定解析器解析到哪一行HTML代码，所以不确定能够访问哪一些HTML代码，**可能也可能不能**访问其他的文档内容。这里翻译加了“干脆”两字有点奇怪。

  犀牛书英文版原文：They can see their own `<script>` element and all document  elements that come before it, and **may or may not** have access to additional document content.

  另外，这里additional翻译成“更多的”比“其他的”要更好一点。

- 应更正为：它们可以看到自己的`<script>`元素和它们之前的所有文档元素，并且可能有也可能没有权限访问更多的文档内容。



### 13.6.2 同源策略

- 位置：P336，子标题“不严格的同源策略”的上面一段，第一句。
- 错误内容：对于防止脚本窃取**似有**的信息来说。
- 错误描述：印刷错误。“似有”应该是“私有”。
- 应更正为：对于防止脚本窃取**私有**的信息来说。





## 第十八章 脚本化 http

### 18.1 使用 XMLHttpRequest

- 位置：P487，页底的方框中的内容。

- 错误内容：IE7之前的版本不支持**非标准**的XMLHttpRequest()构造函数。

- 错误描述：翻译错误。此处应该是“当前标准”（now-standard），而不是“非标准”。结合上下文，这句话的意思是IE7之前的版本支持ActiveX对象，但不支持XMLHttpRequest()构造函数。

  英文版原文：The now-standard XMLHttpRequest() constructor is not supported before IE7.

- 应更正为：IE7之前的版本不支持**当前标准**的XMLHttpRequest()构造函数。



### 18.1.1 指定请求

- 位置：P490，中间方框中“顺序问题”中的内容。
- 错误内容：例如，setRequestHeader()方法的调用必须在调用open()**之前**但在调用send()**之后**，否则它将抛出异常。

- 错误描述：翻译错误。作者的意思应该是：XMLHttpRequest API的设计似乎将每个方法都写入网络流，所以顺序很重要（verb、URL -> header -> body），所以setRequestHeader（header）应该在open（verb、URL）和send（body）的之间。

  英文版原文：for example, must be called after you call open() and before you call send() or it will throw an exception.

- 应修改为：例如，setRequestHeader()方法的调用必须在调用open()**之后**但在调用send()**之前**，否则它将抛出异常。



### 18.1.3 编码请求主体

- 位置：P496中间，例18-6上面的段落

- 错误内容：GET请求**从来没有**主体，所以需要发送给服务器的表单编码**数据“负载”**要作为URL（**后跟一个问好**）的查询部分。

- 错误描述：这里有3个问题：

  1. 我感觉“never have”翻译成“绝对没有”更好，之前在P490介绍`request.send(null)`方法的时候，也翻译成了“GET请求绝对没有主体,”（GET requests never have a body, so you should pass null or omit the argument.）

  2. payload，数据传输中的实际信息称作payload（好像更多的翻译为“有效负载”或“有效载荷”），也称作“实际数据”，这部分是数据传输的基本目的，其余的（HTTP请求头等）则为“开销数据”。这里的意思应该是，POST的实际数据放在body中，而GET没有body，所以实际数据要放在URL的query部分。
  3. “后跟一个问号”，这里应该翻译成“跟在问号后面”。URL规范中，search的格式为：`?query=string`，所以`?`后面的表示query。

  英文原文：GET requests never have a body, so the “payload” of formencoded data has to be sent to the server as the query portion of the URL (following a question mark).

- 应修改为：GET请求绝对没有body，所以表单编码数据的“有效载荷”作为URL的query部分（跟在问号后面）被发送到服务器。



### 18.1.4 HTTP 进度事件

- 位置：P500，18.1.4节第6段。
- 错误内容：可以通过 `XMLHttpRequest` 对象的 `addEventListener()` 方法为这些**progress事件**中的每个都注册处理程序。

- 错误描述：翻译错误，英文原文中有“progress event**s**”和“progress event”两个名词。“progress events”在本节中泛指各类**“进度事件”**，如：load、abort、progress等，在本节中应该翻译成**“进度事件”**，就如本节标题：“18.1.4 HTTP进度事件”。巧合的是这些进度事件中，有个叫“progress event”（本节第二段介绍），指的是 `MLHttpRequest.onprogress`事件，中文版应该翻译为 **“progress事件”**。此处的意思应该是：可以用addEventListener()注册各类**进度事件**，也可以使用更容易的处理程序属性，比如onprogress、onload。

  英文原文：You can call the addEventListener() method of the XMLHttpRequest object register handlers for each of these progress events.

- 应修改为：你可以调用 `XMLHttpRequest` 对象的 `addEventListener()` 方法注册每一个进度事件。