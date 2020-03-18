## 问题

Q：考虑建立一个熟人表acquaintance（friend1，friend2,class)，表示friend1和friend2是朋友，class表示类别，比如“书友”，“酒友”，“球友”等等。
 
### 要求一：写出定义该表的语句。

create table acquaintance
(friend1 varchar(45) not null,
friend2 varchar(45) not null,
class varchar(45) notnull,
PRIMARY KEY(friend1,friend2)
);

### 要求二：在MySQL数据库中新建此表。

![create_table](https://github.com/Sarah6667/Data-Base/blob/master/images/create_table.jpg)

### 要求三：用工具生成一些测试数据。

使用datafactory生成了测试数据。

![produce_data](https://github.com/Sarah6667/Data-Base/blob/master/images/produce_d.jpg)

