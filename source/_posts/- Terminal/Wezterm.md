# Install

### Method 1

```bash
sudo port install wezterm
```

# Configure

> [我用WezTerm替代了kitty\_哔哩哔哩\_bilibili](https://www.bilibili.com/video/BV1m94y1T7aL/?spm_id_from=333.999.0.0&vd_source=b71fdb57a495d5345dbde99cbbeb52ac)

```bash
cd ~
mkdir wezterm
cd wezterm
vim .wezterm.lua
```

```lua
local wezterm = require("wezterm")
local config = {
        font_size = 28,
        font = wezterm.font("Monaco", { weight = "Regular"}),
        color_scheme = "Catppuccin Mocha",

        use_fancy_tab_bar = false,
        hide_tab_bar_if_only_one_tab = true,
        window_decorations = "RESIZE",
        show_new_tab_button_in_tab_bar = false,
        window_background_opacity = 0.9,
        macos_window_background_blur = 70,
        text_background_opacity = 0.9,
        adjust_window_size_when_changing_font_size = false,
        window_padding = {
                left = 20,
                right = 20,
                top = 20,
                bottom = 5,
        },
}
return config
```