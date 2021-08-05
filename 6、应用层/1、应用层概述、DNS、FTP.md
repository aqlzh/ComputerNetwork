> 唯有热爱，可抵岁月漫长
> 
@[toc]
# 应用层概述
应用层对应用程序的通信提供服务。

<font color=red>**应用层协议定义**</font>：
- 应用进程交换的报文类型，请求还是响应？
- 各种报文类型的语法，如报文中的各个字段及其详细描述
- 字段的语义，即包含在字段中的信息的含义。
- 进程何时、如何发送报文，以及对报文进行响应的规则

**应用层的功能：**
1、文件传输、访问和管理
2、电子邮件
3、虚拟终端
4、査询服务和远程作业登录


**应用层的重要协议** ：
1、FTP
2、SMTP、POP3
3、HTTP
4、DNS

## 网络应用模型
<font color=red>**客户/服务器模型**</font>（ Client/ Server ）（CS）
![在这里插入图片描述](https://img-blog.csdnimg.cn/5d96850c222943008e6075c0df07f436.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L1F1YW50dW1Zb3U=,size_16,color_FFFFFF,t_70)

- **服务器**：提供计算服务的设备。
1.永久提供服务
2.永久性访问地址/域名

- **客户机**：请求计算服务的主机。
1.与服务器通信，使用服务器提供的服务
2.间歇性接入网络
3.可能使用动态IP地址

- 应用：Web,文件传输FTP,远程登录，电子邮件

<font color=red>**P2P模型**</font>(Peer-to-peer)
![在这里插入图片描述](https://img-blog.csdnimg.cn/7fefc13d3d114d279ac6212e53cf8f61.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L1F1YW50dW1Zb3U=,size_16,color_FFFFFF,t_70)
不存在永远在线的服务器
每个主机既可以**提供服务**，也可以**请求服务**
任意端系统/节点之间可以**直接通讯**
节点间歇性接入网络
节点可能改变P地址
可扩展性好
网络健壮性强


# DNS 域名解析系统
## 域名
![在这里插入图片描述](https://img-blog.csdnimg.cn/c95d5f006d9f4f999d48e10c067416ce.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L1F1YW50dW1Zb3U=,size_16,color_FFFFFF,t_70)
![在这里插入图片描述](https://img-blog.csdnimg.cn/cc1b777bb773439081f949f0bcd74694.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L1F1YW50dW1Zb3U=,size_16,color_FFFFFF,t_70)
**本地域名服务器**：当一个主机发出DNS查询请求时，这个查询请求报文就发给本地域名服务器。



![在这里插入图片描述](https://img-blog.csdnimg.cn/109a7fa2a78742afbabb45da7358647a.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L1F1YW50dW1Zb3U=,size_16,color_FFFFFF,t_70)

## 域名解析过程
递归查询 、迭代查询
![在这里插入图片描述](https://img-blog.csdnimg.cn/bc35311d2a4d467ebe0daa08c3e51806.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L1F1YW50dW1Zb3U=,size_16,color_FFFFFF,t_70)

# 文件传输协议 FTP
其中可以分为 ==文件传送协议FTP==( File Transfer Protocol)、==简单文件传送协议TFTP==( Trivial File Transfer Protocol) 两大类型

<font color=red>**文件传送协议FTP**</font>( File Transfer Protocol)
- 提供不同种类主机系统(硬、软件体系等都可以不同)之间的文件传输能力。

## FTP服务器和用户端
FTP是基于客户/服务器(C/S)的协议
- 用户通过一个客户机程序连接至在远程计算机上运行的服务器程序。
- 依照FTP协议提供服务，进行文件传送的计算机就是FTP服务器。
- 连接FTP服务器，遵循FTP协议与服务器传送文件的电脑就是FTP客户端。

## FTP 工作原理
- 常规方式：ftp地址  `用户名&密码`
- **匿名登陆** ：互连网中有很大一部分FTP服务器被称为“匿名”（ Anonymous）FTP服务器。这类服务器的目的是向公众提供文件拷贝服务，不要求用户事先在该服务器进行==登记注册==，也不用取得FTP服务器的==授权==。Anonymous（匿名文件传输）能够使用户与远程主机建立连接并以匿名身份从远程主机上拷贝文件，而不必是该远程主机的注册用户。用户使用特殊的用户名“ anonymous"登陆FTP服务，就可访问远程主机上公开的文件。
- FTP使用TCP实现可靠传输

![在这里插入图片描述](https://img-blog.csdnimg.cn/7b727aaefd2541f4a5f84c0407e13d88.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L1F1YW50dW1Zb3U=,size_16,color_FFFFFF,t_70)
**FTP传输模式**
文本模式：ASC模式，以文本序列传输数据；
二进制模式： Binary/模式，以二进制序列传输数据
