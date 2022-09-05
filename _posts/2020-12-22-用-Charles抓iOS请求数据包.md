# 用Charles抓iOS请求数据包
### 1. Charles安装
官网下载安装Charles:
[https://www.charlesproxy.com/download](https://www.charlesproxy.com/download/)

### 2. HTTP抓包
##### （1）查看电脑IP地址
![](https://cdn7a.y523.com/images/blog/images/charles1.png)

![](https://cdn7a.y523.com/images/blog/images/charles2.png)

##### （2）设置手机HTTP代理
手机连上电脑，点击“设置->无线局域网->连接的WiFi”，设置HTTP代理：
服务器为电脑IP地址：如192.168.50.150
端口：8888
![](https://cdn7a.y523.com/images/blog/images/charles3.png)

设置代理后，需要在电脑上打开Charles才能上网

##### （3）电脑上打开Charles进行HTTP抓包
手机上打开某个App或者浏览器什么的，如果不能上网，检查前面步骤是否正确

![](https://cdn7a.y523.com/images/blog/images/charles4.png)

点击“Allow”允许，出现手机的HTTP请求列表
![](https://cdn7a.y523.com/images/blog/images/charles5.png)

### 3. HTTPS抓包

待续......
