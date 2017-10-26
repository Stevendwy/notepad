##webpack + react
 ###webpack + react 项目搭建
    
**创建项目**

    mkdir xxxxx 创建目录 
    
    cd xxxxx 进入目录
    
    npm init 创建
    
    touch .gitignore 添加忽略文件
    
    touch webpack.config.js
    
**配置依赖**
    
>webpack 相关包 
    
    npm install webpack webpack-dev-server html-webpack-plugin --save-dev    

>css\scss 样式文件 图片
    
    npm install css-loader style-loader sass-loader node-sass --save-dev
    npm install file-loader url-loader --save-dev

>babel\react\es6 支持包
    
    npm install babel-core babel-loader babel-preset-es2015 babel-preset-react --save-dev
    npm install jshint jshint-loader --save-dev
    npm install react react-dom --save
    npm install bootstrap@4.0.0-alpha.2 --save-dev
    
**配置webpack**
    
    var path = require('path');
    var webpack = require('webpack');
    var HtmlwebpackPlugin = require('html-webpack-plugin');
    
    var ROOT_PATH = path.resolve(__dirname);
    var APP_PATH = path.resolve(ROOT_PATH, 'app');
    var BUILD_PATH = path.resolve(ROOT_PATH, 'build');
    var TEM_PATH = path.resolve(ROOT_PATH, 'templates');
    
    module.exports= {
      entry: {
        app: path.resolve(APP_PATH, 'index.jsx'),
        mobile: path.resolve(APP_PATH, 'mobile.jsx'),
        vendors: ['jquery', 'moment']
      },
      output: {
        path: BUILD_PATH,
        filename: '[name].js'
      },
      resolve: {
        extensions: ['', '.js', '.jsx']
      },
      //启动dev source map，出错以后就会采用source-map的形式直接显示你出错代码的位置。
      devtool: 'eval-source-map',
      //enable dev server
      devServer: {
        historyApiFallback: true,
        hot: true,
        inline: true,
        progress: true,
        //只要配置dev server map这个参数就可以了
        proxy:{
          '/api/*':{
            target: 'http://localhost:8080',
            secure: false
          }
        }
      },
      //babel重要的loader在这里
      module: {
        //loader前执行处理，这样每次npm run start的时候就可以看到jshint的提示信息
        preLoaders: [
           {
             test: /\.jsx?$/,
             include: APP_PATH,
             loader: "jshint-loader"
           }
         ],
        loaders: [
          {
            test: /\.jsx?$/,
            loader: 'babel',
            include: APP_PATH,
            query: {
              //添加两个presents 使用这两种presets处理js或者jsx文件
              presets: ['es2015', 'react']
            }
          },
          {
            test: /\.scss$/,
            loaders: ['style', 'css', 'sass']
          }
        ]
      },
      //配置jshint的选项，支持es6的校验
       // any jshint option http://www.jshint.com/docs/options/
       jshint: {
         "esnext": true
       },
      plugins: [
        //这个使用uglifyJs压缩你的js代码
        new webpack.optimize.UglifyJsPlugin({minimize: true}),
        new HtmlwebpackPlugin({
          title: 'My first react app',
          template: path.resolve(TEM_PATH, 'index.html'),
          filename: 'index.html',
          chunks: ['app', 'vendors'],
          inject: 'body'
        }),
        new HtmlwebpackPlugin({
          title: 'Hello Mobile app',
          template: path.resolve(TEM_PATH, 'mobile.html'),
          filename: 'mobile.html'
        }),
        //把入口文件里面的数组打包成verdors.js
        new webpack.optimize.CommonsChunkPlugin('vendors', 'vendors.js')
      ]
    }

**npm 添加webpack启动命令**
    
    在package.json 中添加

    ···
          "scripts": {
            "dev": "webpack-dev-server --progress --profile --colors --hot --inline",
            "build": "webpack --progress --profile --colors",
            "test": "test",
          },
    ···

**添加react transform支持**
    
    安装
        
        npm install babel-plugin-react-transform --save-dev`
        npm install react-transform-hmr --save-dev
        npm install --save-dev react-transform-catch-errors redbox-react
        npm install babel-preset-react-hmre --save-dev

    
    将支持 HMR 和 Catch Error 的 present 添加到 .babelrc
        
        {
    //添加两个presents 使用这两种presets处理js或者jsx文件
    presets: ['es2015', 'react'],
    //在开发的时候才启用HMR和Catch Error
    "env": {
       "development": {
         "presets": ["react-hmre"]
       }
    }
    } 


###使用webpack
1、npm init
2、项目中安装webpack 
    npm install --save-dev webpack
3、配置webpack.config.js
    
###安装和配置
**安装**
    
    $npm install webpack -g
    常规项目把依赖 package.json 包
     $npm init
     $npm install webpack --save-dev
     
     webpack 配置过程中注意：
     loader: 'babel-loader?presets[]=es2015&presets[]=react' 这样写会 爆出module 无法找到的错误，将格式修改为：
     loader: "babel-loader",
                query: {
                    presets: ["es2015", "react"]
                }
       保证正确输出

**配置**
    
    每个项目都配置一个 webpack.config.js 告诉webpack 干什么
    
    示例：
    
    var webpack = require('webpack');
    var commonsPlugin = new webpack.optimize.CommonsChunkPlugin('common.js');
     
    module.exports = {
        //插件项
        plugins: [commonsPlugin],
        //页面入口文件配置
        entry: {
            index : './src/js/page/index.js'
        },
        //入口文件输出配置
        output: {
            path: 'dist/js/page',
            filename: '[name].js'
        },
        module: {
            //加载器配置
            loaders: [
                { test: /\.css$/, loader: 'style-loader!css-loader' },
                { test: /\.js$/, loader: 'jsx-loader?harmony' },
                { test: /\.scss$/, loader: 'style!css!sass?sourceMap'},
                { test: /\.(png|jpg)$/, loader: 'url-loader?limit=8192'}
            ]
        },
        //其它解决方案配置
        resolve: {
            root: 'E:/github/flux-example/src', //绝对路径
            extensions: ['', '.js', '.json', '.scss'],
            alias: {
                AppStore : 'js/stores/AppStores.js',
                ActionType : 'js/actions/ActionType.js',
                AppAction : 'js/actions/AppAction.js'
            }
        }
    };
    
**运行webpack**

    $webpack --display-error-details 
    后面的 "--display-error-details" 推荐加上，方便出错时候查阅更详尽的信息
    
    其他参数有
        
    $ webpack --config XXX.js   //使用另一份配置文件（比如webpack.config2.js）来打包
     
    $ webpack --watch   //监听变动并自动打包
     
    $ webpack -p    //压缩混淆脚本，这个非常非常重要！
     
    $ webpack -d    //生成map映射文件，告知哪些模块被最终打包到哪里了
    
####在寻常页面和脚本怎么使用
**html**
    
    <!DOCTYPE html>
    <html>
    <head lang="en">
      <meta charset="UTF-8">
      <title>demo</title>
    </head>
    <body>
      <script src="dist/js/page/common.js"></script>
      <script src="dist/js/page/index.js"></script>
    </body>
    </html>        
     
     样式会动态生成并打到 head 里
     
**js**
    
    require('../../css/reset.scss'); //加载初始化样式
    require('../../css/allComponent.scss'); //加载组件样式
    var React = require('react');
    var AppWrap = require('../component/AppWrap'); //加载组件
    var createRedux = require('redux').createRedux;
    var Provider = require('redux/react').Provider;
    var stores = require('AppStore');
     
    var redux = createRedux(stores);
     
    var App = React.createClass({
        render: function() {
            return (
                <Provider redux={redux}>
                    {function() { return <AppWrap />; }}
                </Provider>
            );
        }
    });
     
    React.render(
        <App />, document.body
    );