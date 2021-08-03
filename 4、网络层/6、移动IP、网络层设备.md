> 择校时不要高估自己学习时不要低估自己

@[toc]
# 移动IP 
## 移动IP相关术语
- 移动P技术是移动结点(计算机/服务器等)以**固定的网络IP地址**，实现跨越不同网段的==漫游==功能，并保证了基于网络P的网络权限在漫游过程中不发生任何改变

- <font color=red>**移动结点**</font> : 具有永久IP地址的移动设备
- <font color=red>**归属代理**（本地代理）</font> :一个移动结点拥有的就“居所”称为==归属网络==，在归属网络中代表移动节点执行。移动管理功能的实体叫做归属代理。
- <font color=red>**外部代理**</font>（外地代理）在==外部网络==中帮助移动节点完成移动管理功能的实体称为外部代理。
- <font color=red>**永久地址**</font>(归属地址/主地址)移动站点在归属网络中的原始地址。
- <font color=red>**转交地址**</font>（辅地址）移动站点在外部网络使用的临时地址。


## 移动IP通信过程

![在这里插入图片描述](https://img-blog.csdnimg.cn/5690a9100ec14344b2b1dfbd95e824af.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L1F1YW50dW1Zb3U=,size_16,color_FFFFFF,t_70)
![在这里插入图片描述](https://img-blog.csdnimg.cn/201aa917e20a4c3787e6b13a46be1578.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L1F1YW50dW1Zb3U=,size_16,color_FFFFFF,t_70)
 
#  网络层设备
## 路由器
- 路由器是一种具有多个输入端口和多个输出端口的专用计算机，其任务是转发分组。


- 转发是在路由器内部进行
![在这里插入图片描述](https://img-blog.csdnimg.cn/fbf79ddcb1ea425f9af34b40a92d5d00.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L1F1YW50dW1Zb3U=,size_16,color_FFFFFF,t_70)

## 对线路上收到的分组的处理
<font color=red>**输入端口**</font>
![在这里插入图片描述](https://img-blog.csdnimg.cn/2c654cdac66546f9bd72af58765b6e77.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L1F1YW50dW1Zb3U=,size_16,color_FFFFFF,t_70)

<font color=red>**输出端口**</font>
![在这里插入图片描述](https://img-blog.csdnimg.cn/8b9ec394af5e403f858d05fd68668dda.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L1F1YW50dW1Zb3U=,size_16,color_FFFFFF,t_70)
## 三层设备的区别

![在这里插入图片描述](https://img-blog.csdnimg.cn/f1f0fe1c85cb4b638527d3cffb5683d4.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L1F1YW50dW1Zb3U=,size_16,color_FFFFFF,t_70)

## 路由表与转发表
![](https://img-blog.csdnimg.cn/7b7417bff24041268936ddef624e7454.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L1F1YW50dW1Zb3U=,size_16,color_FFFFFF,t_70)

## 本章总结思维导图
![在这里插入图片描述](https://img-blog.csdnimg.cn/d2bac16183b046a7ad128a2baaaf1fab.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L1F1YW50dW1Zb3U=,size_16,color_FFFFFF,t_70)
![在这里插入图片描述](https://img-blog.csdnimg.cn/b5ddc58a603d48229082b584afe517d0.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L1F1YW50dW1Zb3U=,size_16,color_FFFFFF,t_70)
![在这里插入图片描述](https://img-blog.csdnimg.cn/7631be1935c6418f8be99dc7175d5bf3.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L1F1YW50dW1Zb3U=,size_16,color_FFFFFF,t_70)

![在这里插入图片描述](https://img-blog.csdnimg.cn/a18cca2484114309a98b97f21e10b57f.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L1F1YW50dW1Zb3U=,size_16,color_FFFFFF,t_70)

![在这里插入图片描述](https://img-blog.csdnimg.cn/f8746113bc664fdda714d346a27c6e10.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L1F1YW50dW1Zb3U=,size_16,color_FFFFFF,t_70)
![在这里插入图片描述](https://img-blog.csdnimg.cn/4587cb8b2f8b40229be08b1f5e56befe.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L1F1YW50dW1Zb3U=,size_16,color_FFFFFF,t_70)

