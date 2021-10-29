---
title: "docker-k8s 虚拟机"
excerpt: ""
toc: true
---

docker-k8s的作用是容器及管理容器的技术服务器。

### 安装Docker {#安装Docker}

1. 安装依赖
``` bash 
sudo yum install -y yum-utils  device-mapper-persistent-data  lvm2
```
2. 配置仓库源
   + 官方地址
   ``` bash 
   sudo yum-config-manager  --add-repo   https://download.docker.com/linux/centos/docker-ce.repo
   ```
   + 官方源可能比较慢，阿里云地址
   ``` bash
   sudo yum-config-manager --add-repo https://mirrors.aliyun.com/docker-ce/linux/centos/docker-ce.repo
   ```
3. 安装docker-ce
   ``` bash
   sudo yum install docker-ce docker-ce-cli containerd.io
   ```
4. 设置docker开机启动
   ``` bash
   systemctl enable docker.service
   ```
5. 启动docker
   ``` bash
   systemctl start docker.service
   ```

### 安装docker-compose {#安装docker-compose}
``` bash
sudo curl -L "https://github.com/docker/compose/releases/download/1.29.2/docker-compose-$(uname -s)-$(uname -m)" -o /usr/local/bin/docker-compose
sudo chmod +x /usr/local/bin/docker-compose
```
### 安装harbor

harbor有在线安装和离线安装两种方式，我使用离线安装。

1. 下载离线安装包
   下载地址<a href="https://github.com/goharbor/harbor/releases" target="_blank">https://github.com/goharbor/harbor/releases</a>，下载不了，参考[github国内访问]({% link _posts/2021-10-21-github国内访问.md %})。4
   把下载的文件放在/usr/local/bin目录下
2. 解压
   <code>tar zxvf 2021-09-30-11-07-32-harbor-harbor-offline-installer-v2.3.3.tgz </code>
3. 进入harbor目录
   <code>cd harbor/</code>
4. 拷贝配置文件
   <code>cp harbor.yml.tmpl harbor.yml</code>
5. 编辑配置文件
   <code>vi harbor.yml</code>

``` text
hostname = 192.168.100.110
port = 80
# https related config
# https:
  # # https port for harbor, default is 443
  # port: 443
  # # The path of cert and key files for nginx
  # certificate: /your/certificate/path
  # private_key: /your/private/key/path
```
6. 环境检测
   <code>./prepare</code>
7. 开始安装并启动
   <code>./install.sh</code>
8. 浏览器管理harbor
   浏览器打开192.168.100.110:80 默认登录用户名/密码：admin/Harbor12345

### docker登录私有仓库 {#docker登录私有仓库}

1. 远程仓库配置
docker 远程仓库登录配置有两种方式。
   1. 配置systemd启动文件
      + 修改配置文件 <code>vi /usr/lib/systemd/system/docker.service</code>
   ``` text
   ExecStart=/usr/bin/dockerd --insecure-registry 192.168.100.110
   ```
      + systemctl daemon-reload
      + systemctl start docker

   2. 配置/etc/docker/daemon.json
      + <code>vi /etc/docker/daemon.json</code>,如果这个文件没有，会自动新建
   ``` text
   {    
    "registry-mirrors":["https://almtd3fa.mirror.aliyuncs.com"],
    "insecure-registries":["192.168.100.110"]
   }
   ```
      + systemctl daemon-reload
      + systemctl start docker
2. 登录远程仓库
   <code>docker login 192.168.100.110</code>,然后输入用户名/密码：admin/Harbor12345