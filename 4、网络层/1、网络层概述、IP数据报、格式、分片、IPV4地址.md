> 夫人之相与，俯仰一世，或取诸怀抱，悟言一室之内；或因寄所托，放浪形骸之外   --------《兰亭集序》——东晋·王羲之

@[toc]
## 本章总思维导图
![在这里插入图片描述](https://img-blog.csdnimg.cn/45480a4785f240f18ee69f5156d1e0af.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L1F1YW50dW1Zb3U=,size_16,color_FFFFFF,t_70)
# 网络层概述
 - 主要任务是把==分组==从源端传到目的端，为分组交换网上的不同主机提供通信服务。网络层传输单位是==数据报==。

 1. 功能一：路由选择与分组转发最佳路径
 2. 功能二：异构网络互联
 3. 功能三：拥塞控制

若所有结点都来不及接受分组，而要丢弃大量分组的话，网络就处于拥塞状态。因此要采取一定措施，缓解这种拥塞。
WAY1：开环控制  静
WAY2；闭环控制  动



## TCP/IP  数据栈
![在这里插入图片描述](https://img-blog.csdnimg.cn/ddf0c146b5024af3b50bd6b786df2965.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L1F1YW50dW1Zb3U=,size_16,color_FFFFFF,t_70)
# IP数据报格式
![在这里插入图片描述](https://img-blog.csdnimg.cn/3fad1d2541fc437885dafeb393c5e212.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L1F1YW50dW1Zb3U=,size_16,color_FFFFFF,t_70)
可变部分可有可无，大部分情况下这部分没有

**首部部分详解：**
![在这里插入图片描述](https://img-blog.csdnimg.cn/118e0d6408054724be4ef05962349093.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L1F1YW50dW1Zb3U=,size_16,color_FFFFFF,t_70)
- **版本** ： IPV4 / IPV6
- **首部长度** ： 单位是四字节，原本按定 0000 ~ 1111 ，由于固定长度为 20 B ,所以最小开始为 0101    （5x4=20）
- **区分服务**：指示期望获得哪种类型的服务。(优先级)
- **总长度**：首部+数据，单位是1B.
- **生存时间**（TTL  -Time to Life）：IP分组的保质期。经过一个路由器-1，变成0则丢弃。
- **协议**：数据部分的协议。  （记忆 TCP 6 , UDP 17）
- **首部检验和**：只检验首部。 (以求和的方式，不检验数据部分)
- **源IP地址和目的IP地址**：32位。
- **可选字段**：0~40B,用来支持排错 ，测量以及安全等措施。
- **填充**：，全0,把首部补成4B的整数倍。

![在这里插入图片描述](https://img-blog.csdnimg.cn/65fc44e49d324750b2c1b9856d0bf33c.png)

> **Tips:**
>   TCP 面向连接的服务 （非常六）
>  UDP  容易被遗弃  （17）


# IP数据报分片
## 最大传送单元MTU
- 链路层数据帧可封装数据的上限。以太网的MTU是1500字节。

![在这里插入图片描述](https://img-blog.csdnimg.cn/0a61fbe73c33489ab1355da0b02d6664.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L1F1YW50dW1Zb3U=,size_16,color_FFFFFF,t_70)
- 如果所传送的数据报长度超过某链路的MTU值？  `进行分片`

![在这里插入图片描述](https://img-blog.csdnimg.cn/1b1c0576755e45b885c340d4b4703c49.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L1F1YW50dW1Zb3U=,size_16,color_FFFFFF,t_70)

## IP  数据报分片过程
![在这里插入图片描述](https://img-blog.csdnimg.cn/8add06350e444a0a85418e3fd9878c09.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L1F1YW50dW1Zb3U=,size_16,color_FFFFFF,t_70)

- 标识用于确定是否属于同一家族
- DF  : 是否允许分片
- MF : 后面是否还有分片



**总**长度单位是1B
**片**偏移单位是8B
**首**部长度单位是48

> Tips :    一种八片首饰
> ![在这里插入图片描述](https://img-blog.csdnimg.cn/c833744dd86f4c20a9f5f29aa6c6796d.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L1F1YW50dW1Zb3U=,size_16,color_FFFFFF,t_70)

# IPV4地址
## IP 地址
**IP  编址的历史阶段** ： `分类的IP地址`  --> `子网的划分`  -- > `构成超网（无分类编址方法）`

### 分类的IP 地址
![在这里插入图片描述](https://img-blog.csdnimg.cn/eced7ed4402745829020b994843107da.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L1F1YW50dW1Zb3U=,size_16,color_FFFFFF,t_70)
![在这里插入图片描述](https://img-blog.csdnimg.cn/bc7cdeebdd0148e994945683cb5a62bb.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L1F1YW50dW1Zb3U=,size_16,color_FFFFFF,t_70)
- 上图中有六个实际网络（画阴影区域）

**分类的IP 地址正题**
![在这里插入图片描述](https://img-blog.csdnimg.cn/711751c204ae4692a5ec442d71f3d4f6.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L1F1YW50dW1Zb3U=,size_16,color_FFFFFF,t_70)


**特殊IP 地址**
![在这里插入图片描述](https://img-blog.csdnimg.cn/3a9b1b202fd64ce494c640c0b8af4332.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L1F1YW50dW1Zb3U=,size_16,color_FFFFFF,t_70)
**私有IP 地址**
![在这里插入图片描述](https://img-blog.csdnimg.cn/92c41a2611bc48029b8a0c754a856d58.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L1F1YW50dW1Zb3U=,size_16,color_FFFFFF,t_70)

---
![在这里插入图片描述](https://img-blog.csdnimg.cn/d3729cf384164f07aed60454321bfc23.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L1F1YW50dW1Zb3U=,size_16,color_FFFFFF,t_70)

网络类别  A
- 全零地址情况，和127地址（软件环回测试）   2^7^-2
- 全零地址（本地主机） 全1地址（广播地址） 2^24^-2

网络类别B
- 全零地址情况    2^14^-1
- 全零地址（本地主机） 全1地址（广播地址） 2^16^-2

网络类别C
- 全零地址情况    2^21^-1
- 全零地址（本地主机） 全1地址（广播地址） 2^8^-2

---

