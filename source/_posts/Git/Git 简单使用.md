> [HCLonely Blog - Git 免密、免 SSH 进行 push & pull](https://blog.hclonely.com/posts/8585e79a/)

以下都以 Gitee 为例, 因为 Github 无法用账号密码登录, 且即使挂了代理速度仍然不是很快

## 一、设置作者信息

在登录之前, 需要配置 git 的 `user.name` 和 `user.email`, 这是用于提交代码时, 显示的作者信息, 与**登录无关 ! ! !**, 但不设置无法提交

```
git config --global user.name "cs_your_username"
git config --global user.email "cs_your_email_its_optional"
```

`--global` 全局, 即表示对所有的仓库生效, 如果不加就是当前的仓库生效

此外, 我的 Gitee 并没有绑定邮箱 (毕竟瓷器有手机号就行了) , 但没有邮箱也会给你一个提交用的邮箱, 比如

![image](https://jsd.cdn.zzko.cn/gh/luxuxl/picx-images-hosting@master/20240215/image.9dcpyfxbq6.webp)

这个邮箱不需要去设置里找, Gitee 在仓库页面会帮你连命令一起生成, 如下

![image](https://jsd.cdn.zzko.cn/gh/luxuxl/picx-images-hosting@master/20240215/image.54xios33rj.webp)

## 二、登录验证

### 法 1、账号密码登录

顾名思义, 也就是用你的 Gitee/Github 账号和密码登录, 但这个方法在 Github 上已经禁用了 (因为不安全)

每次推送代码都会弹出 "Please input username", 然后手动输入账号密码, 很麻烦, 可以在临时电脑上这样弄, 因为我 Gitee 的用户名和密码都挺短的, 这样也算不上麻烦
##### 补充: 记住密码

可以修改配置通过一些凭据管理器, 比如 macOS 的 Keychain、Windows 的 Credential Manager 来储存账号密码, 就不需要每次推送都输入

但我的 mac 每次都会弹出找不到钥匙串, 我也不想弄了, 因为某次意外 (似乎是生成的密码过长溢出上限但 mac 仍然记录了完整的密码) 导致我再也不想使用此类软件

### 法 2、SSH 登录

首先要在你的电脑上生成一对 ssh 密钥, 命令如下

```
ssh-keygen -t rsa
```

然后去储存目录, 将公钥复制下来

```
cat ~/.ssh/id_rsa.pub
```

粘贴进去

![image](https://jsd.cdn.zzko.cn/gh/luxuxl/picx-images-hosting@master/20240215/image.2a4uiue4gq.webp)

然后就可以使用 ssh 协议进行 git 的各种操作了, 再也不需要密码了

此外, 如果你在生成 rsa 密钥时修改了储存位置, 那么则需要修改 `gitconfig` 或者 `sshconfig`, 否则会识别默认位置而失败

### 法 3、令牌登录

去个人设置里生成一个登录令牌, 如下图

![image](https://jsd.cdn.zzko.cn/gh/luxuxl/picx-images-hosting@master/20240215/image.77dbcuustw.webp)

名称随便填, 权限前两个就够了

![image](https://jsd.cdn.zzko.cn/gh/luxuxl/picx-images-hosting@master/20240215/image.7awxakr1zc.webp)

保存显示的令牌密钥

在 clone 时, 需要加上 `oauth2:令牌` 才可以免密操作, 比如

```
git clone https://oauth2:cs_令牌@gitee.com/cs_username/cs_repository
```

```
git config --global user.name 'Luxury'                                                                                 
git config --global user.email '13959213+luxuxl@user.noreply.gitee.com'
export GT="https://oauth2:eb64300fc378ed34341428d844923f85@gitee.com/luxuxl"
```
