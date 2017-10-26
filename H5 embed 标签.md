##H5 embed 标签

 学习于：http://www.cnblogs.com/lgx5/p/5714494.html 感谢！

1、基本语法：<embed src=“your.mid”>
    embed 可以插入各种多媒体，格式可以是：MIDI、 WAV、AIFF、MP3 等

2、 属性 -- 语法 -- 代码 — 说明
    1、自动播放   autostart = true、false  true：音乐下载完后自动播放
        <embed src=“your.mid” autostart=true>
    2、循环播放  loop=正整数、true、false  true：循环播放，正整数为播放次数
        <embed src="your.mid" autostart=true loop=2>
    3、面板显示    hidden = true 、 no   默认为no 显示面板
        <embed src="your.mid" hidden=ture>  
    4、开始时间    starttime=mm：ss （分：秒） 未定义从文件开头播放
        <embed src="your.mid" starttime="00:10"> 
    5、音量大小    volume=0-100 之间的整数 该属性规定视频音量大小 未定义则使用系统设定
        <embed src="your.mid" volume="10”>
    6、容器属性    height = # width = #     取值为正整数或百分数 单位为像素 该属性控制面板的宽高
        <embed src="your.mid" height=200 width=200>
    7、容器单位    units=pixels 、 en     指定高度宽度单位 为en或者 pixels
        <embed src="your.mid" units="pixels" height=200 width=200>
    8、外观设置    controls = console     规定控制面板外观 默认：console
         console：一般正常面板；    smallconsole：较小的面板；    
         playbutton：只显示播放按钮； pausebutton：只显示暂停按钮；
         stopbutton：只显示停止按钮；volumelever：只显示音量调节按钮。
         <embed src="your.mid" controls=smallconsole> 
    9、对象名称    name= #     给对象取名 以便于其他对象使用 
         <embed src="your.mid" name="video”>
    10、说明文字    规定音频或者视频文件的说明文字
         <embed src="your.mid" title="第一首歌”>
    11、前景色和背景色    palette= color | color    color 第一个为前景色 第二个为背景色 
         <embed src="your.mid" palette="red|black”>
    12、对齐方式    align=top    该属性规定控制面板和当前行中对象的对齐方式
         center：控制面板居中；
         left：控制面板居左；
         right：控制面板居右；
         top：控制面板的顶部与当前行中的最高对象的顶部对齐；
         bottom：控制面板的底部与当前行中的对象的基线对齐；
         baseline：控制面板的底部与文本的基线对齐；
         texttop：控制面板的顶部与当前行中的最高的文字顶部对齐；
         middle：控制面板的中间与当前行的基线对齐；
         absmiddle：控制面板的中间与当前文本或对象的中间对齐；
         absbottom：控制面板的底部与文字的底部对齐。
          <embed src="your.mid" align=top>