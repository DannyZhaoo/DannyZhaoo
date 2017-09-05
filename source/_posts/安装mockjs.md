---
title: 安装mockjs
date: 2017-06-02 18:25:39
tags: mockjs
categories: 前端框架/库
---

首先配置安装

## Node

```
#安装mock，这个只能在这个文件中使用
npm install mockjs
```

​ 然后在这个文件夹中新建一个mock.js

```
// 使用 Mock
var Mock = require('mockjs')
var data = Mock.mock({
    // 属性 list 的值是一个数组，其中含有 1 到 10 个元素
    'list|1-10': [{
        // 属性 id 是一个自增数，起始值为 1，每次增 1
        'id|+1': 1
    }]
})
// 输出结果
console.log(JSON.stringify(data, null, 4))
```

​ 在shell中运行，会看到相应的输出结果。

## Bower

```
#这里是需要依赖bower，所以在哪里需要，就在哪里执行
npm install -g bower #-g 全局
bower install --save mockjs
```

​ 然后调用就直接可以用

```
<script type="text/javascript" src="./bower_components/mockjs/dist/mock.js"></scrip
```