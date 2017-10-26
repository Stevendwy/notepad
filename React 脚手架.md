##React 脚手架

搭建生成为 react  es6 webpack 项目
（未安装 node.js 直接看最后安装node.js 流程）

1、确保自己安装了node.js 然后全局安装 yeoman
    npm install -g yo

2、直接安装脚手架
    npm install -g generator-reactpackage

3、合适位置新建文件夹，在文件夹下运行
    yo reactpackage

4、npm run dev //项目开发过程用，启动服务，实时刷新
    npm run build //开发完成打包文件 ( js,css 分开打包)

5、本项目默认监听端口是8888 浏览器：http://localhost:8888 或者index.html 右键 到浏览器打开



错误 或 配置：
1、如果执行上述命令提示错误：Error: getaddrinfo ENOTFOUND localhost，在host文件里面添加127.0.0.1 localhost即可
2、监听端口和实时刷新的功能都能在webpack.config.js文件中修改配置

安装 node.js

1、 npm install -g n //首先安装n模块
2、n stable //升级Node.js 到最新稳定版
3、node -v //检查更新是否成功

4、修改npm 源为淘宝源 加快npm 下载速度 
    npm config set registry “https://registry.npm.taobao.org"