---
title: Date对象的处理技巧
date: 2017-10-11 14:14:44
tags: JavaScript
categories: 编程语言
---

- 获取当前所属的季度

```javascript
function getSeason (month) {
  	//Math.ceil是向上取整
  	return Math.ceil((month + 1) / 3);
}
```

- 判断一个数据是否为日期对象

```javascript
Object.prototype.toString.call(dateObj) !== '[object Date]'
```

- 获取某年二月份的最后一天

```javascript
// 方法一
new Date(2017, 2, 0);
// 方法二 60 * 60 * 24 * 1000
new Date(2017, 2, 1) - 86400000;
// 方法三
var date = new Date(2017, 2, 1);
new Date(date.setDate(date.getDate() - 1));
```

- 获取当天时间的起始时间

```javascript
var now = new Date();
// 方法一 getMonth()得到的月份比正常少一
new Date(now.getFullYear() + '-' + (now.getMonth() + 1) + '-' + now.getDate() + ':00:00:00');
// 方法二
new Date(now.getFullYear(), now.getMonth(), now.getDate());
// 方法3
import date from 'fecha';
fecha.parse(new Date().toString(), 'yyyy-MM-dd');

```

*注意：学习JavaScript的处理函数可以看fecha的源码。*