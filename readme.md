######1.创建版本库
	初始化一个Git仓库，使用git init命令。
	添加文件到Git仓库，分两步：
	第一步，使用命令git add <file>，注意，可反复多次使用，添加多个文件；
	第二步，使用命令git commit，完成。
- mkdir xx ：创建一个名为xx的目录；
- pwd ：显示当前目录；
- git init ：把这个目录变成Git可以管理的仓库；
- git add命令告诉Git，把文件添加到仓库
	(git add xxx ：添加xxx,git add .：添加所有)
- git commit -m "xxx"：把文件提交到仓库，-m后面输入的是本次提交的说明