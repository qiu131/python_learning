# Git_learning

## 1 一些基本操作

![git](G:\photos\blog\git.png)

- 新的空文件夹可以使用git init命令初始化
- git add 把文件添加进git的暂存区（可以是多个文件，一次性提交至暂存区）
- git status可以查看状态（工作区或暂存区文件的状态）
- 用git commit提交修改，把暂存区的所有内容提交到当前分支。**git commit -m '提交操作的记录'**



## 2 文件撤销修改、对比、删除

### 2.1 文件撤销

资料参考：https://www.cnblogs.com/qlqwjy/p/8378851.html

三个场景：

1、未使用 git add 缓存代码时

可以使用 **git checkout -- filepathname** (比如： git checkout -- readme.md ，不要忘记中间的 “--” ，不写就成了检出分支了！！)。放弃所有的文件修改可以使用 git checkout 命令。

此命令用来放弃掉所有还没有加入到缓存区（就是 git add 命令）的修改：内容修改与整个文件删除。但是此命令不会删除掉刚新建的文件。因为刚新建的文件还没已有加入到 git 的管理系统中。所以对于git是未知的。自己手动删除就好了。

2、已经使用了 git add 缓存了代码

可以使用 **git reset HEAD filepathname** （比如： git reset HEAD readme.md）来放弃指定文件的缓存，放弃所以的缓存可以使用 git reset HEAD . 命令。

此命令用来清除 git 对于文件修改的缓存。相当于撤销 git add 命令所在的工作。在使用本命令后，本地的修改并不会消失，而是回到了如（一）所示的状态。继续用（一）中的操作，就可以放弃本地的修改。

3、已经用 git commit 提交了代码

可以使用 **git reset --hard HEAD^** 来回退到上一次该文件commit的状态（回滚上一个版本）。

此命令也可以用来回退到任意版本：**git reset --hard commitid**

可以利用git reflog来查看其commitid



### 2.2 文件比对

1、对比工作区和某个版本中的文件不同。例如：现在要对比工作区中code.txt和HEAD版本中code.txt的不同，可以使用git diff HEAD -- code.txt

2、对比两个版本文件的不同：git diff HEAD HEAD^



### 2.3 文件删除

rm code.txt 此时已经删除了该文件，但现在有两个选择：一是确实要从版本库中删除该文件，那就用命令git rm删掉，并且git commit；此外，利用git checkout - code.txt找回。



## 3 分支管理



几个常用的分支管理的命令：

1、执行如下命令可以查看当前有几个分支并且看到在哪个分支下工作：git branch

2、创建一个分支并切换到该分支上进行工作：git checkout -b dev

3、切换回master分支：git checkout master

4、合并某分支至当前分支：git merge dev

5、删除分支：git branch -d <branchName>

6、删除远程分支：git push origin --delete <branch-name>

7、重命名分支：

```
# 重命名当前分支, 通常情况下需要执行3步
# 1、修改分支名称
# 2、删除远程旧分支
# 3、将重命名分支推送到远程
git branch -m <branchName>
git push origin :old_branch
git push -u origin new_branch
```

详细的Git命令：https://github.com/xjh22222228/git-manual



## 4 用Git上传文件至GitHub

常用命令：

1、推送分支（把该分支上的所有本地提交推送到远程库）：git push origin 分支名称

2、从远程分支上拉取代码：git pull orgin 分支名称







