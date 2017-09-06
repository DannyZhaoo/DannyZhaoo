---
title: setTimeout用法
date: 2017-09-06 10:38:25
tags: JavaScript
categories: 编程语言
---

setTimeout 永远是里面的函数一执行完，就被销毁。

而clearTimeout是在setTimeout里面的函数没被执行的时候就销毁。

setTimeout同时还有别的作用就是这个里面的函数是在所有同步的函数执行完后，才开始执行。相当于改变了代码的执行顺序。

这样做目前的作用是DOM需要绑定这个函数，然而在执行的时候，DOM没有渲染完，函数无法找到DOM，所以需要滞后调用。

而在setTimeout里面写推迟执行的时间，也不是准确的时间。是在所有的函数执行完后才开始计时，这样的计时当然不准。只能做大概推测。