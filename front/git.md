### git基本语法
- git命令
    - git log 显示提交日志 包括版本号
    - git log --pretty=oneline显示提交日志的简写
    - git reflog 可以用来记录版本命令，可以用来查找操作过版本的内容，其中有版本号
    - git add -A添加所有
- git名词

    - 工作区：在硬盘上的目录

    - 版本库：.git文件夹

    - 分支：在创建版本库时，自动创建master分支。每次commit的时候是把内容提交到当前分支上。可以多次add到暂存区中，然后一次commit一起提交到分支上。
- git状态
    - 2 files changed, 579 insertions(+)提示两个文件更改579行
    - git status状态：
        - changes not staged for commit 没有提交的更改
        - Untracked files 没有添加到暂存区（stage）的文件
        - changes to be committed 等待从暂存区提交的文件
        - modified 更改的文件
        - nothing to commit(working directoru clean) 暂存区干净

- 创建版本库
    - cd.. cd e：进入需要进行git控制的文件夹中
    - git init 把这个目录变成git管理的仓库

- 提交新文件
    - git add readme.txt 从工作空间添加到暂存区
    - git commit -m"write a readme.txt消息" 提交到库中

    - 文件更改
    - git status 用来在已经提交后并修改的文件查看状态
    - git diff read.txt查看修改的具体内容

    - 没有问题后执行上面中两步来提交文件

- 版本退回
    - git reset --hard HEAD^ 退回至上一版本
    - git reset --hard HEAD^^退回至上两个版本
    - git reset --hard HEAD~100 退回至上100个版本
    - git reset --hard 322442165 退回至id所在的版本，可以是未来的版本

- 撤销修改
    - git ckeckout -- a.txt 放弃修改（实质是把版本库中的文件替换到工作区）

    - 如果没有添加到暂存区，工作区文件恢复

    - 如果添加到暂存区后修改，恢复到添加暂存区后的状态

    - 如果修改被添加到暂存区，git reset HEAD a.txt 可以用来撤销暂存区修改，重新放到工作区

    - 场景1：当你改乱了工作区某个文件的内容，想直接丢弃工作区的修改时，用命令git checkout -- file。

    - 场景2：当你不但改乱了工作区某个文件的内容，还添加到了暂存区时，想丢弃修改，分两步，第一步用命令git reset HEAD file，就回到了场景1，第二步按场景1操作。

    - 场景3：已经提交了不合适的修改到版本库时，想要撤销本次提交，参考版本回退一节，不过前提是没有推送到远程库。

- 删除文件
    - rm a.txt 或者直接在文件夹中删除文件。
    - git rm a.txt 再版本库中删除改文件
    - git commit -m"删除信息"
- gitignore 新增忽略的文件
   - git rm -r --cached .
   - git add .
   - git commit -m 'updata .gitignore'
- 远程分支检出到 本地分支
  - git checkout -b master origin/master 
- 重命名分支
  - git branch -m new old
- 删除远程分支
  - git push origin --delete master
- 删除本地分支
  - git branch -D master
- 本地分支推送到远程没有的分支
  - g push --set-upstream origin newbranch 
-  git remote add Activity git@github.com:tuhu/Activity.git