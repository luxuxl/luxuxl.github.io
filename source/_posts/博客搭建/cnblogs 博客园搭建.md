# Awescnb 主题

> [安利几款好看的博客园主题 - CryFace - 博客园 (cnblogs.com)](https://www.cnblogs.com/CryFace/p/13508216.html)
> 
> [Awescnb 手册 | Awescnb (gitee.io)](https://guangzan.gitee.io/awescnb-docs/themes)
> 
> [Awescnb 配置选项 (yuque.com)](https://www.yuque.com/awescnb/user/rycpvv#cca02e3f)

## 代码高亮

- 显示行号
- Mac 风格
- 代码字体：Fira Code
- 主题：atom-one-dark

## 页面定制 CSS 代码

- [x] 禁用模板默认 CSS

```css
#loading {

    bottom: 0;

    left: 0;

    position: fixed;

    right: 0;

    top: 0;

    z-index: 9999;

    background-color: #f4f5f5;

    pointer-events: none;

}
.loader-inner {

    will-change: transform;

    width: 40px;

    height: 40px;

    position: absolute;

    top: 50%;

    left: 50%;

    margin: -20px 0 0 -20px;

    background-color: #3742fa;

    border-radius: 50%;

    animation: scaleout 0.6s infinite ease-in-out forwards;

    text-indent: -99999px;

    z-index: 999991;

}
@keyframes scaleout {

    0% {

        transform: scale(0);

        opacity: 0;

    }

    40% {

        opacity: 1;

    }

    100% {

        transform: scale(1);

        opacity: 0;

    }

}
```

## 页首 HTML 代码

```css
<div id="loading"><div class="loader-inner"></div></div>
```

## 页脚 HTML 代码

```css
<script src="https://blog-static.cnblogs.com/files/guangzan/loader.min.js"></script>
<script>
    const config = {
        darkMode: {
            enable: true,
            darkDefault: true,
            autoLight: false,
        },
        theme: {
            name: 'geek',
            color: '#c1a177',
            avatar: 'https://pic.cnblogs.com/avatar/3389865/20240207234337.png',
            headerBackground: 'https://images.cnblogs.com/cnblogs_com/blogs/816612/galleries/2377873/o_240212074031_headerBackground.png'
        },
        signature: {
            enable: true,
            contents: [
                "<i style='color:#dadcdd;font-size:20px;'>Planning to fly away,Let's start at the <i style='color:#eda5d3'>r</i><i style='color:#e9cdc9'>a</i><i style='color:#f8edd1'>i</i><i style='color:#d8e6d5'>n</i><i style='color:#a5e5f1'>b</i><i style='color:#99cdf2'>o</i><i style='color:#c4b9fe'>w</i>.</i>",
            ],
        },
        catalog: {
            enable: true,
            position: 'left'
        },
        bodyBackground: {
            enable: true,
            value:'https://images.cnblogs.com/cnblogs_com/blogs/816612/galleries/2377873/o_240213055439_bodyBackground3.png',
            opacity: 0.9,
            repeat: false,
        },
        github: {
            enable: false,
            url: 'https://github.com/luxuxl',
        },
        tools: {
            enable: false,
            initialOpen: false,
        },
        donation: {
            enable: true,
            qrcodes: ["https://images.cnblogs.com/cnblogs_com/blogs/816612/galleries/2377873/o_240209173123_receive.jpg"],
        },
    }
    $.awesCnb(config)
</script>
```
## 控件设置
![1708243049329](https://cdn.jsdelivr.net/gh/luxuxl/picx-images-hosting@master/20240218/1708243049329.webp)

# Sakura

> [博客园主题美化 最详细的美化过程 - CodeFan* - 博客园](https://www.cnblogs.com/cyy22321-blog/p/16048788.html)


# SimpleMemory

