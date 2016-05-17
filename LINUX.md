# Note

* 安装Nginx

```
vi /etc/yum.repos.d/nginx.repo 
[nginx]
name=nginx repo
baseurl=http://nginx.org/packages/centos/6/$basearch/
gpgcheck=0
enabled=1

yum install nginx

mkdir /usr/share/nginx/web
FileZilla拷贝my-front/... -> ...web
vi /etc/nginx/conf.d/default.conf
root /usr/share/nginx/web;

nginx
nginx -s reload
nginx -s stop
```

* 安装MySQL

```
yum install mysql-server
service mysqld start
mysql -u root -p
设置root密码
set password = password("password");

创建管理帐户，替换root工作
GRANT ALL PRIVILEGES ON *.* TO 'admin'@'localhost' IDENTIFIED BY 'admin';
GRANT ALL PRIVILEGES ON *.* TO 'admin'@'127.0.0.1' IDENTIFIED BY 'admin';
GRANT ALL PRIVILEGES ON *.* TO 'admin'@'%' IDENTIFIED BY 'admin';

把空用户帐户删除
delete from mysql.user where user='';
flush privileges;

创建工作账户
GRANT SELECT, INSERT, UPDATE, DELETE ON `my-feedback`.* TO 'fb'@'%' IDENTIFIED BY 'password';
```

* 安装JRE

```
yum install jre
```

* 安装Tomcat

```
wget http://apache.cs.utah.edu/tomcat/tomcat-8/v8.0.33/bin/apache-tomcat-8.0.33.tar.gz
cd ~/dev/tools
tar -zxvf ~/apache-tomcat-8.0.33.tar.gz
./startup.sh
```

* 更改密码

```
passwd
```

* 安装Shadowsocks

```
wget --no-check-certificate https://raw.githubusercontent.com/teddysun/shadowsocks_install/master/shadowsocks-libev.sh

chmod +x shadowsocks-libev.sh

./shadowsocks-libev.sh 2>&1 | tee shadowsocks-libev.log
password caolei123

/etc/init.d/shadowsocks stop

vi /etc/shadowsocks-libev/config.json
{
    "server":["[::0]","0.0.0.0"],
    "server_port":your_server_port,
    "local_address":"127.0.0.1",
    "local_port":1080,
    "password":"your_password",
    "timeout":600,
    "method":"aes-256-cfb"
}

/etc/init.d/shadowsocks start
```

* 安装PPTP

```
wget http://www.hi-vps.com/shell/vpn_centos6.sh

chmod a+x vpn_centos6.sh

bash vpn_centos6.sh
1
3 -> pptp caolei123
```

* 安装Redis

```
wget http://download.redis.io/releases/redis-3.2.0.tar.gz
tar xzf redis-3.2.0.tar.gz
cd redis-3.2.0
make
make install

vi /root/redis-3.2.0/redis.conf
# bind 127.0.0.1
requirepass caolei123

启动 redis-server /root/redis-3.2.0/redis.conf &
停止 redis-cli -a caolei123 shutdown

连接 redis-cli.exe -h 144.168.63.86 -p 6379 -a caolei123
```

