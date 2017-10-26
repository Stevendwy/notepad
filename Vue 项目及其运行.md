##Vue 项目及其运行
学习博客：
        后台管理：http://www.cnblogs.com/taylorchen/p/6083099.html
如何运行：https://github.com/lzxb/vue-cnode
饿了么  ：https://github.com/bailicangdu/vue2-elm


运行项目：
1.在github官网或者其他下载的项目.
2.安装node.js环境，安装npm,在运行项目之前检查版本号，防止项目使用中的冲突.
3.执行代码： npm install.
4.执行代码:  npm run dev.

新建项目：
1.准备，node,npm,vue-cli
2.创建项目 vue init  webpack   项目名
3.进入项目 npm install 或 cnpm install  下载依赖
4.执行npm run dev 启动项目
5.注意修改端口号,vue端口号位置：config/index.js下的 dev:{port};  需要重新生成文件。

// install vue-cli  安装依赖包
 npm install --g vue-cli
// 使用vue-cli初始化项目
 vue init webpack my-project
// install dependencies and go!
//进入项目目录
 cd my-project
//在项目中安装依赖包
 npm install
//运行项目
npm run dev


打包部署：
1.进入目录执行npm run build  （打包）
2.原文件里面生成dist为名的目录，进入删除csc和js文件夹多余的文件（.map的文件）
3.注意复制出来index.html里面引入的css和js文件路径。
4.部署到服务器上。