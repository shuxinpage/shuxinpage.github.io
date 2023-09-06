---
title: "VSCode中Git同步失败问题探索"
layout: post
---
## 时间线

2023-09-06 CT：问题记录，文章发布，开始探索解决方案。

## 问题描述

近日，在使用vscode进行博客编辑时，发现无法同步到GitHub，报错如下：

```linux
> git push origin master:master
remote: Invalid username or password.
fatal: Authentication failed for
```
经过搜索后发现可能与github开启了Duo Authentication，即两步验证有关。后续将尝试通过获取github token，并给vscode授权的方式解决。
