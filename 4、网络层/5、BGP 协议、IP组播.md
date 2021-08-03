> - 我希望你没有刻意为追求一个数字而生活，我希望你找到了真正的价值所在
> - 你一定要坚持做自己，静下心来做自己喜欢的事，然后把自己交给命运

@[toc]
# BGP 协议
## 路由选择协议分类
![在这里插入图片描述](https://img-blog.csdnimg.cn/6abe33084fb0469bb6042b7ff53ad989.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L1F1YW50dW1Zb3U=,size_16,color_FFFFFF,t_70)
## BGP 协议概述
- **和谁交换**？与其他AS的邻站BGP发言人交换信息。
- **交换什么**？交换的网络可达性的信息，即要到达某个网络所要经过的一系列AS.
- **多久交换**？发生变化时更新有变化的部分。 

![在这里插入图片描述](https://img-blog.csdnimg.cn/c09e0d5a083e4463b4b705ab2467ea08.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L1F1YW50dW1Zb3U=,size_16,color_FFFFFF,t_70)
## BGP协议交换信息的过程
- BGP所交换的网络可达性的信息就是要==到达某个网络所要经过的一系列AS==。当BGP发言人互相交换了网络可达性的信息后，各BGP发言人就根据所米用的策略从收到的路由信息中找出到达各AS的较好路由。


![在这里插入图片描述](https://img-blog.csdnimg.cn/07a05737e8aa4d14886fbbc8f9ac62a4.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L1F1YW50dW1Zb3U=,size_16,color_FFFFFF,t_70)
**BGP发言人交换路径向量：**
- 自治系统AS2的BGP发言人通知主干网AS1的BGP发言人：“要到达网络N1、N2、N3和N4可经过AS2
![在这里插入图片描述](https://img-blog.csdnimg.cn/f7443485946d4e1a99e30960175e2a54.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L1F1YW50dW1Zb3U=,size_16,color_FFFFFF,t_70)
**BGP发言人交换路径向量：**
- 主干网还可发出通知：“要到达网络N5、N6和N7可沿路径(AS1,AS:)。

![在这里插入图片描述](https://img-blog.csdnimg.cn/a90d63d94f244d80b64ac330b210fbc3.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L1F1YW50dW1Zb3U=,size_16,color_FFFFFF,t_70)
## BGP协议报文格式
- 一个BGP发言人与其他自治系统中的BGP发言人要交换路由信息，就要先建立TCP连接，即通过TCP传送，然后在此连接上交换BGP报文以建立BGP会话( session),利用BGP会话交换路由信息。

![在这里插入图片描述](https://img-blog.csdnimg.cn/9ffb1b622fb14c61b34a4c88fa19f1aa.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L1F1YW50dW1Zb3U=,size_16,color_FFFFFF,t_70)
## BGP 协议特点
- BGP==支持CIDR==,因此BGP的路由表也就应当包括目的网络前缀、下一跳路由器，以及到达该目的网络所要经过的各个自治系统序列。
- 在BGP刚刚运行时，BGP的邻站是交换整个的BGP路由表。但以后只需要在==发生变化时更新有变化的部分==。这样做对节省网络带宽和减少路由器的处理开销都有好处。

## BGP-4 四种报文
- 1、<font color=red>**OPEN（打开）报文**</font>：用来与相邻的另一个BGP发言人建立关系，并认证发送方
- 2、 <font color=red>**UPDATE（更新）报文**</font>：通告新路径或撤销原路径。
- 3、  <font color=red>**KEEPALIVE（保活）报文**</font>：在无 UPDATE时，周期性证实邻站的连通性；也作为OPEN的确认。
- 4、 <font color=red>**NOTIFICATION（通知）报文**</font>：报告先前报文的差错；也被用于关闭连接。

## 三种路由协议比较
![在这里插入图片描述](https://img-blog.csdnimg.cn/101e1c894a824acd83b0625a72d6d834.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L1F1YW50dW1Zb3U=,size_16,color_FFFFFF,t_70)
![在这里插入图片描述](https://img-blog.csdnimg.cn/d506ad2a06ae4c9cbaa8fd902e3f4354.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L1F1YW50dW1Zb3U=,size_16,color_FFFFFF,t_70)
# IP 组播
## IP数据报的三种传输方式
- <font color=red size=5>**单播**</font>：单播用于发送数据包到单个目的地，且每发送一份单播报文都使用一个单播IP地址作为目的地址。是一种==点对点传输方式==。下图为单播，在发送者和每一接收者之间需要单独的数据信道

![在这里插入图片描述](https://img-blog.csdnimg.cn/b248c16613284c4bb75fefc4808530c2.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L1F1YW50dW1Zb3U=,size_16,color_FFFFFF,t_70)

- <font color=red size=5>**广播**</font>：广播是指发送数据包到同一广播域或子网内的所有设备的一种数据传输方式是一种==点对多点传输方式==。多播图示如下：
- 组播提高了数据传送效率。减少了主干网出现拥塞的可能性。组播组中的主机可以是在同个物理网络，也可以来自不同的物理网络（如果有组播路由器（运行组**播协议的路由器**（可运行组播也可以运行单播））的支持）。

![在这里插入图片描述](https://img-blog.csdnimg.cn/c317262e57fb4903b8212c66df3d06e8.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L1F1YW50dW1Zb3U=,size_16,color_FFFFFF,t_70)

- <font color=red size=5>**组播**</font>：当网络中的某些用户需要特定数据时，组播数据发送者仅发送一次数据，借助组播路由协议为组播数据包建立组播分发树，被传递的数据到达距离用户端尽可能近的节点后才开始复制和分发，是种==点对多点传输方式==。

## IP 组播地址
解决如何确定该主机是一个主播组内

- IP组播地址让源设备能够将分组发送给一组设备。属于多播组的设备将被分配**一个组播组IP地址**（一群共同需求主机的相同标识）。

- 组播地址范围为`224.0.0.0~239.255.255.255`（D类地址），一个D类地址表示一个组播组。只能用作分组的==目标地址==。==源地址总是为单播地址==。

关于组播地址的注意事项：

- 1、组播数据报也是“尽最大努力交付”，不提供可靠交付，应用于UDP.
- 2、对组播数据报不产生CMP差错报文。

- 3、并非所有D类地址都可以作为组播地址。（有些地址作为特殊用途）

![在这里插入图片描述](https://img-blog.csdnimg.cn/959c2f3cff2c4f2ab05ec1590944b3c8.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L1F1YW50dW1Zb3U=,size_16,color_FFFFFF,t_70)
## 硬件组播
- 同单播地址一样，组播IP地址也需要相应的组播MAC地址在本地网络中实际传送帧。组播MAC地址以十六进制值`01-00-5E`打头，余下的6个十六进制位是根据P组播组地址的最后23位转换得到的。
- TCP/P协议使用的以太网多播地址的范围是：从`01-00-5E-00-00-00到01-00-5E-7F-FF-FF`


![在这里插入图片描述](https://img-blog.csdnimg.cn/c4ec474e317244348859dc0f389cb37b.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L1F1YW50dW1Zb3U=,size_16,color_FFFFFF,t_70)
如何解决前5位不一样，后面相同的问题：
- 收到多播数据报的主机，还要在IP层利用软件进行过滤，把不是本主机要接收的数据报丢弃。

## IGMP协议与组播路由选择协议
IGMP 协议：在一个路由器内部所使用的协议，组播路由器通过该协议了解是否还有主机。

**网际组管理协议IGMP**：

- lGMP协议让路由器知道本局域网上是否有主机（的进程）参加或退出了某个组播组。

![在这里插入图片描述](https://img-blog.csdnimg.cn/b035b9e92d984a5fbad086653b595300.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L1F1YW50dW1Zb3U=,size_16,color_FFFFFF,t_70)


![在这里插入图片描述](https://img-blog.csdnimg.cn/a9a45b4dd0454be19d56c1eec161d970.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L1F1YW50dW1Zb3U=,size_16,color_FFFFFF,t_70)
## lGMP工作的两个阶段
- **阶段一**：某主机要加入组播组时，该主机向组播组的组播地址发送一个IGMP报文，声明自己要称为该组的成员。本地组播路由器收到GMP报文后，要利用组播路由选择协议把这组成员关系发给因特网上的其他组播路由器。
- **阶段二**：本地组播路由器周期性探询本地局域网上的主机，以便知道这些主机是否还是组播组的成员。只要有一个主机对某个组响应，那么组播路由器就认为这个组是活跃的；如果经过几次探询后没有一个主机响应，组播路由器就认为本网络上的没有此组播组的主机，因此就不再把这组的成员关系发给其他的组播路由器。

- 组播路由器知道的成员关系只是所连接的局域网中有无组播组的成员

## 组播路由选择协议
- 组播路由选择协议目的是找出以源主机为==根节点==的组播转发树

- 构造树可以避免在路由器之间兜圈子。
- 对不同的多播组对应于不同的多播转发树；同一个多播组，对不同的源点也会有不同的多播转发树。
![在这里插入图片描述](https://img-blog.csdnimg.cn/310f6b37913d4a508110a627c87c5aff.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L1F1YW50dW1Zb3U=,size_16,color_FFFFFF,t_70)

<font color=red >**组播路由选择协议常使用的三种算法**</font>：
- 基于链路状态的路由选择
- 基于距离-向量的路由选择
- 协议无关的组播(稀疏/密集)


## 小结思维导图
![在这里插入图片描述](https://img-blog.csdnimg.cn/1bbafc43d5e2484aad90c87059362dbd.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L1F1YW50dW1Zb3U=,size_16,color_FFFFFF,t_70)

