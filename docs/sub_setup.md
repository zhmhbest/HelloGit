<!-- ### Download
	- [Download Git](https://git-scm.com/downloads/)
	- [Download SourceTree](https://www.sourcetreeapp.com/)
-->

### 配置Cygwin

下载[Cygwin](https://cygwin.com/install.html)至如下目录

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
- Direct Connection
- User URL = `http://mirrors.aliyun.com/cygwin/`
- View = `Category`
  - 启用`wget`、`unzip`、`vim`、`git`、`git-svn`
- 添加环境变量`CYGWIN_HOME`
- 添加`%CYGWIN_HOME%\bin`到环境变量`PATH`

#### 右键当前目录启动

```batch
REM 以管理员身份运行一个“cmd.exe”窗口
SET REG_ROOT=HKLM\SOFTWARE\Classes\Directory\background\shell
REG ADD "%REG_ROOT%\bashPrompt" /f /ve /t REG_SZ /d "在此处打开 Bash 窗口(&B)"
REG ADD "%REG_ROOT%\bashPrompt" /f /v "Icon" /t REG_SZ /d "%CYGWIN_HOME%\Cygwin-Terminal.ico"
REG ADD "%REG_ROOT%\bashPrompt\command" /f /ve /t REG_SZ /d "\"%CYGWIN_HOME%\bin\mintty.exe\" -c \"%CYGWIN_HOME%\%UserName%\.bash_profile\""
REM REG DELETE "%REG_ROOT%\bashPrompt" /f
```

<!--
#### 添加包管理器

```bash
# 右键“在此处打开 Bash 窗口(B)”
dumpDir=/tmp/dump$RANDOM; mkdir ${dumpDir}; pushd ${dumpDir}
wget https://github.com/transcode-open/apt-cyg/archive/master.zip
unzip master.zip; mv './apt-cyg-master/apt-cyg' '/bin/apt-get'
popd; rm -rf ${dumpDir}
apt-get list
```
-->

### 环境

#### 修复Windows下VSCode版本管理不可用

下载[Git for Windows Portable](https://git-scm.com/download/win)，在当前目录运行命令行并执行以下命令

```batch
REM Batch
@FOR /F "usebackq" %f in (`DIR /A:-D /B ".\PortableGit-*.7z.exe"`) DO (SET PACKAGE=%CD%\%f)
"%ProgramFiles%\7-Zip\7z.exe" x -o"%CYGWIN_HOME%" "%PACKAGE%" cmd mingw64
IF NOT EXIST "%ProgramFiles%\Git" MKDIR "%ProgramFiles%\Git"
IF NOT EXIST "%ProgramFiles%\Git\cmd" MKLINK /J "%ProgramFiles%\Git\cmd" "%CYGWIN_HOME%\cmd"
```

- 添加`%ProgramFiles%\Git\cmd`到环境变量`PATH`

#### 个人信息

<!--
zhmhbest
zhmhbest@gmail.com
-->

```bash
git config --global user.name "YourName"
git config --global user.email "YourName@gmail.com"
```

#### 解决换行符异常

- 在VSCode中搜索`files.eol`设为`\n`；
- 在IDEA中找到`Editor`>`Code Style`>`Line separator`设为`Unix and macOS (\n)`。

```bash
# core.autocrlf = true(提交LF检出CRLF) | false(不转换) | input(提交LF检出不转换)
git config --global core.autocrlf input

# core.safecrlf = true(拒绝提交混合换行符文件) | false(允许) | warn(警告)
git config --global core.safecrlf true
```
