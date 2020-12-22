---
date: "2020-08-20T16:42:11.812Z"
description: Project X 的文档.
title: HTTP
weight: 3
---

HTTP 协议。

{{% notice danger important %}}
**http 协议没有对传输加密，不适宜经公网中传输，更容易成为被人用作攻击的肉鸡。**

`http inbound` 更有意义的用法是在局域网或本机环境下监听，为其他程序提供本地服务。
{{% /notice %}}

{{% notice info %}}
**TIP 1**\
 `http proxy` 只能代理 tcp 协议，udp 系的协议均不能通过。
{{% /notice %}}

{{% notice info %}}
**TIP 2**\
在 Linux 中使用以下环境变量即可在当前 session 使用全局 HTTP 代理（很多软件都支持这一设置，也有不支持的）。

- `export http_proxy=http://127.0.0.1:8080/` (地址须改成你配置的 HTTP 入站代理地址)
- `export https_proxy=$http_proxy`
{{% /notice %}}

## InboundConfigurationObject
---

```json
{
  "timeout": 0,
  "accounts": [
    {
      "user": "my-username",
      "pass": "my-password"
    }
  ],
  "allowTransparent": false,
  "userLevel": 0
}
```

{{% notice dark %}} `timeout`: number{{% /notice %}}

连接空闲的时间限制。单位为秒。默认值为 `300`, 0 表示不限时。

处理一个连接时，如果在 `timeout` 时间内，没有任何数据被传输，则中断该连接。

{{% notice dark %}} `accounts`: \[[AccountObject](#accountobject)\]{{% /notice %}}

一个数组，数组中每个元素为一个用户帐号。默认值为空。

当 `accounts` 非空时，HTTP 代理将对入站连接进行 Basic Authentication 验证。

{{% notice dark %}} `allowTransparent`: true | false{{% /notice %}}

当为 `true` 时，会转发所有 HTTP 请求，而非只是代理请求。

{{% notice info %}}
**TIP**\
若配置不当，开启此选项会导致死循环。{{% /notice %}}


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

