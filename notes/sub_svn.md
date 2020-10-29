
#### 从SVN服务器克隆项目

```bash
# 从SVN仓库克隆一个分支到本地
git svn clone https://<Host>/svn/repos/<ProjectName>/branches/<BranchName> --prefix=svn/

# 从SVN仓库克隆所有分支到本地
git svn clone https://<Host>/svn/repos/<ProjectName> --prefix=svn/
```

#### 从SVN服务器上获取代码

```bash
# 相当于 git pull
# 相当于 svn update
git svn rebase
```

#### 提交本地修改到SVN服务器

```bash
# 相当于 git push
# 相当于 svn commit
git svn rebase
git svn dcommit
```
