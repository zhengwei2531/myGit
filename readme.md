######1.创建版本库
- mkdir xx ：创建一个名为xx的目录；
- pwd ：显示当前目录；
- git init ：把这个目录变成Git可以管理的仓库；
- git add命令告诉Git，把文件添加到仓库
	- git add xxx ：添加xxx
	- git add .：添加所有)
- git commit -m "xxx"：把文件提交到仓库，-m后面输入的是本次提交的说明

---
	初始化一个Git仓库，使用git init命令。
	添加文件到Git仓库，分两步：
	第一步，使用命令git add <file>，注意，可反复多次使用，添加多个文件；
	第二步，使用命令git commit，完成。
######2.时光穿梭机
- git status命令可以让我们时刻掌握仓库当前的状态，可以用在add后，commit前用来查看将要被提交的修改是什么
- git diff xx：顾名思义就是查看xx文件的difference，显示的格式正是Unix通用的diff格式

---
要随时掌握工作区的状态，使用git status命令。
如果git status告诉你有文件被修改过，用git diff可以查看修改内容。
######2.1.版本退回
- git log：显示从最近到最远的提交日志
	- git log --pretty=oneline：一行的简要日志
- git reset --hard HEAD^：回退到上一个版本(即未修改到本版本前)
- git reset --hard xxx：跳转到commit id前几位为xxx的版本

- cat xxx：查看看xxx文件的内容

---
	HEAD指向的版本就是当前版本，因此，Git允许我们在版本的历史之间穿梭，使用命令git reset --hard commit_id。
	穿梭前，用git log可以查看提交历史，以便确定要回退到哪个版本。
	要重返未来，用git reflog查看命令历史，以便确定要回到未来的哪个版本。
######2.2.工作区和暂存区
	前面讲了我们把文件往Git版本库里添加的时候，是分两步执行的：
	第一步是用git add把文件添加进去，实际上就是把文件修改添加到暂存区(status)；
	第二步是用git commit提交更改，实际上就是把暂存区的所有内容提交到当前分支。
* 暂存区是Git非常重要的概念，弄明白了暂存区，就弄明白了Git的很多操作到底干了什么。
######2.3.管理修改
######2.4.撤销修改
- git checkout -- readme.txt意思就是，把readme.txt文件在工作区的修改全部撤销，这里有两种情况：
	一种是readme.txt自修改后还没有被放到暂存区，现在，撤销修改就回到和版本库一模一样的状态；
	一种是readme.txt已经添加到暂存区后，又作了修改，现在，撤销修改就回到添加到暂存区后的状态。