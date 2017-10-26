##react mobx
##知识点
1. @:es6新增的装饰器语法，babel已支持需要安装 babel-plugin-transform-decorators-legacy
2. 类的静态属性：es7新增语法，babel 已支持需安装 babel-preset-stage-2
3. @observer： 让React 组件自动起来，它会自动安装，即便是一个很大的程序也会工作的很好。
4. @observable：监听数据，当数据发生改变的时候自动刷新视图
5. @computed：创建自动运算的表达式
6. @action：改变了@observable 创建的数据，需要装饰action 方法 （需要配合‘use strict’ 使用，有助于更好的构建代码）
7. autorun： 当@observable 创建的数据发生改变时自动执行

Model/index.js

    'use strict';
    import { action, autorun, observable, computed } from "mobx";
    export default class TodoList {
        @observable todos = [{ title: "test", finished: true }];
        @observable data = [];
    　　 constructor(){
    　　　　autorun(()=>{console.log(this.unfinishedTodoCount)});
    　　 }
        @computed get unfinishedTodoCount() {
            return this.todos.filter(todo => !todo.finished).length;
        }
        @action getData() {
            fetch("http://localhost/Server/index.php").then(res => res.json()).then(data => this.data = data);
        }
        @action addList() {
            this.todos.push({ title: "test1", finished: false });
        }
    
    }
    
    
view/index.js

    import React,{Component} from "react";
    import ReactDOM from "react-dom"; 
    import {observer} from "mobx-react";
     
    import TodoList from "../Model/index";
    
    
    
    
    @observer
    class TodoListView extends Component {
        componentDidMount(){
            this.props.todoList.getData();
        }
        clickHandle(){
            this.props.todoList.addList();
        }
        render() {
            return <div>
                <ul>
                    {this.props.todoList.todos.map(todo =>
                        <TodoView todo={todo} key={todo.id} />
                    )}
                </ul>
                Tasks left: {this.props.todoList.unfinishedTodoCount}<br />
                姓名：{this.props.todoList.data.name}<br />
                年龄：{this.props.todoList.data.age}<br />
                密码：{this.props.todoList.data.pass}<br />
                <input name='name' type='button' value="按钮" onClick={this.clickHandle.bind(this)} />
            </div>
        }
    }
    
    const TodoView = observer(({todo}) =>
        <li>
            <input
                type="checkbox"
                checked={todo.finished}
                onClick={() => {return todo.finished = !todo.finished}}
            />{todo.title}
        </li>
    )
    
    const store = new TodoList();
    ReactDOM.render(<TodoListView todoList={store} />, document.getElementById('container'));
    

webpack.config.js
    
    var webpack = require('webpack');
    var commonsPlugin = new webpack.optimize.CommonsChunkPlugin('common.js');
    
    module.exports = {
        //插件项
        // plugins: [commonsPlugin],
        //页面入口文件配置
        entry: {
            index: './View/index.js'
        },
        //入口文件输出配置
        output: {
            path: 'dist/page',
            filename: '[name].js'
        },
        module: {
            //加载器配置
            loaders: [
                { test: /\.css$/, loader: 'style-loader!css-loader' },
                { test: /\.js$/, loader: 'babel-loader' },
                { test: /\.(png|jpg)$/, loader: 'url-loader' }
            ]
        },
    };

.babelrc
    
    {
        "presets": ["react", "es2015", "stage-2"],
        "plugins": [
            "transform-decorators-legacy"
        ]
    }
    
page/index.html
    
    <html>

    <head>
        <meta charset="utf-8" />
    </head>
    
    <body>
        <div id="container"></div>
        <script src="../dist/page/index.js"></script>
    </body>
    
    </html>