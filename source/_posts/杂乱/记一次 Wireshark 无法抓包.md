# 问题描述

安装完 Wireshark 后提示没有权限，ChmodBPF 也安装了

![1708243464758](https://cdn.jsdelivr.net/gh/luxuxl/picx-images-hosting@master/20240218/1708243464758.webp)

# 解决方案

终端运行以下代码

```bash
sudo launchctl enable system/org.wireshark.ChmodBPF
sudo launchctl load '/Library/LaunchDaemons/org.wireshark.ChmodBPF.plist'
```