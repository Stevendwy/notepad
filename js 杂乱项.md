##js 杂乱项
 1、正则 — 全局匹配变量
    string.replace(new RegExp(key,’g’),’b’);

2、react 插入带标签字符串
     dangerouslySetInnerHTML = {{__html:newwold}}

3、回滚到页面顶部
    $(“html,body”).animate({scrollTop:0},500)
    
    refs 方法： this.refs.toTop.scrollIntoView()