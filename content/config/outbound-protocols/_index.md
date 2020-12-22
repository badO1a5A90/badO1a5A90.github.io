---
alwaysopen: false
date: "2020-08-20T16:42:11.812Z"
description: Getting started
# head: <hr/>
hide:
- toc
# post: "&nbsp;\U0001F44B"
title: ounbound可用协议列表
weight: 6
---

{{% alert theme="warning" %}}**这个章节包含了目前所有可用于outbound的协议及具体配置细节.**{{% /alert %}}

## 协议列表
---
{{% notice dark %}}[blackhole](./blackhole){{% /notice %}}
Blackhole（黑洞）是一个出站数据协议，它会阻碍所有数据的出站，配合 [路由（Routing）](../routing) 一起使用，可以达到禁止访问某些网站的效果。
{{% notice dark %}}[dns](./dns){{% /notice %}}
DNS 是一个出站协议，主要用于拦截和转发 DNS 查询。此出站协议只能接收 DNS 流量（包含基于 UDP 和 TCP 协议的查询），其它类型的流量会导致错误。
{{% notice dark %}}[freedom](./freedom){{% /notice %}}
Freedom 是一个出站协议，可以用来向任意网络发送（正常的） TCP 或 UDP 数据。
{{% notice dark %}}[http](./http){{% /notice %}}
HTTP 协议
{{% notice dark %}}[socks](./socks){{% /notice %}}
标准 Socks 协议实现，兼容 [Socks 4](http://ftp.icm.edu.pl/packages/socks/socks4/SOCKS4.protocol)、Socks 4a 和 [Socks 5](http://ftp.icm.edu.pl/packages/socks/socks4/SOCKS4.protocol)。
{{% notice dark %}}[vless](./vless){{% /notice %}}
VLESS 是一个无状态的轻量传输协议，可以作为 Xray 客户端和服务器之间的桥梁。
{{% notice dark %}}[vmess](./vmess){{% /notice %}}
[VMess](../../developer/protocols/vmess.md) 是一个加密传输协议，可以作为 Xray 客户端和服务器之间的桥梁。
{{% notice dark %}}[trojan](./trojan){{% /notice %}}
[Trojan](https://trojan-gfw.github.io/trojan/protocol)协议
{{% notice dark %}}[shadowsocks](./shadowsocks){{% /notice %}}
[Shadowsocks](https://zh.wikipedia.org/wiki/Shadowsocks) 协议。
