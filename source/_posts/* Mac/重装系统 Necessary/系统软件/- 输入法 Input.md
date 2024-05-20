## 删除 ABC

> [m1 mac 关闭自带ABC输入法(20220505亲测可用) - 掘金](https://juejin.cn/post/7094168323968991262)

### 一、关闭 SIP

输入以下命令检查系统是否关闭 SIP

```
csrutil status
```


### 二、修改文件

打开该文件 `sudo open /Users/$USER/Library/Preferences/com.apple.HIToolbox.plist`

找到 AppleEnableInputSources 中包含 ABC 的那项, 全部删除

![image](https://jsd.cdn.zzko.cn/gh/luxuxl/picx-images-hosting@master/20240215/image.9kfxlwvv7c.webp)

重新登陆


```
defaults write -g AppleKeyboardUIMode -int 3
defaults write -g ApplePressAndHoldEnabled -boolean false
```

```
# Enable full keyboard access for all controls
defaults write NSGlobalDomain AppleKeyboardUIMode -int 3

# 禁止按住触发西班牙语, 现在持续按住是重复
defaults write -g ApplePressAndHoldEnabled -boolean false
```