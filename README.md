# Shadowrocket

在Johnshall的lazy配置基础上，增加了防DNS泄露。[General]主要修改如下：

```
# 旁路系统。如果禁用此选项，可能会导致一些系统问题，如推送通知延迟。
bypass-system = true

# DNS 覆写。使用普通 DNS 或加密 DNS（如 DoH、DoQ、DoT 等）覆盖默认的系统 DNS。填 system 表示使用系统 DNS。
dns-server = https://cloudflare-dns.com/dns-query#proxy,https://security.cloudflare-dns.com/dns-query#proxy

# 备用 DNS。当覆写 DNS 查询失败或查询时间超过 2 秒，Shadowrocket 会自动回退备用 DNS。如需指定多个 DNS，可用逗号分隔。system 表示回退到系统 DNS。
fallback-dns-server = https://1.1.1.1/dns-query#proxy 

# 启用 IPv6 支持。false 表示不启用，true 表示启用。启用会同时查询 A 记录和 AAAA 记录，优先使用 IPv4 地址解析。
ipv6 = false

# 首选 IPv6。优先向 IPv6 的 DNS 服务器查询 AAAA 记录，优先使用 IPv6 地址解析。false 表示不启用。
prefer-ipv6 = false

# 直连的域名类规则使用系统 DNS 进行查询。false 表示不启用。
dns-direct-system = false

# ping 数据包自动回复。
icmp-auto-reply = false

# 不开启时，「重写的 REJECT 策略」默认只有在配置模式下生效。开启后，可以令该策略在其他全局路由模式下都生效。
always-reject-url-rewrite = true

# 私有 IP 应答。如果不启用此选项，域名解析返回私有 IP，Shadowrocket 会认为该域名被劫持而强制使用代理。
private-ip-answer = false

# 直连域名解析失败后使用代理。false 表示不启用。
dns-direct-fallback-proxy = true

# DNS 劫持。有些设备或软件总是使用硬编码的 DNS 服务器，例如 Netflix 通过 Google DNS(8.8.8.8或8.8.4.4)发送请求，您可以使用此选项来劫持查询。
hijack-dns = 8.8.8.8:53,8.8.4.4:53

# 当 UDP 流量匹配到规则里不支持 UDP 转发的节点策略时重新选择回退行为，可选行为包括 DIRECT、REJECT。DIRECT 表示直连转发 UDP 流量，REJECT 表示拒绝转发 UDP 流量。
udp-policy-not-supported-behaviour = REJECT

# QUIC协议屏蔽策略。支持使用 all-proxy、all、always-allow 对 QUIC 传输层协议进行设置。其中 all-proxy 表示只对“走代理的连接”阻断 QUIC，直连连接（DIRECT）不会被干预；all 表示对所有连接（包括直连与代理）都屏蔽 QUIC，这会完全禁止系统中一切 UDP/443 流量；always-allow 表示始终允许 QUIC，不做任何屏蔽，等同于“关闭 QUIC 屏蔽”。
block-quic = all-proxy
```

将[Rule]中China.list换为blackmatrix7的Shadowrocket的China.list和China.Domin.list
