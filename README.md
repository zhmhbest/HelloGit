# HelloGit

- [下载](https://git-scm.com/downloads/)

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
