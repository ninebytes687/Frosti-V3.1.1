---
title: "Typecho主题开启评论邮件提醒"
description: "不再错过评论"
pubDate: "Oct 16 2024"
image: "https://s1.imagehub.cc/images/2024/11/27/0909cc9c175104329692d0c0f66034ea.png"
categories:
  - tech
tags:
  - Typecho
---
# 前言
1. Typecho版本为`1.2.0`及以上；  
2. PHP版本>=`7.2.0`；  
3. 若启用SMTP加密需开启PHP Openssl扩展；  

# 1. 安装插件
我用的是`CommentNotifier`插件，搭配网易企业邮箱服务，需要你自己去注册网易企业邮箱账号、绑定你的域名，然后新建用户，自行bing。  
Github项目链接：[https://github.com/jrotty/CommentNotifier](https://github.com/jrotty/CommentNotifier)。  
下载慢的话自己去bing Github文件加速，记得给项目作者点颗Star~。  
下载解压后，将文件夹重命名为`CommentNotifier`。复制到网站目录`/usr/plugins`下。然后进入你的网站后台，启用插件即可。

# 2. 配置插件
去[这里](https://qiye.163.com/help/client-profile.html)查询你绑定的网易企业邮箱对应的POP3、SMTP、IMAP等地址。  
![8 1](https://s1.imagehub.cc/images/2024/12/16/edf223d9874eb393995e0d7043d929c4.png)
然后去设置CommentNotifier插件
1. `邮件推送方式`：选择`SMTP`；  
2. `SMTP服务器地址`：填写刚刚你查询到的SMTP地址；  
3. `SMTP登录用户`和`SMTP邮箱地址`：均填写你的邮箱地址；  
4. `SMTP登录密码`：填写你在网易企邮新建用户时填写的登录密码；~~（不要来问我，我也不知道）~~  
5. `SMTP加密模式`：选择无安全模式或SSL加密均可，注意两种模式的端口不一样；  
6. `SMTP服务端口`：默认`25`；SSL为`465`；TLS为`587`；  
7. `发件人昵称`：自己取；  
8. `站长收件邮箱`：写自己的邮箱；  

这是我的设置：
![8 2](https://s1.imagehub.cc/images/2024/12/16/2a9f32ae10705a6e3e60e73d59de7eaf.png)
# 3. 邮件测试
在CommentNotifier插件设置底部，可以点击这里测试是否配置成功（仅适用于SMTP模式）。
![8 3](https://s1.imagehub.cc/images/2024/12/16/9b55a447cbd4cb045a800789787e56f0.png)
若你填写的配置无误的话，一封以`标题`为主题的邮件就会发送到在你刚刚填写的`站长收件邮箱`内填写的邮箱内。
![8 4](https://s1.imagehub.cc/images/2024/12/16/74a85e802bb913eb242db33c85edd136.png)
当然也可以模仿访客自己去自己文章评论区写点内容测试一下，填写均正确的话，评论邮件提醒就会发送到在你刚刚填写的`站长收件邮箱`内填写的邮箱地址里。
![8 5](https://s1.imagehub.cc/images/2024/12/16/5d36d3a6e6005eca99ddc6acdc5a3f20.jpg)
然后去后台-管理评论中，回复这个评论，测试一下发件功能。
![8 6](https://s1.imagehub.cc/images/2024/12/16/fd2385168061f8bce084fe489c018722.png)
配置无误的话，你将在评论时填写的邮箱地址内收到一封以`新回复`为主题的邮件。
![8 7](https://s1.imagehub.cc/images/2024/12/16/2ff74efe3bba8e6ab7579cf7e7d09397.png)
- Tips：还可以去`后台-控制台-评论邮件提醒外观`中更改发送的邮件的外观

