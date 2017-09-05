---
title: Hexo博客搭建
date: 2017-06-02 18:11:17
tags: 
- hexo
categories: 
- 开发工具
---

## 安装nodejs

去[nodejs官网](https://nodejs.org/en/download/)下载对应系统的安装包，按提示安装

检视安装成功

```shell
node -v	
```

## 利用Hexo搭建博客

### 创建博客目录

```shell
hexo init dannyzhaoo.github.io
cd dannyzhaoo.github.io
```

### 生成静态界面

``` shell
hexo clean  //如果是这个网页上有内容的最好就不要这步了
hexo g
```

|g 即generate

### 运行

```shell
hexo s
```

## 配置文件

这部分主要是指的是站点配置文件

```
title: 流光
subtitle: 细数似水年华的美好
description:
author: DannyZhao
language: zh-Hans   //如果没有设置，文章所有的字都不是简体中文
timezone:
url: http:/dannyzhaoo.github.io
```

## 更换一个好看的主题

### 下载一个主题

```she
git clone https://github.com/iissnan/hexo-theme-next themes/next
```

### 网站的站点文件里设置

```
theme: next   //更换主题
```

## 部署到GitHub上

### 安装[hexo-deployer-git](https://github.com/hexojs/hexo-deployer-git)

```shell
npm install hexo-deployer-git --save
```

### 网站配置文件

```
deploy:
  type: git
  repo: https://github.com/DannyZhaoo/DannyZhaoo.github.io
  branch: master
```

### 部署

```shell
hexo d
```

## 添加标签，分类

## 网站的配置文件

一般下载下来就不用改了，都包含着

```
tag_dir: tags
archive_dir: archives
category_dir: categories
code_dir: downloads/code
```

### 主题的配置文件

```
menu:
  home: /
  categories: /categories
  archives: /archives
  tags: /tags
  about: /about
```

### 新建tags和categories页面

```
hexo new page tags
hexo new page categories
```

### 修改source下的tags/index.md和categories/index.md

注意冒号是**英文**的。

```markdown
title: tags
date: 2017-06-02 16:48:54
type: "tags"
comments: false
```

```
title: categories
date: 2017-06-02 16:48:48
type: "categories"
comments: false

```

## 主题配置

### 设置RSS

```shell
npm install hexo-generator-feed --save
```

### 设置代码高亮

```
# Code Highlight theme
# Available value: normal | night | night eighties | night blue | night bright   可以从这几种中进行选择
# https://github.com/chriskempson/tomorrow-theme
highlight_theme: normal
```

### 设置样式

```
# Schemes
#scheme: Muse
scheme: Mist
#scheme: Pisces
```

### 建立站点时间

```
since: 2017
```

### 设置动画效果

```
use_motion: true  # 开启动画效果
use_motion: false # 关闭动画效果
```

### 设置背景动画

有`canvas_nest`或`three_waves`只能同时开启一种背景动画效果。

```
# canvas_nest
canvas_nest: true //开启动画
canvas_nest: false //关闭动画


# three_waves
three_waves: true //开启动画
three_waves: false //关闭动画
```

### 修改个人介绍部分的图片

要在next的source中images里添加一个图片

```
avatar: /images/avatar.jpg
```

### 设置阅读全文

在主题配置文件中添加

```
auto_excerpt:
  enable: true
  length: 220
```

### 设置Favicon

将图片放在站点的`source`下

### 新建文件的模板

这部分markdown的文件放在站点文件下的scaffolds里。