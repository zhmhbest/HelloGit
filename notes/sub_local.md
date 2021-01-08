### 创建本地仓库

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

### 暂存区

#### 添加修改记录到到暂存区

`<filename>`指存在于工作区或本地仓库的文件名称，其不一定存在于文件系统中。

```bash
git add <filename>
```

#### 删除文件并添加修改记录到暂存区

```bash
# 方式1
git rm <filename>

# 方式2
rm ./<filename>
git add <filename>

# 移除暂存区删除记录并恢复文件
git restore --staged <filename>
git restore <filename>
```

#### 移除暂存区的记录

```bash
# 对于首次追踪的文件（其实是取消文件追踪）
git rm --cached <filename>

# 对于已追踪且修改了的文件
git restore --staged <filename>
```

#### 提交暂存区记录到本地仓库

```bash
git commit -m <message>
```

### 仓库状态

```bash
# 绿色：暂存区记录
# 红色：未追踪的文件
git status
```

```txt
Changes to be committed:
        new file:   ?
        deleted:    ?
        modified:   ?

Untracked files:
        ?
```

### 版本管理

#### 版本记录

```bash
# 从最近到最远的显示提交记录（包括作者和日期）
git log

# 精简显示
git log --pretty=oneline

# 指明版本走向（方便查看分支融合情况）
git log --graph

# 查看版本记录（包括被删除的）
git reflog
```

#### 放弃工作区修改

```bash
# 方式1
git restore <filename>

# 方式2
git checkout -- <filename>

# 方式3
git reset HEAD <filename>
```

#### 版本恢复

```bash
# 回退1个版本
git reset --hard HEAD^

# 回退2个版本
git reset --hard HEAD^^

# 回退10个版本
git reset --hard HEAD~10

# 回退到指定版本，参数由`git reflog`获取
git reset --hard <7位地址>
```

### 工作现场

```bash
# 保存工作现场
git stash

# 列出保存的工作现场
git stash list

# 恢复工作现场
git stash pop
```

### 文件差异

```bash
# 工作区与最近本地仓库对比
# git diff HEAD -- <filename>
git diff <filename>

# 对比最近两个本地仓库
git diff HEAD HEAD^ -- <filename>
```

### 分支管理

#### 查看分支

```bash
# 查看本地所有分支
git branch

# 查看本地所有分支（包括指纹）
git branch -v
```

#### 操作分支

```bash
# 拷贝当前分支，创建新分支
git branch <新分支名称>

# 重命名分支
git branch –m <旧分支名称> <新分支名称>

# 删除分支
git branch –d <分支名称>

# 强制删除分支
git branch –D <分支名称>

# 切换分支
git checkout <已存在的分支名称>

# 拷贝当前分支，创建新分支，并切换到
git checkout -b <新分支名称>
```

#### 合并分支

| 冲突情况 | 解决方案 |
| - | - |
| 两个分支对同一个文件做了修改 | 合并后，需要手动修改该文件再做一次提交 |
| 两个分支分别新增或修改了各自的文件 | 合并后，Git会自动再做一次提交 |

```bash
# 快速合并（Fast-forward）指定分支到合并到当前分支
git merge <分支名称> -m <message>

# 禁用快速合并（合并后重新做一次新的提交）
git merge --no-ff <分支名称> -m <message>

# 查看已合并、未合并的分支
git branch --merged
git branch --no-merged
```

#### 变基合并

将并行开发的分支合并到原分支

```bash
# 将当前分支改动合并到指定分支
git rebase <分支名称>

# 当发生冲突时，可在修改冲突后继续或放弃
git rebase --continue
git rebase --abort
```

测试demo

```bash
# 原始分支
mkdir test
pushd test
git init
echo A>A.txt
git add .
git commit -m A
git log --pretty=oneline

# 拷贝分支
git branch mywork

# 修改master
echo B>>A.txt
git add .
git commit -m B
git log --pretty=oneline

# 修改mywork
git checkout mywork
echo C>C.txt
git add .
git commit -m C
git log --pretty=oneline

# 变基合并
git rebase master
git log --pretty=oneline
more A.txt
more C.txt

# 删除测试环境
popd
rm -rf ./test
```
