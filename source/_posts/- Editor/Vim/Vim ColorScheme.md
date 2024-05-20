## Vim 配色方案

### vim 显示当前配色方案

```
:hi
```

### vim 默认配色方案

vim 默认配色方案 colorscheme default, 但是, 

由于终端会用自己的 ANSI 颜色将其覆盖

所以在 `vimrc` 中声明 default 才可以重新恢复默认配色

但是不建议调整终端颜色来改变 vim 配色, 因为终端多个内容是同一个颜色 

### cterm256 色 

Mac 默认终端支持 256 色, 256 颜色表查询: [256 Colors - Cheat Sheet - Xterm, HEX, RGB, HSL | DITig](https://www.ditig.com/publications/256-colors-cheat-sheet)
### 内置方案一览

set background=light
set background=dark

colorscheme 

evening

![[Pasted image 20240323203135.png]]

habamax

![[Pasted image 20240323203155.png]]

industry

![[Pasted image 20240323203220.png]]

koehler

![[Pasted image 20240323203245.png]]

![[Pasted image 20240323203313.png]]

![[Pasted image 20240323203337.png]]
![[Pasted image 20240323203404.png]]
![[Pasted image 20240323203422.png]]
![[Pasted image 20240323203453.png]]
![[Pasted image 20240323203524.png]]

colorscheme