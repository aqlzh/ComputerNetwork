@[toc]
# 电子邮件
## 电子邮件的信息格式
![在这里插入图片描述](https://img-blog.csdnimg.cn/8d1c6f0bd8ad41c7a0c1d7bb50e02778.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L1F1YW50dW1Zb3U=,size_16,color_FFFFFF,t_70)


## 组成结构
![在这里插入图片描述](https://img-blog.csdnimg.cn/c2d7f8ad409c4063bc972437a0c485d7.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L1F1YW50dW1Zb3U=,size_16,color_FFFFFF,t_70)
![在这里插入图片描述](https://img-blog.csdnimg.cn/734ef3e9e9b54cd28f55a1a603219b19.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L1F1YW50dW1Zb3U=,size_16,color_FFFFFF,t_70)

## 简单邮件传送协议SMTP
- SMTP规定了在两个相互通信的==SMTP进程==之间应如何交换信息。
- 负责发送邮件的SMTP进程就是==SMTP客户==，负责接收邮件的进程就是==SMTP服务器==。
- SMTP规定了14条命令（几个字母）和21种应答信息。(三位数字代码+简单文字说明)。

==注意==： TCP  连接端口号25  C/S


**SMTP通信的三个阶段** ： 连接建立 -->  邮件传送 --> 连接释放


![在这里插入图片描述](https://img-blog.csdnimg.cn/5ea19ddf7a1c43e59462982add318311.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L1F1YW50dW1Zb3U=,size_16,color_FFFFFF,t_70)
==注意==： 命令与数字代码不需要记忆


<font color=red size=4>**SMTP的缺点**</font>
- 1、SMTP不能传送可执行文件或者其他二进制对象
- 2、SMTP仅限于传送7位ASCI码，不能传送其他非英语国家的文字。
- 3、SMTP服务器会拒绝超过一定长度的邮件。

## MIME
![在这里插入图片描述](https://img-blog.csdnimg.cn/de1c2b7d49d24b529f9fac6a7afef77d.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L1F1YW50dW1Zb3U=,size_16,color_FFFFFF,t_70)
## 邮局协议  POP3
![在这里插入图片描述](https://img-blog.csdnimg.cn/855d6872ec164f13acda2e2daa212433.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L1F1YW50dW1Zb3U=,size_16,color_FFFFFF,t_70)
## 网际报文存取协议IMAP
- IMAP协议比POP协议复杂。当用户Pc上的MAP客户程序打开IMAP服务器的邮箱时，用户可以看到邮箱的首部，若用户需要打开某个邮件，该邮件才上传到用户的计算机上。
- IMAP可以让用户在不同的地方使用不同的计算机随时上网阅读处理邮件，还允许只读取邮件中的某一个部分(先看正文，有WiFi的时候再下载附件)。

## 基于万维网的电子邮件（现在常用）
直接在浏览器中使用

![在这里插入图片描述](https://img-blog.csdnimg.cn/c2affed053b64ef2853b0884522e137c.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L1F1YW50dW1Zb3U=,size_16,color_FFFFFF,t_70)
## 小结思维导图
![在这里插入图片描述](https://img-blog.csdnimg.cn/d25948ecdc68455e92dc05eebbf59782.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L1F1YW50dW1Zb3U=,size_16,color_FFFFFF,t_70)
# 万维网和HTTP协议
##  万维网概述
![在这里插入图片描述](https://img-blog.csdnimg.cn/93f850ec30624e47baf2cd8d2f8be631.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L1F1YW50dW1Zb3U=,size_16,color_FFFFFF,t_70)
## HTTP 超文本传输协议
- HTTP协议定义了浏览器（万维网客户进程）怎样向万维网服务器请求万维网文档，以及服务器怎样把文档传送给浏览器。


![在这里插入图片描述](https://img-blog.csdnimg.cn/9c1d1beadaa54c3998d82412d63a2fc5.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L1F1YW50dW1Zb3U=,size_16,color_FFFFFF,t_70)
## HTTP 的特点
- HTTP协议是无状态的
- 但是在实际工作中，一些万维网站点常常希望能够识别用户  --> Cookie
- Cookie是存储在用户主机中的文本文件，记录一段时间内某用户(使用识别码识别，如“123456”)的访问记录   --> 提供个性化服务
- HTTP采用TCP作为运输层协议，但==HTTP协议本身是无连接==的（通信双方在交换HTP报文之前不需要先建立HTP连接）。


![在这里插入图片描述](https://img-blog.csdnimg.cn/6e74d954d45541bc8f7aa677b5588dda.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L1F1YW50dW1Zb3U=,size_16,color_FFFFFF,t_70)

## HTTP 协议的连接方式

![在这里插入图片描述](https://img-blog.csdnimg.cn/264aa2277c5d4d3e8368ece623a16490.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L1F1YW50dW1Zb3U=,size_16,color_FFFFFF,t_70)
## 超文本传输协议HTP一报文结构
![在这里插入图片描述](https://img-blog.csdnimg.cn/3279443d0fc8412b88b1e150e6f212b5.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L1F1YW50dW1Zb3U=,size_16,color_FFFFFF,t_70)
![在这里插入图片描述](https://img-blog.csdnimg.cn/2b3242642273427a9a11a21f05dcb88b.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L1F1YW50dW1Zb3U=,size_16,color_FFFFFF,t_70)
## 本章总结思维导图
![在这里插入图片描述](https://img-blog.csdnimg.cn/423797c72ce24244b03738a257a1074f.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L1F1YW50dW1Zb3U=,size_16,color_FFFFFF,t_70)

