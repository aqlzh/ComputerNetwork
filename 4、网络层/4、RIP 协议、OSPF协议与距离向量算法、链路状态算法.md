> - 我希望你没有刻意为追求一个数字而生活，我希望你找到了真正的价值所在
> - 你一定要**坚持做自己**，**静下心**来做自己**喜欢**的事，然后把自己交给**命运**

@[toc]
# 路由选择协议分类回顾
![在这里插入图片描述](https://img-blog.csdnimg.cn/312014b9f73b41959c5b09d0d9c1129a.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L1F1YW50dW1Zb3U=,size_16,color_FFFFFF,t_70)
# RIP协议 
- Routing Information Protocol,路由信息协议
- RIP是一种分布式的基于==距离向量==的路由选择协议，是因特网的协议标准，最大优点是**简单**。
- RIP协议要求网络中每一个路由器都维护**从它自己到其他每一个目的网络的唯一最佳距离记录**（即一组距离）.
- **距离**：通常为“跳数”，即从源端口到目的端口所经过的路由器个数，经过一个路由器跳数+1.特别的，从一路由器到直接连接的网络距离为1.RIP允许一条路由最多只能包含15个路由器，因此==距离为16表示网络不可达==。

因此：RIP 协议只适用于**小互联网**

##  RIP协议注意事项
<font color=red >**RIP协议和谁交换？多久交换一次？交换什么？**</font>

![在这里插入图片描述](https://img-blog.csdnimg.cn/3295f2a6cc47436e83ec451c5f561d0d.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L1F1YW50dW1Zb3U=,size_16,color_FFFFFF,t_70)
## RIP协议的报文格式(了解)
![在这里插入图片描述](https://img-blog.csdnimg.cn/7c437f1a86d948a4878a7d3576078241.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L1F1YW50dW1Zb3U=,size_16,color_FFFFFF,t_70)
## RIP 协议特点
- RIP协议好消息传得快，坏消息传得慢
![在这里插入图片描述](https://img-blog.csdnimg.cn/db0781fc11bb4f6fbbdbdf4edb055e27.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L1F1YW50dW1Zb3U=,size_16,color_FFFFFF,t_70)
![在这里插入图片描述](https://img-blog.csdnimg.cn/43a7add0b7fe465d82bc4aa52be55763.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L1F1YW50dW1Zb3U=,size_16,color_FFFFFF,t_70)


# 距离向量算法
![在这里插入图片描述](https://img-blog.csdnimg.cn/a94e88804b564971bbde141f43da70b3.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L1F1YW50dW1Zb3U=,size_16,color_FFFFFF,t_70)

## 距离向量法练习1
![在这里插入图片描述](https://img-blog.csdnimg.cn/62c41c6f09154497b4212a2ee85a3e84.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L1F1YW50dW1Zb3U=,size_16,color_FFFFFF,t_70)
## 距离向量法练习2
![在这里插入图片描述](https://img-blog.csdnimg.cn/a8ae9a2e31b34cd1a558ab1fe463a700.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L1F1YW50dW1Zb3U=,size_16,color_FFFFFF,t_70)
# 总结思维导图
![在这里插入图片描述](https://img-blog.csdnimg.cn/0e9b66b57c5845be9d6c353011c8eb25.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L1F1YW50dW1Zb3U=,size_16,color_FFFFFF,t_70)
# OSPF协议与链路状态算法
## OSPF协议
- **开放最短路径优先OSPF协议**：“开放”标明OSPF协议不是受某一家厂商控制，而是==公开发表==的；“最短路径优先”是因为使用了Dijkstra提出的最短路径算法SPF.
- OSPF最主要的特征就是使用分布式的**链路状态协议**。

<font color=red>**OSPF的特点**</font>

**和谁交换**？
1、使用==洪泛法==向自治系统内**所有路由器**发送信息，即路由器通过输出端口向所有相邻的路由器发送信息，而每一个相邻路由器又再次将此信息发往其所有的相邻路由器。类似于==广播==
最终整个区域内所有路由器都得到了这个信息的一个副本。
**交换什么**？
2、发送的信息就是与本路由器相**邻的所有路由器的链路状态**（本路由器和哪些路由器相邻，以及该链路的度量代价一一费用、距离、时延、带宽等）
多久交换？
3、只有当**链路状态发生变化**（而不是前者的相隔几秒）时，路由器才向所有路由器洪泛发送此信息。
最后，所有路由器都能建立一个**链路状态数据库**，即**全网拓扑图。**

## 链路状态路由算法

 1. 每个路由器发现它的==邻居结点==[HELO问候分组]，并了解邻居节点的网络地址。
 2. 设置到它的每个邻居的成本度量 `metric`.
 3. 构造[DD数据库描述分组]，向邻站给出自己的链路状态数据库中的==所有链路状态项目的摘要信息==
 4. 如果DD分组中的摘要自己都有，则邻站不做处理：如果有没有的或者是更新的，则发送[`LSR链路状态请求分组]` 请求自己没有的和比自己更新的信息。
 5. 收到邻站的LSR分组后，发送[`LSU链路状态更新分组`]进行更新
 6. 更新完毕后，邻站返回一个[ `LSACK链路状态确认分组`]进行确认。只要一个路由器的链路状态发生变化：
 7. 泛洪发送[`LSU链路状态更新分组`]进行更新。
 8. 更新完毕后，其他站返回一个[ `LSACK链路状态确认分组`]进行确认
 9. 使用 Dijkstra/根据自己的链路状态数据库构造到其他节点间的最短路径。

## OSPF  区域
- 为了使OSPF能够用于规模很大的网络，OSPF将一个自治系统再划分为若干个更小的范围，叫做区域。每一个区域都有一个32位的区域标识符（用点分十进制表示）。区域也不能太大，在一个区域内的路由器最好不超过200个。


![在这里插入图片描述](https://img-blog.csdnimg.cn/0eca5508b56141dfa533655e90851cf3.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L1F1YW50dW1Zb3U=,size_16,color_FFFFFF,t_70)

## OSPF 分组
考纲上定义为 ： 网络层的协议

![在这里插入图片描述](https://img-blog.csdnimg.cn/bd2a92d78de74f5fa8df2652fac7afb3.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L1F1YW50dW1Zb3U=,size_16,color_FFFFFF,t_70)
## OSPF 的其他特点
- 1、每隔30min,要刷新一次数据库中的链路状态。
- 2、由于一个路由器的链路状态只涉及到与相邻路由器的连通状态，因而与整个互联网的规模并无直接关系。因
此当互联网规模很大时，OSPF协议要比距离向量协议RIP好得多。
- 3、OSPF不存在坏消息，传的慢的问题，它的收敛速度很快。
