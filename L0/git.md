
## 基本概念
### **工作区、暂存区和 Git 仓库区**

- 工作区（Working Directory）： 当我们在本地创建一个 Git 项目，或者从 GitHub 上 clone 代码到本地后，项目所在的这个目录就是“工作区”。这里是我们对项目文件进行编辑和使用的地方。
    
- 暂存区（Staging Area）： 暂存区是 Git 中独有的一个概念，位于 .git 目录中的一个索引文件，记录了下一次提交时将要存入仓库区的文件列表信息。使用 git add 指令可以将工作区的改动放入暂存区。
    
- 仓库区 / 本地仓库（Repository）： 在项目目录中，.git 隐藏目录不属于工作区，而是 Git 的版本仓库。这个仓库区包含了所有历史版本的完整信息，是 Git 项目的“本体”。
### 文件状态

文件在 Git 工作区中的状态可以是：

- 已跟踪：文件已被纳入版本控制，根据其是否被修改，可以进一步分为未修改（Unmodified）、已修改（Modified）或已暂存（Staged）。# git add之后的文件
- 未跟踪：文件存在于工作目录中，但还没被纳入版本控制，也未处于暂存状态。

|状态|未跟踪Untrack|未修改Unmodified|已修改Modified|已暂存Staged|
|---|---|---|---|---|
|说明|"即新建的文件，并未被git所管理"|"文件的内容没有写入修改，已经被git管理"|"文件的内容被写入修改，已经被git管理"|"文件的内容暂存，已经被git管理"|

### 分支

分支是 Git 的一大特性，支持轻量级的分支创建和切换。Git 鼓励频繁使用分支和合并，使得并行开发和错误修正更为高效。
比如main分支，以及其他自创分支 还有dev开发分支

|特性|描述|
|---|---|
|分布式架构|与集中式版本控制系统不同，Git 在每个开发者的机器上都存有完整的代码库副本，包括完整的历史记录。这种分布式的特性增强了数据的安全性和获取效率。|
|分支管理|Git 的分支管理功能非常灵活，支持无缝切换到不同的开发线路（分支），并允许独立开发、测试新功能，最终通过合并操作将这些功能稳定地集成到主项目中。|
|快照系统|Git 通过快照而非差异比较来管理数据。每次提交更新时，Git 实际上是在存储一个项目所有文件的快照。如果文件没有变化，Git 只是简单地链接到之前存储的文件快照。|

## 配置

全局设置（不推荐，建议一个项目一个本地设置）
```bash
git config --global user.name "Your Name"
git config --global user.email "your.email@example.com"
```
本地设置
```bash
git config --local user.name "Your Name"
git config --local user.email "your.email@example.com"
```
#### 查看配置

```bash
git config --local --list
fatal: --local can only be used inside a git repository

git config --local --list
"""
core.repositoryformatversion=0
core.filemode=false
core.bare=false
core.logallrefupdates=true
core.symlinks=false
core.ignorecase=true
remote.origin.url=http://xxx/xxx/xiaoshuo.git
remote.origin.fetch=+refs/heads/*:refs/remotes/origin/*
branch.main.remote=origin
branch.main.merge=refs/heads/main
user.name=xxx
user.email=xxx.com
"""
```

## 简易操作

### 入门四部曲

在Git的日常使用中，下面四步曲是常用的流程，尤其是在团队协作环境中。

- **添（Add）**
    
    - **命令**：`git add <文件名>` 或 `git add .`
    - **作用**：将修改过的文件添加到本地暂存区（Staging Area）。这一步是准备阶段，你可以选择性地添加文件，决定哪些修改应该被包括在即将进行的提交中。
- **提（Commit）**
    
    - **命令**：`git commit -m '描述信息'`
    - **作用**：将暂存区中的更改提交到本地仓库。这一步是将你的更改正式记录下来，每次提交都应附带一个清晰的描述信息，说明这次提交的目的或所解决的问题。
- **拉（Pull）**
    
    - **命令**：`git pull`
    - **作用**：从远程仓库拉取最新的内容到本地仓库，并自动尝试合并到当前分支。这一步是同步的重要环节，确保你的工作基于最新的项目状态进行。在多人协作中，定期拉取可以避免将来的合并冲突。
- **推（Push）**
    
    - **命令**：`git push`
    - **作用**：将本地仓库的更改推送到远程仓库。这一步是共享你的工作成果，让团队成员看到你的贡献。

帮助团队成员有效地管理和同步代码，避免工作冲突，确保项目的顺利进行。正确地使用这些命令可以极大地提高开发效率和协作质量。


### 常用指令

| 指令             | 描述                    |
| -------------- | --------------------- |
| `git config`   | 配置用户信息和偏好设置           |
| `git init`     | 初始化一个新的 Git 仓库        |
| `git clone`    | 克隆一个远程仓库到本地           |
| `git status`   | 查看仓库当前的状态，显示有变更的文件    |
| `git add`      | 将文件更改添加到暂存区           |
| `git commit`   | 提交暂存区到仓库区             |
| `git branch`   | 列出、创建或删除分支            |
| `git checkout` | 切换分支或恢复工作树文件          |
| `git merge`    | 合并两个或更多的开发历史          |
| `git pull`     | 从另一仓库获取并合并本地的版本       |
| `git push`     | 更新远程引用和相关的对象          |
| `git remote`   | 管理跟踪远程仓库的命令           |
| `git fetch`    | 从远程仓库获取数据到本地仓库，但不自动合并 |

更新链接
```bash
git remote set-url origin http://xxx/xxx/xiaoshuo.git
```

```bash
git clone https://github.com/dblab0/Tutorial.git # 克隆项目
Cloning into 'Tutorial'...
remote: Enumerating objects: 7127, done.
remote: Counting objects: 100% (1033/1033), done.
remote: Compressing objects: 100% (162/162), done.
remote: Total 7127 (delta 945), reused 879 (delta 871), pack-reused 6094 (from 1)
Receiving objects: 100% (7127/7127), 68.77 MiB | 13.75 MiB/s, done.
Resolving deltas: 100% (2911/2911), done.
```

```bash
git branch -a  # 列出分支
* camp3
  remotes/origin/HEAD -> origin/camp3
  remotes/origin/camp1
  remotes/origin/camp2
  remotes/origin/camp2_en
  remotes/origin/camp3
  remotes/origin/camp4
  remotes/origin/class
  remotes/origin/revert-1303-camp3_2393
```

```bash
git checkout -b class origin/class  # 切换到分支class
branch 'class' set up to track 'origin/class'.
Switched to a new branch 'class'

git checkout -b class_2569
Switched to a new branch 'class_2569'
```
### 进阶指令

| 指令                | 描述                          |
| ----------------- | --------------------------- |
| `git stash`       | 暂存当前工作目录的修改，以便可以切换分支        |
| `git cherry-pick` | 选择一个提交，将其作为新的提交引入           |
| `git rebase`      | 将提交从一个分支移动到另一个分支            |
| `git reset`       | 重设当前 HEAD 到指定状态，可选修改工作区和暂存区 |
| `git revert`      | 通过创建一个新的提交来撤销之前的提交          |
| `git mv`          | 移动或重命名一个文件、目录或符号链接，并自动更新索引  |
| `git rm`          | 从工作区和索引中删除文件                |
