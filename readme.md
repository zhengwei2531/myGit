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
