
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
#
#	1.工作区（Working Directory）
#		就是Git 创建仓库所在的目录
#
#	2版本库（Repository）
#		工作区有一个隐藏目录.git，这个不是工作区，而是Git的版本库
#
#	Git的版本库里存了很多东西，其中最重要的就是称为stage（或者叫index）的暂存区，还有Git为我们自动创建的第一个分支master，以及指向master的一个指针叫HEAD
#
#		git add 实际上就是把文件修改添加到暂存区
#
#		git commit 实际上就是把暂存区的所有内容提交到当前分支
#			我们创建Git版本库时，Git自动为我们创建了唯一一个master分支，所以，现在，git commit就是往master分支上提交更改

8.查看工作区和版本库里面最新版本的区别
	$ git diff HEAD -- +文件名

9.放弃对文件的更改

	9.1 放弃对"工作区"文件的更改
		$ git checkout -- 文件名
			$ git checkout -- file命令中的--很重要，没有--，就变成了“切换到另一个分支”的命令

	9.2 放弃对"暂存区"文件的更改
		$ git reset HEAD + 文件名

#场景1：当你改乱了工作区某个文件的内容，想直接丢弃工作区的修改时，用命令git checkout -- file。
#
#场景2：当你不但改乱了工作区某个文件的内容，还添加到了暂存区时，想丢弃修改，分两步，第一步用命令git reset HEAD <file>，就回到了场景1，第二步按场景1操作。
#
#场景3：已经提交了不合适的修改到版本库时，想要撤销本次提交，参考版本回退<number 7>，不过前提是没有推送到远程库。
#命令git rm用于删除一个文件。如果一个文件已经被提交到版本库，那么你永远不用担心误删，但是要小心，你只能恢复文件到最新版本，你会丢失最近一次提交后你修改的内容

10.创建GitHub远程仓库
	第1步：创建SSH Key。在用户主目录下，看看有没有.ssh目录，如果有，再看看这个目录下有没有id_rsa,id_rsa.pub这两个文件，如果已经有了，可直接跳到下一步。如果没有，打开Shell（Windows下打开Git Bash），创建SSH Key
		$ ssh-keygen -t rsa -C "youremail@example.com"

	第2步：登陆GitHub，打开“Account settings”，“SSH Keys”页面,然后，点“Add SSH Key”，填上任意Title，在Key文本框里粘贴id_rsa.pub文件的内容

	第3步: 登陆GitHub，在右上角找到“Create a new repo”按钮，创建一个新的仓库,在Repository name填入仓库名，其他保持默认设置，点击“Create repository”按钮，就成功地创建了一个新的Git仓库

	第4步: 在本地shell上 对GitHub上的仓库绑定: git remote add frelon git@github.com:lixuanliming/frelon.git
#		这里的 frelon 是远程仓库的名字,后面是GitHub给的URL












