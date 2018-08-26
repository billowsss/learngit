>**git 学习**
学习资料：
1. [Git 简明指南—罗杰·杜德勒](http://www.runoob.com/manual/git-guide/)
2. [git教程—runoob](http://www.runoob.com/git/git-tutorial.html)
3. [git教程—廖雪峰](https://www.liaoxuefeng.com/wiki/0013739516305929606dd18361248578c67b8067c8c017b000)
4. [Git 完整命令手册地址](http://git-scm.com/docs)

>**git 踩坑**
>**git 笔记**

##踩坑
###git-cmd 与 git-bash 二者区别？

	Bash是基于CMD的，Bash在CMD的基础上新增了一些命令和功能，故建议使用Bash更方便。

###Git 与 SVN 区别
GIT不仅仅是个版本控制系统，它也是个内容管理系统(CMS),工作管理系统等。如果你是一个具有使用SVN背景的人，你需要做一定的思想转换，来适应GIT提供的一些概念和特征。

Git 与 SVN 区别点：

1. GIT是分布式的，SVN不是：这是GIT和其它非分布式的版本控制系统，例如SVN，CVS等，最核心的区别。
2. GIT把内容按元数据方式存储，而SVN是按文件：所有的资源控制系统都是把文件的元信息隐藏在一个类似.svn,.cvs等的文件夹里。
3. GIT分支和SVN的分支不同：分支在SVN中一点不特别，就是版本库中的另外的一个目录。
4. GIT没有一个全局的版本号，而SVN有：目前为止这是跟SVN相比GIT缺少的最大的一个特征。
5. GIT的内容完整性要优于SVN：GIT的内容存储使用的是SHA-1哈希算法。这能确保代码内容的完整性，确保在遇到磁盘故障和网络问题时降低对版本库的破坏。

##git 笔记
###创建新仓库 git init
	创建新文件夹，打开，然后执行 
	git init
	以创建新的 git 仓库