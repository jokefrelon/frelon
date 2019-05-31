
1.建立git仓库
	$ git init

2.把文件添加到仓库
	$ git add + filename

3.把文件提交到仓库
	$ git commit -m "wrote a readme file"

4.查看提交结果/对比工作区和文件和仓库文件的不同之处
	$ git status

5.比对并列出文件和仓库文件的不同之处
	$ git diff

#如果git status告诉你有文件被修改过，用git diff可以查看修改内容。

6.Git查看历史记录
	$ git log/git log --pretty=oneline(查看精简版)

7.退回曾经的某个版本
	$ git reset --hard HEAD^
		用HEAD表示当前版本，上一个版本就是HEAD^，上上一个版本就是HEAD^^，当然往上100个版本写100个^比较容易数不过来，所以写成HEAD~100 

	7.1 退回最新版
		$ git reset --hard + (对应的append GPL的commit id)
	
	7.2 查找所有版本append GPL的commit id
		$ git reflog
#git原理:
#	1.工作区（Working Directory）
#		就是Git 创建仓库所在的目录
#
#	2版本库（Repository）
#		工作区有一个隐藏目录.git，这个不是工作区，而是Git的版本库
#		Git的版本库里存了很多东西，其中最重要的就是称为stage（或者叫index）的暂存区，还有Git为我们自动创建的第一个分支master，以及指向master的一个指针叫HEAD
#
#		git add 实际上就是把文件修改添加到暂存区
#		git commit 实际上就是把暂存区的所有内容提交到当前分支
#			我们创建Git版本库时，Git自动为我们创建了唯一一个master分支，所以，现在，git commit就是往master分支上提交更改
















