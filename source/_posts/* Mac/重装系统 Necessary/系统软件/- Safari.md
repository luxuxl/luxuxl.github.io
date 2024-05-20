# Safari
查看 Safari 偏好设置

```
defaults read com.apple.Safari
```

查看快速搜索词条

```
defaults read /Users/$USERNAME/Library/Safari/SearchDescriptions WebsiteSpecificSearchDescriptions
```

以下分为 **执行** 和 **解释** , 一个为了执行方便, 一个为了理解查阅方便

且 **解释** 中是 Plist 存储的形式,  **执行** 是命令的形式

## 执行

```bash
defaults write com.apple.Safari ShowBackgroundImageInFavorites 1
defaults write com.apple.Safari ShowFavorites 1
defaults write com.apple.Safari ShowFrequentlyVisitedSites 0
defaults write com.apple.Safari ShowHighlightsInFavorites 0
defaults write com.apple.Safari ShowPrivacyReportInFavorites 0
defaults write com.apple.Safari ShowReadingListInFavorites 0
defaults write com.apple.Safari HideStartPageSiriSuggestionsEmptyItemView 0
defaults write com.apple.Safari ShowSiriSuggestionsPreference 0
defaults write com.apple.Safari NSNavLastRootDirectory "~/Desktop"
defaults write com.apple.Safari DownloadsClearingPolicy 2
defaults write com.apple.Safari AutoOpenSafeDownloads 0
defaults write com.apple.Safari "NSWindow Frame BrowserWindowFrame" "0 0 1440 900 0 0 1440 900"
defaults write com.apple.Safari ShowStandaloneTabBar 0
defaults write com.apple.Safari EnableNarrowTabs 0
defaults write com.apple.Safari TabCreationPolicy 2
defaults write com.apple.Safari OpenNewTabsInFront 1
defaults write com.apple.Safari AutoFillCreditCardData 0
defaults write com.apple.Safari AutoFillFromAddressBook 0
defaults write com.apple.Safari AutoFillMiscellaneousForms 0
defaults write com.apple.Safari AutoFillPasswords 0
defaults write com.apple.Safari SearchProviderShortName Bing
defaults write com.apple.Safari SuppressSearchSuggestions 1
defaults write com.apple.Safari WebsiteSpecificSearchEnabled 0
defaults write com.apple.Safari PreloadTopHit 0
defaults write com.apple.Safari IncludeDevelopMenu 1
defaults write com.apple.Safari "NSToolbar Configuration BrowserToolbarIdentifier-v4.6" -dict-add "TB Item Identifiers" "(InputFieldsToolbarIdentifier,UnifiedTabBarToolbarIdentifier)"
defaults write /Users/$USERNAME/Library/Safari/SearchDescriptions WebsiteSpecificSearchDescriptions
```

## 解释

```bash
# ----------- com.apple.Safari -----------
# 首页, 展示背景图片和收藏, 其他全关闭
ShowBackgroundImageInFavorites = 1;
ShowFavorites = 1;
ShowFrequentlyVisitedSites = 0;
ShowHighlightsInFavorites = 0;
ShowPrivacyReportInFavorites = 0;
ShowReadingListInFavorites = 0;
HideStartPageSiriSuggestionsEmptyItemView = 0;
ShowSiriSuggestionsPreference = 0;

# ---- 通用 ------
# 默认下载地址
NSNavLastRootDirectory = "~/Desktop";

# 下载成功移除下载项
DownloadsClearingPolicy = 2;

# 下载后安全打开
AutoOpenSafeDownloads = 0;  

# ---- 标签页 -----
# 窗口最大化
"NSWindow Frame BrowserWindowFrame" = "0 0 1440 900 0 0 1440 900 ";

# 紧凑标签, 好看的那个
ShowStandaloneTabBar = 0;

# 在标签页中始终显示网站标题
EnableNarrowTabs = 0;

# 始终在新标签页打开
TabCreationPolicy = 2;

# 打开新标签页或窗口后，使其成为活跃标签页或窗口
OpenNewTabsInFront = 1;

# ----- 自动填充 -----
# 自动填充. . . 
AutoFillCreditCardData = 0;
AutoFillFromAddressBook = 0;
AutoFillMiscellaneousForms = 0;
AutoFillPasswords = 0;

# ---- 搜索 ------

# 搜索引擎
SearchProviderShortName = Bing;

# 关闭搜索引擎建议, 就是 1 没错
SuppressSearchSuggestions = 1;

# 关闭快速网站搜索
WebsiteSpecificSearchEnabled = 0;

# 关闭在后台载入最佳搜索结果
PreloadTopHit = 0;

# -----------
# 启用开发者菜单
IncludeDevelopMenu = 1;

# --- 菜单栏 -----

"NSToolbar Configuration BrowserToolbarIdentifier-v4.6" = {
    "TB Display Mode" = 2;
    "TB Icon Size Mode" = 1;
    "TB Is Shown" = 1;    
    "TB Size Mode" = 1;
    
    # 移除菜单栏乱七八糟的工具, 其他的也显示是可能会用到
    "TB Item Identifiers" = (
        SidebarSeparatorToolbarItemIdentifier,
        UnifiedTabBarToolbarIdentifier
    );

    # 这样将彻底移除 ToolBar 上所有内容
    "TB Item Identifiers" = (
        SidebarSeparatorToolbarItemIdentifier,
        UnifiedTabBarToolbarIdentifier
    );
};

# ----------- /Users/$USERNAME/Library/Safari/SearchDescriptions.plist -----------
# 这就是快速搜索引擎
WebsiteSpecificSearchDescriptions =     (
            {
        DateAdded = "2024-03-27 12:49:29 +0000";
        SearchURLTemplateStringFromForm = "https://cn.bing.com/search?go=%E6%90%9C%E7%B4%A2&q={searchTerms}&qs=n&form=QBRE&sp=-1&lq=0&pq=mdn&sc=10-3&cvid=9F1AFE72DF034A2BB42825181B5F69F6&ghsh=0&ghacc=0";
        SourcePageURLString = "https://www.bing.com/search?q=msdn&form=APMCS1&PC=APMC";
    },
            {
        DateAdded = "2024-03-27 12:49:29 +0000";
        SearchURLTemplateStringFromForm = "https://cn.bing.com/search?go=%E6%90%9C%E7%B4%A2&q={searchTerms}&qs=n&form=QBRE&sp=-1&lq=0&pq=ms+lerner+pe+fil&sc=7-16&cvid=096D343822D043B58DC464D2461DD9A4&ghsh=0&ghacc=0";
        SourcePageURLString = "https://cn.bing.com/search?q=msdn&form=APMCS1&PC=APMC";
    }
);
```