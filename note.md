# Git 常用命令

## 集中式版本控制

- git add *filename* : 将文件添加到暂存区。
- git commit -m "*summary*"：将暂存区的所有修改提交到仓库
- git status：查看当前工作区的状态
- git log：查看历史记录
- git reflog：查看每一次命令和每一次commit的 *commit id*（用于版本回退）
- git reset --hard HEAD^ ... ：版本回退，HEAD后面有几个^就往前退几个版本，如果回退版本较多则可以用HEAD~100
- git reset --hard *commit id*：版本复原，根据 *commit id* 选择回到哪个版本
- git checkout -- *filename* ：撤销工作区的修改（尚未add到暂存区）（git checkout 实质上是用版本库的版本替换工作区的版本）
- git reset HEAD *filename* ：撤销暂存区的修改，重新放回工作区。
- cd *pathname* ：设置当前路径
- mkdir *pathname* ：新建空白路径
- git rm ：删除版本库中的文件，之后需要commit。

## 分布式版本控制

- git remote add origin git@github.com/*repositoryname*.git ：关联一个github上的远程库
- git push -u origin master：第一次推送master分支上的所有内容
- git push origin master ：向远程库推送最新修改