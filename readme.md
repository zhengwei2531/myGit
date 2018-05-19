#####1.创建版本库
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
#####2.时光穿梭机
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
	第一步是用git add把文件添加进去，实际上就是把文件修改添加到暂存区(stage)；
	第二步是用git commit提交更改，实际上就是把暂存区的所有内容提交到当前分支。
* 暂存区是Git非常重要的概念，弄明白了暂存区，就弄明白了Git的很多操作到底干了什么。
######2.3.管理修改
######2.4.撤销修改
- git checkout -- readme.txt意思就是，把readme.txt文件在工作区的修改全部撤销，这里有两种情况：
	- 一种是readme.txt自修改后还没有被放到暂存区，现在，撤销修改就回到和版本库一模一样的状态；
	- 一种是readme.txt已经添加到暂存区后，又作了修改，现在，撤销修改就回到添加到暂存区后的状态。
	- 总之，就是让这个文件回到最近一次git commit或git add时的状态。

---
	场景1：当你改乱了工作区某个文件的内容，想直接丢弃工作区的修改时，用命令git checkout -- file。
	场景2：当你不但改乱了工作区某个文件的内容，还添加到了暂存区时，想丢弃修改，分两步，第一步用命令git reset HEAD file，就回到了场景1，第二步按场景1操作。
	场景3：已经提交了不合适的修改到版本库时，想要撤销本次提交，参考版本回退一节，不过前提是没有推送到远程库。
######2.5.删除文件
- rm xxx：删除xxx文件；
- git rm xxx 并 git commit -m "remove xxx"：1.从版本库中删除该文件
- git checkout -- xxx：2.删错了，因为版本库里还有呢，所以可以很轻松地把误删的文件恢复到最新版本

---
* 注：git checkout其实是用版本库里的版本替换工作区的版本，无论工作区是修改还是删除，都可以“一键还原”。
#####3.远程仓库
- 1.创建SSH Key：
	- 在用户主目录下，看看有没有.ssh目录，如果有，查看这个目录下有没有id_rsa和id_rsa.pub这两个文件，如果已经有了，可直接跳到下一步。
	- 如果没有，打开Shell（Windows下打开Git Bash），创建SSH Key：
		- ssh-keygen -t rsa -C "youremail@example.com"然后一路回车，使用默认值即可
- 2.登陆GitHub，在setting中“SSH Keys”添加公钥id_rsa.pub；
######3.1.添加远程库：在GitHub创建一个同名Git仓库，并且让这两个仓库进行远程同步
- 1.首先，登陆GitHub，然后，在右上角找到“Create a new repo”按钮，创建一个仓库(与本地同名)(全部默认)；
- 2.成功后这个仓库是空的，GitHub告诉我们，可以从这个仓库克隆出新的仓库，也可以把一个已有的本地仓库与之关联，然后，把本地仓库的内容推送到GitHub仓库
- 3.这里运行推送本地的命令：
	- git remote add origin https://github.com/zhengwei2531/myGit.git 关联
	- git push -u origin master 推送(由于远程库是空的，我们第一次推送master分支时，加上了-u参数，Git不但会把本地的master分支内容推送的远程新的master分支，还会把本地的master分支和远程的master分支关联起来，在以后的推送或者拉取时就可以简化命令。)
- 4.git push origin master：以后可以commit后运行这个命令来把本地master分支的最新修改推送至GitHub上；
######3.2.从远程库克隆
- git clone url
#####4.分支管理
######4.1.创建与合并分支
- git checkout -b dev：创建dev分支，然后切换到dev分支——git checkout命令加上-b参数表示创建并切换：
	- git branch dev：创建
	- git checkout dev：切换
- git branch：命令查看当前分支；
- git checkout master：在dev分支的工作完成后，可以用这个命令切换回master分支；
	- git merge dev：把dev分支的工作成果合并到master分支上，git merge命令用于合并指定分支到当前分支；
	- git branch -d dev：删除dev分支；

---
	Git鼓励大量使用分支：
	查看分支：git branch
	创建分支：git branch <name>
	切换分支：git checkout <name>
	创建+切换分支：git checkout -b <name>
	合并某分支到当前分支：git merge <name>
	删除分支：git branch -d <name>
######4.2.
feature