# Git 学习笔记

## 集中式版本控制

### 基本操作

- git add *filename* : 将文件添加到暂存区。
- git commit -m "*summary*"：将暂存区的所有修改提交到仓库
- git status：查看当前工作区的状态
- git log：查看历史记录
- git reflog：查看每一次命令和每一次commit的 *commit id*（用于版本回退）
- cd *pathname* ：设置当前路径
- mkdir *pathname* ：新建空白路径

### 撤销修改

- git reset --hard HEAD^ ... ：版本回退，HEAD后面有几个^就往前退几个版本，如果回退版本较多则可以用HEAD~100
- git reset --hard *commit id*：版本复原，根据 *commit id* 选择回到哪个版本
- git checkout -- *filename* ：撤销工作区的修改（尚未add到暂存区）（git checkout 实质上是用版本库的版本替换工作区的版本）
- git reset HEAD *filename* ：撤销暂存区的修改，重新放回工作区。
- git rm ：删除版本库中的文件，和add一样，之后需要commit。

## 分布式版本控制

### 本地库与GitHub仓库关联
- git remote add origin git@github.com/*repositoryname*.git ：关联一个github上的远程库
- git push -u origin master ：第一次推送master分支上的所有内容
- git push origin master ：向远程库推送最新修改

### 在本地对别人的代码进行修改（分支操作）

- git clone git@github.com:*username*/*repositoryname*.git ：将Github上已有的代码仓库克隆到本地（支持https,但是git协议速度最快）
- git branch ：查看分支
- git branch *branchname* ：创建分支
- git checkout *branchname* ：切换分支
- git checkout -b *branchname* ：创建并切换分支
- git merge *branchname* ：合并 *branchname* 分支到当前分支
- git branch -d *branchname* ：删除分支
- git merge --no-ff -m "*summary*" *branchname* ：用非fast-forward的方式合并分支。由于此种合并方式会提交一个新的commit，所以需要-m参数来增加描述。


> 当Git无法自动合并分支时，就必须首先解决冲突。解决冲突后，再提交，合并完成

> 在实际开发中，master分支应该非常稳定，仅用来发布新版本。dev分支不稳定，干活都在dev分支上。团队开发每个人都有自己的分支，时不时合并到dev分支.

> 修复bug时，我们会通过创建新的bug分支进行修复，然后合并，最后删除；当手头工作没有完成时，先把工作现场git stash一下，然后去修复bug，修复后，再git stash pop，回到工作现场。

- git stash：把当前分支的工作储藏起来，等以后恢复现场继续工作。
- git stash apply：把最近stash的工作恢复，stash的内容不删除，需要用 git stash drop 来删除
- git stash pop ：把最近stash的工作恢复，stash的内容删除。
- git stash list：查看stash的内容

> 当前工作既不stash又不commit是不可以切换到其他分支的，会有stash提醒。

- git branch -D *branchname* ：强制删除分支




