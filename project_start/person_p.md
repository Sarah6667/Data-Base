##  个人项目的选题

sql性能与查询优化

## 调研

通过在百度上搜索相关sql查询优化的话题，然后选择适合自己的供参考的博客，然后自己再照着进行实验。

参考：https://www.cnblogs.com/atree/archive/2011/02/13/sql_optimize_1.html

## 初步实验

sql语法也会影响到查询的速度，比如说大小写，所以尽量保持sql语句的一致性。

下图两张图片的对比，可以验证上述观点。

![sql1.1](https://raw.githubusercontent.com/Sarah6667/Data-Base/master/images/capture_20200510203546781.bmp)

![sql1.2](https://raw.githubusercontent.com/Sarah6667/Data-Base/master/images/capture_20200510203629928.bmp)

效果一样，一个用时0.001s，一个用时0.000s。

sql查询优化要从基本的开始下手。

