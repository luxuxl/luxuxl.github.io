## 安装

下载 pkg 傻瓜式安装, 注意需要断网安装, 此处补充介绍手动编译安装

先去官网下载源码文件: [Index of /MacPorts](https://distfiles.macports.org/MacPorts/)

```
cd macports/MacPorts-2.8.0
./configure
make
sudo make install
```

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

## 添加环境变量

分为两个部分
- 本体: 本体也在 `opt/local/bin`, 会自动添加, 只需重新登录即可
- 软件: 安装路径为 `/opt/local/bin`, 也会自动添加到 `.zprofile`

## 基础使用

> [MacOS中MacPorts安装和使用](http://xstarcd.github.io/wiki/MacOS/MacOS_MacPorts.html)

```
# 搜索软件
port search cs_pkg_name

# 安装软件
sudo port install cs_pkg_name

# 清理安装时的临时文件
sudo port clean all

# 卸载软件
sudo port uninstall cs_pkg_name

# 查看已安装的软件
port installed

# 查看依赖信息
port deps cs_pkg_name

# 查看包详细信息 
port info cs_pkg_name
```

## 卸载所有软件

```
sudo port -fp uninstall installed
```

清理卸载残留

```
sudo port clean all
```

## 彻底卸载

> [2.4. Uninstall MacPorts](https://guide.macports.org/chunked/installing.macports.uninstalling.html)

### 1. Uninstall All Ports

```
sudo port -fp uninstall installed
```

### 2. Remove Users and Groups

```
sudo dscl . -delete /Users/macports
sudo dscl . -delete /Groups/macports
```

### 3. Remove the Rest of MacPorts

推荐这个, 防止文件找不到而报错终止

```
sudo rm -rf \
    /opt/local \
    /Applications/DarwinPorts \
    /Applications/MacPorts \
    /Library/StartupItems/DarwinPortsStartup \
    /Library/Tcl/darwinports1.0 \
    /Library/Tcl/macports1.0 \
    ~/.macports
```

更全, 但如果不存在则会报错终止

```
sudo rm -rf \
    /opt/local \
    /Applications/DarwinPorts \
    /Applications/MacPorts \
    /Library/LaunchDaemons/org.macports.* \
    /Library/Receipts/DarwinPorts*.pkg \
    /Library/Receipts/MacPorts*.pkg \
    /Library/StartupItems/DarwinPortsStartup \
    /Library/Tcl/darwinports1.0 \
    /Library/Tcl/macports1.0 \
    ~/.macports
```