# Maria数据库安装和使用的基本操作
今天我们学习MariaDB数据库的安装和使用。参考了相关博客文章（https://blog.csdn.net/weixin_30767835/article/details/102267460?depth_1-utm_source=distribute.pc_relevant.none-task&utm_source=distribute.pc_relevant.none-task） 以及w3school上的相关教程  （https://www.w3cschool.cn/mariadb/mariadb_insert_query.html）。

## 安装
首先是MariaDB的安装。
先进行MariaDB的下载。现在百度上搜索“MariaDB下载”，进入官网（https://downloads.mariadb.org/）。
找到最新稳定版的MariaDB，进入下载页面，根据自己电脑配置来选择合适的下载包。由于我的电脑是Windowsx64位的，所以我选择的是mariadb-10.4.12-winx64.zip的安装包，然后下载到桌面。之后对安装包进行解压，根据自己的喜好来选择解压的位置，这里我选择的是E盘，路径是E:\mariadb-10.4.12-winx64。

再进行MariaDB的安装。然后以管理员的身份进入命令提示符（CMD），如果不这样的话，可能会出现安装不了的情况。输入命令：[cd E:\mariadb-10.4.12-winx64]，进入对应的路径中。再执行安装的命令：[mysqld.exe --install MariaDB]。如果之后显示“mysqld' 不是内部或外部命令,也不是可运行的程序 或批处理文件。”的话，先需要检查自己有没有这个文件，我在bin文件夹内发现了这个文件，这时就需要进行系统环境变量的配置了。在自己电脑中搜索环境变量，出现“编辑系统环境变量”，点击进入，然后编辑系统变量Path，新建该路径：“E:\mariadb-10.4.12-winx64\bin”。然后再执行安装的命令，就会显示安装成功。

MariaDB安装完之后还需要手动开启服务。在CMD里继续输入：[net start MariaDB],以开启服务。这时容易出现一些错误，我这里也出现了和教程一样的错误：1067，服务无法启动。然后进入data文件夹，有一个文件叫：主机名.err,使用记事本打开后，可看到对应的错误信息。照上述所讲进入bin目录后，输入：[mysql_install_db],进行mysql的初始化，然后显示“数据库创建成功”，问题就解决了。在bin的目录下重输：[net start MariaDB],显示服务启动成功。

继续在bin目录下输入命令：[mysql -u root -p]，要输入密码时，按Enter跳过，直接进入MariaDB模式。然后为新数据库设置密码，即MariaDB [(none)]> [SET PASSWORD FOR 'root'@'localhost' = PASSWORD('root'););]。此外，可以在bin目录下，输入命令：[mysql -u root -p],再输入设置的密码，执行命令：[show databases]
->;
然后，就会显示已有的数据库名称。接下来，MariaDB就可以开始使用了。

## 数据库的创建
    接下来学习如何创建一个数据库。在启动服务之后，输入：[[mysql -u root -p]”,输入密码，进入MariaDB模式，继续输入:[mysqladmin -u root -p create PRODUCTS]，再输入密码，一个名为products的数据库就创建完成，可在data目录下看到。
有了数据库之后就可以创建表了。

## 表的创建
进入MariaDB模式，输入：[use PRODUCTS],显示Database changed，为创建表做准备。之后输入：
[CREATE TABLE products_tbl(
	  product_id INT NOT NULL AUTO_INCREMENT,
	  product_name VARCHAR(100) NOT NULL,
	  product_manufacturer  VARCHAR(40) NOT NULL,
	PRIMARY KEY ( product_id)
	);
然后再输入[SHOW TABLES;],就会显示数据库名称以及它里面的表格名。

## 插入数据

有了表格之后我们就可以在里面插入数据了。插入的语句为[INSERT INTO tablename (field1,field2,…) VALUES (value1,value2,…);]。例如，在命令提示符中输入[INSERT INTO products_tbl (product_id, product_name) VALUES (12345, “Orbitron 4000”, “JD”);]；再输入[SHOW COLUMNS FROM products_tbl;],表格内的栏目可现，但没有数据出现。

## 选择查询
表内有了数据就可以进行选择查询。例如，输入[SELECT * FROM products_tbl]，表格内的栏目和插入的数据会展现出来。

以上，就是MariaDB数据库的安装和使用的基本操作。
