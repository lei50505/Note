# Python

* pip使用镜像

```
C:\Users\CAOLEI\pip\pip.ini
[global]
index-url = https://pypi.tuna.tsinghua.edu.cn/simple
```

* CentOS7安装Python3

```
yum install -y gcc-c++ zlib-devel openssl-devel python-devel wget m2crypto git sqlite-devel
wget https://www.python.org/ftp/python/3.6.6/Python-3.6.6.tgz
tar xvf Python-3.6.6.tgz
./configure --prefix=/usr/local/python3
make && make install
cat << EOF > /etc/profile.d/python3.sh
export PATH=/usr/local/python3/bin:$PATH
EOF
mv /usr/bin/python /usr/bin/python.bak
ln -fs /usr/local/python3/bin/python3 /usr/bin/python
ln -fs /usr/local/python3/bin/pip3 /usr/bin/pip
vi /usr/libexec/urlgrabber-ext-down
python2
vi /usr/bin/yum
python2
```

* 安装Jupyter

```
pip install jupyter
jupyter notebook --generate-config
jupyter notebook password
caolei963
Edit jupyter_notebook_config.py
c.NotebookApp.password = Copy From jupyter_notebook_config.json
c.NotebookApp.ip = 'ti19.com'
c.NotebookApp.port = 443
c.NotebookApp.allow_root = True
c.NotebookApp.notebook_dir = '/root/jupyter_note/'
c.NotebookApp.open_browser = False
c.NotebookApp.ssl_options = {"certfile":"/root/cert.pem","keyfile":"/root/cert.key"}
cat << EOF > /usr/lib/systemd/system/my-jupyter.service
[Unit]
Description=my-jupyter
[Service]
Type=simple
ExecStart=/usr/local/python3/bin/jupyter notebook --config=/root/jupyter-config.py
[Install]
WantedBy=multi-user.target
EOF
```