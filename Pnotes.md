<table><tr><td bgcolor=#C7EDCC>
<font size=4>
from:https://www.liaoxuefeng.com/wiki/001374738125095c955c1e6d8bb493182103fac9270762a000
#Python 2.7 学习笔记
##1.第一个Python程序
###1.1 使用文本编辑器
	使用notepad++编辑并保存为*.py文件
+ 确保python执行文件已经加入环境变量；
+ 使用python *py命令即可执行python文本；
+ 还可以使用JetBrains PyCharm 2017.2.3 x64完成代码编辑运行。
###1.2 输入和输出
	>>> print 'hello, world'
	hello, world
	
	>>>print 'The quick brown fox', 'jumps over', 'the lazy dog'
	The quick brown fox jumps over the lazy dog
	
	name = raw_input('please enter your name: ')
	print 'hello,', name
+ print语句也可以跟上多个字符串，用逗号“,”隔开，就可以连成一串输出；
+ 用exit()退出Python;
+ raw_input和print是在命令行下面最基本的输入和输出。

##2.Python基础
	# print absolute value of an integer:
	a = 100
	if a >= 0:
	    print a
	else:
	    print -a
+ 以#开头的语句是注释，注释是给人看的，可以是任意内容，解释器会忽略掉注释。其他每一行都是一个语句，当语句以冒号“:”结尾时，缩进的语句视为代码块。 
###2.1数据类型和变量
	#多行字符串：
	>>> print '''line1
	... line2
	... line3'''
	line1
	line2
	line3
	#布尔类型
	>>> True
	True
	>>> False
	False
	>>> 3 > 2
	True
	#动态语言中的变量
	a = 123 # a是整数
	print a
	a = 'ABC' # a变为字符串
	print a
	#常量
	PI = 3.14159265359
	但事实上PI仍然是一个变量，Python根本没有任何机制保证PI不会被改变，所以，用全部大写的变量名表示常量只是一个习惯上的用法。
####2.1.1数据类型
+ 整数(1,100,0x3f)
+ 浮点数(3.14,-9.01,0.000012可以写成1.2e-5)
+ 字符串('',"","I'm Ok!",'I\'m \"OK\"!')
**注："\"为转义字符 \n表示换行，\t表示制表符，字符\本身也要转义，所以\\表示的字符就是\ 
**如果字符串内部有很多换行，用\n写在一行里不好阅读，为了简化，Python允许用'''...'''的格式表示多行内容,多行字符串'''...'''还可以在前面加上r使用;
+ 布尔值（在Python中，可以直接用True、False表示布尔值（请注意大小写），也可以通过布尔运算计算出来，布尔值可以用and、or和not运算。）
+ 空值（None不能理解为0，因为0是有意义的，而None是一个特殊的空值）

+ 常量（在Python中，通常用全部大写的变量名表示常量）
####2.1.2变量
+ 变量（变量名必须是大小写英文、数字和_的组合，且不能用数字开头。
在Python中，等号=是赋值语句，可以把任意数据类型赋值给变量，同一个变量可以反复赋值，而且可以是不同类型的变量。）
	这种变量本身类型不固定的语言称之为动态语言，与之对应的是静态语言。静态语言在定义变量时必须指定变量类型，如果赋值的时候类型不匹配，就会报错。
###2.2字符串和编码、格式化
####2.2.1字符串和编码
	#Python提供了ord()和chr()函数，可以把字母和对应的数字相互转换；
	>>> ord('A')
	65
	>>> chr(65)
	'A'

	>>> print u'中文'
	中文
	>>> u'中'
	u'\u4e2d'
	#把u'xxx'转换为UTF-8编码的'xxx'用encode('utf-8')方法：
	>>> u'ABC'.encode('utf-8')
	'ABC'
	>>> u'中文'.encode('utf-8')
	'\xe4\xb8\xad\xe6\x96\x87'
	#把UTF-8编码表示的字符串'xxx'转换为Unicode字符串u'xxx'用decode('utf-8')方法：
	>>> 'abc'.decode('utf-8')
	u'abc'
	>>> '\xe4\xb8\xad\xe6\x96\x87'.decode('utf-8')
	u'\u4e2d\u6587'
	>>> print '\xe4\xb8\xad\xe6\x96\x87'.decode('utf-8')
	中文

	#len()函数可以返回字符串的长度：
	>>> len(u'ABC')
	3
	>>> len('ABC')
	3
	>>> len(u'中文')
	2
	>>> len('\xe4\xb8\xad\xe6\x96\x87')
	6
	#当Python解释器读取源代码时，为了让它按UTF-8编码读取，我们通常在文件开头写上这两行：
    #!/usr/bin/env python 
    # -*- coding: utf-8 -*-
+ ASCII编码和Unicode编码的区别：ASCII编码是1个字节，而Unicode编码通常是2个字节；
+ 因为Python的诞生比Unicode标准发布的时间还要早，所以最早的Python只支持ASCII编码，普通的字符串'ABC'在Python内部都是ASCII编码的。
+ Python在后来添加了对Unicode的支持，以Unicode表示的字符串用u'...'表示；
+ 字符串'xxx'虽然是ASCII编码，但也可以看成是UTF-8编码，而u'xxx'则只能是Unicode编码。
+ 英文字符转换后表示的UTF-8的值和Unicode值相等（但占用的存储空间不同），而中文字符转换后1个Unicode字符将变为3个UTF-8字符，你看到的\xe4就是其中一个字节，因为它的值是228，没有对应的字母可以显示，所以以十六进制显示字节的数值。
####2.2.2格式化
%运算符就是用来格式化字符串的。在字符串内部，%s表示用字符串替换，%d表示用整数替换，有几个%?占位符，后面就跟几个变量或者值，顺序要对应好。如果只有一个%?，括号可以省略。

	>>> 'Hello, %s' % 'world'
	'Hello, world'
	>>> 'Hi, %s, you have $%d.' % ('Michael', 1000000)
	'Hi, Michael, you have $1000000.'
常见的占位符有：
	
	%d	整数
	%f	浮点数
	%s	字符串
	%x	十六进制整数
格式化整数和浮点数还可以指定是否补0和整数与小数的位数;

	>>> '%2d-%02d' % (3, 1)
	' 3-01'
	>>> '%.2f' % 3.1415926
	'3.14'
有些时候，字符串里面的%是一个普通字符怎么办？这个时候就需要转义，用%%来表示一个%。

	>>> 'growth rate: %d %%' % 7
    'growth rate: 7 %'
###2.3使用list和tuple
####2.3.1 list
比如，列出班里所有同学的名字，就可以用一个list表示：

	>>> classmates = ['Michael', 'Bob', 'Tracy']
	>>> classmates
	['Michael', 'Bob', 'Tracy']
变量classmates就是一个list。用len()函数可以获得list元素的个数：

	>>> len(classmates)
	3
如果要取最后一个元素，除了计算索引位置外，还可以用-1做索引，直接获取最后一个元素：

	>>> classmates[-1]
	'Tracy'
以此类推，可以获取倒数第2个、倒数第3个：

	>>> classmates[-2]
	'Bob'
	>>> classmates[-3]
	'Michael'
list是一个可变的有序表，所以，可以往list中追加元素到末尾：

	>>> classmates.append('Adam')
	>>> classmates
	['Michael', 'Bob', 'Tracy', 'Adam']
也可以把元素插入到指定的位置，比如索引号为1的位置：

	>>> classmates.insert(1, 'Jack')
	>>> classmates
	['Michael', 'Jack', 'Bob', 'Tracy', 'Adam']
要删除list末尾的元素，用pop()方法：

	>>> classmates.pop()
	'Adam'
	>>> classmates
	['Michael', 'Jack', 'Bob', 'Tracy']
要删除指定位置的元素，用pop(i)方法，其中i是索引位置：

	>>> classmates.pop(1)
	'Jack'
	>>> classmates
	['Michael', 'Bob', 'Tracy']
要把某个元素替换成别的元素，可以直接赋值给对应的索引位置：

	>>> classmates[1] = 'Sarah'
	>>> classmates
	['Michael', 'Sarah', 'Tracy']
list里面的元素的数据类型也可以不同，比如：

	>>> L = ['Apple', 123, True]
list元素也可以是另一个list，比如：

	>>> s = ['python', 'java', ['asp', 'php'], 'scheme']
	>>> len(s)
	4
要注意s只有4个元素，其中s[2]又是一个list，如果拆开写就更容易理解了：

	>>> p = ['asp', 'php']
	>>> s = ['python', 'java', p, 'scheme']
要拿到'php'可以写p[1]或者s[2][1]，因此s可以看成是一个二维数组，类似的还有三维、四维……数组，不过很少用到。

如果一个list中一个元素也没有，就是一个空的list，它的长度为0：

	>>> L = []
	>>> len(L)
	0
####2.3.2 tuple
另一种有序列表叫元组：tuple。tuple和list非常类似，但是tuple一旦初始化就不能修改，比如同样是列出同学的名字：

	>>> classmates = ('Michael', 'Bob', 'Tracy')
现在，classmates这个tuple不能变了，它也没有append()，insert()这样的方法。其他获取元素的方法和list是一样的，你可以正常地使用classmates[0]，classmates[-1]，但不能赋值成另外的元素。

不可变的tuple有什么意义？因为tuple不可变，所以代码更安全。如果可能，能用tuple代替list就尽量用tuple。













