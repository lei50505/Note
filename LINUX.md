# Note

* 修改root密码

```
passwd
0p;/(OL>
```

* 修改ssh端口

```
vi /etc/ssh/sshd_config
Port 12300
/etc/init.d/sshd restart
```

* 用户管理

```
useradd dev
passwd dev
90-=op[]
touch /root/start.sh
chmod +x /root/start.sh
touch /root/stop.sh
chmod +x /root/stop.sh
```

* 安装Shadowsocks

```
wget --no-check-certificate https://raw.githubusercontent.com/teddysun/shadowsocks_install/master/shadowsocks-libev.sh

chmod +x shadowsocks-libev.sh

./shadowsocks-libev.sh 2>&1 | tee shadowsocks-libev.log
password caolei123
port 18989

/etc/init.d/shadowsocks stop

vi /etc/shadowsocks-libev/config.json
"server":["[::0]","0.0.0.0"],

/etc/init.d/shadowsocks start

rm -f shadowsocks-libev.sh
rm -f shadowsocks-libev.log
```

* 安装PPTP

```
wget http://www.hi-vps.com/shell/vpn_centos6.sh

chmod a+x vpn_centos6.sh

bash vpn_centos6.sh
1
3 -> pptp caolei123

rm -f dkms-2.0.17.5-1.noarch.rpm 
rm -f  pptpd-1.3.4-2.el6.x86_64.rpm
rm -f kernel_ppp_mppe-1.0.2-3dkms.noarch.rpm
rm -f vpn_centos6.sh
rm -f ppp-2.4.5-17.0.rhel6.x86_64.rpm
rm -f kernel_ppp_mppe-1.0.2-3dkms.noarch.rpm.1
```

* 安装JDK

```
wget --no-check-certificate --no-cookie --header "Cookie: oraclelicense=accept-securebackup-cookie;" http://download.oracle.com/otn-pub/java/jdk/8u91-b14/jdk-8u91-linux-x64.rpm

rpm -ivh jdk-8u91-linux-x64.rpm

echo 'export JAVA_HOME=/usr/java/jdk1.8.0_91' >> /etc/profile.d/java.sh
echo 'export PATH=$JAVA_HOME/bin:$PATH' >> /etc/profile.d/java.sh
source /etc/profile.d/java.sh

rm -f jdk-8u91-linux-x64.rpm
```

* 安装Git

```
yum install git
mkdir /git
chmod 777 /git
mkdir -p /usr/local/dev/git/repos
chmod 777 /usr/local/dev/git/repos
```

* 安装Maven

```
cd
wget http://www-us.apache.org/dist/maven/maven-3/3.3.9/binaries/apache-maven-3.3.9-bin.tar.gz

cd /usr/local
tar -zxvf ~/apache-maven-3.3.9-bin.tar.gz

echo 'export M2_HOME=/usr/local/apache-maven-3.3.9' >> /etc/profile.d/maven.sh
echo 'export PATH=$M2_HOME/bin:$PATH' >> /etc/profile.d/maven.sh
source /etc/profile.d/maven.sh

rm -f ~/apache-maven-3.3.9-bin.tar.gz
```

* 安装MySQL

```
yum install mysql-server
service mysqld start
echo 'service mysqld start' >> /root/start.sh
echo 'service mysqld stop' >> /root/stop.sh
mysql -u root -p

set password = password("caolei123");

GRANT ALL PRIVILEGES ON *.* TO 'admin'@'%' IDENTIFIED BY 'caolei123';

GRANT SELECT, INSERT, UPDATE, DELETE ON `my-feedback`.* TO 'fb'@'%' IDENTIFIED BY 'caolei123';
```

* 安装Redis

```
yum install gcc-c++

cd
wget http://download.redis.io/releases/redis-3.2.0.tar.gz
cd /usr/local
tar -zxvf ~/redis-3.2.0.tar.gz
cd redis-3.2.0
make
make install

vi /usr/local/redis-3.2.0/redis.conf
port 63790
# bind 127.0.0.1
requirepass caolei123

redis-server /usr/local/redis-3.2.0/redis.conf &
# redis-cli -p 63790 -a caolei123 shutdown

echo 'redis-server /usr/local/redis-3.2.0/redis.conf &' >> /root/start.sh
echo 'redis-cli -p 63790 -a caolei123 shutdown' >> /root/stop.sh

# redis-cli -h ti19.com -p 63790 -a caolei123

rm ~/redis-3.2.0.tar.gz
```

* 安装Tomcat

```
# server dev
cd
wget http://apache.cs.utah.edu/tomcat/tomcat-8/v8.0.33/bin/apache-tomcat-8.0.33.tar.gz
tar -zxvf ~/apache-tomcat-8.0.33.tar.gz

touch ~/start.sh
chmod +x ~/start.sh
echo '~/apache-tomcat-8.0.33/bin/startup.sh' >> ~/start.sh
touch ~/stop.sh
chmod +x ~/stop.sh
echo '~/apache-tomcat-8.0.33/bin/shutdown.sh' >> ~/stop.sh

rm -f ~/apache-tomcat-8.0.33.tar.gz
```

* 安装Nginx

```
vi /etc/yum.repos.d/nginx.repo 
[nginx]
name=nginx repo
baseurl=http://nginx.org/packages/centos/6/$basearch/
gpgcheck=0
enabled=1

yum install nginx

mkdir -p /usr/local/dev/nginx/web
chmod 777 /usr/local/dev/nginx/web
vi /etc/nginx/conf.d/default.conf
root /usr/local/dev/nginx/web/my-front;

nginx
# nginx -s reload/stop

echo 'nginx' >> /root/start.sh
echo 'nginx -s stop' >> /root/stop.sh
```

* 配置SSH无密码登录

```
# client
# ssh-keygen -t rsa -b 4096 -C "183515951@qq.com"
ssh-copy-id -p 12300 -i ~/.ssh/id_rsa.pub dev@ti19.com

# ssh -p 12300 dev@ti19.com
```

* 配置nginx自动部署

```
# server:dev
mkdir /git/my-front.git
cd /git/my-front.git
git --bare init

# client
git remote add d ssh://dev@ti19.com:12300/git/my-front.git
git push d

# server:dev
cd /usr/local/dev/nginx/web
git clone /git/my-front.git
vi /git/my-front.git/hooks/post-receive
#!/bin/bash
unset $(git rev-parse --local-env-vars)
cd /usr/local/dev/nginx/web/my-front
git fetch --all
git reset --hard origin/master

chmod +x /git/my-front.git/hooks/post-receive
```

* 配置Tomcat自动部署

```
# server:dev
mkdir -p /git/my-feedback.git
cd /git/my-feedback.git
git --bare init

# client
git remote remove d
git remote add d ssh://dev@ti19.com:12300/git/my-feedback.git
git push d

# server:dev
mkdir -p /usr/local/dev/git/repos
cd /usr/local/dev/git/repos
git clone /git/my-feedback.git

vi /git/my-feedback.git/hooks/post-receive
#!/bin/bash
~/apache-tomcat-8.0.33/bin/shutdown.sh
unset $(git rev-parse --local-env-vars)
cd /usr/local/dev/git/repos/my-feedback
git fetch --all
git reset --hard origin/master
mvn clean install
rm -f ~/apache-tomcat-8.0.33/webapps/my-feedback.war
rm -rf ~/apache-tomcat-8.0.33/webapps/my-feedback
cp /usr/local/dev/git/repos/my-feedback/target/my-feedback.war ~/apache-tomcat-8.0.33/webapps
~/apache-tomcat-8.0.33/bin/startup.sh

chmod +x /git/my-feedback.git/hooks/post-receive
```

