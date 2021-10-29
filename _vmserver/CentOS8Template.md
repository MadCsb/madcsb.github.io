---
title: "CentOS8Template 模板虚拟机"
excerpt: ""
toc: true
---

CentOS是Community Enterprise Operating System的缩写，也叫做社区企业操作系统。是企业Linux发行版领头羊Red Hat Enterprise Linux（以下称之为RHEL）的再编译版本（是一个再发行版本），而且在RHEL的基础上修正了不少已知的 Bug ，相对于其他 Linux 发行版，其稳定性值得信赖。

虚拟机的模板机，我选择CentOS 8，下载文件CentOS-8.3.2011-x86_64-dvd1.iso。

模板虚拟机的作用是安装基础的软件，通过克隆模板虚拟机能够快速完成机器的安装配置。

### VMware 创建虚拟机

#### 打开VMware -> 文件(F) -> 新建虚拟机(N)

<figure>
	<a href="/assets/images/st-new-0.png"><img src="/assets/images/st-new-0.png"></a>
	<figcaption>欢迎使用新建虚拟机向导</figcaption>
</figure>

选择自定义(高级)选项，点击下一步

#### 选择虚拟机硬件兼容性

<figure>
	<a href="/assets/images/st-new-1.png"><img src="/assets/images/st-new-1.png"></a>
	<figcaption>选择虚拟机硬件兼容性</figcaption>
</figure>

我选择了当前版本最新的Workstation 16.x，点击下一步

#### 安装客户机操作系统
<figure>
	<a href="/assets/images/st-new-2.png"><img src="/assets/images/st-new-2.png"></a>
	<figcaption>安装客户机操作系统</figcaption>
</figure>

CentOS操作系统iso文件可以通过<a href="http://isoredirect.centos.org/centos/8/isos/x86_64/" target="_blank">官网下载</a>。

选择安装程序光盘映像文件，点击浏览，选中CentOS-8.3.2011-x86_64-dvd1.iso文件，点击下一步

#### 简易安装信息

<figure>
	<a href="/assets/images/st-new-3.png"><img src="/assets/images/st-new-3.png"></a>
	<figcaption>简易安装信息</figcaption>
</figure>

在这一步为安装好的虚拟机设置全名、用户名/密码。但是没起效果，后期会重新设置。随便输入后点击下一步。

#### 命名虚拟机

<figure>
	<a href="/assets/images/st-new-4.png"><img src="/assets/images/st-new-4.png"></a>
	<figcaption>命名虚拟机</figcaption>
</figure>

输入虚拟机名称:CentOS8Template,选择虚拟机位置，如果目录不存在，则会自动创建。点击下一步

#### 处理器配置

<figure>
	<a href="/assets/images/st-new-5.png"><img src="/assets/images/st-new-5.png"></a>
	<figcaption>处理器配置</figcaption>
</figure>

考虑到大部分测试场景需要多处理器、多内核，所以处理器数量=2，每个处理器的内核数量=2.如果机器实在性能不够，可以减少数量。点击下一步

#### 此虚拟机的内存

<figure>
	<a href="/assets/images/st-new-6.png"><img src="/assets/images/st-new-6.png"></a>
	<figcaption>此虚拟机的内存</figcaption>
</figure>

考虑到大部分测试场景2G内存够基本的应用，如果机器实在性能不够，后期通过设置增大内存。点击下一步

#### 网络类型

<figure>
	<a href="/assets/images/st-new-7.png"><img src="/assets/images/st-new-7.png"></a>
	<figcaption>网络类型</figcaption>
</figure>

创建虚拟机的主要原因是自己开发、测试方便，所以不需要别的机器访问，只需要自己的机器和虚拟机互相访问，选择使用网络地址转换(NAT)连接方式。点击下一步

#### 选择I/O控制器类型

<figure>
	<a href="/assets/images/st-new-8.png"><img src="/assets/images/st-new-8.png"></a>
	<figcaption>选择I/O控制器类型</figcaption>
</figure>

选择LSI Logic。点击下一步

#### 选择磁盘类型

<figure>
	<a href="/assets/images/st-new-9.png"><img src="/assets/images/st-new-9.png"></a>
	<figcaption>选择磁盘类型</figcaption>
</figure>

选择SCSI。点击下一步

#### 选择磁盘

<figure>
	<a href="/assets/images/st-new-10.png"><img src="/assets/images/st-new-10.png"></a>
	<figcaption>选择磁盘</figcaption>
</figure>

选择创建新虚拟磁盘。点击下一步

#### 指定磁盘容量

<figure>
	<a href="/assets/images/st-new-11.png"><img src="/assets/images/st-new-11.png"></a>
	<figcaption>指定磁盘容量</figcaption>
</figure>

一般情况下20G容量已经足够测试，如果后期容量不够，可以通过设置增大容量，或者挂载新的磁盘。点击下一步

#### 指定磁盘文件

<figure>
	<a href="/assets/images/st-new-12.png"><img src="/assets/images/st-new-12.png"></a>
	<figcaption>指定磁盘文件</figcaption>
</figure>

点击下一步

#### 已准备好创建虚拟机

<figure>
	<a href="/assets/images/st-new-13.png"><img src="/assets/images/st-new-13.png"></a>
	<figcaption>已准备好创建虚拟机</figcaption>
</figure>


### VMware 安装虚拟机

#### 打开VMware -> 点击CentOS8Template虚拟机 -> 开启此虚拟机

第一次启动虚拟机可能会出现无法启动，参考[FAQ 1](#FAQ1) <code>Section %packages does not end with %end</code>

#### 选择安装过程语言

<figure>
	<a href="/assets/images/st-install-0.png"><img src="/assets/images/st-install-0.png"></a>
	<figcaption>选择安装过程语言</figcaption>
</figure>

点击继续

#### 安装信息摘要

<figure>
	<a href="/assets/images/st-install-1.png"><img src="/assets/images/st-install-1.png"></a>
	<figcaption>安装信息摘要</figcaption>
</figure>

#### 键盘布局

<figure>
	<a href="/assets/images/st-install-2.png"><img src="/assets/images/st-install-2.png"></a>
	<figcaption>键盘布局</figcaption>
</figure>

安装信息摘要 -> 键盘(K)，打开键盘布局

键盘布局 -> + 添加汉语、英语(English (US, alt, intL)) -> 完成，打开安装信息摘要

#### 安装目标位置

<figure>
	<a href="/assets/images/st-install-3.png"><img src="/assets/images/st-install-3.png"></a>
	<figcaption>安装目标位置</figcaption>
</figure>

安装信息摘要 -> 安装目的地(D)，打开安装目标位置

安装目标位置 -> 存储配置=自动 -> 完成，打开安装信息摘要

由于模板机并不能确定最终安装什么服务/软件，不能确定分区，先自动分区，后期如果硬盘不够，通过挂载保证需求。


#### KDUMP

<figure>
	<a href="/assets/images/st-install-4.png"><img src="/assets/images/st-install-4.png"></a>
	<figcaption>KDUMP</figcaption>
</figure>

安装信息摘要 -> KDUMP，打开KDUMP

KDUMP -> 启用kdump，为Kdump保留的内存=自动 -> 完成，打开安装信息摘要

#### 网络和主机名

安装信息摘要 -> 网络和主机名，打开网络和主机名
<figure>
	<a href="/assets/images/st-install-5.png"><img src="/assets/images/st-install-5.png"></a>
	<figcaption>网络和主机名</figcaption>
</figure>

主机名=template.centos8 -> 应用 -> 配置
<figure>
	<a href="/assets/images/st-install-6.png"><img src="/assets/images/st-install-6.png"></a>
	<figcaption>编辑 nes33</figcaption>
</figure>
IPv4设置 -> 方法=手动 -> 添加地址=192.168.100.100,子网掩码=255.255.255.0,网关=192.168.100.2 -> 保存 ->以太网启用

#### 软件选择

<figure>
	<a href="/assets/images/st-install-7.png"><img src="/assets/images/st-install-7.png"></a>
	<figcaption>软件选择</figcaption>
</figure>

安装信息摘要 -> 软件选择，打开软件选择

软件选择 -> 最小安装,其他都不选中 -> 完成，打开安装信息摘要

#### 根密码

<figure>
	<a href="/assets/images/st-install-8.png"><img src="/assets/images/st-install-8.png"></a>
	<figcaption>根密码</figcaption>
</figure>

安装信息摘要 -> 根密码，打开根密码

根密码 -> Root 密码=123456，确认=123456 -> 完成(双击)，打开安装信息摘要

#### 时间和日期

安装信息摘要 -> 时间和日期，打开时间和日期

忘记截图了，只要用鼠标点击世界地图，选择城市就好了。我选的是上海.

时间和日期 ->  完成，打开安装信息摘要 -> 开始安装

#### 创建用户

开始安装之后，就会创建用户 账号/密码:server/123456

<figure>
	<a href="/assets/images/st-install-9.png"><img src="/assets/images/st-install-9.png"></a>
	<figcaption>创建用户</figcaption>
</figure>

双击完成后，就可以等待安装完成了。

### 修改IP

```
vi /etc/sysconfig/network-scripts/ifcfg-ens33
```
IPADDR=192.168.100.100
DNS1=192.168.100.2
内容如下
<figure>
	<a href="/assets/images/st-install-faq1.png"><img src="/assets/images/st-install-faq1.png"></a>
	<figcaption>ip设置</figcaption>
</figure>

### 开启ssh服务
ssh服务开启后，可以通过xshell、SecureCRT等软件远程连接操作。
```
systemctl enable sshd
```

### 修改yum源为阿里云
1. 备份<code> mv /etc/yum.repos.d/CentOS-Linux-BaseOS.repo /etc/yum.repos.d/CentOS-Linux-BaseOS.repo.backup </code>
2. 获取<code> wget -O /etc/yum.repos.d/CentOS-Base.repo https://mirrors.aliyun.com/repo/Centos-8.repo </code>
3. 更名<code>mv /etc/yum.repos.d/CentOS-Base.repo /etc/yum.repos.d/CentOS-Linux-BaseOS.repo</code>
4. 生成缓存<code>yum makecache</code>
5. 更新yum<code>yum update</code>
   
### 关闭防火墙
```
systemctl stop firewalld.service
```

### 安装wget
```
yum install -y wget
```

### 虚拟机拷贝

#### 打开克隆虚拟机向导

打开VMware -> CentOS8Template -> 鼠标右键 -> 管理 ->克隆
<figure>
	<a href="/assets/images/st-clone-0.png"><img src="/assets/images/st-clone-0.png"></a>
	<figcaption>克隆虚拟机向导</figcaption>
</figure>

#### 克隆源

选择虚拟机中的当前状态
<figure>
	<a href="/assets/images/st-clone-1.png"><img src="/assets/images/st-clone-1.png"></a>
	<figcaption>克隆源</figcaption>
</figure>

#### 克隆类型

选择创建完整克隆
<figure>
	<a href="/assets/images/st-clone-2.png"><img src="/assets/images/st-clone-2.png"></a>
	<figcaption>克隆类型</figcaption>
</figure>

#### 新虚拟机名称

输入虚拟机名称和位置
<figure>
	<a href="/assets/images/st-clone-3.png"><img src="/assets/images/st-clone-3.png"></a>
	<figcaption>新虚拟机名称</figcaption>
</figure>

#### 正在克隆虚拟机

<figure>
	<a href="/assets/images/st-clone-4.png"><img src="/assets/images/st-clone-4.png"></a>
	<figcaption>正在克隆虚拟机</figcaption>
</figure>

#### 修改host

```
vi /etc/hostname
```
内容为新虚拟机的名字,如：server1

#### 修改ip
```
vi /etc/sysconfig/network-scripts/ifcfg-ens33
```
内容为新虚拟机的ip地址,如：IPADDR=192.168.100.101。完整内容参考[无法链接网络](#FAQ2)


### FAQ 1.  Section %packages does not end with %end. {#FAQ1}

创建玩虚拟机后，第一次启动可能会出现如下问题，无法启动

<figure>
	<a href="/assets/images/st-install-faq1.png"><img src="/assets/images/st-install-faq1.png"></a>
	<figcaption>Section %packages does not end with %end.</figcaption>
</figure>

这是由于创建虚拟机，自动加载两个CD，有两个解决方法
1. 虚拟机设置 -> 硬件 -> CD/DVD (IDE) 正在使用autoinst.iso -> 启动时连接 取消勾选
2. 虚拟机设置 -> 硬件 -> CD/DVD (IDE) 正在使用autoinst.iso -> 移除


### FAQ 2.  无法链接网络. {#FAQ2}

在创建虚拟机，或者拷贝虚拟机后，如果无法链接网络，需要对比下图中的配置.

命令行运行<code> vi /etc/sysconfig/network-scripts/ifcfg-ens33 </code>，编辑内容如下。
<figure>
	<a href="/assets/images/st-install-faq1.png"><img src="/assets/images/st-install-faq1.png"></a>
	<figcaption>ip设置</figcaption>
</figure>

注意添加DNS，DNS可以是网关