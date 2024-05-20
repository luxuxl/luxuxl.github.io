# Version One
## 简洁

```bash
# ------ Basic Config ------
set -g base-index 1 # 设置标签页的起始下标为1
set -g pane-base-index 1 # 设置窗格的起始下标为1
set -g renumber-windows on # 连续编号
set -g default-terminal 'screen-256color'

# ------ Shortcuts ------
unbind C-b # 解绑默认 prefix
set -g prefix '≠' # option + = 为 prefix

# ------ Pane Control ------
unbind '"'
bind '-' splitw -v -c '#{pane_current_path}' # - 上下分割
unbind %
bind '\' splitw -h -c '#{pane_current_path}' # \ 左右分割

unbind w
bind w kill-pane

bind Space resize-pane -Z

# ------ Window Control ------

unbind x
bind x kill-window

unbind ,
bind , last-window

unbind .
bind . next-window

unbind l
bind l list-windows
```

## 基础插件

## 美化插件

```bash
# ----- Plugins -----
set -g @plugin 'tmux-plugins/tpm'
set -g @plugin 'tmux-plugins/tmux-sensible'

set -g @plugin 'dracula/tmux'           # A theme plugin

run '~/.tmux/plugins/tpm/tpm' 
```


# Version Two

## 插件

```bash
# ----- Plugins -----
set -g @plugin 'tmux-plugins/tpm'
set -g @plugin 'tmux-plugins/tmux-sensible'

set -g @plugin 'dracula/tmux'           # A theme plugin

run '~/.tmux/plugins/tpm/tpm' 

# ------ Basic Config ------
set -g base-index 1 # 设置标签页的起始下标为1
set -g pane-base-index 1 # 设置窗格的起始下标为1
set -g renumber-windows on # 连续编号
set -g default-terminal 'tmux-256color'

# set -g automatic-rename off # 关闭 rename 机制

# ------ Shortcuts ------
unbind C-b # 解绑默认 prefix
set -g prefix '÷' # option + / 为 prefix

# ------ pane control ------
unbind '"'
bind '-' splitw -v -c '#{pane_current_path}' # - 上下分割
unbind %
bind '\' splitw -h -c '#{pane_current_path}' # \ 左右分割

bind -r w select-pane -U # 绑定 prefix + w为↑，-r表示可重复按键，大概500ms之内
bind -r s select-pane -D # 绑定 prefix + s为↓
bind -r a select-pane -L # 绑定 prefix + a为←
bind -r d select-pane -R # 绑定 prefix + d为→

bind -r W resizep -U 10 # 绑定 prefix + W 往↑调整面板边缘10个单元格
bind -r S resizep -D 10 # 绑定 prefix + S 为往↓调整面板边缘10个单元格
bind -r A resizep -L 10 # 绑定 prefix + A 为往←调整面板边缘10个单元格
bind -r D resizep -R 10 # 绑定 prefix + D 为往→调整面板边缘10个单元格
```