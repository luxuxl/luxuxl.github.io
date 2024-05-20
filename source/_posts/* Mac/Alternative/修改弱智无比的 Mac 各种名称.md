> [3 招教你轻松更改 Mac 计算机名、主机名和 Bonjour 名称 - 系统极客](https://www.sysgeek.cn/customize-mac-name/)

### ComputerName

`ComputerName` 就是显示在 iCloud 设备列表里那个名称, 并无卵用

```
scutil --set ComputerName "NewComputerName"
```

### HostName

终端显示的那个名称

```
scutil --set HostName "NewHostname"
```

