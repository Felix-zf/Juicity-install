# juicity-script

Juicity 协议一键部署脚本

## 一键脚本地址
📦 1. test
```shell
wget -N https://raw.githubusercontent.com/Felix-zf/Juicity-Scripts/main/juicity.sh && bash juicity.sh
```
📦 2. modify
```
bash <(curl -fsSL https://raw.githubusercontent.com/Felix-zf/Juicity-Scripts/main/juicity-installer.sh)
```
## 协议介绍
  Juicity 协议是一个开源的网络代理协议，作者在开发 Juicity 协议时受到了 TUIC 的启发。Juicity、TUIC、Hysteria 协议一样，均基于 QUIC（Quick UDP Internet Connections）协议实现。QUIC 是一个由 Google 开发的基于 UDP 的传输层网络协议，旨在减少连接和传输延迟。Juicity 与 Hysteria 不同之处主要为使用的拥塞算法，Juicity 可以使用的拥塞算法包括 reno、cubic、bbr 和 bbr2 ，而 hysteria 可以使用 brutal 拥塞算法。 brutal 拥塞算法表现的更为霸道与暴力，因此在网络链路不好的情况下，Hysteria 协议比 Juicity 协议的传输速度要快一些。

  正因为 hysteria 协议使用了 brutal 拥塞算法，可能会被 IDC 提供商误认为服务器在对外进行 DDOS 攻击，从而关停服务器。说明一下，我不是在黑 hysteria ，我目前主线路使用的也是 hysteria 协议，我想表达的是根据情况来选择合适的协议，例如在甲骨文云、谷歌云上可以使用同样基于 QUIC 的 Juicity 协议，以避免被封号的风险。

## 客户端配置
1、根据客户端操作系统，下载对应的 Juicity 客户端，以 64 位 windows 操作系统，V2rayN 为例。
- 在官方网站下载 juicity-windows-x86_64.zip，解压后将 juicity-client.exe 文件 copy 到 v2rayN 安装目录 \bin\juicity 目录中。 如果 bin 目录中没有 juicity 文件夹，请自行创建。
- Juicity 客户端：https://github.com/juicity/juicity/releases/latest

2、v2rayN 客户端配置，点击菜单上“服务器”中的“添加自定义服务器”。

3、导入上一步配置好的 client.json 文件， Core 类型选择 juicity ，socks 端口填写上一步设置的监听端口后点确定按钮。

4、苹果手机 Shadowrocket 客户端配置，类型选择 juicity ,分别填入地址、端口、UUID、密码、SIN后保存。

juicity 协议的链接地址格式为：
```
juicity://uuid:password@example.domain.com:port?congestion_control=bbr&sni=example.domain.com&allow_insecure=0&pinned_certchain_sha256=CERT_HASH
```

## 感谢
- Juicity协议：https://github.com/juicity/juicity
- HiFeng's Juicity协议手动安装教程: https://www.hicairo.com/post/74.html
- deathline94'PJ: https://github.com/deathline94/Juicity-Installer
