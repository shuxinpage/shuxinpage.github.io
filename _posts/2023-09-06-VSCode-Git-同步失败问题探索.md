---
title: "VSCode中Git同步失败问题探索"
layout: post
---
## 时间线

2023-09-26 CT：问题解决，解决方案记录在案。
2023-09-06 CT：问题记录，文章发布，开始探索解决方案。

## 问题描述

近日，在使用vscode进行博客编辑时，发现无法同步到GitHub，报错如下：

```linux
> git push origin master:master
remote: Invalid username or password.
fatal: Authentication failed for
```
经过搜索后发现可能与github开启了Duo Authentication，即两步验证有关。后续将尝试通过获取github token，并给vscode授权的方式解决。

## 解决方法

如果已打开2FA Authentication，可通过以下方式解决。（如果没打开，那就打开2FA Authentication吧，百利无一害）

1. 创建Personal Access Token，可参考[Github官方教程](https://docs.github.com/en/authentication/keeping-your-account-and-data-secure/managing-your-personal-access-tokens)

2. 得到Access Token后，在VS Code Terminal中运行下属命令，为VS Code客户端赋权：

```linux
git remote set-url origin https://<TOKEN>@github.com/<user_name or organization_name>/<repo_name>.git
```

将该命令行中进行以下替换：
    1. "<TOKEN>"替换为自己的Access Token
    2. "<user_name>"替换为自己的github用户名，注意是用户名，不是显示的名字。
    3. "<repo_name>"替换为推送的repository的名称

运行后应该就可以顺利通过VS Code进行Git同步了。

## 引用&致谢

该问题解决方法得到了以下网页或论坛内容的帮助，感谢相应的网友与问题回答者：

https://stackoverflow.com/questions/32639393/error-message-authentication-failed-on-the-git-remote
answered by *aleksejjj*, edited by *Meena Chaudhary*