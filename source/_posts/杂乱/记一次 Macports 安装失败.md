# 问题描述

在[官网](https://www.macports.org/install.php)下载了 Macports 的 pkg 安装包，安装卡在“正在运行软件包脚本”

# 解决方案

断网安装 Macports

安装成功后修改 Macports 为国内源：

```bash
sudo vim /opt/local/etc/macports/sources.conf
```

注释以下内容

```bash
rsync://rsync.macports.org/macports/release/tarballs/ports.tar [default] 
```

添加

```bash
rsync://mirrors.tuna.tsinghua.edu.cn/macports/release/ports/ [default]
```

执行

```bash
sudo port -v selfupdate
```