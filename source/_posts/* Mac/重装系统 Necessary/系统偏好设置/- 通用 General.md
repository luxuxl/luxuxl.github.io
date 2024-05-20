##  前言

由于 defaults 命令无法禁用接力, 所以就索性全都 Apple Script 实现

## 解释和执行

由于可以添加注释, 所以 **解释** 和 **执行** 放在了一起

```python
osascript << EOF
tell application "System Preferences"
	activate
	delay 0.1
	reveal pane id "com.apple.preference.general"
    delay 0.5
	tell application "System Events"
        # 修改滚动条点击直接跳转
		set scroll bar action of the appearance preferences to jump to here
        # 禁用接力
		tell process "System Preferences"
            delay 0.1
            # 如果系统是英文要换成 "General"
			tell window "通用"
				if value of checkbox "允许在这台Mac和iCloud设备之间使用“接力”" is 1 then
					click checkbox "允许在这台Mac和iCloud设备之间使用“接力”"
					delay 0.1
					click button "不允许使用接力" of sheet 1
				end if
			end tell
		end tell
	end tell
end tell
EOF
```

## 补充

下面是 `osascript -e` 写法, 可能会有一些问题, 可参考的太少

可以确定的一些规则
- osascript -e 直接执行没有 delay

```
osascript -e 'tell application "System Preferences" to tell application "System Events" to set scroll bar action of the appearance preferences to jump to here'

osascript -e 'tell application "System Preferences" to activate'
osascript -e 'tell application "System Preferences" to reveal pane id "com.apple.preference.general"'

osascript -e 'tell application "System Preferences" to tell application "System Events" to tell process "System Preferences" to tell window "通用" to if (value of checkbox "允许在这台Mac和iCloud设备之间使用“接力”" is 1) then click checkbox "允许在这台Mac和iCloud设备之间使用“接力”"'

osascript -e 'tell application "System Preferences" to tell application "System Events" to tell process "System Preferences" to tell window "通用" to click button "不允许使用接力" of sheet 1'
```