## PHP程序的运行流程

来源：https://blog.csdn.net/diavid/article/details/81035188

1. scanning，将PHP代码转换成语言片段(tokens)。

2. parsing，将语言片段转换成简单而有意义的表达式。

3. compilation，将表达式编译成Opcode。

4. execution，顺次执行Opcodes，从而实现PHP脚本的功能。

## 目前常用的服务器软件

来源：https://www.cnblogs.com/youpeng/p/10667021.html

1. Apache

是世界使用排名第一的Web服务器软件.特点是：简单、速度快、性能稳定，并可做代理服务器来使用。

2. IIS（Internet Information Server）

它是微软公司主推的服务器。最新的版本是Windows2008里面包含的IIS 7，IIS与Window Server完全集成在一起，因而用户能够利用Windows Server和NTFS（NT File System，NT的文件系统）内置的安全特性，建立强大，灵活而安全的Internet和Intranet站点。

3. Nginx 

Nginx (engine x) 是一个高性能的HTTP和反向代理web服务器，同时也提供了IMAP/POP3/SMTP服务。其将源代码以类BSD许可证的形式发布，因它的稳定性、丰富的功能集、示例配置文件和低系统资源的消耗而闻名。
     --百度百科
     
## 如何将PHP与Apache建立关联

来源：https://www.cnblogs.com/li-mei/p/6743822.html

【不知道有没用】

httpd.conf文件中添加如下代码即可实现apache与php的关联。
即：

LoadModule php5_module "D:/softs/php/php5apache2_2.dll"  

AddType application/x-httpd-php .php .html .htm   

PHPIniDir "D:/softs/php" 

## 主目录下面的子目录和虚拟目录有何不同？

来源：https://zhidao.baidu.com/question/1957657070386535180.html

很多时候，上传的文件多了，架设服务器当初设定百的主目录所在盘空间往往就不够了，怎么办？这就需要设置虚拟目录。虚拟目录就是将其他目录以映射的方式虚拟到该FTP服务器的主目录下，这样度，一个FTP服务器的主目录实质上就可以包括很多不同盘内符、不同路径的目录，而不会受到所在盘空间的限制了。当用户登录到主目录下，还可以根据该账户的权容限对它进行相应的操作，就像操作主目录下的子目录一样。 
