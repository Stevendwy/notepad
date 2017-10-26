##React Redux
create-react-app 不支持mobx

1.安装 create-react-app
    npm install -g create-react-app
2.创建项目
    create-react-app demoname
    cd demoname
3.安装第三方模块
    npm install —save redux
    npm install —save react-redux
    npm install —save react-router
4.启动
    npm start


、@ 符号报错、
需要 babel-plugin-transform-decorators-legacy

@: es6 新增装饰器语法，babel 已支持需要安装 babel-plugin-transform-docorators-legacy
类的静态属性：es7 新增的语法，babel 已经支持，需安装 bable-preset-stage-2
@observer: 让React 组件自动起来，会自动更新
@observable：监听数据，当数据发生改变的时候自动刷新视图
@computed：创建自动运算的表达式
@action：改变了@observable 创建的数据，需要修饰action方法
autorun：当@observable 创建的数据发生改变时自动执行