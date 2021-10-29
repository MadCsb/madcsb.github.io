---
title: "虚拟软件 VMware Workstation Pro"
excerpt: "模板虚拟机安装基础软件，通过完整克隆，快速生成其他服务器。"
toc: true
---

VMware Workstation Pro 是行业标准桌面 Hypervisor，使用它可在 Windows 或 Linux 桌面上运行 Windows、Linux 和 BSD 虚拟机。

我使用16.1.2 build-17966106版本的VMware® Workstation 16 Pro 

## NAT (地址转换模式)

在NAT模式中，主机网卡直接与虚拟NAT设备相连，然后虚拟NAT设备与虚拟DHCP服务器一起连接在虚拟交换机VMnet8上，这样就实现了虚拟机联网。

## VMnet8

VMware Network Adapter VMnet8虚拟网卡主要是实现主机与虚拟机之间的通信。

1. 打开VMware -> 编辑(E) -> 虚拟网络编辑器(N)
2. 选中《VMnet8》
    <figure>
        <a href="/assets/images/vmware-vmnet8.png"><img src="/assets/images/vmware-vmnet8.png"></a>
        <figcaption>虚拟网络编辑器</figcaption>
    </figure>
3. 打开《NAT设置》
    <figure>
        <a href="/assets/images/vmware-vmnet8-nat.png"><img src="/assets/images/vmware-vmnet8-nat.png"></a>
        <figcaption>NAT 设置</figcaption>
    </figure>
4. VMnet8 ip设置
    <figure>
        <a href="/assets/images/vmware-vmnet8-ip.png"><img src="/assets/images/vmware-vmnet8-ip.png"></a>
        <figcaption>IPv4 属性</figcaption>
    </figure>