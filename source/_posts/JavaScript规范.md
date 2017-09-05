---
title: JavaScript规范
date: 2017-09-05 09:21:59
tags: 
categories: 前端标准/规范
---

进入公司学习，平时最大的问题除了自己需要学习很多东西外，就是各种代码的缩进和空格等问题。所以在此记录一下自己一直出错的问题。

# 三元运算符

```javascript
// 三元运算符由3部分组成，因此其换行应当根据每个部分的长度不同，形成不同的情况。
var result = thisIsAVeryVeryLongCondition
    ? resultA : resultB;

var result = condition
    ? thisIsAVeryVeryLongResult
    : resultB;
```

