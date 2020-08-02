# repo

###### **基础**

`git init`把这个目录变成Git可以管理的仓库

`git add README.md`文件添加到仓库

`git add . `不但可以跟单一文件，还可以跟通配符，更可以跟目录。一个点就把当前目录下所有未追踪的文件全部add了 

`git commit -m "first commit"`把文件提交到仓库

`git remote add origin git@github.com:yourusername/yourrepositoryname.git`关联远程仓库

`git remote remove origin`删除关联远程仓库

`git push -u origin master`把本地库的所有内容推送到远程库上

`git remote set-url origin git@github.com:yourusername/yourrepositoryname.git`更改仓库指向

`git log`显示所有提交过的版本信息

`git log --pretty=oneline`只会显示版本号和提交时的备注信息

`git reflog`可以查看所有分支的所有操作记录（包括已经被删除的 commit 记录和 reset 的操作）

`git status`

Git管理的文件分为：工作区，版本库，版本库又分为暂存区stage和暂存区分支master(仓库)

工作区>>>>暂存区>>>>仓库

`git add`把文件从工作区>>>>暂存区

`git commit`把文件从暂存区>>>>仓库，

`git diff`查看工作区和暂存区差异，

`git diff --cached`查看暂存区和仓库差异，

`git diff HEAD `查看工作区和仓库的差异，

`git add`的反向命令`git checkout -- file`，撤销工作区修改，即把暂存区最新版本转移到工作区

`git checkout -- file`撤销(`working directory`回到`git commit`或`git add`)

`git commit`的反向命令`git reset HEAD file`，就是把仓库最新版本转移到暂存区

`git reset HEAD file`(撤销缓存区`unstage`)

`git reset --hard HEAD^(HEAD^^)`HEAD就会指向历史commit

`git reset --hard (version)`HEAD就会指向历史version

`git rm file`先手动删除文件，然后使用`git rm filename`和`git add filename`效果是一样的

###### **进阶**

查看分支：`git branch`

创建分支：`git branch branch-name `

切换分支：`git checkout `或者`git switch `

创建+切换分支：`git checkout -b `或者`git switch -c `

合并某分支到当前分支：`git merge `

删除分支：`git branch -d `

用`git log --graph`命令可以看到分支合并图

git merge  --no-ff -m "" <branch> 如果要强制禁用`Fast forward`模式，Git就会在merge时生成一个新的commit，这样，从分支历史上就可以看出分支信息。

git stash 一是用`git stash apply`恢复，但是恢复后，stash内容并不删除，你需要用`git stash drop`来删除；

另一种方式是用`git stash pop`，恢复的同时把stash内容也删了：

多次stash，恢复时先用`git stash list` 然后`git stash apply stash@{0}`

`git cherry-pick <commit>`让我们能复制一个特定的提交到当前分支

开发一个新feature，最好新建一个分支；

如果要丢弃一个没有被合并过的分支，可以通过`git branch -D `强行删除

- 查看远程库信息，使用`git remote -v`；
- 本地新建的分支如果不推送到远程，对其他人就是不可见的；
- 从本地推送分支，使用`git push origin branch-name`，如果推送失败，先用`git pull`抓取远程的新提交；
- 在本地创建和远程分支对应的分支，使用`git checkout -b branch-name origin/branch-name`，本地和远程分支的名称最好一致；
- 建立本地分支和远程分支的关联，使用`git branch --set-upstream branch-name origin/branch-name`；
- 从远程抓取分支，使用`git pull`，如果有冲突，要先处理冲突。

`git rebase`变基

`git tag <name>`就可以打一个新标签`git tag  <name> commit`;用`-a`指定标签名，`-m`指定说明文字：

命令`git tag -a <tagname> -m "blablabla..." commit`可以指定标签信息；

`git tag`查看所有标签

`git show <tagname> `可以看到说明文字

- 命令`git push origin <tagname>`可以推送一个本地标签；
- 命令`git push origin --tags`可以推送全部未推送过的本地标签；
- 命令`git tag -d <tagname> `可以删除一个本地标签；
- 命令`git push origin :refs/tags/<tagname>`可以删除一个远程标签。

part2

自定义`git` 与 `git GUI`