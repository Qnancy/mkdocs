# Git

!!! summary "写在前头"

    怎么会有人现在还不会Git啊，别骂了就是我（
    记录一下自己的补天吧    

### 工作原理 / 流程
!!! info ""
    ![](1.png)


+ Workspace：工作区   

+ Index / Stage：暂存区

+ Repository：仓库区（或本地仓库） 

+ Remote：远程仓库

### 常用命令
!!! info "万能公式"

    **本地没有内容**

    1. 在Github上建仓库，获取仓库的 http / SSH
    2. 从远程将仓库克隆到本地
        + ```git clone <repo-url>``` 

    3. 代码完成修改后将修改添加到暂存区
        + ```git add -A   # 添加所有修改 ```
        + ```git add .    # 添加当前目录下的修改 ```
        + ```git add <file> # 添加指定文件的修改```
    4. 提交修改
        + ```git commit -m "Write commit message here."```

    5. 提交到远程仓库
        + ```git push origin main```
    
    **本地已有内容**
    
    1. cd 到本地目录下
    2. ```git init # 把这个目录变成git可以管理的仓库```
    3. 在本地创建了一个Git仓库后，再在github创建一个Git仓库
    4. 关联远程库
        + ```git remote add origin <repo-url>```
        + ```git branch -M main```
        + ```git push -u origin main```

            > 由于远程库是空的，我们第一次推送master分支时，加上了 –u参数，Git不但会把本地的master分支内容推送到远程新的master分支，还会把本地的master分支和远程的master分支关联起来，在以后的推送或者拉取时就可以简化命令


#### 配置

```shell
# 显示当前的Git配置
$ git config --list

# 编辑Git配置文件
$ git config -e [--global]

# 设置提交代码时的用户信息
$ git config [--global] user.name "[name]"
$ git config [--global] user.email "[email address]"
```

#### 增加/删除文件

```shell
# 添加指定文件到暂存区
$ git add [file1] [file2] ...

# 添加指定目录到暂存区，包括子目录
$ git add [dir]

# 添加当前目录的所有文件到暂存区
$ git add .

# 添加每个变化前，都会要求确认
# 对于同一个文件的多处变化，可以实现分次提交
$ git add -p

# 删除工作区文件，并且将这次删除放入暂存区
$ git rm [file1] [file2] ...

# 停止追踪指定文件，但该文件会保留在工作区
$ git rm --cached [file]

# 改名文件，并且将这个改名放入暂存区
$ git mv [file-original] [file-renamed]
```

#### 代码提交

```shell
# 提交暂存区到仓库区
$ git commit -m [message]

# 提交暂存区的指定文件到仓库区
$ git commit [file1] [file2] ... -m [message]

# 提交工作区自上次commit之后的变化，直接到仓库区
$ git commit -a

# 提交时显示所有diff信息
$ git commit -v

# 使用一次新的commit，替代上一次提交
# 如果代码没有任何新变化，则用来改写上一次commit的提交信息
$ git commit --amend -m [message]

# 重做上一次commit，并包括指定文件的新变化
$ git commit --amend [file1] [file2] ...
```

#### 分支

```shell
# 列出所有本地分支
$ git branch

# 列出所有远程分支
$ git branch -r

# 列出所有本地分支和远程分支
$ git branch -a

# 新建一个分支，但依然停留在当前分支
$ git branch [branch-name]

# 新建一个分支，并切换到该分支
$ git checkout -b [branch]

# 新建一个分支，指向指定commit
$ git branch [branch] [commit]

# 新建一个分支，与指定的远程分支建立追踪关系
$ git branch --track [branch] [remote-branch]

# 切换到指定分支，并更新工作区
$ git checkout [branch-name]

# 切换到上一个分支
$ git checkout -

# 建立追踪关系，在现有分支与指定的远程分支之间
$ git branch --set-upstream [branch] [remote-branch]

# 合并指定分支到当前分支
$ git merge [branch]

# 选择一个commit，合并进当前分支
$ git cherry-pick [commit]

# 删除分支
$ git branch -d [branch-name]

# 删除远程分支
$ git push origin --delete [branch-name]
$ git branch -dr [remote/branch]
```