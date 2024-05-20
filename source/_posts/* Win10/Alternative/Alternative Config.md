# 关闭虚拟化安全

> [Windows 10/11关闭虚拟化安全功能：游戏性能飙升最多37.7％ - 哔哩哔哩](https://www.bilibili.com/read/cv22458400/?from=articleDetail)

1. 确认该功能是否打开，win + r → msinfo32
2. 以管理员身份终端运行`bcdedit /set hypervisorlaunchtype off`

# 关闭 Antimalware Service Executable

> [如何禁用Antimalware Service Executable - Rogn - 博客园](https://www.cnblogs.com/lfri/p/11881329.html)

### Method 1

gpedit.msc → 计算机配置 → 管理模板 → Windows组件 → Windows Defender防病毒程序 → 实时保护 → 关闭实时保护

但好像仍然出现

### Method 2

cmd 运行 

```bash
reg add "HKEY_LOCAL_MACHINE\SOFTWARE\Policies\Microsoft\Windows Defender" /v "DisableAntiSpyware" /d 1 /t REG_DWORD /f
```

# 家庭版开启 Hyper-V

```shell
pushd "%~dp0"

dir /b %SystemRoot%servicingPackages*Hyper-V*.mum >hv.txt

for /f %%i in ('findstr /i . hv.txt 2^>nul') do dism /online /norestart /add-package:"%SystemRoot%servicingPackages%%i"

del hv.txt

Dism /online /enable-feature /featurename:Microsoft-Hyper-V -All /LimitAccess /ALL

pause
```

# 家庭版开启组策略

```shell
@echo off

pushd "%~dp0"

dir /b C:\Windows\servicing\Packages\Microsoft-Windows-GroupPolicy-ClientExtensions-Package~3*.mum >List.txt

dir /b C:\Windows\servicing\Packages\Microsoft-Windows-GroupPolicy-ClientTools-Package~3*.mum >>List.txt
for /f %%i in ('findstr /i . List.txt 2^>nul') do dism /online /norestart /add-package:"C:\Windows\servicing\Packages\%%i"

pause
```

