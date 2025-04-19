---
title: "ZeroSSL申请公网IP SSL证书及部署"
description: ""
pubDate: "Apr 19 2025"
image: "https://s21.ax1x.com/2025/04/19/pE4u4Z4.png"
categories:
  - tech
tags:
  - SSL
---

# 前言
我有一台国内的Debian12云服务器，我只拿它运行Alist。  
因为我的域名是在NameSilo购买的，无法直接进行域名备案，只能申请公网IP证书。  
ZeroSSL有免费的90D公网IP证书，本文章使用ZeroSSL进行公网IP证书的申请及部署。  
（~~其实我也懒得备案，流程太麻烦了~~）  

# 注册ZeroSSL
点击[这里](https://app.zerossl.com/signup)首先进行注册ZeroSSL，需要魔法环境。  

# 安装Nginx
更新软件包：sudo apt update && sudo apt upgrade  
安装Nginx：sudo apt install nginx -y  
安装完成后创建存放验证文件目录：sudo mkdir -p /var/www/html/.well-known/pki-validation/  
.well-known执行755：sudo chmod -R 755 /var/www/html/.well-known/  

# 开放安全组规则
去安全组规则中开放80端口，证书部署完成后再删除80端口规则即可。  

# 申请新证书
点击New Certificate申请新证书，在文本框内输入服务器公网IP地址，然后就一直Next Step即可。  
![1](https://s1.imagehub.cc/images/2025/04/19/32cbbd4ee066aa08ca59fa665c9ac9be.png)
来到验证界面，选择HTTP验证。然后点击Download Auth File下载验证文件，将验证文件上传至刚刚创建的目录内。  
![2](https://s1.imagehub.cc/images/2025/04/19/e769ee1fc7f7c8eeae46685f759299bf.png)

# 编写Nginx配置文件
编写zerossl.conf文件：sudo vim /etc/nginx/zerossl.conf  
```
server {
    listen 80;
    server_name 公网IP地址;    
    root /var/www/html;
    location /.well-known/pki-validation/ {
        allow all;
    }
}
```

然后重启Nginx：sudo systemctl restart nginx  
测试Nginx：sudo nginx -t  
```
ninebytes@hcss-ecs-fc21:~$ sudo nginx -t
nginx: the configuration file /etc/nginx/nginx.conf syntax is ok
nginx: configuration file /etc/nginx/nginx.conf test is successful
```

# 下载证书
操作没有问题的话，验证通过后，ZeroSSL会颁发证书。选择默认的Certificate即可。  
![3](https://s1.imagehub.cc/images/2025/04/19/b60362430118b76bdaadca0ba9a4d1af.png)

# 部署证书
查看公网IP.zip压缩包结构：  
我们需要的是服务器证书和私钥文件，即：certificate.crt和private.key。  
```
ninebytes@hcss-ecs-fc21:~$ unzip -l 公网IP.zip 
Archive:  1.94.228.53.zip
  Length      Date    Time    Name
---------  ---------- -----   ----
     2269  2025-04-19 04:24   certificate.crt
     2431  2025-04-19 04:24   ca_bundle.crt
     1702  2025-04-19 04:24   private.key
---------                     -------
     6402                     3 files
```

首先解压压缩包：unzip 公网IP.zip  
创建证书存放目录：sudo mkdir /opt/alist/date/certs/  
移动服务器证书和私钥文件到证书存放目录：sudo mv certificate.crt private.key /opt/alist/data/certs/  
开放读取权限：sudo chmod 644 /opt/alist/data/certs/*  

# 编写Alist配置文件
编写Alist配置文件：sudo vim /opt/alist/data/config.json  
注意要根据Alist实际安装目录来。  

```
  "scheme": {
    "address": "0.0.0.0",
    "http_port": -1, #关闭HTTP监听
    "https_port": 62772, #设置HTTPS监听端口
    "force_https": false, #关闭强制跳转HTTPS
    "cert_file": "/opt/alist/data/certs/certificate.crt", #服务器证书存放绝对路径
    "key_file": "/opt/alist/data/certs/private.key", #私钥文件存放绝对路径
    "unix_file": "",
    "unix_file_perm": ""
  },
```

重启Alist服务：sudo systemctl restart alist   

# 验证SSL
![4](https://s1.imagehub.cc/images/2025/04/19/7ab3decd10ff21e2497bcb70d6bce799.png)