
>[下载 GitHub CLI](https://cli.github.com/)

#### 登录

```bash
gh auth login
# GitHub.com
# SSH
# %UserProfile%\.ssh\id_rsa.pub
# Paste an authentication token
# https://github.com/settings/tokens
```

#### 仓库操作

```bash
# 列出所有仓库
gh repo list

# 查看仓库README
gh repo view <用户名>/<仓库名>
gh repo view <仓库名>

# 创建新仓库
gh repo create <新仓库名>
```
