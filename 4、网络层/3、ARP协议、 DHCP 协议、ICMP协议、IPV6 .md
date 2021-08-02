> 缺乏**目的、目标、方法、效率**再勤奋也只是一种时间的牺牲
> 专注 静心

@[toc]
# ARP  协议
## 发送数据的过程
![在这里插入图片描述](https://img-blog.csdnimg.cn/37b4776ee91a410782bd7bd90a2f6518.png)

> 考研基于此五层模型 ： 物联网输用 
> OSI  标准的七层模型： 物联网淑惠试用



如何处理无ARP高速缓存 IP地址与MAC地址的映射情况？

答： 采取广播ARP请求分组（一种帧的形式）

### 源主机和目的主机在同一个网络
如下 主机1要与主机3  进行通信：
![在这里插入图片描述](https://img-blog.csdnimg.cn/a15d415e701f43f290d54f2ce04e2577.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L1F1YW50dW1Zb3U=,size_16,color_FFFFFF,t_70)

### 源主机和目的主机不在同一个网络
- 一般而言交换器没有 MAC 地址，只有主机与路由器才有MAC   地址

如下 主机1要与主机5 进行通信：

![在这里插入图片描述](https://img-blog.csdnimg.cn/57554f40aadf4082a022bc32d0666e98.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L1F1YW50dW1Zb3U=,size_16,color_FFFFFF,t_70)

## ARP 总结
- ARP（Address Resolution Protocol） 地址解析协议

由于在实际网络的链路上传送数据帧时，最终必须使用MAC地址
- **ARP协议**：完成主机或路由器IP地址到MAC地址的映射。解决下一跳走哪的问题。
- **ARP协议使用过程** ： 检查ARP高速缓存，有对应表项则写入MAC帧，没有则用目的MAC地址为 FF-FF-FF-FF-FF-FF的帧封
装并==广播ARP请求分组==，==同一局域网==中所有主机都能收到该请求。目的主机收到请求后就会向源主机==单播一个ARP响应分组==，源主机收到后将此映射写入**ARP缓存**（1020min更新一次）.

<font color=red size=4>**ARP协议4种典型情况**：</font>

 1. 主机A发给**本网络**上的主机B：用ARP找到主机B的硬件地址；
 2. 主机A发给**另一网络**上的主机B：用ARP找到本网络上一个路由器（网关）的硬件地址；
 3. 路由器发给**本网络**的主机A：用ARP找到主机A的硬件地址；
 4. 路由器发给**另一网络**的主机B：用ARP找到本网络上的一个路由器的硬件地址。

ARP   协议自动进行

- 主机发送P数据报给主机B,经过了5个路由器，请问此过程总共使用了几次ARP协议？   6次

# DHCP 协议
 - 动态主机配置协议DHCP是==应用层==协议，使用==客户/服务器==方式，客户端和服务端通过==广播方式==进行交互，基于==UDP==

 -   DHCP提供**即插即用**联网的机制，主机可以从服务器动态获取P地址、子网掩码、默认网关、DNS服务器名称与P地址，**允许地址重用**，支持**移动用户加入网络**，支持**在用地址续租**。

## 发送流程

 1. 主机广播DHCP发现报文
 2. DHCP服务器广播DHCP提供报文
 3. 主机广播DHCP请求报文
 4. DHCP服务器广播DHCP确认报文


# ICMP 协议
- ICMP（Internet Control Message Protocol）Internet控制报文协议。它是TCP/IP协议簇的一个子协议，用于在IP主机、路由器之间传递控制消息。控制消息是指网络通不通、主机是否可达、路由是否可用等网络本身的消息。这些控制消息虽然并不传输用户数据，但是对于用户数据的传递起着重要的作用

**网际控制报文协议ICMP**

![在这里插入图片描述](https://img-blog.csdnimg.cn/f4f57f18be9d4bfbaecce539fc1fe3a4.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L1F1YW50dW1Zb3U=,size_16,color_FFFFFF,t_70)

### ICMP差错报告报文(5种
![在这里插入图片描述](https://img-blog.csdnimg.cn/4ec61e0ca2ab474193ee7a8d55844fa1.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L1F1YW50dW1Zb3U=,size_16,color_FFFFFF,t_70)
- 其中第二点**源点抑制**现在已经弃用

### ICMP差错报告报文数据字段


![在这里插入图片描述](https://img-blog.csdnimg.cn/64dc18a8f667452db19cdc03e176c41b.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L1F1YW50dW1Zb3U=,size_16,color_FFFFFF,t_70)
### 不应发送ICMP差错报文的情况
- 广播 ： 一点到所有节点
- 组播：一点到多个节点



 1. 对CMP差错报告报文不再发送ICMP差错报告报文。
 2. 对第一个分片的数据报片的所有后续数据报片都不发送CMP差错报告报文。
 3. 对具有组播地址的数据报都不发送ICMP差错报告报文。
 4. 对具有特殊地址(如127.0.0.0或0.0.0.0)的数据报不发送ICMP差错报告报文。

### ICMP  询问报文
- 1、**回送请求和回答报文** ： 主机或路由器向特定目的主机发出的询问，收到此报文的主机必须给源主机或路由器发送ICMP回送回答报文。==测试目的站是否可达以及了解其相关状态==
- 2、**时间戳请求和回答报文** ： 请某个主机或路由器回答当前的日期和时间。==用来进行时钟同步和测量时间==
- 3、掩码地址请求和回答报文
- 4、路由器询问和通告报文

注意： 后面两种报文现在已经弃用

### ICMP   应用
 - **PING**  : 测试两个主机间的连通性，使用==ICMP 回送请求和回答报文==
 - Traceroute   :  跟踪一个分组从源点到终点的路径，使用了ICMP时间超过差错报告报文

# IPV6
- 产生IPV 6 的原因： 32位的地址空间已经分配殆尽，CIDR  和NAT  协议治标不治本，IPV6 从根本上解决地址耗尽问题 
- 再者采用**改进首部格式的方式** 快速处理/ 转发 数据报 ==支持QoS==
QoS（ Quality of Service，服务质量）指个网络能够利用各种基础技术，为指定的网络通信提供更好的服务能力，是网络的一种安全机制，是用来解决网延迟和阻塞等问题的一种技术。

## IPV 6 数据报格式
![在这里插入图片描述](https://img-blog.csdnimg.cn/2c0c807b41714beb8ecccf1a7a1456de.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L1F1YW50dW1Zb3U=,size_16,color_FFFFFF,t_70)
**与IPV  4  的对照区别学习**

![在这里插入图片描述](https://img-blog.csdnimg.cn/5e2c7919b44440a5a6fff2d4d04020b2.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L1F1YW50dW1Zb3U=,size_16,color_FFFFFF,t_70)

[跳转连接](https://blog.csdn.net/QuantumYou/article/details/119203049?spm=1001.2014.3001.5501)

 ![在这里插入图片描述](https://img-blog.csdnimg.cn/5376f8dc0ff2496d8162e4b8d036d512.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L1F1YW50dW1Zb3U=,size_16,color_FFFFFF,t_70)
## IPV6与IPV4区别
- 1、IPV6将地址从32位(4B)扩大到==128位(16B)==,更大的地址空间。
- 2、IPV6将IPV4的**校验和字段彻底移除**，以减少每跳的处理时间
- 3、IPV6将IPV4的可选字段移出首部，变成了==扩展首部==，成为灵活的首部格式，路由器通常不对扩展首部进行检查，大大提高了路由器的处埋效率。
- 4、Pv6支持==即插即用==（即自动配置），不需要DHCP协议。
- 5、IPv6首部长度必须是==8B的整数倍==，IPv4首部是4B的整数倍
- 6、IPv6==只能在主机处分片==，IPv4可以在路由器和主机处分片。
- 7 、ICMPV6:附加报文类型“分组过大”。
- 8、IPv6支持资源的预分配，支持实时视像等要求，保证一定的带宽和时延的应用。
- 9、IPv6取消了协议字段，改成下一个首部字段。
- 10、IPv6取消了总长度字段，改用有效载荷长度字段
- 11、IPV6取消了服务类型字段。

## IPV6 地址表现形式

![在这里插入图片描述](https://img-blog.csdnimg.cn/82d45840973a44a8b54e46118e6000e8.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L1F1YW50dW1Zb3U=,size_16,color_FFFFFF,t_70)
==注意==： 双冒号表示法在一个地址中只能表示一次  


## IPV6  基本地址
![在这里插入图片描述](https://img-blog.csdnimg.cn/4ca5a2dedea04088bbe8f289394e9081.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L1F1YW50dW1Zb3U=,size_16,color_FFFFFF,t_70)
## IPV 6 向IPV4 的过度策略
<font color=skyblue size=4>**双协议栈**</font>
- 双协议栈技术就是指在一台设备上==同时启用IPV4协议栈和IPV6协议栈==。这样的话，这台设备既能和IPV4网络通信，又能和IPV6网络通信。如果这台设备是一个==路由器==，那么这台路由器的不同接口上，分别配置了PV4地址和Pv6地址，并很可能分别连接了IPV4网络和IPV6网络。如果这台设备是一个==计算机==，那么它将同时拥有IPV4地址和IPV6地址，并具备同时处理这两个协议地址的功能。

<font color=skyblue size=4>**隧道技术**</font>
- 通过使用互联网络的基础设施在网络之间传递数据的方式。使用隧道传递的数据（或负载）可以是不同协议的数据帧或包。隧道协议将其它协议的数据帧或包==重新封装==然后通过隧道发送。
![在这里插入图片描述](https://img-blog.csdnimg.cn/3e2425867f0344309927778a8a9d076d.png)
## 小结思维导图
![在这里插入图片描述](https://img-blog.csdnimg.cn/d9b5461f4cc746e0b5466231632e161c.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L1F1YW50dW1Zb3U=,size_16,color_FFFFFF,t_70)

