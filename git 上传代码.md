##git 上传代码

  创建秘钥：ssh-keygen -C ‘your@email.address’ -t rsa

假设新建了一个项目，切换到根目录下
$ git status //查看当前文件状态
$ git add . //(.) 表示当前所有内容 交给git 管理及提交到本地git 仓库

$ git commit -m “new natter” //添加对修改内容的描述
$ git remote add origin git@github.comxxxxxx.git //第一次提交项目时候，与那个仓库连接

$ git remote -v //查看当前项目连接那个仓库
$ git push -u origin master //将本地项目提交到远程仓库



一般问题：

    输入：$ git remote add origin git@github.com:(账号名)/(项目名).git 
    提示如下错：fatal:remote origin already exists.

    解决方法：
        1、输入：$ git remote rm origin
        2、再输入： $ git remote add origin git@githum.com: (账号名)/(项目名).git  
        3、 如果输入 $ git remote rm origin 还是报错 error: Could not remove config section ‘remote.origin’ 我们需要修改 gitconfig文件内容
        4、找到gitconfig 文件 删除其中的 [remote ‘origin’] 删除

    如果输入：$ ssh -T git@github.com
    如下错误：Permission denied (publickey) . 新生成的key 不能加入ssh 导致连接不上guthub
    解决办法：
            1、输入 $ ssh-agent  再输入 $ ssh-add ~/.ssh/id_key 
           
    输入 $ git push origin master
    提示信息：error:failed to push som refs to ……
    解决办法：
            1、输入 $ git pull origin master 
            2、 再输入 $ git push origin master

            3、报错：fatal:Could’t find remote ref master  或者 fatal:’origin’ does not appear to be a git repository 以及 fatal:Coule not read from remote repository
            4、重新输入 $ git add origin git@github.com:(账号名)/(项目名).git



    本地创建项目过程：
        $ madir ~/hello-world //创建项目
        $ cd ~/hello-world  //打开项目
        $ git init         //初始化
        $ touch README  
        $ git add README  //更新readme 文件
        $ git commit -m ‘first commit’  // 提交更新 注释信息为 first commit
        $ git remote add origin git@github.com: (账号名)/(项目名).git  //连接远程项目
         $ git push -u origin master   //更新到github 项目中

《参考：http://www.cnblogs.com/xiaotaiyang/p/4581401.html》