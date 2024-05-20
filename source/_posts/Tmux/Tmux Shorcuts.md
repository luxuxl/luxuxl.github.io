# Tmux Shortcuts

> [Tmux 使用教程 - 阮一峰的网络日志](https://www.ruanyifeng.com/blog/2019/10/tmux.html)
> 
> [Tmux使用手册 | louis blog](http://louiszhai.github.io/2017/09/30/tmux/#新增面板)
> 
> [tmux disable confirmation prompt on kill-window - Unix & Linux Stack Exchange](https://unix.stackexchange.com/questions/30270/tmux-disable-confirmation-prompt-on-kill-window)
> 
> [tmux(1) - OpenBSD manual pages](https://man.openbsd.org/OpenBSD-current/man1/tmux.1)

## 会话管理

会话，类似于窗口，一个单独的进程，会话禁止嵌套会话，要创建新的会话首先要离开已有的会话

| 会话操作        | 自定义 | 命令                                             | 快捷键          |
| ----------- | --- | ---------------------------------------------- | ------------ |
| 新建会话，必须非会话中 |     | tmux new [-s <name>]                           |              |
| 暂离会话        |     | tmux detach                                    | ctrl + b + d |
| 连接上一个或指定会话  |     | tmux attach [-t <N>/<name>]                    |              |
| 关闭当前或指定会话   |     | tmux kill-session [-t <N>/<name>]              |              |
| 切换会话        |     | tmux switch -t <N>/<name>                      |              |
| 查看会话        |     | tmux ls                                        | ctrl + b + s |
| 重命名当前或指定会话  |     | tmux rename-session [-t <N>/<name>] <new-name> | ctrl + b + $ |

## 标签页 - window 管理

### 常用快捷键

| 标签页操作  | 自定义快捷键      | 快捷键         |
| ------ | ----------- | ----------- |
| 新建标签页  | prefix + c  | prefix + c  |
| 关闭标签页  | prefix + x  | prefix + &  |
| 上一个标签页 | prefix + ,  | prefix + p  |
| 下一个标签页 | prefix + .  | prefix + n  |
| 标签页列表  | prefix + l  | prefix + w  |
| 切换标签页  | prefix + 数字 | prefix + 数字 |

### 我的标签页管理

由于标签页的使用频率比窗格低, 创建就用默认的不太方便的 `prefix + c` 

关闭用边上的 `prefix + x` 

切换有三种选择
- 上、下标签页
- 标签页列表
- 数字

## 窗格 - pane 常用

### 常用快捷键

| 窗格操作        | 自定义后           | 快捷键                   |
| ----------- | -------------- | --------------------- |
| 上下分割        | prefix + -     | prefix + "            |
| 左右分割        | prefix + \     | prefix + %            |
| 关闭窗格        | prefix + w     | prefix + x            |
| 显示编号并通过编号跳转 | prefix + q     | prefix + q            |
| 最大化面板       | prefix + space | prefix + z            |
| 均分面板        |                | prefix + E            |
| 新窗口中打开      |                | prefix + !            |
| 移动光标        |                | prefix + <方向键>        |
| 调整大小        |                | prefix + ctrl + <方向键> |

### 我的窗格管理

prefix 为 `option + =` , 可以很方便地按到 `-` , `\` , 进行窗格分割

关闭窗格改成 `prefix + w`

窗格跳转使用 `prefix + q` + 数字, 可以快速定位并省下 `wsad` 的位置

全屏则利用 `prefix + space`

至此, 窗格管理右手负责按 `prefix`, 左手只需要按 `q, w, e, 数字, space` 键

## 其他

### 快捷键

| 窗格操作   |     | 快捷键        | 命令  |
| ------ | --- | ---------- | --- |
| 帮助文档   |     | prefix + ? |     |
| 查询某个命令 |     | prefix + / |     |
| 进入命令模式 |     | prefix + : |     |
| 进入复制模式 |     | prefix + [ |     |
| 粘贴文本   |     | prefix + ] |     |
