# Nmap的使用

### Nmap扫描原理

首先判断nmap输入的命令行是否包含域名，如果包含需要利用DNS服务器进行域名解析，然后发送ICMP EchoRequest来探测主机存活性。

### Nmap的使用

nmap [参数] ip或域名

参数：

-h：查看帮助nmap自带的帮助信息

--iflist：查看所有网卡信息。

-e interface ：指定扫描的网卡。

主机发现

-iL：从文件中进行主机发现

-sL：仅列出网段上的所有主机，不发送报文

-sP：使用ping进行扫描

-PS：TCP SYN ping扫描

-PA：TCP ACK 扫描

-n：禁止反向DNS解析

-Pn/-PO：对于已经知道主机存活或防火墙开启的机器，使用-Pn参数来停止之前的ICMP请求。已达到不触发防火墙安全机制。无ping扫描。

-traceroute：路由跟踪

--dns-servers 域名服务器：指定域名解析的服务器

端口扫描

-A：全面扫描/综合扫描

-sS：使用SYN半开放式扫描，隐蔽扫描

-sT：扫描开放的TCP端口

-sU：扫描开放的UDP端口

-p m-n：nmap默认只会对一部分端口进行探测，可能不满足工作需求，因此使用-p m-n来指定探测端口范围为m-n之间的所有端口。

-T4：快速扫描，常规的扫描方式

-sV ：版本探测，配合-A参数结果更详细

--top-ports100：对最常用的100个端口进行扫描

-allports：全端口探测

-O：启动操作系统探测

-v：显示扫描过程中的扫描细节

--script=firewalk：使用脚本探测防火墙

结果输出

-oN：标准保存

-oX：xml保存

-oA：保存到所有格式

### 端口状态

open：表示端口处于开放状态

closed：表示端口处于关闭状态

filterd：表示端口被防火墙IDS/IPSp屏蔽，无法确认状态

unfilterd：表示端口没有被屏蔽，但是否开放需要进一步确认

opend/unfilterd：表示端口处于开放状态或被屏蔽

closed/unfilterd：表示端口处于关闭状态或被屏蔽

### 服务指纹

为了确保有一个成功的渗透测试或网络设备监控，必须要知道目标系统中服务的指纹信息，服务指纹信息包括服务端口、服务名和版本等。

通过分析目标往Nmap发送数据包中某些协议标记、选项和数据，我们可以推断发送这些数据包的操作系统等。

Nmap通过向目标主机发送多个UDP与TCP数据包并分析其响应来进行操作系统指纹识别工作。

-sV IP地址：识别目标及其的服务信息。

### Nmap侵略性探测

nmap -A -v- T4 IP地址：来探测目标机器的操作系统、服务等信息。

nmap -sC -sV -O：来探测目标机器的操作系统、服务等信息。

参数：-sC：表示使用Nmap脚本进行探测，-sV：表示探测目标机器上的服务信息，-O：表示探测目标机器的操作系统信息。

### Nmap主机发现

CIDR：无类别域间路由，网络名。eg.192.168.1.0/24

nmap -sP CIDR：对该网络中所有主机进行ping扫描，以探测主机存活性，扫描过程中使用了TCP SYN 扫描、ICMP echo Request来探测主机存活。

nmap -sn CIDR：对该网络中所有主机进行ping扫描，以探测主机存活性。

nmap -sn CIDR -oX 文件名.xml：将扫描结果存入xml文件中。

### 端口探测技巧

nmap -p[端口] IP：针对某个端口进行探测。

-p后可以跟多个端口。eg. nmap -p80,135,445 192.168.1.118

-p-：对所有端口进行测试。

-p 协议:端口：指定协议探测端口。eg. nmap -p T:25,U:53 192.168.2.118 （T是TCP协议，U是UDP协议）

### NSE的使用

NSE（Nmap Script Engine）是Nmap的脚本引擎，内置很多可以用来扫描的、针对特定任务的脚本。通过NSE可以不断拓展Nmap的扫描策略，加强Nmap的功能。

Nmap中使用--script 参数来指定调用的脚本，并且脚本存储在Nmap安装路径下的script文件夹下，对于kali linux 存储在/var/share/nmap/script/下。

nmap --script 脚本名称 IP：使用脚本探测IP

eg. nmap --script http-title scnme.nmap.org    探测web服务的title信息。

使用nmap的http-title 脚本并指定使用对应的User-Agent。

nmap -sV --script http-title --script-args http.useragent="Mozilla 999"

可以使用nmap --script-updatedb对NSE进行更新。

### NSE分类使用

对目标使用多个分类脚本进行探测，可以更快的找到目标的信息与弱点。

使用Nmap中漏洞分类脚本对目标进行探测：

nmap -sV --script vuln 目标

使用Nmap中发现和版本信息分类进行探测：

nmap -sV --script=“version，discovery” 目标

使用Nmap中http*的脚本，但是除了（http-brute和http-sloweors）：

nmap -sV --script “http*） and not （http-slowors and http-brute）

NSE调试

使用nmap中exploit，可以开启调试模式。

nmap -sV --script exploit -d [数字] --script-trace 目标

注意：-d是debug，范围是0-9

### ndiff工具

对比两个xml文件的不同，不同点包括状态的改变，端口状态的改变，服务状态的改变，操作系统的改变。

ndiff [参数] file1 file2

参数：--text：使用text形式展示（默认）

​            --xml：使用xml形式展示


