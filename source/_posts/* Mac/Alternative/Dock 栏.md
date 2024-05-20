# 移除 Dock 栏所有固定的图标
## 方法一、直接删除 plist 文件

> [automation - Applescript to remove items from dock - Stack Overflow](https://stackoverflow.com/questions/56121092/applescript-to-remove-items-from-dock)

```zsh
cd ~/Library/Preferences
```

```zsh
defaults delete com.apple.dock persistent-apps; killall Dock
```

## ~~方法二、Apple Script~~

> [一大波AppleScript：新窗口移位置载项目执命令 等 - 知乎](https://zhuanlan.zhihu.com/p/41837831)

# Dock 栏添加空白应用

> [关于Mac Dock的10 个隐藏终端命令 - 知乎](https://zhuanlan.zhihu.com/p/459948105)

```bash
defaults write com.apple.dock persistent-apps -array-add '{"tile-type"="spacer-tile";}'; killall Dock
```

# 隐藏 Dock 栏某个 App 图标

> [MacOS隐藏Dock栏中特定App图标的三种方法 - 知乎](https://zhuanlan.zhihu.com/p/464697398)

找到某个需要隐藏的 App → Contents → info.plist

在 `<dict>` 下添加

```
<key>LSUIElement</key> 
<true/>
```

注: 一段时间后 App 会无法打开, 建议将原始的 `info.plist` 备份

