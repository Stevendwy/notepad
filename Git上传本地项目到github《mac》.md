##Git上传本地项目到github《mac》

 1、GitHub 上先创建一个项目
    new reponsitory

2、输入命令
    git init

3、配置ssh
    ssh-keygen -t rsa -C "jiayi_li10@163.com" (邮箱替换成你登录github的邮箱)
    例子：ssh-keygen -t rsa -C "bluedwy@126.com" (邮箱替换成你登录github的邮箱)

    这个地方请注意，它会在你选择的路径下上生成 ssh key，如果你直接点击回车，会在默认路径下创建 ssh 。如果你有多个项目，有工作的，有自己玩的，那么请配置不同的路径，或者一个路径换个文件名，我就用：/Users/lijiayi/.ssh/id_test_rsa 作为演示。输入路径之后点击回车

~/.ssh/id_rsa2 生成新的ssh key 文件名

4、此处输入密码：直接回车不输入
     密码设置：至少五位数 aa123456

5、将ssh 代码复制到剪切板作用代码：
    pbcopy < ~/.ssh/id_test_rsa.pub

6、回到gethub 点击》头像 点击》setting 点击》ssh and GPG keys 点击》new ssh key

    输入title 将ssh 代码复制到下面框中 生成

7、验证添加 ssh 成功 ssh -T git@github.com

8、当successfully之后，在 git config 里设置一下你的 github 登录名以及登陆邮箱，执行以下两个命令：

git config --global user.name "your name" 

git config --global user.email "your_email@youremail.com"

9、将项目代码拉到文件夹 执行命令 git status 可以看到项目的改动

10、执行 命令：git commit -m "第一次更新”
    然后执行：git remote add origin https://github.com/你的用户名/github项目名.git

11、如果出现错误：
    有如下几种解决方法：

    1.使用强制push的方法：$ git push -u origin master -f 

这样会使远程修改丢失，一般是不可取的，尤其是多人协作开发的时候。

2.push前先将远程repository修改pull下来：

$ git pull origin master

$ git push -u origin master

3.若不想merge远程和本地修改，可以先创建新的分支：$ git branch [name]

然后push：$ git push -u origin [name]