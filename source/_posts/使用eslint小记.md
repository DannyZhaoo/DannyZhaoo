---
title: 使用eslint小记
date: 2017-10-17 17:34:53
tags: 开发流程/部署
categories: Eslint
---

# 问题

在工作中，每个队伍都有一套编程规则，方便大家看懂彼此的代码。但是，我看代码就有容易把自己的代码规则和别人的搞混，有时候也会记错。

而今天， 我发现了**Eslint**。这个在写代码的时候真的很方便，会给出提示，但是前提是自己得会配置。所以，把自己踩得的都记一下。

# 配置

1. 下载eslint

```shell
npm install -g eslint
eslint --init
```

2. 写eslint的配置文件。

推荐一个github，这个上面列出的eslint配置对**前端**是个很好的参考。

```shell
git clone git@github.com:AlloyTeam/eslint-config-alloy.git
```

3. 在vs code上的配置

最重要的地方，指明eslint配置的地方。

```shell
{
    "eslint.options": {
        "eslintConfig": "/Users/workspace/panama-2-m-fe/.eslintrc.json"
    }
}
```

# 提示

1. VS code上提示哪个配置是invalid，那就把那部分给删掉，这就可能是你的eslint版本太低了，不支持这个。（我就一直踩这个坑，还不知道原因）
2. VS code在开始的时候提示*Definition for rule 'switch-colon-spacing' was not found* 这个是你的eslint版本不支持这个。
3. 不要配置autoFixOnSave，这样最起码代码还在自己控制中，否则一旦规则写错了，你就倒霉了。