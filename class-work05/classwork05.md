### 常见编译型高级编程语言数据库接口

####	C语言：
ODBC（开放数据库连接）它为Oracle，SQL   Server，MS   Excel等都提供了驱动程序，使得用户可以使用SQL语句对数据库进行直接的底层功能操作。在使用ODBC   API时，用户须引入的头文件为 "sql.h "， "sqlext.h "， "sqltypes.h "。

####	C++：
 ADO(ActiveX Data Object) ActiveX数据对象，是微软提供的面向对象的接口，与OLE   DB类似，但接口更简单，具有更广泛的特征数组和更高程度的灵活性。ADO基于COM,提供编程语言可利用的对象，除了面向VC++，还提供面向其他各种开发工具的应用，如VB，VJ等。ADO在服务器应用方面非常有用，特别是对于动态服务器页面ASP(Active Server Page)。

### 常见解释型高级编程语言数据库接口

####	python：
##### DB-API   
Python所有的数据库接口程序都在一定程度上遵守 Python DB-API 规范。DB-API 是一个规范，它定义了一系列必须的对象和数据库存取方式，以便为各种各样的底层数据库系统和多种多样的数据库接口程序提供一致的访问接口。由于DB-API 为不同的数据库提供了一致的访问接口， 在不同的数据库之间移植代码成为一件轻松的事情。

#### JAVA
##### JDBC
Java数据库连接，（Java Database Connectivity，简称JDBC）是Java语言中用来规范客户端程序如何来访问数据库的应用程序接口，提供了诸如查询和更新数据库中数据的方法。 

#### C#
ADO.NET的名称起源于ADO（ActiveX Data Objects），是一个COM组件库，用于在以往的Microsoft技术中访问数据。之所以使用ADO.NET名称，是因为Microsoft希望表明，这是在NET编程环境中优先使用的数据访问接口。

### python编程语言连接数据库的不同方式
#### MySQL数据库

##### Sqlalchemy
sqlalchemy是python中著名的orm框架，通过这个框架可以不用关心sql语句，就能操作数据库。大大的提高开发效率。当然通过orm来操作数据库会执行很多的数据库冗余操作，降低程序的运行效率。
 
##### MySQLdb
MySQLdb是用于Python链接Mysql数据库的接口，它实现了Python 数据库API规范V2.0，基于MySQL C API上建立的。 
       
##### PyMySQL
PyMySQL是一个纯Python写的MySQL客户端，它的目标是替代MySQLdb，可以在CPython、PyPy、IronPython和Jython环境下运行。PyMySQL的性能和MySQLdb几乎相当，如果对性能要求不是特别的强，使用PyMySQL将更加方便。PyMySQL的使用方法和MySQLdb几乎一样。

#### PostgreSQL数据库
PostgreSQL可以用Python psycopg2模块集成。 sycopg2是Python编程语言的PostgreSQL数据库的适配器。 其程序代码少，速度快，稳定。
	oracle数据库
Python有一个模块cx_Oracle可以与Oracle相连。


### 参考链接
https://blog.csdn.net/qq_40304090/java/article/details/90369424

https://blog.csdn.net/xqhrs232/article/details/78259479 

https://blog.csdn.net/shang_0122/article/details/90257947?depth_1-utm_source=distribute.pc_relevant.none-task&utm_source=distribute.pc_relevant.none-task
