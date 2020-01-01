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
    
    # 添加到暂存区
    git add <filename>
    git add ...
    # 提交到仓库
    git commit -m <message>

### 查看提交记录

    git log
    #从最近到最远的显示提交记录（包括作者和日期）

    git log --pretty=oneline
    # 精简显示

### 查看已修改和未添加的文件

    git status

### 放弃文件的修改

    git checkout -- <filename>
    # 回到和版本库一样的状态 或
    # 回到添加暂存区后的状态

### 与本地仓库对比文件差异

    git diff <filename>

### 查看版本记录（包括被删除的）

    git reflog

### 版本回退与撤销

    git reset --hard HEAD^
    # 回退1个版本

    git reset --hard HEAD^^
    # 回退2个版本

    git reset --hard HEAD~100
    # 回退100个版本

    git reset --hard <7bitcode>
    # 参数由`git reflog`获取
    # 撤销回退
