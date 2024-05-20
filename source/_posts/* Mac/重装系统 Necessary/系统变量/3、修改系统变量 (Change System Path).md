注: 还需补充 Apple Script 修改方法, 似乎是系统级别的修改

## 修改颜色区分、HOME、PATH

为防止其他软件在 `HOME` 下写入大量隐藏文件夹, 修改 `$HOME` 变量, `.sogouinput` 暂时无解

```Shell
cd ~
mkdir .config
touch .zprofile
vim .zprofile
```

`.zprofile` 内容如下

```bash
# change color
export CLICOLOR=1
export LSCOLORS=exgxbxdxcxegedabagacad

# change home dir
HOME="${HOME}/.config"

# self variable
D="/Users/$USERNAME/Desktop"
N="/Users/$USERNAME/Library/Mobile Documents/iCloud~md~obsidian/Documents/Notes"
H="/Users/$USERNAME"

# add local bin
local="/usr/local/bin/"
export PATH="$local:$PATH"

# self path
pyvenv="/Users/luxury/Desktop/.code/python/project1/bin"
export PATH="$pyvenv:$PATH"
```

