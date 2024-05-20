> [hexo+gitee(码云)搭建个人博客避开所有坑_hexo搭建博客优缺点-CSDN博客](https://blog.csdn.net/weixin_45631738/article/details/104716374)
> 
> [文档 | Hexo](https://hexo.io/zh-cn/docs/)
> 
> [Hexo功能增强插件 - 西西弗苏 - SegmentFault 思否](https://segmentfault.com/a/1190000018402194)

## 配置 Hexo

终端运行

```bash
npm install -g hexo-cli
hexo init cs_blog_folder
cd cs_blog_folder # 必须要 cd ，因为插件要安装在这里
# enhancer 可以为子文件夹生成
npm install hexo-enhancer --save
```

修改`_config.yml`

```css
permalink: /:abbrlink.html
```

## 部署

git clone 远程仓库

将之前的 `cs_blog_folder` 内所有文件移动到\仓库中, 因为有 `.gitignore` 文件

```
cp -r cs_blog_folder/* cs_your_respository
cp -r cs_blog_folder/.* cs_your_respository
```

删除 `.gitignore` 的 `public`

修改 `_config.yaml`

```python
url:  https://luxuxl.gitee.io/public
# 注意, root 必填, 否则样式无法生效
root: /
```

## 主题安装及配置

>[Hexo 10款好看的主题｜新手建站必备！ | 李小沐 (lixiaomu.fun)](https://blog.lixiaomu.fun/posts/43857/)
> 
> [Themes | Hexo](https://hexo.io/themes/)

### 安装&配置 volantis 主题

> [开始使用 - Volantis](https://volantis.js.org/v6/getting-started/)

1. 在`blog/_config.yml`文件中找到并修改
```nasm
theme: volantis
```

2. 在终端中输入
```bash
cd cs_blog_folder
npm i hexo-theme-volantis
```

打开 `blog/_config.volantis.yml`, 配置主题

```
############################### Cover ############################### > start

cover:
  height_scheme: full # full, half 
  layout_scheme: search # blank (留白), search (搜索), dock (坞), featured (精选), focus (焦点)
  display:
    home: true
    archive: false
    others: false
  search: Search...
  features: 

############################### Cover ############################### > end

############################### Navigation Bar ############################### > start

# 注意事项：建议规范全站路径 URL 最后带一个 "/" 例如 "about/"
navbar:
  visiable: auto # always, auto
  logo: # choose [img] or [icon + title]
    img: 
    icon:
    title: Luxury
  menu:
    - name: 首页
      icon: fa-solid fa-rss
      url: /
    - name: 分类
      icon: fa-solid fa-folder-open
      url: categories/
      search: Search...   # Search bar placeholder

custom_css:
  navbar:
    height: 64px
    width: max # auto, max
    effect: [shadow] # [shadow, floatable, blur]
    
############################### Navigation Bar ############################### > end

############################### Sidebar ############################### > start
sidebar:
  position: right # left right 侧边栏的位置
  
  for_page: [blogger, category] # 主页、分类、归档等独立页面的组件
  
  for_post: [toc] # docs/post 这类文章页面
  # 侧边栏组件库
  widget_library:
    blogger:
      class: blogger
      display: [desktop] # [desktop, mobile]
      avatar: https://cdn.jsdelivr.net/gh/luxuxl/picx-images-hosting@master/20231218/avatar.webp
      title:
      subtitle:
      jinrishici: true # Poetry Today. You can set a string, and it will be displayed when loading fails.
      social: false
  
############################### Sidebar ############################### > end


############################### Site Footer ############################### > start

site_footer:
  # layout of footer: [aplayer, social, license, info, copyright]
  layout: [aplayer]
  
############################### Site Footer ############################### > end

############################### Plugins ############################### > start

plugins:
  # APlayer is only available in mainland China.
  aplayer:
    enable: true
    # Required
    server: netease   # netease, tencent, kugou, xiami, baidu
    type: playlist    # song, playlist, album, search, artist
    id: 411796573    # song id / playlist id / album id / search keyword
    # Optional
    fixed: false      # enable fixed mode
    theme: '#D23A32'  # main color
    autoplay: false   # audio autoplay
    order: list       # player play order, values: 'list', 'random'
    loop: all         # player loop play, values: 'all', 'one', 'none'
    volume: 0.5       # default volume, notice that player will remember user setting
    list_max_height: 320px # list max height
    list_folded: true
    autoHide: true    # hide automaticaly
  darkmode:
    enable: true

############################### Plugins ############################### > end
```

### 安装&配置 Butterfly 主题

> [Butterfly 安裝文檔(一) 快速開始 | Butterfly](https://butterfly.js.org/posts/21cfbf15/)

1. 在`blog/_config.yml`文件中找到并修改

```nasm
theme: butterfly
```

2. 在终端中输入
```bash
npm install hexo-theme-butterfly
```

### 安装&配置 Fluid 主题

> [开始使用 | Hexo Fluid 用户手册 (fluid-dev.com)](https://hexo.fluid-dev.com/docs/start/)

1. 在`blog/_config.yml`文件中找到并修改

```nasm
theme: fluid
```

2. 在终端中输入
```bash
npm install hexo-theme-fluid
```

### 安装&配置 Shoka 主题


### 安装&配置 Sakura 主题





