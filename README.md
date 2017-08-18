# 《JavaScript权威指南》勘误表中文版

官方英文原版勘误表：[Errata for JavaScript: The Definitive Guide](http://www.oreilly.com/catalog/errata.csp?isbn=9780596805531)

---

**注意**：

1. 本勘误表，以《JavaScript权威指南》中文第六版实体书的章节及页数为准。
1. 本勘误表中顺序，并未与官方原版勘误表对应，而是以实体书的页码顺序进行排序。

勘误表格式说明：

```text
第X章-第Y节 // 错误所在的章和节
位置：第Z页中间 // 错误所在的位置
错误内容：本小节的第一个网址 http:/oreilly.com/catalog/9780596805531 // 出现错误的内容
应更正为：http://oreilly.com/catalog/errata.csp?isbn=9780596805531 // 错误所应更正为的内容
```

---

## 前言-勘误表以及如何联系我们

- 位置：第3页
- 错误内容：本小节的第一个网址 http:/oreilly.com/catalog/9780596805531
- 应更正为：http://oreilly.com/catalog/errata.csp?isbn=9780596805531

## 第一章-第二节客户端JavaScript

- 位置：第15页上方一大段代码，倒数第二行的函数
- 错误内容：`function hide(event) { event.target.style.visibility = "hidden"; }`
- 应更正为：

```js
function hide(event) {
    // srcElement属性在IE8中要用到，target属性则用于Chrome及Firefox
    var target = event.target ? event.target : event.srcElement;
}
```
