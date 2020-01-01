# HelloGit

- [Download Git](https://git-scm.com/downloads/)

## 配置用户名

    git config --global user.name "zhmhbest"
    git config --global user.email "zhmhbest@gmail.com"
    # notepad %Userprofile%\.gitconfig

## 本地使用

### 创建本地仓库
    
    mkdir <repositorie>
    cd <repositorie>
    type nul>.gitignore
    git init

### 提交文件到仓库

    # 添加文件到暂存区
    git add <filename>
    git add ...

    # 提交删除
    git rm <filename>

    # 提交修改到本地仓库（创建版本记录）
    git commit -m <message>

### 查看提交记录

    #从最近到最远的显示提交记录（包括作者和日期）
    git log

    # 精简显示
    git log --pretty=oneline

    # 指明版本走向（方便查看分支融合情况）
    git log --graph --pretty=oneline

### 查看工作区状态

    # 红色：已修改或未添加文件
    # 绿色：已添加到暂存区的文件
    git status

### 放弃文件的修改

    # 放弃 暂存区修改
    # git reset HEAD <filename>
    git restore --staged <filename> 

    # 放弃 工作区修改
    git checkout -- <filename>

### 对比文件差异

    # 工作区与最近本地仓库对比
    # git diff HEAD -- <filename>
    git diff <filename>

    # 对比最近两个本地仓库
    git diff HEAD HEAD^ -- <filename>

### 查看版本记录（包括被删除的）

    git reflog

### 版本回退与撤销

    # 回退1个版本
    git reset --hard HEAD^

    # 回退2个版本
    git reset --hard HEAD^^

    # 回退100个版本
    git reset --hard HEAD~100

    # 回退到指定版本，参数由`git reflog`获取
    git reset --hard <7bitcode>

### 工作现场

    # 保存工作现场
    git stash

    # 列出保存的工作现场
    git stash list

    # 恢复工作现场
    git stash pop

## 分支管理

### 查看分支
    # 查看本地所有分支
    git branch
    
    # 查看本地所有分支（包括指纹）
    git branch -v

    # 查看云端所有分支
    git branch -vr

    # 查看本地和远程所有分支
    git branch -va

### 创建分支

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

### 合并分支

    # 快速合并（Fast-forward）指定分支到当前分支
    git merge <branchname>

    # 禁用快速合并（合并后重新做一次新的提交）
    git merge --no-ff <branchname> -m <message>

#### 冲突类型

1. 两个分支对同一个文件做了修改
    - 合并后，需要手动修改该文件并做一次提交。
2. 两个分支分别新增了各自的文件
    - 合并后，Git会自动再做一次提交。
 
## 云端联动

- [Github](https://github.com)
- [Gitee](https://gitee.com/)


