### Q1

测试使用用户权限控制的语句(建议使用命令行)

#### A1

SQL:grant select on acquaintance to 'root'@'localhost';

Result: Query OK, 0 rows affected (0.007 sec)

之前把root用户的权限取消，用select语句查询会发生如下错误：#1142 - SELECT command denied to user 'root'@'localhost' for table 'students'”。而现在再用select语句查询，如：[select * from acquaintance where class='A';],结果出现有着查询结果的表格。

### Q2

检索MySQL批处理相关功能并实验

####

MySQL批处理相关功能

参考：https://www.cnblogs.com/linkworld/p/7620122.html
      https://blog.csdn.net/waterxcfg304/article/details/37880741

1）批处理指针对更新（增加、删除、更改）语句。默认此功能关闭，若要使用，需要在url中配置参数，如：jdbc:mysal://localhost:3306/mydb1?rewriteBatchedStatements=true。可降低与数据库的连接次数，提高执行效率。 

2）可以将SQL多条语句放在一个txt文件中，记录路径，再命令行中输入类似的语句：mysql -u root -p test < (txt文件的路径）。test是数据库的名字。执行语句后，可以在同一目录下看到一个新的txt文件。打开就可以看到SQL语句执行的结果。
