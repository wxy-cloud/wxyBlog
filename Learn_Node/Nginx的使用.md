# 一. Nginx介绍

反向代理服务器，一般为服务器实现动静分离，负载均衡。

特点：1. 稳定性极强，7*24小时不断运行；2. Nginx提供了非常丰富的配置实例；3. 占用内存小，并发能力强。

# 二. Nginx的反向代理

## 	1. 正向代理

​			正向代理服务由客户端设立，客户端了解代理服务器和目标			服务器，正向代理是帮助客户端实现突破访问权限。提高访			问速度，对目标服务器隐藏客户端的IP地址。

<img src="C:\Users\86183\AppData\Roaming\Typora\typora-user-images\image-20210412111103569.png" alt="image-20210412111103569" style="zoom:80%;" />

## 	2. 反向代理

​			反向代理服务器是配置在服务端的，客户端是不知道访问的			道理是哪一台服务器。使用反向代理达到了负载均衡，并且			可以隐藏服务器的真正的IP地址。

<img src="C:\Users\86183\AppData\Roaming\Typora\typora-user-images\image-20210412111513368.png" alt="image-20210412111513368" style="zoom:80%;" />

# 三. 基于Nginx实现反向代理

准备一个目标服务器，启动令一个服务器，编写Nginx的配置文件，通过Nginx访问到服务器。

```json
server{
  listen 80;
  server_name localhost;
  location / {
  proxy_pass http://192.168.199.109:8080/;
  }
}
```

Nginx的location的路径映射

> 优先级关系：
>
> (location = ) >  (location = /xxx) > (location ^~) > (location ~,~*) > (location /起始路径) > (location /)

```json
# 1. 匹配
localtion = / {
	# 精准匹配，主机名后边不能带任何的字符串
}
```

```json
# 2. 通用匹配
location /xxx{
	# 匹配所有以/xxx开头的路径
}
```

```json
# 3. 正则匹配
location~ /xxx{
	# 匹配所有以/xxx开头的路径
}
```

```json
# 4. 匹配开头路径
location ^~ /images{
	# 匹配所有以/images开头的路径
}
```

```json
# 5. 
location ~* \.(gif|jpg|png)${
	#匹配以相应格式为结尾的路径
}
```

# 四. Nginx负载均衡

> Nginx为我们提供了三种负载均衡策略：
>
> 1. 轮询：将客户端发起的请求，平均的分配给每一台服务器。
> 2. 权重：会将客户端的请求，根据服务器的权重值不同，分配不同的数量。
> 3. IP_hash：基于发起请求的客户端的IP地址不同，他始终会将请求发送到指定的服务器上。

## 1. 轮询

> 想要实现Nginx轮询负载均衡机制只需要在配置文件中添加以下内容。

```json
# default.conf
upstream 名字 {
    server IP:port
    server IP:port
    ……
}
server {
    listen 80;
    server_name localhost;
    
    location /{
    proxy_pass http://upstream的名字/;
}
}
```

## 2. 权重

> 实现权重的方式

```json
# default.conf
upstream 名字 {
    server IP:port weight=权重比例
    server IP:port weight=权重比例
    ……
}
server {
    listen 80;
    server_name localhost;
    
    location /{
    proxy_pass http://upstream的名字/;
}
}
```

## 3. IP_hash

> 实现IP_hash的方式

```json
# default.conf
upstream 名字 {
    ip_hash;
    server IP:port weight=权重比例
    server IP:port weight=权重比例
    ……
}
server {
    listen 80;
    server_name localhost;
    
    location /{
    proxy_pass http://upstream的名字/;
}
}
```

# 五. Nginx的动静分离

> Nginx的并发能力：
>
> ​    wirker_processes * wirker_connections / 4 | 2 = Nginx最终的并发能力。
>
> 动态资源需要 / 4，静态资源需要 / 2 。
>
> Nginx通过Nginx通过动静分离，来提升Nginx的并发能力，更快的给用户响应。

## 1. 动态资源代理

```json
# 配置如下
location / {
  proxy_pass 路径;
}
```

## 2. 静态资源代理

```json
# 配置如下
location / {
  root 静态资源路径;
  index 默认访问路径下的什么资源;
  autoindex on;	# 代表展示静态资源的全部内容，以列表的形式展开。
}

```

# 六. Nginx集群

> 单点故障，避免Nginx的宕机，导致整个程序的奔溃
>
> 准备多台Nginx。
>
> 准备keepalived，监听Nginx的健康情况。
>
> 准备haproxy，提供一个虚拟的路径，统一的去接收用户的请求。

![image-20210412140013741](C:\Users\86183\AppData\Roaming\Typora\typora-user-images\image-20210412140013741.png)



