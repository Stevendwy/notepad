##npm module 发布
 1、新建文件夹owindow-first , cd 到该文件夹下 下载基础配置文件
    npm init
2、 创建一个index.js 文件，文件输入 exports  简单实例如下：
    module.exports = 12345678;
3、退出当前文件夹 登录npm
    npm login 《输入：用户名-密码-邮箱》
4、开始发布 
    npm publish owindow-first 
    《如果有发布失败：1、请参看修改npm源 ，修改npm 源为官网源
                                        2、查看所发布模块名称是否已经被使用》

附：1、发布完毕 可以在npm 网站上搜索查看
        2、发布24小时内可以删除
            npm - - force unpublish owindow-first
        3、即使撤销模块，发包的时候也不能再和撤销包名称和版本重复了
        4、模块名不能有大写字母、空格、下划线

《看你骨骼精奇，贡献社会大任就交给你了！》