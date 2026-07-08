---
title: "CloudFlare Workers反向代理GitHub文件加速部署"
description: "CloudFlare恩情一辈子还不完"
pubDate: "Jul 08 2026"
image: "/cover/CloudFlare Workers反向代理GitHub文件加速部署.jpg"
categories:
  - tech
tags:
  - GitHub
  - 反向代理
---
首先打开你的CloudFlare Workers，然后点击`创建应用程序`，点击`从"Hello World!开始"`。
![1](https://blog.ninebytes.top/article/20260708/1.png)
然后点击`部署`。
![2](https://blog.ninebytes.top/article/20260708/2.png)
workers创建好后点击`编辑代码`。
![3](https://blog.ninebytes.top/article/20260708/3.png)
然后打开我的[GitHub仓库](https://github.com/ninebytes687/GitHub-Proxy)，复制worker.js代码并替换掉你新建的workers。  
绑定一个你自定义的二级域名。
![4](https://blog.ninebytes.top/article/20260708/4.png)
然后点击`设置`，在`变量和密钥`栏中点击`添加`。
![5](https://blog.ninebytes.top/article/20260708/5.png)
添加一个`密钥`类型，变量名称为`MY_TOTP_SECRET`的变量，值为你自定义的密码。 
![6](https://blog.ninebytes.top/article/20260708/6.png)
至此独属于你的GitHub文件加速代理站就部署好了。
