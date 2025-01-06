# IPv4 优先

执行以下命令调整网络前缀优先级，让 IPv4 访问优先，一行行执行。
这里实际修改生效的是第二条命令。但是 Windows 有个 bug，其他不调整优先级的规则如果不 set 一次，重启之后规则会丢失。

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

调整后执行以下命令查看最新的优先级。

```
netsh interface ipv6 show prefixpolicies
```

# IPv6 优先

Windows 默认即为 IPv6 优先，如设置了 IPv4 优先，执行以下命令进行重置，重启电脑生效。

```
netsh interface ipv6 reset
```
