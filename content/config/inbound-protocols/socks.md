---
date: "2020-08-20T16:42:11.812Z"
description: Project X 的文档.
title: Socks
weight: 4
---

标准 Socks 协议实现，兼容 [Socks 4](http://ftp.icm.edu.pl/packages/socks/socks4/SOCKS4.protocol)、Socks 4a 和 [Socks 5](http://ftp.icm.edu.pl/packages/socks/socks4/SOCKS4.protocol)。

{{% notice danger important %}}
**socks 协议没有对传输加密，不适宜经公网中传输**

`socks inbound` 更有意义的用法是在局域网或本机环境下监听，为其他程序提供本地服务。
{{% /notice %}}

## InboundConfigurationObject

```json
{
  "auth": "noauth",
  "accounts": [
    {
      "user": "my-username",
      "pass": "my-password"
    }
  ],
  "udp": false,
  "ip": "127.0.0.1",
  "userLevel": 0
}
```

{{% notice dark %}} `auth`: "noauth" | "password"{{% /notice %}}

Socks 协议的认证方式，支持 `"noauth"` 匿名方式和 `"password"` 用户密码方式。

默认值为 `"noauth"`。

{{% notice dark %}} `accounts`: \[ [AccountObject](#accountobject) \]{{% /notice %}}

一个数组，数组中每个元素为一个用户帐号。

此选项仅当 `auth` 为 `password` 时有效。

默认值为空。

{{% notice dark %}} `udp`: true | false{{% /notice %}}

是否开启 UDP 协议的支持。

默认值为 `false`。

{{% notice dark %}} `ip`: address{{% /notice %}}

当开启 UDP 时，Xray 需要知道本机的 IP 地址。

默认值为 `"127.0.0.1"`。

{{% notice dark %}} `userLevel`: number{{% /notice %}}

用户等级，连接会使用这个用户等级对应的[本地策略](../../policy#levelpolicyobject)。

userLevel 的值, 对应 [policy](../../policy#policyobject) 中 level 的值. 如不指定, 默认为 0.

<br />
### AccountObject
---

```json
{
  "user": "my-username",
  "pass": "my-password"
}
```

{{% notice dark %}} `user`: string{{% /notice %}}

用户名，字符串类型。必填。

{{% notice dark %}} `pass`: string{{% /notice %}}

密码，字符串类型。必填。
