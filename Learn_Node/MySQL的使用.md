# MySQL的使用

## 概述

DB：Database，数据库数据库实际上在硬盘上以文件的形式存在。

DBMS：Database Management System，数据库管理系统常见的有：MySQL、Oracle、DB2、sqlserver。

SQL：结构化查询语言，是一门标准通用语言。标准的SQL适用于所有数据库产品。SQL属于高级语言。SQL语句在执行的时候，实际上内部也会先进行编译，然后在执行SQL（SQL语句的编译由DBMS完成）。

table：表，表是数据库的基本组成单元，所有的数据以表格的形式组织，目的是可读性强。一个表包括行和列，行，被称为数据或记录（data），列，被称为字段（column）。每个字段应该包含字段名、数据类型、相关的约束。

### SQL语句的分类

- DQL（Data Query Language，数据查询语言）：查询语句，凡是select语句都是查询语句。
- DML（Data Manipulation Language，数据操作语言）：insert，delete，update，对表中的数据进行增删改。
- DDL（Data Definition Language，数据定义语言）：create，drop，altert，对表结构进行增删改。
- TCL（Transaction Control Language，事务控制语言）：commit-提交事务，rollback-回滚事务。
- DCL（数据控制语言）：grant-授权，revoke-撤销权限 等。

### 基本的MySQL命令

这些是MySQL的命令，不是SQL语句。

```mysql
show databases;			//查看有哪些数据库
show tables;			//查看有哪些数据表
use 数据库;			//使用数据库
create database 数据库;	//创建数据库
source 数据库路径		//执行SQL脚本
扩展名为.sql的文件时SQL脚本文件，文件中编写了大量的SQL语句。
desc 表名;				//查看表结构
select database()			//查看当前使用的数据库
select version()			//查看数据库版本号
show create table emp		//查看创建表的建表语句
```

## 数据查询（DQL）

### 简单查询

select 字段名1,字段名2,字段名3,.... from 表名;

查询全部字段：不建议在实际开发中使用。

```sql
select * from emp;
```

字段名可以进行数字运算，可以给字段名取别名，使用as关键字，可省略。（别名可以使用中文，但是需要用单引号括起来，在MySQL中双引号也可以，但是在标准SQL语句中必须要用单引号）

```sql
select sal*12 as '年薪' from emp;
```

对查询结果去重，使用关键字distinct,放在所有字段前边，对后边的字段进行联合去重。

```mysql
select distinct 字段 from 数据表;
```

### 条件查询

select 字段,字段... from 表名 where 条件;

执行顺序：先from，然后where，最后select。

MySQL支持的运算符：

| 运算符          | 说明                                                         |
| --------------- | ------------------------------------------------------------ |
| =               | 等于                                                         |
| <>或!=          | 不等于                                                       |
| <               | 小于                                                         |
| <=              | 小于等于                                                     |
| >               | 大于                                                         |
| >=              | 大于等于                                                     |
| between … and … | 两个值之间，等同于>= and <=                                  |
| is null         | 为null（is not null 不为空）                                 |
| and             | 并且，优先级比or高                                           |
| or              | 或者                                                         |
| in              | 包含，相当于多个or（not in 不在这个范围内）                  |
| not             | not可以取非，主要用在is或in中                                |
| like            | 模糊匹配，支持%或者下划线匹配，%代表多个字符，_ 代表一个字符 |

在数据库中NULL不是一个值，代表什么也没有，为空。空不是一个值，不能用等号衡量，必须使用is null 或 is not null。

### 排序（升序、降序）

排序使用order by 关键字，默认为升序，asc表示升序，desc表示降序。多个排序字段排序用等号隔开。

order by后的排序字段可以使用数字表示，数字是查询字段的位置。（不建议）

排序一般放在最后，并且最后执行。

### 分组函数

**重点：在所有数据库软件中都规定，只要有NULL参与的运算结果一定为NULL。**

分组函数也叫多行处理函数，输入多行，最终结果输出一行。分组函数会自动忽略NULL。

**分组函数不可直接使用在where子句当中。因为分组函数只能在group by执行之后才能使用，而group by是在where执行之后才会执行的。**

| 函数    | 功能     |
| ------- | -------- |
| count() | 计数     |
| sum()   | 求和     |
| avg()   | 求平均值 |
| max()   | 求最大值 |
| min()   | 求最小值 |

count(*)：统计总记录条数（与某个字段无关）

count(字段)：统计某个字段中数据不为NULL的数据总数量。

### 单行处理函数

#### 数值型函数

| 函数名称                                                     | 作 用                                                      |
| ------------------------------------------------------------ | ---------------------------------------------------------- |
| [ABS](http://c.biancheng.net/mysql/abc.html)                 | 求绝对值                                                   |
| [SQRT](http://c.biancheng.net/mysql/sqrt.html)               | 求二次方根                                                 |
| [MOD](http://c.biancheng.net/mysql/mod.html)                 | 求余数                                                     |
| [CEIL 和 CEILING](http://c.biancheng.net/mysql/ceil_celing.html) | 两个函数功能相同，都是返回不小于参数的最小整数，即向上取整 |
| [FLOOR](http://c.biancheng.net/mysql/floor.html)             | 向下取整，返回值转化为一个BIGINT                           |
| [RAND](http://c.biancheng.net/mysql/rand.html)               | 生成一个0~1之间的随机数，传入整数参数是，用来产生重复序列  |
| [ROUND](http://c.biancheng.net/mysql/round.html)             | 对所传参数进行四舍五入                                     |
| [SIGN](http://c.biancheng.net/mysql/sign.html)               | 返回参数的符号                                             |
| [POW 和 POWER](http://c.biancheng.net/mysql/pow_power.html)  | 两个函数的功能相同，都是所传参数的次方的结果值             |
| [SIN](http://c.biancheng.net/mysql/sin.html)                 | 求正弦值                                                   |
| [ASIN](http://c.biancheng.net/mysql/asin.html)               | 求反正弦值，与函数 SIN 互为反函数                          |
| [COS](http://c.biancheng.net/mysql/cos.html)                 | 求余弦值                                                   |
| [ACOS](http://c.biancheng.net/mysql/acos.html)               | 求反余弦值，与函数 COS 互为反函数                          |
| [TAN](http://c.biancheng.net/mysql/tan.html)                 | 求正切值                                                   |
| [ATAN](http://c.biancheng.net/mysql/atan.html)               | 求反正切值，与函数 TAN 互为反函数                          |

#### 字符串函数

| 函数名称                                                 | 作 用                                                        |
| -------------------------------------------------------- | ------------------------------------------------------------ |
| [LENGTH](http://c.biancheng.net/mysql/length.html)       | 计算字符串长度函数，返回字符串的字节长度                     |
| [CONCAT](http://c.biancheng.net/mysql/concat.html)       | 合并字符串函数，返回结果为连接参数产生的字符串，参数可以使一个或多个 |
| [INSERT](http://c.biancheng.net/mysql/insert.html)       | 替换字符串函数                                               |
| [LOWER](http://c.biancheng.net/mysql/lower.html)         | 将字符串中的字母转换为小写                                   |
| [UPPER](http://c.biancheng.net/mysql/upper.html)         | 将字符串中的字母转换为大写                                   |
| [LEFT](http://c.biancheng.net/mysql/left.html)           | 从左侧字截取符串，返回字符串左边的若干个字符                 |
| [RIGHT](http://c.biancheng.net/mysql/right.html)         | 从右侧字截取符串，返回字符串右边的若干个字符                 |
| [TRIM](http://c.biancheng.net/mysql/trim.html)           | 删除字符串左右两侧的空格                                     |
| [REPLACE](http://c.biancheng.net/mysql/replace.html)     | 字符串替换函数，返回替换后的新字符串                         |
| [SUBSTRING](http://c.biancheng.net/mysql/substring.html) | 截取字符串，返回从指定位置开始的指定长度的字符换             |
| [REVERSE](http://c.biancheng.net/mysql/reverse.html)     | 字符串反转（逆序）函数，返回与原始字符串顺序相反的字符串     |

#### 日期和时间函数

| 函数名称                                                     | 作 用                                                        |
| ------------------------------------------------------------ | ------------------------------------------------------------ |
| [CURDATE 和 CURRENT_DATE](http://c.biancheng.net/mysql/curdate_current_date.html) | 两个函数作用相同，返回当前系统的日期值                       |
| [CURTIME 和 CURRENT_TIME](http://c.biancheng.net/mysql/curtime_current_time.html) | 两个函数作用相同，返回当前系统的时间值                       |
| [NOW 和 SYSDATE](http://c.biancheng.net/mysql/now_sysdate.html) | 两个函数作用相同，返回当前系统的日期和时间值                 |
| [UNIX_TIMESTAMP](http://c.biancheng.net/mysql/unix_timestamp.html) | 获取UNIX时间戳函数，返回一个以 UNIX 时间戳为基础的无符号整数 |
| [FROM_UNIXTIME](http://c.biancheng.net/mysql/from_unixtime.html) | 将 UNIX 时间戳转换为时间格式，与UNIX_TIMESTAMP互为反函数     |
| [MONTH](http://c.biancheng.net/mysql/month.html)             | 获取指定日期中的月份                                         |
| [MONTHNAME](http://c.biancheng.net/mysql/monthname.html)     | 获取指定日期中的月份英文名称                                 |
| [DAYNAME](http://c.biancheng.net/mysql/dayname.html)         | 获取指定曰期对应的星期几的英文名称                           |
| [DAYOFWEEK](http://c.biancheng.net/mysql/dayofweek.html)     | 获取指定日期对应的一周的索引位置值                           |
| [WEEK](http://c.biancheng.net/mysql/week.html)               | 获取指定日期是一年中的第几周，返回值的范围是否为 0〜52 或 1〜53 |
| [DAYOFYEAR](http://c.biancheng.net/mysql/dayofyear.html)     | 获取指定曰期是一年中的第几天，返回值范围是1~366              |
| [DAYOFMONTH](http://c.biancheng.net/mysql/dayofmonth.html)   | 获取指定日期是一个月中是第几天，返回值范围是1~31             |

| 函数名称                                                     | 作用                                             |
| ------------------------------------------------------------ | ------------------------------------------------ |
| [YEAR](http://c.biancheng.net/mysql/year.html)               | 获取年份，返回值范围是 1970〜2069                |
| [TIME_TO_SEC](http://c.biancheng.net/mysql/time_to_sec.html) | 将时间参数转换为秒数                             |
| [SEC_TO_TIME](http://c.biancheng.net/mysql/sec_to_time.html) | 将秒数转换为时间，与TIME_TO_SEC 互为反函数       |
| [DATE_ADD 和 ADDDATE](http://c.biancheng.net/mysql/date_add_adddate.html) | 两个函数功能相同，都是向日期添加指定的时间间隔   |
| [DATE_SUB 和 SUBDATE](http://c.biancheng.net/mysql/date_sub_subdate.html) | 两个函数功能相同，都是向日期减去指定的时间间隔   |
| [ADDTIME](http://c.biancheng.net/mysql/addtime.html)         | 时间加法运算，在原始时间上添加指定的时间         |
| [SUBTIME](http://c.biancheng.net/mysql/subtime.html)         | 时间减法运算，在原始时间上减去指定的时间         |
| [DATEDIFF](http://c.biancheng.net/mysql/datediff.html)       | 获取两个日期之间间隔，返回参数 1 减去参数 2 的值 |
| [DATE_FORMAT](http://c.biancheng.net/mysql/date_format.html) | 格式化指定的日期，根据参数返回指定格式的值       |
| [WEEKDAY](http://c.biancheng.net/mysql/weekday.html)         | 获取指定日期在一周内的对应的工作日索引           |

#### 流程控制函数

| 函数名称                                           | 作用                                           |
| -------------------------------------------------- | ---------------------------------------------- |
| [IF](http://c.biancheng.net/mysql/if.html)         | 判断，流程控制                                 |
| [IFNULL](http://c.biancheng.net/mysql/ifnull.html) | 对NULL进行预处理，把字段exp1中的NULL值换成exp2 |
| [CASE](http://c.biancheng.net/mysql/case.html)     | 搜索语句                                       |

### 分组查询

group by：按照某个字段或者某些字段进行分组。

having：对分组之后的数据进行再次过滤。

分组函数一般都会和group by联合使用。并且任何一个分组函数都是在group by语句执行结束之后才会执行。

**当一条语句中有group by 的话，select后边只能跟分组函数和参与分组的字段。**

having只能出现在group by 之后，对分完组之后的数据进行过滤。能使用where对数据过滤时，尽量使用where过滤，where无法过滤，在考虑使用having进行过滤。

### 完整的DQL语句

选取——来自——筛选——分组——筛选——排序

select … from … where … group by … having … order by …

执行顺序：5-1-2-3-4-6

### 连接查询

在实际开发中，大部分情况下都不是从单表中查询数据，一般都是多张表联合查询取出最终的结果。在实际开发中，一般一个业务都会对应多张表。

- 根据表的链接方式划分包括内连接、外连接、全连接（很少用）。
  - 内连接分为等值链接、非等值链接、自连接。
  - 外连接分为左外链接（左连接）和右外连接（右连接）。

在多表查询时会调用多个表，因此可以对表名进行取别名。

eg. 

```mysql
select e.ename,d.dname from emp e,dept d;
```

*笛卡尔积：当两张表进行连接查询的时候，没有任何条件进行限制，最终的查询结果条数是两张表记录条数的乘积。*

对查询语句结果进行过滤可以避免笛卡尔积现象，但是不会减少匹配次数，只不过只显示有效记录。

eg.  

```mysql
select e.ename,d.dname from emp e,dept d where e.deptno=d.deptno;
```



#### 内连接之等值连接

特点：条件是等量关系。

语法：… A <inner> join B on 连接条件 where …		//inner可省略，带上可读性更高

eg.  查询每个员工的部门名称，要求显示员工和部门名。

```mysql
select e.ename,d.dname from emp e inner join dept d on e.deptno=d.deptno;
```



#### 内连接之非等值连接

特点：条件不是等量关系。

eg.  找出每个员工的工资等级，要求显示员工名、工资、工资等级。

```mysql
select e.ename,e.sal,s.grade from emp e inner join salgrade s on e.sal between s.losal and s.hisal;
```



#### 内连接之自连接

特点：一张表看做两个表，自己连接自己。

eg.  找出每个员工的上级领导，要求显示员工名和对应的领导名。

```mysql
 select e1.ename,e2.ename from emp e1 inner join emp e2 on e1.mgr=e2.empno;
```

#### 外连接

语法：… A left/right <outer> join B on 连接条件 where …		//outer可省略，带上可读性更高

内连接与外连接的区别：

- 内连接：假如A和B进行连接，凡是A表和B表能够匹配上的记录都查询出来，A表和B表没有主副之分，两张表是平等的。如果一张表中的有一条数据匹配不上，则不会显示该条数据。
- 外连接：假如A表和B表进行连接，A表和B表中有一张表是主表，一张表是副表，主要查询主表中的数据，捎带着查询副表，当副表中的数据没有和主表中的数据匹配上，副表自动模拟出NULL与之匹配。和Excel中的vlookup函数类似。

外连接最重要的特点是：主表中的数据会无条件的全部查询出来。

左外连接（左连接）：表示左边的表是主表。

右外连接（右连接）：表示右边的表是主表。

左连接可以写成右连接，右连接也可以写成左连接。在工作中外连接居多。

eg.  找出每个员工的上级领导，要求显示员工名和对应的领导名。

```mysql
select e1.ename,e2.ename from emp e1 left outer join emp e2 on e1.mgr=e2.empno;
select e1.ename,e2.ename from emp e2 right outer join emp e1 on e1.mgr=e2.empno;
```

eg. 找出哪个部门没有员工。

```mysql
select d.* from emp e right outer join dept d on e.deptno=d.deptno where e.deptno is null;
```

#### 多表查询

语法：… A join B join C on …

表示：A表和B表先进行表连接，连接 之后A继续与C表进行连接。

eg. 找出每个员工的部门名称及工资等级。

```mysql
select e.ename,d.dname,s.grade from emp e join dept d join salgrade s on e.deptno=d.deptno and e.sal between s.losal and s.hisal;
select e.ename,d.dname,s.grade from emp e join dept d on e.deptno=d.deptno join salgrade s on e.sal between s.losal and s.hisal;
```

eg. 找出每个员工的部门名称、工资等级、以及上级领导。

```mysql
select e1.ename,e2.ename,d.dname,s.grade from emp e1 left join emp e2 on e1.mgr=e2.empno join dept d on e1.deptno=d.deptno join salgrade s on e1.sal between s.losal and s.hisal;
```

### 子查询

子查询：select语句中嵌套select语句，被嵌套的select 语句被称为子查询。

子查询可以出现的位置：select …(select)… from …(select)… where …(select)…

#### where后边嵌套子查询

eg.  找出高于平均薪资的员工信息。

```mysql
select * from emp where sal>(select avg(sal) from emp);
```

#### from 后边嵌套子查询

eg.  找出每个部门平均薪水的薪资等级。

第一步：找出每个部门的平均薪水

```mysql
select deptno,avg(sal) as avgsal from emp group by deptno;
```

第二步：将第一步查询出的结果当做临时表t，让t表和salgrade表连接。

```mysql
select t.*,s.grade from (select deptno,avg(sal) as avgsal from emp group by deptno) t join salgrade s on t.avgsal between t.losal and t.hisal;
```

eg.  找出每个部门平均的薪水等级。

```mysql
select e.deptno,avg(s.grade) from emp e join salgrade s on e.sal between s.losal and s.hisal group by e.deptno;
```

#### select后面嵌套子查询

eg.  找出每个员工所在的部门名称，要求显示员工名和部门名。

```mysql
select e.ename,(select d.dname from dept d where e.deptno = d.deptno) as dname from emp e;
```

### union(可以将查询结果集拼接在一起)

eg.  找出工作岗位是salesman 和manager 的员工。

```mysql
select ename,job from emp where job='manager' union select ename,job from emp where job = 'salesman';
```

### limit（MySQL特有）

limit可以将查询出的结果截取部分显示。limit是select语句最后执行的环节。

语法：limit <start>,length			//start表示起始位置，起始值为0，默认为0，可省略，length表示取几个

eg. 取出工资前5名的员工。

```mysql
select * from emp order by sal desc limit 5;
```

## 表的增删改（DDL）

### 创建表

语法格式：

create table 表名(字段名1 数据类型 [default 默认值] [约束],字段名2 数据类型,字段名3 数据类型，…);

MySQL中常见的数据类型

| 类型    | 描述                                       |
| ------- | ------------------------------------------ |
| int     | 整数                                       |
| bigint  | 长整型                                     |
| float   | 浮点型                                     |
| char    | 定长字符串                                 |
| varchar | 可变长字符串（最多255个字符）              |
| date    | 日期类型                                   |
| BLOB    | 二进制大对象（存储图片、视频等流媒体信息） |
| CLOB    | 字符大对象（存储较大文本）                 |

在实际开发中，当一个字段中的长度不发生改变时，是定长的，例如：性别、生日等都采用char。当一个字段的数据长度不确定时，例如：简介、姓名等都是采用varchar。

### 数据约束

在创建表的时候，可以给表的字段添加相应的约束，添加的目的是为了保证表中数据的合法性、有效性、完整性。

常见的约束有：

- 非空约束（not null）：约束的字段不能为NULL。
- 唯一约束（unique）：约束的字段不能重复。
- 主键约束（primary key）：约束的字段既不能为NULL也不能重复。（简称PK）
- 外键约束（foreign key）：（简称FK）
- 检查约束（check）：检查约束在Oracle数据库中存在，目前MySQL不支持检查约束。

#### 非空约束

约束的字段不能为空，在创建表的字段后添加not null。

非空约束只能在字段后添加，不能在创建完字段后再添加。因此非空约束只有列级约束，没有表级约束。

#### 唯一约束（unique）

唯一性约束修饰的字段具有唯一性，不能重复，但可以为NULL。

可以给多个字段添加联合唯一约束。在创建表的字段中添加 unique(字段1,,字段2)，而不能分开添加。

**在字段后边添加约束是列级约束，在创建完字段后添加的约束是表级约束。**

#### 主键约束（primary key）

主键约束修饰的字段既不能为NULL也不能重复（简称PK）。

在创建表的字段后添加 primary key 也可以在创建表的字段后再添加primary key(字段1, 字段2)，制作联合主键。

主键约束既可以是列级约束，也可以是表级约束。

主键的作用：

- 表的设计三范式中有要求，第一范式要求任意一张表都应该有主键。
- 主键值是这行记录是在这张表当中的唯一标识。

主键的分类：

- 根据主键字段分类，可以分为：单一主键和联合主键（复合主键）（不建议使用，违背三范式）。
- 根据主键性质分类，可以分为：自然主键（一个和业务没有任何关系的自然数）和业务主键（主键值与业务挂钩，不建议使用）。

**一张表的主键约束只能有一个。**

MySQL中主键值自增的关键字 auto_increment ，自动维护一个自增的数字，从1开始，以1递增。

Oracle数据库也提供了一和自增机制，叫做：序列(sequence)对象。

#### 外键约束

语法：foreign key(字段) references 表名(字段)		//references-引用

创建表时，在创建完字段后，添加外键。

外键可以为NULL。被引用的字段不一定是主键，但至少具有唯一性约束。

A表中的字段通过外键引用了B表中的字段，A表叫做子表，B表叫做父表。

顺序要求：

删除数据时，先删除子表，再删除父表；

添加数据时，先添加父表，再添加子表；

创建表时，先创建父表，再创建子表；

删除表时，先删除子表，再删除父表。

###  删除表

语法：drop table 表名;

drop table if exists 表名;		//当这个表存在的话删除，Oracle数据库不支持这种写法。

### 修改表

语法：alter table 表名 modify 字段名 数据类型 [修改选项]

修改选项：

- add column 字段 <类型>		添加字段
- change column <旧字段> <新字段> <新字段类型>	修改字段名称，新字段类型也可修改，但不能为空。
- modify <字段> <字段类型>	修改字段属性
- drop <字段>	删除字段
- remove <新表名>	修改表名

### 复制表

语法：create table 表名 as select 语句;

将查询结果当做表创建出来。

## 数据的增删改（DML）

### 插入数据

语法格式：insert into 表名(字段名1,字段名2,字段名3,……) values（值1,值2,值3,……),(……);

要求：字段名的数量和值的数量相同，并且数据类型要对应相同。

insert语句中可以将写全部字段，也可以写部分字段，也可以将字段顺序打乱。只写部分字段会将未填写的字段默认为NULL。也可以自己设定默认值。

字段可以省略不写，但是值必须全部填写。

当一条insert语句执行成功之后，表格当中必然会出现一行记录。即使多的这条记录当中的某些字段是NULL，后期也无法使用insert插入该条记录，只能使用update进行更新。

将查询结果插入到一张表中：

insert into 表名 select * from 表名;

### 修改数据

语法：update 表名 set 字段名1=值1,字段名2=值2 …… where 条件;

注意：没有条件整张表数据全部更新。

### 删除数据

delete from 表名 where 条件;

注意：没有条件删除所有数据。

使用delete删除数据可以通过事务回滚。

delete删除数据速度会比较慢，在删除数据量庞大的情况下，不建议使用。

删除大表中的数据使用关键字truncate：

truncate table 表名;

truncate 是对表进行截断，只保留表头。且无法使用事务回滚，永久丢失。

*增删改查的术语：CRUD操作。*

*Create（添加），Retrieve（检索），Update（修改），Delete（删除）*

## 存储引擎（MySQL特有）

完整的建表语句：

create table 表名(……) engine=InnoDB default charset=utf-8;

MySQL中默认的存储引擎是InnoDB，默认的字符集是utf-8。

存储引擎只有在MySQL中存在，Oracle中有对应的机制，但不叫做存储引擎，没有特殊的名字，就叫“表的存储方式”。

MySQL支持很多存储引擎，每一个存储引擎都对应了不同的存储方式。每一个存储引擎都有自己的优缺点，需要在合适的时机选择合适的存储引擎。

查看当前MySQL支持的存储引擎：

show engines \G;

常见的存储引擎：

- MyISAM：MySQL中最常用的存储引擎。它使用三个文件表示每个表，格式文件-存储表结构的定义(.frm)，数据文件-存储行表中行的内容(.myd)，索引文件-存储表上索引(.myi)。
  - 优点：可被压缩，节省存储空间。并且可以转换成只读表，提高检索效率。
  - 缺点：不支持事务。
- InnoDB：MySQL中默认的存储引擎。表的结构存储在.frm文件中，数据存储在tablespace这样的表空间中（逻辑概念），无法被压缩，无法转换成只读。这种存储引擎在MySQL数据库奔溃之后提供自动恢复机制。支持级联删除和级联更新。
  - 优点：支持事务、行级锁、外键等，这种存储引擎数据的安全得到了保障。
  - 缺点：占用空间较大。
- MEMORY：数据存储在内存中，且行的长度固定。在数据库目录内，每个表以.frm格式的文件表示。支持表级锁。不能包含TEXT或BLOB字段。
  - 优点：查询效率是最高的。
  - 缺点：不安全，断电后数据会消失。因为数据和索引都存储在内存当中。

## 事务（Transaction）

一个事务是一个完整的业务逻辑单元，不可再分。

eg.  银行账户转账，从A账户向B账户转账1000元，需要执行两条update语句：

update t_act set balance - 1000 where actno = 'A';

update t_act set balance + 1000 where actno = 'B';

以上两条DML语句必须同时成功，或者同时失败，不允许出现一条成功，一条失败。

要保证以上两条DML语句同时成功或者同时失败，那么就需要使用数据库的“事务机制”。

和事务相关的语句只有DML语句（insert，delete，update），因为只有这三个语句都是和数据表中的“数据”相关的。事务的存在就是为了保证数据的完整性和安全性。

事务的四大特性：ACID

- A — 原子性：事务是最小的工作单元，不可再分。
- C — 一致性：事务必须保证多条DML语句同时成功或同时失败。
- I — 隔离性：事务A和事务B之间具有隔离。
- D — 持久性：最终数据必须持久化到硬盘文件中，事务才算成功的结束。

### 事务之间的隔离性

事务隔离性存在隔离级别，理论上隔离级别包括4个：

第一级别：读未提交（read uncommitted）

​	对方事务还没有提交，我们当前事务可以读到对方未提交的数据。这种级别可能存在脏读（Dirty Read）现象——表示读到脏的数据。

第二级别：读已提交（read committed）

​	对方事务提交之后的数据我放可以读取到。该级别解决了脏读现象，存在的问题是，不可重复读。

第三级别：可重复读（repeatable read）

​	该级别解决了不可重复读问题，存在的问题：读取到的数据是幻象。

第四级别： 序列化读/串行化读（serializable)

​	该级别解决了所有问题。存在的问题：效率低，需要事务排队。

Oracle数据库默认的隔离级别是：读已提交。

MySQL数据库默认的隔离级别是：可重复读。

### 事务的使用

MySQL中默认是关闭事务的。需要使用start transaction; 开启事务。

开启之后使用commit 提交事务，rollback 回滚事务。

也可以使用savepoint 名字; 保存回滚点。

设置事务隔离级别：

set global transaction isolation level 隔离级别;

查看事务的全局隔离级别：

select @@global.tx_isolation;

## 索引

索引就是一本书的目录，通过目录可以快速的找到对应的资源。

在数据库方面，查询一张表有两种检索方式：全盘扫描和根据索引检索（效率很高）。

索引最根本的原理就是缩小了扫描范围，索引虽然可以提高检索效率，但不能随意添加索引，因为索引也是数据库中的对象，也需要数据库不断的维护。一旦数据修改，索引需要重新排序，进行维护。

添加索引是给某个字段或某些字段添加索引。当字段没有添加索引时，SQL语句会进行全表扫描。当字段添加索引后，SQL语句会根据索引扫描，快速定位。

### 创建索引

创建索引需要满足的条件：

- 数据量庞大
- 该字段很少的DML操作
- 该字段经常出现在where子句中

**主键和具有unique约束的字段自动回添加索引。因此根据主键查询效率较高，尽量根据主键检索。**

查看SQL语句的执行计划（MySQL特有）：

explain SQL语句;

添加索引：

create index 索引名称 on 表名(字段名);

删除索引：

drop index 索引名称 on 表名;

### 索引的原理

索引采用的数据结构是：B+tree

索引通过B tree 缩小扫描范围，底层索引进行了排序，分区，索引会携带数据在表中的“物理地址”，最终通过索引检索到数据之后，获取到关联的物理地址，通过物理地址定位表中的数据，效率是最高的。

eg.  select ename from emp where ename = 'SMITH';

​		通过索引转换为：

​		select ename from emp where 物理地址 = 0x3;

### 索引的分类

索引分为：

- 单一索引：给单个字段添加索引
- 复合索引：给多个字段联合起来添加一个索引
- 主键索引：主键上会自动添加索引
- 唯一索引：有unique约束的字段上会自动添加索引

### 索引失效

在进行模糊查询时，第一个通配符使用的是%，这时索引会失效。

## 视图（view）

视图就是 站在不同的角度去看数据（同一张表的数据通过不同的角度去看待）。

### 创建删除视图

create view 视图名 as DQL语句;

drop view 视图名;

对视图进行增删改查，会影响到原表数据。（通过视图影响原表数据，不是直接操作原表）

### 视图的作用

视图可以隐藏表的实现细节。保密级别较高的系统，数据库只对外提供相关的视图。程序员只对视图对象进行CRUD。

## DBA命令

### 新建用户

命令：

create user 用户名 identified by '密码';

### 授权用户

命令：

grant all privileges on dbname.tbname to 'username'@'login ip' identified by 'password' with grant option;

dbname=* 表示所有数据库

tbname=* 表示所有表

login ip=% 表示任何IP

with grant option 表示该用户还可以授权给其他用户

###  撤销权限

命令

revoke privileges on dbname[.tbname] from username;

### 导出数据库

dos命令窗口下：

mysqldump 数据库名 [表名]>导出路径\文件名.sql -u root -p333;

可以导出指定数据库的指定数据表。

### 导入数据库

需要先创建数据库，然后进行导入

source 文件路径

## 数据库设计三范式

设计模式：设计表的依据，按照这个三范式设计表不会出现数据冗余。

### 三范式

- 第一范式：任何一张表都应该有主键，并且每个字段原子性不可再分。
- 第二范式：建立在第一范式的基础上，所有非主键字段完全依赖主键，不能产生部分依赖。
- 第三范式：建立在第二范式的基础上，所有非主键字段直接依赖主键，不能产生传递依赖。

### 表的经典设计方案

在实际开发过程中，以满足客户的需求为主，有的时候会拿冗余换执行速度。

- 在一对一的情况下，有可能需要拆成两张表。在设计时，可以选择两种方案，分别是主键共享和外键唯一。
  - 主键共享是第一张表有主键，第二张表的主键是既是主键也是外键。
  - 外键唯一是第一张表有主键，第二张表多加一个字段，多出来的字段是第一张表的主键，并且添加外键约束和唯一性约束。

- 在一对多的情况时，设置两张表，多的表加外键。
- 在多对多的情况时，设置三张表，关系表两个外键。

