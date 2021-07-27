> 按照自己的节奏，竭尽全力（剩下的都留给命运）
你一定要做自己，做自己喜欢的事，然后把自己交给命运
加油！当自己的实力不能满足自己的目标时，**就静下心去学习！，不要乱想与顾虑**
一年后考研择校、现在开冲，静下心，积攒实力，厚积薄发，反正保底NCU
只要心甘情愿，二三战都不是事

@[toc]
# CSMA / CD 协议 （重点）
- 载波监听多点接入/碰撞检测 CSMA/CD( carrier sense multiple access with collision detection)

**CS**：载波侦听/监听，每一个站在==发送数据之前==以及==发送数据时==都要检测一下总线上是否有其他计算机在发送数据。
**MA**：多点接入，表示许多计算机以多点接入的方式连接在一根总线上。*总线型网络*
**CD**：碰撞检测（冲突检测），“边发送边监听”，适配器边发送数据边检测信道上信号电压的变化情况，以便判断自己在发送数据时其他站是否也在发送数据。 *半双工网络*


==导致先听后发还会引起冲突的原因==：因为电磁波在总线上总是以有限的速率传播
## 传播时延对载波监听的影响

![在这里插入图片描述](https://img-blog.csdnimg.cn/9baca283faa14c67b6ef03951c091a45.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L1F1YW50dW1Zb3U=,size_16,color_FFFFFF,t_70)
- 只要经过 `2τ` 时间还没有检测到碰撞，就能肯定这次发送不会发生碰撞。

## 如何确定碰撞后的重传时机？
截断二进制指数规避算法

![在这里插入图片描述](https://img-blog.csdnimg.cn/c0fcb67e38fc4e468075b6a79f6cb74d.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L1F1YW50dW1Zb3U=,size_16,color_FFFFFF,t_70)
## 最小帧长问题
![在这里插入图片描述](https://img-blog.csdnimg.cn/b5d133dd6fa64b35ba9148ef200003a8.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L1F1YW50dW1Zb3U=,size_16,color_FFFFFF,t_70)

- 以太网规定最短帧长为64B,凡是长度小于64B的都是由于冲突而异常终止的无效帧。

## 小结思维导图
![在这里插入图片描述](https://img-blog.csdnimg.cn/973573e63f5c4b35987bed3a9d0ed9b7.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L1F1YW50dW1Zb3U=,size_16,color_FFFFFF,t_70)
# CSMA / CA协议 （了解）
- 载波监听多点接入/碰撞避免 CSMA/CA( carrier sense multiple access with collision avoidance)

![在这里插入图片描述](https://img-blog.csdnimg.cn/cc1d58fd58644341b9e2d3cca038c8e9.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L1F1YW50dW1Zb3U=,size_16,color_FFFFFF,t_70)
## CSMA/CA协议工作原理

 1. 发送数据前，先检测信道是否空闲
 2. 空闲则发出**RTS**（ request to send），RTS包括发射端的地址、接收端的地址、下一份数据将持续发送的时间等信息；信道忙则等待
 3. 接收端收到RTS后，将响应**CTS**（ clear to send）.
 4. 发送端收到CTS后，开始发送数据帧（同时==预约信道==：发送方告知其他站点自己要传多久数据）.
 5. 接收端收到数据帧后，将用CRC来检验数据是否正确，正确则响应**ACK帧**
 6. 发送方收到ACK就可以进行下一个数据帧的发送，若没有则一直重传至规定重发次数为止（采用==二进制指数退避算法==来确定随机的推迟时间）.

## CSMA/CD 与  CSMA/CA 异同
**相同点：**
- CSMA/CD与 CSMA/CA机制都从属于CSMA的思路，其核心是==先听再说==。换言之，两个在接入信道之前都须要进行监听。当发现信道空闲后，才能进行接入。

**不同点：**
- 传输介质不同： CSMA/CD用于总线式以太网【有线】，而 CSMA/CA用于无线局域网【无线】.
- 载波检测方式不同：因传输介质不同， CSMA/CD与 CSMA/CA的检测方式也不同。 CSMA/CD通过电缆中电压
的变化来检测，当数据发生碰撞时，电缆中的电压就会随着发生变化；而 CSMA/CA采用能量检测（ED）载波检测（CS）和能量载波混合检测三种检测信道空闲的方式。
- CSMA/CD检测冲突， CSMA/CA避免冲突，二者出现冲突后都会进行有上限的重传。


# 轮询访问介质访问控制
##  介质访问控制
<font color=red size=4>**信道划分介质访问控制( MAC Multiple  Access Control)协议**</font>
- 基于多路复用技术划分资源。
- 网络负载重：共享信道效率高，且公平
- 网络负载轻：共享信道效率低

<font color=red size=4>**随机访问MAC协议：**</font>
- 用户根据意愿随机发送信息，发送信息时可独占信道带宽。
- 网络负载重：产生冲突开销
- 网络负载轻：共享信道效率高，单个结点可利用信道全部带宽

<font color=red size=4>**轮询访问MAC协议/轮流协议/轮转访问MAC协议**</font>
- 既要不产生冲突，又要发送时占全部带宽。

- 轮询协议、**令牌传递协议**

## 轮询协议
![在这里插入图片描述](https://img-blog.csdnimg.cn/eb0f43ec193746c0a0c99f3ecbd99599.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L1F1YW50dW1Zb3U=,size_16,color_FFFFFF,t_70)
## 令牌传递协议(重要)

![在这里插入图片描述](https://img-blog.csdnimg.cn/dbcd2561d95243a193bab3718bda798f.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L1F1YW50dW1Zb3U=,size_16,color_FFFFFF,t_70)
## MAC 协议总结
![在这里插入图片描述](https://img-blog.csdnimg.cn/f970c2bc405e4f12bcb8ccb247206ef4.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L1F1YW50dW1Zb3U=,size_16,color_FFFFFF,t_70)

