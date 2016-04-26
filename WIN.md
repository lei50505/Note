# Note

* 新建文件夹

```
D:\dev\repos
D:\dev\tools
```

* 安装Typora

```
安装typora-setup.exe
```
* 安装Git

```
安装Git-2.6.3-64-bit.exe
打开Git Bash
ssh-keygen -t rsa -b 4096 -C "183515951@qq.com"
cd .ssh/
cat id_rsa.pub
添加到GitHub

git config --global push.default simple
git config --global user.name "CAOLEI"
git config --global user.email 183515951@qq.com

C:\Users\CAOLEI\AppData\Local\Programs\Git\etc -> 右键Git GUI Here打开文件位置 -> etc/bash.bashrc
alias ga='git add'
alias gb='git branch'
alias gba='git branch -a'
alias gc='git commit'
alias gco='git checkout'
alias gd='git diff'
alias gl='git pull'
alias glog='git log --oneline --decorate --color --graph'
alias gm='git merge'
alias gp='git push'
alias gst='git status'
```

* VS Project添加Git

```
新建WPF项目
解决方案IPGW -> 右键 -> 将解决方案添加到源代码管理 -> Git -> 确定
GitHub新建仓库IPGW
项目目录内 -> 右键 -> Git Bash Here
git add -A
git commit -m "init"
git remote add origin git@github.com:lei50505/IPGW.git
git push -u origin master
```

* 安装JDK

```
安装jdk-8u77-windows-x64.exe
配置环境变量
新建 -> JAVA_HOME -> C:\Program Files\Java\jdk1.8.0_77
PATH前加 -> %JAVA_HOME%\bin
```

* 安装Maven

```
解压apache-maven-3.3.9-bin.zip -> D:\dev\tools
配置环境变量
新建 -> M2_HOME -> D:\dev\tools\apache-maven-3.3.9
PATH前加 -> %M2_HOME%\bin
```

* 安装Tomcat8

```
解压apache-tomcat-8.0.22-windows-x64.zip -> -> D:\dev\tools
```

* 安装Spring Tool Suite 3.6.3

```
解压spring-tool-suite-3.6.3.RELEASE-e4.4.1-win32-x86_64.zip -> D:\Programs
创建快捷方式 -> D:\Programs\sts-bundle\sts-3.6.3.RELEASE\STS.exe

打开STS
Select a workspace
Workspace -> D:\STS
选中Use this as the defult... -> OK

Preferences
Install/Update -> Automatic Update -> 取消Automatically find...
Java -> Installed JREs -> 选择JDK1.8 -> 只有JRE需添加JDK -> 无用的移除 -> Edit...
Default VM arguments -> 填写 -Dmaven.multiModuleProjectDirectory=$M2_HOME
Server -> Runtime Environments -> Add... -> Tomcat v8.0 + Create a new... -> OK -> Tomcat installation directory -> dev/tools/apache-tomcat-8.0.30 -> JRE选择JDK1.8 -> Finish
Maven -> Installations -> Add... -> Installation home -> dev/tools/apache-maven-3.3.9 -> Finish -> 选择新添加 -> Apply
General -> Editors -> Text Editors -> 选中Insert spaces for tabs -> OK
Java -> Code Style -> Formatter -> Edit... -> Tab policy -> 选Spaces only -> Profile name -> 改Spaces only -> OK

布局
左
Package Explorer
下
Console
Servers
Problems
Progress
右
Outline

下Servers -> 删除Pivotal tc Server... -> 选中Delete unused...
双击Tomcat v8.0 -> Open
Server Locations -> 选中Use Tomcat installation...
Deploy path -> webapps
command + S 保存

退出
Confirm Exit -> 选中Always exit without prompt
```

* 安装MySQL

```
安装mysql-essential-5.1.68-win32.msi
最后选中Config MySQL ... Now
Detailed Configuration -> Developer Machine -> Multifunctional Database -> Manual Selected Default Character Set/Collation -> utf8 -> Include Bin Directory in Windows PATH -> 取消Launch MySQL Server automatically -> 设置Root密码为password -> 选中Enable root access from...
```

* 安装Navicat

```
安装并注册navicat 10.0.10+注册机+注册码.rar
```

* 安装WebStorm

```
安装WebStorm-10.0.4.exe
激活
User or company Name:
EMBRACE
===== LICENSE KEY=====
24718-12042010
00001h6wzKLpfo3gmjJ8xoTPw5mQvY
YA8vwka9tH!vibaUKS4FIDIkUfy!!f
3C"rQCIRbShpSlDcFT1xmJi5h0yQS6
===== LICENSE END =====
```

* 安装Nginx

```
解压nginx-1.8.1.zip -> ...dev\tools
进目录Shift + 右击 -> 在此处打开命令窗口 -> start nginx 运行
nginx.exe -s stop 停止
nginx.exe -s quit 正常退出
nginx.exe -s reload 重新加载
```

