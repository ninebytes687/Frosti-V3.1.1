---
title: "Rocky Linux 9.4 VMware安装教程"
description: "仅限amdx86_64CPU架构"
pubDate: "Nov 3 2024"
image: "https://s1.imagehub.cc/images/2024/11/27/77cdf7b34f0ad71469ce6d87454af479.jpeg"
categories:
  - tech
tags:
  - VMware
  - Rocky Linux
  - Linux
---
# 1. 下载镜像
首先下载Rocky Linux 9.4的镜像，可以去[Rocky Linux官网](https://rockylinux.org/zh-CN)或者阿里、网易等镜像站下载。  
注意架构不要选择错了。
![9 1](https://s1.imagehub.cc/images/2025/01/04/91e30eb1af2251869981c422befd1c9f.png)
# 2. 创建新的虚拟机
打开VMware Workstation Pro 17，创建新的虚拟机。  
类型选择`典型`。
![9 2](https://s1.imagehub.cc/images/2025/01/04/3e2b6d84ebf594fb1eca1a0061832abb.png)
选择`稍后安装操作系统`。
![9 3](https://s1.imagehub.cc/images/2025/01/04/4f359b9f29f481cdb486d124971f097f.png)
客户机操作系统选择`Linux`，版本选择`其他 Linux 5.x 内核 64位`。
![9 4](https://s1.imagehub.cc/images/2025/01/04/34c8e953ebe86b62cd57a568dbce28d6.png)
填写虚拟机名称及选择虚拟机安装位置。
![9 5](https://s1.imagehub.cc/images/2025/01/04/75b24a8cd93f08191f9efd7f2fd487aa.png)
最大磁盘大小建议`50G+`。
![9 6](https://s1.imagehub.cc/images/2025/01/04/6035a483ac3ad7f0266cef2093179ab0.png)
点击`自定义硬件`。
![9 7](https://s1.imagehub.cc/images/2025/01/04/96be0ab44e803fee0f56d82a28cac67f.png)
内存设置`4096MB`，根据你的实体机的硬件配置适量增减。
![9 8](https://s1.imagehub.cc/images/2025/01/04/8cdf9558e2f4cd1d2fb6c1b68b1eb797.png)
处理器数量设置`1`，每个处理器内核数量设置为`8`，适量减少也可以。  
如果有虚拟化需求就勾选`虚拟化引擎`。
![9 9](https://s1.imagehub.cc/images/2025/01/04/36daed5990058b11509f4fbf2427f2c6.png)
CD/DVD 点击`浏览`选择到你的Rocky Linux9.4镜像。
![9 10](https://s1.imagehub.cc/images/2025/01/04/b2c08da63e4fea86dc66077658b06f16.png)
网络适配器模式按需选择，不了解的自行bing。  
全部设置完成后点击`关闭`，再点击`完成`即可。
![9 11](https://s1.imagehub.cc/images/2025/01/04/b28e97e97b73e9926e8c1f0532843ad2.png)

# 3. 安装虚拟机
点击`开启此虚拟机`。
![9 12](https://s1.imagehub.cc/images/2025/01/04/b6a74593927fc9b030d22ae03aa3210e.png)
用上下方向键选择到`Install Rocky Linux 9.4`。
![9 13](https://s1.imagehub.cc/images/2025/01/04/1ccb9501eebf091e11fd8c3b8057c9ff.png)
稍加等待，然后选择系统语言，点击继续。
![9 14](https://s1.imagehub.cc/images/2025/01/04/985551761fc769dc39cf9300991370e7.png)
带有黄色感叹号的选项是必须进行配置的。
![9 15](https://s1.imagehub.cc/images/2025/01/04/b9621988471e3546e0c11a155e7ff89e.png)
首先来配置安装位置，点击`SYSTEM`下方的`Installation Destination`。  
点击选择到这个80GiB的磁盘，然后点击`Done`。
![9 16](https://s1.imagehub.cc/images/2025/01/04/b04bf1d93455878b0f75bdd85e7cc8c4.png)
然后配置Root密码。
![9 17](https://s1.imagehub.cc/images/2025/01/04/7a6717442994b2d8c0b99db32437420f.png)
设置完密码后，勾选`Allow root SSH login with password`,允许root用户使用密码进行SSH登录。  
当你使用的密码是弱密码时，需要点击2次`Done`。
![9 18](https://s1.imagehub.cc/images/2025/01/04/8c77c0c2ca6c82d8bcd5f129636186e5.png)
同时也可以点击`User Creation`创建一个普通用户，键入你的用户名及密码。  
`Make this user administrator`：设置此用户为管理员。  
`Require a password to use this accout`：需要密码才能使用这个账户。  
点击`Done`保存配置。  
![9 19](https://s1.imagehub.cc/images/2025/01/04/968d4b89adb053e6d3ae8cd53efbd27d.png)
然后点击`Software Selection`，选择软件版本。
![9 20](https://s1.imagehub.cc/images/2025/01/04/1cfc8da481d31def58e6b0ab22335eed.png)
我选择的是`Minimal Install`最小安装，只有命令行界面。
想要带有GUI界面的选择第1个`Server with GUI`,选择完成后点击`Done`。
![9 21](https://s1.imagehub.cc/images/2025/01/04/af0d6b0d5e429dfee5836612ca60063a.png)
然后就可以点击`Begin Installation`开始安装Rocky Linux 9.4了。
耐心等待安装。
![9 22](https://s1.imagehub.cc/images/2025/01/04/5e446e844603ab51ec970d5bb17d451a.png)
安装完成后点击`Reboot System`。
![9 23](https://s1.imagehub.cc/images/2025/01/04/92dc03fb5ec889f9a84ca08ae4349ed9.png)
然后就可以开始你的操作了。
![9 24](https://s1.imagehub.cc/images/2025/01/04/ba392b26ae76b820b62433c6730f2996.png)
