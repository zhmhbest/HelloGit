<link rel="stylesheet" href="https://zhmhbest.gitee.io/hellomathematics/style/index.css">
<script src="https://zhmhbest.gitee.io/hellomathematics/style/index.js"></script>

# [HelloGit](https://github.com/zhmhbest/HelloGit)

[TOC]

## 准备工作

<!-- ### Download
	- [Download Git](https://git-scm.com/downloads/)
	- [Download SourceTree](https://www.sourcetreeapp.com/)
-->

### 环境

安装[Cygwin](https://cygwin.com/install.html)并配置环境变量`CYGWIN_HOME`。

#### 添加可执行文件

以管理员身份执行以下命令。

```batch
REM Batch
ECHO @SET PATH=^%CYGWIN_HOME^%\bin;^%CYGWIN_HOME^%\usr\local\bin;^%PATH^%>%SystemRoot%\bash.cmd
ECHO @^"^%CYGWIN_HOME^%\bin\bash.exe^" ^%*>>%SystemRoot%\bash.cmd
```

#### 添加包管理器

```bash
# Bash
dumpDir=/tmp/dump$RANDOM; mkdir ${dumpDir}; pushd ${dumpDir}
wget https://github.com/transcode-open/apt-cyg/archive/master.zip
unzip master.zip; mv './apt-cyg-master/apt-cyg' '/bin/apt-get'
popd; rm -rf ${dumpDir}
apt-get list
```

#### 安装Git

```bash
# Bash
apt-get install git git-svn
```

#### 修复Windows下VSCode版本管理不可用

下载[64-bit Git for Windows Portable](https://git-scm.com/download/win)并运行以下命令

```batch
@FOR /F "usebackq" %f in (`DIR /A:-D /B ".\PortableGit-*.7z.exe"`) DO (SET PACKAGE=%CD%\%f)
"%ProgramFiles%\7-Zip\7z.exe" x -o"%CYGWIN_HOME%" "%PACKAGE%" cmd mingw64
IF NOT EXIST "%ProgramFiles%\Git" MKDIR "%ProgramFiles%\Git"
IF NOT EXIST "%ProgramFiles%\Git\cmd" MKLINK /J "%ProgramFiles%\Git\cmd" "%CYGWIN_HOME%\cmd"
```

### 个人信息

<!-- 
zhmhbest
zhmhbest@gmail.com
-->

```bash
git config --global user.name "YourName"
git config --global user.email "YourName@gmail.com"
more ~/.gitconfig
```

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

### SVN

@import "sub_svn.md"
