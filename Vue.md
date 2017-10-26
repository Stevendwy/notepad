##Vue
##vue start

>命令行工具：
    
**全局安装 vue-cli**

    $npm install --global vue-cli
    
**创建一个基于 webpack 的模板新项目**

    $vue init webpack my-project

**安装依赖**

    $cd my-project
    $npm install
    $npm run dev
    
###填坑过程

*1.空格*
    
    key value 之间对应用一个空格隔开，避免报错
    逗号后面换行，避免严格语法错误
    输入对象格式数据时候，要注意后面不要携带空格

**2.过滤器**
    
    {{message  | reverse | uppercase }} 

    自定义过滤器 
    Vue.filter('reverse', function (value) {
        return value.split('').reverse().join('')
    })
    
**vue-wechat**
    
    weixin 模仿代码
    
    放在GitHub oneget 中


##代码编辑过程中 空格报错
     webpack.base.conf.js 中注释以下内容

//    {
//      test: /\.(js|vue)$/,
//      loader: 'eslint-loader',
//      enforce: 'pre',
//      include: [resolve('src'), resolve('test')],
//      options: {
//        formatter: require('eslint-friendly-formatter')
//      }
//    },

 ##父子组件传值
###父给子 传值

1. 子组件在props 中创建一个属性，用以接受父组件传过来的值
2. 父组件中注册子组件
3. 在子组件标签中添加子组件props中创建的属性
4. 把需要传给子组件的值赋给该属性

###子给父 传值
 
1. 子组件需要以某种方式 例如点击事件来触发 一个自定义事件
2. 将需要传的值作为 $emit 的第二个参数 该值作为实参 传给响应自定义事件的方法
3. 在父组件中注册子组件 并在子组件标签上绑定自定义事件的监听

##this.$nextTick
    
<template>
<div class="hello">
<div ref="msgDiv">{{msg}}</div>
<div v-if="msg1">Message got outside $nextTick: {{msg1}}</div>
<div v-if="msg2">Message got inside $nextTick: {{msg2}}</div>
<div v-if="msg3">Message got outside $nextTick: {{msg3}}</div>
<button @click="changeMsg">
Change the Message
</button>
</div>
</template>

<script>
export default {
name: 'Helloworld',
data () {
return {
msg: 'Hello world',
msg1: '',
msg2: '',
msg3: ''
}
},
methods: {
changeMsg() {
this.msg = "Hello world"
this.msg1 = this.$refs.msgDiv.innerHTML
this.$nextTick(() => {
this.msg2 = this.$refs.msgDiv.innerHTML
})
this.msg3 = this.$refs.msgDiv.innerHTML
}
}
}
</script>