@[toc]
# 网络地址转换NAT
- 路由器对目的地址是私有P地址的数据报一律不进行转发。

- 端口号可以唯一标识主机中某一进程

![在这里插入图片描述](https://img-blog.csdnimg.cn/4ed5233cc76f4b1a94be68924040a898.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L1F1YW50dW1Zb3U=,size_16,color_FFFFFF,t_70)
- 网络地址转换**NAT**（ Network Address Translation）：在==专用网==连接到==因特网==的路由器上安装NAT软件，安装了NAT软件的路由器叫**NAT路由器**，它至少有一个有效的**外部全球IP地址。**

# 子网划分
**分类的IP地址存在的缺点**
1、IP地址空间的利用率有时很低
2、两级IP地址不够灵活。

划分思想如下图

![在这里插入图片描述](https://img-blog.csdnimg.cn/6f5201eeda1f4762b249b0971c3d580f.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L1F1YW50dW1Zb3U=,size_16,color_FFFFFF,t_70)


- 主机号最少要留下两位，因为一位的情况（全零与全一的情况是不允许的）（注意：子网是否能全零或全一要看情况）



# 子网掩码
外部世界发送的分组想传输至 145.13.3.10  该怎么办呢？ ——>  子网掩码
![在这里插入图片描述](https://img-blog.csdnimg.cn/922cbec76787435fb1409d263ace01a2.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L1F1YW50dW1Zb3U=,size_16,color_FFFFFF,t_70)

### 子网掩码推出
![在这里插入图片描述](https://img-blog.csdnimg.cn/6e43637d745047edb93bf0832d8accac.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L1F1YW50dW1Zb3U=,size_16,color_FFFFFF,t_70)

子网掩码与IP地址逐位相与，就得到子网各地址


### 子网掩码练习题
<font color=red>**练习题 1**</font>
![在这里插入图片描述](https://img-blog.csdnimg.cn/3276106db1934f63af729d0aca778fd4.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L1F1YW50dW1Zb3U=,size_16,color_FFFFFF,t_70)

下面的表格要熟悉 （各个二进制所对应的十进制）
![在这里插入图片描述](https://img-blog.csdnimg.cn/de54b546fbf448b3ae95babc28c96eb4.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L1F1YW50dW1Zb3U=,size_16,color_FFFFFF,t_70)
<font color=red>**练习题 2**</font>
![在这里插入图片描述](https://img-blog.csdnimg.cn/cbd67030d5ed4a52b22e220b44dee13e.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L1F1YW50dW1Zb3U=,size_16,color_FFFFFF,t_70)

> 计算套路总结 ：
> ①  广播分组 则最后一位全为 1 即为 255
> ② 255.255.252.60    ----> 8.8.6.0     个1 ，即为网络号8+8=16.子网号为  6，剩下的32-8-8-6=10  为主机号
> ③ 子网   77  --> 01001101  取前六位 后面根据广播全化为1  --->
> 01001111  --> 79 

### 使用子网时分组的转发
**路由器转发分组的算法：**

直接交付： 可以直接给此路由器连接的子网
间接交付：需要转发给其他路由器（路由器连接的网络不存在目的地址）

![在这里插入图片描述](https://img-blog.csdnimg.cn/30649e81dda04ca9a0b9531cd11aae9d.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L1F1YW50dW1Zb3U=,size_16,color_FFFFFF,t_70)
# 无分类编址CIDR
- 产生背景 ：B类地址很快将分配完毕！  路由表中的项目急剧增长！

![在这里插入图片描述](https://img-blog.csdnimg.cn/9fea7e714bb343d9a895d86bf6e85747.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L1F1YW50dW1Zb3U=,size_16,color_FFFFFF,t_70)
## 无分类编址CIDR解释
- 网络前缀
![在这里插入图片描述](https://img-blog.csdnimg.cn/c64bbcce160d450f9a39628d0579ef59.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L1F1YW50dW1Zb3U=,size_16,color_FFFFFF,t_70)
## 无分类编址CIDR练习

```bash
192.199.170.82/27
```
- 问题一：有多少主机    32-27=5   --> 2^5^
- 问题二 ： 最大地址与最小地址    82--> 010 10010  最大让后5位全1，最小让后5位全0
- 问题三：该子网掩码为 只要让后面5位全0，其余全1


## 构成超网
- 将多个子网聚合成一个较大的子网，叫做构成超网，或路由聚合。
- 方法：将网络前缀缩短（所有网络地址取交集）。

划分子网是少→多   ； 构成超网是多→少  的过程

![在这里插入图片描述](https://img-blog.csdnimg.cn/bf3b006dc1d94e49a6270fe5288c2fc6.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L1F1YW50dW1Zb3U=,size_16,color_FFFFFF,t_70)

**例题：**
![在这里插入图片描述](https://img-blog.csdnimg.cn/cd841b8e323f4b37a770fa7bf1b46f49.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L1F1YW50dW1Zb3U=,size_16,color_FFFFFF,t_70)
## 最长前缀匹配
- 使用CIDR时，査找路由表可能得到几个匹配结果（跟网络掩码按位相与），应选择具有**最长网络前缀**的路由。前缀越长，地址块越小，路由越具体。

**例子1：**
![在这里插入图片描述](https://img-blog.csdnimg.cn/420902ab9bf84480a29dc8b2555300c3.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L1F1YW50dW1Zb3U=,size_16,color_FFFFFF,t_70)
**例子2**

![在这里插入图片描述](https://img-blog.csdnimg.cn/87881e67f16b4d4db5f514b833b7e2f1.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L1F1YW50dW1Zb3U=,size_16,color_FFFFFF,t_70)
/8  前8位全1，后面全为0
/11 前11位全1，后面全位0
