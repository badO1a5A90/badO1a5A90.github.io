---
date: "2020-08-20T16:42:11.812Z"
description: Project X 的文档.
title: 统计信息
weight: 9
---

用于配置 Xray 流量数据的统计。

## StatsObject

`StatsObject` 对应配置文件的 `stats` 项。

```json
{
  "stats": {}
}
```

目前统计信息不需要任何参数，只要 `StatsObject` 项存在，内部的统计即会开启。

开启了统计以后, 只需在 [Policy](../policy) 中开启对应的项，就可以统计对应的数据。

<br />
## 获取统计信息
---
可以用 `xray api` 的相关命令获取统计信息.

目前已有的统计信息如下：

- 用户数据

  - `user>>>[email]>>>traffic>>>uplink`

    特定用户的上行流量，单位字节。

  - `user>>>[email]>>>traffic>>>downlink` 

    特定用户的下行流量，单位字节。

  {{% notice info %}}
  **TIP**\
  如果对应用户没有指定 Email，则不会开启统计。
  {{% /notice %}}


- 全局数据

  - `inbound>>>[tag]>>>traffic>>>uplink`

    特定inbound的上行流量，单位字节。

  - `inbound>>>[tag]>>>traffic>>>downlink`

    特定inbound的下行流量，单位字节。

  - `outbound>>>[tag]>>>traffic>>>uplink`

    特定outbound的上行流量，单位字节。

  - `outbound>>>[tag]>>>traffic>>>downlink`

    特定outbound的下行流量，单位字节。
