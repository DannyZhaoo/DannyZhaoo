---
title: CSS布局总结
date: 2017-12-12 13:50:40
tags: CSS
categories: 编程语言
---

## flex居中显示

想要的效果，div内的三个内容分别每一列都是**独占一行并且居中显示**。

HTML结构如下

```html
<div class="know">
    <img width="270px" height="307px"/>
    <span class="know-tip">报名成功</span>
   	<button class="know-button">知道了</button>
</div>
```

CSS：

```css
.know {
    width: 100%;
    @include flexbox;
    @include justify-content;
}
```

问题:

div包含的元素都在一列显示，不是单独占一行，并且这个跟子元素是行内元素还是块级元素无关。

之后把后面两个子元素设置成如下，然后局部再调整。

```scss
.know {
    &-tip, &-button {
      	position: absolute;
    }
}
```

但是这个在某些手机上，后面两个的位置会被挤的偏右，不是居中显示。所以只能设置单个元素如下：

```scss
.know {
    &-tip, &-button {
      	position: absolute;
      	left: 50%;
      	transform: translateX(-50%);
    }
}
```

