# SQL注入

## MySQL常用函数

current_user()					当前用户名

session_user()					连接数据库的用户名

@@basedir						 MySQL安装的路径

@@datadir						  数据库路径

@@version_compile_os	操作系统版本

concat(),concat_ws(),group_concat()			字符串连接函数

substr(),mid(),left(),right(),locate()				 字符串截取函数

locate：返回第一个字符串首次出现在第二个字符串出现的位置

ascii,ord								返回指定的ASCII字符对应的值

char										返回指定数字对应的ASCII码字符函数

sleep									   延迟时间

if(exp1,exp2,exp3)				exp1正确执行exp2，否则执行exp3

## MySQL的注释方法

#

--+

/**/

/*!\*/

## MySQL注入原理

所谓SQL注入，就是把SQL命令插入到Web表单提交或输入域名或页面请求的查询字符串，最终将达到欺骗服务器执行恶意的SQL命令。具体来说，它是利用现有应用程序，将（恶意的）SQL命令注入到后台数据库引擎执行的能力，他通过在Web表单中输入（恶意）SQL语句得到一个存在安全漏洞的网站上的数据库，而不是按照设计者意图去执行SQL语句。

SQL注入的危害：

数据库信息泄露：数据库中存放用户的信息隐私数据的泄露；

服务器被控制，被安装后门。