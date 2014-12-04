# 几分钟学习一门编程语言之Python篇 (最新)

>翻译自 `Learn X in Y Minutes: Where X = Python` [Learn X in Y Minutes: Where X = Python](https://github.com/adambard/learnxinyminutes-docs/blob/master/python.html.markdown)

Python由`Guido Van Rossum`发明于90年代初期，是当今最流行的编程语言之一，我深深被它清晰简洁的语法所折服并从此爱上了它。Python的代码之简洁，几乎就是可执行的伪代码。

若能提供给我们反馈，将非常欢迎！你可以通过推特@louiedinh或邮箱louiedinh AT gmail来联系我。

请注意：本文是专门针对Python 2.7的，但应该同样也适用于Python 2.x的。至于 Python 3.x，请阅读我们最新的指南 [Learn X in Y Minutes: Where X = Python 3](https://github.com/adambard/learnxinyminutes-docs/blob/master/python3.html.markdown)

```python
# 单行注释以"#"字符开头

""" 我们可以使用三个双引号（"）或单引号（'）来表示多行字符串，这种方法常用来来写多行注释。
"""

####################################################
## 1. 基本数据类型和操作符
####################################################

# 数字
3  # => 3

# 数学运算跟你想象中的并没有啥不同
1 + 1  # => 2
8 - 1  # => 7
10 * 2  # => 20
35 / 5  # => 7

# 除法跟想象中略有不同，它的结果会自动向下取整
5 / 2  # => 2

# 要想得到我们期望的除法，我们首先需要学习浮点数`floats`
2.0     # 这是一个浮点数
11.0 / 4.0  # => 2.75 啊哈...貌似结果好很多了

# 用双斜杠"//"做整型数除法，正负数都适用，结果会向下取整
5 // 3     # => 1
5.0 // 3.0 # => 1.0 # 对浮点数同样适用
-5 // 3  # => -2
-5.0 // 3.0 # => -2.0

# 取模运算
7 % 3 # => 1

# 指数(x的y次方)
2**4 # => 16

# 使用括号来增强计算的优先顺序
(1 + 3) * 2  # => 8

# 布尔运算 
# 注意 "and" 和 "or"大小写敏感
True and False #=> False
False or True #=> True

# 注意ints型跟布尔型的混用
0 and 2 #=> 0
-5 or 0 #=> -5
0 == False #=> True
2 == True #=> False
1 == True #=> True

# 用not来否定
not True  # => False
not False  # => True

# 表示相等用"=="
1 == 1  # => True
2 == 1  # => False

# 表示不等用"!="
1 != 1  # => False
2 != 1  # => True

# 更多比较操作
1 < 10  # => True
1 > 10  # => False
2 <= 2  # => True
2 >= 2  # => True

# 比较可以是级联的!
1 < 2 < 3  # => True
2 < 3 < 2  # => False

# 创建字符串用双引号“或者单引号'都行
"This is a string."
'This is also a string.'

# 字符串也可以相加！
"Hello " + "world!"  # => "Hello world!"

# ... 又或者相乘
"Hello" * 3  # => "HelloHelloHello"

# 字符串可以被认为是一系列字符组成的列表(list)
"This is a string"[0]  # => 'T'

# 百分号 % 用来格式化输出字符串
"%s can be %s" % ("strings", "interpolated")

# 还有一种新的方式来格式化输出字符串
# 我们推荐用这种方式
"{0} can be {1}".format("strings", "formatted")
# 如果你不喜欢用数字，也可以使用关键字参数
"{name} wants to eat {food}".format(name="Bob", food="lasagna")

# None也是一个对象
None  # => None

# 千万不要使用"=="来对一个对象和None作比较
# 正确的方法是用 "is"
"etc" is None  # => False
None is None  # => True

# 'is' 操作符用来比较俩对象的标识符(译者注:即内存地址)
# 它对于普通的数值比较不管用
# 但在处理对象比较时则很有用

# None, 0, 还有空字符串/列表在布尔运算中值都为False 
# 除此之外的其他值的布尔运算结果都是True
bool(0)  # => False
bool("")  # => False


####################################################
## 2. 变量和集合
####################################################

# 在所有2.x版本中，Python有一个print语句，但在Python 3里面被移除了
print "I'm Python. Nice to meet you!"
# Python还有一个print函数，只在python 2.7和python 3中有 
# 但是对于Python 2.7，你需要添加import(去掉前面的注释):
# from __future__ import print_function
print("I'm also Python! ")

# 给变量赋值前，无需事先声明
some_var = 5    # 变量的命名规范是用小写字母加下划线( lower_case_with_underscores)
some_var  # => 5

# 试图访问没有赋值的变量会抛出异常
# 参考”流程控制“部分来学习更多关于异常处理
some_other_var  # 会抛出一个NameError异常

# if可以作为表达式使用
"yahoo!" if 3 > 2 else 2  # => "yahoo!"

# 列表(Lists)用于存储一个序列(sequences）
li = []
# 你可以从一个预先填充好的列表开始
other_li = [4, 5, 6]

# 用append方法往列表末尾添加元素
li.append(1)    # li is now [1]
li.append(2)    # li is now [1, 2]
li.append(4)    # li is now [1, 2, 4]
li.append(3)    # li is now [1, 2, 4, 3]
# 用pop方法将元素从列表末尾删除
li.pop()        # => 返回3，li现在为[1, 2, 4]
# 让我们加回去
li.append(3)    # li现在又变回了[1, 2, 4, 3]

# 像访问任何数组一样访问列表的元素
li[0]  # => 1
# 用等号"="给已经初始化过的列表元素赋新值
li[0] = 42
li[0]  # => 42
li[0] = 1  # 注意：将li[0]的值赋值为原先的值
# 访问列表的最后一个元素的方法
li[-1]  # => 3

# 访问列表界外的元素会抛出一个IndexError异常
li[4]  # 抛出 IndexError

# 你可以使用切片语法来查看列表的一个区间
# （这个范围相当于数学中的左闭右开区间）
li[1:3]  # => [2, 4]
# 省略开头
li[2:]  # => [4, 3]
# 省略结尾
li[:3]  # => [1, 2, 4]
# 隔个选择
li[::2]   # =>[1, 4]
# 将列表反转
li[::-1]   # => [3, 4, 2, 1]
# 用下面的任意组合来完成高级的切片
# li[start:end:step]

# 用"del"从列表中删除任意元素
del li[2]   # li现在是[1, 2, 3]

# 列表可以相加
li + other_li   # => [1, 2, 3, 4, 5, 6]
# 注意: li和other_li的元素值并没有被改变

# 用"extend()"方法扩展(级联)列表
li.extend(other_li)   # 现在li是[1, 2, 3, 4, 5, 6]

# 查看列表中是否存在元素用"in"
1 in li   # => True

# 用"len()"检查列表长度
len(li)   # => 6


# 元祖(Tuples)和列表(lists)类似，只是它们"不可变"
tup = (1, 2, 3)
tup[0]   # => 1
tup[0] = 3  # 抛TypeError异常

# 你可以对元祖操作那些你操作列表的方法
len(tup)   # => 3
tup + (4, 5, 6)   # => (1, 2, 3, 4, 5, 6)
tup[:2]   # => (1, 2)
2 in tup   # => True

# 你可以将元祖(或者列表)元素分解后赋给几个变量
a, b, c = (1, 2, 3)     # a现在是1, b现在是2， c现在是3
# 如果你省略了括号，则元祖会被自动创建
d, e, f = 4, 5, 6
# 现在来瞧瞧交换两个值是多么容易N
e, d = d, e     # d现在是5，e现在是 4


# 字典存储映射表
empty_dict = {}
# 这里是一个预先填充的字典
filled_dict = {"one": 1, "two": 2, "three": 3}

# 用[]符号查找字典值
filled_dict["one"]   # => 1

# 用"keys()"方法得到所有的key值
filled_dict.keys()   # => ["three", "two", "one"]
# 注意 - 字典key的顺序不保证
# 你的结果可能跟这里显示的不完全一致

# 用"values()"方法获取列表的所有值
filled_dict.values()   # => [3, 2, 1]
# 注意 - 这里也有上面说的顺序的问题

# 用“in”来查找字典里是否含有某个key值
"one" in filled_dict   # => True
1 in filled_dict   # => False

# 试图查找不存在的key会抛出一个KeyError异常
filled_dict["four"]   # KeyError异常

# 使用"get()"方法来避免KeyError异常
filled_dict.get("one")   # => 1
filled_dict.get("four")   # => None
# 如果值不存在，get还方法支持传入一个默认参数
filled_dict.get("one", 4)   # => 1
filled_dict.get("four", 4)   # => 4
# 注意filled_dict.get("four")还是 => 4
# (get并没有为字典设置新值)

# 为字典的key设置值得语法跟列表类似
filled_dict["four"] = 4  # now, filled_dict["four"] => 4

# "setdefault()" 只在给定的key不存在时才往字典里插入值
filled_dict.setdefault("five", 5)  # filled_dict["five"]的值现在被置为5
filled_dict.setdefault("five", 6)  # filled_dict["five"]的值仍然是5


# 集合(Sets)存储的是...呃，集合！(类似列表但是不能包含重复的元素)
empty_set = set()
# 用一堆值来初始化一个"set()"
some_set = set([1, 2, 2, 3, 4])   # some_set现在是set([1, 2, 3, 4])

# 即使有时候看起来像是被排序过的，集合并不保证它元素的顺序
another_set = set([4, 3, 2, 2, 1])  # another_set现在是set([1, 2, 3, 4])

# 从Python 2.7开始, 可以用{}来声明一个集合
filled_set = {1, 2, 2, 3, 4}   # => {1, 2, 3, 4}

# 向集合中添加更多元素
filled_set.add(5)   # filled_set现在是{1, 2, 3, 4, 5}

# 交集运算用：&
other_set = {3, 4, 5, 6}
filled_set & other_set   # => {3, 4, 5}

# 并集运算用：|
filled_set | other_set   # => {1, 2, 3, 4, 5, 6}

# 差集运算用：-
{1, 2, 3, 4} - {2, 3, 5}   # => {1, 4}

# 检查元素在集合中存在与否用：in
2 in filled_set   # => True
10 in filled_set   # => False


####################################################
## 3. 流程控制
####################################################

# 我们先生成一个变量
some_var = 5

# 这是一个if语句，python中对齐是非常重要的！
# 输出 "some_var is smaller than 10"
if some_var > 10:
    print("some_var is totally bigger than 10.")
elif some_var < 10:    # 这里的elif从句是可选的
    print("some_var is smaller than 10.")
else:           # 这也是可选的
    print("some_var is indeed 10.")


"""
For语句用来对列表进行循环迭代 
输出:
    dog is a mammal
    cat is a mammal
    mouse is a mammal
"""
for animal in ["dog", "cat", "mouse"]:
    # 你可以使用%来插入格式化字符串
    print("%s is a mammal" % animal)

"""
"range(number)" 返回一从0到number(不包含)的一列数
输出:
    0
    1
    2
    3
"""
for i in range(4):
    print(i)

"""
While循环会一直执行，直到条件不再满足 
输出:
    0
    1
    2
    3
"""
x = 0
while x < 4:
    print(x)
    x += 1  # 表示x = x + 1

# 用try/except语块来处理异常

# 适用于Python 2.6或更高版本:
try:
    # 用"raise"抛出一个异常
    raise IndexError("This is an index error")
except IndexError as e:
    pass    # Pass只是一个啥也不干的空操作，通常你会在这里写些恢复操作的代码 
except (TypeError, NameError):
    pass    # 如果需要，可以同时处理多个异常
else:   # 对于try/except语块是可选的，必须跟在所有except语块后面
    print "All good!"   # 只在try当中的代码没有抛出任何异常时执行

####################################################
## 4. 函数
####################################################

# 用"def"创建新的函数
def add(x, y):
    print("x is %s and y is %s" % (x, y))
    return x + y    # 用return语句返回值

# 调用带参数的函数
add(5, 6)   # =>输出"x is 5 and y is 6" 并返回结果11

# 调用函数的另一种方式：利用关键字
add(y=6, x=5)   # 关键字参数的顺序是任意的

# 你可以定义位置参数(positional args)个数可变的函数
# 这些位置参数将会被解释成一个元组，如果你不适用*号的话
def varargs(*args):
    return args

varargs(1, 2, 3)   # => (1, 2, 3)


# 你可以定义关键字参数(keyword args)可变的函数
# 同样，这些关键字参数将会被解释成一个map,如果你不使用**号的话
def keyword_args(**kwargs):
    return kwargs

# 让我们调用下，看看发生了什么
keyword_args(big="foot", loch="ness")   # => {"big": "foot", "loch": "ness"}


# 如果愿意，你可以同时使用可变位置参数和可变关键字参数
def all_the_args(*args, **kwargs):
    print(args)
    print(kwargs)
"""
all_the_args(1, 2, a=3, b=4) 会输出:
    (1, 2)
    {"a": 3, "b": 4}
"""

# 当调用函数时，你可以做跟args/kwargs相反的事情！
# 用*号来扩展位置参数，用**来扩展关键字参数
args = (1, 2, 3, 4)
kwargs = {"a": 3, "b": 4}
all_the_args(*args)   # 等同于foo(1, 2, 3, 4)
all_the_args(**kwargs)   # 等同于foo(a=3, b=4)
all_the_args(*args, **kwargs)   # 等同于foo(1, 2, 3, 4, a=3, b=4)

# 通过相应地设置符号*和符号** 
# 你可以向其接收args/kwargs的函数传递args和kwargs
def pass_all_the_args(*args, **kwargs):
    all_the_args(*args, **kwargs)
    print varargs(*args)
    print keyword_args(**kwargs)

# 函数作用域                                                            
x = 5

def setX(num):
    # 局部变量x跟全局变量x不是同一个
    x = num # => 43
    print x # => 43

def setGlobalX(num):
    global x
    print x # => 5
    x = num # 全局变量x现在被设置成6
    print x # => 6

setX(43)
setGlobalX(6)

# Python有first class函数
# [译者注:关于first class function，请参照函数式编程相关书籍
# first class function:它可以让你的函数就像变量一样来使用。也就是说，你的函数可以像变量一样被创建，修改，并当成变量一样传递，返回或是在函数中嵌套函数。]
def create_adder(x):
    def adder(y):
        return x + y
    return adder

add_10 = create_adder(10)
add_10(3)   # => 13

# 还有匿名函数
(lambda x: x > 2)(3)   # => True

# 还有一些内建的高阶函数
map(add_10, [1, 2, 3])   # => [11, 12, 13]
filter(lambda x: x > 5, [3, 4, 5, 6, 7])   # => [6, 7]

# 我们可以使用列表推导式来同样达到map 和 filter的效果
[add_10(i) for i in [1, 2, 3]]  # => [11, 12, 13]
[x for x in [3, 4, 5, 6, 7] if x > 5]   # => [6, 7]


####################################################
## 5. 类
####################################################

# 我们从object父类继承得到子类
class Human(object):

    # 类的属性。由这个类的所有实例共享。
    species = "H. sapiens"

    # 基本的初始化函数__init__，当这个类被实例化时被调用
    # 注意前后两个下划线用来表示存在于用户控制的命名空间中的被python保留
	# 的对象或属性，你自己不能发明使用这类的名字
    def __init__(self, name):
        # 赋值一个参数给对象实例的name属性
        self.name = name

    # 一个实例方法。所有的方法均要以"self"作为第一个参数
    def say(self, msg):
        return "%s: %s" % (self.name, msg)

    # 一个类的方法被它的所有实例所共享
    # 类方法在调用时，会将类本身作为第一个函数传入。
    @classmethod
    def get_species(cls):
        return cls.species

    # 调用类的静态方法，不需要传入类或者实例的引用
    @staticmethod
    def grunt():
        return "*grunt*"


# 实例化一个类
i = Human(name="Ian")
print(i.say("hi"))     # 输出 "Ian: hi"

j = Human("Joel")
print(j.say("hello"))  # 输出 "Joel: hello"

# 调用我们的类方法
i.get_species()   # => "H. sapiens"

# 修改共享的属性
Human.species = "H. neanderthalensis"
i.get_species()   # => "H. neanderthalensis"
j.get_species()   # => "H. neanderthalensis"

# 调用静态方法
Human.grunt()   # => "*grunt*"


####################################################
## 6. 模块
####################################################

# 你可以导入模块
import math
print(math.sqrt(16))  # => 4

# 你可以从模块中导入指定函数
from math import ceil, floor
print(ceil(3.7))  # => 4.0
print(floor(3.7))   # => 3.0

# 你也可以一次性从模块中导入所有函数
# 警告: 这不是推荐的方法
from math import *

# 你可以让模块的名字变得短一些
import math as m
math.sqrt(16) == m.sqrt(16)   # => True
# 你可以测试下这两个函数其实是同一个
from math import sqrt
math.sqrt == m.sqrt == sqrt  # => True

# Python中的模块只是普通的python文件。你可以有自己的模块。 
# 你可以导入它们。模块的名字就是该文件的的名字

# 你可以找出都是由哪些函数和属性构成了一个模块
import math
dir(math)


####################################################
## 7. 高级功能
####################################################

# 生成器帮助你让代码变得"懒惰"
def double_numbers(iterable):
    for i in iterable:
        yield i + i

# 生成器在运行的时候创建值
# 它是在每一次的迭代中创建一个值，而不是一次性创建并返回所有的值
# 这意味着，在我们这个例子中，大于15的数将不会在double_numbers函数中处理.
# 注意xrange是一个生成器，不过它做的事情跟range是一样的
# 创建一个1-900000000的列表会花费很多时间和存储空间
# xrange创建一个xrange生成器，而不是像range那样一次性创建整个列表
# 如果希望使用跟python关键字冲突的变量名，我们可以在变量末尾添加一个下划线
xrange_ = xrange(1, 900000000)

# 将会把所有的数翻倍，直到result大等于30
for i in double_numbers(xrange_):
    print(i)
    if i >= 30:
        break


# 装饰器
# 在这个例子里beg包装了say
# Beg将会调用say。如果say_please为True，那么它会修改返回的消息

from functools import wraps


def beg(target_function):
    @wraps(target_function)
    def wrapper(*args, **kwargs):
        msg, say_please = target_function(*args, **kwargs)
        if say_please:
            return "{} {}".format(msg, "Please! I am poor :(")
        return msg

    return wrapper


@beg
def say(say_please=False):
    msg = "Can you buy me a beer?"
    return msg, say_please


print(say())  # Can you buy me a beer?
print(say(say_please=True))  # Can you buy me a beer? Please! I am poor :(
```

### 没读过瘾，想要阅读更多内容？

#### 免费在线阅读 (Free Online)

- [Learn Python The Hard Way](http://learnpythonthehardway.org/book/)
- [Dive Into Python](http://www.diveintopython.net/)
- [The Official Docs](http://docs.python.org/2.6/)
- [Hitchhiker's Guide to Python](http://docs.python-guide.org/en/latest/)
- [Python Module of the Week](http://pymotw.com/2/)
- [A Crash Course in Python for Scientists](http://nbviewer.ipython.org/5920182)

#### 实体书 (Dead Tree)
- [Programming Python](http://www.amazon.com/gp/product/0596158106/ref=as_li_qf_sp_asin_tl?ie=UTF8&camp=1789&creative=9325&creativeASIN=0596158106&linkCode=as2&tag=homebits04-20)
- [Dive Into Python](http://www.amazon.com/gp/product/1441413022/ref=as_li_tf_tl?ie=UTF8&camp=1789&creative=9325&creativeASIN=1441413022&linkCode=as2&tag=homebits04-20)
- [Python Essential Reference](http://www.amazon.com/gp/product/0672329786/ref=as_li_tf_tl?ie=UTF8&camp=1789&creative=9325&creativeASIN=0672329786&linkCode=as2&tag=homebits04-20)

### 译者注
- 更新时间：`2014-12-01`
- 本人翻译的初衷是为了自身学习和记录，翻译不好的地方，还望读者见谅。
- 这篇翻译是目前网上最新的，包括了所有新的改动，原文在 [Learn X in Y Minutes: Where X = Python](https://github.com/adambard/learnxinyminutes-docs/blob/master/python.html.markdown)
- 本人会持续关注原文的更新，并保证这里的一直是最新版。
