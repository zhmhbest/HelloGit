<link rel="stylesheet" href="https://zhmhbest.gitee.io/hellomathematics/style/index.css">
<script src="https://zhmhbest.gitee.io/hellomathematics/style/index.js"></script>

# [HelloGit](https://github.com/zhmhbest/HelloGit)

[TOC]

## 准备工作

<!-- ### Download
	- [Download Git](https://git-scm.com/downloads/)
	- [Download SourceTree](https://www.sourcetreeapp.com/)
-->

### 配置Cygwin

下载[Cygwin](https://cygwin.com/setup-x86_64.exe)至如下目录

```txt
CYGWIN_HOME:.
├─setup
│      setup-x86_64.exe
│
└─...
```

- 运行`setup-x86_64.exe`
- Install from Internet
- Root Directory = `%CYGWIN_HOME%`
- Local Package Directory = `%CYGWIN_HOME%\setup`
- Use HTTP/FTP Proxy
  - Proxy Host = `.`
  - Could not download mirror sites list
  - 上一步
- Direct Connection
- User URL = `https://mirrors.tuna.tsinghua.edu.cn/cygwin/`
- View = `Category`
  - 启用`wget`
  - 启用`unzip`
- 添加环境变量`CYGWIN_HOME`
- 添加`%CYGWIN_HOME%\bin`到环境变量`PATH`

#### 右键启动

```batch
REM 以管理员身份运行一个“cmd.exe”窗口
SET REG_ROOT=HKLM\SOFTWARE\Classes\Directory\background\shell
reg add "%REG_ROOT%\bashPrompt" /f /ve /t REG_SZ /d "在此处打开 Bash 窗口(&B)"
reg add "%REG_ROOT%\bashPrompt" /f /v "Icon" /t REG_SZ /d "%CYGWIN_HOME%\Cygwin-Terminal.ico"
reg add "%REG_ROOT%\bashPrompt\command" /f /ve /t REG_SZ /d "\"%CYGWIN_HOME%\bin\mintty.exe\" -c \"%CYGWIN_HOME%\%UserName%\.bash_profile\""
```

#### 添加包管理器

```bash
# 右键“在此处打开 Bash 窗口(B)”
dumpDir=/tmp/dump$RANDOM; mkdir ${dumpDir}; pushd ${dumpDir}
wget https://github.com/transcode-open/apt-cyg/archive/master.zip
unzip master.zip; mv './apt-cyg-master/apt-cyg' '/bin/apt-get'
popd; rm -rf ${dumpDir}
apt-get list
```

### 环境

#### 安装Git

```bash
# Bash
apt-get install git git-svn
```

#### 修复Windows下VSCode版本管理不可用

下载[Git for Windows Portable](https://git-scm.com/download/win)，在当前目录运行命令行并执行以下命令

```batch
REM Batch
@FOR /F "usebackq" %f in (`DIR /A:-D /B ".\PortableGit-*.7z.exe"`) DO (SET PACKAGE=%CD%\%f)
"%ProgramFiles%\7-Zip\7z.exe" x -o"%CYGWIN_HOME%" "%PACKAGE%" cmd mingw64
IF NOT EXIST "%ProgramFiles%\Git" MKDIR "%ProgramFiles%\Git"
IF NOT EXIST "%ProgramFiles%\Git\cmd" MKLINK /J "%ProgramFiles%\Git\cmd" "%CYGWIN_HOME%\cmd"
```

#### 个人信息

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
