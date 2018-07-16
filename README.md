# GitHubTest
开始学习使用GitHub

 [git学习网站](https://www.liaoxuefeng.com/wiki/0013739516305929606dd18361248578c67b8067c8c017b000)
 
 学习总结：
 
# Git 学习

Pull：直译过来就是「拉」的意思，如果别人提交代码到远程仓库，这个时候你需要把远程仓 库的最新代码拉下来，然后保证两端代码的同步。 代码示例： git pull origin master

Push ：直译过来就是「推」的意思，什么意思呢？如果你本地代码有更新了，那么就需要把 本地代码推到远程仓库，这样本地仓库跟远程仓库就可以保持同步了。 代码示例： git push origin master 意思就是把本地代码推到远程 master 分支。


#分支

Git鼓励大量使用分支：
查看分支：git branch
创建分支：git branch <name>
切换分支：git checkout <name>
创建+切换分支：git checkout -b <name>
合并某分支到当前分支：git merge <name>
删除分支：git branch -d <name>

用git log --graph命令可以看到分支合并图


#合并
git merge命令用于合并指定分支到当前分支
$ git merge dev
 //把dev 分支合并到当前分支


#删除分支
$ git branch -d dev

如果要丢弃一个没有被合并过的分支，可以通过git branch -D <name>强行删除。

//
创建分支：$ git branch dev

切换到dev :$ git checkout dev

上下一样
$ git checkout -b dev
//

要查看远程库的信息，用git remote：
$ git remote -v


#推送分支
推送分支，就是把该分支上的所有本地提交推送到远程库。推送时，要指定本地分支，这样，Git就会把该分支推送到远程库对应的远程分支上：
$ git push origin master
如果要推送其他分支，比如dev，就改成：
$ git push origin dev


#协作
* 查看远程库信息，使用git remote -v； 
* 本地新建的分支如果不推送到远程，对其他人就是不可见的； 
* 从本地推送分支，使用git push origin branch-name，如果推送失败，先用git pull抓取远程的新提交； 
* 在本地创建和远程分支对应的分支，使用git checkout -b branch-name origin/branch-name，本地和远程分支的名称最好一致； 
* 建立本地分支和远程分支的关联，使用git branch --set-upstream branch-name origin/branch-name； 
* 从远程抓取分支，使用git pull，如果有冲突，要先处理冲突。 
标签
	•	命令git tag <tagname>用于新建一个标签，默认为HEAD，也可以指定一个commit id； 
* 命令git tag -a <tagname> -m "blablabla..."可以指定标签信息； 
* 命令git tag可以查看所有标签。
* 
*  	•	命令git push origin <tagname>可以推送一个本地标签； 
* 命令git push origin --tags可以推送全部未推送过的本地标签； 
* 命令git tag -d <tagname>可以删除一个本地标签； 
* 命令git push origin :refs/tags/<tagname>可以删除一个远程标签。 





////
#分支策略

在实际开发中，我们应该按照几个基本原则进行分支管理：
首先，master分支应该是非常稳定的，也就是仅用来发布新版本，平时不能在上面干活；

那在哪干活呢？干活都在dev分支上，也就是说，dev分支是不稳定的，到某个时候，比如1.0版本发布时，再把dev分支合并到master上，在master分支发布1.0版本；

你和你的小伙伴们每个人都在dev分支上干活，每个人都有自己的分支，时不时地往dev分支上合并就可以了。
所以，团队合作的分支看起来就像这样：
￼
小结
Git分支十分强大，在团队开发中应该充分应用。
合并分支时，加上--no-ff参数就可以用普通模式合并，合并后的历史有分支，能看出来曾经做过合并，而fast forward合并就看不出来曾经做过合并。