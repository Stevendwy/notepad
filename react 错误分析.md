##react 错误分析
1、Target container is not a DOM element  或者叫： Minified react error
   可能性很大的原因是 js 引用顺序问题。创建dom的
js 放在了静态页面前了。

2、 阻止冒泡无用 注意引入 e 
    let _listChoose = this.listChoose.bind(this)
    <div  onClick={(e)=>_listChoose(item,e)}>{item}</div>