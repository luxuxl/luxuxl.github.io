> [VIM学习笔记 自动命令-实例(autocmd-examples) - 知乎](https://zhuanlan.zhihu.com/p/98966660#:~:text=例如以下自动命令，将删除php文件行尾的空格：%20autocmd%20BufEnter%20%2A.php%20%3A%25s%2F%5B%20tr%5D%2B%24%2F%2Fe,可以根据文件类型，载入相关插件：%20autocmd%20Filetype%20html%2Cxml%2Cxsl%20source%20%24VIM%2Fvimfile%2Fplugin%2Fclosetag.vim)
> 
> [VIM学习笔记 自动命令(autocmd) - 知乎](https://zhuanlan.zhihu.com/p/98360630)

简单写一个执行完终端命令后, 自动判断是否为 Terminal, 是则退出

```
autocmd BufEnter,WinEnter,FocusGained * if &buftype=='terminal' | :q! | :wincmd p | endif
```

```
autocmd BufLeave * if &buftype=='terminal' | :q | endif
```

```
autocmd BufEnter,FocusGained * if &buftype== 'terminal' | noremap <Esc><Esc> :q!<Cr> | endif
```

