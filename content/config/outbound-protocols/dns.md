---
date: "2020-08-20T16:42:11.812Z"
description: Getting started
title: DNS
weight: 2
---

DNS 是一个出站协议，主要用于拦截和转发 DNS 查询。

此出站协议只能接收 DNS 流量（包含基于 UDP 和 TCP 协议的查询），其它类型的流量会导致错误。

在处理 DNS 查询时，此出站协议会将 IP 查询（即 A 和 AAAA）转发给内置的 [DNS 服务器](../../dns)。其它类型的查询流量将被转发至它们原本的目标地址。

## OutboundConfigurationObject

---

```json
{
  "network": "tcp",
  "address": "1.1.1.1",
  "port": 53
}
```

{{% notice dark %}} `network`: "tcp" | "udp"{{% /notice %}}

修改 DNS 流量的传输层协议，可选的值有 `"tcp"` 和 `"udp"`。当不指定时，保持来源的传输方式不变。

{{% notice dark %}} `address`: address{{% /notice %}}

修改 DNS 服务器地址。当不指定时，保持来源中指定的地址不变。

{{% notice dark %}} `port`: number{{% /notice %}}

修改 DNS 服务器端口。当不指定时，保持来源中指定的端口不变。

<br />

## DNS配置实例
---

{{% badge warning %}}In progress{{% /badge %}}
