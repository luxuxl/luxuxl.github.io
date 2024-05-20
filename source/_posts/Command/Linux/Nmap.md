> [NMAP参数详解 - 知乎](https://zhuanlan.zhihu.com/p/420316338)

## 目标选择

```
nmap ip
nmap domain.com
nmap nmap 192.168.1.1-20
nmap 192.168.1.1/24
```

## 端口扫描

`<target>` 即上面的目标选择中的格式, 由于可以是 **某个 IP**、**域名**、**一段 IP**、**子网**, 所以用 `<target>` 指代

```
nmap -p 80 <target>

nmap -p 80,22,3306 <target>

nmap -p 1-100 <target>

nmap -F <target>

nmap -p- <target>
```

## 操作系统扫描

部分可能需要在前面加 sudo, 例如 `sudo nmap -O <target>`

```bash
# 探测操作系统
nmap -O <target>

# 探测软件版本
nmap -V <target>
nmap -sTV -p- -Pn <target>

# 检测操作系统和服务
nmap -A <target>

# 标准服务检测
nmap -sV <target>

# 轻量
nmap -sV --version-intensity 0 <target>

# 全面
nmap -sV --version-intensity 5 <target>
```

## 网站目录扫描

```bash
nmap --script=http-enum -p 80 <target>
```

