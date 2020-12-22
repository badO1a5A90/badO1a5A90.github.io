---
date: "2020-08-20T16:42:11.812Z"
description: Getting started
title: 本地策略
weight: 5
---

本地策略，可以设置不同的用户等级和对应的策略设置，比如连接超时设置。Xray 处理的每一个连接都对应一个用户，按照用户的等级（level）应用不同的策略。

## PolicyObject
---
`PolicyObject` 对应配置文件的 `policy` 项。

```json
{
  "policy": {
    "levels": {
      "0": {
        "handshake": 4,
        "connIdle": 300,
        "uplinkOnly": 2,
        "downlinkOnly": 5,
        "statsUserUplink": false,
        "statsUserDownlink": false,
        "bufferSize": 4
      }
    },
    "system": {
      "statsInboundUplink": false,
      "statsInboundDownlink": false,
      "statsOutboundUplink": false,
      "statsOutboundDownlink": false
    }
  }
}
```
{{% notice dark %}}`level`: map{string: [LevelPolicyObject](#levelpolicyobject)}{{% /notice %}}

一组键值对，每个键是一个字符串形式的数字（JSON 的要求），比如 `"0"`、`"1"` 等，双引号不能省略，此数字对应用户等级。每一个值是一个 [LevelPolicyObject](#levelpolicyobject).

{{% notice info %}}
**TIP**\
每个入站出站代理现在都可以设置用户等级，Xray 会根据实际的用户等级应用不同的本地策略。
{{% /notice %}}

{{% notice dark %}}`system`: [SystemPolicyObject](#systempolicyobject){{% /notice %}}

Xray系统级别的策略

<br />
### LevelPolicyObject
---
```json
{
    "handshake": 4,
    "connIdle": 300,
    "uplinkOnly": 2,
    "downlinkOnly": 5,
    "statsUserUplink": false,
    "statsUserDownlink": false,
    "bufferSize": 10240
}
```
{{% notice dark %}}`handshake`: number{{% /notice %}}

连接建立时的握手时间限制。单位为秒。默认值为 `4`。在入站代理处理一个新连接时，在握手阶段如果使用的时间超过这个时间，则中断该连接。

{{% notice dark %}}`connIdle`: number{{% /notice %}}

连接空闲的时间限制。单位为秒。默认值为 `300`。inbound/outbound处理一个连接时，如果在 `connIdle` 时间内，没有任何数据被传输（包括上行和下行数据），则中断该连接。

{{% notice dark %}}`uplinkOnly`: number{{% /notice %}}

当连接下行线路关闭后的时间限制。单位为秒。默认值为 `2`。当服务器（如远端网站）关闭下行连接时，出站代理会在等待 `uplinkOnly` 时间后中断连接。

{{% notice dark %}}`downlinkOnly`: number{{% /notice %}}

当连接上行线路关闭后的时间限制。单位为秒。默认值为 `5`。当客户端（如浏览器）关闭上行连接时，入站代理会在等待 `downlinkOnly` 时间后中断连接。

{{% notice info %}}
**TIP**\
在 HTTP 浏览的场景中，可以将 `uplinkOnly` 和 `downlinkOnly` 设为 `0`，以提高连接关闭的效率。
{{% /notice %}}

{{% notice dark %}}`statsUserUplink`: true | false{{% /notice %}}

当值为 `true` 时，开启当前等级的所有用户的上行流量统计。

{{% notice dark %}}`statsUserDownlink`: true | false{{% /notice %}}

当值为 `true` 时，开启当前等级的所有用户的下行流量统计。

{{% notice dark %}}`bufferSize`: number{{% /notice %}}

每个连接的内部缓存大小。单位为 kB。当值为 `0` 时，内部缓存被禁用。

默认值: 
* 在 ARM、MIPS、MIPSLE 平台上，默认值为 `0`。
* 在 ARM64、MIPS64、MIPS64LE 平台上，默认值为 `4`。
* 在其它平台上，默认值为 `512`。

{{% notice info %}}
**TIP**\
`bufferSize` 选项会覆盖 [环境变量](env.md#每个连接的缓存大小)中 `Xray.ray.buffer.size` 的设定。
{{% /notice %}}

<br />
### SystemPolicyObject
---
```json
{
    "statsInboundUplink": false,
    "statsInboundDownlink": false,
    "statsOutboundUplink": false,
    "statsOutboundDownlink": false
}
```
{{% notice dark %}}`statsInboundUplink`: true | false{{% /notice %}}

当值为 `true` 时，开启所有入站代理的上行流量统计。
{{% notice dark %}}`statsInboundDownlink`: true | false{{% /notice %}}

当值为 `true` 时，开启所有入站代理的下行流量统计。
{{% notice dark %}}`statsOutboundUplink`: true | false{{% /notice %}}
当值为 `true` 时，开启所有出站代理的上行流量统计。
{{% notice dark %}}`statsOutboundDownlink`: true | false{{% /notice %}}
当值为 `true` 时，开启所有出站代理的下行流量统计。
