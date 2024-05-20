> [Mac安装Homebrew的正确姿势 - 简书](https://www.jianshu.com/p/e0471aa6672d)

前言: Homebrew 不行, 换 Macports 吧

## 安装

强烈谴责国内某些搬运魔改恶心行为, 推广自己的群、公众号, 二维码恰烂钱我都忍了, 结果 arm 架构能帮我 `HOMEBREW_PREFIX` 设置成 intel 架构的路径

![01908734_13959213](https://jsd.cdn.zzko.cn/gh/luxuxl/picx-images-hosting@master/20240215/01908734_13959213.8ad0qtldvw.webp)

终端代理直接下 Github 原作者文件

```
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"
```

一个开屏二维码, 一个列出安装路径, 只能说高下立判

![image](https://jsd.cdn.zzko.cn/gh/luxuxl/picx-images-hosting@master/20240215/image.2yy4648qed.webp)

卸载 Homebrew

```
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/uninstall.sh)"
```

## 添加环境变量

分为两个部分
- 本体: 由于 Homebrew 本体默认安装位置为 `/opt/homebrew/bin/brew`, 先软链到软件的安装路径中, 直接为软件添加环境变量即可
- 软件: 安装路径为 `/usr/local/bin`

操作过程

```
sudo ln -s -n /opt/homebrew/bin/brew /usr/local/bin

vim ~/../.zprofile
```

添加如下内容

```
local="/usr/local/bin/"
export PATH="$local:$PATH"
```

## 基础使用

