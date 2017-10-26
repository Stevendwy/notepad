##npm 相关
1、npm install -g 模块名称 全局安装
2、npm install 模块名称 本地安装

安装遇到权限不够：sudo 

3、npm install 模块： 安装好不写入package.json 中
4、npm install 模块 - - save ： 安装好写入package.json 的 dependencies中 （生产环境依赖）
5、npm install 模块 - - save - dev ： 安装好写入package.json 的 devDepencies 中（开发环境依赖）

删除全局模块
npm uninstall -g <package>
删除本地模块
npm uninstall 模块

删除本地模块时你应该思考的问题：是否将在package.json上的相应依赖信息也消除？
npm uninstall 模块：删除模块，但不删除模块留在package.json中的对应信息
npm uninstall 模块 --save 删除模块，同时删除模块留在package.json中dependencies下的对应信息
npm uninstall 模块 --save-dev 删除模块，同时删除模块留在package.json中devDependencies下的对应信息

6、npm 版本控制 Semantic versioning(语义化版本)

体现为：version :’x.y.z’
1、修复bug 小改动 增加 z
2、增加新特性，仍能向后兼容，增加y
3、大改动 无法向后兼容 增加x

7、通过 npm version <update_type> 自动改变版本
    update_type 为 patch 、minor、major 表示 补丁、小改、大改


《参考：http://www.cnblogs.com/penghuwan/p/6973702.html 》