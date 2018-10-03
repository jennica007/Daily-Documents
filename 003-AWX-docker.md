---
title: AWX-Docker-installation
date: 2018-10-01
categories: Tools
tags: AWX
---  

**System environment**  
- centos7 64bit  
- python 2.7.5  
- System memoty must be greater than 2G  

**Installation**  
#### step 1.
 clone repo.
```bash  
git clone https://github.com/ansible/awx.git
```  

#### step 2.
Ansible（Version 2.4+）.
``` bash
yum install ansible -y
```

Docker  
If you already installed old version of docker, the first step is delete old version.  
```bash
yum -y remove docker docker-common container-selinux
yum -y remove docker-selinux
```  
docker-py Python module
``` bash
wget https://bootstrap.pypa.io/get-pip.py
python get-pip.py
pip install docker
```

 GNU Make
``` bash
yum install make -y
```

Git Requires Version 1.8.4+
```bash   
# yum
yum install git-all  
# Source code compilation and installation  
yum install -y epel-release
yum install -y dh-autoreconf curl-devel expat-devel gettext-devel \
  openssl-devel perl-devel zlib-devel
yum install -y install asciidoc xmlto docbook2X
yum install gnu-getopt -y
ln -s /usr/bin/db2x_docbook2texi /usr/bin/docbook2x-texi
wget https://mirrors.edge.kernel.org/pub/software/scm/git/git-1.8.4.5.tar.gz
tar zxvf git-1.8.4.5.tar.gz
cd git-1.8.4.5/
make configure
./configure --prefix=/usr
make all doc info
make install install-doc install-html install-info
```  

Docker-compose  
``` bash
wget https://github.com/docker/compose/releases/download/1.17.1/docker-compose-Linux-x86_64
mv docker-compose-Linux-x86_64 /usr/bin/docker-compose
chmod 755 /usr/bin/docker-compose
```

 Node 6.x LTS version and NPM 3.x LTS
``` bash
wget https://nodejs.org/dist/v8.11.3/node-v8.11.3-linux-x64.tar.xz
tar Jxvf node-v8.11.3-linux-x64.tar.xz
mv node-v8.11.3-linux-x64/ /usr/local/node

echo "export PATH=$PATH:/usr/local/node/bin" > /etc/profile.d/node.sh
source /etc/profile
#Check version
npm -v
5.6.0

node -v
v8.11.3
```

#### step 3. install awx base on docker-compose
``` bash
# By default,installer/inventory installed AWX on local host,，If need to install on remote hosts，Modify installer/install.yml
cd awx/
cd /root/awx/installer
ansible-playbook -i inventory install.yml  
# Browsing
http://47.75.212.160 /
admin/password
admin/GSMCpassword666
#Check images
docker ps
CONTAINER ID        IMAGE                        COMMAND                  CREATED             STATUS              PORTS                                                 NAMES
a44a322cc32b        ansible/awx_task:latest      "/tini -- /bin/sh -c…"   5 hours ago         Up 5 hours          8052/tcp                                              awx_task
3f592321fb4c        ansible/awx_web:latest       "/tini -- /bin/sh -c…"   5 hours ago         Up 5 hours          0.0.0.0:80->8052/tcp                                  awx_web
12438872fc22        memcached:alpine             "docker-entrypoint.s…"   5 hours ago         Up 5 hours          11211/tcp                                             memcached
e8439ec38bdf        ansible/awx_rabbitmq:3.7.4   "docker-entrypoint.s…"   5 hours ago         Up 5 hours          4369/tcp, 5671-5672/tcp, 15671-15672/tcp, 25672/tcp   rabbitmq
968c0a32dd65        postgres:9.6                 "docker-entrypoint.s…"   5 hours ago         Up 5 hours          5432/tcp                                              postgres
```    
```bash  
#stop
sudo docker stop $( sudo docker ps -q)  
#delete
docker rm $(docker ps -aq)
 ```
