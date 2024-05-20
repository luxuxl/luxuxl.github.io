### defaults read -g 中存放了哪些有用的东西

```
"com.apple.keyboard.fnState" = 0;
取消将 fn 作为标准功能键, 就是按了直接可以调亮度、静音、暂停

待测试
AppleAquaColorVariant = 1;

"com.apple.springing.delay" = "0.5";
"com.apple.springing.enabled" = 1;
"com.apple.swipescrolldirection" = 1;
"com.apple.trackpad.forceClick" = 0;
"com.apple.trackpad.scaling" = 2;
```

### 时钟

```
dafaults read com.apple.MenuBarClock
```

ClockEnabled = 0;

### com.apple.Preview

```
dafaults read com.apple.Preview
```

可以修改预览的标注快捷键

### 通知中心

```

## 通知中心

还未测试

defaults write -g NSFileProviderDomainDisableAll 1

```