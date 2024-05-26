#linux 
print the route packets trace to network host

trace-route to a host named *rubin.internal.bladeranger.com*:
```bash
traceroute rubin.internal.bladeranger.com 
traceroute to rubin.internal.bladeranger.com (10.200.200.113), 30 hops max, 60 byte packets
 1  internal.bladeranger.com (10.200.200.2)  86.758 ms  86.713 ms  86.896 ms
 2  rubin.internal.bladeranger.com (10.200.200.113)  207.962 ms  209.011 ms  209.023 ms
```