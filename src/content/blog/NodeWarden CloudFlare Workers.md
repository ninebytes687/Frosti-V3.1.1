---
title: "Cloudflare Worker部署NodeWarden"
description: "兼容Bitwarden客户端的个人专属自建密码管理服务端"
pubDate: "May 16 2026"
image: "https://s1.imagehub.cc/images/2026/05/17/c5033e090909577df25f73ee264a62d4.jpg"
categories:
  - tech
tags:
  - Cloudflare Workers
  - NodeWarden
---

# 什么是NodeWarden？
- 第三方Bitwarden兼容服务端，仅服务端，无独立客户端，直接用Bitwarden官方客户端连接；  
- 基于Cloudflare Workers+D1+R2，无服务器Serverless架构，主打零成本、免运维、全球边缘加速；  
- 定位：仅限个人单用户，不支持企业 / 团队组织功能；  

# Bitwarden与NodeWarden对比
| 功能项 | Bitwarden（官方） | NodeWarden（第三方） |
|:--- |:--- |:--- |
| Web网页密码库 | ✅  | ✅ 兼容原版Web Vault |
| 全量密码同步 | ✅ | ✅ 完美兼容官方客户端同步 |
| 文件附件存储 | ✅ | ✅ 基于Cloudflare R2 |
| Send文件/文本分享 | ✅ | ✅ 完整支持 |
| 导入导出（JSON/CSV） | ✅ | ✅ 兼容Bitwarden格式 |
| 多用户/家庭/组织 | ✅  | ❌ 仅个人 |
| 密码健康报告、泄露检测 | ✅ | ❌  |
| 应急访问、高级2FA | ✅ | ❌ 部分缺失 |
| 密钥管理、企业级权限 | ✅ | ❌  |
| 批量操作、审计日志 | 付费版 | 增强版支持 |

# Fork仓库
首先打开Github Fork [shuaiplus/nodewarden](https://github.com/shuaiplus/nodewarden)

# 创建Workers
然后打开你的CloudFlare Workers和Pages，创建应用程序。  
选择`Continue with GitHub`，选择到你刚刚Fork的nodewarden仓库。
![1](https://s1.imagehub.cc/images/2026/05/17/ad7f3c575c6dcfb2cef8a62c39075bf4.png)
默认使用R2对象存储，点击部署即可。  
若你的CF账号没有绑卡，可以将`npx wrangler deploy`改为`npm run deploy:kv`使用KV代替。
![2](https://s1.imagehub.cc/images/2026/05/17/036b43b89c1dd0d64874b7e7b7e69c85.png)
然后点击域-添加域名
![3](https://s1.imagehub.cc/images/2026/05/17/5743465cdb005107ff8352c7c2506d40.png)
然后输入子域名，添加即可（没有域名的也可以直接点击Worker URL访问）。
![4](https://s1.imagehub.cc/images/2026/05/17/1e22812284c0de464e475fda200e1605.png)

# 添加JWT密钥
然后打开你刚刚添加的子域名，复制下方自动生成的32位密钥。
![5](https://s1.imagehub.cc/images/2026/05/17/256e8e66057d13d777de7f2e20e7b2f4.png)
在Workers设置-变量和机密中，点击添加
![6](https://s1.imagehub.cc/images/2026/05/17/56530bd15003c4f9f2ddab0a39a08d1a.png)
`类型`选择`密钥`，`变量名称`为`JWT_SECRET`，值为你刚刚复制的32位随机密钥。
![7](https://s1.imagehub.cc/images/2026/05/17/1de4e60f214709c490b49b5a85f78bd5.png)
![8](https://s1.imagehub.cc/images/2026/05/17/d27b640615a694b8543b0a34eae59682.png)

# 注册管理员账户
密钥添加完成后，回到你的子域名链接内，使用F5刷新页面，注册账户，第一个注册的账户为管理员账户。
![9](https://s1.imagehub.cc/images/2026/05/17/bc100af58415480c862df47fe3e7f266.png)
# Success🎇
账户注册完成后，登录即可。  
手机客户端直接选择自托管，填入你的子域名链接即可登录。
![10](https://s1.imagehub.cc/images/2026/05/17/0f87d6504a6d304d4e1859066b703c72.png)