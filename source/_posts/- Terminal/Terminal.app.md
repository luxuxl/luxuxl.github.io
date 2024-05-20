# 修改提示符

## 介绍

`PS1` 是一个环境变量，用于定义终端提示符（Prompt String 1）的格式和内容

可以在终端 → Shell → 启动处修改启动命令, 如下所示

但是在 `.zprofile` 里修改不生效

![image](https://jsd.cdn.zzko.cn/gh/luxuxl/picx-images-hosting@master/20240215/image.99t3srdqpn.webp)

## 变量解释

默认的环境变量 `$PS1` 值为 `"%n@%m %1~ %#"`, 如果想要让他们变色, 将在美化中介绍

下面解释含义
- `%n`：当前用户的用户名
- `%m`：当前计算机的主机名
- `%1`：当前文件夹名称
- `%~`：当前工作目录的简化形式, 似乎同 `%d`
- `%d`：当前工作目录的完整路径
- `%h`：未知
- `%t`：当前时间, 12小时
- `%T`：当前时间, 24小时
- `%w`：星期 和 日期
- `%W`：年 月 日

## 实例

##### 1、显示固定字符

```
PS1="~/"; clear;
```

##### 2、显示当前文件夹名称

当然, 你也可以在后面添加以下固定字符

```
PS1="%1~ ";clear;
```

##### 3、显示当前路径

```
PS1="%d ➤ ";clear;
```

## 进阶

其实就是上面一节基础上修改了颜色
- `%F`: 前景色, 即字体颜色
- `%K`: 背景色
- `%k`: 还原前景色
- `%k`: 还原背景色

```
PS1="%F{white}%K{blue}%d%F{blue}%k ➤ %f%k";clear;cd $D;
# optional symbol ▶ ➥ ➨ ➧➽ ➜ ⮕
```

# 修改文件颜色

默认的终端不区分各种文件的颜色, 可以在 `.zprofile` 里设置

```
export CLICOLOR=1
export LSCOLORS=Cxgxbxdxcxegedabagacad
```

这边具体解析一下 `LSCOLORS`

每两个字母为一组, 可以分成 11 组 (可以数一数), 然后每组分别表示  (此处不影响 Vim 颜色)
1. 文件夹 - 蓝色 e
2. 软链, symbolic link - 青色 g
3. socket, 未知
4. pipe, 未知
5. 可执行文件 - 绿色 c
6. block special, 未知
7. character special, 未知
8. executable with setuid bit set, 未知
9. executable without setgid bit set , 未知
10. directory writable to others, with sticky bit , 未知
11. directory writable to others, without sticky bit, 未知

再来介绍颜色字母, x 为默认色彩
![image](https://jsd.cdn.zzko.cn/gh/luxuxl/picx-images-hosting@master/20240215/image.wibjkc5l9.webp)

比如第一组是 `ex`, 则表示文件夹的前景色为 `e` 蓝色, 背景色为 `x` 无
















