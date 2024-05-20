# 前置要求

获取 OneDrive 的
- client id
- client_secret
- refresh_token

比较麻烦的是 refresh_token 的获取，有以下四种方法：
##### 方法一（适合 win）

> [通过Rclone获取onedrive的refresh_token - 哔哩哔哩 (bilibili.com)](https://www.bilibili.com/read/cv15496588/)

##### 方法二（全平台适用）

> [用Cloudflare Workers搭建免费OneDrive网盘 - 春风吹 - 浅秋枫影的博客 (cuojue.org)](https://cuojue.org/read/Cloudflare-Workers-OneDrive.html)

本地自建环境获取

##### 方法三（已失效）

> [用Cloudflare Workers搭建免费OneDrive网盘 - 春风吹 - 浅秋枫影的博客 (cuojue.org)](https://cuojue.org/read/Cloudflare-Workers-OneDrive.html)

通过 [Microsoft Graph API Auth (heymind.github.io)](https://heymind.github.io/tools/microsoft-graph-api-auth) 获取

按教程获取 refresh_token 会失败

##### 方法四（类似三）

> [(Example) How to Get the Access Token Credentials from OneDrive (agilepoint.com)](https://documentation.agilepoint.com/00/appbuilder/accesstokenFindClientIdSecretIdOneDriveClone.html)

| name                    | value                                    |
| ----------------------- | ---------------------------------------- |
| Application (client) ID | 8e69b5e5-0a1f-417f-a9e6-71c6b9cf5443     |
| client secret           | 5AL8Q~2RBO-J3cQEK1jToQGm1AehIPLY6SEbbbXo | 
# onedrive-cf-index 部署

> [用Cloudflare Workers搭建免费OneDrive网盘 - 春风吹 - 浅秋枫影的博客 (cuojue.org)](https://cuojue.org/read/Cloudflare-Workers-OneDrive.html)
> 
> [如何零成本挂载 OneDrive | 小嘉的部落格 (imzjw.cn)](https://blog.imzjw.cn/posts/cf-onedrive/index.html#%E9%85%8D%E7%BD%AE-Cloudflare)

克隆项目

```bash
git clone https://github.com/spencerwooo/onedrive-cf-index.git
```

安装依赖项

```bash
cd onedrive-cf-index
npm install
```

安装 cloudflare 官方 workers 编译部署工具

```bash
npm i @cloudflare/wrangler -g
```

登录 Cloudflare 账户

```
wrangler login
```

服务器上测试没成功，懒得本机搭环境了，鸽了
# OneManager + Cloudflare 部署

> [GitHub - qkqpttgf/OneManager-php](https://github.com/qkqpttgf/OneManager-php)
> 
> [GitHub - qkqpttgf/OneManager-cfworkerskv: 部署在cloudflare的workers中的OneManager。](https://github.com/qkqpttgf/OneManager-cfworkerskv)
> 
> [OneManager+CloudFlare Workers部署教程_cloudflare worker环境在哪儿-CSDN博客](https://blog.csdn.net/qq_39010320/article/details/119923459)
> 
> [CloudFlare Workers 设置使用自己的域名 - VirCloud's Blog - Learning&Sharing](https://vircloud.net/exp/cf-worker-domain.html)

也可以利用 Vercel 部署，在下一小节，先介绍 Cloudflare 部署并自定义域名

## 创建 KV 和 Worker

创建一个 KV，名字无所谓，后面会有下拉框让你选择，方便识别就行

创建一个 Worker，名字会影响你分配的域名，但反正都被墙，需要路由到自己的域名，所以也无所谓

进入 Worker 并编辑代码，复制并粘贴以下代码：[OneManager-cfworkerskv](https://github.com/qkqpttgf/OneManager-cfworkerskv)

然后进入 Worker 的设置 → 变量 → KV 命名空间绑定，变量名称为`OMKV`，KV命名空间选择你创建的

## 配置 OneManager

进入给你分配的 Worker 域名（需要开代理），按照指引步骤来


## 路由至自定义域名

需要将域名托管到 Cloudflare 才可以，此处不再赘述

进入要托管的网站，在左侧找到 Workers 路由，点击添加，路由填写`cs_subdomain.cs_domain/*`，`custom_subdomain`处填写你想要的子域名，`cs_domain`处是你托管的域名，最后的 `/*` 必须要加上，否则子路径无法进行路由



# OneManager + Vercel 部署

>  [使用 Vercel+OneManager+阿里云盘 0成本搭建不限速网盘](https://certstone.top/index.php/archives/48/)

# Alist 部署

> [OneDrive | AList文档 (nn.ci)](https://alist.nn.ci/zh/guide/drivers/onedrive.html)

