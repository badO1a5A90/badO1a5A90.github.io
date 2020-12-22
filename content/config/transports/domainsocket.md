---
date: "2020-08-20T16:42:11.812Z"
description: Project X 的文档.
title: Domain Socket
weight: 3
---

{{% notice danger important %}}
推荐写到 [inbounds](../../inbounds) 的 `listen` 处，传输方式可选 TCP、WebSocket、HTTP/2.<br />
未来这里的 DomainSocket 可能会被弃用。
{{% /notice %}}

Domain Socket 使用标准的 Unix domain socket 来传输数据。

它的优势是使用了操作系统内建的传输通道，而不会占用网络缓存。
理论上相比起本地环回网络（local loopback）来说，Domain socket 速度略快一些。

目前仅可用于支持 Unix domain socket 的平台，如 Linux 和 macOS。在 Windows 10 Build 17036 前不可用。

如果指定了 domain socket 作为传输方式，在入站出站代理中配置的端口和 IP 地址将会失效，所有的传输由 domain socket 取代。

## DomainSocketObject

---

`DomainSocketObject` 对应传输配置的 `dsSettings` 项。

```json
{
  "path": "/path/to/ds/file",
  "abstract": false,
  "padding": false
}
```

{{% notice dark %}} `path`: string{{% /notice %}}

一个合法的文件路径。
{{% notice danger important %}}
在运行 Xray 之前，这个文件必须不存在。
{{% /notice %}}

{{% notice dark %}} `abstract`: true | false{{% /notice %}}

是否为 abstract domain socket，默认值 `false`。

{{% notice dark %}} `padding`: true | false{{% /notice %}}
abstract domain socket 是否带 padding，默认值 `false`。
