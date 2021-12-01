# 安装mysql

**第一步**，查看是否安装：

```js
rpm -qa| grep mysql-server
```

没有我们就开始安装，点击 [这里](https://dev.mysql.com/downloads/mysql/5.7.html#downloads)，获取下载页面，按照图示选择合适的版本：

![img](https://ask.qcloudimg.com/http-save/2539306/4g8s25i9rb.png?imageView2/2/w/1620)

**第二步**，进入`/usr/local/soft/`目录，在里面执行`wget 下载链接`命令，或者是先下载到windows然后通过xftp上传到CentOS的该目录下，然后使用`tar -zxvf mysql-5.7.29-linux-glibc2.12-x86_64.tar.gz`命令进行解压；

**第三步**，使用命令`mv mysql-5.7.29-linux-glibc2.12-x86_64 mysql`命令修改一下文件的名称为[mysql](https://cloud.tencent.com/product/cdb?from=10680)。

**第四步**，创建mysql用户组和用户并修改权限，使用的命令如下：

```js
groupadd mysql
useradd -r -g mysql mysql
```

接着创建数据目录并赋予权限，使用的命令如下（注意必须使用mysql用户，不能使用root用户，否则会由于文件从属关系导致mysql启动失败）：

```js
mkdir -p  /data/mysql              #创建目录
chown mysql:mysql -R /data/mysql   #赋予权限
```

**第五步**，使用命令`vi /etc/my.cnf`修改配置文件，往其中新增以下代码：

```js
[mysqld]
bind-address=0.0.0.0
port=3306
user=mysql
basedir=/usr/local/soft/mysql  # mysql安装目录
datadir=/data/mysql  # 数据存放目录
socket=/tmp/mysql.sock
log-error=/data/mysql/mysql.err
pid-file=/data/mysql/mysql.pid
#character config
character_set_server=utf8mb4
symbolic-links=0
explicit_defaults_for_timestamp=true
```

**第六步**，开始初始化数据库。进入mysql的bin目录，我这里是`/usr/local/soft/mysql/bin`路径，然后在里面执行下面一行代码（注意里面两个路径必须与你在my.cnf配置文件中设置的一致，否则会报错）：

```js
./mysqld --defaults-file=/etc/my.cnf --basedir=/usr/local/soft/mysql/ --datadir=/data/mysql/ --user=mysql --initialize
```

执行完可以看到会出现一个临时密码（复制一下，后面进入数据库需要使用到）：

![img](https://ask.qcloudimg.com/http-save/2539306/bni2tt0zhk.png?imageView2/2/w/1620)

**第七步**，启动mysql服务。注意先将`mysql.server`放置到`/etc/init.d/mysql`中，可以让dameon来管理Mysql的启动(即也就是service，CentOS7就是syetemctl)，可以使用下面的命令复制一份过去，且将`mysql.server`修改为mysql，这样便于记忆启动命令：

```js
cp /usr/local/soft/mysql/support-files/mysql.server /etc/init.d/mysql
```

完成复制后就使用命令`service mysql start`启动mysql，注意如果在此过程中出现下面的错误：

```js
Starting MySQL...The server quit without updating PID file [FAILED]ysql/iZuf67on1pthsx5glu6ohyZ.pid).
```

请点击 [这里](https://blog.csdn.net/eagle89/article/details/79813405)，或者查看日志文件`/data/mysql/mysql.err`。然后使用命令`ps -ef|grep mysql`查看一下mysql是否真的已经启动了。

**第八步**，修改数据库密码。进入到mysql安装目录的bin目录下面，我的路径是`/usr/local/soft/mysql/bin`，然后使用前面随机生成的密码来进入数据库，使用的命令如下：

```js
./mysql -uroot -p临时密码
```

在数据库中接着执行以下三行代码：

```js
SET PASSWORD = PASSWORD('123456');
ALTER USER 'root'@'localhost' PASSWORD EXPIRE NEVER;
FLUSH PRIVILEGES; 
```

这样数据库密码就修改成功了。但是此时你如果远程连接数据库，你会发现无法联通，这是正常现象，因为你还没有开放访问IP端口。

**第九步**，开发访问IP端口。先进入到数据库，接着执行以下三行代码，这样就开放了数据库访问IP端口。

```js
use mysql;     #访问mysql库
update user set host = '%' where user = 'root';   #使root用户能在任何IP进行访问
FLUSH PRIVILEGES;
```

**第十步**，鉴于目前进入mysql都是需要进入到mysql安装的bin目录下，这是非常麻烦的，因此可以使用软连接`ln -s  /usr/local/soft/mysql/bin/mysql    /usr/bin`（注意语句结尾没有分号），这样以后就可以直接使用`mysql -uroot -p密码`快捷命令了。

由于mysql安装过程坑较多，这里附上mysql的安装包。点击 [这里](https://pan.baidu.com/s/1oZLaBAELK9tuB1FCfQfzUg) 获取，文档密码：mvji。最后祝你好运，一次成功哈。

### 完全卸载mysql

前面介绍了如何安装mysql，现在介绍如何完全卸载mysql。如果你是使用yum安装的mysql，如果想要完全卸载mysql，可以按照下面的方式进行卸载：

**第一步**，使用下面的命令查看mysql安装了哪些依赖：

```js
rpm -qa |grep -i mysql
```

**第二步**，依次执行下面的命令开始卸载mysql及其依赖：

```js
yum remove mysql-community-common-5.7.20-1.el7.x86_64
yum remove mysql-community-client-5.7.20-1.el7.x86_64
yum remove mysql57-community-release-el7-11.noarch
yum remove mysql-community-libs-5.7.20-1.el7.x86_64
yum removemysql-community-server-5.7.20-1.el7.x86_64
```

**第三步**，继续使用第一步中的命令来查看mysql是否卸载完成：

```js
rpm -qa |grep -i mysql
```

**第四步**，使用下面的命令来查找mysql相关目录信息：

```js
find / -name mysql
```

**第五步**，使用下面的命令来删除mysql相关目录信息：

```js
rm -rf  目录信息
```

**第六步**，使用下面的命令来删除`/etc/my.cnf`配置文件：

```js
rm -rf /etc/my.cnf
```

**第七步**，使用下面的命令来删除`/var/log/mysqld.log`日志文件，注意如果不删除这个文件，会导致新安装的mysql无法生成新密码，进而导致无法登陆：

```js
rm -rf /var/log/mysqld.log
```