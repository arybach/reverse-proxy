# reverse-proxy
# Nginx-apache reverse proxy load balancer
# for installation on Centos 7/8
# install docker
yum install -y yum-utils
yum-config-manager \
    --add-repo \
    https://download.docker.com/linux/centos/docker-ce.repo
    
yum install docker-ce docker-ce-cli containerd.io
systemctl start docker
systemctl stop firewalld

# clone reverse-proxy master to /etc/apache directory
# add /var/log + subdirectories
# from apache directory
docker-compose up --build

# tree of apache directory
├── apache80
│   ├── httpd.conf
│   └── index.html
├── apache81
│   ├── httpd.conf
│   └── index.html
├── apache82
│   ├── httpd.conf
│   └── index.html
├── default_httpd.conf
├── docker-compose.yml
├── Dockerfile.apache80
├── Dockerfile.apache81
├── Dockerfile.apache82
├── Dockerfile.nginx
├── Dockerfile.php
├── Executing
├── nginx
│   └── nginx.conf
├── php
│   ├── index.html
│   └── index.php
├── reverse-proxy
└── var
    ├── log
    │   ├── apache80
    │   │   ├── access.log
    │   │   └── error.log
    │   ├── apache81
    │   │   ├── access.log
    │   │   └── error.log
    │   ├── apache82
    │   └── nginx
    │       ├── access.log
    │       └── error.log
    └── www
        └── html
