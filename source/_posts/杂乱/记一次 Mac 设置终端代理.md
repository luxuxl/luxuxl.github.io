> [Mac Terminal VPN：如何在“终端”设置网络代理？ - 知乎 (zhihu.com)](https://zhuanlan.zhihu.com/p/638495799)

该方法为临时设置终端为 Clash 代理

```bash
export httpproxy=http://localhost:7890
export httpsproxy=http://localhost:7890
export https_proxy=http://127.0.0.1:7890 http_proxy=http://127.0.0.1:7890 all_proxy=socks5://127.0.0.1:7890
```

取消代理

```bash
unset httpproxy
unset httpsproxy
```