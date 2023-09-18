# learnJS
learn js


#创建并进入目录
``mkdir git_parent && cd git_parent``
``git remote show origin``
``cat .git\config``
#循环遍历每个submodule pull代码
``git submodule foreach git pull``

对于一个包含子module的git 项目来说，开发者拉去代码 的时候
默认只能获取的parent 项目的内容，子模块的内容是拉去不到的，还要
执行两个命令
在parent目录下执行
`` git submodule init`` --子模块init
``git submodule update --recusive`` --子模块代码递归获取

* 删除submodule
* 先从暂存区中删除 ``git rm --cached mymodule``
* 再把mymodule 从工作区中删除   ``rm -rf mymodule``
* 最后执行git add . 并且commit和push
* 进入到 .git 目录下 删除.gitmodules 目录 并commit 和push


* git subtree介绍
* 首先在subtree parent 目录中 去添加 子subtree的地址
* git remote add subtree-origin git@github.com:gitlecture/git_subtree_child.git
* 展示远程地址 git remote show 包含origin subtree-origin
* 使用命令 git subtree add --prefix=<prefix> <repository> <ref> 
*         git subtree add --prefix=subtree subtree-origin master --squash
        其中 <prefix> 代表 subtree存放目录  <repository> subtree的git地址 <ref> 指定subtree的分支
*       --squash 用于合并历史提交为新提交  历史提交就没有
* subtree 作用 可以在parent目录直接修改child目录里的内容 
* push时候的注意点 ：
* 先提交parent 的提交 git push -u 然后在push到child分支 git subtree push --prefix=subtree subtree-origin master
*                                                                 其中 <prefix> 代表 subtree存放目录  <repository> subtree的git地址 <ref> 指定subtree的分支
* 在parent目录中 子模块的版本提交log使用命令 git log subtree-origin/master
* 


* echo 'child5' >> child.txt  往 child.txt的末尾行追加child5
* echo 'child5' > child.txt 往child.txt文件里写入child5 覆盖掉原本内容

* child2目录里修改了文件内容 并推送到远程 ，紧接着在parent2目录 中使用git subtree pull 命令 ，将
* subtree2 push上去的内容拉取到本地时候 还是会出现冲突，产生的根本原因 gitk 图形工具 经过一系列的时间点倒推，发现在项目最初的提交
* 点时他们没有公共的祖先，完全是两个仓库。所以目前只能解决冲突。

* cherry-pick （樱桃 捡起来）将你对某一个分支的修改 commit 应用到另外一个分支上。
*  git cherry-pick commit-id
* 将 已经在develop分支上开发出来的commit 移除 方法：
* 找到需要恢复到的点 即commitid ，然后使用命令 git checkout commitid后 ，
* 使用git branch -D develop （强制循环删除develop分支），git提醒需要创建一个分支名称，使用
* 命令git checkout -b develop 创建devlop分支 。
* 



