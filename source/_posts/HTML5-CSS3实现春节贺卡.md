---
title: HTML5+CSS3实现春节贺卡
date: 2017-06-05 18:37:39
tags: 
- HTML5
- CSS3
categories: 移动终端
---

## 目标

- 根据设计稿对项目进行整套项目的需求进行剖析并开发。
- 对项目开发流程需要有一个基本的了解。
- 运用切图、重构、前端的知识对项目进行灵活控制。

### 需求分析

- 项目主题，恭贺新春，采取欢快活泼的表现形式。
- 根据psd稿图层分析，多页视觉放到一个网页文档，采取视觉差特效完成分析展示。
- 音乐不跟随翻页，位置固定，播放旋转，可暂停。

### 开发技能分析

- 移动端项目，采取Html5作为项目的结构层。
- 分析网页呈现形势，直接采用CSS3完成网页的表现层。
- 特效分析，采用CSS3完成主要特效，采用JavaScript控制交互。
- 背景音乐直接采取JavaScript控制Audio的API进行控制。
- 直接采取原生态的JavaScript控制CSS实现翻页效果，放弃前端框架。和类库。

### 性能优化分析

- 项目为移动端项目，尽可能简化结构层标签。
- 尽可能少用图片，尽量直接用CSS3控制标签完成图片效果。
- 尽可能减小文件的大小，压缩图片到无损最小值。
- 减少服务器请求此次数，用原生态JavaScript代替Zepto等前端框架。

## 移动端项目开发

切图 ---> 重构 ---> 前端 ---> 优化

-  减少图片文件，背景图片采取JPG格式，其他图片采取png24透明格式。
-  小型项目，直接采取手写HTML5+CSS3完成。
-  采用JavaScript控制HTML5API完成特效。
-  测试并优化整体网站性能，采用WampServer为本地服务器测试环境。

### 项目开发----结构层

```html
<!DOCTYPE html>
<html lang="Zh-cn">
    <head>
        <title>慕课贺春</title>
        <meta charset="UTF-8">
        <!-- 强制以webkit内核渲染-->
        <meta http-equiv="X-UA-Compatible" content="IE=edge, chrome=1">
        <!--视口-->
        <meta name="viewport" content="width=device-width,initial-scale=1,minium-scale=1,maximum-scale=1,user-scalable=no">
        <!--不拨号-->
        <meta name="format-detection" content="telephone=no">
        <link rel="stylesheet" type="" href="css/style.css">
    </head>
    <body>
        <div class="music">
            <img src="images/music_pointer.png">
            <img class="play" id="music" src="images/music_disc.png">
        </div>
        <div class="page" id="page1">
            <div class="bg"></div>
            <div class="p1_lantern">点击屏幕<br>开启好运2016</div>
            <div class="p1_imooc"></div>
            <div class="p1_words">2016年慕课网新年特献</div>
        </div>
        <div class="page" id="page2">
            <div class="bg p2_bg_loading"></div>
            <div class="bg"></div>
            <div class="p2_circle"></div>
            <div class="p2_2016"></div>
        </div>
        <div class="page" id="page3">
            <div class="bg"></div>
            <div class="p3_logo"></div>
            <div class="p3_title"></div>
            <div class="p3_second"></div>
            <div class="p3_first"></div>
            <div class="p3_blessing"></div>
        </div>
        <audio autoplay="true">
            <source src="audio/happynewyear.mp3" type="audio/mpeg">
        </audio>
        <script src="js/script.js" type="text/javascript"></script>
    </body>
</html> 
```

### 项目开发----表示层

#### 全局设定

```css
* {
  margin: 0;
  padding: 0;
  border:0;
  /*注意这个单位是vw*/
  font-size:1.5625vw;
  font-family: "Microsoft Yahei";
}
```

####  music的部分

```css
.music {
  position: fixed;
  top:3vh;
  right: 4vw;
  z-index:5;
  width:15vw;
  height:15vw;
  border: 4px solid #ef1639;
  border-radius: 50%;
  background: #fff;
}
.music > img:first-of-type {
  position:absolute;
  /*这里是为了让指针在盘上*/
  z-index:1;
  top:24%;
  right:2.5%;
  width: 28.421%;
}
.music > img:last-of-type{
  position: absolute;
  z-index:0;
  top: 0;
  right: 0;
  bottom: 0;
  left: 0;
  margin: auto;
  width: 79%;
}
.music > img.play{
    -webkit-animation: music_disc 4s linear infinite;
            animation: music_disc 4s linear infinite;}
@keyframes music_disc {
    0% {
        -webkit-transform: rotate(0deg) ;
                transform: rotate(0deg) ;
    }
    100% {
        -webkit-transform: rotate(360deg);
        transform: rotate(360deg);
        }
}
@-webkit-keyframes music_disc {
    0% {
        -webkit-transform: rotate(0deg);
        transform: rotate(0deg);
    }
    100% {
        -webkit-transform: rotate(360deg);
        transform: rotate(360deg);
        }
}

```

#### 设置每一页

```css
.page{
  position: absolute;
  idth: 100%;
  height: 100%}
.page> .bg{
  position: absolute;
  /* 让其成为背景，不能遮住字 */
  z-index:-1; 
  width: 100%;
  height: 100%;}

/* page1 */

#page1 {display: block;}
#page1 > .bg{
  background: url("../images/p1_bg.jpg") no-repeat center center;/* 使之自适应 */background-size: 100%;}
#page1 > .p1_lantern{color:#fff;position: absolute;/* 确定下面的空间*/top: -3.4%;right:0;left: 0;margin:auto;background: url("../images/p1_lantern.png") no-repeat center bottom;background-size: 100%;width: 45vw;height:71.2vh;font-size: 3.506rem;padding-top: 31vh;text-align: center;-webkit-box-sizing: border-box;   -moz-box-sizing: border-box;-ms-box-sizing: border-box; -o-box-sizing: border-box;box-sizing: border-box;}
#page1 > .p1_lantern::before{
    /*定位中间*/position: absolute;
    top: 0;
    right: 0;
    bottom: 0;
    left:0;
    z-index: -1;
    content: "";
    margin:auto;
    width:30vw;
    height: 30vw;
    background: #d60b3b;
    opacity: 0.5;
    border-radius: 50%;
    -webkit-box-shadow: 0 0 10vw 10vw #d60b3b;
    -moz-box-shadow: 0 0 10vw 10vw #d60b3b;
    -ms-box-shadow: 0 0 10vw 10vw #d60b3b;
    -o-box-shadow: 0 0 10vw 10vw #d60b3b;
    box-shadow: 0 0 10vw 10vw #d60b3b;
    animation: p1_lantern .5s infinite alternate;
    -webkit-animation: p1_lantern .5s infinite al;
}
@-webkit-keyframes p1_lantern{
    0% {
        opacity: .5;
        -webkit-transform: scale(.8,.8);
        transform: scale(.8,.8);
    }
    100%{
        opacity: 1;
    }
}
@keyframes p1_lantern{
    0% {
        opacity: .5;
        -webkit-transform: scale(.8,.8);
        transform: scale(.8,.8);

    }
    100%{
        opacity: 1;
    }
}
#page1 > .p1_imooc{position: absolute;right: 0;bottom:9vh;left:0;background: url("../images/p1_imooc.png") no-repeat center center;width: 27.656vw;height: 18.63vh;margin: auto;}
#page1 > .p1_words {font-size: 2.134rem;position: absolute;right:0;left: 0;bottom: 48px;text-align: center;color: #231815;}

/* page2 */

#page2 {
  	display: none;
  	/*发生变化时逐渐变化*/
    -webkit-transition:.5s;
    transition:.5s;
}
#page2.fadeOut{
  	/*水平上不变，垂直方向上向上移动*/
  	opacity: .3;
    -webkit-transform: translate(0,-100%);
            transform: translate(0,-100%);
}
#page2 > .p2_bg_loading{
    z-index: 4;
    background: #ef1639;
    -webkit-animation: p2_bg_loading 1s linear forwards;
    animation: p2_bg_loading 1s linear forwards; 
}
@-webkit-keyframes p2_bg_loading{
    0%{opacity: 1;}
    100%{opacity: 0;}
}
@keyframes p2_bg_loading{
    0%{opacity: 1;}
    100%{opacity: 0;}
}
#page2 > .bg{
  	background: url("../images/p2_bg.jpg") no-repeat center center;
 	 /* 使之自适应 */
 	 background-size: 100%
}
#page2 > .p2_circle{
    position: absolute;
    top: 0;
    right: 0;
    bottom: 0;
    left: 0;
    margin: auto;
    border-radius: 50%;
    background: url("../images/p2_circle_outer.png") no-repeat center center;
    background-size: 100%;
    width: 59.375vw;
    height: 59.375vw;
    -webkit-animation:p2_circle_outer 1s linear 3s infinite;
            animation:p2_circle_outer 1s linear 3s infinite;
}
@-webkit-keyframes p2_circle_outer{
    0% {
        -webkit-transform: rotate(0deg);
        transform: rotate(0deg);
    }
    100% {
      	/*注意三个图片转动的角度不能一样*/
        -webkit-transform: rotate(-360deg);
        transform: rotate(-360deg);
}
}
@keyframes p2_circle_outer{
    0% {
        -webkit-transform: rotate(0deg);
        transform: rotate(0deg);
    }
    100% {
        -webkit-transform: rotate(-360deg);
        transform: rotate(-360deg);
    }
}
/*在同一个位置添加多个图的方法，不能少了content*/
#page2 > .p2_circle::before{
    position: absolute;
    top: 0;
    right: 0;
    bottom: 0;
    left: 0;
    margin: auto;
    content: "";
    border-radius: 50%;
    background: url("../images/p2_circle_middle.png") no-repeat center center;
    background-size: 100%;
    width: 45.625vw;
    height: 45.625vw;
    -webkit-animation:p2_circle_middle 1s linear 2s infinite;
    animation:p2_circle_middle 1s linear 2s infinite;
}
@-webkit-keyframes p2_circle_middle{
    0% {
        -webkit-transform: rotate(0deg);
        transform: rotate(0deg);
    }
    100% {
        -webkit-transform: rotate(720deg);
        transform: rotate(720deg);
}
}
@keyframes p2_circle_middle{
    0% {
        -webkit-transform: rotate(0deg);
        transform: rotate(0deg);
    }
    100% {
        -webkit-transform: rotate(720deg);
        transform: rotate(720deg);
}
}
#page2 > .p2_circle::after{
    position: absolute;
    top: 0;
    right: 0;
    bottom: 0;
    left: 0;
    margin: auto;
    content: "";
    border-radius: 50%;
    background: url("../images/p2_circle_inner.png") no-repeat center center;
    background-size: 100%;
    width: 39.9375vw;
    height: 39.9375vw;
    -webkit-animation:p2_circle_inner 1s linear 1s infinite;
    animation:p2_circle_inner 1s linear 1s infinite;
}
@-webkit-keyframes p2_circle_inner{
    0% {
        -webkit-transform: rotate(0deg);
        transform: rotate(0deg);
    }
    100% {
        -webkit-transform: rotate(-1080deg);
        transform: rotate(-1080deg);
        }
}
@keyframes p2_circle_inner{
    0% {
        -webkit-transform: rotate(0deg);
        transform: rotate(0deg);
    }
    100% {
        -webkit-transform: rotate(-1080deg);
        transform: rotate(-1080deg);
        }
}
#page2 > .p2_2016{
  position: absolute;
  top: 0;
  right: 0;
  bottom: 0;
  left: 0;
  margin: auto;
  background: url("../images/p2_2016.png") no-repeat center center;
  background-size: 100%;
  width: 27.5vw;
  height: 6.24vh;
}

/* page3 */

#page3 {
  	display: none;
    -webkit-transition: .5s;
    transition: .5s;}
#page3.fadeIn{
    -webkit-transform: translate(0,-100%);
    transform: translate(0,-100%);
}
#page3 > .bg{
  background: url("../images/p3_bg.jpg") no-repeat center center;
  /* 使之自适应 */
  background-size: 100%;
}
#page3 > .p3_logo {
  width:34.6875vw;
  height: 6.327vh;
  position: absolute;
  top:7.82vh;
  right: 0;
  left: 0;
  margin: auto;
  background: url("../images/p3_logo.png") no-repeat center center;
  /* 撑到指定的宽度 */
  background-size: 100%;
}
#page3 > .p3_title{
  width: 48.125vw;
  height: 50vh;
  position: absolute;
  top: 21vh;
  right: 0;
  left: 0;
  margin: auto;
  background: url("../images/p3_title.png") no-repeat center center;
  background-size: 100%;
}
#page3 > .p3_second{
  width: 22.8125vw;
  height: 41.625vh;
  position: absolute;
  top: 25.48vh;
  left: 3.75vw;
  background: url("../images/p3_couplet_second.png") no-repeat center center;
  background-size: 100%;
}
#page3 > .p3_first{
  width: 22.8125vw;
  height: 41.625vh;
  position: absolute;
  top: 25.48vh;
  right: 3.75vw;
  background: url("../images/p3_couplet_first.png") no-repeat center center;
  background-size: 100%;
}
#page3 > .p3_blessing {
    width: 32vw;
    height: 32vw;
    position: absolute;
    bottom: 10vh;
    right: 0;
    left: 0;
    margin: auto;
    border-radius: 50%;
    background: url("../images/p3_blessing.png") no-repeat center center;
    /*撑到指定的宽度*/
  	background-size: 100%;
    -webkit-animation:p3_blessing 3s linear infinite;
    animation:p3_blessing 3s linear infinite;
}
@-webkit-keyframes p3_blessing{
    0% {
        -webkit-transform: rotate(0deg);
        transform: rotate(0deg);
    }
    100% {
        -webkit-transform: rotate(360deg);
        transform: rotate(360deg);
	}
}
@keyframes p3_blessing{
    0% {
        -webkit-transform: rotate(0deg);
        transform: rotate(0deg);
    }
    100% {
        -webkit-transform: rotate(360deg);
        transform: rotate(360deg);
	}
}
```

#### 动态效果部分

```javascript
//获取元素
var page1 = document.getElementById("page1");
var page2 = document.getElementById("page2");
var page3 = document.getElementById("page3");
var music = document.getElementById("music");
var audio = document.getElementsByTagName("audio")[0];
//当音乐播放完停止时候，自动停止光盘旋转效果
audio.addEventListener("ended",function(event){
    music.setAttribute("class","");
},false);
//点击音乐图标，控制音乐播放效果   适合触屏操作
music.addEventListener("touchstart",function(event){
    if(audio.paused){
        audio.play();
        this.setAttribute("class","play");
    }else{ 
        audio.pause();    
        this.setAttribute("class","");
    };
},false);
//点击屏幕，开启好运2016
page1.addEventListener("touchstart",function(event){
    page1.style.display = "none";
    page2.style.display = "block";
    page3.style.display = "block";
     page3.style.top = "100%";
    setTimeout(function(){
        page2.setAttribute("class","page fadeOut")
        page3.setAttribute("class","page fadeIn")

    },5500);
},false);
```

## 总结

做完这个项目，觉得**前端**要积累还真是很多啊。

不管是编码工具，测试方法，要关注的地方都十分的多，还是需要继续练习啊！

