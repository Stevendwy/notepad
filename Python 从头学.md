##Python 从头学
python 运行环境
command + d 或者 quit（）退出

1、解释器
    python hello.py 指定了由python 解释器来执行
        如果想要类似 shell 脚本 执行 python，在头部添加指定解释器
            如： #！/usr/bin/env python 
                如此 执行./hello.py 即可

2、内容编码
    告诉解释器用那种编码来执行
        #-*- coding:utf-8 -*-

3、注释
    当行注释 ： #被注释内容
    多行注释：””” 被注释内容”””

4、执行脚本传入参数
    import sys 

5、变量定义规则
    1、只能是字母 数字 或下划线 组合
    2、第一个字符不能是数字
    3、关键字不能为变量名

6、输入
     name = raw_input('请输入用户名：’)
            输入密码时候，不可见 用getpass 模块
                    import getpass
                    pwd = getpass.getpass('请输入密码’)

7、流程控制和缩进
  1、用户登录验证    
    # 提示输入用户名和密码
    # 验证
    #    错误 输出用户名和错误密码
    #    正确 输出欢迎
        import getpass
        
        name = input (‘请输入用户名：’)
        pwd = getpass.getpass('请输入密码：’)

        if name == ‘abc’ and pwd == ‘abc’
            print  “欢迎”
        else:
            print “输入错误”
    2、根据用户输出起权限
        #    alex 超级管理员
        #     eric 普通用户
        name = input('请输入用户：’)
        
        if name == ‘alex’:  
            print ('超级用户’)
        else name == ‘eric’:
            print (‘普通管理员’)
        elif name == ’tony’:
            print （’主管）
        else :
            print '普通用户'   
    
8、基本数据类型
    1、数字
            int      (整型)
            lone     (长整型)
            float     (浮点型)
            complex     (复数)
    2、布尔值
            真或假
            1 或者 0
    3、字符串
            “hello”
            name = “alex”
            print “i am %s”  % name
            输出： i am alex
    4、列表
            name_list = [‘aaa’,’bbb’,’ddd’]
            或者 name_list = list([‘aaa’,’bbb’,’ccc’])
    5、字典无序
            person = {‘aa’:’aas’,’bb’:’bbb’}
            或者 person = dict({’name’:’mr’,’age’:’age’})


文本操作

1、打开文件     存在则覆盖 不然就创建
    file_obj = file(‘文件路径’,’模式’)
        r  只读方式打开
        w 只用于写入
        a 用以追加 
        w+     用于读写 
2、一次性加载所有内容到内存
        obj.read()
    一次加载内容到内存 根据行分割成字符串
        obj.readlines()
     每次仅读取一行数据
        for line in obj:
3、写文件内容
        obj.write('内容’)
4、关闭句柄
        obj.close()