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

### 万能公式
??? quote "创建 + 修改提交"

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
        + ```git push origin master```
    
    **本地已有内容**
    
    1. cd 到本地目录下
    2. ```git init # 把这个目录变成git可以管理的仓库```
    3. 在本地创建了一个Git仓库后，再在github创建一个Git仓库
    4. 关联远程库
        + ```git remote add origin <repo-url>```
        + ```git branch -M main```
        + ```git push -u origin master```

            > 由于远程库是空的，我们第一次推送master分支时，加上了 –u参数，Git不但会把本地的master分支内容推送到远程新的master分支，还会把本地的master分支和远程的master分支关联起来，在以后的推送或者拉取时就可以简化命令


??? quote "查看状态"

    + ```git status # 查看处于哪个分支，以及是否还有文件未提交``` 
    + ```git diff <file> # 查看修改内容```

