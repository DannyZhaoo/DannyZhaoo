---
title: Latex入门笔记
date: 2017-06-06 20:20:23
tags: 
- Latex
categories: 软技能
---

因为Latex的排版一直为人称道，而近期我们需要写一个指导手册，所以就学习用一下Latex。

## 下载安装

在ctex.org下载ctex套装(203Mb或1.3Gb)（含MikTeX及WinEdt），等着下载好了之后，就一步一步安装。

## 写第一个文档

主要是使用界面较为简单的**TeXworks**。

```latex
\documentclass{article}
\begin{document}
hello,world
\end{document} 
```

此处的第一行 `\documentclass{article}` 中包含了一个控制序列（或称命令/标记）。所谓控制序列，是以反斜杠`\`开头，以第一个**空格或非字母** 的字符结束的一串文字，他们并不被输出，但是他们会影响输出文档的效果。这里的控制序列是 `documentclass`，它后面紧跟着的 `{article}` 代表这个控制序列有一个必要的参数，该参数的值为 `article`。这个控制序列的作用，是调用名为 “article” 的文档类。

尝试输出**中文**

```latex
\documentclass[UTF8]{ctexart}
\begin{document}
你好，世界！
\end{document} 
```

可以如愿输出中文，ps:用latex输出中文真是不容易！！！

相较于之前，这份代码有些细微的差别:

> 1. 文档从`article`变为`ctextart`;
> 2. 增加了文档累选项`UTF8`。

## 作者、标题、日期

```latex
\documentclass[UTF8]{ctexart}
\title{你好，world!}
\author{Liam}
\date{\today}
\begin{document}
\maketitle
你好，world!
\end{document}
```

在 `document` 环境中，除了原本的`你好，world!`，还多了一个控制序列 `maketitle`。这个控制序列能将在导言区中定义的标题、作者、日期 按照预定的格式展现出来。

## 章节和段落

```latex
\documentclass[UTF8]{ctexart}
\title{你好，world!}
\author{Liam}
\date{\today}
\begin{document}
\maketitle
\section{你好中国}
中国在East Asia.
\subsection{Hello Beijing}
北京是capital of China.
\subsubsection{Hello Dongcheng District}
\paragraph{Tian'anmen Square}
is in the center of Beijing
\subparagraph{Chairman Mao}
is in the center of 天安门广场。
\subsection{Hello 山东}
\paragraph{山东大学} is one of the best university in 山东。
\end{document}
```

在文档类 `article`/`ctexart` 中，定义了五个控制序列来调整行文组织结构。他们分别是

- `\section{·}`
- `\subsection{·}`
- `\subsubsection{·}`
- `\paragraph{·}`
- `\subparagraph{·}`

> 在`report`/`ctexrep`中，还有`\chapter{·}`；在文档类`book`/`ctexbook`中，还定义了`\part{·}`。

## 插入目录

```latex
\documentclass[UTF8]{ctexart}
\title{你好，world!}
\author{Liam}
\date{\today}
\begin{document}
\maketitle
\tableofcontents  %插入的位置
\section{你好中国}
中国在East Asia.
\subsection{Hello Beijing}
北京是capital of China.
\subsubsection{Hello Dongcheng District}
\paragraph{Tian'anmen Square}
is in the center of Beijing
\subparagraph{Chairman Mao}
is in the center of 天安门广场。
\subsection{Hello 山东}
\paragraph{山东大学} is one of the best university in 山东。
\end{document}
```

如果交换 `\maketitle` 和 `\tableofcontents` 的顺序，那么下面所有的内容全部就都变成了目录的内容了。而不是自动生成。

## 插入图片

在 LaTeX 中插入图片，有很多种方式。最好用的应当属利用 `graphicx` 宏包提供的 `\includegraphics` 命令。比如你在你的 TeX 源文件同目录下，有名为 `a.jpg` 的图片，你可以用这样的方式将它插入到输出文档中：

```
\documentclass{article}
\usepackage{graphicx}
\begin{document}
\includegraphics{a.jpg}
\end{document}

```

图片可能很大，超过了输出文件的纸张大小，或者干脆就是你自己觉得输出的效果不爽。这时候你可以用 `\includegraphics` 控制序列的可选参数来控制。比如

```
\includegraphics[width = .8\textwidth]{a.jpg}

```

这样图片的宽度会被缩放至页面宽度的百分之八十，图片的总高度会按比例缩放。

> `\includegraphics` 控制序列还有若干其他的可选参数可供使用，一般并用不到。感兴趣的话，可以去查看[该宏包的文档](http://texdoc.net/texmf-dist/doc/latex/graphics/graphicx.pdf)。

插图和表格通常需要占据大块空间，所以在文字处理软件中我们经常需要调整他们的位置。`figure` 和 `table` 环境可以自动完成这样的任务；这种自动调整位置的环境称作浮动体(float)。我们以 `figure` 为例。

```
\begin{figure}[htbp]
\centering
\includegraphics{a.jpg}
\caption{有图有真相}
\label{fig:myphoto}
\end{figure}

```

“htbp” 选项用来指定插图的理想位置，这几个字母分别代表here, top, bottom, float page，也就是就这里、页顶、页尾、浮动页(专门放浮动体的单独页面) 。`\centering` 用来使插图居中；`\caption` 命令设置插图标题，LaTeX 会自动给浮动体的标题加上编号。注意 `\label` 应该放在标题命令之后。

## 版面设置

### 页边距

设置页边距，推荐使用 `geometry` 宏包。可以在[这里](http://texdoc.net/texmf-dist/doc/latex/geometry/geometry.pdf)查看它的说明文档。

比如我希望，将纸张的长度设置为 20cm、宽度设置为 15cm、左边距 1cm、右边距 2cm、上边距 3cm、下边距 4cm，可以在导言区加上这样几行：

```
\usepackage{geometry}
\geometry{papersize={20cm,15cm}}
\geometry{left=1cm,right=2cm,top=3cm,bottom=4cm}

```

### 页眉页脚

设置页眉页脚，推荐使用 `fancyhdr` 宏包。可以在[这里](http://texdoc.net/texmf-dist/doc/latex/fancyhdr/fancyhdr.pdf)查看它的说明文档。

比如我希望，在页眉左边写上我的名字，中间写上今天的日期，右边写上我的电话；页脚的正中写上页码；页眉和正文之间有一道宽为 0.4pt 的横线分割，可以在导言区加上如下几行：

```
\usepackage{fancyhdr}
\pagestyle{fancy}
\lhead{\author}
\chead{\date}
\rhead{152xxxxxxxx}
\lfoot{}
\cfoot{\thepage}
\rfoot{}
\renewcommand{\headrulewidth}{0.4pt}
\renewcommand{\headwidth}{\textwidth}
\renewcommand{\footrulewidth}{0pt}

```

### 首行缩进

`CTeX` 宏集已经处理好了首行缩进的问题（自然段前空两格汉字宽度）。

> 不使用 `CTeX` 宏集（使用 `xeCJK` 宏包）的话，请遵照以下提示操作。
>
> 中国人写文章，习惯每一段的段首都空出两个中文汉字的长度。美国人没有这个习惯，他们每一小节的段首都顶格。为了解决这个问题，我们可以在导言区调用 `\usepackage{indentfirst}`.
>
> 就算是这样，首行缩进的长度，仍然不符合中国人的习惯。我们可以在导言区添加这样的控制序列 `\setlength{\parindent}{\ccwd}` 来调整首行缩进的大小。这里的 `\ccwd` 是当前字号下一个中文汉字的宽度。

### 行间距

我们可以通过 `setspace`宏包提供的命令来调整行间距。比如在导言区添加如下内容，可以将行距设置为字号的 1.5 倍：

```
\usepackage{setspace}
\onehalfspacing

```

具体可以查看该宏包的[文档](http://texdoc.net/texmf-dist/doc/latex/setspace/README)。

> 请注意用词的差别：
>
> - 行距是字号的 1.5 倍；
> - 1.5 倍行距。
>
> 事实上，这不是设置 1.5 倍行距的正确方法，请参考：[http://liam0205.me/2013/10/17/LaTeX-Linespace/](http://liam0205.me/2013/10/17/LaTeX-Linespace/)

### 段间距

我们可以通过修改长度 `\parskip` 的值来调整段间距。例如在导言区添加以下内容

```
\addtolength{\parskip}{.4em}

```

则可以在原有的基础上，增加段间距 0.4em。如果需要减小段间距，只需将该数值改为负值即可。