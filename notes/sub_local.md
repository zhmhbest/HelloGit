## Local

### Init

```batch
REM Batch
type nul>.gitignore
git init
```

```bash
# Bash
touch .gitignore
git init
```

### Status

```bash
# 绿色：暂存区的修改记录（增、删、改）
# 红色：已修改但未添加或未添加文件
git status
```

```txt
Changes to be committed:
  (use "git restore --staged <file>..." to unstage)
        new file:   ?
        deleted:    ?
        modified:   ?

Untracked files:
  (use "git add <file>..." to include in what will be committed)
        ?
```

### Stage

```bash
# 添加文件到Stage
git add <filename>

# 提交删除到Stage
git rm <filename>

# 放弃在Stage的修改
git restore --staged <filename>

# 提交修改到本地仓库（创建版本记录）
git commit -m <message>
```

### Log

```bash
# 从最近到最远的显示提交记录（包括作者和日期）
git log

# 精简显示
git log --pretty=oneline

# 指明版本走向（方便查看分支融合情况）
git log --graph --pretty=oneline

# 查看版本记录（包括被删除的）
git reflog
```

### Diff

```bash
# 工作区与最近本地仓库对比
# git diff HEAD -- <filename>
git diff <filename>

# 对比最近两个本地仓库
git diff HEAD HEAD^ -- <filename>
```

### Restore

```bash
# 放弃 工作区修改
git restore <filename>

# 放弃 工作区修改
git checkout -- <filename>

# 放弃 工作区修改
git reset HEAD <filename>
```

```bash
# 回退1个版本
git reset --hard HEAD^

# 回退2个版本
git reset --hard HEAD^^

# 回退100个版本
git reset --hard HEAD~100

# 回退到指定版本，参数由`git reflog`获取
git reset --hard <7bitcode>
```

### Stash

```bash
# 保存工作现场
git stash

# 列出保存的工作现场
git stash list

# 恢复工作现场
git stash pop
```

## 分支管理

### 查看分支

```bash
# 查看本地所有分支
git branch

# 查看本地所有分支（包括指纹）
git branch -v
```

### 分支管理

```bash
# 拷贝当前分支，创建新分支
git branch <branchname>

# 重命名分支
git branch –m <oldname> <newname>

# 删除分支
git branch –d <branchname>

# 强制删除分支
git branch –D <branchname>

# 切换分支
# git checkout master
git checkout <branchname>

# 拷贝当前分支，创建新分支，并切换到
git checkout -b <branchname>
```

### 合并分支

| 冲突情况 | 解决方案 |
| - | - |
| 两个分支对同一个文件做了修改 | 合并后，需要手动修改该文件再做一次提交 |
| 两个分支分别新增了各自的文件 | 合并后，Git会自动再做一次提交 |

```bash
# 快速合并（Fast-forward）指定分支到当前分支
git merge <branchname> -m <message>

# 禁用快速合并（合并后重新做一次新的提交）
git merge --no-ff <branchname> -m <message>

# 查看已合并、未合并的分支
git branch --merged
git branch --no-merged
```
