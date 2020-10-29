## 云端联动

- [Github](https://github.com)
- [Gitee](https://gitee.com/)

### 为Github添加密钥

#### 新建钥匙

```bash
ssh-keygen -t rsa -C "{email}"

# Generating public/private rsa key pair.
# Enter file in which to save the key (%Userprofile%/.ssh/id_rsa):
# ...
notepad %Userprofile%/.ssh/id_rsa.pub
```

#### 将公钥保存到Github

>[Settings](https://github.com/settings) > [SSH and GPG keys](https://github.com/settings/keys) > [New SSH key](https://github.com/settings/ssh/new)

![](./images/ssh.png)

#### 配置无效问题

使用https时，无法应用ssh密钥。

```bash
# 查看问题是否存在
git remote -v

# origin  https://github.com/<用户名>/<仓库名> (fetch)
# origin  https://github.com/<用户名>/<仓库名> (push)
```

```bash
# 修改连接方式
git remote rm origin
git remote add origin git@github.com:<用户名>/<仓库名>.git
git remote -v
git push -u origin master

# 第一次使用SSH推送会产生警告
# The authenticity of host 'github.com (13.229.188.59)' can't be established.
# RSA key fingerprint is SHA256:nThbg6kXUpJWGl7E1IGOCspRomTxdCARLviKw6E5SY8.
# Are you sure you want to continue connecting (yes/no/[fingerprint])? yes
```

### 从云端克隆一个仓库

```bash
git clone https://github.com/<用户名>/<远程仓库名>.git
```

### 跟踪

#### 本地仓库跟踪远程仓库

```bash
# cd <本地仓库目录>
git remote add origin https://github.com/<用户名>/<远程仓库名>.git
git push -u origin master
```

#### 本地分支跟踪云端分支

```bash
# git push origin master
git branch --set-upstream-to=origin/<远程分支名> <本地分支名>
```

### 云端互传

```bash
# 当前分支推送到远程
# git push origin master
git push origin <远程分支名>

# 当配置远程跟踪后可以直接使用如下命令
git push

# 拉取云端分支到本地并自动合并
git pull origin <远程分支名>
```

### 获取最新远程分支到本地

```bash
git fetch origin master:tmp
git diff tmp
git merge tmp
git branch –d tmp
```

### 远程分支管理

```bash
# 查看云端所有分支
git branch -r

# 查看本地和远程所有分支
git branch -a

# 删除远程分支
git branch –d -r <branchname>
git push origin:<branchname>
```

