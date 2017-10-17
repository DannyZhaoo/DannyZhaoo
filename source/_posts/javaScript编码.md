---
title: javaScript编码
date: 2017-10-11 17:10:21
tags: JavaScript
categories: 编程语言
---

javascript 的编码一般有三个，但是常用的是后面两种。

1. escape()、unescape()

这个是对字符串的编码，会返回一个字符的Unicode编码值。

escape()这个函数不对“+”编码，因为在提交表单的时候，空格会被转化为+字符。

这个函数现在已经不提倡使用。

2. encodeURl()、decodeURl()

对URL其中的某些字符将被十六进制的转义序列进行替换，不会对 ASCII 字母和数字进行编码，也不会对这些 ASCII 标点符号进行编码：;/?:@&=+$,'#。

3. encodeURlComponent()、decodeURlComponent()

对URL其中的某些字符将被十六进制的转义序列进行替换，同时也能编码：;/?:@&=+$,'#这些特殊字符。