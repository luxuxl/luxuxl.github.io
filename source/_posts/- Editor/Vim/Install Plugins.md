## Install Vim-plug

Vim-plug is a vim plugins manager, use it to easily install plugins
#### Method 1
```bash
curl -fLo ~/.vim/autoload/plug.vim --create-dirs \
    https://raw.githubusercontent.com/junegunn/vim-plug/master/plug.vim
```

#### Method 2

Save this file [plug.vim](https://raw.githubusercontent.com/junegunn/vim-plug/master/plug.vim) to `~/.vim/autoload/`

#### The use of Vim-plug

```vb
:PlugInstall " 安装 vimrc 中的插件 "
:PlugInstall cs_plugin_name " 安装指定的插件 "
:PlugStatus " 查看已安装的插件 "
:PlugClean " 卸载插件 "
:PlugUpgrade " 更新 Vim-plug "
```

## Install Other Plugins

Use Vim-plug to install other plugins, add this to head of `.vimrc`

```vb
call plug#begin()
Plug 'cs_wanted_plugins'
call plug#end()
```

Then open vim,enter the command mode,input `PlugInstall` to install

## Recommend Plugins

> [多语言编程必备的十大 Vim 插件 - 知乎](https://zhuanlan.zhihu.com/p/95596162)
> 
> [打造余杭区最好用的 VIM/NVIM 自动补全插件 - 知乎](https://zhuanlan.zhihu.com/p/366496399)
> 
> [Vim2021：超轻量级代码补全系统 - 知乎](https://zhuanlan.zhihu.com/p/349271041)
> 
> [VIM学习笔记 插件(Plugin)](http://yyq123.github.io/learn-vim/learn-vim-plugin.html)
> 
> [Vim Awesome](https://vimawesome.com)
> 
> [colorswat.ch/vim](https://colorswat.ch/vim/list?cat=all)

```vb
call plug#begin()
Plug 'preservim/nerdtree'
Plug 'skywind3000/vim-auto-popmenu'
Plug 'itchyny/lightline.vim'
Plug 'jiangmiao/auto-pairs'
Plug 'luochen1990/rainbow'
call plug#end()
```

### NERDTree

> [vim - How can I keep my custom keybindings with NERDTree? - Stack Overflow](https://stackoverflow.com/questions/44988549/how-can-i-keep-my-custom-keybindings-with-nerdtree)

功能: 侧边显示文件树

显示帮助: `:help NERDTreeMappings` / [Github NerdTree 文档](https://github.com/preservim/nerdtree/blob/master/doc/NERDTree.txt)

These are some usual shortcuts:
- `u`: Back to last level folder
- `C`: Enter current folder
- `o`: Open the file in a new buffer or open/close directory
- `t`: Open the selected file in a new tab
- `i`: Open the selected file in a horizontal split window
- `s`: Open the selected file in a vertical split window
- `I`: Toggle hidden files
- `m`: Show the NERD Tree menu
- `R`: Refresh the tree, useful if files change outside of Vim
- `?`: Toggle NERD Tree's quick help

### auto-popmenu

### lightline

### auto-pairs

### rainbow






