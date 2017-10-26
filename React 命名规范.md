##React 命名规范
##命名
    
* 组件名称： 大驼峰
* 属性名称： 小驼峰
* 事件处理函数：handleSomething
* 自定义事件属性名称： onSomething = {this.handleSomething}
* key:不能使用组件index，构造或使用唯一的id
* 组件方法名称：避免使用下划线开头的命名

###js 书写规范
    
**自闭合**

    <Foo className="stuff"></Foo>
    <Foo className="stuff" />
    
**属性对其**
    
    //bad
    <Foo superLongParam="bar"
     anotherSuperLongParam="baz" />

    // good
    <Foo
        superLongParam="bar"
        anotherSuperLongParam="baz"
    />