##React-router
##react-router
*内容参考：http://www.jianshu.com/p/0e54c6b6ab2b*

**1.组件传参的技巧**

第一：传送一些 onChange 什么的参数， {...this.props} 然后在父级的时候 传入。
第二：传送 input 的数据，用event ，在onChange 事件中，传event ，然后用event.target 来获取 input 的 DOM。

**2.关于url 传参的问题**

比如，想打开
    
    /repos/reactjs/react-router
    /repos/facebook/react

怎么处理？ 可以暂且定义这样：
    
    /repos/:userName/:repoName

>第一、路由怎么写？

    <Route path="/repos/:userName/:repoName" component={Repo} />

>第二、Link 怎么写？
    
    <Link to="/repos/reactjs/react-router">React</Link>

>第三、如何在页面获取参数
    
    <h2>{this.props.params.repoName}</h2>
    
**3.关于用 js 来实现页面路由跳转问题**

>在react-router 中，有两种方法：
>第一：使用 withRouter(),然后在内部获取 this.props.router
>第二：使用 this.context.router ,不过在使用前必须定义这个类的 contextTypes。

*withRouter 怎么用？*
    
    ...
     import {withRouter} from 'react-router'
     class Abc extends Component {
                      ...
           this.props.router.push('/')
    }
    export default withRouter(Abc)    

*用context怎么用？*

    ...
    export default class Abc extends Component {
                      ...
           this.context.router.push('/')
    }
    Abc.contextTypes = {
           router: React.PropsTypes.object
    }