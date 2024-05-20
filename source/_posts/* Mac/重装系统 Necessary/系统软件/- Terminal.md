

## 执行

无法执行, 老老实实导入 `.terminal` 文件

`curl -OL $cs_my_download_site/config/terminal.zip`

## 解释

```python
# 配色方案
"Window Settings" = {
    Basic = {
        # ----------- 背景 ---------------
        # 不透明度 + 颜色
        BackgroundColor = {length = 1045, bytes = 0x62706c69 73743030 d4010203 04050607 ... 00000000 000003a5 };        
        BackgroundBlur = "0.05";

        # 不活跃的窗口
        BackgroundSettingsForInactiveWindows = 1;
        BackgroundAlphaInactive = "0.35";
        BackgroundBlurInactive = "0.10";

        # ------------ 字体 --------------
        Font = {length = 259, bytes = 0x62706c69 73743030 d4010203 04050607 ... 00000000 000000c7 };
        TextColor = {length = 948, bytes = 0x62706c69 73743030 d4010203 04050607 ... 00000000 00000344 };
        
        # 字符间距
        FontAntialias = 1;
        # 行间距
        FontWidthSpacing = 1;
        # 不 允许使用粗体字
        UseBoldFonts = 0;

        # --------- ANSI颜色 ----------
        ANSIBlackColor = {length = 274, bytes = 0x62706c69 73743030 d4010203 04050607 ... 00000000 000000d9 };
        ANSIBlueColor = {length = 1014, bytes = 0x62706c69 73743030 d4010203 04050607 ... 00000000 00000386 };
        ANSIBrightBlackColor = {length = 274, bytes = 0x62706c69 73743030 d4010203 04050607 ... 00000000 000000d9 };
        ANSIBrightBlueColor = {length = 1017, bytes = 0x62706c69 73743030 d4010203 04050607 ... 00000000 00000389 };
        ANSIBrightCyanColor = {length = 274, bytes = 0x62706c69 73743030 d4010203 04050607 ... 00000000 000000d9 };
        ANSIBrightGreenColor = {length = 273, bytes = 0x62706c69 73743030 d4010203 04050607 ... 00000000 000000d8 };
        ANSIBrightMagentaColor = {length = 263, bytes = 0x62706c69 73743030 d4010203 04050607 ... 00000000 000000ce };
        ANSIBrightRedColor = {length = 262, bytes = 0x62706c69 73743030 d4010203 04050607 ... 00000000 000000cd };
        ANSIBrightWhiteColor = {length = 1017, bytes = 0x62706c69 73743030 d4010203 04050607 ... 00000000 00000389 };
        ANSIBrightYellowColor = {length = 273, bytes = 0x62706c69 73743030 d4010203 04050607 ... 00000000 000000d8 };
        ANSICyanColor = {length = 274, bytes = 0x62706c69 73743030 d4010203 04050607 ... 00000000 000000d9 };
        ANSIGreenColor = {length = 273, bytes = 0x62706c69 73743030 d4010203 04050607 ... 00000000 000000d8 };
        ANSIMagentaColor = {length = 263, bytes = 0x62706c69 73743030 d4010203 04050607 ... 00000000 000000ce };
        ANSIRedColor = {length = 263, bytes = 0x62706c69 73743030 d4010203 04050607 ... 00000000 000000ce };
        ANSIWhiteColor = {length = 237, bytes = 0x62706c69 73743030 d4010203 04050607 ... 00000000 000000b4 };
        ANSIYellowColor = {length = 273, bytes = 0x62706c69 73743030 d4010203 04050607 ... 00000000 000000d8 };
        # ---------- 光标 ---------
        # 类型
        CursorType = 2;
        # 颜色
        CursorColor = {length = 995, bytes = 0x62706c69 73743030 d4010203 04050607 ... 00000000 00000373 };
        # 闪动
        CursorBlink = 1;

        # ----------- 窗口 ------------
        WindowTitle = "";
        ShowRepresentedURLInTitle = 0;
        ShowActiveProcessInTitle = 0;
        ShowActiveProcessArgumentsInTitle = 0;
        ShowWindowSettingsNameInTitle = 1;
        ShowDimensionsInTitle = 0;
        ShowCommandKeyInTitle = 1;
        # ------ 窗口大小 -------
        columnCount = 200;
        rowCount = 200;

        # ---------- 标签页 ----------
        ShowRepresentedURLInTabTitle = 1;
        ShowRepresentedURLPathInTabTitle = 1;
        ShowActiveProcessInTabTitle = 1;
        ShowActiveProcessArgumentsInTabTitle = 1;
        ShowComponentsWhenTabHasCustomTitle = 0;
        ShowActivityIndicatorInTab = 1;
        
        # --------- Shell --------
        CommandString = "clear;";
        
        # 键盘
        ScrollAlternateScreen = 0;
    };
};
```