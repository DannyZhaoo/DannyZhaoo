---
title: 安装Gitbook
date: 2017-06-08 21:25:35
tags: gitbook
categories: gitbook
---

## Gitbook安装

安装gitbook的前提是已经安装过nodejs

```shell
//安装gitbook
D:> npm install gitbook-cli -g
//验证
D:>	gitbook -v
```

## 图书编辑

### 先建立SUMMARY.md

这个文件是一本书的目录结构，使用markdown语法，这个文件在使用gitbook命令行之前要先写好，以便之后生成书的目录。例如：

```markdown
* [基本安装](howtouse/README.md)
 - [Node.js安装](howtouse/Nodejsinstall.md)
 - [Gitbook安装](howtouse/gitbookinstall.md)
 - [Gitbook命令行速览](howtouse/gitbookcli.md)
* [图书编辑](book/README.md)
 - [gitbook命令行&markdown编辑](book/gitbook-cli.md)
 - [gitbook editor编辑](book/editor.md)
* [图书输出](output/README.md)
 - [输出为静态网站](output/outfile.md)
 - [输出PDF](output/pdfandebook.md)
* [发布](publish/README.md)
  - [发布到gitbook.com](publish/gitbook.md)
  - [Github集成](publish/github.md)
  - [发布到Github Pages](publish/gitpages.md)
* [结束](end/README.md)
```

列表加链接，链接中可以使用目录，也可以不必使用。

## 书籍目录初始化&内容编写

在存书籍的目录下，先建立了`SUMMARY.md`，然后用`gitbook init`，就会生成一系列目录文件。

## 图书输出

### 输出为静态网站

```shell
//在目录文件下
gitbook serve .
gitbook serve ./
```

之后就可以在自己浏览器输入`http://localhost:4000`来查看。

这里你会发现，你在你的图书项目的目录中多了一个名为`_book`的文件目录，而这个目录中的文件，即是生成的静态网站内容。

#### 使用build参数生成到指定目录

1. mkdir outbook
2. cd..,退到上一层目录，即E:\gitbook (如果不，会出错)
3. 然后,E:\gitbook>gitbook build gitbook-studying gitbook-studying/outbook
4. 则在 E:\gitbook\gitbook-studying\outbook下生成了同样的静态html文件

### 输出pdf

输出pdf文件步骤如下:

1. 由于生成PDF文件依赖于`ebook-convert`，故首先在该处[ebook-convert下载链接](http://calibre-ebook.com/download)点击下载所需要的版本，安装即可;
2. 打开cmd，进入E:\gitbook目录;
3. E:\gitbook>gitbook pdf gitbook-studying gitbook-studying/gitbook入门教程.pdf
4. 则在目录E:\gitbook\gitbook-studying下生成了该pdf文件

然后，你会发现你的目录里多了一个名为`gitbook入门教程.pdf`的文件，就是它了！

## 发布

### 发布到gitbook.com

先在线创建一个书的仓库，然后用git来管理。

1. 首先打开cmd，进入书籍目录，E:\gitbook\gitbook-studying;
2. 运行E:\gitbook\gitbook-studying>`git init`，这里如果git提示错误，则是没配置git的环境变量的path；
3. 将目录的章节文件夹一个个加进，git里，使用`git add 文件夹名`;
4. 接下来，`git commit -m "提交信息(必填，否则出错)"`;
5. 然后，将本地的git 仓库与gitbook.com上远程仓库连接，`git remote add gitbook https://git.gitbook.com/yuzeshan/gitbook-studying.git`(注意:不是github上的git remote add origin git@....);
6. 最后，将本地仓库全部push到远程，`git push -u gitbook master`，以后每次更改，然后add再commit，而第二次push时，直接`git push gitbook master`即可

提交到 GitBook.com 后，书籍就自动发布了，用户就可以通过书籍的地址访问了，例如：[http://yuzeshan.gitbooks.io/gitbook-studying/content/](http://yuzeshan.gitbooks.io/gitbook-studying/content/)

**ps:如果本地没有git初始化过得仓库，则可以将在线建立的仓库，克隆到本地，进行修改，提交，push，简洁步骤如下:**

1.  首先进入想要建立书籍的目录，这里是E:\gitbook\gitbook-studying；
2. 运行命令`git clone https://git.gitbook.com/yuzeshan/gitbook-studying.git`;
3. 然后，通过之前介绍的书籍编辑:gitbook init,gitbook serve 等方法，编辑好书籍后，再用git命令add commit添加提交书籍目录文件；
4. 最后，`git push gitbook master`即可。

### 发布到github仓库

1. 首先在github上建立相应的仓库。
2. 创建一个新的文件，在里面运行命令 `$git clone git@github.com:yuzeshan/gitbook-studying.git`。
3. 进入到这个`gitbook-studying`文件里。
4. 到Gitbook.com页面，将书籍的 Git 项目设置为 GitHub 上的项目。
5. 保存后，可以看到之前不可点击的 "Add a deployment webhook" 按钮已经可以点击了，这个按钮表示：每当用户配置的 GitHub 上的项目更新时，自动更新Gitbook.com书籍
6.  将之前编辑的书籍目录为`E:\gitbook\gitbook-studying`中除.git文件，全部拷贝到克隆的目录中，即`E:\gitbook\gitbook-studying-github\gitbook-studying`中；
7. 将已经编辑好的书籍文件，用git add/commit命令依次添加，提交后;
8. 接下来将书籍仓库与远程github连接到一起，运行命令:`git remote add github https://github.com//yuzeshan/gitbook-studying.git`(注意:并不是`git remote add origin https://github.com:yuzeshan/gitbook-studying.git`,也许不运行此命令也可，因为克隆的文件本身就关联了，未尝试。。。)；
9. 最后，将书籍仓库push到github仓库上，运行命令：`git push -u github master`;
10. git push 命令中的 -u 表示将本地 master 分支的上游分支设置为 github/master，所以以后修改了本地 master 分支后，git push 将推送到 github 上，而非原来的 `git remote add gitbook https://git.gitbook.com/yuzeshan/gitbook-studying.git`。

### 发布到GitHub Pages

在自己的代码仓库里添加一个GitHub  Pages静态文件。

1. 创建一个空仓库
2. 克隆到本地
3. 创建一个新分支`git checkout -b gh-pages`，注意，分支必须为 **gh-pages**。
4. 将分支push到仓库 `git push -u origin gh-pages`。
5. 切换到主分支 `git checkout master`。
6. 克隆 `gh-pages`分支 `git clone -b gh-pages git@github.com:USERNAME/book.git book-end`。这步克隆 `gh-pages`分支并存放在 `book-end`目录中。
7. 而且只能copy，用build会把git信息去掉。