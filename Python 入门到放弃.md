##Python 入门到放弃
1、brew install python3   安装  （参考链接：http://www.jianshu.com/p/51811fa24752/）
2、which python3  查看是否安装成功
3、变量名指向实际对象，变量本身无类型  python 自动释放未引用的对象
4、python 将 0-255 的值放进缓存中

type 检查类型函数 

通用操作：
  改变某个元素值 s[i] = x
 改变特定范围内元素值 s[ i: j ] = t
                                       s[I : j: k] = t
删除元素  del s[I]   //   del s[ I:j]  // del s[ I : j : k]  
S.remove(x) 删除第一个匹配值  
S.clear() 清空序列

S.append(x) 追加元素
S.extent(x) 扩展序列
S.insert(I,x) 插入元素
Pop()弹出并删除某元素
S.reverse() 反转序列

版本3 中打印加 括号
chmod +x test.py     # 脚本文件添加可执行权限

python 转义字符
    \（在行尾） 续行符
    \a 响铃
    \b 退格    backspace
    \e 转义
    \t 横向制表符
    \v 纵向制表符
    \f 换页
    \other 其他字符以普通格式输出

python 运算符
    下表a 值为字符串”Hello” b为变量值：”Python”
*     重复输出字符串     a * 2 ‘HelloHello'
   [1]  通过索引获取字符串中字符  a[1] ‘e’
    [:] 截取字符中一部分 a[1:4] ‘ell’
    in 是否包含    “H” in a  True
    not in 通 in     ‘M’ not in a   True
    r/R 原始字符串 所有字符串都是按照字面意思使用 print r’\n’ \n

python 字符串内建函数
    string.capitalize() 
        把字符串的第一个字符大写
    string.center(width) 
        返回一个元字符串居中，并使用空格填充至长度width的新字符串
    string.count(str,beg=0,end=len(string)) 
        返回str在string 中出现的次数，如果beg 或者 end 指定返回内 str 出现次数
    string.lower() 
        转换string 中大写字符为小写
    string.lstrip()
        转换string 左边的空格
    max(str) 
        返回str 中最大的字母
    string.rfind(str,beg=0,end=len(string)) 
        类似find（） 不过是从右边开始查找
    string.rindex(width) 
        类似index（），不过是右边开始

python 脚本操作符
    len(1,2,3)             3                             长度
    [1,2,3]+[4,5,6]      [1,2,3,4,5,6]             组合
    [‘Hi’]*4                  [‘Hi’,’Hi’,’Hi’,‘Hi’]    重复
    3 in [1,2,3]            true                        是否存在
    for x in [1,2,3];print (x)  1 2 3             迭代


L[2] 读取列表中第三个元素
L[-2] 读取倒数第二个元素
L[1:]  从第二个元素开始截取列表


python 函数方法
    cmp(list1,list2) 
        比较两个列表的元素
    len(list)
        列表元素个数
    list(seq)
        将元组转换为列表
    list.append(obj)
        在列表末尾添加新对象
    list.count(obj)
        统计某个元素在列表中出现的次数
    list.index(obj)
        从列表找出匹配项的索引位置
    list.insert(index,obj)
        将对象插入列表
    list.pop(obj = list[-1])
        移除列表中一个元素（默认最后一个元素，并且返回该元素的值）
    list.remove(obj)
        移除列表中某个值的每一个匹配项
    list.reverse()
        反向列表中元素
    list.sort(func)
        对原列表进行排序


python 字典内置方法
    dict.clear()
        删除字典内所有元素
    dict.copy()
        返回一个字典的浅复制
    dict.fromkeys(seq[,val])
        创建一个新字典，以序列seq 中元素做字典的键，val 为字典所有键对应的初始值
    dict.get(key,default=None)
        返回指定键的值，如果不在字典中返回default值
    dict.items()
        以列表返回可遍历的(键，值) 元组数组
    dict.keys()
        以列表返回一个字典所有的键
    dict.update(dict2)
        把字典dict2的键/值对更新到dict里
    dict.values()
        以列表返回字典中的所有值
    pop(key[,default])
        删除字典给定键 key 所对应的值 key 必须给出，否则default 返回
    popitem()
        随机返回并删除字典中的一对键和值

python time 模块
    time.asctime([tupletime])
        接受时间元组并返回一个可读的形式为"Tue Dec 11 18:07:14 2008"（2008年12月11日 周二18时07分14秒）的24个字符的字符串。
    time.strptime(str,fmt='%a %b %d %H:%M:%S %Y’)
        根据fmt的格式把一个时间字符串解析为时间元组。
    time.tzset()
        根据环境变量TZ重新初始化时间相关的设置

    calendar.calenday(year,w=2,l=1,c=6)
        返回一个多行字符串格式的year年年历，3个月一行，间隔距离为c。 每日宽度间隔为w字符。每行长度为21* W+18+2* C。l是每星期行数
     calendar.firstweekday()
        返回当前每周起始日期的设置，默认情况下即星期一
    calendar.isleap(year)
        是闰年返回True 否则返回false
    calendar.leapdays(y1,y2)
        返回在Y1 Y2 时间段见的闰年总数
    calendar.month(year,month,w=2,l=1)
        返回一个多行字符串格式的year年month 月日历。
    calendar.setfirstweekday(weekday)
        设置每周的起始日期码，0(周一) 到6 （星期天)
    calendar.weekday(year,month,day)
        返回给定日期的日期码。0 （星期一） 到 6 （星期天），月份1 （一月） 到 12 （12月）

python 内置函数
    getattr(emp1,’age’)     #如果存在’age’ 属性返回True
    hasattr(obj,name)        #检查是否存在一个属性
    setattr(obj,name,value) #设置一个属性，如果属性不存在，会创建一个新属性
    delattr(obj,name)         #删除属性

python 内置类属性
    __dict__:类的属性，包含一个字典，由类的数据组成
    __doc__:类的文档字符串
    __name__:类名
    __module__:类定义所在的模块
    __bases__:类的所在父类构成元素


数据库
打开数据库 
    db = MySQLdb.connect(“localhost”,”testuser”,”test123”,”TESTDB”)
使用cursor() 获取操作游标
    cursor = db.cursor()
使用execute()方法执行SQL 语法
    cursor.ececute(“SELECT VERSION()”)
使用 fetchone（） 方法获取一条数据库
    data = cursor.fetchone()
关闭数据库连接
    db.close()

执行函数放在  main函数中 避免污染
def main():
    print (aaa())
if __name__ == ‘__main__’
    main()

函数参数   
  def power(x):
    return x*x
1、（x）    一个参数 位置参数
2、(x,n)      两个参数,位置参数
3、（x,n,city='hang’）     city 默认参数
        坑：def add_end(L=[]):
                    L.append(‘End’)
                    return L
                首次调用没有问题，第二次调用时候出错
           解析：Python函数在定义的时候 默认参数 l 被计算出，l 本身也是一变量，每次调用时候如果改变了l 默认参数就变了
       牢记：：：默认参数指向不变参数
        def add_end(L = None):
            if L is None:
                L = [ ] 
                L.append(‘end’)
            return L
4、可变参数
    参数前加 * 参数可以传入任意参数 包含0 个参数
5、**extra 表示把 extra 这个dict 把所有key-value 关键词参数传入 **kw 参数，注意：kw 获得的dict 是 extra 的一个拷贝，对kw 改动不影响 extra

参数定义顺序：必选参数、默认参数、可变参数、命名关键字参数、关键字参数

运算符：
    and
     or
    not 
    / 除法运算结果是浮点数 结果也是浮点数
    // 地板除 两个除法仍然是整数
    % 除法取余数
    ord() 获取字符的整数表示
    chr() 把编码转为字符

python 数据格式化
    % 运算符就是用来格式化字符串的，
    %s 表示用字符串替换，
    %d 表示整数替换 
    有几个 %? 占位符，后面就有几个变量，
    如果只有一个 %？ 括号可以省略
         格式化整数和浮点数 还可以指定是否补0 和整数 与小数的位数
                ‘%2d-%02d’ % (3,1)   == ‘ 3-01’
                ‘%.2f’ % 3.1415926     == ‘3.14’
    遇到% 为普通字符 用 %% 表示一个%

数据运算：
       L[0:3] 从索引 0 开始取 直到索引 3 为止 不包括索引 3
       L[-1]     取倒数第一个元素
       L[:10]     切取 前十位
       L[-10:]    后10位
        L[:10:2]    前十位，每两个取一个
        L[::5]        所有每5 取一
        L[:]        原样复制一个

python     for in  只要是可迭代对象都能用
    from collections import Iterable
    isinstance(“abs”,Iterable)    true 可迭代

[x*x for x in range()1,11) if x%2 ==0]        //把x*x 放在前面，后面跟for 循环
[m+n for m in ‘abs’ for n in ‘xyz’]             //使用两层循环，生成全排列