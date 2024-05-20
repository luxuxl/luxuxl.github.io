# Enable Administrator Account

Download:
- [蓝奏云 - del.zip](https://luxuyyds.lanzouq.com/b04wyq2la)
- `curl -OL https://my-website/win/del.zip`

```shell
:: 1. 激活 Administrator 账户，必须要斜线
net user Administrator /active:yes

:: 2. 取消 Administrator 账户密码
net user Administrator ""

:: 3. 删除当前账户，用户名改为创建的用户名
::net user your_account /del

:: 以管理员身份运行
```

# Active Windows

Download:
- [蓝奏云 - CMWTAT 激活工具](https://luxuyyds.lanzouq.com/iMEwV1l4s2re)
- `curl -OL https://my-website/win/active.zip`

# Forbid Windows Update

### Method 1

gpedit.msc → 计算机配置 → 管理模块 → windows 组件 → windows 更新 → 禁用

### Method 2

```shell
:: 1. stop the update service
sc stop wuauserv
:: 2. dont start auto
sc config wuauserv start=disabled
:: 3. start failure then dont take actions
sc failure wuauserv reset=0 actions=none
```

### Method 3

```shell
reg add "HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\WindowsUpdate\UX\Settings" /v FlightSettingsMaxPauseDays /t reg_dword /d 9999 /f
```

# Taskbar Transparent & Remove Icons


> [一分钟使win10任务栏完全透明化设置教程，无需下载软件\_哔哩哔哩\_bilibili](https://www.bilibili.com/video/BV1GL411g7wK/?spm_id_from=333.337.search-card.all.click&vd_source=b71fdb57a495d5345dbde99cbbeb52ac)

Download：
- `curl -OL https://my-website/reg.zip`

```shell
:: cmd 或 bat 运行
:: 1. 任务栏透明
reg add "HKCU\Software\Microsoft\Windows\CurrentVersion\Explorer\Advanced" /v TaskbarAcrylicOpacity /t REG_DWORD /d 0 /f

:: 2. 去除固定的快速图标
reg delete "HKCU\Software\Microsoft\Windows\CurrentVersion\Explorer\Taskband" /f

:: 3. 隐藏 Cortana
reg add "HKCU\Software\Microsoft\Windows\CurrentVersion\Explorer\Advanced" /v ShowCortanaButton /t REG_DWORD /d 0 /f

:: 4. 隐藏任务视图
reg add "HKCU\Software\Microsoft\Windows\CurrentVersion\Explorer\Advanced" /v ShowTaskViewButton /t REG_DWORD /d 0 /f

:: 5. 隐藏搜索栏
reg add "HKCU\SOFTWARE\Microsoft\Windows\CurrentVersion\Search" /v SearchboxTaskbarMode /t REG_DWORD /d 0 /f

:: 6. 重启 explorer
taskkill /f /im explorer.exe & explorer.exe
```

# Uninstall Builtin Apps

Download：
- `curl -OL https://my-website/reg.zip`

```shell
PowerShell "Get-AppxPackage *Clipchamp* -AllUsers | Remove-AppxPackage"                                                     # 卸载视频编辑器
PowerShell "Get-AppxPackage *Microsoft.549981C3F5F10* -AllUsers | Remove-AppxPackage"                                       # 卸载Cortana
PowerShell "Get-AppxPackage *Microsoft.BingNews* -AllUsers | Remove-AppxPackage"                                            # 资讯，没见过
PowerShell "Get-AppxPackage *Microsoft.BingWeather* -AllUsers | Remove-AppxPackage"                                         # 天气，没见过
PowerShell "Get-AppxPackage *Microsoft.WindowsSoundRecorder* -AllUsers | Remove-AppxPackage"                                # 录音
PowerShell "Get-AppxPackage *Microsoft.Wallet* -AllUsers | Remove-AppxPackage"                                              # 钱包？？
PowerShell "Get-AppxPackage *Microsoft.Microsoft.ZuneMusic* -AllUsers | Remove-AppxPackage"                                 # 不懂什么垃圾
PowerShell "Get-AppxPackage *Microsoft.WindowsAlarms* -AllUsers | Remove-AppxPackage"                                       # 闹钟
PowerShell "Get-AppxPackage *Microsoft.Windows.PeopleExperienceHost* -AllUsers | Remove-AppxPackage"                        # 不懂
PowerShell "Get-AppxPackage *Microsoft.GetHelp* -AllUsers | Remove-AppxPackage"                                             # 帮助
PowerShell "Get-AppxPackage *Microsoft.Getstarted* -AllUsers | Remove-AppxPackage"                                          # 使用技巧
PowerShell "Get-AppxPackage *Microsoft.Microsoft3DViewer* -AllUsers | Remove-AppxPackage"                                   # 3D Viewer
PowerShell "Get-AppxPackage *Microsoft.MicrosoftOfficeHub* -AllUsers | Remove-AppxPackage"                                  # Office 网页版
PowerShell "Get-AppxPackage *Microsoft.MicrosoftSolitaireCollection* -AllUsers | Remove-AppxPackage"                        # 扑克游戏
PowerShell "Get-AppxPackage *Microsoft.MicrosoftStickyNotes* -AllUsers | Remove-AppxPackage"                                # 便笺
PowerShell "Get-AppxPackage *Microsoft.MixedReality.Portal* -AllUsers | Remove-AppxPackage"                                 # 混合现实门户
PowerShell "Get-AppxPackage *Microsoft.MSPaint* -AllUsers | Remove-AppxPackage"                                             # 疑似 3D 画图，卸载应该对老版 mspaint 无影响
PowerShell "Get-AppxPackage *Microsoft.Office.OneNote* -AllUsers | Remove-AppxPackage"                                      # OneNote，win10 没有
PowerShell "Get-AppxPackage *Microsoft.People* -AllUsers | Remove-AppxPackage"                                              # 人脉
PowerShell "Get-AppxPackage *Microsoft.PowerAutomateDesktop* -AllUsers | Remove-AppxPackage"                                # PowerAutomate Desktop 不懂什么
PowerShell "Get-AppxPackage *Microsoft.ScreenSketch* -AllUsers | Remove-AppxPackage"                                        # 截图和草图
PowerShell "Get-AppxPackage *Microsoft.SkypeApp* -AllUsers | Remove-AppxPackage"                                            # Skype
PowerShell "Get-AppxPackage *Microsoft.Todos* -AllUsers | Remove-AppxPackage"                                               # Todos
PowerShell "Get-AppxPackage *Microsoft.WindowsFeedbackHub* -AllUsers | Remove-AppxPackage"                                  # 反馈中心
PowerShell "Get-AppxPackage *Microsoft.WindowsMaps* -AllUsers | Remove-AppxPackage"                                         # 地图
PowerShell "Get-AppxPackage *Microsoft.YourPhone* -AllUsers | Remove-AppxPackage"                                           # 你的手机
PowerShell "Get-AppxPackage *MicrosoftCorporationII.QuickAssist* -AllUsers | Remove-AppxPackage"                            # 快速助手
PowerShell "Get-AppxPackage *MicrosoftTeams* -AllUsers | Remove-AppxPackage"                                                # Microsoft Teams
# PowerShell "Get-AppxPackage *Microsoft.Windows.Search* -AllUsers | Remove-AppxPackage"                                    # 搜索
# PowerShell "Get-AppxPackage *Microsoft.GamingApp* -AllUsers | Remove-AppxPackage"                                         # 游戏组件
# PowerShell "Get-AppxPackage *Microsoft.Xbox* -AllUsers | Remove-AppxPackage"                                              # Xbox 组件
# PowerShell "Get-AppxPackage -AllUsers | Remove-AppxPackage"                                                               # 所有应用商店的软件
```

