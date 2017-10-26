##coffce-Pjax

 coffee-pjax 可以将页面所有的跳转替换为AJAX 请求，把网站改造成单页面。《note：由于浏览器限制，pjax 需要在服务器环境下使用，即不不要使用file://xxx.html 运行》

###有何用处
*  可以在页面切换间平滑过渡，增加Loading 动画
* 可以在各个页面间传递数据，不依赖Url
* 可以选择性的保留状态，如音乐网站，切换页面时不停止播放。
* 所有的标签都可以用来跳转，不仅仅是a标签。
* 避免的公共js 的反复执行，如无需各个页面的登录判断。
* 减少了请求体积，节省流量，加快页面响应速度。
* 平滑降级到低版本浏览器上，对seo 也不会影响。

###兼容性
    当代浏览器基本全部支持

如何使用
    ###安装：npm install coffce-pjax

引入
    //使用全局变量
    var  pjax = window.CoffcePJAX

     //使用commonJS 或者 AMD 
    var pjax = require(“coffce-pjax”)

###简单配置
    pjax.init({
    //替换新页面内容的容器
    container：“body”,
    //是否低版本浏览器使用hash
    hash:true
})

###完整配置：
    pjax:init({
        // 选择器，支持querySelector选择器
    selector: "a",
    // 要替换内容的容器，可为选择器字符串或DOM对象
    container: "body",
    // 是否在前进后退时开启本地缓存功能
    cache : true,
    // 是否对低版本浏览器启用hash方案，不启用此项的低版本浏览器则会按照普通模式跳转
    hash: false,
    // 是否允许跳转到当前相同URL，相当于刷新
    same: true,
    // 调试模式，console.log调试信息
    debug: false,
    
    // 各个执行阶段的过滤函数，返回false则停止pjax执行
    filter: {
        // 选择器过滤，如果querySelector无法满足需求，可以在此函数里二次过滤
        selector: function(a) {},
        // 接收到ajax请求返回的内容时触发
        content: function(title, html) {}
    },
    // 各个阶段的自定义函数，将代替默认函数
    custom: {
        // 自定义更换页面函数，可以在此实现动画效果等
        append: function(html, container) {}
    },
    // 要监听的事件，相当于pjax.on(...)，事件列表看下面
    events: {}
})


接口
    
    /**
     * 初始化
     * @param {Object} options 配置，详情见上面↑
     */
    pjax.init(config);

    //注销插件，一般来说不需要使用这个方法
    pjax.destroy();

   /**
     * 使用pjax跳转到指定页面
     * @param {String}   url
     * @param {Object}   data     要传到新页面的参数，可以为null或        undefined
     * @param {Function} callback 请求成功时的回调，可以为null或undefined
     */
    pjax.turn(url, data, callback);

    /**
     * 监听事件，事件类型见下面↓
     * @param {String}   type     事件类型
     * @param {Function} listener 回调
     * @param {String}   url      只监听某个url，可以是相对和绝对路径
     */
    pjax.on(type, listener);
    pjax.on(type, url, listener);    

    /**
     * 解除监听
     * @param {String} type 事件类型
     * @param {String} url  只监听某个url，可以是相对和绝对路径
     */
    pjax.off(type);
    pjax.off(type, url);


    /**
     * 触发事件
     * @param {String} type 事件类型
     * @param {Object} args 参数
     */
    pjax.trigger(type, args);


事件
    
###监听事件
    //通过接口监听
    pjax.on(type,url,function);
    pjax.on(type,function);

    //通过配置监听
    pjax.init({
    events:{
    type:function(){}
    }    
})

###事件类型init
    在每个页面加载完成后触发，有一个object 参数：{title,html}

end
    在每个页面离开前触发

ajaxbegin
    在请求开始时触发。有一个object参数：{url,fnb,data,xhr}
    url 表示新页面的url
    fnb 表示是否有浏览器前进后退触发
    data表示传到新页面的数据
    xhr 是请求XMLHttpRequest() 实例

ajaxSuccess
    在请求成功后触发。参数与begin 一样

ajaxerror
    在请求失败后触发，参数与begin 一样

特性
    1、优先使用标签上的data-coffce-pjax-href 其次使用href
    2、标签上若有data-coffce-pjax 属性，将作为data 属性传递到新页面
    
    //将跳转到b.html ，并传递字符串data
    <a href="a.html" data-coffce-pjax-href="b.html" data-coffce-pjax="data"></a>

服务器配合
    *对于pjax 请求，服务器并不需要返回完整HTML ，只返回变动的Content 部分即可，对于普通请求，怎需要返回完整HTML
    *conffce-pjax 发送请求时，会带上请求头Coffce-pjax：true ,可以依次来判断当前请求是pjax 请求还是普通请求
    *由于没有返回完整的html，服务器应该将document.title 放在请求头coffce-pjax-title里。