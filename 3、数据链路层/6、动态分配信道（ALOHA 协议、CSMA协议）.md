> 按照自己的节奏，竭尽全力（剩下的都留给命运）
你一定要做自己，做自己喜欢的事，然后把自己交给命运
加油！当自己的实力不能满足自己的目标时，**就静下心去学习！**

@[toc]
![在这里插入图片描述](https://img-blog.csdnimg.cn/d960ff88336344548c98e9cdc78a194a.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L1F1YW50dW1Zb3U=,size_16,color_FFFFFF,t_70)
# ALOHA 协议
## 纯 ALOHA协议
- **纯 ALOHA协议思想**：不监听信道，不按时间槽发送，随机重发。想发就发

**冲突如何检测？**
如果发生冲突，接收方在就会检测出差错 ，然后不予确认，发送方在一定时间内收不到就判断发生冲突。
**冲突如何解决？**
超时后等一随机时间再重传。

![在这里插入图片描述](https://img-blog.csdnimg.cn/5b193b5435654982adb784a6f8b52f27.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L1F1YW50dW1Zb3U=,size_16,color_FFFFFF,t_70)
## 时隙 ALOHA协议
- **时隙 ALOHA协议的思想**：把时间分成若干个相同的时间片，所有用户在时间片开始时刻同步接入网络信道，若发生冲突，则必须等到下一个时间片开始时刻再发送。     *控制想发就发的随意性*

![在这里插入图片描述](https://img-blog.csdnimg.cn/f992e695df134b25998c0a348d334de3.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L1F1YW50dW1Zb3U=,size_16,color_FFFFFF,t_70)

## ALOHA 协议小结
- 1、纯 ALOHA比时隙 ALOHA吞吐量更低，效率更低。
- 2、纯 ALOHA想发就发，时隙 ALOHA只有在时间片段开始时才能发。

# CSMA 协议
<font color=red>**载波监听多路访问协议CSMA( carrier sense multiple access)**</font>
- CS:载波侦听/监听，每一个站在发送数据之前要检测一下总线上是否有其他计算机在发送数据。当几个站同时在总线上发送数据时，总线上的信号**电压摆动值将会增大**（互相叠加）。当一个站检测到的信号电压摆动值超过一定门限值时，就认为总线上至少有两个站同时在发送数据，表明产生了碰撞，即发生了冲突

- **MA** : 多点接入，表示许多计算机以多点接入的方式连接在一根总线上。

**协议思想**：发送帧之前，==监听信道==。


![在这里插入图片描述](https://img-blog.csdnimg.cn/ae5228e098244ca3ba834a2ecd5cd0ec.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L1F1YW50dW1Zb3U=,size_16,color_FFFFFF,t_70)

## 1-坚持CSMA
坚持指的是对于监听信道忙之后的坚持。
**1-坚持CSMA思想**：如果一个主机要发送消息，那么它先监听信道。 空闲则直接传输，不必等待。忙则一直监听，直到空闲马上传输。如果有冲突（一段时间内未收到肯定回复），则等待一个随机长的时间再监听，重复上述过程
- **优点**：只要媒体空闲，站点就马上发送，避免了媒体利用率的损失。
- **缺点**：假如有两个或两个以上的站点有数据要发送，冲突就不可避免。

## 非坚持CSMA
- 非坚持指的是对于监听信道忙之后就不继续监听。
**非坚持CSMA思想**：如果一个主机要发送消息，那么它先监听信道。 <font color=skyblue>空闲则直接传输，不必等待。</font><font color=red>忙则等待一个随机的时间之后再进行监听。</font>
- **优点**：采用随机的重发延迟时间可以减少冲突发生的可能性。
- **缺点**：可能存在大家都在延迟等待过程中，使得媒体仍可能处于空闲状态，媒体使用率降低。


## p-坚持CSMA
p-坚持指的是对于监听信道**空闲**的处理。
 **p坚持CSMA思想**：如果一个主机要发送消息，那么它先监听信道。
 1. 空闲则以p概率直接传输，不必等待；概率1-p等待到下一个时间槽再传输。
 2. 忙则持续监听直到信道空闲再以p概率发送。
 3. 若冲突则等到下一个时间槽开始再监听并重复上述过程。

**优点**：既能像非坚持算法那样减少冲突，又能像1-坚持算法那样减少媒体空闲时间的这种方案。
但是，发生冲突后还是要坚持把数据帧发送完，造成了浪费。


## 三种CSMA 对比
![在这里插入图片描述](https://img-blog.csdnimg.cn/a3ab0a7c86d949fba23f7ca076973aa3.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L1F1YW50dW1Zb3U=,size_16,color_FFFFFF,t_70)

