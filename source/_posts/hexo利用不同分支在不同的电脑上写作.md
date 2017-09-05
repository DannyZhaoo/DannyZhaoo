---
title: hexo利用不同分支在不同的电脑上写作
date: 2017-09-04 18:20:19
tags: 
- git
- hexo 
categories: 开发工具
---

我在面对这个问题的时候，其实考虑过放弃GitHub Page，去转而用更方便的现成的博客平台。然而经过对比，还有结合我这个写博客的特点，其实还是用**markdown**最方便。

还有毕竟自己是个程序员，什么都是自己可控的，这对自己还是有不小的吸引力的。

当时我的情况是：

我一直在windows上写东西，但是最近我到公司发了新的电脑，我在GitHub Page上的是用hexo生成后的代码。这样就算我clone下来，也没有自己原来配置的内容。

这样的情况下，我在网上查到可以用这个仓库的另外一个分支保存源码的方式。我就照着做了，大概用了两三个小时，踩了不少坑。

1. 在本地新建一个分支。

2. 把这个分支推到GitHub上。
   当然在这个之前，你得确保把这个文件夹都`git init`过了，而且添加了`git remote`。

3. 把这个新建的分支设置成默认分支。


在新的电脑上

1. 从clone这个仓库
2. 用npm下载hexo-cli，hexo，hexo-deployer-git
```shell
npm install hexo-cli -g
npm install hexo
npm install
npm install hexo-deployer-git –-save
```
3. 切记下载主题git clone https://github.com/iissnan/hexo-theme-next themes/next
4. 按照需要**设置主题**，这个不会在git上有记录。

最后切记自己遇到问题，不要一切就真的推翻重做，其实再查查就成功了。或者倒退几步，但是真的不用全部重新来过。

这个步骤是我后来总结的，我自己做的时候一直有问题，然后就一直查。而且每个电脑环境不同，遇到的问题也不同，一定不要全部推翻重做！！！






