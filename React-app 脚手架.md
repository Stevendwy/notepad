##React-app 脚手架
###自动搭建
安装 create-react-app
    npm install -g create-react-app
    
创建项目
    create-react-app demo_name
    
运行项目
    npm install > npm start


###脚手架 react
    
    npm install -g create-react-app
    
    create-react-app my-app
    
    cd my-app/
    
    npm start


    
##ES6 react 组件生命周期

    import React,{Component} from 'react'
    export default class Life extends Component{
    
     constructor(props){
         super(peops)
         //初始化state 
         this.state={
             begin:begins
         }
     }
         
     componentWillMount(){}    //组件将要渲染到 真实dom
     
     componentDidMount(){}//组件已经插入到真是的dom 节点中
     
     shouldComponentUpdate(){}//组件是否要被重新渲染
     
     componentWillUpdate(){}//组件将要被重新渲染
     
     componentDidUpdate(){}//组件已经被重新渲染
     
     componentWillReceiveProps(){}//组件将要接受到新属性
     
     click1=（）=>{
         console.log("点击了单击事件")
     }
     render(){
         let _props = this.state.begin
         return (
             <div>
                 <h1 onClick={this.click1}>{_props}</h1>
             </div>
         )
     }
     
    } 
     
         
##React 在开发中常用结构

**demo 解析**
    
        import reqwest from 'reqwest';
        import React from 'react';
        import ReactDOM from 'react-dom';
        
        var Header = React.createClass({
           handleClick:function(){
             console.log(this.refs.head);
             console.log(ReactDOM.findDOMNode(this.refs.head));
           },
           render:function(){
             return (
              <div style={{ backgroundColor:'blue' }} onClick={ this.handleClick } ref='head'>
                <p>Header组件</p>
              </div>
             )
           }
        })
        
        var ComponentDemo = React.createClass({
        //默认state
          getInitialState() {
            return {
              current: 1,
              openKeys: [],
              result_data : {}
            };
          },
        //默认props
          getDefaultProps() {
              return {
                key:{
                  value:2
                }
              };
          },
          //静态方法  调用 ComponentDemo. getBusinessName()
          statics:{ 
             getBusinessName:function(){
               return console.log('getBusinessName方法被调用。。。')
             }
           },
          handleClick(e) {
             console.log('div被点击。。。');
             console.log(this.refs.cct);
             console.log(ReactDOM.findDOMNode(this.refs.cct))
          },
          componentDidMount: function() {
        
            //异步请求
            reqwest({
              url: 'http://localhost:90/menu',
              method: 'get',
              type: 'json'
            }).then(result => {
              if(this.isMounted()){
                this.setState({
                  result_data : result.data
                });
              }
              
            },function(err, msg){
               console.log(err)
               console.log(msg)
            });
        
            //使用props
            console.log(this.props.key.value)
        
          },
          componentWillReceiveProps(nextProps) {
              //接受新的props时候被触发
          },
          render() {
        
            return (
              <div>
                  <Header ref='cct'/>
                  <div style={{ height:'100%',width:200 }} className='btn'  onClick={ this.handleClick }>CCT部分</div>
              </div>
            );
          }
        })
        
        ReactDOM.render(<ComponentDemo />,
        document.getElementById('contain'));                    


>1.improt 引入方法，es6语法，也可用require
>
>2、Header 组件，组件的创建使用React.creatClass({}),es6 写法
>
>3、每个组件都需要一个 redner 函数，return 中只能包含一个顶层标签，我们一般用div包裹，且组件名称开头大写。
>
>4、refs 属性可以获取到真实DOM 结构，this.refs.XXX写法来获取react 结构。我们应该用 react-dom 提供的专门操作DOM 的方法：ReactDOM.findDOMNode(this.refs.XXX).
>
>5、react 最核心是状态机，getInitialState(只会在组件初始化的时候调用一次)就是用来初始化状态的，我们可以通过this.setState() 来修改状态，状态每次修改都会触发 render 函数。
>
>6、getDefaultProps 这个函数可以帮助设置一个不变的数据结构，相当于定义了一个常量。
>
>7、statics 就是用来顶一个静态方法的，我们可以定义各种函数，并通过 ComponentDemo.getBusinessName() 方法来调用。结构为： 祖建明.函数名
>
>8、最重要的事件机制也是存在的，如: onClick
>
>9、componentDidMount(只会在组件渲染结束后调用一次)，这个函数就是跟组件的生命周期相关了，我们一般会在里面进行异步的请求之类操作。
>componentWillMount (只会在组件初始化渲染之前调用一次)，理解为 开始和离开的 钩子，
> shouldComponentUpdate(object nextProps,boject nextState)(在函数有新的props 或 state 的时候触发) 这个钩子会主要管理组件是否更新，返回是布尔值。
>
>10、组件需要css 润色，这里添加style 必须为对象形式，如果是数字，默认单位 px，其他属性用 驼峰命名
>
>11、isMounted() 用来判断组件是否已经插入 DOM，一般请求在判断是否插入后操作 state。
>*绝对不要直接改变 this.state，因为在之后调用 setState() 可能会替换掉你做的更改。把 this.state 当做不可变的。*

*setState() 不会立刻改变 this.state，而是创建一个即将处理的 state 转变。在调用该方法之后获取 this.state 的值可能会得到现有的值，而不是最新设置的值。*

*不保证 setState() 调用的同步性，为了提升性能，可能会批量执行 state 转变和 DOM 渲染。*

*setState() 将总是触发一次重绘，除非在 shouldComponentUpdate() 中实现了条件渲染逻辑。如果使用可变的对象，但是又不能在 shouldComponentUpdate() 中实现这种逻辑，仅在新 state 和之前的 state 存在差异的时候调用 setState() 可以避免不必要的重新渲染*

###兄弟组件传值回调

    <!--参看运营数据-->
    this.props.typeChoose(_type, (data) => console.log(data))//给上层传状态

####this.props.children

>this.props.children 表示组件的所有子节点 

    
    var NotesList = React.createClass({
      render: function() {
        return (
          <ol>
          {
            React.Children.map(this.props.children, function (child) {
              return <li>{child}</li>;
            })
          }
          </ol>
        );
      }
    });

    ReactDOM.render(
      <NotesList>
        <span>hello</span>
        <span>world</span>
      </NotesList>,
      document.body
    );
    
    输出： 1.hello
            2.world