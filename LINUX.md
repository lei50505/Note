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

