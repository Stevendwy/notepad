##git 命令

git clone 
    已经有一个远程 Git 版本库 克隆一份到本地
git remote -v 
    查看远程仓库
git remote add [name] [url] 
    添加远程仓库
git remote rm [name]
    删除远程仓库
git remote set-url —push [name] [newUrl]
    修改远程仓库
git pull [remoteName] [localBranchName]
    拉取远程仓库
git push [remoteName] [localBranchName]
    推送远程仓库    

*如果想把本地某个分支test提交到远程仓库，并作为远程仓库的master分支，或者另外一个名test分之下*

git push origin test:master //提交本地test 分支作为远程master分支
git push origin test:test //提交本地test 作为远程test 分支

2、版本操作相关命令
    git tag 查看版本
    git tag [name] 创建版本
    git tag -d [name] 删除版本
    git tag -r 查看远程版本
    git push origin [name] 创建远程版本
    git push origin :refs/tags/[name] 删除远程版本
    git pull origin —tags 上传本地tag 到远程仓库
    git tag -a [name] -m ‘yourMessage' 创建带注释的tag

3、git fetch <远程主机名>  将更新取回本地
    git fetch origin/master 将分支合并

4、git pull 取回远程主机某个分支
    git pull origin next:master 如果远程分支是与当前分支合并，则冒号后部分可以省略。

5、git push 命令将本地分支推送到远程主机
    git push <远程主机名><本地分支名><远程分支名>




git  init 和 git remote 
    当你本地创建了一个工作目录，可以进入该目录，使用 ‘git init’进行初始化，
git 以后就会对该文件进行版本控制，这时候你需要将它放到远程服务器上，可以在远程服务器上创建一个目录，并把访问的url 记录下来，此时就可以利用’git remote add’ 来增加一个远程服务器端
例如：git remote add origin git://github.com/someone/project.git
上面命令就是添加“git://github.com/someone/project.git” 命名为远程服务器，以后提交代码时候只使用 origin 别名即可