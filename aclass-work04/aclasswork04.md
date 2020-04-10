### 问题一

测试使用python或php连接两种以上数据库服务端，并执行简单查询并打印返回结果。

#### 答案一

##### 连接MySQL

我选择python的操作方式。python版本是3.7，所以选择的python接口为pymysql;如果是python,可能要改为MySQLdb。

“PyMySQL 是在 Python3.x 版本中用于连接 MySQL 服务器的一个库，Python2中则使用mysqldb。PyMySQL 遵循 Python 数据库 API v2.0 规范，并包含了 pure-Python MySQL 客户端库。”

“MySQLdb 是用于Python链接Mysql数据库的接口，它实现了 Python 数据库 API 规范 V2.0，基于 MySQL C API 上建立的。”

查询资料的相关链接：

1） https://www.runoob.com/python3/python3-mysql.html 

2） https://blog.csdn.net/kongsuhongbaby/article/details/84948205?depth_1-utm_source=distribute.pc_relevant.none-task-blog-BlogCommendFromMachineLearnPai2-2&utm_source=distribute.pc_relevant.none-task-blog-BlogCommendFromMachineLearnPai2-2

3） https://www.runoob.com/python/python-mysql.html

1. 打开cmd，也就是命令操作符，键入[pip install pymysql]，就可以安装最新版本的pymysql。若出现一下结果，则说明安装成功，在python中就可以使用了。

![result](https://github.com/Sarah6667/Data-Base/blob/master/images/1.jpg)

2. 键入[python]，进入python环境。连接数据库后，还要拿到操作数据库的游标，才能操作数据。用cursor()方法来获取。以下就是获取了游标的结果。

![result1](https://github.com/Sarah6667/Data-Base/blob/master/images/2.jpg)

3. 用execute()来执行单条SQL语句，executemany()批量执行语句。

由于我使用的数据库test中已经存在表acquaintance，所以直接返回查询结果如下。此外，你还可以用上述方法创建新的数据库，创建数据表以及插3数据。
)

![result3](https://github.com/Sarah6667/Data-Base/blob/master/images/3.jpg)

##### 连接sqlite3

python的标准库中已经包含了sqlite3，并且我自己之前下载安装了sqlite3,所以可直接使用python来操作sqlite数据库。

1. 导入sqlite3

同样进入到python的环境中，键入[import sqlite3]，然后就可以进行后续操作了。

2. 连接想要操作数据的数据库，并得到查询结果。

由于我的sqlite数据库里并没有表，所以我先创建表，再插入数据。在操作过程中发生了错误，可略过不看。可以通过游标使用fetchall()方法来获取所有查询结果，然后再用print()打印出来。

![result4](https://github.com/Sarah6667/Data-Base/blob/master/images/4.jpg)

### 问题二

测试python或php使用两种以上不同方法连接同一数据库服务端，并执行简单查询并打印返回结果。

#### 答案二

我选择用php的两种方式来连接并对MySQL数据库进行操作。

查询资料的相关链接：

1） https://blog.csdn.net/wd2011063437/article/details/79003477?depth_1-utm_source=distribute.pc_relevant.none-task-blog-BlogCommendFromBaidu-6&utm_source=distribute.pc_relevant.none-task-blog-BlogCommendFromBaidu-6

2) 

##### 面向过程（最简单的方式）

1. 首先要创建一个PHP网页，使用相关操作符和函数来完成。代码以及查询结果如下：

![result5](https://github.com/Sarah6667/Data-Base/blob/master/images/5.jpg)

##### 面向对象

![result6](https://github.com/Sarah6667/Data-Base/blob/master/images/6.jpg)

以上，就是所有的结果。




