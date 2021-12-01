# tomcat的安全设置

## 1. 初始化配置

### （1） 关闭服务器端口

外人可以通过telnet连接到Tomcat，然后使用shutdown命令关闭服务器，因此需要把shutdown命令更改为不易被知道的命令。

> 在项目文件中的conf\server.xml中
>
> 修改第22行的shutdown命令，改为
>
> ```xml
> <Server port = "8006" shutdown = "自定义的命令">
> ```

### （2）隐藏版本信息

黑客可以针对版本做针对性的攻击，因此我们需要隐藏或修改版本信息。

> 修改方式：
>
> 在项目文件中的lib\catalina.jar\org\apache\catalina\util\ServerInfo.properties 中
>
> 修改server.info 改为 server.info = NO SERVICE

### （3)  禁用Tomcat管理页面

黑客可以通过管理页面进行攻击，因此可以将webapps\ROOT 重命名，然后创建一个空的ROOT文件。

###   (4)  自定义错误页面

默认的错误页对用户很不友好，而且可能有一些安全隐患。因此我们可以将错误文件自定义。将自定义的error.html 页面放到webapps\ROOT\下，然后在conf\web.xml 文件中添加一些错误码。

```xml
<error-page>

	<error-code>400</error-code>

	<location>/error.html</location>

</error-pade>

<error-page>

	<error-code>404</error-code>

	<location>/error.html</location>

</error-pade>

<error-page>

	<error-code>500</error-code>

	<location>/error.html</location>

</error-pade>
```

### （5）AJP端口管理

AJP 是为Apache 和Tomcat 之间通信而定制的协议，它可以提供比较高的通信速度和效率。在项目开发中，如果Tomcat 前端使用的是Apache服务器时就会使用到AJP 连接器，但是前端如果用的是Nginx 做的前端代理的话，就可以不使用这个连接器，因此我们需要把这个连接器注释掉。在conf\server.xml 文件中的第97行，

<Connector port = "8019" protocol = "AJP/1.3" redirectPort = "8443"/>

### （6）启用cookie的HttpOnly

启用Httponly 可以提高cookie的安全性。黑客可以通过XSS 攻击，把恶意脚本插入到浏览器页面中，当用户浏览页面时，恶意代码会执行，从而达到对用户的攻击。启动Httponly 后，程序无发读取cookie的信息。

> 启动Httponly：
>
> 在conf\context.xml 文件中，在context中添加属性。
>
> ```xml
> <Context userHttpOnly = "true">
> ```

## 2. Tomcat的安全规范

(1)  用户权限的配置

给用户在可用状态下的最小权限。

在conf\tomcat.xml 文件中

```xml
<role rolename = "manager-gui"/>
<role rolename = "admin-gui"/>
<user username = "tomcat" password = "dome1234" roles = "manager-gui,admin-gui"/>
```

(2)  日志配置操作

应该给用户登录进行记录。

在conf\server.xml 文件中，把142-144行取消注释。

```xml
<valve classname = "org.apache.cataline.valves.AccessLogValve" Directory = "logs" Prefix = "localhost_access_log." Suffix = ".txt" Patttern = "common" resloveHosts = "false"/>
```

(3)  定时登出

其他设备用户登录时，应设置登录时间限制，提高安全性。

在conf\server.xml 文件中的第72-74行中的connectionTimeout属性。

```xml
<Connector port="8081" portocol="HTTP/1.1" connectionTimeout="20000" redirectPort="8443"/>
```

## 3. 运动模式

运动模式可以有效提升性能

- BIO：tomcat7以下的默认模式，效率低。
- DIO：基于缓存区、非阻塞的I/O
- APR：tomcat7以上的默认模式