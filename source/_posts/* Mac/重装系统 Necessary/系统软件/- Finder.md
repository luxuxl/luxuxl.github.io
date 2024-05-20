查看 Finder 的设置

```
defaults read com.apple.finder
```

## 常规设置

### 执行

```
defaults write com.apple.finder ShowHardDrivesOnDesktop 0
defaults write com.apple.finder ShowExternalHardDrivesOnDesktop 1
defaults write com.apple.finder ShowMountedServersOnDesktop 0
defaults write com.apple.finder ShowRemovableMediaOnDesktop 0
defaults write com.apple.finder NewWindowTarget PfHm
defaults write com.apple.finder NewWindowTargetPath "file:///Users/luxury"
defaults write com.apple.finder FinderSpawnTab 1
defaults write com.apple.finder FavoriteTagNames '()'
defaults write -g AppleShowAllExtensions 1
defaults write com.apple.finder FXEnableExtensionChangeWarning 0
defaults write com.apple.finder "_FXSortFoldersFirst" 1
defaults write com.apple.finder "_FXSortFoldersFirstOnDesktop" 1
defaults write com.apple.finder AppleShowAllFiles 1
defaults write com.apple.finder FXDefaultSearchScope 'SCcf'
chflags nohidden ~/Library
defaults write com.apple.finder ShowPathbar 1
defaults write com.apple.finder ShowStatusBar 0
defaults write com.apple.finder ShowSidebar 1
defaults write com.apple.finder SidebarWidth 194
defaults write com.apple.finder ShowPreviewPane 0
defaults write com.apple.finder ShowRecentTags 0
defaults write com.apple.finder "NSToolbar Configuration Browser" -dict-add "TB Display Mode" 2
defaults write com.apple.finder "NSToolbar Configuration Browser" -dict-add "TB Item Identifiers" '("com.apple.finder.BACK","com.apple.finder.SRCH")'
defaults write com.apple.finder FXPreferredGroupBy 'Name'
defaults write com.apple.finder NSUserKeyEquivalents '{"\033\U524d\U5f80\033\U4e0b\U8f7d" = "@$l";"\033\U6587\U4ef6\033\U538b\U7f29" = "@g";"\033\U663e\U793a\033\U6574\U7406" = "@k";"\033\U7f16\U8f91\033\U5c06\U9879\U76ee\U79fb\U5230\U8fd9\U91cc" = "@$v";}'
defaults write com.apple.desktopservices DSDontWriteUSBStores 1
```

### 解释

```python
# ----------- 通用 ---------
# 在桌面上显示这些项目
ShowHardDrivesOnDesktop = 0;
ShowExternalHardDrivesOnDesktop = 1;
ShowMountedServersOnDesktop = 0;
ShowRemovableMediaOnDesktop = 0;

# 开启新“访达”窗口时打开
NewWindowTarget = PfHm;
NewWindowTargetPath = "file:///Users/luxury/";

# 总是在新标签打开
FinderSpawnTab = 1;

# ----------- 标签 ----------
# 需要清空
FavoriteTagNames = (
    "",
    "\\U7ea2\\U8272",
    "\\U6a59\\U8272",
    "\\U9ec4\\U8272",
    "\\U7eff\\U8272",
    "\\U84dd\\U8272",
    "\\U7d2b\\U8272",
    "\\U7070\\U8272"
);

# --------- 高级 -----------
# -g 全局设置中 显示所有文件扩展名
AppleShowAllExtensions = 1;

# 修改扩展名不提示 
FXEnableExtensionChangeWarning = 0;

# 文件夹放在前面
"_FXSortFoldersFirst" = 1;
"_FXSortFoldersFirstOnDesktop" = 1;

# com.apple.finder 显示隐藏文件
AppleShowAllFiles = 1;

# 不 隐藏资源库, 非 defaults 命令
chflags nohidden ~/Library

# com.apple.finder 搜索当前文件夹
FXDefaultSearchScope = SCcf;

# ------------ 显示设置 ------------
# 各种 Bar
ShowPathbar = 1;
ShowStatusBar = 0;
ShowSidebar = 1;
SidebarWidth = 194;
ShowPreviewPane = 0;
ShowRecentTags = 0;

# ------------- 工具栏设置 ---------------

"NSToolbar Configuration Browser" = {
    # 仅图标
    "TB Display Mode" = 2;
    # 工具栏图标
    "TB Item Identifiers" = (
        "com.apple.finder.BACK",
        "com.apple.finder.SRCH"
    );
};

# ------- 分组方式 ---------
FXPreferredGroupBy = Name;

# ------- 快捷键设置 -------
NSUserKeyEquivalents = {
    # cmd shift l 下载
    "\033\U524d\U5f80\033\U4e0b\U8f7d" = "@$l";
    # cmd g 压缩
    "\033\U6587\U4ef6\033\U538b\U7f29" = "@g";
    # cmd k 整理 
    "\033\U663e\U793a\033\U6574\U7406" = "@k";
    # cmd shift v 将项目移到这里     
    "\033\U7f16\U8f91\033\U5c06\U9879\U76ee\U79fb\U5230\U8fd9\U91cc" = "@$v";
};

# 去除 DS_Store
defaults write com.apple.desktopservices DSDontWriteUSBStores 1

# ---------- 可选 ----------
# Allow quitting Finder via ⌘ + Q , doing so will also hide desktop icons
# defaults write com.apple.finder QuitMenuItem -bool true

# --------------- 待测试 -------------
SidebarDevicesSectionDisclosedState = 1;
SidebarPlacesSectionDisclosedState = 1;
SidebarShowingSignedIntoiCloud = 1;
SidebarShowingiCloudDesktop = 1;
SidebarTagsSctionDisclosedState = 1;
SidebariCloudDriveSectionDisclosedState = 1;
```

## 显示设置

> [macOS Preferences Defaults · GitHub](https://gist.github.com/ChristopherA/98628f8cd00c94f11ee6035d53b0d3c6?permalink_comment_id=3976606)

查看当前文件夹的显示选项

```python
defaults read com.apple.finder DesktopViewSettings
defaults read com.apple.finder StandardViewSettings
defaults read com.apple.finder ComputerViewSettings
defaults read com.apple.finder "FK_StandardViewSettings"
```

### 执行

经测试, 利用 `defaults` 修改无法生效, 利用 `/usr/libexec/PlistBuddy` 可以修改成功, 但有前提条件, 否则就算和系统生成值一模一样, 仍然无法生效

猜测是导致 `plist` 文件格式改变成 `XML` 形式

前提条件就是, 必须手动随笔修改一个桌面显示选项, 由系统自动生成, 然后再用 `/usr/libexec/PlistBuddy -c Set`

```python
export tool="/usr/libexec/PlistBuddy"
$tool -c "Set :DesktopViewSettings:IconViewSettings:arrangeBy grid" ~/Library/Preferences/com.apple.finder.plist
$tool -c "Set :DesktopViewSettings:IconViewSettings:iconSize 52" ~/Library/Preferences/com.apple.finder.plist
$tool -c "Set :DesktopViewSettings:IconViewSettings:gridSpacing 1" ~/Library/Preferences/com.apple.finder.plist
$tool -c "Set :DesktopViewSettings:IconViewSettings:textSize 10" ~/Library/Preferences/com.apple.finder.plist
$tool -c "Set :DesktopViewSettings:IconViewSettings:labelOnBottom 1" ~/Library/Preferences/com.apple.finder.plist
$tool -c "Set :DesktopViewSettings:IconViewSettings:showIconPreview 1" ~/Library/Preferences/com.apple.finder.plist
$tool -c "Set :DesktopViewSettings:IconViewSettings:showItemInfo 0" ~/Library/Preferences/com.apple.finder.plist
$tool -c "Set :DesktopViewSettings:IconViewSettings:viewOptionsVersion 1" ~/Library/Preferences/com.apple.finder.plist

$tool -c "Set :StandardViewSettings:IconViewSettings:arrangeBy name" ~/Library/Preferences/com.apple.finder.plist
$tool -c "Set :StandardViewSettings:IconViewSettings:iconSize 64" ~/Library/Preferences/com.apple.finder.plist
$tool -c "Set :StandardViewSettings:IconViewSettings:gridSpacing 42" ~/Library/Preferences/com.apple.finder.plist
$tool -c "Set :StandardViewSettings:IconViewSettings:textSize 12" ~/Library/Preferences/com.apple.finder.plist
$tool -c "Set :StandardViewSettings:IconViewSettings:labelOnBottom 1" ~/Library/Preferences/com.apple.finder.plist
$tool -c "Set :StandardViewSettings:IconViewSettings:showIconPreview 1" ~/Library/Preferences/com.apple.finder.plist
$tool -c "Set :StandardViewSettings:IconViewSettings:showItemInfo 1" ~/Library/Preferences/com.apple.finder.plist
```


### 解释

```js
// 桌面显示选项
DesktopViewSettings = {
    IconViewSettings =     {
        arrangeBy = grid;
        iconSize = 52;
        gridOffsetX = 0;
        gridOffsetY = 0;
        gridSpacing = 1;
        textSize = 10;
        labelOnBottom = 1;
        showItemInfo = 0;
        showIconPreview = 1;
    };
};

// 默认显示选项
defaults read com.apple.finder StandardViewSettings

StandardViewSettings
{
    IconViewSettings =     {
        arrangeBy = name;
        iconSize = 64;
        gridOffsetX = 0;
        gridOffsetY = 0;
        gridSpacing = 42;
        textSize = 12;
        labelOnBottom = 1;
        showItemInfo = 1;
        showIconPreview = 1;
    };
};

// 未知 - ComputerViewSettings

// 未知 - FK_StandardViewSettings
```














# For Test

```python
export tool="/usr/libexec/PlistBuddy"
defaults delete com.apple.finder DesktopViewSettings
defaults read com.apple.finder DesktopViewSettings
open ~/Library/Preferences

# 以下参照系统默认格式写法, 请单独执行, 忽略上面的内容
export tool="/usr/libexec/PlistBuddy"
defaults delete com.apple.finder DesktopViewSettings
$tool -c "Add :DesktopViewSettings:IconViewSettings:backgroundColorBlue integer 1" ~/Library/Preferences/com.apple.finder.plist
$tool -c "Add :DesktopViewSettings:IconViewSettings:backgroundColorGreen integer 1" ~/Library/Preferences/com.apple.finder.plist
$tool -c "Add :DesktopViewSettings:IconViewSettings:backgroundColorRed integer 1" ~/Library/Preferences/com.apple.finder.plist
$tool -c "Add :DesktopViewSettings:IconViewSettings:backgroundType integer 0" ~/Library/Preferences/com.apple.finder.plist
$tool -c "Add :DesktopViewSettings:IconViewSettings:gridOffsetX integer 0" ~/Library/Preferences/com.apple.finder.plist
$tool -c "Add :DesktopViewSettings:IconViewSettings:gridOffsetY integer 0" ~/Library/Preferences/com.apple.finder.plist
$tool -c "Add :DesktopViewSettings:IconViewSettings:gridSpacing integer 1" ~/Library/Preferences/com.apple.finder.plist
$tool -c "Add :DesktopViewSettings:IconViewSettings:iconSize integer 52" ~/Library/Preferences/com.apple.finder.plist
$tool -c "Add :DesktopViewSettings:IconViewSettings:labelOnBottom bool 1" ~/Library/Preferences/com.apple.finder.plist
$tool -c "Add :DesktopViewSettings:IconViewSettings:showIconPreview bool 1" ~/Library/Preferences/com.apple.finder.plist
$tool -c "Add :DesktopViewSettings:IconViewSettings:showItemInfo bool 0" ~/Library/Preferences/com.apple.finder.plist
$tool -c "Add :DesktopViewSettings:IconViewSettings:textSize integer 1" ~/Library/Preferences/com.apple.finder.plist
$tool -c "Add :DesktopViewSettings:IconViewSettings:viewOptionsVersion integer 1" ~/Library/Preferences/com.apple.finder.plist

$tool -c "Set :DesktopViewSettings:IconViewSettings:arrangeBy grid" ~/Library/Preferences/com.apple.finder.plist
$tool -c "Set :DesktopViewSettings:IconViewSettings:backgroundColorBlue 1" ~/Library/Preferences/com.apple.finder.plist
$tool -c "Set :DesktopViewSettings:IconViewSettings:backgroundColorGreen 1" ~/Library/Preferences/com.apple.finder.plist
$tool -c "Set :DesktopViewSettings:IconViewSettings:backgroundColorRed 1" ~/Library/Preferences/com.apple.finder.plist
$tool -c "Set :DesktopViewSettings:IconViewSettings:backgroundType 0" ~/Library/Preferences/com.apple.finder.plist
$tool -c "Set :DesktopViewSettings:IconViewSettings:gridOffsetX 0" ~/Library/Preferences/com.apple.finder.plist
$tool -c "Set :DesktopViewSettings:IconViewSettings:gridOffsetY 0" ~/Library/Preferences/com.apple.finder.plist
$tool -c "Set :DesktopViewSettings:IconViewSettings:gridSpacing 1" ~/Library/Preferences/com.apple.finder.plist
$tool -c "Set :DesktopViewSettings:IconViewSettings:iconSize 52" ~/Library/Preferences/com.apple.finder.plist
$tool -c "Set :DesktopViewSettings:IconViewSettings:labelOnBottom 1" ~/Library/Preferences/com.apple.finder.plist
$tool -c "Set :DesktopViewSettings:IconViewSettings:showIconPreview 1" ~/Library/Preferences/com.apple.finder.plist
$tool -c "Set :DesktopViewSettings:IconViewSettings:showItemInfo 0" ~/Library/Preferences/com.apple.finder.plist
$tool -c "Set :DesktopViewSettings:IconViewSettings:textSize 1" ~/Library/Preferences/com.apple.finder.plist
$tool -c "Set :DesktopViewSettings:IconViewSettings:viewOptionsVersion 1" ~/Library/Preferences/com.apple.finder.plist
```