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
###2.2字符串和编码
+ 