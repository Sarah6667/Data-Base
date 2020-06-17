## sql性能与查询优化

### 参考

https://blog.csdn.net/qq_38789941/article/details/83744271?depth_1-utm_source=distribute.pc_relevant.none-task-blog-BlogCommendFromBaidu-1&utm_source=distribute.pc_relevant.none-task-blog-BlogCommendFromBaidu-1

### 实验

#### 引言

我们用SQL语句进行查询，增添，修改和删除我们的数据库内容。数据库存储着大批的数据，其实我们用的最多的就是SQL的查询语句了，用SQL查询语句来从数据库中获取我们所需要的数据。当在数据库量不大的情况下，SQL语句的查询效率没多大区别；但是当数据库数据量逐渐增加，原来的SQL语句可能运行效率将下降，这时候优化SQL语句就是必然了。

#### 优化SQL语句的几个例子（主要从有索引的表下手）

我们都知道在数据表上增加索引，能提高查询速度。但索引太多，可能会降低插入和更新的效率。

1. 对查询进行优化，应尽量避免全表扫描，首先应考虑在 where 及 order by 涉及的列上建立索引。

2. in 和 not in 也要慎用，否则会导致全表扫描；对于连续的数值，能用 between 就不要用 in。

eg:  select MATCHNO from matches where LOST in(1,2,3);
   
     select MATCHNO from matches LOST between 1 and 3;

![s2](https://github.com/Sarah6667/Data-Base/blob/master/images/s2.jpg)

注：此结果可能因为我表数据量不大，无法体现SQL语句的优化与否。

3. 应尽量避免在 where 子句中对字段进行表达式操作，这将导致引擎放弃使用索引而进行全表扫描。

eg:  select MATCHNO from matches where PLAYERNO/2=56;
     
     select MATCHNO from matches where PLAYERNO=56*2;
     
![s1](https://github.com/Sarah6667/Data-Base/blob/master/images/s1.jpg)

结果有很鲜明的对比。

4. 多数时候最好用exists代替in。

5. 尽可能的使用 varchar 代替 char ，因为首先变长字段存储空间小，可以节省存储空间。其次对于查询来说，在一个相对较小的字段内搜索效率显然要高些。   

6. 任何地方都不要使用 select * from t ，用具体的字段列表代替“*”，不要返回用不到的任何字段。

#### 实验总结

SQL语句的使用效率在数据库表量不大的情况下不会很明显；一旦数据库表其中的数据量增多，SQL语句的使用效率问题就会突显。这时候就要优化SQL语句了。

除了以上这些，还可以通过查询慢日志来精准找出导致SQL语句执行效率差的主要地方。
