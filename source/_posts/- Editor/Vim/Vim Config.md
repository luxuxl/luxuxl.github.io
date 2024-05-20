## 基础配置

```bash
curl -fLo ~/.vim/autoload/plug.vim --create-dirs https://raw.githubusercontent.com/luxuxl/vim-plug/master/plug.vim
```

```vb
" ----- 1、插件及插件配置 -----
call plug#begin()
Plug 'preservim/nerdtree'
Plug 'luxuxl/vim-popup'
Plug 'luxuxl/vim-statusbar'
Plug 'jiangmiao/auto-pairs'
Plug 'luxuxl/vim-rainbow'
call plug#end()

set cpt=.,k,w,b 
set completeopt=menuone,noselect

" ----- 2、基础设置 -----
" autocmd FileType * setlocal formatoptions-=c formatoptions -=r formatoptions-=o
" autocmd FileType * setlocal formatoptions -=o
set timeoutlen=160
set virtualedit=onemore                 " 可以移到最后一个字符
set encoding=utf8
set shortmess+=c
set noswapfile
set nu rnu
set autoindent
set shiftwidth=4
set tabstop=4
set laststatus=2
set showtabline=2
set cmdheight=2
set syntax=on                           " 语法高亮
set hlsearch                            " 搜索结果高亮
set fillchars=vert:┇
set fillchars+=eob:\ 
"█▉▊▋▌▍▎▏┃│┇】█▌▍▎▏"

" ----- 编辑、自动保存 -----
autocmd TextChanged,TextChangedI * silent update
autocmd FocusGained * if &buftype== 'terminal' | :cd - | endif
autocmd BufLeave * if &buftype=='terminal' | :q | endif

noremap <Cr> o
noremap qq :q!<Cr>
nmap x d
noremap D d
noremap <C-Left> <Esc>I
noremap <C-Right> <Esc>A
noremap rr <Esc>:cd %:p:h<Cr>:term make p=%:p:h<Cr>
inoremap <Tab> <C-t>
inoremap <S-Tab> <C-d>
inoremap <C-Left> <Esc>I
inoremap <C-Right> <Esc>A
inoremap qq <Esc>


" vim-popup会覆盖, 所以得在 popup 里修改

" ------ 禁用 --------
noremap s <Nop>
noremap r <Nop>
noremap q <Nop>
noremap d <Nop>
map <C-w> <Nop>

" nerdtree 优化
map \\ :NERDTreeToggle<CR>I
autocmd BufEnter * stopinsert
autocmd TabEnter * if &buftype == 'nofile' | wincmd w | endif
let g:NERDTreeWinSize = 20
let g:NERDTreeMapChangeRoot="i"

let g:NERDTreeMapJumpFirstChild=0
let g:NERDTreeMapJumpLastChild=0

" 新/标签页管理和窗口管理 "
noremap H :wincmd W<Cr>
noremap L :wincmd w<Cr>
noremap J :tabp<Cr>
noremap K :tabn<Cr>
noremap T :tabnew<Cr>
noremap Z <C-z>

" 美化, 防止 comment 被 ANSI 覆盖
set background=light
hi Comment cterm=underline ctermfg=245
" 当前行, 为了高亮行号 "
set cursorline
hi clear CursorLine
hi CursorLine cterm=none ctermbg=245

" 行号 "
hi LineNr ctermfg=240
hi CursorLineNr cterm=bold ctermfg=215

" 标签页栏 "
hi clear TabLineFill
hi TabLineSel cterm=none ctermfg=231 ctermbg=39
hi TabLine cterm=none ctermfg=255 ctermbg=none

" 面板分隔 "
hi clear VertSplit









" ----- 备选 ----- "

" 标签页管理
noremap <C-j> gT
noremap <C-t> :tabnew<Cr>
noremap <C-k> gt
inoremap <C-j> <Esc>gT
inoremap <C-k> <Esc>gt
inoremap <C-t> <Esc>:tabnew<Cr>

" 窗口管理
noremap <C-h> <Esc><C-w>W
noremap <C-l> <Esc><C-w>w
noremap <C-f> <Esc><C-z>
" 该选项无效, 会触发 Mac 自带的删除功能 "
inoremap <C-h> <Esc><C-w>W
inoremap <C-l> <Esc><C-w>w
inoremap <C-f> <Esc><C-z>

" 二、habamax 颜色太淡了 "
colorscheme habamax
set cursorline
hi clear CursorLine
hi CursorLine ctermbg=242 guibg=#404040
hi clear TabLineFill
hi TabLine cterm=none ctermfg=white ctermbg=none gui=None guifg=white guibg=none
hi TabLineSel ctermfg=0 ctermbg=lightgreen guifg=black guibg=lightgreen
hi clear VertSplit

" 三、slate 勉强把"

" N、终端 ANSI 配色, 终端会用自己的配色覆盖 vim 配色, Comment 颜色要在终端修改 "
hi LineNr ctermfg=240
hi CursorLineNr cterm=bold ctermfg=215

set cursorline
hi CursorLine cterm=none ctermbg=250

hi clear TabLineFill
hi TabLineSel ctermfg=255 ctermbg=39 guifg=#ffffff guibg=#4fb4d8
hi TabLine cterm=none ctermfg=255 ctermbg=none

hi clear VertSplit

" ----- 待定 ----- "
nnoremap <C-w> <Up>
nnoremap <C-s> <Down>
nnoremap <C-a> <Left>
nnoremap <C-d> <Right>
```

## 未整理

```vb
" ----- plugins ----- "
call plug#begin()
Plug 'preservim/nerdtree'
Plug 'luxuxl/vim-popup'
Plug 'luxuxl/vim-statusbar'
Plug 'jiangmiao/auto-pairs'
Plug 'luochen1990/rainbow'
call plug#end()

map <C-\> :NERDTreeToggle<CR>I
let g:NERDTreeMapUpdir = "<C-q>"
let g:NERDTreeMapChangeRoot = "<C-e>"

set cpt=.,k,w,b    " 从字典文件以及当前打开的文件里收集补全单词 
set completeopt=menuone,noselect   " 不自动选择 "
set shortmess+=c   " dont know 禁止在下方显示一些啰嗦的提示 "

let g:rainbow_active = 1           " enable rainbow "

set encoding=utf-8                       " 编码设置,似乎可以防止 replace 模式?

set termencoding=utf-8
set fileformats=unix                            " 此三行设置默认非 replace 模式
set encoding=prc

set shiftwidth=4                         " #?设定自动缩进为4个字符
set splitright                           " #?设置左右分割窗口时，新窗口出现在右侧
set splitbelow                           " #?设置水平分割窗口时，新窗口出现在底部

set virtualedit=onemore                           " 所有空字符可编辑
set syntax=on                                   " 语法高亮
set rnu                                         " 设置相对行号
set tabstop=4                            " tab缩进为 4
set expandtab                            " 用 space 替代 tab

" ----- mode switch smooth -----
noremap <Backspace> Xi
noremap <Cr> o
cnoremap Q q
cnoremap W w

" ----- Alternative -----
" command mode > normal mode > insert mode
noremap <C-e> i 
inoremap <C-q> <Esc><Right>
noremap <C-q> :
cnoremap <C-q> <Esc>

" ----- Normal Mode -----
" move
nnoremap <C-w> <Up>
nnoremap <C-s> <Down>
nnoremap <C-a> <Left>
nnoremap <C-d> <Right>

" ----- Insert Mode -----
" move
inoremap <C-w> <Up>
inoremap <C-s> <Down>
inoremap <C-a> <Left>
inoremap <C-d> <Right>

" dont use

" custom
inoremap <Tab> <C-t>
inoremap <S-Tab> <C-d>

" ----- windows shortcuts -----
noremap <C-h> <C-w>W           
" control + h/j 上/下一个窗格
noremap <C-l> <C-w>w
```

