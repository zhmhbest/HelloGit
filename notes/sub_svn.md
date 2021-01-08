
#### SVN仓库结构

```txt
仓库地址
├─branches          项目分支
│  ├─A
│  └─B
├─tags              发布的版本
│  ├─1.0
│  └─1.1
└─trunk             主版本
    └─project
```

#### 从SVN服务器克隆项目

```bash
# 克隆到本地
git svn clone [-r <开始提交记录>:<结束提交记录>] [--prefix=svn/] <仓库地址|分支地址>

# 克隆最新到本地
git svn clone -r HEAD --prefix=svn/ <仓库地址|分支地址>
```

#### 从SVN服务器上获取代码

```bash
git svn rebase
```

#### 提交本地修改到SVN服务器

```bash
git svn rebase
git svn dcommit
```
