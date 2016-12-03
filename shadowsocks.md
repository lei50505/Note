* 修复sysctl

```
rm -f /sbin/modprobe 
ln -s /bin/true /sbin/modprobe

rm -f /sbin/sysctl 
ln -s /bin/true /sbin/sysctl
```

* 提高连接数

```
vi /etc/security/limits.conf
* soft nofile 51200
* hard nofile 51200

/etc/rc.d/rc.local
ulimit -n 51200
```

* 优化内核参数

```
vi /etc/sysctl.conf
fs.file-max = 51200

net.core.rmem_max = 67108864
net.core.wmem_max = 67108864
net.core.netdev_max_backlog = 250000
net.core.somaxconn = 4096

net.ipv4.tcp_syncookies = 1
net.ipv4.tcp_tw_reuse = 1
net.ipv4.tcp_tw_recycle = 0
net.ipv4.tcp_fin_timeout = 30
net.ipv4.tcp_keepalive_time = 1200
net.ipv4.ip_local_port_range = 10000 65000
net.ipv4.tcp_max_syn_backlog = 8192
net.ipv4.tcp_max_tw_buckets = 5000
net.ipv4.tcp_fastopen = 3
net.ipv4.tcp_mem = 25600 51200 102400
net.ipv4.tcp_rmem = 4096 87380 67108864
net.ipv4.tcp_wmem = 4096 65536 67108864
net.ipv4.tcp_mtu_probing = 1
net.ipv4.tcp_congestion_control = hybla


sysctl -p
```