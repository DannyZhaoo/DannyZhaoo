---
title: UI层的松耦合
date: 2017-10-12 09:51:04
tags: JavaScript编程模式
categories: 编程知识储备
---

目的：修改一个组件而不需要更改其他组件。

减少跟踪文本和结构性问题的复杂度，提高代码的可维护性。

- 将JavaScript从CSS中抽离

> 避免在CSS中使用JavaScript代码。

- 将CSS从JavaScript中抽离。

> 操作CSS的className来替代直接修改与元素样式。

- 将JavaScript从HTML中抽离。

> 使用JavaScript来添加事件，而不是用在HTML中直接给on属性挂载事件。
>
> 将所有的JavaScript代码都放入外置文件中。

- 将HTML从JavaScript中抽离。

> 定义模板，用占位符或是在HTML中使用变量。类似于vue的data。



*摘自《编写可维护的JavaScript》*