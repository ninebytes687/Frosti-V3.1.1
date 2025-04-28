---
title: "Rocky Linux 9.4 VMware安装教程"
description: "仅限amdx86_64CPU架构"
pubDate: "Nov 3 2024"
image: "https://s21.ax1x.com/2025/01/16/pEF5GMd.jpg"
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
![4 1](https://s1.imagehub.cc/images/2025/04/26/ff84b91741de87db800953e0177dc51d.png)
# 2. 创建新的虚拟机
打开VMware Workstation Pro 17，创建新的虚拟机。  
类型选择`典型`。
![4 2](https://s1.imagehub.cc/images/2025/04/26/790c65fd8bc1b77b002680a11e96cf35.png)
选择`稍后安装操作系统`。
![4 3](https://s1.imagehub.cc/images/2025/04/26/b3973f3524444d6af8b1ba2cd672b47e.png)
客户机操作系统选择`Linux`，版本选择`其他 Linux 5.x 内核 64位`。
![4 4](https://s1.imagehub.cc/images/2025/04/26/4cf52482491d809fce6630004f94227a.png)
填写虚拟机名称及选择虚拟机安装位置。
![4 5](https://s1.imagehub.cc/images/2025/04/26/57cbc6a36abc2bad5d437129ade71e7d.png)
最大磁盘大小建议`50G+`。
![4 6](https://s1.imagehub.cc/images/2025/04/26/75647d37853938b16217eb6f57f6a78c.png)
点击`自定义硬件`。
![4 7](https://s1.imagehub.cc/images/2025/04/26/ef6bd37aa3b224b8f3c633bee2481a9f.png)
内存设置`4096MB`，根据你的实体机的硬件配置适量增减。
![4 8](https://s1.imagehub.cc/images/2025/04/26/17c3104cdce43908e4225c7c3dac7d06.png)
处理器数量设置`1`，每个处理器内核数量设置为`8`，适量减少也可以。  
如果有虚拟化需求就勾选`虚拟化引擎`。
![4 9](https://s1.imagehub.cc/images/2025/04/26/8998ddf539af5976a076d7d69ea15ae6.png)
CD/DVD 点击`浏览`选择到你的Rocky Linux9.4镜像。
![4 10](https://s1.imagehub.cc/images/2025/04/26/c3b3be119e917fabcb986928384aac6c.png)
网络适配器模式按需选择，不了解的自行bing。  
全部设置完成后点击`关闭`，再点击`完成`即可。
![4 11](https://s1.imagehub.cc/images/2025/04/26/35b3082704e3475cefb6bb0e379f4e6e.png)

# 3. 安装虚拟机
点击`开启此虚拟机`。
![4 12](https://s1.imagehub.cc/images/2025/04/26/7942ac919fa4507570dd6cab96e2286c.png)
用上下方向键选择到`Install Rocky Linux 9.4`。
![4 13](https://s1.imagehub.cc/images/2025/04/26/f4f90717981d6fd522ef4a0df3d2b891.png)
稍加等待，然后选择系统语言，点击继续。
![4 14](https://s1.imagehub.cc/images/2025/04/26/7ec44e6998232fe50ad544ba5865b3fc.png)
带有黄色感叹号的选项是必须进行配置的。
![4 15](https://s1.imagehub.cc/images/2025/04/26/efefa15e690f70ac32b0baa12dc5b157.png)
首先来配置安装位置，点击`SYSTEM`下方的`Installation Destination`。  
点击选择到这个80GiB的磁盘，然后点击`Done`。
![4 16](https://s1.imagehub.cc/images/2025/04/26/60848fceef946943edcce22753f70455.png)
然后配置Root密码。
![4 17](https://s1.imagehub.cc/images/2025/04/26/d97c1c24b3707f43e03be135e91477db.png)
设置完密码后，勾选`Allow root SSH login with password`,允许root用户使用密码进行SSH登录。  
当你使用的密码是弱密码时，需要点击2次`Done`。
![4 18](https://s1.imagehub.cc/images/2025/04/26/6e1891f57241949f9e47af0322588f9a.png)
同时也可以点击`User Creation`创建一个普通用户，键入你的用户名及密码。  
`Make this user administrator`：设置此用户为管理员。  
`Require a password to use this accout`：需要密码才能使用这个账户。  
点击`Done`保存配置。  
![4 19](https://s1.imagehub.cc/images/2025/04/28/a809f84ade73b30e3601c03503f49e68.png)
然后点击`Software Selection`，选择软件版本。
![4 20](https://s1.imagehub.cc/images/2025/04/28/d3824137a7fc0a1e63ff44e21ca416d3.png)
我选择的是`Minimal Install`最小安装，只有命令行界面。
想要带有GUI界面的选择第1个`Server with GUI`,选择完成后点击`Done`。
![4 21](https://s1.imagehub.cc/images/2025/04/28/31620ea0f4fe923cf798ba56eb1cce79.png)
然后就可以点击`Begin Installation`开始安装Rocky Linux 9.4了。
耐心等待安装。
![4 22](https://s1.imagehub.cc/images/2025/04/28/7af462a79952fda97769e0f384d7ad11.png)
安装完成后点击`Reboot System`。
![4 23](https://s1.imagehub.cc/images/2025/04/28/0ff948ca8e076f41fb8eec95ecc4fdca.png)
然后就可以开始你的操作了。
![4 24](https://s1.imagehub.cc/images/2025/04/28/da610dd50eb16a57fce0fac12b6676b7.png)
