---
title: 利用Timeout制作导航
date: 2017-06-02 18:20:41
tags:
categories:
---

## html部分

- ### 首先用**Emmet**写出html文件的结构

  div#nav>ul>(li>a[href=”javascript::”]+div.subnav>em.arrow+p>span>(a[href=”javascript”])*8)*8

  **好处：**

  ​ 用Emmet写html速度很快，而且结构一目了然，在sublime中的快捷键是`ctrl + alt + enter`。


- ### 然后补充相应的导航内容

```
<div id="nav">
		<ul>
			<li>
				<a href="javascript::">站长直接</a>
			</li>
			<li>
				<a href="javascript::">行业资讯</a>
				<div class="subnav">
					<em class="arrow"></em>
					<p>
						<span>
							<a href="javascript:;">业界动态</a>|
							<a href="javascript:;">收购融资</a>|
							<a href="javascript:;">门户动态</a>|
							<a href="javascript:;">搜索引擎</a>|
							<a href="javascript:;">网络游戏</a>|
							<a href="javascript:;">电子商务</a>|
							<a href="javascript:;">广告传媒</a>|
							<a href="javascript:;">厂商开发</a>

						</span>
					</p>
				</div>
			</li>
			<li>
				<a href="javascript::">站长在线</a>
				<div class="subnav">
					<em class="arrow"></em>
					<p><span>
						<a href="javascript:;">站长报道</a>|
						<a href="javascript:;">好站推荐</a>|
						<a href="javascript:;">站长聚会</a>|
						<a href="javascript:;">站长访谈</a>|
						<a href="javascript:;">站长茶馆</a>|
						<a href="javascript:;">网站排行</a>

					</span></p>
				</div>
			</li>
			<li>
				<a href="javascript::">网站运营</a>
				<div class="subnav">
					<em class="arrow"></em>
					<p><span>
						<a href="javascript:;">建站经验</a>|
						<a href="javascript:;">策划盈利</a>|
						<a href="javascript:;">搜索优化</a>|
						<a href="javascript:;">网站推广</a>|
						<a href="javascript:;">免费资源</a>

					</span></p>
				</div>
			</li>
			<li>
				<a href="javascript::">设计在线</a>
				<div class="subnav">
					<em class="arrow"></em>
					<p><span>
						<a href="javascript:;">酷站推荐</a>|
						<a href="javascript:;">网页设计</a>|
						<a href="javascript:;">WEB标准</a>|
						<a href="javascript:;">视频处理</a>|
						<a href="javascript:;">设计活动</a>

					</span></p>
				</div>
			</li>
			<li>
				<a href="javascript::">网络编程</a>
				<div class="subnav">
					<em class="arrow"></em>
					<p><span>
						<a href="javascript:;">Asp编程</a>|
						<a href="javascript:;">Php编程</a>|
						<a href="javascript:;">.Net编程</a>|
						<a href="javascript:;">Xml编程</a>|
						<a href="javascript:;">Access</a>|
						<a href="javascript:;">Mssql</a>|
						<a href="javascript:;">Mysql</a>

					</span></p>
				</div>
			</li>
			<li>
				<a href="javascript::">联盟资讯</a>
				<div class="subnav">
					<em class="arrow"></em>
					<p><span>
						<a href="javascript:;">联盟动态</a>|
						<a href="javascript:;">联盟介绍</a>|
						<a href="javascript:;">联盟点评</a>|
						<a href="javascript:;">网赚技巧</a>

					</span></p>
				</div>
			</li>
			<li>
				<a href="javascript::">服务器</a>
				<div class="subnav">
					<em class="arrow"></em>
					<p><span>
						<a href="javascript:;">Web服务器</a>|
						<a href="javascript:;">Ftp服务器</a>|
						<a href="javascript:;">Mail服务器</a>|
						<a href="javascript:;">Dns服务器</a>|
						<a href="javascript:;">Win服务器</a>|
						<a href="javascript:;">Linux服务器</a>|
						<a href="javascript:;">安全防护</a>|
						<a href="javascript:;">虚拟主机</a>

					</span></p>
				</div>
			</li>
		</ul>
	</div>
```

## css部分

我这是看着代码想的写css应该的每部分的作用，同时也有利于设计html的层次结构

- ### 首先设置一般的所有默认属性

  ```
  body,div,ul,li,p{
    margin:0;
    padding:0;
  }
  body{
    font:12px/1.5 Arial;
  }
  ul{
    list-style-type:none;
  }
  ```

- ### 这个导 航栏的背景主要用的是一个图片

  ```
  #nav,#nav ul,#nav ul li,#nav ul li a:hover,#nav .subnav,#nav .subnav p,#nav .subnav p span,#nav .subnav .arrow{
  background:url(http://fgm.cc/learn/lesson4/img/nav_bg.png) no-repeat;
  }
  ```

[![导航栏的背景图片](http://fgm.cc/learn/lesson4/img/nav_bg.png)](http://fgm.cc/learn/lesson4/img/nav_bg.png)

- ### 导航的css的用法解释

```css
/*最外层设置宽度，位置*/
#nav{
position:relative;/*对二级标题的位置设置有用*/
width:910px;
background-position:0 -36px;/*这是设置最左边的背景，属性值是相对于原来的位置偏移多少*/
margin:10px auto;
}
/*ul设置高度还有整体的导航栏的左右宽度,多余的部分都隐藏起来*/
#nav ul{
height:36px;
line-height:36px;
margin-left:10px;
padding-right:10px;
overflow:hidden;
background-position:right -72px;/*设置最右边的背景*/
}
/*ul的li需要全部靠左浮动，浮动后元素就可以设置宽高*/
#nav ul li{
float:left;
width:110px;
margin-left:-2px;
background-position:0 -108px;
}
/*主要是设置字大小，颜色，居中显示，去掉<a>原来的修饰*/
#nav ul li a{
font-size:14px;
color:#fff;
width:102px;
display:block;
text-align:center;
text-decoration:none;
margin:0 2px 0 4px;
}
/*设置hover后的变化*/
#nav ul li a:hover{
font-weight:700;
background-position:-3px -144px;
}
/*下面是设置二级标题，类似于一级标题*/
#nav .subnav{
display:none;
position:absolute;
top:41px;
width:auto!important;
min-width:110px;
height:27px;
line-height:27px;
white-space:nowrap;/*规定段落中的文本不进行换行*/
background-position:0 -180px;
}
#nav .subnav p{
margin-left:10px;
padding-right:10px;
background-position:right -234px;
}
#nav .subnav p span{
display:block;
color:#235e99;
background-repeat:repeat-x;/*沿着x轴的方向重复*/
background-position:0 -207px;
}
#nav .subnav p a{
font-size:12px;
display:inline;/*a标签会继承父元素的display*/
color:#235e99;
text-decoration:none;
margin:0 5px;
padding:0 2px;
}
#nav .subnav p a:hover{
font-weight:400;
background-image:none;
border-bottom:2px solid;
}
#nav .subnav .arrow{
position:absolute;
top:-4px;
display:block;
width:11px;
height:5px;
background-position:0 -261px;
}
```



## JavaScript部分

- ### 首先是一个方法集合，容易得到元素

  ```
  var get={
  	//通过id得到元素
  	byId:function(id){
  		return document.getElementById(id);
  	},
  	//得到oParent里包含的所有带有sClass的元素
  	byClass:function(sClass, oParent){
  		var aClass = [];
  		var reClass = new RegExp("(^|)"+sClass+"(|$)");
  		//oParent子代中所有元素
  		var aElem = this.byTagName("*",oParent);
  		for(var i=0; i < aElem.length; i++){
  			//包含sClass
  			reClass.test(aElem[i].className)&&aClass.push(aElem[i]);
  		}
  		return aClass;
  	},
  	//在obj里得到标签是elem的元素组
  	byTagName:function(elem,obj){
  		return (obj||doocument).getElementsByTagName(elem)
  	}
  };
  ```

- ### 元素的动态变化

  ```
  window.onload=function(){
  	var oNav = get.byId("nav");
  	var aLi = get.byTagName("li",oNav);
  	var aSubNav = get.byClass("subnav",oNav);
  	var oSubNav = oEm = timer = null;
  	var i = 0;

  	for(i=1;i<aLi.length;i++){
  		aLi[i].onmouseover = function(){
  			//隐藏所有的子菜单
  			for(i=0;i<aSubNav.length;i++){
  				aSubNav[i].style.display = "none";
  			}
  			//获得该项下的子菜单
  			oSubNav = get.byClass("subnav",this)[0];
  			//获取该项下的指示箭头
  			oEm = get.byTagName("em",this)[0];
  			//显示该项下的菜单
  			oSubNav.style.display = "block";
  			//判断显示区域，与nav的position属性设置为relative对应
  			oNav.offsetWidth - this.offsetLeft > oSubNav.offsetWidth?oSubNav.style.left = this.offsetLeft + "px":oSubNav.style.right=0;
  			//计算指标箭头显示位置
  			oEm.style.left = this.offsetLeft - oSubNav.offsetLeft + 50+ "px";
  			clearTimeout(timer);
  			//阻止事件冒泡，后面有解释原因
  			oSubNav.onmouseover = function(event){
  				(event||window.event).cancelBubble = true;
  				clearTimeout(timer);
  			}
  		};
  		aLi[i].onmouseout = function(){
  			//300毫秒后display为none
  			timer = setTimeout(function(){
  				oSubNav.style.display = "none";
  			},300)
  		}

  	}
  };
  ```

#### **为什么js要阻止事件冒泡**

某个DOM节点绑定了某事件监听器，本来是想当该DOM节点触发事件，才会执行回调函数。结果是该节点的某后代节点触发某事件，由于事件冒泡，该DOM节点事件也会触发，执行了回调函数，这样就违背了最初的本意了。
在这个例子中，二级元素的鼠标放上去，会触发一级标题的onmouseover函数，而这个就是调用就会形成无限循环，一直调用，所以此处阻止冒泡，就触发不了父元素的onmouseover事件了。