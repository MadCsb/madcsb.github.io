---
title: "服务器介绍"
excerpt: "开发过程中，怎样通过虚拟机配置不同的开发环境，我自己的虚拟机是怎么工作的。"
redirect_from:
  - /vmserver-setup/
toc: true
---

不清楚大家在开发过程中，有没有遇到各种各样的框架、组件、服务。非常希望自己能够搞懂这些东西，但是没有足够多的服务器，也不想把自己的电脑装太多东西，导致电脑最后乱七八糟的。

我使用虚拟机就非常方便，不同的虚拟机上安装不同的服务。当所有的一切都开发、实验、测试完成后，也方便整个虚拟机拷贝出来。
如果你说docker也能完成一些这方面的工作啊，其实docker只能完成一部分，针对整个linux的学习实验，感觉用虚拟机更完整。

## 虚拟软件 VMware Workstation Pro

VMware Workstation Pro 提供虚拟机的创建和管理。

* VMware® Workstation 16 Pro 版本16.1.2 build-17966106
* VMnet8 
   + 子网IP 192.168.100.0
   + 子网掩码 255.255.255.0
   + 网关IP 192.168.100.2

## CentOS8Template 模板虚拟机

模板虚拟机安装基础软件，通过完整克隆，快速生成其他服务器。

* linux系统版本 CentOS-8.3.2011-x86_64-dvd1.iso
* ip = 192.168.100.100
* 管理员用户：root,密码：123456
* 普通用户：server,密码：123456
* 开启ssh服务
* 关闭防火墙
* 安装wget
* 修改yum源为阿里云

## docker-k8s 虚拟机

学习容器的服务端

* docker
* docker-compose
* harbor 镜像仓库 管理界面
  + 管理界面 [192.168.100.110:80](http://192.168.100.110:80)
  + 账户 admin
  + 密码 Harbor12345
* ip = 192.168.100.110

## docker-learn 虚拟机

学习容器的客户端

* docker
* docker-compose
* docker login 私有仓库
* ip = 192.168.100.206

## 大前端 虚拟机

学习容器的客户端

* git
* curl 网络下载工具
* nvm nodejs版本管理工具
* ruby
* jekyll bundler
* 主机、虚拟机共享jekyll文件
* ip = 192.168.100.202

## server1 虚拟机

* RabbitMQ 单节点 管理界面
  + 管理界面 [192.168.100.101:15672](http://192.168.100.101:15672/)
  + 账户 admin
  + 密码 admin123

* ip = 192.168.100.101

## server2 虚拟机

功能待定，安装redis mysql es nacos 集群

* ip = 192.168.100.102

## server3 虚拟机

功能待定，安装redis mysql es nacos 集群

* ip = 192.168.100.103

## server4 虚拟机

功能待定，安装redis mysql es nacos 集群

* ip = 192.168.100.104

## server5 虚拟机

功能待定，安装redis mysql es nacos 集群

* ip = 192.168.100.105

## server6 虚拟机

功能待定，安装redis mysql es nacos 集群

* ip = 192.168.100.106

