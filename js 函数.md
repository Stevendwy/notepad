##js 函数
 ###js 

**函数语法**
显示一个时钟：
    
    function startTime()
    {
    var today=new Date()
    var h=today.getHours()
    var m=today.getMinutes()
    var s=today.getSeconds()
    // add a zero in front of numbers<10
    m=checkTime(m)
    s=checkTime(s)
    document.getElementById('txt').innerHTML=h+":"+m+":"+s
    t=setTimeout('startTime()',500)
    }
    
    function checkTime(i)
    {
    if (i<10) 
      {i="0" + i}
      return i
    }

**数组操作**

    For...In 声明来循环数组中元素
    
    concat() 合并两个数组
    
    join() 将元素组成一个字符串
    
    sort() 排序
    
    push() 数组末尾添加元素
    
    slice()从已有数组中返回选定元素
    
    shift() 删除数组第一个元素
    
**算数**
    
    random() 随机数 
    
    max() 最大数
    
    abs()绝对值
    
    ceil()对数进行上舍入
    
    floor()对数进行下舍入
    
    round()把数四舍五入为最接近的整数
    
    valueOf()    返回 Math 对象的原始值
    
**正则**
    
    RegExp 3个方法：test()、exec()、compile()
    
*test() 检索字符串中指定值，返回 true 或者 false*
    
    var patt1=new RegExp("e");

    document.write(patt1.test("The best things in life are free"));
    
    
*exec() 方法检索字符串中的指定值，没有返回null*
    
*compile() 用于改变RegExp*

*修饰符*

>修饰符 i 执行大小写不敏感的匹配
>
>g 执行全局匹配
>
>m 执行多行匹配

*方括号*

>[abc] 查找方括号之间的任何字符 
>
>[^abc] 查找任何不在方括号之间的字符
>
>[0-9] 查找任何 0 至 9 的数字
>
>[a-z] 查找任何从a 到 z 的字符 小写
>
>[adgk] 查找给定集合内的任何字符
>
>[^adgk]    查找给定集合外任何字符

*元字符*

元字符（Metacharacter）拥有特殊含义的字符

>\w 查找单词字符
>
>\W 查找非单词字符
>
>\d 查找数字
>
>\s 查找空白字符
>
>\b 匹配单词边界
>
>\B 匹配非单词边界
>    
    
*量词*

>n+ 包含至少一个 n 的字符串
>
>n? 匹配包含零个或一个 n 的字符串
>
>n{x} 包含x 个 n 的序列字符串
>
>n$ 匹配任何结尾为 n 的字符串
>
>^n 任何开头为 n 的字符串
>
>?=n 匹配任何后紧跟指定字符串 n 的字符串
>
>?!n 匹配任何其后没有紧接字符串n 的字符串


*支持正则表达式String 对象的方法*

>search 检索与正则表达式相匹配的值
>
>match 找到一个或多个正则表达式的匹配
>
>replace 替换与正则表达式匹配的子串
>
>split 把字符串分割为字符串数组
    
    
**window**

>screen.availWidth 可用的屏幕高度
>返回访问者屏幕的高度，以像素计算，减去界面特性。

* location.hostname 返回 web 主机的域名
    * location.pathname 返回当前页面的路径和文件名
    * location.port 返回 web 主机的端口 （80 或 443）
    * location.protocol 返回所使用的 web 协议（http:// 或 https://）
    *  window.navigator 对象包含有关访问者浏览器的信息

**match**
    
    匹配指定的字符，找到则返回该字符，没有则返回null
    
**replace**
    
    替换字符串中的字符