---
title: "server1 虚拟机"
excerpt: ""
toc: true
---

server1的安装常用服务的机器。

虚拟机先
+ [安装Docker]({% link _vmserver/docker-k8s.md %}#安装Docker)
+ [安装docker-compose]({% link _vmserver/docker-k8s.md %}#安装docker-compose)

### Docker安装单节点RabbitMQ

1. 查找rabbitmq镜像
   打开https://hub.docker.com/search?q=rabbitmq&type=image，打开最多的镜像的Tags。
2. 选择安装management版本，自带web管理页面
3. 安装镜像
   ``` bash
   sudo docker pull rabbitmq:3.8.2-management
   ```
4. 启动容器
   ``` bash
   docker run -d --hostname my-rabbit --name rabbitmq -e RABBITMQ_DEFAULT_USER=admin -e RABBITMQ_DEFAULT_PASS=admin123 -p 15672:15672 -p 5672:5672 rabbitmq:3.8.2-management
   ```
   docker 参数
   * -d 后台运行
   * --hostname 指定容器的主机名。或 -h
   * --name 容器名称，必须唯一
   * -e 设置环境变量
   * -p 映射的端口
   rabbitmq用户名/密码：admin/admin123
5. 更新容器配置
   可选.主机重启后自动启动容器
   ``` bash
   docker update --restart=always rabbitmq
   ```
6. 防火墙设置
   ``` bash
   firewall-cmd --add-port=5672/tcp --permanent
   firewall-cmd --reload
   ```
7. 访问管理界面
   浏览器打开 http://192.168.100.101:15672，登录账号admin，登录密码admin123

### Docker安装单节点Zookeeper (还未正式测试)

1. 下载最新镜像
   docker pull wurstmeister/zookeeper
2. 单机方式启动
   docker run -d --name zookeeper -p 2181:2181 -t wurstmeister/zookeeper

### Docker安装单节点kafka (还未正式测试)

1. 下载最新镜像
   docker pull wurstmeister/kafka
2. 单机方式启动
   docker run -d --name kafka \
   -p 9092:9092 \
   -e KAFKA_BROKER_ID=0 \
   -e KAFKA_ZOOKEEPER_CONNECT=10.0.0.101:2181 \
   -e KAFKA_ADVERTISED_LISTENERS=PLAINTEXT://10.0.0.101:9092 \
   -e KAFKA_LISTENERS=PLAINTEXT://0.0.0.0:9092 wurstmeister/kafka

