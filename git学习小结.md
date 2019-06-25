>**git 学习**
学习资料：
1. [Git 简明指南—罗杰·杜德勒](http://www.runoob.com/manual/git-guide/)
2. [git教程—runoob](http://www.runoob.com/git/git-tutorial.html)
3. [git教程—廖雪峰](https://www.liaoxuefeng.com/wiki/0013739516305929606dd18361248578c67b8067c8c017b000)
4. [Git 完整命令手册地址](http://git-scm.com/docs)

>**git 踩坑**
>**git 笔记**

##踩坑
### git-cmd 与 git-bash 二者区别？

	Bash是基于CMD的，Bash在CMD的基础上新增了一些命令和功能，故建议使用Bash。
	
### Git 与 SVN 区别点：
  Git不仅仅是版本控制系统，也是内容管理系统(CMS),工作管理系统等。如果你是一个具有使用SVN背景的人，你需要做一定的思想转换，来适应Git提供的一些概念和特征。

	1. Git是分布式的，SVN不是：这是Git和其它非分布式的版本控制系统，例如SVN，CVS等，最核心的区别。
	 
	2. Git把内容按元数据方式存储，而SVN是按文件：所有的资源控制系统都是把文件的元信息隐藏在一个类似.svn,.cvs等的文件夹里。
	
	3. Git分支和SVN的分支不同：分支在SVN中一点不特别，就是版本库中的另外的一个目录。
	
	4. Git没有一个全局的版本号，而SVN有：目前为止这是跟SVN相比Git缺少的最大的一个特征。
	
	5. Git的内容完整性要优于SVN：Git的内容存储使用的是SHA-1哈希算法。这能确保代码内容的完整性，确保在遇到磁盘故障和网络问题时降低对版本库的破坏。
	
### Git&GitHub

	- Git 是一种专为处理文本文件而设计的版本控制系统，它允许你通过提交对一个系统（或一组）文件的历史进行注释。这些提交便是在给定时间点对系统做出的差异"快照".
	
	- Github 获取 Git 中的提交历史，并将其存储在互联网上，因此你可以从任一一台电脑访问它。你在本机推送（pushing）提交到 Github，然后从另一台电脑上拉取（pulling）这些提交.

##git 笔记
###创建新仓库 git init
	创建新文件夹，打开，然后执行 
	git init
	以创建新的 git 仓库
- 添加 
		git add 文件名称 添加到暂存区

- 提交
		git commit -m "此次提交注释/备注" 只负责提交暂存区的修改

- 查看版本历史记录
		git log	 	显示从最近到最远的提交日志

- 版本回退
		git reset --hard HEAD^
	* 在Git中，用HEAD表示当前版本，
	* 上一个版本就是HEAD^，上上一个版本就是HEAD^^
	* 往上n个版本，可以写成HEAD~n
	
		
- 查看命令历史，以便确定要回到未来的哪个版本	
		git reflog

###工作区&暂存区

####版本库（Repository）
	工作区有一个隐藏目录.git，这个不算工作区，而是Git的版本库。
Git的版本库里存了很多东西，其中最重要的就是称为stage（或者叫index）的暂存区，还有Git为我们自动创建的第一个分支master，以及指向master的一个指针叫HEAD

前面讲了我们把文件往Git版本库里添加的时候，是分两步执行的：

    1. 用git add把文件添加进去，实际上就是把文件修改添加到暂存区；
    2. 用git commit提交更改，实际上就是把暂存区的所有内容提交到当前分支。

因为我们创建Git版本库时，Git自动为我们创建了唯一一个master分支，所以现在，git commit就是往master分支上提交更改。

	git status 查看状态
#####撤销修改checkout
	git checkout --文件名称 撤销对工作区的修改这里有两种情况：

  * 一种是readme.txt自修改后还没有被放到暂存区，现在，撤销修改就回到和版本库一模一样的状态.
  * 一种是readme.txt已经添加到暂存区后，又作了修改，现在，撤销修改就回到添加到暂存区后的状态.

**总之，就是让这个文件回到最近一次git commit或git add时的状态**。

**小结**

- 场景1：当你改乱了工作区某个文件的内容，想直接丢弃工作区的修改时，用命令git checkout -- file。

- 场景2：当你不但改乱了工作区某个文件的内容，还添加到了暂存区时，想丢弃修改，分两步，第一步用命令git reset HEAD <file>，就回到了场景1，第二步按场景1操作。

- 场景3：已经提交了不合适的修改到版本库时，想要撤销本次提交，参考版本回退一节，不过前提是没有推送到远程库。

#####删除文件
在文件管理器中把没用的文件删了，或者用rm命令删了。工作区和版本库就不一致了，git status命令会告诉你哪些文件被删除了：2种选择
- 一是确实要从版本库中删除该文件，那就用命令git rm删掉，并且git commit：
		$git rm 文件名称
		$git commit -m "备注"

- 二是删错了，因为版本库里还有呢，所以可以很轻松地把误删的文件恢复到最新版本：
		$ git checkout -- 文件名称

git checkout其实是用版本库里的版本替换工作区的版本，无论工作区是修改还是删除，都可以“一键还原”。

##远程仓库
由于你的本地Git仓库和GitHub仓库之间的传输是通过SSH加密的，所以，需要一点设置：

第1步：创建SSH Key。在用户主目录下，看看有没有.ssh目录，如果有，再看看这个目录下有没有id_rsa和id_rsa.pub这两个文件，如果已经有了，可直接跳到下一步。如果没有，打开Shell（Windows下打开Git Bash），创建SSH Key：

	$ ssh-keygen -t rsa -C "youremail@example.com" 
 然后一路回车，使用默认值即可

为什么GitHub需要SSH Key呢？因为GitHub需要识别出你推送的提交确实是你推送的，而不是别人冒充的，而Git支持SSH协议，所以，GitHub只要知道了你的公钥，就可以确认只有你自己才能推送。

当然，GitHub允许你添加多个Key。假定你有若干电脑，你既可在公司提交，也可在家里提交，只要把每台电脑的Key都添加到GitHub，就可以在每台电脑上往GitHub推送了。

###添加远程库
* 在本地的learngit仓库下运行命令：

	$ git remote add origin git@github.com:michaelliao/learngit.git
注意：
	* 把上面的michaelliao替换成你自己的GitHub账户名
	* 添加后，远程库的名字就是origin，这是Git默认的叫法，当然也可以改成别的
	* 解除本地目录下关联的远程库 git remote remove origin
* 把本地库的所有内容推送到远程库上：
	- 把本地库的内容推送到远程，用git push命令，实际上是把当前分支master推送到远程。
	- 由于远程库是空的，我们第一次推送master分支时，加上了-u参数，Git不但会把本地的master分支内容推送的远程新的master分支，还会把本地的master分支和远程的master分支关联起来，在以后的推送或者拉取时就可以简化命令。

小结
要关联一个远程库，使用命令

	git remote add origin git@server-name:path/repo-name.git；

关联后，使用命令

	git push -u origin master第一次推送master分支的所有内容；

此后，每次本地提交后，只要有必要，就可以使用命令
	git push origin master推送最新修改；

分布式版本系统的最大好处之一是在本地工作完全不需要考虑远程库的存在，也就是有没有联网都可以正常工作，而SVN在没有联网的时候是拒绝干活的！当有网络的时候，再把本地提交推送一下就完成了同步，真是太方便了
###从远程库克隆
登陆GitHub，创建一个新的仓库，名字叫gitskills：

	github-init-repo
我们勾选Initialize this repository with a README，这样GitHub会自动为我们创建一个README.md文件。创建完毕后，可以看到README.md文件：

下一步是用命令git clone克隆一个本地库：

	$ git clone git@github.com:michaelliao/gitskills.git

GitHub给出的地址不止一个，还可以用https://github.com/michaelliao/gitskills.git这样的地址。实际上，Git支持多种协议，默认的git://使用ssh，但也可以使用https等其他协议。

使用https除了速度慢以外，还有个最大的麻烦是每次推送都必须输入口令，但是在某些只开放http端口的公司内部就无法使用ssh协议而只能用https。

**小结**
- 要克隆一个仓库，首先必须知道仓库的地址，然后使用git clone命令克隆。

- Git支持多种协议，包括https，但通过ssh支持的原生git协议速度最快。

##分支管理
###创建合并
Git鼓励大量使用分支：

查看分支：git branch

创建分支：git branch <name>

切换分支：git checkout <name>

创建+切换分支：git checkout -b <name>

合并某分支到当前分支：git merge <name>

删除分支：git branch -d <name>
###
###
###
###
##标签管理
