# IPv4 优先

执行以下命令调整网络前缀优先级，让 IPv4 访问优先

```
netsh interface ipv6 set prefixpolicy ::1/128       50 0
netsh interface ipv6 set prefixpolicy ::ffff:0:0/96 45 4
netsh interface ipv6 set prefixpolicy ::/0          40 1
netsh interface ipv6 set prefixpolicy 2002::/16     30 2
netsh interface ipv6 set prefixpolicy 2001::/32     5  5
netsh interface ipv6 set prefixpolicy fc00::/7      3  13
netsh interface ipv6 set prefixpolicy fec0::/10     1  11
netsh interface ipv6 set prefixpolicy 3ffe::/16     1  12
netsh interface ipv6 set prefixpolicy ::/96         1  3
```

```
netsh interface ipv6 show prefixpolicies
```

# IPv6 优先

默认即为 IPv6 优先，如设置了 IPv4 优先，执行以下命令后重启即可。

```
netsh interface ipv6 reset
```
