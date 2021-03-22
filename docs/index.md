<link rel="stylesheet" href="https://zhmhbest.gitee.io/hellomathematics/style/index.css">
<script src="https://zhmhbest.gitee.io/hellomathematics/style/index.js"></script>

# [HelloGit](https://github.com/zhmhbest/HelloGit)

[TOC]

## 准备工作

@import "sub_setup.md"

## 本地使用

@import "sub_local.md"

## 云端联动

### 常用云平台

- [Github](https://github.com)
- [Gitee](https://gitee.com/)
- SVN: 内网部署

### 创建密钥

```bash
# Bash
ssh-keygen -t rsa -C "YourName@gmail.com"
ls -al ~/.ssh/
# id_rsa     : 私钥（个人持有）
# id_rsa.pub : 公钥（公开到云端）
```

### Github

@import "sub_github.md"

### Github-Cli

@import "gh_cli.md"

### SVN

@import "sub_svn.md"
