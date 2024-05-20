## Install TPM(Tmux Plugins Manager)

```bash
git clone https://github.com/tmux-plugins/tpm ~/.tmux/plugins/tpm
```

```bash
vim ~/.tmux.conf
```

```bash
set -g @plugin 'tmux-plugins/tpm'
set -g @plugin 'tmux-plugins/tmux-sensible'

run '~/.tmux/plugins/tpm/tpm' 
```

## Install Other Plugins

After installing the TPM, you can use it to install other plugins

For example, add `set -g @plugin 'dracula/tmux'` to `~/.tmux.conf`

```bash
set -g @plugin 'tmux-plugins/tpm'
set -g @plugin 'tmux-plugins/tmux-sensible'

set -g @plugin 'dracula/tmux'           # A theme plugin

run '~/.tmux/plugins/tpm/tpm' 
```

Then Enter Tmux, it will update automatically
Or try to press `prefix + shift + i` to update plugins by yourself

## Recommend Plugins

> [简单而轻巧的Tmux插件扩展 | Escape](https://www.escapelife.site/posts/1a9a72ec.html#toc-heading-7)
> 
> [Tmux 终端复用器美化(2021/11/20) - Hit不死的小强 - 博客园](https://www.cnblogs.com/xiaoQQya/p/16313824.html#32-插件推荐)
> 
> [GitHub - gpakosz/.tmux: 🇫🇷 Oh my tmux! My self-contained, pretty & versatile tmux configuration made with ❤️](https://github.com/gpakosz/.tmux)
> 
> [提升 Tmux 状态栏颜值 - Linux - 大象笔记](https://www.sunzhongwei.com/enhance-tmux-status-bar-appearance?from=bottom)
> 
> [tmux外貌篇：让你的tmux更好看 | 卡瓦邦噶！](https://www.kawabangga.com/posts/2477)

### 







