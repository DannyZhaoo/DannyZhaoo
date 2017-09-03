---
title: 配置客户端git
date: 2017-06-02 18:30:21
tags: git
categories: git
---

配置客户端git，让git可以push和pull

## 设置名字和邮箱地址

```shell
$ git config --global user.name "John Doe"
$ git config --global user.email johndoe@example.com
```

## 生成一个新的ssh秘钥

打开 Git Bash，输入如下命令，然后连续按三个回车即可：

```
ssh-keygen -t rsa -C "your_email@example.com"
```

## 将生成的公钥复制到GitHub

## 测试

```
ssh -T git@github.com
```

输入yes后回车，如果提示中的用户名是你的，说明设置成功。