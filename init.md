* 修改密码

```
passwd
此命令为修改当前用户密码，连续输入两次新密码即可
```

* 修改SSH端口号

```
/etc/ssh/sshd_config
修改最后的Port为12300
```

* SSH连接不上

```
删除~/.ssh/known_hosts
```