### install python2 and python3
yum install wget gdbm gdbm-devel zlib-devel bzip2-devel ncurses-devel sqlite-devel readline-devel tk-devel gcc xz-devel bsddb openssl-devel

then:

installpy2.sh
```
!/bin/sh

wget https://www.python.org/ftp/python/2.7.16/Python-2.7.16.tgz
tar zxvf Python-2.7.16.tgz
mkdir python27
cd Python-2.7.16
./configure --prefix=/home/software/python27/
make
make install
cd /home/software/python27/bin/
wget https://bootstrap.pypa.io/get-pip.py
./python get-pip.py
ln -sf /home/software/python27/bin/python /usr/bin/python
ln -sf /home/software/python27/bin/pip /usr/bin/pip
```
after installing python2, yum can't work for we have replace the default python, so.
vim /usr/bin/yum
first line: `#!/usr/bin/python -> #!/usr/bin/python2.7`
vim /usr/libexec/urlgrabber-ext-down
first line: `#!/usr/bin/python -> #!/usr/bin/python2.7`

installpy3.sh
```
!/bin/sh

wget https://www.python.org/ftp/python/3.6.8/Python-3.6.8.tgz
tar zxvf Python-3.6.8.tgz
mkdir python368
cd Python-3.6.8
./configure --prefix=/home/software/python368/
make
make install
ln -sf /home/software/python368/bin/python3 /usr/bin/python3
ln -sf /home/software/python368/bin/pip3 /usr/bin/pip3

```

### install mongo
installmongo.sh
```
#!/bin/sh

echo "[mongodb-org]
name=MongoDB Repository
baseurl=http://mirrors.aliyun.com/mongodb/yum/redhat/7Server/mongodb-org/3.2/x86_64/
gpgcheck=0
enabled=1
" >> /etc/yum.repos.d/mongodb-org.repo

yum install -y mongodb-org

```