> 按照自己的节奏，竭尽全力（剩下的都留给命运）
你一定要做自己，做自己喜欢的事，然后把自己交给命运
加油！当自己的实力不能满足自己的目标时，就静下心去学习！，不要乱想与顾虑
一年后考研择校、现在开冲，静下心，积攒实力，厚积薄发，反正保底NCU
只要心甘情愿，二三战都不是事

@[toc]
# 广域网
- 广域网(WAN, Wide Area Network),通常跨接很大的物理范围，所覆盖的范围从几十公里到几千公里，它能连接多个城市或国家，或横跨几个洲并能提供远距离通信，形成国际性的远程网络。
- 广域网的通信子网主要使用==分组交换技术==。广域网的通信子网可以利用公用分组交换网、卫星通信网和无线分组交换网，它将分布在不同地区的**局域网或计算机系统**互连起来，达到==资源共享==的目的。如因特网( Internet)是世界范围内最大的广域网。

![在这里插入图片描述](https://img-blog.csdnimg.cn/510323f67e144bb6a8d10690cec3628c.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L1F1YW50dW1Zb3U=,size_16,color_FFFFFF,t_70)

小知识点：

> - 节点交换机：在单个设备间交换信息
> - 路由器 ： 在多个设备间交换信息
> - **局域网**覆盖的网络体系结构层次 :物理层、 链路层、强调数据传输
> - **广域网**覆盖的网络体系结构层次 ： 物理层、 链路层、网络层、因为范围广，所以数据传输快，但因为延迟，所以强调**资源共享**


## PPP 协议
**PPP协议的特点** ： 
- 点对点协议PPP( Point-to- Point Protocol)是目前使用最广泛的数据链路层协议，用户使用拨号电话接入因特网时一般都使用PPP协议。
- 只支持全双工链路。

### PPP协议应满足的要求
- **简单** : 对于链路层的帧，无需纠错，无需序号，无需流量控制
- **封装成帧** : 帧定界符
- **透明传输** : 与帧定界符一样比特组合的数据应该如何处理：异步线路用字节填充，同步线路用比特填充
- **多种网络层协议** : 封装的IP数据报可以采用多种协议。
- **多种类型链路** ： 串行/并行，同步/异步，电/光……
- **差错检测** ： 错就丢弃。
- **检测连接状态**：链路是否正常工作
- **最大传送单元** ： 数据部分最大长度MTU
- **网络层地址协商** ： 知道通信双方的网络层地址
- **数据压缩协商**

### PPP协议中无需满足的要求
- **纠错**
- **流量控制**
- **序号**
- **不支持多点线路**


### PPP协议的三个组成部分
- 1、一个将IP数据报封装到串行链路(同步串行/异步串行)的方法。
- 2、链路控制协议**LCP**:建立并维护数据链路连接。==身份验证==
- 3、网络控制协议**NCP**: PPP可支持多种网络层协议，每个不同的网络层协议都要一个相应的NCP来配置，为网络层协议建立和配置逻辑连接。

### PPP协议的状态图
![在这里插入图片描述](https://img-blog.csdnimg.cn/9ba1d76263d54cf580502295c809645f.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L1F1YW50dW1Zb3U=,size_16,color_FFFFFF,t_70)
### PPP 协议的帧格式
面向字节的协议
![在这里插入图片描述](https://img-blog.csdnimg.cn/807cfe6158f24c0687805650a04d3fb0.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L1F1YW50dW1Zb3U=,size_16,color_FFFFFF,t_70)
## HDLC 协议
高级数据链路控制(High- Level Data Link Controll或简称HDLC),是一个在同步网上传输数据、面向比特的数据链路层协议，它是由国际标准化组织(SIO)根据IBM公司的 SDLC(Synchronous Data Link Control协议扩展开发而成的。
- 数据报文可透明传输，用于实现透明传输的“0比特插入法”易于硬件实现
- 采用全双工通信
- 所有帧采用CRC检验，对信息帧进行顺序编号，可防止漏收或重份，传输可靠性高。

### HDLC的站
- 1、主站的主要功能是发送命令（包括数据信息）帧、接收响应帧，并负责对整个链路的控制系统的初启、
流程的控制、差错检测或恢复等。
- 2、从站的主要功能是接收由主站发来的命令帧，向主站发送响应帧，并且配合主站参与差错恢复等链路
控制。
-  3、复合站的主要功能是既能发送，又能接收命令帧和响应帧，并且负责整个链路的控制

三种数据操作方式
1.正常响应方式
2.异步平衡方式
3.异步响应方式

### HDLC的帧格式
![在这里插入图片描述](https://img-blog.csdnimg.cn/56bd75929fe7455b9e5c208f3b8afcf0.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L1F1YW50dW1Zb3U=,size_16,color_FFFFFF,t_70)
Tips : 无奸细

### PPP协议&HDLC协议

![在这里插入图片描述](https://img-blog.csdnimg.cn/c53c37c173b34553945290b8ca48926f.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L1F1YW50dW1Zb3U=,size_16,color_FFFFFF,t_70)
## 小结思维导图
![在这里插入图片描述](https://img-blog.csdnimg.cn/72f7482259714b1eb18208e2d3d5c699.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L1F1YW50dW1Zb3U=,size_16,color_FFFFFF,t_70)
# 链路层设备
## 物理层扩展以太网
![在这里插入图片描述](https://img-blog.csdnimg.cn/b060dfe15feb492b8e2dfbad5ea8b429.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L1F1YW50dW1Zb3U=,size_16,color_FFFFFF,t_70)
## 链路层扩展以太网
- **网桥**根据==MAC帧的目的地址==对帧进行**转发**和**过滤**。当网桥收到一个帧时，并不向所有接口转发此帧，而是先检查此帧的目的MAC地址，然后再确定将该帧转发到哪一个接口，或者是把它丢弃（即过滤）。


![在这里插入图片描述](https://img-blog.csdnimg.cn/d6122abd71b44db18f2d882e07f15e0c.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L1F1YW50dW1Zb3U=,size_16,color_FFFFFF,t_70)
<font color=red>**网桥优点**</font>
1.过滤通信量，增大吞吐量。
2.扩大了物理范围。
3.提高了可靠性
4.可互连不同物理层、不同MAC子层和不同速率的以太网。


**网段**：一般指一个计算机网络中使用同一物理层设备(传输介质，中继器，集线器等）能够直接通讯的那部分。


## 网桥分类一一透明网桥
- **透明网桥**：“透明”指以太网上的站点并不知道所发送的帧将经过哪几个网桥，是一种即插即用设备——自学习
![在这里插入图片描述](https://img-blog.csdnimg.cn/41fe16d17c6b4222b988454d9575f916.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L1F1YW50dW1Zb3U=,size_16,color_FFFFFF,t_70)
## 网桥分类一一源路由网桥
- **源路由网桥**：在发送帧时，把详细的最佳路由信息(路由最少/时间最短)放在帧的首部中。
- **方法**：源站以广播方式向欲通信的目的站发送一个发现帧。

![在这里插入图片描述](https://img-blog.csdnimg.cn/768f4ace9b2b4c2d9335256095a521d6.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L1F1YW50dW1Zb3U=,size_16,color_FFFFFF,t_70)
## 多接口网桥一一以太网交换机
![在这里插入图片描述](https://img-blog.csdnimg.cn/8f18bc2ead4743969db8f64d7b16319d.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L1F1YW50dW1Zb3U=,size_16,color_FFFFFF,t_70)
### 以太网交换机的两种交换方式
![在这里插入图片描述](https://img-blog.csdnimg.cn/fe6bba6d21a24a008e72dc8245eb1a3b.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L1F1YW50dW1Zb3U=,size_16,color_FFFFFF,t_70)
## 冲突域与广播域
![在这里插入图片描述](https://img-blog.csdnimg.cn/daa4426d3e9240bbb92cff2bfffd4f30.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L1F1YW50dW1Zb3U=,size_16,color_FFFFFF,t_70)
![在这里插入图片描述](https://img-blog.csdnimg.cn/7cbd0fe4e1a34eb6be49ce01e9b5b8bf.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L1F1YW50dW1Zb3U=,size_16,color_FFFFFF,t_70)
## 小结思维导图
![在这里插入图片描述](https://img-blog.csdnimg.cn/47ad9b9bbec440ff892d70a7e6c06170.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L1F1YW50dW1Zb3U=,size_16,color_FFFFFF,t_70)
# 本章总结思维导图
![在这里插入图片描述](https://img-blog.csdnimg.cn/8df8df3adb8041288bc7c0f58a2ff7d8.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L1F1YW50dW1Zb3U=,size_16,color_FFFFFF,t_70)

